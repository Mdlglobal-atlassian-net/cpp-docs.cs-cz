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
ms.openlocfilehash: e017b1b6316c4b6d49563d9a543950ab28961d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359361"
---
# <a name="semaphore-class"></a>Semaphore – třída

Představuje objekt synchronizace, který řídí sdílený prostředek, který může podporovat omezený počet uživatelů.

## <a name="syntax"></a>Syntaxe

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)       | Popis
---------- | ------------------------------------------------------
`SyncLock` | Synonymum pro třídu, která podporuje synchronní zámky.

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                               | Popis
---------------------------------- | ----------------------------------------------------
[Semafor::Semafor](#semaphore) | Inicializuje novou instanci třídy. `Semaphore`

### <a name="public-methods"></a>Veřejné metody

Name (Název)                     | Popis
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[Semafor::Zamknout](#lock) | Čeká, dokud aktuální objekt nebo objekt přidružený k zadanému popisovači, je v signalizovaném stavu nebo zadaný časový limit uplynul.

### <a name="public-operators"></a>Veřejné operátory

Name (Název)                                     | Popis
---------------------------------------- | ---------------------------------------------------------------------------------------
[Semafor::operátor=](#operator-assign) | Přesune zadaný popisovač z `Semaphore` `Semaphore` objektu na aktuální objekt.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Semaphore`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky

## <a name="semaphorelock"></a><a name="lock"></a>Semafor::Zamknout

Čeká, dokud aktuální objekt `Semaphore` nebo objekt přidružený k zadanému popisovači, je v signalizovaném stavu nebo zadaný časový limit uplynul.

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

*milisekundy*<br/>
Časový interval v milisekundách. Výchozí hodnota je INFINITE, která čeká neomezeně dlouho.

*H*<br/>
Úchyt `Semaphore` k objektu.

### <a name="return-value"></a>Návratová hodnota

Položka `Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`.

## <a name="semaphoreoperator"></a><a name="operator-assign"></a>Semafor::operátor=

Přesune zadaný popisovač z `Semaphore` `Semaphore` objektu na aktuální objekt.

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Rvalue-odkaz na `Semaphore` objekt.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální `Semaphore` objekt.

## <a name="semaphoresemaphore"></a><a name="semaphore"></a>Semafor::Semafor

Inicializuje novou instanci třídy. `Semaphore`

```cpp
explicit Semaphore(
   HANDLE h
);

WRL_NOTHROW Semaphore(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Popisovač nebo rvalue odkaz `Semaphore` na objekt.
