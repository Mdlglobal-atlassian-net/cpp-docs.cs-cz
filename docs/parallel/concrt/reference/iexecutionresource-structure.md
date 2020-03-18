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
ms.openlocfilehash: 40799d1ed6e21e6932f1adfbad117c436918b792
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417178"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource – struktura

Abstrakce pro hardwarové vlákno.

## <a name="syntax"></a>Syntaxe

```cpp
struct IExecutionResource;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IExecutionResource:: CurrentSubscriptionLevel –](#currentsubscriptionlevel)|Vrátí počet aktivovaných kořenových adresářů virtuálních procesorů a odběr externích vláken aktuálně přidružených k základnímu hardwarovému vláknu, které tento prostředek spuštění představuje.|
|[IExecutionResource:: Getexecutionresourceid –](#getexecutionresourceid)|Vrátí jedinečný identifikátor hardwarového vlákna, které tento prostředek spuštění představuje.|
|[IExecutionResource:: Getnodeid –](#getnodeid)|Vrátí jedinečný identifikátor uzlu procesoru, do kterého patří tento prostředek spuštění.|
|[IExecutionResource:: Remove](#remove)|Vrátí tento prostředek spuštění do Správce prostředků.|

## <a name="remarks"></a>Poznámky

Prostředky spuštění můžou být samostatné nebo přidružené k kořenovým adresářům virtuálních procesorů. Samostatný prostředek spuštění se vytvoří, když vlákno ve vaší aplikaci vytvoří odběr vlákna. Metody [ISchedulerProxy:: SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) a [ISchedulerProxy:: RequestInitialVirtualProcessors –](ischedulerproxy-structure.md#requestinitialvirtualprocessors) vytvořit odběry vlákna a vracet `IExecutionResource` rozhraní představující předplatné. Vytvořením předplatného vlákna je způsob, jak informovat Správce prostředků, že se dané vlákno bude podílet na práci zařazené do fronty plánovače spolu s kořeny virtuálního procesoru Správce prostředků přiřadí plánovači. Správce prostředků používá informace k tomu, abyste se vyhnuli přepočtu neodběrů hardwarových vláken, kde může.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IExecutionResource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="currentsubscriptionlevel"></a>IExecutionResource:: CurrentSubscriptionLevel – – metoda

Vrátí počet aktivovaných kořenových adresářů virtuálních procesorů a odběr externích vláken aktuálně přidružených k základnímu hardwarovému vláknu, které tento prostředek spuštění představuje.

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální úroveň předplatného.

### <a name="remarks"></a>Poznámky

Úroveň předplatného oznamuje, kolik spuštěných vláken je přidruženo k hardwarovému vláknu. To zahrnuje jenom vlákna, o kterých Správce prostředků ví ve formě přihlášených vláken, a kořenových adresářích virtuálních procesorů, které aktivně spouštějí proxy vlákna.

Volání metody [ISchedulerProxy:: SubscribeCurrentThread –](ischedulerproxy-structure.md#subscribecurrentthread)nebo metody [ISchedulerProxy:: RequestInitialVirtualProcessors –](ischedulerproxy-structure.md#requestinitialvirtualprocessors) s parametrem `doSubscribeCurrentThread` nastaveným na hodnotu **true** zvýší úroveň předplatného hardwarového vlákna o jednu. Také vracejí `IExecutionResource` rozhraní představující předplatné. Odpovídající volání metody [IExecutionResource:: Remove](#remove) sníží úroveň předplatného hardwarového vlákna o jednu.

Způsob aktivace kořene virtuálního procesoru pomocí metody [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate) zvyšuje úroveň předplatného hardwarového vlákna o jednu. Metody [IVirtualProcessorRoot::D eactivate](ivirtualprocessorroot-structure.md#deactivate)nebo [IExecutionResource:: Remove](#remove) při vyvolání v aktivovaném kořenovém adresáři virtuálního procesoru sníží úroveň předplatného o jednu.

Správce prostředků používá informace na úrovni předplatného jako jeden ze způsobů, jak určit, kdy se mají přesouvat prostředky mezi plánovači.

## <a name="getexecutionresourceid"></a>IExecutionResource:: Getexecutionresourceid – – metoda

Vrátí jedinečný identifikátor hardwarového vlákna, které tento prostředek spuštění představuje.

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor pro hardwarové vlákno podkladu tohoto prostředku provádění.

### <a name="remarks"></a>Poznámky

Každému hardwarovému vláknu je Concurrency Runtime přiřazen jedinečný identifikátor. Pokud je k dispozici více prostředků spuštění, bude mít každý z nich stejný identifikátor prostředku spuštění.

## <a name="getnodeid"></a>IExecutionResource:: Getnodeid – – metoda

Vrátí jedinečný identifikátor uzlu procesoru, do kterého patří tento prostředek spuštění.

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor uzlu procesoru.

### <a name="remarks"></a>Poznámky

Concurrency Runtime představuje hardwarová vlákna v systému v rámci skupin uzlů procesorů. Uzly jsou obvykle odvozeny od hardwarové topologie systému. Například všechny procesory určitého soketu nebo konkrétního uzlu NUMA mohou patřit do stejného uzlu procesoru. Správce prostředků přiřadí těmto uzlům jedinečné identifikátory počínaje `0` až do `nodeCount - 1`, kde `nodeCount` představuje celkový počet uzlů procesoru v systému.

Počet uzlů lze získat z [GetProcessorNodeCount –](concurrency-namespace-functions.md)funkce.

## <a name="remove"></a>IExecutionResource:: Remove – metoda

Vrátí tento prostředek spuštění do Správce prostředků.

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>Parametry

*pScheduler*<br/>
Rozhraní Scheduleru, které vydává požadavek na odebrání tohoto prostředku spuštění.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li vracet samostatné prostředky pro spuštění i prostředky spuštění přidružené k kořenům virtuálního procesoru Správce prostředků.

Pokud se jedná o samostatný prostředek spuštění, který jste dostali z některé z metod [ISchedulerProxy:: SubscribeCurrentThread –](ischedulerproxy-structure.md#subscribecurrentthread) nebo [ISchedulerProxy:: RequestInitialVirtualProcessors –](ischedulerproxy-structure.md#requestinitialvirtualprocessors), volání metody `Remove` ukončí předplatné vlákna, které se prostředek vytvořil, aby představoval. Před vypínáním proxy serveru Scheduler je nutné ukončit všechna předplatná vlákna a musí volat `Remove` z vlákna, které vytvořilo odběr.

Kořene virtuálního procesoru, je také možné vrátit do Správce prostředků vyvoláním metody `Remove`, protože rozhraní `IVirtualProcessorRoot` dědí z rozhraní `IExecutionResource`. Je možné, že budete muset vrátit kořen virtuálního procesoru buď jako reakci na volání metody [IScheduler:: RemoveVirtualProcessors –](ischeduler-structure.md#removevirtualprocessors) , nebo když jste hotovi s nadplatným kořenem virtuálního procesoru, který jste získali z metody [ISchedulerProxy:: CreateOversubscriber –](ischedulerproxy-structure.md#createoversubscriber) . U kořenových adresářů virtuálních procesorů neexistují žádná omezení, která může vlákno vyvolat metodu `Remove`.

`invalid_argument` je vyvolána, pokud je parametr `pScheduler` nastaven na `NULL`.

`invalid_operation` je vyvolána, pokud se `pScheduler` parametru liší od Scheduleru, pro který byl vytvořen tento prostředek spuštění pro, nebo pomocí samostatného prostředku spuštění, pokud se aktuální vlákno liší od vlákna, které vytvořilo odběr vlákna.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)
