---
title: rts_alloc – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4bff519ea12646e94e92cde219fa38e4009a767
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956450"
---
# <a name="rtsalloc-class"></a>rts_alloc – třída

Rts_alloc – třída šablony popisuje [filtr](../standard-library/allocators-header.md) , který obsahuje celou řadu mezipaměti instancí a určuje, kterou instanci chcete použít pro přidělování a navracení zpět za běhu místo v době kompilace.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*mezipaměť*|Typ instance mezipaměti obsažené v poli. To může být [cache_chunklist – třída](../standard-library/cache-chunklist-class.md), [cache_freelist –](../standard-library/cache-freelist-class.md), nebo [cache_suballoc –](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Poznámky

Této třídy šablony obsahuje více bloku přidělování instancí a určuje, kterou instanci chcete použít pro přidělení nebo zrušení přidělení v době běhu místo v době kompilace. Používá se s kompilátory, které nelze zkompilovat obnovení vazby.

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přiděluje blok paměti.|
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů z úložiště počínaje na určené pozici.|
|[equals](#equals)|Porovná rovnost dvou mezipamětí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="allocate"></a>  rts_alloc::allocate

Přiděluje blok paměti.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Počet*|Počet prvků v poli, které mají být přiděleny.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidělený objekt.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `caches[_IDX].allocate(count)`, kde index `_IDX` se určuje podle velikosti požadovaný blok *počet*, nebo pokud *počet* je příliš velký, vrátí `operator new(count)`. `cache`, který představuje objekt mezipaměti.

## <a name="deallocate"></a>  rts_alloc::deallocate

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

Volání členských funkcí `caches[_IDX].deallocate(ptr, count)`, kde index `_IDX` se určuje podle velikosti požadovaný blok *počet*, nebo pokud *počet* je příliš velký, vrátí `operator delete(ptr)`.

## <a name="equals"></a>  rts_alloc::Equals

Porovná rovnost dvou mezipamětí.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Cache*|Objekt mezipaměti přidružené k filtru.|
|*Ji_né*|Mezipaměť objekt k porovnání rovnosti.|

### <a name="remarks"></a>Poznámky

**Hodnota TRUE** Pokud výsledek `caches[0].equals(other.caches[0])`; v opačném případě **false**. `caches` představuje pole objektů mezipaměti.

## <a name="see-also"></a>Viz také:

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)<br/>
[\<alokátory: >](../standard-library/allocators-header.md)<br/>
