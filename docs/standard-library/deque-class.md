---
title: deque – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- deque/std::deque
- deque/std::deque::allocator_type
- deque/std::deque::const_iterator
- deque/std::deque::const_pointer
- deque/std::deque::const_reference
- deque/std::deque::const_reverse_iterator
- deque/std::deque::difference_type
- deque/std::deque::iterator
- deque/std::deque::pointer
- deque/std::deque::reference
- deque/std::deque::reverse_iterator
- deque/std::deque::size_type
- deque/std::deque::value_type
- deque/std::deque::assign
- deque/std::deque::at
- deque/std::deque::back
- deque/std::deque::begin
- deque/std::deque::cbegin
- deque/std::deque::cend
- deque/std::deque::clear
- deque/std::deque::crbegin
- deque/std::deque::crend
- deque/std::deque::emplace
- deque/std::deque::emplace_back
- deque/std::deque::emplace_front
- deque/std::deque::empty
- deque/std::deque::end
- deque/std::deque::erase
- deque/std::deque::front
- deque/std::deque::get_allocator
- deque/std::deque::insert
- deque/std::deque::max_size
- deque/std::deque::pop_back
- deque/std::deque::pop_front
- deque/std::deque::push_back
- deque/std::deque::push_front
- deque/std::deque::rbegin
- deque/std::deque::rend
- deque/std::deque::resize
- deque/std::deque::shrink_to_fit
- deque/std::deque::size
- deque/std::deque::swap
dev_langs:
- C++
helpviewer_keywords:
- std::deque [C++]
- std::deque [C++], allocator_type
- std::deque [C++], const_iterator
- std::deque [C++], const_pointer
- std::deque [C++], const_reference
- std::deque [C++], const_reverse_iterator
- std::deque [C++], difference_type
- std::deque [C++], iterator
- std::deque [C++], pointer
- std::deque [C++], reference
- std::deque [C++], reverse_iterator
- std::deque [C++], size_type
- std::deque [C++], value_type
- std::deque [C++], assign
- std::deque [C++], at
- std::deque [C++], back
- std::deque [C++], begin
- std::deque [C++], cbegin
- std::deque [C++], cend
- std::deque [C++], clear
- std::deque [C++], crbegin
- std::deque [C++], crend
- std::deque [C++], emplace
- std::deque [C++], emplace_back
- std::deque [C++], emplace_front
- std::deque [C++], empty
- std::deque [C++], end
- std::deque [C++], erase
- std::deque [C++], front
- std::deque [C++], get_allocator
- std::deque [C++], insert
- std::deque [C++], max_size
- std::deque [C++], pop_back
- std::deque [C++], pop_front
- std::deque [C++], push_back
- std::deque [C++], push_front
- std::deque [C++], rbegin
- std::deque [C++], rend
- std::deque [C++], resize
- std::deque [C++], shrink_to_fit
- std::deque [C++], size
- std::deque [C++], swap
ms.assetid: 64842ee5-057a-4063-8c16-4267a0332584
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0ed609de9d36b602bf525a9643534cf5d1d55a8
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963031"
---
# <a name="deque-class"></a>deque – třída

Uspořádá prvky daného typu v lineární uspořádání a, podobně jako vektor, umožňuje rychlý náhodný přístup na libovolný element a efektivní vložení a odstranění zádi kontejneru. Ale na rozdíl od vektor `deque` třída také podporuje efektivní vkládání a odstranění do přední části kontejneru.

## <a name="syntax"></a>Syntaxe

```unstlib
template <class Type, class Allocator =allocator<Type>>
class deque
```

### <a name="parameters"></a>Parametry

*Typ* typ dat prvku, který bude uložen do deque.

*Allocator* typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navracení zpět paměti deque. Tento argument je nepovinný a výchozí hodnota je **alokátoru\<typ > ***.*

## <a name="remarks"></a>Poznámky

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. [Vektory](../standard-library/vector-class.md) by měl být upřednostňované kontejner pro správu sekvenci, když je náhodný přístup k libovolnému prvku v na úrovni premium a vložení nebo odstranění prvků jsou pouze požadované na konci sekvence. Výkon kontejneru seznamu je vynikající při efektivní vložení a odstranění (v konstantním čase) v libovolném umístění v rámci sekvence v na úrovni premium. Tyto operace uprostřed sekvence vyžadují kopie elementu a přiřazení úměrný počtu prvků v sekvenci (lineární čas).

Deque realokace dojde, pokud musíte vložit nebo Vymazat elementy sekvence členské funkce:

