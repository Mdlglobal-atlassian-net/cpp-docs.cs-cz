---
title: default_scheduler_exists – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists::default_scheduler_exists
dev_langs:
- C++
helpviewer_keywords:
- default_scheduler_exists class
ms.assetid: f6e575e2-4e0f-455a-9e06-54f462ce0c1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 488f1d08c089b159971834729596d74b4e3dab22
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106042"
---
# <a name="defaultschedulerexists-class"></a>default_scheduler_exists – třída
Tato třída popisuje výjimku vyvolána, když `Scheduler::SetDefaultSchedulerPolicy` metoda se volá, když je výchozím plánovačem již existuje v rámci procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class default_scheduler_exists : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[default_scheduler_exists](#ctor)|Přetíženo. Vytvoří `default_scheduler_exists` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `default_scheduler_exists`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> default_scheduler_exists – 

 Vytvoří `default_scheduler_exists` objektu.  
  
```
explicit _CRTIMP default_scheduler_exists(_In_z_ const char* _Message) throw();

default_scheduler_exists() throw();
```  
  
### <a name="parameters"></a>Parametry  
*_TEXT*<br/>
Popisná zpráva chyby.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
