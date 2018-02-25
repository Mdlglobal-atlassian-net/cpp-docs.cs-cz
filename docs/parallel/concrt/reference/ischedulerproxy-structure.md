---
title: "Ischedulerproxy – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
dev_langs:
- C++
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9fa2a67b432fac1dc7ec685e6563acb87fd69087
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy – struktura
Rozhraní, pomocí kterého plánovače komunikovat se správcem prostředků pro vyjednávání přidělení prostředků Concurrency Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct ISchedulerProxy;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[ISchedulerProxy::BindContext](#bindcontext)|Přidruží kontextu provádění vlákna proxy, pokud ještě není spojen s jednou.|  
|[ISchedulerProxy::CreateOversubscriber](#createoversubscriber)|Vytvoří nový kořen virtuálních procesorů ve vlákně hardwaru přidružené existujícího provádění prostředku.|  
|[ISchedulerProxy::RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|Požadavky počáteční přidělení kořeny virtuálních procesorů. Každý procesor virtuálního kořenového představuje možnost spustit jedno vlákno, které můžete provést úlohy plánovače.|  
|[ISchedulerProxy::Shutdown](#shutdown)|Upozorní správce prostředků, že je plánovač vypíná. To způsobí, že správce prostředků, aby okamžitě uvolnit všechny prostředky udělit plánovače.|  
|[ISchedulerProxy::SubscribeCurrentThread](#subscribecurrentthread)|Zaregistruje aktuální vlákno s správce prostředků, přiřadí se mu tuto plánovače.|  
|[ISchedulerProxy::UnbindContext](#unbindcontext)|Zrušíte vlákno proxy z určeného kontextu spuštění `pContext` parametr a vrátí ji do fondu volných objekt factory proxy přístup z více vláken. Tuto metodu lze volat pouze v kontextu spuštění, který se bude vázán prostřednictvím [ischedulerproxy::bindcontext –](#bindcontext) metoda a prostřednictvím se ještě nebyla zahájena `pContext` parametr [ithreadproxy::switchto – ](ithreadproxy-structure.md#switchto) volání metody.|  
  
## <a name="remarks"></a>Poznámky  
 Resource Manager předá `ISchedulerProxy` rozhraní pro každý plánovače, který zaregistruje se pomocí [iresourcemanager::registerscheduler –](iresourcemanager-structure.md#registerscheduler) metoda.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ISchedulerProxy`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="bindcontext"></a>  ISchedulerProxy::BindContext Method  
 Přidruží kontextu provádění vlákna proxy, pokud ještě není spojen s jednou.  
  
```
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Rozhraní pro provádění kontext, který má přidružit k proxy serveru přístup z více vláken.  
  
### <a name="remarks"></a>Poznámky  
 Za normálních okolností [ithreadproxy::switchto –](ithreadproxy-structure.md#switchto) metoda vytvoří vazbu proxy přístup z více vláken na kontext provádění na vyžádání. Existují, ale okolnosti, kde je potřeba vytvořit vazbu kontextu předem lze zajistit, aby `SwitchTo` metoda přepne do kontextu již vázané. Je tomu v UMS, plánování kontextu, protože ji nelze volat metody, které přidělit paměť a vazby vlákno proxy může zahrnovat přidělení paměti, pokud vlákno proxy není ve fondu volných objektu pro vytváření proxy vlákno snadno dostupné.  
  
 `invalid_argument` je vyvolána, pokud parametr `pContext` má hodnotu `NULL`.  
  
##  <a name="createoversubscriber"></a>  Ischedulerproxy::createoversubscriber – metoda  
 Vytvoří nový kořen virtuálních procesorů ve vlákně hardwaru přidružené existujícího provádění prostředku.  
  
```
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pExecutionResource`  
 `IExecutionResource` Rozhraní, které představuje hardwaru vlákno, které chcete přidělit nadměrnému počtu procesů.  
  
### <a name="return-value"></a>Návratová hodnota  
 `IVirtualProcessorRoot` Rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, když chce vašeho scheduleru oversubscribe vlákna konkrétní hardware pro omezené množství času. Jakmile jste hotovi s kořenem virtuální procesor, by měl vrátí do Správce prostředků voláním [odebrat](iexecutionresource-structure.md#remove) metodu `IVirtualProcessorRoot` rozhraní.  
  
 Můžete dokonce oversubscribe existující kořenový virtuálních procesorů, protože `IVirtualProcessorRoot` rozhraní dědí z `IExecutionResource` rozhraní.  
  
##  <a name="requestinitialvirtualprocessors"></a>  Ischedulerproxy::requestinitialvirtualprocessors – metoda  
 Požadavky počáteční přidělení kořeny virtuálních procesorů. Každý procesor virtuálního kořenového představuje možnost spustit jedno vlákno, které můžete provést úlohy plánovače.  
  
```
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `doSubscribeCurrentThread`  
 Určuje, zda chcete objednat předplatné aktuální vlákno a zohlednily při přidělování prostředků.  
  
### <a name="return-value"></a>Návratová hodnota  
 `IExecutionResource` Rozhraní pro aktuální vlákno, pokud parametr `doSubscribeCurrentThread` má hodnotu `true`. Pokud je hodnota `false`, vrátí metoda `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Před plánovače veškerou práci, ho musí tuto metodu použijte k vyžádání kořeny virtuálních procesorů ze Správce prostředků. Správce prostředků bude plánovače zásada přístupu pomocí [ischeduler::getpolicy –](ischeduler-structure.md#getpolicy) a používají hodnoty pro klíče zásad `MinConcurrency`, `MaxConcurrency` a `TargetOversubscriptionFactor` určit počet podprocesů hardwaru přiřadit Scheduler původně a počet virtuálních procesorů kořeny vytvořit pro každé vlákno hardwaru. Další informace o jak zásady plánovače slouží k určení scheduleru pro počáteční přidělení, najdete v části [PolicyElementKey](concurrency-namespace-enums.md).  
  
 Resource Manager uděluje prostředky plánovače voláním metody [ischeduler::addvirtualprocessors –](ischeduler-structure.md#addvirtualprocessors) seznam kořeny virtuálních procesorů. Metoda je volána jako zpětné volání do plánovače předtím, než tato metoda vrátí hodnotu.  
  
 Pokud plánovač požadované předplatné pro aktuální vlákno nastavením parametru `doSubscribeCurrentThread` k `true`, vrátí tato metoda hodnotu `IExecutionResource` rozhraní. Předplatné musí být ukončen později pomocí [iexecutionresource::Remove –](iexecutionresource-structure.md#remove) metoda.  
  
 Při určování, které vláken hardwaru jsou vybrané, se pokusí Resource Manager za účelem optimalizace pro spřažení uzlu. Pokud předplatné je vyžadovaná pro aktuální vlákno, je znamená, že aktuální vlákno v úmyslu účastnit přidělena tento plánovače. V takovém případě kořeny přidělené virtuální procesory jsou umístěny na uzlu procesoru, kdy je prováděna aktuální vlákno, pokud je to možné.  
  
 Operace přihlášení k odběru vlákna zvyšuje úroveň předplatného základní hardware vlákno jedna. Úrovni předplatného se sníží o jedna při ukončení předplatného. Další informace o úrovních předplatné najdete v tématu [iexecutionresource::currentsubscriptionlevel –](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="shutdown"></a>  Ischedulerproxy::Shutdown – metoda  
 Upozorní správce prostředků, že je plánovač vypíná. To způsobí, že správce prostředků, aby okamžitě uvolnit všechny prostředky udělit plánovače.  
  
```
virtual void Shutdown() = 0;
```  
  
### <a name="remarks"></a>Poznámky  
 Všechny `IExecutionContext` rozhraní plánovače přijatých v důsledku odběr externí vlákno pomocí metody `ISchedulerProxy::RequestInitialVirtualProcessors` nebo `ISchedulerProxy::SubscribeCurrentThread` musí být vrácen Resource Manager pomocí `IExecutionResource::Remove` před plánovače ukončí sám.  
  
 Kdyby měl vašeho scheduleru žádné deaktivováno kořeny virtuálních procesorů, musíte je aktivovat pomocí [ivirtualprocessorroot::Activate –](ivirtualprocessorroot-structure.md#activate)a mít proxy přístup z více vláken provádění na nich ponechte `Dispatch` metoda spuštění kontexty jejich jsou odeslání před vyvolání `Shutdown` na proxy server plánovače.  
  
 Není nutné pro Plánovač k jednotlivě vrácení všech virtuálních procesorů kořeny Resource Manager udělit prostřednictvím volání `Remove` metoda vzhledem k tomu, že všechny virtuální procesory kořeny bude vrácen Resource Manager při vypnutí počítače.  
  
##  <a name="subscribecurrentthread"></a>  Ischedulerproxy::subscribecurrentthread – metoda  
 Zaregistruje aktuální vlákno s správce prostředků, přiřadí se mu tuto plánovače.  
  
```
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `IExecutionResource` Propojení představující aktuální vlákno v modulu runtime.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, pokud chcete, aby správce prostředků, aby účet pro aktuální vlákno při přidělování prostředků do vašeho scheduleru a dalších plánovače. Je obzvláště užitečná při plány vlákno zapojit se do práce zařazených do fronty pro Plánovač, společně s procesor virtuálního adresáře, které Plánovač obdrží ze Správce prostředků. Správce prostředků používá informace aby se zabránilo zbytečným Překryvný odběr hardwaru vláken v systému.  
  
 Provádění prostředku přijatých prostřednictvím této metody by měla být vrácena Resource Manager pomocí [iexecutionresource::Remove –](iexecutionresource-structure.md#remove) metoda. Vlákno, které volá `Remove` metoda musí být stejné vlákno, které označovaly jako `SubscribeCurrentThread` metoda.  
  
 Operace přihlášení k odběru vlákna zvyšuje úroveň předplatného základní hardware vlákno jedna. Úrovni předplatného se sníží o jedna při ukončení předplatného. Další informace o úrovních předplatné najdete v tématu [iexecutionresource::currentsubscriptionlevel –](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="unbindcontext"></a>  Ischedulerproxy::unbindcontext – metoda  
 Zrušíte vlákno proxy z určeného kontextu spuštění `pContext` parametr a vrátí ji do fondu volných objekt factory proxy přístup z více vláken. Tuto metodu lze volat pouze v kontextu spuštění, který se bude vázán prostřednictvím [ischedulerproxy::bindcontext –](#bindcontext) metoda a prostřednictvím se ještě nebyla zahájena `pContext` parametr [ithreadproxy::switchto – ](ithreadproxy-structure.md#switchto) volání metody.  
  
```
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Kontext spuštění pro zrušení přiřazení z jeho proxy přístup z více vláken.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Struktura rozhraní IScheduler](ischeduler-structure.md)   
 [Ithreadproxy – struktura](ithreadproxy-structure.md)   
 [Ivirtualprocessorroot – struktura](ivirtualprocessorroot-structure.md)   
 [IResourceManager – struktura](iresourcemanager-structure.md)
