---
title: CMFCDynamicLayout – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 40dedbe2737a79b7531b8acd47870ce7cb788604
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237582"
---
# <a name="cmfcdynamiclayout-class"></a>CMFCDynamicLayout – třída

Určuje, jak přesunout a změně velikosti jako uživatel zmenší okno pod ovládacích prvků v okně.

## <a name="syntax"></a>Syntaxe

```
class CMFCDynamicLayout : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CMFCDynamicLayout::CMFCDynamicLayout`|Vytvoří `CMFCDynamicLayout` objektu.|
|`CMFCDynamicLayout::~CMFCDynamicLayout`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCDynamicLayout::AddItem](#additem)|Podřízené okno, obvykle ovládacího prvku, přidá do seznamu oken, které se řídí správce dynamické rozložení.|
|[CMFCDynamicLayout::Adjust](#adjust)|Podřízené okno, obvykle ovládacího prvku, přidá do seznamu oken, které se řídí správce dynamické rozložení.|
|[CMFCDynamicLayout::Create](#create)|Úložiště a ověří okno hostitele.|
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|Vrací ukazatel na okno hostitele.|
|[CMFCDynamicLayout::GetMinSize](#getminsize)|Vrátí velikost okna, pod kterou se upraví rozložení.|
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|Načte obdélník pro aktuální klientské oblasti okna.|
|[CMFCDynamicLayout::HasItem](#hasitem)|Kontroluje se, pokud podřízený ovládací prvek byl přidán do dynamického rozložení.|
|[CMFCDynamicLayout::IsEmpty](#isempty)|Kontroluje, jestli má dynamické rozložení žádná podřízená okna Přidat.|
|[CMFCDynamicLayout::LoadResource](#loadresource)|Dynamické rozložení načteme prostředků AFX_DIALOG_LAYOUT a poté použije rozložení okna hostitele.|
|static [CMFCDynamicLayout::MoveHorizontal](#movehorizontal)|Získá [MoveSettings](#movesettings_structure) hodnotu, která určuje, kolik podřízený ovládací prvek posunout vodorovně když uživatel změní jeho hostitelského okna.|
|static [CMFCDynamicLayout::MoveHorizontalAndVertical](#movehorizontalandvertical)|Získá [MoveSettings](#movesettings_structure) hodnotu, která určuje, kolik podřízený ovládací prvek posunout vodorovně když uživatel změní jeho hostitelského okna.|
|static [CMFCDynamicLayout::MoveNone](#movenone)|Získá [MoveSettings](#movesettings_structure) hodnotu, která představuje bez pohybu, svislé nebo vodorovné pro podřízený ovládací prvek.|
|static [CMFCDynamicLayout::MoveVertical](#movevertical)|Získá [MoveSettings](#movesettings_structure) hodnotu, která určuje, kolik podřízený ovládací prvek posunout svisle když uživatel změní jeho hostitelského okna.|
|[CMFCDynamicLayout::SetMinSize](#setminsize)|Nastaví velikost okna, pod kterou se upraví rozložení.|
|statické [CMFCDynamicLayout::SizeHorizontal](#sizehorizontal)|Získá [SizeSettings](#sizesettings_structure) hodnotu, která určuje, kolik podřízený ovládací prvek svou velikost vodorovně když uživatel změní jeho hostitelského okna.|
|static [CMFCDynamicLayout::SizeHorizontalAndVertical](#sizehorizontalandvertical)|Získá [SizeSettings](#sizesettings_structure) hodnotu, která určuje, kolik podřízený ovládací prvek svou velikost vodorovně když uživatel změní jeho hostitelského okna.|
|statické [CMFCDynamicLayout::SizeNone](#sizenone)|Získá [SizeSettings](#sizesettings_structure) hodnotu, která představuje nezměnila velikost podřízeného ovládacího prvku.|
|static [CMFCDynamicLayout::SizeVertical](#sizevertical)|Získá [SizeSettings](#sizesettings_structure) hodnotu, která určuje, kolik podřízený ovládací prvek svou velikost svisle když uživatel změní jeho hostitelského okna.|

## <a name="nested-types"></a>Vnořené typy

|Název|Popis|
|----------|-----------------|
|[CMFCDynamicLayout::MoveSettings Structure](#movesettings_structure)|Zapouzdřuje přesunu dat pro ovládací prvky v dynamické rozložení.|
|[Cmfcdynamiclayout::sizesettings – struktura](#sizesettings_structure)|Zapouzdří data změny velikosti pro ovládací prvky v dynamické rozložení.|

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxlayout.h

##  <a name="additem"></a>  CMFCDynamicLayout::AddItem

Podřízené okno, obvykle ovládacího prvku, přidá do seznamu oken, které se řídí správce dynamické rozložení.

```
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Popisovač okna pro přidání.

*nID*<br/>
ID podřízeného ovládacího prvku pro přidání.

*moveSettings*<br/>
Struktura, která popisuje, jak přesunout ovládací prvek při změně velikosti okna.

*sizeSettings*<br/>
Struktura, která popisuje, jak by měl být ovládací prvek svou velikost při změně velikosti okna.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byla položka přidána úspěšně; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Umístění a velikost podřízeného ovládacího prvku se změní dynamicky, pokud je během změny velikosti hostitelského okna.

##  <a name="adjust"></a>  CMFCDynamicLayout::Adjust

Podřízené okno, obvykle ovládacího prvku, přidá do seznamu oken, které se řídí správce dynamické rozložení.

```
void Adjust();
```

### <a name="remarks"></a>Poznámky

Umístění a velikost podřízeného ovládacího prvku se změní dynamicky, pokud je během změny velikosti hostitelského okna.

##  <a name="create"></a>  CMFCDynamicLayout::Create

Úložiště a ověří okno hostitele.

```
BOOL Create(CWnd* pHostWnd);
```

### <a name="parameters"></a>Parametry

*pHostWnd*<br/>
Ukazatel na okno hostitele.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byla úspěšně vytvořena; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="gethostwnd"></a>  CMFCDynamicLayout::GetHostWnd

Vrací ukazatel na okno hostitele.

```
CWnd* GetHostWnd();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno hostitele.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení přepočítá všechny podřízené ovládací prvek pozice relativně k toto okno.

##  <a name="getminsize"></a>  CMFCDynamicLayout::GetMinSize

Vrátí velikost okna, pod kterou se upraví rozložení.

```
CSize GetMinSize();
```

### <a name="return-value"></a>Návratová hodnota

Velikost okna, pod kterou se upraví rozložení.

### <a name="remarks"></a>Poznámky

Umístění a velikost podřízeného ovládacího prvku se změní dynamicky, pokud je během změny velikosti hostitelského okna, ale je minimální velikost, pod kterou se upraví rozložení. Uživatel může změnit velikost okna menší velikost, ale část okna jsou poté skryté ze zobrazení.

##  <a name="getwindowrect"></a>  CMFCDynamicLayout::GetWindowRect

Načte obdélník pro aktuální klientské oblasti okna.

```
void GetHostWndRect(CRect& rect,);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Po vrácení funkce tento parametr obsahuje ohraničující obdélník oblasti rozvržení. Toto je výstupní parametr; Vstupní hodnota se přepíše.

### <a name="remarks"></a>Poznámky

##  <a name="hasitem"></a>  CMFCDynamicLayout::HasItem

Kontroluje se, pokud podřízený ovládací prvek byl přidán do dynamického rozložení.

```
BOOL HasItem(HWND hwnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Popisovač okna pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud už má tuto položku; rozložení v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="isempty"></a>  CMFCDynamicLayout::IsEmpty

Kontroluje, jestli má dynamické rozložení žádná podřízená okna Přidat.

```
BOOL IsEmpty();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě rozložení nemá žádné položky.; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="loadresource"></a>  CMFCDynamicLayout::LoadResource

Dynamické rozložení načteme prostředků AFX_DIALOG_LAYOUT a poté použije rozložení okna hostitele.

```
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);
```

### <a name="parameters"></a>Parametry

*pHostWnd*<br/>
Ukazatel na okno hostitele.

*lpResource*<br/>
Ukazatel do vyrovnávací paměti, která obsahuje AFX_DIALOG_LAYOUT prostředků.

*dwSize*<br/>
Velikost vyrovnávací paměti v bajtech.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě prostředků jsou načítány a použity do hostitelského okna. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="movehorizontal"></a>  CMFCDynamicLayout::MoveHorizontal

Získá [MoveSettings](#movesettings_structure) hodnotu, která určuje, kolik podřízený ovládací prvek posunout vodorovně když uživatel změní jeho hostitelského okna.

```
static MoveSettings MoveHorizontal(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek posunout vodorovně když uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

A [MoveSettings](#movesettings_structure) hodnotu, která zapouzdřuje požadovanou přesunout poměr.

### <a name="remarks"></a>Poznámky

##  <a name="movehorizontalandvertical"></a>  CMFCDynamicLayout::MoveHorizontalAndVertical

Získá [MoveSettings](#movesettings_structure) hodnotu, která určuje, kolik podřízený ovládací prvek posunout vodorovně když uživatel změní jeho hostitelského okna.

```
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parametry

*nXRatio*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek posunout vodorovně když uživatel změní velikost okna hostitele.

*nYRatio*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek posunout svisle když uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

A [MoveSettings](#movesettings_structure) hodnotu, která zapouzdřuje požadovanou přesunout poměr.

### <a name="remarks"></a>Poznámky

##  <a name="movenone"></a>  CMFCDynamicLayout::MoveNone

Získá [MoveSettings](#movesettings_structure) hodnotu, která představuje bez pohybu, svislé nebo vodorovné pro podřízený ovládací prvek.

```
static MoveSettings MoveNone();
```

### <a name="return-value"></a>Návratová hodnota

A [MoveSettings](#movesettings_structure) hodnotu, která řeší ovládacího prvku na místě, tak, aby nepřesouvá jako uživatel změní velikost okna hostitele.

### <a name="remarks"></a>Poznámky

##  <a name="movesettings_structure"></a>  Cmfcdynamiclayout::movesettings – struktura

Zapouzdřuje přesunu dat pro ovládací prvky v dynamické rozložení.

```
struct CMFCDynamicLayout::MoveSettings;
```

### <a name="remarks"></a>Poznámky

To je vnořená třída uvnitř `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout::MoveSettings::IsHorizontal

Zaškrtněte, pokud přesunutí dat určuje nenulovou Vodorovný pohyb.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud `MoveSettings` objekt určuje nenulovou Vodorovný pohyb.

## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout::MoveSettings::IsNone

Zaškrtněte, pokud přesunutí dat určuje bez pohybu.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud `MoveSettings` objekt určuje bez pohybu.

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout::MoveSettings::IsVertical

  Zaškrtněte, pokud přesunutí dat určuje nenulovou svislé pohyb.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud `MoveSettings` objekt určuje nenulovou svislý pohyb.

##  <a name="movevertical"></a>  CMFCDynamicLayout::MoveVertical

Získá [MoveSettings](#movesettings_structure) hodnotu, která určuje, kolik podřízený ovládací prvek posunout svisle když uživatel změní jeho hostitelského okna.

```
static MoveSettings MoveVertical(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek posunout svisle když uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

A [MoveSettings](#movesettings_structure) hodnotu, která zapouzdřuje požadovanou přesunout poměr.

### <a name="remarks"></a>Poznámky

##  <a name="setminsize"></a>  CMFCDynamicLayout::SetMinSize

Nastaví velikost okna, pod kterou se upraví rozložení.

```
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Požadovaná velikost, pod kterou se upraví rozložení.

### <a name="remarks"></a>Poznámky

Umístění a velikost podřízeného ovládacího prvku se změní dynamicky, pokud je během změny velikosti hostitelského okna, ale je minimální velikost, pod kterou se upraví rozložení. Uživatel může změnit velikost okna menší velikost, ale část okna jsou poté skryté ze zobrazení.

##  <a name="sizehorizontal"></a>  CMFCDynamicLayout::SizeHorizontal

Získá [SizeSettings](#sizesettings_structure) hodnotu, která určuje, kolik podřízený ovládací prvek svou velikost vodorovně když uživatel změní jeho hostitelského okna.

```
static SizeSettings SizeHorizontal(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek svou velikost vodorovně když uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

A [SizeSettings](#sizesettings_structure) hodnotu, která zapouzdřuje poměr požadované velikosti.

### <a name="remarks"></a>Poznámky

##  <a name="sizehorizontalandvertical"></a>  CMFCDynamicLayout::SizeHorizontalAndVertical

Získá [SizeSettings](#sizesettings_structure) hodnotu, která určuje, kolik podřízený ovládací prvek svou velikost vodorovně když uživatel změní jeho hostitelského okna.

```
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parametry

*nXRatio*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek svou velikost vodorovně když uživatel změní velikost okna hostitele.

*nYRatio*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek svou velikost svisle když uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

A [SizeSettings](#sizesettings_structure) hodnotu, která zapouzdřuje poměr požadované velikosti.

### <a name="remarks"></a>Poznámky

##  <a name="sizenone"></a>  CMFCDynamicLayout::SizeNone

Získá [SizeSettings](#sizesettings_structure) hodnotu, která představuje nezměnila velikost podřízeného ovládacího prvku.

```
static SizeSettings SizeNone();
```

### <a name="return-value"></a>Návratová hodnota

A [SizeSettings](#sizesettings_structure) hodnotu, která řeší ovládacího prvku na určitou velikost, takže nemění velikost, protože uživatel změní velikost okna hostitele.

### <a name="remarks"></a>Poznámky

##  <a name="sizesettings_structure"></a>  Cmfcdynamiclayout::sizesettings – struktura

Zapouzdří data změny velikosti pro ovládací prvky v dynamické rozložení.

```
struct CMFCDynamicLayout::SizeSettings;
```

### <a name="remarks"></a>Poznámky

To je vnořená třída uvnitř `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout::SizeSettings::IsHorizontal

Kontroluje,-li změnit velikost dat určuje nenulovou vodorovné změny velikosti.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud `SizeSettings` objekt určuje nenulovou vodorovné změny velikosti.

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout::SizeSettings::IsNone

Kontroluje,-li změnit velikost dat určuje beze změny velikosti.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud `SizeSettings` objekt určuje beze změny velikosti.

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout::SizeSettings::IsVertical

Kontroluje,-li změnit velikost dat určuje nenulovou svislé změny velikosti.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud `SizeSettings` objekt určuje nenulovou svislé změny velikosti.

##  <a name="sizevertical"></a>  CMFCDynamicLayout::SizeVertical

Získá [SizeSettings](#sizesettings_structure) hodnotu, která určuje, kolik podřízený ovládací prvek svou velikost svisle když uživatel změní jeho hostitelského okna.

```
static SizeSettings SizeVertical(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Definuje jako procento, jak daleko podřízený ovládací prvek svou velikost svisle když uživatel změní velikost okna hostitele.

### <a name="return-value"></a>Návratová hodnota

A [SizeSettings](#sizesettings_structure) hodnotu, která zapouzdřuje poměr požadované velikosti.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
