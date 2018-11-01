---
title: '&lt;ostream&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: ee1a9a6829dbef13b034300d696c43ddba48d9d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449420"
---
# <a name="ltostreamgt-operators"></a>&lt;ostream&gt; operátory

||
|-|
|[– Operátor&lt;&lt;](#op_lt_lt)|

## <a name="op_lt_lt"></a>  – Operátor&lt;&lt;

Různé typy zapíše do datového proudu.

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

*_Ch*<br/>
Znak.

*_Elem*<br/>
Typ elementu.

*_Ostr*<br/>
A `basic_ostream` objektu.

*str*<br/>
Řetězec znaků.

*_Tr*<br/>
Vlastnosti znaků.

*Val*<br/>
Typ

### <a name="return-value"></a>Návratová hodnota

Datový proud.

### <a name="remarks"></a>Poznámky

`basic_ostream` Třída také definuje několik operátorů insertion. Další informace najdete v tématu [basic_ostream::operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

Funkce šablon

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

Určuje délku N = `traits_type::` [délka](../standard-library/char-traits-struct.md#length)(`str`) z pořadí počínaje *str*a vloží sekvenci. Pokud N < `_Ostr.` [šířka](../standard-library/ios-base-class.md#width), pak funkce také vloží opakování `_Ostr.width` -N znaky výplně. Opakování předchází pořadí, pokud (`_Ostr`. [příznaky](../standard-library/ios-base-class.md#flags)  &  `adjustfield` ! = [levé](../standard-library/ios-functions.md#left). V opačném případě opakování následuje sekvence. Funkce vrátí *_Ostr*.

Funkce šablon

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

Vloží prvek `_Ch`. Pokud 1 < `_Ostr.width`, pak funkce také vloží opakování `_Ostr.width` – 1 zadejte znaky. Opakování předchází pořadí, pokud `_Ostr.flags & adjustfield != left`. V opačném případě opakování následuje sekvence. Vrátí *_Ostr*.

Funkce šablon

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```

chová se stejně jako

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

s tím rozdílem, že každý prvek *_Ch* z pořadí počínaje *str* je převeden na objekt typu `Elem` voláním `_Ostr.` [umístit](../standard-library/basic-ostream-class.md#put)(`_Ostr.` [rozšířit](../standard-library/basic-ios-class.md#widen)(`_Ch`)).

Funkce šablon

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```

chová se stejně jako

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

s tím rozdílem, že *_Ch* je převeden na objekt typu `Elem` voláním `_Ostr.put`( `_Ostr.widen`( `_Ch`)).

Funkce šablon

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```

chová se stejně jako

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

(Nemá rozšířit prvky před jejich vložením.)

Funkce šablon

```cpp
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```

chová se stejně jako

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

(Není nutné rozšířit *_Ch* před vložením.)

Funkce šablon

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

Vrátí `_Ostr` << (`const char *`) `str`.

Funkce šablon

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

Vrátí `_Ostr` << (`char`) `_Ch`.

Funkce šablony:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

Vrátí `_Ostr` << (`const char *`) `str`.

Funkce šablony:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

Vrátí `_Ostr` << (`char`) `_Ch`.

Funkce šablony:

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

Vrátí `_Ostr` `<<` `val` (a převede [odkaz RValue](../cpp/rvalue-reference-declarator-amp-amp.md) k `_Ostr` na lvalue v procesu).

### <a name="example"></a>Příklad

Zobrazit [vyprázdnění](../standard-library/ostream-functions.md#flush) příklad použití `operator<<`.

## <a name="see-also"></a>Viz také:

[\<ostream >](../standard-library/ostream.md)<br/>
