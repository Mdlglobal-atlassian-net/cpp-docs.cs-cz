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
ms.openlocfilehash: 2c84ce888e37b2a8985ca63cf3544205bc61f69f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491536"
---
# <a name="crect-class"></a>CRect – třída

Podobně jako ve struktuře Windows [Rect](/windows/win32/api/windef/ns-windef-rect) .

## <a name="syntax"></a>Syntaxe

```
class CRect : public tagRECT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CRect::CRect](#crect)|`CRect` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CRect::BottomRight](#bottomright)|Vrátí pravý dolní bod `CRect`.|
|[CRect::CenterPoint](#centerpoint)|Vrátí Centerpoint `CRect`.|
|[CRect::CopyRect](#copyrect)|Zkopíruje rozměry zdrojového obdélníku do `CRect`.|
|[CRect::DeflateRect](#deflaterect)|Zmenší šířku a výšku `CRect`.|
|[CRect::EqualRect](#equalrect)|Určuje, `CRect` zda se rovná danému obdélníku.|
|[CRect:: Height](#height)|Vypočítá výšku `CRect`.|
|[CRect::InflateRect](#inflaterect)|Zvětší šířku a výšku `CRect`.|
|[CRect::IntersectRect](#intersectrect)|Nastaví `CRect` se jako průnik dvou obdélníků.|
|[CRect::IsRectEmpty](#isrectempty)|Určuje, `CRect` zda je prázdný. `CRect`je prázdné, pokud je šířka nebo výška 0.|
|[CRect::IsRectNull](#isrectnull)|Určuje `top`, zda proměnné `bottom`členů `left`,, `right` a jsou všechny rovny 0.|
|[CRect::MoveToX](#movetox)|Přesune `CRect` se na zadanou souřadnici x.|
|[CRect::MoveToXY](#movetoxy)|Přesune `CRect` se na zadané souřadnice x a y.|
|[CRect::MoveToY](#movetoy)|Přesune `CRect` se na zadanou souřadnici y.|
|[CRect::NormalizeRect](#normalizerect)|Standardizace výšky a šířky `CRect`.|
|[CRect::OffsetRect](#offsetrect)|Přesune `CRect` se o zadané posuny.|
|[CRect::PtInRect](#ptinrect)|Určuje, zda zadaný bod leží v `CRect`rámci.|
|[CRect::SetRect](#setrect)|Nastaví rozměry `CRect`.|
|[CRect::SetRectEmpty](#setrectempty)|Nastaví `CRect` prázdný obdélník (všechny souřadnice se rovnají 0).|
|[CRect:: size](#size)|Vypočítá velikost `CRect`.|
|[CRect::SubtractRect](#subtractrect)|Odečte jeden obdélník od druhého.|
|[CRect::TopLeft](#topleft)|Vrátí levý horní bod `CRect`.|
|[CRect::UnionRect](#unionrect)|Nastaví `CRect` se jako sjednocení dvou obdélníků.|
|[CRect:: Width](#width)|Vypočítá šířku `CRect`.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CRect:: operator-](#operator_-)|Odečte zadané posuny od `CRect` nebo `CRect` deplochí a vrátí výslednou `CRect`hodnotu.|
|[CRect:: operator LPCRECT](#operator_lpcrect)|`CRect` Převede`LPCRECT`na.|
|[CRect:: operator LPRECT](#operator_lprect)|`CRect` Převede`LPRECT`na.|
|[CRect:: operator! =](#operator_neq)|Určuje, `CRect` zda se nerovná obdélníku.|
|[CRect:: operator&amp;](#operator_amp)|Vytvoří průnik `CRect` a obdélník a vrátí výslednou `CRect`hodnotu.|
|[CRect:: operator&amp;=](#operator_amp_eq)|Nastaví `CRect` se jako `CRect` průsečík a obdélník.|
|[CRect:: operator&#124;](#operator_or)|Vytvoří sjednocení `CRect` a obdélník a vrátí výslednou `CRect`hodnotu.|
|[CRect:: operator &#124;=](#operator_or_eq)|Nastaví `CRect` se jako `CRect` sjednocení a obdélník.|
|[CRect:: operator + – operátor](#operator_add)|Přidá dané posunutí do `CRect` nebo `CRect` neplochý a vrátí výslednou `CRect`hodnotu.|
|[CRect:: operator + =](#operator_add_eq)|Přidá zadané posuny do `CRect` nebo `CRect`neploché.|
|[CRect:: operator =](#operator_eq)|Zkopíruje rozměry obdélníku do `CRect`.|
|[CRect:: operator-=](#operator_-_eq)|Odečte zadané posuny od nebo `CRect` `CRect`z.|
|[CRect:: operator = = – operátor](#operator_eq_eq)|Určuje, `CRect` zda se rovná obdélník.|

## <a name="remarks"></a>Poznámky

`CRect`zahrnuje také členské funkce pro manipulaci s `CRect` objekty a strukturami systému Windows. `RECT`

Objekt může být předán jako parametr funkce všude, kde je `RECT` struktura, `LPCRECT`nebo `LPRECT` může být předána. `CRect`

> [!NOTE]
> Tato třída je odvozena z `tagRECT` struktury. (Název `tagRECT` je méně často používaný název `RECT` pro strukturu.) To znamená, že datové členy (`left`, `top`, `right` `bottom`a) `RECT` struktury jsou přístupné datovým členům `CRect`.

`CRect` Obsahuje proměnné členů, které definují levý horní a dolní pravý bod obdélníku.

Když zadáte `CRect`, musíte být opatrní, aby se vytvořila, aby byla normalizovaná – jinými slovy, aby byla hodnota levého souřadnice menší než vpravo a horní hranice je menší než dolní. Například levý horní okraj (10, 10) a vpravo dole od (20, 20) definuje normalizovaný obdélník, ale v levém horním rohu (20, 20) a vpravo dole od (10, 10) definuje nenormalizovaný obdélník. Pokud obdélník není normalizován, mnoho `CRect` členských funkcí může vracet nesprávné výsledky. (Další informace najdete v tématu [CRect:: NormalizeRect](#normalizerect) .) Před voláním funkce, která vyžaduje normalizované obdélníky, můžete normalizovat nenormalizované obdélníky voláním `NormalizeRect` funkce.

Buďte opatrní při manipulaci `CRect` s pomocí členských funkcí [CDC::D ptolp](../../mfc/reference/cdc-class.md#dptolp) a [CDC:: LPtoDP](../../mfc/reference/cdc-class.md#lptodp) . Je-li režim mapování kontextu zobrazení tak, že hodnota y je záporná, jako v `MM_LOENGLISH`, pak `CDC::DPtoLP` bude transformovat `CRect` tak, aby jeho horní hodnota byla větší než dolní. Funkce `CRect`, jako `Height` například `Size` a, pak vrátí záporné hodnoty pro výšku transformované a obdélník bude nenormalizovaný.

Při `CRect` použití přetížených operátorů musí být prvním operandem `CRect`a; druhým může být struktura [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` objekt.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagRECT`

`CRect`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltypes. h

##  <a name="bottomright"></a>CRect::BottomRight

Souřadnice jsou vráceny jako odkaz na objekt [CPoint](cpoint-class.md) , který je obsažen v `CRect`.

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Souřadnice pravého dolního rohu obdélníku

### <a name="remarks"></a>Poznámky

Tuto funkci můžete použít buď k získání nebo nastavení pravého dolního rohu obdélníku. Nastavte roh pomocí této funkce na levé straně operátoru přiřazení.

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

##  <a name="centerpoint"></a>CRect::CenterPoint

Vypočítá centerpointy `CRect` přidáním levé a pravé hodnoty a vydělením dvěma a přidáním horních a dolních hodnot a vydělením dvěma.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Objekt, který je `CRect`Centerpoint. `CPoint`

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

##  <a name="copyrect"></a>CRect::CopyRect

Zkopíruje obdélník do `CRect`. `lpSrcRect`

```
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>Parametry

