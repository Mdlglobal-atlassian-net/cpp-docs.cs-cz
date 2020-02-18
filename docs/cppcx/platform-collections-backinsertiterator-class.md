---
title: 'Platform:: Collections:: BackInsertIterator – třída'
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
ms.openlocfilehash: be5a905725c2ed0f056f1686d17d87c74b9cdc5e
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416061"
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platform:: Collections:: BackInsertIterator – třída

Představuje iterátor, který vkládá místo přepsání prvky do back-endu sekvenční kolekce.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class BackInsertIterator :
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;
```

#### <a name="parameters"></a>Parametry

*Š*<br/>
Typ položky v aktuální kolekci.

### <a name="remarks"></a>Poznámky

Třída BackInsertIterator implementuje pravidla, která vyžaduje [třída back_insert_iterator](../standard-library/back-insert-iterator-class.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[BackInsertIterator::BackInsertIterator](#ctor)|Inicializuje novou instanci třídy BackInsertIterator.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[BackInsertIterator:: operator * – operátor](#operator-dereference)|Načte odkaz na aktuální BackInsertIterator.|
|[Operátor BackInsertIterator:: operator + +](#operator-increment)|Vrátí odkaz na aktuální BackInsertIterator. Iterátor je nezměněný.|
|[BackInsertIterator:: operator = – operátor](#operator-assign)|Připojí zadaný objekt ke konci aktuální sekvenční kolekce.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BackInsertIterator`

### <a name="requirements"></a>Požadavky

**Header:** Collection. h

<a name="namespace-platformcollections"></a>**Obor názvů:** Platform:: Collections
---
## <a name="ctor"></a>BackInsertIterator:: BackInsertIterator – konstruktor

Inicializuje novou instanci třídy `BackInsertIterator`.

## <a name="syntax"></a>Syntaxe

```

explicit BackInsertIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

#### <a name="parameters"></a>Parametry

*ICES*<br/>
Objekt IVector\<T >.

### <a name="remarks"></a>Poznámky

`BackInsertIterator` vloží prvky za poslední prvek objektu určeného parametrem `v`.

## <a name="operator-assign"></a>BackInsertIterator:: operator = – operátor

Připojí zadaný objekt ke konci aktuální sekvenční kolekce.

## <a name="syntax"></a>Syntaxe

```
BackInsertIterator& operator=( const T& t);
```

#### <a name="parameters"></a>Parametry

*š*<br/>
Objekt, který se má připojit k aktuální kolekci.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální BackInsertIterator.

## <a name="operator-dereference"></a>BackInsertIterator:: operator * – operátor

Načte odkaz na aktuální BackInsertIterator.

## <a name="syntax"></a>Syntaxe

```
BackInsertIterator& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální BackInsertIterator.

### <a name="remarks"></a>Poznámky

Tento operátor vrátí odkaz na aktuální BackInsertIterator; není k žádnému prvku v aktuální kolekci.

## <a name="operator-increment"></a>Operátor BackInsertIterator:: operator + +

Vrátí odkaz na aktuální BackInsertIterator. Iterátor je nezměněný.

## <a name="syntax"></a>Syntaxe

```

BackInsertIterator& operator++();

BackInsertIterator operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální BackInsertIterator.

### <a name="remarks"></a>Poznámky

Podle návrhu první příklad syntaxe předem zvýší aktuální BackInsertIterator a druhý syntax po přírůstcích aktuální BackInsertIterator. Typ `int` ve druhé syntaxi označuje operaci po přírůstcích, nikoli skutečný celočíselný operand.

Tento operátor však ve skutečnosti nemění BackInsertIterator. Místo toho vrátí tento operátor odkaz na neupravený aktuální iterátor. Jedná se o stejné chování jako [operátor *](#operator-dereference).

## <a name="see-also"></a>Viz také

[Obor názvů platformy](platform-namespace-c-cx.md)
