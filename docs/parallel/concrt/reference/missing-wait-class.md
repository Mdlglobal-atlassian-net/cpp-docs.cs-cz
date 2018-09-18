---
title: missing_wait – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
dev_langs:
- C++
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2a44cbdb5abeed7d5dbd7be7dfaba37ba1d0145
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024944"
---
# <a name="missingwait-class"></a>missing_wait – třída
Tato třída popisuje výjimku vyvolanou při stále naplánované úlohy `task_group` nebo `structured_task_group` objektu v době tento objekt destruktor. Tato výjimka bude vyvolána nikdy destruktor při dosažení z důvodu výjimky v důsledku uvolnění zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class missing_wait : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[missing_wait –](#ctor)|Přetíženo. Vytvoří `missing_wait` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Chybějící výjimka toku, zodpovídáte za volání buď `wait` nebo `run_and_wait` metodu `task_group` nebo `structured_task_group` objekt předtím, než tento objekt k destrukci. Modul runtime vyvolá tuto výjimku jako znamením, že jste zapomněli volání `wait` nebo `run_and_wait` metody.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `missing_wait`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> missing_wait – 

 Vytvoří `missing_wait` objektu.  
  
```
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```  
  
### <a name="parameters"></a>Parametry  
*_TEXT*<br/>
Popisná zpráva chyby.  
  
## <a name="see-also"></a>Viz také  
 [souběžnost Namespace](concurrency-namespace.md)   
 [task_group – třída](task-group-class.md)   
 [Počkej](task-group-class.md)   
 [run_and_wait –](task-group-class.md)   
 [structured_task_group – třída](structured-task-group-class.md)
