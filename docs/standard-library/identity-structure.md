---
title: identity – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- utility/std::identity
dev_langs:
- C++
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 991333f279053d19ec27fda86ea0bf769371fd90
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="identity-structure"></a>identity – struktura

Struktura, která poskytuje definice typu jako parametr šablony.

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
|`left`|Hodnota k identifikaci.|

## <a name="remarks"></a>Poznámky

Třída obsahuje definici veřejné typu `type`, což je stejný jako parametr šablony typu. Se používá ve spojení s funkce šablony [dál](../standard-library/utility-functions.md#forward) zajistit, že parametr funkce není požadovaný typ.

K zajištění kompatibility se starším kódu, třída také definuje funkci identity `operator()` která její argument vrací `left`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<nástroj >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[\<nástroj >](../standard-library/utility.md)<br/>
