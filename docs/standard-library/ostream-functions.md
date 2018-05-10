---
title: '&lt;ostream –&gt; funkce | Microsoft Docs'
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
ms.openlocfilehash: e85ce2728aaaa8ae9b23067bfb1dcbb3ff2db7d0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ltostreamgt-functions"></a>&lt;ostream –&gt; funkce

Toto jsou globální šablona funkce definované v &lt;ostream –&gt;. Členské funkce, najdete v článku [basic_ostream – třída](basic-ostream-class.md) dokumentaci.

||||
|-|-|-|
|[endl](#endl)|[ukončení](#ends)|[Vyprázdnění](#flush)|
|[Swap](#swap)|

## <a name="endl"></a>endl

Ukončí řádku a vyprázdní vyrovnávací paměť.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametry

*Elem* typ elementu.

*Ostr* objekt typu **basic_ostream**.

*Tr* znak vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Objekt typu **basic_ostream**.

### <a name="remarks"></a>Poznámky

Volání manipulator *Ostr*.[ uveďte](../standard-library/basic-ostream-class.md#put)(*Ostr*.[ widen](../standard-library/basic-ios-class.md#widen)(\n)) a potom zavolá *Ostr*.[ vyprázdnění](../standard-library/basic-ostream-class.md#flush). Vrátí *Ostr*.

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

*Elem* typ elementu.

*Ostr* objekt typu **basic_ostream**.

*Tr* znak vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Objekt typu **basic_ostream**.

### <a name="remarks"></a>Poznámky

Volání manipulator *Ostr*.[ uveďte](../standard-library/basic-ostream-class.md#put)(*Elem*(\0)). Vrátí *Ostr*.

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

*Elem* typ elementu.

*Ostr* objekt typu **basic_ostream**.

*Tr* znak vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Objekt typu **basic_ostream**.

### <a name="remarks"></a>Poznámky

Volání manipulator *Ostr*.[ vyprázdnění](../standard-library/basic-ostream-class.md#flush). Vrátí *Ostr*.

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

Výměny hodnoty dva **basic_ostream** objekty.

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parametry

*Elem* typ elementu.

*Tr* znak vlastnosti.

*levé* lvalue odkaz na **basic_ostream** objektu.

*pravé* lvalue odkaz na **basic_ostream** objektu.

### <a name="remarks"></a>Poznámky

Funkce šablony **swap** provede `left.swap(right)`.

## <a name="see-also"></a>Viz také

[\<ostream – >](../standard-library/ostream.md)
