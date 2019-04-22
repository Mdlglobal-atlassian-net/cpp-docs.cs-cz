---
title: Csize – třída
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
ms.openlocfilehash: 5e19ab9b9339f3e6f61abf7731a40ed3832b50c9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767359"
---
# <a name="csize-class"></a>Csize – třída

Podobně jako Windows [velikost](/windows/desktop/api/windef/ns-windef-tagsize) struktura, která implementuje relativní souřadnice nebo pozici.

## <a name="syntax"></a>Syntaxe

```
class CSize : public tagSIZE
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSize::CSize](#csize)|Vytvoří `CSize` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CSize::operator-](#operator_-)|Odečte dvou velikostech.|
|[CSize::operator! =](#operator_neq)|Zkontroluje nerovnost mezi `CSize` a velikost.|
|[CSize::operator +](#operator_add)|Přidá dvě velikosti.|
|[CSize::operator +=](#operator_add_eq)|Přidá velikost pro `CSize`.|
|[CSize::operator-=](#operator_-_eq)|Odečte velikost z `CSize`.|
|[CSize::operator ==](#operator_eq_eq)|Vyhledá rovnost mezi `CSize` a velikost.|

## <a name="remarks"></a>Poznámky

Tato třída je odvozena z `SIZE` struktury. To znamená, že můžete předat `CSize` parametrem, který volá `SIZE` a datové členy `SIZE` struktury jsou dostupné datové členy `CSize`.

`cx` a `cy` členy `SIZE` (a `CSize`) jsou veřejné. Kromě toho `CSize` implementuje členské funkce pro manipulaci s `SIZE` struktury.

> [!NOTE]
> Další informace o sdílené třídy nástroje (jako je `CSize`), najdete v článku [sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagSIZE`

`CSize`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltypes.h

##  <a name="csize"></a>  CSize::CSize

Vytvoří `CSize` objektu.

```
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw();
```

### <a name="parameters"></a>Parametry

*initCX*<br/>
Nastaví `cx` člena `CSize`.

*initCY*<br/>
Nastaví `cy` člena `CSize`.

*initSize*<br/>
[VELIKOST](/windows/desktop/api/windef/ns-windef-tagsize) struktury nebo `CSize` objekt použitý k inicializaci `CSize`.

*initPt*<br/>
[BOD](/windows/desktop/api/windef/ns-windef-tagpoint) struktury nebo `CPoint` objekt použitý k inicializaci `CSize`.

*dwSize*<br/>
DWORD použitý k inicializaci `CSize`. Je nižší řád slova `cx` člen a vyšší řád slova je `cy` člena.

### <a name="remarks"></a>Poznámky

Pokud nejsou zadány žádné argumenty, `cx` a `cy` jsou inicializovány na nulu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

##  <a name="operator_eq_eq"></a>  CSize::operator ==

Kontroly pro rovnost mezi dvěma formáty.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí nenulovou hodnotu, pokud jsou stejné velikosti, otherwize 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

##  <a name="operator_neq"></a>  CSize::operator! =

Kontroly pro nerovnost mezi dvěma formáty.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí nenulovou hodnotu, pokud velikosti nejsou stejné, jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

##  <a name="operator_add_eq"></a>  CSize::operator +=

Přidá k tomuto velikost `CSize`.

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

##  <a name="operator_-_eq"></a>  CSize::operator-=

Odečte velikost z tohoto `CSize`.

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

##  <a name="operator_add"></a>  CSize::operator +

Přidejte tyto operátory `CSize` hodnotu k hodnotě parametru.

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>Poznámky

V následujících popisech jednotlivé operátory:

- **operátor + (** *velikost* **)**

  Tato operace přidá dvě `CSize` hodnoty.

- **operátor + (** *bodu* **)**

  Tato operace posun (přesun) [bodu](/previous-versions/dd162805\(v=vs.85\)) (nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) hodnotu situace `CSize` hodnotu. `cx` a `cy` členy tohoto `CSize` hodnoty se přidají do `x` a `y` datové členy `POINT` hodnotu. Je obdobou verzi [CPoint::operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) , která přijímá [velikost](/windows/desktop/api/windef/ns-windef-tagsize) parametru.

- **operátor + (** *lprect –* **)**

   Tato operace posun (přesun) [RECT](/previous-versions/dd162897\(v=vs.85\)) (nebo [crect –](../../atl-mfc-shared/reference/crect-class.md)) hodnotu situace `CSize` hodnotu. `cx` a `cy` členy tohoto `CSize` hodnoty se přidají do `left`, `top`, `right`, a `bottom` datové členy `RECT` hodnotu. Je obdobou verzi [CRect::operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) , která přijímá [velikost](/windows/desktop/api/windef/ns-windef-tagsize) parametru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

##  <a name="operator_-"></a>  CSize::operator-

První tři z těchto operátorů odečíst to `CSize` hodnotu k hodnotě parametru.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Poznámky

Čtvrtý operátor Unární minus, změní znaménko `CSize` hodnotu. V následujících popisech jednotlivé operátory:

- **operátor-(** *velikost* **)**

  Tato operace odečte dvě `CSize` hodnoty.

- **operátor-(** *bodu* **)**

  Tato operace posun (přesun) [bodu](/previous-versions/dd162805\(v=vs.85\)) nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) hodnoty additive inverzní to `CSize` hodnotu. `cx` a `cy` tohoto `CSize` jsou hodnota odečtena od `x` a `y` datové členy `POINT` hodnotu. Je obdobou verzi [CPoint::operator -](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) , která přijímá [velikost](/windows/desktop/api/windef/ns-windef-tagsize) parametr.

- **operátor-(** *lprect –* **)**

  Tato operace posun (přesun) [RECT](/previous-versions/dd162897\(v=vs.85\)) nebo [crect –](../../atl-mfc-shared/reference/crect-class.md) hodnoty additive inverzní to `CSize` hodnotu. `cx` a `cy` členy tohoto `CSize` jsou hodnota odečtena od `left`, `top`, `right`, a `bottom` datové členy `RECT` hodnotu. Je obdobou verzi [CRect::operator -](../../atl-mfc-shared/reference/crect-class.md#operator_-) , která přijímá [velikost](/windows/desktop/api/windef/ns-windef-tagsize) parametr.

- **operátor-)**

  Tato operace Vrátí inverzní additive tohoto `CSize` hodnotu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRect – třída](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint – třída](../../atl-mfc-shared/reference/cpoint-class.md)
