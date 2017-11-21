---
title: "Cmenu – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMenu
- AFXWIN/CMenu
- AFXWIN/CMenu::CMenu
- AFXWIN/CMenu::AppendMenu
- AFXWIN/CMenu::Attach
- AFXWIN/CMenu::CheckMenuItem
- AFXWIN/CMenu::CheckMenuRadioItem
- AFXWIN/CMenu::CreateMenu
- AFXWIN/CMenu::CreatePopupMenu
- AFXWIN/CMenu::DeleteMenu
- AFXWIN/CMenu::DeleteTempMap
- AFXWIN/CMenu::DestroyMenu
- AFXWIN/CMenu::Detach
- AFXWIN/CMenu::DrawItem
- AFXWIN/CMenu::EnableMenuItem
- AFXWIN/CMenu::FromHandle
- AFXWIN/CMenu::GetDefaultItem
- AFXWIN/CMenu::GetMenuContextHelpId
- AFXWIN/CMenu::GetMenuInfo
- AFXWIN/CMenu::GetMenuItemCount
- AFXWIN/CMenu::GetMenuItemID
- AFXWIN/CMenu::GetMenuItemInfo
- AFXWIN/CMenu::GetMenuState
- AFXWIN/CMenu::GetMenuString
- AFXWIN/CMenu::GetSafeHmenu
- AFXWIN/CMenu::GetSubMenu
- AFXWIN/CMenu::InsertMenu
- AFXWIN/CMenu::InsertMenuItem
- AFXWIN/CMenu::LoadMenu
- AFXWIN/CMenu::LoadMenuIndirect
- AFXWIN/CMenu::MeasureItem
- AFXWIN/CMenu::ModifyMenu
- AFXWIN/CMenu::RemoveMenu
- AFXWIN/CMenu::SetDefaultItem
- AFXWIN/CMenu::SetMenuContextHelpId
- AFXWIN/CMenu::SetMenuInfo
- AFXWIN/CMenu::SetMenuItemBitmaps
- AFXWIN/CMenu::SetMenuItemInfo
- AFXWIN/CMenu::TrackPopupMenu
- AFXWIN/CMenu::TrackPopupMenuEx
- AFXWIN/CMenu::m_hMenu
dev_langs: C++
helpviewer_keywords:
- CMenu [MFC], CMenu
- CMenu [MFC], AppendMenu
- CMenu [MFC], Attach
- CMenu [MFC], CheckMenuItem
- CMenu [MFC], CheckMenuRadioItem
- CMenu [MFC], CreateMenu
- CMenu [MFC], CreatePopupMenu
- CMenu [MFC], DeleteMenu
- CMenu [MFC], DeleteTempMap
- CMenu [MFC], DestroyMenu
- CMenu [MFC], Detach
- CMenu [MFC], DrawItem
- CMenu [MFC], EnableMenuItem
- CMenu [MFC], FromHandle
- CMenu [MFC], GetDefaultItem
- CMenu [MFC], GetMenuContextHelpId
- CMenu [MFC], GetMenuInfo
- CMenu [MFC], GetMenuItemCount
- CMenu [MFC], GetMenuItemID
- CMenu [MFC], GetMenuItemInfo
- CMenu [MFC], GetMenuState
- CMenu [MFC], GetMenuString
- CMenu [MFC], GetSafeHmenu
- CMenu [MFC], GetSubMenu
- CMenu [MFC], InsertMenu
- CMenu [MFC], InsertMenuItem
- CMenu [MFC], LoadMenu
- CMenu [MFC], LoadMenuIndirect
- CMenu [MFC], MeasureItem
- CMenu [MFC], ModifyMenu
- CMenu [MFC], RemoveMenu
- CMenu [MFC], SetDefaultItem
- CMenu [MFC], SetMenuContextHelpId
- CMenu [MFC], SetMenuInfo
- CMenu [MFC], SetMenuItemBitmaps
- CMenu [MFC], SetMenuItemInfo
- CMenu [MFC], TrackPopupMenu
- CMenu [MFC], TrackPopupMenuEx
- CMenu [MFC], m_hMenu
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5b54a2cecf6ae091680582a3997cc8ee9c1c625d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmenu-class"></a>Cmenu – třída
Zapouzdření Windows `HMENU`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMenu : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMenu::CMenu](#cmenu)|Vytvoří `CMenu` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMenu::AppendMenu](#appendmenu)|Přidá novou položku na konec této nabídky.|  
|[CMenu::Attach](#attach)|Připojí popisovač nabídky systému Windows pro `CMenu` objektu.|  
|[CMenu::CheckMenuItem](#checkmenuitem)|Umístí zatržení vedle nebo odebere zaškrtnutí položky nabídky v místní nabídce.|  
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|Umístí přepínač vedle položky nabídky a odebere přepínač ze všech jiných položek nabídky ve skupině.|  
|[CMenu::CreateMenu](#createmenu)|Vytvoří prázdný nabídky a připojí jej k `CMenu` objektu.|  
|[CMenu::CreatePopupMenu](#createpopupmenu)|Vytvoří prázdný místní nabídky a připojí jej k `CMenu` objektu.|  
|[CMenu::DeleteMenu](#deletemenu)|Odstraní určenou položku z nabídky. Pokud má položka nabídky přidružené místní nabídky, zničí popisovač pro místní nabídky a uvolní paměť se používá.|  
|[CMenu::DeleteTempMap](#deletetempmap)|Odstraní všechny dočasné `CMenu` objekty vytvořené `FromHandle` – členská funkce.|  
|[CMenu::DestroyMenu](#destroymenu)|Zničí nabídky připojené k `CMenu` objektu a uvolní paměť v nabídce zaneprázdněn.|  
|[CMenu::Detach](#detach)|Umožňuje odpojit zpracování nabídky systému Windows z `CMenu` objektu a vrátí popisovač.|  
|[CMenu::DrawItem](#drawitem)|Voláno rámcem při visual aspektů nabídce vykreslovaných vlastníkem změny.|  
|[CMenu::EnableMenuItem](#enablemenuitem)|Povolí, zakáže nebo ztlumí (šedé) položku nabídky.|  
|[CMenu::FromHandle](#fromhandle)|Vrátí ukazatel na `CMenu` objekt daný popisovač nabídky systému Windows.|  
|[CMenu::GetDefaultItem](#getdefaultitem)|Určuje výchozí položku nabídky v nabídce zadaný.|  
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|Načte ID kontextové nápovědy přidružené k nabídce.|  
|[CMenu::GetMenuInfo](#getmenuinfo)|Načte informace o konkrétní nabídky.|  
|[CMenu::GetMenuItemCount](#getmenuitemcount)|Určuje počet položek v nabídce místní nebo nejvyšší úrovně.|  
|[CMenu::GetMenuItemID](#getmenuitemid)|Získá identifikátor položky nabídky pro položku nabídky na zadané pozici.|  
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|Načte informace o položku nabídky.|  
|[CMenu::GetMenuState](#getmenustate)|Vrátí stav zadaná položka nabídky nebo počet položek v místní nabídce.|  
|[CMenu::GetMenuString](#getmenustring)|Načte popisek zadaná položka nabídky.|  
|[CMenu::GetSafeHmenu](#getsafehmenu)|Vrátí `m_hMenu` zabalen to `CMenu` objektu.|  
|[CMenu::GetSubMenu](#getsubmenu)|Načte ukazatel na místní nabídky.|  
|[CMenu::InsertMenu](#insertmenu)|Vloží novou položku nabídky na zadané pozici, přesunutí dolů v nabídce Další položky.|  
|[CMenu::InsertMenuItem](#insertmenuitem)|Vloží novou položku nabídky na zadané pozici v nabídce.|  
|[CMenu::LoadMenu](#loadmenu)|Načte prostředek nabídky z spustitelný soubor a připojí jej k `CMenu` objektu.|  
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|Načte nabídky z nabídky šablony v paměti a připojí jej k `CMenu` objektu.|  
|[CMenu::MeasureItem](#measureitem)|Voláno rámcem pro určení dimenze nabídky, kdy je vytvořena vykreslovaných vlastníkem nabídky.|  
|[CMenu::ModifyMenu](#modifymenu)|Změní stávající položku nabídky na zadané pozici.|  
|[CMenu::RemoveMenu](#removemenu)|Vymaže položku nabídky s přidružené místní nabídky z nabídky zadaný.|  
|[CMenu::SetDefaultItem](#setdefaultitem)|Nastaví výchozí položku nabídky pro zadaný nabídky.|  
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|Nastaví ID kontextu nápovědy má být přidružen k nabídce.|  
|[CMenu::SetMenuInfo](#setmenuinfo)|Nastaví informace o konkrétní nabídky.|  
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|Přidruží zadané značky zaškrtnutí bitmap položku nabídky.|  
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|Změní informace o položku nabídky.|  
|[CMenu::TrackPopupMenu](#trackpopupmenu)|Zobrazí plovoucí místní nabídky v zadaném umístění a sleduje výběr položek v místní nabídce.|  
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|Zobrazí plovoucí místní nabídky v zadaném umístění a sleduje výběr položek v místní nabídce.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMenu::operator HMENU](#operator_hmenu)|Načte popisovač objektu nabídky.|  
|[CMenu::operator! =](#operator_neq)|Určuje, pokud dva objekty nabídky nejsou stejné.|  
|[CMenu::operator ==](#operator_eq_eq)|Určuje, jestli jsou dva objekty nabídky stejné.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMenu::m_hMenu](#m_hmenu)|Určuje popisovač do nabídky systému Windows, který je připojen k `CMenu` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Poskytuje členské funkce pro vytváření, sledování, aktualizaci a odstraňování nabídky.  
  
 Vytvoření `CMenu` objekt v rámci zásobníku jako místní, pak volání `CMenu`na členské funkce k manipulaci s nové nabídky podle potřeby. Pak zavolejte [CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu) lze nastavit v nabídce v časovém období, za nímž okamžitě voláním `CMenu` objektu [odpojení](#detach) – členská funkce. `CWnd::SetMenu` – Členská funkce nastaví nabídce okna pro nové nabídky, způsobí, že okno překreslit, aby odrážely změny nabídky a také předá vlastnictví v nabídce v okně. Volání **odpojení** odpojí `HMENU` z `CMenu` objektu, tak který po místní `CMenu` proměnná předává mimo rozsah, `CMenu` destruktoru objektu nebude pokoušet o zrušení nabídky ho žádné již vlastní. V nabídce sám automaticky zničena při okno zničena.  
  
 Můžete použít [LoadMenuIndirect](#loadmenuindirect) – členská funkce vytvořit nabídky ze šablony v paměti, ale nabídky vytvořené z prostředku voláním [LoadMenu](#loadmenu) je snazší údržbu a prostředek nabídky sám sebe můžete vytvořit a upravit pomocí editoru nabídky.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenu`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="appendmenu"></a>CMenu::AppendMenu  
 Přidá novou položku na konec nabídky.  
  
```  
BOOL AppendMenu(
    UINT nFlags,  
    UINT_PTR nIDNewItem = 0,  
    LPCTSTR lpszNewItem = NULL);

 
BOOL AppendMenu(
    UINT nFlags,  
    UINT_PTR nIDNewItem,  
    const CBitmap* pBmp);
```  
  
### <a name="parameters"></a>Parametry  
 `nFlags`  
 Určuje informace o stavu nové položky nabídky při jejím přidání do nabídky. Obsahuje jeden nebo více hodnot, které jsou uvedené v oddílu Poznámky.  
  
 `nIDNewItem`  
 Určuje ID příkazu nové položky nabídky nebo, pokud `nFlags` je nastaven na **MF_POPUP**, popisovač nabídky ( `HMENU`) z místní nabídky. `nIDNewItem` Parametr je ignorován (není potřeba), pokud `nFlags` je nastaven na **MF_SEPARATOR**.  
  
 `lpszNewItem`  
 Určuje obsah novou položku nabídky. `nFlags` Parametr se používá k interpretaci `lpszNewItem` následujícím způsobem:  
  
|nFlags|Výklad lpszNewItem|  
|------------|-----------------------------------|  
|`MF_OWNERDRAW`|Obsahuje hodnotu 32-bit zadané aplikace, který aplikace můžete použít ke správě další data přidružená k položce nabídky. Tato hodnota 32-bit je k dispozici pro aplikaci, když zpracovává `WM_MEASUREITEM` a `WM_DRAWITEM` zprávy. Hodnota je uložena v **itemData** členem strukturu součástí těchto zpráv.|  
|**MF_STRING**|Obsahuje ukazatel na řetězce ukončené hodnotou null. Toto je výchozí interpretaci.|  
|**MF_SEPARATOR**|`lpszNewItem` Parametr je ignorován (není potřeba).|  
  
 *pBmp*  
 Odkazuje na `CBitmap` objekt, který se použije jako položku nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace můžete určit stav položky nabídky nastavením hodnoty v `nFlags`. Když `nIDNewItem` Určuje místní nabídky, stane se součástí nabídky, ke kterému se připojuje. Pokud této nabídky zničení, budou také nabídce připojením zničena. Připojením nabídky musí odpojit od `CMenu` objekt, který chcete, aby nedošlo ke konfliktu. Všimněte si, že **MF_STRING** a `MF_OWNERDRAW` nejsou platné pro rastrový obrázek verzi `AppendMenu`.  
  
 Následující seznam popisuje příznaky, které lze nastavit v `nFlags`:  
  
- **MF_CHECKED** funguje jako přepínač s **MF_UNCHECKED** umístit výchozí zaškrtnutí vedle položky. Kdy aplikace poskytuje značky zaškrtnutí Bitmap (najdete v článku [SetMenuItemBitmaps](#setmenuitembitmaps) – členská funkce), se zobrazí rastrový obrázek "zaškrtnutí na".  
  
- **MF_UNCHECKED** funguje jako přepínač s **MF_CHECKED** zrušte zaškrtnutí vedle položky. Kdy aplikace poskytuje bitmap značky zaškrtnutí (najdete v článku `SetMenuItemBitmaps` – členská funkce), se zobrazí rastrový obrázek "zaškrtnutí vypnout".  
  
- **MF_DISABLED** zakáže položky nabídky, takže ji nelze vybrat, ale není dim.  
  
- `MF_ENABLED`Položky nabídky umožňuje, aby ho lze vybrat a obnoví z stav neaktivní.  
  
- **MF_GRAYED** zakáže položky nabídky tak, aby nelze vybrat a ztlumí ho.  
  
- **MF_MENUBARBREAK** umístí položku na nový řádek v nabídkách statické nebo v novém sloupci v místní nabídky. Nový sloupec místní nabídky budou ze staré sloupce odděleny svislou čarou rozdíl.  
  
- **MF_MENUBREAK** umístí položku na nový řádek v nabídkách statické nebo v novém sloupci v místní nabídky. Žádný rozdíl řádek je umístěn mezi sloupci.  
  
- `MF_OWNERDRAW`Určuje, že je položka položku vykreslování vlastníka. V případě, že v nabídce se zobrazí při prvním, obdrží okně, které vlastní nabídce `WM_MEASUREITEM` zprávu, která načte výška a šířka položky nabídky. `WM_DRAWITEM` Zpráva je odeslána vždy, když vlastník musíte aktualizovat vzhled položky nabídky. Tato možnost není platný pro položku nabídky nejvyšší úrovně.  
  
- **MF_POPUP** určí, že položky nabídky má místní nabídky s ním spojená. Parametr ID Určuje popisovač pro místní nabídky, které má být přidružená k položce. Používá se k přidání položky místní nabídky nejvyšší úrovně místní nabídky nebo hierarchické místní nabídky.  
  
- **MF_SEPARATOR** nevykresluje na vodorovném řádku rozdíl. Lze použít pouze v místní nabídce. Tento řádek nelze neaktivní, zakázán nebo zvýrazněná. Další parametry jsou ignorovány.  
  
- **MF_STRING** Určuje, že položky nabídky je řetězec znaků.  
  
 Každý z těchto skupin uvádí příznaky, které se vzájemně vylučují a nelze použít společně:  
  
- **MF_DISABLED**, `MF_ENABLED`, a **MF_GRAYED**  
  
- **MF_STRING**, `MF_OWNERDRAW`, **MF_SEPARATOR**a verze rastrového obrázku  
  
- **MF_MENUBARBREAK** a **MF_MENUBREAK**  
  
- **MF_CHECKED** a **MF_UNCHECKED**  
  
 Vždy, když nabídky, které nachází v okno změní (nebo zda se zobrazí okno), aplikace by měly volat [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::CreateMenu](#createmenu).  
  
##  <a name="attach"></a>CMenu::Attach  
 Připojí k existující nabídky systému Windows `CMenu` objektu.  
  
```  
BOOL Attach(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 `hMenu`  
 Určuje popisovač pro nabídky systému Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla operace úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci nelze volat, pokud nabídky je již připojen k `CMenu` objektu. Popisovač nabídky je uložen v `m_hMenu` – datový člen.  
  
 Pokud je už přidružená ke okno nabídky, kterou chcete upravit, můžete použít [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu) funkce získání popisovače do nabídky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="checkmenuitem"></a>CMenu::CheckMenuItem  
 Značky zaškrtnutí k přidá nebo odebere značky zaškrtnutí z položek nabídky v místní nabídce.  
  
```  
UINT CheckMenuItem(
    UINT nIDCheckItem,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDCheckItem`  
 Určuje položku nabídky ke kontrole, počítáno od `nCheck`.  
  
 `nCheck`  
 Určuje, jak zkontrolovat položku nabídky a jak určit umístění položky v nabídce. `nCheck` Parametr může být kombinací **MF_CHECKED** nebo **MF_UNCHECKED** s **MF_BYPOSITION** nebo **MF_BYCOMMAND** Příznaky. Tyto příznaky lze spojovat pomocí bitový operátor OR. Mají následující významy:  
  
- **MF_BYCOMMAND** Určuje, že parametr obsahuje ID příkazu, který existující položky nabídky. Toto nastavení je výchozí.  
  
- **MF_BYPOSITION** Určuje, že parametr dává pozici existující položky nabídky. První položka je na pozici 0.  
  
- **MF_CHECKED** funguje jako přepínač s **MF_UNCHECKED** umístit výchozí zaškrtnutí vedle položky.  
  
- **MF_UNCHECKED** funguje jako přepínač s **MF_CHECKED** zrušte zaškrtnutí vedle položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí stav položky: **MF_CHECKED** nebo **MF_UNCHECKED**, nebo 0xFFFFFFFF položky nabídky neexistovala.  
  
### <a name="remarks"></a>Poznámky  
 `nIDCheckItem` Parametr určuje položku, kterou chcete upravit.  
  
 `nIDCheckItem` Parametr mohou identifikovat položky místní nabídky, jakož i položku nabídky. Žádné speciální kroky jsou nutné k vyhledání položky místní nabídky. Nelze zkontrolovat, nabídek na nejvyšší úrovni. Položky místní nabídky musí být kontrolované umístěním, protože nemá identifikátor položky nabídky s ním spojená.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::GetMenuState](#getmenustate).  
  
##  <a name="checkmenuradioitem"></a>CMenu::CheckMenuRadioItem  
 Zkontroluje položku zadané nabídky a umožňuje položku přepínač.  
  
```  
BOOL CheckMenuRadioItem(
    UINT nIDFirst,  
    UINT nIDLast,  
    UINT nIDItem,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDFirst`  
 Určuje (jako ID nebo offset, v závislosti na hodnotě `nFlags`) ve skupině přepínacích tlačítek první položku.  
  
 `nIDLast`  
 Určuje (jako ID nebo offset, v závislosti na hodnotě `nFlags`) poslední položky nabídky ve skupině přepínacích tlačítek.  
  
 `nIDItem`  
 Určuje (jako ID nebo offset, v závislosti na hodnotě `nFlags`) položky ve skupině, která bude ověřena pomocí přepínače.  
  
 `nFlags`  
 Určuje interpretaci `nIDFirst`, `nIDLast`, a `nIDItem` následujícím způsobem:  
  
|nFlags|Interpretace|  
|------------|--------------------|  
|**MF_BYCOMMAND**|Určuje, že parametr obsahuje ID příkazu, který existující položky nabídky. Toto je výchozí, pokud **MF_BYCOMMAND** ani **MF_BYPOSITION** nastavena.|  
|**MF_BYPOSITION**|Určuje, že parametr dává pozici existující položky nabídky. První položka je na pozici 0.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0  
  
### <a name="remarks"></a>Poznámky  
 Funkce ve stejnou dobu, zruší tohoto systému zaškrtnutí všech ostatních položek nabídky v přidružené skupině a vymaže příznak přepínač položky typu pro tyto položky. Zaškrtnuté položky se zobrazí pomocí přepínačů tlačítko (nebo odrážka) rastrový obrázek místo rastrového obrázku značky zaškrtnutí.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [on_command_range –](message-map-macros-mfc.md#on_command_range).  
  
##  <a name="cmenu"></a>CMenu::CMenu  
 Vytvoří prázdný nabídky a připojí jej k `CMenu` objektu.  
  
```  
CMenu();
```  
  
### <a name="remarks"></a>Poznámky  
 V nabídce vytvořen až volání jednoho z členské funkce vytvořit nebo načíst z **cmenu –:**  
  
- [CreateMenu –](#createmenu)  
  
- [Createpopupmenu –](#createpopupmenu)  
  
- [LoadMenu](#loadmenu)  
  
- [LoadMenuIndirect](#loadmenuindirect)  
  
- [Připojení](#attach)  
  
##  <a name="createmenu"></a>CMenu::CreateMenu  
 Vytvoří z nabídky a připojí jej k `CMenu` objektu.  
  
```  
BOOL CreateMenu();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se v nabídce úspěšně; vytvořil jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 V nabídce je původně prázdné. Položky nabídky můžete přidat pomocí `AppendMenu` nebo `InsertMenu` – členská funkce.  
  
 Pokud v nabídce je přiřazen k okno, automaticky byla při okno zničena.  
  
 Před ukončením, musí aplikace uvolnit systémové prostředky, které jsou přidružené k nabídce Pokud v nabídce není přiřazen k okno. Aplikace uvolní nabídky voláním [DestroyMenu](#destroymenu) – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]  
  
##  <a name="createpopupmenu"></a>CMenu::CreatePopupMenu  
 Vytvoří místní nabídky a připojí jej k `CMenu` objektu.  
  
```  
BOOL CreatePopupMenu();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud v místní nabídce byl úspěšně vytvořen; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 V nabídce je původně prázdné. Položky nabídky můžete přidat pomocí `AppendMenu` nebo `InsertMenu` – členská funkce. Aplikace můžete přidat místní nabídky do existující nabídky nebo místní nabídky. `TrackPopupMenu` Člen funkci lze používat k zobrazení této nabídky jako plovoucí místní nabídky a sledovat výběr v místní nabídce.  
  
 Pokud v nabídce je přiřazen k okno, automaticky byla při okno zničena. Pokud je v nabídce Přidat do existující nabídky, automaticky byla při této nabídky zničena.  
  
 Před ukončením, musí aplikace uvolnit systémové prostředky, které jsou spojené s místní nabídky, pokud v nabídce není přiřazen k časového období. Aplikace uvolní nabídky voláním [DestroyMenu](#destroymenu) – členská funkce.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::CreateMenu](#createmenu).  
  
##  <a name="deletemenu"></a>CMenu::DeleteMenu  
 Vymaže položku v nabídce.  
  
```  
BOOL DeleteMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `nPosition`  
 Určuje položku nabídky, která má být odstraněn, počítáno od `nFlags`.  
  
 `nFlags`  
 Slouží k interpretaci `nPosition` následujícím způsobem:  
  
|nFlags|Výklad nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Určuje, že parametr obsahuje ID příkazu, který existující položky nabídky. Toto je výchozí, pokud **MF_BYCOMMAND** ani **MF_BYPOSITION** nastavena.|  
|**MF_BYPOSITION**|Určuje, že parametr dává pozici existující položky nabídky. První položka je na pozici 0.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud má položka nabídky přidružené místní nabídky, `DeleteMenu` zničí popisovač pro místní nabídky a uvolní množství paměti používané v místní nabídce.  
  
 Vždy, když nabídky, které nachází v okno změní (nebo zda se zobrazí okno), aplikace musí volat [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).  
  
##  <a name="deletetempmap"></a>CMenu::DeleteTempMap  
 Volá se automaticky `CWinApp` doby nečinnosti obslužnou rutinu, odstraní všechny dočasné `CMenu` objekty vytvořené [FromHandle](#fromhandle) – členská funkce.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>Poznámky  
 `DeleteTempMap`Umožňuje odpojit objekt nabídky systému Windows, který je připojen do dočasného `CMenu` objekt před odstraněním `CMenu` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]  
  
##  <a name="destroymenu"></a>CMenu::DestroyMenu  
 Zničí v nabídce a všechny prostředky systému Windows, které byly používány.  
  
```  
BOOL DestroyMenu();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud v nabídce zničeno; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 V nabídce odpojený od `CMenu` objektu předtím, než byla. Windows `DestroyMenu` funkce je automaticky volána `CMenu` destruktor.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::CreateMenu](#createmenu).  
  
##  <a name="detach"></a>CMenu::Detach  
 Umožňuje odpojit z nabídky systému Windows `CMenu` objektu a vrátí popisovač.  
  
```  
HMENU Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač typu `HMENU`, do nabídky systému Windows, pokud úspěšná, jinak hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 `m_hMenu` – Datový člen je nastaven na **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="drawitem"></a>CMenu::DrawItem  
 Voláno rámcem při visual aspektů nabídce vykreslovaných vlastníkem změny.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Ukazatel [drawitemstruct –](../../mfc/reference/drawitemstruct-structure.md) struktura, která obsahuje informace o typu kreslení vyžaduje.  
  
### <a name="remarks"></a>Poznámky  
 `itemAction` Členem `DRAWITEMSTRUCT` struktura definuje kreslení akci, která má být provedena. Člen funkci implementovat kreslení pro kreslení vlastníka přepsat `CMenu` objektu. Aplikace by měla obnovit všechny grafiky zařízení rozhraní GDI objekty vybrané pro zadaný kontext zobrazení v `lpDrawItemStruct` před ukončení této funkce člen.  
  
 V tématu [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) popis `DRAWITEMSTRUCT` struktura.  
  
### <a name="example"></a>Příklad  
 Následující kód je z knihovny MFC [CTRLTEST](../../visual-cpp-samples.md) ukázka:  
  
 [!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]  
  
##  <a name="enablemenuitem"></a>CMenu::EnableMenuItem  
 Povolí, zakáže nebo ztlumí položku nabídky.  
  
```  
UINT EnableMenuItem(
    UINT nIDEnableItem,  
    UINT nEnable);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDEnableItem*  
 Určuje položku nabídky, aby byl povolen, počítáno od `nEnable`. Tento parametr můžete zadat položky místní nabídky, jakož i standardních položek nabídky.  
  
 `nEnable`  
 Určuje akci, kterou trvat. Může být kombinací **MF_DISABLED**, `MF_ENABLED`, nebo **MF_GRAYED**, s **MF_BYCOMMAND** nebo **MF_BYPOSITION**. Tyto hodnoty lze spojovat pomocí bitový operátor OR. Tyto hodnoty mají následující významy:  
  
- **MF_BYCOMMAND** Určuje, že parametr obsahuje ID příkazu, který existující položky nabídky. Toto nastavení je výchozí.  
  
- **MF_BYPOSITION** Určuje, že parametr dává pozici existující položky nabídky. První položka je na pozici 0.  
  
- **MF_DISABLED** zakáže položky nabídky, takže ji nelze vybrat, ale není dim.  
  
- `MF_ENABLED`Položky nabídky umožňuje, aby ho lze vybrat a obnoví z stav neaktivní.  
  
- **MF_GRAYED** zakáže položky nabídky tak, aby nelze vybrat a ztlumí ho.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí stav ( **MF_DISABLED**, `MF_ENABLED`, nebo **MF_GRAYED**) nebo -1, pokud není platný.  
  
### <a name="remarks"></a>Poznámky  
 [CreateMenu –](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu), a [LoadMenuIndirect](#loadmenuindirect) členské funkce můžete také nastavit stav (povolené, zakázané nebo nedostupné) položky nabídky.  
  
 Pomocí **MF_BYPOSITION** hodnotu vyžaduje aplikaci k používání správných `CMenu`. Pokud `CMenu` nabídky panelu se používá, je ovlivněno nabídka nejvyšší úrovně (položku v panelu nabídek). Chcete-li nastavit stav položky v místní nebo vnořená místní nabídky umístěním, musíte zadat aplikaci `CMenu` z místní nabídky.  
  
 Určuje, kdy aplikace **MF_BYCOMMAND** příznak, systém Windows kontroluje všechny položky místní nabídky, které jsou podřízené `CMenu`; proto, pokud duplicitní položky nejsou přítomny, pomocí `CMenu` v nabídce panelu je dostatečná.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]  
  
##  <a name="fromhandle"></a>CMenu::FromHandle  
 Vrátí ukazatel na `CMenu` objekt daný popisovačů systému Windows k nabídce.  
  
```  
static CMenu* PASCAL FromHandle(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 `hMenu`  
 Popisovačů systému Windows k nabídce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CMenu` , může být v dočasné nebo trvalé.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CMenu` objekt není už připojený k objektu nabídky systému Windows, dočasného `CMenu` objekt se vytvoří a připojené.  
  
 Toto dočasný `CMenu` objektu je platná pouze až po příštím aplikace má čas nečinnosti v jeho událostí ve smyčce, po kterém se odstraní všechny dočasné objekty.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::CreateMenu](#createmenu).  
  
##  <a name="getdefaultitem"></a>CMenu::GetDefaultItem  
 Určuje výchozí položku nabídky v nabídce zadaný.  
  
```  
UINT GetDefaultItem(
    UINT gmdiFlags,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *gmdiFlags*  
 Hodnota, která určuje, jak funkce hledá položky nabídky. Tento parametr může být none, jeden nebo kombinace těchto hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|**GMDI_GOINTOPOPUPS**|Určuje, že, pokud výchozí položku, která otevře podnabídky, funkce je k vyhledání v odpovídající rekurzivně podnabídky. Pokud podnabídky žádné výchozí položku, identifikuje návratovou hodnotu položky, které se otevře podnabídky.<br /><br /> Ve výchozím nastavení funkce vrátí první výchozí položku v nabídce zadaný bez ohledu na to, zda je položka, která otevře podnabídky.|  
|**GMDI_USEDISABLED**|Určuje, že funkce je vrátit výchozí položku, i když je zakázán.<br /><br /> Ve výchozím nastavení přeskočí funkce zakázané nebo šedým položek.|  
  
 `fByPos`  
 Hodnota, která určuje, jestli se má načíst identifikátor položky nabídky nebo jeho umístění. Pokud tento parametr je **FALSE**, je vrácen identifikátor. Jinak vrátí se pozice.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu identifikátor nebo pozice položky nabídky. V případě selhání funkce návratová hodnota je - 1.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování funkce Win32 [GetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647976), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getmenucontexthelpid"></a>CMenu::GetMenuContextHelpId  
 Načte kontextovou nápovědu ID přidružené k `CMenu`.  
  
```  
DWORD GetMenuContextHelpId() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kontextovou nápovědu aktuálně přidružen ID `CMenu` pokud existuje; jinak hodnota nula.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getmenuinfo"></a>CMenu::GetMenuInfo  
 Načte informace pro nabídky.  
  
```  
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpcmi`  
 Ukazatel [MENUINFO](http://msdn.microsoft.com/library/windows/desktop/ms647575) struktura obsahující informace o nabídce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu nenulové; návratovou hodnotu, jinak hodnota rovná nule.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se načíst informace o nabídce.  
  
##  <a name="getmenuitemcount"></a>CMenu::GetMenuItemCount  
 Určuje počet položek v nabídce místní nebo nejvyšší úrovně.  
  
```  
UINT GetMenuItemCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v nabídce, je-li funkce úspěšně; jinak-1.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).  
  
##  <a name="getmenuitemid"></a>CMenu::GetMenuItemID  
 Získá identifikátor položky nabídky pro položku nabídky na pozici definované `nPos`.  
  
```  
UINT GetMenuItemID(int nPos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Určuje pozici (počítáno od nuly) položky nabídky Probíhá načítání s ID.  
  
### <a name="return-value"></a>Návratová hodnota  
 ID položky pro zadaná položka v místní nabídce Pokud funkce je úspěšné. Pokud zadaná položka místní nabídky (na rozdíl od položky v rámci místní nabídky), je vrácenou hodnotu -1. Pokud `nPos` odpovídá **ODDĚLOVAČE** položky nabídky, návratová hodnota je 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getmenuiteminfo"></a>CMenu::GetMenuItemInfo  
 Načte informace o položku nabídky.  
  
```  
BOOL GetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `uItem`  
 Identifikátor nebo pozice položky nabídky se získat informace. Význam tohoto parametru závisí na hodnotu `ByPos`.  
  
 `lpMenuItemInfo`  
 Ukazatel [MENUITEMINFO](http://msdn.microsoft.com/library/windows/desktop/ms647578), jak je popsáno v sadě Windows SDK, který obsahuje informace o nabídce.  
  
 `fByPos`  
 Hodnota, která určuje význam `nIDItem`. Ve výchozím nastavení `ByPos` je **FALSE**, což znamená, že uItem je identifikátor položky nabídky. Pokud `ByPos` není nastavený na **FALSE**, znamená to umístění položky v nabídce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu nenulové hodnoty. Pokud funkce selže, je vrácenou hodnotu nula. Chcete-li získat rozšířené informace o chybě, použijte funkci Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360), jak je popsáno v sadě Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování funkce Win32 [GetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms647980), jak je popsáno v sadě Windows SDK. Všimněte si, že implementace MFC `GetMenuItemInfo`, nepoužívejte popisovač pro nabídky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]  
  
##  <a name="getmenustate"></a>CMenu::GetMenuState  
 Vrátí stav zadaná položka nabídky nebo počet položek v místní nabídce.  
  
```  
UINT GetMenuState(
    UINT nID,  
    UINT nFlags) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Určuje ID položky nabídky, počítáno od `nFlags`.  
  
 `nFlags`  
 Určuje druh `nID`. Může být jedna z následujících hodnot:  
  
- **MF_BYCOMMAND** Určuje, že parametr obsahuje ID příkazu, který existující položky nabídky. Toto nastavení je výchozí.  
  
- **MF_BYPOSITION** Určuje, že parametr dává pozici existující položky nabídky. První položka je na pozici 0.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota 0xFFFFFFFF, pokud zadaná položka neexistuje. Pokud *nId* identifikuje místní nabídky, vysoce pořadí bajtů počet položek v rozbalovací nabídce a nejnižší bajtů obsahuje příznaky nabídky spojené s místní nabídky. V opačném případě vrácená hodnota je masku (logická hodnota nebo) z hodnot z následujícího seznamu (Tato maska popisuje stav v nabídce položku, která *nId* identifikuje):  
  
- **MF_CHECKED** funguje jako přepínač s **MF_UNCHECKED** umístit výchozí zaškrtnutí vedle položky. Kdy aplikace poskytuje značky zaškrtnutí Bitmap (najdete v článku `SetMenuItemBitmaps` – členská funkce), se zobrazí rastrový obrázek "zaškrtnutí na".  
  
- **MF_DISABLED** zakáže položky nabídky, takže ji nelze vybrat, ale není dim.  
  
- `MF_ENABLED`Položky nabídky umožňuje, aby ho lze vybrat a obnoví z stav neaktivní. Všimněte si, že tato konstanta hodnotu 0; aplikace by neměl testování proti 0 pro typ selhání při použití této hodnoty.  
  
- **MF_GRAYED** zakáže položky nabídky tak, aby nelze vybrat a ztlumí ho.  
  
- **MF_MENUBARBREAK** umístí položku na nový řádek v nabídkách statické nebo v novém sloupci v místní nabídky. Nový sloupec místní nabídky budou ze staré sloupce odděleny svislou čarou rozdíl.  
  
- **MF_MENUBREAK** umístí položku na nový řádek v nabídkách statické nebo v novém sloupci v místní nabídky. Žádný rozdíl řádek je umístěn mezi sloupci.  
  
- **MF_SEPARATOR** nevykresluje na vodorovném řádku rozdíl. Lze použít pouze v místní nabídce. Tento řádek nelze neaktivní, zakázán nebo zvýrazněná. Další parametry jsou ignorovány.  
  
- **MF_UNCHECKED** funguje jako přepínač s **MF_CHECKED** zrušte zaškrtnutí vedle položky. Kdy aplikace poskytuje bitmap značky zaškrtnutí (najdete v článku `SetMenuItemBitmaps` – členská funkce), se zobrazí rastrový obrázek "zaškrtnutí vypnout". Všimněte si, že tato konstanta hodnotu 0; aplikace by neměl testování proti 0 pro typ selhání při použití této hodnoty.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]  
  
##  <a name="getmenustring"></a>CMenu::GetMenuString  
 Popisek zadaná položka nabídky zkopíruje do zadané vyrovnávací paměti.  
  
```  
int GetMenuString(
    UINT nIDItem,  
    LPTSTR lpString,  
    int nMaxCount,  
    UINT nFlags) const;  
  
int GetMenuString(
    UINT nIDItem,  
    CString& rString,  
    UINT nFlags) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIDItem`  
 Určuje celé číslo identifikátor položky nabídky nebo offset položky nabídky v nabídce, v závislosti na hodnotě `nFlags`.  
  
 `lpString`  
 Body do vyrovnávací paměti, která se zobrazí popisek.  
  
 `rString`  
 Odkaz na `CString` objekt, který je řetězec zkopírovaný nabídky.  
  
 `nMaxCount`  
 Určuje maximální délku (ve znacích) štítek, který chcete zkopírovat. Pokud je delší než maximální zadaný v popisek `nMaxCount`, se zkrátí znaky navíc.  
  
 `nFlags`  
 Určuje výklad `nIDItem` parametr. Může být jedna z následujících hodnot:  
  
|nFlags|Výklad nIDItem|  
|------------|-------------------------------|  
|**MF_BYCOMMAND**|Určuje, že parametr obsahuje ID příkazu, který existující položky nabídky. Toto je výchozí, pokud **MF_BYCOMMAND** ani **MF_BYPOSITION** nastavena.|  
|**MF_BYPOSITION**|Určuje, že parametr dává pozici existující položky nabídky. První položka je na pozici 0.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje skutečný počet znaků, které jsou zkopírovány do vyrovnávací paměti není včetně ukončení hodnotu null.  
  
### <a name="remarks"></a>Poznámky  
 `nMaxCount` Parametr by měl být jeden větší než počet znaků v popisku zohlednit znak hodnoty null, která ukončuje řetězec.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getsafehmenu"></a>CMenu::GetSafeHmenu  
 Vrátí `HMENU` zabalen to `CMenu` objekt, nebo **NULL** `CMenu` ukazatel.  
  
```  
HMENU GetSafeHmenu() const;  
```  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::LoadMenu](#loadmenu).  
  
##  <a name="getsubmenu"></a>CMenu::GetSubMenu  
 Načte `CMenu` objekt místní nabídky.  
  
```  
CMenu* GetSubMenu(int nPos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Určuje umístění v místní nabídce obsažené v nabídce. Hodnoty pozice začínají hodnotou 0 pro první položku. Místní nabídky identifikátor nelze použít v této funkci.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CMenu` objekt, jehož `m_hMenu` člen obsahuje popisovač pro místní nabídky, pokud existuje místní nabídky na dané pozici; v opačném případě **NULL**. Pokud `CMenu` objekt neexistuje, pak se vytvoří dočasný jeden. `CMenu` Vrácený ukazatel by neměly být uloženy.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::TrackPopupMenu](#trackpopupmenu).  
  
##  <a name="insertmenu"></a>CMenu::InsertMenu  
 Vloží novou položku nabídky na pozici určeného `nPosition` a dalších položek se posouvá směrem dolů v nabídce.  
  
```  
BOOL InsertMenu(
    UINT nPosition,  
    UINT nFlags,  
    UINT_PTR nIDNewItem = 0,  
    LPCTSTR lpszNewItem = NULL);

 
BOOL InsertMenu(
    UINT nPosition,  
    UINT nFlags,  
    UINT_PTR nIDNewItem,  
    const CBitmap* pBmp);
```  
  
### <a name="parameters"></a>Parametry  
 `nPosition`  
 Určuje položku nabídky, před kterou je možné vložit novou položku nabídky. `nFlags` Parametru lze interpretovat `nPosition` následujícími způsoby:  
  
|nFlags|Výklad nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Určuje, že parametr obsahuje ID příkazu, který existující položky nabídky. Toto je výchozí, pokud **MF_BYCOMMAND** ani **MF_BYPOSITION** nastavena.|  
|**MF_BYPOSITION**|Určuje, že parametr dává pozici existující položky nabídky. První položka je na pozici 0. Pokud `nPosition` je -1, nové položky nabídky je připojen na konec v nabídce.|  
  
 `nFlags`  
 Určuje, jak `nPosition` interpretována a určuje informace o stavu nové položky nabídky při jejím přidání do nabídky. Seznam příznaky, které lze nastavit, najdete v článku [AppendMenu](#appendmenu) – členská funkce. Chcete-li zadat více než jednu hodnotu, použijte kombinovat s bitový operátor OR **MF_BYCOMMAND** nebo **MF_BYPOSITION** příznak.  
  
 `nIDNewItem`  
 Určuje ID příkazu nové položky nabídky nebo, pokud `nFlags` je nastaven na **MF_POPUP**, popisovač nabídky ( `HMENU`) z místní nabídky. `nIDNewItem` Parametr je ignorován (není potřeba), pokud `nFlags` je nastaven na **MF_SEPARATOR**.  
  
 `lpszNewItem`  
 Určuje obsah novou položku nabídky. `nFlags`Umožňuje interpretovat `lpszNewItem` následujícími způsoby:  
  
|nFlags|Výklad lpszNewItem|  
|------------|-----------------------------------|  
|`MF_OWNERDRAW`|Obsahuje hodnotu 32-bit zadané aplikace, který aplikace můžete použít ke správě další data přidružená k položce nabídky. Tato hodnota 32-bit je k dispozici pro aplikace **itemData** členem strukturu poskytl [WM_MEASUREITEM](http://msdn.microsoft.com/library/windows/desktop/bb775925) a [WM_DRAWITEM](http://msdn.microsoft.com/library/windows/desktop/bb775923) zprávy. Tyto zprávy jsou odesílány při položky nabídky počátečním zobrazení nebo změně.|  
|**MF_STRING**|Obsahuje dlouho ukazatel na řetězce ukončené hodnotou null. Toto je výchozí interpretaci.|  
|**MF_SEPARATOR**|`lpszNewItem` Parametr je ignorován (není potřeba).|  
  
 *pBmp*  
 Odkazuje na `CBitmap` objekt, který se použije jako položku nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace můžete určit stav položky nabídky nastavením hodnoty v `nFlags`.  
  
 Vždy, když nabídky, které nachází v okno změní (nebo zda se zobrazí okno), aplikace by měly volat `CWnd::DrawMenuBar`.  
  
 Když `nIDNewItem` Určuje místní nabídky, stane se součástí nabídky, ve kterém je vložen. Pokud této nabídky zničení, budou také nabídce vložené zničena. Vložené nabídky musí odpojit od `CMenu` objekt, který chcete, aby nedošlo ke konfliktu.  
  
 Pokud aktivní maximalizaci více dokumentů (MDI) rozhraní podřízeného okna a aplikaci vloží místní nabídky do nabídky MDI voláním této funkce a určením **MF_BYPOSITION** je vložen příznak, v nabídce dále o jednu pozici vlevo, než se očekávalo. K tomu dochází, protože v nabídce ovládací prvek aktivního podřízeného okna MDI se vloží do první pozici rámce okna MDI řádku nabídek. Na pozici v nabídce správně, musí aplikace přidat 1 na pozici hodnotu, která by jinak použít. Aplikace můžete použít **WM_MDIGETACTIVE** zpráva k určení, zda je aktuálně aktivní podřízeného okna maximalizované.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]  
  
##  <a name="insertmenuitem"></a>CMenu::InsertMenuItem  
 Vloží novou položku nabídky na zadané pozici v nabídce.  
  
```  
BOOL InsertMenuItem(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `uItem`  
 Popis `uItem` v [InsertMenuItem](http://msdn.microsoft.com/library/windows/desktop/ms647988) ve Windows SDK.  
  
 `lpMenuItemInfo`  
 Popis `lpmii` v **InsertMenuItem** ve Windows SDK.  
  
 `fByPos`  
 Popis `fByPosition` v **InsertMenuItem** ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Zabalí tuto funkci [InsertMenuItem](http://msdn.microsoft.com/library/windows/desktop/ms647988), které jsou popsány v sadě Windows SDK.  
  
##  <a name="loadmenu"></a>CMenu::LoadMenu  
 Načte prostředek nabídky z spustitelný soubor aplikace a připojí jej k `CMenu` objektu.  
  
```  
BOOL LoadMenu(LPCTSTR lpszResourceName);  
BOOL LoadMenu(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszResourceName`  
 Odkazuje na řetězec ukončené hodnotou null, který obsahuje název prostředku nabídky načíst.  
  
 `nIDResource`  
 Určuje ID nabídky prostředku nabídky načíst.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl úspěšně; načten prostředků nabídky jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Před ukončením, musí aplikace uvolnit systémové prostředky, které jsou přidružené k nabídce Pokud v nabídce není přiřazen k okno. Aplikace uvolní nabídky voláním [DestroyMenu](#destroymenu) – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]  
  
##  <a name="loadmenuindirect"></a>CMenu::LoadMenuIndirect  
 Načte prostředek ze šablony nabídky v paměti a připojí jej k `CMenu` objektu.  
  
```  
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 *lpMenuTemplate*  
 Odkazuje na šablonu nabídky (což je jediný [MENUITEMTEMPLATEHEADER](http://msdn.microsoft.com/library/windows/desktop/ms647583) strukturu a kolekce jednoho nebo více [MENUITEMTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms647581) struktury). Další informace o těchto dvou struktur najdete v části Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl úspěšně; načten prostředků nabídky jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Šablonu nabídky je hlavičku následuje kolekce jednoho nebo více [MENUITEMTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms647581) struktury, z nichž každá může obsahovat jednu nebo více položek nabídky a místní nabídky.  
  
 Číslo verze musí být 0.  
  
 **MtOption** by měla obsahovat příznaky **MF_END** pro poslední položky v seznamu místní nabídky a poslední položky v seznamu hlavní. Najdete v článku `AppendMenu` – členská funkce pro nastavení další příznaky. **MtId** člena musí být vynechána z **MENUITEMTEMPLATE** struktury při **MF_POPUP** je uveden v **mtOption**.  
  
 Místo přidělené **MENUITEMTEMPLATE** struktury musí být dostatečně velký pro **mtString** tak, aby obsahovala název položky nabídky jako řetězce ukončené hodnotou null.  
  
 Před ukončením, musí aplikace uvolnit systémové prostředky, které jsou přidružené k nabídce Pokud v nabídce není přiřazen k okno. Aplikace uvolní nabídky voláním [DestroyMenu](#destroymenu) – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]  
  
##  <a name="m_hmenu"></a>CMenu::m_hMenu  
 Určuje, `HMENU` popisovač nabídku Windows připojené k `CMenu` objektu.  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::LoadMenu](#loadmenu).  
  
##  <a name="measureitem"></a>CMenu::MeasureItem  
 Voláno rámcem při vytváření nabídky s styl vykreslování vlastníka.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpMeasureItemStruct`  
 Ukazatel na `MEASUREITEMSTRUCT` struktury.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato funkce člen neprovede žádnou akci. Funkci člena přepsat a vyplňte `MEASUREITEMSTRUCT` struktura informovat systém Windows v nabídce dimenzí.  
  
 V tématu [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) popis `MEASUREITEMSTRUCT` struktura.  
  
### <a name="example"></a>Příklad  
 Následující kód je z knihovny MFC [CTRLTEST](../../visual-cpp-samples.md) ukázka:  
  
 [!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]  
  
##  <a name="modifymenu"></a>CMenu::ModifyMenu  
 Změní stávající položku nabídky na pozici určeného `nPosition`.  
  
```  
BOOL ModifyMenu(
    UINT nPosition,  
    UINT nFlags,  
    UINT_PTR nIDNewItem = 0,  
    LPCTSTR lpszNewItem = NULL);

 
BOOL ModifyMenu(
    UINT nPosition,  
    UINT nFlags,  
    UINT_PTR nIDNewItem,  
    const CBitmap* pBmp);
```  
  
### <a name="parameters"></a>Parametry  
 `nPosition`  
 Určuje položku nabídky se musí změnit. `nFlags` Parametru lze interpretovat `nPosition` následujícími způsoby:  
  
|nFlags|Výklad nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Určuje, že parametr obsahuje ID příkazu, který existující položky nabídky. Toto je výchozí, pokud **MF_BYCOMMAND** ani **MF_BYPOSITION** nastavena.|  
|**MF_BYPOSITION**|Určuje, že parametr dává pozici existující položky nabídky. První položka je na pozici 0.|  
  
 `nFlags`  
 Určuje, jak `nPosition` interpretována a poskytuje informace o změnách, které musí být pro položku nabídky. Seznam příznaky, které lze nastavit, najdete v článku [AppendMenu](#appendmenu) – členská funkce.  
  
 `nIDNewItem`  
 Určuje ID příkazu položky nabídky upravené nebo, pokud `nFlags` je nastaven na **MF_POPUP**, popisovač nabídky ( `HMENU`) z místní nabídky. `nIDNewItem` Parametr je ignorován (není potřeba), pokud `nFlags` je nastaven na **MF_SEPARATOR**.  
  
 `lpszNewItem`  
 Určuje obsah novou položku nabídky. `nFlags` Parametru lze interpretovat `lpszNewItem` následujícími způsoby:  
  
|nFlags|Výklad lpszNewItem|  
|------------|-----------------------------------|  
|`MF_OWNERDRAW`|Obsahuje hodnotu 32-bit zadané aplikace, který aplikace můžete použít ke správě další data přidružená k položce nabídky. Tato hodnota 32-bit je k dispozici pro aplikaci, když zpracovává **MF_MEASUREITEM** a **MF_DRAWITEM**.|  
|**MF_STRING**|Obsahuje dlouho ukazatel na řetězec ukončené hodnotou null nebo na `CString`.|  
|**MF_SEPARATOR**|`lpszNewItem` Parametr je ignorován (není potřeba).|  
  
 *pBmp*  
 Odkazuje na `CBitmap` objekt, který se použije jako položku nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace určuje nový stav položky nabídky nastavením hodnoty v `nFlags`. Pokud tuto funkci nahrazuje místní nabídky přidružené k položce nabídky, odstraní staré místní nabídky a uvolní množství paměti používané v místní nabídce.  
  
 Když `nIDNewItem` Určuje místní nabídky, stane se součástí nabídky, ve kterém je vložen. Pokud této nabídky zničení, budou také nabídce vložené zničena. Vložené nabídky musí odpojit od `CMenu` objekt, který chcete, aby nedošlo ke konfliktu.  
  
 Vždy, když nabídky, které nachází v okno změní (nebo zda se zobrazí okno), aplikace by měly volat `CWnd::DrawMenuBar`. Pro změnu atributů existující položky nabídky, je mnohem rychlejší používat `CheckMenuItem` a `EnableMenuItem` členské funkce.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="operator_hmenu"></a>CMenu::operator HMENU  
 Tento operátor umožňuje načíst popisovač `CMenu` objektu.  
  
```  
operator HMENU() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu popisovač `CMenu` objektu; jinak, **hodnotu NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač můžete přímo volat rozhraní API systému Windows.  
  
##  <a name="operator_neq"></a>CMenu::operator! =  
 Určuje, jestli dvě nabídky jsou logicky nejsou stejné.  
  
```  
BOOL operator!=(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `menu`  
 A `CMenu` objekt pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Testy, pokud objekt nabídky na levé straně není rovno nabídky objekt na pravé straně.  
  
##  <a name="operator_eq_eq"></a>CMenu::operator ==  
 Určuje, jestli dvě nabídky jsou logicky stejné.  
  
```  
BOOL operator==(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `menu`  
 A `CMenu` objekt pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Testů, pokud objekt nabídky na levé straně je rovno (z hlediska `HMENU` hodnotu) do nabídky objekt na pravé straně.  
  
##  <a name="removemenu"></a>CMenu::RemoveMenu  
 Vymaže položku nabídky s přidružené místní nabídky v nabídce.  
  
```  
BOOL RemoveMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `nPosition`  
 Určuje položku nabídky odeberou. `nFlags` Parametru lze interpretovat `nPosition` následujícími způsoby:  
  
|nFlags|Výklad nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Určuje, že parametr obsahuje ID příkazu, který existující položky nabídky. Toto je výchozí, pokud **MF_BYCOMMAND** ani **MF_BYPOSITION** nastavena.|  
|**MF_BYPOSITION**|Určuje, že parametr dává pozici existující položky nabídky. První položka je na pozici 0.|  
  
 `nFlags`  
 Určuje, jak `nPosition` interpretována.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Toto nezničí popisovač pro místní nabídky, tak v nabídce lze znovu použít. Před voláním této funkce, může aplikace zavolat `GetSubMenu` – členská funkce načíst místní nabídce `CMenu` objekt pro opakované použití.  
  
 Vždy, když nabídky, které nachází v okno změní (nebo zda se zobrazí okno), aplikace musí volat `CWnd::DrawMenuBar`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="setdefaultitem"></a>CMenu::SetDefaultItem  
 Nastaví výchozí položku nabídky pro zadaný nabídky.  
  
```  
BOOL SetDefaultItem(
    UINT uItem,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `uItem`  
 Identifikátor nebo pozice nový výchozí položku nabídky nebo - 1 pro žádné výchozí položku. Význam tohoto parametru závisí na hodnotu `fByPos`.  
  
 `fByPos`  
 Hodnota, která určuje význam `uItem`. Pokud tento parametr je **FALSE**, `uItem` je identifikátor položky nabídky. Jinak je umístění položky v nabídce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu nenulové hodnoty. Pokud funkce selže, je vrácenou hodnotu nula. Chcete-li získat rozšířené informace o chybě, použijte funkci Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360), jak je popsáno v sadě Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování funkce Win32 [SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="setmenucontexthelpid"></a>CMenu::SetMenuContextHelpId  
 Přidruží ID kontextu pomoc s `CMenu`.  
  
```  
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```  
  
### <a name="parameters"></a>Parametry  
 `dwContextHelpId`  
 ID kontextu nápovědy pro přidružení `CMenu`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0  
  
### <a name="remarks"></a>Poznámky  
 Všechny položky v nabídce sdílet tento identifikátor – není možné připojit identifikátor kontextové nápovědy k položky jednotlivé nabídky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="setmenuinfo"></a>CMenu::SetMenuInfo  
 Nastaví informace o nabídce.  
  
```  
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```  
  
### <a name="parameters"></a>Parametry  
 `lpcmi`  
 Ukazatel [MENUINFO](http://msdn.microsoft.com/library/windows/desktop/ms647575) struktura obsahující informace o nabídce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu nenulové; návratovou hodnotu, jinak hodnota rovná nule.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto funkci nastavit konkrétní informace o nabídce.  
  
##  <a name="setmenuitembitmaps"></a>CMenu::SetMenuItemBitmaps  
 Přidruží zadané bitmap položku nabídky.  
  
```  
BOOL SetMenuItemBitmaps(
    UINT nPosition,  
    UINT nFlags,  
    const CBitmap* pBmpUnchecked,  
    const CBitmap* pBmpChecked);
```  
  
### <a name="parameters"></a>Parametry  
 `nPosition`  
 Určuje položku nabídky se musí změnit. `nFlags` Parametru lze interpretovat `nPosition` následujícími způsoby:  
  
|nFlags|Výklad nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Určuje, že parametr obsahuje ID příkazu, který existující položky nabídky. Toto je výchozí, pokud **MF_BYCOMMAND** ani **MF_BYPOSITION** nastavena.|  
|**MF_BYPOSITION**|Určuje, že parametr dává pozici existující položky nabídky. První položka je na pozici 0.|  
  
 `nFlags`  
 Určuje, jak `nPosition` interpretována.  
  
 `pBmpUnchecked`  
 Určuje rastrový obrázek, který chcete použít pro položky nabídky, které nejsou zkontrolovat.  
  
 `pBmpChecked`  
 Určuje rastrový obrázek, který chcete použít pro položky nabídky, které jsou zaškrtnutá políčka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Zda položky nabídky je zaškrtnuté nebo nezaškrtnuté, systém Windows zobrazí odpovídající rastrový obrázek vedle položky nabídky.  
  
 Pokud má jedna `pBmpUnchecked` nebo `pBmpChecked` je **NULL**, pak Windows zobrazí nic vedle položky nabídky pro odpovídající atribut. Pokud jsou oba parametry **NULL**, systém Windows používá výchozí zaškrtnutí při položka je zaškrtnuté políčko, zrušíte zaškrtnutí, pokud položka není zaškrtnuta.  
  
 Když v nabídce zničení, nejsou zničen tyto bitmap; aplikace musí ničit.  
  
 Windows **GetMenuCheckMarkDimensions** funkce načte dimenze výchozí zaškrtnutí použitý pro položky nabídky. Aplikace tyto hodnoty používá k určení odpovídající velikost pro bitmap zadaný pomocí této funkce. Získat velikost, vytvoření vaší rastrové obrázky a potom je nastaví.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]  
  
##  <a name="setmenuiteminfo"></a>CMenu::SetMenuItemInfo  
 Změní informace o položku nabídky.  
  
```  
BOOL SetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `uItem`  
 Popis `uItem` v [SetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms648001) ve Windows SDK.  
  
 `lpMenuItemInfo`  
 Popis `lpmii` v **SetMenuItemInfo** ve Windows SDK.  
  
 `fByPos`  
 Popis `fByPosition` v **SetMenuItemInfo** ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Zabalí tuto funkci [SetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms648001), které jsou popsány v sadě Windows SDK.  
  
##  <a name="trackpopupmenu"></a>CMenu::TrackPopupMenu  
 Zobrazí plovoucí místní nabídky v zadaném umístění a sleduje výběr položek v místní nabídce.  
  
```  
BOOL TrackPopupMenu(
    UINT nFlags,  
    int x,  
    int y,  
    CWnd* pWnd,  
    LPCRECT lpRect = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nFlags`  
 Určuje pozici obrazovky a myš pozice. V tématu [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) seznam dostupných příznaků.  
  
 *x*  
 Určuje vodorovné umístění v souřadnice obrazovky místní nabídky. V závislosti na hodnotě `nFlags` parametr, v nabídce může být zarovnaný doleva, zarovnaný doprava nebo na střed vzhledem ke tuto pozici.  
  
 *y*  
 Určuje svislé umístění v souřadnice obrazovky horní nabídce na obrazovce.  
  
 `pWnd`  
 Identifikuje okně, které vlastní místní nabídky. Tento parametr nemůže být **NULL**, i když **TPM_NONOTIFY** zadán příznak. Toto okno přijímá všechny **wm_command –** zprávy z nabídky. V systému Windows verze 3.1 nebo novější, neobdrží okno **wm_command –** zpráv, dokud `TrackPopupMenu` vrátí. V systému Windows 3.0 okno přijímá **wm_command –** zprávy před `TrackPopupMenu` vrátí.  
  
 `lpRect`  
 Ignorovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí výsledek volání [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Plovoucí místní nabídky může vyskytovat kdekoli na obrazovce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]  
  
##  <a name="trackpopupmenuex"></a>CMenu::TrackPopupMenuEx  
 Zobrazí plovoucí místní nabídky v zadaném umístění a sleduje výběr položek v místní nabídce.  
  
```  
BOOL TrackPopupMenuEx(
    UINT fuFlags,  
    int x,  
    int y,  
    CWnd* pWnd,  
    LPTPMPARAMS lptpm);
```  
  
### <a name="parameters"></a>Parametry  
 `fuFlags`  
 Určuje různé funkce pro nabídky Rozšířené. Seznam všech hodnot a jejich významu najdete v tématu [TrackPopupMenuEx](http://msdn.microsoft.com/library/windows/desktop/ms648003).  
  
 *x*  
 Určuje vodorovné umístění v souřadnice obrazovky místní nabídky.  
  
 *y*  
 Určuje svislé umístění v souřadnice obrazovky horní nabídce na obrazovce.  
  
 `pWnd`  
 Ukazatel na okno vlastnící rozbalovací nabídce a příjem zpráv z nabídky vytvořený. Toto okno může být jakékoli okno z aktuální aplikace, ale nemůže být **NULL**. Pokud zadáte **TPM_NONOTIFY** v `fuFlags` parametr funkce neodesílá všechny zprávy a pokuste se `pWnd`. Funkce musí vracet pro údržbu, na kterou odkazuje `pWnd` přijímat **wm_command –** zprávy.  
  
 *lptpm*  
 Ukazatel na [TPMPARAMS](http://msdn.microsoft.com/library/windows/desktop/ms647586) struktura, která určuje oblast obrazovky v nabídce se nesmí překrývat. Tento parametr může být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud zadáte **TPM_RETURNCMD** v `fuFlags` parametr vrácená hodnota je identifikátor položky nabídky položky, kterou uživatel vybral. Pokud uživatel zruší nabídce bez provedení výběru, nebo pokud dojde k chybě, návratová hodnota je 0.  
  
 Pokud nezadáte **TPM_RETURNCMD** v `fuFlags` nenulové hodnoty, pokud se podaří funkce a 0 je návratovou hodnotu parametr, pokud se nezdaří. Chcete-li získat rozšířené informace o chybě, volejte [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Poznámky  
 Plovoucí místní nabídky může vyskytovat kdekoli na obrazovce. Další informace o zpracování chyb při vytváření místní nabídky, najdete v části [TrackPopupMenuEx](http://msdn.microsoft.com/library/windows/desktop/ms648003).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC CTRLTEST](../../visual-cpp-samples.md)   
 [Ukázka MFC DYNAMENU](../../visual-cpp-samples.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)
