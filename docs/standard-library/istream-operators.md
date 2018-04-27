---
title: '&lt;IStream on Request&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- istream/std::operator&gt;&gt;
dev_langs:
- C++
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0b1508ff4bd27470fdcb14945bc9ad3317a30b8
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltistreamgt-operators"></a>&lt;IStream on Request&gt; operátory

## <a name="op_gt_gt"></a>  Operátor&gt;&gt;

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

`Ch` Znak.

`Istr` Datový proud.

`str` Řetězec.

`val` Typ.

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

Extrahuje až *N* – 1 elementy a ukládá je do pole počínaje _ *Str*. Pokud `Istr`. [Šířka](../standard-library/ios-base-class.md#width) je větší než nula, *N* je `Istr`. **Šířka**, jinak je velikost největší pole **Elem** , lze deklarovat. Funkce vždy ukládá hodnotu **Elem()** po žádné extrahování elementy ukládá. Extrakce zastaví již v rané fázi na konci souboru, na znak s hodnotou **Elem**(0) (který není extrahovat), nebo u libovolného elementu (která není extrahována), které by být zrušeny [ws](../standard-library/istream-functions.md#ws). Pokud funkci extrahuje žádné elementy, zavolá `Istr`. [setstate –](../standard-library/basic-ios-class.md#setstate)( **failbit**). V každém případě volá `Istr`. **Šířka**(0) a vrátí `Istr`.

**Poznámka k zabezpečení** řetězce ukončené hodnotou null se extrahují z vstupního datového proudu nesmí být delší než velikost vyrovnávací paměti cílový `str`. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).

Funkce šablony:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

Extrahuje elementu, pokud je možné a uloží jej do `Ch`. Jinak zavolá **je**. [setstate –](../standard-library/basic-ios-class.md#setstate)( **failbit**). V každém případě vrátí `Istr`.

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

Vrátí `Istr` `>>` `val` (a převede `rvalue reference` k `Istr` k `lvalue` v procesu).

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

[\<IStream on Request >](../standard-library/istream.md)<br/>
