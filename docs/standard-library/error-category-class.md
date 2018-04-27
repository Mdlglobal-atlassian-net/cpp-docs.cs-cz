---
title: error_category – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- system_error/std::error_category
- system_error/std::error_category::value_type
- system_error/std::error_category::default_error_condition
- system_error/std::error_category::equivalent
- system_error/std::error_category::message
- system_error/std::error_category::name
dev_langs:
- C++
helpviewer_keywords:
- std::error_category
- std::error_category::value_type
- std::error_category::default_error_condition
- std::error_category::equivalent
- std::error_category::message
- std::error_category::name
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 21e17cb951273cf1a920867154a503f02f4cd760
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="errorcategory-class"></a>error_category – třída

Představuje abstraktní, běžné základ pro objekty, která popisuje kategorie kódy chyb.

## <a name="syntax"></a>Syntaxe

```cpp
class error_category;
```

## <a name="remarks"></a>Poznámky

Dva předdefinované objekty implementovat `error_category`: [generic_category](../standard-library/system-error-functions.md#generic_category) a [system_category](../standard-library/system-error-functions.md#system_category).

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[value_type](#value_type)|Typ, který představuje hodnotu kódu uložené chyby.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[default_error_condition](#default_error_condition)|Ukládá hodnotu kódu chyby pro objekt podmínku chyby.|
|[Ekvivalentní](#equivalent)|Vrátí hodnotu, která určuje, zda jsou ekvivalentní objekty chyby.|
|[message](#message)|Vrací název zadané chybový kód.|
|[Jméno](#name)|Vrací název kategorie.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator==](#op_eq_eq)|Testování rovnosti mezi `error_category` objekty.|
|[operator!=](#op_neq)|Testy nerovnost mezi `error_category` objekty.|
|[operátor <](#op_lt)|Testuje, pokud [error_category](../standard-library/error-category-class.md) objekt je menší než `error_category` objekt předaná pro porovnání.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<system_error – >

**Namespace:** – std

## <a name="default_error_condition"></a>  error_category::default_error_condition

Ukládá hodnotu kódu chyby pro objekt podmínku chyby.

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`_Errval`|Hodnotu kód chyby pro ukládání [error_condition](../standard-library/error-condition-class.md).|

### <a name="return-value"></a>Návratová hodnota

Vrátí `error_condition(_Errval, *this)`.

### <a name="remarks"></a>Poznámky

## <a name="equivalent"></a>  error_category::Equivalent

Vrátí hodnotu, která určuje, zda jsou ekvivalentní objekty chyby.

```cpp
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`_Errval`|Kód chyby se hodnoty k porovnání.|
|`_Cond`|[Error_condition](../standard-library/error-condition-class.md) objekt k porovnání.|
|`_Code`|[Error_code](../standard-library/error-code-class.md) objekt k porovnání.|

### <a name="return-value"></a>Návratová hodnota

`true` Pokud jsou kategorie a hodnota rovna; v opačném `false`.

### <a name="remarks"></a>Poznámky

Vrátí první členská funkce `*this == _Cond.category() && _Cond.value() == _Errval`.

Vrátí druhou členská funkce `*this == _Code.category() && _Code.value() == _Errval`.

## <a name="message"></a>  error_category::Message

Vrací název zadané chybový kód.

```cpp
virtual string message(error_code::value_type val) const = 0;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`val`|Hodnota kódu chyby k popisu.|

### <a name="return-value"></a>Návratová hodnota

Vrátí popisný název kódu chyby `val` pro kategorii.

### <a name="remarks"></a>Poznámky

## <a name="name"></a>  error_category::Name

Vrací název kategorie.

```cpp
virtual const char *name() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Vrací název kategorie jako řetězec bajtů ukončené hodnotou null.

### <a name="remarks"></a>Poznámky

## <a name="op_eq_eq"></a>  error_category::Operator ==

Testování rovnosti mezi `error_category` objekty.

```cpp
bool operator==(const error_category& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`right`|Objekt, který má být testována rovnosti.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud objekty jsou stejné; **false** Pokud objekty nejsou stejné.

### <a name="remarks"></a>Poznámky

Tento člen operátor vrátí `this == &right`.

## <a name="op_neq"></a>  error_category::Operator! =

Testy nerovnost mezi `error_category` objekty.

```cpp
bool operator!=(const error_category& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`right`|Objekt, který má být testována nerovnost.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud `error_category` objekt není rovno `error_category` objekt předaný v `right`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Vrací člena operátor `(!*this == right)`.

## <a name="op_lt"></a>  error_category::Operator&lt;

Testuje, pokud [error_category](../standard-library/error-category-class.md) objekt je menší než `error_category` objekt předaná pro porovnání.

```cpp
bool operator<(const error_category& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`right`|`error_category` Objekt, který má být porovnána.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud `error_category` objekt je menší než `error_category` objekt předaná pro porovnání; V opačném **false**.

### <a name="remarks"></a>Poznámky

Vrací člena operátor `this < &right`.

## <a name="value_type"></a>  error_category::value_type

Typ, který představuje hodnotu kódu uložené chyby.

```cpp
typedef int value_type;
```

### <a name="remarks"></a>Poznámky

Definici tohoto typu se jedná o synonymum `int`.

## <a name="see-also"></a>Viz také

[<system_error>](../standard-library/system-error.md)<br/>
