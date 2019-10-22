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
ms.openlocfilehash: 2591c4cd124f83085235828d3eb29ab1a90d894a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684076"
---
# <a name="weak_ptr-class"></a>weak_ptr – třída

Zalomí slabě propojený ukazatel.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T> class weak_ptr;
```

### <a name="parameters"></a>Parametry

*T* \
Typ řízený slabým ukazatelem.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který odkazuje na prostředek, který je spravován jedním nebo více [shared_ptr](shared-ptr-class.md) objekty. @No__t_0 objektů, které ukazují na prostředek, nemá vliv na počet odkazů prostředku. Po zničení posledního `shared_ptr` objektu, který spravuje tento prostředek, se uvolní i v případě, že se k tomuto prostředku odkazují objekty `weak_ptr`. Toto chování je nezbytné pro předcházení cyklům v datových strukturách.

Objekt `weak_ptr` odkazuje na prostředek, pokud byl vytvořen z objektu `shared_ptr`, který je vlastníkem tohoto prostředku, pokud byl vytvořen z objektu `weak_ptr`, který odkazuje na tento prostředek, nebo pokud byl tento prostředek přiřazen pomocí [operátoru =](#op_eq). Objekt `weak_ptr` neposkytuje přímý přístup k prostředku, na který odkazuje. Kód, který potřebuje použít prostředek, provede prostřednictvím objektu `shared_ptr`, který vlastní tento prostředek, vytvořený voláním [zámku](#lock)členské funkce. K objektu `weak_ptr` vypršela platnost, pokud byl prostředek, na který ukazuje, uvolněn, protože všechny objekty `shared_ptr`, které prostředek vlastní, byly zničeny. Volání `lock` na objektu `weak_ptr`, jehož platnost vypršela, vytvoří prázdný objekt shared_ptr.

Prázdný objekt weak_ptr odkazuje na žádné prostředky a nemá žádný řídicí blok. Jeho členská funkce `lock` vrátí prázdný objekt shared_ptr.

K cyklu dochází, když dva nebo více prostředků, které jsou ovládány `shared_ptr` objekty, se vzájemně odkazují na `shared_ptr` objekty. Například cyklický propojený seznam se třemi prvky má hlavní uzel `N0`; Tento uzel obsahuje objekt `shared_ptr`, který vlastní další uzel, `N1`; Tento uzel obsahuje objekt `shared_ptr`, který vlastní další uzel, `N2`; Tento uzel zase obsahuje objekt `shared_ptr`, který vlastní hlavní uzel, `N0` a zavírá cyklus. V této situaci se nepočítá reference nikdy nula a uzly v cyklu se nikdy neuvolňují. Aby se cyklus vyloučil, měl by poslední uzel `N2` obsahovat objekt `weak_ptr` odkazující na `N0` namísto objektu `shared_ptr`. Vzhledem k tomu, že objekt `weak_ptr` nevlastní `N0` nemá vliv na počet odkazů `N0` a když je poslední odkaz na hlavní uzel zničen, uzly v seznamu budou také zničeny.

## <a name="members"></a>Členové

|||
|-|-|
| **Konstruktory** | |
|[weak_ptr](#weak_ptr)|Vytvoří `weak_ptr`.|
| **Destruktory** | |
|[~ weak_ptr](#tilde-weak_ptr)|Vytvoří `weak_ptr`.|
| **Definice typedef** | |
|[element_type](#element_type)|Typ elementu.|
| **Členské funkce** | |
|[vypršela](#expired)|Testuje, jestli vypršela platnost vlastnictví.|
|[lock](#lock)|Získá exkluzivní vlastnictví prostředku.|
|[owner_before](#owner_before)|Vrátí **hodnotu true** , pokud je tato `weak_ptr` seřazena před (nebo je menší než) poskytnutý ukazatel.|
|[nové](#reset)|Vydává vlastní prostředek.|
|[adresu](#swap)|Zamění dva objekty `weak_ptr`.|
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

Typ je synonymum pro parametr šablony `T`.

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

Členská funkce vrátí **hodnotu true** , pokud vypršela platnost `*this`, v opačném případě **false**.

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

Získá `shared_ptr`, který sdílí vlastnictví prostředku.

```cpp
shared_ptr<T> lock() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí prázdný objekt [shared_ptr](shared-ptr-class.md) , pokud vypršela platnost `*this`. v opačném případě vrátí objekt `shared_ptr<T>`, který vlastní prostředek, na který `*this` odkazuje. Vrátí hodnotu odpovídající atomovém spuštění `expired() ? shared_ptr<T>() : shared_ptr<T>(*this)`.

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

