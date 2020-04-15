---
title: CSize – třída
ms.date: 10/18/2018
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
ms.openlocfilehash: 6d1b82e3f60428e3a778709dc69de983a7f886bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317675"
---
# <a name="csize-class"></a>CSize – třída

Podobně jako windows [size](/windows/win32/api/windef/ns-windef-size) struktury, která implementuje relativní souřadnice nebo pozice.

## <a name="syntax"></a>Syntaxe

```
class CSize : public tagSIZE
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSize::CSize](#csize)|Vytvoří `CSize` objekt.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CSize::operátor -](#operator_-)|Odečte dvě velikosti.|
|[CSize::operátor !=](#operator_neq)|Kontroluje nerovnost mezi `CSize` a velikostí.|
|[CSize::operátor +](#operator_add)|Přidá dvě velikosti.|
|[CSize::operátor +=](#operator_add_eq)|Přidá velikost `CSize`do .|
|[CSize::operátor -=](#operator_-_eq)|Odečte velikost od `CSize`.|
|[CSize::operátor ==](#operator_eq_eq)|Kontroluje rovnost mezi `CSize` a velikostí.|

## <a name="remarks"></a>Poznámky

Tato třída je odvozena od `SIZE` struktury. To znamená, že `CSize` můžete předat v `SIZE` parametr, který volá `SIZE` pro a, že `CSize`datové členy struktury jsou přístupné datové členy .

A `cx` `cy` členové `SIZE` (a `CSize`) jsou veřejní. Kromě toho `CSize` implementuje členské funkce `SIZE` pro manipulaci se strukturou.

> [!NOTE]
> Další informace o sdílených `CSize`třídách nástrojů (například ) naleznete [v tématu Sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagSIZE`

`CSize`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltypes.h

## <a name="csizecsize"></a><a name="csize"></a>CSize::CSize

Vytvoří `CSize` objekt.

```
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw();
```

### <a name="parameters"></a>Parametry

*initCX*<br/>
Nastaví `cx` člen `CSize`pro .

*initCY*<br/>
Nastaví `cy` člen `CSize`pro .

*initSize*<br/>
[STRUKTURA VELIKOSTI](/windows/win32/api/windef/ns-windef-size) nebo `CSize` objekt `CSize`použitý k inicializaci .

*initPt*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point) struktura `CPoint` nebo objekt používaný `CSize`k inicializaci .

*dwVelikost*<br/>
DWORD slouží k `CSize`inicializaci . Slovo nižšího řádu `cx` je členem a slovo vyššího `cy` řádu je členem.

### <a name="remarks"></a>Poznámky

Pokud nejsou uvedeny `cx` žádné `cy` argumenty a jsou inicializovány na nulu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

## <a name="csizeoperator-"></a><a name="operator_eq_eq"></a>CSize::operátor ==

Kontroluje rovnost mezi dvěma velikostmi.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí nenulovou, pokud jsou velikosti stejné, otherwize 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

## <a name="csizeoperator-"></a><a name="operator_neq"></a>CSize::operátor !=

Kontroluje nerovnost mezi dvěma velikostmi.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí nenulovou, pokud velikost i rovna, jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add_eq"></a>CSize::operátor +=

Přidá k tomuto `CSize`rozměru velikost .

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-_eq"></a>CSize::operátor -=

Odečte velikost od `CSize`tohoto .

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add"></a>CSize::operátor +

Tyto operátory `CSize` přidat tuto hodnotu hodnotu parametru.

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>Poznámky

Viz následující popisy jednotlivých operátorů:

- **operátor +(** *velikost* **)**

  Tato operace `CSize` přidá dvě hodnoty.

- **operátor +(** *bod* **)**

  Tato operace posune (přesune) hodnotu [POINT](/previous-versions/dd162805\(v=vs.85\)) (nebo [CPoint)](../../atl-mfc-shared/reference/cpoint-class.md)o tuto `CSize` hodnotu. A `cx` `cy` členy této `CSize` hodnoty jsou `x` přidány `y` a datové `POINT` členy hodnoty. Je obdobou verze [CPoint::operator +,](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) která přebírá parametr [SIZE.](/windows/win32/api/windef/ns-windef-size)

- **operátor +(** *lpRect* **)**

   Tato operace posune (přesune) hodnotu [RECT](/previous-versions/dd162897\(v=vs.85\)) (nebo `CSize` [CRect)](../../atl-mfc-shared/reference/crect-class.md)touto hodnotou. Členy `cx` `cy` a členy `CSize` této hodnoty `left`jsou `top` `right`přidány `bottom` do , `RECT` , a datové členy hodnoty. Je obdobou verze [CRect::operator +,](../../atl-mfc-shared/reference/crect-class.md#operator_add) která přebírá parametr [SIZE.](/windows/win32/api/windef/ns-windef-size)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-"></a>CSize::operátor -

První tři z těchto operátorů odečíst tuto `CSize` hodnotu na hodnotu parametru.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Poznámky

Čtvrtý operátor unární mínus změní znaménko `CSize` hodnoty. Viz následující popisy jednotlivých operátorů:

- **operátor -(** *velikost* **)**

  Tato operace odečte `CSize` dvě hodnoty.

- **operátor -(** *bod* **)**

  Tato operace posune (přesune) [point](/previous-versions/dd162805\(v=vs.85\)) nebo [cpoint](../../atl-mfc-shared/reference/cpoint-class.md) hodnotu `CSize` aditivní inverzní této hodnoty. A `cx` `cy` a `CSize` tato hodnota jsou odečteny od `x` a `y` datové členy `POINT` hodnoty. Je obdobou verze [CPoint::operator -](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) která přebírá parametr [SIZE.](/windows/win32/api/windef/ns-windef-size)

- **operátor -(** *lpRect* **)**

  Tato operace posune (přesune) hodnotu [RECT](/previous-versions/dd162897\(v=vs.85\)) nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) aditivní inverzní k této `CSize` hodnotě. A `cx` `cy` členy této `CSize` hodnoty jsou odečteny `top` `right`od `bottom` `left`, , `RECT` a datových členů hodnoty. Je obdobou verze [CRect::operator -](../../atl-mfc-shared/reference/crect-class.md#operator_-) která přebírá parametr [SIZE.](/windows/win32/api/windef/ns-windef-size)

- **operátor -()**

  Tato operace vrátí aditivum inverzní této `CSize` hodnoty.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Viz také

[MDI vzorku knihovny MFc](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRect – třída](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint – třída](../../atl-mfc-shared/reference/cpoint-class.md)
