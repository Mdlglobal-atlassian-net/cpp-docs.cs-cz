---
title: '&lt;system_error&gt; functions'
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
ms.openlocfilehash: 78be83af678b553babbf1cde3d96c1507940b611
ms.sourcegitcommit: 9e85c2e029d06b4c1c69837437468718b4d54908
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2019
ms.locfileid: "58172904"
---
# <a name="ltsystemerrorgt-functions"></a>&lt;system_error&gt; functions

||||
|-|-|-|
|[generic_category](#generic_category)|[make_error_code](#make_error_code)|[make_error_condition](#make_error_condition)|
|[system_category](#system_category)|||

## <a name="generic_category"></a> generic_category –

Představuje konkrétní kategorii obecné chyby.

```cpp
const error_category& generic_category() noexcept;
```

### <a name="remarks"></a>Poznámky

`generic_category` Objektu je implementace [error_category](../standard-library/error-category-class.md).

## <a name="make_error_code"></a>  make_error_code –

Vytváří objekt error kódu.

```cpp
error_code make_error_code(std::errc error) noexcept;
```

### <a name="parameters"></a>Parametry

*Chyba*\
`std::errc` Hodnotu výčtu pro uložení objektu kód chyby.

### <a name="return-value"></a>Návratová hodnota

Objekt kódu chyby.

### <a name="remarks"></a>Poznámky

## <a name="make_error_condition"></a>  make_error_condition

Vytváří objekt error podmínku.

```cpp
error_condition make_error_condition(std::errc error) noexcept;
```

### <a name="parameters"></a>Parametry

*Chyba*\
`std::errc` Hodnotu výčtu pro uložení objektu kód chyby.

### <a name="return-value"></a>Návratová hodnota

Objekt, podmínku chyby.

### <a name="remarks"></a>Poznámky

## <a name="system_category"></a>  system_category –

Představuje konkrétní kategorii chyby způsobené nižší úrovně systému přetečení.

```cpp
const error_category& system_category() noexcept;
```

### <a name="remarks"></a>Poznámky

`system_category` Objektu je implementace [error_category](../standard-library/error-category-class.md).

## <a name="see-also"></a>Viz také:

[\<system_error>](../standard-library/system-error.md)<br/>
