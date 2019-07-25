---
title: deque – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: d78bbc6e66fe97af1049fa6976ac8c5fa806ef43
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448564"
---
# <a name="deque-class"></a>deque – třída

Uspořádá prvky daného typu v lineárním uspořádání a, jako je vektor, umožňuje rychlý náhodný přístup k jakémukoli prvku a efektivní vkládání a odstraňování na zadní straně kontejneru. Nicméně na rozdíl od vektoru `deque` třída také podporuje efektivní vkládání a odstraňování na přední straně kontejneru.

## <a name="syntax"></a>Syntaxe

```unstlib
template <class Type, class Allocator =allocator<Type>>
class deque
```

### <a name="parameters"></a>Parametry

*Textový*\
Typ dat prvku, který bude uložen v deque.

*Dělující*\
Typ, který představuje uložený objekt přidělování, který zapouzdřuje informace o přidělování a navracení paměti deque. Tento argument je nepovinný a výchozí hodnota je **typ\<přidělování >** .

## <a name="remarks"></a>Poznámky

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. [Vektory](../standard-library/vector-class.md) by měly být upřednostňovaným kontejnerem pro správu sekvence, pokud je náhodný přístup k jakémukoli prvku na úrovni Premium a vložení nebo odstranění prvků je vyžadováno pouze na konci sekvence. Výkon kontejneru seznamu je vynikající, když jsou efektivní vkládání a mazání (v konstantním čase) v jakémkoli umístění v rámci sekvence na prémii. Tyto operace uprostřed sekvence vyžadují kopie prvků a přiřazení úměrné počtu prvků v sekvenci (lineární čas).

K realokaci deque dojde, pokud členská funkce musí vkládat nebo mazat prvky sekvence:

