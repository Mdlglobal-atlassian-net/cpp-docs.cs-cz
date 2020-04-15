---
title: CriticalSection – třída
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::cs_
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::IsValid
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::CriticalSection class
- Microsoft::WRL::Wrappers::CriticalSection::cs_ data member
- Microsoft::WRL::Wrappers::CriticalSection::IsValid method
- Microsoft::WRL::Wrappers::CriticalSection::Lock method
- Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection, destructor
- Microsoft::WRL::Wrappers::CriticalSection::CriticalSection, constructor
- Microsoft::WRL::Wrappers::CriticalSection::TryLock method
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
ms.openlocfilehash: 5deb89e795d1886ca316886ae1ea260ce1f36fd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372592"
---
# <a name="criticalsection-class"></a>CriticalSection – třída

Představuje objekt kritického oddílu.

## <a name="syntax"></a>Syntaxe

```cpp
class CriticalSection;
```

## <a name="members"></a>Členové

### <a name="constructor"></a>Konstruktor

Name (Název)                                                        | Popis
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::CriticalSection](#criticalsection)        | Inicializuje objekt synchronizace, který je podobný objektu mutex, ale může být použit pouze vlákny jednoho procesu.
[CriticalSection::~CriticalSection](#tilde-criticalsection) | Deinitializes a zničí `CriticalSection` aktuální objekt.

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                 | Popis
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[Kritický oddíl::IsValid](#isvalid) | Označuje, zda je aktuální kritický oddíl platný.
[CriticalSection::Zamknout](#lock)       | Čeká na vlastnictví zadaného objektu kritického oddílu. Funkce vrátí, když volající vlákno je uděleno vlastnictví.
[CriticalSection::TryLock](#trylock) | Pokusí se zadat kritický oddíl bez blokování. Pokud je volání úspěšné, volající vlákno převezme vlastnictví kritické části.

### <a name="protected-data-members"></a>Členové chráněných dat

Name (Název)                        | Popis
--------------------------- | ----------------------------------------
[CriticalSection::cs_](#cs) | Deklaruje datový člen kritické ho oddílu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CriticalSection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky

## <a name="criticalsectioncriticalsection"></a><a name="tilde-criticalsection"></a>CriticalSection::~CriticalSection

Deinitializes a zničí `CriticalSection` aktuální objekt.

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsectioncriticalsection"></a><a name="criticalsection"></a>CriticalSection::CriticalSection

Inicializuje objekt synchronizace, který je podobný objektu mutex, ale může být použit pouze vlákny jednoho procesu.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Parametry

*spincount*<br/>
Počet odstřeďování pro objekt kritické části. Výchozí hodnota je 0.

### <a name="remarks"></a>Poznámky

Další informace o kritických oddílech `InitializeCriticalSectionAndSpinCount` a spincounts, naleznete v `Synchronization` části rozhraní API prostředí Windows documenation.

## <a name="criticalsectioncs_"></a><a name="cs"></a>CriticalSection::cs_

Deklaruje datový člen kritické ho oddílu.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>Poznámky

Tento datový člen je chráněn.

## <a name="criticalsectionisvalid"></a><a name="isvalid"></a>Kritický oddíl::IsValid

Označuje, zda je aktuální kritický oddíl platný.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

Ve výchozím nastavení vždy vrátí **hodnotu true**.

## <a name="criticalsectionlock"></a><a name="lock"></a>CriticalSection::Zamknout

Čeká na vlastnictví zadaného objektu kritického oddílu. Funkce vrátí, když volající vlákno je uděleno vlastnictví.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*Cs*<br/>
Objekt kritického oddílu zadaný uživatelem.

### <a name="return-value"></a>Návratová hodnota

Objekt zámku, který lze použít k odemknutí aktuální kritické části.

### <a name="remarks"></a>Poznámky

První `Lock` funkce ovlivňuje aktuální objekt kritického řezu. Druhá `Lock` funkce ovlivňuje kritický oddíl zadaný uživatelem.

## <a name="criticalsectiontrylock"></a><a name="trylock"></a>CriticalSection::TryLock

Pokusí se zadat kritický oddíl bez blokování. Pokud je volání úspěšné, volající vlákno převezme vlastnictví kritické části.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*Cs*<br/>
Objekt kritického oddílu zadaný uživatelem.

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota, pokud je kritický oddíl úspěšně zadán nebo aktuální vlákno již kritický oddíl vlastní. Nula, pokud jiný podproces již vlastní kritický oddíl.

### <a name="remarks"></a>Poznámky

První `TryLock` funkce ovlivňuje aktuální objekt kritického řezu. Druhá `TryLock` funkce ovlivňuje kritický oddíl zadaný uživatelem.
