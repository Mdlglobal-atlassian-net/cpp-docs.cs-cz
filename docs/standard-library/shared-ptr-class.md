---
title: shared_ptr – třída
ms.date: 07/29/2019
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
ms.openlocfilehash: 59346dfded63aec315304f76c9bed753a4db1224
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682443"
---
# <a name="sharedptr-class"></a>shared_ptr – třída

Zabalí inteligentní ukazatel počítaný odkazy do dynamicky alokovaného objektu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class shared_ptr;
```

## <a name="remarks"></a>Poznámky

`shared_ptr` Třída popisuje objekt, který používá počítání odkazů pro správu prostředků. `shared_ptr` Objekt efektivně udržuje ukazatel na prostředek, který vlastní, nebo obsahuje nulový ukazatel. Prostředek může být vlastněn více než jedním `shared_ptr` objektem. Pokud je poslední `shared_ptr` objekt, který vlastní určitý prostředek, zničen, prostředek je uvolněn.

`shared_ptr` Zastaví vlastnictví prostředku při jeho přiřazení nebo resetování.

Argument `T` šablony může být neúplný typ s výjimkou případů uvedených pro určité členské funkce.

`T*` `G*` `shared_ptr<G>` `G*` Když je objektvytvořenzukazateleprostředkutypuneboz,musíbýttypukazatelepřevoditelnéna.`shared_ptr<T>` Pokud není převoditelné, kód nebude zkompilován. Příklad:

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

`shared_ptr` Objekt vlastní prostředek:

- Pokud byl vytvořen s ukazatelem na tento prostředek,

- Pokud byl vytvořen z `shared_ptr` objektu, který je vlastníkem tohoto prostředku,

- Pokud byl vytvořen z objektu [weak_ptr](weak-ptr-class.md) , který odkazuje na tento prostředek, nebo

- Pokud je vlastnictví tohoto prostředku přiřazeno, buď pomocí [shared_ptr:: operator =](#op_eq) , nebo voláním členské funkce [shared_ptr:: Reset](#reset).

`shared_ptr` Objekty, které vlastní prostředek, sdílí řídicí blok. Řídicí blok obsahuje:

- počet `shared_ptr` objektů, které prostředek vlastní,

- počet `weak_ptr` objektů, které odkazují na prostředek,

- Odstranit pro daný prostředek, pokud má nějaký,

- vlastní Alokátor pro řídicí blok, pokud má jeden.

`shared_ptr` Objekt, který je inicializován pomocí nulového ukazatele, má řídicí blok a není prázdný. Poté, co objekt uvolní prostředek, již není vlastníkem tohoto prostředku. `shared_ptr` Poté, co objekt uvolní prostředek, již neukazuje na tento prostředek. `weak_ptr`

Pokud je počet `shared_ptr` objektů, které prostředek vlastní, nulový, prostředek se uvolní, protože ho odstraní nebo předáte jeho adresu na odstranění, a to v závislosti na tom, jak bylo vlastnictví prostředku původně vytvořené. Pokud je počet `shared_ptr` objektů, které prostředek vlastní, nula, a `weak_ptr` počet objektů, které odkazují na tento prostředek, je nulový, řídicí blok je uvolněn pomocí vlastního přidělujícího ovládacího prvku pro řídicí blok, pokud má jeden.

Prázdný `shared_ptr` objekt nevlastní žádné prostředky a nemá žádný řídicí blok.

Odstranění je objekt funkce, který má členskou funkci `operator()`. Jeho typ musí být kopírovací constructible a jeho kopírovací konstruktor a destruktor nesmí vyvolávat výjimky. Přijímá jeden parametr, objekt, který má být odstraněn.

Některé funkce přebírají seznam argumentů, který definuje vlastnosti výsledného `shared_ptr<T>` objektu `weak_ptr<T>` nebo. Takový seznam argumentů můžete zadat několika způsoby:

žádné argumenty – výsledný objekt je prázdný `shared_ptr` objekt nebo prázdný `weak_ptr` objekt.

`ptr`– ukazatel typu `Other*` na prostředek, který se má spravovat. `T`musí být úplný typ. Pokud dojde k chybě funkce (protože řídicí blok nelze přidělit), vyhodnotí výraz `delete ptr`.

`ptr, deleter`– ukazatel typu `Other*` na prostředek, který se má spravovat, a odstranění pro daný prostředek. Pokud dojde k chybě funkce (protože nelze přidělit řídicí blok), volá `deleter(ptr)`, což musí být jasně definované.

`ptr, deleter, alloc`– ukazatel typu `Other*` na prostředek, který se má spravovat, odstranit pro daný prostředek a přidělující modul pro správu úložiště, které se musí přidělit a uvolnit. Pokud dojde k chybě funkce (protože nelze přidělit řídicí blok), volá `deleter(ptr)`, což musí být jasně definované.

`sp`-- `shared_ptr<Other>` objekt, který je vlastníkem prostředku, který se má spravovat.

`wp`-- `weak_ptr<Other>` objekt, který odkazuje na prostředek, který se má spravovat.

`ap`-- `auto_ptr<Other>` objekt, který obsahuje ukazatel na prostředek, který se má spravovat. Pokud je funkce úspěšná, volá `ap.release()`se. v opačném `ap` případě nezůstane beze změny.

Ve všech případech musí být typ `Other*` ukazatele převoditelné na. `T*`

## <a name="thread-safety"></a>Bezpečnost vlákna

Více vláken může současně číst a zapisovat `shared_ptr` různé objekty, i když jsou objekty kopírovány, které sdílejí vlastnictví.

## <a name="members"></a>Členové

|||
|-|-|
| **Konstruktory** | |
|[shared_ptr](#shared_ptr)|`shared_ptr`Vytvoří.|
|[~ shared_ptr](#dtorshared_ptr)|`shared_ptr`Zničí.|
| **Definice typedef** | |
|[element_type](#element_type)|Typ prvku|
|[weak_type](#weak_type)|Typ slabého ukazatele na prvek.|
| **Členské funkce** | |
|[get](#get)|Načte adresu vlastněné prostředku.|
|[owner_before](#owner_before)|Vrátí hodnotu true, `shared_ptr` Pokud je tato hodnota řazena před (nebo je menší než) poskytnutý ukazatel.|
|[reset](#reset)|Nahraďte vlastněný prostředek.|
|[swap](#swap)|Zamění dva `shared_ptr` objekty.|
|[unique](#unique)|Testuje, zda je vlastní prostředek jedinečný.|
|[use_count](#use_count)|Počítá počty vlastníků prostředků.|
| **Operátory** | |
|[operátor bool](#op_bool)|Testuje, zda existuje vlastněný prostředek.|
|[podnikatel](#op_star)|Získá určenou hodnotu.|
|[operátor =](#op_eq)|Nahradí vlastněný prostředek.|
|[podnikatel&gt;](#op_arrow)|Získá ukazatel na určenou hodnotu.|

## <a name="element_type"></a>element_type

Typ prvku

```cpp
typedef T element_type;                  // before C++17
using element_type = remove_extent_t<T>; // C++17
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr `T`šablony. `element_type`

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

