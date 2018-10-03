---
title: sync_per_container – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
dev_langs:
- C++
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d470b60716ab81636be838f2a61e58542a52ffd9
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234837"
---
# <a name="syncpercontainer-class"></a>sync_per_container – třída

Popisuje [filtr synchronizace](../standard-library/allocators-header.md) , který poskytuje objekt samostatné mezipaměti pro každý objekt alokátoru.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_per_container
    : public Cache
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*mezipaměť*|Typ mezipaměti přidružené k filtru synchronizace. To může být [cache_chunklist –](../standard-library/cache-chunklist-class.md), [cache_freelist –](../standard-library/cache-freelist-class.md), nebo [cache_suballoc –](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[equals](#equals)|Porovná rovnost dvou mezipamětí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="equals"></a>  sync_per_container::Equals

Porovná rovnost dvou mezipamětí.

```cpp
bool equals(const sync_per_container<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*mezipaměť*|Objekt mezipaměti filtr synchronizace.|
|*Jiné*|Mezipaměť objekt k porovnání rovnosti.|

### <a name="return-value"></a>Návratová hodnota

Členská funkce vždy vrátí **false**.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[\<alokátory: >](../standard-library/allocators-header.md)<br/>
