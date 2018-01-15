---
title: "allocator_base – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::allocator_base
- allocators/stdext::allocators::allocator_base
- allocators/stdext::allocator_base::const_pointer
- allocators/stdext::allocator_base::const_reference
- allocators/stdext::allocator_base::difference_type
- allocators/stdext::allocator_base::pointer
- allocators/stdext::allocator_base::reference
- allocators/stdext::allocator_base::size_type
- allocators/stdext::allocator_base::value_type
- allocators/stdext::allocator_base::_Charalloc
- allocators/stdext::allocator_base::_Chardealloc
- allocators/stdext::allocator_base::address
- allocators/stdext::allocator_base::allocate
- allocators/stdext::allocator_base::construct
- allocators/stdext::allocator_base::deallocate
- allocators/stdext::allocator_base::destroy
- allocators/stdext::allocator_base::max_size
dev_langs: C++
helpviewer_keywords:
- stdext::allocator_base [C++]
- stdext::allocators [C++], allocator_base
- stdext::allocator_base [C++], const_pointer
- stdext::allocator_base [C++], const_reference
- stdext::allocator_base [C++], difference_type
- stdext::allocator_base [C++], pointer
- stdext::allocator_base [C++], reference
- stdext::allocator_base [C++], size_type
- stdext::allocator_base [C++], value_type
- stdext::allocator_base [C++], _Charalloc
- stdext::allocator_base [C++], _Chardealloc
- stdext::allocator_base [C++], address
- stdext::allocator_base [C++], allocate
- stdext::allocator_base [C++], construct
- stdext::allocator_base [C++], deallocate
- stdext::allocator_base [C++], destroy
- stdext::allocator_base [C++], max_size
ms.assetid: f920b45f-2a88-4bb0-8ead-b6126b426ed4
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf1127a6ec3e921e19c9626cc51197eb2a87d6ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="allocatorbase-class"></a>allocator_base – třída
Definuje základní třídu a běžné funkce, které jsou nutné k vytvoření přidělení uživatelem definované z filtr synchronizace.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Type, class Sync>  
class allocator_base
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Type`|Typ elementů přidělené pomocí přidělujícího modulu.|  
|`Sync`|Zásady synchronizace pro přidělení, což je [sync_none – třída](../standard-library/sync-none-class.md), [sync_per_container – třída](../standard-library/sync-per-container-class.md), [sync_per_thread – třída](../standard-library/sync-per-thread-class.md), nebo [sync_shared Třída](../standard-library/sync-shared-class.md).|  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[allocator_base –](#allocator_base)|Vytvoří objekt typu `allocator_base`.|  
  
### <a name="typedefs"></a>Definice TypeDef  
  
|||  
|-|-|  
|[const_pointer –](#const_pointer)|Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.|  
|[const_reference –](#const_reference)|Typ, který poskytuje konstantní odkaz na typ objektu spravovaného pomocí přidělujícího modulu.|  
|[difference_type –](#difference_type)|Integrální typ se znaménkem představující rozdíl mezi hodnotami ukazatelé na typ objektu spravovaného pomocí přidělujícího modulu.|  
|[ukazatele](#pointer)|Typ, který poskytuje ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.|  
|[referenční dokumentace](#reference)|Typ, který obsahuje odkaz na typ objektu spravovaného pomocí přidělujícího modulu.|  
|[size_type –](#size_type)|Typu bez znaménka integrální, představující Délka libovolného pořadí, které objekt třídy šablony `allocator_base` můžete přidělit.|  
|[value_type](#value_type)|Typ, který je spravován pomocí přidělujícího modulu.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[_Charalloc –](#charalloc)|Přidělí úložiště pro pole typu `char`.|  
|[_Chardealloc –](#chardealloc)|Uvolní úložiště pro pole obsahující elementy typu `char`.|  
|[Adresa](#address)|Vyhledá objekt, jehož hodnota je zadána adresa.|  
|[allocate](#allocate)|Přiděluje blok paměti dostatečně velký pro uložení alespoň některé zadaný počet elementů.|  
|[konstrukce](#construct)|Vytvoří určitý typ objektu na zadané adrese, který je inicializován se zadanou hodnotou.|  
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů ze začátku úložiště na zadané pozici.|  
|[Destroy –](#destroy)|Volá destruktor objekty bez rušení přidělení paměti uloží objekt.|  
|[max_size –](#max_size)|Vrátí počet prvků typu `Type` , by mohly být přiděleny v objektu třídy allocator před použitím volné paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
##  <a name="charalloc"></a>allocator_base::_Charalloc  
 Přidělí úložiště pro pole typu `char`.  
  
```
char *_Charalloc(size_type count);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`count`|Počet prvků v poli, která bude přidělena.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na objekt přidělená.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen používá kontejnery, když kompilujete s kompilátoru, která nelze kompilovat obnovení vazby. Implementuje `_Charalloc` pro uživatelem definované allocator vrácením výsledku volání `allocate` funkce filtru synchronizace.  
  
##  <a name="chardealloc"></a>allocator_base::_Chardealloc  
 Uvolní úložiště pro pole obsahující elementy typu `char`.  
  
```
void _Chardealloc(void* ptr, size_type count);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ptr`|Ukazatel na první objekt, který má být navrácena z úložiště.|  
|`count`|Počet objektů, které chcete být navrácena z úložiště.|  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen používá kontejnery, když kompilujete s kompilátoru, která nelze kompilovat obnovení vazby. Implementuje `_Chardealloc` pro uživatelem definované allocator voláním `deallocate` funkce filtru synchronizace. Ukazatele ptr, aby byl dříve vrátil voláním `_Charalloc` allocator objektu, který porovnává rovna `*this`, přidělování objekt stejnou velikost a typ pole. `_Chardealloc`nikdy vyvolá výjimku.  
  
