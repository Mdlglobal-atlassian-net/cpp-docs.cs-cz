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
ms.openlocfilehash: a38b931da8ed2191f21d210449c100c410f74e85
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523141"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy – struktura

Rozhraní, pomocí kterého plánovači komunikovat se správcem prostředků pro vyjednávání přidělení prostředků modulu Runtime souběžnosti.

## <a name="syntax"></a>Syntaxe

```
struct ISchedulerProxy;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[ISchedulerProxy::BindContext](#bindcontext)|Pokud ještě není přidružený nejméně k jednomu přidruží vlákno proxy kontextu spuštění.|
|[ISchedulerProxy::CreateOversubscriber](#createoversubscriber)|Vytvoří nový kořen virtuálního procesoru na vlákno hardwaru spojené s existujícím prostředkem spuštění.|
|[ISchedulerProxy::RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|Požádá o počáteční přidělení kořenových adresářů virtuálního procesoru. Každý kořen virtuálního procesoru představuje možnost spustit jedno vlákno, které provádí práci pro Plánovač.|
|[ISchedulerProxy::Shutdown](#shutdown)|Upozorní správce prostředků, že je plánovač vypínání. To způsobí, že správce prostředků okamžitě uvolnit všechny prostředky, které jsou udělena pro Plánovač.|
|[ISchedulerProxy::SubscribeCurrentThread](#subscribecurrentthread)|Zaregistruje se správcem prostředků, přiřadí se mu tento plánovač aktuální vlákno.|
|[ISchedulerProxy::UnbindContext](#unbindcontext)|Zruší přidružení proxy vlákna od určeného kontextu spuštění `pContext` parametr a vrátí ji do volného fondu objekt factory proxy vlákna. Tuto metodu lze volat pouze v kontextu spuštění, který se bude vázán prostřednictvím [ischedulerproxy::bindcontext –](#bindcontext) metoda a nebyla dosud spuštěna prostřednictvím se `pContext` parametr [ithreadproxy::switchto – ](ithreadproxy-structure.md#switchto) volání metody.|

## <a name="remarks"></a>Poznámky

Předá Resource Manageru `ISchedulerProxy` rozhraní pro každou plánovače, která se registruje pomocí [iresourcemanager::registerscheduler –](iresourcemanager-structure.md#registerscheduler) metody.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ISchedulerProxy`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Namespace:** souběžnosti

##  <a name="bindcontext"></a>  Ischedulerproxy::bindcontext – metoda

Pokud ještě není přidružený nejméně k jednomu přidruží vlákno proxy kontextu spuštění.

```
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Rozhraní pro kontext spuštění pro přidružení k proxy vlákna.

### <a name="remarks"></a>Poznámky

Za normálních okolností [ithreadproxy::switchto –](ithreadproxy-structure.md#switchto) metoda vytvoří vazbu mezi proxy vlákna a kontext spuštění na vyžádání. Existují, ale okolností, kde je potřeba vytvořit vazbu kontextu předem zajistit, aby `SwitchTo` metoda přepne do již vázané kontextu. V takovém na UMS plánování kontextu, protože ji nelze volat metody, které přidělení paměti a vazby proxy vlákna může zahrnovat přidělení paměti, pokud vlákno proxy není snadno dostupné ve fondu volných objektu pro vytváření proxy vlákna.

`invalid_argument` je vyvolána, pokud parametr `pContext` má hodnotu `NULL`.

##  <a name="createoversubscriber"></a>  Ischedulerproxy::createoversubscriber – metoda

Vytvoří nový kořen virtuálního procesoru na vlákno hardwaru spojené s existujícím prostředkem spuštění.

```
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>Parametry

*pExecutionResource*<br/>
`IExecutionResource` Rozhraní, které představuje vlákno hardwaru, kterou chcete přidělit nadměrnému počtu procesů.

### <a name="return-value"></a>Návratová hodnota

