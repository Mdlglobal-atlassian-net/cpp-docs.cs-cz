---
title: '&lt;operátory&gt; IStream'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 5ac5c61488530f99cdad38ca1bfca365b6ac0f8c
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890178"
---
# <a name="ltistreamgt-operators"></a>&lt;operátory&gt; IStream

## <a name="op_gt_gt"></a>operátor &gt; &gt;

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

*Ch* \
Znak.

*Istr*\
Datový proud.

\ *str*
Řetězec.

\ *Val*
Typ.

### <a name="return-value"></a>Návratová hodnota

Datový proud

### <a name="remarks"></a>Poznámky

Třída `basic_istream` také definuje několik operátorů extrakce. Další informace naleznete v tématu [basic_istream:: operator > >](../standard-library/basic-istream-class.md#op_gt_gt).

Šablona funkce:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

extrahuje až `N - 1` prvky a uloží je v poli začínajícím na *str*. Pokud je `Istr.`[Šířka](../standard-library/ios-base-class.md#width) větší než nula, *N* `Istr.width`; v opačném případě je to velikost největší pole `Elem`, které lze deklarovat. Funkce vždy ukládá hodnotu `Elem()` po všech extrahovaných prvcích, které ukládá. Extrakce se zastaví na konci souboru, na znaku s hodnotou `Elem(0)` (která není extrahována) nebo na jakémkoli elementu (který není extrahován), který by byl zahozen pomocí [WS](../standard-library/istream-functions.md#ws). Pokud funkce neextrahuje žádné prvky, volá `Istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. V každém případě volá `Istr.width(0)` a vrátí *ISTR*.

**Poznámka k zabezpečení** Řetězec zakončený hodnotou null ze vstupního datového proudu nesmí překročit velikost cílového *str*vyrovnávací paměti. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Šablona funkce:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

extrahuje element, pokud je to možné, a uloží ho do *ch*. V opačném případě volá `is.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. V každém případě vrátí *ISTR*.

Šablona funkce:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

Vrátí `Istr >> ( char * ) str`.

Šablona funkce:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

Vrátí `Istr >> ( char& ) Ch`.

Šablona funkce:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

Vrátí `Istr >> ( char * ) str`.

Šablona funkce:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

Vrátí `Istr >> ( char& ) Ch`.

Šablona funkce:

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

[\<istream >](../standard-library/istream.md)
