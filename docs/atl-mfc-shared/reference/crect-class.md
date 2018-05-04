---
title: Třída CRect | Microsoft Docs
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
ms.openlocfilehash: a819cfc95588dc9225570a82b8a359d90a8f6b9f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="crect-class"></a>CRect – třída
Podobně jako Windows [Rect –](../../mfc/reference/rect-structure1.md) struktura.  
  
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
|[CRect::BottomRight](#bottomright)|Vrací vpravo dole bod `CRect`.|  
|[CRect::CenterPoint](#centerpoint)|Vrátí centerpoint z `CRect`.|  
|[CRect::CopyRect](#copyrect)|Zkopíruje dimenze zdroje obdélníku do `CRect`.|  
|[CRect::DeflateRect](#deflaterect)|Snižuje se šířka a Výška `CRect`.|  
|[CRect::EqualRect](#equalrect)|Určuje, zda `CRect` rovná dané rámeček.|  
|[CRect::Height](#height)|Vypočítá výšku `CRect`.|  
|[CRect::InflateRect](#inflaterect)|Zvyšuje šířka a Výška `CRect`.|  
|[CRect::IntersectRect](#intersectrect)|Nastaví `CRect` rovna průnik dvou tvaru.|  
|[CRect::IsRectEmpty](#isrectempty)|Určuje, zda `CRect` je prázdný. `CRect` je prázdný, pokud je šířka nebo výška mají hodnotu 0.|  
|[CRect::IsRectNull](#isrectnull)|Určuje, zda **horní**, **dolní**, **levém**, a **správné** členské proměnné jsou všechny rovna 0.|  
|[CRect::MoveToX](#movetox)|Přesune `CRect` k zadané souřadnice x.|  
|[CRect::MoveToXY](#movetoxy)|Přesune `CRect` do zadaných x a y souřadnic.|  
|[CRect::MoveToY](#movetoy)|Přesune `CRect` k zadané souřadnici y.|  
|[CRect::NormalizeRect](#normalizerect)|Standardizuje výška a šířka `CRect`.|  
|[CRect::OffsetRect](#offsetrect)|Přesune `CRect` podle zadaných odsazení.|  
|[CRect::PtInRect](#ptinrect)|Určuje, zda se zadaný bod je v rámci `CRect`.|  
|[CRect::SetRect](#setrect)|Nastaví rozměry `CRect`.|  
|[CRect::SetRectEmpty](#setrectempty)|Nastaví `CRect` na prázdný obdélník (všechny souřadnice rovno 0).|  
|[CRect::Size](#size)|Vypočítá velikost `CRect`.|  
|[CRect::SubtractRect](#subtractrect)|Odečítá od jeden rámeček z jiné.|  
|[CRect::TopLeft](#topleft)|Vrátí bod levého horního `CRect`.|  
|[CRect::UnionRect](#unionrect)|Nastaví `CRect` rovna sjednocení dvou tvaru.|  
|[CRect::Width](#width)|Vypočítá šířku `CRect`.|  
  
### <a name="public-operators"></a>Veřejné operátory    
|Název|Popis|  
|----------|-----------------|  
|[CRect::operator-](#operator_-)|Odečítá od daného posuny z `CRect` nebo snížení kapacity `CRect` a vrátí výsledný `CRect`.|  
|[Lpcrect – CRect::operator](#operator_lpcrect)|Převede `CRect` k **lpcrect –**.|  
|[CRect::operator lprect –](#operator_lprect)|Převede `CRect` k `LPRECT`.|  
|[CRect::operator! =](#operator_neq)|Určuje, zda `CRect` není roven obdélníku.|  
|[CRect::operator &amp;](#operator_amp)|Vytvoří průnik `CRect` a obdélníku a vrátí výsledný `CRect`.|  
|[CRect::operator &amp;=](#operator_amp_eq)|Nastaví `CRect` rovna průnik `CRect` a obdélníku.|  
|[CRect::operator |](#operator_or)|Vytvoří sjednocení `CRect` a obdélníku a vrátí výsledný `CRect`.|  
|[CRect::operator |=](#operator_or_eq)|Nastaví `CRect` rovna sjednocení `CRect` a obdélníku.|  
|[CRect::operator +](#operator_add)|Přidá daný posuny k `CRect` nebo zvýšení kapacity `CRect` a vrátí výsledný `CRect`.|  
|[CRect::operator +=](#operator_add_eq)|Přidá zadaný posun na `CRect` nebo zvýšení kapacity `CRect`.|  
|[CRect::operator =](#operator_eq)|Zkopíruje dimenze obdélníku do `CRect`.|  
|[CRect::operator-=](#operator_-_eq)|Odečítá od zadaných odsazení z `CRect` nebo snížení kapacity `CRect`.|  
|[CRect::operator ==](#operator_eq_eq)|Určuje, zda `CRect` rovná obdélníku.|  
  
## <a name="remarks"></a>Poznámky  
 `CRect` také obsahuje členské funkce k manipulaci s `CRect` objekty a Windows `RECT` struktury.  
  
 A `CRect` objekt můžete předat jako parametr funkce bez ohledu `RECT` struktura, **lpcrect –**, nebo `LPRECT` lze předat.  
  
> [!NOTE]
>  Tato třída je odvozený od **tagRECT** struktury. (Název **tagRECT** je název méně běžně používané `RECT` struktura.) To znamená, že datové členy (**levém**, **horní**, **správné**, a **dolní**) z `RECT` struktura jsou přístupná data Členové `CRect`.  
  
 A `CRect` obsahuje členské proměnné, které definují levém horním a pravém dolním body obdélníku.  
  
 Při zadávání `CRect`, je třeba dbát na vytvořit ji tak, aby je normalized – jinými slovy, menší než dolní je tak, aby hodnota levou souřadnici je menší než vpravo a horní. Například top levé (10,10) a dolním rohu (20,20) definuje normalizovaný obdélníku, ale top levé (20,20) a dolním rohu (10,10) definuje obdélníku zadání nenormalizovaného. Pokud rámeček není normalized, mnoho `CRect` členské funkce může vrátit nesprávné výsledky. (Viz [CRect::NormalizeRect](#normalizerect) seznam tyto funkce.) Před voláním funkce, které vyžadují normalizovaný obdélníků můžete normalizovat zadání nenormalizovaného obdélníků voláním `NormalizeRect` funkce.  
  
 Buďte opatrní při manipulaci s `CRect` s [CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp) a [CDC::LPtoDP](../../mfc/reference/cdc-class.md#lptodp) členské funkce. Pokud je režim mapování kontextu zobrazení tak, aby byla v rozsahu y záporná, jako v `MM_LOENGLISH`, pak `CDC::DPtoLP` transformuje `CRect` tak, aby jeho horní je větší než dolní. Funkce, jako **výška** a **velikost** pak vrátí záporné hodnoty pro výšku transformovaných `CRect`, a zadání nenormalizovaného rámeček.  

  
 Při použití přetížený `CRect` operátory, musí být první operand `CRect`; druhý může být buď [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo `CRect` objektu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `tagRECT`  
  
 `CRect`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atltypes.h  
  
##  <a name="bottomright"></a>  CRect::BottomRight  
 Souřadnice se vrátí jako odkaz na [CPoint](cpoint-class.md) objekt, který je součástí `CRect`.  
  
```  
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Souřadnice pravého dolního rohu obdélníku.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží k získání nebo nastavení pravém dolním rohu obdélníku. Nastavte rohu pomocí této funkce na levé straně operátoru přiřazení.  
  
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
 Vypočítá centerpoint z `CRect` přidání levé a pravé hodnoty a dělení dva týdny a přidáním hodnoty horní a dolní a dělení dvou.  
  
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
 `lpSrcRect`  
 Odkazuje na [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo `CRect` objekt, který je zkopírovat.  
  
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
 Určuje horní části `CRect`.  
  
 *r*  
 Určuje pravou pozici `CRect`.  
  
 *b*  
 Určuje dolní části `CRect`.  
  
 *srcRect*  
 Odkazuje [Rect –](../../mfc/reference/rect-structure1.md) struktura s souřadnice pro `CRect`.  
  
 `lpSrcRect`  
 Odkazuje na `RECT` struktura s souřadnice pro `CRect`.  
  
 `point`  
 Určuje počáteční bod pro rámeček k zkonstruovat. Odpovídá levého horního rohu.  
  
 `size`  
 Určuje posunutí v levém horním rohu na pravém dolním rohu obdélníku, aby zkonstruovat.  
  
 *TopLeft*  
 Určuje umístění levého horního `CRect`.  
  
 *BottomRight*  
 Určuje pozici vpravo dole `CRect`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud jsou zadány žádné argumenty, **levém**, **horní**, **správné**, a **dolní** členy nejsou inicializovány.  
  
 `CRect`(**Const Rect – &**) a `CRect`(**lpcrect –**) provést konstruktory [CopyRect](#copyrect). Další konstruktory inicializace členské proměnné objektu přímo.  
  
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
 `DeflateRect` snížení kapacity `CRect` přesunutím jeho stranách směrem k jeho středu.  
  
```  
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Určuje počet jednotek na levé straně deflate a pravé straně `CRect`.  
  
 *y*  
 Určuje počet jednotek k deflate horní a dolní část `CRect`.  
  
 `size`  
 A [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) nebo [CSize](csize-class.md) určující počet jednotek k deflate `CRect`. `cx` Hodnota určuje počet jednotek k deflate levé a pravé straně a `cy` hodnota určuje počet jednotek pro horní a dolní deflate.  
  
 `lpRect`  
 Odkazuje na [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo `CRect` určující počet jednotek na každé straně deflate.  
  
 *l*  
 Určuje počet jednotek na levé straně deflate `CRect`.  
  
 *t*  
 Určuje počet jednotek do horní části deflate `CRect`.  
  
 *r*  
 Určuje počet jednotek na pravé straně deflate `CRect`.  
  
 *b*  
 Určuje počet jednotek do dolní části deflate `CRect`.  
  
### <a name="remarks"></a>Poznámky  
 K tomu, `DeflateRect` přidá jednotky na levé straně a horní a odečítá od jednotky z vpravo a dole. Parametry `DeflateRect` jsou podepsané hodnoty; kladné hodnoty deflate `CRect` a záporné hodnoty zvýšilo ho.  
  
 První dva přetížení deflate obou dvojic opačné strany `CRect` tak, aby jeho celková šířka se snížila o dvakrát *x* (nebo `cx`) a jeho celková výška je snížila o dvakrát *y* () nebo `cy`). Další dvě přetížení deflate každé straně `CRect` nezávisle na ostatních.  
  
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
 Určuje, zda `CRect` rovná dané rámeček.  
  
```  
BOOL EqualRect(LPCRECT lpRect) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Odkazuje na [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo `CRect` objekt, který obsahuje souřadnice levém horním a pravém dolním rohu obdélníku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud dva obdélníků stejné nejvyšší, vlevo, dolní a pravé hodnoty; jinak 0.  
  
> [!NOTE]
>  Obě obdélníků budou normalizovány nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníků před voláním této funkce.  
  
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
 Vypočítá výšku `CRect` odečtením nejvyšší hodnotu než dolní.  
  
```  
int Height() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška `CRect`.  
  
### <a name="remarks"></a>Poznámky  
 Výsledná hodnota může být záporná.  
  
> [!NOTE]
>  Musí být normalizovány rámeček nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci rámeček před voláním této funkce.  
  
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
 `InflateRect` zvýšení kapacity `CRect` přesunutím jeho stranách od jeho center.  
  
```  
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Určuje počet jednotek k zvýšilo doleva a pravé straně `CRect`.  
  
 *y*  
 Určuje počet jednotek k zvýšilo horní a dolní část `CRect`.  
  
 `size`  
 A [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) nebo [CSize](csize-class.md) určující počet jednotek k zvýšilo `CRect`. `cx` Hodnota určuje počet jednotek k zvýšilo levé a pravé straně a `cy` hodnota určuje počet jednotek k zvýšilo horní a dolní.  
  
 `lpRect`  
 Odkazuje na [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo `CRect` určující počet jednotek na každé straně narůstat.  
  
 *l*  
 Určuje počet jednotek na levé straně zvýšilo `CRect`.  
  
 *t*  
 Určuje počet jednotek do horní části zvýšilo `CRect`.  
  
 *r*  
 Určuje počet jednotek na pravé straně zvýšilo `CRect`.  
  
 *b*  
 Určuje počet jednotek do dolní části zvýšilo `CRect`.  
  
### <a name="remarks"></a>Poznámky  
 K tomu, `InflateRect` odečítá od jednotky z vlevo a nahoře a přidá jednotky vpravo a dole. Parametry `InflateRect` jsou podepsané hodnoty, kladné hodnoty zvýšilo `CRect` a záporné hodnoty deflate ho.  
  
 První dva přetížení zvýšilo obou dvojic opačné strany `CRect` tak, aby jeho celková šířka je zvýšen dvakrát *x* (nebo `cx`) a jeho celková výška je zvýšen dvakrát *y* () nebo `cy`). Další dvě přetížení zvýšilo každé straně `CRect` nezávisle na ostatních.  
  
### <a name="example"></a>Příklad  
```cpp  
 CRect rect(0, 0, 300, 300);
 rect.InflateRect(50, 200);

 // rect is now (-50, -200, 350, 500)
 ASSERT(rect == CRect(-50, -200, 350, 500));  
```
  
##  <a name="intersectrect"></a>  CRect::IntersectRect  
 Díky `CRect` rovna průnik dvou existující tvaru.  
  
```  
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect1`  
 Odkazuje na [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo `CRect` objekt, který obsahuje obdélníku zdroje.  
  
 `lpRect2`  
 Odkazuje na `RECT` struktura nebo `CRect` objekt, který obsahuje obdélníku zdroje.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud průnik není prázdná. 0, pokud průnik je prázdný.  
  
### <a name="remarks"></a>Poznámky  
 Průnik je největší rámeček obsažené v obou existující obdélníky.  
  
> [!NOTE]
>  Obě obdélníků budou normalizovány nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníků před voláním této funkce.  
  
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
 Pokud nenulové hodnoty `CRect` je prázdný; 0 Pokud `CRect` není prázdná.  
  
### <a name="remarks"></a>Poznámky  
 Obdélník je prázdný, pokud je šířka nebo výška mají hodnotu 0 nebo záporné. Se liší od `IsRectNull`, která určuje, zda jsou všechny souřadnice rámeček nula.  
  
> [!NOTE]
>  Musí být normalizovány rámeček nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci rámeček před voláním této funkce.  
  
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
 Určuje, zda nahoře vlevo, dolů a pravým hodnoty `CRect` jsou na stejné úrovni na hodnotu 0.  
  
```  
BOOL IsRectNull() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `CRect`je dolů vlevo, nahoře, a pravé hodnoty jsou všechny rovná 0; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Se liší od `IsRectEmpty`, která určuje, zda rámeček je prázdný.  
  
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
 Volání této funkce pro přesun rámeček do absolutní souřadnice x určeného *x*.  
  
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
 Volání této funkce můžete přesunout k absolutní souřadnic x a y-zadaný rámeček.  
  
```  
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Absolutní souřadnice x levého horního rohu obdélníku.  
  
 *y*  
 Absolutní souřadnice y levého horního rohu obdélníku.  
  
 `point`  
 A **bodu** struktura zadání absolutní levého horního rohu obdélníku.  
  
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
 Volání této funkce pro přesun rámeček do absolutní souřadnice y určeného *y*.  
  
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
 Normalizuje `CRect` tak, aby výška a šířka jsou pozitivní.  
  
```  
void NormalizeRect() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Rámeček normalizována pro čtvrtý kvadrantu umístění, které Windows se obvykle používá pro souřadnice. `NormalizeRect` Porovná hodnoty horní a dolní a prohození je, pokud je větší než dolní horní. Podobně prohození levé a pravé hodnoty, pokud je větší než právo levé straně. Tato funkce je užitečná při plánování práce s mapování různé režimy a obdélníky obrácený.  
  
> [!NOTE]
>  Následující `CRect` členské funkce vyžadují normalizovaný obdélníků správné fungování: [výška](#height), [šířka](#width), [velikost](#size), [ IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [ SubtractRect](#subtractrect), [operátor ==](#operator_eq_eq), [operátor! =](#operator_neq), [operátor &#124; ](#operator_or), [operátor &#124;=](#operator_or_eq), [operátor &](#operator_amp), a [operátor & =](#operator_amp_eq).  
  
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
 Určuje dobu, přesunout doleva nebo doprava. Musí to být záporné přesunout vlevo.  
  
 *y*  
 Určuje dobu, chcete-li přesunout nahoru nebo dolů. Musí to být záporné přesunout nahoru.  
  
 `point`  
 Obsahuje [bodu](../../mfc/reference/point-structure1.md) struktura nebo [CPoint](cpoint-class.md) objekt zadání obou dimenzí, kterým se mají přesunout.  
  
 `size`  
 Obsahuje [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura nebo [CSize](csize-class.md) objekt zadání obou dimenzí, kterým se mají přesunout.  
  
### <a name="remarks"></a>Poznámky  
 Přesune `CRect` *x* jednotky podél osy x a *y* jednotky podél osy y. *x* a *y* parametry jsou podepsané hodnoty, takže `CRect` lze přesunout doleva nebo doprava a nahoru nebo dolů.  
  
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

  
##  <a name="operator_lpcrect"></a>  Lpcrect – převede CRect::operator `CRect` k [lpcrect –](../../mfc/reference/data-types-mfc.md).  

  
```  
operator LPCRECT() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Použijete-li tuto funkci, není nutné adresu z (**&**) operátor. Tento operátor se automaticky použije při předání `CRect` objekt, který má funkci, která očekává **lpcrect –**.  
  

##  <a name="operator_lprect"></a>  CRect::operator lprect –  
 Převede `CRect` k [lprect –](../../mfc/reference/data-types-mfc.md).  

  
```
operator LPRECT() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Použijete-li tuto funkci, není nutné adresu z (**&**) operátor. Tento operátor se automaticky použije při předání `CRect` objekt, který má funkci, která očekává `LPRECT`.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [lpcrect – CRect::operator](#operator_lpcrect).  
  
##  <a name="operator_eq"></a>  CRect::operator =  
 Přiřadí *srcRect* k `CRect`.  
  
```  
void operator=(const RECT& srcRect) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *srcRect*  
 Odkazuje na zdroj obdélníku. Může být [Rect –](../../mfc/reference/rect-structure1.md) nebo `CRect`.  
  
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
 Určuje, zda `rect` rovná `CRect` tak, že porovnáte souřadnice jejich levém horním a pravém dolním rozích.  
  
```  
BOOL operator==(const RECT& rect) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Odkazuje na zdroj obdélníku. Může být [Rect –](../../mfc/reference/rect-structure1.md) nebo `CRect`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je to stejné; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Obě obdélníků budou normalizovány nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníků před voláním této funkce.  
  
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
 Určuje, zda `rect` se nerovná `CRect` tak, že porovnáte souřadnice jejich levém horním a pravém dolním rozích.  
  
```  
BOOL operator!=(const RECT& rect) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Odkazuje na zdroj obdélníku. Může být [Rect –](../../mfc/reference/rect-structure1.md) nebo `CRect`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud není rovno; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Obě obdélníků budou normalizovány nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníků před voláním této funkce.  
  
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
 První dva přetížení přesunout `CRect` podle zadaných odsazení.  
  
```  
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 A [bodu](../../mfc/reference/point-structure1.md) struktura nebo [CPoint](cpoint-class.md) objekt, který určuje počet jednotek přesunout rámeček.  
  
 `size`  
 A [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura nebo [CSize](csize-class.md) objekt, který určuje počet jednotek přesunout rámeček.  
  
 `lpRect`  
 Odkazuje na [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo `CRect` objekt, který obsahuje počet jednotek na každé straně zvýšilo `CRect`.  
  
### <a name="remarks"></a>Poznámky  
 Parametru *x* a *y* (nebo `cx` a `cy`) hodnoty se přidají do `CRect`.  
  
 Zvýšení kapacity třetí přetížení `CRect` podle počtu jednotek zadaných v každém členovi parametru.  
  
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
 První dva přetížení přesunout `CRect` podle zadaných odsazení.  
  
```  
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 A [bodu](../../mfc/reference/point-structure1.md) struktura nebo [CPoint](cpoint-class.md) objekt, který určuje počet jednotek přesunout rámeček.  
  
 `size`  
 A [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura nebo [CSize](csize-class.md) objekt, který určuje počet jednotek přesunout rámeček.  
  
 `lpRect`  
 Odkazuje na [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo `CRect` objekt, který obsahuje počet jednotek na každé straně deflate `CRect`.  
  
### <a name="remarks"></a>Poznámky  
 Parametru *x* a *y* (nebo `cx` a `cy`) hodnoty jsou odečten od `CRect`.  
  
 Snížení kapacity třetí přetížení `CRect` podle počtu jednotek zadaných v každém členovi parametru. Všimněte si, že toto přetížení funkce jako [DeflateRect](#deflaterect).  
  
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
 Nastaví `CRect` rovna průnik `CRect` a `rect`.  
  
```  
void operator&=(const RECT& rect) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Obsahuje [Rect –](../../mfc/reference/rect-structure1.md) nebo `CRect`.  
  
### <a name="remarks"></a>Poznámky  
 Průnik je největší obdélníku, která se nachází v obou rámečků.  
  
> [!NOTE]
>  Obě obdélníků budou normalizovány nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníků před voláním této funkce.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CRect::IntersectRect](#intersectrect).  
  
##  <a name="operator_or_eq"></a>  CRect::operator &#124;=  
 Nastaví `CRect` rovna sjednocení `CRect` a `rect`.  
  
```  
void operator|=(const RECT& rect) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Obsahuje `CRect` nebo [Rect –](../../mfc/reference/rect-structure1.md).  
  
### <a name="remarks"></a>Poznámky  
 Sjednocení je nejmenší obdélníku, která obsahuje oba zdroje obdélníky.  
  
> [!NOTE]
>  Obě obdélníků budou normalizovány nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníků před voláním této funkce.  
  
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
 Vrátí první dva přetížení `CRect` objekt, který se rovná `CRect` po přidání zadaných odsazení.  
  
```  
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 A [bodu](../../mfc/reference/point-structure1.md) struktura nebo [CPoint](cpoint-class.md) objekt, který určuje počet jednotek přesunout návratovou hodnotu.  
  
 `size`  
 A [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura nebo [CSize](csize-class.md) objekt, který určuje počet jednotek přesunout návratovou hodnotu.  
  
 `lpRect`  
 Odkazuje na [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo `CRect` objekt, který obsahuje počet jednotek k zvýšilo každé straně návratovou hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `CRect` Vyplývající z přesunutí nebo nafouknutí `CRect` podle počtu jednotek zadaný v parametru.  
  
### <a name="remarks"></a>Poznámky  
 Parametru *x* a *y* (nebo `cx` a `cy`) parametry jsou přidány do `CRect`je pozice.  
  
 Vrátí novou třetí přetížení `CRect` který se rovná `CRect` zvětšený podle počtu jednotek zadaných v každém členovi parametru.  
  
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
 Vrátí první dva přetížení `CRect` objekt, který se rovná `CRect` po přidání zadaných odsazení.  
  
```  
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 A [bodu](../../mfc/reference/point-structure1.md) struktura nebo `CPoint` objekt, který určuje počet jednotek přesunout návratovou hodnotu.  
  
 `size`  
 A [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura nebo `CSize` objekt, který určuje počet jednotek přesunout návratovou hodnotu.  
  
 `lpRect`  
 Odkazuje na [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo `CRect` objekt, který obsahuje počet jednotek na každé straně návratovou hodnotu deflate.  
  
### <a name="return-value"></a>Návratová hodnota  
 `CRect` Vyplývající z přesunutí nebo deflaci `CRect` podle počtu jednotek zadaný v parametru.  
  
### <a name="remarks"></a>Poznámky  
 Parametru *x* a *y* (nebo `cx` a `cy`) jsou parametry odečten od `CRect`je pozice.  
  
 Vrátí novou třetí přetížení `CRect` který se rovná `CRect` zmenšený podle počtu jednotek zadaných v každém členovi parametru. Všimněte si, že toto přetížení funkce jako [DeflateRect](#deflaterect), nikoli [SubtractRect](#subtractrect).  
  
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
 Vrátí `CRect` tedy průnik `CRect` a *rect2*.  
  
```  
CRect operator&(const RECT& rect2) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *rect2*  
 Obsahuje [Rect –](../../mfc/reference/rect-structure1.md) nebo `CRect`.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CRect` tedy průnik `CRect` a *rect2*.  
  
### <a name="remarks"></a>Poznámky  
 Průnik je největší obdélníku, která se nachází v obou rámečků.  
  
> [!NOTE]
>  Obě obdélníků budou normalizovány nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníků před voláním této funkce.  
  
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
 Vrátí `CRect` tedy sjednocení `CRect` a *rect2*.  
  
```   
CRect operator|(const RECT& 
rect2) const throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 *rect2*  
 Obsahuje [Rect –](../../mfc/reference/rect-structure1.md) nebo `CRect`.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CRect` tedy sjednocení `CRect` a *rect2*.  
  
### <a name="remarks"></a>Poznámky  
 Sjednocení je nejmenší obdélníku, která obsahuje oba obdélníky.  
  
> [!NOTE]
>  Obě obdélníků budou normalizovány nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníků před voláním této funkce.  
  
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
 Určuje, zda se zadaný bod je v rámci `CRect`.  
  
```   
BOOL PtInRect(POINT point) const throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Obsahuje [bodu](../../mfc/reference/point-structure1.md) struktura nebo [CPoint](cpoint-class.md) objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se bod nachází v rámci `CRect`; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Bod je v rámci `CRect` Pokud je na straně levého nebo horního nebo je v rámci všechny čtyři strany. Bod na pravé nebo dolní straně je mimo `CRect`.  
  
> [!NOTE]
>  Musí být normalizovány rámeček nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci rámeček před voláním této funkce.  
  
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
 Nastaví rozměry `CRect` k zadané souřadnice.  
  
```   
void SetRect(int x1, int y1, int x2, int y2) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `x1`  
 Určuje souřadnici x levého horního rohu.  
  
 `y1`  
 Určuje souřadnici y levého horního rohu.  
  
 `x2`  
 Určuje souřadnici x v pravém dolním rohu.  
  
 `y2`  
 Určuje souřadnici y pravém dolním rohu.  
  
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
 Díky `CRect` null obdélníku nastavením všechny souřadnice na nulu.  
  
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
 `cx` a `cy` návratovou hodnotu obsahují výška a šířka `CRect`.  
  
```  
CSize Size() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CSize](csize-class.md) objekt, který obsahuje velikost `CRect`.  
  
### <a name="remarks"></a>Poznámky  
 Šířka nebo výška může být záporná.  
  
> [!NOTE]
>  Musí být normalizovány rámeček nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci rámeček před voláním této funkce.  
  
### <a name="example"></a>Příklad  
```cpp  
 CRect rect(10, 10, 50, 50);
 CSize sz = rect.Size();
 ASSERT(sz.cx == 40 && sz.cy == 40);  
```

##  <a name="subtractrect"></a>  CRect::SubtractRect  
 Díky rozměry **CRect** rovna odčítání z `lpRectSrc2` z `lpRectSrc1`.  
  
```  
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpRectSrc1`  
 Odkazuje na [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo `CRect` objekt, ze kterého se bude odečítat obdélníku.  
  
 `lpRectSrc2`  
 Odkazuje na `RECT` struktura nebo `CRect` objekt, který se bude odečítat od rámeček na kterou odkazuje `lpRectSrc1` parametr.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Operátor odečítání je nejmenší obdélníku, která obsahuje všechny body v `lpRectScr1` které nejsou v průniku `lpRectScr1` a *lpRectScr2*.  
  
 Rámeček určeného `lpRectSrc1` bude beze změny, pokud rámeček určeného `lpRectSrc2` nepřekrývá úplně rámeček určeného *lpRectSrc1* alespoň v jedné z x - nebo y pokynů.  
  
 Například pokud `lpRectSrc1` byly (10,10, 100,100) a `lpRectSrc2` byly (50,50, 150,150), rámeček na kterou odkazuje `lpRectSrc1` by beze změny, když funkce vrátila. Pokud `lpRectSrc1` byly (10,10, 100,100) a `lpRectSrc2` byly (50,10, 150,150), ale rámeček na kterou odkazuje `lpRectSrc1` by obsahovat souřadnice (10,10, 50,100) při funkce vrátila.  
  
 `SubtractRect` není stejný jako [operátor -](#operator_-) ani [operátor-=](#operator_-_eq). Ani jeden z těchto operátorů někdy volá `SubtractRect`.  
  
> [!NOTE]
>  Obě obdélníků budou normalizovány nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníků před voláním této funkce.  
  
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
 Souřadnice se vrátí jako odkaz na [CPoint](cpoint-class.md) objekt, který je součástí `CRect`.  
  
```  
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Souřadnice levého horního rohu obdélníku.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží k získání nebo nastavení levého horního rohu obdélníku. Nastavte rohu pomocí této funkce na levé straně operátoru přiřazení.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CRect::CenterPoint](#centerpoint).  
  
##  <a name="unionrect"></a>  CRect::UnionRect  
 Díky rozměry `CRect` rovna sjednocení obdélníky dva zdroje.  
  
```  
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect1`  
 Odkazuje na [Rect –](../../mfc/reference/rect-structure1.md) nebo `CRect` obsahující obdélníku zdroje.  
  
 `lpRect2`  
 Odkazuje na `RECT` nebo `CRect` obsahující obdélníku zdroje.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud sjednocení není prázdná. 0, pokud sjednocení je prázdný.  
  
### <a name="remarks"></a>Poznámky  
 Sjednocení je nejmenší obdélníku, která obsahuje oba zdroje obdélníky.  
  
 Windows ignoruje dimenze prázdný obdélníku; To znamená, který má žádné výšky nebo žádné šířka obdélníku.  
  
> [!NOTE]
>  Obě obdélníků budou normalizovány nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci obdélníků před voláním této funkce.  
  
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
 Vypočítá šířku `CRect` odečtením levé hodnoty z pravé hodnoty.  
  
```  
int Width() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka `CRect`.  
  
### <a name="remarks"></a>Poznámky  
 Šířka může být záporná.  
  
> [!NOTE]
>  Musí být normalizovány rámeček nebo této funkce může selhat. Můžete volat [NormalizeRect](#normalizerect) k normalizaci rámeček před voláním této funkce.  
  
### <a name="example"></a>Příklad  

```cpp  
   CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
   // nWid is now 60
   ASSERT(nWid == 60);   
```
## <a name="see-also"></a>Viz také  
 [CPoint – třída](cpoint-class.md)   
 [CSize – třída](csize-class.md)   
 [RECT –](../../mfc/reference/rect-structure1.md)


