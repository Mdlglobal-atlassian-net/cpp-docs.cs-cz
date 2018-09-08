---
title: '&lt;ostream&gt; functions | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 494c750ec80000ef9090824e0436f6e443593847
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107604"
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; funkce

Toto jsou globální šablona funkce definované v &lt;ostream&gt;. Členské funkce, najdete v článku [basic_ostream – třída](basic-ostream-class.md) dokumentaci.

||||
|-|-|-|
|[endl](#endl)|[končí](#ends)|[Vyprázdnění](#flush)|
|[Prohození](#swap)|

## <a name="endl"></a>endl

Ukončení řádku a vyprázdní vyrovnávací paměť.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Typ elementu.

*Ostr*<br/>
Objekt typu **basic_ostream –**.

*tr*<br/>
Vlastnosti znaků.

### <a name="return-value"></a>Návratová hodnota

Objekt typu **basic_ostream –**.

### <a name="remarks"></a>Poznámky

Volání manipulátor *Ostr*.[ Vložit](../standard-library/basic-ostream-class.md#put)(*Ostr*.[ rozšířit](../standard-library/basic-ios-class.md#widen)('\n')) a pak zavolá *Ostr*.[ vyprázdnění](../standard-library/basic-ostream-class.md#flush). Vrátí *Ostr*.

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

*Elem*<br/>
Typ elementu.

*Ostr*<br/>
Objekt typu `basic_ostream`.

*tr*<br/>
Vlastnosti znaků.

### <a name="return-value"></a>Návratová hodnota

Objekt typu `basic_ostream`.

### <a name="remarks"></a>Poznámky

Volání manipulátor *Ostr*.[ Vložit](../standard-library/basic-ostream-class.md#put)(*Elem*('\0')). Vrátí *Ostr*.

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

*Elem*<br/>
Typ elementu.

*Ostr*<br/>
Objekt typu `basic_ostream`.

*tr*<br/>
Vlastnosti znaků.

### <a name="return-value"></a>Návratová hodnota

Objekt typu `basic_ostream`.

### <a name="remarks"></a>Poznámky

Volání manipulátor *Ostr*.[ vyprázdnění](../standard-library/basic-ostream-class.md#flush). Vrátí *Ostr*.

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

Vymění hodnoty dvou `basic_ostream` objekty.

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Typ elementu.

*tr*<br/>
Vlastnosti znaků.

*doleva*<br/>
Odkaz na lvalue k `basic_ostream` objektu.

*doprava*<br/>
Odkaz na lvalue k `basic_ostream` objektu.

### <a name="remarks"></a>Poznámky

Funkce šablony `swap` spustí `left.swap(right)`.

## <a name="see-also"></a>Viz také:

[\<ostream >](../standard-library/ostream.md)
