---
title: Crect – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e54ef7a173dca0e261143af788e95ed3347d20d
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757175"
---
# <a name="crect-class"></a>Crect – třída

Podobně jako Windows [RECT](../../mfc/reference/rect-structure1.md) struktury.

## <a name="syntax"></a>Syntaxe

```
class CRect : public tagRECT  
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRect::CRect](#crect)|Vytvoří `CRect` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRect::BottomRight](#bottomright)|Vrátí bod vpravo dole `CRect`.|
|[CRect::CenterPoint](#centerpoint)|Vrátí centerpoint z `CRect`.|
|[CRect::CopyRect](#copyrect)|Zkopíruje rozměry zdrojového obdélníku do `CRect`.|
|[CRect::DeflateRect](#deflaterect)|Snižuje šířku a výšku `CRect`.|
|[CRect::EqualRect](#equalrect)|Určuje, zda `CRect` je rovna hodnotě dané obdélník.|
|[CRect::Height](#height)|Vypočítá výška `CRect`.|
|[CRect::InflateRect](#inflaterect)|Zvětšuje šířku a výšku `CRect`.|
|[CRect::IntersectRect](#intersectrect)|Nastaví `CRect` rovna průnik dvou obdélníků.|
|[CRect::IsRectEmpty](#isrectempty)|Určuje, zda `CRect` je prázdný. `CRect` je prázdný, pokud šířku nebo výšku je 0.|
|[CRect::IsRectNull](#isrectnull)|Určuje, zda `top`, `bottom`, `left`, a `right` členské proměnné jsou všechny rovnat 0.|
|[CRect::MoveToX](#movetox)|Přesune `CRect` k zadané souřadnice x.|
|[CRect::MoveToXY](#movetoxy)|Přesune `CRect` do zadaných x a y souřadnic.|
|[CRect::MoveToY](#movetoy)|Přesune `CRect` k zadané souřadnice na ose y.|
|[CRect::NormalizeRect](#normalizerect)|Standardizuje výšku a šířku `CRect`.|
|[CRect::OffsetRect](#offsetrect)|Přesune `CRect` podle zadaných odsazení.|
|[CRect::PtInRect](#ptinrect)|Určuje, zda se zadaný bod nachází v rámci `CRect`.|
|[CRect::SetRect](#setrect)|Nastaví rozměry `CRect`.|
|[CRect::SetRectEmpty](#setrectempty)|Nastaví `CRect` na prázdný obdélník (všechny souřadnice rovno 0).|
|[CRect::Size](#size)|Vypočítá velikost `CRect`.|
|[CRect::SubtractRect](#subtractrect)|Odečte jeden obdélník z jiného.|
|[CRect::TopLeft](#topleft)|Vrátí bod levého horního rohu `CRect`.|
|[CRect::UnionRect](#unionrect)|Nastaví `CRect` rovna sjednocení dvou obdélníků.|
|[CRect::Width](#width)|Vypočítá šířku `CRect`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CRect::operator-](#operator_-)|Odečte daný posun od `CRect` nebo vyfoukne `CRect` a vrátí výsledný `CRect`.|
|[CRect::operator lpcrect –](#operator_lpcrect)|Převede `CRect` do `LPCRECT`.|
|[CRect::operator lprect –](#operator_lprect)|Převede `CRect` do `LPRECT`.|
|[CRect::operator! =](#operator_neq)|Určuje, zda `CRect` není roven obdélníku.|
|[CRect::operator &amp;](#operator_amp)|Vytvoří průsečík `CRect` a obdélník a vrátí výsledný `CRect`.|
|[CRect::operator &amp;=](#operator_amp_eq)|Nastaví `CRect` rovno je určena průsečíkem `CRect` a obdélníku.|
|[CRect::operator |](#operator_or)|Vytvoří sjednocení `CRect` a obdélník a vrátí výsledný `CRect`.|
|[CRect::operator |=](#operator_or_eq)|Nastaví `CRect` rovna sjednocení `CRect` a obdélníku.|
|[CRect::operator +](#operator_add)|Přidá daný posuny k `CRect` nebo zvýšení kapacity `CRect` a vrátí výsledný `CRect`.|
|[CRect::operator +=](#operator_add_eq)|Přidá zadaný posun k `CRect` nebo zvýšení kapacity `CRect`.|
|[CRect::operator =](#operator_eq)|Zkopíruje dimenze obdélníku do `CRect`.|
|[CRect::operator-=](#operator_-_eq)|Odečte zadaný posun od `CRect` nebo vyfoukne `CRect`.|
|[CRect::operator ==](#operator_eq_eq)|Určuje, zda `CRect` rovná obdélníku.|

## <a name="remarks"></a>Poznámky

`CRect` zahrnuje také členské funkce pro manipulaci s `CRect` objekty a Windows `RECT` struktury.

A `CRect` objekt je možné předat jako parametr funkce bez ohledu na to `RECT` strukturu, `LPCRECT`, nebo `LPRECT` mohou být předány.

> [!NOTE]
>  Tato třída je odvozena z `tagRECT` struktury. (Název `tagRECT` je názvu nižší běžně používané pro `RECT` struktura.) To znamená, že datové členy (`left`, `top`, `right`, a `bottom`) z `RECT` struktury jsou dostupné datové členy `CRect`.

A `CRect` obsahuje členské proměnné, které definují body vlevo nahoře a pravém dolním rohu obdélníku.

Při zadávání `CRect`, musíte být opatrní při jeho vytvoření, tak, aby se normalizuje – jinými slovy, menší než dolní je tak, aby hodnota levou souřadnici je menší než vpravo a horní části. Například levém horním rohu (10,10) a pravém dolním rohu (20,20) definuje normalizované obdélník, ale horním levém rohu (20,20) a pravém dolním rohu (10,10) definuje nenormalizovaný obdélníku. Pokud obdélník není normalizovaná, mnoho `CRect` členské funkce může vrátit nesprávné výsledky. (Viz [CRect::NormalizeRect](#normalizerect) seznam těchto funkcí.) Před voláním funkce, která vyžaduje normalizované obdélníků můžete normalizovat nenormalizovaný obdélníků pomocí volání `NormalizeRect` funkce.

Buďte opatrní při manipulaci s `CRect` s [CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp) a [CDC::LPtoDP](../../mfc/reference/cdc-class.md#lptodp) členské funkce. Pokud je režim mapování kontextu zobrazení tak, aby byla záporná, stejně jako v rozsahu y `MM_LOENGLISH`, pak `CDC::DPtoLP` transformuje `CRect` tak, aby její horní části je větší než dolní části. Funkce, jako například `Height` a `Size` potom vrátí záporné hodnoty Výška transformovaná `CRect`, a nenormalizovaný obdélníku.  


Při použití přetížené `CRect` operátory, musí být první operand `CRect`; druhého může být buď [RECT](../../mfc/reference/rect-structure1.md) struktury nebo `CRect` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagRECT`

