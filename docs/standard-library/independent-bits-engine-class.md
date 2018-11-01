---
title: independent_bits_engine – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: 8f420ca054d20cd222b8eda9a4a35a383a8e535a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635835"
---
# <a name="independentbitsengine-class"></a>independent_bits_engine – třída

Generuje náhodné pořadí čísel s zadaný počet bitů ve opětovné bitů z hodnot vrácených základním modulem.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Parametry

*Modul*<br/>
Typ základního modulu.

*W*<br/>
**Word velikost**. Velikost v bitech, každé číslo vygenerována. **Předběžná podmínka**: `0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType*<br/>
Typ výsledku celého čísla bez znaménka. Možné typy, najdete v části [ \<náhodné >](../standard-library/random.md).

## <a name="members"></a>Členové

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Další informace o členech modul, naleznete v tématu [ \<náhodné >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato třída šablony popisuje *modul adaptér* , která vytváří hodnoty přebalením bitů z hodnot vrácených základním modulem, což vede k *W*-bitové hodnoty.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