- Pokud je element vložen do prázdné sekvence nebo je-li prvek smazán, chcete-li opustit prázdnou sekvenci, pak iterátory dříve vrácené funkcí [Begin](#begin) a [End](#end) se stanou neplatnými.

- Pokud je element vložen na první pozici deque, pak všechny iterátory, ale žádné odkazy, které určují existující prvky, se stanou neplatnými.

- Pokud je element vložen na konci deque, pak [Ukončete](#end) a všechny iterátory, ale žádné odkazy, které určují existující prvky, se stanou neplatnými.

- Pokud je prvek smazán na začátku deque, pouze tento iterátor a odkazy na smazáný element se stanou neplatnými.

- Pokud je poslední prvek smazán z konce deque, pouze tento iterátor koncového prvku a odkazy na vymazání elementu se stanou neplatnými.

V opačném případě vložení nebo mazání elementu zruší platnost všech iterátorů a odkazů.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[deque](#deque)|`deque`Vytvoří. K dispozici je několik konstruktorů pro nastavení obsahu nového `deque` v různých způsobech: prázdné; načteno se zadaným počtem prázdných prvků. obsah byl přesunut nebo zkopírován z jiného `deque`, obsah byl zkopírován nebo přesunut pomocí iterátoru. jeden prvek byl `deque` `count` zkopírován do doby. Některé konstruktory umožňují použití vlastního `allocator` pro vytváření elementů.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje `allocator` třídu `deque` pro objekt.|
|[const_iterator](#const_iterator)|Typ, který poskytuje iterátor náhodného přístupu, který má přístup k prvkům v As `deque` a jejich čtení`const`|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na prvek v `deque` podobě`const.`|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na prvek v `deque` pro čtení a jiné operace jako`const.`|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje iterátor náhodného přístupu, který má přístup k prvkům v As `deque` **const**a jejich čtení. Deque se zobrazí v obráceném pořadí. Další informace naleznete v tématu [Třída reverse_iterator](../standard-library/reverse-iterator-class.md) .|
|[difference_type](#difference_type)|Typ, který poskytuje rozdíl mezi dvěma iterátory náhodného přístupu, které odkazují na prvky ve stejné `deque`.|
|[iterator](#iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat libovolný prvek v `deque`.|
|[pointer](#pointer)|Typ, který poskytuje ukazatel na prvek v `deque`.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na prvek uložený v `deque`.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat prvek v `deque`. Deque se zobrazí v obráceném pořadí.|
|[size_type](#size_type)|Typ, který počítá počet prvků v `deque`.|
|[value_type](#value_type)|Typ, který představuje datový typ uložený v `deque`.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[assign](#assign)|Vymaže prvky z `deque` a a zkopíruje do cíle `deque`novou sekvenci prvků.|
|[at](#at)|Vrátí odkaz na prvek v zadaném umístění v `deque`.|
|[návrat](#back)|Vrátí odkaz na poslední prvek `deque`.|
|[ifunctiondiscovery](#begin)|Vrátí iterátor náhodného přístupu, který adresuje první prvek v `deque`.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor na první prvek v `deque`.|
|[cend](#cend)|Vrátí **konstantní** iterátor s náhodným přístupem, který odkazuje hned za konec `deque`.|
|[jejich](#clear)|Smaže všechny prvky `deque`.|
|[crbegin](#crbegin)|Vrátí konstantní iterátor s náhodným přístupem k prvnímu prvku v `deque` zobrazení v opačném pořadí.|
|[crend](#crend)|Vrátí konstantní iterátor s náhodným přístupem k prvnímu prvku v `deque` zobrazení v opačném pořadí.|
|[emplace](#emplace)|Vloží prvek sestavený na místo `deque` na zadané pozici.|
|[emplace_back](#emplace_back)|Přidá prvek konstruovaný na konci `deque`.|
|[emplace_front](#emplace_front)|Přidá prvek vytvořený na místo na začátek `deque`.|
|[empty](#empty)|Vrátí **hodnotu true** , `deque` Pokud obsahuje nula prvků a **hodnotu false** , pokud obsahuje jeden nebo více prvků.|
|[účelu](#end)|Vrátí iterátor náhodného přístupu, který odkazuje hned za konec `deque`.|
|[ověřování](#erase)|Odebere prvek nebo rozsah prvků v `deque` zadaném umístění.|
|[dopředu](#front)|Vrátí odkaz na první prvek v `deque`.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objektu, který se používá k `deque`vytvoření.|
|[zadat](#insert)|Vloží prvek, několik prvků nebo rozsah prvků do `deque` zadané pozice.|
|[max_size](#max_size)|Vrátí maximální možnou délku `deque`.|
|[pop_back](#pop_back)|Vymaže element na konci `deque`.|
|[pop_front](#pop_front)|Vymaže element na začátku `deque`.|
|[push_back](#push_back)|Přidá prvek na konec `deque`.|
|[push_front](#push_front)|Přidá prvek na začátek `deque`.|
|[rbegin](#rbegin)|Vrátí iterátor náhodného přístupu k prvnímu prvku v obráceném pořadí `deque`.|
|[rend](#rend)|Vrátí iterátor náhodného přístupu, který odkazuje hned za poslední prvek v obráceném pořadí `deque`.|
|[velikost](#resize)|Určuje novou velikost pro `deque`.|
|[shrink_to_fit](#shrink_to_fit)|Zahodí nadbytečnou kapacitu.|
|[hodnota](#size)|Vrátí počet prvků v `deque`.|
|[swap](#swap)|Vyměňuje prvky dvou `deque`s.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[podnikatel&#91;&#93;](#op_at)|Vrátí odkaz na `deque` prvek na zadané pozici.|
|[operátor =](#op_eq)|Nahradí prvky `deque` kopie jiné `deque`.|

## <a name="allocator_type"></a>allocator_type

Typ, který představuje třídu přidělování pro objekt deque.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type`je synonymum pro parametr `Allocator`šablony.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_allocator](#get_allocator).

## <a name="assign"></a>řadit

Vymaže prvky z deque a zkopíruje novou sadu prvků do cílového deque.

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

*První*\
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány z argumentu deque.

*Posledního*\
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány z argumentu deque.

*Výpočtu*\
Počet kopií prvku vloženého do deque.

*Počítává*\
Hodnota prvku vloženého do deque.

*IList*\
Initializer_list vložené do deque.

### <a name="remarks"></a>Poznámky

Po vymazání `assign` všech stávajících prvků v cílovém deque buď Vloží zadaný rozsah prvků z původní deque nebo z jiného deque do cílového deque, nebo vloží kopie nového prvku zadané hodnoty do cílového deque.

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

## <a name="at"></a>Počínaje

Vrátí odkaz na prvek v zadaném umístění v deque.

```cpp
reference at(size_type pos);

const_reference at(size_type pos) const;
```

### <a name="parameters"></a>Parametry

*POS*\
Dolní index (nebo číslo pozice) prvku, na který se má odkazovat v deque.

### <a name="return-value"></a>Návratová hodnota

Pokud je *POS* větší než velikost deque, `at` vyvolá výjimku.

### <a name="return-value"></a>Návratová hodnota

Pokud `at` je vrácená hodnota přiřazena `const_reference`k, objekt deque nelze změnit. Pokud `at` je vrácená hodnota přiřazena `reference`k, lze objekt deque upravit.

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

## <a name="back"></a>návrat

Vrátí odkaz na poslední prvek deque.

```cpp
reference back();
const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Poslední prvek deque. Pokud je deque prázdné, návratová hodnota není definována.

### <a name="remarks"></a>Poznámky

Pokud `back` je vrácená hodnota přiřazena `const_reference`k, objekt deque nelze změnit. Pokud `back` je vrácená hodnota přiřazena `reference`k, lze objekt deque upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definovaného jako 1 nebo 2 dojde k chybě za běhu, pokud se pokusíte o přístup k elementu v prázdném deque.  Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md) .

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

## <a name="begin"></a>ifunctiondiscovery

Vrátí iterátor adresující první prvek v deque.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor náhodného přístupu, který adresuje první prvek v deque nebo do umístění, který je úspěšný prázdný deque.

### <a name="remarks"></a>Poznámky

Pokud `begin` je vrácená hodnota přiřazena `const_iterator`k, objekt deque nelze změnit. Pokud `begin` je vrácená hodnota přiřazena `iterator`k, lze objekt deque upravit.

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

## <a name="cbegin"></a>cbegin

Vrátí **konstantní** iterátor, který adresuje první prvek v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor  náhodného přístupu const, který odkazuje na první prvek rozsahu nebo umístění hned za konec prázdného rozsahu (pro prázdný rozsah `cbegin() == cend()`).

### <a name="remarks"></a>Poznámky

V případě návratové hodnoty `cbegin`nelze prvky v rozsahu upravovat.

Tuto členskou funkci můžete použít místo `begin()` členské funkce k zajištění, že návratová hodnota je. `const_iterator` Obvykle se používá ve spojení s klíčovým slovem srážky typu [auto](../cpp/auto-cpp.md) , jak je znázorněno v následujícím příkladu. V příkladu zvažte `Container` , že jde o upravitelný ( `const`jiný) kontejner libovolného druhu, který podporuje `begin()` a `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

Vrátí **konstantní** iterátor, který adresuje umístění hned za poslední prvek v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor pro náhodný přístup, který ukazuje přesně za konec rozsahu.

### <a name="remarks"></a>Poznámky

`cend`slouží k otestování, zda iterátor prošl na konci rozsahu.

Tuto členskou funkci můžete použít místo `end()` členské funkce k zajištění, že návratová hodnota je. `const_iterator` Obvykle se používá ve spojení s klíčovým slovem srážky typu [auto](../cpp/auto-cpp.md) , jak je znázorněno v následujícím příkladu. `Container` V příkladu zvažte, že se jedná o upravitelný kontejner (nekonstantní) jakýkoli druh, který podporuje `end()` a. `cend()`

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Hodnota vrácená `cend` by neměla být zpětně odkazovaná.

## <a name="clear"></a>jejich

Smaže všechny prvky deque.

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

## <a name="const_iterator"></a>const_iterator

Typ, který poskytuje iterátor náhodného přístupu, který může přistupovat k elementu **const** a číst ho v deque.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít pro úpravu hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [zpět](#back).

## <a name="const_pointer"></a>const_pointer

Poskytuje ukazatel na prvek **const** v deque.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít pro úpravu hodnoty prvku. [Iterátor](#iterator) se častěji používá pro přístup k elementu deque.

## <a name="const_reference"></a>const_reference

Typ, který poskytuje odkaz na prvek **const** uložený v deque pro čtení a provádění operací **const** .

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

Typ `const_reference` nelze použít pro úpravu hodnoty prvku.

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

## <a name="const_reverse_iterator"></a>const_reverse_iterator

Typ, který poskytuje iterátor náhodného přístupu, který může číst libovolný  element const v deque.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a používá se k iterování přes deque v obráceném pořadí.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat iterátor, najdete v příkladu pro [rbegin](#rbegin) .

## <a name="crbegin"></a>crbegin –

Vrátí konstantní iterátor na první prvek v obráceném dequeě.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní iterátor s náhodným přístupem, který adresuje první prvek v obráceném [deque](../standard-library/deque-class.md) nebo řeší, co byl poslední prvek v neobráceném `deque`pořadí.

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `crbegin` `deque` nelze objekt upravit.

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

## <a name="crend"></a>crend

Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v obráceném dequeě.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor reverzního náhodného přístupu, který adresuje umístění následující po posledním prvku v obráceném [deque](../standard-library/deque-class.md) (umístění, které předchází prvnímu prvku v neobráceném deque).

### <a name="remarks"></a>Poznámky

`crend`se používá s obráceným znaménkem `deque` jako [Array:: cend](../standard-library/array-class-stl.md#cend) `deque`se používá s.

V případě návratové hodnoty `crend` (vhodně sníženo) `deque` objekt nelze změnit.

`crend`dá se použít k otestování, jestli reverzní iterátor dosáhl konce jeho deque.

Hodnota vrácená `crend` by neměla být zpětně odkazovaná.

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

## <a name="deque"></a>deque

Sestaví deque konkrétní velikosti nebo pomocí prvků konkrétní hodnoty nebo pomocí konkrétního přidělujícího modulu nebo jako kopie celého nebo části nějakého jiného deque.

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

*VŠ*\
Třída alokátoru, která se má použít s tímto objektem.

*Výpočtu*\
Počet prvků v konstruované deque

*Počítává*\
Hodnota prvků v konstruované deque

*Kliknutím*\
Deque, ze kterého má být vytvořená deque kopie.

*První*\
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*Posledního*\
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

*IList*\
Initializer_list, který se má zkopírovat

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt přidělování (*Al*) a inicializují deque.

První dva konstruktory určují prázdné počáteční deque; Druhá také určuje typ přidělování (`_Al`), který se má použít.

Třetí konstruktor určuje opakování zadaného počtu (`count`) prvků výchozí hodnoty pro třídu `Type`.

Čtvrtý a pátý konstruktor určuje opakování (*počet*) prvků hodnoty `val`.

Šestý konstruktor určuje kopii pravého dequeu .

Sedmý a osmá konstruktory kopírují rozsah `[First, Last)` deque.

Sedmý konstruktor přesune deque *doprava*.

Osmá konstruktor kopíruje obsah objektu initializer_list.

Žádný z konstruktorů neprovede žádná dočasná přerozdělení.

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

## <a name="difference_type"></a>difference_type

Typ, který poskytuje rozdíl mezi dvěma iterátory, které odkazují na prvky v rámci stejného deque.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` Lze také popsat jako počet prvků mezi dvěma ukazateli.

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

## <a name="emplace"></a>emplace

Vloží prvek sestavený na místo do deque na zadané pozici.

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozice v [deque](../standard-library/deque-class.md) , kde je vložen první prvek.

*počítává*\
Hodnota prvku vloženého do `deque`.

### <a name="return-value"></a>Návratová hodnota

Funkce vrátí iterátor, který odkazuje na pozici, kam byl nový prvek vložen do objektu deque.

### <a name="remarks"></a>Poznámky

Jakákoli operace vložení může být náročná, `deque` najdete v ní diskuzi o `deque` výkonu.

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

## <a name="emplace_back"></a>emplace_back

Přidá prvek vytvořený na místo na konci deque.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Parametry

*počítává*\
Prvek přidaný na konec [deque](../standard-library/deque-class.md).

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

## <a name="emplace_front"></a>emplace_front

Přidá prvek vytvořený na místo na konci deque.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*počítává*\
Prvek přidaný na začátek [deque](../standard-library/deque-class.md).

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

## <a name="empty"></a>obsahovat

Testuje, zda je deque prázdné.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je deque prázdné; **false** , pokud deque není prázdný.

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

## <a name="end"></a>účelu

Vrátí iterátor, který adresuje umístění následující po posledním prvku v objektu deque.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor náhodného přístupu, který adresuje umístění následující po posledním prvku v deque. Pokud je deque prázdné, potom deque:: end = = deque:: begin.

### <a name="remarks"></a>Poznámky

`end`slouží k otestování, zda iterátor dosáhl konce jeho deque.

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

## <a name="erase"></a>ověřování

Odebere prvek nebo rozsah prvků v objektu deque ze zadané pozice.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozice prvku, který má být odebrán z deque.

*první*\
Pozice prvního prvku byla odebrána z deque.

*posledního*\
Pozice hned za posledním prvkem odebraným z deque.

### <a name="return-value"></a>Návratová hodnota

Iterátor náhodného přístupu, který určuje první prvek zbývající za odebranými prvky, nebo ukazatel na konec deque, pokud žádný takový prvek neexistuje.

### <a name="remarks"></a>Poznámky

`erase`nikdy nevyvolává výjimku.

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

## <a name="front"></a>dopředu

Vrátí odkaz na první prvek v deque.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je deque prázdné, vrácení zpět není definováno.

### <a name="remarks"></a>Poznámky

Pokud `front` je vrácená hodnota přiřazena `const_reference`k, objekt deque nelze změnit. Pokud `front` je vrácená hodnota přiřazena `reference`k, lze objekt deque upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definovaného jako 1 nebo 2 dojde k chybě za běhu, pokud se pokusíte o přístup k elementu v prázdném deque.  Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md) .

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

## <a name="get_allocator"></a>get_allocator

Vrátí kopii objektu přidělování, která se používá k vytvoření deque.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný dequeem.

### <a name="remarks"></a>Poznámky

Přidělování pro třídu deque určují, jak Třída spravuje úložiště. Výchozí přidělující třídy kontejnerů C++ standardní knihovny jsou dostačující pro většinu programovacích potřeb. Psaní a používání vlastního třídy přidělování je pokročilým C++ tématem.

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

## <a name="insert"></a>zadat

Vloží prvek nebo počet prvků nebo rozsah prvků do deque na zadané pozici.

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

*,* \
Pozice v cílovém deque, kde je vložen první prvek.

*Počítává*\
Hodnota prvku vloženého do deque.

*Výpočtu*\
Počet prvků vložených do deque.

*První*\
Pozice prvního prvku v rozsahu prvků v argumentu deque, který má být zkopírován.

*Posledního*\
Pozice prvního prvku mimo rozsah prvků v argumentu deque, který má být zkopírován.

*IList*\
Initializer_list prvků, které mají být vloženy.

### <a name="return-value"></a>Návratová hodnota

První dvě funkce INSERT Vrátí iterátor, který odkazuje na pozici, kam byl nový prvek vložen do deque.

### <a name="remarks"></a>Poznámky

Jakákoli operace vložení může být náročná.

## <a name="iterator"></a>iterátor

Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat libovolný prvek v deque.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

Typ `iterator` lze použít pro úpravu hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začátek](#begin).

## <a name="max_size"></a>max_size

Vrátí maximální délku deque.

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

## <a name="op_at"></a>operator [] – operátor

Vrátí odkaz na element deque na zadané pozici.

```cpp
reference operator[](size_type pos);

const_reference operator[](size_type pos) const;
```

### <a name="parameters"></a>Parametry

*POS*\
Pozice prvku deque, na který se má odkazovat

### <a name="return-value"></a>Návratová hodnota

Odkaz na element, jehož pozice je určena v argumentu. Pokud je zadaná pozice větší než velikost deque, výsledek není definován.

### <a name="remarks"></a>Poznámky

Pokud `operator[]` je vrácená hodnota přiřazena `const_reference`k, objekt deque nelze změnit. Pokud `operator[]` je vrácená hodnota přiřazena `reference`k, lze objekt deque upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definovaného jako 1 nebo 2 dojde k chybě za běhu, pokud se pokusíte o přístup k prvku mimo hranice deque.  Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md) .

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

## <a name="op_eq"></a>operátor =

Nahradí prvky tohoto deque pomocí elementů z jiného deque.

```cpp
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Deque, který poskytuje nový obsah.

### <a name="remarks"></a>Poznámky

První přepsání zkopíruje prvky do tohoto deque napravo od zdroje přiřazení. Druhé přepsání přesune prvky do tohoto deque zprava .

Prvky, které jsou obsaženy v tomto deque před spuštěním operátoru, se odeberou.

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

## <a name="pointer"></a>ukazatele

Poskytuje ukazatel na prvek v [deque](../standard-library/deque-class.md).

```unstlib
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze použít pro úpravu hodnoty prvku. [Iterátor](#iterator) se častěji používá pro přístup k elementu deque.

## <a name="pop_back"></a>pop_back

Odstraní prvek na konci deque.

```cpp
void pop_back();
```

### <a name="remarks"></a>Poznámky

Poslední prvek nesmí být prázdný. `pop_back`nikdy nevyvolává výjimku.

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

## <a name="pop_front"></a>pop_front

Odstraní element na začátku deque.

```cpp
void pop_front();
```

### <a name="remarks"></a>Poznámky

První prvek nesmí být prázdný. `pop_front`nikdy nevyvolává výjimku.

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

## <a name="push_back"></a>push_back

Přidá prvek na konec deque.

```cpp
void push_back(const Type& val);

void push_back(Type&& val);
```

### <a name="parameters"></a>Parametry

*počítává*\
Prvek přidaný na konec deque.

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, deque zůstane beze změny a výjimka je znovu vyvolána.

## <a name="push_front"></a>push_front

Přidá prvek na začátek deque.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*počítává*\
Prvek přidaný na začátek deque.

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, deque zůstane beze změny a výjimka je znovu vyvolána.

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

## <a name="rbegin"></a>rbegin

Vrátí iterátor na první prvek v obráceném dequeě.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní iterátor s náhodným přístupem, který adresuje první prvek v obráceném deque nebo řeší, co byl poslední prvek v neobráceném deque.

### <a name="remarks"></a>Poznámky

`rbegin`se používá s obráceným deque stejně jako [Begin](#begin) se používá s deque.

Pokud `rbegin` je vrácená hodnota přiřazena `const_reverse_iterator`k, objekt deque nelze změnit. Pokud `rbegin` je vrácená hodnota přiřazena `reverse_iterator`k, lze objekt deque upravit.

`rbegin`dá se použít k iteraci deque dozadu.

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

## <a name="reference"></a>odkaz

Typ, který poskytuje odkaz na prvek uložený v objektu deque.

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

## <a name="rend"></a>rend

Vrátí iterátor, který adresuje umístění následující po posledním prvku v obráceném dequeě.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor náhodného přístupu, který adresuje umístění následující po posledním prvku v obráceném deque (umístění, které předchází prvnímu prvku v neobráceném deque).

### <a name="remarks"></a>Poznámky

`rend`se používá s obráceným deque jako [End](#end) se používá s deque.

Pokud `rend` je vrácená hodnota přiřazena `const_reverse_iterator`k, objekt deque nelze změnit. Pokud `rend` je vrácená hodnota přiřazena `reverse_iterator`k, lze objekt deque upravit.

`rend`dá se použít k otestování, jestli reverzní iterátor dosáhl konce jeho deque.

Hodnota vrácená `rend` by neměla být zpětně odkazovaná.

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

## <a name="resize"></a>velikost

Určuje novou velikost pro deque.

```cpp
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Parametry

*_Newsize*\
Nová velikost deque

*počítává*\
Hodnota nových prvků, které mají být přidány do deque, pokud je nová velikost větší než původní velikost. Pokud je hodnota vynechána, nové prvky jsou přiřazeny výchozí hodnotě pro třídu.

### <a name="remarks"></a>Poznámky

Pokud je velikost deque menší než požadovaná velikost, *_Newsize*prvky se přidají do deque, dokud nedosáhne požadované velikosti.

Pokud je velikost deque větší než požadovaná velikost, prvky nejbližší konci deque jsou odstraněny, dokud deque nedosáhne velikosti *_Newsize*.

Pokud je aktuální velikost deque stejná jako požadovaná velikost, není provedena žádná akce.

[Velikost](#size) odráží aktuální velikost deque.

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

## <a name="reverse_iterator"></a>reverse_iterator

Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat prvek v obráceném dequeě.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iterování přes deque.

### <a name="example"></a>Příklad

Podívejte se na příklad pro rbegin.

## <a name="shrink_to_fit"></a>shrink_to_fit

Zahodí nadbytečnou kapacitu.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Poznámky

Neexistuje žádný přenosný způsob, jak určit, `shrink_to_fit` jestli omezuje úložiště, které [deque](../standard-library/deque-class.md)používá.

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

## <a name="size"></a>hodnota

Vrátí počet prvků v deque.

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

## <a name="size_type"></a>size_type

Typ, který počítá počet prvků v deque.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [Velikost](#size).

## <a name="swap"></a>adresu

Vyměňuje prvky dvou deques.

```cpp
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Deque poskytuje prvky, které mají být měněny, nebo deque, jejichž prvky mají být vyměňovány pomocí těch deque `left`.

*zbývá*\
Deque, jehož prvky mají být vyměňovány pomocí deque *práva*.

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

## <a name="value_type"></a>value_type

Typ, který představuje datový typ uložený ve deque.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Poznámky

`value_type`je synonymum pro parametr `Type`šablony.

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

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