## <a name="get"></a>Čtěte

Načte adresu vlastněné prostředku.

```cpp
element_type* get() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrací adresu vlastněné prostředku. Pokud objekt nevlastní prostředek, vrátí hodnotu 0.

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

## <a name="op_bool"></a>operátor bool

Testuje, zda existuje vlastněný prostředek.

```cpp
explicit operator bool() const noexcept;
```

### <a name="remarks"></a>Poznámky

Operátor vrátí hodnotu **true** , pokud `get() != nullptr`v opačném případě **false**.

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

## <a name="op_star"></a>podnikatel

Získá určenou hodnotu.

```cpp
T& operator*() const noexcept;
```

### <a name="remarks"></a>Poznámky

Operátor dereference vrátí `*get()`. Proto nesmí mít uložený ukazatel hodnotu null.

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

## <a name="op_eq"></a>operátor =

Nahradí vlastněný prostředek.

```cpp
shared_ptr& operator=(const shared_ptr& sp) noexcept;

shared_ptr& operator=(shared_ptr&& sp) noexcept;

template <class Other>
shared_ptr& operator=(const shared_ptr<Other>& sp) noexcept;

template <class Other>
shared_ptr& operator=(shared_ptr<Other>&& sp) noexcept;

template <class Other>
shared_ptr& operator=(auto_ptr<Other>&& ap);    // deprecated in C++11, removed in C++17

