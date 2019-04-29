---
title: Microsoft::WRL::Wrappers::HandleTraits – obor názvů
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: 6ed8156b6a0e71d40d1579fc9a33912f698e1773
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391969"
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
|[CriticalSectionTraits – struktura](criticalsectiontraits-structure.md)|Se specializuje `CriticalSection` objektu pro podporu neplatný kritický oddíl nebo funkci uvolnění kritický oddíl.|
|[EventTraits – struktura](eventtraits-structure.md)|Definuje vlastnosti `Event` popisovač třídy.|
|[FileHandleTraits – struktura](filehandletraits-structure.md)|Definuje vlastnosti popisovače souboru.|
|[HANDLENullTraits – struktura](handlenulltraits-structure.md)|Definuje běžné vlastnosti neinicializovaný popisovač.|
|[HANDLETraits – struktura](handletraits-structure.md)|Definuje běžné vlastnosti popisovač.|
|[MutexTraits – struktura](mutextraits-structure.md)|Definuje běžné vlastnosti [Mutex](mutex-class.md) třídy.|
|[SemaphoreTraits – struktura](semaphoretraits-structure.md)|Definuje běžné vlastnosti objektu pro spolupráci.|
|[SRWLockExclusiveTraits – struktura](srwlockexclusivetraits-structure.md)|Popisuje běžné vlastnosti `SRWLock` třídy ve výhradním režimu zámku.|
|[SRWLockSharedTraits – struktura](srwlocksharedtraits-structure.md)|Popisuje běžné vlastnosti `SRWLock` třídy ve sdíleném režimu zámku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Viz také:

[Microsoft::WRL::Wrappers – obor názvů](microsoft-wrl-wrappers-namespace.md)