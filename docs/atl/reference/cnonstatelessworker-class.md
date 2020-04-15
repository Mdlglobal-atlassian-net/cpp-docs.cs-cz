---
title: Třída CNonStatelessWorker
ms.date: 11/04/2016
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
ms.openlocfilehash: f3604f95c8217c7407c100671265140bbadbab78
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326735"
---
# <a name="cnonstatelessworker-class"></a>Třída CNonStatelessWorker

Přijímá požadavky z fondu vláken a předává je pracovnímu objektu, který je vytvořen a zničen při každém požadavku.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>Parametry

*Pracovník*<br/>
Třída pracovního vlákna odpovídající [archetypu pracovního procesu](../../atl/reference/worker-archetype.md) vhodnépro zpracování požadavků zařazených do fronty v [cthreadpoolu](../../atl/reference/cthreadpool-class.md).

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CNonStatelessWorker::RequestType](#requesttype)|Implementace [typu WorkerArchetype::RequestType](worker-archetype.md#requesttype).|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CNonStatelessWorker::Spustit](#execute)|Implementace [Typu WorkerArchetype::Execute](worker-archetype.md#execute).|
|[CNonStatelessWorker::Inicializovat](#initialize)|Implementace [typu WorkerArchetype::Initialize](worker-archetype.md#initialize).|
|[CNonStatelessWorker::Ukončit](#terminate)|Implementace [typu WorkerArchetype::Terminate](worker-archetype.md#terminate).|

## <a name="remarks"></a>Poznámky

Tato třída je jednoduché pracovní vlákno pro použití s [CThreadPool](../../atl/reference/cthreadpool-class.md). Tato třída neposkytuje žádné vlastní možnosti zpracování požadavků. Místo toho instanci jedné instance *Worker* na požadavek a deleguje implementaci jeho metod na tuto instanci.

Výhodou této třídy je, že poskytuje pohodlný způsob, jak změnit model stavu pro existující třídy pracovních vláken. `CThreadPool`vytvoří jednoho pracovníka po dobu životnosti vlákna, takže pokud třída pracovníka obsahuje stav, bude jej držet ve více požadavcích. Jednoduchým zabalením `CNonStatelessWorker` této třídy `CThreadPool`v šabloně před jejím použitím s , životnost pracovníka a stav, který drží je omezena na jeden požadavek.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="cnonstatelessworkerexecute"></a><a name="execute"></a>CNonStatelessWorker::Spustit

Implementace [Typu WorkerArchetype::Execute](worker-archetype.md#execute).

```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří instanci třídy *Worker* v zásobníku a volá [Initialize](worker-archetype.md#initialize) na tento objekt. Pokud je inicializace úspěšná, tato metoda také volá [Execute](worker-archetype.md#execute) a [Terminate](worker-archetype.md#terminate) na stejném objektu.

## <a name="cnonstatelessworkerinitialize"></a><a name="initialize"></a>CNonStatelessWorker::Inicializovat

Implementace [typu WorkerArchetype::Initialize](worker-archetype.md#initialize).

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Tato třída neprovádí žádnou `Initialize`inicializaci v .

## <a name="cnonstatelessworkerrequesttype"></a><a name="requesttype"></a>CNonStatelessWorker::RequestType

Implementace [typu WorkerArchetype::RequestType](worker-archetype.md#requesttype).

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>Poznámky

Tato třída zpracovává stejný typ pracovní položky jako třída použitá pro parametr šablony *pracovníka.* Podrobnosti najdete v [tématu CNonStatelessWorker Overview.](../../atl/reference/cnonstatelessworker-class.md)

## <a name="cnonstatelessworkerterminate"></a><a name="terminate"></a>CNonStatelessWorker::Ukončit

Implementace [typu WorkerArchetype::Terminate](worker-archetype.md#terminate).

```
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>Poznámky

Tato třída neprovádí žádné `Terminate`vyčištění v .

## <a name="see-also"></a>Viz také

[Třída CThreadPool](../../atl/reference/cthreadpool-class.md)<br/>
[Archetyp pracovníka](../../atl/reference/worker-archetype.md)<br/>
[Třídy](../../atl/reference/atl-classes.md)
