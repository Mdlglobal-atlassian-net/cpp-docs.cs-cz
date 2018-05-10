---
title: discard_block_engine – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::discard_block_engine
dev_langs:
- C++
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b814f64f340577508add6bf3c0f85ffac0786db7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="discardblockengine-class"></a>discard_block_engine – třída

Generuje náhodné pořadí zrušením hodnot vrácených jeho základní modul.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Parametry

`Engine` Typ základního modulu.

`P` **Velikost bloku**. Počet hodnot v jednotlivých bloků.

`R` **Použít bloku**. Počet hodnot v jednotlivých bloků, které se používají. Ostatní jsou zahozeny ( `P`  -  `R`). **Předběžnou**: `0 < R ≤ P`

## <a name="members"></a>Členové

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

Další informace o modulu členy najdete v tématu [ \<náhodných >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato třída šablony Popisuje modul adaptér, který produkuje hodnoty zrušením některé z hodnot vrácených jeho základní modul.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodných >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[\<náhodné >](../standard-library/random.md)<br/>