*Jiné* \
Typ řízený argumentem Shared nebo slabý ukazatel.

\ *PTR*
Slabý ukazatel nebo sdílený ukazatel na kopírování.

### <a name="remarks"></a>Poznámky

Všechny tyto operátory vydávají prostředek, na který aktuálně odkazuje `*this` a přiřazují vlastnictví prostředku s názvem *PTR* na `*this`. Pokud operátor dojde k chybě, opustí `*this` beze změny. Každý operátor má efekt podobný `weak_ptr(ptr).swap(*this)`.

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

Vrátí **hodnotu true** , pokud je tato `weak_ptr` seřazena před (nebo je menší než) poskytnutý ukazatel.

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr) const noexcept;

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr) const noexcept;
```

### <a name="parameters"></a>Parametry

\ *PTR*
Odkaz lvalue buď na `shared_ptr`, nebo na `weak_ptr`.

### <a name="remarks"></a>Poznámky

Členská funkce šablony vrátí **hodnotu true** , pokud je `*this` seřazena před *PTR*.

## <a name="reset"></a>nové

Uvolní vlastněný prostředek.

```cpp
void reset() noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce uvolní prostředek, na který odkazoval, pomocí `*this` a převede `*this` na prázdný objekt `weak_ptr`.

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

Zamění dva objekty `weak_ptr`.

```cpp
void swap(weak_ptr& wp) noexcept;
```

Zahrnuje také specializaci:

```cpp
template<class T>
void swap(weak_ptr<T>& a, weak_ptr<T>& b) noexcept;
```

### <a name="parameters"></a>Parametry

\ *WP*
Slabý ukazatel pro prohození.

### <a name="remarks"></a>Poznámky

Po `swap` prostředek, na který se původně odkazovalo pomocí `*this`, odkazuje na *WP*a zdroj, na který se původně odkazoval pomocí *WP* , ukazuje na `*this`. Funkce nemění počty odkazů pro tyto dva prostředky a nevyvolá žádné výjimky. Účinek specializace šablony je ekvivalentem `a.swap(b)`.

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

Členská funkce vrátí počet `shared_ptr` objektů, na které se odkazuje prostředek, na který odkazuje `*this`.

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

Vytvoří `weak_ptr`.

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

*Jiné* \
Typ řízený argumentem Shared/slabé. Tyto konstruktory nejsou součástí řešení přetížení, pokud nejsou _jiné \*_ kompatibilní s `element_type*`.

\ *WP*
Slabý ukazatel, který se má kopírovat.

\ *SP*
Sdílený ukazatel, který se má zkopírovat

### <a name="remarks"></a>Poznámky

Výchozí konstruktor vytvoří prázdný objekt `weak_ptr`. Konstruktory, které přebírají argument každý vytvoří prázdný objekt `weak_ptr`, pokud ukazatel argumentu je prázdný. Jinak vytvoří objekt `weak_ptr`, který odkazuje na prostředek pojmenovaný argumentem. Počet odkazů sdíleného objektu se nezmění.

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

Zničí `weak_ptr`.

```cpp
~weak_ptr();
```

### <a name="remarks"></a>Poznámky

Destruktor zničí toto `weak_ptr`, ale nemá žádný vliv na počet odkazů objektu, na který odkazuje ukazatel na.

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](cpp-standard-library-header-files.md)
[\<memory >](memory.md) \
[shared_ptr – třída](shared-ptr-class.md)
