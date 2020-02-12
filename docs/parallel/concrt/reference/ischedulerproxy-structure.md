---
title: ISchedulerProxy – struktura
ms.date: 11/04/2016
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
ms.openlocfilehash: 776f70f9b93eb2e38151ceb5e84b4664420cf954
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140335"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy – struktura

Rozhraní, podle kterého budou schedulery komunikovat s Správce prostředků Concurrency Runtime k vyjednání přidělení prostředků.

## <a name="syntax"></a>Syntaxe

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[ISchedulerProxy:: Bindcontext –](#bindcontext)|Přidruží kontext spuštění k proxy vláknu, pokud ještě není přidružen k jednomu.|
|[ISchedulerProxy:: CreateOversubscriber –](#createoversubscriber)|Vytvoří nový kořen virtuálního procesoru v hardwarovém vlákně přidruženém k existujícímu prostředku spuštění.|
|[ISchedulerProxy:: RequestInitialVirtualProcessors –](#requestinitialvirtualprocessors)|Vyžádá počáteční přidělení kořenových adresářů virtuálních procesorů. Každý kořen virtuálního procesoru představuje možnost spuštění jednoho vlákna, které může pro Plánovač provádět práci.|
|[ISchedulerProxy:: Shutdown](#shutdown)|Oznamuje Správce prostředků, že se Plánovač vypíná. Tato akce způsobí, že Správce prostředků okamžitě uvolní všechny prostředky udělené plánovači.|
|[ISchedulerProxy:: SubscribeCurrentThread –](#subscribecurrentthread)|Zaregistruje aktuální vlákno do Správce prostředků a přidruží ho k tomuto plánovači.|
|[ISchedulerProxy:: UnbindContext](#unbindcontext)|Zruší přidružení proxy vlákna z kontextu spuštění určeného parametrem `pContext` a vrátí ho do bezplatného fondu objektů proxy vlákna. Tato metoda může být volána pouze v kontextu spuštění, který byl svázán prostřednictvím metody [ISchedulerProxy:: bindcontext –](#bindcontext) a ještě nebyla spuštěna, pomocí parametru `pContext` volání metody [IThreadProxy:: SwitchTo –](ithreadproxy-structure.md#switchto) .|

## <a name="remarks"></a>Poznámky

Správce prostředků do každého plánovače, který se registruje pomocí metody [IResourceManager:: registerscheduler –](iresourcemanager-structure.md#registerscheduler) , zavolá `ISchedulerProxy` rozhraní.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ISchedulerProxy`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="bindcontext"></a>ISchedulerProxy:: Bindcontext – – metoda

Přidruží kontext spuštění k proxy vláknu, pokud ještě není přidružen k jednomu.

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Rozhraní pro kontext spuštění, které se přidruží k proxy vlákna.

### <a name="remarks"></a>Poznámky

V normálním případě metoda [IThreadProxy:: SwitchTo –](ithreadproxy-structure.md#switchto) vytvoří vazby proxy vlákna k kontextu spuštění na vyžádání. Existují však situace, kdy je nutné svázat kontext předem, aby se zajistilo, že se `SwitchTo` metoda přepíná na již vázaný kontext. Jedná se o případ v kontextu plánování UMS, protože nemůže volat metody, které přidělují paměť, a vazba proxy vlákna může zahrnovat přidělení paměti, pokud proxy vlákna není k dispozici v bezplatném fondu objektu pro vytváření proxy vláken.

`invalid_argument` je vyvolána, pokud `pContext` parametru má hodnotu `NULL`.

## <a name="createoversubscriber"></a>ISchedulerProxy:: CreateOversubscriber – – metoda

Vytvoří nový kořen virtuálního procesoru v hardwarovém vlákně přidruženém k existujícímu prostředku spuštění.

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>Parametry

*pExecutionResource*<br/>
Rozhraní `IExecutionResource`, které představuje hardwarové vlákno, pro které chcete přehlásit odběr.

### <a name="return-value"></a>Návratová hodnota

Rozhraní `IVirtualProcessorRoot`.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte v případě, že váš Plánovač chce po omezené době vymezit předplatné konkrétního hardwarového vlákna. Až budete s kořenovým adresářem virtuálního procesoru hotovi, měli byste ho vrátit do Správce prostředků voláním metody [Remove](iexecutionresource-structure.md#remove) v rozhraní `IVirtualProcessorRoot`.

Můžete dokonce přeodebírat stávající kořen virtuálního procesoru, protože rozhraní `IVirtualProcessorRoot` dědí z rozhraní `IExecutionResource`.

## <a name="requestinitialvirtualprocessors"></a>ISchedulerProxy:: RequestInitialVirtualProcessors – – metoda

Vyžádá počáteční přidělení kořenových adresářů virtuálních procesorů. Každý kořen virtuálního procesoru představuje možnost spuštění jednoho vlákna, které může pro Plánovač provádět práci.

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>Parametry

*doSubscribeCurrentThread*<br/>
Zda se má přihlásit k odběru aktuálního vlákna a účtu během přidělování prostředků.

### <a name="return-value"></a>Návratová hodnota

Rozhraní `IExecutionResource` pro aktuální vlákno, pokud parametr `doSubscribeCurrentThread` má hodnotu **true**. Pokud je hodnota **false**, vrátí metoda hodnotu null.

### <a name="remarks"></a>Poznámky

Předtím, než Scheduler spustí veškerou práci, by měl tuto metodu použít k vyžádání kořenových adresářů virtuálních procesorů z Správce prostředků. Správce prostředků k zásadám plánovače přistupuje pomocí [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy) a pomocí hodnot klíčů zásad `MinConcurrency`, `MaxConcurrency` a `TargetOversubscriptionFactor` k určení, kolik hardwarových vláken se má nejdřív přiřadit plánovači, a kolik kořenových virtuálních procesorů se má vytvořit pro každé vlákno hardwaru. Další informace o tom, jak se používají zásady plánovače k určení počátečního přidělení plánovače, najdete v tématu [PolicyElementKey –](concurrency-namespace-enums.md).

Správce prostředků přidělí prostředky plánovači voláním metody [IScheduler:: AddVirtualProcessors –](ischeduler-structure.md#addvirtualprocessors) se seznamem kořenových adresářů virtuálních procesorů. Metoda je vyvolána jako zpětné volání do Scheduleru před tím, než tato metoda vrátí.

Pokud Plánovač požadoval odběr pro aktuální vlákno nastavením parametru `doSubscribeCurrentThread` na **hodnotu true**, metoda vrátí rozhraní `IExecutionResource`. Předplatné je nutné ukončit později v pozdějším bodě pomocí metody [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) .

Při určování, které hardwarové podprocesy jsou vybrány, se Správce prostředků pokusí o optimalizaci pro spřažení uzlů procesoru. Pokud je pro aktuální vlákno požadováno předplatné, je známa, že aktuální vlákno je v úmyslu zúčastnit se práce přiřazené tomuto plánovači. V takovém případě se přidělené kořenové virtuální procesory nacházejí v uzlu procesoru, na kterém je spuštěno aktuální vlákno, pokud je to možné.

Přihlášení k odběru vlákna zvyšuje úroveň předplatného podkladového vlákna hardwaru o jednu. Úroveň předplatného se po ukončení předplatného zmenší o jednu. Další informace o úrovních předplatného najdete v tématu [IExecutionResource:: CurrentSubscriptionLevel –](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="shutdown"></a>ISchedulerProxy:: Shutdown – metoda

Oznamuje Správce prostředků, že se Plánovač vypíná. Tato akce způsobí, že Správce prostředků okamžitě uvolní všechny prostředky udělené plánovači.

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>Poznámky

Všechna `IExecutionContext` rozhraní, která Scheduler přijal jako výsledek odběru externího vlákna pomocí metod `ISchedulerProxy::RequestInitialVirtualProcessors` nebo `ISchedulerProxy::SubscribeCurrentThread` musí být vrácen do Správce prostředků pomocí `IExecutionResource::Remove` předtím, než se Plánovač vypíná.

Pokud má váš Plánovač nějaké deaktivované kořenové adresáře virtuálních procesorů, musíte je aktivovat pomocí [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate)a nechat spuštěné proxy vlákna. ponechají metodu `Dispatch` kontextů provádění, které odesílají, než `Shutdown` vyvoláte na proxy serveru Scheduleru.

Služba Scheduler není nutná k tomu, aby mohl jednotlivě vracet všechny kořenové adresáře virtuálních procesorů, které jim Správce prostředků uděleny prostřednictvím volání metody `Remove`, protože všechny kořeny virtuálních procesorů se vrátí do Správce prostředků při vypnutí.

## <a name="subscribecurrentthread"></a>ISchedulerProxy:: SubscribeCurrentThread – – metoda

Zaregistruje aktuální vlákno do Správce prostředků a přidruží ho k tomuto plánovači.

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>Návratová hodnota

`IExecutionResource`, která představuje aktuální vlákno v modulu runtime.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, pokud chcete, aby Správce prostředků účet pro aktuální vlákno při přidělování prostředků plánovači a dalším plánovačům. To je užitečné hlavně v případě, že se plány vláken účastní práce zařazené do fronty plánovače spolu s kořeny virtuálního procesoru, které Plánovač obdrží z Správce prostředků. Správce prostředků používá informace k tomu, aby nedocházelo k zbytečnému nadměrnému navýšení hardwarových vláken v systému.

Prostředek spuštění přijatý prostřednictvím této metody by měl být vrácen do Správce prostředků pomocí metody [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) . Vlákno, které volá metodu `Remove` musí být stejné jako vlákno, které dříve volalo metodu `SubscribeCurrentThread`.

Přihlášení k odběru vlákna zvyšuje úroveň předplatného podkladového vlákna hardwaru o jednu. Úroveň předplatného se po ukončení předplatného zmenší o jednu. Další informace o úrovních předplatného najdete v tématu [IExecutionResource:: CurrentSubscriptionLevel –](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="unbindcontext"></a>ISchedulerProxy:: UnbindContext – metoda

Zruší přidružení proxy vlákna z kontextu spuštění určeného parametrem `pContext` a vrátí ho do bezplatného fondu objektů proxy vlákna. Tato metoda může být volána pouze v kontextu spuštění, který byl svázán prostřednictvím metody [ISchedulerProxy:: bindcontext –](#bindcontext) a ještě nebyla spuštěna, pomocí parametru `pContext` volání metody [IThreadProxy:: SwitchTo –](ithreadproxy-structure.md#switchto) .

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontext spuštění, který se má zrušit přidružení k proxy vlákna.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)<br/>
[IThreadProxy – struktura](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager – struktura](iresourcemanager-structure.md)
