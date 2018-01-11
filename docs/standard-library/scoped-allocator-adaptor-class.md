---
title: "scoped_allocator_adaptor – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- scoped_allocator/std::scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor::rebind Struct
- scoped_allocator/std::scoped_allocator_adaptor::allocate
- scoped_allocator/std::scoped_allocator_adaptor::construct
- scoped_allocator/std::scoped_allocator_adaptor::deallocate
- scoped_allocator/std::scoped_allocator_adaptor::destroy
- scoped_allocator/std::scoped_allocator_adaptor::inner_allocator
- scoped_allocator/std::scoped_allocator_adaptor::max_size
- scoped_allocator/std::scoped_allocator_adaptor::outer_allocator
- scoped_allocator/std::scoped_allocator_adaptor::select_on_container_copy_construction
dev_langs: C++
helpviewer_keywords:
- std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor::allocate
- std::scoped_allocator_adaptor::construct
- std::scoped_allocator_adaptor::deallocate
- std::scoped_allocator_adaptor::destroy
- std::scoped_allocator_adaptor::inner_allocator
- std::scoped_allocator_adaptor::max_size
- std::scoped_allocator_adaptor::outer_allocator
- std::scoped_allocator_adaptor::select_on_container_copy_construction
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 66c188c490861e0b632791755b2d9914a7919865
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="scopedallocatoradaptor-class"></a>scoped_allocator_adaptor – třída
Představuje vnoření alokátorů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <class Outer, class... Inner>  
class scoped_allocator_adaptor;  
```  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy zapouzdří vnoření jeden nebo více alokátorů. Každá tato třída má nejkrajnější allocator typu `outer_allocator_type`, synonymum pro `Outer`, což je veřejný základ `scoped_allocator_adaptor` objektu. `Outer`slouží k přidělení paměti se použil kontejner. Můžete získat odkaz na tento objekt základní allocator voláním `outer_allocator`.  
  
 Zbývající část vnoření má typ `inner_allocator_type`. Vnitřní allocator se používá k přidělení paměti pro elementům v kontejneru. Můžete získat odkaz na uložený objekt tohoto typu voláním `inner_allocator`. Pokud `Inner...` není prázdná, `inner_allocator_type` má typ `scoped_allocator_adaptor<Inner...>`, a `inner_allocator` označí objekt člena. V opačném `inner_allocator_type` má typ `scoped_allocator_adaptor<Outer>`, a `inner_allocator` označí celý objekt.  
  
 Vnoření se chová jako kdyby se libovolný hloubku, jeho nejvnitřnější zapouzdřené allocator replikaci, podle potřeby.  
  
 Několik konceptů, které nejsou součástí rozhraní viditelné podpory v popisující chování této třídy šablony. *Nejkrajnější allocator* zprostředkovává všechna volání konstruktu a zrušení metody. Efektivně je definována funkce rekurzivní `OUTERMOST(X)`, kde `OUTERMOST(X)` je jedním z následujících akcí.  
  
-   Pokud `X.outer_allocator()` je ve správném formátu, pak `OUTERMOST(X)` je `OUTERMOST(X.outer_allocator())`.  
  
-   V opačném `OUTERMOST(X)` je `X`.  
  
 Tři typy jsou definovány v zájmu budeme:  
  
|Typ|Popis|  
|----------|-----------------|  
|`Outermost`|Typ `OUTERMOST(*this)`.|  
|`Outermost_traits`|`allocator_traits<Outermost>`|  
|`Outer_traits`|`allocator_traits<Outer>`|  
  
### <a name="constructors"></a>Konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|Vytvoří `scoped_allocator_adaptor` objektu.|  
  
### <a name="typedefs"></a>Typedefs  
  
|Název|Popis|  
|----------|-----------------|  
|`const_pointer`|Tento typ se jedná o synonymum `const_pointer` je spojeno s přidělujícího modulu `Outer`.|  
|`const_void_pointer`|Tento typ se jedná o synonymum `const_void_pointer` je spojeno s přidělujícího modulu `Outer`.|  
|`difference_type`|Tento typ se jedná o synonymum `difference_type` je spojeno s přidělujícího modulu `Outer`.|  
|`inner_allocator_type`|Tento typ je synonymum pro typ vnořené adaptéru `scoped_allocator_adaptor<Inner...>`.|  
|`outer_allocator_type`|Tento typ je synonymum pro typ základní allocator `Outer`.|  
|`pointer`|Tento typ se jedná o synonymum `pointer` přidružené přidělujícího modulu `Outer`.|  
|`propagate_on_container_copy_assignment`|Typ obsahuje hodnotu true pouze v případě `Outer_traits::propagate_on_container_copy_assignment` platí nebo `inner_allocator_type::propagate_on_container_copy_assignment` platí.|  
|`propagate_on_container_move_assignment`|Typ obsahuje hodnotu true pouze v případě `Outer_traits::propagate_on_container_move_assignment` platí nebo `inner_allocator_type::propagate_on_container_move_assignment` platí.|  
|`propagate_on_container_swap`|Typ obsahuje hodnotu true pouze v případě `Outer_traits::propagate_on_container_swap` platí nebo `inner_allocator_type::propagate_on_container_swap` platí.|  
|`size_type`|Tento typ se jedná o synonymum `size_type` přidružené přidělujícího modulu `Outer`.|  
|`value_type`|Tento typ se jedná o synonymum `value_type` přidružené přidělujícího modulu `Outer`.|  
|`void_pointer`|Tento typ se jedná o synonymum `void_pointer` přidružené přidělujícího modulu `Outer`.|  
  
### <a name="structs"></a>Struktury  
  
|Název|Popis|  
|----------|-----------------|  
|[scoped_allocator_adaptor::rebind – struktura](#rebind_struct)|Definuje typ `Outer::rebind\<Other>::other` jako synonymum pro `scoped_allocator_adaptor\<Other, Inner...>`.|  
  
### <a name="methods"></a>Metody  
  
|Název|Popis|  
|----------|-----------------|  
|[allocate](#allocate)|Přidělí paměť pomocí `Outer` přidělení.|  
|[konstrukce](#construct)|Vytvoří objekt.|  
|[zrušit přidělení](#deallocate)|Zruší přidělení objektů pomocí přidělujícího modulu vnější.|  
|[Destroy –](#destroy)|Odstraní zadaný objekt.|  
|[inner_allocator](#inner_allocator)|Získá odkaz na uložený objekt typu `inner_allocator_type`.|  
|[max_size –](#max_size)|Určuje maximální počet objektů, které mohou být přiděleny pomocí přidělujícího modulu vnější.|  
|[outer_allocator](#outer_allocator)|Získá odkaz na uložený objekt typu `outer_allocator_type`.|  
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Vytvoří novou `scoped_allocator_adaptor` objekt se každý objekt uložené allocator inicializuje pomocí volání `select_on_container_copy_construction` pro každý odpovídající přidělení.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<scoped_allocator – >  
  
 **Namespace:** – std  
  
##  <a name="allocate"></a>scoped_allocator_adaptor::allocate –
 Přidělí paměť pomocí `Outer` přidělení.  
  
```cpp  
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Počet elementů, u kterých je přidělit dostatek místa.  
  
 `hint`  
 Ukazatele, který může pomoct objekt allocator vyhledáním adresu objektu přidělené před žádosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první členská funkce `Outer_traits::allocate(outer_allocator(), count)`. Vrátí druhou členská funkce `Outer_traits::allocate(outer_allocator(), count, hint)`.  
  
