---
title: Platforma::Kolekce::BackInsertIterator Class
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
ms.openlocfilehash: fcb680c8f43a50801d081762bb5b546cb110c52d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354774"
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platforma::Kolekce::BackInsertIterator Class

Představuje iterátor, který vloží, nikoli přepíše, prvky do zadní části sekvenční kolekce.

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

BackInsertIterator třída implementuje pravidla vyžadovaná [back_insert_iterator Class](../standard-library/back-insert-iterator-class.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[BackInsertIterator::BackInsertIterator](#ctor)|Inicializuje novou instanci třídy BackInsertIterator.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[BackInsertIterator::operátor* Operátor](#operator-dereference)|Načte odkaz na aktuální BackInsertIterator.|
|[BackInsertIterator::operátor++ Operátor](#operator-increment)|Vrátí odkaz na aktuální BackInsertIterator. Iterátor je nezměněn.|
|[BackInsertIterator::operátor= Operátor](#operator-assign)|Připojí zadaný objekt na konec aktuální sekvenční kolekce.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BackInsertIterator`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Obor názvů:** Platforma::Kolekce

## <a name="backinsertiteratorbackinsertiterator-constructor"></a><a name="ctor"></a>BackInsertIterator::Konstruktor BackInsertIterator

Inicializuje novou instanci třídy. `BackInsertIterator`

## <a name="syntax"></a>Syntaxe

```
explicit BackInsertIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

#### <a name="parameters"></a>Parametry

*V*<br/>
Objekt>\<IVector T.

### <a name="remarks"></a>Poznámky

A `BackInsertIterator` vloží prvky za poslední prvek objektu určeného parametrem `v`.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-assign"></a>BackInsertIterator::operátor= Operátor

Připojí zadaný objekt na konec aktuální sekvenční kolekce.

## <a name="syntax"></a>Syntaxe

```
BackInsertIterator& operator=( const T& t);
```

#### <a name="parameters"></a>Parametry

*t*<br/>
Objekt připojit k aktuální kolekci.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální BackInsertIterator.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-dereference"></a>BackInsertIterator::operátor* Operátor

Načte odkaz na aktuální BackInsertIterator.

## <a name="syntax"></a>Syntaxe

```
BackInsertIterator& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální BackInsertIterator.

### <a name="remarks"></a>Poznámky

Tento operátor vrátí odkaz na aktuální BackInsertIterator; není žádný prvek v aktuální kolekci.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-increment"></a>BackInsertIterator::operátor++ Operátor

Vrátí odkaz na aktuální BackInsertIterator. Iterátor je nezměněn.

## <a name="syntax"></a>Syntaxe

```
BackInsertIterator& operator++();

BackInsertIterator operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální BackInsertIterator.

### <a name="remarks"></a>Poznámky

Podle návrhu první syntaktický příklad předčí aktuální BackInsertIterator a druhá syntaxe post-přírůstky aktuální BackInsertIterator. Typ `int` v druhé syntaxi označuje operaci po přírůstku, nikoli skutečný celočíselný operand.

Tento operátor však ve skutečnosti nezmění BackInsertIterator. Místo toho tento operátor vrátí odkaz na nezměněné, aktuální iterátor. Toto je stejné chování jako [operátor*](#operator-dereference).

## <a name="see-also"></a>Viz také

[Obor názvů platformy](platform-namespace-c-cx.md)
