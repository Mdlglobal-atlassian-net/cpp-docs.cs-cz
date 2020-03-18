---
title: funkce &lt;ostream&gt;
ms.date: 11/04/2016
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 8d93e46b0323058d93c6d0bd8c1ee566998aef61
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419705"
---
# <a name="ltostreamgt-functions"></a>funkce &lt;ostream&gt;

Jedná se o funkce globálních šablon definované v &lt;ostream&gt;. Členské funkce naleznete v dokumentaci [třídy basic_ostream](basic-ostream-class.md) .

||||
|-|-|-|
|[endl](#endl)|[přípon](#ends)|[zaznamenány](#flush)|
|[adresu](#swap)|

## <a name="endl"></a>endl

Ukončí řádek a vyprázdní vyrovnávací paměť.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametry

*Elem*\
Typ elementu.

*Ostr*\
Objekt typu **basic_ostream**.

*Tr*\
Vlastnosti znaků.

### <a name="return-value"></a>Návratová hodnota

Objekt typu **basic_ostream**.

### <a name="remarks"></a>Poznámky

Manipulátor volá *OSTR*. [Put](../standard-library/basic-ostream-class.md#put)(*OSTR*.[ rozšířit](../standard-library/basic-ios-class.md#widen)(' \n ')) a potom zavolá *OSTR*. [vyprázdnit](../standard-library/basic-ostream-class.md#flush). Vrátí *OSTR*.

### <a name="example"></a>Příklad

```cpp
// ostream_endl.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << endl;
}
```

```Output
testing
```

## <a name="ends"></a>zakončení

Ukončí řetězec.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& ends(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametry

*Elem*\
Typ elementu.

*Ostr*\
Objekt typu `basic_ostream`.

*Tr*\
Vlastnosti znaků.

### <a name="return-value"></a>Návratová hodnota

Objekt typu `basic_ostream`.

### <a name="remarks"></a>Poznámky

Manipulátor volá *OSTR*. [Put](../standard-library/basic-ostream-class.md#put)(*elem*(' \ 0 ')). Vrátí *OSTR*.

### <a name="example"></a>Příklad

```cpp
// ostream_ends.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "a";
   cout << "b" << ends;
   cout << "c" << endl;
}
```

```Output
ab c
```

## <a name="flush"></a>flush

Vyprázdní vyrovnávací paměť.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& flush(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametry

*Elem*\
Typ elementu.

*Ostr*\
Objekt typu `basic_ostream`.

*Tr*\
Vlastnosti znaků.

### <a name="return-value"></a>Návratová hodnota

Objekt typu `basic_ostream`.

### <a name="remarks"></a>Poznámky

Manipulátor volá *OSTR*. [vyprázdnit](../standard-library/basic-ostream-class.md#flush). Vrátí *OSTR*.

### <a name="example"></a>Příklad

```cpp
// ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << flush;
}
```

```Output
testing
```

## <a name="swap"></a>swap

Vyměňuje hodnoty dvou `basic_ostream` objektů.

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parametry

*Elem*\
Typ elementu.

*Tr*\
Vlastnosti znaků.

*levý*\
Odkaz l-hodnoty na objekt `basic_ostream`.

*pravé*\
Odkaz l-hodnoty na objekt `basic_ostream`.

### <a name="remarks"></a>Poznámky

Funkce šablony `swap` spouští `left.swap(right)`.

## <a name="see-also"></a>Viz také

[\<ostream >](../standard-library/ostream.md)
