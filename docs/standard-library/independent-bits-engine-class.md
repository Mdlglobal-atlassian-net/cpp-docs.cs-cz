---
title: independent_bits_engine – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::independent_bits_engine
dev_langs:
- C++
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb76c477c54192dc6b6b969ecd4cdd32850c015f
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110302"
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
