---
title: ModuleType – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 3c7486cbc761975dd133f229f23dcf0b70e7e3ac
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039149"
---
# <a name="moduletype-enumeration"></a>ModuleType – výčet

Určuje, zda modul by měl podporovat v procesový server nebo server mimo proces.

## <a name="syntax"></a>Syntaxe

```cpp
enum ModuleType;
```

## <a name="members"></a>Členové

### <a name="values"></a>Hodnoty

|Name|Popis|
|----------|-----------------|
|`InProc`|V procesový server.|
|`OutOfProc`|Server služby mimo proces.|
|`DisableCaching`|Zakázání mechanismu ukládání do mezipaměti na modul.|
|`InProcDisableCaching`|Kombinace `InProc` a `DisableCaching`.|
|`OutOfProcDisableCaching`|Kombinace `OutOfProc` a `DisableCaching`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také:

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)