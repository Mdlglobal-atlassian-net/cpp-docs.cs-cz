---
title: CMFCDynamicLayout – třída
ms.date: 08/29/2019
f1_keywords:
- CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout::AddItem
- AFXLAYOUT/CMFCDynamicLayout::Adjust
- AFXLAYOUT/CMFCDynamicLayout::Create
- AFXLAYOUT/CMFCDynamicLayout::GetHostWnd
- AFXLAYOUT/CMFCDynamicLayout::GetMinSize
- AFXLAYOUT/CMFCDynamicLayout::GetWindowRect
- AFXLAYOUT/CMFCDynamicLayout::HasItem
- AFXLAYOUT/CMFCDynamicLayout::IsEmpty
- AFXLAYOUT/CMFCDynamicLayout::LoadResource
- AFXLAYOUT/CMFCDynamicLayout::SetMinSize
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
ms.openlocfilehash: f1ddf35b514d9b89f53d5f1307a6ecb7132d2854
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177509"
---
# <a name="cmfcdynamiclayout-class"></a>CMFCDynamicLayout – třída

Určuje, jak jsou ovládací prvky v okně přesunuty a mění se jejich velikost, protože uživatel změní velikost okna.

## <a name="syntax"></a>Syntaxe

```
class CMFCDynamicLayout : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|`CMFCDynamicLayout::CMFCDynamicLayout`|`CMFCDynamicLayout` Vytvoří objekt.|
|`CMFCDynamicLayout::~CMFCDynamicLayout`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCDynamicLayout::AddItem](#additem)|Přidá podřízené okno, obvykle ovládací prvek, do seznamu oken, které jsou ovládány pomocí programu Dynamic Layout Manager.|
|[CMFCDynamicLayout:: upravit](#adjust)|Přidá podřízené okno, obvykle ovládací prvek, do seznamu oken, které jsou ovládány pomocí programu Dynamic Layout Manager.|
|[CMFCDynamicLayout::Create](#create)|Ukládá a ověřuje okno hostitele.|
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|Vrátí ukazatel na okno hostitele.|
|[CMFCDynamicLayout:: getminsize](#getminsize)|Vrátí velikost okna, pod kterým se rozložení neupravuje.|
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|Načte rámeček pro aktuální klientskou oblast okna.|
|[CMFCDynamicLayout::HasItem](#hasitem)|Kontroluje, zda byl podřízený ovládací prvek přidán do dynamického rozložení.|
|[CMFCDynamicLayout::IsEmpty](#isempty)|Zkontroluje, jestli se do dynamického rozložení nepřidala žádná podřízená okna.|
|[CMFCDynamicLayout::LoadResource](#loadresource)|Přečte dynamické rozložení z prostředku AFX_DIALOG_LAYOUT a pak použije rozložení v hostitelském okně.|
|statické [CMFCDynamicLayout:: MoveHorizontal](#movehorizontal)|Získá hodnotu [MoveSettings –](#movesettings_structure) , která definuje, jak velká část podřízeného ovládacího prvku je přesunuta vodorovně, když uživatel změní velikost svého hostitelského okna.|
|statické [CMFCDynamicLayout:: MoveHorizontalAndVertical](#movehorizontalandvertical)|Získá hodnotu [MoveSettings –](#movesettings_structure) , která definuje, jak velká část podřízeného ovládacího prvku je přesunuta vodorovně, když uživatel změní velikost svého hostitelského okna.|
|statické [CMFCDynamicLayout:: MoveNone](#movenone)|Získá hodnotu [MoveSettings –](#movesettings_structure) , která pro podřízený ovládací prvek nepředstavuje žádný pohyb, svislou nebo vodorovnou.|
|static [CMFCDynamicLayout::MoveVertical](#movevertical)|Získá hodnotu [MoveSettings –](#movesettings_structure) , která definuje, jak velká část podřízeného ovládacího prvku je přesunuta svisle v případě, že uživatel změní velikost svého hostitelského okna.|
|[CMFCDynamicLayout:: SetMinSize](#setminsize)|Nastaví velikost okna, pod kterým se rozložení neupravuje.|
|statické [CMFCDynamicLayout:: SizeHorizontal](#sizehorizontal)|Získá hodnotu [SizeSettings –](#sizesettings_structure) , která definuje, jak velká část podřízeného ovládacího prvku se změní vodorovně, když uživatel změní velikost svého hostitelského okna.|
|statické [CMFCDynamicLayout:: SizeHorizontalAndVertical](#sizehorizontalandvertical)|Získá hodnotu [SizeSettings –](#sizesettings_structure) , která definuje, jak velká část podřízeného ovládacího prvku se změní vodorovně, když uživatel změní velikost svého hostitelského okna.|
|statické [CMFCDynamicLayout:: SizeNone](#sizenone)|Získá hodnotu [SizeSettings –](#sizesettings_structure) , která nepředstavuje žádné změny velikosti pro podřízený ovládací prvek.|
|statické [CMFCDynamicLayout:: SizeVertical](#sizevertical)|Získá hodnotu [SizeSettings –](#sizesettings_structure) , která definuje, jak velká část podřízeného ovládacího prvku se změní svisle v případě, že uživatel změní velikost svého hostitelského okna.|

## <a name="nested-types"></a>Vnořené typy

|Name|Popis|
|----------|-----------------|
|[CMFCDynamicLayout:: MoveSettings – – struktura](#movesettings_structure)|Zapouzdřuje přesun dat pro ovládací prvky v dynamickém rozložení.|
|[CMFCDynamicLayout:: SizeSettings – – struktura](#sizesettings_structure)|Zapouzdřuje data změny velikosti pro ovládací prvky v dynamickém rozložení.|

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxlayout. h

##  <a name="additem"></a>CMFCDynamicLayout:: AddItem

Přidá podřízené okno, obvykle ovládací prvek, do seznamu oken, které jsou ovládány pomocí programu Dynamic Layout Manager.

```
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```

### <a name="parameters"></a>Parametry

*HWND*<br/>
Popisovač okna, které se má přidat

*nID*<br/>
ID podřízeného ovládacího prvku, který se má přidat

*moveSettings*<br/>
Struktura, která popisuje, jak se má ovládací prvek přesunout jako změny velikosti okna

*sizeSettings*<br/>
Struktura, která popisuje, jak se má změnit velikost ovládacího prvku při změně velikosti okna.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se položka úspěšně přidala; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pozice a velikost podřízeného ovládacího prvku se dynamicky mění při změně velikosti hostitelského okna.

##  <a name="adjust"></a>CMFCDynamicLayout:: upravit

Přidá podřízené okno, obvykle ovládací prvek, do seznamu oken, které jsou ovládány pomocí programu Dynamic Layout Manager.

```
void Adjust();
```

### <a name="remarks"></a>Poznámky

Pozice a velikost podřízeného ovládacího prvku se dynamicky mění při změně velikosti hostitelského okna.

##  <a name="create"></a>CMFCDynamicLayout:: Create

Ukládá a ověřuje okno hostitele.

```
BOOL Create(CWnd* pHostWnd);
```

### <a name="parameters"></a>Parametry

*pHostWnd*<br/>
Ukazatel na okno hostitele.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je vytvoření úspěšné; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="gethostwnd"></a>CMFCDynamicLayout:: GetHostWnd

Vrátí ukazatel na okno hostitele.

```
CWnd* GetHostWnd();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno hostitele.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou všechny pozice podřízených ovládacích prvků přepočteny relativně k tomuto oknu.

