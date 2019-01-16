---
title: Microsoft::WRL::Wrappers – obor názvů
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: 953318e09c4c0d00748f2b6189615dbd66677a96
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334712"
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
|[CriticalSection – třída](criticalsection-class.md)|Představuje objekt kritický oddíl.|
|[Event – třída (WRL)](event-class-wrl.md)|Představuje událost.|
|[HandleT – třída](handlet-class.md)|Reprezentuje popisovač objektu.|
|[HString – třída](hstring-class.md)|Poskytuje podporu pro práci s popisovači HSTRING.|
|[HStringReference – třída](hstringreference-class.md)|Představuje HSTRING, který je vytvořený z existujícího řetězce.|
|[Mutex – třída](mutex-class.md)|Představuje objekt synchronizace, který řídí výhradně sdíleného prostředku.|
|[RoInitializeWrapper – třída](roinitializewrapper-class.md)|Inicializuje modul Windows Runtime.|
|[Semaphore – třída](semaphore-class.md)|Představuje objekt synchronizace, který řídí sdíleného prostředku, který podporuje omezený počet uživatelů.|
|[SRWLock – třída](srwlock-class.md)|Představuje zámek tenký čtení/zápis.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)