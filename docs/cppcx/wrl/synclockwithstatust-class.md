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
ms.openlocfilehash: 77bcb8336e4650de7ed01a067fa1bdd7ec0ba3e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374269"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT – třída

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Parametry

*SyncTraits*<br/>
Typ, který může převzít výhradní nebo sdílené vlastnictví prostředku.

## <a name="remarks"></a>Poznámky

Představuje typ, který může mít výhradní nebo sdílené vlastnictví prostředku.

Třída `SyncLockWithStatusT` se používá k implementaci [Mutex](mutex-class.md) a [Semafor](semaphore-class.md) třídy.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                                             | Popis
---------------------------------------------------------------- | --------------------------------------------------------------
[synclockwithstatust::SyncLockWithStatusT](#synclockwithstatust) | Inicializuje novou instanci třídy. `SyncLockWithStatusT`

### <a name="protected-constructors"></a>Chráněné konstruktory

Name (Název)                                                             | Popis
---------------------------------------------------------------- | --------------------------------------------------------------
[synclockwithstatust::SyncLockWithStatusT](#synclockwithstatust) | Inicializuje novou instanci třídy. `SyncLockWithStatusT`

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                         | Popis
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::GetStatus](#getstatus) | Načte stav čekání aktuálního `SyncLockWithStatusT` objektu.
[SyncLockWithStatusT::Uzamčeno](#islocked)   | Označuje, zda `SyncLockWithStatusT` aktuální objekt vlastní prostředek; to znamená, `SyncLockWithStatusT` že objekt je *uzamčen*.

### <a name="protected-data-members"></a>Členové chráněných dat

Name (Název)                                    | Popis
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::status_](#status) | Obsahuje výsledek operace základní čekání po operaci uzamčení na `SyncLockWithStatusT` objekt u aktuálního objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky::Details

## <a name="synclockwithstatustgetstatus"></a><a name="getstatus"></a>SyncLockWithStatusT::GetStatus

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>Návratová hodnota

Výsledek operace čekání na objekt, který je `SyncLockWithStatusT` založen na třídy, například [Mutex](mutex-class.md) nebo [Semafor](semaphore-class.md). Zero (0) označuje, že operace čekání vrátila signalovaný stav; v opačném případě došlo k jinému stavu, jako je například hodnota časového limitu uplynul.

### <a name="remarks"></a>Poznámky

Načte stav čekání aktuálního `SyncLockWithStatusT` objektu.

Funkce GetStatus() načte hodnotu podkladového [status_](#status) datového člena. Když objekt založený `SyncLockWithStatusT` na třídě provede operaci uzamčení, objekt nejprve čeká na objekt k dispozici. Výsledek této operace čekání je `status_` uložen v datovém členu. Možné hodnoty datového `status_` člena jsou vrácené hodnoty operace čekání. Další informace naleznete v návratových `WaitForSingleObjectEx()` hodnotách funkce v knihovně MSDN.

## <a name="synclockwithstatustislocked"></a><a name="islocked"></a>SyncLockWithStatusT::Uzamčeno

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Poznámky

Označuje, zda `SyncLockWithStatusT` aktuální objekt vlastní prostředek; to znamená, `SyncLockWithStatusT` že objekt je *uzamčen*.

### <a name="return-value"></a>Návratová hodnota

**true,** `SyncLockWithStatusT` pokud je objekt uzamčen; jinak **false**.

## <a name="synclockwithstatuststatus_"></a><a name="status"></a>SyncLockWithStatusT::status_

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
DWORD status_;
```

### <a name="remarks"></a>Poznámky

Obsahuje výsledek operace základní čekání po operaci uzamčení na `SyncLockWithStatusT` objekt u aktuálního objektu.

## <a name="synclockwithstatustsynclockwithstatust"></a><a name="synclockwithstatust"></a>synclockwithstatust::SyncLockWithStatusT

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

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

*Další*<br/>
Rvalue odkaz na `SyncLockWithStatusT` jiný objekt.

*synchronizace*<br/>
Odkaz na `SyncLockWithStatusT` jiný objekt.

*Stav*<br/>
Hodnota [status_](#status) datový člen *jiného* parametru nebo parametr *synchronizace.*

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy. `SyncLockWithStatusT`

První konstruktor inicializuje `SyncLockWithStatusT` aktuální objekt `SyncLockWithStatusT` z jiného určeného parametrem `SyncLockWithStatusT` *other*a potom zruší platnost jiného objektu. Druhý konstruktor `protected`je a inicializuje `SyncLockWithStatusT` aktuální objekt do neplatného stavu.
