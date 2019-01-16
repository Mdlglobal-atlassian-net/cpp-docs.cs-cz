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
ms.openlocfilehash: d27e6ba8601d0e822113bf3a4a65269c89437271
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334734"
---
# <a name="synclockt-class"></a>SyncLockT – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>Parametry

*SyncTraits*<br/>
Typ, který může převzít vlastnictví prostředku.

## <a name="remarks"></a>Poznámky

Představuje typ, který může trvat exkluzivní nebo sdílené vlastnictví prostředku.

`SyncLockT` Třída se používá, třeba k implementaci [SRWLock](srwlock-class.md) třídy.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                      | Popis
----------------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt)        | Inicializuje novou instanci třídy `SyncLockT` třídy.
[SyncLockT::~SyncLockT](#tilde-synclockt) | Uvolní instanci `SyncLockT` třídy.

### <a name="protected-constructors"></a>Chráněné konstruktory

Název                               | Popis
---------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt) | Inicializuje novou instanci třídy `SyncLockT` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                             | Popis
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT::IsLocked](#islocked) | Označuje, zda aktuální `SyncLockT` vlastní prostředek objektu; to znamená, `SyncLockT` objekt je *uzamčen*.
[Synclockt::Unlock –](#unlock)     | Verze ovládacího prvku prostředku držené aktuální `SyncLockT` objektu, pokud existuje.

### <a name="protected-data-members"></a>Chránění členové dat

Název                      | Popis
------------------------- | -------------------------------------------------------------------
[SyncLockT::sync_](#sync) | Obsahuje základní prostředku reprezentovaného `SyncLockT` třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SyncLockT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="tilde-synclockt"></a>SyncLockT::~SyncLockT

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Poznámky

Uvolní instanci `SyncLockT` třídy.

Tento destruktor také odemkne aktuální `SyncLockT` instance.

## <a name="islocked"></a>SyncLockT::IsLocked

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud `SyncLockT` objekt je uzamčena, jinak **false**.

### <a name="remarks"></a>Poznámky

Označuje, zda aktuální `SyncLockT` vlastní prostředek objektu; to znamená, `SyncLockT` objekt je *uzamčen*.

## <a name="sync"></a>SyncLockT::sync_

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Poznámky

Obsahuje základní prostředku reprezentovaného `SyncLockT` třídy.

## <a name="synclockt"></a>SyncLockT::SyncLockT

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Odkaz rvalue na jiný `SyncLockT` objektu.

*sync*<br/>
Odkaz na jiný `SyncLockWithStatusT` objektu.

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy `SyncLockT` třídy.

První konstruktor inicializuje aktuální `SyncLockT` objektu z jiného `SyncLockT` objekt zadaný parametrem *jiných*a pak zruší platnost druhé `SyncLockT` objektu. Druhý konstruktor není `protected`a inicializuje aktuální `SyncLockT` objekt má neplatný stav.

## <a name="unlock"></a>Synclockt::Unlock –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
void Unlock();
```

### <a name="remarks"></a>Poznámky

Verze ovládacího prvku prostředku držené aktuální `SyncLockT` objektu, pokud existuje.
