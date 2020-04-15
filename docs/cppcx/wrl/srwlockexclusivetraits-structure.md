---
title: SRWLockExclusiveTraits – struktura
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock method
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
ms.openlocfilehash: eb7b30915d6061e8470601df33fecec310d1bbca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374312"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits – struktura

Popisuje společné charakteristiky `SRWLock` třídy v režimu výhradní zámek.

## <a name="syntax"></a>Syntaxe

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)   | Popis
------ | --------------------------------------------------------------------------
`Type` | Synonymum pro ukazatel na třídu [SRWLOCK.](srwlock-class.md)

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                        | Popis
----------------------------------------------------------- | --------------------------------------------------------------------
[SRWLockExclusiveTraits::GetInvalidValue](#getinvalidvalue) | Načte `SRWLockExclusiveTraits` objekt, který je vždy neplatný.
[SRWLockExclusiveTraits::Odemknout](#unlock)                   | Uvolní výhradní řízení zadaného `SRWLock` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SRWLockExclusiveTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky::HandleTraits

## <a name="srwlockexclusivetraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>SRWLockExclusiveTraits::GetInvalidValue

Načte `SRWLockExclusiveTraits` objekt, který je vždy neplatný.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Návratová hodnota

Prázdný `SRWLockExclusiveTraits` objekt.

## <a name="srwlockexclusivetraitsunlock"></a><a name="unlock"></a>SRWLockExclusiveTraits::Odemknout

Uvolní výhradní řízení zadaného `SRWLock` objektu.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parametry

*srwlock*<br/>
Popisovač `SRWLock` objektu.
