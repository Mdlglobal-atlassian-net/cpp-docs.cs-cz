---
title: '&lt;funkce&gt; ostream'
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
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447197"
---
# <a name="ltostreamgt-functions"></a>&lt;funkce&gt; ostream

Jedná se o funkce globálních šablon definované v &lt;ostream&gt;. Pro členské funkce si přečtěte dokumentaci ke [třídě basic_ostream](basic-ostream-class.md) .

||||
|-|-|-|
|[endl](#endl)|[přípon](#ends)|[zaznamenány](#flush)|
|[swap](#swap)|

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

*Recenzent*\
Vlastnosti znaků.

### <a name="return-value"></a>Návratová hodnota

Objekt typu **basic_ostream**.

### <a name="remarks"></a>Poznámky

Manipulátor volá *OSTR*. [Vložit](../standard-library/basic-ostream-class.md#put) (*OSTR*. [rozšířit](../standard-library/basic-ios-class.md#widen) (' \n ')) a potom zavolá *OSTR*. [](../standard-library/basic-ostream-class.md#flush)vyprázdnit. Vrátí *OSTR*.

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

*Recenzent*\
Vlastnosti znaků.

### <a name="return-value"></a>Návratová hodnota

Objekt typu `basic_ostream`.

### <a name="remarks"></a>Poznámky

Manipulátor volá *OSTR*. [Vložit](../standard-library/basic-ostream-class.md#put) (*Elem*(\ 0)). Vrátí *OSTR*.

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

*Recenzent*\
Vlastnosti znaků.

### <a name="return-value"></a>Návratová hodnota

Objekt typu `basic_ostream`.

### <a name="remarks"></a>Poznámky

Manipulátor volá *OSTR*. [](../standard-library/basic-ostream-class.md#flush)vyprázdnit. Vrátí *OSTR*.

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

*Recenzent*\
Vlastnosti znaků.

*zbývá*\
Odkaz l-hodnoty na `basic_ostream` objekt.

*Kliknutím*\
Odkaz l-hodnoty na `basic_ostream` objekt.

### <a name="remarks"></a>Poznámky

Funkce `swap` šablony se spustí `left.swap(right)`.

## <a name="see-also"></a>Viz také:

[\<ostream >](../standard-library/ostream.md)
