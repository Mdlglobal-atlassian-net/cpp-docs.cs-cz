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
ms.openlocfilehash: 69e00893373ccca6e2ed676fbb7f5a109c49efdf
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143046"
---
# <a name="dispatchstate-structure"></a>DispatchState – struktura

Struktura `DispatchState` slouží k přenosu stavu do metody `IExecutionContext::Dispatch`. Popisuje okolnosti, za kterých je metoda `Dispatch` vyvolána v rozhraní `IExecutionContext`.

## <a name="syntax"></a>Syntaxe

```cpp
struct DispatchState;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[DispatchState::D ispatchState](#ctor)|Vytvoří nový objekt `DispatchState`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[DispatchState:: m_dispatchStateSize](#m_dispatchstatesize)|Velikost této struktury, která se používá pro správu verzí.|
|[DispatchState:: m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Určuje, zda tento kontext zadal metodu `Dispatch`, protože předchozí kontext byl asynchronně zablokován. Tato hodnota se používá pouze v kontextu plánování UMS a je nastavena na hodnotu `0` pro všechny ostatní kontexty spuštění.|
|[DispatchState:: m_reserved](#m_reserved)|Služba BITS vyhrazena pro předávání budoucích informací.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`DispatchState`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>DispatchState::D ispatchState – konstruktor

Vytvoří nový objekt `DispatchState`.

```cpp
DispatchState();
```

## <a name="m_dispatchstatesize"></a>Datový člen DispatchState:: m_dispatchStateSize

Velikost této struktury, která se používá pro správu verzí.

```cpp
unsigned long m_dispatchStateSize;
```

## <a name="m_fispreviouscontextasynchronouslyblocked"></a>Datový člen DispatchState:: m_fIsPreviousContextAsynchronouslyBlocked

Určuje, zda tento kontext zadal metodu `Dispatch`, protože předchozí kontext byl asynchronně zablokován. Tato hodnota se používá pouze v kontextu plánování UMS a je nastavena na hodnotu `0` pro všechny ostatní kontexty spuštění.

```cpp
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

## <a name="m_reserved"></a>Datový člen DispatchState:: m_reserved

Služba BITS vyhrazena pro předávání budoucích informací.

```cpp
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