- Pokud element je vložen do prázdné sekvenci, nebo pokud element se vymažou ponechte prázdné sekvenci, pak iterátory dříve vrácené [začít](#begin) a [end](#end) zneplatní.

- Pokud element disku do mechaniky na první pozici deque, pak se všechny iterátory, ale žádné odkazy, které určují prvky stávající stanou neplatnými.

- Pokud se element vloží na konci deque, pak [end](#end) a všech iterátorů, ale žádné odkazy, které určují stávající prvky, které se stanou neplatnými.

- Pokud element se vymažou do přední části deque pouze zneplatní iterátoru a odkazy na vymazaného prvek.

- Pokud se vymažou poslední prvek od konce deque, pouze že iterátor, který má posledním prvkem a odkazy na vymazaného prvek stane neplatným.

V opačném případě vložení nebo odstranění prvku zruší platnost všech iterátorů a odkazy.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[deque –](#deque)|Vytvoří `deque`. Jsou k dispozici několik konstruktorů nastavit obsah nového `deque` různými způsoby: prázdný; načtená zadaného počtu prvků prázdný; obsah přesunut nebo zkopírovaných z jiného `deque`; obsah zkopírovaný ani přesunutý pomocí iterátoru; a jeden element zkopírována `deque` `count` časy. Některé z konstruktorů povolení s využitím vlastní `allocator` k vytváření prvků.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje `allocator` třídy pro `deque` objektu.|
|[const_iterator](#const_iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může zobrazovat a číst prvky `deque` jako `const`|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na prvek v `deque` jako `const.`|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na prvek v `deque` pro čtení a další operace jako `const.`|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může zobrazovat a číst prvky `deque` jako **const**. V opačném pořadí zobrazení deque. Další informace najdete v tématu [reverse_iterator – třída](../standard-library/reverse-iterator-class.md)|
|[difference_type](#difference_type)|Typ, který obsahuje rozdíl mezi dvěma iterátory s náhodným přístupem, které odkazují na prvky ve stejném `deque`.|
|[iterátor](#iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat libovolný prvek v `deque`.|
|[Ukazatel](#pointer)|Typ, který poskytuje ukazatel na prvek v `deque`.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na prvek uložený v `deque`.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat prvek v `deque`. V opačném pořadí zobrazení deque.|
|[size_type](#size_type)|Typ, který vrátí počet prvků v `deque`.|
|[value_type](#value_type)|Typ, který představuje typ dat uložených v `deque`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[přiřazení](#assign)|Odstraní prvky ze `deque` a zkopíruje novou posloupnost prvků k cíli `deque`.|
|[at](#at)|Vrátí odkaz na prvek v zadaném umístění v `deque`.|
|[Zpět](#back)|Vrátí odkaz na poslední prvek `deque`.|
|[začít](#begin)|Vrátí iterátor náhodného přístupu adresující první prvek v `deque`.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor na první prvek `deque`.|
|[cend](#cend)|Vrátí náhodným přístupem **const** iterátor, který ukazuje přesně za konec `deque`.|
|[Vymazat](#clear)|Vymaže všechny prvky `deque`.|
|[crbegin](#crbegin)|Vrátí konstantní iterátor náhodného přístupu na první prvek v `deque` zobrazit v obráceném pořadí.|
|[crend –](#crend)|Vrátí konstantní iterátor náhodného přístupu na první prvek v `deque` zobrazit v obráceném pořadí.|
|[emplace –](#emplace)|Vloží vytvořený prvek na místo do `deque` na určené pozici.|
|[emplace_back](#emplace_back)|Přidá prvek vytvořený v místě na konec objektu `deque`.|
|[emplace_front –](#emplace_front)|Přidá prvek vytvořený v místě na začátek `deque`.|
|[prázdný](#empty)|Vrátí **true** Pokud `deque` neobsahuje žádnou prvky a **false** pokud obsahuje jeden nebo více prvků.|
|[ukončení](#end)|Vrátí iterátor náhodného přístupu, na kterou odkazuje přesně za konec `deque`.|
|[vymazání](#erase)|Odebere prvek nebo rozsah prvků `deque` od zadané pozice.|
|[Přední](#front)|Vrátí odkaz na první prvek v `deque`.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu `allocator` objekt, který se používá ke konstrukci `deque`.|
|[Vložit](#insert)|Vloží prvek, několik prvků nebo rozsahu prvků do `deque` na určené pozici.|
|[max_size](#max_size)|Vrátí maximální možná délka `deque`.|
|[pop_back –](#pop_back)|Odstraní prvek na konec `deque`.|
|[pop_front](#pop_front)|Odstraní prvek na začátku `deque`.|
|[push_back](#push_back)|Přidá prvek na konec objektu `deque`.|
|[push_front](#push_front)|Přidá prvek na začátku `deque`.|
|[rbegin –](#rbegin)|Vrátí iterátor s náhodným přístupem na první prvek v obráceném objektu `deque`.|
|[rend –](#rend)|Vrátí iterátor náhodného přístupu, který ukazuje za poslední prvek v obráceném objektu `deque`.|
|[Změna velikosti](#resize)|Určuje novou velikost `deque`.|
|[shrink_to_fit](#shrink_to_fit)|Odstraní nadbytečnou kapacitu.|
|[Velikost](#size)|Vrátí počet prvků v `deque`.|
|[Prohození](#swap)|Vymění prvky dvou `deque`s.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[– operátor&#91;&#93;](#op_at)|Vrátí odkaz na `deque` prvek na zadané pozici.|
|[operátor =](#op_eq)|Nahradí prvky objektu `deque` s kopií jiného `deque`.|

## <a name="requirements"></a>Požadavky

**Hlavička**: \<deque >

## <a name="allocator_type"></a>  deque::allocator_type

Typ, který představuje třídu alokátoru pro objekt deque.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type` je synonymum pro parametr šablony `Allocator`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_allocator](#get_allocator).

## <a name="assign"></a>  deque::Assign

Odstraní prvky z deque a zkopíruje novou sadu prvků do cílového deque.

```cpp
template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);

void assign(
    size_type Count,
    const Type& Val);

void assign(initializer_list<Type> IList);
```

### <a name="parameters"></a>Parametry

*První* pozice prvního prvku v rozsahu prvků, zkopírovány z argumentu deque.

*Poslední* pozice prvního prvku mimo rozsah prvků zkopírovány z argumentu deque.

*Počet* počet kopií prvku vloženého do deque.

*Val* hodnota prvku vloženého do deque.

*IList* initializer_list vloženého do deque.

### <a name="remarks"></a>Poznámky

Po jakýchkoli prvků v cílovém deque jsou vymazány, `assign` buď vložení zadaného rozsahu prvků z původního deque nebo z některé deque do cílové deque nebo vložení kopií nového prvku zadané hodnoty do cílového deque.

### <a name="example"></a>Příklad

```cpp
// deque_assign.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <initializer_list>

int main()
{
    using namespace std;
    deque <int> c1, c2;
    deque <int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    deque<int> d1{ 1, 2, 3, 4 };
    initializer_list<int> iList{ 5, 6, 7, 8 };
    d1.assign(iList);

    cout << "d1 = ";
    for (int i : d1)
        cout << i;
    cout << endl;

    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

}

```

```Output
d1 = 5678c1 =102030c1 =5060c1 =4444444
```

## <a name="at"></a>  deque::AT

Vrátí odkaz na prvek v zadaném umístění deque.

```cpp
reference at(size_type pos);

const_reference at(size_type pos) const;
```

### <a name="parameters"></a>Parametry

*POS* dolní index (nebo číslo pozice) elementu odkazovat deque.

### <a name="return-value"></a>Návratová hodnota

Pokud *pos* je větší než velikost deque, `at` vyvolá výjimku.

### <a name="return-value"></a>Návratová hodnota

Pokud návratová hodnota `at` je přiřazen `const_reference`, deque objekt nelze změnit. Pokud návratová hodnota `at` je přiřazen `reference`, deque objekt lze upravit.

### <a name="example"></a>Příklad

```cpp
// deque_at.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int& i = c1.at( 0 );
   int& j = c1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a>  deque::back

Vrátí odkaz na poslední prvek deque.

```cpp
reference back();
const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Poslední prvek deque. Pokud deque je prázdný, návratová hodnota není definována.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `back` je přiřazen `const_reference`, deque objekt nelze změnit. Pokud návratová hodnota `back` je přiřazen `reference`, deque objekt lze upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definováno jako 1 nebo 2, dojde k chybě při pokusu o přístup k prvku v prázdné deque.  Zobrazit [Checked Iterators](../standard-library/checked-iterators.md) Další informace.

### <a name="example"></a>Příklad

```cpp
// deque_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.back( );
   const int& ii = c1.front( );

   cout << "The last integer of c1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of c1 is " << ii << endl;
}
```

```Output
The last integer of c1 is 11
The next-to-last integer of c1 is 10
```

## <a name="begin"></a>  deque::begin

Vrátí iterátor adresující první prvek deque.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor pro náhodný přístup adresující první prvek deque nebo na umístění následující po prázdný deque.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `begin` je přiřazen `const_iterator`, deque objekt nelze změnit. Pokud návratová hodnota `begin` je přiřazena `iterator`, deque objekt lze upravit.

### <a name="example"></a>Příklad

```cpp
// deque_begin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::const_iterator c1_cIter;

   c1.push_back( 1 );
   c1.push_back( 2 );

   c1_Iter = c1.begin( );
   cout << "The first element of c1 is " << *c1_Iter << endl;

*c1_Iter = 20;
   c1_Iter = c1.begin( );
   cout << "The first element of c1 is now " << *c1_Iter << endl;

   // The following line would be an error because iterator is const
   // *c1_cIter = 200;
}
```

```Output
The first element of c1 is 1
The first element of c1 is now 20
```

## <a name="cbegin"></a>  deque::cbegin

Vrátí **const** iterátor adresující první prvek v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

A **const** iterátor s náhodným přístupem, který ukazuje na první prvek rozsahu nebo na umístění hned za koncem prázdného rozsahu (pro prázdný rozsah `cbegin() == cend()`).

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin`, nejde upravit prvky v rozsahu.

Můžete použít tuto členskou funkci místo `begin()` členskou funkci pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) zadejte klíčovým slovem odvození, jak je znázorněno v následujícím příkladu. V tomto příkladu zvažte `Container` jako upravitelný (jinou hodnotu než `const`) kontejner jakéhokoli druhu, který podporuje `begin()` a `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  deque::cend

Vrátí **const** iterátor adresující umístění hned za posledním prvkem v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor pro náhodný přístup, který ukazuje přesně za konec rozsahu.

### <a name="remarks"></a>Poznámky

`cend` slouží k otestování, zda iterátor prošel konec rozsahu.

Můžete použít tuto členskou funkci místo `end()` členskou funkci pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) zadejte klíčovým slovem odvození, jak je znázorněno v následujícím příkladu. V tomto příkladu zvažte `Container` jako upravitelný (jinou hodnotu než **const**) kontejner jakéhokoli druhu, který podporuje `end()` a `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Hodnota vrácená `cend` by neměla být dereferencována.

## <a name="clear"></a>  deque::clear

Vymaže všechny prvky deque.

```cpp
void clear();
```

### <a name="example"></a>Příklad

```cpp
// deque_clear.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the deque is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of the deque after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the deque is initially 3
The size of the deque after clearing is 0
```

## <a name="const_iterator"></a>  deque::const_iterator

Typ, který poskytuje iterátor náhodného přístupu, který může zobrazovat a číst **const** prvek deque.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [zpět](#back).

## <a name="const_pointer"></a>  deque::const_pointer

Poskytuje ukazatel **const** element v deque.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku. [Iterátoru](#iterator) se běžněji používá pro přístup k prvku deque.

## <a name="const_reference"></a>  deque::const_reference

Typ, který poskytuje odkaz na **const** prvek uložený v deque – pro čtení a provádění **const** operace.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

Typ `const_reference` nelze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

```cpp
// deque_const_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const deque <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a>  deque::const_reverse_iterator

Typ, který poskytuje iterátor náhodného přístupu, který může přečíst jakýkoli **const** prvek deque.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` hodnotu prvku nelze změnit a slouží k iteraci v rámci deque – v opačném pořadí.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rbegin –](#rbegin) příklad toho, jak deklarovat a používat iterátor.

## <a name="crbegin"></a>  deque::crbegin

Vrátí konstantní iterátor na první prvek v obráceném objektu deque.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Reverse konstantní iterátor adresující první prvek v obráceném objektu s náhodným přístupem [deque](../standard-library/deque-class.md) nebo co bylo posledním prvkem v neobráceném adresování `deque`.

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `crbegin`, `deque` objekt nelze změnit.

### <a name="example"></a>Příklad

```cpp
// deque_crbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator v1_Iter;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of deque is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed deque is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of deque is 1.
The first element of the reversed deque is 2.
```

## <a name="crend"></a>  deque::crend

Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu deque.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Reverse konstantní iterátor s náhodným přístupem, který adresuje umístění následující po posledním prvku v obráceném objektu [deque](../standard-library/deque-class.md) (umístění, ke které došlo před první prvek v neobráceném deque).

### <a name="remarks"></a>Poznámky

`crend` se používá s obráceném objektu `deque` stejně jako [array::cend](../standard-library/array-class-stl.md#cend) se používá s `deque`.

S návratovou hodnotou `crend` (vhodně snížen), `deque` objekt nelze změnit.

`crend` slouží k otestování pro Určuje, zda zpětný iterátor dosáhl konce jeho deque.

Hodnota vrácená `crend` by neměla být dereferencována.

### <a name="example"></a>Příklad

```cpp
// deque_crend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="deque"></a>  deque::deque

Sestaví deque určité velikosti nebo s prvky určité hodnoty, nebo se zvláštní alokátory nebo jako kopii celé nebo části některé deque.

```cpp
deque();

explicit deque(const Allocator& Al);
explicit deque(size_type Count);
deque(size_type Count, const Type& Val);

deque(
    size_type Count,
    const Type& Val,
    const Allocator& Al);

deque(const deque& Right);

template <class InputIterator>
deque(InputIterator First,  InputIterator Last);

template <class InputIterator>
deque(
   InputIterator First,
   InputIterator Last,
   const Allocator& Al);

deque(initializer_list<value_type> IList, const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Al*|Třída alokátoru, která se má použít s tímto objektem.|
|*Počet*|Počet prvků v konstruovaný deque.|
|*Val*|Hodnota prvků v konstruovaný deque.|
|*Doprava*|Deque –, který je vytvořený deque kopií.|
|*první*|Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.|
|*poslední*|Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.|
|* IList.|Objekt initializer_list, které se mají zkopírovat.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt alokátoru (*Al*) a inicializovat deque.

První dva konstruktory určují prázdný počáteční deque; pro druhou kolekci také určuje typ alokátoru (`_Al`) který se má použít.

Třetí konstruktor určuje opakování zadaného počtu (`count`) prvků výchozí hodnoty pro třídu `Type`.

Čtvrtý a pátý konstruktor určuje opakování (*počet*) prvků hodnoty `val`.

Šestý konstruktor určuje kopii deque *vpravo*.

Sedmý a osmý konstruktory kopírují rozsah `[First, Last)` z deque.

Sedmý konstruktor přesune deque *vpravo*.

Osmý konstruktor zkopíruje obsah objektu initializer_list.

Žádné konstruktory neprovádí žádná prozatímní přerozdělení.

### <a name="example"></a>Příklad

```cpp
/ compile with: /EHsc
#include <deque>
#include <iostream>
#include <forward_list>

int main()
{
    using namespace std;

    forward_list<int> f1{ 1, 2, 3, 4 };

    f1.insert_after(f1.begin(), { 5, 6, 7, 8 });

    deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1(3);

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2(5, 2);

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3(3, 1, c2.get_allocator());

    // Create a copy, deque c4, of deque c2
    deque <int> c4(c2);

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    deque <int> c5(c4.begin(), c4_Iter);

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    deque <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

    initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for (int i : c1)
        cout << i << " ";
    cout << endl;

    cout << "c2 = ";
    for (int i : c2)
        cout << i << " ";
    cout << endl;

    cout << "c3 = ";
    for (int i : c3)
        cout << i << " ";
    cout << endl;

    cout << "c4 = ";
    for (int i : c4)
        cout << i << " ";
    cout << endl;

    cout << "c5 = ";
    for (int i : c5)
        cout << i << " ";
    cout << endl;

    cout << "c6 = ";
    for (int i : c6)
        cout << i << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7(move(c6));
    deque <int>::iterator c7_Iter;

    cout << "c7 =";
    for (int i : c7)
        cout << i << " ";
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    for (int i : c9)
        cout << i << " ";
    cout << endl;

    int x = 3;
}
// deque_deque.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
    using namespace std;
   deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1( 3 );

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2( 5, 2 );

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3( 3, 1, c2.get_allocator( ) );

    // Create a copy, deque c4, of deque c2
    deque <int> c4( c2 );

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin( );
    c4_Iter++;
    c4_Iter++;
    deque <int> c5( c4.begin( ), c4_Iter );

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin( );
   c4_Iter++;
   c4_Iter++;
   c4_Iter++;
   deque <int> c6( c4.begin( ), c4_Iter, c2.get_allocator( ) );

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

        initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
        cout << *c1_Iter << " ";
    cout << endl;

    cout << "c2 = ";
    for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
        cout << *c2_Iter << " ";
    cout << endl;

    cout << "c3 = ";
    for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
        cout << *c3_Iter << " ";
    cout << endl;

    cout << "c4 = ";
    for ( c4_Iter = c4.begin( ); c4_Iter != c4.end( ); c4_Iter++ )
        cout << *c4_Iter << " ";
    cout << endl;

    cout << "c5 = ";
    for ( c5_Iter = c5.begin( ); c5_Iter != c5.end( ); c5_Iter++ )
        cout << *c5_Iter << " ";
    cout << endl;

    cout << "c6 = ";
    for ( c6_Iter = c6.begin( ); c6_Iter != c6.end( ); c6_Iter++ )
        cout << *c6_Iter << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7( move(c6) );
    deque <int>::iterator c7_Iter;

    cout << "c7 =" ;
    for ( c7_Iter = c7.begin( ) ; c7_Iter != c7.end( ) ; c7_Iter++ )
        cout << " " << *c7_Iter;
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    or (int i : c9)
        cout << i << " ";
    cout << endl;
}
```

## <a name="difference_type"></a>  deque::difference_type

Typ, který obsahuje rozdíl mezi dvěma iterátory, které odkazují na prvky v rámci stejné deque.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

A `difference_type` lze popsat také jako počet prvků mezi dvěma ukazateli.

### <a name="example"></a>Příklad

```cpp
// deque_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <deque>
#include <algorithm>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   deque <int>::difference_type df_typ1, df_typ2, df_typ3;

   df_typ1 = count( c1_Iter, c2_Iter, 10 );
   df_typ2 = count( c1_Iter, c2_Iter, 20 );
   df_typ3 = count( c1_Iter, c2_Iter, 30 );
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";
}
```

```Output
The number '10' is in c1 collection 1 times.
The number '20' is in c1 collection 2 times.
The number '30' is in c1 collection 3 times.
```

## <a name="emplace"></a>  deque::emplace

Vloží vytvořený prvek na místo do deque na určené pozici.

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*_Where*|Pozice v [deque](../standard-library/deque-class.md) vloženy první prvek.|
|*Val*|Hodnota prvku vloženého do `deque`.|

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor, který odkazuje na místo, kde nový prvek vložila do deque.

### <a name="remarks"></a>Poznámky

Všechny operace vložení může být nákladné, naleznete v tématu `deque` diskuzi o `deque` výkonu.

### <a name="example"></a>Příklad

```cpp
// deque_emplace.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
vv1[0] = 10 20 30
```

## <a name="emplace_back"></a>  deque::emplace_back

Přidá prvek vytvořený v místě na konec objektu deque.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Prvek přidán na konec objektu [deque](../standard-library/deque-class.md).|

### <a name="example"></a>Příklad

```cpp
// deque_emplace_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_back( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="emplace_front"></a>  deque::emplace_front

Přidá prvek vytvořený v místě na konec objektu deque.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Element přidá na začátek [deque](../standard-library/deque-class.md).|

### <a name="example"></a>Příklad

```cpp
// deque_emplace_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_front( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="empty"></a>  deque::Empty

Testuje, zda deque je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud deque je prázdná. **false** Pokud deque není prázdný.

### <a name="example"></a>Příklad

```cpp
// deque_empty.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The deque is empty." << endl;
   else
      cout << "The deque is not empty." << endl;
}
```

```Output
The deque is not empty.
```

## <a name="end"></a>  deque::end

Vrátí iterátor adresující umístění následující po posledním prvku v deque.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor s náhodným přístupem, který adresuje umístění následující po posledním prvku v deque. Pokud deque je prázdný, pak deque::end == deque::begin.

### <a name="remarks"></a>Poznámky

`end` slouží k otestování, zda iterátor dosáhl konce jeho deque.

### <a name="example"></a>Příklad

```cpp
// deque_end.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
 *c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is " << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // deque <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The deque is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The deque is now: 10 400 30
```

## <a name="erase"></a>  deque::Erase

Odebere prvek nebo rozsah prvků v deque od zadané pozice.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Parametry

*_Where* pozici elementu, který má být odebrán z deque.

*první* pozice prvního prvku odebrán deque.

*poslední* pozice bezprostředně za posledním prvkem odebrán deque.

### <a name="return-value"></a>Návratová hodnota

Iterátor náhodného přístupu, který určuje první prvek zbývající za jakýmikoli odstraněnými prvky, nebo ukazatel na konci deque, pokud žádný takový prvek neexistuje.

### <a name="remarks"></a>Poznámky

`erase` nikdy nevyvolá výjimku.

### <a name="example"></a>Příklad

```cpp
// deque_erase.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial deque is: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the deque becomes:  ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, deque becomes: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
}
```

```Output
The initial deque is: 10 20 30 40 50
After erasing the first element, the deque becomes:  20 30 40 50
After erasing all elements but the first, deque becomes: 20
```

## <a name="front"></a>  deque::front

Vrátí odkaz na první prvek v deque.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud deque je prázdný, vrácení není definován.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `front` je přiřazen `const_reference`, deque objekt nelze změnit. Pokud návratová hodnota `front` je přiřazen `reference`, deque objekt lze upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definováno jako 1 nebo 2, dojde k chybě při pokusu o přístup k prvku v prázdné deque.  Zobrazit [Checked Iterators](../standard-library/checked-iterators.md) Další informace.

### <a name="example"></a>Příklad

```cpp
// deque_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.front( );
   const int& ii = c1.front( );

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The second integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 11
```

## <a name="get_allocator"></a>  deque::get_allocator

Vrátí kopii přidělování objektu používanou k vytvoření deque.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Allocator používané deque.

### <a name="remarks"></a>Poznámky

Alokátory pro deque – Třída zadejte, jak spravuje třídu úložiště. Výchozí alokátorů součástí třídy kontejneru standardní knihovny C++ postačí pro většinu programovacích potřeb. Psaní a použití vlastní třídu alokátoru je rozšířená C++.

### <a name="example"></a>Příklad

```cpp
// deque_get_allocator.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   deque <int> c1;
   deque <int, allocator<int> > c2 = deque <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   deque <int> c3( c1.get_allocator( ) );

   deque <int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a>  deque::Insert

Vloží prvek nebo prvky, nebo rozsah prvků do deque na určené pozici.

```cpp
iterator insert(
    const_iterator Where,
    const Type& Val);

iterator insert(
    const_iterator Where,
    Type&& Val);

void insert(
    iterator Where,
    size_type Count,
    const Type& Val);

template <class InputIterator>
void insert(
    iterator Where,
    InputIterator First,
    InputIterator Last);

iterator insert(
    iterator Where,initializer_list<Type>
IList);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*kde*|Pozice v cílové deque vloženy první prvek.|
|*Val*|Hodnota prvku vloženého do deque.|
|*Počet*|Počet prvků vloženého do deque.|
|*první*|Pozice prvního prvku v rozsahu prvků v deque argumentů, které se mají zkopírovat.|
|*poslední*|Pozice prvního prvku mimo rozsah prvků v deque argumentů, které se mají zkopírovat.|
|*IList*|Objekt initializer_list elementy vložit.|

### <a name="return-value"></a>Návratová hodnota

Vložit první dvě funkce vrátí iterátor, který odkazuje na místo, kde nový prvek vložila do deque.

### <a name="remarks"></a>Poznámky

Všechny operace vložení může být nákladné.

## <a name="iterator"></a>  deque::iterator

Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat libovolný prvek v deque.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

Typ `iterator` lze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin).

## <a name="max_size"></a>  deque::max_size

Vrátí maximální délku objektu deque.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka deque.

### <a name="example"></a>Příklad

```cpp
// deque_max_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   i = c1.max_size( );
   cout << "The maximum possible length of the deque is " << i << "." << endl;
}
```

## <a name="op_at"></a>  deque::Operator]

Vrátí odkaz na element deque na určené pozici.

```cpp
reference operator[](size_type pos);

const_reference operator[](size_type pos) const;
```

### <a name="parameters"></a>Parametry

*POS* pozice prvku deque má odkazovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na element, jehož pozice se zadaným v argumentu. Pokud zadané umístění je větší než velikost deque, výsledek není definován.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `operator[]` je přiřazen `const_reference`, deque objekt nelze změnit. Pokud návratová hodnota `operator[]` je přiřazen `reference`, deque objekt lze upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definováno jako 1 nebo 2, dojde k chybě při pokusu o přístup k prvku mimo hranice deque.  Zobrazit [Checked Iterators](../standard-library/checked-iterators.md) Další informace.

### <a name="example"></a>Příklad

```cpp
// deque_op_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   cout << "The first integer of c1 is " << c1[0] << endl;
   int& i = c1[1];
   cout << "The second integer of c1 is " << i << endl;

}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 20
```

## <a name="op_eq"></a>  deque::Operator =

Nahradí prvky objektu tohoto deque, konkrétně pomocí elementů z jiného deque.

```cpp
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*doprava*|Deque –, který poskytuje nový obsah.|

### <a name="remarks"></a>Poznámky

První přepsání zkopíruje prvky tohoto deque z *správné*, zdroj přiřazení. Druhý přepsání přesune prvky na této deque z *správné*.

Elementy, které jsou součástí této deque před provedením operátor, který se odeberou.

### <a name="example"></a>Příklad

```cpp
// deque_operator_as.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
using namespace std;

typedef deque<int> MyDeque;

template<typename MyDeque> struct S;

template<typename MyDeque> struct S<MyDeque&> {
  static void show( MyDeque& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
    cout << endl;
  }
};

template<typename MyDeque> struct S<MyDeque&&> {
  static void show( MyDeque&& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
cout << " via unnamed rvalue reference " << endl;
  }
};

int main( )
{
   MyDeque d1, d2;

   d1.push_back(10);
   d1.push_back(20);
   d1.push_back(30);
   d1.push_back(40);
   d1.push_back(50);

   cout << "d1 = " ;
   S<MyDeque&>::show( d1 );

   d2 = d1;
   cout << "d2 = ";
   S<MyDeque&>::show( d2 );

   cout << "     ";
   S<MyDeque&&>::show ( move< MyDeque& > (d1) );
 }
```

## <a name="pointer"></a>  deque::Pointer

Poskytuje ukazatel na prvek v [deque](../standard-library/deque-class.md).

```unstlib
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze použít ke změně hodnoty prvku. [Iterátoru](#iterator) se běžněji používá pro přístup k prvku deque.

## <a name="pop_back"></a>  deque::pop_back

Odstraní prvek na konec deque.

```cpp
void pop_back();
```

### <a name="remarks"></a>Poznámky

Poslední prvek nesmí být prázdný. `pop_back` nikdy nevyvolá výjimku.

### <a name="example"></a>Příklad

```cpp
// deque_pop_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the deque, the "
      "last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the deque, the last element is: 1
```

## <a name="pop_front"></a>  deque::pop_front

Odstraní prvek na začátku deque.

```cpp
void pop_front();
```

### <a name="remarks"></a>Poznámky

První prvek nesmí být prázdný. `pop_front` nikdy nevyvolá výjimku.

### <a name="example"></a>Příklad

```cpp
// deque_pop_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the "
      "deque, the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the deque, the first element is: 2
```

## <a name="push_back"></a>  deque::push_back

Přidá prvek na konec objektu deque.

```cpp
void push_back(const Type& val);

void push_back(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Prvek přidán na konec objektu deque.|

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, deque zůstane beze změny a je znovu vyvolána výjimka.

## <a name="push_front"></a>  deque::push_front

Přidá prvek na začátku deque.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Element přidá na začátek deque.|

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, deque zůstane beze změny a je znovu vyvolána výjimka.

### <a name="example"></a>Příklad

```cpp
// deque_push_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a deque of strings
   deque <string> c2;
   string str("a");

   c2.push_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
First element: 1
New first element: 2
Moved first element: a
```

## <a name="rbegin"></a>  deque::rbegin

Vrátí iterátor na první prvek v obráceném objektu deque.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Zpětný iterátor náhodného přístupu adresující první prvek v obráceném objektu deque nebo adresování, co bylo posledním prvkem v neobráceném deque.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s obrácený deque – stejně jako [začít](#begin) se používá s deque.

Pokud návratová hodnota `rbegin` je přiřazen `const_reverse_iterator`, deque objekt nelze změnit. Pokud návratová hodnota `rbegin` je přiřazen `reverse_iterator`, deque objekt lze upravit.

`rbegin` můžete použít k iteraci v rámci deque zpětně.

### <a name="example"></a>Příklad

```cpp
// deque_rbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rbegin( );
   cout << "Last element in the deque is " << *c1_rIter << "." << endl;

   cout << "The deque contains the elements: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << "in that order.";
   cout << endl;

   // rbegin can be used to iterate through a deque in reverse order
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rbegin( );
 *c1_rIter = 40;  // This would have caused an error if a
                    // const_reverse iterator had been declared as
                    // noted above
   cout << "Last element in deque is now " << *c1_rIter << "." << endl;
}
```

```Output
Last element in the deque is 30.
The deque contains the elements: 10 20 30 in that order.
The reversed deque is: 30 20 10
Last element in deque is now 40.
```

## <a name="reference"></a>  deque::Reference

Typ, který poskytuje odkaz na prvek uložený v deque.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Příklad

```cpp
// deque_reference.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="rend"></a>  deque::rend

Vrátí iterátor adresující umístění následující po posledním prvku v obráceném objektu deque.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Zpětný iterátor náhodného přístupu, který adresuje umístění následující po posledním prvku v obráceném objektu deque (umístění, ke které došlo před první prvek v neobráceném deque).

### <a name="remarks"></a>Poznámky

`rend` se používá s obrácený deque – stejně jako [end](#end) se používá s deque.

Pokud návratová hodnota `rend` je přiřazen `const_reverse_iterator`, deque objekt nelze změnit. Pokud návratová hodnota `rend` je přiřazen `reverse_iterator`, deque objekt lze upravit.

`rend` slouží k ověření, zda zpětný iterátor dosáhl konce jeho deque.

Hodnota vrácená `rend` by neměla být dereferencována.

### <a name="example"></a>Příklad

```cpp
// deque_rend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;
   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --; // Decrementing a reverse iterator moves it forward
                // in the deque (to point to the first element here)
   cout << "The first element in the deque is: " << *c1_rIter << endl;

   cout << "The deque is: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << endl;

   // rend can be used to test if an iteration is through all of
   // the elements of a reversed deque
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--; // Decrementing the reverse iterator moves it backward
               // in the reversed deque (to the last element here)
 *c1_rIter = 40; // This modification of the last element would
                   // have caused an error if a const_reverse
                   // iterator had been declared (as noted above)
   cout << "The modified reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;
}
```

```Output
The first element in the deque is: 10
The deque is: 10 20 30
The reversed deque is: 30 20 10
The modified reversed deque is: 30 20 40
```

## <a name="resize"></a>  deque::Resize

Určuje novou velikost deque.

```cpp
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Parametry

*_Newsize* novou velikost deque.

*Val* nové prvky, které mají být přidány do deque – Pokud je nová velikost větší hodnotu, která původní velikost. Pokud je hodnota vynechána, nové prvky jsou přiřazeny výchozí hodnotě pro třídu.

### <a name="remarks"></a>Poznámky

Pokud deque velikost je menší než požadovaná velikost *_Newsize*, prvky jsou přidány do deque, dokud nedosáhne požadované velikosti.

Pokud deque velikost je větší než požadovaná velikost, prvky nejblíže konci deque jsou odstraněny, dokud deque dosáhne velikosti *_Newsize*.

Pokud je k dispozici velikost deque je stejná jako požadovaná velikost, nedojde k žádné akci.

[velikost](#size) odráží aktuální velikost deque.

### <a name="example"></a>Příklad

```cpp
// deque_resize.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is: 4
The value of the last element is 40
The size of c1 is now: 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse_iterator"></a>  deque::reverse_iterator

Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat prvek v obráceném objektu deque.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iteraci v rámci deque.

### <a name="example"></a>Příklad

Podívejte se na příklad pro rbegin –.

## <a name="shrink_to_fit"></a>  deque::shrink_to_fit

Odstraní nadbytečnou kapacitu.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Poznámky

Neexistuje žádný přenosný způsob, jak zjistit, jestli `shrink_to_fit` snižuje úložiště využitá službou [deque](../standard-library/deque-class.md).

### <a name="example"></a>Příklad

```cpp
// deque_shrink_to_fit.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   //deque <int>::iterator Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
   v1.shrink_to_fit();
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
}
```

```Output
Current size of v1 = 1
Current size of v1 = 1
```

## <a name="size"></a>  deque::size

Vrátí počet prvků deque.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka deque.

### <a name="example"></a>Příklad

```cpp
// deque_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   c1.push_back( 1 );
   i = c1.size( );
   cout << "The deque length is " << i << "." << endl;

   c1.push_back( 2 );
   i = c1.size( );
   cout << "The deque length is now " << i << "." << endl;
}
```

```Output
The deque length is 1.
The deque length is now 2.
```

## <a name="size_type"></a>  deque::size_type

Typ, který vrátí počet prvků v deque.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [velikost](#size).

## <a name="swap"></a>  deque::swap

Vymění prvky dvou deques.

```cpp
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*správné* deque poskytující prvky pro záměnu nebo deque, jehož prvky mají vyměnit s těmi deque `left`.

*levé* deque, jehož prvky mají vyměnit s těmi deque *správné*.

### <a name="example"></a>Příklad

```cpp
// deque_swap.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2, c3;
   deque <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap<>(c1, c2);
   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original deque c1 is: 1 2 3
After swapping with c2, deque c1 is: 10 20
After swapping with c3, deque c1 is: 100
After swapping with c2, deque c1 is: 1 2 3
```

## <a name="value_type"></a>  deque::value_type

Typ, který představuje datový typ uložený v deque.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Poznámky

`value_type` je synonymum pro parametr šablony `Type`.

### <a name="example"></a>Příklad

```cpp
// deque_value_type.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
int main( )
{
   using namespace std;
   deque<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
