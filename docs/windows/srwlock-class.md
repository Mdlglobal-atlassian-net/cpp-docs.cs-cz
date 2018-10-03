---
title: Srwlock – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/25/2018
ms.technology:
- cpp-windows
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 771a375d46177bb3b9d263f0a5221039bb963bc2
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48233967"
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

Název                | Popis
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | Synonymum pro `SRWLock` objekt, který je požadován ve výhradním režimu.
`SyncLockShared`    | Synonymum pro `SRWLock` objekt, který je požadován ve sdíleném režimu.

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                     | Popis
---------------------------------------- | --------------------------------------------------
[Srwlock::srwlock –](#srwlock-constructor) | Inicializuje novou instanci třídy `SRWLock` třídy.
[SRWLock:: ~ SRWLock](#tilde-srwlock)      | Uvolní instanci `SRWLock` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                                           | Popis
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[Srwlock::lockexclusive –](#lockexclusive)       | Získá `SRWLock` objektu ve výhradním režimu.
[Srwlock::lockshared –](#lockshared)             | Získá `SRWLock` objektu ve sdíleném režimu.
[Srwlock::trylockexclusive –](#trylockexclusive) | Pokusí se získat `SRWLock` objektu ve výhradním režimu pro aktuální nebo zadané `SRWLock` objektu.
[Srwlock::trylockshared –](#trylockshared)       | Pokusí se získat `SRWLock` objektu ve sdíleném režimu pro aktuální nebo zadané `SRWLock` objektu.

### <a name="protected-data-member"></a>Chráněný datový člen

Název                                      | Popis
----------------------------------------- | -----------------------------------------------------------------------
[Srwlock::srwlock_ –](#srwlock-data-member) | Obsahuje základní proměnnou zámek pro aktuální `SRWLock` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SRWLock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="tilde-srwlock"></a>SRWLock:: ~ SRWLock

Uvolní instanci `SRWLock` třídy.

```cpp
~SRWLock();
```

## <a name="lockexclusive"></a>Srwlock::lockexclusive –

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

## <a name="lockshared"></a>Srwlock::lockshared –

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

## <a name="srwlock-constructor"></a>Srwlock::srwlock –

Inicializuje novou instanci třídy `SRWLock` třídy.

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>Srwlock::srwlock_ –

Obsahuje základní proměnnou zámek pro aktuální `SRWLock` objektu.

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>Srwlock::trylockexclusive –

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

## <a name="trylockshared"></a>Srwlock::trylockshared –

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
