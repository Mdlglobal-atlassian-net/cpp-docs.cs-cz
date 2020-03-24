---
title: Microsoft::WRL::Wrappers::HandleTraits – obor názvů
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: b19cc426fc7c1b4fc6ec0638730d59998f8c108a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213730"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits – obor názvů

Popisuje charakteristiky běžných typů prostředků založených na popisovačích.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Wrappers::HandleTraits;
```

## <a name="members"></a>Členové

### <a name="structures"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[CriticalSectionTraits – struktura](criticalsectiontraits-structure.md)|Specializuje objekt `CriticalSection` na podporu buď neplatného kritického oddílu, nebo funkce pro vydání kritického oddílu.|
|[EventTraits – struktura](eventtraits-structure.md)|Definuje charakteristiky popisovače třídy `Event`.|
|[FileHandleTraits – struktura](filehandletraits-structure.md)|Definuje charakteristiky popisovače souboru.|
|[HANDLENullTraits – struktura](handlenulltraits-structure.md)|Definuje běžné charakteristiky neinicializovaného popisovače.|
|[HANDLETraits – struktura](handletraits-structure.md)|Definuje společné charakteristiky popisovače.|
|[MutexTraits – struktura](mutextraits-structure.md)|Definuje společné charakteristiky třídy [mutex](mutex-class.md) .|
|[SemaphoreTraits – struktura](semaphoretraits-structure.md)|Definuje společné vlastnosti objektu semaforu.|
|[SRWLockExclusiveTraits – struktura](srwlockexclusivetraits-structure.md)|Popisuje běžné charakteristiky třídy `SRWLock` ve výhradním režimu zámku.|
|[SRWLockSharedTraits – struktura](srwlocksharedtraits-structure.md)|Popisuje běžné charakteristiky třídy `SRWLock` ve sdíleném režimu zámku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers. h

**Obor názvů:** Microsoft:: WRL:: Wrappers

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers – obor názvů](microsoft-wrl-wrappers-namespace.md)
