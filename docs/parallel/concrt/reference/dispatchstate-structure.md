---
title: DispatchState – struktura
ms.date: 11/04/2016
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
ms.openlocfilehash: 4c15fc0ba9c78d8b6416cd88480c8ada6e3febf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603560"
---
# <a name="dispatchstate-structure"></a>DispatchState – struktura

`DispatchState` Struktura se používá k přenosu stavu `IExecutionContext::Dispatch` metody. Popisuje okolností, pod kterým `Dispatch` metoda se vyvolá u `IExecutionContext` rozhraní.

## <a name="syntax"></a>Syntaxe

```
struct DispatchState;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Dispatchstate::dispatchstate –](#ctor)|Sestaví nový `DispatchState` objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[Dispatchstate::m_dispatchstatesize –](#m_dispatchstatesize)|Velikost struktury, který se používá pro správu verzí.|
|[DispatchState::m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Určuje, zda má zadaný kontext `Dispatch` metoda vzhledem k tomu, že předchozí kontext asynchronně blokované. To se používá pouze v rámci plánování UMS a je nastaveno na hodnotu `0` u všech ostatních kontextech spuštění.|
|[DispatchState::m_reserved](#m_reserved)|Služba BITS vyhrazené pro budoucí informace o předávání.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`DispatchState`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Namespace:** souběžnosti

##  <a name="ctor"></a>  Dispatchstate::dispatchstate – konstruktor

Sestaví nový `DispatchState` objektu.

```
DispatchState();
```

##  <a name="m_dispatchstatesize"></a>  Dispatchstate::m_dispatchstatesize – datový člen

Velikost struktury, který se používá pro správu verzí.

```
unsigned long m_dispatchStateSize;
```

##  <a name="m_fispreviouscontextasynchronouslyblocked"></a>  Dispatchstate::m_fispreviouscontextasynchronouslyblocked – datový člen

Určuje, zda má zadaný kontext `Dispatch` metoda vzhledem k tomu, že předchozí kontext asynchronně blokované. To se používá pouze v rámci plánování UMS a je nastaveno na hodnotu `0` u všech ostatních kontextech spuštění.

```
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

##  <a name="m_reserved"></a>  Dispatchstate::m_reserved – datový člen

Služba BITS vyhrazené pro budoucí informace o předávání.

```
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
