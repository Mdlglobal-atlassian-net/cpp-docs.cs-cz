---
title: shared_ptr – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::shared_ptr
- memory/std::shared_ptr::element_type
- memory/std::shared_ptr::get
- memory/std::shared_ptr::owner_before
- memory/std::shared_ptr::reset
- memory/std::shared_ptr::swap
- memory/std::shared_ptr::unique
- memory/std::shared_ptr::use_count
- memory/std::shared_ptr::operator boolean-type
- memory/std::shared_ptr::operator*
- memory/std::shared_ptr::operator=
- memory/std::shared_ptr::operator->
dev_langs:
- C++
helpviewer_keywords:
- std::shared_ptr [C++]
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
ms.assetid: 1469fc51-c658-43f1-886c-f4530dd84860
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eff0c41993a450e74b468b747776368bae6ad848
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="sharedptr-class"></a>shared_ptr – třída

Zabalí inteligentní ukazatel počítaný odkazy do dynamicky alokovaného objektu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class shared_ptr;
```

## <a name="remarks"></a>Poznámky

Shared_ptr – třída popisuje objekt, který používá ke správě prostředků při počítání referencí. A `shared_ptr` efektivně má objekt ukazatel k prostředku, vlastní nebo obsahuje ukazatele null. Prostředek může být vlastněn více než jeden `shared_ptr` objektu; při poslední `shared_ptr` zničena objektu, který vlastní určitý prostředek, prostředek je uvolněno.

A `shared_ptr` zastaví, který je vlastníkem prostředku, pokud je znovu přiřazen nebo resetovat.

Argument šablony `T` může být neúplné typy s výjimkou uvedených určité členské funkce.

Když `shared_ptr<T>` objekt je vytvořen z prostředků ukazatel typu `G*` nebo z `shared_ptr<G>`, je ukazatel typu `G*` musí být převoditelná na `T*`. Pokud není, nebude zkompilovat kód. Příklad:

```cpp
#include <memory>
using namespace std;

class F {};
class G : public F {};

