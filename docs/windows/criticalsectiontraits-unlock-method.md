---
title: Criticalsectiontraits::Unlock – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 8fb382f5-6eda-407e-9673-71d77bda4962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 003bb9c845ef8124ade1262a25368d3d4cb34fa6
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606428"
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock – metoda

Se specializuje `CriticalSection` šablony tak, že podporuje uvolňující vlastnictví objektu zadaného kritický oddíl.

## <a name="syntax"></a>Syntaxe

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Parametry

*cs*  
Ukazatel na objekt kritický oddíl.

## <a name="remarks"></a>Poznámky

`Type` Modifikátor je definován jako `typedef CRITICAL_SECTION* Type;`.

Další informace najdete v tématu **LeaveCriticalSection funkce** v **funkce synchronizace** část dokumentace k rozhraní API Windows.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Viz také

[CriticalSectionTraits – struktura](../windows/criticalsectiontraits-structure.md)