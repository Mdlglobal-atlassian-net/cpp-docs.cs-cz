---
title: "weak_ptr – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 821992a6a0684e965f804729b470075038310ef1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="weakptr-class"></a>weak_ptr – třída
Zalomí slabě propojený ukazatel.  
  
## <a name="syntax"></a>Syntaxe  
```    
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
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ řízené slabé ukazatele.  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje objekt, který odkazuje na prostředek, který je spravovaný nástrojem jeden nebo více [shared_ptr – třída](../standard-library/shared-ptr-class.md) objekty. `weak_ptr` Objekty, které odkazují na prostředek, neovlivní počet odkazů prostředku. Proto když poslední `shared_ptr` zničena objekt, který spravuje prostředku prostředek bude uvolněno, i když jsou `weak_ptr` objekty odkazující na tento prostředek. To je nezbytné pro vyloučení cykly v datové struktury.  
  
 A `weak_ptr` objekt odkazuje na prostředek, pokud byl zkonstruován z `shared_ptr` objektu, který vlastní tento prostředek, pokud byl zkonstruován z `weak_ptr` objekt, který odkazuje na prostředek, nebo pokud tento prostředek byl přiřazen k němu s [ operátor =](#op_eq). A `weak_ptr` objekt neposkytuje přímý přístup k prostředku, který odkazuje. Kód, který potřebuje používat prostředek se tak prostřednictvím `shared_ptr` objektu, který vlastní tento prostředek, vytvořit voláním členské funkce [zámku](#lock). A `weak_ptr` objekt vypršela platnost, pokud prostředek, který odkazuje na bylo uvolněno, protože všechny `shared_ptr` objekty, které vlastní prostředek zničena. Volání metody `lock` na `weak_ptr` objektu s vypršenou platností vytvoří objekt shared_ptr prázdný.  
  
 Weak_ptr prázdný objekt neodkazuje na žádné prostředky a nemá žádné řídicí blok. Jeho – členská funkce `lock` vrátí prázdný shared_ptr objekt.  
  
 Cyklus nastane, když dva nebo více zdrojů řízené `shared_ptr` objekty uložení vzájemně odkazující na `shared_ptr` objekty. Například seznam cyklické propojené s tři prvky má hlavního uzlu `N0`; obsahuje tento uzel `shared_ptr` objektu, který vlastní další uzel `N1`; obsahuje tento uzel `shared_ptr` objektu, který vlastní další uzel `N2`; tento uzel v vypnout, blokování `shared_ptr` objektu, který vlastní hlavního uzlu `N0`, zavření cyklu. V takovém případě žádné počty odkazů se někdy stane nula a uzly v cyklu neuvolní. K vyloučení cyklus, poslední uzel `N2` by měl obsahovat `weak_ptr` odkazující na objekt `N0` místo `shared_ptr` objektu. Vzhledem k tomu `weak_ptr` není vlastníkem objektu `N0` nemá vliv `N0`na referenční počet a když program poslední odkaz k hlavnímu uzlu zničen uzly v seznamu budou také zničena.  
  
## <a name="members"></a>Členové  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[weak_ptr](#weak_ptr)|Vytvoří `weak_ptr`.|  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[ELEMENT_TYPE](#element_type)|Typ elementu.|  
|[platnost](#expired)|Testy, pokud vypršela platnost vlastnictví.|  
|[lock](#lock)|Získá výhradní vlastnictví prostředku.|  
|[owner_before –](#owner_before)|Vrátí `true` Pokud `weak_ptr` je seřadí před (nebo menší než) zadané ukazatele.|  
|[resetování](#reset)|Verze vlastní prostředek.|  
|[swap](#swap)|Prohození dva `weak_ptr` objekty.|  
|[use_count –](#use_count)|Určený počet počty `shared_ptr` objekty.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#op_eq)|Nahradí vlastní prostředek.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<paměti >  
  
 **Namespace:** – std  
  
##  <a name="element_type"></a>ELEMENT_TYPE  
 Typ elementu.  
  
```  
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
  
