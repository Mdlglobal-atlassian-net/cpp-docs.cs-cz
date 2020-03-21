---
title: operátory &lt;system_error&gt;
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 8631cae146a311f1890583900b564471d5a80958
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076264"
---
# <a name="ltsystem_errorgt-operators"></a>operátory &lt;system_error&gt;

## <a name="operator"></a><a name="op_eq_eq"></a>operator = = – operátor

Testuje, zda je objekt na levé straně operátoru roven objektu na pravé straně.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);

bool operator==(const error_condition& left,
    const error_condition& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt, který má být testován pro rovnost.

*pravé*\
Objekt, který má být testován pro rovnost.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou objekty stejné; **false** , pokud objekty nejsou stejné.

### <a name="remarks"></a>Poznámky

Tato funkce vrací `left.category() == right.category() && left.value() == right.value()`.

## <a name="operator"></a><a name="op_neq"></a>! = – operátor

Testuje, zda objekt na levé straně operátoru není roven objektu na pravé straně.

```cpp
bool operator!=(const error_code& left, const error_condition& right);
bool operator!=(const error_condition& left, const error_code& right);
bool operator!=(const error_code& left, const error_code& right);
bool operator!=(const error_condition& left, const error_condition& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt, který má být testován pro nerovnost.

*pravé*\
Objekt, který má být testován pro nerovnost.

### <a name="return-value"></a>Návratová hodnota

**true** *, pokud*objekt předaný *doleva* není rovno předanému objektu; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato funkce vrací `!(left == right)`.

## <a name="operatorlt"></a><a name="op_lt"></a>operátor&lt;

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

*levý*\
Objekt, který chcete porovnat.

*pravé*\
Objekt, který chcete porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** , *Pokud je* předaný objekt menší než objekt předaný do *pravé*části; V opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato funkce testuje pořadí chyb.

## <a name="operatorltlt"></a><a name="op_ostream"></a>operátor&lt;&lt;

```cpp
template <class charT, class traits>
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
