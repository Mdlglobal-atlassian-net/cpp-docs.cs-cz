---
title: shared_ptr – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 57874a87dcd7102c98ec5a387f1d3346bfa00195
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627549"
---
# <a name="sharedptr-class"></a>shared_ptr – třída

Zabalí inteligentní ukazatel počítaný odkazy do dynamicky alokovaného objektu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class shared_ptr;
```

## <a name="remarks"></a>Poznámky

Shared_ptr – třída popisuje objekt, který používá počítání odkazů ke správě prostředků. A `shared_ptr` objekt účinně drží ukazatel na prostředek, který je vlastníkem, nebo drží ukazatel s hodnotou null. Prostředek může být vlastněn více než jeden `shared_ptr` objektu při poslední `shared_ptr` objekt, který vlastní určitý prostředek, zničen, prostředek je uvolněn.

A `shared_ptr` přestane vlastnit prostředek, když je znovu přiřazen nebo obnoven.

Argument šablony `T` může být neúplný typ s výjimkou, jak je uvedeno pro určité členské funkce.

Když `shared_ptr<T>` objekt je vytvořen z ukazatele na prostředek typu `G*` nebo z `shared_ptr<G>`, typ ukazatele `G*` musí být převeditelný na `T*`. Pokud není, nebude kompilovat kód. Příklad:

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

A `shared_ptr` vlastní prostředek objektu:

- Pokud byl vytvořen s ukazatelem na tento prostředek

- Pokud byl vytvořen z `shared_ptr` objekt, který vlastní prostředek,

- Pokud byl vytvořen z [weak_ptr – třída](../standard-library/weak-ptr-class.md) , která odkazuje na prostředek, nebo

- Pokud bylo vlastnictví tohoto prostředku přiřazeno k němu, buď pomocí [shared_ptr::operator =](#op_eq) nebo voláním členské funkce [shared_ptr::reset](#reset).

`shared_ptr` Objekty, které prostředek vlastní, sdílejí řídicí blok. Kontrolní blok obsahuje:

- počet `shared_ptr` objekty, které zdroj vlastní,

- počet `weak_ptr` objekty, které odkazují na prostředek

- odstraňovač pro tento prostředek, pokud existuje,

- vlastní Alokátor pro řídicí blok, má-li nějaký.

A `shared_ptr` obsahuje řídicí blok, který je inicializován pomocí ukazatele s hodnotou null a není prázdný. Po `shared_ptr` objekt uvolní zdroj, již nevlastní tento zdroj. Po `weak_ptr` objekt uvolní zdroj, již neukazuje na tento prostředek.

Když počet `shared_ptr` objekty, vlastní prostředek na nulu, zdroj je uvolněn odstraněním nebo předáním jeho adresy deleteru podle toho, jak bylo vlastnictví prostředku původně vytvořil. Když počet `shared_ptr` objekty, které prostředek vlastní, je nula a počet `weak_ptr` objekty, které odkazují na, prostředek je nula, řídicí blok je uvolněn, pomocí vlastního alokátoru pro řídicí blok, má-li nějaký.

Prázdná `shared_ptr` objekt není vlastníkem žádného prostředku a nemá žádný řídicí blok.

Odstraňovač je objekt funkce, který má členská funkce `operator()`. Jeho typ musí mít kopírovací a kopírovací konstruktor a destruktor musí vyvolávat výjimky. Přijímá jeden parametr, objekt, který má být odstraněna.

Některé funkce přijímají seznam argumentů, která definuje vlastnosti výsledného `shared_ptr<T>` nebo `weak_ptr<T>` objektu. Seznam argumentů můžete zadat několika způsoby:

bez argumentů – výsledný objekt je prázdný `shared_ptr` objekt nebo na prázdný `weak_ptr` objektu.

`ptr` – ukazatel typu `Other*` na prostředek, který chcete spravovat. `T` musí být dokončený typ. Pokud funkce selže (protože nelze přidělit řídicí blok), vyhodnotí výraz `delete ptr`.

`ptr, dtor` – ukazatel typu `Other*` a prostředek, který má být spravován, deleter pro daný prostředek. Pokud funkce selže (protože nelze přidělit řídicí blok), zavolá `dtor(ptr)`, které musí být dobře definované.

`ptr, dtor, alloc` – ukazatel typu `Other*` na prostředek má být spravován, deleter pro daný prostředek a Alokátor ke správě úložiště, který musí být přiděleno a uvolněno. Pokud funkce selže (protože nelze přidělit řídicí blok), které volá `dtor(ptr)`, které musí být dobře definované.

`sp` -- `shared_ptr<Other>` objekt, který vlastní prostředek, který chcete spravovat.

`wp` -- `weak_ptr<Other>` , která odkazuje na prostředek, který chcete spravovat.

`ap` – `auto_ptr<Other>` objekt, který uchovává ukazatel na prostředek, který chcete spravovat. Pokud funkce uspěje, volá `ap.release()`; v opačném případě zůstanou `ap` beze změny.

Ve všech případech se typ ukazatele `Other*` musí být převeditelný na `T*`.

## <a name="thread-safety"></a>Bezpečnost vlákna

Více vláken může číst a zapisovat různé `shared_ptr` objekty ve stejnou dobu, i když jsou objekty kopie, které sdílejí vlastnictví.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[shared_ptr](#shared_ptr)|Vytvoří `shared_ptr`.|
|[shared_ptr::~shared_ptr](#dtorshared_ptr)|Odstraní `shared_ptr`.|

### <a name="types"></a>Typy

|Název typu|Popis|
|-|-|
|[element_type](#element_type)|Typ prvku|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[get](#get)|Získá adresu vlastněného prostředku.|
|[owner_before –](#owner_before)|Vrátí hodnotu PRAVDA, pokud `shared_ptr` je řazen před (nebo menší než) poskytnutý ukazatel.|
|[Resetovat](#reset)|Nahraďte vlastněný zdroj.|
|[Prohození](#swap)|Prohodí dva `shared_ptr` objekty.|
|[unique](#unique)|Testuje, zda je vlastněný zdroj jedinečný.|
|[use_count –](#use_count)|Počítá vlastníky zdrojů.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[shared_ptr::Operator bool](#op_bool)|Testuje, zda existuje vlastněný prostředek.|
|[shared_ptr::operator*](#op_star)|Získá určenou hodnotu.|
|[shared_ptr::operator=](#op_eq)|Nahradí vlastněný zdroj.|
|[shared_ptr::operator-&gt;](#op_arrow)|Získá ukazatel na určenou hodnotu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** std

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

Získá adresu vlastněného prostředku.

```cpp
T *get() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu vlastněného prostředku. Pokud objekt není vlastníkem prostředku vrátí hodnotu 0.

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

