---
title: auto_ptr – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::auto_ptr
- memory/std::auto_ptr::element_type
- memory/std::auto_ptr::get
- memory/std::auto_ptr::release
- memory/std::auto_ptr::reset
dev_langs:
- C++
helpviewer_keywords:
- std::auto_ptr [C++]
- std::auto_ptr [C++], element_type
- std::auto_ptr [C++], get
- std::auto_ptr [C++], release
- std::auto_ptr [C++], reset
ms.assetid: 7f9108b6-9eb3-4634-b615-cf7aa814f23b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83c211617752a9c9701f513373d8fe796a26a1c6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850714"
---
# <a name="autoptr-class"></a>auto_ptr – třída

Zabalí inteligentní ukazatel kolem na prostředek, který zajistí, že prostředek automaticky zničen při řízení opustí blok.

Více podporující `unique_ptr` třída nahrazuje `auto_ptr`. Další informace najdete v tématu [unique_ptr – třída](../standard-library/unique-ptr-class.md).

Další informace o `throw()` a zpracování výjimek, najdete v části [specifikace výjimek (throw)](../cpp/exception-specifications-throw-cpp.md).

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

`right` `auto_ptr` Ze kterého chcete získat existující prostředek.

`ptr` Ukazatel zadaný nahrazení ukazatele uložené.

## <a name="remarks"></a>Poznámky

Šablony třídy popisuje chytré ukazatele, volána `auto_ptr`, k přidělené objektu. Ukazatel musí být buď hodnotu null nebo označení objektu přidělena `new`. `auto_ptr` Přenos vlastnictví, pokud jeho uložené hodnoty je přiřazen k jinému objektu. (Nahradí uložené hodnoty po převodu ukazatele null.) Destruktor pro `auto_ptr<Type>` odstraní přidělené objektu. `auto_ptr<Type>` Zajistí, že objekt přidělené při řízení opustí blok, klidně i prostřednictvím vyvolaná výjimka automaticky odstraněna. Nesmí vytvořit dva `auto_ptr<Type>` objekty, které vlastní stejný objekt.

