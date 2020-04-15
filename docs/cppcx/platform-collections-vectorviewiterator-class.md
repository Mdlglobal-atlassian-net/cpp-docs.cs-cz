---
title: Platforma::Kolekce::Třída VectorViewIterator
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 01ae4286e996db9819cb697360f6de9c344edd21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363700"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platforma::Kolekce::Třída VectorViewIterator

Poskytuje iterátor standardní knihovny šablon pro objekty`IVectorView` odvozené z rozhraní prostředí Windows Runtime.

`ViewVectorIterator`je proxy iterátor, který ukládá `VectorProxy<T>`prvky typu . Objekt proxy je však téměř nikdy viditelné pro uživatelský kód. Další informace naleznete v [tématu Kolekce (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class VectorViewIterator;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Název typu třídy šablony VectorViewIterator.

### <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|`difference_type`|Rozdíl ukazatele (ptrdiff_t).|
|`iterator_category`|Kategorie iterátoru náhodného přístupu (::std::random_access_iterator_tag).|
|`pointer`|Ukazatel na vnitřní typ, který je vyžadován pro implementaci VectorViewIterator.|
|`reference`|Odkaz na vnitřní typ, který je vyžadován pro implementaci VectorViewIterator.|
|`value_type`|Název `T` typu.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[VektorViewIterator::VectorViewIterator](#ctor)|Inicializuje novou instanci třídy VectorViewIterator.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[VectorViewIterator::operátor- Operátor](#operator-minus)|Odečte buď zadaný počet prvků z aktuálního iterátoru, který poskytuje nový iterátor, nebo zadaný iterátor z aktuálního iterátoru, který dává počet prvků mezi iterátory.|
|[VectorViewIterator::operátor-- Operátor](#operator-decrement)|Sníží aktuální VectorViewIterator.|
|[VectorViewIterator::operátor!= Operátor](#operator-inequality)|Označuje, zda aktuální VectorViewIterator se nerovná zadanému VectorViewIterator.|
|[VectorViewIterator::operátor* Operátor](#operator-dereference)|Načte odkaz na prvek určený aktuální VectorViewIterator.|
|[VectorViewIterator::operátor\[\]](#operator-at)|Načte odkaz na prvek, který je zadaný posunutí z aktuálníHo VectorViewIterator.|
|[VectorViewIterator::operátor+ Operátor](#operator-plus)|Vrátí VectorViewIterator, který odkazuje na prvek při zadaném posunutí ze zadaného VectorViewIterator.|
|[VectorViewIterator::operátor++ Operátor](#operator-increment)|Zintáží aktuální VectorViewIterator.|
|[VectorViewIterator::operátor+= Operátor](#operator-plus-equals)|Zintáží aktuální VectorViewIterator o zadané posunutí.|
|[VectorViewIterator::operátor< Operátor](#operator-less-than)|Označuje, zda aktuální VectorViewIterator je menší než zadaný VectorViewIterator.|
|[VectorViewIterator::operátor\<= Operátor](#operator-less-than-or-equals)|Označuje, zda aktuální VectorViewIterator je menší nebo rovna zadané Mu.|
|[VectorViewIterator::operátor-= Operátor](#operator-minus-assign)|Sníží aktuální VectorViewIterator o zadané posunutí.|
|[VectorViewIterator::operator== Operátor](#operator-equality)|Označuje, zda aktuální VectorViewIterator se rovná zadané MuVectorViewIterator.|
|[VectorViewIterator::operátor> Operátor](#operator-greater-than)|Označuje, zda aktuální VectorViewIterator je větší než zadaný VectorViewIterator.|
|[VectorViewIterator::operátor-> Operátor](#operator-arrow)|Načte adresu prvku, na který odkazuje aktuální VectorViewIterator.|
|[VectorViewIterator::operátor>= Operátor](#operator-greater-than-or-equals)|Označuje, zda aktuální VectorViewIterator je větší nebo rovna zadané Mu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`VectorViewIterator`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Obor názvů:** Platforma::Kolekce

## <a name="vectorviewiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>VectorViewIterator::operátor-&gt; Operátor

Načte adresu prvku, na který odkazuje aktuální VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota prvku, který je odkazován aktuální VectorViewIterator.

Typ vrácené hodnoty je nespecifikovaný vnitřní typ, který je vyžadován pro implementaci tohoto operátoru.

## <a name="vectorviewiteratoroperator---operator"></a><a name="operator-decrement"></a>VectorViewIterator::operátor-- Operátor

Sníží aktuální VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```
VectorViewIterator& operator--();
VectorViewIterator operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

První syntaxe sníží a potom vrátí aktuální VectorViewIterator. Druhá syntaxe vrátí kopii aktuálního VectorViewIterator a pak sníží aktuální VectorViewIterator.

### <a name="remarks"></a>Poznámky

První Syntaxe VectorViewIterator pre-dekrements aktuální VectorViewIterator.

Druhá syntaxe post-dekrements aktuální VectorViewIterator. Typ `int` v druhé syntaxi označuje operaci po snížení, nikoli skutečný celočíselný operand.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-dereference"></a>VectorViewIterator::Operátor\* operátora

Načte odkaz na prvek určený aktuální VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```
reference operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Prvek určený aktuální VectorViewIterator.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-equality"></a>VectorViewIterator::operator== Operátor

Označuje, zda aktuální VectorViewIterator se rovná zadané MuVectorViewIterator.

### <a name="syntax"></a>Syntaxe

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další VectorViewIterator.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `VectorViewIterator` je proud roven *ostatním*; jinak **false**.

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>VectorViewIterator::Operátor&gt; operátora

Označuje, zda aktuální VectorViewIterator je větší než zadaný VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další VectorViewIterator.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud aktuální VectorViewIterator je větší než *ostatní*; jinak **false**.

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorViewIterator::operátor&gt;= Operátor

Označuje, zda `VectorViewIterator` je proud větší nebo `VectorViewIterator`roven zadanému .

### <a name="syntax"></a>Syntaxe

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další VectorViewIterator.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `VectorViewIterator` je proud větší nebo roven *ostatním*; jinak **false**.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-increment"></a>VectorViewIterator::operátor++ Operátor

Zintáží aktuální VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```

VectorViewIterator& operator++();
VectorViewIterator operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První syntaxe přírůstky a potom vrátí aktuální VectorViewIterator. Druhá syntaxe vrátí kopii aktuálního VectorViewIterator a potom se zpříne aktuální VectorViewIterator.

### <a name="remarks"></a>Poznámky

První Syntaxe VectorViewIterator pre-přírůstky aktuální VectorViewIterator.

Druhá syntaxe post-přírůstky aktuální VectorViewIterator. Typ `int` v druhé syntaxi označuje operaci po přírůstku, nikoli skutečný celočíselný operand.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-inequality"></a>VectorViewIterator::operátor!= Operátor

Označuje, zda aktuální VectorViewIterator se nerovná zadanému VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další VectorViewIterator.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `VectorViewIterator` se proud nerovná *ostatním*; jinak **false**.

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than"></a>VectorViewIterator::Operátor&lt; operátora

Označuje, zda aktuální VectorIterator je menší než zadaný VectorIterator.

### <a name="syntax"></a>Syntaxe

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další `VectorIterator`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `VectorIterator` je proud menší než *jiný*; jinak **false**.

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorViewIterator::operátor&lt;= Operátor

Označuje, zda `VectorIterator` je proud menší nebo `VectorIterator`roven zadanému .

### <a name="syntax"></a>Syntaxe

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Další `VectorIterator`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `VectorIterator` je proud menší nebo roven *ostatním*; jinak **false**.

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus"></a>VectorViewIterator::operátor- Operátor

Odečte buď zadaný počet prvků z aktuálního iterátoru, který poskytuje nový iterátor, nebo zadaný iterátor z aktuálního iterátoru, který dává počet prvků mezi iterátory.

### <a name="syntax"></a>Syntaxe

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*N*<br/>
Počet prvků.

*Další*<br/>
Další VectorViewIterator.

### <a name="return-value"></a>Návratová hodnota

První operátor syntaxe vrátí VectorViewIterator `n` objekt, který je prvky menší než aktuální VectorViewIterator. Druhá syntaxe operátoru vrátí počet prvků `other` mezi aktuální a VectorViewIterator.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus-equals"></a>VectorViewIterator::operátor+= Operátor

Zintáží aktuální VectorViewIterator o zadané posunutí.

### <a name="syntax"></a>Syntaxe

```
VectorViewIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parametry

*N*<br/>
Celé číslo posunutí.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný VectorViewIterator.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus"></a>VectorViewIterator::operátor+ Operátor

Vrátí VectorViewIterator, který odkazuje na prvek při zadaném posunutí ze zadaného VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```

VectorViewIterator operator+(difference_type n) const;

template <typename T>
inline VectorViewIterator<T> operator+
   (ptrdiff_t n,
   const VectorViewIterator<T>& i);
```

### <a name="parameters"></a>Parametry

*T*<br/>
V druhé syntaxi název typu VectorViewIterator.

*N*<br/>
Celé číslo posunutí.

*I*<br/>
V druhé syntaxi VectorViewIterator.

### <a name="return-value"></a>Návratová hodnota

V první syntaxi VectorViewIterator, který odkazuje na prvek na zadané posunutí z aktuálního VectorViewIterator.

V druhé syntaxi VectorViewIterator, který odkazuje na prvek na zadané `i`posunutí od začátku parametru .

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus-assign"></a>VectorViewIterator::operátor-= Operátor

Sníží aktuální VektorIterátor o zadané posunutí.

### <a name="syntax"></a>Syntaxe

```
VectorViewIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parametry

*N*<br/>
Celé číslo posunutí.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný VectorIterator.

## <a name="vectorviewiteratoroperator"></a><a name="operator-at"></a>VectorViewIterator::operátor\[\]

Načte odkaz na prvek, který je zadaný posunutí z aktuálníHo VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parametry

*N*<br/>
Celé číslo posunutí.

### <a name="return-value"></a>Návratová hodnota

Prvek, který je `n` posunuty prvky z aktuálního VectorViewIterator.

## <a name="vectorviewiteratorvectorviewiterator-constructor"></a><a name="ctor"></a>VectorViewIterator::Konstruktor VectorViewIterátor

Inicializuje novou instanci třídy VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```

VectorViewIterator();

explicit VectorViewIterator(
   Windows::Foundation::Collections::IVectorView<T>^ v
);
```

### <a name="parameters"></a>Parametry

*V*<br/>
Objekt>\<IVectorView T.

### <a name="remarks"></a>Poznámky

První syntaktický příklad je výchozí konstruktor. Druhý syntaktický příklad je explicitní konstruktor, který se používá k vytvoření\<VectorViewIterator z> objektu IVectorView T.

## <a name="see-also"></a>Viz také

[Obor názvů platformy](platform-namespace-c-cx.md)
