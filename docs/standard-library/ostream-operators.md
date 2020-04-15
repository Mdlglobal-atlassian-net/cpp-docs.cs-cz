---
title: '&lt;provozovatelé&gt; ostream'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: d8b6f4e0f0b5bca41f8d895415fff4003231ad1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373609"
---
# <a name="ltostreamgt-operators"></a>&lt;provozovatelé&gt; ostream

||
|-|
|[Operátor&lt;&lt;](#op_lt_lt)|

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>Operátor&lt;&lt;

Zapisuje různé typy do datového proudu.

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
Postava.

*_Elem*\
Typ prvku.

*_Ostr*\
Objekt. `basic_ostream`

*Str*\
Řetězec znaků.

*_Tr*\
Charakterové rysy.

*Val*\
Typ

### <a name="return-value"></a>Návratová hodnota

Proud.

### <a name="remarks"></a>Poznámky

Třída `basic_ostream` také definuje několik operátorů vložení. Další informace naleznete v [tématu basic_ostream::operator&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

Funkce šablony

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

určuje délku N `traits_type::`=`str` [délku](../standard-library/char-traits-struct.md#length)( ) sekvence začínající na *str*a vloží sekvenci. Pokud N `_Ostr.`< [šířku](../standard-library/ios-base-class.md#width), pak funkce `_Ostr.width` také vloží opakování - N výplní znaků. Opakování předchází sekvenci if (`_Ostr`. [flags](../standard-library/ios-base-class.md#flags) &  příznaky`adjustfield` != [vlevo](../standard-library/ios-functions.md#left). V opačném případě opakování následuje posloupnost. Funkce vrátí *_Ostr*.

Funkce šablony

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

vloží prvek `_Ch`. Pokud 1 `_Ostr.width`< , pak funkce také `_Ostr.width` vloží opakování - 1 výplň znaky. Opakování předchází sekvence `_Ostr.flags & adjustfield != left`if . V opačném případě opakování následuje posloupnost. Vrátí *_Ostr*.

Funkce šablony

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

s tím, že každý prvek *_Ch* sekvence začínající na *str* je převeden na objekt typu `Elem` voláním `_Ostr.` [put](../standard-library/basic-ostream-class.md#put)`_Ostr.`([widen](../standard-library/basic-ios-class.md#widen)(`_Ch`)).

Funkce šablony

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

s tím, že *_Ch* je `Elem` převeden `_Ostr.put`na `_Ostr.widen` `_Ch`objekt typu voláním ( ( ).).

Funkce šablony

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

(Není nutné rozšířit prvky před jejich vložením.)

Funkce šablony

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

(Před vložením nemusí *_Ch* rozšiřovat.)

Funkce šablony

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

vrátí `_Ostr` `const char *` << ( `str`).

Funkce šablony

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

vrátí `_Ostr` `char` << ( `_Ch`).

Funkce šablony:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

vrátí `_Ostr` `const char *` << ( `str`).

Funkce šablony:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

vrátí `_Ostr` `char` << ( `_Ch`).

Funkce šablony:

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

`_Ostr` `<<` vrátí `val` (a převede odkaz `_Ostr` [RValue na](../cpp/rvalue-reference-declarator-amp-amp.md) lvalue v procesu).

### <a name="example"></a>Příklad

Viz [flush](../standard-library/ostream-functions.md#flush) pro `operator<<`příklad pomocí .

## <a name="see-also"></a>Viz také

[\<ostream>](../standard-library/ostream.md)
