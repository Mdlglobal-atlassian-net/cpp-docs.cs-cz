---
title: SRWLockSharedTraits – struktura
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock method
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
ms.openlocfilehash: af567fd333854519df4543ad24084e52cda4d96e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383279"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits – struktura

Popisuje běžné vlastnosti `SRWLock` třídy ve sdíleném režimu zámku.

## <a name="syntax"></a>Syntaxe

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Název   | Popis
------ | --------------------------------------------------------------------------
`Type` | Synonymum pro ukazatel [SRWLOCK](srwlock-class.md) třídy.

### <a name="public-methods"></a>Veřejné metody

Název                                                     | Popis
-------------------------------------------------------- | -----------------------------------------------------------------
[Srwlocksharedtraits::getinvalidvalue –](#getinvalidvalue) | Načte `SRWLockSharedTraits` objekt, který je pořád platný.
[Srwlocksharedtraits::Unlock –](#unlock)                   | Uvolní výhradní kontrolu zadaného `SRWLock` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SRWLockSharedTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>Srwlocksharedtraits::getinvalidvalue –

Načte `SRWLockSharedTraits` objekt, který je pořád platný.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač `SRWLockSharedTraits` objektu.

## <a name="unlock"></a>Srwlocksharedtraits::Unlock –

Uvolní výhradní kontrolu zadaného `SRWLock` objektu.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parametry

*srwlock*<br/>
Popisovač `SRWLock` objektu.
