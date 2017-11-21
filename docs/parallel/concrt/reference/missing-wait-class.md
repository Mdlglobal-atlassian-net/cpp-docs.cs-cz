---
title: "missing_wait – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
dev_langs: C++
helpviewer_keywords: missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ab27107ad76e77601286b77ad28e90b69fa0411e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="missingwait-class"></a>missing_wait – třída
Tato třída popisuje výjimka vyvolaná při stále naplánované úlohy `task_group` nebo `structured_task_group` objektu v době tento objekt destruktor. Tato výjimka bude vyvolána nikdy Pokud destruktoru je dostupný z důvodu unwinding v důsledku výjimky zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class missing_wait : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[missing_wait](#ctor)|Přetíženo. Vytvoří `missing_wait` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Chybějící výjimka tok, jste odpovědni za volání buď `wait` nebo `run_and_wait` metodu `task_group` nebo `structured_task_group` objekt před povolením tento objekt, který chcete destruct. Modul runtime vyvolá výjimku jako znamená, že jste zapomněli k volání `wait` nebo `run_and_wait` metoda.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `missing_wait`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a>missing_wait 

 Vytvoří `missing_wait` objektu.  
  
```
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popisný zpráva o chybě.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [task_group – třída](task-group-class.md)   
 [Počkej](task-group-class.md)   
 [run_and_wait –](task-group-class.md)   
 [structured_task_group – třída](structured-task-group-class.md)
