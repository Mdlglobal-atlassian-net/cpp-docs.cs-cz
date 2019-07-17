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
ms.openlocfilehash: 308fa1a2309ddfda1a02fe6a687360185c1e7c6e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245844"
---
# <a name="errorcategory-class"></a>error_category – třída

Představuje abstraktní, běžné základ pro objekty, které popisují kategorie kódů chyb.

## <a name="syntax"></a>Syntaxe

```cpp
class error_category;

constexpr error_category() noexcept;
virtual ~error_category();
error_category(const error_category&) = delete
```

## <a name="remarks"></a>Poznámky

Dvě předdefinované objekty, které implementují `error_category`: [generic_category](../standard-library/system-error-functions.md#generic_category) a [system_category](../standard-library/system-error-functions.md#system_category).

## <a name="members"></a>Členové

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|Typ představující uložený chybová hodnota kódu.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[default_error_condition](#default_error_condition)|Uloží hodnotu Chyba kódu pro objekt chybová podmínka.|
|[ekvivalent](#equivalent)|Vrátí hodnotu, která určuje, zda jsou ekvivalentní objekty chyby.|
|[generic_category –](#generic)||
|[message](#message)|Vrací název zadané chybový kód.|
|[name](#name)|Vrátí název kategorie.|
|[system_category](#system)||

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_as)||
|[operator==](#op_eq_eq)|Ověřuje rovnost mezi `error_category` objekty.|
|[operator!=](#op_neq)|Testy pro nerovnost mezi `error_category` objekty.|
|[Operator <](#op_lt)|Testuje, zda [error_category](../standard-library/error-category-class.md) objekt je menší než `error_category` objekt předaný k porovnání.|

## <a name="default_error_condition"></a> default_error_condition –

Uloží hodnotu Chyba kódu pro objekt chybová podmínka.

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>Parametry

*_Errval*\
Hodnota kódu chyby k ukládání [error_condition –](../standard-library/error-condition-class.md).

### <a name="return-value"></a>Návratová hodnota

Vrátí `error_condition(_Errval, *this)`.

### <a name="remarks"></a>Poznámky

### <a name="equivalent"></a> ekvivalent

Vrátí hodnotu, která určuje, zda jsou ekvivalentní objekty chyby.

```cpp
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```

#### <a name="parameters"></a>Parametry

*_Errval*\
Hodnota kódu chyby k porovnání.

*_Cond*\
[Error_condition –](../standard-library/error-condition-class.md) objekt k porovnání.

*_Fragmenty*\
[Error_code](../standard-library/error-code-class.md) objekt k porovnání.

#### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud kategorie a hodnota jsou stejné, jinak **false**.

#### <a name="remarks"></a>Poznámky

První členská funkce vrátí `*this == _Cond.category() && _Cond.value() == _Errval`.

Druhá členská funkce vrátí `*this == _Code.category() && _Code.value() == _Errval`.

### <a name="generic"></a> generic_category –

```cpp
const error_category& generic_category();
```

### <a name="message"></a> Zpráva

Vrací název zadané chybový kód.

```cpp
virtual string message(error_code::value_type val) const = 0;
```

#### <a name="parameters"></a>Parametry

*Val*\
Hodnota kódu chyby k popisu.

#### <a name="return-value"></a>Návratová hodnota

Vrátí kód chyby: popisný název *val* kategorie.

#### <a name="remarks"></a>Poznámky

### <a name="name"></a> Jméno

Vrátí název kategorie.

```cpp
virtual const char *name() const = 0;
```

#### <a name="return-value"></a>Návratová hodnota

Vrátí název kategorie, jako řetězec zakončený hodnotou null bajtů.

### <a name="op_as"></a> operátor =

```cpp
error_category& operator=(const error_category&) = delete;
```


### <a name="op_eq_eq"></a> Operator ==

Ověřuje rovnost mezi `error_category` objekty.

```cpp
bool operator==(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*doprava*\
Objekt, který chcete testovat rovnost.

#### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud jsou objekty shodné; **false** Pokud objekty nejsou stejné.

#### <a name="remarks"></a>Poznámky

Tento členský operátor vrátí `this == &right`.

### <a name="op_neq"></a> Operator! =

Testy pro nerovnost mezi `error_category` objekty.

```cpp
bool operator!=(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*doprava*\
Objekt, který má být testována nerovnost.

#### <a name="return-value"></a>Návratová hodnota

**true** Pokud `error_category` není roven objektu `error_category` objekt předaný v *správné*; jinak vrátí hodnotu **false**.

#### <a name="remarks"></a>Poznámky

Členský operátor vrátí `(!*this == right)`.

### <a name="op_lt"></a> – Operátor&lt;

Testuje, zda [error_category](../standard-library/error-category-class.md) objekt je menší než `error_category` objekt předaný k porovnání.

```cpp
bool operator<(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*doprava*\
`error_category` Objekt k porovnání.

#### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud `error_category` objekt je menší než `error_category` objekt předaný k porovnání; V opačném případě **false**.

#### <a name="remarks"></a>Poznámky

Členský operátor vrátí `this < &right`.

### <a name="system"></a> system_category –

```cpp
const error_category& system_category();
```

### <a name="value_type"></a> value_type

Typ představující uložený chybová hodnota kódu.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Poznámky

Tato definice typu je synonymum pro **int**.
