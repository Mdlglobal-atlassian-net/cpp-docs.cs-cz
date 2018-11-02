---
title: scheduler_ptr Structure
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 7fd81a1ccf6702c74a013c5772d59f01121b61a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479219"
---
# <a name="schedulerptr-structure"></a>scheduler_ptr Structure

Představuje ukazatel na Plánovač. Tato třída existuje pro povolení specifikace sdílené životnosti pomocí shared_ptr nebo jen prostým odkazem pomocí nezpracovaného ukazatele.

## <a name="syntax"></a>Syntaxe

```
struct scheduler_ptr;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[scheduler_ptr::scheduler_ptr](#ctor)|Přetíženo. Vytvoří ukazatel plánovače z shared_ptr do plánovače|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[scheduler_ptr::get](#get)|Vrátí ukazatel raw pro Plánovač|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[scheduler_ptr::Operator bool](#operator_bool)|Otestujte, zda ukazatel plánovače nemá hodnotu null|
|[scheduler_ptr::operator-&gt;](#operator_ptr)|Chovají se jako ukazatel|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`scheduler_ptr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** pplinterface.h

**Namespace:** souběžnosti

##  <a name="get"></a>  scheduler_ptr::Get – metoda

Vrátí ukazatel raw pro Plánovač

```
scheduler_interface* get() const;
```

### <a name="return-value"></a>Návratová hodnota

##  <a name="operator_bool"></a>  scheduler_ptr::Operator bool

Otestujte, zda ukazatel plánovače nemá hodnotu null

'''operator bool() const;
```

##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;

Behave like a pointer

```
scheduler_interface – * – operátor -> const;)
```

### Return Value

##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr Constructor

Creates a scheduler pointer from shared_ptr to scheduler

```
scheduler_ptr – explicitní (std::shared_ptr < scheduler_interface – > Plánovač);

scheduler_ptr – explicitní (_In_opt_ pScheduler scheduler_interface – *);
```

### Parameters

*scheduler*<br/>
The scheduler to convert.

*pScheduler*<br/>
The scheduler pointer to convert.

## See Also

[concurrency Namespace](concurrency-namespace.md)
