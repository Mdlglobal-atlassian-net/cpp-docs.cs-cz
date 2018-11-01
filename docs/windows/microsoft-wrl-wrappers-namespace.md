---
title: Microsoft::WRL::Wrappers – obor názvů
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: eac85d10351a141ce561da4272d033644128608f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535483"
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