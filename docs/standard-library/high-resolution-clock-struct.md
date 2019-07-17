---
title: Struktura jsme high_resolution_clock | Dokumentace Microsoftu
ms.custom: ''
ms.date: 05/22/2018
ms.technology: cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::high_resolution_clock
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b00b20e7cea4fa24b37ad33d5536eb9844e6953
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268090"
---
# <a name="steadyclock-struct"></a>steady_clock – struktura

Představuje *high_resolution* hodiny.

## <a name="syntax"></a>Syntaxe

```cpp
class high_resolution_clock
```

## <a name="members"></a>Členové

### <a name="typedefs"></a>Typedefs

|Name|Popis|
|----------|-----------------|
|`duration`|Synonymum pro `nanoseconds`definované v \<chrono >.|
|`period`|Synonymum pro `nano`definované v \<poměr >.|
|`rep`|Synonymum pro **dlouhé** **dlouhé**, typ, který reprezentuje počet taktů v uzavřeném vytváření instancí `duration`.|
|`time_point`|Synonymum pro `chrono::time_point<high_resolution_clock>`.|

## <a name="functions"></a>Funkce

|||
|-|-|
|`now`|Vrátí aktuální čas jako `time_point` hodnotu.|

## <a name="constants"></a>Konstanty

|Name|Popis|
|----------|-----------------|
|`is_steady`|Obsahuje **true**. A `high_resolution_clock` je *stabilní*.|
