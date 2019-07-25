---
title: discard_block_engine – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::discard_block_engine
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
ms.openlocfilehash: 76a78a2f47bd160c6b2b981b1ccdda2ef3a90575
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454399"
---
# <a name="discardblockengine-class"></a>discard_block_engine – třída

Vygeneruje náhodnou sekvenci vyhozením hodnot vrácených základním modulem.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Parametry

*Jádra*\
Typ základního modulu.

*TRUB*\
**Velikost bloku** Počet hodnot v každém bloku.

*R*\
**Použitý blok**. Počet hodnot v každém použitém bloku. Zbývající jsou zahozena`P`( - `R`). **Předběžná podmínka**:`0 < R ≤ P`

## <a name="members"></a>Členové

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

Další informace o členech motoru naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato třída šablony popisuje adaptér modulu, který vytváří hodnoty tím, že zahodí některé hodnoty vrácené jeho základním modulem.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<náhodné >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)
