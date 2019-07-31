---
title: weak_ptr – třída
ms.date: 07/29/2019
f1_keywords:
- memory/std::weak_ptr
- memory/std::weak_ptr::element_type
- memory/std::weak_ptr::expired
- memory/std::weak_ptr::lock
- memory/std::weak_ptr::owner_before
- memory/std::weak_ptr::reset
- memory/std::weak_ptr::swap
- memory/std::weak_ptr::use_count
- memory/std::weak_ptr::operator=
helpviewer_keywords:
- std::weak_ptr [C++]
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
ms.openlocfilehash: d4ba30f737bc570a4ee700b3a317b5feebe8a50a
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682412"
---
# <a name="weakptr-class"></a>weak_ptr – třída

Zalomí slabě propojený ukazatel.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T> class weak_ptr;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ řízený slabým ukazatelem.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který odkazuje na prostředek, který je spravován jedním nebo více [shared_ptr](shared-ptr-class.md) objekty. `weak_ptr` Objekty, které ukazují na prostředek, nemají vliv na počet odkazů prostředku. Když je poslední `shared_ptr` objekt, který spravuje tento prostředek, zničen, prostředek bude uvolněn i v případě `weak_ptr` , že objekty odkazují na tento prostředek. Toto chování je nezbytné pro předcházení cyklům v datových strukturách.

