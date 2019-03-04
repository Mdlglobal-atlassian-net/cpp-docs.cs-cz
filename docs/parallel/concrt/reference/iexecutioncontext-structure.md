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
ms.openlocfilehash: 8c49df5a8c7f214b574b4f6118d182b63fec5dca
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264960"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext – struktura

Rozhraní pro provádění kontext, který můžete spustit na danou virtuální procesor a být spolupráce při přepnutí kontextu.

## <a name="syntax"></a>Syntaxe

```
struct IExecutionContext;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IExecutionContext::Dispatch](#dispatch)|Metoda, která je volána, když proxy vlákna začne provádět kontextu konkrétního spuštění. Je třeba rutina hlavní pracovního procesu pro váš plánovač.|
|[IExecutionContext::GetId](#getid)|Vrací jedinečný identifikátor pro kontext spuštění.|
|[IExecutionContext::GetProxy](#getproxy)|Vrátí rozhraní proxy vlákna, který spouští tento kontext.|
|[IExecutionContext::GetScheduler](#getscheduler)|Vrátí rozhraní plánovači patří tento kontext spuštění.|
|[IExecutionContext::SetProxy](#setproxy)|Přidruží vlákno proxy s tímto kontextem za spuštění. Proxy přidružené vlákno vyvolá tato metoda práva dříve, než začne provádění objektu context `Dispatch` metody.|

## <a name="remarks"></a>Poznámky

Pokud implementujete vlastní plánovač, které sdílí rozhraní se správcem prostředků modulu Runtime souběžnosti, budete muset implementovat `IExecutionContext` rozhraní. Vlákna vytvořená pomocí Resource Manageru provádět práci jménem váš Plánovač spuštěním `IExecutionContext::Dispatch` metody.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IExecutionContext`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Namespace:** souběžnosti

##  <a name="dispatch"></a>  Iexecutioncontext::Dispatch – metoda

Metoda, která je volána, když proxy vlákna začne provádět kontextu konkrétního spuštění. Je třeba rutina hlavní pracovního procesu pro váš plánovač.

```
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>Parametry

*pDispatchState*<br/>
Ukazatel na stav, pod kterým je odesílán tento kontext spuštění. Další informace týkající se stavu odeslání najdete v tématu [dispatchstate –](dispatchstate-structure.md).

##  <a name="getid"></a>  Iexecutioncontext::getid – metoda

Vrací jedinečný identifikátor pro kontext spuštění.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Celé číslo jedinečný identifikátor.

### <a name="remarks"></a>Poznámky

Používáte metodu `GetExecutionContextId` získat jedinečný identifikátor pro objekt, který implementuje `IExecutionContext` rozhraní, než použijete rozhraní jako parametr metodám zadaný správcem prostředků. Očekává se vrátit stejný identifikátor při `GetId` vyvolání funkce.

Identifikátor získané z jiného zdroje může způsobit nedefinované chování.

##  <a name="getproxy"></a>  Iexecutioncontext::getproxy – metoda

Vrátí rozhraní proxy vlákna, který spouští tento kontext.

```
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>Návratová hodnota

`IThreadProxy` Rozhraní. Pokud proxy vlákna kontextu spuštění nebyla inicializována pomocí volání `SetProxy`, funkce musí vracet `NULL`.

### <a name="remarks"></a>Poznámky

Vyvolá Resource Manageru `SetProxy` metodu na kontextu spuštění, s `IThreadProxy` rozhraní jako parametr, před vstupem `Dispatch` metodu na pro daný kontext. Očekává se uložit tento argument a vrátí na volání `GetProxy()`.

##  <a name="getscheduler"></a>  Iexecutioncontext::getscheduler – metoda

Vrátí rozhraní plánovači patří tento kontext spuštění.

```
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>Návratová hodnota

`IScheduler` Rozhraní.

### <a name="remarks"></a>Poznámky

Je potřeba inicializovat kontext spuštění s platným `IScheduler` rozhraní před jejich použitím jako parametr metodám zadaný správcem prostředků.

##  <a name="setproxy"></a>  Iexecutioncontext::setproxy – metoda

Přidruží vlákno proxy s tímto kontextem za spuštění. Proxy přidružené vlákno vyvolá tato metoda práva dříve, než začne provádění objektu context `Dispatch` metody.

```
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>Parametry

*pThreadProxy*<br/>
Rozhraní pro proxy vlákna, která je zaujmout `Dispatch` metoda v tomto kontextu spuštění.

### <a name="remarks"></a>Poznámky

Předpokládá, že uložit parametr `pThreadProxy` a vraťte se na volání `GetProxy` metody. Správce prostředků zaručuje, že vlákno proxy spojené s kontextem spuštění nezmění při provádění proxy vlákna `Dispatch` metody.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)<br/>
[IThreadProxy – struktura](ithreadproxy-structure.md)
