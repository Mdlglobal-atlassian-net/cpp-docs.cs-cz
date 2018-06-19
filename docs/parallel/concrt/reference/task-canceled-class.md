---
title: task_canceled – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- task_canceled
- CONCRT/concurrency::task_canceled
- CONCRT/concurrency::task_canceled::task_canceled
dev_langs:
- C++
helpviewer_keywords:
- task_canceled class
ms.assetid: c3f0b234-2cc1-435f-a48e-995f45b190be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f535a4cce75d388437025967b9c0c9b1ae0fd7a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690244"
---
# <a name="taskcanceled-class"></a>task_canceled – třída
Tato třída popisuje výjimka vyvolaná objektem vrstvě PPL úlohy, aby vynutil aktuální úlohu zrušit. Je také vyvolané `get()` metodu [úloh](/visualstudio/extensibility/debugger/task-class-internal-members), zrušené úlohy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class task_canceled : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[task_canceled](#ctor)|Přetíženo. Vytvoří `task_canceled` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `task_canceled`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> task_canceled 

 Vytvoří `task_canceled` objektu.  
  
```
explicit _CRTIMP task_canceled(_In_z_ const char* _Message) throw();

task_canceled() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popisný zpráva o chybě.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