##  <a name="expired"></a>platnost  
 Testy, pokud vypršela platnost vlastnictví.  
  
```  
bool expired() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `true` Pokud `*this` vypršela platnost, jinak `false`.  
  
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
  
##  <a name="lock"></a>Zámek  
 Získá výhradní vlastnictví prostředku.  
  
```  
shared_ptr<Ty> lock() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí objekt shared_ptr prázdný, pokud `*this` vypršela platnost; v opačném případě vrátí [shared_ptr – třída](../standard-library/shared-ptr-class.md) `<Ty>` objekt, který je vlastníkem prostředku, který `*this` odkazuje na.  
  
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
  
##  <a name="op_eq"></a>operátor =  
 Nahradí vlastní prostředek.  
  
```  
weak_ptr& operator=(const weak_ptr& wp);

template <class Other>  
weak_ptr& operator=(const weak_ptr<Other>& wp);

template <class Other>  
weak_ptr& operator=(const shared_ptr<Other>& sp);
```  
  
### <a name="parameters"></a>Parametry  
 `Other`  
 Typ řízené ukazatele sdílené nebo weak argument.  
  
 `wp`  
 Slabé ukazatel ke kopírování.  
  
 `sp`  
 Sdílené ukazatel ke kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Operátory všechny verze prostředku, na kterou aktuálně odkazuje `*this` a přiřaďte vlastnictví prostředek s názvem pořadím operand k `*this`. Pokud operátor selže nechá `*this` beze změny.  
  
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
  
##  <a name="owner_before"></a>owner_before –  
 Vrátí `true` Pokud `weak_ptr` je seřadí před (nebo menší než) zadané ukazatele.  
  
```  
template <class Other>  
bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>  
bool owner_before(const weak_ptr<Other>& ptr);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 `lvalue` Odkaz na buď `shared_ptr` nebo `weak_ptr`.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce šablony vrátí `true` Pokud `*this` je `ordered before` `ptr`.  
  
##  <a name="reset"></a>resetování  
 Verze vlastní prostředek.  
  
```  
void reset();
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce uvolní prostředků, na kterou odkazuje `*this` a převede `*this` do objektu weak_ptr prázdný.  
  
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
  
##  <a name="swap"></a>swap  
 Prohození dva `weak_ptr` objekty.  
  
```  
void swap(weak_ptr& wp);
```  
  
### <a name="parameters"></a>Parametry  
 `wp`  
 Slabé ukazatel na prohození s.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce opustí prostředků, na kterou původně odkazuje `*this` následně ukazuje `wp`a prostředků, na kterou původně odkazuje `wp` následně ukazuje `*this`. Funkce nezmění počty odkazů pro tyto dva prostředky a nevyvolá jakékoli výjimky.  
  
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
  
##  <a name="use_count"></a>use_count –  
 Určený počet počty `shared_ptr` objekty.  
  
```  
long use_count() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí počet `shared_ptr` objekty, které vlastní prostředek ukazující na `*this`.  
  
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
  
##  <a name="weak_ptr"></a>weak_ptr  
 Vytvoří `weak_ptr`.  
  
```  
weak_ptr();

weak_ptr(const weak_ptr& wp);

template <class Other>  
weak_ptr(const weak_ptr<Other>& wp);

template <class Other>  
weak_ptr(const shared_ptr<Other>& sp);
```  
  
### <a name="parameters"></a>Parametry  
 `Other`  
 Typ řízené ukazatele sdílené nebo weak argument.  
  
 `wp`  
 Slabé ukazatel ke kopírování.  
  
 `sp`  
 Sdílené ukazatel ke kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktory každý vytvořit objekt, který odkazuje na prostředek s názvem operand pořadí.  
  
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
  
## <a name="see-also"></a>Viz také  
 [shared_ptr – třída](../standard-library/shared-ptr-class.md)

