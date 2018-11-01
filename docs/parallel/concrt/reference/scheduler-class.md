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
ms.openlocfilehash: 1b2b4de2a0aa844f9450af9d853b11ea6f485274
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638266"
---
# <a name="scheduler-class"></a>Třída plánovače

Představuje abstrakci pro Plánovač Concurrency Runtime.

## <a name="syntax"></a>Syntaxe

```
class Scheduler;
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[Scheduler](#ctor)|Objekt `Scheduler` třída může pouze vytvořit pomocí metody pro vytváření objektů, nebo implicitně.|
|[~Scheduler Destructor](#dtor)|Objekt `Scheduler` třídy implicitně zničen při všechny externí odkazy na něj přestávají existovat.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Attach](#attach)|Plánovač se připojuje k volání kontextu. Po návratu tato metoda volání kontextu spravuje Plánovač a Plánovač stane aktuálního plánovače.|
|[Vytvoření](#create)|Vytvoří nový Plánovač, jehož chování je popsán `_Policy` parametr, uvádí počáteční odkaz na plánovači a vrátí ukazatel na něj.|
|[CreateScheduleGroup](#createschedulegroup)|Přetíženo. Vytvoří novou skupinu plán v rámci plánovače. Verze, která přebírá parametr `_Placement` způsobí, že úlohy ve skupině nově vytvořený plán tendenční směrem k provádění v místě určeném v parametru.|
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|Vrátí aktuální počet virtuálních procesorů pro Plánovač.|
|[GetPolicy](#getpolicy)|Vrátí kopii objektu zásad, který byl vytvořen plánovač.|
|[ID](#id)|Vrací jedinečný identifikátor pro Plánovač.|
|[Isavailablelocation –](#isavailablelocation)|Určuje, zda je na dané místo k dispozici na Plánovač.|
|[Referenční informace](#reference)|Zvýší počet odkazů plánovače.|
|[RegisterShutdownEvent](#registershutdownevent)|Způsobí, že obslužná rutina události Windows předaný `_Event` parametru má být signalizován, když Plánovač vypne a odstraní sama. V době, kdy událost je signalizována všechny práce, která má naplánované Plánovač je dokončena. Prostřednictvím této metody lze registrovat více událostí vypnutí.|
|[Vydaná verze](#release)|Sníží počet referenční plánovače.|
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|Obnoví výchozí zásadu plánovače pro výchozí modul runtime. Další čas, který je výchozím plánovačem vytvořili, použije výchozí nastavení zásady modulu runtime.|
|[Scheduletask –](#scheduletask)|Přetíženo. Naplánuje lehký úkol v rámci plánovače. Lehký úkol se umístí do skupiny plánu určeno modulem runtime. Verze, která přebírá parametr `_Placement` způsobí, že úkol tendenční směrem k provádění v zadaném umístění.|
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|Povolí zásady definované uživatelem se použije k vytvoření výchozího plánovače. Tuto metodu lze volat pouze v případě, že neexistuje žádný výchozí plánovače v rámci procesu. Po nastavení výchozí zásady zůstává v platnosti až do další platné volání na buď `SetDefaultSchedulerPolicy` nebo [resetdefaultschedulerpolicy –](#resetdefaultschedulerpolicy) metody.|

## <a name="remarks"></a>Poznámky

Plánovač Concurrency Runtime používá kontexty spuštění, které mapují na kontexty spuštění operačního systému, jako je například vlákno, k provedení práce ve frontě v aplikaci. V každém okamžiku úroveň souběžnosti plánovače rovná počtu virtuálních procesorů udělen Resource Manageru. Virtuální procesor je abstrakcí pro zpracování zdrojů a map pro vlákno hardwaru v podkladovém systému. Pouze jeden kontext plánovače může provádět na virtuální procesor v daném okamžiku.

Modulu Runtime souběžnosti vytvoří výchozí plánovač proces ke spuštění paralelní práci. Kromě toho můžete vytvořit vlastní plánovač instancí a manipulaci s pomocí této třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Scheduler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="attach"></a> Připojení

Plánovač se připojuje k volání kontextu. Po návratu tato metoda volání kontextu spravuje Plánovač a Plánovač stane aktuálního plánovače.

```
virtual void Attach() = 0;
```

### <a name="remarks"></a>Poznámky

Připojení plánovače implicitně umístí odkaz na Plánovač.

V určitém okamžiku v budoucnu, je třeba zavolat [currentscheduler::detach –](currentscheduler-class.md#detach) metody, aby bylo možné povolit, aby vypnout.

Pokud tato metoda se volá z kontextu, který je již připojena k jiné plánovače, stávající plánování se uloží, jako předchozí Plánovač a nově vytvořený scheduleru se stane aktuálního plánovače. Při volání `CurrentScheduler::Detach` metoda později předchozí scheduleru se obnoví jako aktuálního plánovače.

Tato metoda vyvolá výjimku [improper_scheduler_attach –](improper-scheduler-attach-class.md) výjimku, pokud je tento plánovač aktuálního plánovače kontext volání.

##  <a name="create"></a> Vytvoření

Vytvoří nový Plánovač, jehož chování je popsán `_Policy` parametr, uvádí počáteční odkaz na plánovači a vrátí ukazatel na něj.

```
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parametry

