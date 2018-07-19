---
title: '&lt;system_error –&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 838a63fc43ef71561c0911cfa4c85c76cf04bc08
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959662"
---
# <a name="ltsystemerrorgt-functions"></a>&lt;system_error –&gt; funkce

||||
|-|-|-|
|[generic_category –](#generic_category)|[make_error_code](#make_error_code)|[make_error_condition](#make_error_condition)|
|[system_category](#system_category)|

## <a name="generic_category"></a>  generic_category –

Představuje konkrétní kategorii obecné chyby.

```cpp
extern const error_category& generic_category();
```

### <a name="remarks"></a>Poznámky

`generic_category` Objektu je implementace [error_category](../standard-library/error-category-class.md).

## <a name="make_error_code"></a>  make_error_code –

Vytváří objekt error kódu.

```cpp
error_code make_error_code(generic_errno _Errno);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Errno*|Hodnota výčtu k uložení objektu kód chyby.|

### <a name="return-value"></a>Návratová hodnota

Objekt kódu chyby.

### <a name="remarks"></a>Poznámky

## <a name="make_error_condition"></a>  make_error_condition –

Vytváří objekt error podmínku.

```cpp
error_condition make_error_condition(generic_errno _Errno);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Errno*|Hodnota výčtu k uložení objektu chybová podmínka.|

### <a name="return-value"></a>Návratová hodnota

Objekt, podmínku chyby.

### <a name="remarks"></a>Poznámky

## <a name="system_category"></a>  system_category –

Představuje konkrétní kategorii chyby způsobené nižší úrovně systému přetečení.

```cpp
extern const error_category& system_category();
```

### <a name="remarks"></a>Poznámky

`system_category` Objektu je implementace [error_category](../standard-library/error-category-class.md).

## <a name="see-also"></a>Viz také:

[<system_error>](../standard-library/system-error.md)<br/>
