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
ms.openlocfilehash: 26bb43355f4dff3f77a905068bea83dd1ceaf79c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491646"
---
# <a name="csize-class"></a>CSize – třída

Podobně jako struktura [velikosti](/windows/win32/api/windef/ns-windef-size) systému Windows, která implementuje relativní souřadnici nebo polohu.

## <a name="syntax"></a>Syntaxe

```
class CSize : public tagSIZE
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSize::CSize](#csize)|`CSize` Vytvoří objekt.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CSize:: operator-](#operator_-)|Odečte dvě velikosti.|
|[CSize:: operator! =](#operator_neq)|Kontroluje nerovnost mezi `CSize` a velikostí.|
|[CSize:: operator + – operátor](#operator_add)|Přidá dvě velikosti.|
|[CSize:: operator + =](#operator_add_eq)|Přidá velikost do `CSize`.|
|[CSize:: operator-=](#operator_-_eq)|Odečte velikost od `CSize`.|
|[CSize:: operator = = – operátor](#operator_eq_eq)|Kontroluje rovnost mezi `CSize` a velikostí.|

## <a name="remarks"></a>Poznámky

Tato třída je odvozena z `SIZE` struktury. To znamená, že můžete předat `CSize` do parametr, který volá `SIZE` pro a, aby datové členy `SIZE` struktury byly přístupné datovým členům `CSize`.

A členové (a )`CSize`jsouveřejné. `SIZE` `cy` `cx` Kromě toho `CSize` implementuje členské funkce pro manipulaci s `SIZE` strukturou.

> [!NOTE]
> Další informace o třídách sdílených nástrojů (například `CSize`) naleznete v tématu [Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagSIZE`

`CSize`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltypes. h

##  <a name="csize"></a>CSize::CSize

`CSize` Vytvoří objekt.

```
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw();
```

### <a name="parameters"></a>Parametry

*initCX*<br/>
`cx` Nastaví člena`CSize`pro.

*initCY*<br/>
`cy` Nastaví člena`CSize`pro.

*initSize*<br/>
[Velikost](/windows/win32/api/windef/ns-windef-size) struktury nebo `CSize` objektu používaného k `CSize`inicializaci.

*initPt*<br/>
Struktura [bodu](/windows/win32/api/windef/ns-windef-point) nebo `CPoint` objekt použitý k inicializaci `CSize`.

*nenulového dwSize funkci*<br/>
Hodnota DWORD používaná k `CSize`inicializaci. Slovo s nižším pořadím je `cx` člen a v rámci něj `cy` je slovo s vyšším pořadím členem.

### <a name="remarks"></a>Poznámky

Pokud nejsou zadány `cx` žádné argumenty a `cy` jsou inicializovány na nulu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

##  <a name="operator_eq_eq"></a>CSize:: operator = = – operátor

Kontroluje rovnost mezi dvěma velikostmi.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí nenulovou hodnotu, pokud jsou velikosti stejné, otherwize 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

##  <a name="operator_neq"></a>CSize:: operator! =

Kontroluje nerovnost mezi dvěma velikostmi.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí nenulovou hodnotu, pokud nejsou velikosti stejné, jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

##  <a name="operator_add_eq"></a>CSize:: operator + =

Přidá k této `CSize`velikosti.

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

##  <a name="operator_-_eq"></a>CSize:: operator-=

Odečte velikost od tohoto `CSize`.

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

##  <a name="operator_add"></a>CSize:: operator + – operátor

Tyto operátory přidávají `CSize` tuto hodnotu k hodnotě parametru.

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>Poznámky

Podívejte se na následující popisy jednotlivých operátorů:

- **operator + (** *Size* **)** – operátor

  Tato operace přidá dvě `CSize` hodnoty.

- **operator + (** *Point* **)** – operátor

  Tato operace posune (přesouvá) hodnotu [bodu](/previous-versions/dd162805\(v=vs.85\)) (nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) na základě této `CSize` hodnoty. `x` `y` Členové `cx` a `cy` této hodnoty`CSize` jsou přidánidodatových`POINT` členů a hodnoty. Je obdobou verzi [CPoint:: operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) , která přijímá parametr [velikosti](/windows/win32/api/windef/ns-windef-size) .

- **+ – operátor (** *lpRect* **)**

   Tato operace posune (přesouvá) hodnotu [Rect](/previous-versions/dd162897\(v=vs.85\)) (nebo [CRect](../../atl-mfc-shared/reference/crect-class.md)) podle této `CSize` hodnoty. `left` `right` `top` `bottom` Členové `cx` a `cy` této`CSize` hodnoty jsou přidáni do datových členů,, a v`RECT` hodnotě. Je obdobou verzi [CRect:: operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) , která přijímá parametr [velikosti](/windows/win32/api/windef/ns-windef-size) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

##  <a name="operator_-"></a>CSize:: operator-

První tři z těchto operátorů odečtou `CSize` tuto hodnotu na hodnotu parametru.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Poznámky

Čtvrtý operátor, Unární minus, změní znaménko `CSize` hodnoty. Podívejte se na následující popisy jednotlivých operátorů:

- **-(** *Size* **)** – operátor

  Tato operace odečte dvě `CSize` hodnoty.

- **-(** *Point* **)** – operátor

  Tato operace posune (přesouvá) hodnotu [Point](/previous-versions/dd162805\(v=vs.85\)) nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) doplňkovou hodnotou, která je doplňkovou `CSize` hodnotou. `y` `x` A z této hodnotyjsou`POINT` odečteny od datových členů a hodnoty. `CSize` `cy` `cx` Je obdobou verzi [CPoint:: operator-](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) , která přijímá parametr [velikosti](/windows/win32/api/windef/ns-windef-size) .

- **– – operátor (** *lpRect* **)**

  Tato operace posune (přesouvá) hodnotu [Rect](/previous-versions/dd162897\(v=vs.85\)) nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) doplňkovou hodnotou, která je doplňkovou `CSize` hodnotou. `top` `right` `left` `bottom` A členové této hodnotyjsou`RECT` odečteni od datových členů hodnoty,, a. `CSize` `cy` `cx` Je obdobou verzi [CRect:: operator-](../../atl-mfc-shared/reference/crect-class.md#operator_-) , která přijímá parametr [velikosti](/windows/win32/api/windef/ns-windef-size) .

- **– operátor ()**

  Tato operace vrátí doplňkovou `CSize` hodnotu pro doplňkovou hodnotu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázka MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRect – třída](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint – třída](../../atl-mfc-shared/reference/cpoint-class.md)
