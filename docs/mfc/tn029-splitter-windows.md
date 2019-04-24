---
title: 'TN029: Rozdělovač Windows'
ms.date: 11/04/2016
f1_keywords:
- vc.windows.splitter
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
ms.openlocfilehash: 6c2f619d9cd619ca598c66ca657faa1b9dccaaa2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305707"
---
# <a name="tn029-splitter-windows"></a>TN029: Rozdělovač Windows

Tato poznámka popisuje MFC [CSplitterWnd – třída](../mfc/reference/csplitterwnd-class.md), která poskytuje okno rozdělí a spravuje, změna velikosti další podokno okna.

## <a name="splitter-styles"></a>Styly rozdělovač

A `CSplitterWnd` podporuje dva různé styly rozdělení systému windows.

V "statické příčky," vytvoří okna s rozdělovačem podokna při jeho vytvoření. Pořadí a počet podokna nikdy nezmění. Rozdělovač panely se používají ke změně velikosti různých podoken. Tento styl slouží k zobrazení různých zobrazení třídy v každém podokně. Editor grafiky Visual C++ a Správce souborů Windows jsou příkladem programy, které používají tento styl rozdělovač. Tento styl okno s rozdělovačem nepoužívá rozdělovač polí.

V "dynamické příčky," jsou další podokna vytvořen a zničen jako uživatel rozdělení a zrušit rozdělení nová zobrazení. Tento rozdělovač s pohledem na začátku a poskytuje rozdělovač polí pro uživatele, pro kterého rozdělení. Okna s rozdělovačem dynamicky vytvoří nový objekt zobrazení, pokud je rozdělený zobrazení v jednom směru. Tento nový objekt zobrazení představuje nové podokno. Pokud zobrazení je v obou směrech rozdělit přes rozhraní klávesnice, okna s rozdělovačem vytvoří tři nové objekty pro tři podokna zobrazení. Rozdělení je aktivní, Windows zobrazí okno rozdělovače jako oddělovač mezi podokny. Windows odstraní objekty další zobrazení, když uživatel odebere rozdělení, ale původní zobrazení zůstane až do okna s rozdělovačem samotného je zničen. Aplikace Microsoft Excel a Microsoft Word jsou příkladem aplikací, které používají dynamické rozdělovače style.

Když vytvoříte buď druh okno s rozdělovačem, musíte zadat maximální počet řádků a sloupců, které budou spravovat příčky. Statické rozdělovače vytvoří podokna tak, aby vyplnil všechny řádky a sloupce. Dynamické rozdělovače vytvoří pouze první podokno při `CSplitterWnd` se vytvoří.

Maximální počet podoken, kterou zadáte pro statické příčky je 16 řádků a 16 sloupců. Doporučená konfigurace jsou:

- 1 řádek x 2 sloupce: obvykle s odlišnými podokny

- sloupec 2 řádky x 1: obvykle s odlišnými podokny

- 2 řádky x 2 sloupce: obvykle se podobá podokna

Maximální počet podoken, které zadáte pro dynamické příčky je 2 řádky podle 2 sloupce. Doporučená konfigurace jsou:

- 1 řádek x 2 sloupce: pro sloupcová data o

- sloupec 2 řádky x 1: pro textový nebo jiná data

- 2 řádky x 2 sloupce: pro tabulku nebo mřížky orientovaný dat

## <a name="splitter-examples"></a>Příklady rozdělovač

Řadu ukázek programů MFC přímo nebo nepřímo použít rozdělovače oken. Ukázky knihovny MFC Obecné [VIEWEX](../overview/visual-cpp-samples.md) ukazuje několik použití statické příčky, včetně postupu, které mají být umístěny rozdělovač rozdělovač.

K vytvoření nového více dokumentu rozhraní (MDI) třída podřízeného rámce okna obsahující okno s rozdělovačem. můžete také použít ClassWizard. Další informace o rozdělovače oken, naleznete v tématu [více typů dokumentů, zobrazení a rámečku Windows](../mfc/multiple-document-types-views-and-frame-windows.md).

## <a name="terminology-used-by-implementation"></a>Terminologie použitá implementací

Tady je seznam termínů, které jsou specifické pro rozdělovače oken:

`CSplitterWnd`: Okno, které poskytuje podokně rozdělování ovládací prvky a posuvníků, které jsou sdíleny mezi všechny podokna na řádek nebo sloupec. Zadejte řádků a sloupců s nulovým základem čísla (je podokno první řádek = 0 and sloupec = 0).

Podokno: Okno aplikace specifické pro aplikaci, která `CSplitterWnd` spravuje. Podokno je obvykle objekt, který je odvozen z [CView Class](../mfc/reference/cview-class.md), ale může být kterýkoli [CWnd](../mfc/reference/cwnd-class.md) objekt, který má ID odpovídající podřízené okno.

Použití `CWnd`-odvozené objektu, předejte RUNTIME_CLASS objekt, který má `CreateView` fungovat stejně jako v případě, že jste používali `CView`-odvozené třídy. Vaše třída musíte použít DECLARE_DYNCREATE a IMPLEMENT_DYNCREATE, protože rozhraní používá dynamické vytváření za běhu. I když existuje velké množství kódu v `CSplitterWnd` , která je specifická pro `CView` třídy [CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof) vždy použita dříve, než se provádí tyto akce.

