---
title: invalid_scheduler_policy_key – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 1e7dc90ce1ff04d3d02aed13927f137a2b4f7f75
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113289"
---
# <a name="invalidschedulerpolicykey-class"></a>invalid_scheduler_policy_key – třída
Tato třída popisuje výjimku vyvolanou při neplatný nebo je předán neznámý klíč `SchedulerPolicy` konstruktor objektu nebo `SetPolicyValue` metodu `SchedulerPolicy` objekt je předán klíč, který musí být změněno pomocí jiným způsobem, jako `SetConcurrencyLimits` – metoda.  
  
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
  
##  <a name="ctor"></a> invalid_scheduler_policy_key – 

 Vytvoří `invalid_scheduler_policy_key` objektu.  
  
```
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```  
  
### <a name="parameters"></a>Parametry  
*_TEXT*<br/>
Popisná zpráva chyby.  
  
## <a name="see-also"></a>Viz také  
 [souběžnost Namespace](concurrency-namespace.md)   
 [SchedulerPolicy – třída](schedulerpolicy-class.md)
