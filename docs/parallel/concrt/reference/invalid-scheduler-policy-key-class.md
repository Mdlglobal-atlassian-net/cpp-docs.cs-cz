---
title: invalid_scheduler_policy_key – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key::invalid_scheduler_policy_key
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_key class
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b78bc955b43f3b6650f7a2fe654e5920c9cac971
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705169"
---
# <a name="invalidschedulerpolicykey-class"></a>invalid_scheduler_policy_key – třída
Tato třída popisuje výjimka vyvolaná při neplatný nebo je předán neznámý klíč `SchedulerPolicy` konstruktoru objektu, nebo `SetPolicyValue` metodu `SchedulerPolicy` klíč, který je třeba změnit pomocí jiným způsobem, jako je předán objekt `SetConcurrencyLimits` metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class invalid_scheduler_policy_key : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[invalid_scheduler_policy_key](#ctor)|Přetíženo. Vytvoří `invalid_scheduler_policy_key` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `invalid_scheduler_policy_key`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> invalid_scheduler_policy_key 

 Vytvoří `invalid_scheduler_policy_key` objektu.  
  
```
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popisný zpráva o chybě.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [SchedulerPolicy – třída](schedulerpolicy-class.md)
