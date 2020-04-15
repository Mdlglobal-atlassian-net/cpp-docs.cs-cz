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
ms.openlocfilehash: 2c4103f89f7fc74c5368bafac3c82685ff9b6e03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372701"
---
# <a name="dispatchstate-structure"></a>DispatchState – struktura

Struktura `DispatchState` se používá k přenosu `IExecutionContext::Dispatch` stavu metody. Popisuje okolnosti, za kterých je `Dispatch` metoda `IExecutionContext` vyvolána v rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
struct DispatchState;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[DispatchState::DispatchState](#ctor)|Vytvoří nový `DispatchState` objekt.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[DispatchState::m_dispatchStateSize](#m_dispatchstatesize)|Velikost této struktury, která se používá pro správu verzí.|
|[DispatchState::m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Určuje, zda tento `Dispatch` kontext zadal metodu, protože předchozí kontext asynchronně blokován. Používá se pouze v kontextu plánování služby UMS `0` a je nastaven na hodnotu pro všechny ostatní kontexty provádění.|
|[DispatchState::m_reserved](#m_reserved)|Bity vyhrazené pro předávání budoucích informací.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`DispatchState`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="dispatchstatedispatchstate-constructor"></a><a name="ctor"></a>DispatchState:konstruktor :DispatchState

Vytvoří nový `DispatchState` objekt.

```cpp
DispatchState();
```

## <a name="dispatchstatem_dispatchstatesize-data-member"></a><a name="m_dispatchstatesize"></a>DispatchState::m_dispatchStateSize datový člen

Velikost této struktury, která se používá pro správu verzí.

```cpp
unsigned long m_dispatchStateSize;
```

## <a name="dispatchstatem_fispreviouscontextasynchronouslyblocked-data-member"></a><a name="m_fispreviouscontextasynchronouslyblocked"></a>DispatchState::m_fIsPreviousContextAsynchronouslyBlocked datový člen

Určuje, zda tento `Dispatch` kontext zadal metodu, protože předchozí kontext asynchronně blokován. Používá se pouze v kontextu plánování služby UMS `0` a je nastaven na hodnotu pro všechny ostatní kontexty provádění.

```cpp
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

## <a name="dispatchstatem_reserved-data-member"></a><a name="m_reserved"></a>DispatchState::m_reserved datový člen

Bity vyhrazené pro předávání budoucích informací.

```cpp
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)
