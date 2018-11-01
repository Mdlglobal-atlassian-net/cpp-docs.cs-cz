---
title: ModuleType – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: d822d214d9bad564286cd2c7494c9f480abdcf00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524745"
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