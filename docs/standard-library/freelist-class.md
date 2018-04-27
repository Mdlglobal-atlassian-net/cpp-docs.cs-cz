---
title: FreeList – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
dev_langs:
- C++
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9b332dcf7b67f6d5054ea4d160faac6ea2a5ad17
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="freelist-class"></a>freelist – třída

Spravuje seznam bloky paměti.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, class Max>
class freelist
 : public Max
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`Sz`|Počet prvků v poli, která bude přidělena.|
|`Max`|Maximální třída představující maximální počet elementů k uložení do seznamu volné. Maximální třída může být [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md), nebo [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Poznámky

Tato třída šablony spravuje seznam bloky paměti o velikosti `Sz` s maximální délkou seznamu určit maximální třídou předaná `Max`.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[FreeList](#freelist)|Vytvoří objekt typu `freelist`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[POP](#pop)|Odebere první blok paměti ze seznamu volné.|
|[push](#push)|Blok paměti přidá do seznamu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext –

## <a name="freelist"></a>  FreeList::FreeList

Vytvoří objekt typu `freelist`.

```cpp
freelist();
```

### <a name="remarks"></a>Poznámky

## <a name="pop"></a>  FreeList::POP

Odebere první blok paměti ze seznamu volné.

```cpp
void *pop();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatele na blok paměti odebrat ze seznamu.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu `NULL` Pokud je seznam prázdný. Odebere, jinak hodnota prvního bloku paměti ze seznamu.

## <a name="push"></a>  FreeList::push

Blok paměti přidá do seznamu.

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`ptr`|Ukazatel na paměti blok, který má být přidán do seznamu volné.|

### <a name="return-value"></a>Návratová hodnota

`true` Pokud `full` funkce max třídy vrací `false`, jinak hodnota `push` funkce vrátí `false`.

### <a name="remarks"></a>Poznámky

Pokud `full` funkce max třídy vrací `false`, přidá bloku paměti, na kterou odkazuje tento – členská funkce `ptr` na první pozice v seznamu.

## <a name="see-also"></a>Viz také

[\<alokátorů >](../standard-library/allocators-header.md)<br/>
