---
title: ModuleType – výčet | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
dev_langs:
- C++
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe8d41aded38db7cde5316e04cfa1689845aa4e7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595469"
---
# <a name="moduletype-enumeration"></a>ModuleType – výčet

Určuje, zda modul by měl podporovat v procesový server nebo server mimo proces.

## <a name="syntax"></a>Syntaxe

```cpp
enum ModuleType;
```

## <a name="members"></a>Členové

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`InProc`|V procesový server.|
|`OutOfProc`|Server služby mimo proces.|
|`DisableCaching`|Zakázání mechanismu ukládání do mezipaměti na modul.|
|`InProcDisableCaching`|Kombinace `InProc` a `DisableCaching`.|
|`OutOfProcDisableCaching`|Kombinace `OutOfProc` a `DisableCaching`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)