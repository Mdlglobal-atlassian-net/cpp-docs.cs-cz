---
title: Struktura rozhraní IScheduler
ms.date: 11/04/2016
f1_keywords:
- IScheduler
- CONCRTRM/concurrency::IScheduler
- CONCRTRM/concurrency::IScheduler::IScheduler::AddVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::GetId
- CONCRTRM/concurrency::IScheduler::IScheduler::GetPolicy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyBusy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyIdle
- CONCRTRM/concurrency::IScheduler::IScheduler::RemoveVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::Statistics
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
ms.openlocfilehash: 54db5d664a48f95a952eb1b409839d8ac3421e30
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274073"
---
# <a name="ischeduler-structure"></a>Struktura rozhraní IScheduler

Rozhraní pro abstrakci pracovní plánovače. Správce prostředků modulu Runtime souběžnosti používá ke komunikaci s plánovači pracovní toto rozhraní.

## <a name="syntax"></a>Syntaxe

```
struct IScheduler;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IScheduler::AddVirtualProcessors](#addvirtualprocessors)|Poskytuje plánovače sadu kořenových adresářů virtuálního procesoru pro jeho použití. Každý `IVirtualProcessorRoot` rozhraní představuje oprávnění ke spuštění jedno vlákno, které provádí práci jménem plánovače.|
|[Ischeduler::getid –](#getid)|Vrací jedinečný identifikátor pro Plánovač.|
|[Ischeduler::getpolicy –](#getpolicy)|Vrátí kopii objektu zásad plánovače. Další informace o zásadách plánovače naleznete v tématu [schedulerpolicy –](schedulerpolicy-class.md).|
|[IScheduler::NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|Upozorní tento plánovač, která hardwarových vláken reprezentována sadu kořenových adresářů virtuálního procesoru v poli `ppVirtualProcessorRoots` nyní používá jiné plánovače.|
|[IScheduler::NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|Upozorní tento plánovač, která hardwarových vláken reprezentována sadu kořenových adresářů virtuálního procesoru v poli `ppVirtualProcessorRoots` nejsou používány jiné plánovače.|
|[Ischeduler::removevirtualprocessors –](#removevirtualprocessors)|Inicializuje odstranění kořenových adresářů virtuálního procesoru, které byly dříve přiděleny na Plánovač.|
|[Ischeduler::Statistics –](#statistics)|Obsahuje informace související s míry přijetí a dokončení úlohy a změna v délka fronty plánovače.|

## <a name="remarks"></a>Poznámky

Pokud implementujete vlastní plánovač, který komunikuje s Resource Managerem, by měla poskytnout implementaci položky `IScheduler` rozhraní. Toto rozhraní je na jednom konci obousměrný kanál komunikace mezi plánovače a Resource Manageru. Druhém konci je reprezentována `IResourceManager` a `ISchedulerProxy` rozhraní, které jsou implementované pomocí Správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IScheduler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Namespace:** souběžnosti

##  <a name="addvirtualprocessors"></a>  Ischeduler::addvirtualprocessors – metoda

Poskytuje plánovače sadu kořenových adresářů virtuálního procesoru pro jeho použití. Každý `IVirtualProcessorRoot` rozhraní představuje oprávnění ke spuštění jedno vlákno, které provádí práci jménem plánovače.

```
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Pole `IVirtualProcessorRoot` rozhraní představující virtuální procesor kořeny přidávaný do plánovače.

*Počet*<br/>
Počet `IVirtualProcessorRoot` rozhraní jako pole.

### <a name="remarks"></a>Poznámky

Volá správce prostředků `AddVirtualProcessor` metoda udělit počáteční sadu kořenových adresářů virtuálního procesoru do fronty plánovače. Také to může vyvolat metodu se při jej znovu vytvoří rovnováhu mezi plánovači prostředky přidat do plánovače kořenových adresářů virtuálního procesoru.

##  <a name="getid"></a>  Ischeduler::getid – metoda

Vrací jedinečný identifikátor pro Plánovač.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Celé číslo jedinečný identifikátor.

### <a name="remarks"></a>Poznámky