*Zásady _protokolu*<br/>
Zásady plánovače, která popisuje chování nově vytvořený plánovače.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený plánovače. To `Scheduler` objekt má počet počáteční odkazů na ní umístěny.

### <a name="remarks"></a>Poznámky

Po vytvoření plánovače s `Create` metoda, je třeba zavolat `Release` metoda v určitém okamžiku v budoucnu za účelem odeberte počet počáteční odkazů a umožnit, aby vypnout.

Plánovač vytvořené pomocí této metody není připojen k volání kontextu. Může být připojen k pomocí kontextu [připojit](#attach) metody.

Tato metoda může vyvolat výjimky, včetně různých [scheduler_resource_allocation_error –](scheduler-resource-allocation-error-class.md) a [invalid_scheduler_policy_value –](invalid-scheduler-policy-value-class.md).

##  <a name="createschedulegroup"></a> Createschedulegroup –

Vytvoří novou skupinu plán v rámci plánovače. Verze, která přebírá parametr `_Placement` způsobí, že úlohy ve skupině nově vytvořený plán tendenční směrem k provádění v místě určeném v parametru.

```
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```

### <a name="parameters"></a>Parametry

*_Umístění.*<br/>
Odkaz na umístění, ve kterém se úlohy ve skupině plánování tendenční směrem k provedení.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený plán skupiny. To `ScheduleGroup` objekt má počet počáteční odkazů na ní umístěny.

### <a name="remarks"></a>Poznámky

Je nutné vyvolat [vydání](schedulegroup-class.md#release) metodu na skupinu plánování po dokončení plánování práce. Plánovač zničí plánu skupiny, pokud veškerou práci ve frontě byla dokončena.

Všimněte si, že pokud explicitně vytvořeny tento plánovač musí uvolnit všechny odkazy na skupiny v ní, plánů, ještě před vydáním vaše odkazy na Plánovač.

##  <a name="getnumberofvirtualprocessors"></a> Getnumberofvirtualprocessors –

Vrátí aktuální počet virtuálních procesorů pro Plánovač.

```
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální počet virtuálních procesorů pro Plánovač.

##  <a name="getpolicy"></a> GetPolicy

Vrátí kopii objektu zásad, který byl vytvořen plánovač.

```
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Kopie zásad, který byl vytvořen plánovač.

##  <a name="id"></a> ID

Vrací jedinečný identifikátor pro Plánovač.

```
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor pro Plánovač.

##  <a name="isavailablelocation"></a> Isavailablelocation –

Určuje, zda je na dané místo k dispozici na Plánovač.

```
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```

### <a name="parameters"></a>Parametry

*_Umístění.*<br/>
Odkaz na umístění o dotazování plánovače.

### <a name="return-value"></a>Návratová hodnota

Označení, zda je nebo není umístění určeném `_Placement` argument je k dispozici na Plánovač.

### <a name="remarks"></a>Poznámky

Všimněte si, že vrácená hodnota je okamžité vzorkování Určuje, zda je k dispozici daného umístění. Dynamickou správu prostředků za přítomnosti více plánovače, můžete přidat nebo odnést prostředky z plánovače v libovolném bodě. Se to stane, daného umístění můžete změnit dostupnost.

##  <a name="reference"></a> Referenční dokumentace

Zvýší počet odkazů plánovače.

```
virtual unsigned int Reference() = 0 ;
```

### <a name="return-value"></a>Návratová hodnota

Počet nově zvýšena odkazů.

### <a name="remarks"></a>Poznámky

To se obvykle používá ke správě životnosti Plánovač složení. Když počet odkazů Plánovač klesne na nulu, Plánovač se vypne a destruct samotného koneckonců pracovat na Plánovač byla dokončena.

Metoda vyvolá výjimku [improper_scheduler_reference –](improper-scheduler-reference-class.md) výjimku, pokud odkaz na počet před voláním `Reference` metode nula a při volání z kontextu, které není vlastněno plánovače.

##  <a name="registershutdownevent"></a> Registershutdownevent –

Způsobí, že obslužná rutina události Windows předaný `_Event` parametru má být signalizován, když Plánovač vypne a odstraní sama. V době, kdy událost je signalizována všechny práce, která má naplánované Plánovač je dokončena. Prostřednictvím této metody lze registrovat více událostí vypnutí.

```
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```

### <a name="parameters"></a>Parametry

*_Událostí*<br/>
Popisovač objektu události Windows, který bude signál modulem runtime, když Plánovač vypne a odstraní sama.

##  <a name="release"></a> Vydání verze

Sníží počet referenční plánovače.

```
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na nově snížen počet.

### <a name="remarks"></a>Poznámky

To se obvykle používá ke správě životnosti Plánovač složení. Když počet odkazů Plánovač klesne na nulu, Plánovač se vypne a destruct samotného koneckonců pracovat na Plánovač byla dokončena.

##  <a name="resetdefaultschedulerpolicy"></a> Resetdefaultschedulerpolicy –

Obnoví výchozí zásadu plánovače pro výchozí modul runtime. Další čas, který je výchozím plánovačem vytvořili, použije výchozí nastavení zásady modulu runtime.

```
static void __cdecl ResetDefaultSchedulerPolicy();
```

### <a name="remarks"></a>Poznámky

Tuto metodu lze volat při výchozím plánovačem existuje v rámci procesu. Nebude to mít vliv zásad existující výchozí plánovače. Ale pokud výchozím plánovačem byly vypnout a nové výchozí nastavení chtěli vytvořit později, nové Plánovač byste použili výchozí nastavení zásady modulu runtime.

##  <a name="ctor"></a> Scheduler

Objekt `Scheduler` třída může pouze vytvořit pomocí metody pro vytváření objektů, nebo implicitně.

```
Scheduler();
```

### <a name="remarks"></a>Poznámky

Výchozím plánovačem procesu se vytvářejí implicitně, když využívat řadu funkce modulu runtime, které vyžadují Plánovač, připojí se k volání kontextu. Metody v rámci `CurrentScheduler` třídy a funkce vrstvy PPL a agentů obvykle provádí implicitní přílohy.

Můžete také vytvořit plánovače explicitně pomocí kteréhokoliv `CurrentScheduler::Create` metoda nebo `Scheduler::Create` metoda.

##  <a name="dtor"></a> ~ Scheduler

Objekt `Scheduler` třídy implicitně zničen při všechny externí odkazy na něj přestávají existovat.

```
virtual ~Scheduler();
```

##  <a name="scheduletask"></a> Scheduletask –

Naplánuje lehký úkol v rámci plánovače. Lehký úkol se umístí do skupiny plánu určeno modulem runtime. Verze, která přebírá parametr `_Placement` způsobí, že úkol tendenční směrem k provádění v zadaném umístění.

```
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
Ukazatel na funkci, která se má spustit provádění těla lehký úkol.

*_Data*<br/>
Ukazatel void data, která se předá jako parametr do těla úkolu.

*_Umístění.*<br/>
Odkaz na umístění, ve kterém bude možné lehký úkol tendenční směrem k provedení.

##  <a name="setdefaultschedulerpolicy"></a> Setdefaultschedulerpolicy –

Povolí zásady definované uživatelem se použije k vytvoření výchozího plánovače. Tuto metodu lze volat pouze v případě, že neexistuje žádný výchozí plánovače v rámci procesu. Po nastavení výchozí zásady zůstává v platnosti až do další platné volání na buď `SetDefaultSchedulerPolicy` nebo [resetdefaultschedulerpolicy –](#resetdefaultschedulerpolicy) metody.

```
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parametry

*Zásady _protokolu*<br/>
Zásady pro nastavení jako výchozí zásadu plánovače.

### <a name="remarks"></a>Poznámky

Pokud `SetDefaultSchedulerPolicy` metoda se volá, když je výchozím plánovačem již existuje v rámci procesu, modul runtime vyvolá výjimku [default_scheduler_exists –](default-scheduler-exists-class.md) výjimky.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Scheduler – třída](scheduler-class.md)<br/>
[Policyelementkey –](concurrency-namespace-enums.md)<br/>
[Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

