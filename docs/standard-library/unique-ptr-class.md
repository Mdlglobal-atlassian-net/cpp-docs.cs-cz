---
title: "unique_ptr – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- memory/std::unique_ptr
- memory/std::unique_ptr::deleter_type
- memory/std::unique_ptr::element_type
- memory/std::unique_ptr::pointer
- memory/std::unique_ptr::get
- memory/std::unique_ptr::get_deleter
- memory/std::unique_ptr::release
- memory/std::unique_ptr::reset
- memory/std::unique_ptr::swap
dev_langs:
- C++
helpviewer_keywords:
- std::unique_ptr [C++]
- std::unique_ptr [C++], deleter_type
- std::unique_ptr [C++], element_type
- std::unique_ptr [C++], pointer
- std::unique_ptr [C++], get
- std::unique_ptr [C++], get_deleter
- std::unique_ptr [C++], release
- std::unique_ptr [C++], reset
- std::unique_ptr [C++], swap
ms.assetid: acdf046b-831e-4a4a-83aa-6d4ee467db9a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ba8adc1da5e29d1bd6cbf082c6c38fe0692d925
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="uniqueptr-class"></a>unique_ptr – třída
Ukládá ukazatel na vlastní objekt nebo pole. Objekt nebo pole vlastní žádná jiná `unique_ptr`. Objekt nebo pole zničen při `unique_ptr` zničena.  
  
## <a name="syntax"></a>Syntaxe  
```  
class unique_ptr {
public:
    unique_ptr();
    unique_ptr(nullptr_t Nptr);
    explicit unique_ptr(pointer Ptr);
    unique_ptr(pointer Ptr,
        typename conditional<is_reference<Del>::value, Del,
        typename add_reference<const Del>::type>::type Deleter);
    unique_ptr(pointer Ptr,
        typename remove_reference<Del>::type&& Deleter);
    unique_ptr(unique_ptr&& Right);
    template <class T2, Class Del2>
    unique_ptr(unique_ptr<T2, Del2>&& Right);
    unique_ptr(const unique_ptr& Right) = delete;
    unique_ptr& operator=(const unique_ptr& Right) = delete;
};

//Specialization for arrays:  
template <class T, class D>
class unique_ptr<T[], D> {
public:
    typedef pointer;
    typedef T element_type;
    typedef D deleter_type;
    constexpr unique_ptr() noexcept;
    template <class U>
    explicit unique_ptr(U p) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    unique_ptr(unique_ptr&& u) noexcept;
    constexpr unique_ptr(nullptr_t) noexcept : unique_ptr() { }     template <class U, class E>
        unique_ptr(unique_ptr<U, E>&& u) noexcept;
    ~unique_ptr();
    unique_ptr& operator=(unique_ptr&& u) noexcept;
    template <class U, class E>
    unique_ptr& operator=(unique_ptr<U, E>&& u) noexcept;
    unique_ptr& operator=(nullptr_t) noexcept;
    T& operator[](size_t i) const;


    pointer get() const noexcept;
    deleter_type& get_deleter() noexcept;
    const deleter_type& get_deleter() const noexcept;
    explicit operator bool() const noexcept;
    pointer release() noexcept;
    void reset(pointer p = pointer()) noexcept;
    void reset(nullptr_t = nullptr) noexcept;
    template <class U>
    void reset(U p) noexcept = delete;
    void swap(unique_ptr& u) noexcept;  // disable copy from lvalue unique_ptr(const unique_ptr&) = delete;  
    unique_ptr& operator=(const unique_ptr&) = delete;
};
```  
  
#### <a name="parameters"></a>Parametry  
 `Right`  
 A `unique_ptr`.  
  
 `Nptr`  
 `rvalue` Typu `std::nullptr_t`.  
  
 `Ptr`  
 A `pointer`.  
  
 `Deleter`  
 A `deleter` funkce, která je vázána `unique_ptr`.  
  
## <a name="exceptions"></a>Výjimky  
 Žádné výjimky generované `unique_ptr`.  
  
