---
title: FreeList – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae7e56fd33de888ad31a24ad1e3130acc96daa28
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702827"
---
# <a name="freelist-class"></a>freelist – třída

Spravuje seznam bloky paměti.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Sz*|Počet prvků v poli, které mají být přiděleny.|
|*Max*|Maximální počet Třída reprezentující maximální počet prvků, které mají být uloženy v seznamu zdarma. Maximální počet třída může být [max_none –](../standard-library/max-none-class.md), [max_unbounded –](../standard-library/max-unbounded-class.md), [max_fixed_size –](../standard-library/max-fixed-size-class.md), nebo [max_variable_size –](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Poznámky

Spravuje seznam paměťových bloků velikosti této třídy šablony *Sz* s maximální délkou seznamu určit maximální třídou předaný *maximální*.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[FreeList –](#freelist)|Vytvoří objekt typu `freelist`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[POP](#pop)|Odebere první blok paměti ze seznamu zdarma.|
|[push](#push)|Blok paměti se přidá do seznamu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="freelist"></a>  FreeList::FreeList

Vytvoří objekt typu `freelist`.

```cpp
freelist();
```

### <a name="remarks"></a>Poznámky

## <a name="pop"></a>  FreeList::POP

Odebere první blok paměti ze seznamu zdarma.

```cpp
void *pop();
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na blok paměti odebrán ze seznamu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu NULL, pokud je seznam prázdný. V opačném případě Odebere první blok paměti ze seznamu.

## <a name="push"></a>  FreeList::push

Blok paměti se přidá do seznamu.

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatele na blok paměti mají být přidány do seznamu zdarma.|

### <a name="return-value"></a>Návratová hodnota

**true** Pokud `full` vrátí maximální třídy **false**; v opačném případě `push` vrací funkce **false**.

### <a name="remarks"></a>Poznámky

Pokud `full` vrátí maximální třídy **false**, přidá bloku paměti, na které odkazuje tato členská funkce *ptr* k začátku seznamu.

## <a name="see-also"></a>Viz také:

[\<alokátory: >](../standard-library/allocators-header.md)<br/>
