---
title: ModuleType – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 937649eada481f7c45359fa0816266f62dc03875
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334717"
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

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)