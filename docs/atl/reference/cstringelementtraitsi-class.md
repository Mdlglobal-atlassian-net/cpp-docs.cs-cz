---
title: Třída CStringElementTraitsI
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
ms.openlocfilehash: 32980e19443cb17a3a688c85ff21195c60ed2124
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330593"
---
# <a name="cstringelementtraitsi-class"></a>Třída CStringElementTraitsI

Tato třída poskytuje statické funkce související s řetězci uloženými v objektech třídy kolekce. Je podobný [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), ale provádí porovnání bez rozlišování velkých a malých písmen.

## <a name="syntax"></a>Syntaxe

```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>
class CStringElementTraitsI : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat, která mají být uložena v kolekci.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CStringElementTraitsI::INARGTYPE](#inargtype)|Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.|
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|Datový typ, který se má použít pro načítání prvků z objektu třídy kolekce.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CStringElementTraitsI::Porovnat prvky](#compareelements)|Volání této statické funkce porovnat dva řetězce prvky rovnosti, ignoruje rozdíly v případě.|
|[CStringElementTraitsI::PorovnatprvkyOrdered](#compareelementsordered)|Volání této statické funkce porovnat dva řetězce prvky, ignoruje rozdíly v případě.|
|[CStringElementTraitsI::Hash](#hash)|Volání této statické funkce k výpočtu hodnoty hash pro daný prvek řetězce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje statické funkce pro porovnávání řetězců a pro vytvoření hodnoty hash. Tyto funkce jsou užitečné při použití třídy kolekce k ukládání dat založených na řetězci. Použijte [CStringRefElementTraits,](../../atl/reference/cstringrefelementtraits-class.md) když mají být objekty řetězce zpracovány jako odkazy.

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="cstringelementtraitsicompareelements"></a><a name="compareelements"></a>CStringElementTraitsI::Porovnat prvky

Volání této statické funkce porovnat dva řetězce prvky rovnosti, ignoruje rozdíly v případě.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První prvek řetězce.

*str2*<br/>
Druhý řetězec element.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud jsou prvky stejné, false otherwise.

### <a name="remarks"></a>Poznámky

Porovnání jsou malá a velká písmena.

## <a name="cstringelementtraitsicompareelementsordered"></a><a name="compareelementsordered"></a>CStringElementTraitsI::PorovnatprvkyOrdered

Volání této statické funkce porovnat dva řetězce prvky, ignoruje rozdíly v případě.

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

### <a name="remarks"></a>Poznámky

Porovnání jsou malá a velká písmena.

## <a name="cstringelementtraitsihash"></a><a name="hash"></a>CStringElementTraitsI::Hash

Volání této statické funkce k výpočtu hodnoty hash pro daný prvek řetězce.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Prvek řetězce.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hash vypočtenou pomocí obsahu řetězce.

## <a name="cstringelementtraitsiinargtype"></a><a name="inargtype"></a>CStringElementTraitsI::INARGTYPE

Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsioutargtype"></a><a name="outargtype"></a>CStringElementTraitsI::OUTARGTYPE

Datový typ, který se má použít pro načítání prvků z objektu třídy kolekce.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Viz také

[Třída CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)
