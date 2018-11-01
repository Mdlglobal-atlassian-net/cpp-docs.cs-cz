---
title: Microsoft::WRL::Wrappers::HandleTraits – obor názvů
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: e558838ca9cd06fb5529f689d45a920db151d272
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643245"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits – obor názvů

Popisuje charakteristiky běžné typy prostředků pro popisovač.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Wrappers::HandleTraits;
```

## <a name="members"></a>Členové

### <a name="structures"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[CriticalSectionTraits – struktura](../windows/criticalsectiontraits-structure.md)|Se specializuje `CriticalSection` objektu pro podporu neplatný kritický oddíl nebo funkci uvolnění kritický oddíl.|
|[EventTraits – struktura](../windows/eventtraits-structure.md)|Definuje vlastnosti `Event` popisovač třídy.|
|[FileHandleTraits – struktura](../windows/filehandletraits-structure.md)|Definuje vlastnosti popisovače souboru.|
|[HANDLENullTraits – struktura](../windows/handlenulltraits-structure.md)|Definuje běžné vlastnosti neinicializovaný popisovač.|
|[HANDLETraits – struktura](../windows/handletraits-structure.md)|Definuje běžné vlastnosti popisovač.|
|[MutexTraits – struktura](../windows/mutextraits-structure.md)|Definuje běžné vlastnosti [Mutex](../windows/mutex-class1.md) třídy.|
|[SemaphoreTraits – struktura](../windows/semaphoretraits-structure.md)|Definuje běžné vlastnosti objektu pro spolupráci.|
|[SRWLockExclusiveTraits – struktura](../windows/srwlockexclusivetraits-structure.md)|Popisuje běžné vlastnosti `SRWLock` třídy ve výhradním režimu zámku.|
|[SRWLockSharedTraits – struktura](../windows/srwlocksharedtraits-structure.md)|Popisuje běžné vlastnosti `SRWLock` třídy ve sdíleném režimu zámku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)