---
title: invalid_scheduler_policy_value – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec11d7ebc7d2c074344e9651a7c548fe1ad01943
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689724"
---
# <a name="invalidschedulerpolicyvalue-class"></a>invalid_scheduler_policy_value – třída
Tato třída popisuje výjimka vyvolaná při zásad klíč `SchedulerPolicy` je nastavena na neplatnou hodnotu pro tento klíč.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class invalid_scheduler_policy_value : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[invalid_scheduler_policy_value] (invalid-scheduler-policy-thread-specification-class.md#ctor|Přetíženo. Vytvoří `invalid_scheduler_policy_value` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `invalid_scheduler_policy_value`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
    
##  <a name="ctor"></a> invalid_scheduler_policy_value 

 Vytvoří `invalid_scheduler_policy_value` objektu.  
  
```
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popisný zpráva o chybě.  
  

## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [SchedulerPolicy – třída](schedulerpolicy-class.md)
