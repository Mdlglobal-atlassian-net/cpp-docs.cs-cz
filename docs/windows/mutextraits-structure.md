---
title: MutexTraits – struktura
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock method
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
ms.openlocfilehash: 84bfac08a944928ff91a7734cdbaccbe4d351e16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650746"
---
# <a name="mutextraits-structure"></a>MutexTraits – struktura

Definuje běžné vlastnosti [Mutex](../windows/mutex-class1.md) třídy.

## <a name="syntax"></a>Syntaxe

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

Název                           | Popis
------------------------------ | ------------------------------------------------
[Mutextraits::Unlock –](#unlock) | Uvolní výhradní kontrolu nad sdíleného prostředku.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="unlock"></a>Mutextraits::Unlock – metoda

Uvolní výhradní kontrolu nad sdíleného prostředku.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Popisovač objektu mutex.
