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
ms.openlocfilehash: 9e8334db52e05f4a61adb7256e87ed611f0d3ecb
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689286"
---
# <a name="move_iterator-class"></a>move_iterator – třída

Šablona třídy `move_iterator` je obálkou pro iterátor. Iterátor move_iterator poskytuje stejné chování jako iterátor, kterého zabalí (uloží). Výjimkou je, že operátor přesměrování uloženého iterátoru mění na odkaz hodnoty rvalue a kopírování se tak mění na přesunutí. Další informace o rvalue naleznete v tématu [rvalue reference deklarátor: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="syntax"></a>Syntaxe

```cpp
class move_iterator;
```

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který se chová jako iterátor s výjimkou případů, kdy došlo k jeho zpětnému odkazování. Ukládá iterátor náhodného přístupu typu `Iterator`, k němuž přistupuje prostřednictvím členské funkce `base()`. Všechny operace na `move_iterator` jsou prováděny přímo na uloženém iterátoru s tím rozdílem, že výsledek `operator*` je implicitně převeden na `value_type&&`, aby odkazoval na odkaz rvalue.

@No__t_0 může být schopen operací, které nejsou definovány zabalením iterátoru. Tyto operace by neměly být použity.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[move_iterator](#move_iterator)|Konstruktor pro objekty typu `move_iterator`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[iterator_type](#iterator_type)|Synonymum pro parametr šablony `RandomIterator`.|
|[iterator_category](#iterator_category)|Synonymum pro delší výraz **TypeName** stejného názvu, `iterator_category` určuje obecné možnosti iterátoru.|
|[value_type](#value_type)|Synonymum pro delší výraz **TypeName** stejného názvu, `value_type` popisuje typ prvků iterátoru.|
|[difference_type](#difference_type)|Synonymum pro delší výraz **TypeName** stejného názvu, `difference_type` popisuje celočíselný typ vyžadovaný pro vyjádření rozdílových hodnot mezi prvky.|
|[ukazatele](#pointer)|Synonymum pro parametr šablony `RandomIterator`.|
|[odkaz](#reference)|Synonymum pro odkaz na `rvalue` `value_type&&`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[base](#base)|Členská funkce vrátí uložený iterátor uzavřený tímto `move_iterator`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[move_iterator:: operator * – operátor](#op_star)|Vrátí `(reference)*base().`|
|[move_iterator:: operator + +](#op_add_add)|Zvýší uložený iterátor. Přesné chování závisí na tom, zda se jedná o operaci před přírůstkem nebo po přírůstku.|
|[move_iterator:: operator--](#operator--)|Sníží uložený iterátor. Přesné chování závisí na tom, zda se jedná o operaci před snížením nebo po snížení.|
|[move_iterator:: operator-&gt;](#op_arrow)|Vrátí `&**this`.|
|[move_iterator:: operator-](#operator-)|Vrátí `move_iterator(*this) -=` tím, že nejprve odečte hodnotu vpravo od aktuální pozice.|
|[move_iterator:: operator [] – operátor](#op_at)|Vrátí `(reference)*(*this + off)`. Umožňuje určit posun od aktuálního základu k získání hodnoty v tomto umístění.|
|[move_iterator:: operator + – operátor](#op_add)|Vrátí `move_iterator(*this) +=` hodnotu. Umožňuje přidat posun k základu k získání hodnoty v tomto umístění.|
|[move_iterator:: operator + =](#op_add_eq)|Přidá hodnotu na pravé straně k uloženému iterátoru a vrátí `*this`.|
|[move_iterator:: operator-=](#operator-_eq)|Odečte pravou hodnotu od uloženého iterátoru a vrátí `*this`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterator >

**Obor názvů:** std

## <a name="base"></a>move_iterator:: Base

Vrátí uložený iterátor pro tento `move_iterator`.

```cpp
RandomIterator base() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uložený iterátor.

## <a name="difference_type"></a>move_iterator::d ifference_type

Typ `difference_type` je `move_iterator` `typedef` na základě vlastnosti iterátoru `difference_type` a dá se k němu zaměnit.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro vlastnost iterátoru `typename iterator_traits<RandomIterator>::pointer`.

## <a name="iterator_category"></a>move_iterator::iterator_category

Typ `iterator_category` je `move_iterator` `typedef` na základě vlastnosti iterátoru `iterator_category` a dá se k němu zaměnit.

```cpp
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro vlastnost iterátoru `typename iterator_traits<RandomIterator>::iterator_category`.

## <a name="iterator_type"></a>move_iterator::iterator_type

Typ `iterator_type` je založen na parametru šablony `RandomIterator` pro šablonu třídy `move_iterator` a lze jej v místě použít zaměnitelné.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `RandomIterator`.

## <a name="move_iterator"></a>move_iterator::move_iterator

Vytvoří iterátor přesunutí. Použije parametr jako uložený iterátor.

```cpp
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Iterátor, který se má použít jako uložený iterátor.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje uložený iterátor s jeho výchozím konstruktorem. Zbývající konstruktory inicializují uložený iterátor pomocí `base.base()`.

## <a name="op_add_eq"></a>move_iterator:: operator + =

Přidá posun k uloženému iterátoru, aby uložené iterátory odkazovaly na element v novém aktuálním umístění. Operátor pak přesune nový aktuální prvek.

```cpp
move_iterator& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_Off* \
Posun, který má být přidán na aktuální pozici pro určení nové aktuální pozice.

### <a name="return-value"></a>Návratová hodnota

Vrátí nový aktuální prvek.

### <a name="remarks"></a>Poznámky

Operátor přidá *_Off* k uloženému iterátoru. Pak vrátí `*this`.

## <a name="operator-_eq"></a>move_iterator:: operator-=

Přesune se přes zadaný počet předchozích prvků. Tento operátor odečte posun od uloženého iterátoru.

```cpp
move_iterator& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

Operátor vyhodnocuje `*this += -_Off`. Pak vrátí `*this`.

## <a name="op_add_add"></a>move_iterator:: operator + +

Zvýší uložený iterátor, který patří k tomuto `move_iterator.` k aktuálnímu prvku se přistupoval pomocí operátoru postinkrement. K dalšímu prvku se dostanete pomocí operátoru "Increment".

```cpp
move_iterator& operator++();
move_iterator operator++(int);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

První (přírůstkový) operátor zvýší uložený iterátor. Pak vrátí `*this`.

Druhý operátor (postinkrement) vytvoří kopii `*this`, vyhodnotí `++*this`. Pak vrátí kopii.

## <a name="op_add"></a>move_iterator:: operator + – operátor

Vrátí pozici iterátoru rozšířenou libovolným počtem prvků.

```cpp
move_iterator operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

Operátor vrací `move_iterator(*this) +=` `_Off`.

## <a name="op_at"></a>move_iterator:: operator [] – operátor

Umožňuje přístup k indexu pole prvkům v rozsahu `move iterator`.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

Operátor vrací `(reference)*(*this + _Off)`.

## <a name="operator--"></a>move_iterator:: operator--

Postdekrement členské operátory provádějí na uložené iterátory snížení.

```cpp
move_iterator& operator--();
move_iterator operator--();
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

První operátor členu (předsnížení) snižuje uložený iterátor. Pak vrátí `*this`.

Druhý operátor (postdekrement) vytvoří kopii `*this`, vyhodnotí `--*this`. Pak vrátí kopii.

## <a name="operator-"></a>move_iterator:: operator-

Sníží uložený iterátor a vrátí určenou hodnotu.

```cpp
move_iterator operator-(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Poznámky

Operátor vrací `move_iterator(*this) -= _Off`.

## <a name="op_star"></a>move_iterator:: operator * – operátor

Ododkazuje na uložený iterátor a vrátí hodnotu. Ta se chová jako `rvalue reference` a provádí přiřazení přesunutí. Operátor převede aktuální prvek ze základního iterátoru. Prvek, který následuje, se stal novým aktuálním prvkem.

```cpp
reference operator*() const;
```

### <a name="remarks"></a>Poznámky

Operátor vrací `(reference)*base()`.

## <a name="op_arrow"></a>move_iterator:: operator-&gt;

Podobně jako normální `RandomIterator` `operator->` poskytuje přístup k polím, která patří do aktuálního prvku.

```cpp
pointer operator->() const;
```

### <a name="remarks"></a>Poznámky

Operátor vrací `&**this`.

## <a name="pointer"></a>move_iterator::p ointer

Typ `pointer` je typu **typedef** na základě `RandomIterator` náhodného iterátoru pro `move_iterator` a lze jej použít zaměnitelné.

```cpp
typedef RandomIterator  pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `RandomIterator`.

## <a name="reference"></a>move_iterator:: Reference

Typ `reference` je typu **typedef** založeného na `value_type&&` pro `move_iterator` a lze jej použít zaměnitelné v `value_type&&`.

```cpp
typedef value_type&& reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `value_type&&`, což je odkaz rvalue.

## <a name="value_type"></a>move_iterator::value_type

Typ `value_type` je `move_iterator` `typedef` na základě vlastnosti iterátoru `value_type` a dá se k němu zaměnit.

```cpp
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro vlastnost iterátoru `typename iterator_traits<RandomIterator>::value_type`.

## <a name="see-also"></a>Viz také:

[\<iterator >](../standard-library/iterator.md) \
[Hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) \
[Konstruktory přesunutí a operátory přiřazení přesunutí (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md) \
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
