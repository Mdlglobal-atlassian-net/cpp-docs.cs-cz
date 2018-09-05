---
title: Cnonstatelessworker – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
dev_langs:
- C++
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb3b6411e9ce34ba0196d25c8a63f3f066d78549
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765119"
---
# <a name="cnonstatelessworker-class"></a>Cnonstatelessworker – třída

Přijímá požadavky od fondu vláken a předává je do objektu pracovního procesu, který je vytvořeno a zničeno při každém požadavku.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class Worker>  
class CNonStatelessWorker
```

#### <a name="parameters"></a>Parametry

*Pracovního procesu*  
Třída pracovní vlákno odpovídají [archetyp pracovního procesu](../../atl/reference/worker-archetype.md) vhodný pro zpracování požadavků ve frontě na [cthreadpool –](../../atl/reference/cthreadpool-class.md).

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CNonStatelessWorker::RequestType](#requesttype)|Provádění [WorkerArchetype::RequestType](worker-archetype.md#requesttype).|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CNonStatelessWorker::Execute](#execute)|Provádění [WorkerArchetype::Execute](worker-archetype.md#execute).|
|[CNonStatelessWorker::Initialize](#initialize)|Provádění [WorkerArchetype::Initialize](worker-archetype.md#initialize).|
|[CNonStatelessWorker::Terminate](#terminate)|Provádění [WorkerArchetype::Terminate](worker-archetype.md#terminate).|

## <a name="remarks"></a>Poznámky

Tato třída je jednoduchý pracovní vlákno pro použití s [cthreadpool –](../../atl/reference/cthreadpool-class.md). Tato třída neposkytuje žádné možnosti zpracování požadavků své vlastní. Místo toho vytvoří jedna instance *pracovního procesu* každý požadavek a delegátů implementace metody do této instance.

Výhodou této třídy je, že poskytuje pohodlný způsob, jak změnit model stavu pro existující třídy, vlákna pracovního procesu. `CThreadPool` vytvoří jeden pracovní proces pro životnost vlákna, takže pokud pracovník třída obsahuje stav, se bude obsahovat mezi více požadavků. Jednoduše obalením třídy v `CNonStatelessWorker` šablony před jeho s použitím `CThreadPool`, dobu života pracovního procesu a stav obsahuje, jsou omezená na jednu žádost.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

##  <a name="execute"></a>  CNonStatelessWorker::Execute

Provádění [WorkerArchetype::Execute](worker-archetype.md#execute).  

```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří instanci *pracovního procesu* třídu v zásobníku a volání [inicializovat](worker-archetype.md#initialize) k tomuto objektu. Pokud se inicializace je úspěšný, tato metoda také zavolá [Execute](worker-archetype.md#execute) a [Terminate](worker-archetype.md#terminate) na stejný objekt.  

##  <a name="initialize"></a>  CNonStatelessWorker::Initialize

Provádění [WorkerArchetype::Initialize](worker-archetype.md#initialize).

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Tato třída udělat všechny inicializace `Initialize`.

##  <a name="requesttype"></a>  CNonStatelessWorker::RequestType

Provádění [WorkerArchetype::RequestType](worker-archetype.md#requesttype).

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>Poznámky

Tato třída zpracovává stejný typ pracovní položky jako třída použitá pro *pracovního procesu* parametr šablony. Zobrazit [cnonstatelessworker – přehled](../../atl/reference/cnonstatelessworker-class.md) podrobnosti.

##  <a name="terminate"></a>  CNonStatelessWorker::Terminate

Provádění [WorkerArchetype::Terminate](worker-archetype.md#terminate).

```
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>Poznámky

Tato třída není nutné vyčištění `Terminate`.

## <a name="see-also"></a>Viz také

[Cthreadpool – třída](../../atl/reference/cthreadpool-class.md)   
[Archetyp pracovního procesu](../../atl/reference/worker-archetype.md)   
[Třídy](../../atl/reference/atl-classes.md)
