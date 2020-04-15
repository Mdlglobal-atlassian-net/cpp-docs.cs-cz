---
title: SyncLockT – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::sync_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockT class
- Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockT::sync_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT, constructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT, destructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock method
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
ms.openlocfilehash: 52c4404fa28f680a9a7a4592d03f535e8406d1a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374287"
---
# <a name="synclockt-class"></a>SyncLockT – třída

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>Parametry

*SyncTraits*<br/>
Typ, který může převzít vlastnictví prostředku.

## <a name="remarks"></a>Poznámky

Představuje typ, který může mít výhradní nebo sdílené vlastnictví prostředku.

Třída `SyncLockT` se používá například k implementaci třídy [SRWLock.](srwlock-class.md)

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                      | Popis
----------------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt)        | Inicializuje novou instanci třídy. `SyncLockT`
[SyncLockT::~SyncLockT](#tilde-synclockt) | Deinitializes instance třídy. `SyncLockT`

### <a name="protected-constructors"></a>Chráněné konstruktory

Name (Název)                               | Popis
---------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt) | Inicializuje novou instanci třídy. `SyncLockT`

### <a name="public-methods"></a>Veřejné metody

Name (Název)                             | Popis
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT::Uzamčeno](#islocked) | Označuje, zda `SyncLockT` aktuální objekt vlastní prostředek; to znamená, `SyncLockT` že objekt je *uzamčen*.
[SyncLockT::Odemknout](#unlock)     | Uvolní řízení prostředku drženého aktuálním `SyncLockT` objektem, pokud existuje.

### <a name="protected-data-members"></a>Členové chráněných dat

Name (Název)                      | Popis
------------------------- | -------------------------------------------------------------------
[SyncLockT::sync_](#sync) | Obsahuje základní prostředek reprezentované třídou. `SyncLockT`

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SyncLockT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky::Details

## <a name="synclocktsynclockt"></a><a name="tilde-synclockt"></a>SyncLockT::~SyncLockT

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Poznámky

Deinitializes instance třídy. `SyncLockT`

Tento destruktor také `SyncLockT` odemkne aktuální instanci.

## <a name="synclocktislocked"></a><a name="islocked"></a>SyncLockT::Uzamčeno

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** `SyncLockT` pokud je objekt uzamčen; jinak **false**.

### <a name="remarks"></a>Poznámky

Označuje, zda `SyncLockT` aktuální objekt vlastní prostředek; to znamená, `SyncLockT` že objekt je *uzamčen*.

## <a name="synclocktsync_"></a><a name="sync"></a>SyncLockT::sync_

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Poznámky

Obsahuje základní prostředek reprezentované třídou. `SyncLockT`

## <a name="synclocktsynclockt"></a><a name="synclockt"></a>SyncLockT::SyncLockT

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Rvalue odkaz na `SyncLockT` jiný objekt.

*synchronizace*<br/>
Odkaz na `SyncLockWithStatusT` jiný objekt.

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy. `SyncLockT`

První konstruktor inicializuje `SyncLockT` aktuální objekt `SyncLockT` z jiného objektu určeného *jiným*parametrem a potom zruší platnost druhého `SyncLockT` objektu. Druhý konstruktor `protected`je a inicializuje `SyncLockT` aktuální objekt do neplatného stavu.

## <a name="synclocktunlock"></a><a name="unlock"></a>SyncLockT::Odemknout

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
void Unlock();
```

### <a name="remarks"></a>Poznámky

Uvolní řízení prostředku drženého aktuálním `SyncLockT` objektem, pokud existuje.
