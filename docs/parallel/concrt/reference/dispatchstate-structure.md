---
title: "Dispatchstate – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
dev_langs: C++
helpviewer_keywords: DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a6997596876f080ea00611af90d05eb4fddd2857
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|[Dispatchstate::m_fispreviouscontextasynchronouslyblocked –](#m_fispreviouscontextasynchronouslyblocked)|Informuje, zda tento kontext přešla `Dispatch` metoda blokovanému předchozí kontext asynchronně. To se používá pouze v kontextu plánování UMS a je nastaven na hodnotu `0` pro všechny ostatní kontexty provádění.|  
|[Dispatchstate::m_reserved –](#m_reserved)|Služba BITS vyhrazena pro budoucí informace předávání.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `DispatchState`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a>Dispatchstate::dispatchstate – konstruktor  
 Vytvoří nový `DispatchState` objektu.  
  
```
DispatchState();
```  
  
##  <a name="m_dispatchstatesize"></a>Dispatchstate::m_dispatchstatesize – datový člen  
 Velikost tato struktura, která se používá pro správu verzí.  
  
```
unsigned long m_dispatchStateSize;
```  
  
##  <a name="m_fispreviouscontextasynchronouslyblocked"></a>Dispatchstate::m_fispreviouscontextasynchronouslyblocked – datový člen  
 Informuje, zda tento kontext přešla `Dispatch` metoda blokovanému předchozí kontext asynchronně. To se používá pouze v kontextu plánování UMS a je nastaven na hodnotu `0` pro všechny ostatní kontexty provádění.  
  
```
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```  
  
##  <a name="m_reserved"></a>Dispatchstate::m_reserved – datový člen  
 Služba BITS vyhrazena pro budoucí informace předávání.  
  
```
unsigned int m_reserved : 31;
```  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)
