---
title: Třída plánovače | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97abec33d5fa4b372bc26874fd37397a2b78bb29
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693676"
---
# <a name="scheduler-class"></a>Třída plánovače
Představuje abstrakci pro Concurrency Runtime plánovače.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class Scheduler;
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Scheduler](#ctor)|Objekt `Scheduler` třídy může obsahovat jenom vytvořené pomocí metod vytváření nebo implicitně.|  
|[~Scheduler Destructor](#dtor)|Objekt `Scheduler` třída implicitně zničena při všechny externí odkazy do ní přestanou existovat.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Attach](#attach)|Plánovač připojuje k volání kontextu. Po návratu tato metoda kontext volání spravuje Plánovač a Plánovač stane aktuálního plánovače.|  
|[Vytvoření](#create)|Vytvoří nový scheduler, jehož chování je popsán `_Policy` parametr umístí odkaz na počáteční na Plánovač a vrátí ukazatel na ni.|  
|[CreateScheduleGroup](#createschedulegroup)|Přetíženo. Vytvoří novou skupinu plánu v rámci plánovače. Verze, která přebírá parametr `_Placement` způsobí, že úlohy v rámci skupiny nově vytvořený plán můžete být tendenční směrem k provádění v umístění zadaném hodnotou tohoto parametru.|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|Vrátí aktuální počet virtuálních procesorů pro Plánovač.|  
|[Getpolicy –](#getpolicy)|Vrátí kopii zásad, který byl vytvořený plánovače.|  
|[ID](#id)|Vrací jedinečný identifikátor pro Plánovač.|  
|[Isavailablelocation –](#isavailablelocation)|Určuje, zda je k dispozici na Plánovač daného umístění.|  
|[Referenční informace](#reference)|Zvýší počet odkazů plánovače.|  
|[RegisterShutdownEvent](#registershutdownevent)|Příčiny předaná popisovač události systému Windows `_Event` parametr signál při Plánovač ukončí a zničí sám sebe. V době, kdy signalizace události všechny práci, kterou naplánoval Plánovač je dokončena. Prostřednictvím této metody může být registrováno více událostí vypnutí.|  
|[Vydaná verze](#release)|Snižuje počet odkaz na plánovače.|  
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|Výchozí zásady plánovače obnoví na výchozí modul runtime. Při příštím vytvoření plánovače výchozí použije výchozí nastavení zásady modulu runtime.|  
|[Scheduletask –](#scheduletask)|Přetíženo. Naplánuje úlohu šedé – v rámci plánovače. Šedé – úloha bude umístěna ve skupině plán určit modulem runtime. Verze, která přebírá parametr `_Placement` úlohu být tendenční směrem k provádění do zadaného umístění.|  
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|Umožňuje použít k vytvoření plánovače výchozí zásad definované uživatelem. Tuto metodu lze volat pouze v případě, že žádná výchozí plánovač existuje v rámci procesu. Po nastavení výchozích zásad, zůstává v platnosti, dokud další platný volání buď `SetDefaultSchedulerPolicy` nebo [resetdefaultschedulerpolicy –](#resetdefaultschedulerpolicy) metoda.|  
  
## <a name="remarks"></a>Poznámky  
 Plánovač Concurrency Runtime používá provádění kontextů, které mapovat kontextů spuštění operačního systému, jako je například vlákno, k provedení práce zařazených do fronty se vaše aplikace. Kdykoli se rovná počet virtuálních procesorů udělit pomocí Správce prostředků úroveň souběžnosti plánovače. Virtuálního procesoru je abstrakci pro zpracování prostředků a mapy na vlákno hardwaru v základním systému. Pouze kontextu jedné Plánovač můžete spustit na virtuálních procesorů v daném okamžiku.  
  
 Concurrency Runtime vytvoří výchozí plánovač podle procesu provést paralelní práce. Kromě toho můžete vytvořit vlastní plánovače instancí a upravit pomocí této třídy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Scheduler`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="attach"></a> Připojení 

 Plánovač připojuje k volání kontextu. Po návratu tato metoda kontext volání spravuje Plánovač a Plánovač stane aktuálního plánovače.  
  
```
virtual void Attach() = 0;
```  
  
### <a name="remarks"></a>Poznámky  
 Připojení plánovače implicitně umístí odkaz na plánovače.  
  
 V určitém okamžiku v budoucnosti, musí volat [currentscheduler::detach –](currentscheduler-class.md#detach) metoda, aby bylo možné povolit Plánovač a ukončí se.  
  
 Pokud tato metoda je volána z kontextu, který je již připojena k jiné plánovače, existující Plánovač se uloží jako předchozí Plánovač a nově vytvořený Plánovač stane aktuálního plánovače. Při volání `CurrentScheduler::Detach` metoda později předchozí Plánovač obnovení jako aktuálního plánovače.  
  
 Tato metoda vyvolá výjimku [improper_scheduler_attach](improper-scheduler-attach-class.md) výjimka, pokud je tento plánovač aktuálního plánovače volání kontextu.  
  
##  <a name="create"></a> Vytvoření 

 Vytvoří nový scheduler, jehož chování je popsán `_Policy` parametr umístí odkaz na počáteční na Plánovač a vrátí ukazatel na ni.  
  
```
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>Parametry  
 `_Policy`  
 Zásady plánovače, které popisuje chování nově vytvořený plánovače.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený plánovače. To `Scheduler` objekt má počet počáteční odkazů na ní umístěny.  
  
### <a name="remarks"></a>Poznámky  
 Po vytvoření plánovače s `Create` metodu, musí volat `Release` metoda v určitém okamžiku v budoucnu chcete-li odebrat odkaz na počáteční počet a povolit Plánovač a ukončí se.  
  
 Plánovače vytvořené pomocí této metody není připojen k volání kontextu. Může být připojen k kontext pomocí [Attach](#attach) metoda.  
  
 Tuto metodu můžete vyvolat různé výjimky, včetně [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) a [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).  
  
##  <a name="createschedulegroup"></a> Createschedulegroup – 

 Vytvoří novou skupinu plánu v rámci plánovače. Verze, která přebírá parametr `_Placement` způsobí, že úlohy v rámci skupiny nově vytvořený plán můžete být tendenční směrem k provádění v umístění zadaném hodnotou tohoto parametru.  
  
```
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Placement`  
 Odkaz na umístění, kde bude směrem provádění na tendenční úkoly v rámci skupiny pro plán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený plán skupiny. To `ScheduleGroup` objekt má počet počáteční odkazů na ní umístěny.  
  
### <a name="remarks"></a>Poznámky  
 Je nutné vyvolat [verze](schedulegroup-class.md#release) metoda ve skupině plán po dokončení plánování práce. Plánovač zničí plán skupiny, když na ni ve frontě všechny pracovní byla dokončena.  
  
 Poznámka: Pokud jste vytvořili explicitně tento plánovač, je nutné uvolnit všechny odkazy na plánování skupin v rámci, před uvolnit vaše odkazy na plánovače.  
  
##  <a name="getnumberofvirtualprocessors"></a> Getnumberofvirtualprocessors – 

 Vrátí aktuální počet virtuálních procesorů pro Plánovač.  
  
```
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální počet virtuálních procesorů pro Plánovač.  
  
##  <a name="getpolicy"></a> Getpolicy – 

 Vrátí kopii zásad, který byl vytvořený plánovače.  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopie zásad, který byl vytvořený plánovače.  
  
##  <a name="id"></a> ID 

 Vrací jedinečný identifikátor pro Plánovač.  
  
```
virtual unsigned int Id() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedinečný identifikátor pro Plánovač.  
  
##  <a name="isavailablelocation"></a> Isavailablelocation – 

 Určuje, zda je k dispozici na Plánovač daného umístění.  
  
```
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Placement`  
 Odkaz na umístění, do dotazu Plánovač o.  
  
### <a name="return-value"></a>Návratová hodnota  
 Údaj o tom, jestli umístění určeného `_Placement` argument je dostupný na plánovače.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že návratová hodnota je okamžitou vzorkování, zda je k dispozici daného umístění. Za přítomnosti více plánovače dynamickou správu prostředků můžete přidat nebo trvat prostředky, z plánovače v libovolném bodě. By k tomu dojít daného umístění můžete změnit dostupnosti.  
  
##  <a name="reference"></a> Referenční dokumentace 

 Zvýší počet odkazů plánovače.  
  
```
virtual unsigned int Reference() = 0 ;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet nově zvýšena odkazů.  
  
### <a name="remarks"></a>Poznámky  
 To se obvykle používá ke správě životnost Plánovač pro složení. Když počet scheduler spadá nule odkazů Plánovač se zastaví a destruct samotné po všech práce na Plánovač byla dokončena.  
  
 Vyvolá metodu [improper_scheduler_reference](improper-scheduler-reference-class.md) Pokud odkaz na počet před voláním `Reference` metoda byla nula a při volání z kontextu, který není vlastníkem plánovače.  
  
##  <a name="registershutdownevent"></a> Registershutdownevent – 

 Příčiny předaná popisovač události systému Windows `_Event` parametr signál při Plánovač ukončí a zničí sám sebe. V době, kdy signalizace události všechny práci, kterou naplánoval Plánovač je dokončena. Prostřednictvím této metody může být registrováno více událostí vypnutí.  
  
```
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Event`  
 Popisovač objektu událostí systému Windows, který bude signál modulem runtime, když Plánovač ukončí a zničí sám sebe.  
  
##  <a name="release"></a> Verze 

 Snižuje počet odkaz na plánovače.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet nově odečte odkazů.  
  
### <a name="remarks"></a>Poznámky  
 To se obvykle používá ke správě životnost Plánovač pro složení. Když počet scheduler spadá nule odkazů Plánovač se zastaví a destruct samotné po všech práce na Plánovač byla dokončena.  
  
##  <a name="resetdefaultschedulerpolicy"></a> Resetdefaultschedulerpolicy – 

 Výchozí zásady plánovače obnoví na výchozí modul runtime. Při příštím vytvoření plánovače výchozí použije výchozí nastavení zásady modulu runtime.  
  
```
static void __cdecl ResetDefaultSchedulerPolicy();
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze volat, když plánovače výchozí existuje v rámci procesu. Zásady plánovače existující výchozí neovlivní. Ale pokud výchozí plánovač byly vypnutí a nový výchozí chtěli vytvořit později, nové Plánovač využije výchozí nastavení zásady modulu runtime.  
  
##  <a name="ctor"></a> Scheduler 

 Objekt `Scheduler` třídy může obsahovat jenom vytvořené pomocí metod vytváření nebo implicitně.  
  
```
Scheduler();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí scheduler proces je vytvořen implicitně po můžete využívat mnoho funkcí modulu runtime, které vyžadují plánovače být připojen k volání kontextu. Metod v rámci `CurrentScheduler` třídy a funkce PPL a agenty vrstvy provádějí obvykle implicitní přílohy.  
  
 Můžete také vytvořit plánovače explicitně prostřednictvím buď `CurrentScheduler::Create` metoda nebo `Scheduler::Create` metoda.  
  
##  <a name="dtor"></a> ~ Scheduler 

 Objekt `Scheduler` třída implicitně zničena při všechny externí odkazy do ní přestanou existovat.  
  
```
virtual ~Scheduler();
```  
  
##  <a name="scheduletask"></a> Scheduletask – 

 Naplánuje úlohu šedé – v rámci plánovače. Šedé – úloha bude umístěna ve skupině plán určit modulem runtime. Verze, která přebírá parametr `_Placement` úlohu být tendenční směrem k provádění do zadaného umístění.  
  
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
 `_Proc`  
 Ukazatel na funkci provést k provedení úkolu šedé –.  
  
 `_Data`  
 Neplatný ukazatel na data, která se předají jako parametr k tělu úlohy.  
  
 `_Placement`  
 Odkaz na umístění, kde bude s úlohu šedé – předpětím směrem provádění na.  
  
##  <a name="setdefaultschedulerpolicy"></a> Setdefaultschedulerpolicy – 

 Umožňuje použít k vytvoření plánovače výchozí zásad definované uživatelem. Tuto metodu lze volat pouze v případě, že žádná výchozí plánovač existuje v rámci procesu. Po nastavení výchozích zásad, zůstává v platnosti, dokud další platný volání buď `SetDefaultSchedulerPolicy` nebo [resetdefaultschedulerpolicy –](#resetdefaultschedulerpolicy) metoda.  
  
```
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>Parametry  
 `_Policy`  
 Zásada nastavit jako výchozí zásady plánovače.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `SetDefaultSchedulerPolicy` metoda je volána, když plánovače výchozí již existuje v rámci procesu, vyvolá výjimku modulu runtime [default_scheduler_exists](default-scheduler-exists-class.md) výjimka.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Scheduler – třída](scheduler-class.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