`CRect`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltypes.h

##  <a name="bottomright"></a>  CRect::BottomRight

Souřadnice jsou vrácena jako odkaz na [CPoint](cpoint-class.md) objekt, který je součástí `CRect`.

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Souřadnice pravého dolního rohu obdélníku.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k získání nebo nastavení pravého dolního rohu obdélníku. Nastavení rohu s použitím této funkce na levé straně operátoru přiřazení.

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

##  <a name="centerpoint"></a>  CRect::CenterPoint

Vypočítá centerpoint z `CRect` přidání levé a pravé hodnoty a dělení dvou a přidáním hodnoty horní a dolní a dělení dvou.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Návratová hodnota

A `CPoint` objekt, který je centerpoint z `CRect`.

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

##  <a name="copyrect"></a>  CRect::CopyRect

Kopie `lpSrcRect` obdélníku do `CRect`.

```
void CopyRect(LPCRECT lpSrcRect) throw(); 
```

### <a name="parameters"></a>Parametry

*lpSrcRect*  
Odkazuje [RECT](../../mfc/reference/rect-structure1.md) struktury nebo `CRect` objekt, který se mají zkopírovat.

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


##  <a name="crect"></a>  CRect::CRect

Vytvoří `CRect` objektu.

```
CRect() throw();
CRect(int l, int t, int r, int b) throw();
CRect(const RECT& srcRect) throw();
CRect(LPCRECT lpSrcRect) throw();
CRect(POINT point, SIZE size) throw();
CRect(POINT topLeft, POINT bottomRight) throw();  
```

### <a name="parameters"></a>Parametry

*l*  
Určuje umístění levého `CRect`.

*t*  
Určuje horní `CRect`.

*r*  
Určuje pravou pozici `CRect`.

*b*  
Určuje dolní `CRect`.

*srcRect*  
Odkazuje [RECT](../../mfc/reference/rect-structure1.md) strukturu s souřadnice pro `CRect`.

*lpSrcRect*  
Odkazuje `RECT` strukturu s souřadnice pro `CRect`.

*Bod*  
Určuje počáteční bod pro obdélník budovat. Odpovídá do levého horního rohu.

*Velikost*  
Určuje posunutí z levého horního rohu do pravého dolního rohu obdélníku, aby byly konstruovány.

*TopLeft*  
Určuje umístění levého horního rohu `CRect`.

*BottomRight*  
Určuje pozici vpravo dole `CRect`.

### <a name="remarks"></a>Poznámky

Pokud nejsou zadány žádné argumenty, `left`, `top`, `right`, a `bottom` členy nejsou inicializovány.