template <class Other, class Deleter>
shared_ptr& operator=(unique_ptr<Other, Deleter>&& up);
```

### <a name="parameters"></a>Parametry

*SP*\
Sdílený ukazatel, ze kterého se má kopírovat nebo přesunout.

*amortizac*\
Automatický ukazatel, který se má přesunout `auto_ptr` Přetížení je zastaralé v c++ 11 a odebráno v c++ 17.

*následn*\
Jedinečný ukazatel na objekt pro přijetí vlastnictví. Po volání *nevlastní žádný* objekt.

*Jiná*\
Typ objektu, na který odkazovalo pomocí *SP*, *AP*nebo *up*.

*Deleter*\
Typ odstranění vlastněného objektu, který je uložen pro pozdější odstranění objektu.

### <a name="remarks"></a>Poznámky

Všechny operátory snižují počet odkazů pro prostředek, který je aktuálně vlastníkem `*this` , a přiřazují vlastnictví prostředku, který `*this`je pojmenován sekvencí operandu. Pokud počet odkazů klesne na nulu, prostředek se uvolní. Pokud operátor dojde k chybě, zůstane `*this` beze změny.

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
    std::unique_ptr<int> up(new int(10));

    sp0 = sp1;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    sp0 = up;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
*sp0 == 10
```

## <a name="op_arrow"></a>operátor->

Získá ukazatel na určenou hodnotu.

```cpp
T* operator->() const noexcept;
```

### <a name="remarks"></a>Poznámky

Operátor `get()`výběru vrátí, takže se výraz `(sp.get())->member` `sp->member` chová stejně jako `sp` objekt třídy `shared_ptr<T>`. Proto nesmí mít uložený ukazatel hodnotu null a `T` musí se jednat o typ třídy, struktury nebo sjednocení s členem. `member`

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

## <a name="owner_before"></a>owner_before

Vrátí hodnotu true, `shared_ptr` Pokud je tato hodnota řazena před (nebo je menší než) poskytnutý ukazatel.

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr) const noexcept;

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr) const noexcept;
```

### <a name="parameters"></a>Parametry

*střed*\
Odkaz l-hodnotu na `shared_ptr` `weak_ptr`nebo.

### <a name="remarks"></a>Poznámky

Členská funkce šablony vrátí hodnotu true `*this` , pokud je `ptr`seřazena před.

## <a name="reset"></a>nové

Nahraďte vlastněný prostředek.

```cpp
void reset() noexcept;

template <class Other>
void reset(Other *ptr);

template <class Other, class Deleter>
void reset(
    Other *ptr,
    Deleter deleter);

template <class Other, class Deleter, class Allocator>
void reset(
    Other *ptr,
    Deleter deleter,
    Allocator alloc);
```

### <a name="parameters"></a>Parametry

*Jiná*\
Typ řízený ukazatelem argumentu.

*Deleter*\
Typ odstranění.

*střed*\
Ukazatel, který se má zkopírovat

*Deleter*\
Odstranění, které se má zkopírovat

*Dělující*\
Typ přidělování.

*vyhrazen*\
Alokátor ke kopírování.

### <a name="remarks"></a>Poznámky

Všechny operátory snižují počet odkazů pro prostředek, který je aktuálně vlastníkem `*this` , a přiřazují vlastnictví prostředku, který `*this`je pojmenován sekvencí operandu. Pokud počet odkazů klesne na nulu, prostředek se uvolní. Pokud operátor dojde k chybě, zůstane `*this` beze změny.

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

## <a name="shared_ptr"></a>shared_ptr

`shared_ptr`Vytvoří.

```cpp
constexpr shared_ptr() noexcept;

constexpr shared_ptr(nullptr_t) noexcept : shared_ptr() {}

shared_ptr(const shared_ptr& sp) noexcept;

shared_ptr(shared_ptr&& sp) noexcept;

template <class Other>
explicit shared_ptr(Other* ptr);

