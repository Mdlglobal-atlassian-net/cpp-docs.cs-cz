---
title: Cstringelementtraitsi – třída
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
ms.openlocfilehash: 35215546268c4c48f913e7aef763768fffc76d59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551720"
---
# <a name="cstringelementtraitsi-class"></a>Cstringelementtraitsi – třída

Tato třída poskytuje statické funkce související se ukládají v objektech třídy kolekce řetězců. Je to podobné [cstringelementtraits –](../../atl/reference/cstringelementtraits-class.md), ale provádí porovnávání bez rozlišování.

## <a name="syntax"></a>Syntaxe

```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>
class CStringElementTraitsI : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat uložených v kolekci.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CStringElementTraitsI::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání prvků do objektu třídy kolekce.|
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|Datový typ použitý pro získání prvky z třídy objektu kolekce.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStringElementTraitsI::CompareElements](#compareelements)|Voláním této funkce statických porovnat dva prvky řetězce pro rovnosti, ignoruje se rozdíly v případě.|
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|Voláním této funkce statických porovnat dva prvky řetězce rozdíly v případě se ignoruje.|
|[CStringElementTraitsI::Hash](#hash)|Voláním této funkce statických vypočítat hodnotu hash pro prvek zadaného řetězce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje statické funkce pro porovnávání řetězců a pro vytvoření hodnoty hash. Tyto funkce jsou užitečné při použití třídy kolekce k ukládání dat založené na řetězci. Použití [cstringrefelementtraits –](../../atl/reference/cstringrefelementtraits-class.md) při řetězcových objektů mají být pomocí řešena jako odkazy.

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Celementtraitsbase –](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="compareelements"></a>  CStringElementTraitsI::CompareElements

Voláním této funkce statických porovnat dva prvky řetězce pro rovnosti, ignoruje se rozdíly v případě.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Parametry

*Str1*<br/>
První řetězec elementu.

*řetězci Str2*<br/>
Druhý řetězec elementu.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud prvky jsou stejné, jinak hodnota false.

### <a name="remarks"></a>Poznámky

Porovnávání rozlišuje malá a velká písmena.

##  <a name="compareelementsordered"></a>  CStringElementTraitsI::CompareElementsOrdered

Voláním této funkce statických porovnat dva prvky řetězce rozdíly v případě se ignoruje.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Parametry

*Str1*<br/>
První řetězec elementu.

*řetězci Str2*<br/>
Druhý řetězec elementu.

### <a name="return-value"></a>Návratová hodnota

Nula v případě, že jsou řetězce identické, < 0 Pokud *str1* je menší než *řetězci str2*, nebo > 0 Pokud *str1* je větší než *řetězci str2*. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) metoda se používá k provádění porovnání.

### <a name="remarks"></a>Poznámky

Porovnávání rozlišuje malá a velká písmena.

##  <a name="hash"></a>  CStringElementTraitsI::Hash

Voláním této funkce statických vypočítat hodnotu hash pro prvek zadaného řetězce.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Parametry

*str*<br/>
Element řetězce.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hash pomocí obsahu řetězce.

##  <a name="inargtype"></a>  CStringElementTraitsI::INARGTYPE

Datový typ pro použití při přidávání prvků do objektu třídy kolekce.

```
typedef T::PCXSTR INARGTYPE;
```

##  <a name="outargtype"></a>  CStringElementTraitsI::OUTARGTYPE

Datový typ použitý pro získání prvky z třídy objektu kolekce.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Viz také

[CElementTraitsBase – třída](../../atl/reference/celementtraitsbase-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[CStringElementTraits – třída](../../atl/reference/cstringelementtraits-class.md)
