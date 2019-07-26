---
title: '&lt;ostream&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: c80abcb08423b4bb269e7d60ac43ef97d197a0e9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453523"
---
# <a name="ltostreamgt-operators"></a>&lt;ostream&gt; operátory

||
|-|
|[podnikatel&lt;&lt;](#op_lt_lt)|

## <a name="op_lt_lt"></a>podnikatel&lt;&lt;

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
A `basic_ostream` objektu.

*str*\
Řetězec znaků.

*_Tr*\
Vlastnosti znaků.

*počítává*\
Typ

### <a name="return-value"></a>Návratová hodnota

Datový proud.

### <a name="remarks"></a>Poznámky

`basic_ostream` Třída také definuje několik operátorů vložení. Další informace naleznete v tématu [basic_ostream:: operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

Funkce šablony

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

Určuje délku `traits_type::`N = [Length](../standard-library/char-traits-struct.md#length)(`str`) sekvence začínající na *str*a vloží sekvenci. Pokud N < `_Ostr.` [Šířka](../standard-library/ios-base-class.md#width), pak funkce také vloží opakování `_Ostr.width` N znaků výplně. Opakování předchází sekvenci if (`_Ostr`. [](../standard-library/ios-base-class.md#flags)příznaky & != [Left](../standard-library/ios-functions.md#left).`adjustfield` V opačném případě bude opakování postupovat podle sekvence. Funkce vrátí *_Ostr*.

Funkce šablony

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

Vloží element `_Ch`. Pokud se 1 `_Ostr.width`<, funkce také vloží `_Ostr.width` opakování – 1 znaků výplně. Opakování předchází sekvenci, pokud `_Ostr.flags & adjustfield != left`. V opačném případě bude opakování postupovat podle sekvence. Vrátí *_Ostr*.

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

s výjimkou toho, že každý prvek *_Ch* sekvence začínající na *str* , je převeden na objekt `Elem` typu voláním metody`_Ostr.` `_Ostr.` [Put](../standard-library/basic-ostream-class.md#put)(`_Ch`[rozšiřující](../standard-library/basic-ios-class.md#widen)()).

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

s výjimkou, že *_Ch* je převeden na objekt `Elem` typu voláním `_Ostr.widen` `_Ostr.put`( `_Ch`()).

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

(Není nutné rozšířit *_Ch* před vložením.)

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

Vrátí `_Ostr` `_Ostr` [](../cpp/rvalue-reference-declarator-amp-amp.md) (a převede odkaz rvalue na lvalue v procesu). `<<` `val`

### <a name="example"></a>Příklad

Příklad [](../standard-library/ostream-functions.md#flush) použití `operator<<`naleznete v tématu flush.

## <a name="see-also"></a>Viz také:

[\<ostream >](../standard-library/ostream.md)
