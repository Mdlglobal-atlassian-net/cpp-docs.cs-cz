---
title: Microsoft::WRL::Wrappers – obor názvů
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: ece26b3f9928d44a593de830cf8a25c57e4c2d89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213743"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers – obor názvů

Definuje typy obálky získávání prostředků je inicializace (RAII), které zjednodušují správu životního cyklu objektů, řetězců a popisovačů.

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
|[CriticalSection – třída](criticalsection-class.md)|Představuje objekt kritického oddílu.|
|[Event – třída (WRL)](event-class-wrl.md)|Představuje událost.|
|[HandleT – třída](handlet-class.md)|Představuje popisovač objektu.|
|[HString – třída](hstring-class.md)|Poskytuje podporu pro manipulaci s HSTRING popisovači.|
|[HStringReference – třída](hstringreference-class.md)|Představuje HSTRING, který je vytvořen z existujícího řetězce.|
|[Mutex – třída](mutex-class.md)|Představuje synchronizační objekt, který ovládá výhradně sdílený prostředek.|
|[RoInitializeWrapper – třída](roinitializewrapper-class.md)|Inicializuje prostředí Windows Runtime.|
|[Semaphore – třída](semaphore-class.md)|Představuje synchronizační objekt, který řídí sdílený prostředek, který může podporovat omezený počet uživatelů.|
|[SRWLock – třída](srwlock-class.md)|Představuje zámek pro čtení/zápis na tenkém zařízení.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers. h

**Obor názvů:** Microsoft:: WRL:: Wrappers

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)
