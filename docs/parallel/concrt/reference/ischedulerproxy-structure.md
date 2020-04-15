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
ms.openlocfilehash: f4a9e79c2da56406610ad6da08fb438e2f92923d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368159"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy – struktura

Rozhraní, pomocí kterého plánovači komunikují se Správcem prostředků modulu Resourcetime souběžnosti za účelem vyjednání přidělení prostředků.

## <a name="syntax"></a>Syntaxe

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[ISchedulerProxy::BindContext](#bindcontext)|Přidruží kontext spuštění k proxy vlákna, pokud již není přidružen k jednomu.|
|[ISchedulerProxy::CreateOversubscriber](#createoversubscriber)|Vytvoří nový kořen virtuálního procesoru v hardwarovém vlákně přidruženém k existujícímu prostředku spuštění.|
|[ISchedulerProxy::RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|Požaduje počáteční přidělení kořenů virtuálního procesoru. Každý kořen virtuálního procesoru představuje schopnost spustit jedno vlákno, které může provádět práci pro plánovače.|
|[ISchedulerProxy::Vypnutí](#shutdown)|Upozorní Správce prostředků, že plánovač se vypíná. To způsobí, že Správce prostředků okamžitě znovu získat všechny prostředky poskytnuté plánovači.|
|[ISchedulerProxy::SubscribeCurrentThread](#subscribecurrentthread)|Zaregistruje aktuální vlákno se Správceprostředků a přissokuje jej k tomuto plánovači.|
|[ISchedulerProxy::UnbindContext](#unbindcontext)|Odpojí proxy vlákna z kontextu spuštění `pContext` určeného parametrem a vrátí jej do volného fondu proxy vlákna. Tato metoda může být volána pouze v kontextu spuštění, který byl vázán prostřednictvím metody [ISchedulerProxy::BindContext](#bindcontext) a ještě nebyla spuštěna prostřednictvím parametru `pContext` volání metody [IThreadProxy::SwitchTo.](ithreadproxy-structure.md#switchto)|

## <a name="remarks"></a>Poznámky

Správce prostředků předá `ISchedulerProxy` rozhraní každému plánovači, který se s ním zaregistruje pomocí metody [IResourceManager::RegisterScheduler.](iresourcemanager-structure.md#registerscheduler)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ISchedulerProxy`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="ischedulerproxybindcontext-method"></a><a name="bindcontext"></a>ISchedulerProxy::Metoda BindContext

Přidruží kontext spuštění k proxy vlákna, pokud již není přidružen k jednomu.

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pKontext*<br/>
Rozhraní kontextu spuštění přidružit k proxy podprocesu.

### <a name="remarks"></a>Poznámky

Metoda [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto) obvykle sváže proxy vlákna s kontextem spuštění na vyžádání. Existují však okolnosti, kdy je nutné předem svázat kontext, aby bylo zajištěno, že `SwitchTo` metoda přepne na již vázaný kontext. To je případ v kontextu plánování UMS, protože nemůže volat metody, které přidělují paměť, a vazba proxy vlákna může zahrnovat přidělení paměti, pokud proxy vlákna není snadno dostupná ve volném fondu továrně proxy vlákna.

`invalid_argument`je vyvolána, `pContext` pokud má `NULL`parametr hodnotu .

## <a name="ischedulerproxycreateoversubscriber-method"></a><a name="createoversubscriber"></a>ISchedulerProxy::Metoda CreateOversubscriber

Vytvoří nový kořen virtuálního procesoru v hardwarovém vlákně přidruženém k existujícímu prostředku spuštění.

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>Parametry

*pExecutionResource*<br/>
Rozhraní, `IExecutionResource` které představuje hardwarové vlákno, které chcete přepsat.

### <a name="return-value"></a>Návratová hodnota

Rozhraní. `IVirtualProcessorRoot`

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, pokud plánovač chce přepsat určité hardwarové vlákno po omezenou dobu. Jakmile budete hotovi s kořenem virtuálního procesoru, měli [Remove](iexecutionresource-structure.md#remove) byste jej `IVirtualProcessorRoot` vrátit do správce prostředků voláním Remove metoda na rozhraní.

Můžete dokonce oversubscribe existující kořen virtuálního `IVirtualProcessorRoot` procesoru, `IExecutionResource` protože rozhraní dědí z rozhraní.

## <a name="ischedulerproxyrequestinitialvirtualprocessors-method"></a><a name="requestinitialvirtualprocessors"></a>ISchedulerProxy::RequestInitialVirtualProcessors Method

Požaduje počáteční přidělení kořenů virtuálního procesoru. Každý kořen virtuálního procesoru představuje schopnost spustit jedno vlákno, které může provádět práci pro plánovače.

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>Parametry

*doSubscribeCurrentThread*<br/>
Určuje, zda se má přihlásit k odběru aktuálního vlákna a účet pro něj během přidělení prostředků.

### <a name="return-value"></a>Návratová hodnota

Rozhraní `IExecutionResource` pro aktuální vlákno, pokud `doSubscribeCurrentThread` má parametr hodnotu **true**. Pokud je hodnota **false**, metoda vrátí NULL.

### <a name="remarks"></a>Poznámky

Před plánovač provede jakoukoli práci, měl by použít tuto metodu k vyžádání kořeny virtuální procesor z Resource Manager. Správce prostředků bude přistupovat k zásadám plánovače pomocí [IScheduler::GetPolicy](ischeduler-structure.md#getpolicy) `MinConcurrency`a `MaxConcurrency` `TargetOversubscriptionFactor` použije hodnoty pro klíče zásad a určí, kolik hardwarových podprocesů má být nejprve přiřazeno plánovači a kolik kořenů virtuálního procesoru má být vytvořit pro každé hardwarové vlákno. Další informace o tom, jak se zásady plánovače používají k určení počátečního přidělení plánovače, naleznete v [tématu PolicyElementKey](concurrency-namespace-enums.md).

Správce prostředků uděluje prostředky plánovači voláním metody [IScheduler::AddVirtualProcessors](ischeduler-structure.md#addvirtualprocessors) se seznamem kořenů virtuálního procesoru. Metoda je vyvolána jako zpětné volání do plánovače před tato metoda vrátí.

Pokud plánovač požadované odběr pro aktuální vlákno `doSubscribeCurrentThread` nastavením parametru **true**, metoda vrátí `IExecutionResource` rozhraní. Odběr musí být ukončen později pomocí [metody IExecutionResource::Remove.](iexecutionresource-structure.md#remove)

Při určování, které hardwarové podprocesy jsou vybrány, správce prostředků se pokusí optimalizovat pro spřažení uzlů procesoru. Pokud odběr je požadováno pro aktuální vlákno, je údaj, že aktuální vlákno má v úmyslu účastnit se práce přiřazené k tomuto plánovači. V takovém případě přidělené kořeny virtuálních procesorů jsou umístěny v uzlu procesoru aktuální vlákno je spuštěna na, pokud je to možné.

Akt přihlášení podprocesu zvyšuje úroveň předplatného základní ho hardwarové vlákno o jednu. Úroveň předplatného se sníží o jednu při ukončení předplatného. Další informace o úrovních předplatného naleznete v [tématu IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ischedulerproxyshutdown-method"></a><a name="shutdown"></a>ISchedulerProxy::Metoda vypnutí

Upozorní Správce prostředků, že plánovač se vypíná. To způsobí, že Správce prostředků okamžitě znovu získat všechny prostředky poskytnuté plánovači.

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>Poznámky

Všechna `IExecutionContext` rozhraní plánovače přijaté v důsledku přihlášení externí vlákno pomocí `ISchedulerProxy::RequestInitialVirtualProcessors` metod `ISchedulerProxy::SubscribeCurrentThread` nebo musí být vrácena správce prostředků pomocí `IExecutionResource::Remove` před plánovač vypne sám.

Pokud váš plánovač měl deaktivované kořeny virtuálního procesoru, musíte je aktivovat pomocí [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate)a nechat proxy vlákna, které jsou na nich spuštěny, ponechat `Dispatch` metodu kontextů spuštění, které odesílávají, před vyvoláním `Shutdown` na proxy plánovači.

Není nutné, aby plánovač jednotlivě vrátil všechny kořeny virtuálního procesoru, které `Remove` mu Správce prostředků udělil prostřednictvím volání metody, protože všechny kořeny virtuálních procesorů budou při vypnutí vráceny správci prostředků.

## <a name="ischedulerproxysubscribecurrentthread-method"></a><a name="subscribecurrentthread"></a>ISchedulerProxy::Metoda SubscribeCurrentThread

Zaregistruje aktuální vlákno se Správceprostředků a přissokuje jej k tomuto plánovači.

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Propojení `IExecutionResource` představující aktuální vlákno v době běhu.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, pokud chcete, aby Správce prostředků účet pro aktuální vlákno při přidělování prostředků plánovače a další plánovače. To je užitečné zejména v případě, že vlákno plánuje účastnit se práce ve frontě na plánovače, spolu s kořeny virtuální procesor plánovač obdrží od Správce prostředků. Správce prostředků používá informace k zabránění zbytečnému přeodběru hardwarových vláken v systému.

Prostředek spuštění přijatý touto metodou by měl být vrácen Správci prostředků pomocí metody [IExecutionResource::Remove.](iexecutionresource-structure.md#remove) Podproces, který `Remove` volá metodu musí být `SubscribeCurrentThread` stejné vlákno, které dříve volal metodu.

Akt přihlášení podprocesu zvyšuje úroveň předplatného základní ho hardwarové vlákno o jednu. Úroveň předplatného se sníží o jednu při ukončení předplatného. Další informace o úrovních předplatného naleznete v [tématu IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ischedulerproxyunbindcontext-method"></a><a name="unbindcontext"></a>ISchedulerProxy::Metoda UnbindContext

Odpojí proxy vlákna z kontextu spuštění `pContext` určeného parametrem a vrátí jej do volného fondu proxy vlákna. Tato metoda může být volána pouze v kontextu spuštění, který byl vázán prostřednictvím metody [ISchedulerProxy::BindContext](#bindcontext) a ještě nebyla spuštěna prostřednictvím parametru `pContext` volání metody [IThreadProxy::SwitchTo.](ithreadproxy-structure.md#switchto)

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pKontext*<br/>
Kontext spuštění zrušit přidružení od jeho proxy vlákna.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)<br/>
[IThreadProxy – struktura](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager – struktura](iresourcemanager-structure.md)