##  <a name="getminsize"></a>CMFCDynamicLayout:: getminsize

Vrátí velikost okna, pod kterým se rozložení neupravuje.

```
CSize GetMinSize();
```

### <a name="return-value"></a>Návratová hodnota

Velikost okna, pod kterým se rozložení neupravuje

### <a name="remarks"></a>Poznámky

Pozice a velikost podřízeného ovládacího prvku se dynamicky mění při změně velikosti hostitelského okna, ale existuje minimální velikost, pod kterou se rozložení neupravuje. Uživatel může změnit velikost okna na menší velikost, ale části okna jsou pak skryty ze zobrazení.

##  <a name="getwindowrect"></a>CMFCDynamicLayout:: GetWindowRect

Načte rámeček pro aktuální klientskou oblast okna.

```
void GetHostWndRect(CRect& rect,);
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
Po návratu funkce tento parametr obsahuje ohraničující obdélník oblasti rozložení. Toto je výstupní parametr; vstupní hodnota je přepsána.

### <a name="remarks"></a>Poznámky

##  <a name="hasitem"></a>CMFCDynamicLayout:: HasItem

Kontroluje, zda byl podřízený ovládací prvek přidán do dynamického rozložení.

```
BOOL HasItem(HWND hwnd);
```

### <a name="parameters"></a>Parametry

*HWND*<br/>
Popisovač okna pro ovládací prvek

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud rozložení již tuto položku obsahuje; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="isempty"></a>CMFCDynamicLayout::-Empty

Zkontroluje, jestli se do dynamického rozložení nepřidala žádná podřízená okna.

```
BOOL IsEmpty();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud rozložení neobsahuje žádné položky; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="loadresource"></a>CMFCDynamicLayout:: LoadResource

