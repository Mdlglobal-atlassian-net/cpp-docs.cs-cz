---
title: task_handle – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
dev_langs:
- C++
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f93bd91453b6edc27e9e68413e1944b258a91757
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059742"
---
# <a name="taskhandle-class"></a>task_handle – třída
`task_handle` Třída představuje jednotlivé paralelní pracovní položku. Zapouzdřuje pokynů a data potřebná k provedení práce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<
    typename _Function  
>  
class task_handle : public ::Concurrency::details::_UnrealizedChore;  
```  
  
#### <a name="parameters"></a>Parametry  
*_Function*<br/>
Typ objektu funkce, která bude volána k provedení práce reprezentována `task_handle` objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[task_handle](#ctor)|Sestaví nový `task_handle` objektu. Pracovní úloha provádí volání funkce zadat jako parametr do konstruktoru.|  
|[~task_handle Destructor](#dtor)|Odstraní `task_handle` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Operator()](#task_handle__operator_call)|Operátor volání funkce, která volá modul runtime pro provedení úlohy popisovače.|  
  
## <a name="remarks"></a>Poznámky  
 `task_handle` objekty lze použít ve spojení s `structured_task_group` nebo obecnějším `task_group` objektu k rozložení práce na paralelní úlohy. Další informace najdete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Všimněte si, že Autor `task_handle` objekt je odpovědná za správu životního cyklu vytvořeného `task_handle` objektu, dokud ho už není nutné v Concurrency Runtime. Obvykle to znamená, že `task_handle` objektu nesmí destrukce dokud buď `wait` nebo `run_and_wait` metodu `task_group` nebo `structured_task_group` na kterém je zařazeno do fronty byla volána.  
  
 `task_handle` objekty se obvykle používají ve spojení s lambda výrazy jazyka C++. Protože si nejste jisti skutečný typ výrazu lambda, [make_task –](concurrency-namespace-functions.md#make_task) funkce se obvykle používá k vytvoření `task_handle` objektu.  
  
 Modul runtime vytvoří kopii pracovní funkce, které můžete předat `task_handle` objektu. Proto objekt změny stavu, ke kterým dochází ve funkci předání `task_handle` objektu se nezobrazí v kopii tohoto objektu funkce.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `task_handle`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppl.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="task_handle__operator_call"></a> Operator() 

 Operátor volání funkce, která volá modul runtime pro provedení úlohy popisovače.  
  
```  
void operator()() const;

 
```  
  
##  <a name="task_handle__ctor"></a> task_handle – 

 Sestaví nový `task_handle` objektu. Pracovní úloha provádí volání funkce zadat jako parametr do konstruktoru.  
  
```  
task_handle(const _Function& _Func);
```  
  
### <a name="parameters"></a>Parametry  
*_Func*<br/>
Funkce, která bude volána k provedení práce reprezentována `task_handle` objektu. To může být funktor lambda, ukazatele na funkci, nebo žádný objekt, který podporuje verzi operátoru volání funkce s podpisem `void operator()()`.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime vytvoří kopii pracovní funkce, které můžete předat konstruktoru. Proto objekt změny stavu, ke kterým dochází ve funkci předání `task_handle` objektu se nezobrazí v kopii tohoto objektu funkce.  
  
##  <a name="dtor"></a> ~ task_handle – 

 Odstraní `task_handle` objektu.  
  
```  
~task_handle();
```  
  
## <a name="see-also"></a>Viz také  
 [souběžnost Namespace](concurrency-namespace.md)   
 [task_group – třída](task-group-class.md)   
 [structured_task_group – třída](structured-task-group-class.md)
