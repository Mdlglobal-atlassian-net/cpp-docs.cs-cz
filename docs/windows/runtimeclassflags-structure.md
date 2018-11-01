---
title: RuntimeClassFlags – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
ms.openlocfilehash: 74ae72dc87d45abba04d15303ed2ec92b18f8c28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668530"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags – struktura

Obsahuje typ pro instanci [RuntimeClass](../windows/runtimeclass-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Parametry

*příznaky*<br/>
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
