---
title: '&lt;system_error&gt; funkce'
ms.date: 03/15/2019
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: ab4d0d1ee810df8f719bba762262eb03bf899408
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422421"
---
# <a name="ltsystem_errorgt-functions"></a>&lt;system_error&gt; funkce

## <a name="generic_category"></a>generic_category

Představuje kategorii pro obecné chyby.

```cpp
const error_category& generic_category() noexcept;
```

### <a name="remarks"></a>Poznámky

Objekt `generic_category` je implementací [error_category](../standard-library/error-category-class.md).

## <a name="is_error_code_enum_v"></a>is_error_code_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_code_enum_v = is_error_code_enum<T>::value;
```

## <a name="is_error_condition_enum_v"></a>is_error_condition_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_condition_enum_v = is_error_condition_enum<T>::value;
```

## <a name="make_error_code"></a>make_error_code

Vytvoří objekt kódu chyby.

```cpp
error_code make_error_code(std::errc error) noexcept;
```

### <a name="parameters"></a>Parametry

*chyba*\
Hodnota výčtu `std::errc` pro uložení do objektu kódu chyby.

### <a name="return-value"></a>Návratová hodnota

Objekt kódu chyby.

### <a name="remarks"></a>Poznámky

## <a name="make_error_condition"></a>make_error_condition

Vytvoří objekt chybové podmínky.

```cpp
error_condition make_error_condition(std::errc error) noexcept;
```

### <a name="parameters"></a>Parametry

*chyba*\
Hodnota výčtu `std::errc` pro uložení do objektu kódu chyby.

### <a name="return-value"></a>Návratová hodnota

Chybový stav objektu.

### <a name="remarks"></a>Poznámky

## <a name="system_category"></a>system_category

Představuje kategorii pro chyby způsobené přetečeními systému nižší úrovně.

```cpp
const error_category& system_category() noexcept;
```

### <a name="remarks"></a>Poznámky

Objekt `system_category` je implementací [error_category](../standard-library/error-category-class.md).
