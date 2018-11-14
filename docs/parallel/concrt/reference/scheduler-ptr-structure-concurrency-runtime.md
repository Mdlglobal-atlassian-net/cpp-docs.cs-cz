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
ms.openlocfilehash: 0da45fa18d12b3f1c93df6b8c8736ed1bfb58ade
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524992"
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

Vrátí ukazatel raw pro Plánovač.

```
scheduler_interface* get() const;
```

### <a name="return-value"></a>Návratová hodnota

##  <a name="operator_bool"></a>  scheduler_ptr::Operator bool

Ověřuje, zda ukazatel plánovače nemá hodnotu null.

```
operator bool() const;
```

##  <a name="operator_ptr"></a>  scheduler_ptr::Operator –&gt;

Se chová jako ukazatel.

```
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr – konstruktor

Vytvoří ukazatel plánovače z shared_ptr do plánovače.

```
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Parametry

*scheduler*<br/>
Plánovač pro převod.

*pScheduler*<br/>
Ukazatel plánovače pro převod.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