Můžete předat `auto_ptr<Type>` objektu podle hodnoty jako argument pro volání funkce. `auto_ptr` Nemůže být element všechny standardní knihovna kontejneru. Nelze spravovat spolehlivě posloupnost `auto_ptr<Type>` objekty pomocí standardní knihovna C++ kontejneru.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[auto_ptr](#auto_ptr)|V konstruktoru pro objekty typu `auto_ptr`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[element_type](#element_type)|Typ je synonymum pro parametr šablony `Type`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[get](#get)|Členská funkce vrátí uložené ukazatele `myptr`.|
|[Verze](#release)|Člen nahrazuje uložené ukazatele `myptr` s ukazatele null a vrátí dříve uložené ukazatele.|
|[Resetování](#reset)|Členská funkce vyhodnotí výraz `delete myptr`, ale jenom v případě uložené ukazatel hodnota `myptr` změny v důsledku volání funkce. Nahradí uložené ukazatel s `ptr`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Operátor přiřazení, který přenos vlastnictví z jednoho `auto_ptr` objekt do jiné.|
|[operátor *](#op_star)|Při přesměrování operátor pro objekty typu `auto_ptr`.|
|[-> – operátor](#op_arrow)|Operátor pro povolení přístup ke členu.|
|[operátor auto_ptr\<Další >](#op_auto_ptr_lt_other_gt)|Druh vrhá z jednoho `auto_ptr` k jinému typu služby `auto_ptr`.|
|[operátor auto_ptr_ref\<Další >](#op_auto_ptr_ref_lt_other_gt)|Vrhá z `auto_ptr` k `auto_ptr_ref`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** – std

## <a name="auto_ptr"></a>  auto_ptr::auto_ptr

V konstruktoru pro objekty typu `auto_ptr`.

```cpp
explicit auto_ptr(Type* ptr  = 0) throw();

auto_ptr(auto_ptr<Type>& right) throw();

auto_ptr(auto _ptr_ref<Type> right) throw();

template <class Other>
auto _ptr(auto _ptr<Other>& right) throw();
```

### <a name="parameters"></a>Parametry

`ptr` Ukazatele na objekt, `auto_ptr` zapouzdří.

`right` `auto_ptr` Objekt, který má být zkopírovaná pomocí konstruktoru.

### <a name="remarks"></a>Poznámky

První úložiště konstruktor `ptr` v **myptr**, uložené ukazatel na objekt přidělená. Druhý konstruktor přenos vlastnictví ukazatele uložené v `right`, a to uložením `right`. [verze](#release) v **myptr**.

Třetí konstruktor se chová stejně jako druhá, s tím rozdílem, že ho ukládá **správné**. `ref`. **verze** v **myptr**, kde `ref` je odkaz na uložený v `right`.

Konstruktor šablony se chová stejně jako druhý konstruktor, za předpokladu, že ukazatel na **jiných** může být implicitně převedena na ukazatel na **typu**.

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

Typ je synonymum pro parametr šablony **typu**.

```cpp

typedef Type element  _type;
```

## <a name="get"></a>  auto_ptr::Get

Členská funkce vrátí uložené ukazatele **myptr**.

```cpp
Type *get() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Uložené ukazatele **myptr**.

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

Operátor přiřazení, který přenos vlastnictví z jednoho `auto_ptr` objekt do jiné.

```cpp
template <class Other>
auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```

### <a name="parameters"></a>Parametry

`right` Objekt typu `auto_ptr`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt typu `auto_ptr` \< **typ**>.

### <a name="remarks"></a>Poznámky

Vyhodnotí výraz přiřazení **odstranit myptr**, ale jenom v případě uložené ukazatele **myptr** změny v důsledku přiřazení. Potom přenosu vlastnictví ukazatele uložené v _ *vpravo*, a to uložením \_ *vpravo*. [verze](#release) v **myptr**. Funkce vrátí hodnotu  **\*to**.

### <a name="example"></a>Příklad

Příklad použití operátoru člen, naleznete v části [auto_ptr::auto_ptr](#auto_ptr).

## <a name="op_star"></a>  auto_ptr::Operator *

Při přesměrování operátor pro objekty typu `auto_ptr`.

```cpp
Type& operator*() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt typu **typ** vlastnící ukazatele.

### <a name="remarks"></a>Poznámky

Deferenční operátor vrátí `*` [získat](#get). Proto uložené ukazatele nesmí mít hodnotu null.

### <a name="example"></a>Příklad

Příklad použití – členská funkce naleznete v části [auto_ptr::auto_ptr](#auto_ptr).

## <a name="op_arrow"></a>  auto_ptr::Operator-&gt;

Operátor pro povolení přístup ke členu.

```cpp
Type * operator->() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Člen objektu, který **auto_ptr** vlastní.

### <a name="remarks"></a>Poznámky

Vrátí operátor selekce [získat](#get)`( )`tak, aby výraz *Asie*-> **člen** se chová stejně jako ( *Asie*. **získat**()) -> **člen**, kde *Asie* je objekt třídy `auto_ptr` \< **typ**>. Proto uložené ukazatele nesmí mít hodnotu null, a **typ** musí být třída, struktura nebo typu union s **člen** člen.

### <a name="example"></a>Příklad

Příklad použití – členská funkce naleznete v části [auto_ptr::auto_ptr](#auto_ptr).

## <a name="op_auto_ptr_lt_other_gt"></a>  auto_ptr::Operator auto_ptr&lt;jiné&gt;

Druh vrhá z jednoho `auto_ptr` k jinému typu služby `auto_ptr`.

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

## <a name="op_auto_ptr_ref_lt_other_gt"></a>  auto_ptr::Operator auto_ptr_ref&lt;jiné&gt;

Vrhá z `auto_ptr` k **auto_ptr_ref**.

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

Člen nahrazuje uložené ukazatele **myptr** s ukazatele null a vrátí dříve uložené ukazatele.

```cpp
Type *release() throw();
```

### <a name="return-value"></a>Návratová hodnota

Dříve uložené ukazatel.

### <a name="remarks"></a>Poznámky

Člen nahrazuje uložené ukazatele **myptr** s ukazatele null a vrátí dříve uložené ukazatele.

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

Členská funkce vyhodnotí výraz **odstranit** **myptr**, ale jenom v případě uložené ukazatel hodnota **myptr** změny v důsledku volání funkce. Nahradí uložené ukazatel s **ptr**.

```cpp
void reset(Type* ptr = 0);
```

### <a name="parameters"></a>Parametry

`ptr` Ukazatel zadaný nahrazení ukazatele uložené **myptr**.

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

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[unique_ptr – třída](../standard-library/unique-ptr-class.md)<br/>
