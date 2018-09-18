---
title: Currentscheduler – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: e96b9d70e48b63eafb8cb3c6f4938f962114fd39
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059482"
---
# <a name="currentscheduler-class"></a>CurrentScheduler – třída
Představuje abstrakci pro aktuální Plánovač přidružený kontext volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CurrentScheduler;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Vytvoření](#create)|Vytvoří nový Plánovač, jehož chování je popsán `_Policy` parametr a připojí ho k volání kontextu. Nově vytvořený scheduleru se stanou aktuálního plánovače pro kontext volání.|  
|[CreateScheduleGroup](#createschedulegroup)|Přetíženo. Vytvoří novou skupinu plán v rámci plánovače, přidružený k volání kontextu. Verze, která přebírá parametr `_Placement` způsobí, že úlohy ve skupině nově vytvořený plán tendenční směrem k provádění v místě určeném v parametru.|  
|[Detach](#detach)|Odpojí aktuální Plánovač z volání kontextu a obnoví dříve připojené služby Plánovač jako aktuálního plánovače, pokud existuje. Po návratu tato metoda volání kontextu potom spravuje plánovače, který byl dříve připojena ke kontextu buď pomocí `CurrentScheduler::Create` nebo `Scheduler::Attach` metody.|  
|[získat](#get)|Vrací ukazatel na Plánovač přidružený k volání kontextu označuje také jako aktuálního plánovače.|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|Vrátí aktuální počet virtuálních procesorů pro Plánovač přidružený kontext volání.|  
|[GetPolicy](#getpolicy)|Vrátí kopii objektu zásad, který byl vytvořen aktuálního plánovače.|  
|[ID](#id)|Vrací jedinečný identifikátor pro aktuální plánovač.|  
|[Isavailablelocation –](#isavailablelocation)|Určuje, zda je k dispozici pro aktuální Plánovač na dané místo.|  
|[RegisterShutdownEvent](#registershutdownevent)|Způsobí, že obslužná rutina události Windows předaný `_ShutdownEvent` parametru má být signalizován, když Plánovač spojené s aktuálním kontextu vypne a odstraní sama. V době, kdy událost je signalizována všechny práce, která má naplánované Plánovač je dokončena. Prostřednictvím této metody lze registrovat více událostí vypnutí.|  
|[Scheduletask –](#scheduletask)|Přetíženo. Naplánuje lehký úkol v rámci plánovače, přidružený k volání kontextu. Lehký úkol se umístí do skupiny plánu určeno modulem runtime. Verze, která přebírá parametr `_Placement` způsobí, že úkol tendenční směrem k provádění v zadaném umístění.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud není žádný Plánovač (naleznete v tématu [Plánovač](scheduler-class.md)) přidružený k volání kontextu mnoho metod v rámci `CurrentScheduler` třídy způsobí přílohy procesu výchozím plánovačem. Může to také znamenat, že procesu výchozím plánovačem se vytvoří během těchto volání.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CurrentScheduler`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="create"></a> Vytvoření 

 Vytvoří nový Plánovač, jehož chování je popsán `_Policy` parametr a připojí ho k volání kontextu. Nově vytvořený scheduleru se stanou aktuálního plánovače pro kontext volání.  
  
```
static void __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>Parametry  
*Zásady _protokolu*<br/>
Zásady plánovače, která popisuje chování nově vytvořený plánovač.  
  
### <a name="remarks"></a>Poznámky  
 Plánovač přílohu kontext volání implicitně uvádí počet odkazů na Plánovač.  
  
 Po vytvoření plánovače s `Create` metoda, je třeba zavolat [currentscheduler::detach –](#detach) metoda v určitém okamžiku v budoucnu, aby bylo možné povolit, aby vypnout.  
  
 Pokud tato metoda se volá z kontextu, který je již připojena k jiné plánovače, stávající plánování se uloží, jako předchozí Plánovač a nově vytvořený scheduleru se stane aktuálního plánovače. Při volání `CurrentScheduler::Detach` metoda později předchozí scheduleru se obnoví jako aktuálního plánovače.  
  
 Tato metoda může vyvolat výjimky, včetně různých [scheduler_resource_allocation_error –](scheduler-resource-allocation-error-class.md) a [invalid_scheduler_policy_value –](invalid-scheduler-policy-value-class.md).  
  
##  <a name="createschedulegroup"></a> Createschedulegroup – 

 Vytvoří novou skupinu plán v rámci plánovače, přidružený k volání kontextu. Verze, která přebírá parametr `_Placement` způsobí, že úlohy ve skupině nově vytvořený plán tendenční směrem k provádění v místě určeném v parametru.  
  
```
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```  
  
### <a name="parameters"></a>Parametry  
*_Umístění.*<br/>
Odkaz na umístění, kde bude možné úlohy ve skupině plánování tendenční směrem k provedení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený plán skupiny. To `ScheduleGroup` objekt má počet počáteční odkazů na ní umístěny.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda způsobí procesu výchozím plánovačem se vytvoří a/nebo připojené k volání kontextu, pokud neexistuje žádný Plánovač aktuálně přiřazen k volání kontextu.  
  
 Je nutné vyvolat [vydání](schedulegroup-class.md#release) metodu na skupinu plánování po dokončení plánování práce. Plánovač zničí plánu skupiny, pokud veškerou práci ve frontě byla dokončena.  
  
 Všimněte si, že pokud explicitně vytvořeny tento plánovač musí uvolnit všechny odkazy na skupiny v ní, plánů, ještě před vydáním referenci na plánovači, odpojíte aktuální kontext z něj.  
  
##  <a name="detach"></a> Odpojení 

 Odpojí aktuální Plánovač z volání kontextu a obnoví dříve připojené služby Plánovač jako aktuálního plánovače, pokud existuje. Po návratu tato metoda volání kontextu potom spravuje plánovače, který byl dříve připojena ke kontextu buď pomocí `CurrentScheduler::Create` nebo `Scheduler::Attach` metody.  
  
```
static void __cdecl Detach();
```  
  
### <a name="remarks"></a>Poznámky  
 `Detach` Metoda se implicitně odeberou počet odkazů z plánovače.  
  
 Pokud neexistuje žádný Plánovač připojit ke kontextu volání, bude výsledkem volání této metody [scheduler_not_attached –](scheduler-not-attached-class.md) vyvolání výjimky.  
  
 Voláním této metody z kontextu, který je interní a spravované pomocí plánovače nebo kontext, který se připojil pomocí jiné metody než pomocí [Scheduler::Attach –](scheduler-class.md#attach) nebo [currentscheduler::Create –](#create) metod Výsledkem bude [improper_scheduler_detach –](improper-scheduler-detach-class.md) vyvolání výjimky.  
  
##  <a name="get"></a> získat 

 Vrací ukazatel na Plánovač přidružený k volání kontextu označuje také jako aktuálního plánovače.  
  
```
static Scheduler* __cdecl Get();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na Plánovač spojený s kontextem volání (aktuální plánovač).  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda způsobí procesu výchozím plánovačem se vytvoří a/nebo připojené k volání kontextu, pokud neexistuje žádný Plánovač aktuálně přiřazen k volání kontextu. Žádný další odkaz je umístěn na `Scheduler` objekt vrácený touto metodou.  
  
##  <a name="getnumberofvirtualprocessors"></a> Getnumberofvirtualprocessors – 

 Vrátí aktuální počet virtuálních procesorů pro Plánovač přidružený kontext volání.  
  
```
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je přidružený kontext volání, aktuální počet virtuálních procesorů pro Plánovač; plánovače v opačném případě hodnota `-1`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda opozdí v scheduleru přílohy Pokud není kontext volání již přidružen plánovače.  
  
 Vrácená hodnota z této metody je okamžité vzorkování počet virtuálních procesorů pro Plánovač přidružený kontext volání. Tato hodnota může být zastaralá v okamžiku, kdy bude vrácen.  
  
##  <a name="getpolicy"></a> GetPolicy 

 Vrátí kopii objektu zásad, který byl vytvořen aktuálního plánovače.  
  
```
static SchedulerPolicy __cdecl GetPolicy();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopie zásad, který byl vytvořen aktuálního plánovače.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda způsobí procesu výchozím plánovačem se vytvoří a/nebo připojené k volání kontextu, pokud neexistuje žádný Plánovač aktuálně přiřazen k volání kontextu.  
  
##  <a name="id"></a> ID 

 Vrací jedinečný identifikátor pro aktuální plánovač.  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je přidružený kontext volání jedinečný identifikátor pro Plánovač; plánovače v opačném případě hodnota `-1`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda opozdí v scheduleru přílohy Pokud není kontext volání již přidružen plánovače.  
  
##  <a name="isavailablelocation"></a> Isavailablelocation – 

 Určuje, zda je k dispozici pro aktuální Plánovač na dané místo.  
  
```
static bool __cdecl IsAvailableLocation(const location& _Placement);
```  
  
### <a name="parameters"></a>Parametry  
*_Umístění.*<br/>
Odkaz na umístění o dotazování aktuálního plánovače.  
  
### <a name="return-value"></a>Návratová hodnota  
 Označení, zda je nebo není umístění určeném `_Placement` argument je k dispozici pro aktuální plánovač.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda opozdí v scheduleru přílohy Pokud není kontext volání již přidružen plánovače.  
  
 Všimněte si, že vrácená hodnota je okamžité vzorkování Určuje, zda je k dispozici daného umístění. Dynamickou správu prostředků za přítomnosti více plánovače, můžete přidat nebo odnést prostředky z plánovače v libovolném bodě. Se to stane, daného umístění můžete změnit dostupnost.  
  
##  <a name="registershutdownevent"></a> Registershutdownevent – 

 Způsobí, že obslužná rutina události Windows předaný `_ShutdownEvent` parametru má být signalizován, když Plánovač spojené s aktuálním kontextu vypne a odstraní sama. V době, kdy událost je signalizována všechny práce, která má naplánované Plánovač je dokončena. Prostřednictvím této metody lze registrovat více událostí vypnutí.  
  
```
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```  
  
### <a name="parameters"></a>Parametry  
*_ShutdownEvent*<br/>
Popisovač objektu události Windows, který bude signál modulem runtime, když Plánovač spojené s aktuálním kontextu vypne a odstraní sama.  
  
### <a name="remarks"></a>Poznámky  
 Pokud neexistuje žádný Plánovač připojit ke kontextu volání, bude výsledkem volání této metody [scheduler_not_attached –](scheduler-not-attached-class.md) vyvolání výjimky.  
  
##  <a name="scheduletask"></a> Scheduletask – 

 Naplánuje lehký úkol v rámci plánovače, přidružený k volání kontextu. Lehký úkol se umístí do skupiny plánu určeno modulem runtime. Verze, která přebírá parametr `_Placement` způsobí, že úkol tendenční směrem k provádění v zadaném umístění.  
  
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
*_Proc*<br/>
Ukazatel na funkci, která se má spustit provádění těla lehký úkol.  
  
*_Data*<br/>
Ukazatel void data, která se předá jako parametr do těla úkolu.  
  
*_Umístění.*<br/>
Odkaz na umístění, ve kterém bude možné lehký úkol tendenční směrem k provedení.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda způsobí procesu výchozím plánovačem se vytvoří a/nebo připojené k volání kontextu, pokud neexistuje žádný Plánovač aktuálně přiřazen k volání kontextu.  
  
## <a name="see-also"></a>Viz také  
 [souběžnost Namespace](concurrency-namespace.md)   
 [Scheduler – třída](scheduler-class.md)   
 [Policyelementkey –](concurrency-namespace-enums.md)   
 [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



