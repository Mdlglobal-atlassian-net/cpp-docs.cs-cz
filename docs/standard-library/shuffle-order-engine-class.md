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
ms.openlocfilehash: bf767c12a19e4ae47c34a8f01e1b1a2f1e028eb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399431"
---
# <a name="shuffleorderengine-class"></a>shuffle_order_engine – třída

Generuje náhodné posloupnosti opětovným uspořádáním hodnot ze základního modulu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t K>
class shuffle_order_engine;
```

### <a name="parameters"></a>Parametry

*Modul*<br/>
Typ základního modulu.

*K*<br/>
**Velikost tabulky**. Počet prvků ve vyrovnávací paměti (tabulka). **Předběžná podmínka**: `0 < K`

## <a name="members"></a>Členové

||||
|-|-|-|
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|

Další informace o členech modul, naleznete v tématu [ \<náhodné >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato třída šablony popisuje *modul adaptér* , která vytváří hodnoty opětovným uspořádáním hodnot vrácených základním modulem. Každý konstruktor vyplní interní tabulku *K* hodnoty vrácené základním modulem a náhodného prvku je vybrán z tabulky, pokud je požadována hodnota.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
