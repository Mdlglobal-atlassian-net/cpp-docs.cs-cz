---
title: Semafor třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/25/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Semaphore class
- Microsoft::WRL::Wrappers::Semaphore::Lock method
- Microsoft::WRL::Wrappers::Semaphore::operator= operator
- Microsoft::WRL::Wrappers::Semaphore::Semaphore, constructor
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 269b3229a0755e88d55fc4fa5d14b843345ccc44
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234449"
---
# <a name="semaphore-class"></a>Semaphore – třída

Představuje objekt synchronizace, který řídí sdíleného prostředku, který podporuje omezený počet uživatelů.

## <a name="syntax"></a>Syntaxe

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>
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

**Namespace:** Microsoft::WRL:: wrappers –

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
