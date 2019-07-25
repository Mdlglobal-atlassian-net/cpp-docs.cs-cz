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
ms.openlocfilehash: 14841662235f075d74120673208dd54531763c09
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456716"
---
# <a name="autoptr-class"></a>auto_ptr – třída

Zalomí inteligentní ukazatel kolem prostředku, který zajišťuje, že je prostředek zničen automaticky, když ovládací prvek opustí blok.

Třída s možností `unique_ptr` příschopností `auto_ptr`nahrazuje. Další informace naleznete v tématu [Třída unique_ptr](../standard-library/unique-ptr-class.md).

Další informace o `throw()` zpracování výjimek naleznete v tématu [Specifikace výjimek (throw)](../cpp/exception-specifications-throw-cpp.md).

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

*Kliknutím*\
, `auto_ptr` Ze kterého se má získat existující prostředek.

*střed*\
Ukazatel, který je určen k nahrazení uloženého ukazatele.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje inteligentní ukazatel nazvaný `auto_ptr`a přiřazenému objektu. Ukazatel musí mít buď hodnotu null, nebo určovat objekt přidělený **novým**. Přenese vlastnictví, `auto_ptr` Pokud je jeho uložená hodnota přiřazena k jinému objektu. (Po přenosu s nulovým ukazatelem nahradí uloženou hodnotu.) Destruktor pro `auto_ptr<Type>` odstranění přiděleného objektu. `auto_ptr<Type>` Zajišťuje, aby byl přidělený objekt automaticky odstraněn, když ovládací prvek opustí blok, a to i přes vyvolanou výjimku. Neměli byste vytvářet dva `auto_ptr<Type>` objekty, které vlastní tento objekt.

`auto_ptr<Type>` Objektu můžete předat hodnotu jako argument volání funkce. Element `auto_ptr` nemůže být prvkem žádného standardního kontejneru knihovny. Nelze spolehlivě spravovat sekvenci `auto_ptr<Type>` objektů se C++ standardním kontejnerem knihovny.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[auto_ptr](#auto_ptr)|Konstruktor pro objekty typu `auto_ptr`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|Typ je synonymum pro parametr `Type`šablony.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[get](#get)|Členská funkce vrátí uložený ukazatel `myptr`.|
|[předběžné](#release)|Člen nahradí uložený ukazatel `myptr` ukazatelem s hodnotou null a vrátí dříve uložený ukazatel.|
|[reset](#reset)|Členská funkce vyhodnotí výraz `delete myptr`, ale pouze v případě, že se `myptr` hodnota uloženého ukazatele změní v důsledku volání funkce. Pak nahradí uložený ukazatel pomocí *PTR*.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_eq)|Operátor přiřazení, který přenáší vlastnictví jednoho `auto_ptr` objektu na jiný.|
|[podnikatel](#op_star)|Operátor přesměrování pro objekty typu `auto_ptr`.|
|[operátor->](#op_arrow)|Operátor pro povolení přístupu členů|
|[operátor auto_ptr\<jiné >](#op_auto_ptr_lt_other_gt)|Přetypování z jednoho typu `auto_ptr` na jiný `auto_ptr`typ.|
|[operátor auto_ptr_ref\<jiné >](#op_auto_ptr_ref_lt_other_gt)|Přetypování z `auto_ptr` `auto_ptr_ref`a na.|

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

*střed*\
Ukazatel na objekt, který `auto_ptr` zapouzdřuje.

*Kliknutím*\
`auto_ptr` Objekt, který má být zkopírován konstruktorem.

#### <a name="remarks"></a>Poznámky

První konstruktor ukládá *PTR* do `myptr`, uložený ukazatel na přidělený objekt. Druhý konstruktor převádí vlastnictví ukazatele uloženého *vpravo*uložením *vpravo*. [vydaná verze](#release) v `myptr`produktu.

Třetí konstruktor se chová stejně jako druhý s tím rozdílem, že ukládá `right`. `ref`. `release`v `myptr`, kde `ref` je odkaz uložený v `right`.

Konstruktor šablony se chová stejně jako druhý konstruktor za předpokladu, že ukazatel na `Other` může být implicitně převeden na ukazatel na. `Type`

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

Typ je synonymum pro parametr `Type`šablony.

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

Operátor přiřazení, který přenáší vlastnictví jednoho `auto_ptr` objektu na jiný.

```cpp
template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```

#### <a name="parameters"></a>Parametry

*Kliknutím*\
Objekt typu `auto_ptr`.

#### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt typu `auto_ptr<Type>`.

#### <a name="remarks"></a>Poznámky

Přiřazení vyhodnotí výraz `delete myptr`, ale pouze v případě, že se `myptr` uložený ukazatel změní jako výsledek přiřazení. Pak přenáší vlastnictví ukazatele uloženého *vpravo*uložením *práva*. [vydaná verze](#release) v `myptr`produktu. Funkce vrátí  __\*tuto__hodnotu.

#### <a name="example"></a>Příklad

Příklad použití operátoru členu naleznete v tématu [auto_ptr](#auto_ptr).

### <a name="op_star"></a>podnikatel

Operátor přesměrování pro objekty typu `auto_ptr`.

```cpp
Type& operator*() const throw();
```

#### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt typu `Type` , který vlastní ukazatel.

#### <a name="remarks"></a>Poznámky

Operátor dereference vrací `*` [Get](#get). Proto nesmí mít uložený ukazatel hodnotu null.

#### <a name="example"></a>Příklad

Příklad použití členské funkce naleznete v tématu [auto_ptr](#auto_ptr).

### <a name="op_arrow"></a>podnikatel&gt;

Operátor pro povolení přístupu členů

```cpp
Type * operator->() const throw();
```

#### <a name="return-value"></a>Návratová hodnota

Člen objektu, který `auto_ptr` je vlastníkem.

#### <a name="remarks"></a>Poznámky

Operátor výběru vrátí [Get](#get)`( )`, aby se**člen** Expression *AP*-> choval stejně jako ( *AP*. **získat** ())-> **člen**, kde *AP* je objekt `auto_ptr` **typu**třídy \< >. Proto nesmí mít uložený ukazatel hodnotu null a `Type` musí se jednat o typ třídy, struktury nebo sjednocení `member` s členem.

#### <a name="example"></a>Příklad

Příklad použití členské funkce naleznete v tématu [auto_ptr](#auto_ptr).

### <a name="op_auto_ptr_lt_other_gt"></a>auto_ptr&lt;– operátor&gt;

Přetypování z jednoho typu `auto_ptr` na jiný `auto_ptr`typ.

```cpp
template <class Other>
operator auto _ptr<Other>() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Operátor přetypování typu vrátí `auto_ptr` \< **jiné**> (  **\*this**).

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

### <a name="op_auto_ptr_ref_lt_other_gt"></a>auto_ptr_ref&lt;– operátor&gt;

Přetypování z `auto_ptr` `auto_ptr_ref`a na.

```cpp
template <class Other>
operator auto _ptr  _ref<Other>() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Operátor přetypování typu vrátí **auto_ptr_ref** \< **jinou**> (  **\*this**).

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

Členská funkce vyhodnotí výraz `delete myptr`, ale pouze v případě, že se `myptr` hodnota uloženého ukazatele změní v důsledku volání funkce. Pak nahradí uložený ukazatel pomocí `ptr`.

```cpp
void reset(Type* ptr = 0);
```

#### <a name="parameters"></a>Parametry

*střed*\
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
