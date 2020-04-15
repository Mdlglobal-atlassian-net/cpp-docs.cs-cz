---
title: '&lt;provozovatelé&gt; istreamu'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 3b9521fde1b5a03389bfc1ad3e35fa407d9d6ac0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363042"
---
# <a name="ltistreamgt-operators"></a>&lt;provozovatelé&gt; istreamu

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a>Operátor&gt;&gt;

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

*Ch*\
Postava.

*Istr*\
Potok.

*Str*\
Řetězec.

*Val*\
Typ.

### <a name="return-value"></a>Návratová hodnota

Datový proud

### <a name="remarks"></a>Poznámky

Třída `basic_istream` také definuje několik operátorů extrakce. Další informace naleznete [v tématu basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt).

Šablona funkce:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

extrahuje `N - 1` až do prvků a ukládá je do pole od *str*. Pokud `Istr.`je [šířka](../standard-library/ios-base-class.md#width) *N* větší `Istr.width`než nula, N je ; jinak je velikost největší pole, `Elem` které lze deklarovat. Funkce vždy ukládá `Elem()` hodnotu za všechny extrahované prvky, které ukládá. Extrakce se zastaví brzy na konci `Elem(0)` souboru, na znak s hodnotou (která není extrahována) nebo na jakémkoli prvku (který není extrahován), který by byl zahozen [ws](../standard-library/istream-functions.md#ws). Pokud funkce extrahuje žádné `Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`prvky, volá . V každém případě `Istr.width(0)` volá a vrací *Istr*.

**Poznámka k zabezpečení** Řetězec ukončený hodnotou null, který je extrahován ze vstupního datového proudu, nesmí překročit velikost cílové vyrovnávací paměti *str*. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Šablona funkce:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

extrahuje prvek, pokud je to možné, a uloží jej v *Ch*. V opačném `is.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`případě volá . V každém případě se vrátí *Istr*.

Šablona funkce:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

vrátí `Istr >> ( char * ) str`.

Šablona funkce:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

vrátí `Istr >> ( char& ) Ch`.

Šablona funkce:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

vrátí `Istr >> ( char * ) str`.

Šablona funkce:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

vrátí `Istr >> ( char& ) Ch`.

Šablona funkce:

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

vrátí `Istr >> val` (a převede odkaz `Istr` rvalue na lvalue v procesu).

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

## <a name="see-also"></a>Viz také

[\<istream>](../standard-library/istream.md)
