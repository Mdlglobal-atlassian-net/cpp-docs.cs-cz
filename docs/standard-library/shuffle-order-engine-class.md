---
title: shuffle_order_engine – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::shuffle_order_engine
- random/std::shuffle_order_engine::base
- random/std::shuffle_order_engine::discard
- random/std::shuffle_order_engine::operator()
- random/std::shuffle_order_engine::base_type
- random/std::shuffle_order_engine::seed
helpviewer_keywords:
- std::shuffle_order_engine [C++]
- std::shuffle_order_engine [C++], base
- std::shuffle_order_engine [C++], discard
- std::shuffle_order_engine [C++], base_type
- std::shuffle_order_engine [C++], seed
ms.assetid: 0bcd1fb0-44d7-4e59-bb1b-4a9b673a960d
ms.openlocfilehash: d72cfaae2e7f6768a68439fbc30aa5ab0d38f270
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686420"
---
# <a name="shuffle_order_engine-class"></a>shuffle_order_engine – třída

Vygeneruje náhodnou sekvenci změnou pořadí hodnot vrácených z jeho základního modulu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t K>
class shuffle_order_engine;
```

### <a name="parameters"></a>Parametry

@No__t_1 *modulu*
Typ základního modulu.

*K* \
**Velikost tabulky** Počet prvků ve vyrovnávací paměti (tabulce). **Předběžná podmínka**: `0 < K`

## <a name="members"></a>Členové

||||
|-|-|-|
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|

Další informace o členech motoru naleznete v tématu [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato šablona třídy popisuje *adaptér modulu* , který vytváří hodnoty změnou pořadí hodnot vrácených základním modulem. Každý konstruktor vyplní interní tabulku hodnotami *K* , které vrátil základní modul, a z tabulky se vybere náhodný prvek, když je požadovaná hodnota.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<random >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<random >](../standard-library/random.md)
