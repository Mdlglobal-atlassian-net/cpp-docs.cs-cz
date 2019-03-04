---
title: AFX – zprávy
ms.date: 11/04/2016
f1_keywords:
- SB_LINELEFT
- SB_THUMBTRACK
- AFX_TOOLTIP_TYPE_EDIT
- AFX_WM_ON_HSCROLL
- SB_PAGERIGHT
- AFX_WM_RESETPROMPT
- AFX_WM_CHANGE_RIBBON_CATEGORY
- AFX_TOOLTIP_TYPE_MINIFRAME
- AFX_WM_CUSTOMIZETOOLBAR
- AFX_WM_CHANGE_ACTIVE_TAB
- AFX_WM_ACCGETOBJECT
- AFX_WM_TOOLBARMENU
- AFX_TOOLTIP_TYPE_DOCKBAR
- AFX_WM_CUSTOMIZEHELP
- AFX_WM_ON_GET_TAB_TOOLTIP
- AFX_WM_ON_RIBBON_CUSTOMIZE
- AFX_WM_ON_DRAGCOMPLETE
- AFX_WM_RESETTOOLBAR
- AFX_WM_ON_MOVETOTABGROUP
- AFX_WM_CHECKEMPTYMINIFRAME
- AFX_WM_GETDOCUMENTCOLORS
- SB_RIGHT
- AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU
- AFX_WM_ACCGETSTATE
- SB_PAGELEFT
- SB_ENDSCROLL
- AFX_WM_ON_CANCELTABMOVE
- AFX_TOOLTIP_TYPE_TAB
- AFX_WM_WINDOW_HELP
- AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM
- AFX_WM_SHOWREGULARMENU
- AFX_TOOLTIP_TYPE_TOOLBAR
- AFX_WM_CHANGE_CURRENT_FOLDER
- AFX_WM_UPDATETOOLTIPS
- AFX_WM_ON_MOVE_TAB
- AFX_WM_CHANGING_ACTIVE_TAB
- AFX_WM_RESETMENU
- AFX_WM_GETDRAGBOUNDS
- AFX_WM_RESETCONTEXTMENU
- AFX_TOOLTIP_TYPE_BUTTON
- AFX_WM_ON_CLOSEPOPUPWINDOW
- AFX_TOOLTIP_TYPE_TOOLBOX
- AFX_WM_CHANGEVISUALMANAGER
- SB_LINERIGHT
- AFX_WM_ON_RENAME_TAB
- AFX_TOOLTIP_TYPE_DEFAULT
- AFX_WM_ON_TABGROUPMOUSEMOVE
- SB_LEFT
- AFX_WM_DELETETOOLBAR
- AFX_WM_PROPERTY_CHANGED
- AFX_TOOLTIP_TYPE_ALL
- AFX_WM_ACCHITTEST
- AFX_WM_ON_AFTER_SHELL_COMMAND
- AFX_WM_ON_PRESS_CLOSE_BUTTON
- AFX_WM_RESETKEYBOARD
- AFX_WM_ON_MOVETABCOMPLETE
- AFX_WM_CREATETOOLBAR
- SB_THUMBPOSITION
- AFX_WM_POSTSETPREVIEWFRAME
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
ms.openlocfilehash: 5caf40fc757e2c5c90c06e1698ce4c15d1ed6240
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284733"
---
# <a name="afx-messages"></a>AFX – zprávy

Tyto zprávy se používají v knihovně MFC.

## <a name="messages"></a>Zprávy

V následující tabulce jsou uvedeny zprávy, které se používají v knihovně MFC:

||||||
|-|-|-|-|-|
|Zpráva|Popis|[in] *wParam*|*lParam* (všechny parametry jsou [in], pokud není uvedeno jinak.)|Návratová hodnota|
|AFX_WM_ACCGETOBJECT|Nepoužívá se.|Nepoužívá se.|Nelze použít.|Nelze použít.|
|AFX_WM_ACCGETSTATE|Používá se pro usnadnění přístupu. Odesílání této zprávy `CMFCPopupMenu` nebo `CMFCRibbonPanelMenu` načítání stavu aktuálního prvku.|Index prvku, který může být tlačítko nabídky nebo oddělovač.|Nepoužívá se.|Stav elementu. Index je neplatný, je -1, 0, pokud na tlačítko nabídky nemá žádné speciální atributy. V opačném případě je kombinací následujících příznaků:<br /><br /> TBBS_DISABLED – položka je zakázána.<br /><br /> TBBS_CHECKED – je položka zaškrtnuta<br /><br /> TBBS_BUTTON – položka je standardní pushbutton<br /><br /> TBBS_PRESSED – stisknutí tlačítka<br /><br /> TBBS_INDETERMINATE – nedefinovaný stav<br /><br /> TBBS_SEPARATOR - místo tlačítka nabídky, tento element formuláře a oddělení mezi dalšími položkami nabídky|
|AFX_WM_CHANGE_ACTIVE_TAB|Rozhraní pošle tuto zprávu do ovládacího prvku panel možností změny velikosti ovládacího prvku. Tuto zprávu pro příjem oznámení z `CMFCTabCtrl` objekty, když uživatel změní aktivní kartě.|Index karty.|Nepoužívá se.|Nenulovou hodnotu.|
|AFX_WM_CHANGE_CURRENT_FOLDER|Rozhraní pošle tuto zprávu nadřazený `CMFCShellListCtrl` když uživatel změnil do aktuální složky.|Nepoužívá se.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_CHANGEVISUALMANAGER|Rozhraní pošle tuto zprávu všech oken s rámečkem, když uživatel změní aktuální správce Visual. V reakci na tuto zprávu okno rámce přepočítá jeho oblast a upraví další parametry, podle potřeby. Pokud potřebujete, abyste dostávali oznámení o této události, může zpracovat zprávy AFX_WM_CHANGEVISUALMANAGER ve vaší aplikaci. Je nutné volat obslužnou rutinu základní třídy (`OnChangeVisualManager`) k zajištění, že rozhraní poškodilo vnitřní zpracování této události dojde.|Nepoužívá se.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_CHANGING_ACTIVE_TAB|Odesílat nadřazený `CMFCTabCtrl` objektu.  Tuto zprávu zpracovat, pokud chcete dostávat oznámení od `CMFCTabCtrl` objektů, pokud uživatel obnoví na kartě.|Index karty, která se aktivuje.|Nepoužívá se.|Nenulovou hodnotu.|
|AFX_WM_CHECKEMPTYMINIFRAME|Pouze pro interní použití.|Nelze použít.|Nelze použít.|Nelze použít.|
|AFX_WM_CREATETOOLBAR|Odeslaný `CMFCToolBarsListPropertyPage` když uživatel vytvoří nový panel nástrojů v průběhu vlastního nastavení. Vytvoření vlastní instance objektu odvozené cmfctoolbar – této zprávy může zpracovat. Pokud tuto zprávu zpracovat a vytvořit vlastní panel nástrojů, vynechejte volání výchozí obslužnou rutinu.|Nepoužívá se.|Ukazatel na řetězec, který obsahuje název panelu nástrojů.|Ukazatel na nově vytvořený panel nástrojů. NULL znamená, že byla zrušena vytvoření panelu nástrojů.|
|AFX_WM_CUSTOMIZEHELP|Odeslané do okna hlavního rámce z vlastností přizpůsobení `CMFCToolbarCustomize Dialog` když uživatel stiskne klávesu **pomáhají** tlačítko nebo klávesy F1.|Určuje aktivní stránka vlastností vlastního nastavení.|Ukazatel `CMFCToolbarCustomize Dialog` objektu.|Nula.|
|AFX_WM_CUSTOMIZETOOLBAR|`CMFCToolbarCustomize Dialog` Pošle tuto zprávu upozornění nadřazeného rámce, že uživatel vytváří nový panel nástrojů.|Hodnota TRUE, při přizpůsobení spuštění, FALSE po dokončení úprav.|Nepoužívá se.|Nula.|
|AFX_WM_DELETETOOLBAR|Odesílá se do okna hlavního rámce, když je uživatel Chystáte se odstranit panel nástrojů v režimu vlastního nastavení.<br /><br /> Zpracování této zprávy provést další akce, když uživatel odstraní panelu nástrojů v režimu úprav. Měli byste také zavolat výchozí obslužnou rutinu (`OnToolbarDelete`), která odstraňuje panelu nástrojů. Výchozí obslužná rutina vrací hodnotu určující, zda je možné odstranit panel nástrojů.|Nepoužívá se.|Ukazatel `CMFCToolBar` objektu, která se má odstranit.|Nenulové, pokud nelze odstranit panel nástrojů. jinak 0.|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton` pošle tuto zprávu do okna hlavního rámce načíst barvy dokumentu.|Nepoužívá se.|[out v] Ukazatel `CList<COLORREF, COLORREF>` objektu.|Nula.|
|AFX_WM_GETDRAGBOUNDS|Pouze pro interní použití.|Nelze použít.|Nelze použít.|Nelze použít.|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Odesílá se do okna hlavního rámce, když uživatel označuje položku seznamu pásu karet.|Index zvýrazněné položky|Ukazatel na `CMFCBaseRibbonElement`|Nepoužívá se.|
|AFX_WM_ON_AFTER_SHELL_COMMAND|Odeslání do nadřízeného objektu `CMFCShellListCtrl` nebo `CMFCShellTreeCtrl` řídí, kdy uživatel dokončí provádění příkazu prostředí.|ID příkazu, který uživatel provést|Nepoužívá se.|Pokud se aplikace zpracuje tuto zprávu, měla by vrátit nula.|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|Rozhraní pošle tuto zprávu nadřazené na pásu karet předtím, než se zobrazí v místní nabídce. Můžete tuto zprávu zpracovat a kdykoli upravit místní nabídky.|Nepoužívá se.|Ukazatel na `CMFCBaseRibbonElement`|Nepoužívá se.|
|AFX_WM_ON_CANCELTABMOVE|Pouze pro interní použití.|Nelze použít.|Nelze použít.||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|Rozhraní pošle tuto zprávu hlavního rámce, když uživatel změní aktivní ovládací prvek pásu karet kategorie.|Nepoužívá se.|Ukazatel `CMFCRibbonBar` došlo ke změně jehož kategorie.|Nepoužívá se.|
|AFX_WM_ON_CLOSEPOPUPWINDOW|Rozhraní pošle tuto zprávu oznámit vlastníkovi `CMFCDesktopAlertWnd` , že je okno bude uzavřen.|Nepoužívá se.|Ukazatel na `CMFCDesktopAlertWnd` objektu.|Nepoužívá se.|
|AFX_WM_ON_DRAGCOMPLETE|Pouze pro interní použití.|Nelze použít.|Nelze použít.|Nelze použít.|
|AFX_WM_ON_GET_TAB_TOOLTIP|Odesílá se do okna hlavního rámce, když okno s kartou se chystá zobrazení popisu tlačítka pro kartu, pokud jsou povolené vlastní popisky.|Nepoužívá se.|Ukazatel `CMFCTabToolTipInfo` struktury.|Nepoužívá se.|
|AFX_WM_ON_HSCROLL|Odeslání do ovládacího prvku panel možností změny velikosti ovládacího prvku. Tuto zprávu pro příjem oznámení z `CMFCTabCtrl` objekty při výskytu události posouvání v záložkách widgetu vodorovný posuvník.|Nižší řád slova Určuje hodnotu posuvníku panelu, který označuje, že uživatel je posouvání požadavku.  Další informace najdete v tabulce dále v tomto tématu.|Nepoužívá se.|Nenulovou hodnotu.|
|AFX_WM_ON_MOVE_TAB|Odesílá do nadřazeného okna s kartami, když uživatel přetáhne na kartě na jiné místo.|Index založený na nule kartu z jeho původní pozice.|[out] Index založený na nule kartu na nové pozici.|Nula.|
|AFX_WM_ON_MOVETABCOMPLETE|Pouze pro interní použití.|Nelze použít.|Nelze použít.|Nelze použít.|
|AFX_WM_ON_MOVETOTABGROUP|Odesílá se do okna hlavního rámce, když uživatel přesune podřízené okno MDI z jedné skupiny s kartami na jiný.|Popisovač okna s kartami (`CMFCTabCtrl`) ze které byla odebrána podřízené okno MDI.|[out] Popisovač okna s kartami (`CMFCTabCtrl`) na která byla vložena podřízené okno MDI.|Ignorovat.|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Odeslání do nadřízeného objektu `CDockablePane` když uživatel klikne **Zavřít** tlačítko na titulek ovládacím panelu.|Nepoužívá se.|Ukazatel na ukotvitelné podokno, ve kterém uživatel kliknul **Zavřít** tlačítko.|Hodnota TRUE, pokud nelze zavřít podokno; v opačném případě FALSE.|
|AFX_WM_ON_RENAME_TAB|Po přejmenování uživatel upravovat kartu, odešle do nadřazeného okna s kartami.|Index založený na nule přejmenováno kartu.|[out] Ukazatel na řetězec, který obsahuje název nové karty.|Nenulové, pokud aplikace zpracuje této zprávy. rozhraní framework potlačí volání `CMFCBaseTabCtrl::SetTabLabel`.  Pokud je vrácena nula, pak `CMFCBaseTabCtrl::SetTabLabel` je voláno rozhraním.|
|AFX_WM_ON_RIBBON_CUSTOMIZE|Odesílá se do nadřazeného rámce, když uživatel spustí vlastní nastavení. Tuto zprávu zpracovat, pokud chcete zobrazit dialogové okno Vlastní přizpůsobení.|Nepoužívá se.|Ukazatel na ovládací prvek pásu karet k přizpůsobení.|Nenulové, pokud aplikace zpracovává tuto zprávu a zobrazí jeho vlastní dialogového okna vlastního nastavení. Pokud aplikace vrátí hodnotu 0, rozhraní se zobrazí dialogové okno integrované přizpůsobení.|
|AFX_WM_ON_TABGROUPMOUSEMOVE|Pouze pro interní použití.|Nelze použít.|Nelze použít.|Nelze použít.|
|AFX_WM_POSTSETPREVIEWFRAME|Odesílat oznámení hlavního rámce, že uživatel změnil režim náhledu tisku.|Hodnota TRUE označuje, zda je režim náhledu tisku nastaven. Hodnota FALSE označuje, že tento režim náhledu tisku je vypnutý.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_PROPERTY_CHANGED|Odesílá se vlastníkovi ovládací prvek mřížky vlastností (`CMFCPropertyGridCtrl`) když uživatel změní hodnotu vybrané vlastnosti.|ID ovládacího prvku seznamu vlastností.|Ukazatel na vlastnosti (`CMFCPropertyGridProperty`), která se změnila.|Nepoužívá se.|
|AFX_WM_RESETCONTEXTMENU|Odesílá se do okna hlavního rámce, když uživatel během přizpůsobování obnoví v místní nabídce.|ID prostředku v místní nabídce.|Ukazatel na aktuální místní nabídce `CMFCPopupMenu`.|Nepoužívá se.|
|AFX_WM_RESETKEYBOARD|Pokud uživatel obnoví všechny klávesové zkratky během přizpůsobování rozhraní pošle tuto zprávu do okna hlavního rámce.|Nepoužívá se.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_RESETMENU|Rozhraní pošle tuto zprávu vlastníkovi nabídky (okno rámce) Pokud uživatel obnoví rámec nabídky aplikace během přizpůsobování|ID nabídky prostředku.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_RESETPROMPT|Rozhraní pošle tuto zprávu při dialogové okno vlastní uživatel obnoví a nástrojů na panelu nástrojů. Výchozí obslužnou rutinu se zobrazí okno se zprávou s dotazem, jestli uživatel chce obnovit panelu nástrojů.|Nepoužívá se.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_RESETTOOLBAR|A `CMFCToolBar` objekt pošle tuto zprávu na panelu nástrojů po obnovení do původního stavu, tedy načtené z prostředků. Tuto zprávu znovu vložit tlačítka panelu nástrojů, jejichž třídy jsou odvozeny z `CMFCToolbarButton`. Další informace naleznete v tématu `CMFCToolbarComboBoxButton`.|ID prostředku nástrojů, jehož stav byl obnoven.|Nepoužívá se.|Nula.|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton` objekt pošle tuto zprávu její vlastník, když uživatel klikne na tlačítko nabídky regulárních. Pokaždé, když použijete tuto zprávu zpracovat `CMFCToolbarMenuButton` k zobrazení místní nabídky, když uživatel klikne na tlačítko.|Identifikátor příkazu tlačítka, která odesílá zprávy.|Souřadnice obrazovky kurzoru. Nižší řád slova Určuje souřadnici x. Vyšší řád slova Určuje souřadnici y.|Nepoužívá se.|
|AFX_WM_TOOLBARMENU|Odesílá se do okna hlavního rámce, když uživatel uvolní pravé tlačítko myši, zatímco ukazatel myši v klienta nebo neklientská oblast na stavového řádku.|Nepoužívá se.|Souřadnice obrazovky ukazatele myši. Nižší řád slova Určuje souřadnici x. Vyšší řád slova Určuje souřadnici y.|Nula v případě aplikace zpracovává této zprávy. v opačném případě nenulovou hodnotu.|
|AFX_WM_UPDATETOOLTIPS|Odeslat všichni vlastníci popisek k označení, že jejich ovládacích prvků tooltip znovu vytvořit.|Typ ovládacího prvku, který by měl zpracovat tuto zprávu. V tabulce dále v tomto tématu pro seznam možných hodnot.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog` pošle tuto zprávu nadřazeného rámce, když uživatel klikne **pomáhají** tlačítko nebo přejde do režimu nápovědy kliknutím **pomáhají** titulek tlačítka nebo klávesy F1.|Nepoužívá se.|Ukazatel na instanci `CMFCWindowsManagerDialog`.|Nepoužívá se.|

V následující tabulce jsou uvedeny hodnot dolní slovo *lParam* parametr AFX_WM_HSCROLL metody:

|||
|-|-|
|Hodnota|Význam|
|SB_ENDSCROLL|Uživatel končí posuvníku.|
|SB_LEFT|Uživatel přesune do levé horní části.|
|SB_RIGHT|Uživatel přesune do pravého dolního.|
|SB_LINELEFT|Uživatel posune doleva o jednu jednotku.|
|SB_LINERIGHT|Uživatel posune doprava o jednu jednotku.|
|SB_PAGELEFT|Uživatel posune doleva o šířku okna.|
|SB_PAGERIGHT|Uživatel posune doprava o šířku okna.|
|SB_THUMBPOSITION|Uživatel má kvůli usnadnění použití vypsány posuvníku (palce) a vydání tlačítko myši. Vyšší řád slova označuje pozice posuvníku na konci operace přetažení.|
|SB_THUMBTRACK|Uživatel přetahuje posuvníku. Zpráva AFX_WM_ON_HSCROLL se pošle opakovaně s touto hodnotou, dokud uživatel uvolní tlačítko myši. Vyšší řád slova označuje pozici, která byla přetažena posuvníku.|

> [!NOTE]
>  Vyšší řád slova *lParam* parametr určuje aktuální pozice posuvníku, pokud je nižší řád slova SB_THUMBPOSITION nebo SB_THUMBTRACK; v opačném případě se nepoužívá toto slovo.

V následující tabulce jsou uvedeny hodnoty příznak *lParam* parametr AFX_WM_UPDATETOOLTIPS zprávy:

|||
|-|-|
|Příznak|Hodnota|
|AFX_TOOLTIP_TYPE_DEFAULT|0x0001|
|AFX_TOOLTIP_TYPE_TOOLBAR|0x0002|
|AFX_TOOLTIP_TYPE_TAB|0x0004|
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|
|AFX_TOOLTIP_TYPE_EDIT|0x0020|
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|
|AFX_TOOLTIP_TYPE_TOOLBOX|0x0080|
|AFX_TOOLTIP_TYPE_ALL|0xFFFF|

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