## <a name="remarks"></a>Poznámky  
 `unique_ptr` Třída nahrazuje `auto_ptr`a může sloužit jako element standardní knihovna C++ kontejnerů.  
  
 Použití [make_unique](../standard-library/memory-functions.md#make_unique) pomocné funkce efektivně vytvoření nové instance třídy `unique_ptr`.  
  
 `unique_ptr` spravuje jednoznačně prostředku. Každý `unique_ptr` objekt ukazatel na objekt, vlastní nebo ukládá ukazatele null. Prostředek může být vlastněn více než jeden `unique_ptr` objektu;  Když `unique_ptr` zničena objektu, který vlastní určitý prostředek, prostředek je uvolněno. A `unique_ptr` objektu může být přesunuta, ale nebylo možné zkopírovat;  Další informace najdete v tématu [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
 Prostředek je uvolněno voláním uložené `deleter` objektu typu `Del` který zná přidělování prostředků pro konkrétní `unique_ptr`. Výchozí hodnota `deleter` `default_delete<T>` předpokládá, že prostředek na kterou odkazuje `ptr` je přiřazen `new`, a může být uvolněno voláním `delete _Ptr`. (Částečná specializace `unique_ptr<T[]>`spravuje pole objektů, kterým je přiřazen `new[]`, a má výchozí `deleter` `default_delete<T[]>`, specializované volání delete [] – `ptr`.)  
  
 Uložené ukazatel na prostředek vlastní `stored_ptr` má typ `pointer`. Je `Del::pointer` -li definována, a `T *` není-li. Uložených `deleter` objekt `stored_deleter` nezabírá prostor v objektu, pokud `deleter` je bezstavové. Všimněte si, že `Del` může být odkazového typu.  
  
## <a name="members"></a>Členové  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[unique_ptr](#unique_ptr)|Existují sedm konstruktory pro `unique_ptr`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[deleter_type](#deleter_type)|Synonymum pro parametr šablony `Del`.|  
|[element_type](#element_type)|Synonymum pro parametr šablony `T`.|  
|[pointer](#pointer)|Synonymum pro `Del::pointer` -li definována, jinak `T *`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[get](#get)|Vrátí `stored_ptr`.|  
|[get_deleter](#get_deleter)|Vrátí odkaz na `stored_deleter`.|  
|[release](#release)|ukládá `pointer()` v `stored_ptr` a vrátí jeho předchozí obsah.|  
|[reset](#reset)|Uvolní aktuálně vlastněný prostředek a přijme nový prostředek.|  
|[swap](#swap)|Výměny prostředků a `deleter` poskytnutým `unique_ptr`.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|`operator bool`|Vrátí hodnotu typu, který je převést na operátor `bool`. Výsledek převodu na `bool` je `true` při `get() != pointer()`, jinak `false`.|  
|`operator->`|Členské funkce vrátí hodnotu `stored_ptr`.|  
|`operator*`|Členské funkce vrátí hodnotu `*stored_ptr`.|  
|[unique_ptr operator=](#unique_ptr_operator_eq)|Přiřadí hodnota `unique_ptr` (nebo `pointer-type`) na aktuální `unique_ptr`.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<paměti >  
  
 **Namespace:** – std  
  
##  <a name="deleter_type"></a>  deleter_type  
 Typ je synonymum pro parametr šablony `Del`.  
  
```  
typedef Del deleter_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Del`.  
  
##  <a name="element_type"></a>  element_type  
 Typ je synonymum pro parametr šablony `Type`.  
  
```  
typedef Type element_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Ty`.  
  
##  <a name="get"></a>  unique_ptr::Get  
 Vrátí `stored_ptr`.  
  
```  
pointer get() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `stored_ptr`.  
  
##  <a name="get_deleter"></a>  unique_ptr::get_deleter  
 Vrátí odkaz na `stored_deleter`.  
  
```  
Del& get_deleter();

const Del& get_deleter() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí odkaz na `stored_deleter`.  
  
##  <a name="unique_ptr_operator_eq"></a>  unique_ptr operator=  
 Adresa poskytnutého `unique_ptr` do stávající.  
  
```  
unique_ptr& operator=(unique_ptr&& right);
template <class U, Class Del2>  
unique_ptr& operator=(unique_ptr<Type, Del>&& right);
unique_ptr& operator=(pointer-type);
```  
  
### <a name="parameters"></a>Parametry  
 A `unique_ptr` odkaz sloužící k přidělování hodnotu aktuální `unique_ptr`.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce volání `reset(right.release())` a přesuňte `right.stored_deleter` k `stored_deleter`, pak vrátí `*this`.  
  
##  <a name="pointer"></a>  Ukazatele  
 Synonymum pro `Del::pointer` -li definována, jinak `Type *`.  
  
```  
typedef T1 pointer;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ se jedná o synonymum `Del::pointer` -li definována, jinak `Type *`.  
  
##  <a name="release"></a>  unique_ptr::release  
 Uvolní vlastnictví vrácený uložené ukazatele na volajícího a nastaví hodnotu uloženou ukazatel na `nullptr`.  
  
```  
pointer release();
```  
  
### <a name="remarks"></a>Poznámky  
 Použití `release` převzít vlastnictví nezpracovaná ukazatele uložené `unique_ptr`. Volající zodpovídá za odstranění vrácený ukazatele. `unique-ptr` Nastavena na prázdnou sestavený výchozí stav. Můžete přiřadit jinou ukazatel kompatibilní typ `unique_ptr` po volání `release`.  
  
### <a name="example"></a>Příklad  
  Tento příklad ukazuje, jak je zodpovědná za objekt vrácený volající verze:  
  
```cpp  
// stl_release_unique.cpp  
// Compile by using: cl /W4 /EHsc stl_release_unique.cpp  
#include <iostream>  
#include <memory>  
  
struct Sample {  
   int content_;  
   Sample(int content) : content_(content) {  
      std::cout << "Constructing Sample(" << content_ << ")" << std::endl;  
   }  
   ~Sample() {  
      std::cout << "Deleting Sample(" << content_ << ")" << std::endl;  
   }  
};  
  
void ReleaseUniquePointer() {  
   // Use make_unique function when possible.    
   auto up1 = std::make_unique<Sample>(3);  
   auto up2 = std::make_unique<Sample>(42);  
  
   // Take over ownership from the unique_ptr up2 by using release  
   auto ptr = up2.release();  
   if (up2) {  
      // This statement does not execute, because up2 is empty.  
      std::cout << "up2 is not empty." << std::endl;  
   }  
   // We are now responsible for deletion of ptr.  
   delete ptr;  
   // up1 deletes its stored pointer when it goes out of scope.     
}  
  
int main() {  
   ReleaseUniquePointer();  
}  
```  
  
  Výstup počítače:  
  
```Output  
Constructing Sample(3)  
Constructing Sample(42)  
Deleting Sample(42)  
Deleting Sample(3)  
  
```  
  
##  <a name="reset"></a>  unique_ptr::reset  
 Vlastníkem parametru ukazatele a poté se odstraní původní uložené ukazatele. Pokud je nový ukazatel stejný jako původní uložené ukazatele `reset` odstraní ukazatele a nastaví uložené ukazatele na `nullptr`.  
  
```  
void reset(pointer ptr = pointer());
void reset(nullptr_t ptr);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ptr`|Ukazatel na prostředek, který převzít vlastnictví.|  
  
### <a name="remarks"></a>Poznámky  
 Použití `reset` změnit uložené [ukazatel](#pointer) vlastníkem `unique_ptr` k `ptr` a pak odstraňte původní uložené ukazatele. Pokud `unique_ptr` nebyla prázdná, `reset` vyvolá metoda odstranění funkce vrácený [get_deleter –](#get_deleter) na původní uložené ukazatele.  
  
 Protože `reset` nejprve ukládá nové ukazatele `ptr`a poté se odstraní původní uložené ukazatele, je možné, `reset` okamžitě odstranit `ptr` Pokud je stejný jako původní uložené ukazatele.  
  
##  <a name="swap"></a>  unique_ptr::swap  
 Výměny ukazatele mezi dvěma `unique_ptr` objekty.  
  
```  
void swap(unique_ptr& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 A `unique_ptr` použít se Prohodit ukazatele.  
  
### <a name="remarks"></a>Poznámky  
 Prohození – členská funkce `stored_ptr` s `right.stored_ptr` a `stored_deleter` s `right.stored_deleter`.  
  
##  <a name="unique_ptr"></a>  unique_ptr::unique_ptr  
 Existují sedm konstruktory pro `unique_ptr`.  
  
```  
unique_ptr();

unique_ptr(nullptr_t);
explicit unique_ptr(pointer ptr);

unique_ptr(
    Type* ptr,  
    typename conditional<
    is_reference<Del>::value, 
    Del, 
    typename add_reference<const Del>::type>::type _Deleter);

unique_ptr(pointer ptr, typename remove_reference<Del>::type&& _Deleter);
unique_ptr(unique_ptr&& right);
template <class Ty2, Class Del2>  
unique_ptr(unique_ptr<Ty2, Del2>&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ptr`|Ukazatel na prostředek přiřazení `unique_ptr.`|  
|`_Deleter`|A `deleter` přiřazení `unique_ptr`.|  
|`right`|`rvalue reference` k `unique_ptr` ze kterého `unique_ptr` pole jsou přesunutí přiřazenou nově vytvořený `unique_ptr`.|  
  
### <a name="remarks"></a>Poznámky  
 První dva konstruktory vytvořit objekt, který spravuje žádný prostředek. Třetí úložiště konstruktor `ptr` v `stored_ptr`. Čtvrtý úložiště konstruktor `ptr` v `stored_ptr` a `deleter` v `stored_deleter`.  
  
 Páté úložiště konstruktor `ptr` v `stored_ptr` a přesune `deleter` do `stored_deleter`. Úložiště šesté a sedmého konstruktory `right.release()` v `stored_ptr` a přesune `right.get_deleter()` do `stored_deleter`.  
  
##  <a name="dtorunique_ptr"></a>  unique_ptr ~unique_ptr  
 Destruktor pro `unique_ptr`, zničí `unique_ptr` objektu.  
  
```  
~unique_ptr();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání destruktoru `get_deleter()(stored_ptr)`.  
  
## <a name="see-also"></a>Viz také  
 [\<paměť >](../standard-library/memory.md)


