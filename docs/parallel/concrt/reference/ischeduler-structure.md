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
ms.openlocfilehash: cd7b04b0dc5ca1bc496ce87a6459d00ed5813bf7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422218"
---
# <a name="ischeduler-structure"></a>Struktura rozhraní IScheduler

Rozhraní pro abstrakci pracovního plánovače. Správce prostředků Concurrency Runtime používá toto rozhraní ke komunikaci s plánovači práce.

## <a name="syntax"></a>Syntaxe

```cpp
struct IScheduler;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IScheduler:: AddVirtualProcessors –](#addvirtualprocessors)|Poskytuje Plánovač se sadou kořenů virtuálních procesorů pro jeho použití. Každé rozhraní `IVirtualProcessorRoot` představuje právo spustit jedno vlákno, které může provádět práci jménem plánovače.|
|[IScheduler:: getId –](#getid)|Vrátí jedinečný identifikátor plánovače.|
|[IScheduler:: GetPolicy](#getpolicy)|Vrátí kopii zásady plánovače. Další informace o zásadách plánovače najdete v tématu [SchedulerPolicy](schedulerpolicy-class.md).|
|[IScheduler:: Notifyresourcesexternallybusy –](#notifyresourcesexternallybusy)|Upozorní tohoto plánovače, že hardwarová vlákna reprezentovaná sadou kořenů virtuálních procesorů v poli `ppVirtualProcessorRoots` jsou nyní používána jinými plánovači.|
|[IScheduler:: Notifyresourcesexternallyidle –](#notifyresourcesexternallyidle)|Oznámí tomuto plánovači, že hardwarová vlákna reprezentovaná sadou kořenů virtuálních procesorů v poli `ppVirtualProcessorRoots` nepoužívají jiné plánovače.|
|[IScheduler:: RemoveVirtualProcessors –](#removevirtualprocessors)|Inicializuje odebrání kořenových adresářů virtuálních procesorů, které byly dříve přiděleny tomuto plánovači.|
|[IScheduler:: Statistics](#statistics)|Poskytuje informace týkající se doručení a sazeb dokončení úloh a změny ve frontě pro Plánovač.|

## <a name="remarks"></a>Poznámky

Pokud implementujete vlastního plánovače, který komunikuje s Správce prostředků, měli byste poskytnout implementaci rozhraní `IScheduler`. Toto rozhraní představuje jeden konec obousměrného komunikačního kanálu mezi plánovačem a Správce prostředků. Druhý konec je reprezentován rozhraním `IResourceManager` a `ISchedulerProxy`, která jsou implementována Správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IScheduler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="addvirtualprocessors"></a>IScheduler:: AddVirtualProcessors – – metoda

Poskytuje Plánovač se sadou kořenů virtuálních procesorů pro jeho použití. Každé rozhraní `IVirtualProcessorRoot` představuje právo spustit jedno vlákno, které může provádět práci jménem plánovače.

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Pole rozhraní `IVirtualProcessorRoot` reprezentujících kořeny virtuálního procesoru přidávané do plánovače.

*count*<br/>
Počet `IVirtualProcessorRoot` rozhraní v poli.

### <a name="remarks"></a>Poznámky

Správce prostředků vyvolá metodu `AddVirtualProcessor` pro udělení počáteční sady kořenových adresářů virtuálního procesoru do plánovače. Může také vyvolat metodu pro přidání kořenů virtuálního procesoru do plánovače při přerovnávání prostředků mezi plánovači.

## <a name="getid"></a>IScheduler:: getId – – metoda

Vrátí jedinečný identifikátor plánovače.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný celočíselný identifikátor.

### <a name="remarks"></a>Poznámky

Použijte funkci [GetSchedulerId –](concurrency-namespace-functions.md) k získání jedinečného identifikátoru pro objekt, který implementuje rozhraní `IScheduler`, před použitím rozhraní jako parametru pro metody dodané správce prostředků. Očekává se, že vrátíte stejný identifikátor při vyvolání funkce `GetId`.

Identifikátor získaný z jiného zdroje může mít za následek nedefinované chování.

## <a name="getpolicy"></a>IScheduler:: GetPolicy – metoda

Vrátí kopii zásady plánovače. Další informace o zásadách plánovače najdete v tématu [SchedulerPolicy](schedulerpolicy-class.md).

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Kopie zásad plánovače.

## <a name="notifyresourcesexternallybusy"></a>IScheduler:: Notifyresourcesexternallybusy – – metoda

Upozorní tohoto plánovače, že hardwarová vlákna reprezentovaná sadou kořenů virtuálních procesorů v poli `ppVirtualProcessorRoots` jsou nyní používána jinými plánovači.

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Pole rozhraní `IVirtualProcessorRoot` přidružených k hardwarovým vláknům, u kterých se jiné plánovače stali zaneprázdněnými.

*count*<br/>
Počet `IVirtualProcessorRoot` rozhraní v poli.

### <a name="remarks"></a>Poznámky

Je možné, aby bylo konkrétní hardwarové vlákno přiřazeno více plánovačům současně. Důvodem může být to, že v systému není k dispozici dostatek hardwarových vláken pro splnění minimální souběžnosti pro všechny plánovače bez sdílení prostředků. Další možností je to, že prostředky se dočasně přiřazují jiným plánovačům, když ji vlastnící Plánovač nepoužívají, a to prostřednictvím všech kořenových adresářů virtuálních procesorů v tomto hardwarovém vlákně, které je deaktivované.

Úroveň předplatného hardwarového vlákna vychází z počtu přihlášených vláken a aktivovaných kořenových adresářů virtuálních procesorů přidružených k tomuto hardwarovému vláknu. Z pohledu konkrétního plánovače je externí úroveň předplatného hardwarového vlákna součástí předplatného, ke kterému přispěje jiné plánovače. Oznámení o tom, že prostředky jsou externě zaneprázdněná, se odesílají do Scheduleru, když se externí předplatné na hardwarovém vlákně pohybuje od nuly po kladné území.

Oznámení prostřednictvím této metody jsou odesílána pouze do schedulerů, které mají zásadu, kde je hodnota klíče zásad `MinConcurrency` rovna hodnotě pro klíč zásad `MaxConcurrency`. Další informace o zásadách plánovače najdete v tématu [SchedulerPolicy](schedulerpolicy-class.md).

Plánovač, který v oznámeních vyhovuje, získá sadu počátečních oznámení při jejich vytvoření, informuje o tom, jestli prostředky, které jste právě přiřadili, jsou externě zaneprázdněné nebo nečinné.

## <a name="notifyresourcesexternallyidle"></a>IScheduler:: Notifyresourcesexternallyidle – – metoda

Oznámí tomuto plánovači, že hardwarová vlákna reprezentovaná sadou kořenů virtuálních procesorů v poli `ppVirtualProcessorRoots` nepoužívají jiné plánovače.

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Pole rozhraní `IVirtualProcessorRoot` přidružených k hardwarovým vláknům, u kterých se jiné schedulery staly nečinnými.

*count*<br/>
Počet `IVirtualProcessorRoot` rozhraní v poli.

### <a name="remarks"></a>Poznámky

Je možné, aby bylo konkrétní hardwarové vlákno přiřazeno více plánovačům současně. Důvodem může být to, že v systému není k dispozici dostatek hardwarových vláken pro splnění minimální souběžnosti pro všechny plánovače bez sdílení prostředků. Další možností je to, že prostředky se dočasně přiřazují jiným plánovačům, když ji vlastnící Plánovač nepoužívají, a to prostřednictvím všech kořenových adresářů virtuálních procesorů v tomto hardwarovém vlákně, které je deaktivované.

Úroveň předplatného hardwarového vlákna vychází z počtu přihlášených vláken a aktivovaných kořenových adresářů virtuálních procesorů přidružených k tomuto hardwarovému vláknu. Z pohledu konkrétního plánovače je externí úroveň předplatného hardwarového vlákna součástí předplatného, ke kterému přispěje jiné plánovače. Oznámení o tom, že prostředky jsou na externě zaneprázdněná, se odesílají do Scheduleru, když je externí předplatné na hardwarovém vlákně z předchozí kladné hodnoty nula.

Oznámení prostřednictvím této metody jsou odesílána pouze do schedulerů, které mají zásadu, kde je hodnota klíče zásad `MinConcurrency` rovna hodnotě pro klíč zásad `MaxConcurrency`. Další informace o zásadách plánovače najdete v tématu [SchedulerPolicy](schedulerpolicy-class.md).

Plánovač, který v oznámeních vyhovuje, získá sadu počátečních oznámení při jejich vytvoření, informuje o tom, jestli prostředky, které jste právě přiřadili, jsou externě zaneprázdněné nebo nečinné.

## <a name="removevirtualprocessors"></a>IScheduler:: RemoveVirtualProcessors – – metoda

Inicializuje odebrání kořenových adresářů virtuálních procesorů, které byly dříve přiděleny tomuto plánovači.

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Pole rozhraní `IVirtualProcessorRoot` reprezentujících kořeny virtuálních procesorů, které se mají odebrat.

*count*<br/>
Počet `IVirtualProcessorRoot` rozhraní v poli.

### <a name="remarks"></a>Poznámky

Správce prostředků vyvolá metodu `RemoveVirtualProcessors`, která vrátí sadu kořenových adresářů virtuálních procesorů z plánovače. Je očekáváno, že Scheduler vyvolá metodu [Remove](iexecutionresource-structure.md#remove) pro každé rozhraní, když se provede s kořeny virtuálního procesoru. Nepoužívejte rozhraní `IVirtualProcessorRoot`, když jste v něm vyvolali metodu `Remove`.

Parametr `ppVirtualProcessorRoots` odkazuje na pole rozhraní. V rámci sady kořenových adresářů virtuálních procesorů, které se mají odebrat, nejsou kořeny nikdy aktivované pomocí metody `Remove`. Kořeny, které byly aktivovány a jsou buď vykonávány do práce, nebo byly deaktivovány a čekají na doručení práce, by měly být vráceny asynchronně. Plánovač musí provést pokus o odebrání kořenového virtuálního procesoru co nejrychlejší. Zpoždění odebrání kořenových adresářů virtuálních procesorů může mít za následek neúmyslné neúmyslné předplatné v rámci plánovače.

## <a name="statistics"></a>IScheduler:: Statistics – metoda

Poskytuje informace týkající se doručení a sazeb dokončení úloh a změny ve frontě pro Plánovač.

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>Parametry

*pTaskCompletionRate*<br/>
Počet úloh, které byly dokončeny plánovačem od posledního volání této metody.

*pTaskArrivalRate*<br/>
Počet úkolů, které byly doručeny do plánovače od posledního volání této metody.

*pNumberOfTasksEnqueued*<br/>
Celkový počet úloh ve všech frontách plánovače.

### <a name="remarks"></a>Poznámky

Tuto metodu vyvolá Správce prostředků, aby bylo možné shromáždit statistiky pro Plánovač. Zde shromážděné statistiky budou sloužit k tomu, aby bylo možné určit, kdy je vhodné k plánovači přiřadit více prostředků a kdy se prostředky mají opustit. Hodnoty, které poskytuje Scheduler, můžou být optimistické a nemusí nutně odpovídat aktuálnímu počtu.

Tuto metodu byste měli implementovat, pokud chcete, aby Správce prostředků používala zpětnou vazbu týkající se takových věcí jako doručení úkolu, aby bylo možné určit, jak vyrovnávat prostředky mezi plánovačem a dalšími plánovači zaregistrovanými v Správce prostředků. Pokud se rozhodnete Neshromažďovat statistiky, můžete nastavit klíč zásady `DynamicProgressFeedback` na hodnotu `DynamicProgressFeedbackDisabled` v zásadách plánovače a Správce prostředků tuto metodu ve vašem plánovači vyvolat.

V případě nepřítomnosti statistických informací Správce prostředků použijí úrovně předplatného hardwarového vlákna k provedení rozhodnutí o přidělení a migraci prostředků. Další informace o úrovních předplatného najdete v tématu [IExecutionResource:: CurrentSubscriptionLevel –](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[PolicyElementKey –](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy – třída](schedulerpolicy-class.md)<br/>
[IExecutionContext – struktura](iexecutioncontext-structure.md)<br/>
[IThreadProxy – struktura](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager – struktura](iresourcemanager-structure.md)
