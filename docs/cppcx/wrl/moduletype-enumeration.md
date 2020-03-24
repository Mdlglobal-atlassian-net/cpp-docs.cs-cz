---
title: ModuleType – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 8425a15d594f7b8b30027d3576ee86015b656130
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213717"
---
# <a name="moduletype-enumeration"></a>ModuleType – výčet

Určuje, jestli má modul podporovat server v rámci procesu nebo server mimo proces.

## <a name="syntax"></a>Syntaxe

```cpp
enum ModuleType;
```

## <a name="members"></a>Členové

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`InProc`|V procesovém serveru.|
|`OutOfProc`|Mimo procesový Server.|
|`DisableCaching`|Zakáže mechanismus ukládání do mezipaměti v modulu.|
|`InProcDisableCaching`|Kombinace `InProc` a `DisableCaching`|
|`OutOfProcDisableCaching`|Kombinace `OutOfProc` a `DisableCaching`|

## <a name="requirements"></a>Požadavky

**Záhlaví:** modul. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)