Měli byste použít [getschedulerid –](concurrency-namespace-functions.md) funkce získat jedinečný identifikátor pro objekt, který implementuje `IScheduler` rozhraní, než použijete rozhraní jako parametr metodám zadaný správcem prostředků. Očekává se vrátit stejný identifikátor při `GetId` vyvolání funkce.

Identifikátor získané z jiného zdroje může způsobit nedefinované chování.

##  <a name="getpolicy"></a>  Ischeduler::getpolicy – metoda

Vrátí kopii objektu zásad plánovače. Další informace o zásadách plánovače naleznete v tématu [schedulerpolicy –](schedulerpolicy-class.md).

```
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Kopírovat zásady plánovače.

##  <a name="notifyresourcesexternallybusy"></a>  Ischeduler::notifyresourcesexternallybusy – metoda

Upozorní tento plánovač, která hardwarových vláken reprezentována sadu kořenových adresářů virtuálního procesoru v poli `ppVirtualProcessorRoots` nyní používá jiné plánovače.

```
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Pole `IVirtualProcessorRoot` rozhraní přidružené k vláken hardwaru, na kterých staly další plánovači zaneprázdněn.

*Počet*<br/>
Počet `IVirtualProcessorRoot` rozhraní jako pole.

### <a name="remarks"></a>Poznámky

Je možné pro konkrétní hardware vlákno má být přiřazena k více plánovače ve stejnou dobu. Jedním z důvodů může být, že na systém a splňovat minimální souběžnost pro všechny plánovače, bez sdílení prostředků nejsou dost hardwarových vláken. Další možností je, že prostředky jsou dočasně přiřazené k jiné plánovači při vlastnící Plánovač, není použití prostřednictvím všech jeho kořenových adresářů virtuálního procesoru v daném vláknu hardwaru právě deaktivována.

Úroveň předplatného vlákno hardwaru je označené podle počtu předplacenému vláken a aktivovat kořenových adresářů virtuálního procesoru, které jsou spojené s tímto vláknem hardwaru. Z určitého plánovače úroveň předplatného externí vlákno hardwaru je část předplatné, které další plánovači přispívat do. Oznámení, že prostředky jsou externě zaneprázdněný odesílají do fronty plánovače posune úrovni externí předplatného pro vlákno hardwaru od nuly do kladnou území.

Oznámení prostřednictvím této metody se odesílají jenom plánovačům, které mají zásady kde hodnota `MinConcurrency` klíče zásad je rovna hodnotě pro `MaxConcurrency` klíče zásad. Další informace o zásadách plánovače naleznete v tématu [schedulerpolicy –](schedulerpolicy-class.md).

Plánovače, která kvalifikuje oznámení získá sady počáteční oznámení při jeho vytváření, informuje, zda jsou prostředky, které právě přiřazené externě přetížena nebo nečinnosti.

##  <a name="notifyresourcesexternallyidle"></a>  Ischeduler::notifyresourcesexternallyidle – metoda

Upozorní tento plánovač, která hardwarových vláken reprezentována sadu kořenových adresářů virtuálního procesoru v poli `ppVirtualProcessorRoots` nejsou používány jiné plánovače.

```
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Pole `IVirtualProcessorRoot` rozhraní přidružené k vláken hardwaru, na kterých staly další plánovači nečinnosti.

*Počet*<br/>
Počet `IVirtualProcessorRoot` rozhraní jako pole.

### <a name="remarks"></a>Poznámky

Je možné pro konkrétní hardware vlákno má být přiřazena k více plánovače ve stejnou dobu. Jedním z důvodů může být, že na systém a splňovat minimální souběžnost pro všechny plánovače, bez sdílení prostředků nejsou dost hardwarových vláken. Další možností je, že prostředky jsou dočasně přiřazené k jiné plánovači při vlastnící Plánovač, není použití prostřednictvím všech jeho kořenových adresářů virtuálního procesoru v daném vláknu hardwaru právě deaktivována.

Úroveň předplatného vlákno hardwaru je označené podle počtu předplacenému vláken a aktivovat kořenových adresářů virtuálního procesoru, které jsou spojené s tímto vláknem hardwaru. Z určitého plánovače úroveň předplatného externí vlákno hardwaru je část předplatné, které další plánovači přispívat do. Oznámení, že prostředky jsou externě zaneprázdněný odesílají do fronty plánovače úroveň externí předplatného pro vlákno hardwaru klesne na nulu z předchozí kladnou hodnotu.

Oznámení prostřednictvím této metody se odesílají jenom plánovačům, které mají zásady kde hodnota `MinConcurrency` klíče zásad je rovna hodnotě pro `MaxConcurrency` klíče zásad. Další informace o zásadách plánovače naleznete v tématu [schedulerpolicy –](schedulerpolicy-class.md).

Plánovače, která kvalifikuje oznámení získá sady počáteční oznámení při jeho vytváření, informuje, zda jsou prostředky, které právě přiřazené externě přetížena nebo nečinnosti.

##  <a name="removevirtualprocessors"></a>  Ischeduler::removevirtualprocessors – metoda

Inicializuje odstranění kořenových adresářů virtuálního procesoru, které byly dříve přiděleny na Plánovač.

```
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Pole `IVirtualProcessorRoot` rozhraní představující kořenových adresářů virtuálního procesoru, která se má odebrat.

