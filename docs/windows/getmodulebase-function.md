---
title: Getmodulebase – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
dev_langs:
- C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: afa76ad23c509689dd693bb0f3e13dbb7adb4d54
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075447"
---
# <a name="getmodulebase-function"></a>GetModuleBase – funkce
Načte [ModuleBase](../windows/modulebase-class.md) ukazatel, který umožňuje zvyšování a dekrementace počet odkazů [RuntimeClass](../windows/runtimeclass-class.md) objektu.

## <a name="syntax"></a>Syntaxe

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel `ModuleBase` objektu.

## <a name="remarks"></a>Poznámky

Tato funkce se používá interně ke addref() vrátí odkaz na objekt.

Tuto funkci můžete použít k řízení počty odkazů voláním [modulebase::incrementobjectcount –](../windows/modulebase-incrementobjectcount-method.md) a [modulebase::decrementobjectcount –](../windows/modulebase-decrementobjectcount-method.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)