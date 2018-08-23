---
title: Criticalsectiontraits – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
dev_langs:
- C++
helpviewer_keywords:
- CriticalSectionTraits structure
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6d15f65ecc2253556a6812cfb90ef78f90c7fb29
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594731"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits – struktura

Se specializuje `CriticalSection` objektu pro podporu neplatný kritický oddíl nebo funkci uvolnění kritický oddíl.

## <a name="syntax"></a>Syntaxe

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`Type`|A **typedef** , který definuje ukazatel na kritický oddíl. `Type` je definován jako `typedef CRITICAL_SECTION* Type;`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CriticalSectionTraits::GetInvalidValue – metoda](../windows/criticalsectiontraits-getinvalidvalue-method.md)|Se specializuje `CriticalSection` šablony tak, aby šablona vždy je neplatná.|
|[CriticalSectionTraits::Unlock – metoda](../windows/criticalsectiontraits-unlock-method.md)|Se specializuje `CriticalSection` šablony tak, že podporuje uvolňující vlastnictví objektu zadaného kritický oddíl.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CriticalSectionTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers::HandleTraits – obor názvů](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)