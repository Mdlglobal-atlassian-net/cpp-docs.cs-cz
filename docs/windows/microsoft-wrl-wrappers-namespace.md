---
title: 'Microsoft::WRL:: wrappers – Namespace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
dev_langs:
- C++
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2b1a63494e06ce3117e7e8fccd1d0cbca8cdb4d0
ms.sourcegitcommit: d1527eb2d50156bf923f2a32ec3af9efc7fc4304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48250338"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers – obor názvů

Definuje typy prostředků pořízení je inicializace (RAII) obálky, které zjednodušují správu životnosti objektů, řetězce a obslužné rutiny.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Wrappers;
```

## <a name="members"></a>Členové

### <a name="typedefs"></a>Typedefs

|Název|Popis|
|----------|-----------------|
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[CriticalSection – třída](../windows/criticalsection-class.md)|Představuje objekt kritický oddíl.|
|[Event – třída (WRL)](../windows/event-class-wrl.md)|Představuje událost.|
|[HandleT – třída](../windows/handlet-class.md)|Reprezentuje popisovač objektu.|
|[HString – třída](../windows/hstring-class.md)|Poskytuje podporu pro práci s popisovači HSTRING.|
|[HStringReference – třída](../windows/hstringreference-class.md)|Představuje HSTRING, který je vytvořený z existujícího řetězce.|
|[Mutex – třída](../windows/mutex-class.md)|Představuje objekt synchronizace, který řídí výhradně sdíleného prostředku.|
|[RoInitializeWrapper – třída](../windows/roinitializewrapper-class.md)|Inicializuje modul Windows Runtime.|
|[Semaphore – třída](../windows/semaphore-class.md)|Představuje objekt synchronizace, který řídí sdíleného prostředku, který podporuje omezený počet uživatelů.|
|[SRWLock – třída](../windows/srwlock-class.md)|Představuje zámek tenký čtení/zápis.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)