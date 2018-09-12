---
title: Runtimeclassflags – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/07/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6c3cb141576598aa39c718316048900622c4df41
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691455"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags – struktura

Obsahuje typ pro instanci [RuntimeClass](../windows/runtimeclass-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <
   unsigned int flags
>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Parametry

*příznaky*  
A [runtimeclasstype – výčet](../windows/runtimeclasstype-enumeration.md) hodnotu.

## <a name="members"></a>Členové

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[RuntimeClassFlags::value – konstanta](#value-constant)|Obsahuje [runtimeclasstype – výčet](../windows/runtimeclasstype-enumeration.md) hodnotu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`RuntimeClassFlags`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="value-constant"></a>RuntimeClassFlags::value – konstanta

Pole obsahující [runtimeclasstype – výčet](../windows/runtimeclasstype-enumeration.md) hodnotu.
  
```cpp
static const unsigned int value = flags;
```
