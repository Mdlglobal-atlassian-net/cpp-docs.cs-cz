---
title: Namespace Microsoft::WRL::Wrappers::details | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details
- internal/Microsoft::WRL::Details
- async/Microsoft::WRL::Details
- corewrappers/Microsoft::WRL::Wrappers::Details
- client/Microsoft::WRL::Details
- module/Microsoft::WRL::Details
- event/Microsoft::WRL::Details
dev_langs:
- C++
helpviewer_keywords:
- Details namespace
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3af5add0a934b59cf3027b7beb0ea000a7ae1415
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595704"
---
# <a name="microsoftwrlwrappersdetails-namespace"></a>Microsoft::WRL::Wrappers::Details – obor názvů

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Wrappers::Details;
```

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[SyncLockT – třída](../windows/synclockt-class.md)|Představuje typ, který může trvat exkluzivní nebo sdílené vlastnictví prostředku.|
|[SyncLockWithStatusT – třída](../windows/synclockwithstatust-class.md)|Představuje typ, který může trvat exkluzivní nebo sdílené vlastnictví prostředku.|

### <a name="methods"></a>Metody

|Název|Popis|
|----------|-----------------|
|[CompareStringOrdinal – metoda](../windows/comparestringordinal-method.md)|Porovná dva zadané `HSTRING` objekty a vrátí celé číslo určující jejich relativní umístění v pořadí řazení.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)