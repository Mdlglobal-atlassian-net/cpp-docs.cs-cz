---
title: Iexecutionresource – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
dev_langs:
- C++
helpviewer_keywords:
- IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc69c30f30d25179427ee8e59c536bb7cb5b483d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="iexecutionresource-structure"></a>IExecutionResource – struktura
Abstrakci pro vlákno hardwaru.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IExecutionResource;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Iexecutionresource::currentsubscriptionlevel –](#currentsubscriptionlevel)|Vrátí počet virtuálních procesorů aktivovaný kořeny a odběru externí vláken aktuálně přidružen základní hardware vlákno, které představuje tohoto provádění prostředku.|  
|[Iexecutionresource::getexecutionresourceid –](#getexecutionresourceid)|Vrací jedinečný identifikátor podprocesu hardwaru, který představuje tuto provádění prostředku.|  
|[Iexecutionresource::getnodeid –](#getnodeid)|Vrací jedinečný identifikátor procesoru uzlu, který patří tohoto provádění prostředku.|  
|[Iexecutionresource::Remove –](#remove)|Vrátí tohoto provádění prostředku Resource Manager.|  
  
## <a name="remarks"></a>Poznámky  
 Provádění prostředků může být samostatný nebo ve spojení s kořeny virtuálních procesorů. Samostatné provádění prostředku se vytvoří při vlákno v aplikaci vytvoří odběr přístup z více vláken. Metody [ISchedulerProxy::SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) a [ischedulerproxy::requestinitialvirtualprocessors –](ischedulerproxy-structure.md#requestinitialvirtualprocessors) vytvářet odběry přístup z více vláken a vrátit `IExecutionResource` představující rozhraní předplatné. Vytváření vláken odběru je způsob, jak informovat správce prostředků, který se dané vlákno se bude podílet na práci zařazených do fronty pro Plánovač, společně s procesor virtuálního adresáře, které správce prostředků přiřadí plánovače. Správce prostředků používá informace předejdete oversubscribing hardwaru vláken kde provádět.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IExecutionResource`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="currentsubscriptionlevel"></a>  Iexecutionresource::currentsubscriptionlevel – metoda  
 Vrátí počet virtuálních procesorů aktivovaný kořeny a odběru externí vláken aktuálně přidružen základní hardware vlákno, které představuje tohoto provádění prostředku.  
  
```
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální úroveň předplatného.  
  
### <a name="remarks"></a>Poznámky  
 Úrovni předplatného zjistíte, jak velký počet spuštěných vláken jsou přidruženy vlákno hardwaru. To zahrnuje jenom vláken, která si je vědoma ve formě odebírané vláken a kořeny virtuálních procesorů, které jsou aktivně provádění vlákna proxy Resource Manager.  
  
 Volání metody [ischedulerproxy::subscribecurrentthread –](ischedulerproxy-structure.md#subscribecurrentthread), nebo metodu [ischedulerproxy::requestinitialvirtualprocessors –](ischedulerproxy-structure.md#requestinitialvirtualprocessors) s parametrem `doSubscribeCurrentThread` nastaven na hodnotu `true`zvýší úroveň předplatného vlákno hardwaru o jednu. Navíc vracejí `IExecutionResource` rozhraní představující předplatné. Odpovídající volání [iexecutionresource::Remove –](#remove) snižuje úrovni předplatného vlákno hardwaru o jednu.  
  
 V rámci aktivace kořenové virtuálního procesoru pomocí metody [ivirtualprocessorroot::Activate –](ivirtualprocessorroot-structure.md#activate) zvýší úroveň předplatného vlákno hardwaru o jednu. Metody [ivirtualprocessorroot::Deactivate –](ivirtualprocessorroot-structure.md#deactivate), nebo [iexecutionresource::Remove –](#remove) snížení úrovně předplatného jedním při vyvolání na kořenu aktivovaný virtuálních procesorů.  
  
 Správce prostředků používá jako jeden ze způsobů, jak ve kterém k určení, kdy chcete přesunout prostředky mezi plánovače úrovně informace o předplatném.  
  
##  <a name="getexecutionresourceid"></a>  Iexecutionresource::getexecutionresourceid – metoda  
 Vrací jedinečný identifikátor podprocesu hardwaru, který představuje tuto provádění prostředku.  
  
```
virtual unsigned int GetExecutionResourceId() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedinečný identifikátor pro vlákno hardwaru základní tohoto provádění prostředku.  
  
### <a name="remarks"></a>Poznámky  
 Každé vlákno hardwaru je přiřazena službou Concurrency Runtime jedinečný identifikátor. Pokud jsou více provádění prostředky související hardwarové přístup z více vláken, bude mít stejný identifikátor provádění prostředku.  
  
##  <a name="getnodeid"></a>  Iexecutionresource::getnodeid – metoda  
 Vrací jedinečný identifikátor procesoru uzlu, který patří tohoto provádění prostředku.  
  
```
virtual unsigned int GetNodeId() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedinečný identifikátor pro uzel procesoru.  
  
### <a name="remarks"></a>Poznámky  
 Concurrency Runtime představuje vláken hardwaru systému ve skupinách uzlů procesoru. Uzly jsou obvykle odvozená od hardwarovou topologii systému. Všechny procesory na konkrétní soketu nebo konkrétní uzel NUMA se například může patřit do stejného uzlu procesoru. Resource Manager přiřadí tyto uzly počínaje jedinečné identifikátory `0` včetně `nodeCount - 1`, kde `nodeCount` představuje celkový počet uzlů procesoru v systému.  
  
 Počet uzlů můžete získat z funkce [getprocessornodecount –](concurrency-namespace-functions.md).  
  
##  <a name="remove"></a>  Iexecutionresource::Remove – metoda  
 Vrátí tohoto provádění prostředku Resource Manager.  
  
```
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pScheduler`  
 Rozhraní pro Plánovač provedení požadavku na odebrání tohoto provádění prostředku.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody vrátit samostatné spuštění prostředků a také provádění prostředky přidružené k kořeny virtuálních procesorů pro správce prostředků.  
  
 Pokud se jedná o provádění prostředku samostatné jste dostali od některou z metod [ischedulerproxy::subscribecurrentthread –](ischedulerproxy-structure.md#subscribecurrentthread) nebo [ischedulerproxy::requestinitialvirtualprocessors –](ischedulerproxy-structure.md#requestinitialvirtualprocessors), volání Metoda `Remove` se ukončí vlákno odběr, který prostředek se vytvořil na představují. Vyžaduje k ukončení všech odběrů vlákno před ukončením scheduler proxy, přičemž musí volat `Remove` z vlákna vytvořený odběr.  
  
 Kořeny virtuálních procesorů, mohou být vráceny Resource Manager vyvoláním `Remove` metoda, protože rozhraní `IVirtualProcessorRoot` dědí z `IExecutionResource` rozhraní. Budete muset vrátit kořenové virtuálních procesorů, buď v reakci na volání [ischeduler::removevirtualprocessors –](ischeduler-structure.md#removevirtualprocessors) metoda, nebo když jste hotovi s kořenem oversubscribed virtuálních procesorů jste získali z [ Ischedulerproxy::createoversubscriber –](ischedulerproxy-structure.md#createoversubscriber) metoda. Pro kořeny virtuálních procesorů, neexistují žádná omezení ve vlákně, které můžete vyvolat `Remove` metoda.  
  
 `invalid_argument` je vyvolána, pokud parametr `pScheduler` je nastaven na `NULL`.  
  
 `invalid_operation` je vyvolána, pokud parametr `pScheduler` se liší od Plánovač tohoto provádění prostředku byl vytvořený pro, nebo s samostatné provádění prostředku, pokud aktuální vlákno se liší od vlákno vytvořený odběr přístup z více vláken.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)
