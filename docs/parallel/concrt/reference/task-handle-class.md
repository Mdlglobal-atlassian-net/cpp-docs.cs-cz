---
title: "task_handle – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
dev_langs: C++
helpviewer_keywords: task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 358d217a131ec3e282775604619f1ff265baf490
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="taskhandle-class"></a>task_handle – třída
`task_handle` Třída reprezentuje jednotlivé paralelní pracovní položku. Zapouzdřit pokynů a data potřebná k provedení práce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<
    typename _Function  
>  
class task_handle : public ::Concurrency::details::_UnrealizedChore;  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ objektu funkce, která bude volána k provedení práce reprezentována `task_handle` objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[task_handle](#ctor)|Vytvoří nový `task_handle` objektu. Pracovní úlohy provádí volání funkce určené jako parametr pro konstruktor.|  
|[~ task_handle – destruktor](#dtor)|Zničí `task_handle` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Operator() –](#task_handle__operator_call)|Operátor volání funkce, který vyvolá modulu runtime pro práci popisovače úloh.|  
  
## <a name="remarks"></a>Poznámky  
 `task_handle`objekty lze použít ve spojení s `structured_task_group` nebo další Obecné `task_group` objektu, k rozložení práce do paralelních úloh. Další informace najdete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Všimněte si, že tvůrce `task_handle` objekt zodpovídá za údržbu životnost vytvořený `task_handle` objektu, dokud je už vyžadovanou Concurrency Runtime. Obvykle to znamená, že `task_handle` objekt nesmí destruct dokud buď `wait` nebo `run_and_wait` metodu `task_group` nebo `structured_task_group` na kterém je uložený ve frontě byla volána.  
  
 `task_handle`objekty jsou obvykle používány ve spojení s C++ lambdas. Protože neznáte true typ lambda, [make_task –](concurrency-namespace-functions.md#make_task) funkce se obvykle používá k vytvoření `task_handle` objektu.  
  
 Modul runtime vytvoří kopii pracovní funkce, která můžete předat `task_handle` objektu. Proto změny stavu, ke kterým dochází ve funkci objektu je předat do `task_handle` objektu se nebude zobrazovat na vaší kopie tohoto objektu funkce.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `task_handle`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppl.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="task_handle__operator_call"></a>Operator() – 

 Operátor volání funkce, který vyvolá modulu runtime pro práci popisovače úloh.  
  
```  
void operator()() const;

 
```  
  
##  <a name="task_handle__ctor"></a>task_handle 

 Vytvoří nový `task_handle` objektu. Pracovní úlohy provádí volání funkce určené jako parametr pro konstruktor.  
  
```  
task_handle(const _Function& _Func);
```  
  
### <a name="parameters"></a>Parametry  
 `_Func`  
 Funkce, která bude volána k provedení práce reprezentována `task_handle` objektu. To může být functor lambda, ukazatel na funkci, nebo žádný objektu, která podporuje verzi operátor volání funkce s podpisem `void operator()()`.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime vytvoří kopii pracovní funkce, která je předat do konstruktoru. Proto změny stavu, ke kterým dochází ve funkci objektu je předat do `task_handle` objektu se nebude zobrazovat na vaší kopie tohoto objektu funkce.  
  
##  <a name="dtor"></a>~ task_handle 

 Zničí `task_handle` objektu.  
  
```  
~task_handle();
```  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [task_group – třída](task-group-class.md)   
 [structured_task_group – třída](structured-task-group-class.md)