`CRect`(`const RECT&`) A `CRect`(`LPCRECT`) provádět konstruktory [CopyRect](#copyrect). Další konstruktory inicializovat proměnné členů objektu přímo.

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

##  <a name="deflaterect"></a>  CRect::DeflateRect

`DeflateRect` vyfoukne `CRect` přesunutím jeho stran směrem k středu.

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();  
```

### <a name="parameters"></a>Parametry

*x*  
Určuje počet jednotek deflate levé a pravé straně `CRect`.

*y*  
Určuje počet jednotek, aby se horní a dolní část deflate `CRect`.

*Velikost*  
A [velikost](https://msdn.microsoft.com/library/windows/desktop/dd145106) nebo [CSize](csize-class.md) , která určuje počet jednotek deflate `CRect`. `cx` Hodnota určuje počet jednotek deflate levé a pravé straně a `cy` hodnota určuje počet jednotek, aby se horní a dolní deflate.

*lprect –*  
Odkazuje [RECT](../../mfc/reference/rect-structure1.md) struktury nebo `CRect` , která určuje počet jednotek na každé straně deflate.

*l*  
Určuje počet jednotek na levé straně deflate `CRect`.

*t*  
Určuje počet jednotek, aby se horní deflate `CRect`.

*r*  
Určuje počet jednotek na pravé straně deflate `CRect`.

*b*  
Určuje počet jednotek deflate dolní `CRect`.

### <a name="remarks"></a>Poznámky

K tomu `DeflateRect` přidá jednotky levé straně a zároveň klauzuli top a odečte jednotky z vpravo a dole. Parametry `DeflateRect` jsou podepsané hodnoty; kladné hodnoty deflate `CRect` a záporné hodnoty rozšiřování ho.

První dvě přetížení deflate obou dvojic opačné stranách `CRect` tak, aby jeho celková šířka se sníží dvakrát *x* (nebo `cx`) a jeho celková výška se sníží dvakrát *y* () nebo `cy`). Další dvě přetížení deflate každé straně `CRect` nezávisle na ostatních.

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

##  <a name="equalrect"></a>  CRect::EqualRect

Určuje, zda `CRect` je rovna hodnotě dané obdélník.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*lprect –*  
Odkazuje [RECT](../../mfc/reference/rect-structure1.md) struktury nebo `CRect` objekt, který obsahuje souřadnice levého a pravého dolního rohu obdélníku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud mají dvou obdélníků stejné nejvyšší, vlevo, dolní a pravé hodnoty; jinak 0.

> [!NOTE]
>  Obě obdélníků musí být normalizovaná nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélníků před voláním této funkce.

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

##  <a name="height"></a>  CRect::Height

Vypočítá výška `CRect` odečtením nejvyšší hodnotu z dolní hodnotu.

```
int Height() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Výška `CRect`.

### <a name="remarks"></a>Poznámky

Výsledná hodnota může být záporné.

> [!NOTE]
>  Musí být normalizovaná obdélník nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélník před voláním této funkce.

### <a name="example"></a>Příklad

```cpp  
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

```cpp  
   CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

   // nHt is now 40
   ASSERT(nHt == 40);   
```


##  <a name="inflaterect"></a>  CRect::InflateRect

`InflateRect` zvýšení kapacity `CRect` přesunutím jeho stran od středu.

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();  
```

### <a name="parameters"></a>Parametry

*x*  
Určuje počet jednotek na rozšiřování levé a pravé straně `CRect`.

*y*  
Určuje počet jednotek, aby se zvýšilo horní a dolní část `CRect`.

*Velikost*  
A [velikost](https://msdn.microsoft.com/library/windows/desktop/dd145106) nebo [CSize](csize-class.md) , která určuje počet jednotek, aby se zvýšilo `CRect`. `cx` Hodnota určuje počet jednotek, aby se zvýšilo levé a pravé straně a `cy` hodnota určuje počet jednotek, aby se zvýšilo horní a dolní části.

*lprect –*  
Odkazuje na [RECT](../../mfc/reference/rect-structure1.md) struktury nebo `CRect` , která určuje počet jednotek, aby se zvýšilo každé straně.

*l*  
Určuje počet jednotek, aby se zvýšilo na levé straně `CRect`.

*t*  
Určuje počet jednotek, aby se zvýšilo horní `CRect`.

*r*  
Určuje počet jednotek, aby se zvýšilo pravé straně `CRect`.

*b*  
Určuje počet jednotek, aby se zvýšilo dolní `CRect`.

### <a name="remarks"></a>Poznámky

K tomu `InflateRect` odečte jednotky levé straně a zároveň klauzuli top a přidá jednotky doprava a dolů. Parametry `InflateRect` jsou podepsané hodnoty; kladné hodnoty rozšiřování `CRect` a záporné hodnoty deflate ho.

První dvě přetížení rozšiřování obou dvojic opačné stranách `CRect` tak, aby jeho celková šířka se zvýší o dvakrát *x* (nebo `cx`) a zvyšují jeho celková výška dvakrát *y* () nebo `cy`). Další dvě přetížení rozšiřování každé straně `CRect` nezávisle na ostatních.

### <a name="example"></a>Příklad

```cpp  
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));  
```

##  <a name="intersectrect"></a>  CRect::IntersectRect

Díky `CRect` rovna průnik dvou obdélníků existující.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();  
```

### <a name="parameters"></a>Parametry

*lpRect1*  
Odkazuje [RECT](../../mfc/reference/rect-structure1.md) struktury nebo `CRect` objekt, který obsahuje zdrojového obdélníku.

*lpRect2*  
Odkazuje `RECT` struktury nebo `CRect` objekt, který obsahuje zdrojového obdélníku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je určena průsečíkem není prázdná. 0, pokud je určena průsečíkem je prázdný.

### <a name="remarks"></a>Poznámky

Je určena průsečíkem je největší obdélník obsažené v obou existující obdélníků.

> [!NOTE]
>  Obě obdélníků musí být normalizovaná nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélníků před voláním této funkce.

### <a name="example"></a>Příklad

```cpp  
CRect rectOne(125, 0, 150, 200);
CRect rectTwo(0, 75, 350,  95);
CRect rectInter;

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

##  <a name="isrectempty"></a>  CRect::IsRectEmpty

Určuje, zda `CRect` je prázdný.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `CRect` je prázdný; 0 Pokud `CRect` není prázdný.

### <a name="remarks"></a>Poznámky

Obdélníku je prázdný, pokud je šířka nebo výška mají hodnotu 0 nebo záporné. Se liší od `IsRectNull`, který určuje, zda jsou všechny souřadnice obdélníku nula.

> [!NOTE]
>  Musí být normalizovaná obdélník nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélník před voláním této funkce.

### <a name="example"></a>Příklad

```cpp  
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);

```cpp  
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
   ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
   ASSERT(rectEmpty.IsRectEmpty());   
```


##  <a name="isrectnull"></a>  CRect::IsRectNull

Určuje, zda, vlevo nahoře, dole a klikněte pravým tlačítkem myši hodnoty `CRect` jsou na stejné úrovni na hodnotu 0.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `CRect`na horní, levý, dolní a pravé hodnoty jsou všechny rovná 0; jinak 0.

### <a name="remarks"></a>Poznámky

Se liší od `IsRectEmpty`, který určuje, zda obdélníku je prázdný.

### <a name="example"></a>Příklad

```cpp  
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);

