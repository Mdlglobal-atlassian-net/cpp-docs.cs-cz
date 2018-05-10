---
title: steady_clock – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::steady_clock
dev_langs:
- C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1dbfac1eb8c67c5306bded6e6fd9ee8dacf54b0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
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
