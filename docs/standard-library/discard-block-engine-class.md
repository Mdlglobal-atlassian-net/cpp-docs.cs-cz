---
title: discard_block_engine – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::discard_block_engine
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
ms.openlocfilehash: a0df754f53b52c134b9eb1126f90882ceaaf1e2f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676821"
---
# <a name="discardblockengine-class"></a>discard_block_engine – třída

Generuje náhodné posloupnosti vypuštěním hodnoty vrácené základním modulem.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Parametry

*Modul*<br/>
Typ základního modulu.

*P*<br/>
**Velikost bloku**. Počet hodnot v každém bloku.

*R*<br/>
**Používá blok**. Počet hodnot v každém bloku, které se používají. Ostatní jsou zahozeny (`P` - `R`). **Předběžná podmínka**: `0 < R ≤ P`

## <a name="members"></a>Členové

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

Další informace o členech modul, naleznete v tématu [ \<náhodné >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato třída šablony popisuje adaptér modul, který vytváří hodnoty vypuštěním některé z hodnot vrácených základním modulem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
