---
title: IExecutionContext – struktura
ms.date: 11/04/2016
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
ms.openlocfilehash: 532247ca1776452ad32476d2bcdfafcee3481058
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358792"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext – struktura

Rozhraní pro kontext spuštění, který lze spustit na daném virtuálním procesoru a být kooperativně přepnut kontextu.

## <a name="syntax"></a>Syntaxe

```cpp
struct IExecutionContext;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IExecutionContext::Djeoprava](#dispatch)|Metoda, která je volána při proxy podprocesu spustí provádění konkrétní spuštění kontextu. To by mělo být hlavní pracovní rutiny pro plánovače.|
|[IExecutionContext::GetId](#getid)|Vrátí jedinečný identifikátor pro kontext spuštění.|
|[IExecutionContext::GetProxy](#getproxy)|Vrátí rozhraní proxy vlákna, který je provádění tohoto kontextu.|
|[IExecutionContext::GetScheduler](#getscheduler)|Vrátí rozhraní plánovače, do jehož kontextu tento kontext spuštění patří.|
|[IExecutionContext::SetProxy](#setproxy)|Přidruží proxy vlákna k tomuto kontextu spuštění. Přidružený proxy podproces vyvolá tuto metodu těsně před `Dispatch` spuštěním metody kontextu.|

## <a name="remarks"></a>Poznámky

Pokud implementujete vlastní plánovač, který je propojen se Správcem prostředků modulu Resourcetime souběžnosti, budete muset implementovat `IExecutionContext` rozhraní. Podprocesy vytvořené Správce prostředků provádět práci jménem plánovače `IExecutionContext::Dispatch` provedením metody.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IExecutionContext`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="iexecutioncontextdispatch-method"></a><a name="dispatch"></a>IExecutionContext::Dispatch Metoda

Metoda, která je volána při proxy podprocesu spustí provádění konkrétní spuštění kontextu. To by mělo být hlavní pracovní rutiny pro plánovače.

```cpp
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>Parametry

*pDispatchState*<br/>
Ukazatel na stav, pod kterým je odesílán tento kontext spuštění. Další informace o stavu odeslání naleznete v tématu [DispatchState](dispatchstate-structure.md).

## <a name="iexecutioncontextgetid-method"></a><a name="getid"></a>IExecutionContext::Metoda GetId

Vrátí jedinečný identifikátor pro kontext spuštění.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor celého čísla.

### <a name="remarks"></a>Poznámky

Metodu `GetExecutionContextId` byste měli použít k získání jedinečného identifikátoru pro objekt, který implementuje `IExecutionContext` rozhraní, před použitím rozhraní jako parametru metod poskytovaných Správcem prostředků. Očekává se, že vrátí stejný `GetId` identifikátor při vyvolání funkce.

Identifikátor získaný z jiného zdroje může mít za následek nedefinované chování.

## <a name="iexecutioncontextgetproxy-method"></a><a name="getproxy"></a>IExecutionContext::Metoda GetProxy

Vrátí rozhraní proxy vlákna, který je provádění tohoto kontextu.

```cpp
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní. `IThreadProxy` Pokud proxy vlákna kontextu spuštění nebylinčen `SetProxy`voláním , funkce `NULL`musí vrátit .

### <a name="remarks"></a>Poznámky

Správce prostředků vyvolá `SetProxy` metodu v kontextu spuštění `IThreadProxy` s rozhraním jako parametrem před zadáním `Dispatch` metody v kontextu. Očekává se, že tento argument uložíte `GetProxy()`a vrátíte jej při volání do .

## <a name="iexecutioncontextgetscheduler-method"></a><a name="getscheduler"></a>IExecutionContext::Metoda GetScheduler

Vrátí rozhraní plánovače, do jehož kontextu tento kontext spuštění patří.

```cpp
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní. `IScheduler`

### <a name="remarks"></a>Poznámky

Před použitím jako parametr metody poskytované Správcem prostředků je nutné inicializovat kontext spuštění s platným `IScheduler` rozhraním.

## <a name="iexecutioncontextsetproxy-method"></a><a name="setproxy"></a>IExecutionContext::Metoda SetProxy

Přidruží proxy vlákna k tomuto kontextu spuštění. Přidružený proxy podproces vyvolá tuto metodu těsně před `Dispatch` spuštěním metody kontextu.

```cpp
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>Parametry

*pThreadProxy*<br/>
Rozhraní proxy podprocesu, který se `Dispatch` chystá zadat metodu v tomto kontextu spuštění.

### <a name="remarks"></a>Poznámky

Očekává se, že `pThreadProxy` uložíte parametr a vrátíte jej při volání `GetProxy` metody. Správce prostředků zaručuje, že proxy podprocesu přidružené k kontextu spuštění se `Dispatch` nezmění, zatímco proxy podproces provádí metodu.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)<br/>
[IThreadProxy – struktura](ithreadproxy-structure.md)
