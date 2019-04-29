---
title: Cmenu – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 464b59f7e598ea1901cf88c47c5887cbbf308607
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375792"
---
# <a name="cmenu-class"></a>Cmenu – třída

Zapouzdření nabídky Windows `HMENU`.

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
|[CMenu::Attach](#attach)|Připojí popisovač nabídky Windows `CMenu` objektu.|
|[CMenu::CheckMenuItem](#checkmenuitem)|Umístí značku zaškrtnutí vedle položky nebo zruší zaškrtávací políčko položky nabídky v místní nabídce.|
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|Umístí přepínač vedle položky nabídky a přepínač zruší všechny ostatní položky nabídky ve skupině.|
|[CMenu::CreateMenu](#createmenu)|Vytvoří prázdné nabídky a připojí ho k `CMenu` objektu.|
|[CMenu::CreatePopupMenu](#createpopupmenu)|Vytvoří prázdný rozbalovací nabídky a připojí ho k `CMenu` objektu.|
|[CMenu::DeleteMenu](#deletemenu)|Odstraní zadanou položku v nabídce. Pokud má položka nabídky přidružené rozbalovací nabídky, odstraní popisovač rozbalovací nabídky a uvolní paměť používanou ho.|
|[CMenu::DeleteTempMap](#deletetempmap)|Odstraní všechny dočasné `CMenu` objekty vytvořené `FromHandle` členskou funkci.|
|[CMenu::DestroyMenu](#destroymenu)|Odstraní nabídku připojené k `CMenu` objektu a uvolnění paměti, který v nabídce obsazené.|
|[CMenu::Detach](#detach)|Odpojí popisovač nabídky Windows z `CMenu` objekt a vrátí popisovač.|
|[CMenu::DrawItem](#drawitem)|Volá se rozhraním při úpravě vizuálního aspektu změny vykreslovaných vlastníkem nabídek.|
|[CMenu::EnableMenuItem](#enablemenuitem)|Povolí a zakáže, ztmavnou (šedé) položky nabídky.|
|[CMenu::FromHandle](#fromhandle)|Vrací ukazatel `CMenu` objekt daný popisovač nabídku Windows.|
|[CMenu::GetDefaultItem](#getdefaultitem)|Určuje výchozí položky nabídky v nabídce zadané.|
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|Načte ID kontextové nápovědy přidružené k nabídce.|
|[CMenu::GetMenuInfo](#getmenuinfo)|Načte informace o konkrétní nabídky.|
|[CMenu::GetMenuItemCount](#getmenuitemcount)|Určuje počet položek v nabídce místní nebo nejvyšší úrovně.|
|[CMenu::GetMenuItemID](#getmenuitemid)|Získá identifikátor položky nabídky pro položku nabídky na zadané pozici.|
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|Načte informace o položce nabídky.|
|[CMenu::GetMenuState](#getmenustate)|Vrátí stav položky nabídky nebo počet položek v místní nabídce.|
|[CMenu::GetMenuString](#getmenustring)|Načte popisek položky nabídky.|
|[CMenu::GetSafeHmenu](#getsafehmenu)|Vrátí `m_hMenu` zabalený touto `CMenu` objektu.|
|[CMenu::GetSubMenu](#getsubmenu)|Načte ukazatel na místní nabídky.|
|[CMenu::InsertMenu](#insertmenu)|Vloží novou položku nabídky na zadané pozici přesunutí jiné položky dolů v nabídce.|
|[CMenu::InsertMenuItem](#insertmenuitem)|Vloží novou položku nabídky na konkrétní pozici v nabídce.|
|[CMenu::LoadMenu](#loadmenu)|Načte prostředek nabídky ze spustitelného souboru a připojí ho k `CMenu` objektu.|
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|Načte nabídky z nabídky šablony v paměti a připojí ho k `CMenu` objektu.|
|[CMenu::MeasureItem](#measureitem)|Volá se rozhraním, můžete určit dimenze nabídky, kdy vykreslovaných vlastníkem nabídky se vytvoří.|
|[CMenu::ModifyMenu](#modifymenu)|Změní existující položky nabídky na zadané pozici.|
|[CMenu::RemoveMenu](#removemenu)|Odstraní položku nabídky s přidružené rozbalovací nabídky z nabídky zadané.|
|[CMenu::SetDefaultItem](#setdefaultitem)|Nastaví výchozí položku nabídky pro zadaný nabídky.|
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|Nastaví ID kontextové nápovědy k nabídce.|
|[CMenu::SetMenuInfo](#setmenuinfo)|Nastaví informace o konkrétní nabídce.|
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|Přidruží zadaný zaškrtnutí rastrové obrázky položku nabídky.|
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|Změní informace o položce nabídky.|
|[CMenu::TrackPopupMenu](#trackpopupmenu)|Zobrazí místní nabídku s plovoucí desetinnou čárkou v zadaném umístění a sleduje výběr položek v místní nabídce.|
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|Zobrazí místní nabídku s plovoucí desetinnou čárkou v zadaném umístění a sleduje výběr položek v místní nabídce.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CMenu::operator HMENU](#operator_hmenu)|Načte popisovač objekt nabídky.|
|[CMenu::operator! =](#operator_neq)|Určuje, pokud dva objekty nabídky nejsou stejné.|
|[CMenu::operator ==](#operator_eq_eq)|Určuje, jestli jsou dva objekty nabídky stejné.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CMenu::m_hMenu](#m_hmenu)|Určuje popisovač do nabídky Windows připojené k `CMenu` objektu.|

## <a name="remarks"></a>Poznámky

Poskytuje členské funkce pro vytváření, sledování, aktualizace nebo zničení nabídky.

Vytvoření `CMenu` objekt v rámci zásobníku jako místní, zavolejte `CMenu`pro členské funkce pro manipulaci s novou nabídku podle potřeby. Pak zavolejte [CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu) nastavit v nabídce okna, následovaný ihned volání `CMenu` objektu [odpojit](#detach) členskou funkci. `CWnd::SetMenu` Členská funkce nastaví nabídky v okně do nové nabídky, způsobí, že okno, které vyžadovaly překreslení tak, aby odrážely změny nabídky a také předá vlastnictví v nabídce okno. Volání `Detach` odpojí HMENU z `CMenu` objektu, tak, že místní `CMenu` předá proměnná mimo rozsah, `CMenu` destruktor objektu se nepokusí ke zničení nabídky již nevlastní. V nabídce samotného je automaticky zničen při zničení okna.

Můžete použít [LoadMenuIndirect](#loadmenuindirect) členskou funkci pro vytvoření nabídky ze šablony v paměti, ale vytvořil volání z prostředku nabídky [LoadMenu](#loadmenu) je snazší údržbu a samotného prostředku nabídky můžete vytvořit a upravit pomocí editoru nabídky.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="appendmenu"></a>  CMenu::AppendMenu

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

*nFlags*<br/>
Určuje informace o stavu novou položku nabídky, když se přidá do nabídky. Zahrnuje jeden nebo více hodnot uvedených v části poznámky.

*nIDNewItem*<br/>
Určuje ID příkazu novou položku nabídky nebo pokud *nFlags* je nastavena na MF_POPUP popisovač nabídky ( `HMENU`) z místní nabídky. *NIDNewItem* parametr se ignoruje (není potřeba), pokud *nFlags* je nastavena na MF_SEPARATOR.

*lpszNewItem*<br/>
Určuje obsah novou položku nabídky. *NFlags* parametr se používá k interpretaci *lpszNewItem* následujícím způsobem:

|nFlags|Výklad lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Obsahuje hodnotu 32-bit poskytované aplikací, která aplikace můžete použít ke správě další data přidružená k položce nabídky. Tato hodnota 32-bit je v aplikaci k dispozici po zpracování zprávy WM_MEASUREITEM a WM_DRAWITEM. Hodnota je uložena v `itemData` členu struktury součástí těchto zpráv.|
|MF_STRING|Obsahuje ukazatel na řetězec zakončený hodnotou null. Toto je výchozí výklad.|
|MF_SEPARATOR|*LpszNewItem* parametr se ignoruje (nejsou potřeba).|

*pBmp*<br/>
Odkazuje `CBitmap` objekt, který se použije jako položku nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Nastavením hodnoty v může aplikace určit stav položky nabídky *nFlags*. Když *nIDNewItem* určuje rozbalovací nabídce stane součástí nabídky, ke kterému se připojuje. Pokud této nabídky je zničen, budou také nabídky připojený zničena. Připojený nabídky musí odpojit od `CMenu` objektu, aby nedošlo ke konfliktu. Všimněte si, že MF_STRING a MF_OWNERDRAW nejsou platné pro verzi rastrový obrázek `AppendMenu`.

Následující seznam popisuje příznaky, které mohou být nastaveny v *nFlags*:

- MF_CHECKED slouží jako přepínací tlačítko s MF_UNCHECKED umístit výchozí zaškrtněte políčko vedle položky. Pokud aplikace poskytuje zaškrtávací políčko rastrové obrázky (naleznete v tématu [SetMenuItemBitmaps](#setmenuitembitmaps) členská funkce), zobrazí rastrový obrázek "zaškrtávací políčko na".

- MF_UNCHECKED slouží jako přepínací tlačítko s MF_CHECKED zrušte zaškrtnutí vedle položky. Pokud aplikace poskytuje zaškrtávací políčko rastrové obrázky (naleznete v tématu `SetMenuItemBitmaps` členská funkce), "vypnout zaškrtávací políčko" rastrový obrázek se zobrazí.

- MF_DISABLED zakáže položky nabídky, aby se nedá vybrat, ale ne dim.

- MF_ENABLED umožňuje položky nabídky, takže je možné vybrat a obnoví ze stavu šedě.

- MF_GRAYED zakáže položky nabídky tak, aby nelze vybrat a to ztmavnou.

- MF_MENUBARBREAK umístí položku na nový řádek v statické nabídky nebo v novém sloupci v rozbalovací nabídky. Nový sloupec rozbalovací nabídky budou ze staré sloupce odděleny svislou zřejmý.

- MF_MENUBREAK umístí položku na nový řádek v statické nabídky nebo v novém sloupci v rozbalovací nabídky. Žádný zřejmý, mezi sloupci nachází.

- MF_OWNERDRAW Určuje, že položka je položka vykreslené vlastníkem. Při prvním spuštění se zobrazí v nabídce, okně, které vlastní v nabídce přijme zprávu WM_MEASUREITEM, který načte výšku a šířku položky nabídky. WM_DRAWITEM zprávu, která se posílá vždycky, když vlastník musí aktualizovat vzhled položky nabídky. Tato možnost není platná pro položky nabídek nejvyšší úrovně.

- MF_POPUP Určuje, že položka nabídky obsahuje vyskakovací nabídku s ním spojená. Parametr ID Určuje popisovač pro místní nabídky, který má být přidružená k položce. Používá se pro přidání do položky místní nabídky nejvyšší úrovně místní nabídky nebo hierarchické rozbalovací nabídky.

- MF_SEPARATOR kreslení vodorovné zřejmý. Jde použít jenom v místní nabídce. Tento řádek nelze aktivní, zakázané nebo zvýrazněný. Ostatní parametry budou ignorovány.

- MF_STRING Určuje, zda položka nabídky je řetězec znaků.

Každá z těchto skupin obsahuje příznaky, které se vzájemně vylučují a nelze je použít společně:

- MF_DISABLED MF_ENABLED a MF_GRAYED

- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR a verze rastrový obrázek

- MF_MENUBARBREAK a MF_MENUBREAK

- MF_CHECKED a MF_UNCHECKED

Pokaždé, když se nabídka, která se nachází v okně se změní (nebo zda se zobrazí v okně), by aplikace měla zavolat [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::CreateMenu](#createmenu).

##  <a name="attach"></a>  CMenu::Attach

Připojí k existující nabídky Windows `CMenu` objektu.

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
Určuje popisovač pro nabídku Windows.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla operace úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce neměla být volána, pokud se nabídka je již připojen k `CMenu` objektu. Popisovač nabídky jsou uloženy v `m_hMenu` datový člen.

Pokud nabídky, kterou chcete pracovat s je již spojen s oknem, můžete použít [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu) funkce získat popisovač do nabídky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="checkmenuitem"></a>  CMenu::CheckMenuItem

Značky zaškrtnutí na přidá nebo odebere značky zaškrtnutí položky nabídky v místní nabídce.

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>Parametry

*nIDCheckItem*<br/>
Určuje položku nabídky, která se má zkontrolovat, počítáno od *nZkontrolujte*.

*nZkontrolujte*<br/>
Určuje, jak zkontrolovat položky nabídky a jak určit pozici položky v nabídce. *NZkontrolujte* parametr může být kombinací MF_CHECKED nebo MF_UNCHECKED MF_BYPOSITION nebo MF_BYCOMMAND Flags. Tyto příznaky můžete kombinovat pomocí bitového operátoru OR. Mají následující význam:

- MF_BYCOMMAND Určuje, že parametr poskytuje Identifikátor příkazu existující položky nabídky. Toto nastavení je výchozí.

- MF_BYPOSITION Určuje, že parametr obsahuje pozici existující položku nabídky. První položka je na pozici 0.

- MF_CHECKED slouží jako přepínací tlačítko s MF_UNCHECKED umístit výchozí zaškrtněte políčko vedle položky.

- MF_UNCHECKED slouží jako přepínací tlačítko s MF_CHECKED zrušte zaškrtnutí vedle položky.

### <a name="return-value"></a>Návratová hodnota

Předchozí stav položky: MF_CHECKED nebo MF_UNCHECKED nebo hodnotu 0xFFFFFFFF, pokud neexistuje položka nabídky.

### <a name="remarks"></a>Poznámky

*NIDCheckItem* parametr obsahuje položky, které má být upraven.

*NIDCheckItem* parametr může určit položku rozbalovací nabídky, stejně jako položku nabídky. Žádné speciální kroky je potřeba zkontrolovat položku rozbalovací nabídky. Nejde zkontrolovat položky nabídek nejvyšší úrovně. Položku rozbalovací nabídky musí být kontrolované podle umístění, protože nemá identifikátor položky nabídky s ním spojená.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::GetMenuState](#getmenustate).

##  <a name="checkmenuradioitem"></a>  CMenu::CheckMenuRadioItem

Ověří zadanou položku a zpřístupňuje je přepínač položky.

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*nIDFirst*<br/>
Určuje (jako ID nebo posun, závisí na hodnotě *nFlags*) první položku ve skupině přepínacích tlačítek.

*nIDLast*<br/>
Určuje (jako ID nebo posun, závisí na hodnotě *nFlags*) ve skupině přepínacích tlačítek poslední položky nabídky.

*nIDItem*<br/>
Určuje (jako ID nebo posun, závisí na hodnotě *nFlags*) položky ve skupině, které budou kontrolovat pomocí přepínače.

*nFlags*<br/>
Určuje výklad *nIDFirst*, *nIDLast*, a *nIDItem* následujícím způsobem:

|nFlags|interpretace|
|------------|--------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje Identifikátor příkazu existující položky nabídky. Toto je výchozí, pokud není nastavena ani MF_BYCOMMAND a MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr obsahuje pozici existující položku nabídky. První položka je na pozici 0.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Ve stejnou dobu funkce zruší tohoto systému zaškrtnutí všech ostatních položek nabídky v přidružené skupině a vymaže příznak typ položky přepínač pro tyto položky. Zaškrtnuté položky se zobrazí místo rastrový obrázek zaškrtnutí přepínač tlačítko (nebo odrážek) rastrový obrázek.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).

##  <a name="cmenu"></a>  CMenu::CMenu

Vytvoří prázdné nabídky a připojí ho k `CMenu` objektu.

```
CMenu();
```

### <a name="remarks"></a>Poznámky

V nabídce není vytvořeno, dokud volání jednoho z vytvořit nebo načíst členské funkce `CMenu:`

- [CreateMenu](#createmenu)

- [CreatePopupMenu](#createpopupmenu)

- [LoadMenu](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [Attach](#attach)

##  <a name="createmenu"></a>  CMenu::CreateMenu

Zobrazí se nabídka vytvoří a připojí ho k `CMenu` objektu.

```
BOOL CreateMenu();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud v nabídce byla vytvořena úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

V nabídce je původně prázdné. Položky nabídky můžete přidat pomocí `AppendMenu` nebo `InsertMenu` členskou funkci.

Pokud v nabídce je přiřazen k časového období, to je automaticky zničen při zničení okna.

Před ukončením, aplikace musí uvolnit systémové prostředky, které jsou spojené s nabídkou Pokud nabídky není přiřazen do okna. Aplikace se uvolní nabídky voláním [DestroyMenu](#destroymenu) členskou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

##  <a name="createpopupmenu"></a>  CMenu::CreatePopupMenu

Vytvoří vyskakovací nabídku a připojí ho k `CMenu` objektu.

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl úspěšně vytvořen v rozbalovací nabídce; jinak 0.

### <a name="remarks"></a>Poznámky

V nabídce je původně prázdné. Položky nabídky můžete přidat pomocí `AppendMenu` nebo `InsertMenu` členskou funkci. Aplikace můžete přidat místní nabídky do existující nabídky nebo v rozbalovací nabídce. `TrackPopupMenu` Členská funkce slouží k zobrazení této nabídky jako místní nabídky s plovoucí desetinnou čárkou a sledovat výběry v místní nabídce.

Pokud v nabídce je přiřazen k časového období, to je automaticky zničen při zničení okna. Pokud nabídky je přidána do existující nabídky, je automaticky zničen při zničení této nabídky.

Před ukončením, aplikace musí uvolnit systémové prostředky, které jsou přidružené vyskakovací nabídku, pokud není přiřazen v nabídce okno. Aplikace se uvolní nabídky voláním [DestroyMenu](#destroymenu) členskou funkci.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::CreateMenu](#createmenu).

##  <a name="deletemenu"></a>  CMenu::DeleteMenu

Odstraní položku v nabídce.

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*Npozici*<br/>
Určuje položku nabídky, který má být odstraněn, počítáno od *nFlags*.

*nFlags*<br/>
Slouží k interpretaci parametru *Npozici* následujícím způsobem:

|nFlags|Výklad Npozici|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje Identifikátor příkazu existující položky nabídky. Toto je výchozí, pokud není nastavena ani MF_BYCOMMAND a MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr obsahuje pozici existující položku nabídky. První položka je na pozici 0.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud má položka nabídky přidružené rozbalovací nabídky `DeleteMenu` zničí popisovač rozbalovací nabídky a uvolní paměť používanou v rozbalovací nabídce.

Pokaždé, když se nabídka, která se nachází v okně se změní (nebo zda se zobrazí v okně), aplikace musí volat [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="deletetempmap"></a>  CMenu::DeleteTempMap

Volá se automaticky `CWinApp` doby nečinnosti obslužnou rutinu, odstraní všechny dočasné `CMenu` objekty vytvořené [FromHandle](#fromhandle) členskou funkci.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Poznámky

`DeleteTempMap` Odpojí objekt nabídky Windows připojených do dočasného `CMenu` objektu před odstraněním `CMenu` objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

##  <a name="destroymenu"></a>  CMenu::DestroyMenu

Zničí nabídky a všechny prostředky Windows, které byly použity.

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je zničen v nabídce; jinak 0.

### <a name="remarks"></a>Poznámky

V nabídce odpojen od `CMenu` objektu před jeho zničení. Windows `DestroyMenu` automaticky volána `CMenu` destruktor.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::CreateMenu](#createmenu).

##  <a name="detach"></a>  CMenu::Detach

Odpojí z nabídky Windows `CMenu` objekt a vrátí popisovač.

```
HMENU Detach();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač typu HMENU, do Windows nabídky v případě úspěchu; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

`m_hMenu` Datový člen nastaven na hodnotu NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="drawitem"></a>  CMenu::DrawItem

Volá se rozhraním při úpravě vizuálního aspektu změny vykreslovaných vlastníkem nabídek.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel [drawitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) strukturu, která obsahuje informace o typu kreslení vyžaduje.

### <a name="remarks"></a>Poznámky

`itemAction` Člena `DRAWITEMSTRUCT` struktury definuje výkresu akci, která se má provést. Přepsat tato členská funkce implementovat kreslení pro vykreslené vlastníkem `CMenu` objektu. Aplikace by měl obnovit všechny grafiky zařízení rozhraní GDI systému objekty vybrané pro zadaný kontext zobrazení v *lpDrawItemStruct* před ukončením tato členská funkce.

Zobrazit [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) popis `DRAWITEMSTRUCT` struktury.

### <a name="example"></a>Příklad

Následující kód je z knihovny MFC [CTRLTEST](../../overview/visual-cpp-samples.md) vzorku:

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

##  <a name="enablemenuitem"></a>  CMenu::EnableMenuItem

Povolí, zakáže nebo ztmavnou položku nabídky.

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>Parametry

*nIDEnableItem*<br/>
Určuje položku nabídky, aby byla povolena, počítáno od *nEnable*. Tento parametr lze zadat položky místní nabídky, jakož i standardních položek nabídky.

*nEnable*<br/>
Určuje akce má být provedena. Může se jednat kombinaci MF_DISABLED, MF_ENABLED nebo MF_GRAYED MF_BYCOMMAND nebo MF_BYPOSITION. Tyto hodnoty lze spojovat pomocí bitového operátoru OR. Tyto hodnoty mají následující význam:

- MF_BYCOMMAND Určuje, že parametr poskytuje Identifikátor příkazu existující položky nabídky. Toto nastavení je výchozí.

- MF_BYPOSITION Určuje, že parametr obsahuje pozici existující položku nabídky. První položka je na pozici 0.

- MF_DISABLED zakáže položky nabídky, aby se nedá vybrat, ale ne dim.

- MF_ENABLED umožňuje položky nabídky, takže je možné vybrat a obnoví ze stavu šedě.

- MF_GRAYED zakáže položky nabídky tak, aby nelze vybrat a to ztmavnou.

### <a name="return-value"></a>Návratová hodnota

Předchozí stav (MF_DISABLED, MF_ENABLED nebo MF_GRAYED) nebo -1, pokud není platný.

### <a name="remarks"></a>Poznámky

[CreateMenu –](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu), a [LoadMenuIndirect](#loadmenuindirect) členské funkce můžete také nastavit stav (povoleno, zakázané nebo nedostupné) položky nabídky.

Pomocí hodnoty MF_BYPOSITION vyžaduje, aby aplikace k používání správných `CMenu`. Pokud `CMenu` nabídky panelu se používá, je ovlivněné položky nabídek nejvyšší úrovně (položky v panelu nabídek). Chcete-li nastavit stav položky v rozbalovací nabídce místní, nebo jsou vnořené podle umístění, musíte zadat aplikaci `CMenu` rozbalovací nabídky.

Když aplikace určuje příznak MF_BYCOMMAND Windows kontroluje všechny položky místní nabídky, které jsou podřízené `CMenu`, proto pokud duplicitní položky nejsou k dispozici, pomocí `CMenu` nabídky panelu je dostačující.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

##  <a name="fromhandle"></a>  CMenu::FromHandle

Vrací ukazatel `CMenu` objekt daný popisovač Windows do nabídky.

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
Popisovač Windows do nabídky.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CMenu` , které můžou být dočasné nebo trvalé.

### <a name="remarks"></a>Poznámky

Pokud `CMenu` objekt už není připojen ke dočasný objekt nabídky Windows `CMenu` objekt se vytvoří a připojí.

Tento dočasný `CMenu` objektu je platná pouze až do příštího aplikace má čas nečinnosti v jeho smyčkou událostí, po kterém se odstraní všechny dočasné objekty.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::CreateMenu](#createmenu).

##  <a name="getdefaultitem"></a>  CMenu::GetDefaultItem

Určuje výchozí položky nabídky v nabídce zadané.

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*gmdiFlags*<br/>
Hodnota, která určuje, jak funkce hledá položky nabídky. Tento parametr může být žádný, jeden nebo kombinace těchto hodnot:

|Hodnota|Význam|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|Určuje, zda, pokud je položka výchozí, otevře se podnabídka, funkce pro hledání v odpovídající rekurzivně podnabídka. Pokud příkaz nemá žádný výchozí položku, návratová hodnota identifikuje položku, otevře podnabídka.<br /><br /> Ve výchozím nastavení funkce vrátí první výchozí položku v nabídce zadaný bez ohledu na to, zda je položka, která otevře se podnabídka.|
|GMDI_USEDISABLED|Určuje, že funkce vrátí výchozí položky, i když je zakázán.<br /><br /> Ve výchozím nastavení přeskočí funkce vypnuta nebo šedým položky.|

*fByPos*<br/>
Hodnota, která určuje, jestli se má načíst identifikátor položky nabídky nebo jeho umístění. Pokud tento parametr hodnotu FALSE, vrátí se identifikátor. V opačném případě vrátí se pozice.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje, vrácená hodnota je identifikátor nebo pozici položky nabídky. Pokud funkce selže, vrácená hodnota je - 1.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování funkce Win32 [GetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-getmenudefaultitem), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).

##  <a name="getmenucontexthelpid"></a>  CMenu::GetMenuContextHelpId

Načte kontext nápovědy přidružené k ID `CMenu`.

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>Návratová hodnota

Kontextová nápověda ID aktuálně přiřazen k `CMenu` pokud existuje; jinak hodnota nula.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).

##  <a name="getmenuinfo"></a>  CMenu::GetMenuInfo

Načte informace pro nabídky.

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>Parametry

*lpcmi*<br/>
Ukazatel [MENUINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuinfo) struktura obsahující informace o nabídce.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje, vrácená hodnota je nenulové; jinak vrácená hodnota je nula.

### <a name="remarks"></a>Poznámky

Volání této funkce načtete informace o nabídce.

##  <a name="getmenuitemcount"></a>  CMenu::GetMenuItemCount

Určuje počet položek v nabídce místní nebo nejvyšší úrovně.

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v nabídce, pokud je funkce úspěšná. v opačném případě hodnota-1.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="getmenuitemid"></a>  CMenu::GetMenuItemID

Získá identifikátor položky nabídky pro položku nabídky na pozici určené *nPos*.

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje pozici (počítáno od nuly) položky nabídky jehož ID je načítání.

### <a name="return-value"></a>Návratová hodnota

ID položky pro zadanou položku v rozbalovací nabídce, pokud je funkce úspěšná. Pokud zadaná položka místní nabídky (na rozdíl od položky v rozbalovací nabídce), je návratová hodnota -1. Pokud *nPos* odpovídající položku nabídky ODDĚLOVAČ, vrácená hodnota je 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).

##  <a name="getmenuiteminfo"></a>  CMenu::GetMenuItemInfo

Načte informace o položce nabídky.

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uItem*<br/>
Identifikátor nebo pozici položky nabídky pro získání informací. Význam tohoto parametru závisí na hodnotě `ByPos`.

*lpMenuItemInfo*<br/>
Ukazatel [MENUITEMINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuiteminfoa), jak je popsáno v sadě Windows SDK, který obsahuje informace o nabídce.

*fByPos*<br/>
Hodnota, která určuje význam `nIDItem`. Ve výchozím nastavení `ByPos` má hodnotu FALSE, což znamená, že uItem je identifikátor položky nabídky. Pokud `ByPos` není nastaven na hodnotu FALSE, označuje pozici položky nabídky.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje, vrácená hodnota je nenulový. Pokud funkce selže, vrácená hodnota je nula. Chcete-li získat rozšířené informace o chybě, použijte funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360), jak je popsáno v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování funkce Win32 [GetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-getmenuiteminfoa), jak je popsáno v sadě Windows SDK. Všimněte si, že se v implementaci MFC `GetMenuItemInfo`, nepoužívejte popisovač do nabídky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

##  <a name="getmenustate"></a>  CMenu::GetMenuState

Vrátí stav položky nabídky nebo počet položek v místní nabídce.

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Určuje ID položky nabídky, počítáno od *nFlags*.

*nFlags*<br/>
Určuje druh *nID*. Může být jeden z následujících hodnot:

- MF_BYCOMMAND Určuje, že parametr poskytuje Identifikátor příkazu existující položky nabídky. Toto nastavení je výchozí.

- MF_BYPOSITION Určuje, že parametr obsahuje pozici existující položku nabídky. První položka je na pozici 0.

### <a name="return-value"></a>Návratová hodnota

Hodnota 0xFFFFFFFF, pokud zadaná položka neexistuje. Pokud *nId* identifikuje rozbalovací nabídky bajt nejvyšším obsahuje počet položek v rozbalovací nabídce a nejnižší bajt obsahuje příznaky nabídky spojené s rozbalovací nabídky. V opačném případě vrácená hodnota je maska (logická nebo) z hodnot z následujícího seznamu (Tato maska popisuje stav v nabídce položku, která *nId* identifikuje):

- MF_CHECKED slouží jako přepínací tlačítko s MF_UNCHECKED umístit výchozí zaškrtněte políčko vedle položky. Pokud aplikace poskytuje zaškrtávací políčko rastrové obrázky (naleznete v tématu `SetMenuItemBitmaps` členská funkce), zobrazí rastrový obrázek "zaškrtávací políčko na".

- MF_DISABLED zakáže položky nabídky, aby se nedá vybrat, ale ne dim.

- MF_ENABLED umožňuje položky nabídky, takže je možné vybrat a obnoví ze stavu šedě. Všimněte si, že hodnota této konstanty je 0; aplikace by neměl testujeme funkčnost ve 0 chyby při použití této hodnoty.

- MF_GRAYED zakáže položky nabídky tak, aby nelze vybrat a to ztmavnou.

- MF_MENUBARBREAK umístí položku na nový řádek v statické nabídky nebo v novém sloupci v rozbalovací nabídky. Nový sloupec rozbalovací nabídky budou ze staré sloupce odděleny svislou zřejmý.

- MF_MENUBREAK umístí položku na nový řádek v statické nabídky nebo v novém sloupci v rozbalovací nabídky. Žádný zřejmý, mezi sloupci nachází.

- MF_SEPARATOR kreslení vodorovné zřejmý. Jde použít jenom v místní nabídce. Tento řádek nelze aktivní, zakázané nebo zvýrazněný. Ostatní parametry budou ignorovány.

- MF_UNCHECKED slouží jako přepínací tlačítko s MF_CHECKED zrušte zaškrtnutí vedle položky. Pokud aplikace poskytuje zaškrtávací políčko rastrové obrázky (naleznete v tématu `SetMenuItemBitmaps` členská funkce), "vypnout zaškrtávací políčko" rastrový obrázek se zobrazí. Všimněte si, že hodnota této konstanty je 0; aplikace by neměl testujeme funkčnost ve 0 chyby při použití této hodnoty.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

##  <a name="getmenustring"></a>  CMenu::GetMenuString

Popisek položky nabídky se zkopíruje do zadané vyrovnávací paměti.

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

*nIDItem*<br/>
Určuje celé číslo identifikátor položky nabídky nebo posun položky nabídky v nabídce, závisí na hodnotě *nFlags*.

*lpString*<br/>
Body do vyrovnávací paměti, která se zobrazí popisek.

*rString*<br/>
Odkaz na `CString` objekt, který je na řetězec zkopírovaný nabídky.

*nMaxCount*<br/>
Určuje maximální délku (ve znacích) popisku, které se mají zkopírovat. Pokud popisek, je delší než maximální délka zadaná v *nMaxCount*, jsou přesahující znaky se zkrátí.

*nFlags*<br/>
Určuje výklad *nIDItem* parametru. Může být jeden z následujících hodnot:

|nFlags|Výklad nIDItem|
|------------|-------------------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje Identifikátor příkazu existující položky nabídky. Toto je výchozí, pokud není nastavena ani MF_BYCOMMAND a MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr obsahuje pozici existující položku nabídky. První položka je na pozici 0.|

### <a name="return-value"></a>Návratová hodnota

Určuje skutečný počet znaků, které jsou zkopírovány do vyrovnávací paměti není včetně ukončovacího znaku null.

### <a name="remarks"></a>Poznámky

*NMaxCount* parametr by měl být větší než počet znaků v popisku tak, aby vyhovovaly znak null, který ukončí řetězec.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).

##  <a name="getsafehmenu"></a>  CMenu::GetSafeHmenu

Vrátí HMENU zabalený touto `CMenu` objekt nebo hodnota NULL`CMenu` ukazatele.

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::LoadMenu](#loadmenu).

##  <a name="getsubmenu"></a>  CMenu::GetSubMenu

Načte `CMenu` objekt místní nabídky.

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje pozici v rozbalovací nabídce obsažené v nabídce. Hodnoty pozice začínají hodnotou 0 pro první položku nabídky. V rozbalovací nabídce identifikátor nelze použít v této funkci.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CMenu` jehož `m_hMenu` člena obsahuje popisovač pro místní nabídky, pokud existuje místní nabídky na dané pozici; v opačném případě hodnota NULL. Pokud `CMenu` objekt buď neexistuje, pak je vytvořen dočasný jeden. `CMenu` Vrácený ukazatel by neměly být uloženy.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::TrackPopupMenu](#trackpopupmenu).

##  <a name="insertmenu"></a>  CMenu::InsertMenu

Vloží novou položku nabídky na pozici určené *Npozici* a přesune jiné položky dolů v nabídce.

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

*Npozici*<br/>
Určuje položku nabídky, před kterým má být vložen novou položku nabídky. *NFlags* parametr lze použít k interpretaci *Npozici* následujícími způsoby:

|nFlags|Výklad Npozici|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje Identifikátor příkazu existující položky nabídky. Toto je výchozí, pokud není nastavena ani MF_BYCOMMAND a MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr obsahuje pozici existující položku nabídky. První položka je na pozici 0. Pokud *Npozici* -1, je nová položka nabídky je připojen na konec objektu v nabídce.|

*nFlags*<br/>
Určuje, jak *Npozici* interpretována a určuje informace o stavu novou položku nabídky, když se přidá do nabídky. Seznam příznaků, které lze nastavit, najdete v článku [AppendMenu](#appendmenu) členskou funkci. Chcete-li zadat více než jednu hodnotu, použijte bitový operátor OR je zkombinovat s příznakem MF_BYCOMMAND nebo MF_BYPOSITION.

*nIDNewItem*<br/>
Určuje ID příkazu novou položku nabídky nebo pokud *nFlags* je nastavena na MF_POPUP popisovač nabídky (HMENU) z místní nabídky. *NIDNewItem* parametr se ignoruje (není potřeba), pokud *nFlags* je nastavena na MF_SEPARATOR.

*lpszNewItem*<br/>
Určuje obsah novou položku nabídky. *nFlags* slouží k interpretaci *lpszNewItem* následujícími způsoby:

|nFlags|Výklad lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Obsahuje hodnotu 32-bit poskytované aplikací, která aplikace můžete použít ke správě další data přidružená k položce nabídky. Tato hodnota 32-bit je k dispozici v aplikaci `itemData` členu struktury poskytnutých [WM_MEASUREITEM](/windows/desktop/Controls/wm-measureitem) a [WM_DRAWITEM](/windows/desktop/Controls/wm-drawitem) zprávy. Tyto zprávy se odešlou, pokud položka nabídky je primárně zobrazen nebo je změnit.|
|MF_STRING|Obsahuje dlouhým ukazatelem na řetězec zakončený hodnotou null. Toto je výchozí výklad.|
|MF_SEPARATOR|*LpszNewItem* parametr se ignoruje (nejsou potřeba).|

*pBmp*<br/>
Odkazuje `CBitmap` objekt, který se použije jako položku nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Nastavením hodnoty v může aplikace určit stav položky nabídky *nFlags*.

Pokaždé, když se nabídka, která se nachází v okně se změní (nebo zda se zobrazí v okně), by aplikace měla zavolat `CWnd::DrawMenuBar`.

Když *nIDNewItem* určuje rozbalovací nabídce stane součástí nabídky, ve kterém je vložen. Pokud této nabídky je zničen, budou také nabídky vložené zničena. Vložené: nabídky musí odpojit od `CMenu` objektu, aby nedošlo ke konfliktu.

Pokud aktivní, který maximalizuje více dokumentů (MDI) interface podřízené okno a aplikace vloží místní nabídky do nabídky aplikace MDI voláním této funkce a určení, které je příznak MF_BYPOSITION, v nabídce Vložit vlevo vydrží déle než o jednu pozici byl očekáván. K tomu dochází, protože ovládací prvek nabídky aktivní podřízené okno MDI je vložen do první pozici řádku nabídek okna rámce MDI. Na pozici v nabídce správně, musí aplikace přidat 1 pozici hodnotu, která by jinak použít. Aplikace může použít k určení, zda je aktuálně aktivní podřízené okno maximalizované WM_MDIGETACTIVE zprávy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

##  <a name="insertmenuitem"></a>  CMenu::InsertMenuItem

Vloží novou položku nabídky na konkrétní pozici v nabídce.

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uItem*<br/>
Zobrazit popis *uItem* v [InsertMenuItem](/windows/desktop/api/winuser/nf-winuser-insertmenuitema) v sadě Windows SDK.

*lpMenuItemInfo*<br/>
Zobrazit popis *lpmii* v `InsertMenuItem` v sadě Windows SDK.

*fByPos*<br/>
Zobrazit popis *fByPosition* v `InsertMenuItem` v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Zabalí tuto funkci [InsertMenuItem](/windows/desktop/api/winuser/nf-winuser-insertmenuitema), které jsou popsány v sadě Windows SDK.

##  <a name="loadmenu"></a>  CMenu::LoadMenu

Načte prostředek nabídky ze spustitelného souboru aplikace a připojí ho k `CMenu` objektu.

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje název nabídky prostředek, který chcete načíst.

*nIDResource*<br/>
Určuje ID nabídky prostředku nabídky pro načtení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud nabídce prostředek se načetl úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Před ukončením, aplikace musí uvolnit systémové prostředky, které jsou spojené s nabídkou Pokud nabídky není přiřazen do okna. Aplikace se uvolní nabídky voláním [DestroyMenu](#destroymenu) členskou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

##  <a name="loadmenuindirect"></a>  CMenu::LoadMenuIndirect

Načte prostředek ze šablony nabídky v paměti a připojí ho k `CMenu` objektu.

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>Parametry

*lpMenuTemplate*<br/>
Odkazuje na šablonu nabídky (což je jediný [MENUITEMTEMPLATEHEADER](/windows/desktop/api/winuser/ns-winuser-menuitemtemplateheader) strukturu a kolekce jednoho nebo víc [MENUITEMTEMPLATE](/windows/desktop/api/winuser/ns-winuser-menuitemtemplate) struktury). Další informace o těchto dvou struktur najdete v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud nabídce prostředek se načetl úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Nabídka šablony je záhlaví, za nímž následuje kolekce jednoho nebo víc [MENUITEMTEMPLATE](/windows/desktop/api/winuser/ns-winuser-menuitemtemplate) struktury, z nichž každá může obsahovat jednu nebo více položek nabídky a nabídek.

Číslo verze musí být 0.

`mtOption` Příznaků by měl obsahovat MF_END poslední položky v seznamu místní nabídky a poslední položky v seznamu hlavních. Zobrazit `AppendMenu` členskou funkci pro nastavení další příznaky. `mtId` Člena musí být vynechána z MENUITEMTEMPLATE struktury, pokud MF_POPUP je zadaný v `mtOption`.

Místo přidělené pro strukturu MENUITEMTEMPLATE musí být dostatečně velký pro `mtString` tak, aby obsahovala název položky nabídky jako řetězec zakončený hodnotou null.

Před ukončením, aplikace musí uvolnit systémové prostředky, které jsou spojené s nabídkou Pokud nabídky není přiřazen do okna. Aplikace se uvolní nabídky voláním [DestroyMenu](#destroymenu) členskou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

##  <a name="m_hmenu"></a>  CMenu::m_hMenu

Určuje HMENU popisovač nabídky Windows připojené k `CMenu` objektu.

```
HMENU m_hMenu;
```

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::LoadMenu](#loadmenu).

##  <a name="measureitem"></a>  CMenu::MeasureItem

Volá se rozhraním při vytváření nabídky stylem vykreslené vlastníkem.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Ukazatel `MEASUREITEMSTRUCT` struktury.

### <a name="remarks"></a>Poznámky

Tato členská funkce ve výchozím nastavení nemá žádný účinek. Tato členská funkce přepsání a vyplňte `MEASUREITEMSTRUCT` struktura informovat Windows v nabídce dimenzí.

Zobrazit [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) popis `MEASUREITEMSTRUCT` struktury.

### <a name="example"></a>Příklad

Následující kód je z knihovny MFC [CTRLTEST](../../overview/visual-cpp-samples.md) vzorku:

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

##  <a name="modifymenu"></a>  CMenu::ModifyMenu

Změní existující položky nabídky na pozici určené *Npozici*.

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

*Npozici*<br/>
Určuje položku nabídky, změnit. *NFlags* parametr lze použít k interpretaci *Npozici* následujícími způsoby:

|nFlags|Výklad Npozici|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje Identifikátor příkazu existující položky nabídky. Toto je výchozí, pokud není nastavena ani MF_BYCOMMAND a MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr obsahuje pozici existující položku nabídky. První položka je na pozici 0.|

*nFlags*<br/>
Určuje, jak *Npozici* interpretována a poskytuje informace o změnách provedených na položku nabídky. Seznam příznaků, které lze nastavit, najdete v článku [AppendMenu](#appendmenu) členskou funkci.

*nIDNewItem*<br/>
Určuje Identifikátor příkazu položky upravené nabídky nebo pokud *nFlags* je nastavena na MF_POPUP popisovač nabídky (HMENU) z místní nabídky. *NIDNewItem* parametr se ignoruje (není potřeba), pokud *nFlags* je nastavena na MF_SEPARATOR.

*lpszNewItem*<br/>
Určuje obsah novou položku nabídky. *NFlags* parametr lze použít k interpretaci *lpszNewItem* následujícími způsoby:

|nFlags|Výklad lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Obsahuje hodnotu 32-bit poskytované aplikací, která aplikace můžete použít ke správě další data přidružená k položce nabídky. Tato hodnota 32-bit je v aplikaci k dispozici po zpracování MF_MEASUREITEM a MF_DRAWITEM.|
|MF_STRING|Obsahuje dlouhým ukazatelem na řetězec zakončený hodnotou null nebo na `CString`.|
|MF_SEPARATOR|*LpszNewItem* parametr se ignoruje (nejsou potřeba).|

*pBmp*<br/>
Odkazuje `CBitmap` objekt, který se použije jako položku nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace určuje nový stav položky nabídky nastavením hodnoty v *nFlags*. Pokud tuto funkci nahrazuje místní nabídky přidružené položky nabídky, odstraní staré rozbalovací nabídky a uvolní paměť používanou v rozbalovací nabídce.

Když *nIDNewItem* určuje rozbalovací nabídce stane součástí nabídky, ve kterém je vložen. Pokud této nabídky je zničen, budou také nabídky vložené zničena. Vložené: nabídky musí odpojit od `CMenu` objektu, aby nedošlo ke konfliktu.

Pokaždé, když se nabídka, která se nachází v okně se změní (nebo zda se zobrazí v okně), by aplikace měla zavolat `CWnd::DrawMenuBar`. Chcete-li změnit atributy existujících položek nabídky, je mnohem rychlejší používat `CheckMenuItem` a `EnableMenuItem` členské funkce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).

##  <a name="operator_hmenu"></a>  CMenu::operator HMENU

Tento operátor umožňuje načíst popisovač `CMenu` objektu.

```
operator HMENU() const;
```

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu popisovač `CMenu` objektu; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Popisovač můžete použít pro volání rozhraní API Windows přímo.

##  <a name="operator_neq"></a>  CMenu::operator! =

Určuje, zda dvou nabídek logicky není rovno.

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>Parametry

*Nabídky*<br/>
A `CMenu` objekt k porovnání.

### <a name="remarks"></a>Poznámky

Testuje, zda je objekt nabídky na levé straně není roven objektu nabídky na pravé straně.

##  <a name="operator_eq_eq"></a>  CMenu::operator ==

Určuje, jestli jsou logicky stejné dvou nabídek.

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>Parametry

*Nabídky*<br/>
A `CMenu` objekt k porovnání.

### <a name="remarks"></a>Poznámky

Testuje, zda je objekt nabídky na levé straně je rovno (z hlediska hodnot HMENU) objekt nabídky na pravé straně.

##  <a name="removemenu"></a>  CMenu::RemoveMenu

Odstraní položku nabídky s přidružené rozbalovací nabídky v nabídce.

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*Npozici*<br/>
Určuje položku nabídky, která se má odebrat. *NFlags* parametr lze použít k interpretaci *Npozici* následujícími způsoby:

|nFlags|Výklad Npozici|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje Identifikátor příkazu existující položky nabídky. Toto je výchozí, pokud není nastavena ani MF_BYCOMMAND a MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr obsahuje pozici existující položku nabídky. První položka je na pozici 0.|

*nFlags*<br/>
Určuje, jak *Npozici* je interpretován.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Ho nezničí popisovač pro místní nabídky, takže lze opětovně použít v nabídce. Před voláním této funkce může volat aplikaci `GetSubMenu` členské funkce lze získat automaticky otevírané okno `CMenu` objekt pro opakované použití.

Pokaždé, když se nabídka, která se nachází v okně se změní (nebo zda se zobrazí v okně), aplikace musí volat `CWnd::DrawMenuBar`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).

##  <a name="setdefaultitem"></a>  CMenu::SetDefaultItem

Nastaví výchozí položku nabídky pro zadaný nabídky.

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uItem*<br/>
Identifikátor nebo pozice novou položku nabídky výchozí nebo - 1 pro žádné výchozí položku. Význam tohoto parametru závisí na hodnotě *fByPos*.

*fByPos*<br/>
Hodnota, která určuje význam *uItem*. Pokud tento parametr má hodnotu FALSE, *uItem* je identifikátor položky nabídky. V opačném případě je umístění položky v nabídce.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje, vrácená hodnota je nenulový. Pokud funkce selže, vrácená hodnota je nula. Chcete-li získat rozšířené informace o chybě, použijte funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360), jak je popsáno v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování funkce Win32 [SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).

##  <a name="setmenucontexthelpid"></a>  CMenu::SetMenuContextHelpId

Přidruží ID kontextové nápovědy s `CMenu`.

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>Parametry

*dwContextHelpId*<br/>
ID kontextové nápovědy pro přidružení k `CMenu`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Všechny položky v nabídce sdílet tento identifikátor – není možné se připojit k jednotlivým položkám identifikátor kontextové nápovědy.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu::InsertMenu](#insertmenu).

##  <a name="setmenuinfo"></a>  CMenu::SetMenuInfo

Nastaví informace o nabídce.

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>Parametry

*lpcmi*<br/>
Ukazatel [MENUINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuinfo) struktura obsahující informace o nabídce.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje, vrácená hodnota je nenulové; jinak vrácená hodnota je nula.

### <a name="remarks"></a>Poznámky

Voláním této funkce nastavit konkrétní informace o nabídce.

##  <a name="setmenuitembitmaps"></a>  CMenu::SetMenuItemBitmaps

Přidruží zadané rastrové obrázky položku nabídky.

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>Parametry

*Npozici*<br/>
Určuje položku nabídky, změnit. *NFlags* parametr lze použít k interpretaci *Npozici* následujícími způsoby:

|nFlags|Výklad Npozici|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje Identifikátor příkazu existující položky nabídky. Toto je výchozí, pokud není nastavena ani MF_BYCOMMAND a MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr obsahuje pozici existující položku nabídky. První položka je na pozici 0.|

*nFlags*<br/>
Určuje, jak *Npozici* je interpretován.

*pBmpUnchecked*<br/>
Určuje rastrový obrázek pro položky nabídky, které nejsou zaškrtnuté.

*pBmpChecked*<br/>
Určuje rastrový obrázek pro položky nabídky, které nebyly zvoleny.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Zda je položka nabídky zaškrtnuté nebo nezaškrtnuté, Windows zobrazí odpovídající rastrový obrázek vedle položky nabídky.

Pokud *pBmpUnchecked* nebo *pBmpChecked* má hodnotu NULL, pak Windows nezobrazí nic vedle položky nabídky pro odpovídající atribut. Pokud jsou oba parametry NULL, Windows používá výchozí zaškrtnutí při položka je zaškrtnuté políčko a zrušíte zaškrtnutí, pokud položka není zaškrtnuta.

Tyto rastrové obrázky nejsou zničeny, když v nabídce je zničen, aplikaci musíte zničit.

Windows `GetMenuCheckMarkDimensions` funkce načte dimenze výchozí zaškrtnutí použitý pro položky nabídky. Aplikace tyto hodnoty používá k určení správné velikosti pro rastrové obrázky dodávané s touto funkcí. Získat její velikost, vytvořit vaše rastrové obrázky a jejich nastavení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

##  <a name="setmenuiteminfo"></a>  CMenu::SetMenuItemInfo

Změní informace o položce nabídky.

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uItem*<br/>
Zobrazit popis *uItem* v [SetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-setmenuiteminfoa) v sadě Windows SDK.

*lpMenuItemInfo*<br/>
Zobrazit popis *lpmii* v `SetMenuItemInfo` v sadě Windows SDK.

*fByPos*<br/>
Zobrazit popis *fByPosition* v `SetMenuItemInfo` v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Zabalí tuto funkci [SetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-setmenuiteminfoa), které jsou popsány v sadě Windows SDK.

##  <a name="trackpopupmenu"></a>  CMenu::TrackPopupMenu

Zobrazí místní nabídku s plovoucí desetinnou čárkou v zadaném umístění a sleduje výběr položek v místní nabídce.

```
BOOL TrackPopupMenu(
    UINT nFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPCRECT lpRect = 0);
```

### <a name="parameters"></a>Parametry

*nFlags*<br/>
Určuje umístění obrazovky a pozice myši příznaky. Zobrazit [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) seznam dostupných příznaků.

*x*<br/>
Určuje vodorovná pozice v souřadnicovém systému obrazovky místní nabídky. V závislosti na hodnotu *nFlags* parametr, v nabídce může být zarovnaný doleva, zarovnaný doprava nebo na střed vzhledem k této pozici.

*y*<br/>
Určuje horní části nabídky svislou pozici v souřadnicovém systému obrazovky na obrazovce.

*pWnd*<br/>
Identifikuje okna, který vlastní místní nabídky. Tento parametr nemůže mít hodnotu NULL, i v případě, že je zadán příznak TPM_NONOTIFY. Toto okno přijímá všechny wm_command – zprávy z nabídky. Ve Windows verze 3.1 nebo novější, v okně neobdrží wm_command – zprávy do `TrackPopupMenu` vrátí. V okně Windows 3.0, obdrží wm_command – zprávy před `TrackPopupMenu` vrátí.

*lpRect*<br/>
Ignorovat.

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí výsledek volání [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Místní nabídka s plovoucí desetinnou čárkou může vyskytovat kdekoli na obrazovce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

##  <a name="trackpopupmenuex"></a>  CMenu::TrackPopupMenuEx

Zobrazí místní nabídku s plovoucí desetinnou čárkou v zadaném umístění a sleduje výběr položek v místní nabídce.

```
BOOL TrackPopupMenuEx(
    UINT fuFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPTPMPARAMS lptpm);
```

### <a name="parameters"></a>Parametry

*fuFlags*<br/>
Určuje různé funkce pro nabídku Rozšířené. Seznam všech hodnot a jejich významu najdete v tématu [TrackPopupMenuEx](/windows/desktop/api/winuser/nf-winuser-trackpopupmenuex).

*x*<br/>
Určuje vodorovná pozice v souřadnicovém systému obrazovky místní nabídky.

*y*<br/>
Určuje horní části nabídky svislou pozici v souřadnicovém systému obrazovky na obrazovce.

*pWnd*<br/>
Ukazatel na okno vlastnící rozbalovací nabídky a příjem zpráv z nabídky vytvořený. Toto okno může být jakékoli okno z aktuální aplikace, ale nemůže mít hodnotu NULL. Pokud zadáte TPM_NONOTIFY v *fuFlags* parametr funkce neodešle žádné zprávy k *pWnd*. Funkce musí vracet okna, na které odkazuje *pWnd* wm_command – zpráva.

*lptpm*<br/>
Ukazatel [TPMPARAMS](/windows/desktop/api/winuser/ns-winuser-tagtpmparams) struktura, která určuje oblast na obrazovce v nabídce se nesmí překrývat. Tento parametr může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Pokud zadáte TPM_RETURNCMD v *fuFlags* parametr, návratová hodnota je identifikátor položky nabídky, kterou uživatel vybral položky. Pokud uživatel zruší nabídce bez výběru nebo pokud dojde k chybě, vrácená hodnota je 0.

Pokud nezadáte TPM_RETURNCMD v *fuFlags* nenulovou hodnotu, pokud je funkce úspěšná a 0 je návratová hodnota parametr, pokud selže. Chcete-li získat rozšířené informace o chybě, volejte [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Poznámky

Místní nabídka s plovoucí desetinnou čárkou může vyskytovat kdekoli na obrazovce. Další informace o zpracování chyb při vytváření v rozbalovací nabídce, naleznete v tématu [TrackPopupMenuEx](/windows/desktop/api/winuser/nf-winuser-trackpopupmenuex).

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)
