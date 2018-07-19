---
title: '&lt;system_error –&gt; operátory | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
dev_langs:
- C++
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 974b1294f8ef23936d79e64926595779a9019368
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963690"
---
# <a name="ltsystemerrorgt-operators"></a>&lt;system_error –&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[– Operátor&lt;](#op_lt)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  Operator ==

Testuje, zda je objekt na levé straně operátoru roven objektu na pravé straně.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Objekt, který chcete testovat rovnost.|
|*doprava*|Objekt, který chcete testovat rovnost.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud jsou objekty shodné; **false** Pokud objekty nejsou stejné.

### <a name="remarks"></a>Poznámky

Tato funkce vrací `left.category() == right.category() && left.value() == right.value()`.

## <a name="op_neq"></a>  Operator! =

Testuje, zda je objekt na levé straně operátoru není roven objektu na pravé straně.

```cpp
bool operator!=(const error_code& left,
    const error_condition& right);

bool operator!=(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Objekt, který má být testována nerovnost.|
|*doprava*|Objekt, který má být testována nerovnost.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je objekt předaný v *levé* není shodný s předaným objektem *správné*; jinak vrátí hodnotu **false**.

### <a name="remarks"></a>Poznámky

Tato funkce vrací `!(left == right)`.

## <a name="op_lt"></a>  – Operátor&lt;

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
|*doleva*|Objekt, který chcete porovnat.|
|*doprava*|Objekt, který chcete porovnat.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je objekt předaný v *levé* je menší než objekt předaný v *správné*; V opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato funkce testuje pořadí chyb.

## <a name="see-also"></a>Viz také:

[<system_error>](../standard-library/system-error.md)<br/>
