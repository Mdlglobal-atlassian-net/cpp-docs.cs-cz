---
title: 'TN031: Ovládací pruhy | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls.bars
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6744b4c5ea2da1f572ad721f980f719bb9b25af8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952999"
---
# <a name="tn031-control-bars"></a>TN031: Ovládací pruhy
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje třídy panelu ovládacích prvků v prostředí MFC: Obecné [ccontrolbar –](#_mfcnotes_ccontrolbar), [cstatusbar –](#_mfcnotes_cstatusbar), [ctoolbar –](#_mfcnotes_ctoolbar), [CDialogBar](#_mfcnotes_cdialogbar)a `CDockBar`.  
  
## <a name="_mfcnotes_ccontrolbar"></a> Ccontrolbar – 
  
 A `ControlBar` je `CWnd`-odvozené třídy, který:  
  
-   Je zarovnán do pravého horního nebo dolního okně s rámečkem.  
  
-   Může obsahovat podřízené položky, které jsou buď ovládací prvky založené na HWND (například `CDialogBar`) nebo jiných-`HWND` na základě položky (například `CToolBar`, `CStatusBar`).  
  
 Ovládací pruhy podporují další styly:  
  
- PIN kód CBRS_TOP (výchozí) na panelu Ovládací prvek na začátek.  
  
- PIN kód CBRS_BOTTOM ovládacích pruhů dolů.  
  
- Provést CBRS_NOALIGN není přemístit ovládacích pruhů a když nadřazený změní.  
  
 Třídy odvozené od `CControlBar` poskytovat zajímavějšího implementace:  
  
- `CStatusBar` Stavový řádek položky jsou podokna panelu Stav obsahující text.  
  
- `CToolBar` Panelu nástrojů položky jsou rastrového obrázku tlačítka zarovnán v řádku.  
  
- `CDialogBar` Rámeček panelu nástrojů jako obsahující standardní windows ovládacích prvků (vytvořené z prostředku šablony dialogové okno).  
  
- `CDockBar` Zobecněný ukotvení oblasti pro ostatní `CControlBar` odvozené objekty. Konkrétní členské funkce a proměnné, které jsou k dispozici v této třídě jsou pravděpodobně v budoucích verzích změnit.  
  
 Všechny ovládací prvek panelu objekty nebo windows bude podřízená okna některé nadřazeného rámce okna. Jsou obvykle přidávána na stejné úrovni jako klientské oblasti rámečku (například klienta MDI nebo zobrazení). ID podřízené okno ovládacích pruhů je důležité. Výchozí rozložení ovládacích pruhů funguje výhradně u ovládací pruhy s ID v rozsahu AFX_IDW_CONTROLBAR_FIRST k AFX_IDW_CONTROLBAR_LAST. Všimněte si, že i když je rozsah 256 ovládacího panelu ID, první 32 tyto ovládací prvek panelu ID jsou speciální vzhledem k tomu, že jsou přímo nepodporuje architektura náhledu tisku.  
  
 `CControlBar` Třída poskytuje standardní implementace pro:  
  
-   Zarovnání ovládacích pruhů na nahoru, dolů nebo obou stranách rámečku.  
  
-   Přidělování řízení položky pole.  
  
-   Podpora implementace odvozené třídy.  
  
 Objekty C++ ovládací prvek panelu obvykle budou vloženy jako členy `CFrameWnd` odvozené třídy a kdy se vyčistí nadřazený `HWND` a jsou zničení objektu. Pokud potřebujete přidělit objekt ovládací prvek panelu v haldě, můžete jednoduše nastavit *m_bAutoDestruct* člena **TRUE** aby ovládacích pruhů "**odstranit tento**" při `HWND` zničena.  
  
> [!NOTE]
>  Pokud vytvoříte vlastní `CControlBar`-odvozené třídy, nikoli pomocí jedné z knihovny MFC odvozených tříd, jako například `CStatusBar`, `CToolBar`, nebo `CDialogBar`, budete muset nastavit *m_dwStyle* – datový člen. To lze provést v přepsané `Create`:  
  
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
  
 Algoritmus rozložení ovládacího prvku panel je velmi jednoduchý. Okně s rámečkem odešle zprávu WM_SIZEPARENT na všechny podřízené objekty v rozsahu ovládací prvek panelu. Společně se tato zpráva je předán ukazatel na obdélníku klienta nadřazeného objektu. Tato zpráva je odeslána podřízených objektů v pořadí Z-order. Tyto informace použít podřízených ovládacích pruhů samy stanovují a snížení velikosti nadřazeného klientské oblasti. Konečné obdélníku, který se nechá oblasti normální klienta (méně ovládací pruhy) se používá k umístění okna Hlavní klienta (obvykle klienta, zobrazení nebo rozdělovače okna MDI).  
  
 V tématu `CWnd::RepositionBars` a `CFrameWnd::RecalcLayout` další podrobnosti.  
  
 MFC privátní Windows zprávy, včetně WM_SIZEPARENT, jsou popsané v [Technická poznámka 24](../mfc/tn024-mfc-defined-messages-and-resources.md).  
  
## <a name="_mfcnotes_cstatusbar"></a>  Cstatusbar –  
  
 Stavový řádek je ovládací prvek panel, který má řádek podokna výstup textu. Existují dvě běžné způsoby použití podokna výstup textu:  
  
-   Jako řádek zprávy  
  
     (například standardní nabídky Nápověda řádek zprávy). Tyto jsou obvykle dostupné přes 0 – na základě indexované  
  
-   Jako indikátory stavu  
  
     (například Zakončení, počtu a SCRL indikátory). Tyto jsou obvykle dostupné přes ID řetězec nebo příkazu.  
  
 Písmo pro stavový řádek je bod 10 MS Sans Serif (závisí na Průvodce návrhem aplikace rozhraní Windows nebo nejlepší shodu písma mappers 10 bodů Švýcarskou přímo úměrná písma). V různých verzích systému Windows, jako je například japonské verzi písem vybrané se liší.  
  
 Barvy použité ve stavovém řádku jsou také konzistentní s doporučení příručce pro návrh aplikace rozhraní Windows. Tyto barvy nejsou pevně zakódovanou a jsou dynamicky změnily v reakci na uživatele přizpůsobení v Ovládacích panelech.  
  
|Položka|Hodnota barvy systému Windows|Výchozí RGB|  
|----------|-------------------------|-----------------|  
|Stav pozadí panelu|COLOR_BTNFACE|RGB (192, 192 192.)|  
|Text stavového řádku|COLOR_BTNTEXT|RGB (000, 000 000.)|  
|Stavový řádek levého horního okraje|COLOR_BTNHIGHLIGHT|RGB (255, 255 255.)|  
|Stavový řádek robota/pravého okraje|COLOR_BTNSHADOW|RGB (128, 128, 128)|  
  
 **Cstatusbar – podpora CCmdUI**  
  
 Způsob, jakým jsou obvykle aktualizovány indikátory je přes mechanismus on_update_command_ui –. Na dobu nečinnosti zavolá na stavovém řádku on_update_command_ui – obslužná rutina s ID řetězec podokně indikátoru.  
  
 On_update_command_ui – obslužná rutina můžete volat:  
  
- `Enable`: Chcete-li povolit nebo zakázat v podokně. Zakázané podokně vypadá přesně povoleno podokně ale text je neviditelné (tedy vypne indikátor text).  
  
- `SetText`: Chcete-li změnit text. Dávejte pozor, pokud to použít, protože v podokně se automaticky nezmění.  
  
 Odkazovat třídy [cstatusbar –](../mfc/reference/cstatusbar-class.md) v *knihovny tříd* podrobnosti o `CStatusBar` vytváření a přizpůsobení rozhraní API. Většina přizpůsobení stavových řádků se má provést před stavový řádek původně jsou dostupná.  
  
 Stavový řádek podporuje pouze jeden pružně roztáhnout podokno, obvykle první. Velikost tohoto panelu je skutečně minimální velikost. Pokud stavový řádek je větší, než je minimální velikost všech podoken, bude mu udělená žádné další šířka do podokna pružně roztáhnout. Vzhledem k tomu, že se první podokno pružně roztáhnout má výchozí aplikace s stavového řádku zarovnaný doprava indikátory Zakončení, počtu a SCRL.  
  
## <a name="_mfcnotes_ctoolbar"></a>  Ctoolbar –  
  
 Panel nástrojů je ovládací prvek panel s řádek rastrový obrázek tlačítka, která může obsahovat oddělovače. Podporují se dva styly tlačítek: tlačítek a tlačítka, zaškrtněte políčko. Funkce skupiny přepínačů mohou být vytvořeny políčko tlačítka a on_update_command_ui –.  
  
 Tlačítka rastrového obrázku na panelu nástrojů jsou převzaty z jedné bitové mapy. Tento rastrový obrázek musí obsahovat jednu bitovou kopii nebo glyfů pro každé tlačítko. Pořadí bitové kopie nebo glyfů v souboru bitové mapy je obvykle stejné pořadí, ve kterém se budou vykreslovat na obrazovce. (Toto můžete změnit pomocí přizpůsobení rozhraní API.)  
  
 Každé tlačítko musí mít stejnou velikost. Výchozí hodnota je standardní 24 × 22 pixelů. Každý image glyfy musí mít stejnou velikost a musí být vedle sebe v souboru bitové mapy. Výchozí velikost bitové kopie nebo glyfy je 16 x 15 pixelů. Proto pro panel nástrojů s 10 tlačítka (pomocí standardní velikosti), budete potřebovat rastrového obrázku, který je 160 pixelů a 15 pixelů.  
  
 Každé tlačítko má pouze jeden obrázek nebo glyfů. Tlačítko různé stavy a styly (například stisknutí tlačítka nahoru, dolů, zakázat, zakázané dolů, neurčitém) algorithmically generují z jedné bitové kopie nebo glyfů. Teoreticky lze použít všechny bitové mapy barvu nebo DIB. Pokud původní bitové kopie je odstínech šedi, algoritmus pro generování tlačítko různé stavy funguje nejlépe. Podívejte se na standardním panelu nástrojů tlačítka a clipart tlačítka panelu nástrojů, který je zadaný v ukázce MFC Obecné [CLIPART](../visual-cpp-samples.md) příklady.  
  
 Barvy používané v panelu nástrojů jsou také konzistentní s doporučení příručce pro návrh aplikace rozhraní Windows. Tyto barvy nejsou pevně zakódovanou a jsou dynamicky změnily v reakci na uživatele přizpůsobení v Ovládacích panelech.  
  
|Položka|Hodnota barvy systému Windows|Výchozí RGB|  
|----------|-------------------------|-----------------|  
|Pozadí panelu nástrojů|COLOR_BTNFACE|RGB(192,192,192)|  
|Tlačítka panelu nástrojů levého horního okraje|COLOR_BTNHIGHLIGHT|RGB(255,255,255)|  
|Tlačítka panelu nástrojů robota/pravého okraje|COLOR_BTNSHADOW|RGB(128,128,128)|  
  
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
 Přes mechanismus on_update_command_ui – je způsob, jakým jsou vždy aktualizovány tlačítka panelu nástrojů. Na dobu nečinnosti zavolá panelu nástrojů on_update_command_ui – obslužná rutina s ID příkazu, který tohoto tlačítka. On_update_command_ui – není volána pro oddělovače, ale je volána pro tlačítek a tlačítka, zaškrtněte políčko.  
  
 On_update_command_ui – obslužná rutina můžete volat:  
  
- `Enable`: Chcete-li povolit nebo zakázat tlačítko. Tento postup funguje stejně pro tlačítek a tlačítka, zaškrtněte políčko.  
  
- `SetCheck`: Chcete-li nastavení kontroly stavu tlačítko. Toto volání pro tlačítka panelu nástrojů zapněte i do tlačítka zaškrtávací políčko. `SetCheck` přebírá parametr, který může být 0 (není zaškrtnuto), 1 (zaškrtnuto) nebo 2 (neurčitém)  
  
- `SetRadio`: Sdružená vlastnost pro `SetCheck`.  
  
 Zaškrtněte políčko tlačítka jsou tlačítka, zaškrtněte políčko "AUTO"; To znamená když uživatel stiskne je jejich okamžitě změní stav. Zaškrtnutí je vypnutý nebo stisknuté stavu. Neexistuje žádné integrované uživatelské rozhraní způsob, jak změnit tlačítko do stavu "neurčitém"; které je třeba provést prostřednictvím kódu.  
  
 Přizpůsobení rozhraní API vám umožní změnit stav tlačítka panelu nástrojů dané, ideálně by se měl změnit těchto stavů v on_update_command_ui – obslužná rutina pro příkaz, který představuje tlačítka panelu nástrojů. Pamatujte si, že zpracování při nečinnosti se změní stav tlačítka panelu nástrojů s on_update_command_ui – obslužná rutina, tak všechny změny na tyto stavy provedeny prostřednictvím SetButtonStyle může dojít ke ztrátě po další nečinnosti.  
  
 Tlačítka panelu nástrojů odešle wm_command – zprávy jako normální tlačítka nebo položek nabídky a jsou obvykle zpracováván obslužnou rutinou on_command – ve stejné třídě, která poskytuje on_update_command_ui – obslužná rutina.  
  
 Existují čtyři nástrojů styly tlačítek (TBBS_ hodnoty) používá pro zobrazení stavů:  
  
-   TBBS_CHECKED: zaškrtávací políčko je zaškrtnuto aktuálně (dolů).  
  
-   TBBS_INDETERMINATE: zaškrtávací políčko je aktuálně neurčitou.  
  
-   TBBS_DISABLED: Tlačítko je aktuálně zakázaná.  
  
-   TBBS_PRESSED: Aktuálně stisknutí tlačítka.  
  
 Šest oficiální styly tlačítek Průvodce návrhem aplikace rozhraní systému Windows jsou reprezentované pomocí následujících hodnot TBBS:  
  
-   Až = 0  
  
-   Myš dolů = TBBS_PRESSED (&#124; jiný styl)  
  
-   Zakázané = TBBS_DISABLED  
  
-   Dolů = TBBS_CHECKED  
  
-   Dolů zakázáno = TBBS_CHECKED &#124; TBBS_DISABLED  
  
-   Neurčitém = TBBS_INDETERMINATE  
  
##  <a name="_mfcnotes_cdialogbar"></a> CDialogBar  
 Panel dialogového okna je ovládací prvek panel, který obsahuje standardní ovládací prvky systému Windows. V, aby obsahuje ovládací prvky a podporuje použití tabulátoru mezi nimi, chová se jako dialogové okno. Je taky funguje jako dialogové okno v tom, že používá šablony dialogového okna představují panelu.  
  
 A `CDialogBar` slouží k náhledu nástrojů, který obsahuje standardní uzavření tlačítkem ovládací prvky.  
  
 Použití `CDialogBar` je podobné jako použití `CFormView`. Musí definovat šablony dialogového okna pro panel dialogového okna a odeberte všechny kromě ws_child – styly. Všimněte si, že dialogu nesmí být viditelné.  
  
 Oznámení ovládacího prvku pro `CDialogBar` budou odeslány do nadřazené ovládacích pruhů (stejně jako tlačítka panelu nástrojů).  
  
## <a name="ccmdui-support-for-cdialogbar"></a>CCmdUI podpora CDialogBar  
 Dialogové okno tlačítek na panelu je třeba aktualizovat přes mechanismus on_update_command_ui – obslužná rutina. V době nečinnosti dialogového pruhu zavolá on_update_command_ui – obslužná rutina s ID příkazu, který všechny tlačítka s Identifikátorem > = 0x8000 (který je v rozsahu identifikátory příkazů).  
  
 On_update_command_ui – obslužná rutina můžete volat:  
  
-   Povolit: k povolení nebo zakázání tlačítko.  
  
-   SetText –: Chcete-li změnit text tlačítka.  
  
 Přizpůsobení lze provést pomocí Správce standardní okno rozhraní API.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

