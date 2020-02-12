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
ms.openlocfilehash: fd044a6255a17882c26183223f71564f98c9f7b2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142774"
---
# <a name="scheduler_ptr-structure"></a>scheduler_ptr Structure

Představuje ukazatel na Plánovač. Tato třída existuje, aby povolovala specifikaci sdílené životnosti pomocí shared_ptr nebo pouze jednoduchého odkazu pomocí nezpracovaného ukazatele.

## <a name="syntax"></a>Syntaxe

```cpp
struct scheduler_ptr;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[scheduler_ptr:: scheduler_ptr](#ctor)|Přetíženo. Vytvoří ukazatel plánovače od shared_ptr k plánovači.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[scheduler_ptr:: Get](#get)|Vrátí nezpracovaný ukazatel do plánovače.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[scheduler_ptr:: operator bool](#operator_bool)|Otestuje, zda je ukazatel plánovače jiný než null|
|[scheduler_ptr:: operator-&gt;](#operator_ptr)|Chová se jako ukazatel.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`scheduler_ptr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** pplinterface. h

**Obor názvů:** souběžnost

## <a name="get"></a>scheduler_ptr:: get – metoda

Vrátí nezpracovaný ukazatel do Scheduleru.

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="operator_bool"></a>scheduler_ptr:: operator bool

Testuje, zda je ukazatel Scheduleru jiný než nulový.

```cpp
operator bool() const;
```

## <a name="operator_ptr"></a>scheduler_ptr:: operator-&gt;

Chová se jako ukazatel.

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="ctor"></a>scheduler_ptr:: scheduler_ptr – konstruktor

Vytvoří ukazatel plánovače od shared_ptr k plánovači.

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Parametry

*Plánovač*<br/>
Plánovač, který se má převést.

*pScheduler*<br/>
Ukazatel plánovače, který se má převést

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
