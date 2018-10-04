---
title: Synclockt – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::sync_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockT class
- Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockT::sync_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT, constructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT, destructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock method
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 553429e2a4cc7db319c2176d20cb31e9fa0acdf7
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788745"
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

`SyncLockT` Třída se používá, třeba k implementaci [SRWLock](../windows/srwlock-class.md) třídy.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                      | Popis
----------------------------------------- | ----------------------------------------------------
[Synclockt::synclockt –](#synclockt)        | Inicializuje novou instanci třídy `SyncLockT` třídy.
[SyncLockT:: ~ synclockt –](#tilde-synclockt) | Uvolní instanci `SyncLockT` třídy.

### <a name="protected-constructors"></a>Chráněné konstruktory

Název                               | Popis
---------------------------------- | ----------------------------------------------------
[Synclockt::synclockt –](#synclockt) | Inicializuje novou instanci třídy `SyncLockT` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                             | Popis
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[Synclockt::islocked –](#islocked) | Označuje, zda aktuální `SyncLockT` vlastní prostředek objektu; to znamená, `SyncLockT` objekt je *uzamčen*.
[Synclockt::Unlock –](#unlock)     | Verze ovládacího prvku prostředku držené aktuální `SyncLockT` objektu, pokud existuje.

### <a name="protected-data-members"></a>Chránění členové dat

Název                      | Popis
------------------------- | -------------------------------------------------------------------
[Synclockt::sync_ –](#sync) | Obsahuje základní prostředku reprezentovaného `SyncLockT` třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SyncLockT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="tilde-synclockt"></a>SyncLockT:: ~ synclockt –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Poznámky

Uvolní instanci `SyncLockT` třídy.

Tento destruktor také odemkne aktuální `SyncLockT` instance.

## <a name="islocked"></a>Synclockt::islocked –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud `SyncLockT` objekt je uzamčena, jinak `false`.

### <a name="remarks"></a>Poznámky

Označuje, zda aktuální `SyncLockT` vlastní prostředek objektu; to znamená, `SyncLockT` objekt je *uzamčen*.

## <a name="sync"></a>Synclockt::sync_ –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Poznámky

Obsahuje základní prostředku reprezentovaného `SyncLockT` třídy.

## <a name="synclockt"></a>Synclockt::synclockt –

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
