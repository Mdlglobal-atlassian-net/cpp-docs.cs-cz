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
ms.openlocfilehash: 079f1abe652d8c1610a084f5e1158cc5798d61c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498294"
---
# <a name="srwlock-class"></a>Třída SRWLock

Představuje zámek pro čtení/zápis na tenkém zařízení.

## <a name="syntax"></a>Syntaxe

```cpp
class SRWLock;
```

## <a name="remarks"></a>Poznámky

Zámek na tenké čtečce nebo zapisovači se používá k synchronizaci přístupu mezi vlákny k objektu nebo prostředku. Další informace najdete v tématu [synchronizační funkce](/windows/win32/Sync/synchronization-functions).

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

Name                | Popis
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | Synonymum pro `SRWLock` objekt, který je získán ve výhradním režimu.
`SyncLockShared`    | Synonymum pro `SRWLock` objekt, který je získán ve sdíleném režimu.

### <a name="public-constructors"></a>Veřejné konstruktory

Name                                     | Popis
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | Inicializuje novou instanci třídy `SRWLock` třídy.
[SRWLock::~SRWLock](#tilde-srwlock)      | Zruší inicializaci instance `SRWLock` třídy.

### <a name="public-methods"></a>Veřejné metody

Name                                           | Popis
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | `SRWLock` Získá objekt ve výhradním režimu.
[SRWLock::LockShared](#lockshared)             | `SRWLock` Získá objekt ve sdíleném režimu.
[SRWLock:: Trylockexclusive –](#trylockexclusive) | Pokusí se získat `SRWLock` objekt ve výhradním režimu pro aktuální nebo zadaný `SRWLock` objekt.
[SRWLock::TryLockShared](#trylockshared)       | Pokusí se získat `SRWLock` objekt ve sdíleném režimu pro aktuální nebo zadaný `SRWLock` objekt.

### <a name="protected-data-member"></a>Chráněný datový člen

Name                                      | Popis
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock::SRWLock_](#srwlock-data-member) | Obsahuje základní zamykací proměnnou pro aktuální `SRWLock` objekt.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SRWLock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers. h

**Hosting** Microsoft::WRL::Wrappers

## <a name="tilde-srwlock"></a>SRWLock::~SRWLock

Zruší inicializaci instance `SRWLock` třídy.

```cpp
~SRWLock();
```

## <a name="lockexclusive"></a>SRWLock::LockExclusive

`SRWLock` Získá objekt ve výhradním režimu.

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Ukazatel na `SRWLock` objekt.

### <a name="return-value"></a>Návratová hodnota

`SRWLock` Objekt ve výhradním režimu.

## <a name="lockshared"></a>SRWLock::LockShared

`SRWLock` Získá objekt ve sdíleném režimu.

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Ukazatel na `SRWLock` objekt.

### <a name="return-value"></a>Návratová hodnota

`SRWLock` Objekt ve sdíleném režimu.

## <a name="srwlock-constructor"></a>SRWLock:: SRWLock

Inicializuje novou instanci třídy `SRWLock` třídy.

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>SRWLock:: SRWLock_

Obsahuje základní zamykací proměnnou pro aktuální `SRWLock` objekt.

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>SRWLock:: Trylockexclusive –

Pokusí se získat `SRWLock` objekt ve výhradním režimu pro aktuální nebo zadaný `SRWLock` objekt. Pokud je volání úspěšné, volající vlákno převezme vlastnictví zámku.

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Ukazatel na `SRWLock` objekt.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu `SRWLock` objekt ve výhradním režimu a volající vlákno převezme vlastnictví zámku. V opačném `SRWLock` případě objekt, jehož stav je neplatný.

## <a name="trylockshared"></a>SRWLock:: Trylockshared –

Pokusí se získat `SRWLock` objekt ve sdíleném režimu pro aktuální nebo zadaný `SRWLock` objekt.

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Ukazatel na `SRWLock` objekt.

### <a name="return-value"></a>Návratová hodnota

Je-li to `SRWLock` úspěšné, objekt ve sdíleném režimu a volající vlákno převezme vlastnictví zámku. V opačném `SRWLock` případě objekt, jehož stav je neplatný.