*Počet*<br/>
Počet `IVirtualProcessorRoot` rozhraní jako pole.

### <a name="remarks"></a>Poznámky

Volá správce prostředků `RemoveVirtualProcessors` metoda vzít zpět sadu kořenových adresářů virtuálního procesoru z plánovače. Plánovač má vyvolat [odebrat](iexecutionresource-structure.md#remove) metodu na každé rozhraní, když se provádí pomocí kořenových adresářů virtuálního procesoru. Nepoužívejte `IVirtualProcessorRoot` rozhraní, když jste vyvolali `Remove` metoda na něj.

Parametr `ppVirtualProcessorRoots` odkazuje na pole rozhraní. Mezi sadu kořenových adresářů virtuálního procesoru, která se má odebrat, kořeny mít nikdy neaktivoval mohou být vráceny za použití okamžitě `Remove` metody. Adresáře, které jste aktivovali a jsou buď provádí práci, nebo byly deaktivovány a čekají na práci můžete přejít, má být vrácen asynchronně. Plánovač musíte provést všechny pokusy o co nejrychleji odebrat kořen virtuálního procesoru. Neúmyslnému Překryvný odběr v rámci plánovače, může způsobit zpoždění odebrání kořenových adresářů virtuálního procesoru.

##  <a name="statistics"></a>  Ischeduler::Statistics – metoda

Obsahuje informace související s míry přijetí a dokončení úlohy a změna v délka fronty plánovače.

```
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>Parametry

*pTaskCompletionRate*<br/>
Počet úloh, které byly dokončeny plánovačem od posledního volání této metody.

*pTaskArrivalRate*<br/>
Počet úloh, které jste dostali v Plánovači od posledního volání této metody.

*pNumberOfTasksEnqueued*<br/>
Celkový počet úloh ve všech frontách plánovače.

### <a name="remarks"></a>Poznámky

Tuto metodu je spustit Resource Manageru, aby bylo možné shromažďovat statistiky pro Plánovač. Statistiky shromážděné tady se používá k řízení algoritmy dynamického zpětnou vazbu k určení, kdy je třeba přiřadit více zdrojů pro Plánovač a kdy odnést prostředky. Hodnoty poskytnuté Plánovač může být optimistické a není potřeba přesně odrážet aktuální počet.

Tato metoda by měly implementovat, pokud chcete, aby správce prostředků použít zpětnou vazbu o takové věci jako úloha doručení k určení způsobu vyvážit prostředků mezi váš Plánovač a dalších plánovačům zaregistrované pomocí Resource Manageru. Pokud zvolíte ne ke shromažďování statistik, můžete nastavit klíče zásad `DynamicProgressFeedback` hodnotě `DynamicProgressFeedbackDisabled` váš Plánovač zásad a prostředek správce nebude volat tuto metodu na váš plánovač.

Chybí statistické údaje Resource Manageru pomocí úrovní předplatného vlákno hardwaru rozhodování prostředků přidělení a migrace. Další informace na úrovni předplatného najdete v tématu [iexecutionresource::currentsubscriptionlevel –](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy – třída](schedulerpolicy-class.md)<br/>
[IExecutionContext – struktura](iexecutioncontext-structure.md)<br/>
[IThreadProxy – struktura](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager – struktura](iresourcemanager-structure.md)
