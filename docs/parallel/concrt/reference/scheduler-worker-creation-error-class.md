---
title: "scheduler_worker_creation_error – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
dev_langs: C++
helpviewer_keywords: scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0a628d0ce3d85a2bdcae9c7d25550cbd36386e67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="schedulerworkercreationerror-class"></a>scheduler_worker_creation_error – třída
Tato třída popisuje výjimce z důvodu selhání při vytváření kontextu spuštění pracovního procesu v Concurrency Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[scheduler_worker_creation_error](#ctor)|Přetíženo. Vytvoří `scheduler_worker_creation_error` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato výjimka se obvykle vyvolá, když selže volání operačního systému k vytvoření kontextů provádění z v Concurrency Runtime. Kontexty provádění jsou vláken, které se spouští úlohy v Concurrency Runtime. Kód chyby, která by za normálních okolností vrácená z volání metody Win32 `GetLastError` jsou převedeny na hodnotu typu `HRESULT` a můžete načíst pomocí metody třídy base `get_error_code`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)  
  
 `scheduler_worker_creation_error`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a>scheduler_worker_creation_error 

 Vytvoří `scheduler_worker_creation_error` objektu.  
  
```
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popisný zpráva o chybě.  
  
 `_Hresult`  
 `HRESULT` Hodnotu chyby, který způsobil výjimku.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)
