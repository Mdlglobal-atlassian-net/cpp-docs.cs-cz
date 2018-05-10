---
title: CurrentScheduler – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- CurrentScheduler
- CONCRT/concurrency::CurrentScheduler
- CONCRT/concurrency::CurrentScheduler::Create
- CONCRT/concurrency::CurrentScheduler::CreateScheduleGroup
- CONCRT/concurrency::CurrentScheduler::Detach
- CONCRT/concurrency::CurrentScheduler::Get
- CONCRT/concurrency::CurrentScheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::CurrentScheduler::GetPolicy
- CONCRT/concurrency::CurrentScheduler::Id
- CONCRT/concurrency::CurrentScheduler::IsAvailableLocation
- CONCRT/concurrency::CurrentScheduler::RegisterShutdownEvent
- CONCRT/concurrency::CurrentScheduler::ScheduleTask
dev_langs:
- C++
helpviewer_keywords:
- CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71ca69f645e548b1913904f692eb1c5fae167a9a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="currentscheduler-class"></a>CurrentScheduler – třída
Představuje abstrakci pro přidružený k volání kontextu aktuálního plánovače.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CurrentScheduler;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Vytvoření](#create)|Vytvoří nový scheduler, jehož chování je popsán `_Policy` parametr a připojí k volání kontextu. Nově vytvořený Plánovač začnou aktuálního plánovače pro kontext volání.|  
|[CreateScheduleGroup](#createschedulegroup)|Přetíženo. Vytvoří novou skupinu plánu v rámci Plánovač přidružený k volání kontextu. Verze, která přebírá parametr `_Placement` způsobí, že úlohy v rámci skupiny nově vytvořený plán můžete být tendenční směrem k provádění v umístění zadaném hodnotou tohoto parametru.|  
|[Detach](#detach)|Odpojí aktuální Plánovač z volání kontextu a obnoví dříve připojené Plánovač jako aktuálního plánovače, pokud existuje. Po návratu tato metoda kontext volání je spravován plánovačem, který byl dříve připojen k kontext buď pomocí `CurrentScheduler::Create` nebo `Scheduler::Attach` metoda.|  
|[GET](#get)|Vrátí ukazatel plánovačem přidružený k volání kontextu také označuje jako aktuálního plánovače.|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|Vrátí aktuální počet virtuálních procesorů pro Plánovač přidružený k volání kontextu.|  
|[Getpolicy –](#getpolicy)|Vrátí kopii zásad, který byl vytvořený aktuálního plánovače.|  
|[ID](#id)|Vrací jedinečný identifikátor pro aktuálního plánovače.|  
|[Isavailablelocation –](#isavailablelocation)|Určuje, zda je k dispozici na aktuálního plánovače daného umístění.|  
|[RegisterShutdownEvent](#registershutdownevent)|Příčiny předaná popisovač události systému Windows `_ShutdownEvent` parametr signál při Plánovač přidružené k aktuální kontext ukončí a zničí sám sebe. V době, kdy signalizace události všechny práci, kterou naplánoval Plánovač je dokončena. Prostřednictvím této metody může být registrováno více událostí vypnutí.|  
|[Scheduletask –](#scheduletask)|Přetíženo. Naplánuje úlohu šedé – v rámci Plánovač přidružený k volání kontextu. Šedé – úloha bude umístěna ve skupině plán určit modulem runtime. Verze, která přebírá parametr `_Placement` úlohu být tendenční směrem k provádění do zadaného umístění.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud neexistuje žádné Plánovač (najdete v části [Plánovač](scheduler-class.md)) přidružený k volání kontextu mnoho metod v rámci `CurrentScheduler` třída způsobí připojení se proces výchozí plánovače. Může to také znamenat, že se proces výchozí plánovač se vytvoří během volání.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CurrentScheduler`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="create"></a> Vytvoření 

 Vytvoří nový scheduler, jehož chování je popsán `_Policy` parametr a připojí k volání kontextu. Nově vytvořený Plánovač začnou aktuálního plánovače pro kontext volání.  
  
```
static void __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>Parametry  
 `_Policy`  
 Zásady plánovače, které popisuje chování nově vytvořený plánovače.  
  
### <a name="remarks"></a>Poznámky  
 Přílohu plánovače kontext volání implicitně umístí počet odkazů na plánovače.  
  
 Po vytvoření plánovače s `Create` metodu, musí volat [currentscheduler::detach –](#detach) metoda v určitém okamžiku v budoucnu, aby bylo možné povolit Plánovač a ukončí se.  
  
 Pokud tato metoda je volána z kontextu, který je již připojena k jiné plánovače, existující Plánovač se uloží jako předchozí Plánovač a nově vytvořený Plánovač stane aktuálního plánovače. Při volání `CurrentScheduler::Detach` metoda později předchozí Plánovač obnovení jako aktuálního plánovače.  
  
 Tuto metodu můžete vyvolat různé výjimky, včetně [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) a [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).  
  
##  <a name="createschedulegroup"></a> Createschedulegroup – 

 Vytvoří novou skupinu plánu v rámci Plánovač přidružený k volání kontextu. Verze, která přebírá parametr `_Placement` způsobí, že úlohy v rámci skupiny nově vytvořený plán můžete být tendenční směrem k provádění v umístění zadaném hodnotou tohoto parametru.  
  
```
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```  
  
### <a name="parameters"></a>Parametry  
 `_Placement`  
 Odkaz na umístění, kde bude s úkoly v rámci skupiny pro plán předpětím směrem provádění na.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený plán skupiny. To `ScheduleGroup` objekt má počet počáteční odkazů na ní umístěny.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda bude výsledkem proces výchozí plánovač jejich vytvoření a/nebo pokud neexistuje žádné scheduler aktuálně přidružen kontext volání připojené k volání kontextu.  
  
 Je nutné vyvolat [verze](schedulegroup-class.md#release) metoda ve skupině plán po dokončení plánování práce. Plánovač zničí plán skupiny, když na ni ve frontě všechny pracovní byla dokončena.  
  
 Poznámka: Pokud jste vytvořili explicitně tento plánovač, je nutné uvolnit všechny odkazy na plánování skupin v rámci, než verze vaší odkazu na Plánovač, odpojíte aktuální kontext z něj.  
  
##  <a name="detach"></a> Odpojení 

 Odpojí aktuální Plánovač z volání kontextu a obnoví dříve připojené Plánovač jako aktuálního plánovače, pokud existuje. Po návratu tato metoda kontext volání je spravován plánovačem, který byl dříve připojen k kontext buď pomocí `CurrentScheduler::Create` nebo `Scheduler::Attach` metoda.  
  
```
static void __cdecl Detach();
```  
  
### <a name="remarks"></a>Poznámky  
 `Detach` Metoda implicitně odebere počet odkazů plánovače.  
  
 Pokud není žádná scheduler připojené k volání kontextu, voláním této metody bude mít za následek [scheduler_not_attached](scheduler-not-attached-class.md) se došlo k výjimce.  
  
 Voláním této metody z kontextu, který je interní a spravuje plánovače nebo kontext, který se připojil pomocí metody jiné než [Scheduler::Attach –](scheduler-class.md#attach) nebo [currentscheduler::Create –](#create) metod bude mít za následek [improper_scheduler_detach](improper-scheduler-detach-class.md) se došlo k výjimce.  
  
##  <a name="get"></a> GET 

 Vrátí ukazatel plánovačem přidružený k volání kontextu také označuje jako aktuálního plánovače.  
  
```
static Scheduler* __cdecl Get();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na Plánovač přidružený kontext volání (aktuálního plánovače).  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda bude výsledkem proces výchozí plánovač jejich vytvoření a/nebo pokud neexistuje žádné scheduler aktuálně přidružen kontext volání připojené k volání kontextu. Žádný další odkaz je umístěn na `Scheduler` objekt vrácená touto metodou.  
  
##  <a name="getnumberofvirtualprocessors"></a> Getnumberofvirtualprocessors – 

 Vrátí aktuální počet virtuálních procesorů pro Plánovač přidružený k volání kontextu.  
  
```
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je přidružený kontext volání, aktuální počet virtuálních procesorů pro tento plánovač; plánovače jinak hodnota `-1`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nebude výsledkem scheduler přílohy, pokud kontext volání ještě není přidružen plánovače.  
  
 Vrácená hodnota z této metody je okamžitou vzorkování počet virtuálních procesorů pro Plánovač přidružený k volání kontextu. Tato hodnota může být zastaralé okamžiku, kdy bude vrácen.  
  
##  <a name="getpolicy"></a> Getpolicy – 

 Vrátí kopii zásad, který byl vytvořený aktuálního plánovače.  
  
```
static SchedulerPolicy __cdecl GetPolicy();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopii této zásady, který byl vytvořený aktuálního plánovače.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda bude výsledkem proces výchozí plánovač jejich vytvoření a/nebo pokud neexistuje žádné scheduler aktuálně přidružen kontext volání připojené k volání kontextu.  
  
##  <a name="id"></a> ID 

 Vrací jedinečný identifikátor pro aktuálního plánovače.  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je přidružený kontext volání jedinečný identifikátor pro tento plánovač; plánovače jinak hodnota `-1`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nebude výsledkem scheduler přílohy, pokud kontext volání ještě není přidružen plánovače.  
  
##  <a name="isavailablelocation"></a> Isavailablelocation – 

 Určuje, zda je k dispozici na aktuálního plánovače daného umístění.  
  
```
static bool __cdecl IsAvailableLocation(const location& _Placement);
```  
  
### <a name="parameters"></a>Parametry  
 `_Placement`  
 Odkaz na umístění, do dotazu aktuálního plánovače o.  
  
### <a name="return-value"></a>Návratová hodnota  
 Údaj o tom, jestli umístění určeného `_Placement` argument je dostupný na aktuálního plánovače.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nebude výsledkem scheduler přílohy, pokud kontext volání ještě není přidružen plánovače.  
  
 Všimněte si, že návratová hodnota je okamžitou vzorkování, zda je k dispozici daného umístění. Za přítomnosti více plánovače dynamickou správu prostředků můžete přidat nebo trvat prostředky, z plánovače v libovolném bodě. By k tomu dojít daného umístění můžete změnit dostupnosti.  
  
##  <a name="registershutdownevent"></a> Registershutdownevent – 

 Příčiny předaná popisovač události systému Windows `_ShutdownEvent` parametr signál při Plánovač přidružené k aktuální kontext ukončí a zničí sám sebe. V době, kdy signalizace události všechny práci, kterou naplánoval Plánovač je dokončena. Prostřednictvím této metody může být registrováno více událostí vypnutí.  
  
```
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```  
  
### <a name="parameters"></a>Parametry  
 `_ShutdownEvent`  
 Popisovač objektu událostí systému Windows, který bude signál modulem runtime, když Plánovač přidružené k aktuální kontext ukončí a zničí sám sebe.  
  
### <a name="remarks"></a>Poznámky  
 Pokud není žádná scheduler připojené k volání kontextu, voláním této metody bude mít za následek [scheduler_not_attached](scheduler-not-attached-class.md) se došlo k výjimce.  
  
##  <a name="scheduletask"></a> Scheduletask – 

 Naplánuje úlohu šedé – v rámci Plánovač přidružený k volání kontextu. Šedé – úloha bude umístěna ve skupině plán určit modulem runtime. Verze, která přebírá parametr `_Placement` úlohu být tendenční směrem k provádění do zadaného umístění.  
  
```
static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data);

static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement);
```  
  
### <a name="parameters"></a>Parametry  
 `_Proc`  
 Ukazatel na funkci provést k provedení úkolu šedé –.  
  
 `_Data`  
 Neplatný ukazatel na data, která se předají jako parametr k tělu úlohy.  
  
 `_Placement`  
 Odkaz na umístění, kde bude s úlohu šedé – předpětím směrem provádění na.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda bude výsledkem proces výchozí plánovač jejich vytvoření a/nebo pokud neexistuje žádné scheduler aktuálně přidružen kontext volání připojené k volání kontextu.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Scheduler – třída](scheduler-class.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



