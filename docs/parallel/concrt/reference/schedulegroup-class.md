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
ms.openlocfilehash: 8686b5ef0906e3188a1e683d1190bbe6124cd19e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417129"
---
# <a name="schedulegroup-class"></a>ScheduleGroup – třída

Představuje abstrakci pro skupinu plánů. Skupiny plánů organizují sadu souvisejících práce, které jsou přínosy pro jejich naplánování, a to buď na konci, spuštěním jiného úkolu ve stejné skupině, než přejdete do jiné skupiny, nebo podle toho, že se ve stejné skupině spustí víc položek ve stejné skupině. Uzel NUMA nebo fyzický soket.

## <a name="syntax"></a>Syntaxe

```cpp
class ScheduleGroup;
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[~ Schedule – destruktor](#dtor)||

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[ID](#id)|Vrátí identifikátor skupiny plánů, který je jedinečný v rámci plánovače, do kterého skupina patří.|
|[Referenční informace](#reference)|Zvýší počet odkazů na skupinu plánu.|
|[Vydaná verze](#release)|Sníží počet odkazů na skupinu plánovače.|
|[ScheduleTask –](#scheduletask)|Naplánuje úlohu s lehkým zatížením v rámci skupiny plánování.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ScheduleGroup`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="id"></a>Účet

Vrátí identifikátor skupiny plánů, který je jedinečný v rámci plánovače, do kterého skupina patří.

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor skupiny plánů, který je jedinečný v rámci plánovače, do kterého patří skupina.

## <a name="operator_delete"></a>delete – operátor

Objekt `ScheduleGroup` je interně zničen modulem runtime při uvolnění všech externích odkazů na něj. Nedá se explicitně odstranit.

```cpp
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
Ukazatel na objekt, který má být odstraněn.

## <a name="reference"></a>Odkaz

Zvýší počet odkazů na skupinu plánu.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nově zvýšený počet odkazů.

### <a name="remarks"></a>Poznámky

Obvykle se používá ke správě životnosti skupiny plánování pro složení. Pokud je počet odkazů skupiny plánování nula, Skupina plánování je odstraněna modulem runtime. Skupina plánu vytvořená pomocí metody [CurrentScheduler:: CreateScheduleGroup –](currentscheduler-class.md#createschedulegroup) nebo metody [Scheduler:: CreateScheduleGroup –](scheduler-class.md#createschedulegroup) začíná s počtem odkazů One.

## <a name="release"></a>Předběžné

Sníží počet odkazů na skupinu plánovače.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nově snížený počet odkazů.

### <a name="remarks"></a>Poznámky

Obvykle se používá ke správě životnosti skupiny plánování pro složení. Pokud je počet odkazů skupiny plánování nula, Skupina plánování je odstraněna modulem runtime. Po volání metody `Release` konkrétního počtu, kolikrát chcete odebrat počet odkazů na vytvoření a všechny další odkazy na základě `Reference` metody, nemůžete skupinu Schedule využít dále. V důsledku toho dojde k nedefinovanému chování.

Skupina plánů je přidružená ke konkrétní instanci plánovače. Je nutné zajistit, aby všechny odkazy na skupinu plánů byly vydány dříve, než budou všechny odkazy na Plánovač vydány, protože by to mohlo způsobit zničení plánovače. V opačném případě způsobí nedefinované chování.

## <a name="dtor"></a>~ Schedule

```cpp
virtual ~ScheduleGroup();
```

## <a name="scheduletask"></a>ScheduleTask –

Naplánuje úlohu s lehkým zatížením v rámci skupiny plánování.

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```

### <a name="parameters"></a>Parametry

*_Proc*<br/>
Ukazatel na funkci, která se má provést, aby provedla tělo úlohy s lehkým zatížením.

*_Data*<br/>
Anulování ukazatele na data, která budou předána do těla úkolu jako parametr.

### <a name="remarks"></a>Poznámky

Volání metody `ScheduleTask` implicitně umístí počet odkazů na skupinu plánování, která je po určitou dobu po provedení úlohy odebrána modulem runtime.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[CurrentScheduler – třída](currentscheduler-class.md)<br/>
[Scheduler – třída](scheduler-class.md)<br/>
[Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
