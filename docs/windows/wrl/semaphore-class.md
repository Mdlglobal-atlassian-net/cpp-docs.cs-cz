---
title: Semaphore – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Semaphore class
- Microsoft::WRL::Wrappers::Semaphore::Lock method
- Microsoft::WRL::Wrappers::Semaphore::operator= operator
- Microsoft::WRL::Wrappers::Semaphore::Semaphore, constructor
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
ms.openlocfilehash: 10357bb1cd46a33a8d4090c1ccc30050584d1816
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334767"
---
# <a name="semaphore-class"></a>Semaphore – třída

Představuje objekt synchronizace, který řídí sdíleného prostředku, který podporuje omezený počet uživatelů.

## <a name="syntax"></a>Syntaxe

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Název       | Popis
---------- | ------------------------------------------------------
`SyncLock` | Synonymum pro třídu, která podporuje synchronní zámky.

### <a name="public-constructors"></a>Veřejné konstruktory

Název                               | Popis
---------------------------------- | ----------------------------------------------------
[Semaphore::Semaphore –](#semaphore) | Inicializuje novou instanci třídy `Semaphore` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                     | Popis
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[Semaphore::LOCK –](#lock) | Počká, dokud aktuální objekt nebo objekt přidružený k zadanému popisovači, je do signalizovaného stavu nebo zadaný časový limit uplynul.

### <a name="public-operators"></a>Veřejné operátory

Název                                     | Popis
---------------------------------------- | ---------------------------------------------------------------------------------------
[Semaphore::Operator =](#operator-assign) | Posune Zadaný popisovač z `Semaphore` objektů na aktuální `Semaphore` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Semaphore`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="lock"></a>Semaphore::LOCK –

Počká, až do aktuálního objektu nebo `Semaphore` objekt přidružený k je zadaný popisovač do signalizovaného stavu nebo zadaný časový limit uplynul.

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>Parametry

*Milisekundy*<br/>
Interval časového limitu v milisekundách. Výchozí hodnota je NEKONEČNO, který čekat po neomezenou dobu.

*h*<br/>
Popisovač `Semaphore` objektu.

### <a name="return-value"></a>Návratová hodnota

A `Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`

## <a name="operator-assign"></a>Semaphore::Operator =

Posune Zadaný popisovač z `Semaphore` objektů na aktuální `Semaphore` objektu.

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Odkaz rvalue na `Semaphore` objektu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální `Semaphore` objektu.

## <a name="semaphore"></a>Semaphore::Semaphore –

Inicializuje novou instanci třídy `Semaphore` třídy.

```cpp
explicit Semaphore(
   HANDLE h
);

WRL_NOTHROW Semaphore(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Popisovač nebo odkaz rvalue na `Semaphore` objektu.