---
title: CPoint – třída
ms.date: 11/04/2016
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
ms.openlocfilehash: 331b89ff118f727303e887670960ee6078b01fb1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747080"
---
# <a name="cpoint-class"></a>CPoint – třída

Podobně jako `POINT` struktura systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CPoint : public tagPOINT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPoint::CPoint](#cpoint)|Vytvoří `CPoint`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPoint::Posun](#offset)|Přidá hodnoty `x` a `y` členy `CPoint`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CPoint::operátor -](#operator_-)|Vrátí rozdíl a `CPoint` a velikost nebo negace bodu nebo rozdíl velikosti mezi dvěma body nebo posun zápornou velikostí.|
|[CPoint::operátor !=](#operator_neq)|Kontroluje nerovnost mezi dvěma body.|
|[CPoint::operátor +](#operator_add)|Vrátí součet `CPoint` a a velikost nebo `CRect` bod nebo posun o velikost.|
|[CPoint::operátor +=](#operator_add_eq)|Posune `CPoint` přidáním velikosti nebo bodu.|
|[CPoint::operátor -=](#operator_-_eq)|Posune `CPoint` odečtením velikosti nebo bodu.|
|[CPoint::operátor ==](#operator_eq_eq)|Kontroluje rovnost mezi dvěma body.|

## <a name="remarks"></a>Poznámky

Obsahuje také členské funkce `CPoint` pro manipulaci a [POINT](/windows/win32/api/windef/ns-windef-point) struktury.

Objekt `CPoint` lze použít všude tam, kde je použita `POINT` struktura. Operátory této třídy, které interagují s "size" přijmout buď [CSize](../../atl-mfc-shared/reference/csize-class.md) objekty nebo [size](/windows/win32/api/windef/ns-windef-size) struktury, protože dva jsou zaměnitelné.

> [!NOTE]
> Tato třída je odvozena od `tagPOINT` struktury. (Název `tagPOINT` je méně běžně používaný název `POINT` pro strukturu.) `POINT` To znamená, `x` že datové členy `y`struktury a , `CPoint`jsou přístupné datové členy .

> [!NOTE]
> Další informace o sdílených `CPoint`třídách nástrojů (například ) naleznete [v tématu Sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagPOINT`

`CPoint`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltypes.h

## <a name="cpointcpoint"></a><a name="cpoint"></a>CPoint::CPoint

Vytvoří `CPoint` objekt.

```
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```

### <a name="parameters"></a>Parametry

*initX*<br/>
Určuje hodnotu `x` člena společnosti `CPoint`.

*inity*<br/>
Určuje hodnotu `y` člena společnosti `CPoint`.

*initPt*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point) nebo `CPoint` která určuje hodnoty použité k `CPoint`inicializaci .

*initSize*<br/>
[SIZE](/windows/win32/api/windef/ns-windef-size) structure nebo [CSize,](../../atl-mfc-shared/reference/csize-class.md) která určuje hodnoty `CPoint`použité k inicializaci .

*dwPoint*<br/>
Nastaví `x` člen na slovo nízkého řádu *dwPoint* a `y` člen na slovo vyššího řádu *dwPoint*.

### <a name="remarks"></a>Poznámky

Pokud nejsou uvedeny `x` žádné `y` argumenty a členy jsou nastaveny na 0.

### <a name="example"></a>Příklad

```cpp
CPoint   ptTopLeft(0, 0);
// works from a POINT, too

POINT   ptHere;
ptHere.x = 35;
ptHere.y = 95;

CPoint   ptMFCHere(ptHere);

// works from a SIZE
SIZE   sHowBig;
sHowBig.cx = 300;
sHowBig.cy = 10;

CPoint ptMFCBig(sHowBig);
// or from a DWORD

DWORD   dwSize;
dwSize = MAKELONG(35, 95);

CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```

## <a name="cpointoffset"></a><a name="offset"></a>CPoint::Posun

Přidá hodnoty `x` a `y` členy `CPoint`.

```cpp
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>Parametry

*xOffset*<br/>
Určuje částku, která `x` má `CPoint`být vyrovnána členem .

*yOffset*<br/>
Určuje částku, která `y` má `CPoint`být vyrovnána členem .

*Bod*<br/>
Určuje částku [(POINT](/windows/win32/api/windef/ns-windef-point) nebo `CPoint`) `CPoint`pro odsazení .

*Velikost*<br/>
Určuje částku [(VELIKOST](/windows/win32/api/windef/ns-windef-size) nebo [Velikost CSize)](../../atl-mfc-shared/reference/csize-class.md)pro odsazení `CPoint`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

## <a name="cpointoperator-"></a><a name="operator_eq_eq"></a>CPoint::operátor ==

Kontroluje rovnost mezi dvěma body.

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Obsahuje [point](/windows/win32/api/windef/ns-windef-point) strukturu `CPoint` nebo objekt.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou body stejné; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

## <a name="cpointoperator-"></a><a name="operator_neq"></a>CPoint::operátor !=

Kontroluje nerovnost mezi dvěma body.

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Obsahuje [point](/windows/win32/api/windef/ns-windef-point) strukturu `CPoint` nebo objekt.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud body nejsou stejné; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add_eq"></a>CPoint::operátor +=

První přetížení přidá velikost `CPoint`.

```cpp
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Obsahuje [size](/windows/win32/api/windef/ns-windef-size) strukturu nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.

*Bod*<br/>
Obsahuje [point](/windows/win32/api/windef/ns-windef-point) strukturu nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objektu.

### <a name="remarks"></a>Poznámky

Druhé přetížení přidá bod `CPoint`.

V obou případech se sčítání `x` provádí `cx`přidáním (nebo ) člena pravého operandu `x` k členu `CPoint` a přidáním `y` (nebo `cy` `y` ) člena `CPoint`pravého operandu k členu .

Například přidání `CPoint(5, -7)` matné `CPoint(30, 40)` proměnné, která `CPoint(35, 33)`obsahuje, změní proměnnou na .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-_eq"></a>CPoint::operátor -=

První přetížení odečte velikost od `CPoint`.

```cpp
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Obsahuje [size](/windows/win32/api/windef/ns-windef-size) strukturu nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.

*Bod*<br/>
Obsahuje [point](/windows/win32/api/windef/ns-windef-point) strukturu nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objektu.

### <a name="remarks"></a>Poznámky

Druhé přetížení odečte bod od `CPoint`.

V obou případech se odčítání provádí `x` odečtením (nebo `cx`) člena pravého operandu `x` od člena `cy` `y` `CPoint` `CPoint` a odečtením `y` (nebo ) člena pravého operandu od člena .

Například odečteníod `CPoint(5, -7)` proměnné, která `CPoint(30, 40)` obsahuje, `CPoint(25, 47)`změní proměnnou na .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add"></a>CPoint::operátor +

Tento operátor slouží `CPoint` k `CPoint` `CSize` odsazení `CRect` o `CPoint`nebo objekt nebo odsazení o .

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Obsahuje [size](/windows/win32/api/windef/ns-windef-size) strukturu nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.

*Bod*<br/>
Obsahuje [point](/windows/win32/api/windef/ns-windef-point) strukturu nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objektu.

*lpRect*<br/>
Obsahuje ukazatel na [rect](/windows/win32/api/windef/ns-windef-rect) struktury nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

A, `CPoint` který je posunut o velikost, která `CPoint` `CRect` je posunuta bodem nebo posun bodem.

### <a name="remarks"></a>Poznámky

Například pomocí jednoho z prvních dvou přetížení `CPoint(25, -19)` k odsazení bodu bod `CPoint(15, 5)` nebo velikost `CSize(15, 5)` vrátí hodnotu `CPoint(40, -14)`.

Přidání obdélníku do bodu vrátí obdélník po `x` `y` odsazení a hodnoty zadané v bodě. Například pomocí poslední přetížení odsazení `CPoint(25, -19)` `CRect(150, 200, 350, 400)`obdélníku `CRect(125, 219, 325, 419)` bod vrátí .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-"></a>CPoint::operátor -

Pomocí jednoho z prvních dvou přetížení `CPoint` odečíst `CSize` `CPoint`nebo objekt z .

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Point [POINT](/windows/win32/api/windef/ns-windef-point) struktura nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objektu.

*Velikost*<br/>
A [SIZE](/windows/win32/api/windef/ns-windef-size) struktura nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.

*lpRect*<br/>
Ukazatel na [rect](/windows/win32/api/windef/ns-windef-rect) struktury nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

A, `CSize` který je rozdíl mezi `CPoint` dvěma body, který je kompenzován `CRect` negace velikosti, který je kompenzován `CPoint` negace bodu, nebo, který je negace bodu.

### <a name="remarks"></a>Poznámky

Třetí přetížení kompenzuje `CRect` negace . `CPoint` Nakonec použijte unární operátor k `CPoint`negovat .

Například pomocí první přetížení najít rozdíl mezi `CPoint(25, -19)` `CPoint(15, 5)` dvěma body a vrátí `CSize(10, -24)`.

Odečtením `CSize` od `CPoint` provádí stejný výpočet jako `CPoint` výše, ale `CSize` vrátí objekt, nikoli objekt. Například pomocí druhé přetížení najít rozdíl mezi `CPoint(25, -19)` bodem `CSize(15, 5)` a `CPoint(10, -24)`velikost vrátí .

Odečtením obdélníku od bodu vrátí obdélník posun `x` negativy `y` a hodnoty zadané v bodě. Například pomocí poslední přetížení odsadit `CRect(125, 200, 325, 400)` obdélník `CPoint(25, -19)` bod `CRect(100, 219, 300, 419)`vrátí .

Pomocí unárního operátoru negovat bod. Například pomocí unární operátor s `CPoint(25, -19)` `CPoint(-25, 19)`bodem vrátí .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>Viz také

[MDI vzorku knihovny MFc](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[BODOvá struktura](/windows/win32/api/windef/ns-windef-point)<br/>
[CRect – třída](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize – třída](../../atl-mfc-shared/reference/csize-class.md)
