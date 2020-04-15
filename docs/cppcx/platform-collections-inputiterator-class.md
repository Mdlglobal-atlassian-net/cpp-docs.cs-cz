---
title: Platform::Collections::InputIterator – třída
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
ms.openlocfilehash: 92f9b15f474a5aa3d063f0ccfb663f56baf8de31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354564"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator – třída

Poskytuje vstupní informační službu standardní šablony pro kolekce odvozené z prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename X>
class InputIterator;
```

#### <a name="parameters"></a>Parametry

*×*<br/>
Název typu inputiterator šablony třídy.

### <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|`difference_type`|Rozdíl ukazatele (ptrdiff_t).|
|`iterator_category`|Kategorie vstupního iterátoru (::std::input_iterator_tag).|
|`pointer`|Ukazatel na`const X`|
|`reference`|Odkaz na`const X`|
|`value_type`|Název `X` typu.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[InputIterator::Vstupníiterátor](#ctor)|Inicializuje novou instanci inputiterator třídy.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[Vstupní Iterátor::operátor!= Operátor](#operator-inequality)|Označuje, zda aktuální InputIterator není rovna zadané InputIterator.|
|[Vstupní Iterátor::operátor* Operátor](#operator-dereference)|Načte odkaz na prvek určený aktuálníinputIterator.|
|[Vstupní Iterátor::operátor++ Operátor](#operator-increment)|Zintáží aktuální InputIterator.|
|[VstupníIterátor::operátor== Operátor](#operator-equality)|Označuje, zda aktuální InputIterator se rovná zadané InputIterator.|
|[InputIterator::operátor-> Operátor](#operator-arrow)|Načte adresu prvku odkazuje aktuální InputIterator.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`InputIterator`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Obor názvů:** Platforma::Kolekce

## <a name="inputiteratorinputiterator-constructor"></a><a name="ctor"></a>InputIterator::Konstruktor vstupního iviterátoru

Inicializuje novou instanci inputiterator třídy.

### <a name="syntax"></a>Syntaxe

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iterator);
```

### <a name="parameters"></a>Parametry

*Iterace*<br/>
Objekt iterátoru.

## <a name="inputiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>VstupIterátor::operátor-&gt; Operátor

Načte adresu prvku určeného aktuálníinputIterator.

### <a name="syntax"></a>Syntaxe

```
pointer operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa prvku určeného aktuální inputiterator.

## <a name="inputiteratoroperator-operator"></a><a name="operator-dereference"></a>Vstupní Iterátor::operátor\* operátor

Načte odkaz na prvek určený aktuálníinputIterator.

### <a name="syntax"></a>Syntaxe

```
reference operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Prvek určený aktuální InputIterator.

## <a name="inputiteratoroperator-operator"></a><a name="operator-equality"></a>VstupníIterátor::operátor== Operátor

Označuje, zda aktuální InputIterator se rovná zadané InputIterator.

### <a name="syntax"></a>Syntaxe

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další vstupní iterátor.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je aktuální VstupníIterátor roven *ostatním*; jinak **false**.

## <a name="inputiteratoroperator-operator"></a><a name="operator-increment"></a>Vstupní Iterátor::operátor++ Operátor

Zintáží aktuální InputIterator.

### <a name="syntax"></a>Syntaxe

```
InputIterator& operator++();
InputIterator operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První syntaxe přírůstky a potom vrátí aktuální InputIterator. Druhá syntaxe vrátí kopii aktuálnívstupní InIterator a potom increments aktuální InputIterator.

### <a name="remarks"></a>Poznámky

První InputIterator syntaxe pre-přírůstky aktuální InputIterator.

Druhá syntaxe post-přírůstky aktuální InputIterator. Typ `int` v druhé syntaxi označuje operaci po přírůstku, nikoli skutečný celočíselný operand.

## <a name="inputiteratoroperator-operator"></a><a name="operator-inequality"></a>Vstupní Iterátor::operátor!= Operátor

Označuje, zda aktuální InputIterator není rovna zadané InputIterator.

### <a name="syntax"></a>Syntaxe

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další vstupní iterátor.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud se aktuální vstupní iterátor nerovná *ostatním*; jinak **false**.

## <a name="see-also"></a>Viz také

[Obor názvů platformy](platform-namespace-c-cx.md)
