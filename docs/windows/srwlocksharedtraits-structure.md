---
title: Srwlocksharedtraits – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock method
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5cfebfd1a6ccb1f243b534c9693a4402de574f17
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48233670"
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
`Type` | Synonymum pro ukazatel [SRWLOCK](../windows/srwlock-class.md) třídy.

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
