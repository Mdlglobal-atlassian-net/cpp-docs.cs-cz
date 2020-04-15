---
title: CMenu – třída
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
ms.openlocfilehash: 5ec97d8cf039034078f29b38fb6a41d6ff9a5e53
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369982"
---
# <a name="cmenu-class"></a>CMenu – třída

Zapouzdření systému `HMENU`Windows .

## <a name="syntax"></a>Syntaxe

```
class CMenu : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMenu::CMenu](#cmenu)|Vytvoří `CMenu` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMenu::Nabídka příloh](#appendmenu)|Připojí novou položku na konec této nabídky.|
|[CMenu::Připojit](#attach)|Připojí popisovač nabídky systému Windows k objektu. `CMenu`|
|[CMenu::CheckMenuItem](#checkmenuitem)|Umístí zaškrtnutí vedle nebo odstraní zaškrtnutí z položky nabídky v rozbalovací nabídce.|
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|Umístí přepínací tlačítko vedle položky nabídky a odstraní přepínací tlačítko ze všech ostatních položek nabídky ve skupině.|
|[CMenu::CreateMenu](#createmenu)|Vytvoří prázdnou nabídku a `CMenu` připojí ji k objektu.|
|[CMenu::Nabídka CreatePopupMenu](#createpopupmenu)|Vytvoří prázdnou rozbalovací nabídku a `CMenu` připojí ji k objektu.|
|[CMenu::DeleteMenu](#deletemenu)|Odstraní zadanou položku z nabídky. Pokud má položka nabídky přidruženou rozbalovací nabídku, zničí popisovač rozbalovací nabídky a uvolní paměť, kterou používá.|
|[CMenu::DeleteTempMap](#deletetempmap)|Odstraní všechny `CMenu` dočasné objekty `FromHandle` vytvořené členovou funkcí.|
|[CMenu::DestroyMenu](#destroymenu)|Zničí nabídku připojenou `CMenu` k objektu a uvolní paměť, kterou nabídka obsazena.|
|[CMenu::Detach](#detach)|Odpojí popisovač nabídky systému Windows od objektu `CMenu` a vrátí popisovač.|
|[CMenu::DrawItem](#drawitem)|Volat rámci při změně vizuální aspekt nabídky nakreslené vlastníka.|
|[CMenu::EnableMenuItem](#enablemenuitem)|Povolí, zakáže nebo ztlumí (ztlumí) položku nabídky.|
|[CMenu::FromHandle](#fromhandle)|Vrátí ukazatel na `CMenu` objekt s popisovačem nabídky systému Windows.|
|[CMenu::GetDefaultItem](#getdefaultitem)|Určuje výchozí položku nabídky v zadané nabídce.|
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|Načte ID kontextu nápovědy přidružené k nabídce.|
|[CMenu::GetMenuInfo](#getmenuinfo)|Načte informace v konkrétní nabídce.|
|[CMenu::GetMenuItemCount](#getmenuitemcount)|Určuje počet položek v rozbalovací nabídce nebo v nabídce nejvyšší úrovně.|
|[Cmenu::GetMenuItemID](#getmenuitemid)|Získá identifikátor položky nabídky pro položku nabídky umístěnou na zadané pozici.|
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|Načte informace o položce nabídky.|
|[CMenu::GetMenuState](#getmenustate)|Vrátí stav zadané položky nabídky nebo počet položek v rozbalovací nabídce.|
|[CMenu::GetMenuString](#getmenustring)|Načte popisek zadané položky nabídky.|
|[CMenu::GetSafeHmenu](#getsafehmenu)|Vrátí `m_hMenu` zabalené tímto `CMenu` objektem.|
|[CMenu::GetPodMenu](#getsubmenu)|Načte ukazatel na rozbalovací nabídku.|
|[CMenu::InsertMenu](#insertmenu)|Vloží novou položku nabídky na zadanou pozici a přesune ostatní položky dolů v nabídce.|
|[CMenu::InsertMenuItem](#insertmenuitem)|Vloží novou položku nabídky na zadanou pozici v nabídce.|
|[CMenu::LoadMenu](#loadmenu)|Načte prostředek nabídky ze spustitelného souboru `CMenu` a připojí jej k objektu.|
|[CMenu::LoadMenuNepřím](#loadmenuindirect)|Načte nabídku ze šablony nabídky do paměti `CMenu` a připojí ji k objektu.|
|[CMenu::MeasureItem](#measureitem)|Volat rámci k určení dimenze nabídky při vytvoření nabídky nakreslené vlastníka.|
|[CMenu::ModifyMenu](#modifymenu)|Změní existující položku nabídky na zadané pozici.|
|[CMenu::RemoveMenu](#removemenu)|Odstraní položku nabídky s přidruženou rozbalovací nabídkou ze zadané nabídky.|
|[CMenu::SetDefaultItem](#setdefaultitem)|Nastaví výchozí položku nabídky pro zadanou nabídku.|
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|Nastaví ID kontextu nápovědy, které má být přidruženo k nabídce.|
|[CMenu::SetMenuInfo](#setmenuinfo)|Nastaví informace v konkrétní nabídce.|
|[CMenu::SetMenuItemBitmapy](#setmenuitembitmaps)|Přidruží zadané bitmapy značek zaškrtnutí k položce nabídky.|
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|Změní informace o položce nabídky.|
|[CMenu::TrackPopupMenu](#trackpopupmenu)|Zobrazí plovoucí rozbalovací nabídku v určeném umístění a sleduje výběr položek v rozbalovací nabídce.|
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|Zobrazí plovoucí rozbalovací nabídku v určeném umístění a sleduje výběr položek v rozbalovací nabídce.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CMenu::operátor HMENU](#operator_hmenu)|Načte popisovač objektu nabídky.|
|[CMenu::operátor !=](#operator_neq)|Určuje, zda dva objekty nabídky nejsou stejné.|
|[CMenu::operátor ==](#operator_eq_eq)|Určuje, zda jsou dva objekty nabídky stejné.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CMenu::m_hMenu](#m_hmenu)|Určuje popisovač nabídky systému Windows `CMenu` připojené k objektu.|

## <a name="remarks"></a>Poznámky

Poskytuje členské funkce pro vytváření, sledování, aktualizaci a zničení nabídky.

Vytvořte `CMenu` objekt v rámci zásobníku jako `CMenu`místní a pak volejte členské funkce společnosti a podle potřeby s novou nabídkou manipulujte. Dále zavolejte [CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu) a nastavte nabídku na okno, `CMenu` následované okamžitě voláním členské funkce [Odpojit](#detach) objektu. Členská `CWnd::SetMenu` funkce nastaví nabídku okna na novou nabídku, způsobí, že okno překreslí tak, aby odráželo změnu nabídky, a také předává vlastnictví nabídky do okna. Volání `Detach` odpojí HMENU od `CMenu` objektu, takže když `CMenu` místní proměnná předá `CMenu` mimo rozsah, destruktor objektu se nepokusí zničit nabídku, kterou již nevlastní. Samotná nabídka je automaticky zničena, když je okno zničeno.

Členská funkce [LoadMenuIndirect](#loadmenuindirect) můžete použít k vytvoření nabídky ze šablony v paměti, ale nabídka vytvořená ze zdroje voláním [LoadMenu](#loadmenu) je snadněji udržována a samotný prostředek nabídky může být vytvořen a upraven editorem nabídky.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cmenuappendmenu"></a><a name="appendmenu"></a>CMenu::Nabídka příloh

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

*nPříznaky*<br/>
Určuje informace o stavu nové položky nabídky při přidání do nabídky. Skládá se z jedné nebo více hodnot uvedených v části Poznámky.

*nIDNewItem*<br/>
Určuje buď ID příkazu nové položky nabídky, nebo, pokud je funkce `HMENU` *nFlags* nastavena na MF_POPUP, popisovač nabídky ( ) rozbalovací nabídky. Parametr *nIDNewItem* je ignorován (není potřeba), pokud je *parametr nFlags* nastaven na MF_SEPARATOR.

*lpszNewItem*<br/>
Určuje obsah nové položky nabídky. Parametr *nFlags* se používá k interpretaci *lpszNewItem* následujícím způsobem:

|nPříznaky|Interpretace lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Obsahuje 32bitovou hodnotu dodanou aplikací, kterou může aplikace použít k udržování dalších dat přidružených k položce nabídky. Tato 32bitová hodnota je k dispozici pro aplikaci při procesu WM_MEASUREITEM a WM_DRAWITEM zprávy. Hodnota je uložena `itemData` v člen struktury dodávané s těmito zprávami.|
|MF_STRING|Obsahuje ukazatel na řetězec ukončený nulou. Toto je výchozí interpretace.|
|MF_SEPARATOR|Parametr *lpszNewItem* je ignorován (není potřeba).|

*pBmp*<br/>
Odkazuje na `CBitmap` objekt, který bude použit jako položka nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace může určit stav položky nabídky nastavením hodnot v *nFlags*. Když *nIDNewItem* určuje rozbalovací nabídku, stane se součástí nabídky, ke které je připojen. Pokud je tato nabídka zničena, bude zničena i připojená nabídka. Připojená nabídka by měla `CMenu` být odpojena od objektu, aby nedošlo ke konfliktu. Všimněte si, že MF_STRING a MF_OWNERDRAW `AppendMenu`nejsou platné pro bitmapovou verzi aplikace .

Následující seznam popisuje příznaky, které mohou být nastaveny v *nFlags*:

- MF_CHECKED Jako přepínač s MF_UNCHECKED umístíte výchozí značku zaškrtnutí vedle položky. Když aplikace poskytuje bitmapy zaškrtnutí (viz členská funkce [SetMenuItemBitmaps),](#setmenuitembitmaps) zobrazí se bitmapa "zaškrtnutí na".

- MF_UNCHECKED Jako přepínač s MF_CHECKED odstraní zaškrtnutí vedle položky. Když aplikace poskytuje bitmapy zaškrtnutí (viz `SetMenuItemBitmaps` členská funkce), zobrazí se bitmapa "zaškrtnutí".

- MF_DISABLED Zakáže položku nabídky tak, aby ji nebylo možné vybrat, ale neztlumí ji.

- MF_ENABLED Povolí položku nabídky tak, aby ji bylo možné vybrat a obnoví ji z jeho šedě stavu.

- MF_GRAYED Zakáže položku nabídky tak, aby ji nebylo možné vybrat, a ztlumí ji.

- MF_MENUBARBREAK Umístí položku na nový řádek ve statických nabídkách nebo do nového sloupce v rozbalovacích nabídkách. Nový sloupec rozbalovací nabídky bude oddělen od starého sloupce svislou dělicí čárou.

- MF_MENUBREAK Umístí položku na nový řádek do statických nabídek nebo do nového sloupce v rozbalovacích nabídkách. Mezi sloupce není umístěna žádná dělicí čára.

- MF_OWNERDRAW Určuje, že položka je položka kreslení vlastníka. Při prvním zobrazení nabídky okno, které je vlastní nabídku obdrží zprávu WM_MEASUREITEM, která načte výšku a šířku položky nabídky. Zpráva WM_DRAWITEM je zpráva odeslaná vždy, když vlastník musí aktualizovat vizuální vzhled položky nabídky. Tato možnost není platná pro položku nabídky nejvyšší úrovně.

- MF_POPUP Určuje, že k položce nabídky je přidružena rozbalovací nabídka. Parametr ID určuje popisovač rozbalovací nabídky, která má být přidružena k položce. Používá se k přidání rozbalovací nabídky nejvyšší úrovně nebo hierarchické rozbalovací nabídky k položce rozbalovací nabídky.

- MF_SEPARATOR nakreslí vodorovnou dělicí čáru. Lze použít pouze v rozbalovací nabídce. Tento řádek nelze ztlumit, zakázat ani zvýraznit. Ostatní parametry jsou ignorovány.

- MF_STRING Určuje, že položka nabídky je řetězec znaků.

Každá z následujících skupin uvádí příznaky, které se vzájemně vylučují a nelze je použít společně:

- MF_DISABLED, MF_ENABLED a MF_GRAYED

- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR a bitmapovou verzi

- MF_MENUBARBREAK a MF_MENUBREAK

- MF_CHECKED a MF_UNCHECKED

Při každé změně nabídky, která je umístěna v okně (bez ohledu na to, zda je okno zobrazeno), by aplikace měla volat [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::CreateMenu](#createmenu).

## <a name="cmenuattach"></a><a name="attach"></a>CMenu::Připojit

Připojí existující nabídku systému Windows k objektu. `CMenu`

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hNabídka*<br/>
Určuje popisovač nabídky systému Windows.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla operace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce by neměla být volána, `CMenu` pokud je nabídka již připojena k objektu. Popisovač nabídky je `m_hMenu` uložen v datovém prvku.

Pokud je nabídka, se kterou chcete manipulovat, již přidružena k oknu, můžete pomocí funkce [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu) získat popisovač do nabídky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenucheckmenuitem"></a><a name="checkmenuitem"></a>CMenu::CheckMenuItem

Přidá zaškrtnutí nebo odstraní zaškrtnutí z položek nabídky v rozbalovací nabídce.

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>Parametry

*nIDCheckItem*<br/>
Určuje položku nabídky, která má být zkontrolována, jak je určena *nCheck*.

*nKontrola*<br/>
Určuje, jak zkontrolovat položku nabídky a jak určit polohu položky v nabídce. Parametr *nCheck* může být kombinací MF_CHECKED nebo MF_UNCHECKED s příznaky MF_BYPOSITION nebo MF_BYCOMMAND. Tyto příznaky lze kombinovat pomocí bitového operátoru OR. Mají následující významy:

- MF_BYCOMMAND Určuje, že parametr udává ID příkazu existující položky nabídky. Toto nastavení je výchozí.

- MF_BYPOSITION Určuje, že parametr udává umístění existující položky nabídky. První položka je na pozici 0.

- MF_CHECKED Jako přepínač s MF_UNCHECKED umístíte výchozí značku zaškrtnutí vedle položky.

- MF_UNCHECKED Jako přepínač s MF_CHECKED odstraní zaškrtnutí vedle položky.

### <a name="return-value"></a>Návratová hodnota

Předchozí stav položky: MF_CHECKED nebo MF_UNCHECKED nebo 0xFFFFFFFF, pokud položka nabídky neexistovala.

### <a name="remarks"></a>Poznámky

Parametr *nIDCheckItem* určuje položku, která má být změněna.

Parametr *nIDCheckItem* může identifikovat položku rozbalovací nabídky i položku nabídky. Ke kontrole položky rozbalovací nabídky nejsou nutné žádné speciální kroky. Položky nabídky nejvyšší úrovně nelze zkontrolovat. Položka rozbalovací nabídky musí být zkontrolována podle pozice, protože k ní není přidružen identifikátor položky nabídky.

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::GetMenuState](#getmenustate).

## <a name="cmenucheckmenuradioitem"></a><a name="checkmenuradioitem"></a>CMenu::CheckMenuRadioItem

Zkontroluje zadanou položku nabídky a znívás ji za rádiovou položku.

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*nIDPrvní*<br/>
Určuje (jako ID nebo posun, v závislosti na hodnotě *nFlags)* první položku nabídky ve skupině přepínacích tlačítek.

*nIDLast*<br/>
Určuje (jako ID nebo posun, v závislosti na hodnotě *nFlags)* poslední položku nabídky ve skupině přepínacích tlačítek.

*nIDPoložka*<br/>
Určuje (jako ID nebo posun, v závislosti na hodnotě *nFlags)* položku ve skupině, která bude zkontrolována pomocí přepínacího tlačítka.

*nPříznaky*<br/>
Určuje interpretaci *nIDFirst*, *nIDLast*a *nIDItem* následujícím způsobem:

|nPříznaky|Interpretace|
|------------|--------------------|
|MF_BYCOMMAND|Určuje, že parametr udává ID příkazu existující položky nabídky. Toto je výchozí nastavení, pokud není nastavena MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr udává umístění existující položky nabídky. První položka je na pozici 0.|

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0

### <a name="remarks"></a>Poznámky

Současně funkce zrušit kontroly všech ostatních položek nabídky v přidružené skupině a vymaže příznak typu položky rádia pro tyto položky. Zaškrtnutá položka se zobrazí pomocí bitmapy přepínacího tlačítka (nebo odrážky) namísto bitmapy zaškrtnutí značky.

### <a name="example"></a>Příklad

  Viz příklad pro [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).

## <a name="cmenucmenu"></a><a name="cmenu"></a>CMenu::CMenu

Vytvoří prázdnou nabídku a `CMenu` připojí ji k objektu.

```
CMenu();
```

### <a name="remarks"></a>Poznámky

Nabídka není vytvořena, dokud nezavoláte jednu z funkcí vytváření nebo načítání členů`CMenu:`

- [Vytvořitnabídku](#createmenu)

- [Vytvořit nabídku Popup](#createpopupmenu)

- [Nabídka Load](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [Připojit](#attach)

## <a name="cmenucreatemenu"></a><a name="createmenu"></a>CMenu::CreateMenu

Vytvoří nabídku a připojí `CMenu` ji k objektu.

```
BOOL CreateMenu();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla nabídka úspěšně vytvořena; jinak 0.

