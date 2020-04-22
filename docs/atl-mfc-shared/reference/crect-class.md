---
title: CRect – třída
ms.date: 11/06/2018
f1_keywords:
- CRect
- ATLTYPES/ATL::CRect
- ATLTYPES/ATL::CRect::CRect
- ATLTYPES/ATL::CRect::BottomRight
- ATLTYPES/ATL::CRect::CenterPoint
- ATLTYPES/ATL::CRect::CopyRect
- ATLTYPES/ATL::CRect::DeflateRect
- ATLTYPES/ATL::CRect::EqualRect
- ATLTYPES/ATL::CRect::Height
- ATLTYPES/ATL::CRect::InflateRect
- ATLTYPES/ATL::CRect::IntersectRect
- ATLTYPES/ATL::CRect::IsRectEmpty
- ATLTYPES/ATL::CRect::IsRectNull
- ATLTYPES/ATL::CRect::MoveToX
- ATLTYPES/ATL::CRect::MoveToXY
- ATLTYPES/ATL::CRect::MoveToY
- ATLTYPES/ATL::CRect::NormalizeRect
- ATLTYPES/ATL::CRect::OffsetRect
- ATLTYPES/ATL::CRect::PtInRect
- ATLTYPES/ATL::CRect::SetRect
- ATLTYPES/ATL::CRect::SetRectEmpty
- ATLTYPES/ATL::CRect::Size
- ATLTYPES/ATL::CRect::SubtractRect
- ATLTYPES/ATL::CRect::TopLeft
- ATLTYPES/ATL::CRect::UnionRect
- ATLTYPES/ATL::CRect::Width
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
ms.openlocfilehash: b99eca7fe3a9c84f8b79ef3d694e27b6dd74dcd9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747065"
---
# <a name="crect-class"></a>CRect – třída

Podobně jako struktura [WINDOWS RECT.](/windows/win32/api/windef/ns-windef-rect)

## <a name="syntax"></a>Syntaxe

```
class CRect : public tagRECT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRect::CRect](#crect)|Vytvoří `CRect` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRect::Vpravo dole](#bottomright)|Vrátí pravý dolní bod `CRect`.|
|[CRect::CenterPoint](#centerpoint)|Vrátí středový `CRect`bod aplikace .|
|[CRect::CopyRect](#copyrect)|Zkopíruje rozměry zdrojového `CRect`obdélníku do aplikace .|
|[CRect::DeflateRect](#deflaterect)|Zmenší šířku a `CRect`výšku .|
|[CRect::EqualRect](#equalrect)|Určuje, `CRect` zda se rovná danému obdélníku.|
|[CRect::Výška](#height)|Vypočítá výšku . `CRect`|
|[CRect::InflateRect](#inflaterect)|Zvětší šířku `CRect`a výšku .|
|[CRect::IntersectRect](#intersectrect)|Nastaví `CRect` se jako průsečík dvou obdélníků.|
|[CRect::IsRectEmpty](#isrectempty)|Určuje, `CRect` zda je prázdný. `CRect`je prázdný, pokud je šířka nebo výška 0.|
|[CRect::IsRectNull](#isrectnull)|Určuje, zda `top` `bottom`jsou `left`všechny `right` proměnné , , a členské proměnné rovny 0.|
|[CRect::MoveToX](#movetox)|Přesune `CRect` se na zadanou souřadnici x.|
|[CRect::MoveToXY](#movetoxy)|Přesune `CRect` se na zadané souřadnice x a y.|
|[CRect::MoveToY](#movetoy)|Přesune `CRect` se na zadanou souřadnici y.|
|[CRect::NormalizeRect](#normalizerect)|Standardizuje výšku a šířku `CRect`.|
|[CRect::OffsetRect](#offsetrect)|Posune `CRect` o zadané posuny.|
|[CRect::PtInRect](#ptinrect)|Určuje, zda zadaný `CRect`bod leží uvnitř .|
|[CRect::SetRect](#setrect)|Nastaví rozměry `CRect`.|
|[CRect::SetRectEmpty](#setrectempty)|Nastaví `CRect` na prázdný obdélník (všechny souřadnice se rovnají 0).|
|[CRect::Velikost](#size)|Vypočítá velikost . `CRect`|
|[CRect::SubtractRect](#subtractrect)|Odečte jeden obdélník od druhého.|
|[CRect::Vlevo nahoře](#topleft)|Vrátí levý horní bod `CRect`.|
|[CRect::UnionRect](#unionrect)|Sady `CRect` se rovnají sjednocení dvou obdélníků.|
|[CRect::Šířka](#width)|Vypočítá šířku `CRect`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CRect::operátor -](#operator_-)|Odečte dané posuny `CRect` od nebo `CRect` vyfoukne `CRect`a vrátí výsledné .|
|[CRect::operátor LPCRECT](#operator_lpcrect)|Převede `CRect` a `LPCRECT`na .|
|[CRect::operátor LPRECT](#operator_lprect)|Převede `CRect` a `LPRECT`na .|
|[CRect::operátor !=](#operator_neq)|Určuje, `CRect` zda se nerovná obdélníku.|
|[CRect::operátor&amp;](#operator_amp)|Vytvoří průsečík `CRect` a obdélník a `CRect`vrátí výsledný .|
|[CRect::operátor&amp;=](#operator_amp_eq)|Nastaví `CRect` se jako `CRect` průsečík a obdélník.|
|[CRect::&#124;operátora](#operator_or)|Vytvoří sjednocení `CRect` a obdélník a vrátí `CRect`výsledné .|
|[CRect::operátor &#124;=](#operator_or_eq)|Sady `CRect` se rovnají `CRect` sjednocení a obdélník.|
|[CRect::operátor +](#operator_add)|Přidá dané posuny `CRect` nebo `CRect` nafoukne a `CRect`vrátí výsledné .|
|[CRect::operátor +=](#operator_add_eq)|Přidá zadané posuny `CRect` nebo `CRect`nafoukne .|
|[CRect::operátor =](#operator_eq)|Zkopíruje rozměry obdélníku `CRect`do .|
|[CRect::operátor -=](#operator_-_eq)|Odečte zadané posuny `CRect` od nebo `CRect`vyfoukne .|
|[CRect::operátor ==](#operator_eq_eq)|Určuje, `CRect` zda se rovná obdélníku.|

## <a name="remarks"></a>Poznámky

`CRect`zahrnuje také členské funkce `CRect` pro `RECT` manipulaci s objekty a struktury systému Windows.

Objekt `CRect` může být předán jako parametr `RECT` funkce `LPCRECT`všude tam, kde struktura , nebo `LPRECT` může být předán.

> [!NOTE]
> Tato třída je odvozena od `tagRECT` struktury. (Název `tagRECT` je méně běžně používaný název `RECT` pro strukturu.) To znamená, že`left`datové `top` `right`členy `bottom`( , `RECT` , a ) `CRect`struktury jsou přístupné datové členy .

A `CRect` obsahuje členské proměnné, které definují body obdélníku vlevo nahoře a vpravo dole.

Při zadávání `CRect`, musíte být opatrní, aby ji sestavit tak, aby je normalizována – jinými slovy tak, aby hodnota levé souřadnice je menší než vpravo a horní je menší než dole. Například vlevo nahoře (10,10) a vpravo dole (20,20) definuje normalizované obdélník, ale vlevo nahoře (20,20) a vpravo dole (10,10) definuje nenormalizované obdélník. Pokud obdélník není normalizován, `CRect` mnoho členských funkcí může vrátit nesprávné výsledky. (Seznam těchto funkcí naleznete v tématu [CRect::NormalizeRect.)](#normalizerect) Před voláním funkce, která vyžaduje normalizované obdélníky, můžete normalizovat `NormalizeRect` nenormalizované obdélníky voláním funkce.

Při manipulaci `CRect` s členskými funkcemi [CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp) a [CDC::LPtoDP](../../mfc/reference/cdc-class.md#lptodp) buďte opatrní. Pokud je režim mapování kontextu zobrazení takový, že rozsah y `MM_LOENGLISH`je `CDC::DPtoLP` záporný, jako v , pak transformuje `CRect` tak, aby jeho horní část byla větší než dolní. Funkce, `Height` jako `Size` je například a vrátí záporné hodnoty pro výšku transformované `CRect`a obdélník bude nenormalizován.

Při použití `CRect` přetížené operátory, první `CRect`operand musí být ; druhý může být buď [RECT](/windows/win32/api/windef/ns-windef-rect) `CRect` struktury nebo objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagRECT`

