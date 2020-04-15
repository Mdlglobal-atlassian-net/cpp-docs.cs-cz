---
title: Třída SRWLock
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock_
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::~SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
helpviewer_keywords:
- Microsoft::WRL::Wrappers::SRWLock class
- Microsoft::WRL::Wrappers::SRWLock::LockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::LockShared method
- Microsoft::WRL::Wrappers::SRWLock::SRWLock, constructor
- Microsoft::WRL::Wrappers::SRWLock::SRWLock_ data member
- Microsoft::WRL::Wrappers::SRWLock::~SRWLock, destructor
- Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::TryLockShared method
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
ms.openlocfilehash: e305ad54e30455ce7c25f356c454791da0783591
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377267"
---
# <a name="srwlock-class"></a>Třída SRWLock

Představuje tenký zámek čtečky/zapisovače.

## <a name="syntax"></a>Syntaxe

```cpp
class SRWLock;
```

## <a name="remarks"></a>Poznámky

Tenký zámek čtečky/zapisovače se používá k synchronizaci přístupu mezi vlákny k objektu nebo prostředku. Další informace naleznete [v tématu Synchronizační funkce](/windows/win32/Sync/synchronization-functions).

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)                | Popis
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | Synonymum `SRWLock` pro objekt, který je získán ve výhradním režimu.
`SyncLockShared`    | Synonymum `SRWLock` pro objekt, který je získán ve sdíleném režimu.

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                     | Popis
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | Inicializuje novou instanci třídy. `SRWLock`
[SRWLock:~SRWLock](#tilde-srwlock)      | Deinitializes instance třídy. `SRWLock`

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                           | Popis
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | Získá objekt `SRWLock` ve výhradním režimu.
[SRWLock::LockShared](#lockshared)             | Získá objekt `SRWLock` ve sdíleném režimu.
[SRWLock::TryLockExclusive](#trylockexclusive) | Pokusí se získat `SRWLock` objekt ve výhradním režimu pro aktuální nebo zadaný `SRWLock` objekt.
[SRWLock::TryLockShared](#trylockshared)       | Pokusí se získat `SRWLock` objekt ve sdíleném režimu pro aktuální nebo zadaný `SRWLock` objekt.

### <a name="protected-data-member"></a>Člen chráněných dat

Name (Název)                                      | Popis
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock::SRWLock_](#srwlock-data-member) | Obsahuje základní proměnnou zámku pro aktuální `SRWLock` objekt.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SRWLock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky

## <a name="srwlocksrwlock"></a><a name="tilde-srwlock"></a>SRWLock:~SRWLock

Deinitializes instance třídy. `SRWLock`

```cpp
~SRWLock();
```

## <a name="srwlocklockexclusive"></a><a name="lockexclusive"></a>SRWLock::LockExclusive

Získá objekt `SRWLock` ve výhradním režimu.

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Ukazatel na `SRWLock` objekt.

### <a name="return-value"></a>Návratová hodnota

Objekt `SRWLock` ve výhradním režimu.

## <a name="srwlocklockshared"></a><a name="lockshared"></a>SRWLock::LockShared

Získá objekt `SRWLock` ve sdíleném režimu.

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Ukazatel na `SRWLock` objekt.

### <a name="return-value"></a>Návratová hodnota

Objekt `SRWLock` ve sdíleném režimu.

## <a name="srwlocksrwlock"></a><a name="srwlock-constructor"></a>SRWLock::SRWLock

Inicializuje novou instanci třídy. `SRWLock`

```cpp
SRWLock();
```

## <a name="srwlocksrwlock_"></a><a name="srwlock-data-member"></a>SRWLock::SRWLock_

Obsahuje základní proměnnou zámku pro aktuální `SRWLock` objekt.

```cpp
SRWLOCK SRWLock_;
```

## <a name="srwlocktrylockexclusive"></a><a name="trylockexclusive"></a>SRWLock::TryLockExclusive

Pokusí se získat `SRWLock` objekt ve výhradním režimu pro aktuální nebo zadaný `SRWLock` objekt. Pokud je volání úspěšné, volající vlákno převezme vlastnictví zámku.

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Ukazatel na `SRWLock` objekt.

### <a name="return-value"></a>Návratová hodnota

Pokud je `SRWLock` úspěšná, objekt ve výhradním režimu a volající vlákno převezme vlastnictví zámku. V opačném `SRWLock` případě objekt, jehož stav je neplatný.

## <a name="srwlocktrylockshared"></a><a name="trylockshared"></a>SRWLock::TryLockShared

Pokusí se získat `SRWLock` objekt ve sdíleném režimu pro aktuální nebo zadaný `SRWLock` objekt.

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Ukazatel na `SRWLock` objekt.

### <a name="return-value"></a>Návratová hodnota

Pokud je `SRWLock` úspěšná, objekt ve sdíleném režimu a volající vlákno převezme vlastnictví zámku. V opačném `SRWLock` případě objekt, jehož stav je neplatný.
