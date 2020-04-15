---
title: CriticalSectionTraits – struktura
ms.date: 09/26/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock method
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
ms.openlocfilehash: 05c93bf6a2765bd11489075067c627ab3c3ab691
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372584"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits – struktura

Specializuje `CriticalSection` objekt na podporu buď neplatný kritický oddíl nebo funkce pro uvolnění kritické ho oddílu.

## <a name="syntax"></a>Syntaxe

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)   | Popis
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | A, `typedef` který definuje ukazatel na kritický oddíl. `Type`je definována jako `typedef CRITICAL_SECTION* Type;`.

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                       | Popis
---------------------------------------------------------- | -----------------
[CriticalSectionTraits::GetInvalidValue](#getinvalidvalue) | Specializuje šablonu `CriticalSection` tak, aby šablona byla vždy neplatná.
[CriticalSectionTraits::Odemknout](#unlock)                   | Specializuje šablonu `CriticalSection` tak, aby podporovala uvolnění vlastnictví zadaného objektu kritické ho oddílu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CriticalSectionTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky::HandleTraits

## <a name="criticalsectiontraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>CriticalSectionTraits::GetInvalidValue

Specializuje šablonu `CriticalSection` tak, aby šablona byla vždy neplatná.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí ukazatel na neplatný kritický oddíl.

### <a name="remarks"></a>Poznámky

Modifikátor `Type` je `typedef CRITICAL_SECTION* Type;`definován jako .

## <a name="criticalsectiontraitsunlock"></a><a name="unlock"></a>CriticalSectionTraits::Odemknout

Specializuje šablonu `CriticalSection` tak, aby podporovala uvolnění vlastnictví zadaného objektu kritické ho oddílu.

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Parametry

*Cs*<br/>
Ukazatel na objekt kritického řezu.

### <a name="remarks"></a>Poznámky

Modifikátor `Type` je `typedef CRITICAL_SECTION* Type;`definován jako .

Další informace naleznete v **tématu LeaveCriticalSection funkce** v části **funkce synchronizace** v dokumentaci rozhraní API systému Windows.
