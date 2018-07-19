---
title: allocator_base – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f27cb2bc1a711b77006fa496cc080f546e539ab
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962450"
---
# <a name="allocatorbase-class"></a>allocator_base – třída

Definuje základní třídu a běžné funkce potřebné k vytváření alokátorem definovaný uživatelem z filtru synchronizace.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Sync>
class allocator_base
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Typ*|Typ prvků přidělaná přidělujícího modulu.|
|*Synchronizace*|Zásady synchronizace pro přidělování, což je [sync_none – třída](../standard-library/sync-none-class.md), [sync_per_container – třída](../standard-library/sync-per-container-class.md), [sync_per_thread – třída](../standard-library/sync-per-thread-class.md), nebo [sync_shared – Třída](../standard-library/sync-shared-class.md).|

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[allocator_base –](#allocator_base)|Vytvoří objekt typu `allocator_base`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[const_pointer](#const_pointer)|Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.|
|[const_reference](#const_reference)|Typ, který poskytuje konstantní odkaz na typ objektu spravovaného pomocí přidělujícího modulu.|
|[difference_type](#difference_type)|Celočíselný typ se znaménkem, které mohou představovat rozdíl mezi hodnotami ukazatelů na typ objektu spravovaného pomocí přidělujícího modulu.|
|[Ukazatel](#pointer)|Typ, který poskytuje ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na typ objektu spravovaného pomocí přidělujícího modulu.|
|[size_type](#size_type)|Bez znaménka celočíselného typu, který může představovat Délka libovolného pořadí, které objekt třídy šablony `allocator_base` můžete přidělit.|
|[value_type](#value_type)|Typ, který je spravovaný nástrojem přidělujícího modulu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[_Charalloc](#charalloc)|Alokují prostor pro pole typu **char**.|
|[_Chardealloc –](#chardealloc)|Uvolňuje úložiště pro pole obsahující prvky typu **char**.|
|[Adresa](#address)|Vyhledá adresu objektu, jehož hodnota je určena.|
|[allocate](#allocate)|Přiděluje blok paměti dostatečně velký pro uložení alespoň nějaké zadaný počet prvků.|
|[Konstrukce](#construct)|Vytvoří konkrétní typ objektu na zadané adrese, který je inicializován se zadanou hodnotou.|
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů z úložiště počínaje na určené pozici.|
|[zrušení](#destroy)|Volá destruktor objekty bez rušení přidělení paměti uložení objektu.|
|[max_size](#max_size)|Vrátí počet prvků typu *typ* , které by mohly být přiděleny v objektu alokátoru třídy předtím, než se využilo volné paměti.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="charalloc"></a>  allocator_base::_Charalloc

Alokují prostor pro pole typu **char**.

```cpp
char *_Charalloc(size_type count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Počet*|Počet prvků v poli, které mají být přiděleny.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidělený objekt.

### <a name="remarks"></a>Poznámky

Tato členská funkce používá kontejnery při kompilaci s kompilátorem, který nejde zkompilovat obnovení vazby. Implementuje `_Charalloc` pro uživatelem definované allocator vrácením výsledku volání `allocate` funkce filtru synchronizace.

## <a name="chardealloc"></a>  allocator_base::_Chardealloc

Uvolňuje úložiště pro pole obsahující prvky typu **char**.

```cpp
void _Chardealloc(void* ptr, size_type count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel na první objekt k zrušeno přidělení úložiště.|
|*Počet*|Počet objektů pro zrušeno přidělení úložiště.|

### <a name="remarks"></a>Poznámky

Tato členská funkce používá kontejnery při kompilaci s kompilátorem, který nejde zkompilovat obnovení vazby. Implementuje `_Chardealloc` pro uživatelem definované allocator voláním `deallocate` funkce filtru synchronizace. Ptr ukazatel musí byla předtím vrácena voláním `_Charalloc` pro objekt alokátoru, který při porovnání rovna `*this`, přidělení objektu array stejné velikosti a typu. `_Chardealloc` nikdy nevyvolá výjimku.

## <a name="address"></a>  allocator_base::Address

Vyhledá adresu objektu, jehož hodnota je určena.

```cpp
pointer address(reference val);

const_pointer address(const_reference val);
```

### <a name="parameters"></a>Parametry

*Val* const nebo nonconst hodnotu objektu, jehož adresu má být vyhledán pro.

### <a name="return-value"></a>Návratová hodnota

Najít hodnoty, resp. const nebo nonconst konstantní nebo nonconst ukazatel na objekt.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementován pro allocator definovaný uživatelem, tak, že vrací `&val`.

## <a name="allocate"></a>  allocator_base::allocate

Přiděluje blok paměti dostatečně velký pro uložení alespoň nějaké zadaný počet prvků.

```cpp
template <class Other>
pointer allocate(size_type _Nx, const Other* _Hint = 0);

pointer allocate(size_type _Nx);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Počet prvků v poli, které mají být přiděleny.|
|*_Hint*|Tento parametr je ignorován.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidělený objekt.

### <a name="remarks"></a>Poznámky

Členská funkce implementuje přidělení paměti pro uživatelem definované allocator vrácením výsledku volání `allocate` funkce filtru typu typ, který synchronizace `*` Pokud `_Nx == 1`, jinak vrací výsledek volání za účelem `operator new(_Nx * sizeof(Type))` přetypování na typ `*`.

## <a name="allocator_base"></a>  allocator_base::allocator_base

Vytvoří objekt typu `allocator_base`.

```cpp
allocator_base();

template <class Other>
allocator_base(const allocator_base<Other, Sync>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doprava*|Objekt alokátoru, který má být zkopírován.|

### <a name="remarks"></a>Poznámky

První konstruktor zkonstruuje [allocator_base –](../standard-library/allocator-base-class.md) instance. Druhý konstruktor vytvoří `allocator_base` instance, které pro všechny `allocator_base<Type, _Sync>` instance `a`, `allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a`.

## <a name="const_pointer"></a>  allocator_base::const_pointer

Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.

```cpp
typedef const Type *const_pointer;
```

## <a name="const_reference"></a>  allocator_base::const_reference

Typ, který poskytuje konstantní odkaz na typ objektu spravovaného pomocí přidělujícího modulu.

```cpp
typedef const Type& const_reference;
```

## <a name="construct"></a>  allocator_base::Construct

Vytvoří konkrétní typ objektu na zadané adrese, který je inicializován se zadanou hodnotou.

```cpp
void construct(pointer ptr, const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel na umístění, kde má být vytvořen objekt.|
|*Val*|Hodnota, pomocí kterého je inicializovat objekt vytváří.|

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementován pro uživatelem definované allocator voláním `new((void*)ptr Type(val)`.

## <a name="deallocate"></a>  allocator_base::deallocate

Uvolní zadaný počet objektů z úložiště počínaje na určené pozici.

```cpp
void deallocate(pointer ptr, size_type _Nx);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel na první objekt k zrušeno přidělení úložiště.|
|*_Nx*|Počet objektů pro zrušeno přidělení úložiště.|

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementován pro uživatelem definované allocator voláním `deallocate(ptr)` na filtr synchronizace `Sync` Pokud `_Nx == 1`, jinak voláním `operator delete(_Nx * ptr)`.

## <a name="destroy"></a>  allocator_base::Destroy

Volá destruktor objekty bez rušení přidělení paměti uložení objektu.

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel s vyznačením adresu objektu, který se má zničit.|

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementován pro uživatelem definované allocator voláním `ptr->~Type()`.

## <a name="difference_type"></a>  allocator_base::difference_type

Celočíselný typ se znaménkem, které mohou představovat rozdíl mezi hodnotami ukazatelů na typ objektu spravovaného pomocí přidělujícího modulu.

```cpp
typedef std::ptrdiff_t difference_type;
```

## <a name="max_size"></a>  allocator_base::max_size

Vrátí počet prvků typu `Type` , které by mohly být přiděleny v objektu alokátoru třídy předtím, než se využilo volné paměti.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které by mohly být přiděleny.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementován pro allocator definovaný uživatelem, tak, že vrací `(size_t)-1 / sizeof(Type)` Pokud `0 < (size_t)-1 / sizeof(Type)`, jinak `1`.

## <a name="pointer"></a>  allocator_base::Pointer

Typ, který poskytuje ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.

```cpp
typedef Type *pointer;
```

## <a name="reference"></a>  allocator_base::Reference

Typ, který poskytuje odkaz na typ objektu spravovaného pomocí přidělujícího modulu.

```cpp
typedef Type& reference;
```

## <a name="size_type"></a>  allocator_base::size_type

Bez znaménka celočíselného typu, který může představovat Délka libovolného pořadí, které objekt třídy šablony `allocator_base` můžete přidělit.

```cpp
typedef std::size_t size_type;
```

## <a name="value_type"></a>  allocator_base::value_type

Typ, který je spravovaný nástrojem přidělujícího modulu.

```cpp
typedef Type value_type;
```

## <a name="see-also"></a>Viz také:

[\<alokátory: >](../standard-library/allocators-header.md)<br/>