Objekt odkazuje na prostředek, pokud byl vytvořen `shared_ptr` z objektu, který je vlastníkem tohoto prostředku, pokud byl vytvořen z `weak_ptr` objektu, který odkazuje na tento prostředek, nebo pokud byl tento prostředek přiřazen pomocí operátoru [=](#op_eq). `weak_ptr` `weak_ptr` Objekt neposkytuje přímý přístup k prostředku, na který odkazuje. Kód, který potřebuje použít prostředek, prochází pomocí `shared_ptr` objektu, který vlastní daný prostředek, vytvořený voláním [zámku](#lock)členské funkce. Vypršela platnost `shared_ptr` objektu,pokudbylprostředek,nakterýukazuje,uvolněn,protoževšechnyobjekty,kteréprostředekvlastní,`weak_ptr` byly zničeny. `lock` Volání`weak_ptr` na objekt, jehož platnost vypršela, vytvoří prázdný objekt shared_ptr.

Prázdný objekt weak_ptr odkazuje na žádné prostředky a nemá žádný řídicí blok. Jeho členská `lock` funkce vrátí prázdný objekt shared_ptr.

K cyklu dochází, když dva nebo více prostředků řízených `shared_ptr` objekty podrží vzájemně `shared_ptr` odkazující objekty. Například cyklický propojený seznam se třemi prvky má `N0`hlavní uzel; tento uzel `shared_ptr` obsahuje objekt, který vlastní další uzel, `N1`; tento uzel obsahuje `shared_ptr` objekt, který je vlastníkem dalšího uzlu, `N2`; tento uzel v Zajistěte, `shared_ptr` aby byl objekt vlastnící hlavní uzel, `N0`a uzavřel cyklus. V této situaci se nepočítá reference nikdy nula a uzly v cyklu se nikdy neuvolňují. Chcete-li odstranit cyklus, měl by `N2` poslední uzel `weak_ptr` obsahovat objekt `shared_ptr` odkazující na `N0` místo objektu. Vzhledem k tomu, že `N0` `N0`objekt nevlastní, nemá vliv na počet odkazů a když je poslední odkaz na hlavní uzel zničen, uzly v seznamu budou také zničeny. `weak_ptr`

## <a name="members"></a>Členové

|||
|-|-|
| **Konstruktory** | |
|[weak_ptr](#weak_ptr)|`weak_ptr`Vytvoří.|
| **Destruktory** | |
|[~ weak_ptr](#tilde-weak_ptr)|`weak_ptr`Vytvoří.|
| **Definice typedef** | |
|[element_type](#element_type)|Typ elementu.|
| **Členské funkce** | |
|[vypršela](#expired)|Testuje, jestli vypršela platnost vlastnictví.|
|[lock](#lock)|Získá exkluzivní vlastnictví prostředku.|
|[owner_before](#owner_before)|Vrátí **hodnotu true** , `weak_ptr` Pokud je tato hodnota řazena před (nebo je menší než) poskytnutý ukazatel.|
|[reset](#reset)|Vydává vlastní prostředek.|
|[swap](#swap)|Zamění dva `weak_ptr` objekty.|
|[use_count](#use_count)|Spočítá počet `shared_ptr` objektů.|
| **Operátory** | |
|[operátor =](#op_eq)|Nahradí vlastněný prostředek.|

## <a name="element_type"></a>element_type

Typ elementu.

```cpp
typedef T element_type; // through C++17
using element_type = remove_extent_t<T>; // C++20
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr `T`šablony.

### <a name="example"></a>Příklad

```cpp
// std__memory__weak_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::weak_ptr<int>::element_type val = *wp0.lock();

    std::cout << "*wp0.lock() == " << val << std::endl;

    return (0);
}
```

```Output
*wp0.lock() == 5
```

## <a name="expired"></a>vypršela

Testuje, jestli vypršela platnost vlastnictví, což znamená, že odkazovaný objekt byl odstraněn.

```cpp
bool expired() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí **hodnotu true** , pokud `*this` vypršela platnost, v opačném případě **false**.

### <a name="example"></a>Příklad

```cpp
// std__memory__weak_ptr_expired.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="lock"></a>získáte

Získá objekt `shared_ptr` , který sdílí vlastnictví prostředku.

```cpp
shared_ptr<T> lock() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí prázdný objekt [shared_ptr](shared-ptr-class.md) , pokud `*this` vypršela platnost. `shared_ptr<T>` v opačném případě vrátí objekt, který je `*this` vlastníkem prostředku, na který odkazuje. Vrátí hodnotu ekvivalentu atomového spuštění `expired() ? shared_ptr<T>() : shared_ptr<T>(*this)`.

### <a name="example"></a>Příklad

```cpp
// std__memory__weak_ptr_lock.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="op_eq"></a>operátor =

Nahradí vlastněný prostředek.

```cpp
weak_ptr& operator=(const weak_ptr& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const weak_ptr<Other>& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const shared_ptr<Other>& ptr) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiná*\
Typ řízený argumentem Shared nebo slabý ukazatel.

*střed*\
Slabý ukazatel nebo sdílený ukazatel na kopírování.

### <a name="remarks"></a>Poznámky

Všechny operátory vydávají prostředky, na `*this` které aktuálně odkazuje, a přiřadí vlastnictví prostředku s názvem *PTR* na. `*this` Pokud operátor dojde k chybě, zůstane `*this` beze změny. Každý operátor má efekt podobný `weak_ptr(ptr).swap(*this)`.

### <a name="example"></a>Příklad

```cpp
// std__memory__weak_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::shared_ptr<int> sp1(new int(10));
    wp0 = sp1;
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::weak_ptr<int> wp1;
    wp1 = wp0;
    std::cout << "*wp1.lock() == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*wp0.lock() == 5
*wp0.lock() == 10
*wp1.lock() == 10
```

## <a name="owner_before"></a>owner_before

Vrátí **hodnotu true** , `weak_ptr` Pokud je tato hodnota řazena před (nebo je menší než) poskytnutý ukazatel.

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

Členská funkce šablony vrátí **hodnotu true** , pokud `*this` je seřazena před *PTR*.

## <a name="reset"></a>nové

Uvolní vlastněný prostředek.

```cpp
void reset() noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce uvolní prostředek, na `*this` který odkazoval, a převede `*this` ho na prázdný `weak_ptr` objekt.

### <a name="example"></a>Příklad

```cpp
// std__memory__weak_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp(new int(5));
    std::weak_ptr<int> wp(sp);
    std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    wp.reset();
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    return (0);
}
```

```Output
*wp.lock() == 5
wp.expired() == false
wp.expired() == true
```

## <a name="swap"></a>adresu

Zamění dva `weak_ptr` objekty.

```cpp
void swap(weak_ptr& wp) noexcept;
```

Zahrnuje také specializaci:

```cpp
template<class T>
void swap(weak_ptr<T>& a, weak_ptr<T>& b) noexcept;
```

### <a name="parameters"></a>Parametry

*požadavku*\
Slabý ukazatel pro prohození.

### <a name="remarks"></a>Poznámky

`*this` `*this`Po, prostředek, na který byl původně odkazován, odkazuje na položku WP a prostředek původně na něj odkazovala na odkaz. `swap` Funkce nemění počty odkazů pro tyto dva prostředky a nevyvolá žádné výjimky. Účinek specializace šablony je ekvivalentem `a.swap(b)`.

### <a name="example"></a>Příklad

```cpp
// std__memory__weak_ptr_swap.cpp
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

## <a name="use_count"></a>use_count

Spočítá počet `shared_ptr` objektů, které vlastní sdílený prostředek.

```cpp
long use_count() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet `shared_ptr` objektů, `*this`na které se odkazuje prostředek, na který odkazuje.

### <a name="example"></a>Příklad

```cpp
// std__memory__weak_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    return (0);
}
```

```Output
wp.use_count() == 1
wp.use_count() == 2
```

## <a name="weak_ptr"></a>weak_ptr

`weak_ptr`Vytvoří.

```cpp
constexpr weak_ptr() noexcept;

weak_ptr(const weak_ptr& wp) noexcept;

weak_ptr(weak_ptr&& wp) noexcept;

template <class Other>
weak_ptr(const weak_ptr<Other>& wp) noexcept;

template <class Other>
weak_ptr(weak_ptr<Other>&& sp) noexcept;

template <class Other>
weak_ptr(const shared_ptr<Other>& sp) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiná*\
Typ řízený argumentem Shared/slabé. Tyto konstruktory nejsou součástí řešení přetížení, pokud _není\* jiné_ kompatibilní s `element_type*`.

*požadavku*\
Slabý ukazatel, který se má kopírovat.

*SP*\
Sdílený ukazatel, který se má zkopírovat

### <a name="remarks"></a>Poznámky

Výchozí konstruktor vytvoří prázdný `weak_ptr` objekt. Konstruktory, které přebírají argument jednotlivé konstrukce prázdného `weak_ptr` objektu, pokud je ukazatel argumentu prázdný. Jinak vytvoří `weak_ptr` objekt, který odkazuje na prostředek pojmenovaný argumentem. Počet odkazů sdíleného objektu se nezmění.

### <a name="example"></a>Příklad

```cpp
// std__memory__weak_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp0;
    std::cout << "wp0.expired() == " << std::boolalpha
        << wp0.expired() << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp1(sp1);
    std::cout << "*wp1.lock() == "
        << *wp1.lock() << std::endl;

    std::weak_ptr<int> wp2(wp1);
    std::cout << "*wp2.lock() == "
        << *wp2.lock() << std::endl;

    return (0);
}
```

```Output
wp0.expired() == true
*wp1.lock() == 5
*wp2.lock() == 5
```

## <a name="tilde-weak_ptr"></a>~ weak_ptr

`weak_ptr`Zničí.

```cpp
~weak_ptr();
```

### <a name="remarks"></a>Poznámky

Destruktor zničí toto `weak_ptr` , ale nemá žádný vliv na počet odkazů objektu, na který ukazuje ukazatel na.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](cpp-standard-library-header-files.md)\
[\<> paměti](memory.md)\
[shared_ptr – třída](shared-ptr-class.md)
