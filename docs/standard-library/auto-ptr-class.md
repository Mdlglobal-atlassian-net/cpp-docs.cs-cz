---
title: auto_ptr – třída
ms.date: 11/04/2016
f1_keywords:
- memory/std::auto_ptr
- memory/std::auto_ptr::element_type
- memory/std::auto_ptr::get
- memory/std::auto_ptr::release
- memory/std::auto_ptr::reset
helpviewer_keywords:
- std::auto_ptr [C++]
- std::auto_ptr [C++], element_type
- std::auto_ptr [C++], get
- std::auto_ptr [C++], release
- std::auto_ptr [C++], reset
ms.assetid: 7f9108b6-9eb3-4634-b615-cf7aa814f23b
ms.openlocfilehash: 6b429b0e5c734f81216c988e372c02021528cffd
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690031"
---
# <a name="auto_ptr-class"></a>auto_ptr – třída

Zalomí inteligentní ukazatel kolem prostředku, který zajišťuje, že je prostředek zničen automaticky, když ovládací prvek opustí blok.

@No__t_1 třída s možností pří`unique_ptr` nahrazuje. Další informace naleznete v tématu [Třída unique_ptr](../standard-library/unique-ptr-class.md).

Další informace o `throw()` a zpracování výjimek naleznete v tématu [Specifikace výjimek (throw)](../cpp/exception-specifications-throw-cpp.md).

## <a name="syntax"></a>Syntaxe

```cpp
class auto_ptr {
    typedef Type element_type;
    explicit auto_ptr(Type* ptr = 0) throw();
    auto_ptr(auto_ptr<Type>& right) throw()
        ;
    template <class Other>
    operator auto_ptr<Other>() throw();
    template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
    template <class Other>
    auto_ptr(auto_ptr<Other>& right);
    auto_ptr<Type>& operator=(auto_ptr<Type>& right);
    ~auto_ptr();
    Type& operator*() const throw();
    Type * operator->()const throw();
    Type *get() const throw();
    Type *release()throw();
    void reset(Type* ptr = 0);
};
```

### <a name="parameters"></a>Parametry

*pravé* \
@No__t_0, ze kterého se má získat existující prostředek

\ *PTR*
Ukazatel, který je určen k nahrazení uloženého ukazatele.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje inteligentní ukazatel nazvaný `auto_ptr` k přidělenému objektu. Ukazatel musí mít buď hodnotu null, nebo určovat objekt přidělený **novým**. @No__t_0 přenáší vlastnictví, pokud je jeho uložená hodnota přiřazena k jinému objektu. (Po přenosu s nulovým ukazatelem nahradí uloženou hodnotu.) Destruktor pro `auto_ptr<Type>` odstraní přidělený objekt. @No__t_0 zajišťuje, aby byl přidělený objekt automaticky odstraněn, když ovládací prvek opustí blok, a to i přes vyvolanou výjimku. Neměli byste vytvářet dva objekty `auto_ptr<Type>`, které vlastní stejný objekt.