template <class Other, class Deleter>
shared_ptr(
    Other* ptr,
    Deleter deleter);

template <class Deleter>
shared_ptr(
    nullptr_t ptr,
    Deleter deleter);

template <class Other, class Deleter, class Allocator>
shared_ptr(
    Other* ptr,
    Deleter deleter,
    Allocator alloc);

template <class Deleter, class Allocator>
shared_ptr(
    nullptr_t ptr,
    Deleter deleter,
    Allocator alloc);

template <class Other>
shared_ptr(
    const shared_ptr<Other>& sp) noexcept;

template <class Other>
explicit shared_ptr(
    const weak_ptr<Other>& wp);

template <class &>
shared_ptr(
    std::auto_ptr<Other>& ap);

template <class &>
shared_ptr(
    std::auto_ptr<Other>&& ap);

template <class Other, class Deleter>
shared_ptr(
    unique_ptr<Other, Deleter>&& up);

template <class Other>
shared_ptr(
    const shared_ptr<Other>& sp,
    element_type* ptr) noexcept;

template <class Other>
shared_ptr(
    shared_ptr<Other>&& sp,
    element_type* ptr) noexcept;

template <class Other, class Deleter>
shared_ptr(
    const unique_ptr<Other, Deleter>& up) = delete;
```

### <a name="parameters"></a>Parametry

*Jiná*\
Typ řízený ukazatelem argumentu.

*střed*\
Ukazatel, který se má zkopírovat

*Deleter*\
Typ odstranění.

*Dělující*\
Typ přidělování.

*Deleter*\
Odstraní se.

*vyhrazen*\
Alokátor.

*SP*\
Inteligentní ukazatel, který se má zkopírovat

*požadavku*\
Slabý ukazatel.

*amortizac*\
Automatický ukazatel, který se má zkopírovat

### <a name="remarks"></a>Poznámky

Jednotlivé konstruktory vytvoří objekt, který vlastní prostředek pojmenovaný sekvencí operandu. Konstruktor `shared_ptr(const weak_ptr<Other>& wp)` vyvolá výjimku objektu typu [bad_weak_ptr](bad-weak-ptr-class.md) IF `wp.expired()`.

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

## <a name="dtorshared_ptr"></a>~ shared_ptr

`shared_ptr`Zničí.

```cpp
~shared_ptr();
```

### <a name="remarks"></a>Poznámky

Destruktor snižuje počet odkazů pro prostředek, který aktuálně vlastní `*this`. Pokud počet odkazů klesne na nulu, prostředek se uvolní.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_destroy.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="swap"></a>adresu

Zamění dva `shared_ptr` objekty.

```cpp
void swap(shared_ptr& sp) noexcept;
```

### <a name="parameters"></a>Parametry

*SP*\
Sdílený ukazatel pro prohození.

### <a name="remarks"></a>Poznámky

Členská funkce ponechá prostředek, který `*this` je původně vlastněn nástrojem *SP*, a prostředek původně patřící *aktualizaci SP* následně vlastní. `*this` Funkce nemění počty odkazů pro tyto dva prostředky a nevyvolá žádné výjimky.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="unique"></a>tabulka

Testuje, zda je vlastní prostředek jedinečný. Tato funkce se v C++ 17 nepoužívá a odebrala se v C++ 20.

```cpp
bool unique() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí **hodnotu true** `*this`, pokud `shared_ptr` žádný jiný objekt nevlastní prostředek, který je vlastněn, jinak **false**.

### <a name="example"></a>Příklad

```cpp
// std__memory__shared_ptr_unique.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="use_count"></a>use_count

Počítá počty vlastníků prostředků.

```cpp
long use_count() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet `shared_ptr` objektů, které vlastní prostředek, který je `*this`vlastníkem.

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

## <a name="weak_type"></a>weak_type

Typ slabého ukazatele na prvek.

```cpp
using weak_type = weak_ptr<T>; // C++17
```

### <a name="remarks"></a>Poznámky

`weak_type` Definice byla přidána do c++ 17.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](cpp-standard-library-header-files.md)\
[\<> paměti](memory.md)\
[unique_ptr](unique-ptr-class.md)\
[weak_ptr – třída](weak-ptr-class.md)