*lpSrcRect*<br/>
Odkazuje na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` objekt, který má být zkopírován.

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

##  <a name="crect"></a>CRect::CRect

`CRect` Vytvoří objekt.

```
CRect() throw();
CRect(int l, int t, int r, int b) throw();
CRect(const RECT& srcRect) throw();
CRect(LPCRECT lpSrcRect) throw();
CRect(POINT point, SIZE size) throw();
CRect(POINT topLeft, POINT bottomRight) throw();
```

### <a name="parameters"></a>Parametry

*l*<br/>
Určuje levou pozici `CRect`.

*t*<br/>
Určuje začátek `CRect`.

*r*<br/>
Určuje správnou pozici `CRect`.

*b*<br/>
Určuje dolní část `CRect`.

*srcRect*<br/>
Odkazuje na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) s souřadnicemi pro `CRect`.

*lpSrcRect*<br/>
Odkazuje na `RECT` strukturu s souřadnicemi pro `CRect`.

*Vyberte*<br/>
Určuje počáteční bod pro vykonstrukci obdélníku. Odpovídá levému hornímu rohu.

*hodnota*<br/>
Určuje posun z levého horního rohu do pravého dolního rohu obdélníku, který má být vytvořen.

*topLeft*<br/>
Určuje pozici `CRect`v levém horním rohu.

*bottomRight*<br/>
Určuje pravou pozici `CRect`v pravém dolním rohu.

### <a name="remarks"></a>Poznámky

Pokud nejsou zadány žádné argumenty `left`, `top` `right`,, a `bottom` členy nejsou inicializovány.

[](#copyrect)Konstruktory`const RECT&` `CRect`() a(`LPCRECT`) provádějí CopyRect. `CRect` Ostatní konstruktory inicializují proměnné členů objektu přímo.

### <a name="example"></a>Příklad

```cpp
// default constructor doesn't initialize!
CRect rectUnknown;

