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
ms.openlocfilehash: 0dc43d4b9c16145ed7a5abe03cddb598c59b1e94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374290"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits – struktura

Popisuje běžné charakteristiky `SRWLock` třídy v režimu sdíleného zámku.

## <a name="syntax"></a>Syntaxe

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)   | Popis
------ | --------------------------------------------------------------------------
`Type` | Synonymum pro ukazatel na třídu [SRWLOCK.](srwlock-class.md)

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                     | Popis
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLockSharedTraits::GetInvalidValue](#getinvalidvalue) | Načte `SRWLockSharedTraits` objekt, který je vždy neplatný.
[SRWLockSharedTraits::Odemknout](#unlock)                   | Uvolní výhradní řízení zadaného `SRWLock` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SRWLockSharedTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky::HandleTraits

## <a name="srwlocksharedtraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>SRWLockSharedTraits::GetInvalidValue

Načte `SRWLockSharedTraits` objekt, který je vždy neplatný.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Návratová hodnota

Úchyt `SRWLockSharedTraits` k objektu.

## <a name="srwlocksharedtraitsunlock"></a><a name="unlock"></a>SRWLockSharedTraits::Odemknout

Uvolní výhradní řízení zadaného `SRWLock` objektu.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parametry

*srwlock*<br/>
Úchyt `SRWLock` k objektu.
