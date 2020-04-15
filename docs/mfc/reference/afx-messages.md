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
ms.openlocfilehash: b4ed86c11d3c5b5f1ce38e3146533109f3a6b00d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363601"
---
# <a name="afx-messages"></a>AFX – zprávy

Tyto zprávy se používají v knihovně MFC.

## <a name="messages"></a>Zprávy

V následující tabulce jsou uvedeny zprávy, které se používají v knihovně knihovny Knihovny MFC:

||||||
|-|-|-|-|-|
|Zpráva|Popis|[v] *wParam*|*lParam* (Všechny parametry jsou [in], pokud není uvedeno jinak.)|Návratová hodnota|
|AFX_WM_ACCGETOBJECT|Nepoužívá se.|Nepoužívá se.|Neužívá se.|Neužívá se.|
|AFX_WM_ACCGETSTATE|Používá se pro podporu usnadnění přístupu. Odešlete `CMFCPopupMenu` tuto `CMFCRibbonPanelMenu` zprávu nebo načíst stav aktuálního prvku.|Index prvku, který může být tlačítko nabídky nebo oddělovač.|Nepoužívá se.|Stav prvku. Je -1, pokud je index neplatný, 0, pokud tlačítko nabídky nemá žádné speciální atributy. V opačném případě se jedná o kombinaci následujících příznaků:<br /><br /> TBBS_DISABLED – položka je zakázána.<br /><br /> TBBS_CHECKED — položka je kontrolována<br /><br /> TBBS_BUTTON — položka je standardní tlačítko<br /><br /> TBBS_PRESSED — stisknuto tlačítko<br /><br /> TBBS_INDETERMINATE – nedefinovaný stav<br /><br /> TBBS_SEPARATOR - tento prvek místo tlačítka nabídky tvoří oddělení mezi ostatními položkami nabídky|
|AFX_WM_CHANGE_ACTIVE_TAB|Rozhraní framework odešle tuto zprávu ovládacímu prvku ovládacího panelu s nastavitelnou přesnou cítění. Zpracovat tuto zprávu pro `CMFCTabCtrl` příjem oznámení z objektů, když uživatel změní aktivní kartu.|Index karty.|Nepoužívá se.|Nenulová.|
|AFX_WM_CHANGE_CURRENT_FOLDER|Rozhraní Framework odešle tuto `CMFCShellListCtrl` zprávu nadřazené při změně aktuální složky uživatele.|Nepoužívá se.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_CHANGEVISUALMANAGER|Rozhraní Framework odešle tuto zprávu do všech oken rámce, když uživatel změní aktuální Visual Manager. V reakci na tuto zprávu okno rámce přepočítá svou oblast a podle potřeby upraví další parametry. Pokud potřebujete být na tuto událost upozorněni, můžete AFX_WM_CHANGEVISUALMANAGER zprávu v aplikaci. Musíte volat obslužnou rutinu základní třídy (`OnChangeVisualManager`) a zajistit tak, aby došlo k internímu zpracování této události v rámci.|Nepoužívá se.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_CHANGING_ACTIVE_TAB|Odesláno nadřazenému objektu. `CMFCTabCtrl`  Zpracujte tuto zprávu, pokud `CMFCTabCtrl` chcete dostávat oznámení z objektů, když uživatel obnoví kartu.|Index karty, která je aktivována.|Nepoužívá se.|Nenulová.|
|AFX_WM_CHECKEMPTYMINIFRAME|Pouze pro interní použití.|Neužívá se.|Neužívá se.|Neužívá se.|
|AFX_WM_CREATETOOLBAR|Odesláno `CMFCToolBarsListPropertyPage` z doby, kdy uživatel vytvoří nový panel nástrojů během procesu vlastního nastavení. Tuto zprávu můžete zpracovat k vytvoření instance vlastního objektu odvozeného cmfctoolbar. Pokud zpracováváte tuto zprávu a vytvoříte vlastní panel nástrojů, vynechejte volání výchozí obslužné rutiny.|Nepoužívá se.|Ukazatel na řetězec, který obsahuje název panelu nástrojů.|Ukazatel na nově vytvořený panel nástrojů. Hodnota NULL označuje, že vytvoření panelu nástrojů bylo zrušeno.|
|AFX_WM_CUSTOMIZEHELP|Odesláno do okna hlavního rámce `CMFCToolbarCustomize Dialog` z vlastního listu vlastností, když uživatel stiskne tlačítko **nápovědy** nebo klávesu F1.|Určuje aktivní stránku seznamu vlastností vlastního nastavení.|Ukazatel na `CMFCToolbarCustomize Dialog` objekt.|0|
|AFX_WM_CUSTOMIZETOOLBAR|Odešle `CMFCToolbarCustomize Dialog` tuto zprávu upozornit nadřazený rámec, že uživatel vytváří nový panel nástrojů.|TRUE při spuštění vlastního nastavení, NEPRAVDA po dokončení vlastního nastavení.|Nepoužívá se.|0|
|AFX_WM_DELETETOOLBAR|Odesláno do okna hlavního rámce, když se uživatel chystá odstranit panel nástrojů v režimu vlastního nastavení.<br /><br /> Zpracujte tuto zprávu tak, aby byla přijata další akce, když uživatel odstraní panel nástrojů v režimu vlastního nastavení. Měli byste také zavolat`OnToolbarDelete`výchozí obslužnou rutinu ( ), která odstraní panel nástrojů. Výchozí obslužná rutina vrátí hodnotu, která označuje, zda je možné odstranit panel nástrojů.|Nepoužívá se.|Ukazatel na `CMFCToolBar` objekt, který má být odstraněn.|Nenulová, pokud panel nástrojů nelze odstranit; jinak 0.|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton`odešle tuto zprávu do okna hlavního rámce, aby načetla barvy dokumentu.|Nepoužívá se.|[dovnitř, ven] Ukazatel na `CList<COLORREF, COLORREF>` objekt.|0|
|AFX_WM_GETDRAGBOUNDS|Pouze pro interní použití.|Neužívá se.|Neužívá se.|Neužívá se.|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Odesláno do okna hlavního rámce, když uživatel zvýrazní položku seznamu pásu karet.|Index zvýrazněné položky|Ukazatel na`CMFCBaseRibbonElement`|Nepoužívá se.|
|AFX_WM_ON_AFTER_SHELL_COMMAND|Odesláno nadřazené nebo `CMFCShellListCtrl` `CMFCShellTreeCtrl` ovládací prvky, když uživatel dokončí provádění příkazu prostředí.|ID příkazu, který uživatel provedl|Nepoužívá se.|Pokud aplikace zpracuje tuto zprávu, měla by vrátit nulu.|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|Rozhraní Framework odešle tuto zprávu nadřazené mu na pásu karet před zobrazením rozbalovací nabídky. Tuto zprávu můžete kdykoli zpracovat a upravit rozbalovací nabídky.|Nepoužívá se.|Ukazatel na`CMFCBaseRibbonElement`|Nepoužívá se.|
|AFX_WM_ON_CANCELTABMOVE|Pouze pro interní použití.|Neužívá se.|Neužívá se.||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|Rozhraní Framework odešle tuto zprávu do hlavního rámce, když uživatel změní aktivní kategorii ovládacího prvku pásu karet.|Nepoužívá se.|Ukazatel na `CMFCRibbonBar` jehož kategorii se změnila.|Nepoužívá se.|
|AFX_WM_ON_CLOSEPOPUPWINDOW|Rozhraní framework odešle tuto zprávu `CMFCDesktopAlertWnd` upozornit vlastníka, že okno se chystá zavřít.|Nepoužívá se.|Ukazatel na `CMFCDesktopAlertWnd` objekt.|Nepoužívá se.|
|AFX_WM_ON_DRAGCOMPLETE|Pouze pro interní použití.|Neužívá se.|Neužívá se.|Neužívá se.|
|AFX_WM_ON_GET_TAB_TOOLTIP|Pokud jsou povoleny vlastní popisky, odešle se do okna hlavního rámce, když se okno karty chystá zobrazit popisek pro kartu.|Nepoužívá se.|Ukazatel na `CMFCTabToolTipInfo` strukturu.|Nepoužívá se.|
|AFX_WM_ON_HSCROLL|Odesláno ovládacímu panelu s nastavitelnou přesnou shodou. Zpracovat tuto zprávu pro `CMFCTabCtrl` příjem oznámení z objektů, když dojde k události posouvání v vodorovném posuvníku widgetu s kartami.|Slovo nižšího řádu určuje hodnotu posuvníku, která označuje požadavek uživatele na posouvání.  Další informace naleznete v tabulce dále v tomto tématu.|Nepoužívá se.|Nenulová.|
|AFX_WM_ON_MOVE_TAB|Odesláno nadřazenému oknu s kartami, když uživatel přetáhne kartu na novou pozici.|Nulový index karty v původní poloze.|[out] Nula index karty v nové pozici.|0|
|AFX_WM_ON_MOVETABCOMPLETE|Pouze pro interní použití.|Neužívá se.|Neužívá se.|Neužívá se.|
|AFX_WM_ON_MOVETOTABGROUP|Odesláno do okna hlavního rámce, když uživatel přesune podřízené okno MDI z jedné skupiny s kartami do jiného.|Úchyt do`CMFCTabCtrl`okna s kartami ( ), ze kterého bylo odebráno podřízené okno MDI.|[out] Úchyt do`CMFCTabCtrl`okna s kartami ( ), do kterého bylo vloženo podřízené okno MDI.|Ignorovány.|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Odesláno nadřazené straně, `CDockablePane` když uživatel klepne na tlačítko **Zavřít** na titulku ovládacího panelu.|Nepoužívá se.|Ukazatel na dokovatelné podokno, na které uživatel klepnul na tlačítko **Zavřít.**|PRAVDA, pokud podokno nelze zavřít; jinak FALSE.|
|AFX_WM_ON_RENAME_TAB|Odesláno do nadřazeného okna s kartami poté, co uživatel přejmenoval upravitelnou kartu.|Nulový index přejmenované karty.|[out] Ukazatel na řetězec, který obsahuje nový název karty.|Nenulová, pokud aplikace zpracovává tuto zprávu; rámec potlačí volání `CMFCBaseTabCtrl::SetTabLabel`.  Pokud je vrácena `CMFCBaseTabCtrl::SetTabLabel` nula, pak je volána rámci.|
|AFX_WM_ON_RIBBON_CUSTOMIZE|Odesláno do nadřazeného rámce při spuštění vlastního nastavení uživatelem. Tuto zprávu zpracujte, pokud chcete zobrazit vlastní dialogové okno vlastního nastavení.|Nepoužívá se.|Ukazatel na ovládací prvek pásu karet, který má být přizpůsoben.|Nenulová, pokud aplikace zpracuje tuto zprávu a zobrazí vlastní dialogové okno vlastního nastavení. Pokud aplikace vrátí nulu, rozhraní se zobrazí v estavěné dialogové okno přizpůsobení.|
|AFX_WM_ON_TABGROUPMOUSEMOVE|Pouze pro interní použití.|Neužívá se.|Neužívá se.|Neužívá se.|
|AFX_WM_POSTSETPREVIEWFRAME|Odesláno s upozorněním hlavního rámce, že uživatel změnil režim náhledu tisku|TRUE označuje, že je nastaven režim náhledu tisku. NEPRAVDA označuje, že režim náhledu tisku je vypnutý.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_PROPERTY_CHANGED|Odesláno vlastníkovi ovládacího prvku`CMFCPropertyGridCtrl`mřížky vlastnosti ( ) při změně hodnoty vybrané vlastnosti uživatelem.|ID ovládacího prvku seznamu vlastností.|Ukazatel na vlastnost`CMFCPropertyGridProperty`( ), která se změnila.|Nepoužívá se.|
|AFX_WM_RESETCONTEXTMENU|Odesláno do okna hlavního rámce, když uživatel obnoví místní nabídku během vlastního nastavení.|ID prostředku kontextové nabídky.|Ukazatel na aktuální místní `CMFCPopupMenu`nabídku .|Nepoužívá se.|
|AFX_WM_RESETKEYBOARD|Rozhraní Framework odešle tuto zprávu do okna hlavního rámce, když uživatel resetuje všechny akcelerátory klávesnice během vlastního nastavení.|Nepoužívá se.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_RESETMENU|Rozhraní Framework odešle tuto zprávu vlastníkovi nabídky (okno rámce), když uživatel během vlastního nastavení obnoví nabídku rámce aplikace|ID prostředku nabídky.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_RESETPROMPT|Rozhraní Framework odešle tuto zprávu, když uživatel resetuje panel nástrojů z dialogového okna přizpůsobení panelu nástrojů. Výchozí obslužná rutina zobrazí okno se zprávou, zda chce uživatel obnovit panel nástrojů.|Nepoužívá se.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_RESETTOOLBAR|Objekt `CMFCToolBar` odešle tuto zprávu při obnovení panelu nástrojů do původního stavu, to znamená načtenz prostředků. Zpracovat tuto zprávu znovu vložit tlačítka panelu `CMFCToolbarButton`nástrojů, jejichž třídy jsou odvozeny od . Další informace naleznete v tématu `CMFCToolbarComboBoxButton`.|ID prostředku panelu nástrojů, jehož stav byl obnoven.|Nepoužívá se.|0|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton`objekt odešle tuto zprávu svému vlastníkovi, když uživatel klepne na tlačítko pravidelné nabídky. Zpracujte tuto zprávu `CMFCToolbarMenuButton` pokaždé, když použijete k zobrazení rozbalovací nabídky, když uživatel klepne na tlačítko.|ID příkazu tlačítka, které odešle zprávu.|Souřadnice obrazovky kurzoru. Slovo nižšího řádu určuje souřadnice x. Slovo nejvyššího řádu určuje souřadnici y.|Nepoužívá se.|
|AFX_WM_TOOLBARMENU|Odesláno do okna hlavního rámce, když uživatel uvolní pravé tlačítko myši, zatímco ukazatel myši je v klientské nebo neklientské oblasti podokna.|Nepoužívá se.|Souřadnice obrazovky ukazatele myši. Slovo nižšího řádu určuje souřadnice x. Slovo nejvyššího řádu určuje souřadnici y.|Nula, pokud aplikace zpracuje tuto zprávu; jinak nenulová.|
|AFX_WM_UPDATETOOLTIPS|Odesláno všem vlastníkům popisů, které označují, že jejich ovládací prvky popisů by měly být znovu vytvořeny.|Typ ovládacího prvku, který by měl zpracovat tuto zprávu. Seznam možných hodnot naleznete v tabulce dále v tomto tématu.|Nepoužívá se.|Nepoužívá se.|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog`Odešle tuto zprávu do nadřazeného rámce, když uživatel klepne na tlačítko **Nápověda** nebo přejde do režimu nápovědy klepnutím na tlačítko titulek **nápovědy** nebo klávesu F1.|Nepoužívá se.|Ukazatel na instanci . `CMFCWindowsManagerDialog`|Nepoužívá se.|

V následující tabulce jsou uvedeny hodnoty nízkého slova parametru *lParam* metody AFX_WM_HSCROLL:

|||
|-|-|
|Hodnota|Význam|
|SB_ENDSCROLL|Uživatel ukončí posun.|
|SB_LEFT|Uživatel posune na levé horní.|
|SB_RIGHT|Uživatel posune do pravédolní části.|
|SB_LINELEFT|Uživatel posouvá doleva o jednu jednotku.|
|SB_LINERIGHT|Uživatel se posouvá doprava o jednu jednotku.|
|SB_PAGELEFT|Uživatel posouvá vlevo šířku okna.|
|SB_PAGERIGHT|Uživatel posune vpravo podle šířky okna.|
|SB_THUMBPOSITION|Uživatel přetáhl posuvník (palec) a uvolnil tlačítko myši. Slovo vyššího řádu označuje pozici posuvníku na konci operace přetažení.|
|SB_THUMBTRACK|Uživatel přetahuje posuvník. Zpráva AFX_WM_ON_HSCROLL je odeslána opakovaně s touto hodnotou, dokud uživatel neuvolní tlačítko myši. Slovo vyššího řádu označuje pozici, do které bylo přetaženo posuvníku.|

> [!NOTE]
> Slovo nejvyššího řádu parametru *lParam* určuje aktuální pozici posuvníku, pokud je slovo nižšího řádu SB_THUMBPOSITION nebo SB_THUMBTRACK; v opačném případě se toto slovo nepoužívá.

V následující tabulce jsou uvedeny hodnoty příznaku pro parametr *lParam* zprávy AFX_WM_UPDATETOOLTIPS:

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

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
