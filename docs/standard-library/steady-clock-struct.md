---
title: steady_clock – struktura | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
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
ms.openlocfilehash: 5445379597c4fefcd657303a05c33b6509d54d2e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569895"
---
# <a name="steadyclock-struct"></a>steady_clock – struktura

Představuje *konstantní* hodiny.

## <a name="syntax"></a>Syntaxe

```cpp
struct steady_clock;
```

## <a name="remarks"></a>Poznámky

V systému Windows `steady_clock` zabalí `QueryPerformanceCounter` funkce.

Hodiny, které je *monotónní* Pokud hodnotu, která je vrácen první volání `now` je vždy menší než nebo rovna hodnotu, která je vrácena voláním následné `now`. Hodiny, které je *konstantní* Pokud je *monotónní* a pokud je doba mezi počtu taktů konstantní.

`high_resolution_clock` je typedef pro `steady_clock`.

### <a name="public-typedefs"></a>Veřejné – definice TypeDef

|Název|Popis|
|----------|-----------------|
|`steady_clock::duration`|Synonymum pro `nanoseconds`, definované v \<typu chrono >.|
|`steady_clock::period`|Synonymum pro `nano`, definované v \<poměr >.|
|`steady_clock::rep`|Synonymum pro **dlouho** **dlouho**, typ, který se používá k reprezentování počet v omezením instance počtu taktů `duration`.|
|`steady_clock::time_point`|Synonymum pro `chrono::time_point<steady_clock>`.|

## <a name="public-functions"></a>Veřejné funkce

|Funkce|Popis|
|--------------|-----------------|
|`now`|Vrátí aktuální čas jako `time_point` hodnotu.|

## <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|`steady_clock::is_steady`|Obsahuje `true`. A `steady_clock` je *konstantní*.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<typu chrono >

**Namespace:** std::chrono

## <a name="see-also"></a>Viz také:

- [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock – struktura](../standard-library/system-clock-structure.md)
