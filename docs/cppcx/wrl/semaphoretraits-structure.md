---
title: SemaphoreTraits – struktura
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock method
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
ms.openlocfilehash: e7bd2e5d0993c8e4be7223d98ffb1dbec14cbb74
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403110"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits – struktura

Definuje běžné vlastnosti `Semaphore` objektu.

## <a name="syntax"></a>Syntaxe

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

Název                               | Popis
---------------------------------- | --------------------------------------
[Semaphoretraits::Unlock –](#unlock) | Ovládací prvek verze sdíleného prostředku.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="unlock"></a>Semaphoretraits::Unlock –

Ovládací prvek verze sdíleného prostředku.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Popisovač `Semaphore` objektu.

### <a name="remarks"></a>Poznámky

Pokud neúspěšná, operace odemknutí `Unlock()` generuje chybu, která určuje příčinu selhání.
