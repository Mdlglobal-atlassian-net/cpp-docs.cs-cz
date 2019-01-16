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
ms.openlocfilehash: dd34206741ba8fee8b283e22b6e8eefb3b3efb0e
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334741"
---
# <a name="criticalsection-class"></a>CriticalSection – třída

Představuje objekt kritický oddíl.

## <a name="syntax"></a>Syntaxe

```cpp
class CriticalSection;
```

## <a name="members"></a>Členové

### <a name="constructor"></a>Konstruktor

Název                                                        | Popis
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Criticalsection::criticalsection –](#criticalsection)        | Inicializuje objekt synchronizace, který je podobný objektu mutex, ale může využívat pouze vláken v jednom procesu.
[CriticalSection::~CriticalSection](#tilde-criticalsection) | Uvolní a odstraní aktuální `CriticalSection` objektu.

### <a name="public-methods"></a>Veřejné metody

Název                                 | Popis
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::IsValid](#isvalid) | Označuje, zda aktuální kritický oddíl je platný.
[CriticalSection::Lock](#lock)       | Čeká na vlastnictví objektu zadaného kritický oddíl. Funkce vrátí, pokud volající vlákno bylo uděleno vlastnictví.
[Criticalsection::trylock –](#trylock) | Pokusy o zadání kritický oddíl bez blokování. Pokud je volání úspěšné, volající vlákno trvá vlastnictví kritický oddíl.

### <a name="protected-data-members"></a>Chránění členové dat

Název                        | Popis
--------------------------- | ----------------------------------------
[CriticalSection::cs_](#cs) | Deklaruje datový člen kritický oddíl.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CriticalSection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="tilde-criticalsection"></a>CriticalSection::~CriticalSection

Uvolní a odstraní aktuální `CriticalSection` objektu.

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsection"></a>Criticalsection::criticalsection –

Inicializuje objekt synchronizace, který je podobný objektu mutex, ale může využívat pouze vláken v jednom procesu.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Parametry

*spincount*<br/>
Počet typu číselník pro objekt kritický oddíl. Výchozí hodnota je 0.

### <a name="remarks"></a>Poznámky

Další informace o kritických oddílů a spincounts, najdete v článku `InitializeCriticalSectionAndSpinCount` fungovat v `Synchronization` část jejich rozhraní Windows API.

## <a name="cs"></a>Criticalsection::cs_ –

Deklaruje datový člen kritický oddíl.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>Poznámky

Tento datový člen je chráněný.

## <a name="isvalid"></a>CriticalSection::IsValid

Označuje, zda aktuální kritický oddíl je platný.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

Ve výchozím nastavení, vždy vrátí **true**.

## <a name="lock"></a>Criticalsection::LOCK –

Čeká na vlastnictví objektu zadaného kritický oddíl. Funkce vrátí, pokud volající vlákno bylo uděleno vlastnictví.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*cs*<br/>
Kritický oddíl uživatelem zadaného objektu.

### <a name="return-value"></a>Návratová hodnota

Zamknout objekt, který můžete použít k odemknutí aktuální kritický oddíl.

### <a name="remarks"></a>Poznámky

První `Lock` aktuální objekt kritický oddíl má vliv na funkce. Druhá `Lock` funkce ovlivňuje kritickou sekci zadané uživatelem.

## <a name="trylock"></a>Criticalsection::trylock –

Pokusy o zadání kritický oddíl bez blokování. Pokud je volání úspěšné, volající vlákno trvá vlastnictví kritický oddíl.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*cs*<br/>
Kritický oddíl uživatelem zadaného objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud byly úspěšně uloženy kritický oddíl nebo aktuální vlákno již vlastní kritický oddíl. Nula v případě jiné vlákno již vlastní kritický oddíl.

### <a name="remarks"></a>Poznámky

První `TryLock` aktuální objekt kritický oddíl má vliv na funkce. Druhá `TryLock` funkce ovlivňuje kritickou sekci zadané uživatelem.
