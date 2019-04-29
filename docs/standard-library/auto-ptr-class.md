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
ms.openlocfilehash: f0c8e0c1f4dc2e1082d5df230c74efafcae24f29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377973"
---
# <a name="autoptr-class"></a>auto_ptr – třída

Zabalí inteligentní ukazatel kolem prostředek, který zajistí, že prostředek je zničen automaticky při řízení opustí blok.

Více možností `unique_ptr` třídy nahrazuje `auto_ptr`. Další informace najdete v tématu [unique_ptr – třída](../standard-library/unique-ptr-class.md).

Další informace o `throw()` a zpracování výjimek naleznete v tématu [specifikace výjimek (throw)](../cpp/exception-specifications-throw-cpp.md).

## <a name="syntax"></a>Syntaxe

```cpp
class auto_ptr {
public:
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

*doprava*<br/>
`auto_ptr` Ze kterého chcete získat existující prostředek.

*ptr*<br/>
Ukazatel na zadaný k nahrazení uložený ukazatel.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje inteligentní ukazatel, volá se, `auto_ptr`, na přidělený objekt. Buď musí být ukazatel s hodnotou null nebo označení objektu alokovaného **nové**. `auto_ptr` Převede vlastnictví, pokud je jeho uložené hodnotě přiřazena k jinému objektu. (Nahradí uloženou hodnotu po převodu ukazatel s hodnotou null.) Destruktor `auto_ptr<Type>` odstraní objekt. `auto_ptr<Type>` Zajistí, že přiděleného objektu je automaticky odstraněn při řízení opustí blok, klidně i prostřednictvím vyvolané výjimky. By neměl vytvořit dvě `auto_ptr<Type>` objekty, které vlastníte na stejný objekt.

Můžete předat `auto_ptr<Type>` objektu podle hodnoty jako argument volání funkce. `auto_ptr` Nemůže být prvek kontejneru standardní knihovny. Není možné spolehlivě spravovat posloupnost `auto_ptr<Type>` objekty s kontejnerem standardní knihovny C++.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[auto_ptr](#auto_ptr)|Konstruktor pro objekty typu `auto_ptr`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[element_type](#element_type)|Typ je synonymum pro parametr šablony `Type`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[get](#get)|Členská funkce vrátí uložený ukazatel `myptr`.|
|[Vydání verze](#release)|Nahradí uložený ukazatel člen `myptr` s hodnotou null a vrátí dříve uložený ukazatel.|
|[reset](#reset)|Členská funkce vyhodnotí výraz `delete myptr`, ale pouze tehdy, pokud hodnota uložený ukazatel `myptr` změny jako výsledek volání funkce. Poté nahradí uložený ukazatel s *ptr*.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Operátor přiřazení, který převede vlastnictví z jednoho `auto_ptr` objektu na jiný.|
|[Operator *](#op_star)|Operátor přesměrování pro objekty typu `auto_ptr`.|
|[operator->](#op_arrow)|Operátor pro povolení přístupu ke členu.|
|[auto_ptr – operátor\<Další >](#op_auto_ptr_lt_other_gt)|Druh přetypování z jednoho `auto_ptr` na jiný typ z `auto_ptr`.|
|[operátor auto_ptr_ref\<Další >](#op_auto_ptr_ref_lt_other_gt)|Přetypování z `auto_ptr` do `auto_ptr_ref`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** std

## <a name="auto_ptr"></a>  auto_ptr::auto_ptr

Konstruktor pro objekty typu `auto_ptr`.

```cpp
explicit auto_ptr(Type* ptr  = 0) throw();

auto_ptr(auto_ptr<Type>& right) throw();

auto_ptr(auto _ptr_ref<Type> right) throw();

template <class Other>
auto _ptr(auto _ptr<Other>& right) throw();
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Ukazatel na objekt, který `auto_ptr` zapouzdřuje.

*doprava*<br/>
`auto_ptr` Objektu, který chcete zkopírovat konstruktorem.

### <a name="remarks"></a>Poznámky

