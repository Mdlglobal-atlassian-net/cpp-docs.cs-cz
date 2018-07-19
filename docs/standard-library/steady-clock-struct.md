---
title: steady_clock – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: 53f4deb0bfe9439011f75cd22d0d52b74dae9c1f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959722"
---
# <a name="steadyclock-struct"></a>steady_clock – struktura

Představuje *stabilní* hodiny.

## <a name="syntax"></a>Syntaxe

```cpp
struct steady_clock;
```

## <a name="remarks"></a>Poznámky

Na Windows `steady_clock` zabalí `QueryPerformanceCounter` funkce.

Hodiny jsou *monotónní* Pokud hodnotu, která je vrácena prvním voláním do `now` je vždy menší než hodnota, která je vrácena následujícím voláním do `now`. Hodiny jsou *stabilní* jde *monotónní* a je-li doba mezi cykly hodin konstantní.

`high_resolution_clock` Definice TypeDef pro `steady_clock`.

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`steady_clock::duration`|Synonymum pro `nanoseconds`definované v \<chrono >.|
|`steady_clock::period`|Synonymum pro `nano`definované v \<poměr >.|
|`steady_clock::rep`|Synonymum pro **dlouhé** **dlouhé**, typ, který reprezentuje počet taktů v uzavřeném vytváření instancí `duration`.|
|`steady_clock::time_point`|Synonymum pro `chrono::time_point<steady_clock>`.|

## <a name="public-functions"></a>Veřejné funkce

|Funkce|Popis|
|--------------|-----------------|
|`now`|Vrátí aktuální čas jako `time_point` hodnotu.|

## <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|`steady_clock::is_steady`|Obsahuje **true**. A `steady_clock` je *stabilní*.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<chrono >

**Namespace:** std::chrono

## <a name="see-also"></a>Viz také:

- [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock – struktura](../standard-library/system-clock-structure.md)