`IVirtualProcessorRoot` Rozhraní.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, pokud váš Plánovač chce přidělit nadměrnému počtu procesů vlákno konkrétní hardware pro omezené časové období. Až budete hotovi s kořen virtuálního procesoru, měli byste vrátit se k resource Manageru pomocí volání [odebrat](iexecutionresource-structure.md#remove) metodu `IVirtualProcessorRoot` rozhraní.

Můžete dokonce oversubscribe existující kořen virtuálního procesoru, protože `IVirtualProcessorRoot` rozhraní zdědí `IExecutionResource` rozhraní.

##  <a name="requestinitialvirtualprocessors"></a>  Ischedulerproxy::requestinitialvirtualprocessors – metoda

Požádá o počáteční přidělení kořenových adresářů virtuálního procesoru. Každý kořen virtuálního procesoru představuje možnost spustit jedno vlákno, které provádí práci pro Plánovač.

```
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>Parametry

*doSubscribeCurrentThread*<br/>
Určuje, zda odběru aktuální vlákno a zohlednily při přidělování prostředků.

### <a name="return-value"></a>Návratová hodnota

`IExecutionResource` Rozhraní pro aktuální vlákno, pokud parametr `doSubscribeCurrentThread` má hodnotu **true**. Pokud je hodnota **false**, metoda vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Předtím, než Plánovač spustí každé dílo, ji by měl tuto metodu použijte k vyžádání kořenových adresářů virtuálního procesoru ze Správce prostředků. Zásady plánovače bude přístupu Resource Manageru pomocí [ischeduler::getpolicy –](ischeduler-structure.md#getpolicy) a použijte hodnoty pro klíče zásad `MinConcurrency`, `MaxConcurrency` a `TargetOversubscriptionFactor` určit počet podprocesů hardwaru přiřadit Plánovač zpočátku a kolik kořenových adresářů virtuálního procesoru, chcete-li vytvořit pro každé vlákno hardwaru. Další informace o použití zásad plánovače se určí přidělený objem počáteční Plánovač, naleznete v tématu [policyelementkey –](concurrency-namespace-enums.md).

Resource Manager uděluje prostředky do fronty plánovače voláním metody [ischeduler::addvirtualprocessors –](ischeduler-structure.md#addvirtualprocessors) seznam kořenových adresářů virtuálního procesoru. Metoda je vyvolána jako zpětné volání do plánovače dříve, než tato metoda vrátí.

Pokud plánovač požadované předplatné pro aktuální vlákno tak, že nastavíte parametr `doSubscribeCurrentThread` k **true**, metoda vrátí `IExecutionResource` rozhraní. Předplatné musí být ukončen později pomocí [iexecutionresource::Remove –](iexecutionresource-structure.md#remove) metody.

Při určování, které hardwarových vláken jsou vybrané, se pokusí optimalizovat pro spřažení uzlu Resource Manageru. Pokud je požadováno předplatné pro aktuální vlákno je znamením, že si klade za cíl aktuální vlákno k účasti v práci, která tento plánovač přiřazena. V takovém případě kořeny přidělené virtuální procesory jsou umístěny na uzlu procesoru, na který se provádí aktuální vlákno, pokud je to možné.

V rámci přihlášení k odběru vlákna zvýší o 1 úroveň předplatného podkladové vlákno hardwaru. Na úrovni předplatného se sníží o jedna při ukončení předplatného. Další informace na úrovni předplatného najdete v tématu [iexecutionresource::currentsubscriptionlevel –](iexecutionresource-structure.md#currentsubscriptionlevel).

##  <a name="shutdown"></a>  Ischedulerproxy::Shutdown – metoda

Upozorní správce prostředků, že je plánovač vypínání. To způsobí, že správce prostředků okamžitě uvolnit všechny prostředky, které jsou udělena pro Plánovač.

```
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>Poznámky

Všechny `IExecutionContext` rozhraní plánovače přijatých v důsledku přihlášení k odběru vnějším vláknem pomocí metod `ISchedulerProxy::RequestInitialVirtualProcessors` nebo `ISchedulerProxy::SubscribeCurrentThread` musí být vrácen do Resource Manageru pomocí `IExecutionResource::Remove` před plánovače ukončí sám.

Pokud má váš Plánovač žádné deaktivuje kořenových adresářů virtuálního procesoru, je nutné aktivovat pomocí [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate)a mít proxy vlákna provádění v nich ponechte `Dispatch` metoda spuštění kontexty, jsou odesílání před vyvoláte `Shutdown` na Plánovač proxy.

Není nutné pro Plánovač jednotlivě vrácení všech kořenových adresářů virtuálního procesoru Resource Manageru udělit prostřednictvím volání `Remove` metoda vzhledem k tomu, že všechny kořeny virtuálních procesorů se vrátí do Resource Manageru při vypnutí.

##  <a name="subscribecurrentthread"></a>  Ischedulerproxy::subscribecurrentthread – metoda

Zaregistruje se správcem prostředků, přiřadí se mu tento plánovač aktuální vlákno.

```
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>Návratová hodnota

`IExecutionResource` Vzájemném propojování představující aktuální vlákno v modulu runtime.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, pokud chcete, aby správce prostředků, aby účet pro aktuální vlákno při přidělování prostředků pro váš Plánovač a dalších plánovače. Je užitečné zejména při plány vlákno k účasti na práci ve frontě váš Plánovač, spolu s kořenových adresářů virtuálního procesoru, který Plánovač obdrží z Resource Manageru. Resource Manageru používá informací zabránit zbytečným překročení stanovených množství vláken hardwaru v systému.

Spuštění prostředků přijatých prostřednictvím této metody se vrátit do Resource Manageru pomocí [iexecutionresource::Remove –](iexecutionresource-structure.md#remove) metody. Vlákna, která se volá `Remove` metoda musí být stejném vlákně, které dříve označované jako `SubscribeCurrentThread` metody.

V rámci přihlášení k odběru vlákna zvýší o 1 úroveň předplatného podkladové vlákno hardwaru. Na úrovni předplatného se sníží o jedna při ukončení předplatného. Další informace na úrovni předplatného najdete v tématu [iexecutionresource::currentsubscriptionlevel –](iexecutionresource-structure.md#currentsubscriptionlevel).

##  <a name="unbindcontext"></a>  Ischedulerproxy::unbindcontext – metoda

Zruší přidružení proxy vlákna od určeného kontextu spuštění `pContext` parametr a vrátí ji do volného fondu objekt factory proxy vlákna. Tuto metodu lze volat pouze v kontextu spuštění, který se bude vázán prostřednictvím [ischedulerproxy::bindcontext –](#bindcontext) metoda a nebyla dosud spuštěna prostřednictvím se `pContext` parametr [ithreadproxy::switchto – ](ithreadproxy-structure.md#switchto) volání metody.

```
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontext spuštění zrušit přiřazení z jeho proxy vlákna.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)<br/>
[IThreadProxy – struktura](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager – struktura](iresourcemanager-structure.md)
