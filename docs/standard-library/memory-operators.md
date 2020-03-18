---
title: operátory&gt; &lt;paměti
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
ms.openlocfilehash: 661f1bb4c0f5734d88dd23f73c69b362f59a76c2
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419929"
---
# <a name="ltmemorygt-operators"></a>operátory&gt; &lt;paměti

## <a name="op_neq"></a>! = – operátor

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

*levý*\
Jeden z objektů, který má být testován pro nerovnost.

*pravé*\
Jeden z objektů, který má být testován pro nerovnost.

*Ty1*\
Typ řízený levým sdíleným ukazatelem.

*Ty2*\
Typ řízený správným sdíleným ukazatelem.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud objekty nejsou stejné; **false** , pokud jsou objekty stejné.

### <a name="remarks"></a>Poznámky

První operátor šablony vrátí hodnotu false. (Všechna výchozí přidělování jsou shodná.)

Druhá a třetí operátor šablony vrací `!(left == right)`.

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

## <a name="op_eq_eq"></a>operator = = – operátor

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

*levý*\
Jeden z objektů, který má být testován pro rovnost.

*pravé*\
Jeden z objektů, který má být testován pro rovnost.

*Ty1*\
Typ řízený levým sdíleným ukazatelem.

*Ty2*\
Typ řízený správným sdíleným ukazatelem.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou objekty stejné, **false** , pokud objekty nejsou stejné.

### <a name="remarks"></a>Poznámky

První operátor šablony vrátí hodnotu true. (Všechna výchozí přidělování jsou shodná.)

Druhá a třetí operátor šablony vrací `left.get() ==  right.get()`.

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

## <a name="op_gt_eq"></a>operátor&gt;=

Testy pro jeden objekt, který je větší nebo roven druhému objektu.

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

*levý*\
Jeden z objektů, které mají být porovnány.

*pravé*\
Jeden z objektů, které mají být porovnány.

*Ty1*\
Typ řízený levým sdíleným ukazatelem.

*Ty2*\
Typ řízený správným sdíleným ukazatelem.

### <a name="remarks"></a>Poznámky

Operátory šablony vracejí `left.get() >= right.get()`.

## <a name="op_lt"></a>operátor&lt;

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

*levý*\
Jeden z objektů, které mají být porovnány.

*pravé*\
Jeden z objektů, které mají být porovnány.

*Ty1*\
Typ řízený levým ukazatelem.

*Ty2*\
Typ řízený pravým ukazatelem.

## <a name="op_lt_eq"></a>operátor&lt;=

Testy pro jeden objekt, který je menší nebo roven druhému objektu.

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

*levý*\
Jeden z objektů, které mají být porovnány.

*pravé*\
Jeden z objektů, které mají být porovnány.

*Ty1*\
Typ řízený levým sdíleným ukazatelem.

*Ty2*\
Typ řízený správným sdíleným ukazatelem.

### <a name="remarks"></a>Poznámky

Operátory šablony vracejí `left.get() <= right.get()`

## <a name="op_gt"></a>operátor&gt;

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

*levý*\
Jeden z objektů, které mají být porovnány.

*pravé*\
Jeden z objektů, které mají být porovnány.

*Ty1*\
Typ řízený levým sdíleným ukazatelem.

*Ty2*\
Typ řízený správným sdíleným ukazatelem.

## <a name="op_lt_lt"></a>operátor&lt;&lt;

Zapíše sdílený ukazatel do datového proudu.

```cpp
template <class Elem, class Tr, class Ty>
std::basic_ostream<Elem, Tr>& operator<<(std::basic_ostream<Elem, Tr>& out,
    shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>Parametry

*Elem*\
Typ elementu streamu.

*Tr*\
Zadejte vlastnosti prvku datového proudu.

*Ty*\
Typ řízený sdíleným ukazatelem.

*\*
Výstupní datový proud

\ *SP*
Sdílený ukazatel.

### <a name="remarks"></a>Poznámky

Funkce šablony vrací `out << sp.get()`.

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
