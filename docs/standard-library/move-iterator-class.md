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
ms.openlocfilehash: 3e2e62946325c082e761b6997ae584419175f8fe
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565042"
---
# <a name="moveiterator-class"></a>move_iterator – třída

Šablona třídy `move_iterator` je obálkou iterátoru. Iterátor move_iterator poskytuje stejné chování jako iterátor, kterého zabalí (uloží). Výjimkou je, že operátor přesměrování uloženého iterátoru mění na odkaz hodnoty rvalue a kopírování se tak mění na přesunutí. Další informace o hodnotách rvalue naleznete v tématu [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="syntax"></a>Syntaxe

```cpp
class move_iterator;
```

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který se chová jako iterátor, kromě přesměrovávání. Ukládá iterátor náhodného přístupu typu `Iterator`, přístup pomocí členské funkce `base()`. Všechny operace na `move_iterator` jsou prováděny přímo na uloženém iterátoru, s tím rozdílem, že výsledek `operator*` je implicitně přetypován na `value_type&&` aby odkaz rvalue.

A `move_iterator` může být provádět operace, které nejsou definovány zabaleným iterátorem. Tyto operace by neměly být použity.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[move_iterator](#move_iterator)|Konstruktor pro objekty typu `move_iterator`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[iterator_type](#iterator_type)|Synonymum pro parametr šablony `RandomIterator`.|
|[iterator_category](#iterator_category)|Synonymum pro delší **typename** výraz se stejným názvem, `iterator_category` určuje obecné vlastnosti iterátoru.|
|[value_type](#value_type)|Synonymum pro delší **typename** výraz se stejným názvem, `value_type` popisuje typ prvků iterátoru.|
|[difference_type](#difference_type)|Synonymum pro delší **typename** výraz se stejným názvem, `difference_type` popisuje typ integrálu požadovaný k vyjádření rozdílných hodnot mezi prvky.|
|[pointer](#pointer)|Synonymum pro parametr šablony `RandomIterator`.|
|[Referenční dokumentace](#reference)|Synonymum pro `rvalue` odkaz `value_type&&`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[base](#base)|Členská funkce vrátí uložený iterátor zabalený touto `move_iterator`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[move_iterator::operator*](#op_star)|Vrátí `(reference)*base().`|
|[move_iterator::operator++](#op_add_add)|Zvýší uložený iterátor. Přesné chování závisí na tom, zda se jedná o operaci před přírůstkem nebo po přírůstku.|
|[move_iterator::operator--](#operator--)|Sníží uložený iterátor. Přesné chování závisí na tom, zda se jedná o operaci před snížením nebo po snížení.|
|[move_iterator::operator-&gt;](#op_arrow)|Vrátí `&**this`.|
|[move_iterator::operator-](#operator-)|Vrátí `move_iterator(*this) -=` tak, že nejprve odečte pravou hodnotu od aktuální pozice.|
|[move_iterator::operator[]](#op_at)|Vrátí `(reference)*(*this + off)`. Umožňuje určit posun od aktuálního základu k získání hodnoty v tomto umístění.|
|[move_iterator::operator+](#op_add)|Vrátí `move_iterator(*this) +=` hodnota. Umožňuje přidat posun k základu k získání hodnoty v tomto umístění.|
|[move_iterator::operator+=](#op_add_eq)|Přidá k uloženému iterátoru pravou hodnotu a vrátí `*this`.|
|[move_iterator::operator-=](#operator-_eq)|Odečte od uloženého iterátoru pravou hodnotu a vrátí `*this`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterátor >

**Namespace:** std

## <a name="base"></a>  move_iterator::base

Vrátí uložený iterátor pro tuto `move_iterator`.

```cpp
RandomIterator base() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uložený iterátor.

## <a name="difference_type"></a>  move_iterator::difference_type

Typ `difference_type` je `move_iterator` `typedef` podle vlastností iterátoru `difference_type`a můžou používat Zaměnitelně s ním.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro vlastnost iterátoru `typename iterator_traits<RandomIterator>::pointer`.

## <a name="iterator_category"></a>  move_iterator::iterator_category

Typ `iterator_category` je `move_iterator` `typedef` podle vlastností iterátoru `iterator_category`a můžou používat Zaměnitelně s ním.

```cpp
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro vlastnost iterátoru `typename iterator_traits<RandomIterator>::iterator_category`.

## <a name="iterator_type"></a>  move_iterator::iterator_type

Typ `iterator_type` je založena na parametru šablony `RandomIterator` pro šablonu tříd `move_iterator`a můžou používat Zaměnitelně na příslušné místo.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `RandomIterator`.

## <a name="move_iterator"></a>  move_iterator::move_iterator

Vytvoří iterátor přesunu. Pomocí parametru jako uložený iterátor.

```cpp
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Iterátor, který se použije jako uložený iterátor.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje uložený iterátor s jeho výchozí konstruktor. Zbývající konstruktory inicializují uložený iterátor s `base.base()`.

## <a name="op_add_eq"></a>  move_iterator::Operator +=

Přidá posun do uloženého iterátoru, tak, aby body uložený iterátor na prvek na nové aktuální umístění. Operátor, který převezme nové aktuálního prvku.

```cpp
move_iterator& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Posun pro přidání do aktuální pozicí a určí nové aktuální pozici.

### <a name="return-value"></a>Návratová hodnota

Vrátí nový aktuální prvek.

### <a name="remarks"></a>Poznámky

Operátor, který se přidá *_Off* k uloženému iterátoru. Vrátí `*this`.

## <a name="operator-_eq"></a>  move_iterator::Operator-=

Přesune se do zadaného počtu předchozí prvky. Tento operátor odečte posun od uloženého iterátoru.

```cpp
move_iterator& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

Operátor, který se vyhodnotí `*this += -_Off`. Vrátí `*this`.

## <a name="op_add_add"></a>  move_iterator::Operator ++

Zvýší uložený iterátor, který patří k tomuto `move_iterator.` přístupu k operátoru následného zvýšení aktuálního prvku. Operátor preincrement přistupuje další prvek.

```cpp
move_iterator& operator++();
move_iterator operator++(int);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

První operátor (preinkrement) zvýší uložený iterátor. Vrátí `*this`.

Druhý operátor (postinkrement) vytvoří kopii tohoto `*this`, vyhodnotí `++*this`. Vrátí kopii.

## <a name="op_add"></a>  move_iterator::Operator +

Vrátí pozici iterace advanced libovolný počet prvků.

```cpp
move_iterator operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

Vrátí operátor `move_iterator(*this) +=` `_Off`.

## <a name="op_at"></a>  move_iterator::Operator]

Umožňuje přístup k poli index prvků v rozsahu `move iterator`.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

Vrátí operátor `(reference)*(*this + _Off)`.

## <a name="operator--"></a>  move_iterator::Operator--

Provedení před instrumentací a snížení členské operátory provádějí snížení na uloženém iterátoru.

```cpp
move_iterator& operator--();
move_iterator operator--();
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

První sníží – operátor (predekrement) člen uložený iterátor. Vrátí `*this`.

Druhý operátor (postdekrement) vytvoří kopii tohoto `*this`, vyhodnotí `--*this`. Vrátí kopii.

## <a name="operator-"></a>  move_iterator::Operator-

Sníží uložený iterátor a vrátí uvedenou hodnotu.

```cpp
move_iterator operator-(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

Vrátí operátor `move_iterator(*this) -= _Off`.

## <a name="op_star"></a>  move_iterator::Operator *

Přístupů přes ukazatel uloženého iterátoru a vrátí hodnotu. To se chová jako `rvalue reference` a provádí přiřazení přesunutí. Operátor, který převede aktuální prvek mimo základní iterátor. Nové aktuální prvek se změní na prvek, který následuje.

```cpp
reference operator*() const;
```

### <a name="remarks"></a>Poznámky

Vrátí operátor `(reference)*base()`.

## <a name="op_arrow"></a>  move_iterator::Operator-&gt;

Jako normální `RandomIterator` `operator->`, poskytuje přístup k polím, které patří do aktuálního prvku.

```cpp
pointer operator->() const;
```

### <a name="remarks"></a>Poznámky

Vrátí operátor `&**this`.

## <a name="pointer"></a>  move_iterator::Pointer

Typ `pointer` je **typedef** podle náhodného iterátoru `RandomIterator` pro `move_iterator`a můžou používat Zaměnitelně.

```cpp
typedef RandomIterator  pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `RandomIterator`.

## <a name="reference"></a>  move_iterator::Reference

Typ `reference` je **typedef** na základě `value_type&&` pro `move_iterator`a je možné vzájemně zaměňovat s `value_type&&`.

```cpp
typedef value_type&& reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `value_type&&`, což je odkaz rvalue.

## <a name="value_type"></a>  move_iterator::value_type

Typ `value_type` je `move_iterator` `typedef` podle vlastností iterátoru `value_type`a můžou používat Zaměnitelně s ním.

```cpp
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro vlastnost iterátoru `typename iterator_traits<RandomIterator>::value_type`.

## <a name="see-also"></a>Viz také:

[\<iterator>](../standard-library/iterator.md)<br/>
[L-hodnoty a r-hodnoty](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Konstruktory a operátory přiřazení pro přesunutí (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
