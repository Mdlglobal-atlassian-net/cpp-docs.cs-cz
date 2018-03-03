---
title: "Afx – zprávy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 41f300f285fb4eaf1a6154a21cbbabc0253fc730
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="afx-messages"></a>AFX – zprávy
Tyto zprávy se používají v prostředí MFC.  
  
## <a name="messages"></a>Zprávy  
 Následující tabulka uvádí zprávy, které se používají v knihovně MFC:  
  
||||||  
|-|-|-|-|-|  
|Zpráva|Popis|[v]`wParam`|`lParam`(Všechny parametry jsou [v], pokud není uvedeno jinak.)|Návratová hodnota|  
|AFX_WM_ACCGETOBJECT|Nepoužívá se.|Nepoužívá se.|Nelze použít.|Nelze použít.|  
|AFX_WM_ACCGETSTATE|Použít pro usnadnění přístupu. Odeslat tuto zprávu `CMFCPopupMenu` nebo `CMFCRibbonPanelMenu` při načítání stavu aktuálního elementu.|Index elementu, který může být tlačítko nabídky nebo oddělovač.|Nepoužívá se.|Stav elementu. Je -1, pokud index není platný, 0, pokud tlačítko nabídky nemá žádné speciální atributy. V opačném případě je kombinací následující příznaky:<br /><br /> TBBS_DISABLED – položka je zakázána.<br /><br /> TBBS_CHECKED – položka je zaškrtnuté.<br /><br /> TBBS_BUTTON – položka je standardní pushbutton<br /><br /> TBBS_PRESSED – stisknutí tlačítka<br /><br /> TBBS_INDETERMINATE – nedefinované stavu<br /><br /> TBBS_SEPARATOR - místo tlačítka s nabídkou tento element formuláře a oddělení od jiných položek nabídky|  
|AFX_WM_CHANGE_ACTIVE_TAB|Rozhraní framework odešle zpráva do ovládacího prvku panel s možností změny velikosti ovládacího prvku. Tuto zprávu pro příjem oznámení z `CMFCTabCtrl` objekty, když uživatel změní aktivní karty.|Index na kartě.|Nepoužívá se.|Nenulové hodnoty.|  
|AFX_WM_CHANGE_CURRENT_FOLDER|Rozhraní framework odešle zpráva do nadřazeného `CMFCShellListCtrl` změny aktuální složce uživatele.|Nepoužívá se.|Nepoužívá se.|Nepoužívá se.|  
|AFX_WM_CHANGEVISUALMANAGER|Když uživatel změní aktuální správce Visual rozhraní odešle tuto zprávu do všech oken s rámečkem. V odpovědi na tuto zprávu oken s rámečkem přepočítá jeho oblasti a upraví další parametry, podle potřeby. Pokud potřebujete, abyste dostávali oznámení o této události, může zpracovat AFX_WM_CHANGEVISUALMANAGER zpráva v aplikaci. Je třeba volat základní třídu obslužné rutiny (`OnChangeVisualManager`) k zajištění, že je interní rozhraní probíhá zpracování této události.|Nepoužívá se.|Nepoužívá se.|Nepoužívá se.|  
|AFX_WM_CHANGING_ACTIVE_TAB|Posílá nadřazeného `CMFCTabCtrl` objektu.  Tuto zprávu zpracovat, pokud chcete dostávat oznámení od `CMFCTabCtrl` objekty, pokud uživatel resetuje na kartě.|Index kartu, která je aktivována.|Nepoužívá se.|Nenulové hodnoty.|  
|AFX_WM_CHECKEMPTYMINIFRAME|Pouze pro interní použití.|Nelze použít.|Nelze použít.|Nelze použít.|  
|AFX_WM_CREATETOOLBAR|Odeslaný `CMFCToolBarsListPropertyPage` když uživatel vytvoří nový panel nástrojů během procesu přizpůsobení. Tuto zprávu vytvořit instanci vlastního objektu odvozené CMFCToolBar může zpracovat. Pokud jste tuto zprávu zpracovat a vytvořit vlastní panely nástrojů, vynechejte volání výchozí obslužnou rutinu.|Nepoužívá se.|Ukazatel na řetězec, který obsahuje název panelu nástrojů.|Ukazatel na nově vytvořený panelu nástrojů. NULL označuje, že byla zrušena vytvoření panelu nástrojů.|  
|AFX_WM_CUSTOMIZEHELP|Do hlavního rámce okna odeslaný vlastností přizpůsobení `CMFCToolbarCustomize Dialog` uživatel stiskne **pomoci** tlačítko nebo klávesy F1.|Určuje aktivní stránku vlastností vlastního nastavení.|Ukazatel na `CMFCToolbarCustomize Dialog` objektu.|Nula.|  
|AFX_WM_CUSTOMIZETOOLBAR|`CMFCToolbarCustomize Dialog` Odešle tuto zprávu nadřazeného rámce upozornit, že uživatel vytváří nový panel nástrojů.|`TRUE`Při spuštění přizpůsobení `FALSE` dokončení vlastního nastavení.|Nepoužívá se.|Nula.|  
|AFX_WM_DELETETOOLBAR|Odeslat do hlavního rámce okna, pokud je uživatel Chystáte se odstranit panelu nástrojů v režimu vlastní nastavení.<br /><br /> Zpracování této zprávy provést další akce, když uživatel odstraní panelu nástrojů v režimu vlastní nastavení. Měli byste také zavolat výchozí obslužnou rutinu (`OnToolbarDelete`), která odstraňuje panelu nástrojů. Výchozí obslužná rutina vrátí hodnotu, která určuje, zda je možné odstranit panelu nástrojů.|Nepoužívá se.|Ukazatel na `CMFCToolBar` objekt, který má být odstraněna.|Nenulové hodnoty, pokud nelze odstranit, panelu nástrojů; jinak 0.|  
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton`Tato zpráva se odešle do hlavního rámce okno Načíst barvy dokumentu.|Nepoužívá se.|[ve out] Ukazatel na `CList<COLORREF, COLORREF>` objektu.|Nula.|  
|AFX_WM_GETDRAGBOUNDS|Pouze pro interní použití.|Nelze použít.|Nelze použít.|Nelze použít.|  
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Posílají do okna hlavního rámce, když uživatel zvýrazňuje pás karet položky seznamu.|Index zvýrazněné položky|Ukazatele na`CMFCBaseRibbonElement`|Nepoužívá se.|  
|AFX_WM_ON_AFTER_SHELL_COMMAND|Odeslány do nadřazené položky `CMFCShellListCtrl` nebo `CMFCShellTreeCtrl` prvky, když uživatel dokončí spouštění příkazů prostředí.|ID příkazu, který uživatel provést|Nepoužívá se.|Pokud aplikace zpracovává tuto zprávu, měla by vrátit nula.|  
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|Rozhraní framework odešle tato zpráva do nadřazené na pásu karet předtím, než se zobrazí v místní nabídce. Můžete tuto zprávu a kdykoli upravit místní nabídky.|Nepoužívá se.|Ukazatele na`CMFCBaseRibbonElement`|Nepoužívá se.|  
|AFX_WM_ON_CANCELTABMOVE|Pouze pro interní použití.|Nelze použít.|Nelze použít.||  
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|Rozhraní framework tuto zprávu odešle do hlavního rámce, když uživatel změní aktivní kategorie řízení pásu karet.|Nepoužívá se.|Ukazatel `CMFCRibbonBar` jejichž kategorie se změnila.|Nepoužívá se.|  
|AFX_WM_ON_CLOSEPOPUPWINDOW|Rozhraní framework odešle této zprávy s upozorněním vlastník `CMFCDesktopAlertWnd` , že je okno bude uzavřen.|Nepoužívá se.|Ukazatel na `CMFCDesktopAlertWnd` objektu.|Nepoužívá se.|  
|AFX_WM_ON_DRAGCOMPLETE|Pouze pro interní použití.|Nelze použít.|Nelze použít.|Nelze použít.|  
|AFX_WM_ON_GET_TAB_TOOLTIP|Odeslána do hlavního okna rámce, pokud okno s kartou o zobrazíte popisek pro kartě, pokud jsou povolené vlastní popisky.|Nepoužívá se.|Ukazatel na `CMFCTabToolTipInfo` struktury.|Nepoužívá se.|  
|AFX_WM_ON_HSCROLL|Odeslat do ovládacího prvku panel s možností změny velikosti ovládacího prvku. Tuto zprávu pro příjem oznámení z `CMFCTabCtrl` objekty při výskytu události přejděte v záložkách pomůcky vodorovného posuvníku.|Word nejnižší určuje posuvníku panelu hodnotu, která určuje uživatele je posouvání požadavku.  Další informace najdete v tabulce dál v tomto tématu.|Nepoužívá se.|Nenulové hodnoty.|  
|AFX_WM_ON_MOVE_TAB|Posílají do nadřazené okno s kartami, když uživatel nastavuje tažením na kartě do nového umístění.|Index založený na nule karty v původní pozici.|[out] Index založený na nule karty na nové pozici.|Nula.|  
|AFX_WM_ON_MOVETABCOMPLETE|Pouze pro interní použití.|Nelze použít.|Nelze použít.|Nelze použít.|  
|AFX_WM_ON_MOVETOTABGROUP|Posílají do okna hlavního rámce, když uživatel přesune podřízeného okna MDI z jedné skupiny s kartami na jiný.|Popisovač pro okno s kartami (`CMFCTabCtrl`) z které podřízeného okna MDI odebrána.|[out] Popisovač pro okno s kartami (`CMFCTabCtrl`) pro který byla vložena podřízeného okna MDI.|Ignorovat.|  
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Odeslány do nadřazené položky `CDockablePane` když uživatel klikne **Zavřít** na titulek panelu Ovládací prvek tlačítko.|Nepoužívá se.|Ukazatel na lze ukotvit podokně, na který uživatel klepl **Zavřít** tlačítko.|`TRUE`Pokud nelze zavřít, podokno; jinak hodnota FALSE.|  
|AFX_WM_ON_RENAME_TAB|Odesílá do nadřazené okno s kartami poté, co uživatel přejmenovat upravitelné kartě.|Index založený na nule přejmenovat karty.|[out] Ukazatel na řetězec, který obsahuje název nové kartě.|Nenulové hodnoty, pokud aplikace zpracovává této zprávy. rozhraní bude potlačit volání `CMFCBaseTabCtrl::SetTabLabel`.  Pokud bude vrácena nula, pak `CMFCBaseTabCtrl::SetTabLabel` volá rozhraní.|  
|AFX_WM_ON_RIBBON_CUSTOMIZE|Když uživatel spustí přizpůsobení posílá nadřazeného rámce. Tuto zprávu zpracovat, pokud chcete zobrazit dialogové okno Vlastní přizpůsobení.|Nepoužívá se.|Ukazatel na pásu karet ovládací prvek k přizpůsobení.|Nenulové hodnoty, pokud aplikace zpracovává tuto zprávu a zobrazí dialogové okno Vlastní přizpůsobení. Pokud aplikace vrátí hodnotu 0, rozhraní se zobrazí dialogové okno integrované přizpůsobení.|  
|AFX_WM_ON_TABGROUPMOUSEMOVE|Pouze pro interní použití.|Nelze použít.|Nelze použít.|Nelze použít.|  
|AFX_WM_POSTSETPREVIEWFRAME|Odeslat oznámení hlavního rámce, že uživatel změnit režim náhledu tisku|`TRUE`Označuje, že má nastaven režim náhledu tisku. `FALSE`Označuje, že tento režim náhledu je vypnutý.|Nepoužívá se.|Nepoužívá se.|  
|AFX_WM_PROPERTY_CHANGED|Odešle vlastníkovi ovládacího prvku mřížky vlastnosti (`CMFCPropertyGridCtrl`) když uživatel změní hodnotu vybrané vlastnosti.|ID ovládacího prvku seznam vlastností.|Ukazatel na vlastnosti (`CMFCPropertyGridProperty`), změnit.|Nepoužívá se.|  
|AFX_WM_RESETCONTEXTMENU|Pokud uživatel resetuje v místní nabídce během přizpůsobování posílá hlavního okna rámce.|ID prostředku v místní nabídce.|Ukazatel na místní nabídky aktuální `CMFCPopupMenu`.|Nepoužívá se.|  
|AFX_WM_RESETKEYBOARD|Pokud uživatel resetuje všechny klávesové zkratky během přizpůsobování rozhraní odešle tuto zprávu do hlavního rámce okna.|Nepoužívá se.|Nepoužívá se.|Nepoužívá se.|  
|AFX_WM_RESETMENU|Rozhraní framework odešle vlastníkovi nabídky (okně s rámečkem) Tato zpráva při uživatele resetuje nabídky rámce aplikace během přizpůsobování|ID nabídky prostředku.|Nepoužívá se.|Nepoužívá se.|  
|AFX_WM_RESETPROMPT|Rozhraní framework odešle tuto zprávu, když dialogové okno Vlastní nastavení uživatele a panelu nástrojů na panelu nástrojů. Výchozí obslužnou rutinu zobrazí okno s dotazem, jestli uživatel chce resetovat panelu nástrojů.|Nepoužívá se.|Nepoužívá se.|Nepoužívá se.|  
|AFX_WM_RESETTOOLBAR|A `CMFCToolBar` objekt odešle tuto zprávu panelu nástrojů po obnovení do původního stavu, který je načten z prostředků. Tuto zprávu znovu vložit tlačítka panelu nástrojů, jejichž třídy jsou odvozené od `CMFCToolbarButton`. Další informace naleznete v tématu `CMFCToolbarComboBoxButton`.|ID prostředku nástrojů, jejichž stav byla obnovena.|Nepoužívá se.|Nula.|  
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton`Po kliknutí na tlačítko regulární nabídky objekt odešle tuto zprávu jeho vlastníka. Tuto zprávu zpracovat pokaždé, když používáte `CMFCToolbarMenuButton` zobrazíte místní nabídky, když uživatel klikne na tlačítko.|ID příkazu tlačítka, které odešle zprávu.|Souřadnice obrazovky kurzoru. Word nejnižší Určuje souřadnici x. Horní slovo Určuje souřadnici y.|Nepoužívá se.|  
|AFX_WM_TOOLBARMENU|Když uživatel uvolní pravé tlačítko myši, když ukazatel myši klienta nebo neklientská oblast podokno, odeslána do hlavního rámce okna.|Nepoužívá se.|Souřadnice obrazovky ukazatele myši. Word nejnižší Určuje souřadnici x. Horní slovo Určuje souřadnici y.|Nula, pokud aplikace zpracovává této zprávy. v opačném případě nenulové hodnoty.|  
|AFX_WM_UPDATETOOLTIPS|Odesílané vlastníkům všech popisek k označení, že jejich popiskách znovu vytvořit.|Typ ovládacího prvku, který by měl zpracovat tuto zprávu. Najdete v tabulce dál v tomto tématu pro seznamu možných hodnot.|Nepoužívá se.|Nepoužívá se.|  
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog`Odešle tuto zprávu do nadřazeného rámce, když uživatel klikne **pomoci** tlačítko nebo přejde do režimu nápovědy kliknutím **pomoci** popisek tlačítka nebo klávesy F1.|Nepoužívá se.|Ukazatel na instanci `CMFCWindowsManagerDialog`.|Nepoužívá se.|  
  
 V následující tabulce jsou uvedeny hodnoty pro dolní slovo `lParam` parametru metody AFX_WM_HSCROLL:  
  
|||  
|-|-|  
|Hodnota|Význam|  
|SB_ENDSCROLL|Uživatel končí posuvníku.|  
|SB_LEFT|Uživatel posune vlevo nahoře.|  
|SB_RIGHT|Uživatel posune dolní.|  
|SB_LINELEFT|Uživatel posune doleva o jednu jednotku.|  
|SB_LINERIGHT|Uživatel posune doprava o jednu jednotku.|  
|SB_PAGELEFT|Uživatel posune doleva o šířku okna.|  
|SB_PAGERIGHT|Uživatel posune doprava o šířku okna.|  
|SB_THUMBPOSITION|Uživatel má přetáhnout posouvací políčko (Flash) a vydání tlačítko myši. Word horní označuje pozici jezdce na konci operace přetažení.|  
|SB_THUMBTRACK|Uživatel je přetahování jezdce. AFX_WM_ON_HSCROLL odeslání zprávy jsou opakovaně s touto hodnotou dokud uživatel uvolní tlačítko myši. Word horní označuje pozici, na kterou byla přetáhnout posouvací políčko.|  
  
> [!NOTE]
>  Word horní z `lParam` parametr určuje aktuální pozici posouvací políčko, pokud je slovo nejnižší SB_THUMBPOSITION nebo SB_THUMBTRACK; jinak se nepoužije slovo.  
  
 V následující tabulce jsou uvedeny hodnoty příznak `lParam` parametr AFX_WM_UPDATETOOLTIPS zprávy:  
  
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
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