`CRect`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltypes.h

## <a name="crectbottomright"></a><a name="bottomright"></a>CRect::Vpravo dole

Souřadnice jsou vráceny jako odkaz na [cpoint](cpoint-class.md) objekt, který je obsažen v `CRect`.

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Souřadnice pravého dolního rohu obdélníku.

### <a name="remarks"></a>Poznámky

Tuto funkci můžete použít k získání nebo nastavení pravého dolního rohu obdélníku. Nastavte roh pomocí této funkce na levé straně operátoru přiřazení.

### <a name="example"></a>Příklad

```cpp
// use BottomRight() to retrieve the bottom
// right POINT
CRect rect(210, 150, 350, 900);
CPoint ptDown;

ptDown = rect.BottomRight();

// ptDown is now set to (350, 900)
ASSERT(ptDown == CPoint(350, 900));

// or, use BottomRight() to set the bottom
// right POINT
CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);

CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);
rect2.BottomRight() = ptLow;

// rect2 is now (10, 10, 180, 180)
ASSERT(rect2 == CRect(10, 10, 180, 180));
```

## <a name="crectcenterpoint"></a><a name="centerpoint"></a>CRect::CenterPoint

Vypočítá středový `CRect` bod přidáním levé a pravé hodnoty a dělením dvěma a přidáním nejvyšších a dolních hodnot a dělením dvěma.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Objekt, `CPoint` který je středovým `CRect`bodem aplikace .

### <a name="example"></a>Příklad

