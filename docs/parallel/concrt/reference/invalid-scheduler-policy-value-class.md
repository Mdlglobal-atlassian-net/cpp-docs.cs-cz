---
title: invalid_scheduler_policy_value – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: ae46d9f9de26e80a97d4ea2e9a692caec3445c75
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068153"
---
# <a name="invalidschedulerpolicyvalue-class"></a>invalid_scheduler_policy_value – třída
Tato třída popisuje výjimku vyvolanou při klíč zásady `SchedulerPolicy` objektu je nastavena na neplatnou hodnotu pro daný klíč.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class invalid_scheduler_policy_value : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[invalid_scheduler_policy_value –] (invalid-scheduler-policy-thread-specification-class.md#ctor|Přetíženo. Vytvoří `invalid_scheduler_policy_value` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `invalid_scheduler_policy_value`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
    
##  <a name="ctor"></a> invalid_scheduler_policy_value – 

 Vytvoří `invalid_scheduler_policy_value` objektu.  
  
```
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```  
  
### <a name="parameters"></a>Parametry  
*_TEXT*<br/>
Popisná zpráva chyby.  
  

## <a name="see-also"></a>Viz také  
 [souběžnost Namespace](concurrency-namespace.md)   
 [SchedulerPolicy – třída](schedulerpolicy-class.md)
