---
title: steady_clock – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- chrono/std::chrono::steady_clock
dev_langs:
- C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba4ebbe6db12fef05bfabd9970d354a7726fcd7d
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="steadyclock-struct"></a>steady_clock – struktura

Představuje `steady` hodiny.

## <a name="syntax"></a>Syntaxe

```cpp
struct steady_clock;
```

## <a name="remarks"></a>Poznámky

V systému Windows steady_clock – zabalí funkci QueryPerformanceCounter.

Hodiny, které je *monotónní* Pokud hodnotu, která je vrácen první volání `now()` je vždy menší než nebo rovna hodnotu, která je vrácena voláním následné `now()`.

Hodiny, které je *konstantní* Pokud je *monotónní* a pokud je doba mezi počtu taktů konstantní.

High_resolution_clock je typdef pro steady_clock –.

## <a name="public-functions"></a>Veřejné funkce

|Funkce|Popis|
|--------------|-----------------|
|Nyní|Vrátí aktuální čas jako hodnotu time_point.|

## <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|`system_clock::is_steady`|Obsahuje `true`. A `steady_clock` je *konstantní*.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<typu chrono >

**Namespace:** std::chrono

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[system_clock – struktura](../standard-library/system-clock-structure.md)<br/>
