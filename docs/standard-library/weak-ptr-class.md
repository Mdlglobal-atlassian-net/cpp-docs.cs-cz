---
title: weak_ptr – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 79869773591eee0a85cbc752be246bedb783bad2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462982"
---
# <a name="weakptr-class"></a>weak_ptr – třída

Zalomí slabě propojený ukazatel.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _Ty>
   class weak_ptr {
public:
   typedef Ty element_type;
   weak_ptr();
   weak_ptr(const weak_ptr&);
   template <class Other>
      weak_ptr(const weak_ptr<Other>&);
   template <class Other>
      weak_ptr(const shared_ptr<Other>&);
   weak_ptr& operator=(const weak_ptr&);
   template <class Other>
      weak_ptr& operator=(const weak_ptr<Other>&);
   template <class Other>
      weak_ptr& operator=(shared_ptr<Other>&);
   void swap(weak_ptr&);
   void reset();
   long use_count() const;
   bool expired() const;
   shared_ptr<Ty> lock() const;
   };
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ řízený slabý ukazatel.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který ukazuje na prostředek, který je spravovaný jedním nebo několika [shared_ptr – třída](../standard-library/shared-ptr-class.md) objekty. `weak_ptr` Objekty, které odkazují na prostředek nemají vliv na počet odkazů prostředku. Proto když poslední `shared_ptr` objekt, který spravuje tento prostředek je zničen prostředek bude uvolněn, i když nejsou `weak_ptr` objekty odkazující na tento prostředek. To je nezbytné pro předcházení cykly v datové struktury.

