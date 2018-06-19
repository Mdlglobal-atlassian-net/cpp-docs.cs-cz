---
title: identity – struktura | Microsoft Docs
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
ms.openlocfilehash: 83180020c20f78c16af0b1b33bada91936b6af9b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844403"
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
