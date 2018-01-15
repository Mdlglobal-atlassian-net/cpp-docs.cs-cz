---
title: "invalid_multiple_scheduling – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
dev_langs: C++
helpviewer_keywords: invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa021ec655162cb75837ac1475e5cb9094f79fa8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="invalidmultiplescheduling-class"></a>invalid_multiple_scheduling – třída
Tato třída popisuje výjimka vyvolaná při `task_handle` objekt je naplánované vícekrát používá `run` metodu `task_group` nebo `structured_task_group` objektu bez použité volání buď `wait` nebo `run_and_wait` metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class invalid_multiple_scheduling : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[invalid_multiple_scheduling](#ctor)|Přetíženo. Vytvoří `invalid_multiple_scheduling` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `invalid_multiple_scheduling`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a>invalid_multiple_scheduling 

 Vytvoří `invalid_multiple_scheduling` objektu.  
  
```
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popisný zpráva o chybě.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [task_handle – třída](task-handle-class.md)   
 [task_group – třída](task-group-class.md)   
 [Spustit](task-group-class.md)   
 [Počkej](task-group-class.md)   
 [run_and_wait –](task-group-class.md)   
 [structured_task_group – třída](structured-task-group-class.md)