// four-integers are left, top, right, and bottom
CRect rect(0, 0, 100, 50);
ASSERT(rect.Width() == 100);
ASSERT(rect.Height() == 50);

// Initialize from RECT stucture
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

##  <a name="deflaterect"></a>CRect::D eflateRect

`DeflateRect`rozplochý `CRect` přesunutím jeho stran směrem ke středu.

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Určuje počet jednotek pro zúžení levé a pravé strany `CRect`.

*y*<br/>
Určuje počet jednotek, které se mají uprostřed nahoru a dolů `CRect`.

*hodnota*<br/>
[Velikost](/windows/win32/api/windef/ns-windef-size) nebo [CSize](csize-class.md) , která určuje počet jednotek k zúžení `CRect`. Hodnota určuje počet jednotek pro zúžení levé a pravé strany `cy` a hodnota určuje počet jednotek, které se mají uprostřed nahoru a dolů. `cx`

*lpRect*<br/>
Odkazuje na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` určuje počet jednotek, které se mají uprostřed umístit.

*l*<br/>
Určuje počet jednotek, ve kterých se má uprostřed levá strana `CRect`.

*t*<br/>
Určuje počet jednotek, které se mají uprostřed horní `CRect`části.

*r*<br/>
Určuje počet jednotek pro zúžení pravé strany `CRect`.

*b*<br/>
Určuje počet jednotek, ve kterých se má uprostřed dolů `CRect`.

### <a name="remarks"></a>Poznámky

K tomu `DeflateRect` přidají jednotky vlevo a dolů a odečtou se jednotky od pravého a dolního okraje. Parametry `DeflateRect` jsou podepsané hodnoty; kladné hodnoty zúžené `CRect` a záporné hodnoty jsou neploché.

První dvě přetížení rozdeflate obě páry protilehlých stran `CRect` , aby celková šířka byla snížena o dvojnásobku *hodnoty* *x* (nebo `cx`) a celková výška je snížena o dvě časy (nebo `cy`). Druhá dvě přetížení uprostřed každou stranu `CRect` nezávisle na ostatních.

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

##  <a name="equalrect"></a>CRect::EqualRect

Určuje, `CRect` zda se rovná danému obdélníku.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` objekt, který obsahuje souřadnice levého horního a dolního rohu obdélníku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dva obdélníky mají stejné hodnoty Top, Left, Bottom a Right; v opačném případě 0.

> [!NOTE]
>  Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) pro normalizaci obdélníků před voláním této funkce.

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

##  <a name="height"></a>CRect:: Height

Vypočítá výšku `CRect` odečtením nejvyšší hodnoty od nejnižší hodnoty.

