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
ms.openlocfilehash: 4cbd3f367bc57c2eedf672422a458b67b1908fc0
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334760"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags – struktura

Obsahuje typ pro instanci [RuntimeClass](runtimeclass-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Parametry

*příznaky*<br/>
A [runtimeclasstype – výčet](runtimeclasstype-enumeration.md) hodnotu.

## <a name="members"></a>Členové

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[RuntimeClassFlags::value – konstanta](#value-constant)|Obsahuje [runtimeclasstype – výčet](runtimeclasstype-enumeration.md) hodnotu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`RuntimeClassFlags`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="value-constant"></a>RuntimeClassFlags::value Constant

Pole obsahující [runtimeclasstype – výčet](runtimeclasstype-enumeration.md) hodnotu.

```cpp
static const unsigned int value = flags;
```
