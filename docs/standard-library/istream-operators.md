---
title: '&lt;IStream&gt; operátory | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- istream/std::operator&gt;&gt;
dev_langs:
- C++
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60ec526dd8874529b60558f7131c31f0bf4a2d3b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961110"
---
# <a name="ltistreamgt-operators"></a>&lt;IStream&gt; operátory

## <a name="op_gt_gt"></a>  – Operátor&gt;&gt;

Extrahuje z datového proudu znaků a řetězce.

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem* str);

template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char& Ch);

template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

### <a name="parameters"></a>Parametry

*Ch* znak.

*Istr* datového proudu.

*Str* řetězec.

*Val* typu.

### <a name="return-value"></a>Návratová hodnota

Datový proud

### <a name="remarks"></a>Poznámky

`basic_istream` Třída také definuje několik operátorů extrakce. Další informace najdete v tématu [basic_istream::operator >>](../standard-library/basic-istream-class.md#op_gt_gt).

Funkce šablony:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

Extrahuje až *N* + 1 prvků a ukládá je do pole, počínaje _ *Str*. Pokud `Istr`. [Šířka](../standard-library/ios-base-class.md#width) je větší než nula, *N* je `Istr`. **Šířka**; v opačném případě je velikost největšího pole `Elem` , které mohou být deklarovány. Funkce vždy ukládá hodnotu `Elem()` po žádné elementy, které je uložený. Extrakce zastaví již v rané fázi na konec souboru, na znak s hodnotou **Elem**(0) (které se extrahují), nebo na libovolný prvek (který se extrahuje), které by být zrušeny [ws](../standard-library/istream-functions.md#ws). Pokud funkci extrahuje žádné elementy, zavolá `Istr`. [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). V každém případě volá `Istr`. **Šířka**(0) a vrátí *Istr*.

**Poznámka k zabezpečení** řetězec zakončený hodnotou null se extrahují z vstupního datového proudu nesmí překročit velikost cílové vyrovnávací paměti *str*. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).

Funkce šablony:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

Extrahuje element, pokud je možné a uloží jej do *Ch*. V opačném případě volá **je**. [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). V každém případě vrátí *Istr*.

Funkce šablony:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

Vrátí `Istr` >> ( `char` **\***) `str`.

Funkce šablony:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

Vrátí `Istr` >> ( **char &**) `Ch`.

Funkce šablony:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

Vrátí `Istr` >> ( **char \*** ) `str`.

Funkce šablony:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

Vrátí `Istr` >> ( **char &**) `Ch`.

Funkce šablony:

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

Vrátí `Istr` `>>` `val` (a převede `rvalue reference` k `Istr` do `lvalue` v procesu).

### <a name="example"></a>Příklad

```cpp
// istream_op_extract.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   ws( cin );
   char c[10];

   cin.width( 9 );
   cin >> c;
   cout << c << endl;
}
```

## <a name="see-also"></a>Viz také:

[\<IStream >](../standard-library/istream.md)<br/>
