---
title: Srwlockexclusivetraits – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock method
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7737c802634b618b9ea363c231a44d9381ad30ae
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235162"
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
`Type` | Synonymum pro ukazatel [SRWLOCK](../windows/srwlock-class.md) třídy.

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
