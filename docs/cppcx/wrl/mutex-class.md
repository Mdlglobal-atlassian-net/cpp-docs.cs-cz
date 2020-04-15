---
title: Mutex – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Mutex class
- Microsoft::WRL::Wrappers::Mutex::Lock method
- Microsoft::WRL::Wrappers::Mutex::Mutex, constructor
- Microsoft::WRL::Wrappers::Mutex::operator= operator
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
ms.openlocfilehash: 36466bd00c5b100f20ee87173e68fdef4131ec23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371221"
---
# <a name="mutex-class"></a>Mutex – třída

Představuje objekt synchronizace, který výhradně řídí sdílený prostředek.

## <a name="syntax"></a>Syntaxe

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)       | Popis
---------- | ------------------------------------------------------
`SyncLock` | Synonymum pro třídu, která podporuje synchronní zámky.

### <a name="public-constructor"></a>Veřejný konstruktor

Name (Název)                   | Popis
---------------------- | ------------------------------------------------
[Mutex::Mutex](#mutex) | Inicializuje novou instanci třídy. `Mutex`

### <a name="public-members"></a>Veřejní členové

Name (Název)                 | Popis
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex::Zamknout](#lock) | Čeká, dokud aktuální objekt `Mutex` nebo objekt přidružený k zadanému popisovači uvolní mutex nebo zadaný časový limit.

### <a name="public-operator"></a>Veřejný operátor

Name (Název)                                 | Popis
------------------------------------ | ---------------------------------------------------------------------------
[Mutex::operátor=](#operator-assign) | Přiřadí (přesune) `Mutex` zadaný objekt `Mutex` aktuálnímu objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Mutex`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky

## <a name="mutexlock"></a><a name="lock"></a>Mutex::Zamknout

Čeká, dokud aktuální objekt `Mutex` nebo objekt přidružený k zadanému popisovači uvolní mutex nebo zadaný časový limit.

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
Popisovač objektu. `Mutex`

### <a name="return-value"></a>Návratová hodnota

## <a name="mutexmutex"></a><a name="mutex"></a>Mutex::Mutex

Inicializuje novou instanci třídy. `Mutex`

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Popisovač nebo rvalue odkaz na popisovač, `Mutex` na objekt.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje `Mutex` objekt ze zadaného popisovače. Druhý konstruktor inicializuje `Mutex` objekt ze zadaného popisovače a potom přesune `Mutex` vlastnictví objektu mutex na aktuální objekt.

## <a name="mutexoperator"></a><a name="operator-assign"></a>Mutex::operátor=

Přiřadí (přesune) `Mutex` zadaný objekt `Mutex` aktuálnímu objektu.

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Rvalue odkaz na `Mutex` objekt.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální `Mutex` objekt.

### <a name="remarks"></a>Poznámky

Další informace naleznete v části **Přesunout sémantiku** [v deklarátoru odkazu na rvalu: &&](../../cpp/rvalue-reference-declarator-amp-amp.md).