shared_ptr<G> sp0(new G);   // okay, template parameter G and argument G*
shared_ptr<G> sp1(sp0);     // okay, template parameter G and argument shared_ptr<G>
shared_ptr<F> sp2(new G);   // okay, G* convertible to F*
shared_ptr<F> sp3(sp0);     // okay, template parameter F and argument shared_ptr<G>
shared_ptr<F> sp4(sp2);     // okay, template parameter F and argument shared_ptr<F>
shared_ptr<int> sp5(new G); // error, G* not convertible to int*
shared_ptr<int> sp6(sp2);   // error, template parameter int and argument shared_ptr<F>
```

A `shared_ptr` objektu vlastní prostředek:

- Pokud byl zkonstruován pomocí ukazatele k danému prostředku

- Pokud byl zkonstruován z `shared_ptr` objektu, který vlastní tento prostředek

- Pokud byl zkonstruován z [weak_ptr – třída](../standard-library/weak-ptr-class.md) objekt, který odkazuje na prostředek, nebo

- Pokud se vlastnictví prostředku byl k němu přiřazen, buď pomocí [shared_ptr::operator =](#op_eq) nebo voláním členské funkce [shared_ptr::reset](#reset).

`shared_ptr` Objekty, které vlastní prostředek sdílet řídicí blok. Řídicí blok obsahuje:

- počet `shared_ptr` objekty, které vlastní prostředek,

- počet `weak_ptr` objekty, které odkazují na prostředek,

- metoda odstranění pro tento prostředek, pokud má jedna,

- vlastní přidělení pro řídicí blok, pokud jej obsahuje.

A `shared_ptr` má řídicí blok objekt, který je inicializován pomocí ukazatele null a není prázdná. Po `shared_ptr` objekt uvolní prostředek, už vlastníkem tohoto prostředku. Po `weak_ptr` objekt uvolní prostředek, již neodkazuje na tento prostředek.

Pokud počet `shared_ptr` objekty, vlastní prostředek klesne na nulu, prostředek je uvolněno, odstranění nebo předání adresy metoda odstranění, v závislosti na tom, jak byl původně vytvořen vlastnictví prostředku. Pokud počet `shared_ptr` objekty, které vlastní prostředek je nula a počet `weak_ptr` objekty, které odkazují na, prostředek je nulová, po uvolnění řídicí blok pomocí přidělujícího modulu vlastní pro řídicí blok, pokud má jedna.

Prázdná `shared_ptr` objekt nevlastní žádné prostředky a nemá žádné řídicí blok.

Metoda odstranění je objekt funkce, která obsahuje členské funkce `operator()`. Typ musí být kopie zkonstruovatelný a jeho kopírovacího konstruktoru a destruktor nesmí generování výjimek. Přijímá jeden parametr, objekt, který má být odstraněna.

Některé funkce trvat seznam argumentů, která definuje vlastnosti výsledná `shared_ptr<T>` nebo `weak_ptr<T>` objektu. Můžete určit takový seznam argumentů několika způsoby:

žádné argumenty – výsledný objekt je prázdná `shared_ptr` objektu nebo na prázdný `weak_ptr` objektu.

`ptr` – ukazatel typu `Other*` k prostředku pro správu. `T` musí být typu dokončení. Pokud funkce selže (protože řídicí blok nelze přidělit) se vyhodnotí výraz `delete ptr`.

`ptr, dtor` – ukazatel typu `Other*` prostředků ke správě a metoda odstranění pro tento prostředek. Pokud funkce selže (protože řídicí blok nelze přidělit), zavolá `dtor(ptr)`, která musí být dobře definované.

`ptr, dtor, alloc` – ukazatel typu `Other*` prostředků ke správě, metoda odstranění pro tento prostředek a přidělení ke správě jakékoli úložiště, které se musí přiřadit a uvolnit. Pokud funkce selže (protože řídicí blok nelze přidělit) zavolá `dtor(ptr)`, která musí být dobře definované.

`sp` -- `shared_ptr<Other>` objekt, který je vlastníkem prostředku pro správu.

`wp` -- `weak_ptr<Other>` objekt, který odkazuje na prostředek pro správu.

`ap` – `auto_ptr<Other>` objekt, který obsahuje ukazatel k prostředku pro správu. Pokud funkci úspěšné volání `ap.release()`; v opačném případě opustí `ap` beze změny.

Ve všech případech je ukazatel typu `Other*` musí být převoditelná na `T*`.

## <a name="thread-safety"></a>Bezpečnost vlákna

Více vláken lze číst a zapisovat jiné `shared_ptr` objekty ve stejnou dobu, i když jsou tyto objekty kopií, které sdílejí vlastnictví.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[shared_ptr](#shared_ptr)|Vytvoří `shared_ptr`.|
|[shared_ptr::~shared_ptr](#dtorshared_ptr)|Zničí `shared_ptr`.|

### <a name="types"></a>Typy

|Název typu|Popis|
|-|-|
|[element_type](#element_type)|Typ prvku|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[get](#get)|Získá adresu vlastní prostředek.|
|[owner_before –](#owner_before)|Vrátí hodnotu PRAVDA, pokud `shared_ptr` je seřadí před (nebo menší než) zadané ukazatele.|
|[Resetování](#reset)|Nahraďte vlastní prostředek.|
|[Swap](#swap)|Prohození dva `shared_ptr` objekty.|
|[Jedinečné](#unique)|Testy, pokud je ve vlastnictví prostředků jedinečné.|
|[use_count –](#use_count)|Spočítá počet vlastníky prostředků.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[shared_ptr::Operator bool](#op_bool)|Testy, pokud existuje vlastní prostředek.|
|[shared_ptr::operator*](#op_star)|Získá určenou hodnotu.|
|[shared_ptr::operator=](#op_eq)|Nahradí vlastní prostředek.|
|[shared_ptr::operator-&gt;](#op_arrow)|Získá ukazatel na určenou hodnotu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** – std

## <a name="element_type"></a>  shared_ptr::ELEMENT_TYPE

Typ prvku

```cpp
typedef T element_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `T`.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::shared_ptr<int>::element_type val = *sp0;

    std::cout << "*sp0 == " << val << std::endl;

    return (0);
}

```

```Output
*sp0 == 5
```

## <a name="get"></a>  shared_ptr::Get

Získá adresu vlastní prostředek.

```cpp
T *get() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu vlastní prostředek. Pokud objekt není vlastníkem prostředku vrátí hodnotu 0.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_get.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "sp0.get() == 0 == " << std::boolalpha
        << (sp0.get() == 0) << std::endl;
    std::cout << "*sp1.get() == " << *sp1.get() << std::endl;

    return (0);
}

```

```Output
sp0.get() == 0 == true
*sp1.get() == 5
```

## <a name="op_bool"></a>  shared_ptr::Operator bool

Testy, pokud existuje vlastní prostředek.

```cpp
explicit operator bool() const noexcept;
```

### <a name="remarks"></a>Poznámky

Operátor vrací hodnotu `true` při `get() != nullptr`, jinak `false`.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_operator_bool.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;
    std::cout << "(bool)sp1 == " << std::boolalpha
        << (bool)sp1 << std::endl;

    return (0);
}

```

```Output
(bool)sp0 == false
(bool)sp1 == true
```

## <a name="op_star"></a>  shared_ptr::Operator *

Získá určenou hodnotu.

