---
title: scheduler_worker_creation_error – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
dev_langs:
- C++
helpviewer_keywords:
- scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 077c5a52cf7ac8383fa3b917b3d53867e19ca370
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686422"
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
  
##  <a name="ctor"></a> scheduler_worker_creation_error 

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
 [concurrency – obor názvů](concurrency-namespace.md)
