---
title: IExecutionResource – struktura
ms.date: 11/04/2016
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
helpviewer_keywords:
- IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
ms.openlocfilehash: 4305948aa4e5da36023c1d4fe8b0b84aa4d59e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377321"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource – struktura

Abstrakce pro hardwarové vlákno.

## <a name="syntax"></a>Syntaxe

```cpp
struct IExecutionResource;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IExecutionResource::CurrentSubscriptionLevel](#currentsubscriptionlevel)|Vrátí počet kořenů aktivovaného virtuálního procesoru a odebíraných externích vláken, které jsou aktuálně přidruženy k podkladovému hardwarovému vláknu, které tento prostředek spuštění představuje.|
|[IExecutionResource::GetExecutionResourceId](#getexecutionresourceid)|Vrátí jedinečný identifikátor pro hardwarové vlákno, které představuje tento prostředek spuštění.|
|[IExecutionResource::GetNodeId](#getnodeid)|Vrátí jedinečný identifikátor pro uzel procesoru, ke kterému tento prostředek spuštění patří.|
|[IExecutionResource::Odebrat](#remove)|Vrátí tento prostředek spuštění správce prostředků.|

## <a name="remarks"></a>Poznámky

Prostředky spuštění mohou být samostatné nebo přidružené ke kořenům virtuálního procesoru. Prostředek samostatné spuštění je vytvořen při vlákno ve vaší aplikaci vytvoří odběr vlákna. Metody [ISchedulerProxy::SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) a [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) vytvářejí odběry `IExecutionResource` vláken a vracejí rozhraní představující odběr. Vytvoření odběru vlákna je způsob, jak informovat Správce prostředků, že dané vlákno se bude podílet na práci zařazené do fronty plánovače, spolu s kořeny virtuálního procesoru Resource Manager přiřadí plánovači. Správce prostředků používá informace, aby se zabránilo oversubscribing hardwarových vláken, kde je to možné.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IExecutionResource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="iexecutionresourcecurrentsubscriptionlevel-method"></a><a name="currentsubscriptionlevel"></a>IExecutionResource::CurrentSubscriptionLevel Metoda

Vrátí počet kořenů aktivovaného virtuálního procesoru a odebíraných externích vláken, které jsou aktuálně přidruženy k podkladovému hardwarovému vláknu, které tento prostředek spuštění představuje.

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální úroveň předplatného.

### <a name="remarks"></a>Poznámky

Úroveň předplatného vám řekne, kolik spuštěných podprocesů je přidruženo k hardwarovému vláknu. To zahrnuje pouze podprocesy Resource Manager je vědoma ve formě odebíraných vláken a kořeny virtuálníprocesor, které jsou aktivně provádění proxy podprocesů.

Volání metody [ISchedulerProxy::SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread)nebo metody [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) `doSubscribeCurrentThread` s parametrem nastaveným na hodnotu **true** otáčí úroveň předplatného hardwarového vlákna o jednu. Také vrátí `IExecutionResource` rozhraní představující předplatné. Odpovídající volání [IExecutionResource::Remove](#remove) sníží úroveň předplatného hardwarového vlákna o jednu.

Aktivace kořenového adresáře virtuálního procesoru pomocí metody [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate) zintáží úroveň předplatného hardwarového vlákna o jednu. Metody [IVirtualProcessorRoot::Deactivate](ivirtualprocessorroot-structure.md#deactivate)nebo [IExecutionResource::Remove](#remove) derement úroveň předplatného o jednu při vyvolání v kořenovém adresáři aktivovaného virtuálního procesoru.

Správce prostředků používá informace o úrovni předplatného jako jeden ze způsobů, jak určit, kdy přesunout prostředky mezi plánovači.

## <a name="iexecutionresourcegetexecutionresourceid-method"></a><a name="getexecutionresourceid"></a>IExecutionResource::Metoda GetExecutionResourceId

Vrátí jedinečný identifikátor pro hardwarové vlákno, které představuje tento prostředek spuštění.

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor hardwarového vlákna, na němž je tento prostředek spuštění založen.

### <a name="remarks"></a>Poznámky

Každému podprocesu hardwaru je přiřazen jedinečný identifikátor modulu Souběžnost Runtime. Pokud více prostředků spuštění jsou přidruženy podproces hardwaru, budou mít všechny stejný identifikátor prostředku spuštění.

## <a name="iexecutionresourcegetnodeid-method"></a><a name="getnodeid"></a>IExecutionResource::Metoda GetNodeId

Vrátí jedinečný identifikátor pro uzel procesoru, ke kterému tento prostředek spuštění patří.

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor uzlu procesoru.

### <a name="remarks"></a>Poznámky

Modul Souběžnost Runtime představuje hardwarová vlákna v systému ve skupinách uzlů procesoru. Uzly jsou obvykle odvozeny z hardwarové topologie systému. Například všechny procesory na určitém soketu nebo konkrétní uzel NUMA může patřit do stejného uzlu procesoru. Správce prostředků přiřazuje těmto uzlům jedinečné identifikátory počínaje `0` až do a včetně `nodeCount - 1`, kde `nodeCount` představuje celkový počet uzlů procesoru v systému.

Počet uzlů lze získat z funkce [GetProcessorNodeCount](concurrency-namespace-functions.md).

## <a name="iexecutionresourceremove-method"></a><a name="remove"></a>IExecutionResource::Odebrat metodu

Vrátí tento prostředek spuštění správce prostředků.

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>Parametry

*pScheduler*<br/>
Rozhraní plánovače, který provádí požadavek na odebrání tohoto prostředku spuštění.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete vrátit samostatné prostředky spuštění a také prostředky spuštění přidružené ke kořenům virtuálního procesoru správci prostředků.

Pokud se jedná o samostatný prostředek spuštění, který jste obdrželi z některé z metod [ISchedulerProxy::SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread) `Remove` nebo [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors), volání metody ukončí odběr vlákna, který byl vytvořen k reprezentaci. Před vypnutím proxy plánovače je nutné ukončit všechna odběry `Remove` vláken a musí být volána z vlákna, které předplatné vytvořilo.

Kořeny virtuálního procesoru mohou být také vráceny správci prostředků vyvoláním `Remove` metody, protože rozhraní `IVirtualProcessorRoot` dědí z `IExecutionResource` rozhraní. Možná budete muset vrátit kořen virtuálního procesoru buď v reakci na volání [metody IScheduler::RemoveVirtualProcessors,](ischeduler-structure.md#removevirtualprocessors) nebo když jste hotovi s přepsaným kořenem virtuálního procesoru, který jste získali z metody [ISchedulerProxy::CreateOversubscriber.](ischedulerproxy-structure.md#createoversubscriber) Pro kořeny virtuálního procesoru neexistují žádná `Remove` omezení, na kterém vlákno může vyvolat metodu.

`invalid_argument`je vyvolána, `pScheduler` pokud je `NULL`parametr nastaven na .

`invalid_operation`je vyvolána, `pScheduler` pokud parametr se liší od plánovače, který byl vytvořen pro tento prostředek spuštění, nebo se samostatným zdrojem spuštění, pokud se aktuální vlákno liší od vlákna, které vytvořilo odběr vlákna.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)
