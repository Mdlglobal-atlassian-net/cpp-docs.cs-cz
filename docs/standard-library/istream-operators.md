---
title: '&lt;IStream&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 05b10c27d8e0cf4c0300bb307d8b7ceda43ddb2f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474084"
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

*ch*<br/>
Znak.

*Istr*<br/>
Datový proud.

*str*<br/>
Řetězec.

*Val*<br/>
Typ.

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

**Poznámka k zabezpečení** řetězec zakončený hodnotou null se extrahují z vstupního datového proudu nesmí překročit velikost cílové vyrovnávací paměti *str*. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

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

Vrátí `Istr >> ( char * ) str`.

Funkce šablony:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

Vrátí `Istr >> ( char& ) Ch`.

Funkce šablony:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

Vrátí `Istr >> ( char * ) str`.

Funkce šablony:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

Vrátí `Istr >> ( char& ) Ch`.

Funkce šablony:

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

Vrátí `Istr >> val` (a převede odkaz rvalue na `Istr` na lvalue v procesu).

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