Objekt `auto_ptr<Type>` můžete předat hodnotou jako argument volání funkce. @No__t_0 nemůže být elementem žádného standardního kontejneru knihovny. Nemůžete spolehlivě spravovat sekvenci `auto_ptr<Type>` objektů se C++ standardním kontejnerem knihovny.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[auto_ptr](#auto_ptr)|Konstruktor pro objekty typu `auto_ptr`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|Typ je synonymum pro parametr šablony `Type`.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[get](#get)|Členská funkce vrátí uložený ukazatel `myptr`.|
|[předběžné](#release)|Člen nahradí uložený ukazatel `myptr` ukazatelem s hodnotou null a vrátí dříve uložený ukazatel.|
|[nové](#reset)|Členská funkce vyhodnotí výraz `delete myptr`, ale pouze v případě, že se hodnota uloženého ukazatele `myptr` změní v důsledku volání funkce. Pak nahradí uložený ukazatel pomocí *PTR*.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_eq)|Operátor přiřazení, který přenáší vlastnictví z jednoho objektu `auto_ptr` do jiného.|
|[podnikatel](#op_star)|Operátor přesměrování pro objekty typu `auto_ptr`.|
|[operátor->](#op_arrow)|Operátor pro povolení přístupu členů|
|[auto_ptr – operátor \<Other >](#op_auto_ptr_lt_other_gt)|Přetypování z jednoho druhu `auto_ptr` na jiný typ `auto_ptr`.|
|[auto_ptr_ref – operátor \<Other >](#op_auto_ptr_ref_lt_other_gt)|Přetypování z `auto_ptr` na `auto_ptr_ref`.|

### <a name="auto_ptr"></a>auto_ptr

Konstruktor pro objekty typu `auto_ptr`.

```cpp
explicit auto_ptr(Type* ptr  = 0) throw();

auto_ptr(auto_ptr<Type>& right) throw();

auto_ptr(auto _ptr_ref<Type> right) throw();

template <class Other>
auto _ptr(auto _ptr<Other>& right) throw();
```

#### <a name="parameters"></a>Parametry

\ *PTR*
Ukazatel na objekt, který `auto_ptr` zapouzdření.

*pravé* \
Objekt `auto_ptr`, který má být zkopírován konstruktorem.

#### <a name="remarks"></a>Poznámky

První konstruktor ukládá *PTR* do `myptr`, uložený ukazatel na přidělený objekt. Druhý konstruktor převádí vlastnictví ukazatele uloženého *vpravo*uložením *vpravo*. [vydání](#release) v `myptr`.

Třetí konstruktor se chová stejně jako druhý s tím rozdílem, že ukládá `right`. `ref`. `release` v `myptr`, kde `ref` je odkaz uložený v `right`.

Konstruktor šablony se chová stejně jako druhý konstruktor za předpokladu, že ukazatel na `Other` lze implicitně převést na ukazatel na `Type`.

#### <a name="example"></a>Příklad

```cpp
// auto_ptr_auto_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << endl;
      bIsConstructed = false;
   };
   Int &operator++( )
   {
      x++;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

void function ( auto_ptr<Int> &pi )
{
   ++( *pi );
   auto_ptr<Int> pi2( pi );
   ++( *pi2 );
   pi = pi2;
}

int main( )
{
   auto_ptr<Int> pi ( new Int( 5 ) );
   cout << pi->x << endl;
   function( pi );
   cout << pi->x << endl;
}
```

```Output
Constructing 00311AF8
5
7
Destructing 00311AF8
```

### <a name="element_type"></a>element_type

Typ je synonymum pro parametr šablony `Type`.

```cpp
typedef Type element  _type;
```

### <a name="get"></a>Čtěte

Členská funkce vrátí uložený ukazatel `myptr`.

```cpp
Type *get() const throw();
```

#### <a name="return-value"></a>Návratová hodnota

Uložený ukazatel `myptr`.

#### <a name="example"></a>Příklad

```cpp
// auto_ptr_get.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      x = i;
      cout << "Constructing " << ( void* )this  << " Value: " << x << endl;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << " Value: " << x << endl;
   };

   int x;

};

int main( )
{
   auto_ptr<Int> pi ( new Int( 5 ) );
   pi.reset( new Int( 6 ) );
   Int* pi2 = pi.get ( );
   Int* pi3 = pi.release ( );
   if (pi2 == pi3)
      cout << "pi2 == pi3" << endl;
   delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

### <a name="op_eq"></a>operátor =

Operátor přiřazení, který přenáší vlastnictví z jednoho objektu `auto_ptr` do jiného.

```cpp
template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```

#### <a name="parameters"></a>Parametry

*pravé* \
Objekt typu `auto_ptr`.

#### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt typu `auto_ptr<Type>`.

#### <a name="remarks"></a>Poznámky

Přiřazení vyhodnotí výraz `delete myptr`, ale pouze v případě, že se uložený ukazatel `myptr` změní v důsledku přiřazení. Pak přenáší vlastnictví ukazatele uloženého *vpravo*uložením *práva*. [vydání](#release) v `myptr`. Funkce vrátí __\*this__.

#### <a name="example"></a>Příklad

Příklad použití operátoru členu naleznete v tématu [auto_ptr](#auto_ptr).

### <a name="op_star"></a>podnikatel

Operátor přesměrování pro objekty typu `auto_ptr`.

```cpp
Type& operator*() const throw();
```

#### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt typu `Type`, který vlastní ukazatel.

#### <a name="remarks"></a>Poznámky

Operátor dereference vrací `*`[Get](#get). Proto nesmí mít uložený ukazatel hodnotu null.

#### <a name="example"></a>Příklad

Příklad použití členské funkce naleznete v tématu [auto_ptr](#auto_ptr).

### <a name="op_arrow"></a>operátor-&gt;

Operátor pro povolení přístupu členů

```cpp
Type * operator->() const throw();
```

#### <a name="return-value"></a>Návratová hodnota

Člen objektu, který `auto_ptr` vlastní.

#### <a name="remarks"></a>Poznámky

Operátor výběru vrátí příkaz [get](#get) `( )`, takže se výraz *AP* -> **člen** chová stejně jako ( *AP*. **Get**())-> **člen**, kde *ap* je objekt třídy `auto_ptr` \< **typ**>. Proto musí být uložený ukazatel null a `Type` musí být typu třída, struktura nebo sjednocení s členem `member`.

#### <a name="example"></a>Příklad

Příklad použití členské funkce naleznete v tématu [auto_ptr](#auto_ptr).

### <a name="op_auto_ptr_lt_other_gt"></a>auto_ptr – operátor &lt;Other &gt;

Přetypování z jednoho druhu `auto_ptr` na jiný typ `auto_ptr`.

```cpp
template <class Other>
operator auto _ptr<Other>() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Operátor přetypování typu vrátí `auto_ptr` \< **jiné**> ( **\*this**).

#### <a name="example"></a>Příklad

```cpp
// auto_ptr_op_auto_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;
int main()
{
   auto_ptr<int> pi ( new int( 5 ) );
   auto_ptr<const int> pc = ( auto_ptr<const int> )pi;
}
```

### <a name="op_auto_ptr_ref_lt_other_gt"></a>auto_ptr_ref – operátor &lt;Other &gt;

Přetypování z `auto_ptr` na `auto_ptr_ref`.

```cpp
template <class Other>
operator auto _ptr  _ref<Other>() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Operátor přetypování typu vrátí **auto_ptr_ref** \< **jiné**> ( **\*this**).

#### <a name="example"></a>Příklad

```cpp
// auto_ptr_op_auto_ptr_ref.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class C {
public:
    C(int _i) : m_i(_i) {
    }
    ~C() {
        cout << "~C:  " << m_i << "\n";
    }
    C &operator =(const int &x) {
        m_i = x;
        return *this;
    }
    int m_i;
};
void f(auto_ptr<C> arg) {
};
int main()
{
    const auto_ptr<C> ciap(new C(1));
    auto_ptr<C> iap(new C(2));

    // Error: this implies transfer of ownership of iap's pointer
    // f(ciap);
    f(iap); // compiles, but gives up ownership of pointer

            // here, iap owns a destroyed pointer so the following is bad:
            // *iap = 5; // BOOM

    cout << "main exiting\n";
}
```

```Output
~C:  2
main exiting
~C:  1
```

### <a name="release"></a>předběžné

Člen nahradí uložený ukazatel `myptr` ukazatelem s hodnotou null a vrátí dříve uložený ukazatel.

```cpp
Type *release() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Dřív uložený ukazatel.

#### <a name="remarks"></a>Poznámky

Člen nahradí uložený ukazatel `myptr` ukazatelem s hodnotou null a vrátí dříve uložený ukazatel.

#### <a name="example"></a>Příklad

```cpp
// auto_ptr_release.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int() {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;

};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

### <a name="reset"></a>nové

Členská funkce vyhodnotí výraz `delete myptr`, ale pouze v případě, že se hodnota uloženého ukazatele `myptr` změní v důsledku volání funkce. Pak nahradí uložený ukazatel pomocí `ptr`.

```cpp
void reset(Type* ptr = 0);
```

#### <a name="parameters"></a>Parametry

\ *PTR*
Ukazatel, který je určen k nahrazení uloženého ukazatele `myptr`.

#### <a name="example"></a>Příklad

```cpp
// auto_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int()
    {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;
};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

## <a name="see-also"></a>Viz také:

[unique_ptr – třída](../standard-library/unique-ptr-class.md)
