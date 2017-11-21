---
title: "Criticalsectiontraits – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
dev_langs: C++
helpviewer_keywords: CriticalSectionTraits structure
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 95428e0513193c78f135157b09a354e050014f23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|`Type`|A `typedef` , který definuje ukazatel na kritické část. `Type`je definován jako `typedef CRITICAL_SECTION* Type;`.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Criticalsectiontraits::getinvalidvalue – metoda](../windows/criticalsectiontraits-getinvalidvalue-method.md)|Se specializuje šablonu CriticalSection tak, aby šablona vždy je neplatná.|  
|[Criticalsectiontraits::Unlock – metoda](../windows/criticalsectiontraits-unlock-method.md)|Se specializuje šablonu CriticalSection tak, aby podporoval uvolnit vlastnictví objektu zadaného kritická sekce.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CriticalSectionTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [Namespace Microsoft::WRL::Wrappers::HandleTraits](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)