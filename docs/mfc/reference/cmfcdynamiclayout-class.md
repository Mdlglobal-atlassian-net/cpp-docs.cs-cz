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
ms.openlocfilehash: b70deca78d079c6a95db225814fdc70528e48af9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367515"
---
# <a name="cmfcdynamiclayout-class"></a>CMFCDynamicLayout – třída

Určuje, jak budou ovládací prvky v okně přesunuty a změní velikost při změně velikosti okna uživatelem.

## <a name="syntax"></a>Syntaxe

```
class CMFCDynamicLayout : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCDynamicLayout::CMFCDynamicLayout`|Vytvoří `CMFCDynamicLayout` objekt.|
|`CMFCDynamicLayout::~CMFCDynamicLayout`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCDynamicLayout::AddItem](#additem)|Přidá podřízené okno, obvykle ovládací prvek, do seznamu oken, které jsou řízeny správcem dynamického rozložení.|
|[CMFCDynamicLayout::Upravit](#adjust)|Přidá podřízené okno, obvykle ovládací prvek, do seznamu oken, které jsou řízeny správcem dynamického rozložení.|
|[CMFCDynamicLayout::Vytvořit](#create)|Ukládá a ověřuje okno hostitele.|
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|Vrátí ukazatel na okno hostitele.|
|[CMFCDynamicLayout::GetMinSize](#getminsize)|Vrátí velikost okna, pod kterým není upraveno rozložení.|
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|Načte obdélník pro aktuální klientskou oblast okna.|
|[CMFCDynamicLayout::HasItem](#hasitem)|Zkontroluje, zda byl podřízený ovládací prvek přidán do dynamického rozložení.|
|[CMFCDynamicLayout::IsEmpty](#isempty)|Zkontroluje, zda dynamické rozložení nemá žádné podřízené okna přidána.|
|[CMFCDynamicLayout::Načíst prostředek](#loadresource)|Přečte dynamické rozložení z prostředku AFX_DIALOG_LAYOUT a potom použije rozložení na okno hostitele.|
|statické [CMFCDynamicLayout::Přesunoutvodorovně](#movehorizontal)|Získá [MoveSettings](#movesettings_structure) hodnotu, která definuje, kolik podřízený ovládací prvek je přesunut vodorovně při uživatel změní velikost jeho hostování okna.|
|statické [CMFCDynamicLayout::MoveHorizontalAndVertical](#movehorizontalandvertical)|Získá [MoveSettings](#movesettings_structure) hodnotu, která definuje, kolik podřízený ovládací prvek je přesunut vodorovně při uživatel změní velikost jeho hostování okna.|
|statické [CMFCDynamicLayout::MoveNone](#movenone)|Získá [MoveSettings](#movesettings_structure) hodnotu, která představuje žádný pohyb, svislé nebo vodorovné pro podřízený ovládací prvek.|
|statické [CMFCDynamicLayout::MoveVertical](#movevertical)|Získá [MoveSettings](#movesettings_structure) hodnotu, která definuje, kolik podřízený ovládací prvek je přesunut svisle při uživatel změní velikost jeho hostování okna.|
|[CMFCDynamicLayout::SetMinSize](#setminsize)|Nastaví velikost okna, pod kterou rozložení není upraveno.|
|statické [CMFCDynamicLayout::SizeHorizontal](#sizehorizontal)|Získá [SizeSettings](#sizesettings_structure) hodnotu, která definuje, jak moc podřízený ovládací prvek je velikost vodorovně při uživatel změní velikost jeho hostování okna.|
|statické [CMFCDynamicLayout::SizeHorizontalAndVertical](#sizehorizontalandvertical)|Získá [SizeSettings](#sizesettings_structure) hodnotu, která definuje, jak moc podřízený ovládací prvek je velikost vodorovně při uživatel změní velikost jeho hostování okna.|
|statické [CMFCDynamicLayout::SizeNone](#sizenone)|Získá [SizeSettings](#sizesettings_structure) hodnotu, která představuje žádnou změnu velikosti pro podřízený ovládací prvek.|
|statické [CMFCDynamicLayout::SizeVertical](#sizevertical)|Získá [SizeSettings](#sizesettings_structure) hodnotu, která definuje, kolik podřízeného ovládacího prvku je velikost svisle při změně velikosti uživatele jeho hostování okna.|

## <a name="nested-types"></a>Vnořené typy

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCDynamicLayout::Struktura MoveSettings](#movesettings_structure)|Zapouzdření přesunout data pro ovládací prvky v dynamickém rozložení.|
|[CMFCDynamicLayout::Struktura nastavení velikosti](#sizesettings_structure)|Zapouzdřuje data změny velikosti ovládacích prvků v dynamickém rozložení.|

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CmFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxlayout.h

## <a name="cmfcdynamiclayoutadditem"></a><a name="additem"></a>CMFCDynamicLayout::AddItem

Přidá podřízené okno, obvykle ovládací prvek, do seznamu oken, které jsou řízeny správcem dynamického rozložení.

```
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Popisovač do okna přidat.

*Nid*<br/>
ID podřízeného ovládacího prvku, který chcete přidat.

*moveNastavení*<br/>
Struktura, která popisuje, jak by měl být přesunut ovládací prvek jako změny velikosti okna.

*sizeSettings*<br/>
Struktura, která popisuje, jak by měla být velikost ovládacího prvku při změně velikosti okna.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla položka úspěšně přidána; jinak FALSE.

### <a name="remarks"></a>Poznámky

Umístění a velikost podřízeného ovládacího prvku se dynamicky mění při změně velikosti hostitelského okna.

## <a name="cmfcdynamiclayoutadjust"></a><a name="adjust"></a>CMFCDynamicLayout::Upravit

Přidá podřízené okno, obvykle ovládací prvek, do seznamu oken, které jsou řízeny správcem dynamického rozložení.

```
void Adjust();
```

### <a name="remarks"></a>Poznámky

Umístění a velikost podřízeného ovládacího prvku se dynamicky mění při změně velikosti hostitelského okna.

## <a name="cmfcdynamiclayoutcreate"></a><a name="create"></a>CMFCDynamicLayout::Vytvořit

Ukládá a ověřuje okno hostitele.

```
BOOL Create(CWnd* pHostWnd);
```

### <a name="parameters"></a>Parametry

*pHostWnd*<br/>
Ukazatel na okno hostitele.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je vytvoření úspěšné; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcdynamiclayoutgethostwnd"></a><a name="gethostwnd"></a>CMFCDynamicLayout::GetHostWnd

Vrátí ukazatel na okno hostitele.

```
CWnd* GetHostWnd();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno hostitele.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení byly všechny podřízené řídicí pozice přepočítány vzhledem k tomuto oknu.

## <a name="cmfcdynamiclayoutgetminsize"></a><a name="getminsize"></a>CMFCDynamicLayout::GetMinSize

Vrátí velikost okna, pod kterým není upraveno rozložení.

```
CSize GetMinSize();
```

### <a name="return-value"></a>Návratová hodnota

Velikost okna, pod kterým rozložení není upravena.

### <a name="remarks"></a>Poznámky

Umístění a velikost podřízeného ovládacího prvku se dynamicky mění při změně velikosti hostitelského okna, ale existuje minimální velikost, pod kterou není upraveno rozložení. Uživatel může změnit velikost okna na menší velikost, ale části okna jsou pak skryté ze zobrazení.

## <a name="cmfcdynamiclayoutgetwindowrect"></a><a name="getwindowrect"></a>CMFCDynamicLayout::GetWindowRect

Načte obdélník pro aktuální klientskou oblast okna.

```
void GetHostWndRect(CRect& rect,);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Po návratu funkce obsahuje tento parametr ohraničující obdélník oblasti rozložení. Toto je out parametr; vstupní hodnota je přepsána.

### <a name="remarks"></a>Poznámky

## <a name="cmfcdynamiclayouthasitem"></a><a name="hasitem"></a>CMFCDynamicLayout::HasItem

Zkontroluje, zda byl podřízený ovládací prvek přidán do dynamického rozložení.

```
BOOL HasItem(HWND hwnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Popisovač okna pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud rozložení již tuto položku má; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcdynamiclayoutisempty"></a><a name="isempty"></a>CMFCDynamicLayout::IsEmpty

Zkontroluje, zda dynamické rozložení nemá žádné podřízené okna přidána.

```
BOOL IsEmpty();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud rozložení nemá žádné položky; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcdynamiclayoutloadresource"></a><a name="loadresource"></a>CMFCDynamicLayout::Načíst prostředek

Přečte dynamické rozložení z prostředku AFX_DIALOG_LAYOUT a potom použije rozložení na okno hostitele.

```
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);
```

### <a name="parameters"></a>Parametry

*pHostWnd*<br/>
Ukazatel na okno hostitele.

*lpZdroj*<br/>
Ukazatel na vyrovnávací paměť, která obsahuje prostředek AFX_DIALOG_LAYOUT.

*dwVelikost*<br/>
Velikost vyrovnávací paměti v bajtů.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je prostředek načten a použit v okně hostitele; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcdynamiclayoutmovehorizontal"></a><a name="movehorizontal"></a>CMFCDynamicLayout::Přesunoutvodorovně

Získá [MoveSettings](#movesettings_structure) hodnotu, která definuje, kolik podřízený ovládací prvek je přesunut vodorovně při uživatel změní velikost jeho hostování okna.

```
static MoveSettings MoveHorizontal(int nRatio);
```

### <a name="parameters"></a>Parametry

*nPoměr*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek je přesunut vodorovně při uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

A [MoveSettings](#movesettings_structure) hodnota, která zapouzdřuje požadovaný poměr přesunutí.

### <a name="remarks"></a>Poznámky

## <a name="cmfcdynamiclayoutmovehorizontalandvertical"></a><a name="movehorizontalandvertical"></a>CMFCDynamicLayout::MoveHorizontalAndVertical

Získá [MoveSettings](#movesettings_structure) hodnotu, která definuje, kolik podřízený ovládací prvek je přesunut vodorovně při uživatel změní velikost jeho hostování okna.

```
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parametry

*nXRatio*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek je přesunut vodorovně při uživatel změní velikost okna hostitele.

*nYRatio*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek je přesunut svisle při uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

A [MoveSettings](#movesettings_structure) hodnota, která zapouzdřuje požadovaný poměr přesunutí.

### <a name="remarks"></a>Poznámky

## <a name="cmfcdynamiclayoutmovenone"></a><a name="movenone"></a>CMFCDynamicLayout::MoveNone

Získá [MoveSettings](#movesettings_structure) hodnotu, která představuje žádný pohyb, svislé nebo vodorovné pro podřízený ovládací prvek.

```
static MoveSettings MoveNone();
```

### <a name="return-value"></a>Návratová hodnota

A [MoveSettings](#movesettings_structure) hodnotu, která opravuje ovládací prvek na místě, tak, aby se nepřesune jako uživatel změní velikost okna hostitele.

### <a name="remarks"></a>Poznámky

## <a name="cmfcdynamiclayoutmovesettings-structure"></a><a name="movesettings_structure"></a>CMFCDynamicLayout::Struktura MoveSettings

Zapouzdření přesunout data pro ovládací prvky v dynamickém rozložení.

```
struct CMFCDynamicLayout::MoveSettings;
```

### <a name="remarks"></a>Poznámky

Toto je vnořená třída uvnitř `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout::MoveSettings::IsHorizontal

Zkontrolujte, zda data přesunutí určují nenulový vodorovný přesun.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Návratová hodnota

TRUE, `MoveSettings` pokud objekt určuje nenulový vodorovný pohyb.

## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout::MoveSettings::isNone

Zkontrolujte, zda data přesunutí neurčují žádný pohyb.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Návratová hodnota

TRUE, `MoveSettings` pokud objekt neurčuje žádný pohyb.

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout::MoveSettings::IsVertical

Zkontrolujte, zda data přesunu určují nenulový vertikální pohyb.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Návratová hodnota

TRUE, `MoveSettings` pokud objekt určuje nenulový vertikální pohyb.

## <a name="cmfcdynamiclayoutmovevertical"></a><a name="movevertical"></a>CMFCDynamicLayout::MoveVertical

Získá [MoveSettings](#movesettings_structure) hodnotu, která definuje, kolik podřízený ovládací prvek je přesunut svisle při uživatel změní velikost jeho hostování okna.

```
static MoveSettings MoveVertical(int nRatio);
```

### <a name="parameters"></a>Parametry

*nPoměr*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek je přesunut svisle při uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

A [MoveSettings](#movesettings_structure) hodnota, která zapouzdřuje požadovaný poměr přesunutí.

### <a name="remarks"></a>Poznámky

## <a name="cmfcdynamiclayoutsetminsize"></a><a name="setminsize"></a>CMFCDynamicLayout::SetMinSize

Nastaví velikost okna, pod kterou rozložení není upraveno.

```
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Požadovaná velikost, pod kterou rozložení není upravena.

### <a name="remarks"></a>Poznámky

Umístění a velikost podřízeného ovládacího prvku se dynamicky mění při změně velikosti hostitelského okna, ale existuje minimální velikost, pod kterou není upraveno rozložení. Uživatel může změnit velikost okna na menší velikost, ale části okna jsou pak skryté ze zobrazení.

## <a name="cmfcdynamiclayoutsizehorizontal"></a><a name="sizehorizontal"></a>CMFCDynamicLayout::Vodorovná velikost

Získá [SizeSettings](#sizesettings_structure) hodnotu, která definuje, jak moc podřízený ovládací prvek je velikost vodorovně při uživatel změní velikost jeho hostování okna.

```
static SizeSettings SizeHorizontal(int nRatio);
```

### <a name="parameters"></a>Parametry

*nPoměr*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek je velikost vodorovně při uživatel i velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

A [SizeSettings](#sizesettings_structure) hodnota, která zapouzdřuje požadovaný poměr velikosti.

### <a name="remarks"></a>Poznámky

## <a name="cmfcdynamiclayoutsizehorizontalandvertical"></a><a name="sizehorizontalandvertical"></a>CMFCDynamicLayout::SizeHorizontalAndVertical

Získá [SizeSettings](#sizesettings_structure) hodnotu, která definuje, jak moc podřízený ovládací prvek je velikost vodorovně při uživatel změní velikost jeho hostování okna.

```
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parametry

*nXRatio*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek je velikost vodorovně při uživatel i velikost okna hostitele.

*nYRatio*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek je velikost svisle při změně velikosti okna hostitele uživatelem.

### <a name="return-value"></a>Návratová hodnota

A [SizeSettings](#sizesettings_structure) hodnota, která zapouzdřuje požadovaný poměr velikosti.

### <a name="remarks"></a>Poznámky

## <a name="cmfcdynamiclayoutsizenone"></a><a name="sizenone"></a>CMFCDynamicLayout::SizeNone

Získá [SizeSettings](#sizesettings_structure) hodnotu, která představuje žádnou změnu velikosti pro podřízený ovládací prvek.

```
static SizeSettings SizeNone();
```

### <a name="return-value"></a>Návratová hodnota

A [SizeSettings](#sizesettings_structure) hodnotu, která opravuje ovládací prvek v určité velikosti, tak, aby se nezmění velikost jako uživatel změní velikost okna hostitele.

### <a name="remarks"></a>Poznámky

## <a name="cmfcdynamiclayoutsizesettings-structure"></a><a name="sizesettings_structure"></a>CMFCDynamicLayout::Struktura nastavení velikosti

Zapouzdřuje data změny velikosti ovládacích prvků v dynamickém rozložení.

```
struct CMFCDynamicLayout::SizeSettings;
```

### <a name="remarks"></a>Poznámky

Toto je vnořená třída uvnitř `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout::SizeSettings::isHorizontal

Zkontroluje, zda data změny velikosti určují nenulovou vodorovnou velikost.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Návratová hodnota

TRUE, `SizeSettings` pokud objekt určuje nenulovou vodorovnou velikost.

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout::SizeSettings::isNone

Zkontroluje, zda data změny velikosti neurčují žádnou velikost.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Návratová hodnota

TRUE, `SizeSettings` pokud objekt neurčuje žádnou velikost.

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout::SizeSettings::isVertical

Zkontroluje, zda data změny velikosti určují nenulovou svislou velikost.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Návratová hodnota

TRUE, `SizeSettings` pokud objekt určuje nenulovou svislou velikost.

## <a name="cmfcdynamiclayoutsizevertical"></a><a name="sizevertical"></a>CMFCDynamicLayout::SizeVertical

Získá [SizeSettings](#sizesettings_structure) hodnotu, která definuje, kolik podřízeného ovládacího prvku je velikost svisle při změně velikosti uživatele jeho hostování okna.

```
static SizeSettings SizeVertical(int nRatio);
```

### <a name="parameters"></a>Parametry

*nPoměr*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek je velikost svisle při změně velikosti okna hostitele uživatelem.

### <a name="return-value"></a>Návratová hodnota

A [SizeSettings](#sizesettings_structure) hodnota, která zapouzdřuje požadovaný poměr velikosti.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