```cpp
T& operator*() const;
```

### <a name="remarks"></a>Poznámky

Deferenční operátor vrátí `*get()`. Proto uložené ukazatele nesmí mít hodnotu null.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_operator_st.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}

```

```Output
*sp0 == 5
```

## <a name="op_eq"></a>  shared_ptr::Operator =

Nahradí vlastní prostředek.

```cpp
shared_ptr& operator=(const shared_ptr& sp);

template <class Other>
shared_ptr& operator=(const shared_ptr<Other>& sp);

template <class Other>
shared_ptr& operator=(auto_ptr<Other>& ap);

template <class Other>
shared_ptr& operator=(auto_ptr<Other>& ap);

template <class Other>
shared_ptr& operator=(auto_ptr<Other>&& ap);

template <class Other, class Deletor>
shared_ptr& operator=(unique_ptr<Other, Deletor>&& ap);
```

### <a name="parameters"></a>Parametry

`sp` Sdílené ukazatel ke kopírování.

`ap` Ukazatel automaticky ke kopírování.

### <a name="remarks"></a>Poznámky

Všechny operátory sníží počet odkazů pro daný prostředek aktuálně vlastníkem `*this` a přiřaďte vlastnictví prostředek s názvem pořadím operand k `*this`. Pokud počet odkazů klesne na nulu, vydání prostředku. Pokud operátor selže nechá `*this` beze změny.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));
    std::auto_ptr<int> ap(new int(10));

    sp0 = sp1;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    sp0 = ap;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}

```

```Output
*sp0 == 5
*sp0 == 10
```

## <a name="op_arrow"></a>  shared_ptr::Operator-&gt;

Získá ukazatel na určenou hodnotu.

```cpp
T * operator->() const;
```

### <a name="remarks"></a>Poznámky

Vrátí operátor selekce `get()`tak, aby výraz `sp->member` se chová stejně jako `(sp.get())->member` kde `sp` je objekt třídy `shared_ptr<T>`. Proto uložené ukazatele nesmí mít hodnotu null, a `T` musí být třída, struktura nebo typu union s členem `member`.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_operator_ar.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

typedef std::pair<int, int> Mypair;
int main()
{
    std::shared_ptr<Mypair> sp0(new Mypair(1, 2));

    std::cout << "sp0->first == " << sp0->first << std::endl;
    std::cout << "sp0->second == " << sp0->second << std::endl;

    return (0);
}

```

```Output
sp0->first == 1
sp0->second == 2
```

## <a name="owner_before"></a>  shared_ptr::owner_before

Vrátí hodnotu PRAVDA, pokud `shared_ptr` je seřadí před (nebo menší než) zadané ukazatele.

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr);
```

### <a name="parameters"></a>Parametry

`ptr` `lvalue` Odkaz na buď `shared_ptr` nebo `weak_ptr`.

### <a name="remarks"></a>Poznámky

Šablona členská funkce vrátí hodnotu true, pokud `*this` je `ordered before` `ptr`.

## <a name="reset"></a>  shared_ptr::Reset

Nahraďte vlastní prostředek.

```cpp
void reset();

template <class Other>
void reset(Other *ptr;);

template <class Other, class D>
void reset(Other *ptr, D dtor);

template <class Other, class D, class A>
void reset(Other *ptr, D dtor, A alloc);
```

### <a name="parameters"></a>Parametry

`Other` Typ řízené argument ukazatele.

`D` Typ metoda odstranění.

`ptr` Ukazatel ke kopírování.

`dtor` Metoda odstranění pro kopírování.

`A` Typ přidělujícího modulu.

`alloc` Allocator ke kopírování.

### <a name="remarks"></a>Poznámky

Všechny operátory sníží počet odkazů pro daný prostředek aktuálně vlastníkem `*this` a přiřaďte vlastnictví prostředek s názvem pořadím operand k `*this`. Pokud počet odkazů klesne na nulu, vydání prostředku. Pokud operátor selže nechá `*this` beze změny.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp(new int(5));

    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset();
    std::cout << "(bool)sp == " << std::boolalpha
        << (bool)sp << std::endl;

    sp.reset(new int(10));
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset(new int(15), deleter());
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    return (0);
}

```

```Output
*sp == 5
(bool)sp == false
*sp == 10
*sp == 15
```

## <a name="shared_ptr"></a>  shared_ptr::shared_ptr

Vytvoří `shared_ptr`.

```cpp
shared_ptr();

shared_ptr(nullptr_t);

shared_ptr(const shared_ptr& sp);

shared_ptr(shared_ptr&& sp);

template <class Other>
explicit shared_ptr(Other* ptr);

template <class Other, class D>
shared_ptr(Other* ptr, D dtor);

