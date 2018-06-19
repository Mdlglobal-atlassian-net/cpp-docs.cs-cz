---
title: nested_scheduler_missing_detach – třída | Microsoft Docs
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
ms.openlocfilehash: 26027693209bc5b4687686efeae5d190ed374607
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687358"
---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach – třída
Tato třída popisuje výjimka vyvolaná při Concurrency Runtime zjistí, že nevrátil volání `CurrentScheduler::Detach` metoda v kontextu, který je připojen k druhý plánovače pomocí `Attach` metodu `Scheduler` objektu.  
  
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
 Tato výjimka je vyvolána, pouze v případě, že vnořit jeden scheduler uvnitř jiné voláním `Attach` metodu `Scheduler` objektu v kontextu, který je již vlastněn nebo připojený k jiné plánovače. Když tento scénář může zjistit jako pomůcku při hledání problém, Concurrency Runtime vyvolá výjimku tj. Ne všechny instance řetězce zanedbání volání `CurrentScheduler::Detach` metoda záruku, že má být vyvolána výjimka.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `nested_scheduler_missing_detach`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> nested_scheduler_missing_detach 

 Vytvoří `nested_scheduler_missing_detach` objektu.  
  
```
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popisný zpráva o chybě.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Scheduler – třída](scheduler-class.md)
