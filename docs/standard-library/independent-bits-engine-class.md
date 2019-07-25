---
title: independent_bits_engine – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: a90e4be4ff6e92734f6b2e6804f8059be78e66b9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456347"
---
# <a name="independentbitsengine-class"></a>independent_bits_engine – třída

Vygeneruje náhodnou posloupnost čísel se zadaným počtem bitů pomocí opětovného sbalení bitů z hodnot vrácených základním modulem.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Parametry

*Jádra*\
Typ základního modulu.

*W*\
**Velikost slova**. Velikost vygenerovaných čísel v bitech. **Předběžná podmínka**:`0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType*\
Typ výsledku unsigned integer. Možné typy naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="members"></a>Členové

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Další informace o členech motoru naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato třída šablony popisuje *adaptér modulu* , který vytváří hodnoty pomocí opětovného sbalení bitů z hodnot vrácených základním modulem, což *vede k*důsledkům 32bitových hodnot.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<náhodné >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)