Přečte dynamické rozložení z prostředku AFX_DIALOG_LAYOUT a pak použije rozložení v hostitelském okně.

```
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);
```

### <a name="parameters"></a>Parametry

*pHostWnd*<br/>
Ukazatel na okno hostitele.

*lpResource*<br/>
Ukazatel na vyrovnávací paměť, která obsahuje prostředek AFX_DIALOG_LAYOUT.

*nenulového dwSize funkci*<br/>
Velikost vyrovnávací paměti v bajtech.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je prostředek načten a aplikován do hostitelského okna; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="movehorizontal"></a>CMFCDynamicLayout:: MoveHorizontal

Získá hodnotu [MoveSettings –](#movesettings_structure) , která definuje, jak velká část podřízeného ovládacího prvku je přesunuta vodorovně, když uživatel změní velikost svého hostitelského okna.

```
static MoveSettings MoveHorizontal(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Definuje jako procento toho, jak daleko se má vodorovně přesunout podřízený ovládací prvek, když uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

Hodnota [MoveSettings –](#movesettings_structure) , která zapouzdřuje požadovaný poměr přesunutí.

### <a name="remarks"></a>Poznámky

##  <a name="movehorizontalandvertical"></a>CMFCDynamicLayout:: MoveHorizontalAndVertical

Získá hodnotu [MoveSettings –](#movesettings_structure) , která definuje, jak velká část podřízeného ovládacího prvku je přesunuta vodorovně, když uživatel změní velikost svého hostitelského okna.

```
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parametry

*nXRatio*<br/>
Definuje jako procento toho, jak daleko se má vodorovně přesunout podřízený ovládací prvek, když uživatel změní velikost okna hostitele.

*nYRatio*<br/>
Definuje jako procento, jak daleko se přesune podřízený ovládací prvek svisle, když uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

Hodnota [MoveSettings –](#movesettings_structure) , která zapouzdřuje požadovaný poměr přesunutí.

### <a name="remarks"></a>Poznámky

##  <a name="movenone"></a>CMFCDynamicLayout:: MoveNone

Získá hodnotu [MoveSettings –](#movesettings_structure) , která pro podřízený ovládací prvek nepředstavuje žádný pohyb, svislou nebo vodorovnou.

```
static MoveSettings MoveNone();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota [MoveSettings –](#movesettings_structure) , která opravuje ovládací prvek na místě, aby se nepřesunula, protože uživatel změní velikost okna hostitele.

### <a name="remarks"></a>Poznámky

##  <a name="movesettings_structure"></a>CMFCDynamicLayout:: MoveSettings – – struktura

Zapouzdřuje přesun dat pro ovládací prvky v dynamickém rozložení.

```
struct CMFCDynamicLayout::MoveSettings;
```

### <a name="remarks"></a>Poznámky

Toto je vnořená třída uvnitř `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout::MoveSettings::IsHorizontal

Zkontroluje, jestli data přesunu nespecifikují nenulové horizontální přesunutí.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Návratová hodnota

TRUE, `MoveSettings` Pokud objekt určuje nenulové horizontální přesunutí.

## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout::MoveSettings::IsNone

Zkontroluje, jestli data přesunu neobsahují žádný pohyb.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Návratová hodnota

TRUE, `MoveSettings` Pokud objekt neurčuje žádný přesun.

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout::MoveSettings::IsVertical

Zkontroluje, jestli data přesunu zadává nenulový svislý pohyb.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Návratová hodnota

TRUE, `MoveSettings` Pokud objekt určuje nenulový svislý pohyb.

##  <a name="movevertical"></a>CMFCDynamicLayout:: MoveVertical

Získá hodnotu [MoveSettings –](#movesettings_structure) , která definuje, jak velká část podřízeného ovládacího prvku je přesunuta svisle v případě, že uživatel změní velikost svého hostitelského okna.

```
static MoveSettings MoveVertical(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Definuje jako procento, jak daleko se přesune podřízený ovládací prvek svisle, když uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

Hodnota [MoveSettings –](#movesettings_structure) , která zapouzdřuje požadovaný poměr přesunutí.

### <a name="remarks"></a>Poznámky

##  <a name="setminsize"></a>CMFCDynamicLayout:: SetMinSize

Nastaví velikost okna, pod kterým se rozložení neupravuje.

```
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Požadovaná velikost, pod kterou se rozložení neupravuje

### <a name="remarks"></a>Poznámky

Pozice a velikost podřízeného ovládacího prvku se dynamicky mění při změně velikosti hostitelského okna, ale existuje minimální velikost, pod kterou se rozložení neupravuje. Uživatel může změnit velikost okna na menší velikost, ale části okna jsou pak skryty ze zobrazení.

##  <a name="sizehorizontal"></a>CMFCDynamicLayout:: SizeHorizontal

Získá hodnotu [SizeSettings –](#sizesettings_structure) , která definuje, jak velká část podřízeného ovládacího prvku se změní vodorovně, když uživatel změní velikost svého hostitelského okna.

```
static SizeSettings SizeHorizontal(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Definuje jako procento, jak daleko se velikost podřízeného ovládacího prvku změní vodorovně, když uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

Hodnota [SizeSettings –](#sizesettings_structure) , která zapouzdřuje požadovaný poměr velikosti.

### <a name="remarks"></a>Poznámky

##  <a name="sizehorizontalandvertical"></a>CMFCDynamicLayout:: SizeHorizontalAndVertical

Získá hodnotu [SizeSettings –](#sizesettings_structure) , která definuje, jak velká část podřízeného ovládacího prvku se změní vodorovně, když uživatel změní velikost svého hostitelského okna.

```
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parametry

*nXRatio*<br/>
Definuje jako procento, jak daleko se velikost podřízeného ovládacího prvku změní vodorovně, když uživatel změní velikost okna hostitele.

*nYRatio*<br/>
Definuje jako procento, jak daleko se velikost podřízeného ovládacího prvku změní svisle, když uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

Hodnota [SizeSettings –](#sizesettings_structure) , která zapouzdřuje požadovaný poměr velikosti.

### <a name="remarks"></a>Poznámky

##  <a name="sizenone"></a>CMFCDynamicLayout:: SizeNone

Získá hodnotu [SizeSettings –](#sizesettings_structure) , která nepředstavuje žádné změny velikosti pro podřízený ovládací prvek.

```
static SizeSettings SizeNone();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota [SizeSettings –](#sizesettings_structure) , která tento ovládací prvek opravuje na určitou velikost, aby neměnila velikost, jak uživatel změní velikost okna hostitele.

### <a name="remarks"></a>Poznámky

##  <a name="sizesettings_structure"></a>CMFCDynamicLayout:: SizeSettings – – struktura

Zapouzdřuje data změny velikosti pro ovládací prvky v dynamickém rozložení.

```
struct CMFCDynamicLayout::SizeSettings;
```

### <a name="remarks"></a>Poznámky

Toto je vnořená třída uvnitř `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout::SizeSettings::IsHorizontal

Kontroluje, zda data změny určují nenulovou horizontální změnu velikosti.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Návratová hodnota

TRUE, `SizeSettings` Pokud objekt určuje nenulovou horizontální změnu velikosti.

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout::SizeSettings::IsNone

Zkontroluje, jestli data změny velikosti neurčují žádné změny velikosti.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Návratová hodnota

TRUE, `SizeSettings` Pokud objekt neurčuje žádné změny velikosti.

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout::SizeSettings::IsVertical

Kontroluje, zda data změny určují nenulovou svislou změnu velikosti.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Návratová hodnota

TRUE, `SizeSettings` Pokud objekt určuje nenulovou svislou změnu velikosti.

##  <a name="sizevertical"></a>CMFCDynamicLayout:: SizeVertical

Získá hodnotu [SizeSettings –](#sizesettings_structure) , která definuje, jak velká část podřízeného ovládacího prvku se změní svisle v případě, že uživatel změní velikost svého hostitelského okna.

```
static SizeSettings SizeVertical(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Definuje jako procento, jak daleko se velikost podřízeného ovládacího prvku změní svisle, když uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

Hodnota [SizeSettings –](#sizesettings_structure) , která zapouzdřuje požadovaný poměr velikosti.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
