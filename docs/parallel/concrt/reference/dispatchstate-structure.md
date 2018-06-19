---
title: Dispatchstate – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
dev_langs:
- C++
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89d3b62248d305e6acebdc8a03b7ef48c2910b28
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691063"
---
# <a name="dispatchstate-structure"></a>DispatchState – struktura
`DispatchState` Struktura se používá k přenosu stavu, `IExecutionContext::Dispatch` metoda. Je popsaný v případech, ve kterém `Dispatch` metoda je volána `IExecutionContext` rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct DispatchState;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Dispatchstate::dispatchstate –](#ctor)|Vytvoří nový `DispatchState` objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Dispatchstate::m_dispatchstatesize –](#m_dispatchstatesize)|Velikost tato struktura, která se používá pro správu verzí.|  
|[DispatchState::m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Informuje, zda tento kontext přešla `Dispatch` metoda blokovanému předchozí kontext asynchronně. To se používá pouze v kontextu plánování UMS a je nastaven na hodnotu `0` pro všechny ostatní kontexty provádění.|  
|[DispatchState::m_reserved](#m_reserved)|Služba BITS vyhrazena pro budoucí informace předávání.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `DispatchState`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a>  Dispatchstate::dispatchstate – konstruktor  
 Vytvoří nový `DispatchState` objektu.  
  
```
DispatchState();
```  
  
##  <a name="m_dispatchstatesize"></a>  Dispatchstate::m_dispatchstatesize – datový člen  
 Velikost tato struktura, která se používá pro správu verzí.  
  
```
unsigned long m_dispatchStateSize;
```  
  
##  <a name="m_fispreviouscontextasynchronouslyblocked"></a>  Dispatchstate::m_fispreviouscontextasynchronouslyblocked – datový člen  
 Informuje, zda tento kontext přešla `Dispatch` metoda blokovanému předchozí kontext asynchronně. To se používá pouze v kontextu plánování UMS a je nastaven na hodnotu `0` pro všechny ostatní kontexty provádění.  
  
```
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```  
  
##  <a name="m_reserved"></a>  Dispatchstate::m_reserved – datový člen  
 Služba BITS vyhrazena pro budoucí informace předávání.  
  
```
unsigned int m_reserved : 31;
```  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
