---
title: Třída CStringRefElementTraits
ms.date: 11/04/2016
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
ms.openlocfilehash: b4dd76b9592b255a1553be3ca7a249f58fb2672e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330582"
---
# <a name="cstringrefelementtraits-class"></a>Třída CStringRefElementTraits

Tato třída poskytuje statické funkce související s řetězci uloženými v objektech třídy kolekce. Objekty řetězce jsou zpracovány jako odkazy.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CStringRefElementTraits : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat, která mají být uložena v kolekci.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CStringRefElementTraits::Porovnatprvky](#compareelements)|Volání této statické funkce porovnat dva řetězce prvky rovnosti.|
|[CStringRefElementTraits::PorovnatprvkyOrdered](#compareelementsordered)|Volání této statické funkce porovnat dva řetězce prvky.|
|[CStringRefElementTraits::Hash](#hash)|Volání této statické funkce k výpočtu hodnoty hash pro daný prvek řetězce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje statické funkce pro porovnávání řetězců a pro vytvoření hodnoty hash. Tyto funkce jsou užitečné při použití třídy kolekce k ukládání dat založených na řetězci. Na rozdíl od [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) a [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) `CStringRefElementTraits` , způsobí, `CString` že argumenty, které mají být předány jako **const** `CString&` odkazy.

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="cstringrefelementtraitscompareelements"></a><a name="compareelements"></a>CStringRefElementTraits::Porovnatprvky

Volání této statické funkce porovnat dva řetězce prvky rovnosti.

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>Parametry

*element1*<br/>
První prvek řetězce.

*element2*<br/>
Druhý řetězec element.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud jsou prvky stejné, false otherwise.

## <a name="cstringrefelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringRefElementTraits::PorovnatprvkyOrdered

Volání této statické funkce porovnat dva řetězce prvky.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První prvek řetězce.

*str2*<br/>
Druhý řetězec element.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud řetězce jsou identické, < 0, pokud *str1* je menší než *str2*, nebo > 0, pokud *str1* je větší než *str2*. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) Metoda se používá k provedení porovnání.

## <a name="cstringrefelementtraitshash"></a><a name="hash"></a>CStringRefElementTraits::Hash

Volání této statické funkce k výpočtu hodnoty hash pro daný prvek řetězce.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Prvek řetězce.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hash vypočtenou pomocí obsahu řetězce.

## <a name="see-also"></a>Viz také

[Třída CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
