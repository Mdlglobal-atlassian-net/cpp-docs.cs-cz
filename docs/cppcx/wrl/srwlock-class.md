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
ms.openlocfilehash: 6d4a504d9465c858af59a88cf0ef611bf88c3fde
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786982"
---
# <a name="srwlock-class"></a>Třída SRWLock

Představuje zámek tenký čtení/zápis.

## <a name="syntax"></a>Syntaxe

```cpp
class SRWLock;
```

## <a name="remarks"></a>Poznámky

Zámek tenký čtení/zápis se používá k synchronizaci přístupu napříč vlákny na objekt nebo prostředků. Další informace najdete v tématu [funkce synchronizace](/windows/desktop/Sync/synchronization-functions).

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Name                | Popis
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | Synonymum pro `SRWLock` objekt, který je požadován ve výhradním režimu.
`SyncLockShared`    | Synonymum pro `SRWLock` objekt, který je požadován ve sdíleném režimu.

### <a name="public-constructors"></a>Veřejné konstruktory

Name                                     | Popis
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | Inicializuje novou instanci třídy `SRWLock` třídy.
[SRWLock::~SRWLock](#tilde-srwlock)      | Uvolní instanci `SRWLock` třídy.

### <a name="public-methods"></a>Veřejné metody

Name                                           | Popis
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | Získá `SRWLock` objektu ve výhradním režimu.
[SRWLock::LockShared](#lockshared)             | Získá `SRWLock` objektu ve sdíleném režimu.
[SRWLock::TryLockExclusive](#trylockexclusive) | Pokusí se získat `SRWLock` objektu ve výhradním režimu pro aktuální nebo zadané `SRWLock` objektu.
[SRWLock::TryLockShared](#trylockshared)       | Pokusí se získat `SRWLock` objektu ve sdíleném režimu pro aktuální nebo zadané `SRWLock` objektu.

### <a name="protected-data-member"></a>Chráněný datový člen

Name                                      | Popis
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock::SRWLock_](#srwlock-data-member) | Obsahuje základní proměnnou zámek pro aktuální `SRWLock` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SRWLock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="tilde-srwlock"></a>SRWLock::~SRWLock

Uvolní instanci `SRWLock` třídy.

```cpp
~SRWLock();
```

## <a name="lockexclusive"></a>SRWLock::LockExclusive

Získá `SRWLock` objektu ve výhradním režimu.

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Ukazatel `SRWLock` objektu.

### <a name="return-value"></a>Návratová hodnota

`SRWLock` Objektu ve výhradním režimu.

## <a name="lockshared"></a>SRWLock::LockShared

Získá `SRWLock` objektu ve sdíleném režimu.

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Ukazatel `SRWLock` objektu.

### <a name="return-value"></a>Návratová hodnota

`SRWLock` Objektu ve sdíleném režimu.

## <a name="srwlock-constructor"></a>SRWLock::SRWLock

Inicializuje novou instanci třídy `SRWLock` třídy.

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>SRWLock::SRWLock_

Obsahuje základní proměnnou zámek pro aktuální `SRWLock` objektu.

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>SRWLock::TryLockExclusive

Pokusí se získat `SRWLock` objektu ve výhradním režimu pro aktuální nebo zadané `SRWLock` objektu. Pokud je volání úspěšné, volající vlákno převezme vlastnictví zámku.

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Ukazatel `SRWLock` objektu.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu, `SRWLock` objektu ve výhradním režimu a volající vlákno převezme vlastnictví zámku. V opačném případě `SRWLock` objekt, jehož stav je neplatný.

## <a name="trylockshared"></a>SRWLock::TryLockShared

Pokusí se získat `SRWLock` objektu ve sdíleném režimu pro aktuální nebo zadané `SRWLock` objektu.

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Ukazatel `SRWLock` objektu.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu, `SRWLock` objektu ve sdíleném režimu a volající vlákno převezme vlastnictví zámku. V opačném případě `SRWLock` objekt, jehož stav je neplatný.
