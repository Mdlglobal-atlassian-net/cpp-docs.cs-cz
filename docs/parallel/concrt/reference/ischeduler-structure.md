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
ms.openlocfilehash: ccd82b5c5112bc322717f2b58d79d4c8f34f5bbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368172"
---
# <a name="ischeduler-structure"></a>Struktura rozhraní IScheduler

Rozhraní k abstrakci plánovače práce. Správce prostředků modulu Souběžnost Runtime používá toto rozhraní ke komunikaci s plánovači práce.

## <a name="syntax"></a>Syntaxe

```cpp
struct IScheduler;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IScheduler::Přidat virtuální procesory](#addvirtualprocessors)|Poskytuje plánovač se sadou kořenů virtuálního procesoru pro jeho použití. Každé `IVirtualProcessorRoot` rozhraní představuje právo spustit jedno vlákno, které může provádět práci jménem plánovače.|
|[IScheduler::GetId](#getid)|Vrátí jedinečný identifikátor plánovače.|
|[IScheduler::Zásady získání](#getpolicy)|Vrátí kopii zásad plánovače. Další informace o zásadách plánovače naleznete v [tématu SchedulerPolicy](schedulerpolicy-class.md).|
|[IScheduler::NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|Upozorní tento plánovač, že hardwarová vlákna reprezentovaná sadou kořenů virtuálního procesoru v poli `ppVirtualProcessorRoots` jsou nyní používána jinými plánovači.|
|[IScheduler::NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|Upozorní tento plánovač, že hardwarová vlákna reprezentovaná sadou kořenů virtuálního procesoru v poli `ppVirtualProcessorRoots` nejsou používány jinými plánovači.|
|[IScheduler::Odebrat virtuální procesory](#removevirtualprocessors)|Iniciuje odebrání kořenů virtuálního procesoru, které byly dříve přiděleny tomuto plánovači.|
|[IScheduler::Statistika](#statistics)|Obsahuje informace týkající se míry doručení a dokončení úkolu a změnu délky fronty plánovače.|

## <a name="remarks"></a>Poznámky

Pokud implementujete vlastní plánovač, který komunikuje se Správcem prostředků, `IScheduler` měli byste poskytnout implementaci rozhraní. Toto rozhraní je jeden konec obousměrného kanálu komunikace mezi plánovačem a Správcem prostředků. Druhý konec je `IResourceManager` reprezentován `ISchedulerProxy` a rozhraní, které jsou implementovány Správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IScheduler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="ischeduleraddvirtualprocessors-method"></a><a name="addvirtualprocessors"></a>IScheduler::Metoda addvirtualprocesorů

Poskytuje plánovač se sadou kořenů virtuálního procesoru pro jeho použití. Každé `IVirtualProcessorRoot` rozhraní představuje právo spustit jedno vlákno, které může provádět práci jménem plánovače.

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Pole rozhraní `IVirtualProcessorRoot` představující kořeny virtuálního procesoru, které jsou přidávány do plánovače.

*Počet*<br/>
Počet `IVirtualProcessorRoot` rozhraní v poli.

### <a name="remarks"></a>Poznámky

Správce prostředků vyvolá `AddVirtualProcessor` metodu udělit počáteční sadu kořenů virtuálníprocesor pro plánovače. Může také vyvolat metodu přidat kořeny virtuálníprocesor do plánovače při vyvažování prostředků mezi plánovači.

## <a name="ischedulergetid-method"></a><a name="getid"></a>IScheduler::Metoda GetId

Vrátí jedinečný identifikátor plánovače.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor celého čísla.

### <a name="remarks"></a>Poznámky

Před použitím rozhraní jako parametru metody poskytované Správcem prostředků byste `IScheduler` měli použít funkci [GetSchedulerId](concurrency-namespace-functions.md) k získání jedinečného identifikátoru pro objekt, který implementuje rozhraní. Očekává se, že vrátí stejný `GetId` identifikátor při vyvolání funkce.

Identifikátor získaný z jiného zdroje může mít za následek nedefinované chování.

## <a name="ischedulergetpolicy-method"></a><a name="getpolicy"></a>IScheduler::Metoda GetPolicy

Vrátí kopii zásad plánovače. Další informace o zásadách plánovače naleznete v [tématu SchedulerPolicy](schedulerpolicy-class.md).

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Kopie zásad plánovače.

## <a name="ischedulernotifyresourcesexternallybusy-method"></a><a name="notifyresourcesexternallybusy"></a>IScheduler::Metoda NotifyResourcesExternallyBusy

Upozorní tento plánovač, že hardwarová vlákna reprezentovaná sadou kořenů virtuálního procesoru v poli `ppVirtualProcessorRoots` jsou nyní používána jinými plánovači.

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Pole `IVirtualProcessorRoot` rozhraní spojených s hardwarovými vlákny, na kterých jsou zaneprázdněni další plánovači.

*Počet*<br/>
Počet `IVirtualProcessorRoot` rozhraní v poli.

### <a name="remarks"></a>Poznámky

Je možné, že konkrétní hardwarové vlákno lze přiřadit více plánovačům současně. Jedním z důvodů může být, že v systému není dostatek hardwarových vláken, které by splňovaly minimální souběžnost pro všechny plánovače bez sdílení prostředků. Další možností je, že prostředky jsou dočasně přiřazeny k jiným plánovačům, když je vlastnící plánovač nepoužívá, prostřednictvím všech kořenů virtuálního procesoru v tomto hardwarovém vlákně, které jsou deaktivovány.

Úroveň předplatného hardwarového vlákna je označena počtem odebíraných vláken a aktivovaných kořenů virtuálního procesoru přidružených k tomuto hardwarovému vláknu. Z pohledu konkrétního plánovače je externí úroveň předplatného hardwarového vlákna částí předplatného, do které přispívají ostatní plánovači. Oznámení, že prostředky jsou externě zaneprázdněni, jsou odeslána plánovači, když se úroveň externího předplatného pro hardwarové vlákno přesune z nuly do kladné oblasti.

Oznámení prostřednictvím této metody jsou odesílány pouze plánovačům, `MinConcurrency` které mají zásadu, `MaxConcurrency` kde se hodnota klíče zásad rovná hodnotě klíče zásady. Další informace o zásadách plánovače naleznete v [tématu SchedulerPolicy](schedulerpolicy-class.md).

Plánovač, který má nárok na oznámení, získá při vytvoření sadu počátečních oznámení a informuje jej, zda jsou prostředky, které byly právě přiřazeny, externě zaneprázdněné nebo nečinné.

## <a name="ischedulernotifyresourcesexternallyidle-method"></a><a name="notifyresourcesexternallyidle"></a>IScheduler::Metoda NotifyResourcesExternallyIdle

Upozorní tento plánovač, že hardwarová vlákna reprezentovaná sadou kořenů virtuálního procesoru v poli `ppVirtualProcessorRoots` nejsou používány jinými plánovači.

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Pole `IVirtualProcessorRoot` rozhraní spojených s hardwarovými vlákny, na kterých se ostatní plánovače staly nečinnými.

*Počet*<br/>
Počet `IVirtualProcessorRoot` rozhraní v poli.

### <a name="remarks"></a>Poznámky

Je možné, že konkrétní hardwarové vlákno lze přiřadit více plánovačům současně. Jedním z důvodů může být, že v systému není dostatek hardwarových vláken, které by splňovaly minimální souběžnost pro všechny plánovače bez sdílení prostředků. Další možností je, že prostředky jsou dočasně přiřazeny k jiným plánovačům, když je vlastnící plánovač nepoužívá, prostřednictvím všech kořenů virtuálního procesoru v tomto hardwarovém vlákně, které jsou deaktivovány.

Úroveň předplatného hardwarového vlákna je označena počtem odebíraných vláken a aktivovaných kořenů virtuálního procesoru přidružených k tomuto hardwarovému vláknu. Z pohledu konkrétního plánovače je externí úroveň předplatného hardwarového vlákna částí předplatného, do které přispívají ostatní plánovači. Oznámení, že prostředky jsou externě zaneprázdněni, jsou odeslána plánovači, když úroveň externího předplatného pro hardwarové vlákno klesne na nulu z předchozí kladné hodnoty.

Oznámení prostřednictvím této metody jsou odesílány pouze plánovačům, `MinConcurrency` které mají zásadu, `MaxConcurrency` kde se hodnota klíče zásad rovná hodnotě klíče zásady. Další informace o zásadách plánovače naleznete v [tématu SchedulerPolicy](schedulerpolicy-class.md).

Plánovač, který má nárok na oznámení, získá při vytvoření sadu počátečních oznámení a informuje jej, zda jsou prostředky, které byly právě přiřazeny, externě zaneprázdněné nebo nečinné.

## <a name="ischedulerremovevirtualprocessors-method"></a><a name="removevirtualprocessors"></a>IScheduler::Metoda odebrání virtuálních procesorů

Iniciuje odebrání kořenů virtuálního procesoru, které byly dříve přiděleny tomuto plánovači.

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Pole `IVirtualProcessorRoot` rozhraní představující kořeny virtuálního procesoru, které mají být odebrány.

*Počet*<br/>
Počet `IVirtualProcessorRoot` rozhraní v poli.

### <a name="remarks"></a>Poznámky

Správce prostředků vyvolá `RemoveVirtualProcessors` metodu, která převezme sadu kořenů virtuálního procesoru z plánovače. Plánovač se očekává, že vyvolat [Remove](iexecutionresource-structure.md#remove) metoda na každé rozhraní, když se provádí s kořeny virtuální procesor. Nepoužívejte rozhraní, `IVirtualProcessorRoot` jakmile jste vyvolali metodu `Remove` na něm.

Parametr `ppVirtualProcessorRoots` odkazuje na pole rozhraní. Mezi sadu kořenů virtuálníprocesor, které mají být odstraněny, kořeny `Remove` nebyly nikdy aktivovány lze vrátit okamžitě pomocí metody. Kořeny, které byly aktivovány a jsou buď provádění práce nebo byly deaktivovány a čekají na práci, aby se dospělo, by měly být vráceny asynchronně. Plánovač musí provést každý pokus o odebrání kořenového adresáře virtuálního procesoru co nejrychleji. Zpoždění odebrání kořenů virtuálníprocesor může mít za následek neúmyslné přehlasování v rámci plánovače.

## <a name="ischedulerstatistics-method"></a><a name="statistics"></a>IScheduler::Metoda statistiky

Obsahuje informace týkající se míry doručení a dokončení úkolu a změnu délky fronty plánovače.

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>Parametry

*pÚkolCompletionRate*<br/>
Počet úkolů, které byly dokončeny plánovačem od posledního volání této metody.

*pTaskArrivalRate*<br/>
Počet úkolů, které byly doručeny do plánovače od posledního volání této metody.

*pNumberOfTasksEnqueued*<br/>
Celkový počet úkolů ve všech frontách plánovače.

### <a name="remarks"></a>Poznámky

Tato metoda je vyvolána Správce prostředků za účelem shromažďování statistiky pro plánovače. Zde shromážděné statistiky budou použity k řízení algoritmů dynamické zpětné vazby k určení, kdy je vhodné přiřadit plánovači více prostředků a kdy odebere zdroje. Hodnoty poskytované plánovačem mohou být optimistické a nemusí nutně přesně odrážet aktuální počet.

Tuto metodu byste měli implementovat, pokud chcete, aby Správce prostředků používal zpětnou vazbu o takových věcech, jako je doručení úkolu, k určení způsobu vyvážení zdroje mezi plánovačem a ostatními plánovači registrovanými ve Správci prostředků. Pokud se rozhodnete neshromažďovat statistiky, můžete `DynamicProgressFeedback` nastavit `DynamicProgressFeedbackDisabled` klíč zásady na hodnotu v zásadách plánovače a Správce prostředků nebude vyvolat tuto metodu na plánovači.

Pokud neexistují statistické informace, správce prostředků použije úrovně předplatného hardwarových vláken k rozhodování o přidělení prostředků a migraci. Další informace o úrovních předplatného naleznete v [tématu IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)<br/>
[Klíč PolicyElement](concurrency-namespace-enums.md)<br/>
[Třída SchedulerPolicy](schedulerpolicy-class.md)<br/>
[IExecutionContext – struktura](iexecutioncontext-structure.md)<br/>
[IThreadProxy – struktura](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager – struktura](iresourcemanager-structure.md)
