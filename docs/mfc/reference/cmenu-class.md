---
title: CMenu – – třída
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
ms.openlocfilehash: 1cd7be72dc6c9a38fae4f5ccc1a15c184a2d4466
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420804"
---
# <a name="cmenu-class"></a>CMenu – – třída

Zapouzdření `HMENU`Windows.

## <a name="syntax"></a>Syntaxe

```
class CMenu : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMenu –:: CMenu –](#cmenu)|Vytvoří objekt `CMenu`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMenu –:: AppendMenu](#appendmenu)|Připojí novou položku na konec této nabídky.|
|[CMenu –:: Attach](#attach)|Připojí popisovač nabídky systému Windows k objektu `CMenu`.|
|[CMenu –:: CheckMenuItem](#checkmenuitem)|Umístí zaškrtnutí nebo zruší zaškrtnutí u položky nabídky v místní nabídce.|
|[CMenu –:: CheckMenuRadioItem](#checkmenuradioitem)|Umístí přepínač vedle položky nabídky a odebere přepínač ze všech ostatních položek nabídky ve skupině.|
|[CMenu –:: CreateMenu](#createmenu)|Vytvoří prázdnou nabídku a připojí ji k objektu `CMenu`.|
|[CMenu –:: CreatePopupMenu](#createpopupmenu)|Vytvoří prázdnou místní nabídku a připojí ji k objektu `CMenu`.|
|[CMenu –::D eleteMenu](#deletemenu)|Odstraní zadanou položku z nabídky. Pokud má položka nabídky přidruženou místní nabídku, odstraní popisovač do místní nabídky a uvolní paměť, kterou používá.|
|[CMenu –::D eleteTempMap](#deletetempmap)|Odstraní všechny dočasné `CMenu` objekty vytvořené pomocí `FromHandle` členské funkce.|
|[CMenu –::D estroyMenu](#destroymenu)|Odstraní nabídku připojenou k objektu `CMenu` a uvolní veškerou paměť, kterou nabídka zabírala.|
|[CMenu –::D etach](#detach)|Odpojí popisovač nabídky systému Windows od objektu `CMenu` a vrátí popisovač.|
|[CMenu –::D rawItem](#drawitem)|Volá se rozhraním, když se změní vizuální aspekt nabídky sestavené vlastníkem.|
|[CMenu –:: EnableMenuItem](#enablemenuitem)|Povolí, zakáže nebo ztmaví (šedě) položku nabídky.|
|[CMenu –:: FromHandle](#fromhandle)|Vrátí ukazatel na objekt `CMenu` pro danou obslužnou rutinu nabídky systému Windows.|
|[CMenu –:: GetDefaultItem](#getdefaultitem)|Určuje výchozí položku nabídky v zadané nabídce.|
|[CMenu –:: GetMenuContextHelpId](#getmenucontexthelpid)|Načte ID kontextu nápovědě přidružené k této nabídce.|
|[CMenu –:: GetMenuInfo](#getmenuinfo)|Načte informace o konkrétní nabídce.|
|[CMenu –:: GetMenuItemCount](#getmenuitemcount)|Určuje počet položek v místní nabídce nebo v nabídce nejvyšší úrovně.|
|[CMenu –:: GetMenuItemID](#getmenuitemid)|Získá identifikátor položky nabídky pro položku nabídky, která se nachází na zadané pozici.|
|[CMenu –:: GetMenuItemInfo](#getmenuiteminfo)|Načte informace o položce nabídky.|
|[CMenu –:: GetMenuState](#getmenustate)|Vrátí stav zadané položky nabídky nebo počet položek v místní nabídce.|
|[CMenu –:: GetMenuString](#getmenustring)|Načte popisek zadané položky nabídky.|
|[CMenu –:: GetSafeHmenu](#getsafehmenu)|Vrátí `m_hMenu` zabalenou tímto `CMenu`m objektem.|
|[CMenu –:: Get– podnabídka](#getsubmenu)|Načte ukazatel na místní nabídku.|
|[CMenu –:: InsertMenu](#insertmenu)|Vloží novou položku nabídky na určenou pozici a přesune jiné položky v nabídce.|
|[CMenu –:: InsertMenuItem](#insertmenuitem)|Vloží novou položku nabídky na určenou pozici v nabídce.|
|[CMenu –:: LoadMenu](#loadmenu)|Načte prostředek nabídky ze spustitelného souboru a připojí ho k objektu `CMenu`.|
|[CMenu –:: LoadMenuIndirect](#loadmenuindirect)|Načte nabídku ze šablony nabídky v paměti a připojí ji k objektu `CMenu`.|
|[CMenu –:: MeasureItem](#measureitem)|Volá se rozhraním, aby se určily dimenze nabídky, když se vytvoří nabídka pro vykreslení vlastníka.|
|[CMenu –:: ModifyMenu](#modifymenu)|Změní existující položku nabídky na zadané pozici.|
|[CMenu –:: RemoveMenu](#removemenu)|Odstraní položku nabídky s přidruženou místní nabídkou ze zadané nabídky.|
|[CMenu –:: SetDefaultItem](#setdefaultitem)|Nastaví výchozí položku nabídky pro určenou nabídku.|
|[CMenu –:: SetMenuContextHelpId](#setmenucontexthelpid)|Nastaví ID kontextové aplikace Help, které má být přidruženo k této nabídce.|
|[CMenu –:: SetMenuInfo](#setmenuinfo)|Nastaví informace o konkrétní nabídce.|
|[CMenu –:: SetMenuItemBitmaps](#setmenuitembitmaps)|Přidruží zadané rastrové obrázky zaškrtnutí k položce nabídky.|
|[CMenu –:: SetMenuItemInfo](#setmenuiteminfo)|Změní informace o položce nabídky.|
|[CMenu –:: TrackPopupMenu](#trackpopupmenu)|Zobrazí plovoucí místní nabídku v zadaném umístění a sleduje výběr položek v místní nabídce.|
|[CMenu –:: TrackPopupMenuEx](#trackpopupmenuex)|Zobrazí plovoucí místní nabídku v zadaném umístění a sleduje výběr položek v místní nabídce.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CMenu –:: operator HMENU](#operator_hmenu)|Načte popisovač objektu nabídky.|
|[CMenu –:: operator! =](#operator_neq)|Určuje, zda se dva objekty nabídky neshodují.|
|[CMenu –:: operator = = – operátor](#operator_eq_eq)|Určuje, zda jsou dva objekty nabídky stejné.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CMenu –:: m_hMenu](#m_hmenu)|Určuje popisovač pro nabídku systému Windows připojenou k objektu `CMenu`.|

## <a name="remarks"></a>Poznámky

Poskytuje členské funkce pro vytváření, sledování, aktualizaci a zničení nabídky.

Vytvořte objekt `CMenu` v bloku zásobníku jako místní a potom zavolejte členské funkce `CMenu`, abyste podle potřeby mohli pracovat s novou nabídkou. Potom zavolejte [CWnd:: SetMenu](../../mfc/reference/cwnd-class.md#setmenu) , aby se nabídka nastavila na okno, následované hned voláním členské funkce [Odpojit](#detach) objekt `CMenu`. Členská funkce `CWnd::SetMenu` nastaví nabídku okna na novou nabídku, způsobí, že okno bude překresleno tak, aby odráželo změnu nabídky, a také předává vlastnictví nabídky do okna. Volání `Detach` odpojí HMENU od objektu `CMenu`, takže když se místní `CMenu` proměnná předává mimo rozsah, destruktor objektu `CMenu` se nepokusí zničit nabídku, kterou již vlastní. V případě zničení okna je automaticky zničena i nabídka.

Pomocí členské funkce [LoadMenuIndirect](#loadmenuindirect) můžete vytvořit nabídku ze šablony v paměti, ale nabídku vytvořenou z prostředku voláním [LoadMenu](#loadmenu) je snazší udržovat a samotný prostředek nabídky lze vytvořit a upravit pomocí editoru nabídek.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="appendmenu"></a>CMenu –:: AppendMenu

Připojí novou položku na konec nabídky.

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
Určuje informace o stavu nové položky nabídky, když je přidána do nabídky. Obsahuje jednu nebo více hodnot uvedených v části poznámky.

*nIDNewItem*<br/>
Určuje ID příkazu nové položky nabídky nebo, pokud je *nFlags* nastaveno na MF_POPUP, v místní nabídce se zobrazí nabídka (`HMENU`). Parametr *nIDNewItem* se ignoruje (není potřeba), pokud je *nFlags* nastavené na MF_SEPARATOR.

*lpszNewItem*<br/>
Určuje obsah nové položky nabídky. Parametr *nFlags* slouží k interpretaci *lpszNewItem* následujícím způsobem:

|nFlags|Výklad lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Obsahuje hodnotu 32-bit dodanou aplikací, kterou může aplikace použít k udržování dalších dat přidružených k položce nabídky. Tato hodnota 32 je pro aplikaci k dispozici, když zpracovává WM_MEASUREITEM a WM_DRAWITEM zprávy. Hodnota je uložena v `itemData` členu struktury dodávané s těmito zprávami.|
|MF_STRING|Obsahuje ukazatel na řetězec zakončený hodnotou null. Toto je výchozí interpretace.|
|MF_SEPARATOR|Parametr *lpszNewItem* se ignoruje (není nutné).|

*pBmp*<br/>
Odkazuje na objekt `CBitmap`, který bude použit jako položka nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace může určit stav položky nabídky nastavením hodnot v *nFlags*. Když *nIDNewItem* určí místní nabídku, bude se jednat o součást nabídky, ke které se připojí. Pokud je tato nabídka zničena, bude také zničena i připojená nabídka. Připojená nabídka by se měla odpojit od objektu `CMenu`, aby se předešlo konfliktu. Všimněte si, že MF_STRING a MF_OWNERDRAW nejsou platné pro verzi rastrového obrázku `AppendMenu`.

Následující seznam popisuje příznaky, které mohou být nastaveny v *nFlags*:

- MF_CHECKED slouží jako přepínač s MF_UNCHECKED pro umístění výchozího zaškrtnutí vedle položky. Když aplikace poskytuje rastrové obrázky značek zaškrtnutí (viz členská funkce [SetMenuItemBitmaps](#setmenuitembitmaps) ), zobrazí se rastrový obrázek "zaškrtnutí na".

- MF_UNCHECKED slouží jako přepínač s MF_CHECKED, chcete-li odebrat zaškrtnutí vedle položky. Když aplikace poskytuje rastrové obrázky značek zaškrtnutí (viz členská funkce `SetMenuItemBitmaps`), zobrazí se rastrový obrázek "zaškrtnutí vypnuto".

- MF_DISABLED zakáže položku nabídky, aby ji nebylo možné vybrat, ale nedim.

- MF_ENABLED povolí položku nabídky, aby ji bylo možné vybrat a obnovit z jejího neaktivního stavu.

- MF_GRAYED zakáže položku nabídky, aby ji nebylo možné vybrat a ztlumí.

- MF_MENUBARBREAK umístí položku na nový řádek ve statických nabídkách nebo v novém sloupci v místních nabídkách. Nový sloupec místní nabídky bude od starého sloupce oddělen svislou Dělicí čárou.

- MF_MENUBREAK umístí položku na nový řádek ve statických nabídkách nebo v novém sloupci v místních nabídkách. Mezi sloupci se neumístí žádná dělicí čára.

- MF_OWNERDRAW určuje, že položka je položkou vykreslování vlastníka. Při prvním zobrazení nabídky se zobrazí okno, které vlastní nabídka, zprávu WM_MEASUREITEM, která načte výšku a šířku položky nabídky. WM_DRAWITEM zpráva je odeslána pokaždé, když vlastník musí aktualizovat vzhled položky nabídky. Tato možnost není platná pro položku nabídky nejvyšší úrovně.

- MF_POPUP určuje, zda má položka nabídky k ní přidruženou místní nabídku. Parametr ID Určuje popisovač pro místní nabídku, která má být přidružena k položce. Tato možnost se používá pro přidání místní nabídky nejvyšší úrovně nebo hierarchické místní nabídky do položky místní nabídky.

- MF_SEPARATOR nakreslí horizontální dělicí čáru. Dá se použít jenom v místní nabídce. Tento řádek nemůže být ztlumený, zakázaný nebo zvýrazněný. Další parametry jsou ignorovány.

- MF_STRING určuje, zda je položka nabídky znakovým řetězcem.

Každá z následujících skupin obsahuje příznaky, které jsou vzájemně exkluzivní a nelze je použít společně:

- MF_DISABLED, MF_ENABLED a MF_GRAYED

- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR a verze rastrového obrázku

- MF_MENUBARBREAK a MF_MENUBREAK

- MF_CHECKED a MF_UNCHECKED

Pokaždé, když se změní nabídka, která se nachází v okně (bez ohledu na to, zda se okno zobrazí), aplikace by měla zavolat [CWnd::D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: CreateMenu](#createmenu).

##  <a name="attach"></a>CMenu –:: Attach

Připojí existující nabídku systému Windows k objektu `CMenu`.

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
Určuje popisovač v nabídce systému Windows.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud operace byla úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce by neměla být volána, pokud je již nabídka připojena k objektu `CMenu`. Obslužná rutina nabídky je uložena v datovém členu `m_hMenu`.

Pokud je nabídka, kterou chcete manipulovat, již přidružena k oknu, můžete k získání popisovače do nabídky použít funkci [CWnd:: getmenu](../../mfc/reference/cwnd-class.md#getmenu) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="checkmenuitem"></a>CMenu –:: CheckMenuItem

Přidá značky zaškrtnutí do nebo zruší zaškrtnutí položek nabídky v místní nabídce.

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>Parametry

*nIDCheckItem*<br/>
Určuje položku nabídky, která se má zkontrolovat, podle určení v *npokuste*.

*Npokuste*<br/>
Určuje, jak se má položka nabídky kontrolovat a jak se má určit pozice položky v nabídce. Parametr *npokuste* může být kombinací MF_CHECKED nebo MF_UNCHECKED s příznaky MF_BYPOSITION nebo MF_BYCOMMAND. Tyto příznaky lze kombinovat pomocí bitového operátoru OR. Mají následující význam:

- MF_BYCOMMAND určuje, že parametr poskytuje ID příkazu pro existující položku nabídky. Toto nastavení je výchozí.

- MF_BYPOSITION určuje, zda parametr poskytuje pozici existující položky nabídky. První položka je na pozici 0.

- MF_CHECKED slouží jako přepínač s MF_UNCHECKED pro umístění výchozího zaškrtnutí vedle položky.

- MF_UNCHECKED slouží jako přepínač s MF_CHECKED, chcete-li odebrat zaškrtnutí vedle položky.

### <a name="return-value"></a>Návratová hodnota

Předchozí stav položky: MF_CHECKED nebo MF_UNCHECKED nebo 0xFFFFFFFF, pokud položka nabídky neexistuje.

### <a name="remarks"></a>Poznámky

Parametr *nIDCheckItem* Určuje položku, která se má změnit.

Parametr *nIDCheckItem* může identifikovat položku místní nabídky a také položku nabídky. Ke kontrole položky místní nabídky nejsou nutné žádné speciální kroky. Nelze zkontrolovat položky nabídky nejvyšší úrovně. Položka místní nabídky musí být zkontrolována podle pozice, protože k ní není přidružen identifikátor položky nabídky.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: GetMenuState](#getmenustate).

##  <a name="checkmenuradioitem"></a>CMenu –:: CheckMenuRadioItem

Zkontroluje zadanou položku nabídky a vytvoří ji jako přepínač.

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*nIDFirst*<br/>
Určuje (jako ID nebo posunutí, v závislosti na hodnotě *nFlags*) první položku nabídky ve skupině přepínačů.

*nIDLast*<br/>
Určuje (jako ID nebo posun, v závislosti na hodnotě *nFlags*) poslední položka nabídky ve skupině přepínačů.

*nIDItem*<br/>
Určuje (jako ID nebo posun v závislosti na hodnotě *nFlags*) položku ve skupině, která se bude kontrolovat pomocí přepínacího tlačítka.

*nFlags*<br/>
Určuje výklad *nIDFirst*, *nIDLast*a *nIDItem* následujícím způsobem:

|nFlags|Interpretace|
|------------|--------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje ID příkazu pro existující položku nabídky. Toto je výchozí nastavení, pokud není nastavená hodnota MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr poskytuje pozici existující položky nabídky. První položka je na pozici 0.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0

### <a name="remarks"></a>Poznámky

Ve stejnou dobu funkce zruší zaškrtnutí všech ostatních položek nabídky v přidružené skupině a vymaže příznak typ položky pro tyto položky. Kontrolovaná položka se zobrazí s použitím přepínacího tlačítka (nebo odrážky) rastrového obrázku místo rastrového obrázku značky zaškrtnutí.

### <a name="example"></a>Příklad

  Podívejte se na příklad [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).

##  <a name="cmenu"></a>CMenu –:: CMenu –

Vytvoří prázdnou nabídku a připojí ji k objektu `CMenu`.

```
CMenu();
```

### <a name="remarks"></a>Poznámky

Nabídka není vytvořena, dokud nebudete volat jednu z členských funkcí Create nebo Load `CMenu:`

- [CreateMenu](#createmenu)

- [CreatePopupMenu](#createpopupmenu)

- [LoadMenu](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [Attach](#attach)

##  <a name="createmenu"></a>CMenu –:: CreateMenu

Vytvoří nabídku a připojí ji k objektu `CMenu`.

```
BOOL CreateMenu();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se nabídka vytvořila úspěšně; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Nabídka je zpočátku prázdná. Položky nabídky lze přidat pomocí členské funkce `AppendMenu` nebo `InsertMenu`.

