---
title: Třída plánovače
ms.date: 11/04/2016
f1_keywords:
- Scheduler
- CONCRT/concurrency::Scheduler
- CONCRT/concurrency::Scheduler::Scheduler
- CONCRT/concurrency::Scheduler::Attach
- CONCRT/concurrency::Scheduler::Create
- CONCRT/concurrency::Scheduler::CreateScheduleGroup
- CONCRT/concurrency::Scheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::Scheduler::GetPolicy
- CONCRT/concurrency::Scheduler::Id
- CONCRT/concurrency::Scheduler::IsAvailableLocation
- CONCRT/concurrency::Scheduler::Reference
- CONCRT/concurrency::Scheduler::RegisterShutdownEvent
- CONCRT/concurrency::Scheduler::Release
- CONCRT/concurrency::Scheduler::ResetDefaultSchedulerPolicy
- CONCRT/concurrency::Scheduler::ScheduleTask
- CONCRT/concurrency::Scheduler::SetDefaultSchedulerPolicy
helpviewer_keywords:
- Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
ms.openlocfilehash: 77ad876b8352ab1ae86fde622b05712ec5f2cea9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422113"
---
# <a name="scheduler-class"></a>Třída plánovače

Představuje abstrakci pro Concurrency Runtime Scheduler.

## <a name="syntax"></a>Syntaxe

```cpp
class Scheduler;
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[Scheduler](#ctor)|Objekt třídy `Scheduler` lze vytvořit pouze pomocí metod Factory nebo implicitně.|
|[~ Scheduler – destruktor](#dtor)|Objekt `Scheduler` třídy je implicitně zničen, pokud všechny externí odkazy na něj přestanou existovat.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Attach](#attach)|Připojí Plánovač k volajícímu kontextu. Po návratu této metody bude volající kontext spravován plánovačem a plánovačem se zobrazí aktuální Plánovač.|
|[Vytvoření](#create)|Vytvoří nový Plánovač, jehož chování je popsané parametrem `_Policy`, umístí do plánovače počáteční odkaz a vrátí ukazatel na něj.|
|[CreateScheduleGroup –](#createschedulegroup)|Přetíženo. Vytvoří novou skupinu plánu v rámci plánovače. Verze, která přebírá parametr `_Placement` způsobí, že úlohy v nově vytvořené skupině Schedule budou posunuty ke spuštění v umístění určeném parametrem.|
|[Getnumberofvirtualprocessors –](#getnumberofvirtualprocessors)|Vrátí aktuální počet virtuálních procesorů pro Plánovač.|
|[GetPolicy –](#getpolicy)|Vrátí kopii zásady, se kterou se vytvořil Scheduler.|
|[ID](#id)|Vrátí jedinečný identifikátor plánovače.|
|[Isavailablelocation –](#isavailablelocation)|Určuje, zda je dané umístění k dispozici v plánovači.|
|[Referenční informace](#reference)|Zvýší počet odkazů plánovače.|
|[RegisterShutdownEvent –](#registershutdownevent)|Způsobí, že popisovač události systému Windows předaný parametrem `_Event`, který se má signalizovat, když se Plánovač vypne a zničí sám sebe. V okamžiku signalizace události je dokončena veškerá práce, která byla naplánována do plánovače. Pomocí této metody lze zaregistrovat více událostí vypnutí.|
|[Vydaná verze](#release)|Sníží počet odkazů plánovače.|
|[Resetdefaultschedulerpolicy –](#resetdefaultschedulerpolicy)|Obnoví výchozí zásadu plánovače na výchozí nastavení modulu runtime. Při příštím vytvoření výchozího plánovače použije výchozí nastavení zásad modulu runtime.|
|[ScheduleTask –](#scheduletask)|Přetíženo. Naplánuje v Plánovači úlohu s lehkým zatížením. Úloha s lehkým zatížením bude umístěna do skupiny plánování určené modulem runtime. Verze, která přebírá parametr `_Placement` způsobí, že se úloha na zadaném umístění posune směrem k provedení.|
|[SetDefaultSchedulerPolicy –](#setdefaultschedulerpolicy)|Umožňuje, aby se pro vytvoření výchozího plánovače použila zásada definovaná uživatelem. Tuto metodu lze volat pouze v případě, že v rámci procesu neexistuje žádný výchozí Plánovač. Po nastavení výchozí zásady zůstane v platnosti, dokud nedojde k dalšímu platnému volání metody `SetDefaultSchedulerPolicy` nebo [resetdefaultschedulerpolicy –](#resetdefaultschedulerpolicy) .|

## <a name="remarks"></a>Poznámky

Plánovač Concurrency Runtime používá kontexty spuštění, které se mapují na kontexty provádění operačního systému, jako je například vlákno, a spustí tak pracovní zařazení do fronty v aplikaci. V každém okamžiku se úroveň souběžnosti plánovače rovná počtu virtuálních procesorů, které mu Správce prostředků udělily. Virtuální procesor představuje abstrakci pro zpracování prostředku a mapuje se na hardwarové vlákno v podkladovém systému. U virtuálního procesoru v daném okamžiku může běžet pouze jeden kontext plánovače.

Concurrency Runtime vytvoří výchozí Plánovač pro každý proces, který provede paralelní práci. Kromě toho můžete vytvořit vlastní instance plánovače a manipulovat s ní pomocí této třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Scheduler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="attach"></a>Pojovat

Připojí Plánovač k volajícímu kontextu. Po návratu této metody bude volající kontext spravován plánovačem a plánovačem se zobrazí aktuální Plánovač.

```cpp
virtual void Attach() = 0;
```

### <a name="remarks"></a>Poznámky

Připojení plánovače implicitně umístí odkaz na Plánovač.

V určitém okamžiku v budoucnu musíte zavolat metodu [CurrentScheduler::D etach](currentscheduler-class.md#detach) , aby bylo možné Plánovač vypnout.

Pokud je tato metoda volána z kontextu, který je již připojen k jinému plánovači, existující Plánovač je zapamatovat jako předchozí Plánovač a nově vytvořený Plánovač se bude považovat za aktuálního plánovače. Při volání metody `CurrentScheduler::Detach` v pozdějším bodě bude předchozí Plánovač obnoven jako aktuální Plánovač.

Tato metoda vyvolá výjimku [improper_scheduler_attach](improper-scheduler-attach-class.md) , pokud je tento Plánovač aktuálním plánovačem volajícího kontextu.

## <a name="create"></a>Vytvořeny

Vytvoří nový Plánovač, jehož chování je popsané parametrem `_Policy`, umístí do plánovače počáteční odkaz a vrátí ukazatel na něj.

```cpp
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parametry

