---
title: sync_per_container – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
ms.openlocfilehash: 2c60911b5469cbf74944c9f63af44f2351790280
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376555"
---
# <a name="sync_per_container-class"></a>sync_per_container – třída

Popisuje [filtr synchronizace,](../standard-library/allocators-header.md) který poskytuje samostatný objekt mezipaměti pro každý objekt přidělování.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_per_container
    : public Cache
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Typ mezipaměti přidružené k filtru synchronizace. To může být [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md)nebo [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[equals](#equals)|Porovná dvě mezipaměti pro rovnost.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátory>

**Obor názvů:** stdext

## <a name="sync_per_containerequals"></a><a name="equals"></a>sync_per_container::rovná se

Porovná dvě mezipaměti pro rovnost.

```cpp
bool equals(const sync_per_container<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Objekt mezipaměti filtru synchronizace.|
|*Další*|Objekt mezipaměti porovnat rovnost.|

### <a name="return-value"></a>Návratová hodnota

Členská funkce vždy vrátí **false**.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[\<alokátory>](../standard-library/allocators-header.md)
