---
title: Mutex – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Mutex class
- Microsoft::WRL::Wrappers::Mutex::Lock method
- Microsoft::WRL::Wrappers::Mutex::Mutex, constructor
- Microsoft::WRL::Wrappers::Mutex::operator= operator
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 37aaafa636f43671eb18436a49490caa10cf349f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789303"
---
# <a name="mutex-class"></a>Mutex – třída

Představuje objekt synchronizace, který řídí výhradně sdíleného prostředku.

## <a name="syntax"></a>Syntaxe

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Název       | Popis
---------- | ------------------------------------------------------
`SyncLock` | Synonymum pro třídu, která podporuje synchronní zámky.

### <a name="public-constructor"></a>Veřejný konstruktor

Název                   | Popis
---------------------- | ------------------------------------------------
[Mutex::mutex –](#mutex) | Inicializuje novou instanci třídy `Mutex` třídy.

### <a name="public-members"></a>Veřejné členy

Název                 | Popis
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex::LOCK –](#lock) | Počká, až do aktuálního objektu nebo `Mutex` objekt přidružený k Zadaný popisovač mutex nebo zadaný časový limit uplynul vydané verze.

### <a name="public-operator"></a>Veřejný operátor

Název                                 | Popis
------------------------------------ | ---------------------------------------------------------------------------
[Mutex::Operator =](#operator-assign) | Přiřadí (přesun) zadaný `Mutex` objektů na aktuální `Mutex` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Mutex`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="lock"></a>Mutex::LOCK –

Počká, až do aktuálního objektu nebo `Mutex` objekt přidružený k Zadaný popisovač mutex nebo zadaný časový limit uplynul vydané verze.

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
Popisovač `Mutex` objektu.

### <a name="return-value"></a>Návratová hodnota

## <a name="mutex"></a>Mutex::mutex –

Inicializuje novou instanci třídy `Mutex` třídy.

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Popisovač nebo odkaz rvalue na popisovač, do `Mutex` objektu.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje `Mutex` objekt ze zadaného popisovače. Druhý konstruktor inicializuje `Mutex` objekt Zadaný popisovač a pak přesune vlastnictví mutex do aktuální `Mutex` objektu.

## <a name="operator-assign"></a>Mutex::Operator =

Přiřadí (přesun) zadaný `Mutex` objektů na aktuální `Mutex` objektu.

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Odkaz rvalue na `Mutex` objektu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální `Mutex` objektu.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu **přesunutí sémantiky** část [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).
