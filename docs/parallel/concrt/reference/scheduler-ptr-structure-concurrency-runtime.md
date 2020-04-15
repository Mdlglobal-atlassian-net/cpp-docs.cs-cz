---
title: scheduler_ptr struktura
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 60d71a26e5dffcadfb900ef15c26a6d9dc6d6f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358771"
---
# <a name="scheduler_ptr-structure"></a>scheduler_ptr struktura

Představuje ukazatel plánovače. Tato třída existuje, aby umožnila specifikaci sdílené životnosti pomocí shared_ptr nebo pouze prostý odkaz pomocí nezpracovaného ukazatele.

## <a name="syntax"></a>Syntaxe

```cpp
struct scheduler_ptr;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[scheduler_ptr::scheduler_ptr](#ctor)|Přetíženo. Vytvoří ukazatel plánovače z shared_ptr na plánovače.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[scheduler_ptr::získat](#get)|Vrátí nezpracovaný ukazatel na plánovač.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[scheduler_ptr::operátor bool](#operator_bool)|Otestujte, zda ukazatel plánovače není null|
|[scheduler_ptr::operátor-&gt;](#operator_ptr)|Chovat se jako ukazatel|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`scheduler_ptr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** pplinterface.h

**Obor názvů:** souběžnost

## <a name="scheduler_ptrget-method"></a><a name="get"></a>scheduler_ptr::get Metoda

Vrátí nezpracovaný ukazatel plánovače.

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="scheduler_ptroperator-bool"></a><a name="operator_bool"></a>scheduler_ptr::operátor bool

Testuje, zda ukazatel plánovače není null.

```cpp
operator bool() const;
```

## <a name="scheduler_ptroperator-gt"></a><a name="operator_ptr"></a>scheduler_ptr::operátor-&gt;

Chová se jako ukazatel.

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="scheduler_ptrscheduler_ptr-constructor"></a><a name="ctor"></a>scheduler_ptr::scheduler_ptr konstruktor

Vytvoří ukazatel plánovače z shared_ptr plánovače.

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Parametry

*Plánovač*<br/>
Plánovač převést.

*pScheduler*<br/>
Ukazatel plánovače převést.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)
