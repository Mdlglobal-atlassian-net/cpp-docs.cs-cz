---
title: "TN029: Dělená okna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.windows.splitter
dev_langs:
- C++
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 95b7db2678c03b0508a1507567f8bedcf243cd4a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tn029-splitter-windows"></a>TN029: Dělená okna
Tato poznámka se popisuje MFC [CSplitterWnd třída](../mfc/reference/csplitterwnd-class.md), který poskytuje okno rozdělí a spravuje Změna velikosti windows jiných podokně.  
  
## <a name="splitter-styles"></a>Styly rozdělovače  
 A `CSplitterWnd` podporuje dva různé styly rozdělení windows.  
  
 V "statických příčky," okno rozdělovače vytvoří podoken při jeho vytváření. Pořadí a počet podokna nikdy nezmění. Rozdělovače řádky se používají ke změně velikosti různých podoken. Tento styl můžete použít k zobrazení jiné zobrazení třídy v každém podokně. Editor grafiky Visual C++ a Správce souborů systému Windows jsou příklady programy, které používají tento styl rozdělovače. Tento styl okna rozdělovače nepoužívá rozdělovače oken.  
  
 V "dynamické příčky", jsou další podokna vytvořen a zničen jako uživatel rozdělení a zrušit rozdělení nová zobrazení. Tato rozdělovače začíná jediné zobrazení a poskytuje rozdělovače oken pro uživatele k zahájení rozdělení. Rozdělovače oken dynamicky vytvoří nový objekt zobrazení, když je zobrazení rozdělení v jednom směru. Tento nový objekt zobrazení představuje nové podokno. Pokud zobrazení je rozdělená v obou směrech pomocí rozhraní klávesnice, okno rozdělovače vytvoří tři nové objekty pro tři nové podokna zobrazení. V době, kdy rozdělení aktivní, systém Windows zobrazí pole rozdělovače jako rozdělovač mezi podoknem. Windows odstraní objekty další zobrazení, když uživatel odebere rozdělení, ale je zničení původního zobrazení zůstane až do okna rozdělovače sám sebe. Příkladem aplikací, které používají dynamické rozdělovače styl jsou aplikace Microsoft Excel a Microsoft Word.  
  
 Když vytvoříte buď druh rozdělovače oken, musíte zadat maximální počet řádků a sloupců, které budou spravovat rozdělovače. Statické rozdělovače vytvoří podokna k vyplnění všech řádků a sloupců. Dynamické rozdělovače vytvoří pouze první podokně při `CSplitterWnd` je vytvořena.  
  
 Maximální počet podokna, které můžete zadat pro statické příčky je 16 řádků a 16 sloupců. Doporučené konfigurace jsou:  
  
-   1 řádek x 2 sloupce: obvykle s odlišné podokna  
  
-   sloupec 2 řádky x 1: obvykle s odlišné podokna  
  
-   2 řádky x 2 sloupce: obvykle s podobnou podokna  
  
 Maximální počet podokna, které můžete zadat pro dynamické příčky je 2 řádků a sloupců 2. Doporučené konfigurace jsou:  
  
-   1 řádek x 2 sloupce: sloupcová dat  
  
-   sloupec 2 řádky x 1: pro textové nebo další data  
  
-   2 řádky x 2 sloupce: pro tabulku nebo mřížky orientovaných na data  
  
## <a name="splitter-examples"></a>Příklady rozdělovače  
 Mnoho z ukázkových aplikací MFC pomocí rozdělovače oken přímo nebo nepřímo. Ukázka MFC Obecné [VIEWEX](../visual-cpp-samples.md) znázorňuje několik použití statické příčky, včetně toho, jak umístit rozdělovač rozdělovač.  
  
 Můžete taky ClassWizard pro vytvoření nového více dokumentů rozhraní (MDI) podřízené třídy oken s rámečkem obsahující rozděleném okně. Další informace o rozdělovače oken najdete v tématu [více typů dokumentů, zobrazení a oken s rámečkem](../mfc/multiple-document-types-views-and-frame-windows.md).  
  
## <a name="terminology-used-by-implementation"></a>Terminologie použitá implementací  
 Tady je seznam termínů, které jsou specifické pro rozdělovače oken:  
  
 `CSplitterWnd`:  
 Okno, které poskytuje rozdělení podokně ovládací prvky a posuvníky, které jsou sdíleny mezi všechny podokna na sloupce či řádku. Zadejte řádků a sloupců s nulovým základem čísla (první podokno je řádek = 0 a ve sloupci = 0).  
  
 Podokno:  
 Okno s specifické pro aplikaci, `CSplitterWnd` spravuje. Podokno je obvykle objekt, který je odvozený od [CView – třída](../mfc/reference/cview-class.md), ale může být libovolná [CWnd](../mfc/reference/cwnd-class.md) objekt, který má odpovídající podřízené okno ID.  
  
 Používat `CWnd`-odvozené objektu, předat `RUNTIME_CLASS` objektu `CreateView` fungovat stejně jako Pokud jste používali `CView`-odvozené třídy. Musí používat vlastní třídy `DECLARE_DYNCREATE` a `IMPLEMENT_DYNCREATE` protože rozhraní používá dynamického vytváření za běhu. I když je velké množství kódu v `CSplitterWnd` týkající se `CView` třídy, [CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof) je vždy použita dříve, než se provádí tyto akce.  
  
 Rozdělovač:  
 Ovládací prvek, který je umístěn mezi řádků a sloupců podokna. Může se použít ke změně velikosti řádků nebo sloupce podokna.  
  
 Rozdělovače pole:  
 Ovládací prvek v dynamický `CSplitterWnd` , můžete použít k vytvoření nové řádky nebo sloupce podokna. Je umístěn v horní části svislé posuvníky nebo nalevo od vodorovné posuvníky.  
  
 Rozdělovače průnik:  
 Průnik svislý oddělovač a vodorovný oddělovač. Můžete přetáhnout pro nastavení velikosti řádků a sloupců z podokna současně.  
  