```cpp
// Code from this OnPaint() implementation can be pasted into your own application
// to draw lines that would look like a letter "Y" within your dialog.
void CMyDlg::OnPaint()
{
    CPaintDC dc(this);

    // device context for painting

    // get the size and position of the client area of
    // your window

    CRect rect;
    GetClientRect(&rect);

    // Move the current pen to the top left of the window. We call the
    // TopLeft() member of CRect here and it returns a CPoint object we
    // pass to the override of CDC::MoveTo() that accepts a CPoint.

    dc.MoveTo(rect.TopLeft());

    // Draw a line from the top left to the center of the window.
    // CenterPoint() gives us the middle point of the window as a
    // CPoint, and since CDC::LineTo() has an override that accepts a
    // CPoint, we can just pass it along.

    dc.LineTo(rect.CenterPoint());

    // Now, draw a line to the top right of the window. There's no
    // CRect member which returns a CPoint for the top right of the
    // window, so we'll reference the CPoint members directly and call
    // the CDC::LineTo() override which takes two integers.

    dc.LineTo(rect.right, rect.top);

    // The top part of the "Y" is drawn. Now, we'll draw the stem. We
    // start from the center point.

    dc.MoveTo(rect.CenterPoint());

    // and then draw to the middle of the bottom edge of the window.
    // We'll get the x-coordinate from the x member of the CPOINT
    // returned by CenterPoint(), and the y value comes directly from
    // the rect.

    dc.LineTo(rect.CenterPoint().x, rect.bottom);
}
```

## <a name="crectcopyrect"></a><a name="copyrect"></a>CRect::CopyRect

Zkopíruje `lpSrcRect` obdélník `CRect`do .

```cpp
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>Parametry

*lpSrcRect*<br/>
Odkazuje na [rect](/windows/win32/api/windef/ns-windef-rect) `CRect` strukturu nebo objekt, který má být zkopírován.

### <a name="example"></a>Příklad

```cpp
CRect rectSource(35, 10, 125, 10);
CRect rectDest;

rectDest.CopyRect(&rectSource);

// rectDest is now set to (35, 10, 125, 10)

RECT rectSource2;
rectSource2.left = 0;
rectSource2.top = 0;
rectSource2.bottom = 480;
rectSource2.right = 640;

rectDest.CopyRect(&rectSource2);

// works against RECT structures, too!
// rectDest is now set to (0, 0, 640, 480)
```

## <a name="crectcrect"></a><a name="crect"></a>CRect::CRect

Vytvoří `CRect` objekt.

```
CRect() throw();
CRect(int l, int t, int r, int b) throw();
CRect(const RECT& srcRect) throw();
CRect(LPCRECT lpSrcRect) throw();
CRect(POINT point, SIZE size) throw();
CRect(POINT topLeft, POINT bottomRight) throw();
```

### <a name="parameters"></a>Parametry

*L*<br/>
Určuje levou polohu `CRect`souboru .

*t*<br/>
Určuje horní část `CRect`.

*R*<br/>
Určuje správnou polohu `CRect`.

*B*<br/>
Určuje dolní část `CRect`písmene .

*srcRect*<br/>
Odkazuje na strukturu [RECT](/windows/win32/api/windef/ns-windef-rect) se souřadnicemi pro `CRect`.

*lpSrcRect*<br/>
Odkazuje na `RECT` strukturu s souřadnicemi pro `CRect`.

*Bod*<br/>
Určuje počáteční bod pro obdélník, který má být vytvořen. Odpovídá levému hornímu rohu.

*Velikost*<br/>
Určuje posunutí z levého horního rohu do pravého dolního rohu obdélníku, který má být vytvořen.

*topLeft*<br/>
Určuje polohu levého `CRect`horního rohu .

*bottomRight*<br/>
Určuje polohu vpravo `CRect`dole .

### <a name="remarks"></a>Poznámky

Pokud nejsou uvedeny `left`žádné `top` `right`argumenty, , , a `bottom` členy nejsou inicializovány.

Konstruktory `CRect` `CRect`(`LPCRECT``const RECT&`) a ( ) provádějí [CopyRect](#copyrect). Ostatní konstruktory inicializovat členské proměnné objektu přímo.

### <a name="example"></a>Příklad

```cpp
// default constructor doesn't initialize!
CRect rectUnknown;

// four-integers are left, top, right, and bottom
CRect rect(0, 0, 100, 50);
ASSERT(rect.Width() == 100);
ASSERT(rect.Height() == 50);

// Initialize from RECT structure
RECT sdkRect;
sdkRect.left = 0;
sdkRect.top = 0;
sdkRect.right = 100;
sdkRect.bottom = 50;

CRect rect2(sdkRect);
// by reference
CRect rect3(&sdkRect);

// by address
ASSERT(rect2 == rect);
ASSERT(rect3 == rect);

// from a point and a size
CPoint pt(0, 0);
CSize sz(100, 50);
CRect rect4(pt, sz);
ASSERT(rect4 == rect2);

// from two points
CPoint ptBottomRight(100, 50);
CRect rect5(pt, ptBottomRight);
ASSERT(rect5 == rect4);
```

## <a name="crectdeflaterect"></a><a name="deflaterect"></a>CRect::DeflateRect

`DeflateRect`vyfoukne `CRect` pohybem svých stran směrem ke středu.

```cpp
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Určuje počet jednotek, které mají být `CRect`vyfouknuty na levé a pravé straně .

*Y*<br/>
Určuje počet jednotek, které mají být `CRect`vyfouknuty, horní a dolní část .

*Velikost*<br/>
A [SIZE](/windows/win32/api/windef/ns-windef-size) nebo [CSize,](csize-class.md) který určuje `CRect`počet jednotek k deflaci . Hodnota `cx` určuje počet jednotek pro deflaci levé a `cy` pravé strany a hodnota určuje počet jednotek pro deflaci horní a dolní části.

