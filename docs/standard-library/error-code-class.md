---
title: error_code – třída
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_code
- system_error/std::error_code::value_type
- system_error/std::error_code::assign
- system_error/std::error_code::category
- system_error/std::error_code::clear
- system_error/std::error_code::default_error_condition
- system_error/std::error_code::message
- system_error/std::error_code::operator bool
helpviewer_keywords:
- std::error_code
- std::error_code::value_type
- std::error_code::assign
- std::error_code::category
- std::error_code::clear
- std::error_code::default_error_condition
- std::error_code::message
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
ms.openlocfilehash: 919a2a81c66de9adf15deeae8cf8ff3dea08762e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245824"
---
# <a name="errorcode-class"></a>error_code – třída

Reprezentuje chyby nízké úrovně systému, které jsou specifické pro implementaci.

## <a name="syntax"></a>Syntaxe

```cpp
class error_code;
```

## <a name="remarks"></a>Poznámky

Objekt typu `error_code` třída uchovává chybovou hodnotu kód a ukazatele na objekt, který představuje [kategorie](../standard-library/error-category-class.md) chyby kódy, které popisují hlášené chyby nízké úrovně systému.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[error_code](#error_code)|Vytvoří objekt typu `error_code`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|Typ představující uložený chybová hodnota kódu.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[assign](#assign)|Hodnota kódu chyby a kategorie služby přiřadí chybový kód.|
|[Kategorie](#category)|Vrací kategorie chyby.|
|[Vymazat](#clear)|Vymaže hodnota kódu chyby a kategorie.|
|[default_error_condition](#default_error_condition)|Vrátí výchozí chybový stav.|
|[message](#message)|Vrátí název kód chyby.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator==](#op_eq_eq)|Ověřuje rovnost mezi `error_code` objekty.|
|[operator!=](#op_neq)|Testy pro nerovnost mezi `error_code` objekty.|
|[Operator <](#op_lt)|Testuje, zda `error_code` objekt je menší než `error_code` objekt předaný k porovnání.|
|[operátor =](#op_eq)|Přiřadí novou hodnotu výčtu `error_code` objektu.|
|[bool – operátor](#op_bool)|Přetypování proměnné typu `error_code`.|

### <a name="assign"></a> přiřazení

Hodnota kódu chyby a kategorie služby přiřadí chybový kód.

```cpp
void assign(value_type val, const error_category& _Cat);
```

#### <a name="parameters"></a>Parametry

*Val*\
Hodnota kódu chyby k ukládání `error_code`.

*_Cat*\
Kategorie chyby pro uložení v `error_code`.

#### <a name="remarks"></a>Poznámky

Členské funkce úložiště *val* jako hodnota kódu chyby a ukazatel na *_Cat*.

### <a name="category"></a> Kategorie

Vrací kategorie chyby.

```cpp
const error_category& category() const;
```

#### <a name="remarks"></a>Poznámky

### <a name="clear"></a> Vymazat

Vymaže hodnota kódu chyby a kategorie.

```cpp
clear();
```

#### <a name="remarks"></a>Poznámky

Členská funkce ukládá nulová hodnota kódu chyby a ukazatel [generic_category](../standard-library/system-error-functions.md#generic_category) objektu.

### <a name="default_error_condition"></a> default_error_condition –

Vrátí výchozí chybový stav.

```cpp
error_condition default_error_condition() const;
```

#### <a name="return-value"></a>Návratová hodnota

[Error_condition –](../standard-library/error-condition-class.md) určená [default_error_condition –](../standard-library/error-category-class.md#default_error_condition).

#### <a name="remarks"></a>Poznámky

Tato členská funkce vrátí `category().default_error_condition(value())`.

### <a name="error_code"></a> error_code –

Vytvoří objekt typu `error_code`.

```cpp
error_code();

error_code(value_type val, const error_category& _Cat);

template <class _Enum>
error_code(_Enum _Errcode,
    typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type* = 0);
```

#### <a name="parameters"></a>Parametry

*Val*\
Hodnota kódu chyby k ukládání `error_code`.

*_Cat*\
Kategorie chyby pro uložení v `error_code`.

*_Errcode*\
Hodnota výčtu k ukládání `error_code`.

#### <a name="remarks"></a>Poznámky

První konstruktor uloží nulová hodnota kódu chyby a ukazatel [generic_category](../standard-library/system-error-functions.md#generic_category).

Druhý konstruktor ukládá *val* jako hodnota kódu chyby a ukazatel na [error_category](../standard-library/error-category-class.md).

Třetí konstruktor ukládá `(value_type)_Errcode` jako hodnota kódu chyby a ukazatel [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="message"></a> Zpráva

Vrátí název kód chyby.

```cpp
string message() const;
```

#### <a name="return-value"></a>Návratová hodnota

A `string` představující název kód chyby.

#### <a name="remarks"></a>Poznámky

Tato členská funkce vrátí `category().message(value())`.

### <a name="op_eq_eq"></a> Operator ==

Ověřuje rovnost mezi `error_code` objekty.

```cpp
bool operator==(const error_code& right) const;
```

#### <a name="parameters"></a>Parametry

*doprava*\
Objekt, který chcete testovat rovnost.

#### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud jsou objekty shodné; **false** Pokud objekty nejsou stejné.

#### <a name="remarks"></a>Poznámky

Členský operátor vrátí `category() == right.category() && value == right.value()`.

### <a name="op_neq"></a> Operator! =

Testy pro nerovnost mezi `error_code` objekty.

```cpp
bool operator!=(const error_code& right) const;
```

#### <a name="parameters"></a>Parametry

*doprava*\
Objekt, který má být testována nerovnost.

#### <a name="return-value"></a>Návratová hodnota

**true** Pokud `error_code` není roven objektu `error_code` objekt předaný v *správné*; jinak vrátí hodnotu **false**.

#### <a name="remarks"></a>Poznámky

Členský operátor vrátí `!(*this == right)`.

### <a name="op_lt"></a> – Operátor&lt;

Testuje, zda `error_code` objekt je menší než `error_code` objekt předaný k porovnání.

```cpp
bool operator<(const error_code& right) const;
```

#### <a name="parameters"></a>Parametry

*doprava*\
Error_code – objekt, který se má porovnat.

#### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud `error_code` objekt je menší než `error_code` objekt předaný k porovnání; V opačném případě **false**.

#### <a name="remarks"></a>Poznámky

Členský operátor vrátí `category() < right.category() || category() == right.category() && value < right.value()`.

### <a name="op_eq"></a> operátor =

Přiřadí novou hodnotu výčtu `error_code` objektu.

```cpp
template <class _Enum>
typename enable_if<is_error_code_enum<_Enum>::value, error_code>::type&
    operator=(_Enum _Errcode);
```

#### <a name="parameters"></a>Parametry

*_Errcode*\
Hodnota výčtu přiřadit `error_code` objektu.

#### <a name="return-value"></a>Návratová hodnota

Odkaz na `error_code` objekt, který se přiřadí novou hodnotu výčtu členskou funkci.

#### <a name="remarks"></a>Poznámky

Operátor úložišť člen `(value_type)_Errcode` jako hodnota kódu chyby a ukazatel [generic_category](../standard-library/system-error-functions.md#generic_category). Vrátí `*this`.

### <a name="op_bool"></a> bool – operátor

Přetypování proměnné typu `error_code`.

```cpp
explicit operator bool() const;
```

#### <a name="return-value"></a>Návratová hodnota

Logická hodnota `error_code` objektu.

#### <a name="remarks"></a>Poznámky

Operátor vrací lze převést na typ hodnota **true** pouze tehdy, pokud [hodnotu](#value) není rovna hodnotě nula. Návratový typ je lze převést pouze na **bool**, nikoli k `void *` nebo jiné známé Skalární typy.

### <a name="value"></a> Hodnota

Vrátí uložené chybová hodnota kódu.

```cpp
value_type value() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota kódu uložených chyba typu [value_type](#value_type).

### <a name="value_type"></a> value_type

Typ představující uložený chybová hodnota kódu.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Poznámky

Tato definice typu je synonymum pro **int**.
