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
ms.openlocfilehash: e37b2371238211033d6a8a0847a41677b4e908a2
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688045"
---
# <a name="freelist-class"></a>freelist – třída

Spravuje seznam bloků paměti.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*'S*|Počet prvků v poli, které mají být přiděleny.|
|*Počet*|Maximální třída představující maximální počet prvků, které mají být uloženy v seznamu Free. Maximální třída může být [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md)nebo [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Poznámky

Tato šablona třídy spravuje seznam bloků paměti velikosti *SZ* s maximální délkou seznamu určeného maximální třídou předanou *Max.*

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[freelist –](#freelist)|Vytvoří objekt typu `freelist`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[výstrah](#pop)|Odebere první blok paměti ze seznamu Free.|
|[push](#push)|Přidá do seznamu blok paměti.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<allocators >

**Obor názvů:** stdext

## <a name="freelist"></a>freelist –:: freelist –

Vytvoří objekt typu `freelist`.

```cpp
freelist();
```

### <a name="remarks"></a>Poznámky

## <a name="pop"></a>freelist –::p op

Odebere první blok paměti ze seznamu Free.

```cpp
void *pop();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na blok paměti odebraný ze seznamu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu NULL, pokud je seznam prázdný. V opačném případě Odebere první blok paměti ze seznamu.

## <a name="push"></a>freelist –::p USH

Přidá do seznamu blok paměti.

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel na blok paměti, který se má přidat do bezplatného seznamu.|

### <a name="return-value"></a>Návratová hodnota

**true** , pokud funkce `full` třídy max vrátí **hodnotu false**; v opačném případě funkce `push` vrátí **hodnotu false**.

### <a name="remarks"></a>Poznámky

Pokud funkce `full` třídy max vrátí **hodnotu false**, přidá tato členská funkce blok paměti, na který odkazuje *PTR* , na záhlaví seznamu.

## <a name="see-also"></a>Viz také:

[\<allocators >](../standard-library/allocators-header.md)
