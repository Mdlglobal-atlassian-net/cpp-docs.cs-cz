---
title: ScheduleGroup – třída
ms.date: 11/04/2016
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
ms.openlocfilehash: ce7734a1330f2d6e495565338879764482439d09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337541"
---
# <a name="schedulegroup-class"></a>ScheduleGroup – třída

Představuje abstrakci pro skupinu plánování. Skupiny plánování organizují sadu souvisejících prací, které mají výhody z plánovány blízko sebe, buď časově, prováděním jiné úlohy ve stejné skupině před přesunutím do jiné skupiny, nebo prostorově, prováděním více položek ve stejné skupině na stejném Uzel NUMA nebo fyzickém soketu.

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
|[ID](#id)|Vrátí identifikátor plánu skupiny, který je jedinečný v rámci plánovače, do kterého skupina patří.|
|[Referenční informace](#reference)|Zvýší počet odkazů skupiny plánu.|
|[Vydaná verze](#release)|Sníží počet referenční skupiny plánovače.|
|[Scheduletask –](#scheduletask)|Naplánuje lehký úkol ve skupině plánování.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ScheduleGroup`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="id"></a> Id

Vrátí identifikátor plánu skupiny, který je jedinečný v rámci plánovače, do kterého skupina patří.

```
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor plánu skupiny, který je jedinečný v rámci plánovače, do kterého skupina patří.

##  <a name="operator_delete"></a> delete – operátor

A `ScheduleGroup` objekt je zničen interně modulem runtime při vydání všechny externí odkazy na něj. Nelze odstranit explicitně.

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

*_PObject*<br/>
Ukazatel na objekt, který má být odstraněna.

##  <a name="reference"></a> Referenční dokumentace

Zvýší počet odkazů skupiny plánu.

```
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet nově zvýšena odkazů.

### <a name="remarks"></a>Poznámky

To se obvykle používá ke správě životnosti skupiny plánu složení. Když počet odkazů skupiny plánu klesne na nulu, plán skupina se odstranila modulem runtime. Plán skupiny vytvořené pomocí buď [currentscheduler::createschedulegroup –](currentscheduler-class.md#createschedulegroup) metodu, nebo [Scheduler::createschedulegroup –](scheduler-class.md#createschedulegroup) metoda začíná počet odkazů jednoho.

##  <a name="release"></a> Vydání verze

Sníží počet referenční skupiny plánovače.

```
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na nově snížen počet.

### <a name="remarks"></a>Poznámky

To se obvykle používá ke správě životnosti skupiny plánu složení. Když počet odkazů skupiny plánu klesne na nulu, plán skupina se odstranila modulem runtime. Poté, co jste volali `Release` konkrétní počet, kolikrát se odebrat vytváření odkaz na metodu počet a všechny další odkazy umístěna pomocí `Reference` metody, nemůže využít další skupinu plánu. To způsobí nedefinované chování.

Skupinu plánování souvisí s instance určitého plánovače. Ujistěte se, že všechny odkazy na skupinu plánu se vydávají před jsou všechny odkazy na Plánovač, protože může dojít v Plánovači rušení. Provádí se jinak za následek nedefinované chování.

##  <a name="dtor"></a> ~ScheduleGroup

```
virtual ~ScheduleGroup();
```

##  <a name="scheduletask"></a> Scheduletask –

Naplánuje lehký úkol ve skupině plánování.

```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```

### <a name="parameters"></a>Parametry

*_Proc*<br/>
Ukazatel na funkci, která se má spustit provádění těla lehký úkol.

*_Data*<br/>
Ukazatel void data, která se předá jako parametr do těla úkolu.

### <a name="remarks"></a>Poznámky

Volání `ScheduleTask` metoda implicitně umístí počet odkazů skupiny plánu, který bude odebrán modulem runtime v příslušnou dobu, po spuštění úlohy.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[CurrentScheduler – třída](currentscheduler-class.md)<br/>
[Scheduler – třída](scheduler-class.md)<br/>
[Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
