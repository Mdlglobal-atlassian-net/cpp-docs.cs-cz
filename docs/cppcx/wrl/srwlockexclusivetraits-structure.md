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
ms.openlocfilehash: 25249b8823b8c182133e85aa4cd07d38f5874cf2
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786549"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits – struktura

Popisuje běžné vlastnosti `SRWLock` třídy ve výhradním režimu zámku.

## <a name="syntax"></a>Syntaxe

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Název   | Popis
------ | --------------------------------------------------------------------------
`Type` | Synonymum pro ukazatel [SRWLOCK](srwlock-class.md) třídy.

### <a name="public-methods"></a>Veřejné metody

Název                                                        | Popis
----------------------------------------------------------- | --------------------------------------------------------------------
[Srwlockexclusivetraits::getinvalidvalue –](#getinvalidvalue) | Načte `SRWLockExclusiveTraits` objekt, který je pořád platný.
[Srwlockexclusivetraits::Unlock –](#unlock)                   | Uvolní výhradní kontrolu zadaného `SRWLock` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SRWLockExclusiveTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>Srwlockexclusivetraits::getinvalidvalue –

Načte `SRWLockExclusiveTraits` objekt, který je pořád platný.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Návratová hodnota

Prázdná `SRWLockExclusiveTraits` objektu.

## <a name="unlock"></a>Srwlockexclusivetraits::Unlock –

Uvolní výhradní kontrolu zadaného `SRWLock` objektu.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parametry

*srwlock*<br/>
Popisovač `SRWLock` objektu.