První konstruktor ukládá *ptr* v `myptr`, uložený ukazatel na přidělený objekt. Druhý konstruktor převede vlastnictví ukazatele uložené v *správné*, uložením *správné*. [uvolnění](#release) v `myptr`.

Třetí konstruktor se chová stejně jako druhý, s tím rozdílem, že ukládá `right`. `ref`. `release` v `myptr`, kde `ref` je odkaz na uložený v `right`.

Konstruktor šablony se chová stejně jako druhý konstruktor, za předpokladu, že ukazatel na `Other` lze implicitně převést na ukazatel na `Type`.

### <a name="example"></a>Příklad

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

## <a name="element_type"></a>  auto_ptr::ELEMENT_TYPE

Typ je synonymum pro parametr šablony `Type`.

```cpp

typedef Type element  _type;
```

## <a name="get"></a>  auto_ptr::Get

Členská funkce vrátí uložený ukazatel `myptr`.

```cpp
Type *get() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Uložený ukazatel `myptr`.

### <a name="example"></a>Příklad

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

## <a name="op_eq"></a>  auto_ptr::Operator =

Operátor přiřazení, který převede vlastnictví z jednoho `auto_ptr` objektu na jiný.

```cpp
template <class Other>
auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Objekt typu `auto_ptr`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt typu `auto_ptr<Type>`.

### <a name="remarks"></a>Poznámky

Přiřazení vyhodnotí výraz `delete myptr`, ale pouze v případě uložený ukazatel `myptr` změny jako výsledek přiřazení. Potom převede vlastnictví ukazatele uložené v *správné*, uložením *správné*.[ uvolnění](#release) v `myptr`. Funkce vrátí  __\*to__.

### <a name="example"></a>Příklad

Příklad použití operátoru člen, naleznete v tématu [auto_ptr::auto_ptr](#auto_ptr).

## <a name="op_star"></a>  auto_ptr::Operator *

Operátor přesměrování pro objekty typu `auto_ptr`.

```cpp
Type& operator*() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt typu `Type` , který vlastní ukazatel.

### <a name="remarks"></a>Poznámky

Dereferenční operátor vrátí `*` [získat](#get). Proto uložený ukazatel nesmí mít hodnotu null.

### <a name="example"></a>Příklad

Příklad, jak používat členskou funkci, naleznete v tématu [auto_ptr::auto_ptr](#auto_ptr).

## <a name="op_arrow"></a>  auto_ptr::Operator-&gt;

Operátor pro povolení přístupu ke členu.

```cpp
Type * operator->() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Člen objektu, který `auto_ptr` vlastní.

### <a name="remarks"></a>Poznámky

Vrátí operátor výběru [získat](#get)`( )`tak, aby výraz *Asie a Tichomoří*-> **člen** se chová stejně jako ( *AsieaTichomoří*. **získat**()) -> **člen**, kde *Asie a Tichomoří* je objekt třídy `auto_ptr` \< **typ**>. Proto nesmí mít hodnotu null, uložený ukazatel a `Type` musí být třídy, struktury nebo sjednocení typ s `member` člena.

### <a name="example"></a>Příklad

Příklad, jak používat členskou funkci, naleznete v tématu [auto_ptr::auto_ptr](#auto_ptr).

## <a name="op_auto_ptr_lt_other_gt"></a>  auto_ptr::Operator auto_ptr&lt;další&gt;

Druh přetypování z jednoho `auto_ptr` na jiný typ z `auto_ptr`.

```cpp
template <class Other>
operator auto _ptr<Other>() throw();
```

### <a name="return-value"></a>Návratová hodnota

Typ přetypování operátor vrátí `auto_ptr` \< **jiných**> (  **\*to**).

### <a name="example"></a>Příklad

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

## <a name="op_auto_ptr_ref_lt_other_gt"></a>  auto_ptr::Operator auto_ptr_ref&lt;další&gt;

Přetypování z `auto_ptr` do `auto_ptr_ref`.

```cpp
template <class Other>
operator auto _ptr  _ref<Other>() throw();
```

### <a name="return-value"></a>Návratová hodnota

Typ přetypování operátor vrátí **auto_ptr_ref** \< **jiných**> (  **\*to**).

### <a name="example"></a>Příklad

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

## <a name="release"></a>  auto_ptr::Release

Nahradí uložený ukazatel člen `myptr` s hodnotou null a vrátí dříve uložený ukazatel.

```cpp
Type *release() throw();
```

### <a name="return-value"></a>Návratová hodnota

Dříve uložený ukazatel.

### <a name="remarks"></a>Poznámky

Nahradí uložený ukazatel člen `myptr` s hodnotou null a vrátí dříve uložený ukazatel.

### <a name="example"></a>Příklad

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

## <a name="reset"></a>  auto_ptr::Reset

Členská funkce vyhodnotí výraz `delete myptr`, ale pouze tehdy, pokud hodnota uložený ukazatel `myptr` změny jako výsledek volání funkce. Poté nahradí uložený ukazatel s `ptr`.

```cpp
void reset(Type* ptr = 0);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Ukazatel na zadaný k nahrazení uložený ukazatel `myptr`.

### <a name="example"></a>Příklad

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

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[unique_ptr – třída](../standard-library/unique-ptr-class.md)<br/>