```cpp  
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
   ASSERT(!rectSome.IsRectNull());
// note that null means _all_ zeros

CRect rectNotNull(0, 0, 35, 50);
ASSERT(!rectNotNull.IsRectNull());  
```

##  <a name="movetox"></a>  CRect::MoveToX

Voláním této funkce přesunout obdélník na absolutní souřadnice x určené *x*.

```
void MoveToX(int x) throw();  
```

### <a name="parameters"></a>Parametry

*x*  
Absolutní souřadnice x levého horního rohu obdélníku.

### <a name="example"></a>Příklad

```cpp  
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

```cpp  
   CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

   // rect is now (10, 0, 110, 100);
   ASSERT(rect == CRect(10, 0, 110, 100));   
```

##  <a name="movetoxy"></a>  CRect::MoveToXY

Voláním této funkce přesunout obdélník na absolutní souřadnic x a y-zadán.

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();  
```

### <a name="parameters"></a>Parametry

*x*  
Absolutní souřadnice x levého horního rohu obdélníku.

*y*  
Absolutní souřadnice y levého horního rohu obdélníku.

*Bod*  
A `POINT` struktura určení absolutní levého horního rohu obdélníku.

### <a name="example"></a>Příklad

```cpp  
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);

```cpp  
   CRect rect(0, 0, 100, 100);
   rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
   ASSERT(rect == CRect(10, 10, 110, 110));   
```


##  <a name="movetoy"></a>  CRect::MoveToY

Voláním této funkce přesunout obdélník na absolutní souřadnice na ose y určené *y*.

```
void MoveToY(int y) throw();  
```

### <a name="parameters"></a>Parametry

*y*  
Absolutní souřadnice y levého horního rohu obdélníku.

### <a name="example"></a>Příklad

```cpp  
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);

```cpp  
   CRect rect(0, 0, 100, 100);
   rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
   ASSERT(rect == CRect(0, 10, 100, 110));   
```


##  <a name="normalizerect"></a>  CRect::NormalizeRect

Normalizuje `CRect` tak, aby byly kladné výšku a šířku.

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>Poznámky

Obdélníku je normalizovány pro čtvrté kvadrantu umístění, které Windows se obvykle používá pro souřadnice. `NormalizeRect` Porovnává hodnoty horní a dolní a zamění je, pokud je větší než dolní horní části. Podobně Zamění levé a pravé hodnoty, pokud je větší než vpravo levé straně. Tato funkce je užitečná při práci s režimy jinému mapování a obrácený obdélníků.

