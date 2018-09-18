---
title: nested_scheduler_missing_detach – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
dev_langs:
- C++
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3887672f9d0934dbcc38d6db549e383f7976b10
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110975"
---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach – třída
Tato třída popisuje výjimku vyvolanou při modulu Runtime souběžnosti zjistí, že opominul volání `CurrentScheduler::Detach` metody u objektu context, který připojuje k druhé pomocí plánovače `Attach` metodu `Scheduler` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class nested_scheduler_missing_detach : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[nested_scheduler_missing_detach](#ctor)|Přetíženo. Vytvoří `nested_scheduler_missing_detach` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato výjimka je vyvolána pouze v případě, že byste vnořit jeden Plánovač uvnitř jiného voláním `Attach` metodu `Scheduler` objektu v kontextu, který je již vlastněn nebo připojené k jiné plánovače. Modul Concurrency Runtime vyvolá tuto výjimku tj při scénáři může zjistit jako vodítko k vyhledání problém. Ne každá instance zanedbání volat `CurrentScheduler::Detach` je zaručeno, že metoda vyvolávají tuto výjimku.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `nested_scheduler_missing_detach`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> nested_scheduler_missing_detach – 

 Vytvoří `nested_scheduler_missing_detach` objektu.  
  
```
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```  
  
### <a name="parameters"></a>Parametry  
*_TEXT*<br/>
Popisná zpráva chyby.  
  
## <a name="see-also"></a>Viz také  
 [souběžnost Namespace](concurrency-namespace.md)   
 [Scheduler – třída](scheduler-class.md)