*_Policy*<br/>
Zásady plánovače, které popisují chování nově vytvořeného plánovače.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený Plánovač. Na tento objekt `Scheduler` je umístěn počáteční počet odkazů.

### <a name="remarks"></a>Poznámky

Po vytvoření plánovače pomocí metody `Create` je nutné zavolat metodu `Release` v určitém bodě budoucnosti, aby bylo možné odebrat počáteční počet odkazů a aby bylo možné Plánovač vypnout.

Plánovač vytvořený pomocí této metody není připojen k volajícímu kontextu. Dá se připojit ke kontextu pomocí metody [Attach](#attach) .

Tato metoda může vyvolat různé výjimky, včetně [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) a [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).

## <a name="createschedulegroup"></a>CreateScheduleGroup –

Vytvoří novou skupinu plánu v rámci plánovače. Verze, která přebírá parametr `_Placement` způsobí, že úlohy v nově vytvořené skupině Schedule budou posunuty ke spuštění v umístění určeném parametrem.

```cpp
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```

### <a name="parameters"></a>Parametry

*_Placement*<br/>
Odkaz na umístění, kde se úlohy v rámci skupiny plán posunou ke spuštění na.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořenou skupinu plánu. Na tento objekt `ScheduleGroup` je umístěn počáteční počet odkazů.

### <a name="remarks"></a>Poznámky

Až skončíte s plánováním práce, musíte vyvolat metodu [release](schedulegroup-class.md#release) pro skupinu plánů. Plánovač odstraní skupinu plánů, když je dokončená veškerá práce zařazená do fronty.

Všimněte si, že pokud jste tento Plánovač výslovně vytvořili, musíte před vydáním odkazů na Plánovač vydávat všechny odkazy na jejich plánování ve skupinách.

## <a name="getnumberofvirtualprocessors"></a>Getnumberofvirtualprocessors –

Vrátí aktuální počet virtuálních procesorů pro Plánovač.

```cpp
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální počet virtuálních procesorů pro Plánovač.

## <a name="getpolicy"></a>GetPolicy –

Vrátí kopii zásady, se kterou se vytvořil Scheduler.

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Kopie zásady, se kterou byl Plánovač vytvořen.

## <a name="id"></a>Účet

Vrátí jedinečný identifikátor plánovače.

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor pro Plánovač.

## <a name="isavailablelocation"></a>Isavailablelocation –

Určuje, zda je dané umístění k dispozici v plánovači.

```cpp
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```

### <a name="parameters"></a>Parametry

*_Placement*<br/>
Odkaz na umístění pro dotazování plánovače o.

### <a name="return-value"></a>Návratová hodnota

Označení, zda je umístění určené argumentem `_Placement` k dispozici v plánovači.

### <a name="remarks"></a>Poznámky

Všimněte si, že návratová hodnota je okamžitý odběr vzorkování, zda je dané umístění k dispozici. V případě existence více schedulerů může dynamická správa prostředků přidávat nebo odbírat prostředky z schedulerů v jakémkoli okamžiku. K tomu by se mohlo stát, že dané umístění může změnit dostupnost.

## <a name="reference"></a>Odkaz

Zvýší počet odkazů plánovače.

```cpp
virtual unsigned int Reference() = 0 ;
```

### <a name="return-value"></a>Návratová hodnota

Nově zvýšený počet odkazů.

### <a name="remarks"></a>Poznámky

Obvykle se používá ke správě životnosti Scheduleru pro účely složení. Pokud počet odkazů plánovače klesne na nulu, Plánovač se ukončí a destrukci sám po dokončení veškeré práce v plánovači.

Metoda vyvolá výjimku [improper_scheduler_reference](improper-scheduler-reference-class.md) , pokud je počet odkazů před voláním metody `Reference` nula a volání je provedeno z kontextu, který není vlastněn plánovačem.

## <a name="registershutdownevent"></a>RegisterShutdownEvent –

Způsobí, že popisovač události systému Windows předaný parametrem `_Event`, který se má signalizovat, když se Plánovač vypne a zničí sám sebe. V okamžiku signalizace události je dokončena veškerá práce, která byla naplánována do plánovače. Pomocí této metody lze zaregistrovat více událostí vypnutí.

```cpp
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```

### <a name="parameters"></a>Parametry

*_Event*<br/>
Popisovač objektu události systému Windows, který bude signalizovat modulem runtime při vypnutí a zničení služby.

## <a name="release"></a>Předběžné

Sníží počet odkazů plánovače.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nově snížený počet odkazů.

### <a name="remarks"></a>Poznámky

Obvykle se používá ke správě životnosti Scheduleru pro účely složení. Pokud počet odkazů plánovače klesne na nulu, Plánovač se ukončí a destrukci sám po dokončení veškeré práce v plánovači.

## <a name="resetdefaultschedulerpolicy"></a>Resetdefaultschedulerpolicy –

Obnoví výchozí zásadu plánovače na výchozí nastavení modulu runtime. Při příštím vytvoření výchozího plánovače použije výchozí nastavení zásad modulu runtime.

```cpp
static void __cdecl ResetDefaultSchedulerPolicy();
```

### <a name="remarks"></a>Poznámky

Tuto metodu lze volat, pokud v rámci procesu existuje výchozí Plánovač. Nebude to mít vliv na zásady existujícího výchozího plánovače. Pokud se ale výchozí Plánovač vypnul a později se vytvořila nová výchozí hodnota, bude nový Plánovač používat výchozí nastavení zásad modulu runtime.

## <a name="ctor"></a>Plánovač

Objekt třídy `Scheduler` lze vytvořit pouze pomocí metod Factory nebo implicitně.

```cpp
Scheduler();
```

### <a name="remarks"></a>Poznámky

Výchozí Plánovač procesu je implicitně vytvořen, pokud využíváte mnoho běhových funkcí, které vyžadují, aby byl Plánovač připojen k volajícímu kontextu. Metody v rámci `CurrentScheduler` třídy a funkce vrstev PPL a agentů obvykle provádějí implicitní přílohy.

Můžete také vytvořit Plánovač explicitně pomocí metody `CurrentScheduler::Create` nebo `Scheduler::Create`.

## <a name="dtor"></a>~ Scheduler

Objekt `Scheduler` třídy je implicitně zničen, pokud všechny externí odkazy na něj přestanou existovat.

```cpp
virtual ~Scheduler();
```

## <a name="scheduletask"></a>ScheduleTask –

Naplánuje v Plánovači úlohu s lehkým zatížením. Úloha s lehkým zatížením bude umístěna do skupiny plánování určené modulem runtime. Verze, která přebírá parametr `_Placement` způsobí, že se úloha na zadaném umístění posune směrem k provedení.

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;

virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement) = 0;
```

### <a name="parameters"></a>Parametry

*_Proc*<br/>
Ukazatel na funkci, která se má provést, aby provedla tělo úlohy s lehkým zatížením.

*_Data*<br/>
Anulování ukazatele na data, která budou předána do těla úkolu jako parametr.

*_Placement*<br/>
Odkaz na umístění, kde bude úloha s lehkým zatížením posunuta k provedení v.

## <a name="setdefaultschedulerpolicy"></a>SetDefaultSchedulerPolicy –

Umožňuje, aby se pro vytvoření výchozího plánovače použila zásada definovaná uživatelem. Tuto metodu lze volat pouze v případě, že v rámci procesu neexistuje žádný výchozí Plánovač. Po nastavení výchozí zásady zůstane v platnosti, dokud nedojde k dalšímu platnému volání metody `SetDefaultSchedulerPolicy` nebo [resetdefaultschedulerpolicy –](#resetdefaultschedulerpolicy) .

```cpp
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parametry

*_Policy*<br/>
Zásady, které se mají nastavit jako výchozí zásady plánovače.

### <a name="remarks"></a>Poznámky

Pokud je volána metoda `SetDefaultSchedulerPolicy`, když výchozí Plánovač již v rámci procesu existuje, modul runtime vyvolá výjimku [default_scheduler_exists](default-scheduler-exists-class.md) .

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Scheduler – třída](scheduler-class.md)<br/>
[PolicyElementKey –](concurrency-namespace-enums.md)<br/>
[Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