```
int Height() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Výška `CRect`.

### <a name="remarks"></a>Poznámky

Výsledná hodnota může být záporná.

> [!NOTE]
>  Obdélník musí být normalizován nebo tato funkce může selhat. Před voláním této funkce můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníku.

### <a name="example"></a>Příklad

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

##  <a name="inflaterect"></a>CRect::InflateRect

`InflateRect`se nerovná `CRect` přesunutím stran mimo střed.

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Určuje počet jednotek, které mají být nahuštěny na levou a pravou stranu `CRect`.

*y*<br/>
Určuje počet jednotek, které mají být vyrovny horní a dolní `CRect`části.

*hodnota*<br/>
[Velikost](/windows/win32/api/windef/ns-windef-size) nebo [CSize](csize-class.md) , která určuje počet jednotek, které mají být neploché `CRect`. Hodnota určuje počet jednotek, které mají být nahuštěny na levou a pravou stranu `cy` , a hodnota určuje počet jednotek, které mají být vyrovny horní a dolní. `cx`

*lpRect*<br/>
Odkazuje na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` , která určuje počet jednotek, které mají být pro každou stranu ploché.

*l*<br/>
Určuje počet jednotek, které mají být umístěny na levé straně `CRect`.

*t*<br/>
Určuje počet jednotek, které mají být v horní `CRect`části.

*r*<br/>
Určuje počet jednotek, které mají být nahuštěny na pravé straně `CRect`.

*b*<br/>
Určuje počet jednotek, které mají být vyrovny dolnímu `CRect`okraji.

### <a name="remarks"></a>Poznámky

To uděláte tak, `InflateRect` že odečtete jednotky od levého a horního okraje a do pravého a dolního rohu přidáte jednotky. Parametry `InflateRect` jsou podepsané hodnoty; kladné hodnoty jsou `CRect` neploché a jejich zúžené hodnoty.

První dvě přetížení rozplochí obě dvojice protilehlých stran `CRect` , aby celková šířka byla zvýšena o dvojnásobek hodnoty *x* (nebo `cx`) a celková výška je zvýšena o dvojnásobku *y* (nebo `cy`). Druhá dvě přetížení mají neplochou každou stranu `CRect` nezávisle na ostatních.

### <a name="example"></a>Příklad

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

##  <a name="intersectrect"></a>CRect::IntersectRect

`CRect` Je rovno průniku dvou existujících obdélníků.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parametry

*lpRect1*<br/>
Odkazuje na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` objekt, který obsahuje zdrojový obdélník.

*lpRect2*<br/>
Odkazuje na `RECT` strukturu nebo `CRect` objekt, který obsahuje zdrojový obdélník.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud průnik není prázdný; 0, pokud průnik je prázdný.

### <a name="remarks"></a>Poznámky

Průsečík je největší obdélník obsažený v obou stávajících obdélníkech.

> [!NOTE]
>  Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) pro normalizaci obdélníků před voláním této funkce.

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

##  <a name="isrectempty"></a>CRect::IsRectEmpty

Určuje, `CRect` zda je prázdný.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, `CRect` Pokud je prázdné; 0 `CRect` , pokud není prázdné.

### <a name="remarks"></a>Poznámky

Obdélník je prázdný, pokud je šířka nebo výška 0 nebo záporné. Se liší od `IsRectNull`, který určuje, zda jsou všechny souřadnice obdélníku nulové.

> [!NOTE]
>  Obdélník musí být normalizován nebo tato funkce může selhat. Před voláním této funkce můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníku.

### <a name="example"></a>Příklad

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

##  <a name="isrectnull"></a>CRect::IsRectNull

Určuje, zda `CRect` jsou všechny hodnoty nahoře, vlevo, dole a Right rovny 0.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, `CRect`Pokud hodnoty Top, Left, Bottom a Right jsou všechny rovny 0; jinak 0.

### <a name="remarks"></a>Poznámky

Se liší od `IsRectEmpty`, což určuje, zda je obdélník prázdný.

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

##  <a name="movetox"></a>CRect::MoveToX

Voláním této funkce přesunete obdélník na absolutní souřadnici x určenou znakem *x*.

```
void MoveToX(int x) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Absolutní souřadnice x levého horního rohu obdélníku.

### <a name="example"></a>Příklad

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

##  <a name="movetoxy"></a>CRect::MoveToXY

Voláním této funkce přesunete obdélník na absolutní souřadnice x a y.

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Absolutní souřadnice x levého horního rohu obdélníku.

