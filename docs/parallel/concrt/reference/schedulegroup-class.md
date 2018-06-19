---
title: ScheduleGroup – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
dev_langs:
- C++
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf679abbeb1134332d98ef0bd2ba8f2b845d30a4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688684"
---
# <a name="schedulegroup-class"></a>ScheduleGroup – třída
Představuje abstrakci pro skupinu plánu. Skupiny plánů uspořádání sady souvisejících pracovních této výhody z naplánován blízko sebe, buď dočasně, a to spuštěním jiná úloha ve stejné skupině před přesunutím do jiné skupiny, nebo jinými objekty, spuštěním více položek v jedné skupině na stejné Nebo soket fyzického uzlu NUMA.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class ScheduleGroup;
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[~ScheduleGroup Destructor](#dtor)||  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[ID](#id)|Vrátí identifikátor skupiny plán, který je v rámci scheduler, do které patří skupině jedinečné.|  
|[Referenční informace](#reference)|Zvýší počet odkazů skupiny plánu.|  
|[Vydaná verze](#release)|Snižuje počet referenční příručka skupiny plánovače.|  
|[Scheduletask –](#scheduletask)|Naplánuje úlohu šedé – v rámci skupiny pro plán.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ScheduleGroup`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="id"></a> ID 

 Vrátí identifikátor skupiny plán, který je v rámci scheduler, do které patří skupině jedinečné.  
  
```
virtual unsigned int Id() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor skupiny plán, který je v rámci scheduler, do které patří skupině jedinečné.  
  
##  <a name="operator_delete"></a> delete – operátor 

 A `ScheduleGroup` objekt zničena interně modulem runtime při vydání všechny externí odkazy na ni. Nelze explicitně odstranit.  
  
```
void operator delete(
    void* _PObject);

void operator delete(
    void* _PObject,
    int,
 const char *,
    int);
```    
  
### <a name="parameters"></a>Parametry  
 `_PObject`  
 Ukazatel na objekt, který má být odstraněna.  
  
##  <a name="reference"></a> Referenční dokumentace 

 Zvýší počet odkazů skupiny plánu.  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet nově zvýšena odkazů.  
  
### <a name="remarks"></a>Poznámky  
 To se obvykle používá ke správě životnost skupině plán pro složení. Když počet odkazů skupiny plánu klesne na nulu, je plán skupinu odstranit modulem runtime. Plán skupinu vytvořit buď pomocí [currentscheduler::createschedulegroup –](currentscheduler-class.md#createschedulegroup) metody nebo [Scheduler::createschedulegroup –](scheduler-class.md#createschedulegroup) metoda začíná se odkaz započítává jako jeden.  
  
##  <a name="release"></a> Verze 

 Snižuje počet referenční příručka skupiny plánovače.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet nově odečte odkazů.  
  
### <a name="remarks"></a>Poznámky  
 To se obvykle používá ke správě životnost skupině plán pro složení. Když počet odkazů skupiny plánu klesne na nulu, je plán skupinu odstranit modulem runtime. Po můžete volat `Release` metoda konkrétní počet opakování odebrat vytvoření odkazovat počet a všechny další odkazy umístěna pomocí `Reference` metoda, nemůže využít další skupině plán. Díky tomu bude mít za následek nedefinované chování.  
  
 Skupinu plán je přidružen instance konkrétní plánovače. Je nutné zajistit, že všechny odkazy na skupiny plán uvolnění před všechny odkazy na Plánovač vydávají, vzhledem k tomu může dojít v Plánovači bude zrušeno. Provádění jinak za následek nedefinované chování.  
  
##  <a name="dtor"></a> ~ ScheduleGroup 

```
virtual ~ScheduleGroup();
```  
  
##  <a name="scheduletask"></a> Scheduletask – 

 Naplánuje úlohu šedé – v rámci skupiny pro plán.  
  
```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Proc`  
 Ukazatel na funkci provést k provedení úkolu šedé –.  
  
 `_Data`  
 Neplatný ukazatel na data, která se předají jako parametr k tělu úlohy.  
  
### <a name="remarks"></a>Poznámky  
 Volání `ScheduleTask` metoda implicitně umístí počet odkazů na skupině plán, který je odebraný modulem runtime v příslušnou dobu, po provedení úlohy.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [CurrentScheduler – třída](currentscheduler-class.md)   
 [Scheduler – třída](scheduler-class.md)   
 [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



