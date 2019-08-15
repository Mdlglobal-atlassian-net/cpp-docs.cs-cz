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
ms.openlocfilehash: b7c13ef8b9656c5c2fa6a90fefca0d9babbe1c84
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491228"
---
# <a name="cpoint-class"></a>CPoint – třída

Podobný struktuře Windows `POINT` .

## <a name="syntax"></a>Syntaxe

```
class CPoint : public tagPOINT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CPoint::CPoint](#cpoint)|`CPoint`Vytvoří.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CPoint:: offset](#offset)|Přidá hodnoty do `x` členů `y` `CPoint`a.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CPoint:: operator-](#operator_-)|Vrátí rozdíl `CPoint` velikosti a velikosti nebo negaci bodu nebo rozdíl velikosti mezi dvěma body nebo posunutím se zápornou velikostí.|
|[CPoint:: operator! =](#operator_neq)|Kontroluje nerovnost mezi dvěma body.|
|[CPoint:: operator + – operátor](#operator_add)|Vrátí součet `CPoint` a velikost nebo bod `CRect` nebo posun o velikost.|
|[CPoint:: operator + =](#operator_add_eq)|`CPoint` Posuny přidáním velikosti nebo bodu.|
|[CPoint:: operator-=](#operator_-_eq)|`CPoint` Posuny odečtou velikost nebo bod.|
|[CPoint:: operator = = – operátor](#operator_eq_eq)|Kontroluje rovnost mezi dvěma body.|

## <a name="remarks"></a>Poznámky

Obsahuje také členské funkce pro manipulaci `CPoint` s strukturami a [bodovými](/windows/win32/api/windef/ns-windef-point) strukturami.

Objekt lze použít `POINT` všude, kde je použita struktura. `CPoint` Operátory této třídy, které komunikují s "velikostí", přijímají buď objekty [CSize](../../atl-mfc-shared/reference/csize-class.md) , nebo struktury [velikosti](/windows/win32/api/windef/ns-windef-size) , protože tyto dvě jsou zaměnitelné.

> [!NOTE]
>  Tato třída je odvozena z `tagPOINT` struktury. (Název `tagPOINT` je méně často používaný název `POINT` struktury.) To znamená `POINT` , že datové členy `x` struktury a `y`jsou přístupné datové členy `CPoint`.

> [!NOTE]
>  Další informace o třídách sdílených nástrojů (například `CPoint`) naleznete v tématu [Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagPOINT`

`CPoint`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltypes. h

##  <a name="cpoint"></a>  CPoint::CPoint

`CPoint` Vytvoří objekt.

```
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```

### <a name="parameters"></a>Parametry

*initX*<br/>
Určuje hodnotu `x` `CPoint`člena.

*Inicializace*<br/>
Určuje hodnotu `y` `CPoint`člena.

*initPt*<br/>
Struktura [bodu](/windows/win32/api/windef/ns-windef-point) nebo `CPoint` , která určuje hodnoty používané k inicializaci `CPoint`.

*initSize*<br/>
[Velikost](/windows/win32/api/windef/ns-windef-size) struktury nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) , která určuje hodnoty používané k inicializaci `CPoint`.

*dwPoint*<br/>
Nastaví člena na *dwPoint slovo* s nižším pořadím a člennaslovodwPointsvyššímpořadím`y`. `x`

### <a name="remarks"></a>Poznámky

Pokud nejsou zadány `x` žádné argumenty a `y` členy jsou nastaveny na hodnotu 0.

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

##  <a name="offset"></a>CPoint:: offset

Přidá hodnoty do `x` členů `y` `CPoint`a.