> [!NOTE]
>  Následující `CRect` členské funkce vyžadují normalizované obdélníky správné fungování: [výška](#height), [šířka](#width), [velikost](#size), [ IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [ SubtractRect](#subtractrect), [operátor ==](#operator_eq_eq), [operátor! =](#operator_neq), [operátor &#124; ](#operator_or), [operátor &#124;=](#operator_or_eq), [operátor &](#operator_amp), a [operátor & =](#operator_amp_eq).

### <a name="example"></a>Příklad

```cpp  
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);

```cpp  
   CRect rect1(110, 100, 250, 310);
   CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
   rect2.NormalizeRect();
ASSERT(rect1 == rect2);  
```

##  <a name="offsetrect"></a>  CRect::OffsetRect

Přesune `CRect` podle zadaných odsazení.

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();  
```

### <a name="parameters"></a>Parametry

*x*  
Určuje dobu, chcete-li posunout vlevo nebo vpravo. Musí být záporná hodnota, při doleva.

*y*  
Určuje dobu, chcete-li přesunout nahoru nebo dolů. Musí být záporná hodnota, při přesunutí nahoru.

*Bod*  
Obsahuje [bodu](../../mfc/reference/point-structure1.md) struktury nebo [CPoint](cpoint-class.md) určující oba rozměry, podle kterého se má přesunout.

*Velikost*  
Obsahuje [velikost](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktury nebo [CSize](csize-class.md) určující oba rozměry, podle kterého se má přesunout.

### <a name="remarks"></a>Poznámky

Přesune `CRect` *x* jednotky podél osy x a *y* jednotky podél osy y. *x* a *y* parametry jsou hodnoty se znaménkem, takže `CRect` může přesunou doleva nebo doprava a nahoru nebo dolů.

### <a name="example"></a>Příklad

```cpp  
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

```cpp  
   CRect rect(0, 0, 35, 35);
   rect.OffsetRect(230, 230);

   // rect is now (230, 230, 265, 265)
   ASSERT(rect == CRect(230, 230, 265, 265));   
```


##  <a name="operator_lpcrect"></a>  CRect::operator lpcrect – převede `CRect` do [lpcrect –](../../mfc/reference/data-types-mfc.md).  


```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Poznámky

Když tuto funkci použít, nepotřebujete adresy (**&**) – operátor. Tento operátor se automaticky použije při předání `CRect` objekt funkce, která očekává, že `LPCRECT`.

##  <a name="operator_lprect"></a>  CRect::operator lprect –

Převede `CRect` do [lprect –](../../mfc/reference/data-types-mfc.md).  


```
operator LPRECT() throw();
```

### <a name="remarks"></a>Poznámky

Když tuto funkci použít, nepotřebujete adresy (**&**) – operátor. Tento operátor se automaticky použije při předání `CRect` objekt funkce, která očekává, že `LPRECT`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [lpcrect – CRect::operator](#operator_lpcrect).

##  <a name="operator_eq"></a>  CRect::operator =

Přiřadí *srcRect* k `CRect`.

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Parametry

*srcRect*  
Odkazuje na zdrojového obdélníku. Může být [RECT](../../mfc/reference/rect-structure1.md) nebo `CRect`.

### <a name="example"></a>Příklad

```cpp  
CRect rect(0, 0, 127, 168);
CRect rect2;

```cpp  
   CRect rect(0, 0, 127, 168);
   CRect rect2;

   rect2 = rect;
   ASSERT(rect2 == CRect(0, 0, 127, 168));   
```


##  <a name="operator_eq_eq"></a>  CRect::operator ==

Určuje, zda `rect` rovná `CRect` porovnáním souřadnice jejich pravém a levém horním rohu.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parametry

*Rect*  
Odkazuje na zdrojového obdélníku. Může být [RECT](../../mfc/reference/rect-structure1.md) nebo `CRect`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud shodné; jinak 0.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Obě obdélníků musí být normalizovaná nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélníků před voláním této funkce.

### <a name="example"></a>Příklad

```cpp  
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999,  6,  3);

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


##  <a name="operator_neq"></a>  CRect::operator! =

Určuje, zda *rect* není roven `CRect` porovnáním souřadnice jejich pravém a levém horním rohu.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parametry

*Rect*  
Odkazuje na zdrojového obdélníku. Může být [RECT](../../mfc/reference/rect-structure1.md) nebo `CRect`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud není rovno; jinak 0.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Obě obdélníků musí být normalizovaná nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélníků před voláním této funkce.

### <a name="example"></a>Příklad

```cpp  
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999,  6,  3);

```cpp  
   CRect rect1(35, 150, 10, 25);
   CRect rect2(35, 150, 10, 25);
   CRect rect3(98, 999, 6, 3);
ASSERT(rect1 != rect3);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect3 != test);  
```

##  <a name="operator_add_eq"></a>  CRect::operator +=

První dvě přetížení přesunout `CRect` podle zadaných odsazení.

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parametry

*Bod*  
A [bodu](../../mfc/reference/point-structure1.md) struktury nebo [CPoint](cpoint-class.md) objekt, který určuje počet jednotek přesunout obdélník.

*Velikost*  
A [velikost](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktury nebo [CSize](csize-class.md) objekt, který určuje počet jednotek přesunout obdélník.

*lprect –*  
Odkazuje na [RECT](../../mfc/reference/rect-structure1.md) struktury nebo `CRect` objekt, který obsahuje počet jednotek na každé straně rozšiřování `CRect`.

### <a name="remarks"></a>Poznámky

Parametr *x* a *y* (nebo `cx` a `cy`) přidání hodnot do `CRect`.

Tento třetí přetížení `CRect` podle počtu jednotek zadaný v parametru každého člena.

### <a name="example"></a>Příklad

```cpp  
CRect rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect rect2(135, 300, 235, 400);

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2(135, 300, 235, 400);

   rect1 += pt;
   ASSERT(rect1 == rect2);   
```

##  <a name="operator_-_eq"></a>  CRect::operator-=

První dvě přetížení přesunout `CRect` podle zadaných odsazení.

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parametry

*Bod*  
A [bodu](../../mfc/reference/point-structure1.md) struktury nebo [CPoint](cpoint-class.md) objekt, který určuje počet jednotek přesunout obdélník.

*Velikost*  
A [velikost](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktury nebo [CSize](csize-class.md) objekt, který určuje počet jednotek přesunout obdélník.

*lprect –*  
Odkazuje [RECT](../../mfc/reference/rect-structure1.md) struktury nebo `CRect` objekt, který obsahuje počet jednotek na každé straně deflate `CRect`.

### <a name="remarks"></a>Poznámky

Parametr *x* a *y* (nebo `cx` a `cy`) jsou hodnoty odečtena od `CRect`.

Třetí přetížení vyfoukne `CRect` podle počtu jednotek zadaný v parametru každého člena. Všimněte si, že toto přetížení funkce jako [DeflateRect](#deflaterect).

### <a name="example"></a>Příklad

```cpp  
CRect rect1(100, 235, 200, 335);
CPoint pt(35, 65);
rect1 -= pt;

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);

   rect1 -= pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect1 == rectResult);   
