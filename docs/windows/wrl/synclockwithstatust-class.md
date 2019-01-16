---
title: SyncLockWithStatusT – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT class
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT, constructor
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
ms.openlocfilehash: 1c9c0805834a59d10a559bfc2b6da0f10e2fe160
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334703"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Parametry

*SyncTraits*<br/>
Typ, který může trvat exkluzivní nebo sdílené vlastnictví prostředku.

## <a name="remarks"></a>Poznámky

Představuje typ, který může trvat exkluzivní nebo sdílené vlastnictví prostředku.

`SyncLockWithStatusT` Třída se používá k implementaci [Mutex](mutex-class.md) a [semafor](semaphore-class.md) třídy.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                                             | Popis
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Inicializuje novou instanci třídy `SyncLockWithStatusT` třídy.

### <a name="protected-constructors"></a>Chráněné konstruktory

Název                                                             | Popis
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Inicializuje novou instanci třídy `SyncLockWithStatusT` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                                         | Popis
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[Synclockwithstatust::getStatus –](#getstatus) | Načte aktuální stav Čekání `SyncLockWithStatusT` objektu.
[SyncLockWithStatusT::IsLocked](#islocked)   | Označuje, zda aktuální `SyncLockWithStatusT` vlastní prostředek objektu; to znamená, `SyncLockWithStatusT` objekt je *uzamčen*.

### <a name="protected-data-members"></a>Chránění členové dat

Název                                    | Popis
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::status_](#status) | Obsahuje výsledek základní operace čekání po operaci zámku na objektu na základě aktuálního `SyncLockWithStatusT` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="getstatus"></a>Synclockwithstatust::getStatus –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>Návratová hodnota

Výsledek operace čekání na objekt, který je založen na `SyncLockWithStatusT` třídy, jako například [Mutex](mutex-class.md) nebo [semafor](semaphore-class.md). Nula (0) označuje, že operace čekání vrátí signalizovaného stavu; v opačném případě jiný stav došlo k chybě, jako hodnotu časového limitu vypršel.

### <a name="remarks"></a>Poznámky

Načte aktuální stav Čekání `SyncLockWithStatusT` objektu.

Načte hodnotu základní funkce GetStatus() [status_ –](#status) datový člen. Když se objekt na platformě `SyncLockWithStatusT` třída provádí operace uzamčení, objekt nejprve počká na objekt k dispozici. Výsledek této operace čekání je uložen v `status_` datový člen. Možné hodnoty `status_` datový člen jsou vrácené hodnoty operace čekání. Další informace najdete v tématu vrácené hodnoty `WaitForSingleObjectEx()` funkce v knihovně MSDN.

## <a name="islocked"></a>SyncLockWithStatusT::IsLocked

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Poznámky

Označuje, zda aktuální `SyncLockWithStatusT` vlastní prostředek objektu; to znamená, `SyncLockWithStatusT` objekt je *uzamčen*.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud `SyncLockWithStatusT` objekt je uzamčena, jinak **false**.

## <a name="status"></a>SyncLockWithStatusT::status_

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
DWORD status_;
```

### <a name="remarks"></a>Poznámky

Obsahuje výsledek základní operace čekání po operaci zámku na objektu na základě aktuálního `SyncLockWithStatusT` objektu.

## <a name="synclockwithstatust"></a>SyncLockWithStatusT::SyncLockWithStatusT

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
SyncLockWithStatusT(
   _Inout_ SyncLockWithStatusT&& other
);

explicit SyncLockWithStatusT(
   typename SyncTraits::Type sync,
   DWORD status
);
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Odkaz rvalue na jiný `SyncLockWithStatusT` objektu.

*sync*<br/>
Odkaz na jiný `SyncLockWithStatusT` objektu.

*status*<br/>
Hodnota [status_ –](#status) datový člen třídy *jiných* parametr nebo *synchronizace* parametr.

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy `SyncLockWithStatusT` třídy.

První konstruktor inicializuje aktuální `SyncLockWithStatusT` objektu z jiného `SyncLockWithStatusT` určené parametrem *jiných*a pak zruší platnost druhé `SyncLockWithStatusT` objektu. Druhý konstruktor není `protected`a inicializuje aktuální `SyncLockWithStatusT` objekt má neplatný stav.
