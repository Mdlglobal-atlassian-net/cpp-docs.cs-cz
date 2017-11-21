---
title: "TN031: Ovládací pruhy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.controls.bars
dev_langs: C++
helpviewer_keywords:
- control bars [MFC], styles
- CStatusBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], deriving from
- control bars [MFC], classes [MFC]
- CDialogBar class [MFC], Tech Note 31 usage
- CToolBar class [MFC], Tech Note 31 usage
- TN031
- styles [MFC], control bars
ms.assetid: 8cb895c0-40ea-40ef-90ee-1dd29f34cfd1
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 18bc2ce03f4868a942d118a8f597df5b5f6eb4df
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tn031-control-bars"></a>TN031: Ovládací pruhy
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje třídy panelu ovládacích prvků v prostředí MFC: Obecné [ccontrolbar –](#_mfcnotes_ccontrolbar), [cstatusbar –](#_mfcnotes_cstatusbar), [ctoolbar –](#_mfcnotes_ctoolbar), [CDialogBar](#_mfcnotes_cdialogbar)a  **CDockBar**.  
  
## <a name="_mfcnotes_ccontrolbar"></a>Ccontrolbar – 
  
 A **ControlBar** je `CWnd`-odvozené třídy, který:  
  
-   Je zarovnán do pravého horního nebo dolního okně s rámečkem.  
  
-   Může obsahovat podřízené položky, které jsou buď ovládací prvky založené na HWND (například `CDialogBar`) nebo jiných-`HWND` na základě položky (například `CToolBar`, `CStatusBar`).  
  
 Ovládací pruhy podporují další styly:  
  
- `CBRS_TOP`(Výchozí) připnout na ovládací prvek panelu na začátek.  
  
- `CBRS_BOTTOM`Připnete na ovládací prvek panelu do dolní.  
  
- `CBRS_NOALIGN`Když změní velikost nadřazené není přemístit na ovládací prvek panelu.  
  
 Třídy odvozené od `CControlBar` poskytovat zajímavějšího implementace:  
  
- `CStatusBar`Stavový řádek položky jsou podokna panelu Stav obsahující text.  
  
- `CToolBar`Panelu nástrojů položky jsou rastrového obrázku tlačítka zarovnán v řádku.  
  
- `CDialogBar`Rámeček panelu nástrojů jako obsahující standardní windows ovládacích prvků (vytvořené z prostředku šablony dialogové okno).  
  
- **CDockBar** zobecněný ukotvení oblasti pro ostatní `CControlBar` odvozené objekty. Konkrétní členské funkce a proměnné, které jsou k dispozici v této třídě jsou pravděpodobně v budoucích verzích změnit.  
  
 Všechny ovládací prvek panelu objekty nebo windows bude podřízená okna některé nadřazeného rámce okna. Jsou obvykle přidávána na stejné úrovni jako klientské oblasti rámečku (například klienta MDI nebo zobrazení). ID podřízené okno ovládacích pruhů je důležité. Výchozí rozložení ovládacích pruhů funguje výhradně u ovládací pruhy s identifikátory v rozsahu **AFX_IDW_CONTROLBAR_FIRST** k **AFX_IDW_CONTROLBAR_LAST**. Všimněte si, že i když je rozsah 256 ovládacího panelu ID, první 32 tyto ovládací prvek panelu ID jsou speciální vzhledem k tomu, že jsou přímo nepodporuje architektura náhledu tisku.  
  
 `CControlBar` Třída poskytuje standardní implementace pro:  
  
-   Zarovnání ovládacích pruhů na nahoru, dolů nebo obou stranách rámečku.  
  
-   Přidělování řízení položky pole.  
  
-   Podpora implementace odvozené třídy.  
  
 Objekty C++ ovládací prvek panelu obvykle budou vloženy jako členy `CFrameWnd` odvozené třídy a kdy se vyčistí nadřazený `HWND` a jsou zničení objektu. Pokud potřebujete přidělit objekt ovládací prvek panelu v haldě, můžete jednoduše nastavit **m_bAutoDestruct** člena **TRUE** aby ovládacích pruhů "**odstranit tento**" při `HWND` zničena.  
  
> [!NOTE]
>  Pokud vytvoříte vlastní `CControlBar`-odvozené třídy, nikoli pomocí jedné z knihovny MFC odvozených tříd, jako například `CStatusBar`, `CToolBar`, nebo `CDialogBar`, budete muset nastavit `m_dwStyle` – datový člen. To lze provést v přepsané **vytvořit**:  
  
```  
// CMyControlBar is derived from CControlBar  
BOOL CMyControlBar::Create(CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID)  
{  
    m_dwStyle = dwStyle;  
 
 .  
 .  
 .  
}  
```  
  
 **Algoritmus rozložení ovládacích pruhů**  
  
 Algoritmus rozložení ovládacího prvku panel je velmi jednoduchý. Okně s rámečkem odešle zprávu **WM_SIZEPARENT** na všechny podřízené objekty v rozsahu ovládací prvek panelu. Společně se tato zpráva je předán ukazatel na obdélníku klienta nadřazeného objektu. Tato zpráva je odeslána podřízených objektů v pořadí Z-order. Tyto informace použít podřízených ovládacích pruhů samy stanovují a snížení velikosti nadřazeného klientské oblasti. Konečné obdélníku, který se nechá oblasti normální klienta (méně ovládací pruhy) se používá k umístění okna Hlavní klienta (obvykle klienta, zobrazení nebo rozdělovače okna MDI).  
  
 V tématu `CWnd::RepositionBars` a `CFrameWnd::RecalcLayout` další podrobnosti.  
  
 MFC privátní Windows zprávy, včetně **WM_SIZEPARENT**, jsou dokumentovány v článku [Technická poznámka 24](../mfc/tn024-mfc-defined-messages-and-resources.md).  
  
## <a name="_mfcnotes_cstatusbar"></a>Cstatusbar –  
  
 Stavový řádek je ovládací prvek panel, který má řádek podokna výstup textu. Existují dvě běžné způsoby použití podokna výstup textu:  
  
-   Jako řádek zprávy  
  
     (například standardní nabídky Nápověda řádek zprávy). Tyto jsou obvykle dostupné přes 0 – na základě indexované  
  
-   Jako indikátory stavu  
  
     (například Zakončení, počtu a SCRL indikátory). Tyto jsou obvykle dostupné přes ID řetězec nebo příkazu.  
  
 Písmo pro stavový řádek je bod 10 MS Sans Serif (závisí na Průvodce návrhem aplikace rozhraní Windows nebo nejlepší shodu písma mappers 10 bodů Švýcarskou přímo úměrná písma). V různých verzích systému Windows, jako je například japonské verzi písem vybrané se liší.  
  
 Barvy použité ve stavovém řádku jsou také konzistentní s doporučení příručce pro návrh aplikace rozhraní Windows. Tyto barvy nejsou pevně zakódovanou a jsou dynamicky změnily v reakci na uživatele přizpůsobení v Ovládacích panelech.  
  
|Položka|Hodnota barvy systému Windows|Výchozí RGB|  
|----------|-------------------------|-----------------|  
|Stav pozadí panelu|**COLOR_BTNFACE**|RGB (192, 192 192.)|  
|Text stavového řádku|**COLOR_BTNTEXT**|RGB (000, 000 000.)|  
|Stavový řádek levého horního okraje|**COLOR_BTNHIGHLIGHT**|RGB (255, 255 255.)|  
|Stavový řádek robota/pravého okraje|**COLOR_BTNSHADOW**|RGB (128, 128, 128)|  
  
 **Cstatusbar – podpora CCmdUI**  
  
 Způsob, jakým jsou obvykle aktualizovány indikátory je prostřednictvím `ON_UPDATE_COMMAND_UI` mechanismus. Na dobu nečinnosti, bude volat stavového řádku `ON_UPDATE_COMMAND_UI` obslužná rutina s ID řetězec podokně indikátoru.  
  
 `ON_UPDATE_COMMAND_UI` Můžete volat obslužné rutiny:  
  
- **Povolit**: Pokud chcete povolit nebo zakázat v podokně. Zakázané podokně vypadá přesně povoleno podokně ale text je neviditelné (tedy vypne indikátor text).  
  
- **SetText –**: Chcete-li změnit text. Dávejte pozor, pokud to použít, protože v podokně se automaticky nezmění.  
  
 Odkazovat třídy [cstatusbar –](../mfc/reference/cstatusbar-class.md) v *knihovny tříd* podrobnosti o `CStatusBar` vytváření a přizpůsobení rozhraní API. Většina přizpůsobení stavových řádků se má provést před stavový řádek původně jsou dostupná.  
  
 Stavový řádek podporuje pouze jeden pružně roztáhnout podokno, obvykle první. Velikost tohoto panelu je skutečně minimální velikost. Pokud stavový řádek je větší, než je minimální velikost všech podoken, bude mu udělená žádné další šířka do podokna pružně roztáhnout. Vzhledem k tomu, že se první podokno pružně roztáhnout má výchozí aplikace s stavového řádku zarovnaný doprava indikátory Zakončení, počtu a SCRL.  
  
## <a name="_mfcnotes_ctoolbar"></a>Ctoolbar –  
  
 Panel nástrojů je ovládací prvek panel s řádek rastrový obrázek tlačítka, která může obsahovat oddělovače. Podporují se dva styly tlačítek: tlačítek a tlačítka, zaškrtněte políčko. Funkce skupiny přepínačů mohou být vytvořeny políčko tlačítka a `ON_UPDATE_COMMAND_UI`.  
  
 Tlačítka rastrového obrázku na panelu nástrojů jsou převzaty z jedné bitové mapy. Tento rastrový obrázek musí obsahovat jednu bitovou kopii nebo glyfů pro každé tlačítko. Pořadí bitové kopie nebo glyfů v souboru bitové mapy je obvykle stejné pořadí, ve kterém se budou vykreslovat na obrazovce. (Toto můžete změnit pomocí přizpůsobení rozhraní API.)  
  
 Každé tlačítko musí mít stejnou velikost. Výchozí hodnota je standardní 24 × 22 pixelů. Každý image glyfy musí mít stejnou velikost a musí být vedle sebe v souboru bitové mapy. Výchozí velikost bitové kopie nebo glyfy je 16 x 15 pixelů. Proto pro panel nástrojů s 10 tlačítka (pomocí standardní velikosti), budete potřebovat rastrového obrázku, který je 160 pixelů a 15 pixelů.  
  
 Každé tlačítko má pouze jeden obrázek nebo glyfů. Tlačítko různé stavy a styly (například stisknutí tlačítka nahoru, dolů, zakázat, zakázané dolů, neurčitém) algorithmically generují z jedné bitové kopie nebo glyfů. Teoreticky lze použít všechny bitové mapy barvu nebo DIB. Pokud původní bitové kopie je odstínech šedi, algoritmus pro generování tlačítko různé stavy funguje nejlépe. Podívejte se na standardním panelu nástrojů tlačítka a clipart tlačítka panelu nástrojů, který je zadaný v ukázce MFC Obecné [CLIPART](../visual-cpp-samples.md) příklady.  
  
 Barvy používané v panelu nástrojů jsou také konzistentní s doporučení příručce pro návrh aplikace rozhraní Windows. Tyto barvy nejsou pevně zakódovanou a jsou dynamicky změnily v reakci na uživatele přizpůsobení v Ovládacích panelech.  
  
|Položka|Hodnota barvy systému Windows|Výchozí RGB|  
|----------|-------------------------|-----------------|  
|Pozadí panelu nástrojů|**COLOR_BTNFACE**|RGB(192,192,192)|  
|Tlačítka panelu nástrojů levého horního okraje|**COLOR_BTNHIGHLIGHT**|RGB(255,255,255)|  
|Tlačítka panelu nástrojů robota/pravého okraje|**COLOR_BTNSHADOW**|RGB(128,128,128)|  
  
 Kromě toho jsou rastrového obrázku tlačítka panelu nástrojů přebarveny, jako kdyby byly standardní ovládací prvky Windows tlačítko. Tato přebarvení nastane, když bitmapy je načtena z prostředku a v reakci na změny v systému barvy v reakci na uživatele přizpůsobení v Ovládacích panelech. Následující barev v rastrového obrázku panelu nástrojů bude přebarvení automaticky, je možné používat opatrně. Pokud nechcete, aby tak, aby měl část vaší bitové mapy přebarveny, použijte barvu, která se blíží jednu namapovanou hodnoty RGB. Mapování je potřeba podle přesné hodnoty RGB.  
  
|Hodnoty RGB|Dynamicky namapované hodnoty barvy|  
|---------------|------------------------------------|  
|RGB (000, 000 000.)|COLOR_BTNTEXT|  
|RGB (128, 128, 128)|COLOR_BTNSHADOW|  
|RGB (192, 192 192.)|COLOR_BTNFACE|  
|RGB (255, 255 255.)|COLOR_BTNHIGHLIGHT|  
  
 Odkazovat třídy [ctoolbar –](../mfc/reference/ctoolbar-class.md) *knihovny tříd* podrobnosti o `CToolBar` vytváření a přizpůsobení rozhraní API. Většina přizpůsobení panelů nástrojů se má provést před panelu nástrojů původně jsou dostupná.  
  
 Přizpůsobení rozhraní API slouží k úpravě tlačítko ID, styly, šířka oddělovací a které image glyfy se používá pro jaké tlačítko. Ve výchozím nastavení není potřeba použijte tato rozhraní API.  
  
## <a name="ccmdui-support-for-ctoolbar"></a>Ctoolbar – podpora CCmdUI  
 Způsob, jakým jsou vždy aktualizovány tlačítka panelu nástrojů je prostřednictvím `ON_UPDATE_COMMAND_UI` mechanismus. Na dobu nečinnosti, bude volat panelu nástrojů `ON_UPDATE_COMMAND_UI` obslužná rutina s ID příkazu, který tohoto tlačítka. `ON_UPDATE_COMMAND_UI`není volán pro oddělovače, ale je volána pro tlačítek a tlačítka, zaškrtněte políčko.  
  
 `ON_UPDATE_COMMAND_UI` Můžete volat obslužné rutiny:  
  
- **Povolit**: Pokud chcete povolit nebo zakázat tlačítko. Tento postup funguje stejně pro tlačítek a tlačítka, zaškrtněte políčko.  
  
- `SetCheck`: Chcete-li nastavení kontroly stavu tlačítko. Toto volání pro tlačítka panelu nástrojů zapněte i do tlačítka zaškrtávací políčko. `SetCheck`přebírá parametr, který může být 0 (není zaškrtnuto), 1 (zaškrtnuto) nebo 2 (neurčitém)  
  
- `SetRadio`: Sdružená vlastnost pro `SetCheck`.  
  
 Zaškrtněte políčko tlačítka jsou tlačítka, zaškrtněte políčko "AUTO"; To znamená když uživatel stiskne je jejich okamžitě změní stav. Zaškrtnutí je vypnutý nebo stisknuté stavu. Neexistuje žádné integrované uživatelské rozhraní způsob, jak změnit tlačítko do stavu "neurčitém"; které je třeba provést prostřednictvím kódu.  
  
 Přizpůsobení rozhraní API vám umožní změnit stav tlačítka panelu nástrojů dané, ideálně by se měl změnit těchto stavů v `ON_UPDATE_COMMAND_UI` obslužné rutiny pro příkaz představuje tlačítka panelu nástrojů. Pamatujte si, že zpracování při nečinnosti se změní stav tlačítka panelu nástrojů s `ON_UPDATE_COMMAND_UI` obslužné rutiny, takže všechny změny na tyto stavy provedeny prostřednictvím SetButtonStyle může dojít ke ztrátě po další nečinnosti.  
  
 Tlačítka panelu nástrojů odešle **wm_command –** zprávy jako normální tlačítka nebo položek nabídky a jsou obvykle zpracovávány `ON_COMMAND` obslužné rutiny ve stejné třídě, která poskytuje `ON_UPDATE_COMMAND_UI` obslužné rutiny.  
  
 Existují čtyři nástrojů styly tlačítek (TBBS_ hodnoty) používá pro zobrazení stavů:  
  
-   TBBS_CHECKED: zaškrtávací políčko je zaškrtnuto aktuálně (dolů).  
  
-   TBBS_INDETERMINATE: zaškrtávací políčko je aktuálně neurčitou.  
  
-   TBBS_DISABLED: Tlačítko je aktuálně zakázaná.  
  
-   TBBS_PRESSED: Aktuálně stisknutí tlačítka.  
  
 Šest oficiální styly tlačítek Průvodce návrhem aplikace rozhraní systému Windows jsou reprezentované pomocí následujících hodnot TBBS:  
  
-   Až = 0  
  
-   Myš dolů = TBBS_PRESSED (&#124; žádný jiný styl)  
  
-   Zakázané = TBBS_DISABLED  
  
-   Dolů = TBBS_CHECKED  
  
-   Dolů zakázáno = TBBS_CHECKED &#124; TBBS_DISABLED  
  
-   Neurčitém = TBBS_INDETERMINATE  
  
##  <a name="_mfcnotes_cdialogbar"></a>CDialogBar  
 Panel dialogového okna je ovládací prvek panel, který obsahuje standardní ovládací prvky systému Windows. V, aby obsahuje ovládací prvky a podporuje použití tabulátoru mezi nimi, chová se jako dialogové okno. Je taky funguje jako dialogové okno v tom, že používá šablony dialogového okna představují panelu.  
  
 A `CDialogBar` slouží k náhledu nástrojů, který obsahuje standardní uzavření tlačítkem ovládací prvky.  
  
 Použití `CDialogBar` je podobné jako použití `CFormView`. Je nutné definovat šablony dialogového okna pro panel dialogového okna a odeberte všechny styly s výjimkou **ws_child –**. Všimněte si, že dialogu nesmí být viditelné.  
  
 Oznámení ovládacího prvku pro `CDialogBar` budou odeslány do nadřazené ovládacích pruhů (stejně jako tlačítka panelu nástrojů).  
  
## <a name="ccmdui-support-for-cdialogbar"></a>CCmdUI podpora CDialogBar  
 Tlačítka panelu dialogovém okně by měly být aktualizovány prostřednictvím `ON_UPDATE_COMMAND_UI` mechanismus obslužné rutiny. V době nečinnosti, bude volat panel dialogového okna `ON_UPDATE_COMMAND_UI` obslužná rutina s ID příkazu, který všechny tlačítka s Identifikátorem > = 0x8000 (který je v rozsahu identifikátory příkazů).  
  
 `ON_UPDATE_COMMAND_UI` Můžete volat obslužné rutiny:  
  
-   Povolit: k povolení nebo zakázání tlačítko.  
  
-   SetText –: Chcete-li změnit text tlačítka.  
  
 Přizpůsobení lze provést pomocí Správce standardní okno rozhraní API.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