A `weak_ptr` objektu odkazuje na prostředek, pokud byl vytvořen z `shared_ptr` objekt, který vlastní prostředek, pokud byl vytvořen z `weak_ptr` objekt, který ukazuje na prostředek, nebo pokud se tento prostředek byl přiřazen přes [ operátor =](#op_eq). A `weak_ptr` objekt neposkytuje přímý přístup k prostředku, který odkazuje. Kód, který je potřeba použít na prostředek se tak prostřednictvím `shared_ptr` objekt, který vlastní prostředek, vytvořen voláním členské funkce [Zámek](#lock). A `weak_ptr` objekt vypršela platnost, když prostředek, který odkazuje na bylo uvolněno, protože všechny `shared_ptr` zničení objektů, které vlastní prostředek. Volání `lock` na `weak_ptr` shared_ptr prázdný objekt vytvoří objekt, kterému vypršela platnost.

Weak_ptr – prázdný objekt neodkazuje na žádné prostředky a nemá žádný řídicí blok. Jeho členskou funkci `lock` vrátí shared_ptr prázdný objekt.

Cyklus nastane, pokud dva nebo více zdrojů řídí `shared_ptr` objektů, podržte vzájemně odkazující na `shared_ptr` objekty. Cyklické propojený seznam se třemi prvky má například hlavní uzel `N0`; obsahuje tento uzel `shared_ptr` objekt, který je vlastníkem další uzel `N1`; tento uzel obsahuje `shared_ptr` objekt, který je vlastníkem další uzel `N2`; tento uzel v Zapněte, blokování `shared_ptr` objekt, který je vlastníkem hlavního uzlu `N0`, zavírání cyklu. V takovém případě žádné počty odkazů se někdy stane nula a uzlů v cyklu se neuvolní. A Eliminujte zacyklení, poslední uzel `N2` uchovávat `weak_ptr` odkazuje `N0` místo `shared_ptr` objektu. Protože `weak_ptr` není vlastníkem objektu `N0` nemá vliv `N0`společnosti odkazovat na počtu a při zničení programu poslední odkaz k hlavnímu uzlu uzly v seznamu budou také zničena.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[weak_ptr](#weak_ptr)|Vytvoří `weak_ptr`.|

### <a name="methods"></a>Metody

|||
|-|-|
|[element_type](#element_type)|Typ elementu.|
|[Vypršela platnost](#expired)|Testuje, zda je vlastnictví vypršela platnost.|
|[lock](#lock)|Získá výhradní vlastnictví prostředku.|
|[owner_before –](#owner_before)|Vrátí **true** tato `weak_ptr` je řazen před (nebo menší než) poskytnutý ukazatel.|
|[Resetovat](#reset)|Verze vlastněný zdroj.|
|[Prohození](#swap)|Prohodí dva `weak_ptr` objekty.|
|[use_count –](#use_count)|Určený počet počty `shared_ptr` objekty.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Nahradí vlastněný zdroj.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** std

## <a name="element_type"></a>  ELEMENT_TYPE

Typ elementu.

```cpp
typedef Ty element_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Ty`.

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

## <a name="expired"></a>  Vypršela platnost

Testuje, zda je vlastnictví vypršela platnost.

```cpp
bool expired() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí **true** Pokud `*this` vypršela, jinak **false**.

### <a name="example"></a>Příklad

```cpp
// std__memory__weak_ptr_expired.cpp
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

## <a name="lock"></a>  Zámek

Získá výhradní vlastnictví prostředku.

```cpp
shared_ptr<Ty> lock() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí prázdný shared_ptr objektu, pokud `*this` vypršela platnost; v opačném případě vrátí [shared_ptr – třída](../standard-library/shared-ptr-class.md)\<Ty > objekt, který vlastní prostředek, který `*this` odkazuje na.

### <a name="example"></a>Příklad

```cpp
// std__memory__weak_ptr_lock.cpp
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

## <a name="op_eq"></a>  operátor =

Nahradí vlastněný zdroj.

```cpp
weak_ptr& operator=(const weak_ptr& wp);

template <class Other>
weak_ptr& operator=(const weak_ptr<Other>& wp);

template <class Other>
weak_ptr& operator=(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Jiné*<br/>
Typ řízený ukazatelem argumentu sdílené/weak.

*webové části*<br/>
Slabý ukazatel na kopii.

*SP*<br/>
Sdílený ukazatel na kopii.

### <a name="remarks"></a>Poznámky

Všechny operátory uvolnění prostředku, na kterou aktuálně odkazuje `*this` a přiřazení vlastnictví prostředků s názvem podle sekvenci operandů pro `*this`. Pokud se operátor nezdaří ponechá `*this` beze změny.

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

## <a name="owner_before"></a>  owner_before –

Vrátí **true** tato `weak_ptr` je řazen před (nebo menší než) poskytnutý ukazatel.

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

Členská funkce šablony vrátí **true** Pokud `*this` je `ordered before` `ptr`.

## <a name="reset"></a>  Resetovat

Verze vlastněný zdroj.

```cpp
void reset();
```

### <a name="remarks"></a>Poznámky

Členská funkce uvolní zdroj, na které odkazuje `*this` a převede `*this` prázdný weak_ptr objektu.

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

## <a name="swap"></a>  Prohození

Prohodí dva `weak_ptr` objekty.

```cpp
void swap(weak_ptr& wp);
```

### <a name="parameters"></a>Parametry

*webové části*<br/>
Slabý ukazatel, který chcete Prohodit s.

### <a name="remarks"></a>Poznámky

Členská funkce opustí prostředku původně ukazuje `*this` následně odkazované *wp*a prostředky původně ukazuje *wp* následně ukazuje `*this`. Funkce nezmění počty odkazů pro tyto dva prostředky a nevyvolá žádné výjimky.

### <a name="example"></a>Příklad

```cpp
// std__memory__weak_ptr_swap.cpp
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

## <a name="use_count"></a>  use_count –

Určený počet počty `shared_ptr` objekty.

```cpp
long use_count() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet `shared_ptr` objekty, které zdroj vlastní odkazované `*this`.

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

## <a name="weak_ptr"></a>  weak_ptr

Vytvoří `weak_ptr`.

```cpp
weak_ptr();

weak_ptr(const weak_ptr& wp);

template <class Other>
weak_ptr(const weak_ptr<Other>& wp);

template <class Other>
weak_ptr(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Jiné*<br/>
Typ řízený ukazatelem argumentu sdílené/weak.

*webové části*<br/>
Slabý ukazatel na kopii.

*SP*<br/>
Sdílený ukazatel na kopii.

### <a name="remarks"></a>Poznámky

Konstruktory jednotlivých vytvořit objekt, který odkazuje na prostředek s názvem podle sekvenci operandů.

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

## <a name="see-also"></a>Viz také:

[shared_ptr – třída](../standard-library/shared-ptr-class.md)<br/>
