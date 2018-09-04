---
title: error_condition – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- system_error/std::error_condition
- system_error/std::error_condition::value_type
- system_error/std::error_condition::assign
- system_error/std::error_condition::category
- system_error/std::error_condition::clear
- system_error/std::error_condition::message
- system_error/std::error_condition::operator bool
dev_langs:
- C++
helpviewer_keywords:
- std::error_condition
- std::error_condition::value_type
- std::error_condition::assign
- std::error_condition::category
- std::error_condition::clear
- std::error_condition::message
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66096fcfee62e869577527b632f3409fea231b35
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690828"
---
# <a name="errorcondition-class"></a>error_condition – třída

Představuje uživatelem definované chybové kódy.

## <a name="syntax"></a>Syntaxe

```cpp
class error_condition;
```

## <a name="remarks"></a>Poznámky

Objekt typu `error_condition` ukládá chybovou hodnotu kód a ukazatele na objekt, který představuje [kategorie](../standard-library/error-category-class.md) z chybové kódy používané pro hlášené chyby definovaný uživatelem.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[error_condition](#error_condition)|Vytvoří objekt typu `error_condition`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[value_type](#value_type)|Typ představující uložený chybová hodnota kódu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[přiřazení](#assign)|Hodnota kódu chyby a kategorie služby přiřadí chybovou podmínku.|
|[Kategorie](#category)|Vrací kategorie chyby.|
|[Vymazat](#clear)|Vymaže hodnota kódu chyby a kategorie.|
|[message](#message)|Vrátí název kód chyby.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator==](#op_eq_eq)|Ověřuje rovnost mezi `error_condition` objekty.|
|[operator!=](#op_neq)|Testy pro nerovnost mezi `error_condition` objekty.|
|[Operator <](#op_lt)|Testuje, zda `error_condition` objekt je menší než `error_code` objekt předaný k porovnání.|
|[operátor =](#op_eq)|Přiřadí novou hodnotu výčtu `error_condition` objektu.|
|[bool – operátor](#op_bool)|Přetypování proměnné typu `error_condition`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<system_error >

**Namespace:** std

## <a name="assign"></a>  error_condition::Assign

Hodnota kódu chyby a kategorie služby přiřadí chybovou podmínku.

```cpp
void assign(value_type val, const error_category& _Cat);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Val*|Hodnota kódu chyby k ukládání `error_code`.|
|*_Cat*|Kategorie chyby pro uložení v `error_code`.|

### <a name="remarks"></a>Poznámky

Členské funkce úložiště *val* jako hodnota kódu chyby a ukazatel na *_Cat*.

## <a name="category"></a>  error_condition::category

Vrací kategorie chyby.

```cpp
const error_category& category() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na kategorie uložené chyby

### <a name="remarks"></a>Poznámky

## <a name="clear"></a>  error_condition::clear

Vymaže hodnota kódu chyby a kategorie.

```cpp
clear();
```

### <a name="remarks"></a>Poznámky

Členská funkce ukládá nulová hodnota kódu chyby a ukazatel [generic_category](../standard-library/system-error-functions.md#generic_category) objektu.

## <a name="error_condition"></a>  error_condition::error_condition

Vytvoří objekt typu `error_condition`.

```cpp
error_condition();

error_condition(value_type val, const error_category& _Cat);

template <class _Enum>
error_condition(_Enum _Errcode,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_code>::type* = 0);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Val*|Hodnota kódu chyby k ukládání `error_condition`.|
|*_Cat*|Kategorie chyby pro uložení v `error_condition`.|
|*_Errcode*|Hodnota výčtu k ukládání `error_condition`.|

### <a name="remarks"></a>Poznámky

První konstruktor uloží nulová hodnota kódu chyby a ukazatel [generic_category](../standard-library/system-error-functions.md#generic_category).

Druhý konstruktor ukládá *val* jako hodnota kódu chyby a ukazatel na [error_category](../standard-library/error-category-class.md).

Třetí konstruktor ukládá `(value_type)_Errcode` jako hodnota kódu chyby a ukazatel [generic_category](../standard-library/system-error-functions.md#generic_category).

## <a name="message"></a>  error_condition::Message

Vrátí název kód chyby.

```cpp
string message() const;
```

### <a name="return-value"></a>Návratová hodnota

A `string` představující název kód chyby.

### <a name="remarks"></a>Poznámky

Tato členská funkce vrátí `category().message(value())`.

## <a name="op_eq_eq"></a>  error_condition::Operator ==

Ověřuje rovnost mezi `error_condition` objekty.

```cpp
bool operator==(const error_condition& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doprava*|Ojbect chcete testovat rovnost.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud jsou objekty shodné; **false** Pokud objekty nejsou stejné.

### <a name="remarks"></a>Poznámky

Členský operátor vrátí `category() == right.category() && value == right.value()`.

## <a name="op_neq"></a>  error_condition::Operator! =

Testy pro nerovnost mezi `error_condition` objekty.

```cpp
bool operator!=(const error_condition& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doprava*|Objekt, který má být testována nerovnost.|

### <a name="return-value"></a>Návratová hodnota

**true** Pokud `error_condition` není roven objektu `error_condition` objekt předaný v *správné*; jinak vrátí hodnotu **false**.

### <a name="remarks"></a>Poznámky

Členský operátor vrátí `!(*this == right)`.

## <a name="op_lt"></a>  error_condition::Operator&lt;

Testuje, zda `error_condition` objekt je menší než `error_code` objekt předaný k porovnání.

```cpp
bool operator<(const error_condition& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doprava*|`error_condition` Objekt k porovnání.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud `error_condition` objekt je menší než `error_condition` objekt předaný k porovnání; V opačném případě **false**.

### <a name="remarks"></a>Poznámky

Členský operátor vrátí `category() < right.category() || category() == right.category() && value < right.value()`.

## <a name="op_eq"></a>  error_condition::Operator =

Přiřadí novou hodnotu výčtu `error_condition` objektu.

```cpp
template <class _Enum>
error_condition(_Enum error,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_condition>::type&
 operator=(Enum _Errcode);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Errcode*|Hodnota výčtu přiřadit `error_condition` objektu.|

### <a name="return-value"></a>Návratová hodnota

Odkaz na `error_condition` objekt, který se přiřadí novou hodnotu výčtu členskou funkci.

### <a name="remarks"></a>Poznámky

Operátor úložišť člen `(value_type)error` jako hodnota kódu chyby a ukazatel [generic_category](../standard-library/system-error-functions.md#generic_category). Vrátí `*this`.

## <a name="op_bool"></a>  error_condition::Operator bool

Přetypování proměnné typu `error_condition`.

```cpp
explicit operator bool() const;
```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota `error_condition` objektu.

### <a name="remarks"></a>Poznámky

Operátor vrací lze převést na typ hodnota **true** pouze tehdy, pokud [hodnotu](#value) není rovna hodnotě nula. Návratový typ je lze převést pouze na **bool**, nikoli k `void *` nebo jiné známé Skalární typy.

## <a name="value"></a>  error_condition::Value

Vrátí uložené chybová hodnota kódu.

```cpp
value_type value() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota kódu uložených chyba typu [value_type](#value_type).

### <a name="remarks"></a>Poznámky

## <a name="value_type"></a>  error_condition::value_type

Typ představující uložený chybová hodnota kódu.

```cpp
typedef int value_type;
```

### <a name="remarks"></a>Poznámky

Definice typu je synonymum pro **int**.

## <a name="see-also"></a>Viz také:

[error_category – třída](../standard-library/error-category-class.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
