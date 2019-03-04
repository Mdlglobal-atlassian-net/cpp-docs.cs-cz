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
ms.openlocfilehash: 9f8f5c5629e9794ca8ee2cc6bedbc4ba6bfdb24d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264934"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource – struktura

Abstrakce pro vlákno hardwaru.

## <a name="syntax"></a>Syntaxe

```
struct IExecutionResource;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Iexecutionresource::currentsubscriptionlevel –](#currentsubscriptionlevel)|Vrátí počet aktivovaných virtuálního procesoru kořeny a odběru externí aktuálně přiřazen k podkladové vlákno hardwaru, kterou představuje tento prostředek spuštění vlákna.|
|[IExecutionResource::GetExecutionResourceId](#getexecutionresourceid)|Vrací jedinečný identifikátor pro vlákno hardwaru, který představuje tento prostředek spuštění.|
|[IExecutionResource::GetNodeId](#getnodeid)|Vrátí jedinečný identifikátor pro uzel procesoru, které patří tento prostředek spuštění.|
|[Iexecutionresource::Remove –](#remove)|Vrátí toto spuštění prostředků Resource Manageru.|

## <a name="remarks"></a>Poznámky

Spuštění prostředků může být samostatný nebo přidružené kořenových adresářů virtuálního procesoru. Samostatný prostředek spuštění se vytvoří při vytvoří odběr vlákno na vlákno v aplikaci. Metody [ISchedulerProxy::SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) a [ischedulerproxy::requestinitialvirtualprocessors –](ischedulerproxy-structure.md#requestinitialvirtualprocessors) vytvářet předplatná vlákna a vrátit `IExecutionResource` rozhraní zastupující předplatné. Vytváří se předplatné vlákna je způsob, jak informovat správce prostředků, který dané vlákno se bude podílet na práci ve frontě do fronty plánovače, spolu s kořenových adresářů virtuálního procesoru, které přiřadí Resource Manageru pro Plánovač. Resource Manager používá informace oversubscribing vláken hardwaru, aby ve kterém můžete.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IExecutionResource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Namespace:** souběžnosti

##  <a name="currentsubscriptionlevel"></a>  Iexecutionresource::currentsubscriptionlevel – metoda

Vrátí počet aktivovaných virtuálního procesoru kořeny a odběru externí aktuálně přiřazen k podkladové vlákno hardwaru, kterou představuje tento prostředek spuštění vlákna.

```
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální úroveň předplatného.

### <a name="remarks"></a>Poznámky

Počet spuštěných vláken jsou přidružené vlákno hardwaru říká úrovně předplatného. To zahrnuje pouze vláken, která je seznámen ve formě předplacenému vláken a kořenových adresářů virtuálního procesoru, které aktivně spouštíte proxy vlákna Resource Manageru.

Volání metody [ischedulerproxy::subscribecurrentthread –](ischedulerproxy-structure.md#subscribecurrentthread), nebo metodu [ischedulerproxy::requestinitialvirtualprocessors –](ischedulerproxy-structure.md#requestinitialvirtualprocessors) s parametrem `doSubscribeCurrentThread` nastaven na hodnotu **true** zvýší o jednu úroveň předplatného vlákno hardwaru. Navíc vracejí `IExecutionResource` rozhraní představující předplatné. Odpovídající volání [iexecutionresource::Remove –](#remove) sníží úroveň předplatného vlákno hardwaru o jednu.

V rámci aktivaci kořenu virtuálního procesoru pomocí metody [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate) zvýší o jednu úroveň předplatného vlákno hardwaru. Metody [ivirtualprocessorroot::Deactivate –](ivirtualprocessorroot-structure.md#deactivate), nebo [iexecutionresource::Remove –](#remove) jednou při vyvolání na kořen virtuálního procesoru aktivované snížení úrovně předplatného.

Resource Manager používá jako jeden ze způsobů, jak ve kterých se mají při přesouvání prostředků mezi plánovači informace na úrovni předplatného.

##  <a name="getexecutionresourceid"></a>  Iexecutionresource::getexecutionresourceid – metoda

Vrací jedinečný identifikátor pro vlákno hardwaru, který představuje tento prostředek spuštění.

```
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor pro vlákno hardwaru základního tento prostředek spuštění.

### <a name="remarks"></a>Poznámky

Každé vlákno hardwaru je přiřazen jedinečný identifikátor modulem Runtime souběžnost. Pokud více zdrojů provádění přiřazeném hardwarovém vlákno, bude mít stejný identifikátor prostředku spuštění.

##  <a name="getnodeid"></a>  Iexecutionresource::getnodeid – metoda

Vrátí jedinečný identifikátor pro uzel procesoru, které patří tento prostředek spuštění.

```
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor pro uzel procesoru.

### <a name="remarks"></a>Poznámky

Modul Concurrency Runtime představuje hardwarových vláken v systému ve skupinách procesoru uzlů. Uzly jsou obvykle odvozena z hardwarovou topologii systému. Všechny procesory na soket zvláštní nebo konkrétní uzel NUMA může například patřit do stejného uzlu procesoru. Resource Manager přiřadí tyto uzly počínaje jedinečné identifikátory `0` včetně `nodeCount - 1`, kde `nodeCount` představuje celkový počet uzlů procesoru v systému.

Počet uzlů, které se získají z funkce [getprocessornodecount –](concurrency-namespace-functions.md).

##  <a name="remove"></a>  Iexecutionresource::Remove – metoda

Vrátí toto spuštění prostředků Resource Manageru.

```
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>Parametry

*pScheduler*<br/>
Rozhraní plánovači, že žádost o odebrání tohoto prostředku spuštění.

### <a name="remarks"></a>Poznámky

Pomocí této metody vrátit samostatné spuštění zdrojů, jakož i provádění prostředky spojené s kořenových adresářů virtuálního procesoru na Resource Manager.

Pokud je to prostředek spuštění samostatného jste dostali od některou z metod [ischedulerproxy::subscribecurrentthread –](ischedulerproxy-structure.md#subscribecurrentthread) nebo [ischedulerproxy::requestinitialvirtualprocessors –](ischedulerproxy-structure.md#requestinitialvirtualprocessors), volání Metoda `Remove` se ukončí vlákno předplatné, prostředek se vytvořil pro reprezentaci. Je potřeba ukončit všechny odběry vlákna před ukončením Plánovač proxy server a musí volat `Remove` z vlákna, která vytvoří odběr.

Kořenových adresářů virtuálního procesoru, mohou být vráceny do Správce prostředků vyvoláním `Remove` metody, protože rozhraní `IVirtualProcessorRoot` dědí z `IExecutionResource` rozhraní. Možná budete muset vrátit odpověď na volání v kořenovém adresáři virtuálního procesoru [ischeduler::removevirtualprocessors –](ischeduler-structure.md#removevirtualprocessors) metodu, nebo až budete hotovi s přetížený kořen virtuálního procesoru jste získali z [ Ischedulerproxy::createoversubscriber –](ischedulerproxy-structure.md#createoversubscriber) metody. Kořenových adresářů virtuálního procesoru, neexistují žádná omezení ve vlákně, které můžete vyvolat `Remove` metody.

`invalid_argument` je vyvolána, pokud parametr `pScheduler` je nastavena na `NULL`.

`invalid_operation` je vyvolána, pokud parametr `pScheduler` se liší od plánovači, že tento prostředek provádění vytvořil pro, nebo pomocí samostatné spuštění zdroje, pokud aktuální vlákno se liší od vlákna, které vlákno předplatné vytvořili.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)
