---
title: discard_block_engine – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::discard_block_engine
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
ms.openlocfilehash: eb00945084affb2be9299953e5ca9352c56d3b32
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688096"
---
# <a name="discard_block_engine-class"></a>discard_block_engine – třída

Vygeneruje náhodnou sekvenci vyhozením hodnot vrácených základním modulem.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Parametry

@No__t_1 *modulu*
Typ základního modulu.

*P* \
**Velikost bloku** Počet hodnot v každém bloku.

@No__t_1 *R*
**Použitý blok**. Počet hodnot v každém použitém bloku. Zbývající jsou zahozeny (`P`  -  `R`). **Předběžná podmínka**: `0 < R ≤ P`

## <a name="members"></a>Členové

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

Další informace o členech motoru naleznete v tématu [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato šablona třídy popisuje adaptér modulu, který vytváří hodnoty tím, že zahodí některé hodnoty vrácené jeho základním modulem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<random >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<random >](../standard-library/random.md)