## <a name="shared-scroll-bars"></a>Sdílené posuvníky  
 `CSplitterWnd` Třída také podporuje sdílené posuvníky. Tyto ovládací prvky posuvníku panelu jsou podřízené objekty `CSplitterWnd` a jsou sdíleny s různých podoken v rozdělovače.  
  
 Například v okně sloupec 1 řádek x 2 můžete ws_vscroll – při vytváření `CSplitterWnd`. Windows vytvoří ovládacích prvků na panelu speciální scroll, jež jsou sdílena mezi dvě podokna.  
  
```  
[      ][      ][^]  
[pane00][pane01][|]  
[      ][      ][v]  
```  
  
 Když se uživatel přesune posuvníku, `WM_VSCROLL` zprávy budou odeslány do obou zobrazeních. Když buď zobrazení nastaví pozici posunutí panelu, nastaví se sdílené posuvníku.  
  
 Upozorňujeme, že sdílené posuvníky jsou velmi užitečné s podobnými objekty zobrazení. Pokud můžete kombinovat různé typy zobrazení v rozdělovač, budete muset napsat speciální kód pro koordinaci jejich posuňte pozic. Všechny `CView`-odvozené třídy, která používá `CWnd` posuvníku rozhraní API bude delegovat na sdílené posuvníku, pokud existuje. `CScrollView` Implementace je příkladem `CView` třídu, která podporuje sdílené posuvníky. Třídy, které nejsou odvozeny od `CView`, tříd, které jsou závislé na posuvníky – ovládací prvek nebo třídy, které používají standardní implementace systému Windows (například `CEditView`) nebude fungovat se funkci panelu sdílené scroll `CSplitterWnd`.  
  
## <a name="minimum-sizes"></a>Minimální velikosti  
 Pro každý řádek je minimální výšku řádku a pro každý sloupec je sloupec minimální šířku. Toto minimum zaručuje, že podokno není příliš malá, která se má zobrazit podrobné.  
  
 Statické rozdělovače období je počáteční řádek minimální výška a ve sloupci šířku 0. Dynamické rozdělovače období, se nastavují šířku počáteční řádek minimální výška a ve sloupci `sizeMin` parametr `CSplitterWnd::Create` funkce.  
  
 Tyto minimální velikosti můžete změnit pomocí [CSplitterWnd::SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo) a [CSplitterWnd::SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo) funkce.  
  
## <a name="actual-vs-ideal-sizes"></a>Skutečné vs. Ideální velikosti  
 Rozložení podokna v rozděleném okně, závisí na velikosti rámce, který je obsahuje. Pokud uživatel zmenší obsahující rámec `CSplitterWnd` přemístí a změní velikost podokna tak, aby se vešly a také možné.  
  
 Uživatel může ručně nastavit řádek velikosti šířky výšky a sloupce, nebo program lze nastavit pomocí jeho ideální velikost `CSplitterWnd` třídy. Skutečná velikost může být menší nebo větší než ideální. Pokud není k dispozici dostatek místa k zobrazení jeho ideální velikost, nebo pokud je příliš mnoho prázdného místa v pravé nebo dolní části okna rozdělovače způsobem se upraví Windows skutečná velikost.  
  
## <a name="custom-controls"></a>Vlastní ovládací prvky  
 Mnoho funkcí zajistit přizpůsobené rozhraní a vlastní chování můžete přepsat. Tato první sada poskytnout alternativní dokumentů pro různé součásti grafické okna rozdělovače můžete přepsat.  
  
- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`  
  
- `virtual void OnInvertTracker(const CRect& rect);`  
  
 Volání této funkce můžete vytvořit ovládací prvek sdílené posuvníku. Je možné přepsat jeho vytvořit další ovládací prvky vedle posuvníku.  
  
- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`  
  
 Tyto funkce implementovat logiku okna dynamické rozdělovače. Toto nastavení můžete přepsat zajistit pokročilejší rozdělovače logiku.  
  
- `virtual void DeleteView(int row, int col);`  
  
- `virtual BOOL SplitRow(int cyBefore);`  
  
- `virtual BOOL SplitColumn(int cxBefore);`  
  
- `virtual void DeleteRow(int rowDelete);`  
  
- `virtual void DeleteColumn(int colDelete);`  
  
## <a name="cview-functionality"></a>CView funkce  
 `CView` Třída používá následující příkazy nejvyšší úrovni delegovat `CSplitterWnd` implementace. Protože tyto příkazy jsou virtuální, standardní `CView` implementace nebude vyžadovat celý `CSplitterWnd` implementace propojení. Pro aplikace, které používají `CView` ale ne `CSplitterWnd`, `CSplitterWnd` implementace nebudou propojené s aplikací.  
  
 `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`  
 Kontroluje, zda je nyní možné id_next_pane – nebo id_prev_pane –.  
  
 `virtual void ActivateNext(BOOL bPrev = FALSE);`  
 Spustí příkaz "Další podokno" nebo "Předchozí podokno".  
  
 `virtual BOOL DoKeyboardSplit();`  
 Provede klávesnice split příkazu, obvykle "rozdělení okna".  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

