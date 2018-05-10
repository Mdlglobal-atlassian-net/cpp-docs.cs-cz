---
title: '&lt;system_error –&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
dev_langs:
- C++
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: d0a556505370078f599d6d667fa856723d9bac8f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ltsystemerrorgt-operators"></a>&lt;system_error –&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operátor&lt;](#op_lt)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  Operator ==

Testy, pokud je objekt na levé straně operátoru stejný objekt na pravé straně.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`left`|Objekt, který má být testována rovnosti.|
|`right`|Objekt, který má být testována rovnosti.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud objekty jsou stejné; **false** Pokud objekty nejsou stejné.

### <a name="remarks"></a>Poznámky

Funkce vrátí hodnotu `left.category() == right.category() && left.value() == right.value()`.

## <a name="op_neq"></a>  Operator! =

Testy, pokud objekt na levé straně operátoru není stejný jako objekt na pravé straně.

```cpp
bool operator!=(const error_code& left,
    const error_condition& right);

bool operator!=(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`left`|Objekt, který má být testována nerovnost.|
|`right`|Objekt, který má být testována nerovnost.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud objekt předaný `left` není stejný jako objekt předaný `right`jinak **false**.

### <a name="remarks"></a>Poznámky

Funkce vrátí hodnotu `!(left == right)`.

## <a name="op_lt"></a>  Operátor&lt;

Zkouší, zda je objekt menší než objekt předaný k porovnání.

```cpp
template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type left, _Enum right);

template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type left, _Enum right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`left`|Objekt, který chcete porovnat.|
|`right`|Objekt, který chcete porovnat.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud objekt předaný `left` je menší než předaná objekt `right`; V opačném **false**.

### <a name="remarks"></a>Poznámky

Tato funkce testuje pořadí chyb.

## <a name="see-also"></a>Viz také

[<system_error>](../standard-library/system-error.md)<br/>
