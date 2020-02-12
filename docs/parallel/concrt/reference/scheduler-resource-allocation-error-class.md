---
title: scheduler_resource_allocation_error – třída
ms.date: 11/04/2016
f1_keywords:
- scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::get_error_code
helpviewer_keywords:
- scheduler_resource_allocation_error class
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
ms.openlocfilehash: 2955320b443fb61f26d9f07ca336a45c620e2aa9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143327"
---
# <a name="scheduler_resource_allocation_error-class"></a>scheduler_resource_allocation_error – třída

Tato třída popisuje výjimku vyvolanou v důsledku neúspěšného získání důležitého prostředku v Concurrency Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class scheduler_resource_allocation_error : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[scheduler_resource_allocation_error](#ctor)|Přetíženo. Vytvoří objekt `scheduler_resource_allocation_error`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get_error_code](#get_error_code)|Vrátí kód chyby, který způsobil výjimku.|

## <a name="remarks"></a>Poznámky

Tato výjimka je obvykle vyvolána, když dojde k chybě volání operačního systému z Concurrency Runtime. Kód chyby, který by byl obvykle vrácen z volání metody Win32 `GetLastError`, je převeden na hodnotu typu `HRESULT` a lze jej načíst pomocí metody `get_error_code`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`scheduler_resource_allocation_error`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="get_error_code"></a>get_error_code

Vrátí kód chyby, který způsobil výjimku.

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota `HRESULT` chyby, která způsobila výjimku.

## <a name="ctor"></a>scheduler_resource_allocation_error

Vytvoří objekt `scheduler_resource_allocation_error`.

```cpp
scheduler_resource_allocation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_resource_allocation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

*_Hresult*<br/>
Hodnota `HRESULT` chyby, která způsobila výjimku.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