*lpRect*<br/>
Odkazuje na strukturu [RECT](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` určuje počet jednotek, které mají být vyfouknuty na každé straně.

*L*<br/>
Určuje počet jednotek, které mají `CRect`být vyfouknuty na levé straně .

*t*<br/>
Určuje počet jednotek, které mají `CRect`být vyfouknuty v horní části .

*R*<br/>
Určuje počet jednotek, které mají `CRect`být vyfouknuty na pravé straně .

*B*<br/>
Určuje počet jednotek, které mají `CRect`být vyfouknuty na spodní straně .

### <a name="remarks"></a>Poznámky

Chcete-li `DeflateRect` to provést, přidá jednotky vlevo a nahoře a odečte jednotky z pravé a dolní části. Parametry `DeflateRect` jsou podepsané hodnoty; kladné `CRect` hodnoty se vyfouknou a záporné hodnoty je nafouknou.

První dvě přetížení vyfouknou oba `CRect` páry protilehlých stran tak, aby `cx`jeho celková šířka byla snížena dvakrát *x* (nebo ) a jeho celková výška se snížila dvakrát *y* (nebo `cy`). Další dvě přetížení vyfouknou každou stranu `CRect` nezávisle na ostatních.

### <a name="example"></a>Příklad

```cpp
CRect rect(10, 10, 50, 50);
rect.DeflateRect(1, 2);
ASSERT(rect.left == 11 && rect.right == 49);
ASSERT(rect.top == 12 && rect.bottom == 48);

CRect rect2(10, 10, 50, 50);
CRect rectDeflate(1, 2, 3, 4);
rect2.DeflateRect(&rectDeflate);
ASSERT(rect2.left == 11 && rect2.right == 47);
ASSERT(rect2.top == 12 && rect2.bottom == 46);
```

## <a name="crectequalrect"></a><a name="equalrect"></a>CRect::EqualRect

Určuje, `CRect` zda se rovná danému obdélníku.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na [rect](/windows/win32/api/windef/ns-windef-rect) `CRect` strukturu nebo objekt, který obsahuje souřadnice levého horního a pravého dolního rohu obdélníku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud mají dva obdélníky stejné hodnoty nahoře, vlevo, dole a vpravo; jinak 0.

> [!NOTE]
> Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélníky před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1.EqualRect(rect2));
ASSERT(!rect1.EqualRect(rect3));
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1.EqualRect(&test));
```

## <a name="crectheight"></a><a name="height"></a>CRect::Výška

Vypočítá výšku `CRect` odečtením nejvyšší hodnoty od spodní hodnoty.

```
int Height() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Výška `CRect`.

### <a name="remarks"></a>Poznámky

Výsledná hodnota může být záporná.

> [!NOTE]
> Obdélník musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélník před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

## <a name="crectinflaterect"></a><a name="inflaterect"></a>CRect::InflateRect

`InflateRect`nafoukne `CRect` posunutím boků od středu.

```cpp
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Určuje počet jednotek, které mají nafouknout levou a pravou stranu . `CRect`

*Y*<br/>
Určuje počet jednotek, které mají být `CRect`nafouknuty v horní a dolní části .

*Velikost*<br/>
A [SIZE](/windows/win32/api/windef/ns-windef-size) nebo [CSize,](csize-class.md) který určuje `CRect`počet jednotek nafouknout . Hodnota `cx` určuje počet jednotek pro nafouknutí levé a `cy` pravé strany a hodnota určuje počet jednotek pro nafouknutí horní a dolní části.

*lpRect*<br/>
Odkazuje na strukturu [RECT](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` určuje počet jednotek, které mají být nafouknuty na každé straně.

*L*<br/>
Určuje počet jednotek, které mají `CRect`být nafouknuty na levé straně .

*t*<br/>
Určuje počet jednotek, které mají `CRect`být nafouknuty v horní části .

*R*<br/>
Určuje počet jednotek, které mají `CRect`být nafouknuty na pravé straně .

*B*<br/>
Určuje počet jednotek, které mají `CRect`být nafouknuty na spodní straně .

### <a name="remarks"></a>Poznámky

Chcete-li `InflateRect` to provést, odečte jednotky zleva a nahoru a přidá jednotky vpravo a dole. Parametry `InflateRect` jsou podepsané hodnoty; kladné `CRect` hodnoty se nafouknou a záporné hodnoty je vyfouknou.

První dvě přetížení `CRect` nafouknou oba páry protilehlých stran tak, aby se jeho celková šířka zvýšila dvakrát `cy`x (nebo *x* `cx`) a jeho celková výška se zvýšila dvakrát *y* (nebo ). Další dvě přetížení nafouknou `CRect` každou stranu nezávisle na ostatních.

### <a name="example"></a>Příklad

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

## <a name="crectintersectrect"></a><a name="intersectrect"></a>CRect::IntersectRect

Vytvoří `CRect` rovno průsečíku dvou existujících obdélníků.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parametry

*lpRect1*<br/>
Odkazuje na [rect](/windows/win32/api/windef/ns-windef-rect) `CRect` strukturu nebo objekt, který obsahuje zdrojový obdélník.

*lpRect2*<br/>
Odkazuje na `RECT` strukturu `CRect` nebo objekt, který obsahuje zdrojový obdélník.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud průsečík není prázdný; 0, pokud je průsečík prázdný.

### <a name="remarks"></a>Poznámky

Průsečík je největší obdélník obsažený v obou existujících obdélníků.

> [!NOTE]
> Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélníky před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect rectOne(125,  0, 150, 200);
CRect rectTwo(0, 75, 350, 95);
CRect rectInter;

rectInter.IntersectRect(rectOne, rectTwo);
ASSERT(rectInter == CRect(125, 75, 150, 95));
// operator &= can do the same task:

CRect rectInter2 = rectOne;
rectInter2 &= rectTwo;
ASSERT(rectInter2 == CRect(125, 75, 150, 95));
```

## <a name="crectisrectempty"></a><a name="isrectempty"></a>CRect::IsRectEmpty

Určuje, `CRect` zda je prázdný.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud `CRect` je prázdná; 0, `CRect` pokud není prázdný.

### <a name="remarks"></a>Poznámky

Obdélník je prázdný, pokud je šířka nebo výška 0 nebo záporná. Liší se `IsRectNull`od , který určuje, zda jsou všechny souřadnice obdélníku nulové.

> [!NOTE]
> Obdélník musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélník před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

## <a name="crectisrectnull"></a><a name="isrectnull"></a>CRect::IsRectNull

Určuje, zda jsou nejvyšší, levé, dolní `CRect` a pravé hodnoty rovny 0.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud `CRect`jsou hodnoty 's horní, levé, dolní a pravé rovny 0; jinak 0.

### <a name="remarks"></a>Poznámky

Liší se `IsRectEmpty`od , který určuje, zda je obdélník prázdný.

### <a name="example"></a>Příklad

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
ASSERT(!rectSome.IsRectNull());
// note that null means _all_ zeros

CRect rectNotNull(0, 0, 35, 50);
ASSERT(!rectNotNull.IsRectNull());
```

## <a name="crectmovetox"></a><a name="movetox"></a>CRect::MoveToX

Volánítéto funkce přesunout obdélník na absolutní souřadnice x určené *x*.

```cpp
void MoveToX(int x) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Absolutní souřadnice x pro levý horní roh obdélníku.

### <a name="example"></a>Příklad

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

## <a name="crectmovetoxy"></a><a name="movetoxy"></a>CRect::MoveToXY

Volání této funkce přesunout obdélník na absolutní x- a y souřadnice zadané.

```cpp
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Absolutní souřadnice x pro levý horní roh obdélníku.

*Y*<br/>
Absolutní souřadnice y pro levý horní roh obdélníku.

*Bod*<br/>
Struktura `POINT` určující absolutní levý horní roh obdélníku.

### <a name="example"></a>Příklad

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

## <a name="crectmovetoy"></a><a name="movetoy"></a>CRect::MoveToY

Volání této funkce přesunout obdélník na absolutní souřadnice y určené *y*.

```cpp
void MoveToY(int y) throw();
```

### <a name="parameters"></a>Parametry

*Y*<br/>
Absolutní souřadnice y pro levý horní roh obdélníku.

### <a name="example"></a>Příklad

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

## <a name="crectnormalizerect"></a><a name="normalizerect"></a>CRect::NormalizeRect

Normalizuje `CRect` tak, aby výška i šířka byly kladné.

```cpp
void NormalizeRect() throw();
```

### <a name="remarks"></a>Poznámky

Obdélník je normalizován pro umístění ve čtvrtém kvadrantu, které systém Windows obvykle používá pro souřadnice. `NormalizeRect`porovná horní a dolní hodnoty a zamění je, pokud je horní hodnota větší než dole. Podobně zamění levé a pravé hodnoty, pokud je levá hodnota větší než pravá. Tato funkce je užitečná při práci s různými režimy mapování a obrácené obdélníky.

> [!NOTE]
> Následující `CRect` členské funkce vyžadují normalizované obdélníky, aby fungovaly správně: [Výška](#height), [Šířka](#width), [Velikost](#size), [IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [SubtractRect](#subtractrect), [operátor ==](#operator_eq_eq), [operátor !=](#operator_neq), [operátor &#124;](#operator_or), operátor [&#124;,](#operator_or_eq)operátor [&](#operator_amp)a operátor [&=](#operator_amp_eq).

### <a name="example"></a>Příklad

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

## <a name="crectoffsetrect"></a><a name="offsetrect"></a>CRect::OffsetRect

Posune `CRect` o zadané posuny.

```cpp
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Určuje částku, která má být posunuta doleva nebo doprava. Musí být negativní, když se pohybujete doleva.

*Y*<br/>
Určuje částku, která se má přesunout nahoru nebo dolů. Musí být negativní, když se posunete nahoru.

*Bod*<br/>
Obsahuje [point](/windows/win32/api/windef/ns-windef-point) strukturu nebo [CPoint](cpoint-class.md) objekt určující obě dimenze, podle kterých se mají přesunout.

*Velikost*<br/>
Obsahuje [size](/windows/win32/api/windef/ns-windef-size) structure nebo [CSize](csize-class.md) objekt určující obě dimenze, podle kterých se mají přesunout.

### <a name="remarks"></a>Poznámky

Přesune `CRect` *jednotky x* podél osy x a *jednotek y* podél osy y. Parametry *x* a *y* jsou `CRect` podepsané hodnoty, takže mohou být přesunuty doleva nebo doprava a nahoru nebo dolů.

### <a name="example"></a>Příklad

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

## <a name="crectoperator-lpcrect-converts-a-crect-to-an-lpcrect"></a><a name="operator_lpcrect"></a>CRect::operátor LPCRECT Převede a `CRect` na [LPCRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Poznámky

Při použití této funkce nepotřebujete operátor address-of**&**( ). Tento operátor bude automaticky použit `CRect` při předání objektu funkci, která očekává `LPCRECT`.

## <a name="crectoperator-lprect"></a><a name="operator_lprect"></a>CRect::operátor LPRECT

Převede `CRect` a na [LPRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPRECT() throw();
```

### <a name="remarks"></a>Poznámky

Při použití této funkce nepotřebujete operátor address-of**&**( ). Tento operátor bude automaticky použit `CRect` při předání objektu funkci, která očekává `LPRECT`.

### <a name="example"></a>Příklad

Viz příklad pro [CRect::operator LPCRECT](#operator_lpcrect).

## <a name="crectoperator-"></a><a name="operator_eq"></a>CRect::operátor =

Přiřadí *srcRect* společnosti `CRect`.

```cpp
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Parametry

*srcRect*<br/>
Odkazuje na zdrojový obdélník. Může být [RECT](/windows/win32/api/windef/ns-windef-rect) nebo `CRect`.

### <a name="example"></a>Příklad

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

## <a name="crectoperator-"></a><a name="operator_eq_eq"></a>CRect::operátor ==

Určuje, `rect` zda se `CRect` rovná porovnáním souřadnic jejich levých a pravých dolních rohů.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Odkazuje na zdrojový obdélník. Může být [RECT](/windows/win32/api/windef/ns-windef-rect) nebo `CRect`.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je rovna; jinak 0.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélníky před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1 == rect2);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1 == test);
```

## <a name="crectoperator-"></a><a name="operator_neq"></a>CRect::operátor !=

Určuje, zda *rect* není `CRect` rovno porovnáním souřadnic jejich levého horního a pravého dolního rohu.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Odkazuje na zdrojový obdélník. Může být [RECT](/windows/win32/api/windef/ns-windef-rect) nebo `CRect`.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud není rovna; jinak 0.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélníky před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999,  6,  3);
ASSERT(rect1 != rect3);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect3 != test);
```

## <a name="crectoperator-"></a><a name="operator_add_eq"></a>CRect::operátor +=

První dvě přetížení `CRect` přesunout zadané posuny.

```cpp
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
A [POINT](/windows/win32/api/windef/ns-windef-point) struktura nebo [CPoint](cpoint-class.md) objekt, který určuje počet jednotek přesunout obdélník.

*Velikost*<br/>
A [SIZE](/windows/win32/api/windef/ns-windef-size) struktura nebo [CSize](csize-class.md) objekt, který určuje počet jednotek přesunout obdélník.

*lpRect*<br/>
Odkazuje na [rect](/windows/win32/api/windef/ns-windef-rect) `CRect` strukturu nebo objekt, který obsahuje počet `CRect`jednotek nafouknout každou stranu .

### <a name="remarks"></a>Poznámky

Hodnoty *parametru x* a `cx` *y* (nebo a `CRect` `cy`) jsou přidány do .

Třetí přetížení nafoukne `CRect` počet jednotek určených v každém člen parametru.

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-_eq"></a>CRect::operátor -=

První dvě přetížení `CRect` přesunout zadané posuny.

```cpp
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
A [POINT](/windows/win32/api/windef/ns-windef-point) struktura nebo [CPoint](cpoint-class.md) objekt, který určuje počet jednotek přesunout obdélník.

*Velikost*<br/>
A [SIZE](/windows/win32/api/windef/ns-windef-size) struktura nebo [CSize](csize-class.md) objekt, který určuje počet jednotek přesunout obdélník.

*lpRect*<br/>
Odkazuje na [rect](/windows/win32/api/windef/ns-windef-rect) `CRect` strukturu nebo objekt, který obsahuje počet `CRect`jednotek deflaci každé straně .

### <a name="remarks"></a>Poznámky

Hodnoty *parametru x* a `cx` *y* (nebo a `cy`) `CRect`se odečtou od .

Třetí přetížení vyfoukne `CRect` počet jednotek zadaných v každém člen parametru. Všimněte si, že toto přetížení funguje jako [DeflateRect](#deflaterect).

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp_eq"></a>CRect::operátor&amp;=

Sady `CRect` se rovnají `CRect` průsečíku a `rect`.

```cpp
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Obsahuje [RECT](/windows/win32/api/windef/ns-windef-rect) `CRect`nebo .

### <a name="remarks"></a>Poznámky

Průsečík je největší obdélník, který je obsažen v obou obdélníků.

> [!NOTE]
> Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélníky před voláním této funkce.

### <a name="example"></a>Příklad

Viz příklad pro [CRect::IntersectRect](#intersectrect).

## <a name="crectoperator-124"></a><a name="operator_or_eq"></a>CRect::operátor &#124;=

Sady `CRect` se rovnají `CRect` sjednocení `rect`a .

```cpp
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Obsahuje `CRect` a nebo [RECT](/windows/win32/api/windef/ns-windef-rect).

### <a name="remarks"></a>Poznámky

Sjednocení je nejmenší obdélník, který obsahuje oba zdrojové obdélníky.

> [!NOTE]
> Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélníky před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

## <a name="crectoperator-"></a><a name="operator_add"></a>CRect::operátor +

První dvě přetížení vrátí `CRect` objekt, který `CRect` se rovná posunuze zadané posuny.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
A [POINT](/windows/win32/api/windef/ns-windef-point) struktura nebo [CPoint](cpoint-class.md) objekt, který určuje počet jednotek přesunout vrácenou hodnotu.

*Velikost*<br/>
A [SIZE](/windows/win32/api/windef/ns-windef-size) structure nebo [CSize](csize-class.md) objekt, který určuje počet jednotek přesunout vrácenou hodnotu.

*lpRect*<br/>
Odkazuje na [rect](/windows/win32/api/windef/ns-windef-rect) `CRect` strukturu nebo objekt, který obsahuje počet jednotek nafouknout každou stranu vrácené hodnoty.

### <a name="return-value"></a>Návratová hodnota

Vyplývající `CRect` z přesunutí nebo nafouknutí `CRect` podle počtu jednotek zadaných v parametru.

### <a name="remarks"></a>Poznámky

Parametry *parametru x* a `cx` `cy` *y* (nebo a `CRect`) jsou přidány do polohy 's.

Třetí přetížení vrátí `CRect` nový, který `CRect` se rovná nahuštěné počet jednotek zadaných v každém člen parametru.

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-"></a>CRect::operátor -

První dvě přetížení vrátí `CRect` objekt, který `CRect` se rovná posunuze zadané posuny.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Point [POINT](/windows/win32/api/windef/ns-windef-point) struktura `CPoint` nebo objekt, který určuje počet jednotek přesunout vrácenou hodnotu.

*Velikost*<br/>
A [SIZE](/windows/win32/api/windef/ns-windef-size) `CSize` struktura nebo objekt, který určuje počet jednotek přesunout vrácenou hodnotu.

*lpRect*<br/>
Odkazuje na [rect](/windows/win32/api/windef/ns-windef-rect) `CRect` strukturu nebo objekt, který obsahuje počet jednotek deflaci každé straně vrácené hodnoty.

### <a name="return-value"></a>Návratová hodnota

Vyplývající `CRect` z přesunutí nebo deflaci `CRect` o počet jednotek zadaný v parametru.

### <a name="remarks"></a>Poznámky

Parametry *parametru x* a `cx` `cy` *y* (nebo a ) `CRect`se odečtou od pozice .

Třetí přetížení vrátí `CRect` nový, který `CRect` se rovná deflaci počet jednotek zadaných v každém člen parametru. Všimněte si, že toto přetížení funguje jako [DeflateRect](#deflaterect), ne [SubtractRect](#subtractrect).

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp"></a>CRect::operátor&amp;

Vrátí `CRect` hodnotu a, `CRect` která je průsečíkem a *rect2*.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Parametry

*rect2*<br/>
Obsahuje [RECT](/windows/win32/api/windef/ns-windef-rect) `CRect`nebo .

### <a name="return-value"></a>Návratová hodnota

A, `CRect` který je `CRect` průsečík a *rect2*.

### <a name="remarks"></a>Poznámky

Průsečík je největší obdélník, který je obsažen v obou obdélníků.

> [!NOTE]
> Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélníky před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

## <a name="crectoperator-124"></a><a name="operator_or"></a>CRect::operátor &#124;

Vrátí `CRect` a, která `CRect` je sjednocení a *rect2*.

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>Parametry

*rect2*<br/>
Obsahuje [RECT](/windows/win32/api/windef/ns-windef-rect) `CRect`nebo .

### <a name="return-value"></a>Návratová hodnota

A, `CRect` který je `CRect` spojení a *rect2*.

### <a name="remarks"></a>Poznámky

Sjednocení je nejmenší obdélník, který obsahuje oba obdélníky.

> [!NOTE]
> Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélníky před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectptinrect"></a><a name="ptinrect"></a>CRect::PtInRect

Určuje, zda zadaný `CRect`bod leží uvnitř .

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Obsahuje [point](/windows/win32/api/windef/ns-windef-point) strukturu nebo [CPoint](cpoint-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud `CRect`bod leží uvnitř ; jinak 0.

### <a name="remarks"></a>Poznámky

Bod je `CRect` uvnitř, pokud leží na levé nebo horní straně nebo je ve všech čtyřech stranách. Bod na pravé nebo spodní `CRect`straně je venku .

> [!NOTE]
> Obdélník musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélník před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect rect(5, 5, 100, 100);
CPoint pt1(35, 50);
CPoint pt2(125, 298);

// this is true, because pt1 is inside the rectangle
ASSERT(rect.PtInRect(pt1));

// this is NOT true, because pt2 is outside the rectangle
ASSERT(!rect.PtInRect(pt2));

// note that the right and the bottom aren't inside
ASSERT(!rect.PtInRect(CPoint(35, 100)));
ASSERT(!rect.PtInRect(CPoint(100, 98)));

// but the top and the left are inside
ASSERT(rect.PtInRect(CPoint(5, 65)));
ASSERT(rect.PtInRect(CPoint(88, 5)));

// and that PtInRect() works against a POINT, too
POINT pt;
pt.x = 35;
pt.y = 50;
ASSERT(rect.PtInRect(pt));
```

## <a name="crectsetrect"></a><a name="setrect"></a>CRect::SetRect

Nastaví rozměry `CRect` zadaných souřadnic.

```cpp
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>Parametry

*x1*<br/>
Určuje souřadnici x levého horního rohu.

*y1*<br/>
Určuje souřadnici y levého horního rohu.

*x2*<br/>
Určuje souřadnici x pravého dolního rohu.

*y2*<br/>
Určuje souřadnici y pravého dolního rohu.

### <a name="example"></a>Příklad

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

## <a name="crectsetrectempty"></a><a name="setrectempty"></a>CRect::SetRectEmpty

Vytvoří `CRect` prázdný obdélník nastavením všech souřadnic na nulu.

```cpp
void SetRectEmpty() throw();
```

### <a name="example"></a>Příklad

```cpp
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());
```

## <a name="crectsize"></a><a name="size"></a>CRect::VELIKOST

A `cx` `cy` členy vrácené hodnoty obsahují výšku `CRect`a šířku .

```
CSize Size() const throw();
```

### <a name="return-value"></a>Návratová hodnota

[CSize](csize-class.md) objekt, který obsahuje `CRect`velikost .

### <a name="remarks"></a>Poznámky

Výška nebo šířka může být záporná.

> [!NOTE]
> Obdélník musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélník před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

## <a name="crectsubtractrect"></a><a name="subtractrect"></a>CRect::SubtractRect

Načiní rozměry `CRect` rovná odčítání `lpRectSrc2` od `lpRectSrc1`.

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Parametry

*lpRectSrc1*<br/>
Odkazuje na [rect](/windows/win32/api/windef/ns-windef-rect) `CRect` strukturu nebo objekt, ze kterého má být odečten obdélník.

*lpRectSrc2*<br/>
Odkazuje na `RECT` strukturu `CRect` nebo objekt, který má být odečten od obdélníku odkazuje *parametr lpRectSrc1.*

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Odčítání je nejmenší obdélník, který obsahuje všechny body v *lpRectScr1,* které nejsou v průsečíku *lpRectScr1* a *lpRectScr2*.

Obdélník určený *lpRectSrc1* se nezmění, pokud obdélník určený *lpRectSrc2* zcela nepřekrývá obdélník určený *lpRectSrc1* alespoň v jednom směru x nebo y.

Například pokud *lpRectSrc1* byly (10,10, 100,100) a *lpRectSrc2* byly (50,50, 150,150), obdélník ukázal *lpRectSrc1* by beze změny při vrácení funkce. Pokud *lpRectSrc1* byly (10,10, 100,100) a *lpRectSrc2* byly (50,10, 150,150), nicméně obdélník ukázal *lpRectSrc1* bude obsahovat souřadnice (10,10, 50,100) při vrácení funkce.

`SubtractRect`není totožný jako [operátor -](#operator_-) ani [operátor -=](#operator_-_eq). Ani jeden z těchto `SubtractRect`operátorů nikdy volání .

> [!NOTE]
> Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélníky před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
RECT   rectOne;
RECT   rectTwo;

rectOne.left = 10;
rectOne.top = 10;
rectOne.bottom = 100;
rectOne.right = 100;

rectTwo.left = 50;
rectTwo.top = 10;
rectTwo.bottom = 150;
rectTwo.right = 150;

CRect   rectDiff;

rectDiff.SubtractRect(&rectOne, &rectTwo);
CRect   rectResult(10, 10, 50, 100);

ASSERT(rectDiff == rectResult);

// works for CRect, too, since there is
// implicit CRect -> LPCRECT conversion

CRect rect1(10, 10, 100, 100);
CRect rect2(50, 10, 150, 150);
CRect rectOut;

rectOut.SubtractRect(rect1, rect2);
ASSERT(rectResult == rectOut);
```

## <a name="crecttopleft"></a><a name="topleft"></a>CRect::Vlevo nahoře

Souřadnice jsou vráceny jako odkaz na [cpoint](cpoint-class.md) objekt, který je obsažen v `CRect`.

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Souřadnice levého horního rohu obdélníku.

### <a name="remarks"></a>Poznámky

Tuto funkci můžete použít k získání nebo nastavení levého horního rohu obdélníku. Nastavte roh pomocí této funkce na levé straně operátoru přiřazení.

### <a name="example"></a>Příklad

Viz příklad pro [CRect::CenterPoint](#centerpoint).

## <a name="crectunionrect"></a><a name="unionrect"></a>CRect::UnionRect

Způsobí, že `CRect` rozměry rovná sjednocení dvou zdrojových obdélníků.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parametry

*lpRect1*<br/>
Odkazuje na [RECT](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` který obsahuje zdrojový obdélník.

*lpRect2*<br/>
Odkazuje na `RECT` `CRect` nebo který obsahuje zdrojový obdélník.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud není unie prázdná; 0, pokud je sjednocení prázdné.

### <a name="remarks"></a>Poznámky

Sjednocení je nejmenší obdélník, který obsahuje oba zdrojové obdélníky.

Systém Windows ignoruje rozměry prázdného obdélníku; to znamená obdélník, který nemá výšku nebo nemá šířku.

> [!NOTE]
> Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélníky před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectwidth"></a><a name="width"></a>CRect::Šířka

Vypočítá šířku `CRect` odečtením levé hodnoty od pravé hodnoty.

```
int Width() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Šířka `CRect`.

### <a name="remarks"></a>Poznámky

Šířka může být záporná.

> [!NOTE]
> Obdélník musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) normalizovat obdélník před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
// nWid is now 60
ASSERT(nWid == 60);
```

## <a name="see-also"></a>Viz také

[CPoint – třída](cpoint-class.md)<br/>
[CSize – třída](csize-class.md)<br/>
[Rect](/windows/win32/api/windef/ns-windef-rect)
