---
title: '&lt;operátory&gt; ostream'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: c80abcb08423b4bb269e7d60ac43ef97d197a0e9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874799"
---
# <a name="ltostreamgt-operators"></a>&lt;operátory&gt; ostream

||
|-|
|[operátor&lt;&lt;](#op_lt_lt)|

## <a name="op_lt_lt"></a>operátor&lt;&lt;

Zapisuje do datového proudu různé typy.

```cpp
template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const Elem* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    Elem _Ch);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const char* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);

template <class _Elem, class _Tr, class T>
basic_ostream <_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>&& _Ostr,
    Ty val);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Znak.

*_Elem*\
Typ elementu.

*_Ostr*\
Objekt `basic_ostream`.

\ *str*
Řetězec znaků.

*_Tr*\
Vlastnosti znaků.

\ *Val*
Typ

### <a name="return-value"></a>Návratová hodnota

Datový proud.

### <a name="remarks"></a>Poznámky

Třída `basic_ostream` také definuje několik operátorů vložení. Další informace naleznete v tématu [basic_ostream:: operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

Funkce šablony

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

Určuje délku N = `traits_type::`[délku](../standard-library/char-traits-struct.md#length)(`str`) sekvence začínající na *str*a vloží sekvenci. Pokud N < `_Ostr.`[šířku](../standard-library/ios-base-class.md#width), funkce také vloží opakování `_Ostr.width` znaků N. Opakování předchází sekvenci if (`_Ostr`. [příznaky](../standard-library/ios-base-class.md#flags) & `adjustfield`! = [Left](../standard-library/ios-functions.md#left). V opačném případě bude opakování postupovat podle sekvence. Funkce vrátí *_Ostr*.

Funkce šablony

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

Vloží prvek `_Ch`. Pokud se 1 < `_Ostr.width`, funkce také vloží opakování `_Ostr.width`-1 znaků výplně. Opakování předchází sekvenci, pokud `_Ostr.flags & adjustfield != left`. V opačném případě bude opakování postupovat podle sekvence. Vrátí *_Ostr*.

Funkce šablony

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```

se chová stejně jako

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

s výjimkou toho, že každý prvek *_Ch* sekvence začínající na *str* , je převeden na objekt typu `Elem` voláním `_Ostr.`[put](../standard-library/basic-ostream-class.md#put)(`_Ostr.`[rozšířit](../standard-library/basic-ios-class.md#widen)(`_Ch`)).

Funkce šablony

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```

se chová stejně jako

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

s výjimkou, že *_Ch* je převeden na objekt typu `Elem` voláním `_Ostr.put`(`_Ostr.widen`(`_Ch`)).

Funkce šablony

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```

se chová stejně jako

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

(Není nutné elementy rozšiřovat před jejich vložením.)

Funkce šablony

```cpp
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```

se chová stejně jako

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

(Před vložením není nutné rozšíření *_Ch* .)

Funkce šablony

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

Vrátí `_Ostr` < < (`const char *`) `str`.

Funkce šablony

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

Vrátí `_Ostr` < < (`char`) `_Ch`.

Funkce šablony:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

Vrátí `_Ostr` < < (`const char *`) `str`.

Funkce šablony:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

Vrátí `_Ostr` < < (`char`) `_Ch`.

Funkce šablony:

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

Vrátí `_Ostr` `<<` `val` (a převede [odkaz rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) na `_Ostr` na lvalue v procesu).

### <a name="example"></a>Příklad

Příklad použití `operator<<`naleznete v tématu [flush](../standard-library/ostream-functions.md#flush) .

## <a name="see-also"></a>Viz také

[\<ostream >](../standard-library/ostream.md)