##  <a name="construct"></a>scoped_allocator_adaptor::Construct –
 Vytvoří objekt.  
  
```cpp  
template <class Ty, class... Atypes>  
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>  
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,  
    tuple<Atypes1&&...>  
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>  
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr,  
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Ukazatel na umístění paměti, kde objekt zkonstruovat.  
  
 `args`  
 Seznam argumentů.  
  
 `first`  
 Objekt typu první v pár.  
  
 `second`  
 Objekt v pár druhého typu.  
  
 `right`  
 Existující objekt tak, aby je přesunout ani zkopírovat.  
  
### <a name="remarks"></a>Poznámky  
 První metoda vytvoří objekt v `ptr` voláním `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`, kde `xargs...` je jedním z následujících akcí.  
  
-   Pokud `uses_allocator<Ty, inner_allocator_type>` obsahuje hodnotu false, pak `xargs...` je `args...`.  
  
-   Pokud `uses_allocator<Ty, inner_allocator_type>` platí, a `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` platí, pak `xargs...` je `allocator_arg, inner_allocator(), args...`.  
  
-   Pokud `uses_allocator<Ty, inner_allocator_type>` platí, a `is_constructible<Ty, args..., inner_allocator()>` platí, pak `xargs...` je `args..., inner_allocator()`.  
  
 Druhá metoda vytvoří objekt dvojice v `ptr` voláním `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`, kde `xargs...` je `first...` změnit stejně jako v seznamu nahoře a `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`, kde `xargs...` je `second...` upravit stejně jako v seznamu nahoře.  
  
 Třetí metoda se chová stejně jako `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.  
  
 Čtvrtý metoda se chová stejně jako `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`.  
  
 Metodu páté se chová stejně jako `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`.  
  
 Metodu šesté se chová stejně jako `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`.  
  