### <a name="remarks"></a>Poznámky

Nabídka je zpočátku prázdná. Položky nabídky lze přidat `AppendMenu` `InsertMenu` pomocí členské funkce nebo.

Pokud je nabídka přiřazena k oknu, je automaticky zničena při zničení okna.

Před ukončením aplikace musí uvolnit systémové prostředky přidružené k nabídce, pokud nabídka není přiřazena k oknu. Aplikace uvolní nabídku voláním funkce [člena DestroyMenu.](#destroymenu)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

## <a name="cmenucreatepopupmenu"></a><a name="createpopupmenu"></a>CMenu::Nabídka CreatePopupMenu

Vytvoří rozbalovací nabídku a připojí `CMenu` ji k objektu.

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla rozbalovací nabídka úspěšně vytvořena; jinak 0.

### <a name="remarks"></a>Poznámky

Nabídka je zpočátku prázdná. Položky nabídky lze přidat `AppendMenu` `InsertMenu` pomocí členské funkce nebo. Aplikace může přidat rozbalovací nabídku do existující nabídky nebo rozbalovací nabídky. Členská `TrackPopupMenu` funkce může být použita k zobrazení této nabídky jako plovoucí rozbalovací nabídky a ke sledování výběrů v rozbalovací nabídce.

Pokud je nabídka přiřazena k oknu, je automaticky zničena při zničení okna. Pokud je nabídka přidána do existující nabídky, je automaticky zničena, když je tato nabídka zničena.

Před ukončením musí aplikace uvolnit systémové prostředky přidružené k rozbalovací nabídce, pokud nabídka není přiřazena k oknu. Aplikace uvolní nabídku voláním funkce [člena DestroyMenu.](#destroymenu)

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::CreateMenu](#createmenu).

## <a name="cmenudeletemenu"></a><a name="deletemenu"></a>CMenu::DeleteMenu

Odstraní položku z nabídky.

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*nPozice*<br/>
Určuje položku nabídky, která má být odstraněna, jak je určeno *nFlags*.

*nPříznaky*<br/>
Používá se k interpretaci *nPosition* následujícím způsobem:

|nPříznaky|Interpretace nPozice|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr udává ID příkazu existující položky nabídky. Toto je výchozí nastavení, pokud není nastavena MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr udává umístění existující položky nabídky. První položka je na pozici 0.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud má položka nabídky přidruženou rozbalovací nabídku, `DeleteMenu` zničí popisovač rozbalovací nabídky a uvolní paměť používanou rozbalovací nabídkou.

Při každé změně nabídky, která je umístěna v okně (bez ohledu na to, zda je okno zobrazeno), musí aplikace volat [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Příklad

  Viz příklad pro [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

## <a name="cmenudeletetempmap"></a><a name="deletetempmap"></a>CMenu::DeleteTempMap

Volána automaticky `CWinApp` obslužnou rutinou `CMenu` doby nečinnosti, odstraní všechny dočasné objekty vytvořené členovou funkcí [FromHandle.](#fromhandle)

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Poznámky

`DeleteTempMap`Před odstraněním objektu odpojí objekt `CMenu` nabídky systému `CMenu` Windows připojený k dočasnému objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

## <a name="cmenudestroymenu"></a><a name="destroymenu"></a>CMenu::DestroyMenu

Zničí nabídku a všechny prostředky systému Windows, které byly použity.

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je nabídka zničena; jinak 0.

### <a name="remarks"></a>Poznámky

Nabídka je odpojena `CMenu` od objektu před jeho zničením. Funkce `DestroyMenu` systému Windows je `CMenu` automaticky volána v destruktoru.

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::CreateMenu](#createmenu).

## <a name="cmenudetach"></a><a name="detach"></a>CMenu::Detach

Odpojí nabídku systému `CMenu` Windows od objektu a vrátí popisovač.

```
HMENU Detach();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač typu HMENU do nabídky systému Windows, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Datový `m_hMenu` člen je nastaven na hodnotu NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenudrawitem"></a><a name="drawitem"></a>CMenu::DrawItem

Volat rámci při změně vizuální aspekt nabídky nakreslené vlastníka.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel na strukturu [DRAWITEMSTRUCT,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) která obsahuje informace o požadovaném typu výkresu.

### <a name="remarks"></a>Poznámky

Člen `itemAction` `DRAWITEMSTRUCT` struktury definuje kreslicí akci, která má být provedena. Přepsat tuto členovou funkci implementovat výkres `CMenu` pro objekt nakreslení vlastníka. Aplikace by měla obnovit všechny objekty rozhraní grafického zařízení (GDI) vybrané pro kontext zobrazení dodaný v *lpDrawItemStruct* před ukončením této členské funkce.

Viz [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) popis `DRAWITEMSTRUCT` struktury.

### <a name="example"></a>Příklad

Následující kód je z ukázky [knihovny CtrlTEST:](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

## <a name="cmenuenablemenuitem"></a><a name="enablemenuitem"></a>CMenu::EnableMenuItem

Povolí, zakáže nebo ztlumí položku nabídky.

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>Parametry

*nIDEnableItem*<br/>
Určuje položku nabídky, která má být povolena, podle *nEnable*. Tento parametr může určit položky rozbalovací nabídky a také standardní položky nabídky.

*nPovolit*<br/>
Určuje akci, která má být vyvedena. Může to být kombinace MF_DISABLED, MF_ENABLED nebo MF_GRAYED, s MF_BYCOMMAND nebo MF_BYPOSITION. Tyto hodnoty lze kombinovat pomocí bitového operátoru OR. Tyto hodnoty mají následující význam:

- MF_BYCOMMAND Určuje, že parametr udává ID příkazu existující položky nabídky. Toto nastavení je výchozí.

- MF_BYPOSITION Určuje, že parametr udává umístění existující položky nabídky. První položka je na pozici 0.

- MF_DISABLED Zakáže položku nabídky tak, aby ji nebylo možné vybrat, ale neztlumí ji.

- MF_ENABLED Povolí položku nabídky tak, aby ji bylo možné vybrat a obnoví ji z jeho šedě stavu.

- MF_GRAYED Zakáže položku nabídky tak, aby ji nebylo možné vybrat, a ztlumí ji.

### <a name="return-value"></a>Návratová hodnota

Předchozí stav ( MF_DISABLED, MF_ENABLED nebo MF_GRAYED) nebo -1, pokud není platný.

### <a name="remarks"></a>Poznámky

Funkce [CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu)a [LoadMenuIndirect](#loadmenuindirect) mohou také nastavit stav (povolený, zakázaný nebo šedě) položky nabídky.

Použití hodnoty MF_BYPOSITION vyžaduje, aby `CMenu`aplikace používala správné použití . `CMenu` Pokud je použit řádek nabídek, bude ovlivněna položka nabídky nejvyšší úrovně (položka v řádku nabídek). Chcete-li nastavit stav položky v rozbalovací nebo vnořené rozbalovací nabídce podle polohy, musí aplikace zadat `CMenu` rozbalovací nabídku.

Pokud aplikace určuje příznak MF_BYCOMMAND, systém Windows zkontroluje všechny položky `CMenu`rozbalovací nabídky, které jsou podřízené ; proto, pokud duplicitní položky `CMenu` nabídky jsou k dispozici, pomocí řádku nabídek je dostačující.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

## <a name="cmenufromhandle"></a><a name="fromhandle"></a>CMenu::FromHandle

Vrátí ukazatel na `CMenu` objekt, který má popisovač systému Windows, do nabídky.

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hNabídka*<br/>
Popisovač systému Windows do nabídky.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CMenu` a, který může být dočasný nebo trvalý.

### <a name="remarks"></a>Poznámky

Pokud `CMenu` objekt ještě není připojen k objektu nabídky `CMenu` systému Windows, je vytvořen a připojen dočasný objekt.

Tento `CMenu` dočasný objekt je platný pouze do příště aplikace má dobu nečinnosti ve smyčce událostí, kdy jsou odstraněny všechny dočasné objekty.

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::CreateMenu](#createmenu).

## <a name="cmenugetdefaultitem"></a><a name="getdefaultitem"></a>CMenu::GetDefaultItem

Určuje výchozí položku nabídky v zadané nabídce.

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*vlajky gmdi*<br/>
Hodnota určující způsob, jakým funkce vyhledává položky nabídky. Tento parametr může být žádná, jedna nebo kombinace následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|Určuje, že pokud je výchozí položkou položka, která otevře podnabídku, je funkcí rekurzivně prohledávat v odpovídající podnabídce. Pokud podnabídka nemá žádnou výchozí položku, vrácená hodnota identifikuje položku, která podnabídku otevře.<br /><br /> Ve výchozím nastavení vrátí funkce první výchozí položku v zadané nabídce bez ohledu na to, zda se jedná o položku, která otevře podnabídku.|
|GMDI_USEDISABLED|Určuje, že funkce má vrátit výchozí položku, i když je zakázána.<br /><br /> Ve výchozím nastavení funkce přeskočí zakázané nebo šedé položky.|

*fByPos*<br/>
Hodnota určující, zda má být načten identifikátor položky nabídky nebo její umístění. Pokud je tento parametr FALSE, je vrácen identifikátor. V opačném případě je vrácena pozice.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je identifikátor nebo umístění položky nabídky. Pokud funkce selže, vrácená hodnota je - 1.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování funkce Win32 [GetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetmenucontexthelpid"></a><a name="getmenucontexthelpid"></a>CMenu::GetMenuContextHelpId

Načte ID nápovědy `CMenu`kontextu přidružené k aplikaci .

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>Návratová hodnota

Kontext id nápovědy aktuálně `CMenu` přidružené, pokud má jeden; nula jinak.

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetmenuinfo"></a><a name="getmenuinfo"></a>CMenu::GetMenuInfo

Načte informace pro nabídku.

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>Parametry

*lpcmi*<br/>
Ukazatel na strukturu [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) obsahující informace pro nabídku.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je nenulová; jinak je vrácená hodnota nulová.

### <a name="remarks"></a>Poznámky

Volání této funkce pro načtení informací o nabídce.

## <a name="cmenugetmenuitemcount"></a><a name="getmenuitemcount"></a>CMenu::GetMenuItemCount

Určuje počet položek v rozbalovací nabídce nebo v nabídce nejvyšší úrovně.

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v nabídce, pokud je funkce úspěšná; jinak -1.

### <a name="example"></a>Příklad

  Viz příklad pro [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

## <a name="cmenugetmenuitemid"></a><a name="getmenuitemid"></a>Cmenu::GetMenuItemID

Získá identifikátor položky nabídky pro položku nabídky umístěnou na pozici definované *nPos*.

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje pozici (od nuly) položky nabídky, jejíž ID je načítáno.

### <a name="return-value"></a>Návratová hodnota

ID položky pro zadanou položku v rozbalovací nabídce, pokud je funkce úspěšná. Pokud je zadanou položkou rozbalovací nabídka (na rozdíl od položky v rozbalovací nabídce), vrácená hodnota je -1. Pokud *nPos* odpovídá položce nabídky SEPARATOR, vrácená hodnota je 0.

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetmenuiteminfo"></a><a name="getmenuiteminfo"></a>CMenu::GetMenuItemInfo

Načte informace o položce nabídky.

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uPoložka*<br/>
Identifikátor nebo umístění položky nabídky, o které můžete získat informace. Význam tohoto parametru závisí na `ByPos`hodnotě .

*lpMenuItemInfo*<br/>
Ukazatel na [soubor MENUITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow), jak je popsáno v sadě Windows SDK, který obsahuje informace o nabídce.

*fByPos*<br/>
Hodnota určující význam `nIDItem`. Ve výchozím `ByPos` nastavení je NEPRAVDA, což znamená, že uItem je identifikátor položky nabídky. Pokud `ByPos` není nastavena na hodnotu NEPRAVDA, označuje pozici položky nabídky.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je nenulová. Pokud funkce selže, vrácená hodnota je nula. Chcete-li získat rozšířené informace o chybách, použijte funkci [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)systému Win32 , jak je popsáno v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování funkce Win32 [GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow), jak je popsáno v sadě Windows SDK. Všimněte si, že `GetMenuItemInfo`v implementaci knihovny MFC , nepoužíváte popisovač nabídky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

## <a name="cmenugetmenustate"></a><a name="getmenustate"></a>CMenu::GetMenuState

Vrátí stav zadané položky nabídky nebo počet položek v rozbalovací nabídce.

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Určuje ID položky nabídky určené *nFlags*.

*nPříznaky*<br/>
Určuje povahu *nID*. Může to být jedna z následujících hodnot:

- MF_BYCOMMAND Určuje, že parametr udává ID příkazu existující položky nabídky. Toto nastavení je výchozí.

- MF_BYPOSITION Určuje, že parametr udává umístění existující položky nabídky. První položka je na pozici 0.

### <a name="return-value"></a>Návratová hodnota

Hodnota 0xFFFFFFFF, pokud zadaná položka neexistuje. Pokud *nId* identifikuje rozbalovací nabídku, bajt vyššího řádu obsahuje počet položek v rozbalovací nabídce a bajt nižšího řádu obsahuje příznaky nabídky přidružené k rozbalovací nabídce. V opačném případě je vrácená hodnota maskou (Boolean OR) hodnot z následujícího seznamu (tato maska popisuje stav položky nabídky, kterou *nId* identifikuje):

- MF_CHECKED Jako přepínač s MF_UNCHECKED umístíte výchozí značku zaškrtnutí vedle položky. Když aplikace poskytuje bitmapy zaškrtnutí (viz `SetMenuItemBitmaps` členská funkce), zobrazí se bitmapa "zaškrtnutí na".

- MF_DISABLED Zakáže položku nabídky tak, aby ji nebylo možné vybrat, ale neztlumí ji.

- MF_ENABLED Povolí položku nabídky tak, aby ji bylo možné vybrat a obnoví ji z jeho šedě stavu. Všimněte si, že hodnota této konstanty je 0; aplikace by neměla testovat proti 0 pro selhání při použití této hodnoty.

- MF_GRAYED Zakáže položku nabídky tak, aby ji nebylo možné vybrat, a ztlumí ji.

- MF_MENUBARBREAK Umístí položku na nový řádek ve statických nabídkách nebo do nového sloupce v rozbalovacích nabídkách. Nový sloupec rozbalovací nabídky bude oddělen od starého sloupce svislou dělicí čárou.

- MF_MENUBREAK Umístí položku na nový řádek do statických nabídek nebo do nového sloupce v rozbalovacích nabídkách. Mezi sloupce není umístěna žádná dělicí čára.

- MF_SEPARATOR nakreslí vodorovnou dělicí čáru. Lze použít pouze v rozbalovací nabídce. Tento řádek nelze ztlumit, zakázat ani zvýraznit. Ostatní parametry jsou ignorovány.

- MF_UNCHECKED Jako přepínač s MF_CHECKED odstraní zaškrtnutí vedle položky. Když aplikace poskytuje bitmapy zaškrtnutí (viz `SetMenuItemBitmaps` členská funkce), zobrazí se bitmapa "zaškrtnutí". Všimněte si, že hodnota této konstanty je 0; aplikace by neměla testovat proti 0 pro selhání při použití této hodnoty.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

## <a name="cmenugetmenustring"></a><a name="getmenustring"></a>CMenu::GetMenuString

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

*nIDPoložka*<br/>
Určuje identifikátor celéčíslo položky nabídky nebo posun položky nabídky v nabídce v závislosti na hodnotě *nFlags*.

*lpString*<br/>
Odkazuje na vyrovnávací paměť, která má přijmout popisek.

*rString*<br/>
Odkaz na `CString` objekt, který má přijímat zkopírovaný řetězec nabídky.

*nMaxCount*<br/>
Určuje maximální délku (ve zkopírování) popisku, který má být zkopírován. Pokud je popisek delší než maximální zadaný v *nMaxCount*, jsou další znaky zkráceny.

*nPříznaky*<br/>
Určuje interpretaci parametru *nIDItem.* Může to být jedna z následujících hodnot:

|nPříznaky|Interpretace položky nIDItem|
|------------|-------------------------------|
|MF_BYCOMMAND|Určuje, že parametr udává ID příkazu existující položky nabídky. Toto je výchozí nastavení, pokud není nastavena MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr udává umístění existující položky nabídky. První položka je na pozici 0.|

### <a name="return-value"></a>Návratová hodnota

Určuje skutečný počet znaků zkopírovaných do vyrovnávací paměti, bez zakončení null.

### <a name="remarks"></a>Poznámky

Parametr *nMaxCount* by měl být o jeden větší než počet znaků v popisku, aby se přizpůsobil nulovému znaku, který ukončí řetězec.

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetsafehmenu"></a><a name="getsafehmenu"></a>CMenu::GetSafeHmenu

Vrátí hmenu zabalené tímto `CMenu` objektem`CMenu` nebo ukazatel NULL.

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>Příklad

  Viz příklad [pro CMenu::LoadMenu](#loadmenu).

## <a name="cmenugetsubmenu"></a><a name="getsubmenu"></a>CMenu::GetPodMenu

Načte `CMenu` objekt rozbalovací nabídky.

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje umístění rozbalovací nabídky obsažené v nabídce. Hodnoty polohy začínají na hodnotě 0 pro první položku nabídky. Identifikátor rozbalovací nabídky nelze v této funkci použít.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CMenu` objekt, `m_hMenu` jehož člen obsahuje popisovač rozbalovací nabídky, pokud v dané pozici existuje rozbalovací nabídka; jinak NULL. Pokud `CMenu` objekt neexistuje, je vytvořen dočasný objekt. Vrácený `CMenu` ukazatel by neměl být uložen.

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::TrackPopupMenu](#trackpopupmenu).

## <a name="cmenuinsertmenu"></a><a name="insertmenu"></a>CMenu::InsertMenu

Vloží novou položku nabídky na pozici určenou *nPosition* a přesune další položky dolů v nabídce.

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

*nPozice*<br/>
Určuje položku nabídky, před kterou má být nová položka nabídky vložena. Parametr *nFlags* lze použít k interpretaci *nPosition* následujícími způsoby:

|nPříznaky|Interpretace nPozice|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr udává ID příkazu existující položky nabídky. Toto je výchozí nastavení, pokud není nastavena MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr udává umístění existující položky nabídky. První položka je na pozici 0. Pokud *nPosition* je -1, nová položka nabídky je připojen a na konec nabídky.|

*nPříznaky*<br/>
Určuje způsob interpretace *nPozice* a informace o stavu nové položky nabídky při přidání do nabídky. Seznam příznaků, které mohou být nastaveny, naleznete v tématu [ApendMenu](#appendmenu) členské funkce. Chcete-li zadat více než jednu hodnotu, použijte bitový operátor OR a zkombinujte je s příznakem MF_BYCOMMAND nebo MF_BYPOSITION.

*nIDNewItem*<br/>
Určuje buď ID příkazu nové položky nabídky, nebo, pokud je *nFlags* nastavena na MF_POPUP, popisovač nabídky (HMENU) rozbalovací nabídky. Parametr *nIDNewItem* je ignorován (není potřeba), pokud je *parametr nFlags* nastaven na MF_SEPARATOR.

*lpszNewItem*<br/>
Určuje obsah nové položky nabídky. *nFlags* lze interpretovat *lpszNewItem* následujícími způsoby:

|nPříznaky|Interpretace lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Obsahuje 32bitovou hodnotu dodanou aplikací, kterou může aplikace použít k udržování dalších dat přidružených k položce nabídky. Tato 32bitová hodnota je k `itemData` dispozici pro aplikaci v člen struktury dodané [WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem) a [WM_DRAWITEM](/windows/win32/Controls/wm-drawitem) zprávy. Tyto zprávy jsou odesílány při počátečním zobrazení nebo změně položky nabídky.|
|MF_STRING|Obsahuje dlouhý ukazatel na řetězec ukončený nulou. Toto je výchozí interpretace.|
|MF_SEPARATOR|Parametr *lpszNewItem* je ignorován (není potřeba).|

*pBmp*<br/>
Odkazuje na `CBitmap` objekt, který bude použit jako položka nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace může určit stav položky nabídky nastavením hodnot v *nFlags*.

Při každé změně nabídky, která je umístěna v okně (bez ohledu `CWnd::DrawMenuBar`na to, zda je okno zobrazeno), by měla aplikace volat .

Když *nIDNewItem* určuje rozbalovací nabídku, stane se součástí nabídky, ve které je vložen. Pokud je toto menu zničeno, vložená nabídka bude také zničena. Vložená nabídka by měla `CMenu` být odpojena od objektu, aby nedošlo ke konfliktu.

Pokud je podřízené okno rozhraní MDI (Active Multiple document interface) maximalizované a aplikace vloží rozbalovací nabídku do nabídky aplikace MDI voláním této funkce a zadáním příznaku MF_BYPOSITION, je nabídka vložena o jednu pozici dále doleva, než bylo očekáváno. K tomu dochází, protože ovládací nabídka aktivního podřízeného okna MDI je vložena do první pozice panelu nabídek okna rámce MDI. Chcete-li správně umístit nabídku, aplikace musí přidat 1 k hodnotě pozice, která by jinak byla použita. Aplikace může použít zprávu WM_MDIGETACTIVE k určení, zda je maximalizované aktuálně aktivní podřízené okno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

## <a name="cmenuinsertmenuitem"></a><a name="insertmenuitem"></a>CMenu::InsertMenuItem

Vloží novou položku nabídky na zadanou pozici v nabídce.

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uPoložka*<br/>
Viz popis *uItem* v [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw) v sadě Windows SDK.

*lpMenuItemInfo*<br/>
Viz popis *lpmii* v `InsertMenuItem` souboru Windows SDK.

*fByPos*<br/>
Viz popis *fByPosition* v `InsertMenuItem` souboru Windows SDK.

### <a name="remarks"></a>Poznámky

Tato funkce zabalí [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw), popsané v sadě Windows SDK.

## <a name="cmenuloadmenu"></a><a name="loadmenu"></a>CMenu::LoadMenu

Načte prostředek nabídky ze spustitelného souboru aplikace `CMenu` a připojí jej k objektu.

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje název prostředku nabídky, který má být načíst.

*nIDZdroj*<br/>
Určuje ID nabídky prostředku nabídky, který má být načíst.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl prostředek nabídky úspěšně načten; jinak 0.

### <a name="remarks"></a>Poznámky

Před ukončením aplikace musí uvolnit systémové prostředky přidružené k nabídce, pokud nabídka není přiřazena k oknu. Aplikace uvolní nabídku voláním funkce [člena DestroyMenu.](#destroymenu)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

## <a name="cmenuloadmenuindirect"></a><a name="loadmenuindirect"></a>CMenu::LoadMenuNepřím

Načte prostředek ze šablony nabídky do paměti `CMenu` a připojí jej k objektu.

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>Parametry

*lpMenuTemplate*<br/>
Odkazuje na šablonu nabídky (což je jedna struktura [MENUITEMTEMPLATEHEADER](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader) a kolekce jedné nebo více struktur [MENUITEMTEMPLATE).](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) Další informace o těchto dvou strukturách naleznete v souboru Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl prostředek nabídky úspěšně načten; jinak 0.

### <a name="remarks"></a>Poznámky

Šablona nabídky je záhlaví následované kolekcí jedné nebo více struktur [MENUITEMTEMPLATE,](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) z nichž každá může obsahovat jednu nebo více položek nabídky a rozbalovacích nabídek.

Číslo verze by mělo být 0.

Příznaky `mtOption` by měly obsahovat MF_END pro poslední položku v rozbalovacím seznamu a pro poslední položku v hlavním seznamu. Viz `AppendMenu` členské funkce pro ostatní příznaky. Člen `mtId` musí být vynechán ze struktury MENUITEMTEMPLATE, `mtOption`pokud je v písmenu MF_POPUP zadáno.

Místo přidělené pro strukturu MENUITEMTEMPLATE musí `mtString` být dostatečně velké, aby obsahovalo název položky nabídky jako řetězec ukončený nulou.

Před ukončením aplikace musí uvolnit systémové prostředky přidružené k nabídce, pokud nabídka není přiřazena k oknu. Aplikace uvolní nabídku voláním funkce [člena DestroyMenu.](#destroymenu)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

## <a name="cmenum_hmenu"></a><a name="m_hmenu"></a>CMenu::m_hMenu

Určuje úchyt HMENU nabídky Systému `CMenu` Windows připojené k objektu.

```
HMENU m_hMenu;
```

### <a name="example"></a>Příklad

  Viz příklad [pro CMenu::LoadMenu](#loadmenu).

## <a name="cmenumeasureitem"></a><a name="measureitem"></a>CMenu::MeasureItem

Volána rámci při vytvoření nabídky se stylem kreslení vlastníka.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Ukazatel na `MEASUREITEMSTRUCT` strukturu.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato členská funkce neprovede žádné. Přepsat tuto člennou funkci `MEASUREITEMSTRUCT` a vyplnit strukturu informovat Windows o rozměrech nabídky.

Viz [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) pro popis `MEASUREITEMSTRUCT` struktury.

### <a name="example"></a>Příklad

Následující kód je z ukázky [knihovny CtrlTEST:](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

## <a name="cmenumodifymenu"></a><a name="modifymenu"></a>CMenu::ModifyMenu

Změní existující položku nabídky na pozici určené *nPosition*.

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

*nPozice*<br/>
Určuje položku nabídky, která má být změněna. Parametr *nFlags* lze použít k interpretaci *nPosition* následujícími způsoby:

|nPříznaky|Interpretace nPozice|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr udává ID příkazu existující položky nabídky. Toto je výchozí nastavení, pokud není nastavena MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr udává umístění existující položky nabídky. První položka je na pozici 0.|

*nPříznaky*<br/>
Určuje způsob interpretace *funkce nPosition* a poskytuje informace o změnách, které mají být provedeny v položce nabídky. Seznam příznaků, které mohou být nastaveny, naleznete v tématu [ApendMenu](#appendmenu) členské funkce.

*nIDNewItem*<br/>
Určuje buď ID příkazu upravené položky nabídky, nebo, pokud je *funkce nFlags* nastavena na MF_POPUP, popisovač nabídky (HMENU) rozbalovací nabídky. Parametr *nIDNewItem* je ignorován (není potřeba), pokud je *parametr nFlags* nastaven na MF_SEPARATOR.

*lpszNewItem*<br/>
Určuje obsah nové položky nabídky. Parametr *nFlags* lze použít k interpretaci *lpszNewItem* následujícími způsoby:

|nPříznaky|Interpretace lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Obsahuje 32bitovou hodnotu dodanou aplikací, kterou může aplikace použít k udržování dalších dat přidružených k položce nabídky. Tato 32bitová hodnota je k dispozici pro aplikaci při procesu MF_MEASUREITEM a MF_DRAWITEM.|
|MF_STRING|Obsahuje dlouhý ukazatel na řetězec ukončený nulou `CString`nebo na řetězec .|
|MF_SEPARATOR|Parametr *lpszNewItem* je ignorován (není potřeba).|

*pBmp*<br/>
Odkazuje na `CBitmap` objekt, který bude použit jako položka nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace určuje nový stav položky nabídky nastavením hodnot v *nFlags*. Pokud tato funkce nahradí rozbalovací nabídku přidruženou k položce nabídky, zničí starou rozbalovací nabídku a uvolní paměť používanou rozbalovací nabídkou.

Když *nIDNewItem* určuje rozbalovací nabídku, stane se součástí nabídky, ve které je vložen. Pokud je toto menu zničeno, vložená nabídka bude také zničena. Vložená nabídka by měla `CMenu` být odpojena od objektu, aby nedošlo ke konfliktu.

Při každé změně nabídky, která je umístěna v okně (bez ohledu `CWnd::DrawMenuBar`na to, zda je okno zobrazeno), by měla aplikace volat . Chcete-li změnit atributy existujících položek nabídky, `CheckMenuItem` je `EnableMenuItem` mnohem rychlejší použít a členské funkce.

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::InsertMenu](#insertmenu).

## <a name="cmenuoperator-hmenu"></a><a name="operator_hmenu"></a>CMenu::operátor HMENU

Tento operátor slouží k načtení popisovače objektu. `CMenu`

```
operator HMENU() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, `CMenu` popisovač objektu; jinak NULL.

### <a name="remarks"></a>Poznámky

Pomocí popisovače můžete volat přímo windows api.

## <a name="cmenuoperator-"></a><a name="operator_neq"></a>CMenu::operátor !=

Určuje, zda dvě nabídky logicky nejsou stejné.

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>Parametry

*Nabídky*<br/>
Objekt `CMenu` pro porovnání.

### <a name="remarks"></a>Poznámky

Testuje, pokud se objekt nabídky na levé straně nerovná objektu nabídky na pravé straně.

## <a name="cmenuoperator-"></a><a name="operator_eq_eq"></a>CMenu::operátor ==

Určuje, zda jsou dvě nabídky logicky stejné.

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>Parametry

*Nabídky*<br/>
Objekt `CMenu` pro porovnání.

### <a name="remarks"></a>Poznámky

Testuje, zda je objekt nabídky na levé straně stejný (z hlediska hodnoty HMENU) objektu nabídky na pravé straně.

## <a name="cmenuremovemenu"></a><a name="removemenu"></a>CMenu::RemoveMenu

Odstraní položku nabídky s přidruženou rozbalovací nabídkou z nabídky.

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*nPozice*<br/>
Určuje položku nabídky, která má být odebrána. Parametr *nFlags* lze použít k interpretaci *nPosition* následujícími způsoby:

|nPříznaky|Interpretace nPozice|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr udává ID příkazu existující položky nabídky. Toto je výchozí nastavení, pokud není nastavena MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr udává umístění existující položky nabídky. První položka je na pozici 0.|

*nPříznaky*<br/>
Určuje způsob interpretace *nPozice.*

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Nezničí popisovač pro rozbalovací nabídku, takže nabídku lze znovu použít. Před voláním této funkce může `GetSubMenu` aplikace volat členská `CMenu` funkce k načtení automaticky otevíraný objekt pro opakované použití.

Při každé změně nabídky, která je umístěna v okně (bez ohledu `CWnd::DrawMenuBar`na to, zda je okno zobrazeno), musí aplikace volat .

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::InsertMenu](#insertmenu).

## <a name="cmenusetdefaultitem"></a><a name="setdefaultitem"></a>CMenu::SetDefaultItem

Nastaví výchozí položku nabídky pro zadanou nabídku.

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uPoložka*<br/>
Identifikátor nebo pozice nové výchozí položky nabídky nebo - 1 pro žádnou výchozí položku. Význam tohoto parametru závisí na hodnotě *fByPos*.

*fByPos*<br/>
Hodnota určující význam *uItem*. Pokud je tento parametr FALSE, *uItem* je identifikátor položky nabídky. V opačném případě se jedná o pozici položky nabídky.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je nenulová. Pokud funkce selže, vrácená hodnota je nula. Chcete-li získat rozšířené informace o chybách, použijte funkci [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)systému Win32 , jak je popsáno v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování funkce Win32 [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::InsertMenu](#insertmenu).

## <a name="cmenusetmenucontexthelpid"></a><a name="setmenucontexthelpid"></a>CMenu::SetMenuContextHelpId

Přidruží id `CMenu`nápovědy kontextu s .

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>Parametry

*dwContextHelpId*<br/>
Kontext nápovědy K `CMenu`ID přidružit k aplikaci .

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0

### <a name="remarks"></a>Poznámky

Všechny položky v nabídce sdílejí tento identifikátor – není možné připojit identifikátor kontextu nápovědy k jednotlivým položkám nabídky.

### <a name="example"></a>Příklad

  Viz příklad pro [CMenu::InsertMenu](#insertmenu).

## <a name="cmenusetmenuinfo"></a><a name="setmenuinfo"></a>CMenu::SetMenuInfo

Nastaví informace pro nabídku.

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>Parametry

*lpcmi*<br/>
Ukazatel na strukturu [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) obsahující informace pro nabídku.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je nenulová; jinak je vrácená hodnota nulová.

### <a name="remarks"></a>Poznámky

Voláním této funkce nastavte konkrétní informace o nabídce.

## <a name="cmenusetmenuitembitmaps"></a><a name="setmenuitembitmaps"></a>CMenu::SetMenuItemBitmapy

Přidruží zadané bitmapy k položce nabídky.

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>Parametry

*nPozice*<br/>
Určuje položku nabídky, která má být změněna. Parametr *nFlags* lze použít k interpretaci *nPosition* následujícími způsoby:

|nPříznaky|Interpretace nPozice|
|------------|---------------------------------|
|MF_BYCOMMAND|Určuje, že parametr udává ID příkazu existující položky nabídky. Toto je výchozí nastavení, pokud není nastavena MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Určuje, že parametr udává umístění existující položky nabídky. První položka je na pozici 0.|

*nPříznaky*<br/>
Určuje způsob interpretace *nPozice.*

*pBmpNezaškrtnuto*<br/>
Určuje bitmapu, která se má použít pro položky nabídky, které nejsou zaškrtnuty.

*pBmpKontrolováno*<br/>
Určuje bitmapu, která má být používána pro kontrolované položky nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Bez ohledu na to, zda je položka nabídky zaškrtnuta nebo nezaškrtnutá, systém Windows zobrazí příslušnou bitmapu vedle položky nabídky.

Pokud *je hodnota null hodnota pBmpUnchecked* nebo *pBmpChecked,* systém Windows nezobrazí nic vedle položky nabídky pro odpovídající atribut. Pokud jsou oba parametry null, systém Windows použije výchozí zaškrtnutí při zaškrtnutí položky a odebere zaškrtnutí, když položka není zaškrtnuta.

Když je nabídka zničena, tyto rastrové obrázky nejsou zničeny; aplikace je musí zničit.

Funkce `GetMenuCheckMarkDimensions` systému Windows načte rozměry výchozího zaškrtnutí použitého pro položky nabídky. Aplikace používá tyto hodnoty k určení vhodné velikosti pro bitmapy dodávané s touto funkcí. Získejte velikost, vytvořte bitmapy a nastavte je.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

## <a name="cmenusetmenuiteminfo"></a><a name="setmenuiteminfo"></a>CMenu::SetMenuItemInfo

Změní informace o položce nabídky.

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uPoložka*<br/>
Viz popis *uItem* v [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow) v sadě Windows SDK.

*lpMenuItemInfo*<br/>
Viz popis *lpmii* v `SetMenuItemInfo` souboru Windows SDK.

*fByPos*<br/>
Viz popis *fByPosition* v `SetMenuItemInfo` souboru Windows SDK.

### <a name="remarks"></a>Poznámky

Tato funkce zabalí [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow), popsané v sadě Windows SDK.

## <a name="cmenutrackpopupmenu"></a><a name="trackpopupmenu"></a>CMenu::TrackPopupMenu

Zobrazí plovoucí rozbalovací nabídku v určeném umístění a sleduje výběr položek v rozbalovací nabídce.

```
BOOL TrackPopupMenu(
    UINT nFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPCRECT lpRect = 0);
```

### <a name="parameters"></a>Parametry

*nPříznaky*<br/>
Určuje příznaky polohy obrazovky a pozice myši. Seznam dostupných příznaků naleznete v části [TrackPopupMenu.](/windows/win32/api/winuser/nf-winuser-trackpopupmenu)

*X*<br/>
Určuje vodorovnou polohu v souřadnicích obrazovky rozbalovací nabídky. V závislosti na hodnotě parametru *nFlags* může být nabídka zarovnána doleva, zarovnaná doprava nebo vystředěná vzhledem k této pozici.

*Y*<br/>
Určuje svislou polohu v souřadnicích obrazovky v horní části nabídky na obrazovce.

*pWnd*<br/>
Identifikuje okno, které vlastní rozbalovací nabídku. Tento parametr nemůže být null, i v případě, že je zadán příznak TPM_NONOTIFY. Toto okno obdrží všechny WM_COMMAND zprávy z nabídky. V systému Windows verze 3.1 a novější, `TrackPopupMenu` okno neobdrží WM_COMMAND zprávy, dokud se vrátí. V systému Windows 3.0 okno `TrackPopupMenu` obdrží WM_COMMAND zprávy před vrácením.

*lpRect*<br/>
Ignorovány.

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí výsledek volání [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Plovoucí rozbalovací nabídka se může zobrazit kdekoli na obrazovce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

## <a name="cmenutrackpopupmenuex"></a><a name="trackpopupmenuex"></a>CMenu::TrackPopupMenuEx

Zobrazí plovoucí rozbalovací nabídku v určeném umístění a sleduje výběr položek v rozbalovací nabídce.

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
Určuje různé funkce rozšířené nabídky. Seznam všech hodnot a jejich významu naleznete v [tématu TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

*X*<br/>
Určuje vodorovnou polohu v souřadnicích obrazovky rozbalovací nabídky.

*Y*<br/>
Určuje svislou polohu v souřadnicích obrazovky v horní části nabídky na obrazovce.

*pWnd*<br/>
Ukazatel na okno, které vlastní rozbalovací nabídku a přijímá zprávy z vytvořené nabídky. Toto okno může být libovolné okno z aktuální aplikace, ale nemůže být NULL. Pokud zadáte TPM_NONOTIFY v parametru *fuFlags,* funkce neodešle žádné zprávy společnosti *pWnd*. Funkce se musí vrátit k oknu, na které ukazuje *pWnd,* aby se WM_COMMAND zprávu.

*lptpm*<br/>
Ukazatel na strukturu [TPMPARAMS,](/windows/win32/api/winuser/ns-winuser-tpmparams) která určuje oblast obrazovky, která by se neměla překrývat. Tento parametr může být NULL.

### <a name="return-value"></a>Návratová hodnota

Pokud zadáte TPM_RETURNCMD v parametru *fuFlags,* vrácená hodnota je identifikátor položky, kterou uživatel vybral. Pokud uživatel zruší nabídku bez provedení výběru, nebo pokud dojde k chybě, pak vrácená hodnota je 0.

Pokud nezadáte TPM_RETURNCMD v parametru *fuFlags,* vrácená hodnota je nenulová, pokud je funkce úspěšná, a 0, pokud se nezdaří. Chcete-li získat rozšířené informace o chybě, volejte [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Poznámky

Plovoucí rozbalovací nabídka se může zobrazit kdekoli na obrazovce. Další informace o zpracování chyb při vytváření rozbalovací nabídky naleznete v tématu [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[Vzorek knihovny MFC DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)
