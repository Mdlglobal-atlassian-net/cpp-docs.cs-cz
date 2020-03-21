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
ms.openlocfilehash: 3ed2eceb60c2efa78181faea58a256b0e35d489f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076615"
---
# <a name="error_category-class"></a>error_category – třída

Představuje abstraktní, společný základ pro objekty, které popisují kategorii chybových kódů.

## <a name="syntax"></a>Syntaxe

```cpp
class error_category;

constexpr error_category() noexcept;
virtual ~error_category();
error_category(const error_category&) = delete
```

## <a name="remarks"></a>Poznámky

Dva předdefinované objekty implementují `error_category`: [generic_category](../standard-library/system-error-functions.md#generic_category) a [system_category](../standard-library/system-error-functions.md#system_category).

## <a name="members"></a>Členové

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|Typ, který představuje uloženou hodnotu kódu chyby.|

### <a name="functions"></a>Functions

|||
|-|-|
|[default_error_condition](#default_error_condition)|Ukládá hodnotu kódu chyby pro objekt chybové podmínky.|
|[stejného](#equivalent)|Vrátí hodnotu, která určuje, zda jsou objekty Error ekvivalentní.|
|[generic_category](#generic)||
|[message](#message)|Vrátí název zadaného kódu chyby.|
|[Jméno](#name)|Vrátí název kategorie.|
|[system_category](#system)||

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_as)||
|[operator = = – operátor](#op_eq_eq)|Testuje rovnost mezi objekty `error_category`.|
|[operator!=](#op_neq)|Testy pro nerovnost mezi objekty `error_category`.|
|[operátor <](#op_lt)|Testuje, zda je objekt [error_category](../standard-library/error-category-class.md) menší, než je předaný `error_category` objekt pro porovnání.|

## <a name="default_error_condition"></a><a name="default_error_condition"></a>default_error_condition

Ukládá hodnotu kódu chyby pro objekt chybové podmínky.

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>Parametry

*_Errval*\
Hodnota kódu chyby, která se má Uložit do [error_condition](../standard-library/error-condition-class.md).

### <a name="return-value"></a>Návratová hodnota

Vrací objekt `error_condition(_Errval, *this)`.

### <a name="remarks"></a>Poznámky

### <a name="equivalent"></a><a name="equivalent"></a>stejného

Vrátí hodnotu, která určuje, zda jsou objekty Error ekvivalentní.

```cpp
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```

#### <a name="parameters"></a>Parametry

*_Errval*\
Hodnota kódu chyby, která se má porovnat

*_Cond*\
Objekt [error_condition](../standard-library/error-condition-class.md) , který se má porovnat.

*_Code*\
Objekt [error_code](../standard-library/error-code-class.md) , který se má porovnat.

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud je kategorie a hodnota rovna; v opačném případě **false**.

#### <a name="remarks"></a>Poznámky

První členská funkce vrátí `*this == _Cond.category() && _Cond.value() == _Errval`.

Druhá členská funkce vrací `*this == _Code.category() && _Code.value() == _Errval`.

### <a name="generic_category"></a><a name="generic"></a>generic_category

```cpp
const error_category& generic_category();
```

### <a name="message"></a><a name="message"></a>Zpráva

Vrátí název zadaného kódu chyby.

```cpp
virtual string message(error_code::value_type val) const = 0;
```

#### <a name="parameters"></a>Parametry

\ *Val*
Hodnota kódu chyby, která se má popsat

#### <a name="return-value"></a>Návratová hodnota

Vrátí popisný název hodnoty *Val* kódu chyby pro danou kategorii.

#### <a name="remarks"></a>Poznámky

### <a name="name"></a><a name="name"></a>Jméno

Vrátí název kategorie.

```cpp
virtual const char *name() const = 0;
```

#### <a name="return-value"></a>Návratová hodnota

Vrátí název kategorie jako řetězec bajtů zakončený hodnotou null.

### <a name="operator"></a><a name="op_as"></a>operátor =

```cpp
error_category& operator=(const error_category&) = delete;
```

### <a name="operator"></a><a name="op_eq_eq"></a>operator = = – operátor

Testuje rovnost mezi objekty `error_category`.

```cpp
bool operator==(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*pravé*\
Objekt, který má být testován pro rovnost.

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou objekty stejné; **false** , pokud objekty nejsou stejné.

#### <a name="remarks"></a>Poznámky

Tento členský operátor vrací `this == &right`.

### <a name="operator"></a><a name="op_neq"></a>! = – operátor

Testy pro nerovnost mezi objekty `error_category`.

```cpp
bool operator!=(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*pravé*\
Objekt, který má být testován pro nerovnost.

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud objekt `error_category` není rovno předanému `error_category`mu objektu *;* v opačném případě **false**.

#### <a name="remarks"></a>Poznámky

Operátor member vrátí `(!*this == right)`.

### <a name="operatorlt"></a><a name="op_lt"></a>operátor&lt;

Testuje, zda je objekt [error_category](../standard-library/error-category-class.md) menší, než je předaný `error_category` objekt pro porovnání.

```cpp
bool operator<(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*pravé*\
Objekt `error_category`, který se má porovnat.

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud je objekt `error_category` menší, než je předaný `error_category` objekt pro porovnání; V opačném případě **false**.

#### <a name="remarks"></a>Poznámky

Operátor member vrátí `this < &right`.

### <a name="system_category"></a><a name="system"></a>system_category

```cpp
const error_category& system_category();
```

### <a name="value_type"></a><a name="value_type"></a>value_type

Typ, který představuje uloženou hodnotu kódu chyby.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Poznámky

Tato definice typu je synonymum pro **int**.