##  <a name="deallocate"></a>scoped_allocator_adaptor::deallocate –
 Zruší přidělení objektů pomocí přidělujícího modulu vnější.  
  
```cpp  
void deallocate(pointer ptr, size_type count);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Ukazatel na počáteční umístění objekty, které chcete být navrácena.  
  
 `count`  
 Počet objektů se zrušit přidělení.  
  
##  <a name="destroy"></a>scoped_allocator_adaptor::Destroy –
 Odstraní zadaný objekt.  
  
```cpp  
template <class Ty>  
void destroy(Ty* ptr)  
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Ukazatel na objekt, který má být způsobem zničena.  
  
### <a name="return-value"></a>Návratová hodnota  
 `Outermost_traits::destroy(OUTERMOST(*this), ptr)`  
  
##  <a name="inner_allocator"></a>scoped_allocator_adaptor::inner_allocator –
 Získá odkaz na uložený objekt typu `inner_allocator_type`.  
  
```cpp  
inner_allocator_type& inner_allocator() noexcept;  
const inner_allocator_type& inner_allocator() const noexcept;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na uložený objekt typu `inner_allocator_type`.  
  
##  <a name="max_size"></a>scoped_allocator_adaptor::max_size –
 Určuje maximální počet objektů, které mohou být přiděleny pomocí přidělujícího modulu vnější.  
  
```cpp  
size_type max_size();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `Outer_traits::max_size(outer_allocator())`  
  
##  <a name="outer_allocator"></a>scoped_allocator_adaptor::outer_allocator –
 Získá odkaz na uložený objekt typu `outer_allocator_type`.  
  
```cpp  
outer_allocator_type& outer_allocator() noexcept;  
const outer_allocator_type& outer_allocator() const noexcept;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na uložený objekt typu `outer_allocator_type`.  
  
##  <a name="rebind_struct"></a>scoped_allocator_adaptor::rebind – struktura  
 Definuje typ `Outer::rebind\<Other>::other` jako synonymum pro `scoped_allocator_adaptor\<Other, Inner...>`.  
  
{Struktura obnovení vazby  
   TypeDef Other_traits::rebind\<Další >  
   Other_alloc;  
   scoped_allocator_adaptor – typedef\<Other_alloc, vnitřní... > jiných;  
   };  
  
##  <a name="scoped_allocator_adaptor"></a>scoped_allocator_adaptor::scoped_allocator_adaptor – konstruktor  
 Vytvoří `scoped_allocator_adaptor` objektu.  
  
```cpp  
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(
 const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(
 scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(Outer2&& al,  
    const Inner&... rest) noexcept;  
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Existující `scoped_allocator_adaptor`.  
  
 `al`  
 Existující allocator má být použit jako vnější přidělení.  
  
 `rest`  
 Seznam alokátorů má být použit jako vnitřní alokátorů.  
  
### <a name="remarks"></a>Poznámky  
 První výchozí konstruktor vytvoří jeho uložené přidělování objektů. Každý z následujících třech konstruktory vytvoří jeho uložené přidělování objektů z odpovídajících objektů v `right`. Poslední konstruktoru vytvoří jeho uložené přidělování objektů z odpovídající argumentů v seznamu argumentů.  
  
##  <a name="select_on_container_copy_construction"></a>scoped_allocator_adaptor::select_on_container_copy_construction –
 Vytvoří novou `scoped_allocator_adaptor` objekt se každý objekt uložené allocator inicializuje pomocí volání `select_on_container_copy_construction` pro každý odpovídající přidělení.  
  
```cpp  
scoped_allocator_adaptor select_on_container_copy_construction();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí efektivně `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`. Výsledkem je nový `scoped_allocator_adaptor` objekt se každý objekt uložené allocator inicializuje pomocí volání `al.select_on_container_copy_construction()` pro odpovídající allocator `al`.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)