Pokud je nabídka přiřazena k oknu, je automaticky zničena při zničení okna.

Před ukončením musí aplikace uvolnit systémové prostředky spojené s nabídkou, pokud nabídka není přiřazena k oknu. Aplikace uvolní nabídku voláním členské funkce [DestroyMenu](#destroymenu) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

##  <a name="createpopupmenu"></a>CMenu –:: CreatePopupMenu

Vytvoří místní nabídku a připojí ji k objektu `CMenu`.

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se místní nabídka úspěšně vytvořila; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Nabídka je zpočátku prázdná. Položky nabídky lze přidat pomocí členské funkce `AppendMenu` nebo `InsertMenu`. Aplikace může přidat místní nabídku do existující nabídky nebo místní nabídky. Členská funkce `TrackPopupMenu` může být použita k zobrazení této nabídky jako plovoucí místní nabídky a ke sledování výběru v místní nabídce.

Pokud je nabídka přiřazena k oknu, je automaticky zničena při zničení okna. Pokud je nabídka přidána do existující nabídky, je automaticky zničena při zničení této nabídky.

Před ukončením musí aplikace uvolnit systémové prostředky přidružené k místní nabídce, pokud nabídka není přiřazena k oknu. Aplikace uvolní nabídku voláním členské funkce [DestroyMenu](#destroymenu) .

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: CreateMenu](#createmenu).

##  <a name="deletemenu"></a>CMenu –::D eleteMenu

Odstraní položku z nabídky.

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*Npozici*<br/>
Určuje položku nabídky, která má být odstraněna, jak je určeno *nFlags*.

*nFlags*<br/>
Slouží k interpretaci *npozici* následujícím způsobem:

|nFlags|Výklad Npozici|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje ID příkazu pro existující položku nabídky. Toto je výchozí nastavení, pokud není nastavená hodnota MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr poskytuje pozici existující položky nabídky. První položka je na pozici 0.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud má položka nabídky přidruženou místní nabídku, `DeleteMenu` zničí popisovač do místní nabídky a uvolní paměť využívanou místní nabídkou.

Pokaždé, když se změní nabídka, která se nachází v okně (bez ohledu na to, zda se okno zobrazí), musí aplikace volat [CWnd::D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Příklad

  Viz příklad pro [CWnd:: getmenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="deletetempmap"></a>CMenu –::D eleteTempMap

Volána automaticky `CWinApp` obslužná rutina doby nečinnosti, odstraní všechny dočasné objekty `CMenu` vytvořené členskou funkcí [FromHandle](#fromhandle) .

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Poznámky

`DeleteTempMap` před odstraněním objektu `CMenu` odpojí objekt nabídky systému Windows připojen k dočasnému objektu `CMenu`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

##  <a name="destroymenu"></a>CMenu –::D estroyMenu

Odstraní nabídku a všechny prostředky systému Windows, které byly použity.

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je nabídka zničena; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Nabídka je odpojena od objektu `CMenu` před tím, než je zničena. Funkce Windows `DestroyMenu` je automaticky volána v destruktoru `CMenu`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: CreateMenu](#createmenu).

##  <a name="detach"></a>CMenu –::D etach

Odpojí nabídku systému Windows od objektu `CMenu` a vrátí popisovač.

```
HMENU Detach();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač typu HMENU do nabídky systému Windows, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Datový člen `m_hMenu` je nastaven na hodnotu NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="drawitem"></a>CMenu –::D rawItem

Volá se rozhraním, když se změní vizuální aspekt nabídky sestavené vlastníkem.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel na strukturu [DRAWITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-drawitemstruct) , která obsahuje informace o požadovaném typu výkresu.

### <a name="remarks"></a>Poznámky

`itemAction` člen struktury `DRAWITEMSTRUCT` definuje akci kreslení, která má být provedena. Přepište tuto členskou funkci pro implementaci vykreslování pro objekt `CMenu` vykreslený vlastníkem. Aplikace by měla obnovit všechny objekty GDI (Graphics Device Interface) vybrané pro kontext zobrazení zadaný v *lpDrawItemStruct* před ukončením této členské funkce.

Popis `DRAWITEMSTRUCT` struktury naleznete v tématu [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) .

### <a name="example"></a>Příklad

Následující kód pochází z [CTRLTEST](../../overview/visual-cpp-samples.md) Sample knihovny MFC:

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

##  <a name="enablemenuitem"></a>CMenu –:: EnableMenuItem

Povolí, zakáže nebo ztlumí položku nabídky.

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>Parametry

*nIDEnableItem*<br/>
Určuje položku nabídky, která má být povolena, jak je určeno *nEnable*. Tento parametr může určovat položky místní nabídky a také standardní položky nabídky.

*nEnable*<br/>
Určuje akci, která má být provedena. Může se jednat o kombinaci MF_DISABLED, MF_ENABLED nebo MF_GRAYED s MF_BYCOMMAND nebo MF_BYPOSITION. Tyto hodnoty lze kombinovat pomocí bitového operátoru OR. Tyto hodnoty mají následující význam:

- MF_BYCOMMAND určuje, že parametr poskytuje ID příkazu pro existující položku nabídky. Toto nastavení je výchozí.

- MF_BYPOSITION určuje, zda parametr poskytuje pozici existující položky nabídky. První položka je na pozici 0.

- MF_DISABLED zakáže položku nabídky, aby ji nebylo možné vybrat, ale nedim.

- MF_ENABLED povolí položku nabídky, aby ji bylo možné vybrat a obnovit z jejího neaktivního stavu.

- MF_GRAYED zakáže položku nabídky, aby ji nebylo možné vybrat a ztlumí.

### <a name="return-value"></a>Návratová hodnota

Předchozí stav (MF_DISABLED, MF_ENABLED nebo MF_GRAYED) nebo-1, pokud není platný.

### <a name="remarks"></a>Poznámky

Členské funkce [CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu)a [LoadMenuIndirect](#loadmenuindirect) mohou také nastavit stav (Enabled, disabled nebo dimmed) položky nabídky.

Použití hodnoty MF_BYPOSITION vyžaduje, aby aplikace používala správný `CMenu`. Je-li použita `CMenu` řádku nabídek, bude ovlivněna položka nabídky nejvyšší úrovně (položka v panelu nabídek). Chcete-li nastavit stav položky v automaticky otevíraném okně nebo vnořené místní nabídce podle pozice, aplikace musí určovat `CMenu` místní nabídky.

Když aplikace určí příznak MF_BYCOMMAND, systém Windows zkontroluje všechny místní nabídky položky, které jsou podřízené `CMenu`; proto, pokud nejsou k dispozici duplicitní položky nabídky, je použití `CMenu` panelu nabídek dostatečné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

##  <a name="fromhandle"></a>CMenu –:: FromHandle

Vrátí ukazatel na objekt `CMenu` s daným popisovačem Windows pro nabídku.

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
Popisovač Windows do nabídky

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CMenu`, která může být dočasná nebo trvalá.

### <a name="remarks"></a>Poznámky

Pokud objekt `CMenu` již není připojen k objektu nabídky systému Windows, je vytvořen a připojen dočasný objekt `CMenu`.

Tento dočasný objekt `CMenu` je platný pouze do okamžiku, kdy aplikace bude mít čas nečinnosti ve smyčce události, kdy jsou odstraněny všechny dočasné objekty.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: CreateMenu](#createmenu).

##  <a name="getdefaultitem"></a>CMenu –:: GetDefaultItem

Určuje výchozí položku nabídky v zadané nabídce.

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*gmdiFlags*<br/>
Hodnota určující, jak funkce vyhledává položky nabídky Tento parametr může být None, jedna nebo kombinace následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|Určuje, že pokud je výchozí položkou položka, která otevře podnabídku, je funkce vyhledána v odpovídající podnabídce rekurzivně. Pokud podnabídka nemá výchozí položku, vrácená hodnota identifikuje položku, která otevře podnabídku.<br /><br /> Ve výchozím nastavení funkce vrátí první výchozí položku v zadané nabídce bez ohledu na to, zda se jedná o položku, která otevře podnabídku.|
|GMDI_USEDISABLED|Určuje, že funkce má vrátit výchozí položku, i když je zakázaná.<br /><br /> Ve výchozím nastavení funkce přeskočí zakázané nebo šedé položky.|

*fByPos*<br/>
Hodnota určující, zda má být načten identifikátor položky nabídky nebo její pozice. Pokud je tento parametr FALSE, je vrácen identifikátor. V opačném případě se vrátí pozice.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je identifikátor nebo pozice položky nabídky. Pokud dojde k chybě funkce, vrácená hodnota je-1.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování funkce Win32 [GetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: InsertMenu](#insertmenu).

##  <a name="getmenucontexthelpid"></a>CMenu –:: GetMenuContextHelpId

Načte ID kontextové kontextové informace přidružené k `CMenu`.

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>Návratová hodnota

ID kontextové kontextové informace, které je aktuálně přidruženo k `CMenu`, pokud má jednu z nich; v opačném případě nenulová.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: InsertMenu](#insertmenu).

##  <a name="getmenuinfo"></a>CMenu –:: GetMenuInfo

Načte informace pro nabídku.

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>Parametry

*lpcmi*<br/>
Ukazatel na strukturu [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) obsahující informace pro nabídku.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je nenulová; v opačném případě je vrácená hodnota nulová.

### <a name="remarks"></a>Poznámky

Voláním této funkce načtete informace o této nabídce.

##  <a name="getmenuitemcount"></a>CMenu –:: GetMenuItemCount

Určuje počet položek v místní nabídce nebo v nabídce nejvyšší úrovně.

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v nabídce, pokud je funkce úspěšná; v opačném případě-1.

### <a name="example"></a>Příklad

  Viz příklad pro [CWnd:: getmenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="getmenuitemid"></a>CMenu –:: GetMenuItemID

Získá identifikátor položky nabídky pro položku nabídky nacházející se na pozici definované v *nPos*.

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje pozici (založenou na nule) položky nabídky, jejíž ID se načítá.

### <a name="return-value"></a>Návratová hodnota

ID položky pro zadanou položku v místní nabídce, pokud je funkce úspěšná. Pokud je zadaná položka místní nabídka (na rozdíl od položky v místní nabídce), vrácená hodnota je-1. Pokud *nPos* odpovídá položce nabídky oddělovače, vrácená hodnota je 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: InsertMenu](#insertmenu).

##  <a name="getmenuiteminfo"></a>CMenu –:: GetMenuItemInfo

Načte informace o položce nabídky.

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uItem*<br/>
Identifikátor nebo pozice položky nabídky, o které se mají získat informace Význam tohoto parametru závisí na hodnotě `ByPos`.

*lpMenuItemInfo*<br/>
Ukazatel na [MENUITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow), jak je popsáno v Windows SDK, který obsahuje informace o nabídce.

*fByPos*<br/>
Hodnota určující význam `nIDItem`. Ve výchozím nastavení je `ByPos` FALSE, což označuje, že uItem je identifikátor položky nabídky. Pokud `ByPos` není nastavena na hodnotu FALSE, indikuje umístění položky nabídky.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je nenulová. Pokud dojde k chybě funkce, vrácená hodnota je nula. Chcete-li získat rozšířené informace o chybě, použijte funkci Win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), jak je popsáno v Windows SDK.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow)funkce Win32, jak je popsáno v Windows SDK. Všimněte si, že v implementaci knihovny MFC `GetMenuItemInfo`nepoužíváte popisovač pro nabídku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

##  <a name="getmenustate"></a>CMenu –:: GetMenuState

Vrátí stav zadané položky nabídky nebo počet položek v místní nabídce.

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Určuje ID položky nabídky, jak je určeno *nFlags*.

*nFlags*<br/>
Určuje povaze *NID*. Může to být jedna z následujících hodnot:

- MF_BYCOMMAND určuje, že parametr poskytuje ID příkazu pro existující položku nabídky. Toto nastavení je výchozí.

- MF_BYPOSITION určuje, zda parametr poskytuje pozici existující položky nabídky. První položka je na pozici 0.

### <a name="return-value"></a>Návratová hodnota

Hodnota 0xFFFFFFFF, pokud zadaná položka neexistuje. Pokud *nId* identifikuje místní nabídku, obsahuje horní bajty počet položek v místní nabídce a bajt s nižším pořadím obsahuje příznaky nabídky přidružené k místní nabídce. V opačném případě je vrácená hodnota maska (logická hodnota nebo) hodnot z následujícího seznamu (Tato maska popisuje stav položky nabídky, kterou *nId* identifikuje):

- MF_CHECKED slouží jako přepínač s MF_UNCHECKED pro umístění výchozího zaškrtnutí vedle položky. Když aplikace poskytuje rastrové obrázky značek zaškrtnutí (viz členská funkce `SetMenuItemBitmaps`), zobrazí se rastrový obrázek zaškrtnutí na obrázku.

- MF_DISABLED zakáže položku nabídky, aby ji nebylo možné vybrat, ale nedim.

- MF_ENABLED povolí položku nabídky, aby ji bylo možné vybrat a obnovit z jejího neaktivního stavu. Všimněte si, že hodnota této konstanty je 0; Při použití této hodnoty by aplikace neměla při selhání zkoušet hodnotu 0.

- MF_GRAYED zakáže položku nabídky, aby ji nebylo možné vybrat a ztlumí.

- MF_MENUBARBREAK umístí položku na nový řádek ve statických nabídkách nebo v novém sloupci v místních nabídkách. Nový sloupec místní nabídky bude od starého sloupce oddělen svislou Dělicí čárou.

- MF_MENUBREAK umístí položku na nový řádek ve statických nabídkách nebo v novém sloupci v místních nabídkách. Mezi sloupci se neumístí žádná dělicí čára.

- MF_SEPARATOR nakreslí horizontální dělicí čáru. Dá se použít jenom v místní nabídce. Tento řádek nemůže být ztlumený, zakázaný nebo zvýrazněný. Další parametry jsou ignorovány.

- MF_UNCHECKED slouží jako přepínač s MF_CHECKED, chcete-li odebrat zaškrtnutí vedle položky. Když aplikace poskytuje rastrové obrázky značek zaškrtnutí (viz členská funkce `SetMenuItemBitmaps`), zobrazí se rastrový obrázek "zaškrtnutí vypnuto". Všimněte si, že hodnota této konstanty je 0; Při použití této hodnoty by aplikace neměla při selhání zkoušet hodnotu 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

##  <a name="getmenustring"></a>CMenu –:: GetMenuString

Zkopíruje popisek zadané položky nabídky do zadané vyrovnávací paměti.

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
Určuje celočíselný identifikátor položky nabídky nebo posun položky nabídky v nabídce v závislosti na hodnotě *nFlags*.

*lpString*<br/>
Odkazuje na vyrovnávací paměť, která má obdržet popisek.

*rString*<br/>
Odkaz na objekt `CString`, který má přijmout zkopírovaný řetězec nabídky.

*nMaxCount*<br/>
Určuje maximální délku (ve znacích) popisku, který se má zkopírovat. Pokud je popisek delší než maximální hodnota zadaná v *nMaxCount*, znaky navíc se zkrátí.

*nFlags*<br/>
Určuje výklad parametru *nIDItem* . Může to být jedna z následujících hodnot:

|nFlags|Výklad nIDItem|
|------------|-------------------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje ID příkazu pro existující položku nabídky. Toto je výchozí nastavení, pokud není nastavená hodnota MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr poskytuje pozici existující položky nabídky. První položka je na pozici 0.|

### <a name="return-value"></a>Návratová hodnota

Určuje skutečný počet znaků zkopírovaných do vyrovnávací paměti, včetně ukončovacího znaku null.

### <a name="remarks"></a>Poznámky

Parametr *nMaxCount* by měl být větší než počet znaků v popisku, aby odpovídal znaku null, který ukončuje řetězec.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: InsertMenu](#insertmenu).

##  <a name="getsafehmenu"></a>CMenu –:: GetSafeHmenu

Vrátí HMENU zabalený tímto objektem `CMenu` nebo`CMenu` ukazatel s hodnotou NULL.

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: LoadMenu](#loadmenu).

##  <a name="getsubmenu"></a>CMenu –:: Get– podnabídka

Načte objekt `CMenu` místní nabídky.

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje umístění místní nabídky obsažené v nabídce. Hodnoty pozice začínají na 0 pro první položku nabídky. V této funkci nelze použít místní nabídku identifikátor.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `CMenu`, jehož člen `m_hMenu` obsahuje popisovač do místní nabídky, pokud na dané pozici existuje místní nabídka. jinak NULL. Pokud objekt `CMenu` neexistuje, je vytvořen dočasný. Vrácený ukazatel `CMenu` by neměl být uložen.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: TrackPopupMenu](#trackpopupmenu).

##  <a name="insertmenu"></a>CMenu –:: InsertMenu

Vloží novou položku nabídky na pozici určenou položkou *npozici* a přesune jiné položky v nabídce.

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
Určuje položku nabídky, před kterou bude vložena nová položka nabídky. Parametr *nFlags* lze použít k interpretaci *npozici* následujícími způsoby:

|nFlags|Výklad Npozici|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje ID příkazu pro existující položku nabídky. Toto je výchozí nastavení, pokud není nastavená hodnota MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr poskytuje pozici existující položky nabídky. První položka je na pozici 0. Pokud je *npozici* -1, nová položka nabídky se přidá na konec nabídky.|

*nFlags*<br/>
Určuje způsob interpretace *npozici* a určení informací o stavu nové položky nabídky při jejím přidání do nabídky. Seznam příznaků, které lze nastavit, naleznete v tématu členská funkce [AppendMenu](#appendmenu) . Chcete-li zadat více než jednu hodnotu, použijte operátor OR pro kombinaci s příznakem MF_BYCOMMAND nebo MF_BYPOSITION.

*nIDNewItem*<br/>
Určuje ID příkazu nové položky nabídky nebo, pokud je *nFlags* nastaveno na MF_POPUP, v místní nabídce se zobrazí nabídka HMENU (). Parametr *nIDNewItem* se ignoruje (není potřeba), pokud je *nFlags* nastavené na MF_SEPARATOR.

*lpszNewItem*<br/>
Určuje obsah nové položky nabídky. *nFlags* lze použít k interpretaci *lpszNewItem* následujícími způsoby:

|nFlags|Výklad lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Obsahuje hodnotu 32-bit dodanou aplikací, kterou může aplikace použít k udržování dalších dat přidružených k položce nabídky. Tato hodnota 32 je k dispozici pro aplikaci v `itemData`m členu struktury dodávané [WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem) a [WM_DRAWITEMmi](/windows/win32/Controls/wm-drawitem) zprávami. Tyto zprávy jsou odesílány, když je položka nabídky zpočátku zobrazena nebo se změnila.|
|MF_STRING|Obsahuje dlouhý ukazatel na řetězec zakončený hodnotou null. Toto je výchozí interpretace.|
|MF_SEPARATOR|Parametr *lpszNewItem* se ignoruje (není nutné).|

*pBmp*<br/>
Odkazuje na objekt `CBitmap`, který bude použit jako položka nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace může určit stav položky nabídky nastavením hodnot v *nFlags*.

Pokaždé, když se změní nabídka, která se nachází v okně (bez ohledu na to, zda se okno zobrazí), aplikace by měla volat `CWnd::DrawMenuBar`.

Když *nIDNewItem* určí místní nabídku, bude se jednat o součást nabídky, do které je vložena. Pokud je tato nabídka zničena, bude také zničena i vložená nabídka. Vložená nabídka by se měla odpojit od objektu `CMenu`, aby se předešlo konfliktu.

Pokud je aktivní podřízené okno MDI (Multiple Document Interface) a aplikace vloží místní nabídku do nabídky aplikace MDI voláním této funkce a určením příznaku MF_BYPOSITION, nabídka se vloží o jednu pozici dále, než je Outer. K tomu dochází, protože řídicí nabídka aktivního podřízeného okna MDI je vložena do první pozice řádku nabídek okna rámce MDI. Pro správné umístění nabídky musí aplikace přidat 1 k hodnotě pozice, kterou by jinak bylo možné použít. Aplikace může použít WM_MDIGETACTIVEovou zprávu k určení, zda je aktuálně aktivní podřízené okno maximalizováno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

##  <a name="insertmenuitem"></a>CMenu –:: InsertMenuItem

Vloží novou položku nabídky na určenou pozici v nabídce.

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uItem*<br/>
Viz popis *uItem* v [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw) ve Windows SDK.

*lpMenuItemInfo*<br/>
Viz popis *lpmii* v `InsertMenuItem` Windows SDK.

*fByPos*<br/>
Viz popis *fByPosition* v `InsertMenuItem` Windows SDK.

### <a name="remarks"></a>Poznámky

Tato funkce zalomí [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw), popsané v Windows SDK.

##  <a name="loadmenu"></a>CMenu –:: LoadMenu

Načte prostředek nabídky ze spustitelného souboru aplikace a připojí ho k objektu `CMenu`.

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje název prostředku nabídky, který se má načíst.

*nIDResource*<br/>
Určuje ID nabídky prostředku nabídky, která se má načíst.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl prostředek nabídky úspěšně načten; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Před ukončením musí aplikace uvolnit systémové prostředky spojené s nabídkou, pokud nabídka není přiřazena k oknu. Aplikace uvolní nabídku voláním členské funkce [DestroyMenu](#destroymenu) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

##  <a name="loadmenuindirect"></a>CMenu –:: LoadMenuIndirect

Načte prostředek ze šablony nabídky v paměti a připojí ho k objektu `CMenu`.

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>Parametry

*lpMenuTemplate*<br/>
Odkazuje na šablonu nabídky (která je jedinou strukturou [MENUITEMTEMPLATEHEADER](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader) a kolekcí jedné nebo více [MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) struktur). Další informace o těchto dvou strukturách naleznete v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl prostředek nabídky úspěšně načten; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Šablona nabídky je záhlaví následované kolekcí jedné nebo více [MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) struktur, z nichž každá může obsahovat jednu nebo více položek nabídky a místní nabídky.

Číslo verze by mělo být 0.

Příznaky `mtOption` by měly zahrnovat MF_END pro poslední položku v rozevíracím seznamu a pro poslední položku v hlavním seznamu. Další příznaky najdete v tématu `AppendMenu` členské funkce. Pokud je MF_POPUP určena v `mtOption`, musí být člen `mtId` vynechán ze struktury MENUITEMTEMPLATE.

Prostor přidělený pro strukturu MENUITEMTEMPLATE musí být dostatečně velký, aby `mtString` obsahovat název položky nabídky jako řetězec zakončený hodnotou null.

Před ukončením musí aplikace uvolnit systémové prostředky spojené s nabídkou, pokud nabídka není přiřazena k oknu. Aplikace uvolní nabídku voláním členské funkce [DestroyMenu](#destroymenu) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

##  <a name="m_hmenu"></a>CMenu –:: m_hMenu

Určuje popisovač HMENU nabídky systému Windows připojené k objektu `CMenu`.

```
HMENU m_hMenu;
```

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: LoadMenu](#loadmenu).

##  <a name="measureitem"></a>CMenu –:: MeasureItem

Volá se rozhraním, když se vytvoří nabídka se stylem vykreslování vlastníka.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Ukazatel na strukturu `MEASUREITEMSTRUCT`.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato členská funkce neprovede žádnou akci. Tuto členskou funkci přepište a naplňte `MEASUREITEMSTRUCT` struktury a informujte okna o dimenzích nabídek.

Popis `MEASUREITEMSTRUCT` struktury naleznete v tématu [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) .

### <a name="example"></a>Příklad

Následující kód pochází z [CTRLTEST](../../overview/visual-cpp-samples.md) Sample knihovny MFC:

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

##  <a name="modifymenu"></a>CMenu –:: ModifyMenu

Změní existující položku nabídky na pozici určenou položkou *npozici*.

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
Určuje položku nabídky, která se má změnit. Parametr *nFlags* lze použít k interpretaci *npozici* následujícími způsoby:

|nFlags|Výklad Npozici|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje ID příkazu pro existující položku nabídky. Toto je výchozí nastavení, pokud není nastavená hodnota MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr poskytuje pozici existující položky nabídky. První položka je na pozici 0.|

*nFlags*<br/>
Určuje způsob interpretace *npozici* a poskytuje informace o změnách, které mají být provedeny v položce nabídky. Seznam příznaků, které lze nastavit, naleznete v tématu členská funkce [AppendMenu](#appendmenu) .

*nIDNewItem*<br/>
Určuje ID příkazu upravované položky nabídky nebo, pokud je *nFlags* nastaveno na MF_POPUP, v místní nabídce se zobrazí nabídka HMENU (). Parametr *nIDNewItem* se ignoruje (není potřeba), pokud je *nFlags* nastavené na MF_SEPARATOR.

*lpszNewItem*<br/>
Určuje obsah nové položky nabídky. Parametr *nFlags* lze použít k interpretaci *lpszNewItem* následujícími způsoby:

|nFlags|Výklad lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Obsahuje hodnotu 32-bit dodanou aplikací, kterou může aplikace použít k udržování dalších dat přidružených k položce nabídky. Tato hodnota 32 je pro aplikaci k dispozici, když zpracovává MF_MEASUREITEM a MF_DRAWITEM.|
|MF_STRING|Obsahuje dlouhý ukazatel na řetězec zakončený hodnotou null nebo na `CString`.|
|MF_SEPARATOR|Parametr *lpszNewItem* se ignoruje (není nutné).|

*pBmp*<br/>
Odkazuje na objekt `CBitmap`, který bude použit jako položka nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace určuje nový stav položky nabídky nastavením hodnot v *nFlags*. Pokud tato funkce nahradí místní nabídku přidruženou k položce nabídky, zničí starou místní nabídku a uvolní paměť využívanou místní nabídkou.

Když *nIDNewItem* určí místní nabídku, bude se jednat o součást nabídky, do které je vložena. Pokud je tato nabídka zničena, bude také zničena i vložená nabídka. Vložená nabídka by se měla odpojit od objektu `CMenu`, aby se předešlo konfliktu.

Pokaždé, když se změní nabídka, která se nachází v okně (bez ohledu na to, zda se okno zobrazí), aplikace by měla volat `CWnd::DrawMenuBar`. Chcete-li změnit atributy existujících položek nabídky, je mnohem rychlejší použít členské funkce `CheckMenuItem` a `EnableMenuItem`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: InsertMenu](#insertmenu).

##  <a name="operator_hmenu"></a>CMenu –:: operator HMENU

Tento operátor použijte k načtení popisovače objektu `CMenu`.

```
operator HMENU() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, popisovač objektu `CMenu`; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Můžete použít popisovač k přímému volání rozhraní API systému Windows.

##  <a name="operator_neq"></a>CMenu –:: operator! =

Určuje, zda jsou dvě nabídky logicky nestejné.

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>Parametry

*nabídce*<br/>
Objekt `CMenu` pro porovnání.

### <a name="remarks"></a>Poznámky

Testuje, zda je objekt nabídky na levé straně neroven objektu nabídky na pravé straně.

##  <a name="operator_eq_eq"></a>CMenu –:: operator = = – operátor

Určuje, zda jsou dvě nabídky logicky stejné.

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>Parametry

*nabídce*<br/>
Objekt `CMenu` pro porovnání.

### <a name="remarks"></a>Poznámky

Testuje, zda je objekt nabídky na levé straně shodný s objektem nabídky na pravé straně (z pohledu hodnoty HMENU).

##  <a name="removemenu"></a>CMenu –:: RemoveMenu

Odstraní položku nabídky s přidruženou místní nabídkou v nabídce.

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*Npozici*<br/>
Určuje položku nabídky, která se má odebrat. Parametr *nFlags* lze použít k interpretaci *npozici* následujícími způsoby:

|nFlags|Výklad Npozici|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje ID příkazu pro existující položku nabídky. Toto je výchozí nastavení, pokud není nastavená hodnota MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr poskytuje pozici existující položky nabídky. První položka je na pozici 0.|

*nFlags*<br/>
Určuje způsob interpretace *npozici* .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Nezničí popisovač pro místní nabídku, takže se nabídka dá znovu použít. Před voláním této funkce může aplikace zavolat členskou funkci `GetSubMenu`, aby získala místní `CMenu` objekt pro opakované použití.

Pokaždé, když se změní nabídka, která se nachází v okně (bez ohledu na to, zda je okno zobrazeno), aplikace musí volat `CWnd::DrawMenuBar`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: InsertMenu](#insertmenu).

##  <a name="setdefaultitem"></a>CMenu –:: SetDefaultItem

Nastaví výchozí položku nabídky pro určenou nabídku.

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uItem*<br/>
Identifikátor nebo pozice nové výchozí položky nabídky nebo-1 pro výchozí položku. Význam tohoto parametru závisí na hodnotě *fByPos*.

*fByPos*<br/>
Hodnota určující význam *uItem* Pokud má tento parametr hodnotu FALSE, *uItem* je identifikátor položky nabídky. V opačném případě je to pozice položky nabídky.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je nenulová. Pokud dojde k chybě funkce, vrácená hodnota je nula. Chcete-li získat rozšířené informace o chybě, použijte funkci Win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), jak je popsáno v Windows SDK.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování funkce Win32 [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: InsertMenu](#insertmenu).

##  <a name="setmenucontexthelpid"></a>CMenu –:: SetMenuContextHelpId

Přidruží kontext kontextového ID k `CMenu`.

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>Parametry

*dwContextHelpId*<br/>
ID kontextové kontextové informace, které se má přidružit k `CMenu`

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0

### <a name="remarks"></a>Poznámky

Všechny položky v nabídce sdílejí tento identifikátor – k jednotlivým položkám nabídky není možné připojit identifikátor kontextu aplikace Help.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMenu –:: InsertMenu](#insertmenu).

##  <a name="setmenuinfo"></a>CMenu –:: SetMenuInfo

Nastaví informace pro nabídku.

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>Parametry

*lpcmi*<br/>
Ukazatel na strukturu [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) obsahující informace pro nabídku.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je nenulová; v opačném případě je vrácená hodnota nulová.

### <a name="remarks"></a>Poznámky

Voláním této funkce nastavíte konkrétní informace o nabídce.

##  <a name="setmenuitembitmaps"></a>CMenu –:: SetMenuItemBitmaps

Přidruží zadané rastrové obrázky k položce nabídky.

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>Parametry

*Npozici*<br/>
Určuje položku nabídky, která se má změnit. Parametr *nFlags* lze použít k interpretaci *npozici* následujícími způsoby:

|nFlags|Výklad Npozici|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr poskytuje ID příkazu pro existující položku nabídky. Toto je výchozí nastavení, pokud není nastavená hodnota MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr poskytuje pozici existující položky nabídky. První položka je na pozici 0.|

*nFlags*<br/>
Určuje způsob interpretace *npozici* .

*pBmpUnchecked*<br/>
Určuje rastrový obrázek, který se má použít pro položky nabídky, které nejsou zaškrtnuté.

*pBmpChecked*<br/>
Určuje rastrový obrázek, který se má použít pro položky nabídky, které jsou zaškrtnuté.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

V případě, že je položka nabídky zaškrtnutá nebo nezaškrtnutá, zobrazí systém Windows příslušnou rastrovou mapu vedle položky nabídky.

Pokud *pBmpUnchecked* nebo *pBmpChecked* má hodnotu null, pak systém Windows pro odpovídající atribut nezobrazí nic vedle položky nabídky. Pokud jsou oba parametry NULL, používá systém Windows výchozí značku zaškrtnutí při zaškrtnutí položky a zruší zaškrtnutí zaškrtnutí, pokud je položka nezaškrtnuta.

Po zničení nabídky nejsou tyto rastrové obrázky zničeny; aplikace je musí zničit.

Funkce Windows `GetMenuCheckMarkDimensions` načte rozměry výchozího kontrolního označení použitého pro položky nabídky. Aplikace tyto hodnoty používá k určení vhodné velikosti rastrových obrázků dodaných s touto funkcí. Získat velikost, vytvořit bitmapy a pak je nastavit.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

##  <a name="setmenuiteminfo"></a>CMenu –:: SetMenuItemInfo

Změní informace o položce nabídky.

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uItem*<br/>
Viz popis *uItem* v [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow) ve Windows SDK.

*lpMenuItemInfo*<br/>
Viz popis *lpmii* v `SetMenuItemInfo` Windows SDK.

*fByPos*<br/>
Viz popis *fByPosition* v `SetMenuItemInfo` Windows SDK.

### <a name="remarks"></a>Poznámky

Tato funkce zalomí [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow), popsané v Windows SDK.

##  <a name="trackpopupmenu"></a>CMenu –:: TrackPopupMenu

Zobrazí plovoucí místní nabídku v zadaném umístění a sleduje výběr položek v místní nabídce.

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
Určuje příznaky pozice obrazovky a myši. Seznam dostupných příznaků najdete v tématu [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) .

*znak*<br/>
Určuje vodorovnou pozici na souřadnicích obrazovky v místní nabídce. V závislosti na hodnotě parametru *nFlags* lze nabídku Zarovnat doleva, Zarovnat doprava nebo zarovnat na střed vzhledem k této pozici.

*požadované*<br/>
Určuje svislou pozici v souřadnicích obrazovky horní části nabídky na obrazovce.

*pWnd*<br/>
Identifikuje okno, které vlastní místní nabídku. Tento parametr nemůže mít hodnotu NULL ani v případě, že je zadán příznak TPM_NONOTIFY. Toto okno obdrží všechny zprávy WM_COMMAND z nabídky. V systému Windows verze 3,1 a novějších okno nepřijímá WM_COMMAND zprávy, dokud `TrackPopupMenu` nevrátí. V systému Windows 3,0 okno obdrží zprávy WM_COMMAND, než `TrackPopupMenu` vrátí.

*lpRect*<br/>
Přeskočen.

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrací výsledek volání [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) v Windows SDK.

### <a name="remarks"></a>Poznámky

Plovoucí místní nabídka se může objevit kdekoli na obrazovce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

##  <a name="trackpopupmenuex"></a>CMenu –:: TrackPopupMenuEx

Zobrazí plovoucí místní nabídku v zadaném umístění a sleduje výběr položek v místní nabídce.

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
Určuje různé funkce v rozšířené nabídce. Seznam všech hodnot a jejich významu naleznete v tématu [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

*znak*<br/>
Určuje vodorovnou pozici na souřadnicích obrazovky v místní nabídce.

*požadované*<br/>
Určuje svislou pozici v souřadnicích obrazovky horní části nabídky na obrazovce.

*pWnd*<br/>
Ukazatel na okno vlastnící místní nabídku a příjem zpráv z nabídky vytvořen. Toto okno může být libovolné okno z aktuální aplikace, ale nemůže mít hodnotu NULL. Pokud zadáte TPM_NONOTIFY v parametru *fuFlags* , funkce nepošle žádné zprávy do *pWnd*. Funkce musí vracet pro okno, na které odkazuje *pWnd* , aby mohla přijmout zprávu WM_COMMAND.

*lptpm*<br/>
Ukazatel na strukturu [TPMPARAMS](/windows/win32/api/winuser/ns-winuser-tpmparams) , která určuje oblast obrazovky, na kterou se nabídka nesmí překrývat. Tento parametr může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Pokud zadáte TPM_RETURNCMD v parametru *fuFlags* , návratovou hodnotou je identifikátor položky nabídky položky, kterou uživatel vybral. Pokud uživatel nabídku zruší bez provedení výběru nebo dojde k chybě, vrácená hodnota je 0.

Pokud nezadáte TPM_RETURNCMD v parametru *fuFlags* , návratová hodnota je nenulová, pokud je funkce úspěšná, a 0, pokud selže. Chcete-li získat rozšířené informace o chybě, volejte příkaz [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Poznámky

Plovoucí místní nabídka se může objevit kdekoli na obrazovce. Další informace o zpracování chyb při vytváření místní nabídky najdete v tématu [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

## <a name="see-also"></a>Viz také

[CTRLTEST Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[DYNAMENU Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)
