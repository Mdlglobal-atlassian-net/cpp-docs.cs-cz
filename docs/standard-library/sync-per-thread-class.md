---
title: sync_per_thread – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_thread
- allocators/stdext::sync_per_thread::allocate
- allocators/stdext::sync_per_thread::deallocate
- allocators/stdext::sync_per_thread::equals
helpviewer_keywords:
- stdext::sync_per_thread
- stdext::sync_per_thread [C++], allocate
- stdext::sync_per_thread [C++], deallocate
- stdext::sync_per_thread [C++], equals
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
ms.openlocfilehash: 3cb1946ee68642065488cfd13c146abab818ec60
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623259"
---
# <a name="syncperthread-class"></a>sync_per_thread – třída

Popisuje [filtr synchronizace](../standard-library/allocators-header.md) , který poskytuje objekt samostatné mezipaměti pro každé vlákno.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_per_thread
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Typ mezipaměti přidružené k filtru synchronizace. To může být [cache_chunklist –](../standard-library/cache-chunklist-class.md), [cache_freelist –](../standard-library/cache-freelist-class.md), nebo [cache_suballoc –](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Poznámky

Alokátory, které používají `sync_per_thread` můžete porovnávají se stejně i v případě, že bloky, které jsou přiděleny v jednom vlákně nelze uvolnit z jiného vlákna. Když pomocí jedné z těchto alokátorů bloky paměti přidělené v jedno vlákno by neměl nastavena jako viditelná pro ostatní vlákna. V praxi to znamená, že kontejner, který používá jednu z těchto alokátorů musí přistupovat pouze jedno vlákno.

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přiděluje blok paměti.|
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů z úložiště počínaje na určené pozici.|
|[equals](#equals)|Porovná rovnost dvou mezipamětí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="allocate"></a>  sync_per_thread::allocate

Přiděluje blok paměti.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Počet*|Počet prvků v poli, které mají být přiděleny.|

### <a name="remarks"></a>Poznámky

Členská funkce vrátí výsledek volání `cache::allocate(count)` na objekt mezipaměti patřících k tomuto vláknu. Pokud byl přidělen žádný objekt mezipaměti pro aktuální vlákno, nejprve přiděluje jeden.

## <a name="deallocate"></a>  sync_per_thread::deallocate

Uvolní zadaný počet objektů z úložiště počínaje na určené pozici.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel na první objekt k zrušeno přidělení úložiště.|
|*Počet*|Počet objektů pro zrušeno přidělení úložiště.|

### <a name="remarks"></a>Poznámky

Volání členských funkcí `deallocate` na objekt mezipaměti patřících k tomuto vláknu. Pokud byl přidělen žádný objekt mezipaměti pro aktuální vlákno, nejprve přiděluje jeden.

## <a name="equals"></a>  sync_per_thread::Equals

Porovná rovnost dvou mezipamětí.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Objekt mezipaměti filtr synchronizace.|
|*Jiné*|Mezipaměť objekt k porovnání rovnosti.|

### <a name="return-value"></a>Návratová hodnota

**false** Pokud byl přidělen žádný objekt mezipaměti pro tento objekt nebo *jiných* v aktuálním vlákně. V opačném případě vrátí výsledek použití `operator==` dvěma objekty mezipaměti.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[\<alokátory: >](../standard-library/allocators-header.md)<br/>
