---
title: error_category – třída
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_category
- system_error/std::error_category::value_type
- system_error/std::error_category::default_error_condition
- system_error/std::error_category::equivalent
- system_error/std::error_category::message
- system_error/std::error_category::name
helpviewer_keywords:
- std::error_category
- std::error_category::value_type
- std::error_category::default_error_condition
- std::error_category::equivalent
- std::error_category::message
- std::error_category::name
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
ms.openlocfilehash: 55ff55b2026b741a2b7062d815fe43d6d19b078b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413707"
---
# <a name="errorcategory-class"></a>error_category – třída

Představuje abstraktní, běžné základ pro objekty, které popisují kategorie kódů chyb.

## <a name="syntax"></a>Syntaxe

```cpp
class error_category;
```

## <a name="remarks"></a>Poznámky

Dvě předdefinované objekty, které implementují `error_category`: [generic_category](../standard-library/system-error-functions.md#generic_category) a [system_category](../standard-library/system-error-functions.md#system_category).

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[value_type](#value_type)|Typ představující uložený chybová hodnota kódu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[default_error_condition](#default_error_condition)|Uloží hodnotu Chyba kódu pro objekt chybová podmínka.|
|[ekvivalent](#equivalent)|Vrátí hodnotu, která určuje, zda jsou ekvivalentní objekty chyby.|
|[message](#message)|Vrací název zadané chybový kód.|
|[Jméno](#name)|Vrátí název kategorie.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator==](#op_eq_eq)|Ověřuje rovnost mezi `error_category` objekty.|
|[operator!=](#op_neq)|Testy pro nerovnost mezi `error_category` objekty.|
|[Operator <](#op_lt)|Testuje, zda [error_category](../standard-library/error-category-class.md) objekt je menší než `error_category` objekt předaný k porovnání.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<system_error >

**Namespace:** std

## <a name="default_error_condition"></a>  error_category::default_error_condition

Uloží hodnotu Chyba kódu pro objekt chybová podmínka.

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Errval*|Hodnota kódu chyby k ukládání [error_condition –](../standard-library/error-condition-class.md).|

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
|*_Errval*|Hodnota kódu chyby k porovnání.|
|*_Cond*|[Error_condition –](../standard-library/error-condition-class.md) objekt k porovnání.|
|*_Code*|[Error_code](../standard-library/error-code-class.md) objekt k porovnání.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud kategorie a hodnota jsou stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí `*this == _Cond.category() && _Cond.value() == _Errval`.

Druhá členská funkce vrátí `*this == _Code.category() && _Code.value() == _Errval`.

## <a name="message"></a>  error_category::Message

Vrací název zadané chybový kód.

```cpp
virtual string message(error_code::value_type val) const = 0;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Val*|Hodnota kódu chyby k popisu.|

### <a name="return-value"></a>Návratová hodnota

Vrátí kód chyby: popisný název *val* kategorie.

### <a name="remarks"></a>Poznámky

## <a name="name"></a>  error_category::Name

Vrátí název kategorie.

```cpp
virtual const char *name() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí název kategorie, jako řetězec zakončený hodnotou null bajtů.

### <a name="remarks"></a>Poznámky

## <a name="op_eq_eq"></a>  error_category::Operator ==

Ověřuje rovnost mezi `error_category` objekty.

```cpp
bool operator==(const error_category& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doprava*|Objekt, který chcete testovat rovnost.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud jsou objekty shodné; **false** Pokud objekty nejsou stejné.

### <a name="remarks"></a>Poznámky

Tento členský operátor vrátí `this == &right`.

## <a name="op_neq"></a>  error_category::Operator! =

Testy pro nerovnost mezi `error_category` objekty.

```cpp
bool operator!=(const error_category& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doprava*|Objekt, který má být testována nerovnost.|

### <a name="return-value"></a>Návratová hodnota

**true** Pokud `error_category` není roven objektu `error_category` objekt předaný v *správné*; jinak vrátí hodnotu **false**.

### <a name="remarks"></a>Poznámky

Členský operátor vrátí `(!*this == right)`.

## <a name="op_lt"></a>  error_category::Operator&lt;

Testuje, zda [error_category](../standard-library/error-category-class.md) objekt je menší než `error_category` objekt předaný k porovnání.

```cpp
bool operator<(const error_category& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doprava*|`error_category` Objekt k porovnání.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud `error_category` objekt je menší než `error_category` objekt předaný k porovnání; V opačném případě **false**.

### <a name="remarks"></a>Poznámky

Členský operátor vrátí `this < &right`.

## <a name="value_type"></a>  error_category::value_type

Typ představující uložený chybová hodnota kódu.

```cpp
typedef int value_type;
```

### <a name="remarks"></a>Poznámky

Tato definice typu je synonymum pro **int**.

## <a name="see-also"></a>Viz také:

[<system_error>](../standard-library/system-error.md)<br/>
