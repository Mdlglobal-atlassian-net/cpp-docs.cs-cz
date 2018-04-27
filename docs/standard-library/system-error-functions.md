---
title: '&lt;system_error –&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
caps.latest.revision: 11
manager: ghogen
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: 988c3580d1cd9a66e1b396fc83bd20fd3f4a115e
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltsystemerrorgt-functions"></a>&lt;system_error –&gt; funkce

||||
|-|-|-|
|[generic_category](#generic_category)|[make_error_code](#make_error_code)|[make_error_condition](#make_error_condition)|
|[system_category](#system_category)|

## <a name="generic_category"></a>  generic_category

Představuje kategorii pro obecné chyby.

```cpp
extern const error_category& generic_category();
```

### <a name="remarks"></a>Poznámky

`generic_category` Objektu je implementací [error_category](../standard-library/error-category-class.md).

## <a name="make_error_code"></a>  make_error_code –

Vytvoří objekt kódu chyby.

```cpp
error_code make_error_code(generic_errno _Errno);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`_Errno`|Hodnota výčtu ukládat v objektu, kód chyby.|

### <a name="return-value"></a>Návratová hodnota

Objekt, kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="make_error_condition"></a>  make_error_condition –

Vytvoří objekt podmínku chyby.

```cpp
error_condition make_error_condition(generic_errno _Errno);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`_Errno`|Hodnota výčtu uložit do objektu podmínku chyby.|

### <a name="return-value"></a>Návratová hodnota

Objekt, podmínku chyby.

### <a name="remarks"></a>Poznámky

## <a name="system_category"></a>  system_category

Představuje kategorii pro chyby způsobené některé nízké úrovně systému.

```cpp
extern const error_category& system_category();
```

### <a name="remarks"></a>Poznámky

`system_category` Objektu je implementací [error_category](../standard-library/error-category-class.md).

## <a name="see-also"></a>Viz také

[<system_error>](../standard-library/system-error.md)<br/>