```

##  <a name="operator_amp_eq"></a>  CRect::operator &amp;=

Nastaví `CRect` rovno je určena průsečíkem `CRect` a `rect`.

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parametry

*Rect*  
Obsahuje [RECT](../../mfc/reference/rect-structure1.md) nebo `CRect`.

### <a name="remarks"></a>Poznámky

Je určena průsečíkem je největší obdélník, který je obsažen v obou obdélníků.

> [!NOTE]
>  Obě obdélníků musí být normalizovaná nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélníků před voláním této funkce.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CRect::IntersectRect](#intersectrect).

##  <a name="operator_or_eq"></a>  CRect::operator &#124;=

Nastaví `CRect` rovna sjednocení `CRect` a `rect`.

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parametry

*Rect*  
Obsahuje `CRect` nebo [RECT](../../mfc/reference/rect-structure1.md).

### <a name="remarks"></a>Poznámky

Sjednocení je nejmenší obdélník, který obsahuje oba zdroje obdélníků.

> [!NOTE]
>  Obě obdélníků musí být normalizovaná nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélníků před voláním této funkce.

### <a name="example"></a>Příklad

```cpp  
CRect rect1(100,   0, 200, 300);
CRect rect2( 0, 100, 300, 200);
rect1 |= rect2;

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);

   rect1 |= rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect1);   
```


##  <a name="operator_add"></a>  CRect::operator +

Vrátí první dvě přetížení `CRect` objekt, který je roven `CRect` vytiskne podle zadaných odsazení.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Parametry

*Bod*  
A [bodu](../../mfc/reference/point-structure1.md) struktury nebo [CPoint](cpoint-class.md) objekt, který určuje počet jednotek pro přesun návratovou hodnotu.

*Velikost*  
A [velikost](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktury nebo [CSize](csize-class.md) objekt, který určuje počet jednotek pro přesun návratovou hodnotu.

*lprect –*  
Odkazuje na [RECT](../../mfc/reference/rect-structure1.md) struktury nebo `CRect` objekt, který obsahuje počet jednotek, aby se zvýšilo každé straně návratovou hodnotu.

### <a name="return-value"></a>Návratová hodnota

`CRect` Vyplývající z přesunutí nebo nafouknutí `CRect` podle počtu jednotek zadaný v parametru.

### <a name="remarks"></a>Poznámky

Parametr *x* a *y* (nebo `cx` a `cy`) parametry jsou přidány do `CRect`je umístit.

Vrátí nový třetí přetížení `CRect` , který je roven `CRect` zvětšený podle počtu jednotek zadaný v parametru každého člena.

### <a name="example"></a>Příklad

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 + pt;
   CRect   rectResult(135, 300, 235, 400);
   ASSERT(rectResult == rect2);   
```


