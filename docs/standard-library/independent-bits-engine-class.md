---
title: independent_bits_engine – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: 28c9301d270ef516a1acc59f6ab06f0e61a1c9c5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687932"
---
# <a name="independent_bits_engine-class"></a>independent_bits_engine – třída

Vygeneruje náhodnou posloupnost čísel se zadaným počtem bitů pomocí opětovného sbalení bitů z hodnot vrácených základním modulem.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Parametry

@No__t_1 *modulu*
Typ základního modulu.

*W* \
**Velikost slova**. Velikost vygenerovaných čísel v bitech. **Předběžná podmínka**: `0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType* \
Typ výsledku unsigned integer. Možné typy najdete v tématu [\<random >](../standard-library/random.md).

## <a name="members"></a>Členové

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Další informace o členech motoru naleznete v tématu [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato šablona třídy popisuje *adaptér modulu* , který vytváří hodnoty pomocí opětovného sbalení bitů z hodnot vrácených základním modulem, což *vede k důsledkům 32bitových hodnot*.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<random >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<random >](../standard-library/random.md)
