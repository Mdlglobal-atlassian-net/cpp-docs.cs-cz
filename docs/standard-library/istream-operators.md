---
title: '&lt;IStream&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: c10692194c80051b10ecbe776c7d23a03860d508
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447788"
---
# <a name="ltistreamgt-operators"></a>&lt;IStream&gt; operátory

## <a name="op_gt_gt"></a>podnikatel&gt;&gt;

Extrahuje znaky a řetězce z datového proudu.

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

*Zvolte*\
Znak.

*Istr*\
Datový proud.

*str*\
Řetězec.

*počítává*\
Typ.

### <a name="return-value"></a>Návratová hodnota

Datový proud

### <a name="remarks"></a>Poznámky

`basic_istream` Třída také definuje několik operátorů extrakce. Další informace naleznete v tématu [basic_istream:: operator > >](../standard-library/basic-istream-class.md#op_gt_gt).

Funkce šablony:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

extrahuje do *N* -1 prvků a ukládá je v poli začínajícím na _ *str*. If `Istr`. [Šířka](../standard-library/ios-base-class.md#width) je větší než nula, *N* je `Istr`. **Šířka**; v opačném případě je to velikost největšího pole `Elem` , které lze deklarovat. Funkce vždy ukládá hodnotu `Elem()` po všech extrahovaných prvcích, které ukládá. Extrakce se zastaví na konci souboru na znaku s hodnotou **elem**(0) (která není extrahována) nebo na jakémkoli elementu (který není extrahován), který by byl zahozen pomocí [WS](../standard-library/istream-functions.md#ws). Pokud funkce neextrahuje žádné elementy, volá `Istr`. [setstate](../standard-library/basic-ios-class.md#setstate) (**failbit**). V každém případě volá `Istr`. **Šířka** (0) a vrátí *ISTR*.

**Poznámka k zabezpečení** Řetězec zakončený hodnotou null ze vstupního datového proudu nesmí překročit velikost cílového *str*vyrovnávací paměti. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

Funkce šablony:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

extrahuje element, pokud je to možné, a uloží ho do *ch*. V opačném případě **volá.** [setstate](../standard-library/basic-ios-class.md#setstate) ( **failbit**). V každém případě vrátí *ISTR*.

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

Vrátí `Istr >> val` (a převede odkaz rvalue na `Istr` lvalue v procesu).

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

[\<IStream >](../standard-library/istream.md)
