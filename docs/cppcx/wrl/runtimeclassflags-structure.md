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
ms.openlocfilehash: 9fed5bb31b077288495a78aefcbd8401b3520bb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367216"
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
Hodnota [výčtu typu RuntimeClassType.](runtimeclasstype-enumeration.md)

## <a name="members"></a>Členové

### <a name="public-constants"></a>Veřejné konstanty

|Name (Název)|Popis|
|----------|-----------------|
|[RuntimeClassFlags::value – konstanta](#value-constant)|Obsahuje hodnotu [výčtu typu RuntimeClassType.](runtimeclasstype-enumeration.md)|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`RuntimeClassFlags`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Obor názvů:** Microsoft::WRL

## <a name="runtimeclassflagsvalue-constant"></a><a name="value-constant"></a>RuntimeClassFlags::hodnota Konstanta

Pole, které obsahuje hodnotu [výčtu typu RuntimeClassType.](runtimeclasstype-enumeration.md)

```cpp
static const unsigned int value = flags;
```
