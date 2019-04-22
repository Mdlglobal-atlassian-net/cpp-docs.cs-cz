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
ms.openlocfilehash: ce904ecbd9a5855c63fd43f07f88c215cef544ae
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786854"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits – struktura

Se specializuje `CriticalSection` objektu pro podporu neplatný kritický oddíl nebo funkci uvolnění kritický oddíl.

## <a name="syntax"></a>Syntaxe

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Name   | Popis
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | A `typedef` , který definuje ukazatel na kritický oddíl. `Type` je definován jako `typedef CRITICAL_SECTION* Type;`.

### <a name="public-methods"></a>Veřejné metody

Name                                                       | Popis
---------------------------------------------------------- | -----------------
[Criticalsectiontraits::getinvalidvalue –](#getinvalidvalue) | Se specializuje `CriticalSection` šablony tak, aby šablona vždy je neplatná.
[Criticalsectiontraits::Unlock –](#unlock)                   | Se specializuje `CriticalSection` šablony tak, že podporuje uvolňující vlastnictví objektu zadaného kritický oddíl.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CriticalSectionTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>Criticalsectiontraits::getinvalidvalue –

Se specializuje `CriticalSection` šablony tak, aby šablona vždy je neplatná.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí ukazatel na neplatný kritický oddíl.

### <a name="remarks"></a>Poznámky

`Type` Modifikátor je definován jako `typedef CRITICAL_SECTION* Type;`.

## <a name="unlock"></a>Criticalsectiontraits::Unlock –

Se specializuje `CriticalSection` šablony tak, že podporuje uvolňující vlastnictví objektu zadaného kritický oddíl.

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Parametry

*cs*<br/>
Ukazatel na objekt kritický oddíl.

### <a name="remarks"></a>Poznámky

`Type` Modifikátor je definován jako `typedef CRITICAL_SECTION* Type;`.

Další informace najdete v tématu **LeaveCriticalSection funkce** v **funkce synchronizace** část dokumentace k rozhraní API Windows.
