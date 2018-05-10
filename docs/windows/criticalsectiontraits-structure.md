---
title: Criticalsectiontraits – struktura | Microsoft Docs
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
ms.openlocfilehash: 5534173d594b8fc09ceca8ec44a1c1223bc550b2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits – struktura
Se specializuje objekt CriticalSection pro podporu neplatný kritická sekce nebo funkce, která se verze kritická sekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CriticalSectionTraits;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`Type`|A `typedef` , který definuje ukazatel na kritické část. `Type` je definován jako `typedef CRITICAL_SECTION* Type;`.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CriticalSectionTraits::GetInvalidValue – metoda](../windows/criticalsectiontraits-getinvalidvalue-method.md)|Se specializuje šablonu CriticalSection tak, aby šablona vždy je neplatná.|  
|[CriticalSectionTraits::Unlock – metoda](../windows/criticalsectiontraits-unlock-method.md)|Se specializuje šablonu CriticalSection tak, aby podporoval uvolnit vlastnictví objektu zadaného kritická sekce.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CriticalSectionTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers::HandleTraits – obor názvů](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)