Testuje, zda existuje vlastněný prostředek.

```cpp
explicit operator bool() const noexcept;
```

### <a name="remarks"></a>Poznámky

Operátor vrátí hodnotu **true** při `get() != nullptr`, jinak **false**.

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

Dereferenční operátor vrátí `*get()`. Proto uložený ukazatel nesmí mít hodnotu null.

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

Nahradí vlastněný zdroj.

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

*SP*<br/>
Sdílený ukazatel na kopii.

*Asie a Tichomoří*<br/>
Automatický ukazatel na kopii.

### <a name="remarks"></a>Poznámky

Všechny operátory snížen počet odkazů prostředku aktuálně vlastníkem `*this` a přiřazení vlastnictví prostředků s názvem podle sekvenci operandů pro `*this`. Pokud klesne počet odkazů na nulu, zdroj je uvolněn. Pokud se operátor nezdaří ponechá `*this` beze změny.

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

Vrátí operátor výběru `get()`tak, aby výraz `sp->member` se chová stejně jako `(sp.get())->member` kde `sp` je objekt třídy `shared_ptr<T>`. Proto nesmí mít hodnotu null, uložený ukazatel a `T` musí být třída, struktura nebo typu sjednocení se členem `member`.

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

Vrátí hodnotu PRAVDA, pokud `shared_ptr` je řazen před (nebo menší než) poskytnutý ukazatel.

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
`lvalue` Odkazu na buď `shared_ptr` nebo `weak_ptr`.

### <a name="remarks"></a>Poznámky

Šablony členské funkce vrátí hodnotu PRAVDA, pokud `*this` je `ordered before` `ptr`.

## <a name="reset"></a>  shared_ptr::Reset

Nahraďte vlastněný zdroj.

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

*Jiné*<br/>
Typ řízený ukazatelem argumentu.

*D*<br/>
Typ odstraňovače.

*ptr*<br/>
Ukazatel na kopii.

*dtor*<br/>
Odstraňovač pro kopírování.

*A*<br/>
Typ alokátoru.

*ALLOC*<br/>
Alokátor ke kopírování.

### <a name="remarks"></a>Poznámky

Všechny operátory snížen počet odkazů prostředku aktuálně vlastníkem `*this` a přiřazení vlastnictví prostředků s názvem podle sekvenci operandů pro `*this`. Pokud klesne počet odkazů na nulu, zdroj je uvolněn. Pokud se operátor nezdaří ponechá `*this` beze změny.

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

*Jiné*<br/>
Typ řízený ukazatelem argumentu.

*ptr*<br/>
Ukazatel na kopii.

*D*<br/>
Typ odstraňovače.

*A*<br/>
Typ alokátoru.

*dtor*<br/>
Odstraňovač.

*operátor*<br/>
Alokátor.

*SP*<br/>
Inteligentní ukazatel na kopii.

*webové části*<br/>
Slabý ukazatel.

*Asie a Tichomoří*<br/>
Automatický ukazatel na kopii.

### <a name="remarks"></a>Poznámky

Konstruktory jednotlivých vytvořit objekt, který vlastní prostředek s názvem podle sekvenci operandů. Konstruktor `shared_ptr(const weak_ptr<Other>& wp)` vyvolá objekt výjimky typu [bad_weak_ptr – třída](../standard-library/bad-weak-ptr-class.md) Pokud `wp.expired()`.

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

## <a name="dtorshared_ptr"></a>  shared_ptr –:: ~ shared_ptr

Odstraní `shared_ptr`.

```cpp
~shared_ptr();
```

### <a name="remarks"></a>Poznámky

Destruktor sníží počet odkazů prostředku aktuálně vlastníkem `*this`. Pokud klesne počet odkazů na nulu, zdroj je uvolněn.

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

Prohodí dva `shared_ptr` objekty.

```cpp
void swap(shared_ptr& sp);
```

### <a name="parameters"></a>Parametry

*SP*<br/>
Sdílený ukazatel na Prohodit s.

### <a name="remarks"></a>Poznámky

Členská funkce opustí prostředku původně vlastněné `*this` následně vlastněné *sp*a prostředky původně vlastněné *sp* následně vlastněné `*this`. Funkce nezmění počty odkazů pro tyto dva prostředky a nevyvolá žádné výjimky.

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

Testuje, zda je vlastněný zdroj jedinečný.

```cpp
bool unique() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí **true** Pokud žádné jiné `shared_ptr` objekt vlastníkem prostředku, který je vlastněn `*this`, jinak **false**.

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

Počítá vlastníky zdrojů.

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

## <a name="see-also"></a>Viz také:

[weak_ptr – třída](../standard-library/weak-ptr-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