##  <a name="address"></a>allocator_base::Address  
 Vyhledá objekt, jehož hodnota je zadána adresa.  
  
```
pointer address(reference val);

const_pointer address(const_reference val);
```  
  
### <a name="parameters"></a>Parametry  
 `val`  
 Const nebo nonconst hodnota objektu, jejíž adresa se hledají.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnoty, respektive const nebo nonconst najít const nebo nonconst ukazatele na objekt.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je implementována pro přidělování uživatelem definované vrácením `&val`.  
  
##  <a name="allocate"></a>allocator_base::allocate  
 Přiděluje blok paměti dostatečně velký pro uložení alespoň některé zadaný počet elementů.  
  
```
template <class Other>  
pointer allocate(size_type _Nx, const Other* _Hint = 0);

pointer allocate(size_type _Nx);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`_Nx`|Počet prvků v poli, která bude přidělena.|  
|`_Hint`|Tento parametr je ignorován.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na objekt přidělená.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce implementuje přidělení paměti pro přidělení uživatelem definované vrácením výsledku volání `allocate` funkce synchronizace filtru typu typ `*` Pokud `_Nx == 1`, jinak hodnota vrácením výsledku volání na `operator new(_Nx * sizeof(Type))` přetypování na typ `*`.  
  
##  <a name="allocator_base"></a>allocator_base::allocator_base  
 Vytvoří objekt typu `allocator_base`.  
  
```
allocator_base();

template <class Other>  
allocator_base(const allocator_base<Other, Sync>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`right`|Objekt allocator ke kopírování.|  
  
### <a name="remarks"></a>Poznámky  
 První konstrukce konstruktor [allocator_base](../standard-library/allocator-base-class.md) instance. Druhý konstruktor konstrukce `allocator_base` instanci, například, pro žádné `allocator_base<Type, _Sync>` instance `a`, `allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a`.  
  
##  <a name="const_pointer"></a>allocator_base::const_pointer  
 Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.  
  
```
typedef const Type *const_pointer;
```  
  
##  <a name="const_reference"></a>allocator_base::const_reference  
 Typ, který poskytuje konstantní odkaz na typ objektu spravovaného pomocí přidělujícího modulu.  
  
```
typedef const Type& const_reference;
```  
  
##  <a name="construct"></a>allocator_base::Construct  
 Vytvoří určitý typ objektu na zadané adrese, který je inicializován se zadanou hodnotou.  
  
```
void construct(pointer ptr, const Type& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ptr`|Ukazatel na umístění, kde je objekt zkonstruovat.|  
|`val`|Hodnota, pomocí kterého je objekt vytvářen inicializovat.|  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je implementována pro přidělování uživatelem definované voláním `new((void*)ptr Type(val)`.  
  
##  <a name="deallocate"></a>allocator_base::deallocate  
 Uvolní zadaný počet objektů ze začátku úložiště na zadané pozici.  
  
```
void deallocate(pointer ptr, size_type _Nx);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ptr`|Ukazatel na první objekt, který má být navrácena z úložiště.|  
|`_Nx`|Počet objektů, které chcete být navrácena z úložiště.|  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je implementována pro přidělování uživatelem definované voláním `deallocate(ptr)` ve filtru synchronizace `Sync` Pokud `_Nx == 1`, jinak hodnota voláním `operator delete(_Nx * ptr)`.  
  
##  <a name="destroy"></a>allocator_base::Destroy  
 Volá destruktor objekty bez rušení přidělení paměti uloží objekt.  
  
```
void destroy(pointer ptr);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ptr`|Ukazatel určení adresu objekt, který má být způsobem zničena.|  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je implementována pro přidělování uživatelem definované voláním `ptr->~Type()`.  
  
##  <a name="difference_type"></a>allocator_base::difference_type  
 Integrální typ se znaménkem představující rozdíl mezi hodnotami ukazatelé na typ objektu spravovaného pomocí přidělujícího modulu.  
  
```
typedef std::ptrdiff_t difference_type;
```  
  
##  <a name="max_size"></a>allocator_base::max_size  
 Vrátí počet prvků typu `Type` , by mohly být přiděleny v objektu třídy allocator před použitím volné paměti.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů, které by mohly být přiděleny.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je implementována pro přidělování uživatelem definované vrácením `(size_t)-1 / sizeof(Type)` Pokud `0 < (size_t)-1 / sizeof(Type)`, jinak `1`.  
  
##  <a name="pointer"></a>allocator_base::Pointer  
 Typ, který poskytuje ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.  
  
```
typedef Type *pointer;
```  
  
##  <a name="reference"></a>allocator_base::Reference  
 Typ, který obsahuje odkaz na typ objektu spravovaného pomocí přidělujícího modulu.  
  
```
typedef Type& reference;
```  
  
##  <a name="size_type"></a>allocator_base::size_type  
 Typu bez znaménka integrální, představující Délka libovolného pořadí, které objekt třídy šablony `allocator_base` můžete přidělit.  
  
```
typedef std::size_t size_type;
```  
  
##  <a name="value_type"></a>allocator_base::value_type  
 Typ, který je spravován pomocí přidělujícího modulu.  
  
```
typedef Type value_type;
```  
  
## <a name="see-also"></a>Viz také  
 [\<alokátorů >](../standard-library/allocators-header.md)



