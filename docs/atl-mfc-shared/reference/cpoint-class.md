---
title: Cpoint – třída
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
ms.openlocfilehash: 4f6ab15f80ac448b4e7383e2db92f22262c20d08
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178066"
---
# <a name="cpoint-class"></a>Cpoint – třída

Podobně jako Windows `POINT` struktury.

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
|[CPoint::Offset](#offset)|Přidá hodnoty `x` a `y` členy `CPoint`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CPoint::operator-](#operator_-)|Vrátí rozdíl `CPoint` a velikost nebo negace bod nebo rozdíl velikosti mezi dvěma body nebo offset zápornou velikostí.|
|[CPoint::operator! =](#operator_neq)|Kontroly pro nerovnost mezi dvěma body.|
|[CPoint::operator +](#operator_add)|Vrátí součet `CPoint` a velikost nebo bodu, nebo `CRect` posunut o velikosti.|
|[CPoint::operator +=](#operator_add_eq)|Odsadí `CPoint` přidáním velikosti nebo bodu.|
|[CPoint::operator-=](#operator_-_eq)|Odsadí `CPoint` tak, že se velikost nebo bodu.|
|[CPoint::operator ==](#operator_eq_eq)|Kontroly pro rovnost mezi dvěma body.|

## <a name="remarks"></a>Poznámky

Zahrnuje také členské funkce pro manipulaci s `CPoint` a [bodu](/windows/desktop/api/windef/ns-windef-tagpoint) struktury.

A `CPoint` objektu lze použít všude, kde `POINT` struktura se používá. Operátory, které pracují s "velikost" této třídy buď přijměte [CSize](../../atl-mfc-shared/reference/csize-class.md) objekty nebo [velikost](/windows/desktop/api/windef/ns-windef-tagsize) struktur, protože zaměnitelné.

> [!NOTE]
>  Tato třída je odvozena z `tagPOINT` struktury. (Název `tagPOINT` je název ne tak často používaná pro `POINT` struktura.) To znamená, že datové členy `POINT` strukturu, `x` a `y`, jsou dostupné datové členy `CPoint`.

> [!NOTE]
>  Další informace o sdílené třídy nástroje (jako je `CPoint`), najdete v článku [sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagPOINT`

`CPoint`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltypes.h

##  <a name="cpoint"></a>  CPoint::CPoint

Vytvoří `CPoint` objektu.

```
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```

### <a name="parameters"></a>Parametry

*initX*<br/>
Určuje hodnotu `x` člen `CPoint`.

*initY*<br/>
Určuje hodnotu `y` člen `CPoint`.

*initPt*<br/>
[BOD](/windows/desktop/api/windef/ns-windef-tagpoint) struktury nebo `CPoint` určující hodnoty použité k inicializaci `CPoint`.

*initSize*<br/>
[VELIKOST](/windows/desktop/api/windef/ns-windef-tagsize) struktury nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) určující hodnoty použité k inicializaci `CPoint`.

*dwPoint*<br/>
Nastaví `x` člen pro nižší řád slova *dwPoint* a `y` člena na vyšší řád slova *dwPoint*.

### <a name="remarks"></a>Poznámky

Pokud nejsou zadány žádné argumenty, `x` a `y` členy jsou nastaveny na hodnotu 0.

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

##  <a name="offset"></a>  CPoint::Offset

Přidá hodnoty `x` a `y` členy `CPoint`.

```
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>Parametry

*xOffset*<br/>
Určuje velikost odsazení `x` člena `CPoint`.

*yOffset*<br/>
Určuje velikost odsazení `y` člena `CPoint`.

*Bod*<br/>
Určuje dobu ( [bodu](/windows/desktop/api/windef/ns-windef-tagpoint) nebo `CPoint`) pro posun `CPoint`.

*Velikost*<br/>
Určuje dobu ( [velikost](/windows/desktop/api/windef/ns-windef-tagsize) nebo [CSize](../../atl-mfc-shared/reference/csize-class.md)) pro posun `CPoint`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

##  <a name="operator_eq_eq"></a>  CPoint::operator ==

Kontroly pro rovnost mezi dvěma body.

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Obsahuje [bodu](/windows/desktop/api/windef/ns-windef-tagpoint) struktury nebo `CPoint` objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud body rovnají. jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

##  <a name="operator_neq"></a>  CPoint::operator! =

Kontroly pro nerovnost mezi dvěma body.

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Obsahuje [bodu](/windows/desktop/api/windef/ns-windef-tagpoint) struktury nebo `CPoint` objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud body nejsou stejné; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

##  <a name="operator_add_eq"></a>  CPoint::operator +=

První přetížení přidá velikost, aby `CPoint`.

```
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Obsahuje [velikost](/windows/desktop/api/windef/ns-windef-tagsize) struktury nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.

*Bod*<br/>
Obsahuje [bodu](/windows/desktop/api/windef/ns-windef-tagpoint) struktury nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objektu.

### <a name="remarks"></a>Poznámky

Druhé přetížení přidá bod, který má `CPoint`.

V obou případech sčítání se provádí tak, že přidáte `x` (nebo `cx`) člen zpracovával pravý operand na `x` člena `CPoint` a přidání `y` (nebo `cy`) člen zpracovával pravý operand na `y` člena `CPoint`.

Například přidáním `CPoint(5, -7)` na proměnnou, která obsahuje `CPoint(30, 40)` změní proměnnou `CPoint(35, 33)`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

##  <a name="operator_-_eq"></a>  CPoint::operator-=

Velikost z odečte první přetížení `CPoint`.

```
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Obsahuje [velikost](/windows/desktop/api/windef/ns-windef-tagsize) struktury nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.

*Bod*<br/>
Obsahuje [bodu](/windows/desktop/api/windef/ns-windef-tagpoint) struktury nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objektu.

### <a name="remarks"></a>Poznámky

Odečte bod z druhé přetížení `CPoint`.

V obou případech se provádí odčítání tak, že se `x` (nebo `cx`) člen zpracovával pravý operand z `x` člena `CPoint` a odečítání `y` (nebo `cy`) členem pravém Operand od `y` člena `CPoint`.

Například odečtením `CPoint(5, -7)` z proměnné, která obsahuje `CPoint(30, 40)` změní proměnnou `CPoint(25, 47)`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

##  <a name="operator_add"></a>  CPoint::operator +

Tento operátor odsazení `CPoint` podle `CPoint` nebo `CSize` objektu, nebo odsazení `CRect` podle `CPoint`.

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Obsahuje [velikost](/windows/desktop/api/windef/ns-windef-tagsize) struktury nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.

*Bod*<br/>
Obsahuje [bodu](/windows/desktop/api/windef/ns-windef-tagpoint) struktury nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objektu.

*lprect –*<br/>
Obsahuje ukazatel [RECT](/windows/desktop/api/windef/ns-windef-tagrect) struktury nebo [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

A `CPoint` , který je posunut velikosti `CPoint` , který je posunut bod, nebo `CRect` posunut bod.

### <a name="remarks"></a>Poznámky

Například pomocí jedné z první dvě přetížení odsazení bod `CPoint(25, -19)` bodem `CPoint(15, 5)` nebo velikost `CSize(15, 5)` vrátí hodnotu `CPoint(40, -14)`.

Přidání obdélníku do bodu vrátí obdélníku po se posunut `x` a `y` hodnoty zadané v bodu. Například pomocí poslední přetížení odsazení obdélník `CRect(125, 219, 325, 419)` bodem `CPoint(25, -19)` vrátí `CRect(150, 200, 350, 400)`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

##  <a name="operator_-"></a>  CPoint::operator-

Použijte jednu z prvních dvou přetížení se má odečíst `CPoint` nebo `CSize` objektu z `CPoint`.

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
A [bodu](/windows/desktop/api/windef/ns-windef-tagpoint) struktury nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objektu.

*Velikost*<br/>
A [velikost](/windows/desktop/api/windef/ns-windef-tagsize) struktury nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.

*lprect –*<br/>
Ukazatel [RECT](/windows/desktop/api/windef/ns-windef-tagrect) struktury nebo [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

A `CSize` , který je rozdíl mezi dvěma body `CPoint` , který je posunut negace velikosti, `CRect` , který je posunut negace bod, nebo `CPoint` , který je negace bod.

### <a name="remarks"></a>Poznámky

Třetí přetížení posuny `CRect` negaci `CPoint`. Nakonec použijte unární operátor negovat `CPoint`.

Například pomocí prvního přetížení rozdíl mezi dvěma body `CPoint(25, -19)` a `CPoint(15, 5)` vrátí `CSize(10, -24)`.

Přičítání `CSize` z `CPoint` nemá stejný výpočet, jak je uvedeno výše, ale vrací `CPoint` objekt nelze `CSize` objektu. Například použití druhé přetížení rozdíl mezi bodem `CPoint(25, -19)` a velikost `CSize(15, 5)` vrátí `CPoint(10, -24)`.

Podle negativy z odečtením obdélník z bodu vrátí posunutí obdélník `x` a `y` hodnoty zadané v bodu. Například pomocí poslední přetížení odsazení obdélník `CRect(125, 200, 325, 400)` bodem `CPoint(25, -19)` vrátí `CRect(100, 219, 300, 419)`.

Operátor unární negate bod. Například použití s bodem unární operátor `CPoint(25, -19)` vrátí `CPoint(-25, 19)`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC MDI](../../visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[POINT – struktura](/windows/desktop/api/windef/ns-windef-tagpoint)<br/>
[CRect – třída](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize – třída](../../atl-mfc-shared/reference/csize-class.md)