Rozdělovač: Ovládací prvek, který je umístěn mezi řádky a sloupce podoken. Slouží k úpravě velikosti řádků nebo sloupců podoken.

Rozdělovač pole: Ovládací prvek v dynamické `CSplitterWnd` , můžete použít k vytvoření nových řádků nebo sloupců podoken. Je umístěný v horní části stránky svislé posuvníky nebo nalevo od vodorovné posuvníky.

Rozdělovač průniku: Je určena průsečíkem svislé příčky a vodorovný rozdělovač. Můžete přetáhnout pro nastavení velikosti řádků a sloupců podoken současně.

## <a name="shared-scroll-bars"></a>Posuvníky sdílené

`CSplitterWnd` Třída také podporuje sdílené posuvníky. Tyto ovládací prvky posuvníku panelu jsou podřízené `CSplitterWnd` a jsou sdílené s různými podokny v příčky.

Například v okně sloupec 1 řádek x 2, můžete zadat WS_VSCROLL při vytváření `CSplitterWnd`. Windows vytvoří speciální posuvník, jež jsou sdílena mezi dvě podokna.

```
[      ][      ][^]
[pane00][pane01][|]
[      ][      ][v]
```

Když se uživatel přesune na posuvník, WM_VSCROLL zprávy se odešlou do obou zobrazeních. Při některém zobrazení nastaví pozici panelu posunutí, nastaví se sdílené posuvníku.

Všimněte si, že sdílené posuvníky jsou nejužitečnější s podobnými objekty zobrazení. Pokud je kombinovat různé typy zobrazení v rozdělovač, budete muset psát kód speciální koordinovat jejich pozice posuvníku. Žádné `CView`-odvozené třídy, která používá `CWnd` posuvník rozhraní API budou delegovat na sdílené posuvník, pokud existuje. `CScrollView` Je jeden příklad implementace `CView` třídu, která podporuje sdílené posuvníky. Třídy, které nejsou odvozeny od `CView`, třídy, které využívají – ovládací prvek posuvník nebo třídy, které používají standardní implementace Windows (například `CEditView`) nebude fungovat s funkcí sdílené posuvníku panelu `CSplitterWnd`.

## <a name="minimum-sizes"></a>Minimální velikost

Pro každý řádek je minimální výšku řádku a pro každý sloupec je minimální šířka. Tohle minimum zaručuje, že podokno není příliš malá, chcete-li zobrazit podrobné.

Statický rozdělovač okna je počáteční řádek minimální výšku a ve sloupci šířku 0. Pro dynamické okno s rozdělovačem, počáteční řádek minimální výšku a ve sloupci šířku institut NIST *sizeMin* parametr `CSplitterWnd::Create` funkce.

Tyto minimální velikosti můžete změnit pomocí [CSplitterWnd::SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo) a [CSplitterWnd::SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo) funkce.

## <a name="actual-vs-ideal-sizes"></a>Skutečnost v porovnání s. Ideální velikost

Rozložení podokny okna s rozdělovačem závisí na velikosti rámce, který je obsahuje. Když uživatel změní velikost nadřazeného rámce `CSplitterWnd` přemístí a změní velikost podokna tak, aby se vešly a také možné.

Uživatel může ručně nastavit řádku výšku a ve sloupci šířku velikosti nebo program můžete nastavit ideální velikost pomocí `CSplitterWnd` třídy. Skutečná velikost může být menší nebo větší než ideální. Windows upraví skutečná velikost, pokud není k dispozici dostatek místa pro zobrazení jeho ideální velikost nebo pokud existuje příliš mnoho prázdné místo v pravé nebo dolní části okna s rozdělovačem.

## <a name="custom-controls"></a>Vlastní ovládací prvky

Mnoho funkcí poskytovat vlastní chování a přizpůsobené rozhraní můžete přepsat. Můžete přepsat toto první sada poskytnout alternativní trénováním pro různé součásti grafické okno s rozdělovačem.

- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`

- `virtual void OnInvertTracker(const CRect& rect);`

Volání této funkce můžete vytvořit ovládací prvek posuvníku sdílené. Můžete přepsat tak vytvořit další ovládací prvky vedle posuvníku.

- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`

Tyto funkce implementovat logiku dynamický rozdělovač okna. Toto nastavení můžete přepsat poskytnout více pokročilou logikou rozdělovač.

- `virtual void DeleteView(int row, int col);`

- `virtual BOOL SplitRow(int cyBefore);`

- `virtual BOOL SplitColumn(int cxBefore);`

- `virtual void DeleteRow(int rowDelete);`

- `virtual void DeleteColumn(int colDelete);`

## <a name="cview-functionality"></a>CView – funkce

`CView` Třída používá následující příkazy nejvyšší úrovně delegovat `CSplitterWnd` implementace. Protože tyto příkazy jsou virtuální, standardní `CView` implementace nevyžadují celý `CSplitterWnd` implementace propojení. Pro aplikace, které používají `CView` , ale ne `CSplitterWnd`, `CSplitterWnd` implementace nebude propojena s aplikací.

- `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`

   Kontroluje, zda id_next_pane – nebo id_prev_pane – je aktuálně možné.

- `virtual void ActivateNext(BOOL bPrev = FALSE);`

   Spustí příkaz "Další podokno" nebo "Předchozí podokno".

- `virtual BOOL DoKeyboardSplit();`

   Spouští příkaz rozdělení klávesnice, obvykle "Window Split".

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
