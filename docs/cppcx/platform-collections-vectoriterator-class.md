---
title: Platform::Collections::VectorIterator – třída
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
ms.openlocfilehash: e649027c2ba3f637c42765af691f4d321913fb28
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354370"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator – třída

Poskytuje iterátor standardní knihovny šablon pro objekty odvozené z rozhraní IVector prostředí Windows Runtime.

VectorIterator je proxy iterátor, který ukládá\<prvky typu VectorProxy T>. Objekt proxy je však téměř nikdy viditelné pro uživatelský kód. Další informace naleznete v [tématu Kolekce (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class VectorIterator;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Název typu třídy šablony VectorIterator.

### <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|`difference_type`|Rozdíl ukazatele (ptrdiff_t).|
|`iterator_category`|Kategorie iterátoru náhodného přístupu (::std::random_access_iterator_tag).|
|`pointer`|Ukazatel na vnitřní typ, Platform::Collections::Details::VectorProxy\<T>, který je vyžadován pro implementaci VectorIterator.|
|`reference`|Odkaz na vnitřní typ, Platform::Collections::Details::VectorProxy\<T>,, který je vyžadován pro implementaci VectorIterator.|
|`value_type`|Název `T` typu.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[VektorIterátor::VectorIterator](#ctor)|Inicializuje novou instanci třídy VectorIterator.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[VectorIterator::operátor- Operátor](#operator-minus)|Odečte buď zadaný počet prvků z aktuálního iterátoru, který poskytuje nový iterátor, nebo zadaný iterátor z aktuálního iterátoru, který dává počet prvků mezi iterátory.|
|[VectorIterator::operátor-- Operátor](#operator-decrement)|Sníží aktuální VectorIterator.|
|[VectorIterator::operátor!= Operátor](#operator-inequality)|Označuje, zda aktuální VectorIterator není rovna zadané Mu.|
|[VectorIterator::operátor* Operátor](#operator-dereference)|Načte odkaz na prvek určený aktuálním VectorIterator.|
|[VectorIterator::operátor\[\]](#operator-at)|Načte odkaz na prvek, který je zadaný posunutí z aktuálníVectorIterator.|
|[VectorIterator::operátor+ Operátor](#operator-plus)|Vrátí funkce VectorIterator, která odkazuje na prvek při zadaném posunutí ze zadaného vektorového posunutí.|
|[VectorIterator::operátor++ Operátor](#operator-increment)|Zintáží aktuální VectorIterator.|
|[VectorIterator::operátor+= Operátor](#operator-plus-assign)|Zintáží aktuální VectorIterator o zadané posunutí.|
|[VectorIterator::operátor< Operátor](#operator-less-than)|Označuje, zda aktuální VectorIterator je menší než zadaný VectorIterator.|
|[VectorIterator::operátor\<= Operátor](#operator-less-than-or-equals)|Označuje, zda je aktuální VektorIterátor menší nebo roven zadanému vektorátoru.|
|[VectorIterator::operátor-= Operátor](#operator-minus-equals)|Sníží aktuální VektorIterátor o zadané posunutí.|
|[VectorIterator::operátor== Operátor](#operator-equality)|Označuje, zda je aktuální VectorIterator rovna zadanému VectorIterator.|
|[VectorIterator::operátor> Operátor](#operator-greater-than)|Označuje, zda je aktuální VektorIterátor větší než zadaný VectorIterator.|
|[VectorIterator::operátor-> Operátor](#operator-arrow)|Načte adresu prvku, na který odkazuje aktuální VectorIterator.|
|[VectorIterator::operátor>= Operátor](#operator-greater-than-or-equals)|Označuje, zda je aktuální VektorIterátor větší nebo roven zadanému vektorovému toku.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`VectorIterator`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Obor názvů:** Platforma::Kolekce

## <a name="vectoriteratoroperator-gt-operator"></a><a name="operator-arrow"></a>VectorIterator::operátor-&gt; Operátor

Načte adresu prvku, na který odkazuje aktuální VectorIterator.

### <a name="syntax"></a>Syntaxe

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota prvku, na který odkazuje aktuální VectorIterator.

Typ vrácené hodnoty je nespecifikovaný vnitřní typ, který je vyžadován pro implementaci tohoto operátoru.

## <a name="vectoriteratoroperator---operator"></a><a name="operator-decrement"></a>VectorIterator::operátor-- Operátor

Sníží aktuální VectorIterator.

### <a name="syntax"></a>Syntaxe

```

VectorIterator& operator--();
VectorIterator operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

První syntaxe sníží a potom vrátí aktuální VectorIterator. Druhá syntaxe vrátí kopii aktuálního VectorIterator a pak sníží aktuální VectorIterator.

### <a name="remarks"></a>Poznámky

První syntaxe VectorIterator předem sníží aktuální VectorIterator.

Druhá syntaxe post-dekrements aktuální VectorIterator. Typ `int` v druhé syntaxi označuje operaci po snížení, nikoli skutečný celočíselný operand.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-dereference"></a>VectorIterator::Operátor\* operátora

Načte adresu prvku určeného aktuálním VectorIterator.

### <a name="syntax"></a>Syntaxe

```
reference operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Prvek určený aktuální VectorIterator.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-equality"></a>VectorIterator::operátor== Operátor

Označuje, zda je aktuální VectorIterator rovna zadanému VectorIterator.

### <a name="syntax"></a>Syntaxe

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další VectorIterator.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je aktuální VectorIterator roven *ostatním*; jinak **false**.

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>VectorIterator::Operátor&gt; operátora

Označuje, zda je aktuální VektorIterátor větší než zadaný VectorIterator.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další VectorIterator.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je aktuální VectorIterator větší než *jiný*; jinak **false**.

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorIterator::operátor&gt;= Operátor

Označuje, zda je aktuální VektorIterátor větší nebo roven zadanému VectorIterator.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další VectorIterator.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je aktuální VectorIterator větší nebo roven *ostatním*; jinak **false**.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-increment"></a>VectorIterator::operátor++ Operátor

Zintáží aktuální VectorIterator.

### <a name="syntax"></a>Syntaxe

```
VectorIterator& operator++();
VectorIterator operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První syntaxe se zpříby a potom vrátí aktuální VectorIterator. Druhá syntaxe vrátí kopii aktuálního VectorIterator a potom se zpříne aktuální VectorIterator.

### <a name="remarks"></a>Poznámky

První Syntaxe VectorIterator pre-přírůstky aktuální VectorIterator.

Druhá syntaxe post-přírůstky aktuální VectorIterator. Typ `int` v druhé syntaxi označuje operaci po přírůstku, nikoli skutečný celočíselný operand.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-inequality"></a>VectorIterator::operátor!= Operátor

Označuje, zda aktuální VectorIterator není rovna zadané Mu.

### <a name="syntax"></a>Syntaxe

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další VectorIterator.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud aktuální VectorIterator není rovna *jiné*; jinak **false**.

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than"></a>VectorIterator::Operátor&lt; operátora

Označuje, zda aktuální VectorIterator je menší než zadaný VectorIterator.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další VectorIterator.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je aktuální VectorIterator menší než *jiný*; jinak **false**.

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorIterator::operátor&lt;= Operátor

Označuje, zda je aktuální VektorIterátor menší nebo roven zadanému vektorátoru.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další VectorIterator.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je aktuální VectorIterator menší nebo roven *ostatním*; jinak **false**.

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus"></a>VectorIterator::operátor- Operátor

Odečte buď zadaný počet prvků z aktuálního iterátoru, který poskytuje nový iterátor, nebo zadaný iterátor z aktuálního iterátoru, který dává počet prvků mezi iterátory.

### <a name="syntax"></a>Syntaxe

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parametry

*N*<br/>
Počet prvků.

*Další*<br/>
Další VectorIterator.

### <a name="return-value"></a>Návratová hodnota

První operátor syntaxe vrátí VectorIterator `n` objekt, který je prvky menší než aktuální VectorIterator. Druhá syntaxe operátoru vrátí počet prvků `other` mezi aktuální a VectorIterator.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus-assign"></a>VectorIterator::operátor+= Operátor

Zintáží aktuální VectorIterator o zadané posunutí.

### <a name="syntax"></a>Syntaxe

```
VectorIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parametry

*N*<br/>
Celé číslo posunutí.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný VectorIterator.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus"></a>VectorIterator::operátor+ Operátor

Vrátí funkce VectorIterator, která odkazuje na prvek při zadaném posunutí ze zadaného vektorového posunutí.

### <a name="syntax"></a>Syntaxe

```

VectorIterator operator+(difference_type n);

template <typename T>
inline VectorIterator<T> operator+(
  ptrdiff_t n,
  const VectorIterator<T>& i);
```

### <a name="parameters"></a>Parametry

*T*<br/>
V druhé syntaxi název typu VectorIterator.

*N*<br/>
Celé číslo posunutí.

*I*<br/>
Ve druhé syntaxi VectorIterator.

### <a name="return-value"></a>Návratová hodnota

V první syntaxi VectorIterator, který odkazuje na prvek při zadaném posunutí z aktuálního VectorIterator.

Ve druhé syntaxi VectorIterator, který odkazuje na prvek na zadané `i`posunutí od začátku parametru .

### <a name="remarks"></a>Poznámky

První příklad syntaxe

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus-equals"></a>VectorIterator::operátor-= Operátor

Sníží aktuální VektorIterátor o zadané posunutí.

### <a name="syntax"></a>Syntaxe

```
VectorIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parametry

*N*<br/>
Celé číslo posunutí.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný VectorIterator.

## <a name="vectoriteratoroperator"></a><a name="operator-at"></a>VectorIterator::operátor\[\]

Načte odkaz na prvek, který je zadaný posunutí z aktuálníVectorIterator.

### <a name="syntax"></a>Syntaxe

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parametry

*N*<br/>
Celé číslo posunutí.

### <a name="return-value"></a>Návratová hodnota

Prvek, který je `n` posunuty prvky z aktuálního VectorIterator.

## <a name="vectoriteratorvectoriterator-constructor"></a><a name="ctor"></a>Vektoriterátor::Konstruktor vektorového ivátoru

Inicializuje novou instanci třídy VectorIterator.

### <a name="syntax"></a>Syntaxe

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>Parametry

*V*<br/>
Objekt>\<IVector T.

### <a name="remarks"></a>Poznámky

První syntaktický příklad je výchozí konstruktor. Druhý syntaktický příklad je explicitní konstruktor, který se používá k\<vytvoření VectorIterator z objektu IVector T>.

## <a name="see-also"></a>Viz také

[Obor názvů platformy](platform-namespace-c-cx.md)
