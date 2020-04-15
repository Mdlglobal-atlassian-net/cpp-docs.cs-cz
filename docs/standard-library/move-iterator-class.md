---
title: move_iterator – třída
ms.date: 03/27/2019
f1_keywords:
- iterator/std::move_iterator
- iterator/std::move_iterator::iterator_type
- iterator/std::move_iterator::iterator_category
- iterator/std::move_iterator::value_type
- iterator/std::move_iterator::difference_type
- iterator/std::move_iterator::pointer
- iterator/std::move_iterator::reference
- iterator/std::move_iterator::base
helpviewer_keywords:
- std::move_iterator [C++]
- std::move_iterator [C++], iterator_type
- std::move_iterator [C++], iterator_category
- std::move_iterator [C++], value_type
- std::move_iterator [C++], difference_type
- std::move_iterator [C++], pointer
- std::move_iterator [C++], reference
- std::move_iterator [C++], base
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
ms.openlocfilehash: 17af246a85c4e3f1e0c7eb9d387161ad7b5123a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377411"
---
# <a name="move_iterator-class"></a>move_iterator – třída

Šablona `move_iterator` třídy je obálka pro iterátor. Iterátor move_iterator poskytuje stejné chování jako iterátor, kterého zabalí (uloží). Výjimkou je, že operátor přesměrování uloženého iterátoru mění na odkaz hodnoty rvalue a kopírování se tak mění na přesunutí. Další informace o rvalues naleznete v tématu [Rvalue Reference Declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="syntax"></a>Syntaxe

```cpp
class move_iterator;
```

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který se chová jako iterátor, s výjimkou případů, kdy je odkazováno. Ukládá random-access iterátor typu `Iterator`, přístup prostřednictvím členské `base()`funkce . Všechny operace `move_iterator` na a jsou prováděny přímo na uložené iterátoru, s tím rozdílem, že výsledek `operator*` je implicitně `value_type&&` přetypován, aby se odkazovat na rvalue.

A `move_iterator` může být schopen operací, které nejsou definovány zabalené iterátoru. Tyto operace by neměly být použity.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[move_iterator](#move_iterator)|Konstruktor pro objekty `move_iterator`typu .|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[iterator_type](#iterator_type)|Synonymum pro `RandomIterator`parametr šablony .|
|[iterator_category](#iterator_category)|Synonymum pro výraz delší **název** typu `iterator_category` se stejným názvem identifikuje obecné schopnosti iterátoru.|
|[value_type](#value_type)|Synonymum pro výraz delší **název** typu `value_type` se stejným názvem, popisuje, jaký typ iterátoru prvky jsou.|
|[difference_type](#difference_type)|Synonymum pro výraz delší **název** typu `difference_type` se stejným názvem, popisuje integrální typ potřebný k vyjádření rozdílové hodnoty mezi prvky.|
|[ukazatel](#pointer)|Synonymum pro `RandomIterator`parametr šablony .|
|[Odkaz](#reference)|Synonymum `rvalue` pro `value_type&&`odkaz .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[base](#base)|Členská funkce vrátí uložený iterátor `move_iterator`zabalený tímto .|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[move_iterator::operátor*](#op_star)|Vrátí`(reference)*base().`|
|[move_iterator::operátor++](#op_add_add)|Zvýší uložený iterátor. Přesné chování závisí na tom, zda se jedná o operaci před přírůstkem nebo po přírůstku.|
|[move_iterator::operátor--](#operator--)|Sníží uložený iterátor. Přesné chování závisí na tom, zda se jedná o operaci před snížením nebo po snížení.|
|[move_iterator::operátor-&gt;](#op_arrow)|Vrací objekt `&**this`.|
|[move_iterator::operátor-](#operator-)|Vrátí `move_iterator(*this) -=` nejprve odečtením pravé hodnoty od aktuální pozice.|
|[move_iterator::operátor[]](#op_at)|Vrací objekt `(reference)*(*this + off)`. Umožňuje určit posun od aktuálního základu k získání hodnoty v tomto umístění.|
|[move_iterator::operátor+](#op_add)|Vrátí `move_iterator(*this) +=` hodnotu. Umožňuje přidat posun k základu k získání hodnoty v tomto umístění.|
|[move_iterator::operátor+=](#op_add_eq)|Přidá hodnotu vpravo do uloženého iterátoru a vrátí `*this`.|
|[move_iterator::operátor-=](#operator-_eq)|Odečte pravostrannou hodnotu od uloženého iterátoru a vrátí `*this`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> iterátoru

**Obor názvů:** std

## <a name="move_iteratorbase"></a><a name="base"></a>move_iterator::základna

Vrátí uložený iterátor `move_iterator`pro tento .

```cpp
RandomIterator base() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uložený iterátor.

## <a name="move_iteratordifference_type"></a><a name="difference_type"></a>move_iterator::difference_type

Typ `difference_type` je `move_iterator` `typedef` založen na vlastnosti `difference_type`iterátoru a může být s ním zaměnitelně použit.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro iterátor `typename iterator_traits<RandomIterator>::pointer`znak .

## <a name="move_iteratoriterator_category"></a><a name="iterator_category"></a>move_iterator::iterator_category

Typ `iterator_category` je `move_iterator` `typedef` založen na vlastnosti `iterator_category`iterátoru a může být s ním zaměnitelně použit.

```cpp
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro iterátor `typename iterator_traits<RandomIterator>::iterator_category`znak .

## <a name="move_iteratoriterator_type"></a><a name="iterator_type"></a>move_iterator::iterator_type

Typ `iterator_type` je založen na `RandomIterator` parametru šablony `move_iterator`šablony třídy a lze jej použít zaměnitelně na jeho místě.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `RandomIterator`parametr šablony .

## <a name="move_iteratormove_iterator"></a><a name="move_iterator"></a>move_iterator::move_iterator

Vytvoří iterátor move. Použije parametr jako uložený iterátor.

```cpp
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Iterátor použít jako uložený iterátor.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje uložený iterátor s jeho výchozí konstruktor. Zbývající konstruktory inicializovat uložené iterátor `base.base()`s .

## <a name="move_iteratoroperator"></a><a name="op_add_eq"></a>move_iterator::operátor+=

Přidá posun do uloženého iterátoru tak, aby uložený iterátor odkazuje na prvek v novém aktuálním umístění. Operátor pak přesune nový aktuální prvek.

```cpp
move_iterator& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun, který chcete přidat k aktuální pozici k určení nové aktuální pozice.

### <a name="return-value"></a>Návratová hodnota

Vrátí nový aktuální prvek.

### <a name="remarks"></a>Poznámky

Operátor přidává *_Off* do uloženého iterátoru. Pak `*this`vrátí .

## <a name="move_iteratoroperator-"></a><a name="operator-_eq"></a>move_iterator::operátor-=

Přesune přes zadaný počet předchozích prvků. Tento operátor odečte posun od uloženého iterátoru.

```cpp
move_iterator& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

Operátor vyhodnotí `*this += -_Off`. Pak `*this`vrátí .

## <a name="move_iteratoroperator"></a><a name="op_add_add"></a>move_iterator::operátor++

Přírůstky uložené iterátor, který patří `move_iterator.` k tomuto Aktuální prvek je přístupný operátor postincrement. K dalšímu prvku přistupuje operátor preincrement.

```cpp
move_iterator& operator++();
move_iterator operator++(int);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

První (preincrement) operátor zinkrí uložené iterátor. Pak `*this`vrátí .

Druhý operátor (postincrement) vytvoří `*this`kopii `++*this`, vyhodnotí . Potom vrátí kopii.

## <a name="move_iteratoroperator"></a><a name="op_add"></a>move_iterator::operátor+

Vrátí pozici iterátoru upřesňující libovolný počet prvků.

```cpp
move_iterator operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

Operátor vrátí `move_iterator(*this) +=` `_Off`.

## <a name="move_iteratoroperator"></a><a name="op_at"></a>move_iterator::operátor[]

Umožňuje přístup k prvkům indexu `move iterator`pole v rozsahu rozhraní .

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

Operátor vrátí `(reference)*(*this + _Off)`.

## <a name="move_iteratoroperator--"></a><a name="operator--"></a>move_iterator::operátor--

Pre- a postdecrement členské operátory provést snížení na uložené iterátoru.

```cpp
move_iterator& operator--();
move_iterator operator--();
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

První operátor člena (predecrement) sníží uložené iterátor. Pak `*this`vrátí .

Druhý operátor (postdecrement) vytvoří `*this`kopii `--*this`, vyhodnotí . Potom vrátí kopii.

## <a name="move_iteratoroperator-"></a><a name="operator-"></a>move_iterator::operátor-

Sníží uložených iterátora a vrátí uvedenou hodnotu.

```cpp
move_iterator operator-(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

Operátor vrátí `move_iterator(*this) -= _Off`.

## <a name="move_iteratoroperator"></a><a name="op_star"></a>move_iterator::operátor*

Dereferences uložené iterátor a vrátí hodnotu. To se chová `rvalue reference` jako a provádí přiřazení přesunutí. Operátor převede aktuální prvek ze základního iterátoru. Následující prvek se stane novým aktuálním prvkem.

```cpp
reference operator*() const;
```

### <a name="remarks"></a>Poznámky

Operátor vrátí `(reference)*base()`.

## <a name="move_iteratoroperator-gt"></a><a name="op_arrow"></a>move_iterator::operátor-&gt;

Jako normální `RandomIterator` `operator->`, poskytuje přístup k polím, která patří k aktuálnímu prvku.

```cpp
pointer operator->() const;
```

### <a name="remarks"></a>Poznámky

Operátor vrátí `&**this`.

## <a name="move_iteratorpointer"></a><a name="pointer"></a>move_iterator::pointer

Typ `pointer` je **typedef** na základě náhodného `RandomIterator` iterátoru pro `move_iterator`, a lze jej zaměnit.

```cpp
typedef RandomIterator  pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `RandomIterator`pro .

## <a name="move_iteratorreference"></a><a name="reference"></a>move_iterator::odkaz

Typ `reference` je **typedef** založené `value_type&&` `move_iterator`na for , a lze `value_type&&`použít zaměnitelně s .

```cpp
typedef value_type&& reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `value_type&&`, což je odkaz rvalue.

## <a name="move_iteratorvalue_type"></a><a name="value_type"></a>move_iterator::value_type

Typ `value_type` je `move_iterator` `typedef` založen na vlastnosti `value_type`iterátoru a může být s ním zaměnitelně použit.

```cpp
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro iterátor `typename iterator_traits<RandomIterator>::value_type`znak .

## <a name="see-also"></a>Viz také

[\<>iterátoru](../standard-library/iterator.md)\
[Lhodnoty a Hodnoty R](../cpp/lvalues-and-rvalues-visual-cpp.md)\
[Přesunout konstruktory a přesunout operátory přiřazení (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