```
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>Parametry

*xOffset*<br/>
Určuje velikost, která má být `x` posunuta členovi `CPoint`.

*yOffset*<br/>
Určuje velikost, která má být `y` posunuta členovi `CPoint`.

*Vyberte*<br/>
Určuje velikost ( [Point](/windows/win32/api/windef/ns-windef-point) nebo `CPoint` `CPoint`), která má být odsazena.

*hodnota*<br/>
Určuje množství ( [Velikost](/windows/win32/api/windef/ns-windef-size) nebo [CSize](../../atl-mfc-shared/reference/csize-class.md)), `CPoint`které má být posunuto.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

##  <a name="operator_eq_eq"></a>CPoint:: operator = = – operátor

Kontroluje rovnost mezi dvěma body.

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
Obsahuje strukturu [bodu](/windows/win32/api/windef/ns-windef-point) nebo `CPoint` objekt.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou body stejné; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

##  <a name="operator_neq"></a>CPoint:: operator! =

Kontroluje nerovnost mezi dvěma body.

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
Obsahuje strukturu [bodu](/windows/win32/api/windef/ns-windef-point) nebo `CPoint` objekt.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud body nejsou stejné; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

##  <a name="operator_add_eq"></a>CPoint:: operator + =

První přetížení přidá velikost k `CPoint`.

```
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Obsahuje strukturu [velikosti](/windows/win32/api/windef/ns-windef-size) nebo objekt [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*Vyberte*<br/>
Obsahuje strukturu [bodu](/windows/win32/api/windef/ns-windef-point) nebo objekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

### <a name="remarks"></a>Poznámky

Druhé přetížení přidá bod do `CPoint`.

V obou případech je `x` přidání členem (nebo `cx`) operandu pravého operandu `CPoint` do `x` člena a přidání `y` člena (nebo `cy`) operandu na pravé straně k `y` člen .`CPoint`

Například přidání `CPoint(5, -7)` do proměnné, která obsahuje `CPoint(30, 40)` změnu proměnné na `CPoint(35, 33)`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

##  <a name="operator_-_eq"></a>CPoint:: operator-=

První přetížení odečte velikost od `CPoint`.

```
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Obsahuje strukturu [velikosti](/windows/win32/api/windef/ns-windef-size) nebo objekt [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*Vyberte*<br/>
Obsahuje strukturu [bodu](/windows/win32/api/windef/ns-windef-point) nebo objekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

### <a name="remarks"></a>Poznámky

Druhé přetížení odečte bod od `CPoint`.

V obou případech je odečítání provedeno `x` odečtením člena (nebo `cx`) operandu na pravé straně `CPoint` od `x` `y` členu a odečtením členu (nebo `cy`) na pravé straně. operand od `y` členu `CPoint`.

Například odečtení `CPoint(5, -7)` z proměnné, která obsahuje `CPoint(30, 40)` změnu proměnné na `CPoint(25, 47)`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

##  <a name="operator_add"></a>CPoint:: operator + – operátor

Tento operátor použijte k posunu `CPoint` `CSize` `CPoint` objektunebo`CRect` , nebo k posunutí a o. `CPoint`

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Obsahuje strukturu [velikosti](/windows/win32/api/windef/ns-windef-size) nebo objekt [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*Vyberte*<br/>
Obsahuje strukturu [bodu](/windows/win32/api/windef/ns-windef-point) nebo objekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

*lpRect*<br/>
Obsahuje ukazatel na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) .

### <a name="return-value"></a>Návratová hodnota

Posunutí podle velikosti `CPoint` , posunutí podle bodu nebo `CRect` posunutí bodem. `CPoint`

### <a name="remarks"></a>Poznámky

Například použití jednoho z prvních dvou přetížení pro `CPoint(25, -19)` posunutí bodu podle bodu `CPoint(15, 5)` nebo velikosti `CSize(15, 5)` vrátí hodnotu `CPoint(40, -14)`.

Přidání obdélníku k bodu vrátí obdélník po posunu o `x` hodnoty a `y` zadané v bodě. Například použití posledního přetížení k posunu obdélníku `CRect(125, 219, 325, 419)` `CPoint(25, -19)` o vrácení `CRect(150, 200, 350, 400)`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

##  <a name="operator_-"></a>CPoint:: operator-

Použijte jedno z prvních dvou přetížení pro odečítání `CPoint` objektu nebo `CSize` z `CPoint`.

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
Struktura [bodu](/windows/win32/api/windef/ns-windef-point) nebo objekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

*hodnota*<br/>
Struktura [velikosti](/windows/win32/api/windef/ns-windef-size) nebo objekt [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*lpRect*<br/>
Ukazatel na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) .

### <a name="return-value"></a>Návratová hodnota

Jedná `CSize` se o rozdíl mezi dvěma body `CPoint` , který je odsazen o negaci velikosti, `CRect` která je posunuta `CPoint` negací bodu nebo operátorem, který je negací bodu.

### <a name="remarks"></a>Poznámky

Třetí přetížení posune `CRect` o negaci `CPoint`operátoru. Nakonec použijte unární operátor na negaci `CPoint`.

Například pomocí prvního přetížení najít rozdíl mezi dvěma body `CPoint(25, -19)` a `CPoint(15, 5)` vrátí `CSize(10, -24)`.

Odečtení `CSize` od `CPoint` je stejný výpočet `CPoint` jako výše, ale vrátí objekt, nikoli `CSize` objekt. Například pomocí druhého přetížení můžete najít rozdíl mezi bodem `CPoint(25, -19)` a velikostí `CSize(15, 5)` vrácenou `CPoint(10, -24)`.

Odčítáním obdélníku od bodu vrátí posun obdélníku o záporné `x` hodnoty a `y` zadané v bodě. Například použití posledního přetížení k posunu obdélníku `CRect(125, 200, 325, 400)` o vrácení `CRect(100, 219, 300, 419)`tohoto bodu `CPoint(25, -19)` .

Použijte unární operátor pro negaci bodu. Například použití unárního operátoru s návratovým `CPoint(25, -19)` `CPoint(-25, 19)`bodem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázka MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Struktura bodu](/windows/win32/api/windef/ns-windef-point)<br/>
[CRect – třída](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize – třída](../../atl-mfc-shared/reference/csize-class.md)