template <class D>
shared_ptr(nullptr_t ptr, D dtor);

template <class Other, class D, class A>
shared_ptr(Other* ptr, D dtor, A  alloc);

template <class D, class A>
shared_ptr(nullptr_t ptr, D dtor, A alloc);

template <class Other>
shared_ptr(const shared_ptr<Other>& sp);

template <class Other>
shared_ptr(const weak_ptr<Other>& wp);

template <class &>
shared_ptr(std::auto_ptr<Other>& ap);

template <class &>
shared_ptr(std::auto_ptr<Other>&& ap);

template <class Other, class D>
shared_ptr(unique_ptr<Other, D>&& up);

template <class Other>
shared_ptr(const shared_ptr<Other>& sp, T* ptr);

template <class Other, class D>
shared_ptr(const unique_ptr<Other, D>& up) = delete;
```

### <a name="parameters"></a>Parametry

`Other` Typ řízené argument ukazatele.

`ptr` Ukazatel ke kopírování.

`D` Typ metoda odstranění.

`A` Typ přidělujícího modulu.

`dtor` Metoda odstranění.

`ator` Přidělení.

`sp` Chytré ukazatele pro kopírování.

`wp` Slabé ukazatel.

`ap` Ukazatel automaticky ke kopírování.

### <a name="remarks"></a>Poznámky

Konstruktory každý vytvořit objekt, který vlastní prostředek s názvem operand pořadí. Konstruktor `shared_ptr(const weak_ptr<Other>& wp)` objekt výjimka typu, vyvolá [bad_weak_ptr – třída](../standard-library/bad-weak-ptr-class.md) Pokud `wp.expired()`.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp0;
    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    std::shared_ptr<int> sp2(new int(10), deleter());
    std::cout << "*sp2 == " << *sp2 << std::endl;

    std::shared_ptr<int> sp3(sp2);
    std::cout << "*sp3 == " << *sp3 << std::endl;

    std::weak_ptr<int> wp(sp3);
    std::shared_ptr<int> sp4(wp);
    std::cout << "*sp4 == " << *sp4 << std::endl;

    std::auto_ptr<int> ap(new int(15));
    std::shared_ptr<int> sp5(ap);
    std::cout << "*sp5 == " << *sp5 << std::endl;

    return (0);
}

```

```Output
(bool)sp0 == false
*sp1 == 5
*sp2 == 10
*sp3 == 10
*sp4 == 10
*sp5 == 15
```

## <a name="dtorshared_ptr"></a>  shared_ptr:: ~ shared_ptr

Zničí `shared_ptr`.

```cpp
~shared_ptr();
```

### <a name="remarks"></a>Poznámky

Destruktor snižuje počet odkazů pro daný prostředek aktuálně vlastníkem `*this`. Pokud počet odkazů klesne na nulu, vydání prostředku.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_destroy.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << "use count == " << sp1.use_count() << std::endl;

    {
        std::shared_ptr<int> sp2(sp1);
        std::cout << "*sp2 == " << *sp2 << std::endl;
        std::cout << "use count == " << sp1.use_count() << std::endl;
    }

    // check use count after sp2 is destroyed
    std::cout << "use count == " << sp1.use_count() << std::endl;

    return (0);
}

```

```Output
*sp1 == 5
use count == 1
*sp2 == 5
use count == 2
use count == 1
```

## <a name="swap"></a>  shared_ptr::swap

Prohození dva `shared_ptr` objekty.

```cpp
void swap(shared_ptr& sp);
```

### <a name="parameters"></a>Parametry

`sp` Sdílené ukazatel na prohození s.

### <a name="remarks"></a>Poznámky

Členská funkce opustí původně vlastníkem prostředku `*this` následně vlastníkem `sp`a prostředek původně vlastníkem `sp` následně vlastníkem `*this`. Funkce nezmění počty odkazů pro tyto dva prostředky a nevyvolá jakékoli výjimky.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}

```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5

*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="unique"></a>  shared_ptr::Unique

Testy, pokud je ve vlastnictví prostředků jedinečné.

```cpp
bool unique() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu `true` Pokud žádný jiný `shared_ptr` objekt vlastníkem prostředku, který je vlastněn `*this`, jinak `false`.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_unique.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    return (0);
}

```

```Output
sp1.unique() == true
sp1.unique() == false
```

## <a name="use_count"></a>  shared_ptr::use_count

Spočítá počet vlastníky prostředků.

```cpp
long use_count() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet `shared_ptr` objekty, které vlastní prostředek, který je vlastněn `*this`.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    return (0);
}

```

```Output
sp1.use_count() == 1
sp1.use_count() == 2
```

## <a name="see-also"></a>Viz také

[weak_ptr – třída](../standard-library/weak-ptr-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
