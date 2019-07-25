---
title: allocator_base – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 115f5ad4461b98f24e3aa6756e501b91ae3a1566
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456435"
---
# <a name="allocatorbase-class"></a>allocator_base – třída

Definuje základní třídu a běžné funkce potřebné k vytvoření uživatelem definovaného přidělování z filtru synchronizace.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Sync>
class allocator_base
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Typ*|Typ prvků přidělených přidělováním.|
|*Synchronizace*|Zásady synchronizace pro přidělování, což je [Třída sync_none](../standard-library/sync-none-class.md)třídy, třída [sync_per_container](../standard-library/sync-per-container-class.md), třída [sync_per_thread](../standard-library/sync-per-thread-class.md)nebo [Třída sync_shared](../standard-library/sync-shared-class.md).|

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[allocator_base](#allocator_base)|Vytvoří objekt typu `allocator_base`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[const_pointer](#const_pointer)|Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného přidělováním.|
|[const_reference](#const_reference)|Typ, který poskytuje konstantní odkaz na typ objektu spravovaného přidělováním.|
|[difference_type](#difference_type)|Podepsaný integrální typ, který může představovat rozdíl mezi hodnotami ukazatelů na typ objektu spravovaného přidělováním.|
|[pointer](#pointer)|Typ, který poskytuje ukazatel na typ objektu spravovaného přidělováním.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na typ objektu spravovaného přidělováním.|
|[size_type](#size_type)|Celočíselný typ bez znaménka, který může představovat délku jakékoli sekvence, kterou může objekt třídy `allocator_base` šablony přidělit.|
|[value_type](#value_type)|Typ, který je spravován přidělováním.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[_Charalloc](#charalloc)|Přidělí úložiště pro pole typu **char**.|
|[_Chardealloc](#chardealloc)|Uvolní úložiště pro pole obsahující prvky typu **char**.|
|[address](#address)|Najde adresu objektu, jehož hodnota je určena.|
|[allocate](#allocate)|Přidělí dostatečně velký blok paměti pro uložení alespoň některého zadaného počtu prvků.|
|[Contains](#construct)|Vytvoří konkrétní typ objektu na zadané adrese, která je inicializována se zadanou hodnotou.|
|[uvolnit](#deallocate)|Uvolní zadaný počet objektů od úložiště, které začínají na zadané pozici.|
|[způsobit](#destroy)|Volá destruktor objektů bez zrušení přidělení paměti, kde byl objekt uložen.|
|[max_size](#max_size)|Vrátí počet prvků typu *typu, které* mohou být přiděleny objektem přidělování tříd před vyřazením volné paměti.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> přidělování

**Obor názvů:** stdext

## <a name="charalloc"></a>allocator_base::_Charalloc

Přidělí úložiště pro pole typu **char**.

```cpp
char *_Charalloc(size_type count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*výpočtu*|Počet prvků v poli, které mají být přiděleny.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidělený objekt.

### <a name="remarks"></a>Poznámky

Tato členská funkce se používá kontejnery při kompilaci s kompilátorem, který nemůže kompilovat opětovnou vazby. Implementuje `_Charalloc` pro uživatelem definované přidělování tím, že vrátí výsledek volání `allocate` funkce filtru synchronizace.

## <a name="chardealloc"></a>allocator_base::_Chardealloc

Uvolní úložiště pro pole obsahující prvky typu **char**.

```cpp
void _Chardealloc(void* ptr, size_type count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel na první objekt, který má být vrácen z úložiště.|
|*výpočtu*|Počet objektů, které se mají uvolnit z úložiště|

### <a name="remarks"></a>Poznámky

Tato členská funkce se používá kontejnery při kompilaci s kompilátorem, který nemůže kompilovat opětovnou vazby. Implementuje `_Chardealloc` pro uživatelem definované přidělování `deallocate` voláním funkce filtru synchronizace. Ukazatel PTR musí být dříve vrácen voláním `_Charalloc` pro objekt Alokátor, který porovnává `*this`hodnotu EQUAL a přidělení objektu pole stejné velikosti a typu. `_Chardealloc`nikdy nevyvolává výjimku.

## <a name="address"></a>allocator_base:: Address

Najde adresu objektu, jehož hodnota je určena.

```cpp
pointer address(reference val);

const_pointer address(const_reference val);
```

### <a name="parameters"></a>Parametry

*počítává*\
Hodnota konstanty nebo nepodílu objektu, jehož adresa je prohledávána.

### <a name="return-value"></a>Návratová hodnota

Typ const nebo nepodílu na objektu nalezený, v uvedeném pořadí, konstanta nebo hodnota nenevýhody.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementovaná pro uživatelem definované přidělování vrácením `&val`.

## <a name="allocate"></a>allocator_base:: allocate

Přidělí dostatečně velký blok paměti pro uložení alespoň některého zadaného počtu prvků.

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

Členská funkce implementuje přidělení paměti pro uživatelem definované přidělování tím, že vrátí výsledek volání `allocate` funkce filtru synchronizace typu `*` typ, pokud, v opačném případě `_Nx == 1`vrácením výsledku typu volání přetypování na typ typu `*`. `operator new(_Nx * sizeof(Type))`

## <a name="allocator_base"></a>allocator_base::allocator_base

Vytvoří objekt typu `allocator_base`.

```cpp
allocator_base();

template <class Other>
allocator_base(const allocator_base<Other, Sync>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Kliknutím*|Objekt přidělování, který se má zkopírovat|

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří instanci [allocator_base](../standard-library/allocator-base-class.md) . Druhý konstruktor vytvoří `allocator_base` instanci, tak jak pro libovolnou `allocator_base<Type, _Sync>` instanci `a`, `allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a`.

## <a name="const_pointer"></a>allocator_base::const_pointer

Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného přidělováním.

```cpp
typedef const Type *const_pointer;
```

## <a name="const_reference"></a>allocator_base::const_reference

Typ, který poskytuje konstantní odkaz na typ objektu spravovaného přidělováním.

```cpp
typedef const Type& const_reference;
```

## <a name="construct"></a>allocator_base:: Construct

Vytvoří konkrétní typ objektu na zadané adrese, která je inicializována se zadanou hodnotou.

```cpp
void construct(pointer ptr, const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel na umístění, kde má být objekt vytvořen.|
|*počítává*|Hodnota, se kterou má být inicializován objekt vytvořen.|

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementovaná pro uživatelem definované přidělování voláním `new((void*)ptr Type(val)`.

## <a name="deallocate"></a>allocator_base::d eallocate

Uvolní zadaný počet objektů od úložiště, které začínají na zadané pozici.

```cpp
void deallocate(pointer ptr, size_type _Nx);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel na první objekt, který má být vrácen z úložiště.|
|*_Nx*|Počet objektů, které se mají uvolnit z úložiště|

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementována pro uživatelem definované přidělování voláním `deallocate(ptr)` filtru `Sync` synchronizace, pokud `_Nx == 1`, jinak voláním `operator delete(_Nx * ptr)`.

## <a name="destroy"></a>allocator_base::d estroy

Volá destruktor objektů bez zrušení přidělení paměti, kde byl objekt uložen.

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel označující adresu objektu, který má být zničen.|

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementovaná pro uživatelem definované přidělování voláním `ptr->~Type()`.

## <a name="difference_type"></a>allocator_base::d ifference_type

Podepsaný integrální typ, který může představovat rozdíl mezi hodnotami ukazatelů na typ objektu spravovaného přidělováním.

```cpp
typedef std::ptrdiff_t difference_type;
```

## <a name="max_size"></a>allocator_base::max_size

Vrátí počet prvků typu `Type` , které mohou být přiděleny objektem Alokátor třídy před vyřazením volné paměti.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které mohou být přiděleny.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementována pro uživatelem definované přidělování tím, `(size_t)-1 / sizeof(Type)` že `0 < (size_t)-1 / sizeof(Type)`vrátí IF `1`, jinak.

## <a name="pointer"></a>allocator_base::p ointer

Typ, který poskytuje ukazatel na typ objektu spravovaného přidělováním.

```cpp
typedef Type *pointer;
```

## <a name="reference"></a>allocator_base:: Reference

Typ, který poskytuje odkaz na typ objektu spravovaného přidělováním.

```cpp
typedef Type& reference;
```

## <a name="size_type"></a>allocator_base::size_type

Celočíselný typ bez znaménka, který může představovat délku jakékoli sekvence, kterou může objekt třídy `allocator_base` šablony přidělit.

```cpp
typedef std::size_t size_type;
```

## <a name="value_type"></a>allocator_base::value_type

Typ, který je spravován přidělováním.

```cpp
typedef Type value_type;
```

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)
