---
title: Cstringrefelementtraits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
dev_langs:
- C++
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8369afbbf423f85df0e38f7f2979b3b7e48f8591
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067919"
---
# <a name="cstringrefelementtraits-class"></a>Cstringrefelementtraits – třída

Tato třída poskytuje statické funkce související se ukládají v objektech třídy kolekce řetězců. Řetězcových objektů jsou zpracovány jako odkazy.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CStringRefElementTraits : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat uložených v kolekci.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStringRefElementTraits::CompareElements](#compareelements)|Voláním této funkce statických porovnat dva prvky řetězce pro rovnosti.|
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|Voláním této funkce statických porovnat dva prvky řetězce.|
|[CStringRefElementTraits::Hash](#hash)|Voláním této funkce statických vypočítat hodnotu hash pro prvek zadaného řetězce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje statické funkce pro porovnávání řetězců a pro vytvoření hodnoty hash. Tyto funkce jsou užitečné při použití třídy kolekce k ukládání dat založené na řetězci. Na rozdíl od [cstringelementtraits –](../../atl/reference/cstringelementtraits-class.md) a [cstringelementtraitsi –](../../atl/reference/cstringelementtraitsi-class.md), `CStringRefElementTraits` způsobí, že `CString` argumenty, které mají být předány jako **const** `CString&` odkazy.

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Celementtraitsbase –](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="compareelements"></a>  CStringRefElementTraits::CompareElements

Voláním této funkce statických porovnat dva prvky řetězce pro rovnosti.

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>Parametry

*element1*<br/>
První řetězec elementu.

*element2*<br/>
Druhý řetězec elementu.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud prvky jsou stejné, jinak hodnota false.

##  <a name="compareelementsordered"></a>  CStringRefElementTraits::CompareElementsOrdered

Voláním této funkce statických porovnat dva prvky řetězce.

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

##  <a name="hash"></a>  CStringRefElementTraits::Hash

Voláním této funkce statických vypočítat hodnotu hash pro prvek zadaného řetězce.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Parametry

*str*<br/>
Element řetězce.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hash pomocí obsahu řetězce.

## <a name="see-also"></a>Viz také

[CElementTraitsBase – třída](../../atl/reference/celementtraitsbase-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
