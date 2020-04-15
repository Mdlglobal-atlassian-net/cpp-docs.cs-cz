---
title: freelist – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
ms.openlocfilehash: 712c1f1638b954d1580eb527dd9eab7401917517
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317208"
---
# <a name="freelist-class"></a>freelist – třída

Spravuje seznam paměťových bloků.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Sz*|Počet prvků v poli, které mají být přiděleny.|
|*Max*|Maximální třída představující maximální počet prvků, které mají být uloženy v seznamu volných. Maximální třída může být [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md)nebo [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Poznámky

Tato šablona třídy spravuje seznam paměťových bloků velikosti *Sz* s maximální délkou seznamu určenou maximální třídou předanou v *max*.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[volný seznam](#freelist)|Vytvoří objekt typu `freelist`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Pop](#pop)|Odebere první blok paměti ze seznamu volných.|
|[Push](#push)|Přidá do seznamu blok paměti.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátory>

**Obor názvů:** stdext

## <a name="freelistfreelist"></a><a name="freelist"></a>freelist::freelist

Vytvoří objekt typu `freelist`.

```cpp
freelist();
```

### <a name="remarks"></a>Poznámky

## <a name="freelistpop"></a><a name="pop"></a>freelist::pop

Odebere první blok paměti ze seznamu volných.

```cpp
void *pop();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na blok paměti odebrán ze seznamu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu NULL, pokud je seznam prázdný. V opačném případě odebere první blok paměti ze seznamu.

## <a name="freelistpush"></a><a name="push"></a>volný seznam::push

Přidá do seznamu blok paměti.

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Ptr*|Ukazatel na blok paměti, který má být přidán do seznamu volných.|

### <a name="return-value"></a>Návratová hodnota

**true,** `full` pokud funkce max třídy vrátí **false**; v opačném `push` případě funkce vrátí **false**.

### <a name="remarks"></a>Poznámky

Pokud `full` funkce třídy max vrátí **hodnotu false**, přidá tato členská funkce blok paměti, na který *ptr* ukazuje, do hlavy seznamu.

## <a name="see-also"></a>Viz také

[\<alokátory>](../standard-library/allocators-header.md)
