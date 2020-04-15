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
ms.openlocfilehash: 11719576c9fc7b23f4cd318ee1b3ed9ca3f5edaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360729"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits – struktura

Definuje společné charakteristiky `Semaphore` objektu.

## <a name="syntax"></a>Syntaxe

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

Name (Název)                               | Popis
---------------------------------- | --------------------------------------
[Semafortraits::Odemknout](#unlock) | Uvolní řízení sdíleného prostředku.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky::HandleTraits

## <a name="semaphoretraitsunlock"></a><a name="unlock"></a>Semafortraits::Odemknout

Uvolní řízení sdíleného prostředku.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Popisovač `Semaphore` objektu.

### <a name="remarks"></a>Poznámky

Pokud je operace odemknutí neúspěšná, `Unlock()` vydává chybu, která označuje příčinu selhání.