*y*<br/>
Absolutní souřadnice y levého horního rohu obdélníku.

*Vyberte*<br/>
`POINT` Struktura určující absolutní levý horní roh obdélníku.

### <a name="example"></a>Příklad

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

##  <a name="movetoy"></a>CRect::MoveToY

Voláním této funkce přesunete obdélník na absolutní souřadnici y určenou funkcí *y*.

```
void MoveToY(int y) throw();
```

### <a name="parameters"></a>Parametry

*y*<br/>
Absolutní souřadnice y levého horního rohu obdélníku.

### <a name="example"></a>Příklad

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

##  <a name="normalizerect"></a>CRect::NormalizeRect

Normalizuje `CRect` tak, že výška i šířka jsou kladné.

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>Poznámky

Obdélník je normalizován na umístění čtvrtého kvadrantu, které systém Windows obvykle používá pro souřadnice. `NormalizeRect`Porovná horní a dolní hodnotu a zahodí je, pokud je horní hodnota větší než dolní. Obdobně zamění levou a pravou hodnotu, pokud je levý větší než vpravo. Tato funkce je užitečná při práci s různými režimy mapování a obrácenými obdélníky.

> [!NOTE]
> Následující `CRect` členské funkce vyžadují normalizované obdélníky, aby fungovaly správně: [Výška](#height), [Šířka](#width), [Velikost](#size), [IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [SubtractRect](#subtractrect), [operátor = =](#operator_eq_eq), [operátor! =](#operator_neq), [operátor &#124; ](#operator_or), [operátor &#124;=](#operator_or_eq), [operátor &](#operator_amp)a [operátor & =](#operator_amp_eq).

### <a name="example"></a>Příklad

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

##  <a name="offsetrect"></a>CRect::OffsetRect

Přesune `CRect` se o zadané posuny.

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Určuje velikost, která se má přesunout doleva nebo doprava. Posunutí doleva musí být záporné.

*y*<br/>
Určuje velikost, která se má přesunout nahoru nebo dolů. Aby se mohl přesunout nahoru, musí být záporný.

*Vyberte*<br/>
Obsahuje strukturu [bodu](/windows/win32/api/windef/ns-windef-point) nebo objekt [CPoint](cpoint-class.md) určující obě dimenze, které se mají přesunout.

*hodnota*<br/>
Obsahuje strukturu [velikosti](/windows/win32/api/windef/ns-windef-size) nebo objekt [CSize](csize-class.md) určující obě dimenze, které se mají přesunout.

### <a name="remarks"></a>Poznámky

Přesune `CRect`jednotky *x* podél osy x a *y* podél osy y. Parametry *x* a *y* jsou podepsané, takže `CRect` se dají přesunout doleva nebo doprava a nahoru nebo dolů.

### <a name="example"></a>Příklad

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

##  <a name="operator_lpcrect"></a>CRect:: operator LPCRECT převede `CRect` na [LPCRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Poznámky

Použijete-li tuto funkci, nepotřebujete operátor address-of **&** (). Tento operátor bude automaticky použit při předání `CRect` objektu do funkce, která `LPCRECT`očekává.

##  <a name="operator_lprect"></a>CRect:: operator LPRECT

Převede na lpRect. [](../../mfc/reference/data-types-mfc.md) `CRect`

```
operator LPRECT() throw();
```

### <a name="remarks"></a>Poznámky

Použijete-li tuto funkci, nepotřebujete operátor address-of **&** (). Tento operátor bude automaticky použit při předání `CRect` objektu do funkce, která `LPRECT`očekává.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CRect:: operator LPCRECT](#operator_lpcrect).

##  <a name="operator_eq"></a>CRect:: operator =

Přiřadí *srcRect* k `CRect`.

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Parametry

*srcRect*<br/>
Odkazuje na zdrojový obdélník. Může být [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect`.

### <a name="example"></a>Příklad

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

##  <a name="operator_eq_eq"></a>CRect:: operator = = – operátor

Určuje, `rect` zda je `CRect` rovno porovnání souřadnic jejich levého horního a dolního rohu.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
Odkazuje na zdrojový obdélník. Může být [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je rovno; v opačném případě 0.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) pro normalizaci obdélníků před voláním této funkce.

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

##  <a name="operator_neq"></a>CRect:: operator! =

Určuje, zda není *Rect* rovno `CRect` porovnáním souřadnic jejich levého horního a dolního rohu.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
Odkazuje na zdrojový obdélník. Může být [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud není rovno; v opačném případě 0.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) pro normalizaci obdélníků před voláním této funkce.

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

##  <a name="operator_add_eq"></a>CRect:: operator + =

První dvě přetížení se přesunou `CRect` podle zadaného posunu.

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
Struktura [bodu](/windows/win32/api/windef/ns-windef-point) nebo objekt [CPoint](cpoint-class.md) , který určuje počet jednotek pro přesunutí obdélníku.

*hodnota*<br/>
Struktura [velikosti](/windows/win32/api/windef/ns-windef-size) nebo objekt [CSize](csize-class.md) , který určuje počet jednotek pro přesunutí obdélníku.

*lpRect*<br/>
Odkazuje na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` objekt, který obsahuje počet jednotek, které mají být rozploché pro každou `CRect`stranu.

### <a name="remarks"></a>Poznámky

Hodnoty parametrů *x* a *y* (nebo `cx` a `cy`) jsou přidány do `CRect`.

Třetí přetížení `CRect` má za následek počet jednotek specifikovaných v každém členu parametru.

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

##  <a name="operator_-_eq"></a>CRect:: operator-=

První dvě přetížení se přesunou `CRect` podle zadaného posunu.

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
Struktura [bodu](/windows/win32/api/windef/ns-windef-point) nebo objekt [CPoint](cpoint-class.md) , který určuje počet jednotek pro přesunutí obdélníku.

*hodnota*<br/>
Struktura [velikosti](/windows/win32/api/windef/ns-windef-size) nebo objekt [CSize](csize-class.md) , který určuje počet jednotek pro přesunutí obdélníku.

*lpRect*<br/>
Odkazuje na strukturu [](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` objekt Rect, který obsahuje počet jednotek pro `CRect`zúžení jednotlivých stran.

### <a name="remarks"></a>Poznámky

Hodnoty *x* a *y* (nebo `cx` a `cy`) parametru se odečtou od `CRect`.

Třetí přetížení rozrovná `CRect` počet jednotek specifikovaných v každém členu parametru. Všimněte si, že tato přetížená funkce, jako je [DeflateRect](#deflaterect).

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

##  <a name="operator_amp_eq"></a>CRect:: operator&amp;=

Sada `CRect` je rovna `CRect` průsečíku a `rect`.

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
Obsahuje [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect`.

### <a name="remarks"></a>Poznámky

Průsečík je největší obdélník, který je obsažen v obou obdélnících.

> [!NOTE]
>  Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) pro normalizaci obdélníků před voláním této funkce.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CRect:: IntersectRect](#intersectrect).

##  <a name="operator_or_eq"></a>CRect:: operator &#124;=

Sada `CRect` je rovna `CRect` sjednocení a `rect`.

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
Obsahuje a `CRect` nebo [Rect](/windows/win32/api/windef/ns-windef-rect).

### <a name="remarks"></a>Poznámky

Sjednocení je nejmenší obdélník, který obsahuje oba zdrojové obdélníky.

> [!NOTE]
>  Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) pro normalizaci obdélníků před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

##  <a name="operator_add"></a>CRect:: operator + – operátor

První dvě přetížení vrátí `CRect` objekt, který je `CRect` roven zadaným posunům.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
Struktura [bodu](/windows/win32/api/windef/ns-windef-point) nebo objekt [CPoint](cpoint-class.md) , který určuje počet jednotek pro přesun návratové hodnoty.

*hodnota*<br/>
Struktura [velikosti](/windows/win32/api/windef/ns-windef-size) nebo objekt [CSize](csize-class.md) , který určuje počet jednotek pro přesunutí vrácené hodnoty.

*lpRect*<br/>
Odkazuje na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` objekt, který obsahuje počet jednotek pro deflaci každé strany návratové hodnoty.

### <a name="return-value"></a>Návratová hodnota

Výsledek přesunutí nebo `CRect` rozplochý podle počtu jednotek zadaných v parametru. `CRect`

### <a name="remarks"></a>Poznámky

Parametry *x* a *y* (nebo `cx` a `cy`) parametru jsou přidány do `CRect`pozice.

Třetí přetížení vrátí nový `CRect` , který je `CRect` roven hodnotě vynásobené počtem jednotek specifikovaných v každém členu parametru.

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

##  <a name="operator_-"></a>CRect:: operator-

První dvě přetížení vrátí `CRect` objekt, který je `CRect` roven zadaným posunům.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
Struktura [bodu](/windows/win32/api/windef/ns-windef-point) nebo `CPoint` objekt, který určuje počet jednotek pro přesunutí vrácené hodnoty.

*hodnota*<br/>
[Velikost](/windows/win32/api/windef/ns-windef-size) struktury nebo `CSize` objektu, který určuje počet jednotek pro přesunutí vrácené hodnoty.

*lpRect*<br/>
Odkazuje na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` objekt, který obsahuje počet jednotek pro zúžení všech stran návratové hodnoty.

### <a name="return-value"></a>Návratová hodnota

Výsledek přesunutí nebo `CRect` zúžení podle počtu jednotek zadaných v parametru. `CRect`

### <a name="remarks"></a>Poznámky

Parametry *x* a *y* (nebo `cx` a `cy`) parametru se odečtou od `CRect`pozice.

Třetí přetížení vrátí nový `CRect` , který je `CRect` roven hodnotě oddělený počtem jednotek specifikovaných v každém členu parametru. Všimněte si, že tato přetížení funguje jako [DeflateRect](#deflaterect), ne [SubtractRect](#subtractrect).

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

##  <a name="operator_amp"></a>CRect:: operator&amp;

Vrátí objekt `CRect` , který je `CRect` průsečíkem a *rect2*.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Parametry

*rect2*<br/>
Obsahuje [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect`.

### <a name="return-value"></a>Návratová hodnota

Objekt `CRect` , který je `CRect` průsečíkem a *rect2*.

### <a name="remarks"></a>Poznámky

Průsečík je největší obdélník, který je obsažen v obou obdélnících.

> [!NOTE]
>  Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) pro normalizaci obdélníků před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

##  <a name="operator_or"></a>CRect:: operator&#124;

Vrátí hodnotu `CRect` , která je sjednocením a *rect2.* `CRect`

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>Parametry

*rect2*<br/>
Obsahuje [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect`.

### <a name="return-value"></a>Návratová hodnota

`CRect` A to je sjednocení a *rect2.* `CRect`

### <a name="remarks"></a>Poznámky

Sjednocení je nejmenší obdélník, který obsahuje oba obdélníky.

> [!NOTE]
>  Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) pro normalizaci obdélníků před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="ptinrect"></a>CRect::P tInRect

Určuje, zda zadaný bod leží v `CRect`rámci.

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
Obsahuje strukturu [bodu](/windows/win32/api/windef/ns-windef-point) nebo objekt [CPoint](cpoint-class.md) .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bod leží v `CRect`; jinak 0.

### <a name="remarks"></a>Poznámky

Bod je v rámci `CRect` , pokud leží na levé nebo horní straně nebo je ve všech čtyřech stranách. Bod na pravé nebo dolní straně je mimo `CRect`.

> [!NOTE]
>  Obdélník musí být normalizován nebo tato funkce může selhat. Před voláním této funkce můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníku.

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

##  <a name="setrect"></a>CRect::SetRect

Nastaví rozměry `CRect` na zadané souřadnice.

```
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>Parametry

*x1*<br/>
Určuje souřadnici x levého horního rohu.

*Y1*<br/>
Určuje souřadnici y v levém horním rohu.

*x2*<br/>
Určuje souřadnici x pravého dolního rohu.

*y2*<br/>
Určuje souřadnici y v pravém dolním rohu.

### <a name="example"></a>Příklad

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

##  <a name="setrectempty"></a>CRect::SetRectEmpty

Vytvoří `CRect` obdélník s hodnotou null nastavením všech souřadnic na hodnotu nula.

```
void SetRectEmpty() throw();
```

### <a name="example"></a>Příklad

```cpp
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());
```

##  <a name="size"></a>CRect:: SIZE

Členové `cx` `CRect`a `cy` návratové hodnoty obsahují výšku a šířku.

```
CSize Size() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Objekt [CSize](csize-class.md) , který obsahuje velikost `CRect`.

### <a name="remarks"></a>Poznámky

Buď může být výška nebo šířka záporná.

> [!NOTE]
>  Obdélník musí být normalizován nebo tato funkce může selhat. Před voláním této funkce můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníku.

### <a name="example"></a>Příklad

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

##  <a name="subtractrect"></a>CRect::SubtractRect

Nastaví rozměry `CRect` rovnající se `lpRectSrc2` odčítání z `lpRectSrc1`.

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Parametry

*lpRectSrc1*<br/>
Odkazuje na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` objekt, ze kterého se má odčítat obdélník.

*lpRectSrc2*<br/>
Odkazuje na `RECT` strukturu nebo `CRect` objekt, který má být odečten od obdélníku, na který odkazuje parametr *lpRectSrc1* .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Odčítání je nejmenší obdélník, který obsahuje všechny body v *lpRectScr1* , které nejsou v průsečíku *lpRectScr1* a *lpRectScr2*.

Obdélník určený parametrem *lpRectSrc1* nebude změněn, pokud obdélník určený parametrem *lpRectSrc2* nebude úplně překrývat obdélník určený parametrem *lpRectSrc1* alespoň v jednom z směrů x-nebo y.

Například pokud byl *lpRectSrc1* (10, 10, 100 100) a *lpRectSrc2* (50, 50, 150 150), obdélník, na který se odkazuje pomocí *lpRectSrc1* , by se při vrácení funkce nezměnil. Pokud byl *lpRectSrc1* (10, 10, 100 100) a *lpRectSrc2* (50 150 150, 10,), ale obdélník, na který *lpRectSrc1* odkazuje, obsahuje souřadnice (10, 10, 50 100), až funkce vrátí.

`SubtractRect`není stejný jako [operátor](#operator_-) ani [operátor-=](#operator_-_eq). Žádná z těchto operátorů nikdy `SubtractRect`nevolá.

> [!NOTE]
>  Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) pro normalizaci obdélníků před voláním této funkce.

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

##  <a name="topleft"></a>CRect::TopLeft

Souřadnice jsou vráceny jako odkaz na objekt [CPoint](cpoint-class.md) , který je obsažen v `CRect`.

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Souřadnice levého horního rohu obdélníku.

### <a name="remarks"></a>Poznámky

Tuto funkci můžete použít buď k získání nebo nastavení levého horního rohu obdélníku. Nastavte roh pomocí této funkce na levé straně operátoru přiřazení.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CRect:: Centerpoint](#centerpoint).

##  <a name="unionrect"></a>CRect::UnionRect

Nastaví rozměry `CRect` rovnající se sjednocení dvou zdrojových obdélníků.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parametry

*lpRect1*<br/>
Odkazuje na [Rect](/windows/win32/api/windef/ns-windef-rect) nebo `CRect` obsahující zdrojový obdélník.

*lpRect2*<br/>
Odkazuje na `RECT` nebo `CRect` , který obsahuje zdrojový obdélník.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sjednocení není prázdné; 0, pokud je sjednocení prázdné

### <a name="remarks"></a>Poznámky

Sjednocení je nejmenší obdélník, který obsahuje oba zdrojové obdélníky.

Systém Windows ignoruje rozměry prázdného obdélníku. To znamená, že obdélník, který nemá žádnou výšku, nebo nemá žádnou šířku.

> [!NOTE]
>  Oba obdélníky musí být normalizovány nebo tato funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) pro normalizaci obdélníků před voláním této funkce.

### <a name="example"></a>Příklad

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="width"></a>CRect:: Width

Vypočítá šířku `CRect` odčítáním levé hodnoty od pravé hodnoty.

```
int Width() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Šířka `CRect`.

### <a name="remarks"></a>Poznámky

Šířka může být záporná.

> [!NOTE]
>  Obdélník musí být normalizován nebo tato funkce může selhat. Před voláním této funkce můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníku.

### <a name="example"></a>Příklad

```cpp
CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
// nWid is now 60
ASSERT(nWid == 60);
```

## <a name="see-also"></a>Viz také:

[CPoint – třída](cpoint-class.md)<br/>
[CSize – třída](csize-class.md)<br/>
[OBD](/windows/win32/api/windef/ns-windef-rect)
