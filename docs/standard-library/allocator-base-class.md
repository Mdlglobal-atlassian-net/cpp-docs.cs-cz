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
ms.openlocfilehash: f93c8ff53452fc98415e194966960254e7b44143
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364986"
---
# <a name="allocator_base-class"></a>allocator_base – třída

Definuje základní třídu a běžné funkce potřebné k vytvoření uživatelem definovaného alokátoru z filtru synchronizace.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Sync>
class allocator_base
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Typ*|Typ prvků přidělených alokátorem.|
|*Synchronizovat*|Zásady synchronizace pro alokátor, který je [sync_none Class](../standard-library/sync-none-class.md), [sync_per_container Class](../standard-library/sync-per-container-class.md), sync_per_thread [Class](../standard-library/sync-per-thread-class.md)nebo [sync_shared Class](../standard-library/sync-shared-class.md).|

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[allocator_base](#allocator_base)|Vytvoří objekt typu `allocator_base`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[const_pointer](#const_pointer)|Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného alokátorem.|
|[const_reference](#const_reference)|Typ, který poskytuje konstantní odkaz na typ objektu spravovaného alokátorem.|
|[difference_type](#difference_type)|Podepsaný integrální typ, který může představovat rozdíl mezi hodnotami ukazatelů na typ objektu spravovaného alokátorem.|
|[ukazatel](#pointer)|Typ, který poskytuje ukazatel na typ objektu spravovaného alokátorem.|
|[Odkaz](#reference)|Typ, který poskytuje odkaz na typ objektu spravovaného alokátorem.|
|[size_type](#size_type)|Nepodepsaný integrální typ, který může představovat `allocator_base` délku libovolné sekvence, kterou může objekt typu přidělit.|
|[value_type](#value_type)|Typ, který je spravován alokátorem.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[_Charalloc](#charalloc)|Přiděluje úložiště pro pole typu **char**.|
|[_Chardealloc](#chardealloc)|Uvolní úložiště pro pole obsahující prvky typu **char**.|
|[Adresu](#address)|Vyhledá adresu objektu, jehož hodnota je zadána.|
|[allocate](#allocate)|Přidělí blok paměti dostatečně velký pro uložení alespoň některé zadaný počet prvků.|
|[Vytvořit](#construct)|Vytvoří určitý typ objektu na zadané adrese, která je inicializována se zadanou hodnotou.|
|[Navrátit](#deallocate)|Uvolní zadaný počet objektů z úložiště začínající na zadané pozici.|
|[destroy](#destroy)|Volá destruktor objektů bez zrušení přidělení paměti, kde byl uložen objekt.|
|[max_size](#max_size)|Vrátí počet prvků typu *Type,* které by mohly být přiděleny objektem alokátoru třídy před vybitou volnou pamětí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátory>

**Obor názvů:** stdext

## <a name="allocator_base_charalloc"></a><a name="charalloc"></a>allocator_base::_Charalloc

Přiděluje úložiště pro pole typu **char**.

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

Tato členská funkce je používána kontejnery při kompilaci s kompilátorem, který nemůže zkompilovat rebind. Implementuje `_Charalloc` pro uživatelem definované přidělování vrácením výsledek volání `allocate` funkce filtru synchronizace.

## <a name="allocator_base_chardealloc"></a><a name="chardealloc"></a>allocator_base::_Chardealloc

Uvolní úložiště pro pole obsahující prvky typu **char**.

```cpp
void _Chardealloc(void* ptr, size_type count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Ptr*|Ukazatel na první objekt, který má být deallocated z úložiště.|
|*Počet*|Počet objektů, které mají být deallocated z úložiště.|

### <a name="remarks"></a>Poznámky

Tato členská funkce je používána kontejnery při kompilaci s kompilátorem, který nemůže zkompilovat rebind. Implementuje `_Chardealloc` pro uživatelem definované přidělování voláním `deallocate` funkce filtru synchronizace. Ukazatel ptr musí být dříve vrácena `_Charalloc` volání pro objekt přidělování, který `*this`porovnává rovná , přidělení objektu pole stejné velikosti a typu. `_Chardealloc`nikdy vyvolá výjimku.

## <a name="allocator_baseaddress"></a><a name="address"></a>allocator_base::adresa

Vyhledá adresu objektu, jehož hodnota je zadána.

```cpp
pointer address(reference val);

const_pointer address(const_reference val);
```

### <a name="parameters"></a>Parametry

*Val*\
Hodnota const nebo nonconst objektu, jehož adresa je hledána.

### <a name="return-value"></a>Návratová hodnota

Const nebo nonconst ukazatel na objekt nalezen, v uvedeném pořadí, const nebo nonconst hodnotu.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementována pro uživatelem `&val`definovaný alokátor vrácením .

## <a name="allocator_baseallocate"></a><a name="allocate"></a>allocator_base::přidělit

Přidělí blok paměti dostatečně velký pro uložení alespoň některé zadaný počet prvků.

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

Členská funkce implementuje přidělení paměti pro uživatelem definovaný alokátor vrácením `allocate` výsledku volání funkce synchronizačního filtru typu Type `*` , jinak `operator new(_Nx * sizeof(Type))` `*` `_Nx == 1`vrácením výsledku volání přetypování typu Type .

## <a name="allocator_baseallocator_base"></a><a name="allocator_base"></a>allocator_base::allocator_base

Vytvoří objekt typu `allocator_base`.

```cpp
allocator_base();

template <class Other>
allocator_base(const allocator_base<Other, Sync>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Právo*|Alokátor objektu, který má být zkopírován.|

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří [instanci allocator_base.](../standard-library/allocator-base-class.md) Druhý konstruktor vytvoří `allocator_base` instanci tak, `a` `allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a`aby pro každou `allocator_base<Type, _Sync>` instanci , .

## <a name="allocator_baseconst_pointer"></a><a name="const_pointer"></a>allocator_base::const_pointer

Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného alokátorem.

```cpp
typedef const Type *const_pointer;
```

## <a name="allocator_baseconst_reference"></a><a name="const_reference"></a>allocator_base::const_reference

Typ, který poskytuje konstantní odkaz na typ objektu spravovaného alokátorem.

```cpp
typedef const Type& const_reference;
```

## <a name="allocator_baseconstruct"></a><a name="construct"></a>allocator_base::konstrukce

Vytvoří určitý typ objektu na zadané adrese, která je inicializována se zadanou hodnotou.

```cpp
void construct(pointer ptr, const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Ptr*|Ukazatel na umístění, kde má být objekt vytvořen.|
|*Val*|Hodnota, se kterou má být objekt, který je konstruován, má být inicializován.|

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementována pro uživatelem definovaný alokátor voláním `new((void*)ptr Type(val)`.

## <a name="allocator_basedeallocate"></a><a name="deallocate"></a>allocator_base::deallocate

Uvolní zadaný počet objektů z úložiště začínající na zadané pozici.

```cpp
void deallocate(pointer ptr, size_type _Nx);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Ptr*|Ukazatel na první objekt, který má být deallocated z úložiště.|
|*_Nx*|Počet objektů, které mají být deallocated z úložiště.|

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementována pro uživatelem definovaný alokátor voláním `deallocate(ptr)` filtru `Sync` synchronizace, pokud `_Nx == 1`, jinak voláním `operator delete(_Nx * ptr)`.

## <a name="allocator_basedestroy"></a><a name="destroy"></a>allocator_base::destroy

Volá destruktor objektů bez zrušení přidělení paměti, kde byl uložen objekt.

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Ptr*|Ukazatel označující adresu objektu, který má být zničen.|

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementována pro uživatelem definovaný alokátor voláním `ptr->~Type()`.

## <a name="allocator_basedifference_type"></a><a name="difference_type"></a>allocator_base::difference_type

Podepsaný integrální typ, který může představovat rozdíl mezi hodnotami ukazatelů na typ objektu spravovaného alokátorem.

```cpp
typedef std::ptrdiff_t difference_type;
```

## <a name="allocator_basemax_size"></a><a name="max_size"></a>allocator_base::max_size

Vrátí počet prvků typu, `Type` které by mohly být přiděleny objektem alokátoru třídy před vybitou volnou pamětí.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které by mohly být přiděleny.

### <a name="remarks"></a>Poznámky

Tato členská funkce je implementována pro uživatelem `(size_t)-1 / sizeof(Type)` `0 < (size_t)-1 / sizeof(Type)`definovaný `1`alokátor vrácením, pokud , jinak .

## <a name="allocator_basepointer"></a><a name="pointer"></a>allocator_base::pointer

Typ, který poskytuje ukazatel na typ objektu spravovaného alokátorem.

```cpp
typedef Type *pointer;
```

## <a name="allocator_basereference"></a><a name="reference"></a>allocator_base::odkaz

Typ, který poskytuje odkaz na typ objektu spravovaného alokátorem.

```cpp
typedef Type& reference;
```

## <a name="allocator_basesize_type"></a><a name="size_type"></a>allocator_base::size_type

Nepodepsaný integrální typ, který může představovat `allocator_base` délku libovolné sekvence, kterou může objekt typu přidělit.

```cpp
typedef std::size_t size_type;
```

## <a name="allocator_basevalue_type"></a><a name="value_type"></a>allocator_base::value_type

Typ, který je spravován alokátorem.

```cpp
typedef Type value_type;
```

## <a name="see-also"></a>Viz také

[\<alokátory>](../standard-library/allocators-header.md)