##  <a name="operator_-"></a>  CRect::operator-

Vrátí první dvě přetížení `CRect` objekt, který je roven `CRect` vytiskne podle zadaných odsazení.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*Bod*  
A [bodu](../../mfc/reference/point-structure1.md) struktury nebo `CPoint` objekt, který určuje počet jednotek pro přesun návratovou hodnotu.

*Velikost*  
A [velikost](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktury nebo `CSize` objekt, který určuje počet jednotek pro přesun návratovou hodnotu.

*lprect –*  
Odkazuje na [RECT](../../mfc/reference/rect-structure1.md) struktury nebo `CRect` objekt, který obsahuje počet jednotek na každé straně návratová hodnota deflate.

### <a name="return-value"></a>Návratová hodnota

`CRect` Vyplývající z přesunutí nebo deflaci `CRect` podle počtu jednotek zadaný v parametru.

### <a name="remarks"></a>Poznámky

Parametr *x* a *y* (nebo `cx` a `cy`) jsou parametry odečtena od `CRect`je umístit.

Vrátí nový třetí přetížení `CRect` , který je roven `CRect` zmenšený podle počtu jednotek zadaný v parametru každého člena. Všimněte si, že toto přetížení funkce jako [DeflateRect](#deflaterect), nikoli [SubtractRect](#subtractrect).

### <a name="example"></a>Příklad

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 - pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect2 == rectResult);   
```


##  <a name="operator_amp"></a>  CRect::operator &amp;

Vrátí `CRect` , který je průsečík `CRect` a *rect2*.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Parametry

*rect2*  
Obsahuje [RECT](../../mfc/reference/rect-structure1.md) nebo `CRect`.

### <a name="return-value"></a>Návratová hodnota

A `CRect` , který je průsečík `CRect` a *rect2*.

### <a name="remarks"></a>Poznámky

Je určena průsečíkem je největší obdélník, který je obsažen v obou obdélníků.

> [!NOTE]
>  Obě obdélníků musí být normalizovaná nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélníků před voláním této funkce.

### <a name="example"></a>Příklad

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 & rect2;
   CRect   rectResult(100, 100, 200, 200);
   ASSERT(rectResult == rect3);   
```


##  <a name="operator_or"></a>  CRect::operator&#124;

Vrátí `CRect` , který je sjednocení `CRect` a *rect2*.

``` 
CRect operator|(const RECT& 
rect2) const throw(); 
```

### <a name="parameters"></a>Parametry

*rect2*  
Obsahuje [RECT](../../mfc/reference/rect-structure1.md) nebo `CRect`.

### <a name="return-value"></a>Návratová hodnota

A `CRect` , který je sjednocení `CRect` a *rect2*.

### <a name="remarks"></a>Poznámky

Sjednocení je nejmenší obdélník, který obsahuje oba obdélníků.

> [!NOTE]
>  Obě obdélníků musí být normalizovaná nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélníků před voláním této funkce.

### <a name="example"></a>Příklad

```cpp  
CRect rect1(100,   0, 200, 300);
CRect rect2( 0, 100, 300, 200);
CRect rect3;

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 | rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);   
```


##  <a name="ptinrect"></a>  CRect::PtInRect

Určuje, zda se zadaný bod nachází v rámci `CRect`.

``` 
BOOL PtInRect(POINT point) const throw(); 
```

### <a name="parameters"></a>Parametry

*Bod*  
Obsahuje [bodu](../../mfc/reference/point-structure1.md) struktury nebo [CPoint](cpoint-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bod nachází v rámci `CRect`; jinak 0.

### <a name="remarks"></a>Poznámky

Bod je v rámci `CRect` Pokud leží na straně levého nebo horního nebo je v rámci všechny čtyři strany. Bod na pravé nebo dolní straně je mimo `CRect`.

> [!NOTE]
>  Musí být normalizovaná obdélník nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélník před voláním této funkce.

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

##  <a name="setrect"></a>  CRect::SetRect

Nastaví rozměry `CRect` na zadaných souřadnicích.

``` 
void SetRect(int x1, int y1, int x2, int y2) throw(); 
```

### <a name="parameters"></a>Parametry

*x1*  
Určuje souřadnice x levého horního rohu.

*Y1*  
Určuje souřadnici y levého horního rohu.

*x2*  
Určuje souřadnici x v pravém dolním rohu.

*y2*  
Určuje souřadnici y pravého dolního rohu.

### <a name="example"></a>Příklad

```cpp  
CRect rect;
rect.SetRect(256, 256, 512, 512);

```cpp  
   CRect rect;
   rect.SetRect(256, 256, 512, 512);
   ASSERT(rect == CRect(256, 256, 512, 512));   
```


##  <a name="setrectempty"></a>  CRect::SetRectEmpty

Díky `CRect` obdélníkem tak, že nastavíte všechny souřadnice na nulu.

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

##  <a name="size"></a>  CRect::SIZE

`cx` a `cy` návratová hodnota obsahují výšku a šířku `CRect`.

```
CSize Size() const throw();
```

### <a name="return-value"></a>Návratová hodnota

A [CSize](csize-class.md) objekt, který obsahuje velikost `CRect`.

### <a name="remarks"></a>Poznámky

Šířka nebo výška může být záporné.

> [!NOTE]
>  Musí být normalizovaná obdélník nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélník před voláním této funkce.

### <a name="example"></a>Příklad

```cpp  
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);  
```

##  <a name="subtractrect"></a>  CRect::SubtractRect

Díky rozměry `CRect` rovna odečtení `lpRectSrc2` z `lpRectSrc1`.

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Parametry

*lpRectSrc1*  
Odkazuje na [RECT](../../mfc/reference/rect-structure1.md) struktury nebo `CRect` objektu, ze kterého se bude odečítat obdélníku.

*lpRectSrc2*  
Odkazuje na `RECT` struktury nebo `CRect` objekt, který má být odečtena od obdélník na které odkazují *lpRectSrc1* parametru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Odčítání je nejmenší obdélník, který obsahuje všechny body v *lpRectScr1* , které nejsou v průsečíku *lpRectScr1* a *lpRectScr2*.

Obdélník určené *lpRectSrc1* bude beze změny, pokud obdélník určené *lpRectSrc2* nepřekrývá zcela obdélník určené *lpRectSrc1*alespoň v jedné z x - nebo y pokynů.

Například pokud *lpRectSrc1* byly (10,10, 100,100) a *lpRectSrc2* byly (50,50, 150,150), obdélník odkazované *lpRectSrc1* by být beze změn při Funkce vrátila. Pokud *lpRectSrc1* byly (10,10, 100,100) a *lpRectSrc2* byly (50,10, 150,150), ale obdélník odkazované *lpRectSrc1* by obsahovat souřadnice (10,10, 50,100) po vrácení funkce.

`SubtractRect` není stejný jako [operátor -](#operator_-) ani [operator-=](#operator_-_eq). Ani jeden z těchto operátorů někdy volá `SubtractRect`.

> [!NOTE]
>  Obě obdélníků musí být normalizovaná nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélníků před voláním této funkce.

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

##  <a name="topleft"></a>  CRect::TopLeft

Souřadnice jsou vrácena jako odkaz na [CPoint](cpoint-class.md) objekt, který je součástí `CRect`.

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw(); 
```

### <a name="return-value"></a>Návratová hodnota

Souřadnice levého horního rohu obdélníku.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k získání nebo nastavení levého horního rohu obdélníku. Nastavení rohu s použitím této funkce na levé straně operátoru přiřazení.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CRect::CenterPoint](#centerpoint).

##  <a name="unionrect"></a>  CRect::UnionRect

Díky rozměry `CRect` rovna sjednocení dva zdroje obdélníků.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parametry

*lpRect1*  
Odkazuje [RECT](../../mfc/reference/rect-structure1.md) nebo `CRect` , který obsahuje zdrojového obdélníku.

*lpRect2*  
Odkazuje `RECT` nebo `CRect` , který obsahuje zdrojového obdélníku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sjednocení není prázdná. 0, pokud sjednocení je prázdný.

### <a name="remarks"></a>Poznámky

Sjednocení je nejmenší obdélník, který obsahuje oba zdroje obdélníků.

Windows ignoruje dimenze prázdného obdélník; To znamená, který nemá žádnou výšku nebo šířku obdélníku.

> [!NOTE]
>  Obě obdélníků musí být normalizovaná nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélníků před voláním této funkce.

### <a name="example"></a>Příklad

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3.UnionRect(&rect1, &rect2);
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);   
```

##  <a name="width"></a>  CRect::Width

Vypočítá šířku `CRect` tak, že se levé hodnoty z správné hodnoty.

```
int Width() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Šířka `CRect`.

### <a name="remarks"></a>Poznámky

Šířka může být záporné.

> [!NOTE]
>  Musí být normalizovaná obdélník nebo může dojít k selhání této funkce. Můžete volat [NormalizeRect](#normalizerect) normalizace obdélník před voláním této funkce.

### <a name="example"></a>Příklad  

```cpp  
   CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
   // nWid is now 60
   ASSERT(nWid == 60);   
```
## <a name="see-also"></a>Viz také

[Cpoint – třída](cpoint-class.md)   
[Csize – třída](csize-class.md)   
[RECT](../../mfc/reference/rect-structure1.md)

