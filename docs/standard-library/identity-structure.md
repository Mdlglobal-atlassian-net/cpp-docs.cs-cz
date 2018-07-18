---
title: identity – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- utility/std::identity
dev_langs:
- C++
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f065f7c00d3853d00c1063cd5b2838ec6d1d27b4
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38952994"
---
# <a name="identity-structure"></a>identity – struktura

Struktura, která obsahuje definici typu jako parametr šablony.

## <a name="syntax"></a>Syntaxe

```cpp
struct identity {
   typedef Type type;
   Type operator()(const Type& left) const;
   };
```
### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Hodnota k identifikaci.|

## <a name="remarks"></a>Poznámky

Třída obsahuje definice veřejného typu `type`, což je stejná jako parametr šablony typu. Používá se ve spojení s funkcí šablony [vpřed](../standard-library/utility-functions.md#forward) a ujistěte se, že parametr funkce mají požadovaného typu.

Z důvodu kompatibility se starším kódem, třída také definuje funkci identity `operator()` který vrátí svůj argument *levé*.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<nástroje >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[\<Nástroje >](../standard-library/utility.md)<br/>
