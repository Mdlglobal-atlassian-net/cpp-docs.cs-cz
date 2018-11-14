---
title: '&lt;paměť&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- memory/std::operator!=
- memory/std::operator>
- memory/std::operator>=
- memory/std::operator<
- memory/std::operator<=
- memory/std::operator<<
- memory/std::operator==
ms.assetid: 257e3ba9-c4c2-4ae8-9b11-b156ba9c28de
ms.openlocfilehash: ca1412efb4d095ef9a371b3739d4c282683821dc
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519312"
---
# <a name="ltmemorygt-operators"></a>&lt;paměť&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[– Operátor&gt;](#op_gt)|[– Operátor&gt;=](#op_gt_eq)|
|[– Operátor&lt;](#op_lt)|[– Operátor&lt;&lt;](#op_lt_lt)|[– Operátor&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  Operator! =

Testy pro nerovnost mezi objekty.

```cpp
template <class Type, class Other>
bool operator!=(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class T, class Del1, class U, class Del2>
bool operator!=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator!=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Jeden z objektů má být testována nerovnost.

*doprava*<br/>
Jeden z objektů má být testována nerovnost.

*Ty1*<br/>
Typ řízený levé sdílený ukazatel.

*Ty2*<br/>
Typ řízený správné sdílený ukazatel.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud objekty nejsou stejné; **false** Pokud jsou objekty rovnocenné.

### <a name="remarks"></a>Poznámky

První šablona operátor vrátí hodnotu false. (Všechny výchozí alokátorů jsou si rovny.)

Druhý a třetí šablony operátory vrací `!(left == right)`.

### <a name="example"></a>Příklad

```cpp
// memory_op_me.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<double> Alloc;
   vector <char>:: allocator_type v1Alloc;

   if ( Alloc != v1Alloc )
      cout << "The allocator objects Alloc & v1Alloc not are equal."
           << endl;
   else
      cout << "The allocator objects Alloc & v1Alloc are equal."
           << endl;
}
```

```Output
The allocator objects Alloc & v1Alloc are equal.
```

### <a name="example"></a>Příklad

```cpp
// std__memory__operator_ne.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 != sp0 == " << std::boolalpha
        << (sp0 != sp0) << std::endl;
    std::cout << "sp0 != sp1 == " << std::boolalpha
        << (sp0 != sp1) << std::endl;

    return (0);
    }
```

```Output
sp0 != sp0 == false
sp0 != sp1 == true
```

## <a name="op_eq_eq"></a>  Operator ==

Testy pro rovnost mezi objekty.

```cpp
template <class Type, class Other>
bool operator==(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class Ty1, class Del1, class Ty2, class Del2>
bool operator==(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2, Del2>& right);

template <class Ty1, class Ty2>
bool operator==(
    const shared_ptr<Ty1>& left;,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Jeden z objektů, které chcete testovat rovnost.

*doprava*<br/>
Jeden z objektů, které chcete testovat rovnost.

*Ty1*<br/>
Typ řízený levé sdílený ukazatel.

*Ty2*<br/>
Typ řízený správné sdílený ukazatel.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud se objekty rovnají, **false** Pokud objekty nejsou stejné.

### <a name="remarks"></a>Poznámky

První šablona operátor vrátí hodnotu true. (Všechny výchozí alokátorů jsou si rovny.)

Druhý a třetí šablony operátory vrací `left.get() ==  right.get()`.

### <a name="example"></a>Příklad

```cpp
// memory_op_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<char> Alloc;
   vector <int>:: allocator_type v1Alloc;

   allocator<char> cAlloc(Alloc);
   allocator<int> cv1Alloc(v1Alloc);

   if ( cv1Alloc == v1Alloc )
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."
           << endl;

   if ( cAlloc == Alloc )
      cout << "The allocator objects cAlloc & Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cAlloc & Alloc are not equal."
           << endl;
}
```

```Output
The allocator objects cv1Alloc & v1Alloc are equal.
The allocator objects cAlloc & Alloc are equal.
```

### <a name="example"></a>Příklad

```cpp
// std__memory__operator_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 == sp0 == " << std::boolalpha
        << (sp0 == sp0) << std::endl;
    std::cout << "sp0 == sp1 == " << std::boolalpha
        << (sp0 == sp1) << std::endl;

    return (0);
    }
```

```Output
sp0 == sp0 == true
sp0 == sp1 == false
```

## <a name="op_gt_eq"></a>  – Operátor&gt;=

Testy pro jeden objekt, který je větší než nebo roven druhému objektu.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator>=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U, Del2>& right);

template <class Ty1, class Ty2>
bool operator>=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Jeden z objektů, který se má porovnat.

*doprava*<br/>
Jeden z objektů, který se má porovnat.

*Ty1*<br/>
Typ řízený levé sdílený ukazatel.

*Ty2*<br/>
Typ řízený správné sdílený ukazatel.

### <a name="remarks"></a>Poznámky

Šablona operátory vrací `left.get() >= right.get()`.

## <a name="op_lt"></a>  – Operátor&lt;

Testy pro jeden objekt, který je menší než druhý objekt.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Jeden z objektů, který se má porovnat.

*doprava*<br/>
Jeden z objektů, který se má porovnat.

*Ty1*<br/>
Typ řízený ukazatelem vlevo.

*Ty2*<br/>
Typ řízený ukazatelem správné.

## <a name="op_lt_eq"></a>  – Operátor&lt;=

Testy pro jeden objekt, který je menší než nebo roven druhému objektu.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Jeden z objektů, který se má porovnat.

*doprava*<br/>
Jeden z objektů, který se má porovnat.

*Ty1*<br/>
Typ řízený levé sdílený ukazatel.

*Ty2*<br/>
Typ řízený správné sdílený ukazatel.

### <a name="remarks"></a>Poznámky

Šablona operátory vrací `left.get() <= right.get()`

## <a name="op_gt"></a>  – Operátor&gt;

Testy pro jeden objekt, který je větší než druhý objekt.

```cpp
template <class Ty1, class Del1, class Ty2, class Del2>
bool operator>(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2&, Del2gt;& right);

template <class Ty1, class Ty2>
bool operator>(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Jeden z objektů, který se má porovnat.

*doprava*<br/>
Jeden z objektů, který se má porovnat.

*Ty1*<br/>
Typ řízený levé sdílený ukazatel.

*Ty2*<br/>
Typ řízený správné sdílený ukazatel.

## <a name="op_lt_lt"></a>  – Operátor&lt;&lt;

Sdílený ukazatel zapíše do datového proudu.

```cpp
template <class Elem, class Tr, class Ty>
std::basic_ostream<Elem, Tr>& operator<<(std::basic_ostream<Elem, Tr>& out,
    shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Typ prvku datového proudu.

*tr*<br/>
Typ elementu vlastnosti datového proudu.

*Ty*<br/>
Typ řízený sdíleným ukazatelem.

*out*<br/>
Výstupní datový proud

*SP*<br/>
Sdílený ukazatel.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí `out << sp.get()`.

### <a name="example"></a>Příklad

```cpp
// std__memory__operator_sl.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "sp0 == " << sp0 << " (varies)" << std::endl;

    return (0);
    }
```

```Output
sp0 == 3f3040 (varies)
```

## <a name="see-also"></a>Viz také:

[\<paměť >](../standard-library/memory.md)<br/>
