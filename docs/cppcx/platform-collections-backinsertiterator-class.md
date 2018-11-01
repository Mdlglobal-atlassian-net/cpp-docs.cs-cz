---
title: 'Platform::Collections:: backinsertiterator – třída'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
ms.openlocfilehash: 33397ed7061f14d9aeb9c8b5c3d561865ad91cad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638084"
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platform::Collections:: backinsertiterator – třída

Představuje iterátor, který vloží, spíše než přepíše, prvky do zadní části sekvenční kolekcí.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class BackInsertIterator :
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ položky v aktuální kolekci.

### <a name="remarks"></a>Poznámky

Třída BackInsertIterator implementuje pravidla vyžadované [back_insert_iterator – třída](../standard-library/back-insert-iterator-class.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[BackInsertIterator::BackInsertIterator](#ctor)|Inicializuje novou instanci třídy BackInsertIterator.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[BackInsertIterator::operator * – operátor](#operator-dereference)|Získá odkaz na aktuální BackInsertIterator.|
|[BackInsertIterator::operator++ Operator](#operator-increment)|Vrátí odkaz na aktuální BackInsertIterator. Iterátor zůstává nezměněna.|
|[BackInsertIterator::operator= Operator](#operator-assign)|Připojí zadaný objekt na konec aktuální sekvenční kolekcí.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BackInsertIterator`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platform::Collections –

---
## <a name="ctor"></a>  BackInsertIterator::BackInsertIterator konstruktor

Inicializuje novou instanci třídy `BackInsertIterator` třídy.

## <a name="syntax"></a>Syntaxe

```

explicit BackInsertIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

#### <a name="parameters"></a>Parametry

*v*<br/>
IVector\<T > objektu.

### <a name="remarks"></a>Poznámky

A `BackInsertIterator` vloží prvky za poslední prvek objektu určeného parametrem `v`.

## <a name="operator-assign"></a>  BackInsertIterator::operator = – operátor

Připojí zadaný objekt na konec aktuální sekvenční kolekcí.

## <a name="syntax"></a>Syntaxe

```
BackInsertIterator& operator=( const T& t);
```

#### <a name="parameters"></a>Parametry

*t*<br/>
Objekt, který chcete připojit s aktuální kolekcí.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální BackInsertIterator.

## <a name="operator-dereference"></a>  BackInsertIterator::operator * – operátor

Získá odkaz na aktuální BackInsertIterator.

## <a name="syntax"></a>Syntaxe

```
BackInsertIterator& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální BackInsertIterator.

### <a name="remarks"></a>Poznámky

Tento operátor vrátí odkaz na aktuální BackInsertIterator; není k libovolnému prvku v aktuální kolekci.

## <a name="operator-increment"></a>  BackInsertIterator::operator ++ – operátor

Vrátí odkaz na aktuální BackInsertIterator. Iterátor zůstává nezměněna.

## <a name="syntax"></a>Syntaxe

```

BackInsertIterator& operator++();

BackInsertIterator operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální BackInsertIterator.

### <a name="remarks"></a>Poznámky

Návrh první příklad syntaxe předem zvýší aktuální BackInsertIterator a druhá syntaxe po zvětší aktuální BackInsertIterator. `int` v druhé syntaxi označuje operaci po přírůstku není skutečný celočíselný operand.

Ale tento operátor neprovede žádné změny ve skutečnosti BackInsertIterator. Místo toho tento operátor vrátí odkaz na iterátor bez úprav, aktuální. Jedná se o stejné chování jako [operátor *](#dereference-operator).

## <a name="see-also"></a>Viz také

[Platforma Namespace](platform-namespace-c-cx.md)