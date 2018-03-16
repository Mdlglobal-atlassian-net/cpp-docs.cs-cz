---
title: "deque – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 88ce199617f0628ccb7e022581cd52d83d82e2ac
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="deque-class"></a>deque – třída
Uspořádá elementy daného typu v lineární uspořádání a jako vektor, umožňuje vysoká rychlost náhodného přístup k žádné elementu a efektivní vkládání a odstraňování za kontejnerem. Ale na rozdíl od vektor `deque` třída také podporuje efektivní vkládání a odstraňování vpředu kontejneru.  
  
## <a name="syntax"></a>Syntaxe  
  
```unstlib  
template <class Type, class Allocator =allocator<Type>>  
class deque  
```  
  
#### <a name="parameters"></a>Parametry  
 `Type`  
 Datový typ elementu k uložení do deque.  
  
 `Allocator`  
 Typ, který představuje uložené allocator objekt, který zapouzdřuje informace o přidělení a zrušení přidělení paměti deque. Tento argument je volitelný a výchozí hodnota je **allocator\<typ > ***.*  
  
## <a name="remarks"></a>Poznámky  
 Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. [Vektory](../standard-library/vector-class.md) by měl být upřednostňovaný kontejneru pro správu sekvenci, když je náhodný přístup k libovolného elementu a vložení nebo odstranění elementů jsou pouze požadované na konci pořadí. Výkon kontejneru seznamu je nadřízená při efektivní vložení a odstranění (v čase konstantní) v libovolném umístění v rámci pořadí je třeba šetřit. Tyto operace uprostřed sekvenci vyžadují element kopie a přiřazení úměrná počet elementů v pořadí (lineární čas).  
  
 Deque přerozdělení dojde, pokud musíte vložit nebo Vymazat elementy sekvence členské funkce:  
  
-   Pokud element budou vložena do prázdné sekvenci, nebo pokud chcete nechat prázdné sekvenci vymazáním element, pak iterátory dříve vrácený [začít](#begin) a [end](#end) zneplatní.  
  
-   Pokud je element vložit na první pozici deque, pak se všechny iterátory, ale žádné odkazy, které určit existující prvky se zneplatní.  
  
-   Pokud je element vložit na konci deque, pak [end](#end) a všechny iterátory, ale žádné odkazy, které určit existující prvky se zneplatní.  
  
-   Pokud element vymazáním vpředu deque pouze zneplatní iterator a odkazy na vymazaných element.  
  
-   Pokud je posledním elementem vymazat z konce deque, pouze tento iterator do konečné elementu a odkazy na tento element vymazaných se zneplatní.  
  
 Vložení nebo vymazání element zruší, jinak hodnota všechny iterátory a odkazy.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[deque](#deque)|Vytvoří `deque.` několik konstruktorů jsou poskytnutý pro nastavení obsah nové `deque` různými způsoby: prázdný; načtená zadaný počet prázdné prvky; obsah přesunuté nebo zkopírované z jiného `deque`; obsahu nebo přesunout pomocí iterator; a jeden element zkopírují `deque` `count` časy. Některé z konstruktorů povolit pomocí vlastní `allocator` k vytváření prvků.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Typ, který reprezentuje `allocator` třídy pro `deque` objektu.|  
|[const_iterator](#const_iterator)|Typ, který poskytuje iterator náhodný přístup, který může přistupovat a načítat elementů v `deque` jako `const`|  
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na prvek v `deque` jako `const.`|  
|[const_reference](#const_reference)|Typ, který obsahuje odkaz na element v `deque` pro čtení a další operace jako `const.`|  
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje iterator náhodný přístup, který může přistupovat a načítat elementů v `deque` jako `const`. Deque je zobrazit pozpátku. Další informace najdete v tématu [reverse_iterator – třída](../standard-library/reverse-iterator-class.md)|  
|[difference_type](#difference_type)|Typ, který poskytuje rozdíl mezi dvěma iterátory náhodný přístup, které odkazují na elementy ve stejné `deque`.|  
|[iterator](#iterator)|Typ, který poskytuje iterator náhodný přístup, který může číst nebo upravovat libovolný element v `deque`.|  
|[pointer](#pointer)|Typ, který poskytuje ukazatel na prvek v `deque`.|  
|[reference](#reference)|Typ, který obsahuje odkaz na element uložené v `deque`.|  
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje náhodný přístup iterator, které můžou číst nebo upravte element v `deque`. Deque je zobrazit v obráceném pořadí.|  
|[size_type](#size_type)|Typ, který udává počet elementů v `deque`.|  
|[value_type](#value_type)|Typ, který představuje typ data uložená v `deque`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[assign](#assign)|Vymaže elementy z `deque` a zkopíruje nové pořadí elementů k cíli `deque`.|  
|[at](#at)|Vrátí odkaz na element v zadaném umístění v `deque`.|  
|[zpět](#back)|Vrátí odkaz na poslední prvek `deque`.|  
|[Začátek](#begin)|Vrátí náhodným přístupem iterator adresování prvním elementem v `deque`.|  
|[cbegin](#cbegin)|Vrátí const iterator prvním elementem v `deque`.|  
|[cend –](#cend)|Vrátí náhodný přístup `const` iterator, který odkazuje právě přesahuje za konec `deque`.|  
|[clear](#clear)|Vymaže všechny elementy `deque`.|  
|[crbegin](#crbegin)|Vrátí const iterator náhodným přístupem na prvním elementem v `deque` zobrazit v obráceném pořadí.|  
|[crend –](#crend)|Vrátí const iterator náhodným přístupem na prvním elementem v `deque` zobrazit v obráceném pořadí.|  
|[emplace –](#emplace)|Vloží element sestavený na místě do `deque` na zadané pozici.|  
|[emplace_back](#emplace_back)|Přidá element sestavený na místě na konec `deque`.|  
|[emplace_front](#emplace_front)|Přidá element sestavený opatření ke spuštění `deque`.|  
|[prázdný](#empty)|Vrátí `true` Pokud `deque` obsahuje nulovým počtem elementů a `false` pokud obsahuje jeden či více elementů.|  
|[End](#end)|Vrátí náhodný přístup iterator této body právě přesahuje za konec `deque`.|  
|[vymazání](#erase)|Odebere element nebo rozsah elementů v `deque` ze zadaných pozic.|  
|[Přední](#front)|Vrátí odkaz na prvním elementem v `deque`.|  
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objekt, který se používá pro konstrukci `deque`.|  
|[insert](#insert)|Vloží elementu, několik elementy nebo rozsahu prvků do `deque` na zadané pozici.|  
|[max_size](#max_size)|Vrátí maximální možné délku `deque`.|  
|[pop_back](#pop_back)|Vymaže prvek na konec `deque`.|  
|[pop_front](#pop_front)|Vymaže prvek na začátek `deque`.|  
|[push_back](#push_back)|Přidá prvek na konec `deque`.|  
|[push_front](#push_front)|Přidá prvek na začátek `deque`.|  
|[rbegin](#rbegin)|Vrátí iterator náhodný přístup na první prvek v odstínech `deque`.|  
|[rend –](#rend)|Vrátí iterator náhodný přístup tohoto body bezprostředně za posledním prvkem v odstínech `deque`.|  
|[resize](#resize)|Určuje novou velikost `deque`.|  
|[shrink_to_fit](#shrink_to_fit)|Zahození přebytečnou kapacitou.|  
|[Velikost](#size)|Vrátí počet prvků v `deque`.|  
|[swap](#swap)|Výměny dva elementy `deque`s.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operator&#91;&#93;](#op_at)|Vrátí odkaz na `deque` element na zadané pozici.|  
|[operator=](#op_eq)|Nahradí prvků `deque` kopii jiného `deque`.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví**: \<deque >  
  
##  <a name="allocator_type"></a>  deque::allocator_type  
 Typ, který reprezentuje allocator – třída objektu deque.  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 **allocator_type –** je synonymum pro parametr šablony **Allocator**.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [get_allocator –](#get_allocator).  
  
##  <a name="assign"></a>  deque::Assign  
 Vymaže elementy z deque a zkopíruje novou sadu elementů deque cíl.  
  
```  
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
 `First`  
 Pozice první prvek v rozsahu elementy zkopírovány z argument deque.  
  
 `Last`  
 Pozice první prvek mimo rozsah elementy zkopírovány z argument deque.  
  
 `Count`  
 Počet kopií vkládání do deque elementu.  
  
 `Val`  
 Hodnota elementu vkládání do deque.  
  
 `IList`  
 Initializer_list vkládání do deque.  
  
### <a name="remarks"></a>Poznámky  
 Po existující prvky v cílové deque jsou vymazány, `assign` buď vloží zadaný rozsah elementů z původní deque nebo z některé jiné deque do cílové deque nebo vložení kopie nového elementu zadané hodnoty do deque cíl.  
  
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
  
##  <a name="at"></a>  deque::AT  
 Vrátí odkaz na element v zadaném umístění deque.  
  
```  
reference at(size_type pos);

const_reference at(size_type pos) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Dolní index (nebo číslo pozice) elementu tak, aby odkazovaly v deque.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud `pos` je větší než velikost deque, **v** vyvolá výjimku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud vrátí hodnotu, která **v** je přiřazena k `const_reference`, deque objekt nelze změnit. Pokud vrátí hodnotu, která **v** je přiřazena k **odkaz**, deque objekt můžete upravit.  
  
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
  
##  <a name="back"></a>  deque::back  
 Vrátí odkaz na posledním prvkem deque.  
  
```  
reference back();
const_reference back() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Posledním prvkem deque. Pokud deque je prázdná, není definován návratovou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vrátí hodnotu, která **zpět** je přiřazena k `const_reference`, deque objekt nelze změnit. Pokud vrátí hodnotu, která **zpět** je přiřazena k **odkaz**, deque objekt můžete upravit.  
  
 Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definován jako 1 nebo 2, Chyba za běhu dojde při pokusu o přístup k elementu v prázdný deque.  V tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md) Další informace.  
  
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
  
##  <a name="begin"></a>  deque::begin  
 Vrátí iterator adresování prvním elementem v deque.  
  
```  
const_iterator begin() const;
iterator begin();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresování prvním elementem v deque nebo do umístění úspěšné prázdný deque iterator náhodný přístup.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vrátí hodnotu, která **začít** je přiřazena k `const_iterator`, deque objekt nelze změnit. Pokud vrátí hodnotu, která **začít** je přiřazena k **iterator**, objekt deque je možné upravit.  
  
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
  
##  <a name="cbegin"></a>  deque::cbegin  
 Vrátí `const` iterator, která řeší prvním elementem v rozsahu.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `const` iterator náhodný přístup, který odkazuje na první prvek rozsahu nebo umístění právě přesahuje za konec prázdného rozsahu (pro prázdného rozsahu, `cbegin() == cend()`).  
  
### <a name="remarks"></a>Poznámky  
 S návratovou hodnotou `cbegin`, nemůže být upravena elementů v rozsahu.  
  
 Můžete použít tuto funkci člen místě `begin()` – členská funkce zaručit, že je návratovou hodnotu `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) odvození – klíčové slovo, zadejte, jak je znázorněno v následujícím příkladu. V příkladu, vezměte v úvahu `Container` upravitelná (jinou hodnotu než `const`) kontejneru libovolného typu, který podporuje `begin()` a `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a>  deque::cend  
 Vrátí `const` iterator, která řeší umístění bezprostředně za posledním prvkem v rozsahu.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor pro náhodný přístup, který ukazuje přesně za konec rozsahu.  
  
### <a name="remarks"></a>Poznámky  
 `cend` slouží k ověření, zda iterovat uplynutí konec její rozsah.  
  
 Můžete použít tuto funkci člen místě `end()` – členská funkce zaručit, že je návratovou hodnotu `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) odvození – klíčové slovo, zadejte, jak je znázorněno v následujícím příkladu. V příkladu, vezměte v úvahu `Container` upravitelná (jinou hodnotu než `const`) kontejneru libovolného typu, který podporuje `end()` a `cend()`.  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 Hodnoty vrácené `cend` by neměl být vyhodnoceny odkazy.  
  
##  <a name="clear"></a>  deque::clear  
 Vymaže všechny elementy deque.  
  
```  
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
  
##  <a name="const_iterator"></a>  deque::const_iterator  
 Typ, který poskytuje iterator náhodný přístup, který může přistupovat a načítat **const** element v deque.  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ `const_iterator` nelze použít k úpravě hodnota elementu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [zpět](#back).  
  
##  <a name="const_pointer"></a>  deque::const_pointer  
 Poskytuje odkazy `const` element v deque.  
  
```
typedef typename Allocator::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ `const_pointer` nelze použít k úpravě hodnota elementu. [Iterator](#iterator) se běžně používá pro přístup deque elementu.  
  
##  <a name="const_reference"></a>  deque::const_reference  
 Typ, který obsahuje odkaz na **const** element uložené v deque pro čtení a provádění **const** operace.  
  
```  
typedef typename Allocator::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ `const_reference` nelze použít k úpravě hodnota elementu.  
  
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
  
##  <a name="const_reverse_iterator"></a>  deque::const_reverse_iterator  
 Typ, který poskytuje iterator náhodný přístup, který může číst všechny **const** element v deque.  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ `const_reverse_iterator` nelze změnit hodnotu elementu a slouží k iteraci v rámci deque pozpátku.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [rbegin –](#rbegin) příklad toho, jak deklarace a pomocí iterace.  
  
##  <a name="crbegin"></a>  deque::crbegin  
 Vrátí const iterator prvním elementem v invertovaných deque.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Const reverse náhodný přístup iterator adresování prvním elementem v odstínech [deque](../standard-library/deque-class.md) nebo řešení, co je posledním prvkem v unreversed `deque`.  
  
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
  
##  <a name="crend"></a>  deque::crend  
 Vrátí const iterator, která řeší úspěšné posledním prvkem v invertovaných deque umístění.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Const reverse iterator náhodný přístup, která řeší umístění úspěšné posledním prvkem v odstínech [deque](../standard-library/deque-class.md) (umístění, které měl před prvním elementem v unreversed deque).  
  
### <a name="remarks"></a>Poznámky  
 `crend` se používá s odstínech `deque` stejně jako [array::cend](../standard-library/array-class-stl.md#cend) se používá s `deque`.  
  
 S návratovou hodnotou `crend` (vhodně odečte), `deque` objekt nelze změnit.  
  
 `crend` dá se použít k testování na tom, jestli zpětné iterator dosáhne konce své deque.  
  
 Hodnoty vrácené `crend` by neměl být vyhodnoceny odkazy.  
  
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
  
##  <a name="deque"></a>  deque::deque  
 Vytvoří deque určité velikosti, nebo u elementů na určitou hodnotu, nebo s konkrétní přidělování nebo jako kopii všech nebo součástí některých jiných deque.  
  
```  
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
  
|||  
|-|-|  
|Parametr|Popis|  
|`Al`|Třída alokátoru, která se má použít s tímto objektem.|  
|`Count`|Počet elementů v vytvořený deque.|  
|`Val`|Hodnota elementů v vytvořený deque.|  
|`Right`|Deque, které má být kopie vytvořený deque.|  
|`First`|Pozice první prvek v rozsahu elementy, které se mají zkopírovat.|  
|`Last`|Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.|  
|`IList`|Initializer_list ke kopírování.|  
  
### <a name="remarks"></a>Poznámky  
 Všechny konstruktory uložit objekt allocator ( `Al`) a inicializace deque.  
  
 První dva konstruktory, zadejte prázdnou počáteční deque; druhý také určuje typ allocator ( `_Al`) má být použit.  
  
 Třetí konstruktor určuje opakování určeného čísla ( `count`) elementů výchozí hodnota pro třídu `Type`.  
  
 Konstruktory čtvrté a páté zadejte opakování ( `Count`) elementy hodnoty `val`.  
  
 Šesté konstruktor určuje kopii deque `Right`.  
  
 Konstruktory sedmého a osmého zkopírujte rozsahu `[First, Last)` z deque.  
  
 Sedmého konstruktor přesune deque `Right`.  
  
 Osmého konstruktor zkopíruje obsah initializer_list.  
  
 Žádná z konstruktorů provést všechny dočasné přerozdělení.  
  
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
  
##  <a name="difference_type"></a>  deque::difference_type  
 Typ, který poskytuje rozdíl mezi dvěma iterátory, které odkazují na elementů v rámci stejné deque.  
  
```  
typedef typename Allocator::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 A `difference_type` lze také popsat jako počet elementů mezi dvěma ukazatele.  
  
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
  
##  <a name="emplace"></a>  deque::emplace  
 Vloží element sestavený na místě do deque na zadané pozici.  
  
```  
iterator emplace(
    const_iterator _Where,  
    Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`_Where`|Pozice v [deque](../standard-library/deque-class.md) vloženy první prvek.|  
|`val`|Hodnota elementu vkládání do `deque`.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Funkce vrátí hodnotu iterátor, který odkazuje na pozici, kde byl nového elementu vložit do deque.  
  
### <a name="remarks"></a>Poznámky  
 Všechny operace vložení může být nákladné naleznete v tématu `deque` diskuzi o `deque` výkonu.  
  
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
  
##  <a name="emplace_back"></a>  deque::emplace_back  
 Přidá element v místě na konec deque zkonstruovat.  
  
```  
void emplace_back(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`val`|Prvek přidán na konec [deque](../standard-library/deque-class.md).|  
  
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
  
##  <a name="emplace_front"></a>  deque::emplace_front  
 Přidá element v místě na konec deque zkonstruovat.  
  
```  
void emplace_front(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`val`|Element přidat na začátek [deque](../standard-library/deque-class.md).|  
  
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
  
##  <a name="empty"></a>  deque::Empty  
 Testy, pokud deque je prázdný.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud deque je prázdná. **false** Pokud deque není prázdná.  
  
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
  
##  <a name="end"></a>  deque::end  
 Vrátí iterátor, který řeší úspěšné posledním prvkem v deque umístění.  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator náhodný přístup, která řeší úspěšné posledním prvkem v deque umístění. Pokud deque je prázdný, deque::end == deque::begin.  
  
### <a name="remarks"></a>Poznámky  
 **end** slouží k otestování, jestli iterovat dosáhne konce své deque.  
  
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
  
##  <a name="erase"></a>  deque::Erase  
 Odebere element nebo rozsah elementů v deque ze zadaných pozic.  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```  
  
### <a name="parameters"></a>Parametry  
 `_Where`  
 Pozice elementu, který má být odebrán z deque.  
  
 `first`  
 Pozice první prvek odebrán z deque.  
  
 `last`  
 Pozice bezprostředně za posledním elementem odebrán z deque.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator náhodný přístup, který určuje první prvek zbývající nad rámec všechny elementy odebrána, nebo odkazy na konec deque, pokud neexistuje žádný takový prvek.  
  
### <a name="remarks"></a>Poznámky  
 **Vymazat** nikdy vyvolá výjimku.  
  
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
  
##  <a name="front"></a>  deque::front  
 Vrátí odkaz na prvním elementem v deque.  
  
```  
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud deque je prázdná, návratový není definován.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vrátí hodnotu, která `front` je přiřazena k `const_reference`, deque objekt nelze změnit. Pokud vrátí hodnotu, která `front` je přiřazena k **odkaz**, deque objekt můžete upravit.  
  
 Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definován jako 1 nebo 2, Chyba za běhu dojde při pokusu o přístup k elementu v prázdný deque.  V tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md) Další informace.  
  
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
  
##  <a name="get_allocator"></a>  deque::get_allocator  
 Vrátí kopii allocator objekt použitý k vytvoření deque.  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Allocator používané deque.  
  
### <a name="remarks"></a>Poznámky  
 Alokátorů pro třídu deque zadejte, jak třída spravuje úložiště. Alokátorů výchozí součástí standardní knihovna C++ – třídy kontejnerů postačí pro většinu programovacích potřeb. Psaní a pomocí vlastní allocator – třída je rozšířená C++.  
  
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
  
##  <a name="insert"></a>  deque::Insert  
 Vloží elementu nebo počet elementů nebo rozsah elementů do deque na zadané pozici.  
  
```  
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
  
|||  
|-|-|  
|Parametr|Popis|  
|`Where`|Pozice v deque cíl, kde je první prvek vložit.|  
|`Val`|Hodnota elementu vkládání do deque.|  
|`Count`|Počet elementů vkládání do deque.|  
|`First`|Pozice první prvek v rozsahu elementů v deque argument, který se má zkopírovat.|  
|`Last`|Pozice první prvek mimo rozsah elementů v deque argument, který se má zkopírovat.|  
|`IList`|Initializer_list elementů k vložení.|  
  
### <a name="return-value"></a>Návratová hodnota  
 První dva vložení funkce vrátí iterátor, který odkazuje na pozici, kde byl nového elementu vložit do deque.  
  
### <a name="remarks"></a>Poznámky  
 Všechny operace vložení může být náročná.  
  
##  <a name="iterator"></a>  deque::iterator  
 Typ, který poskytuje iterator náhodný přístup, který může číst nebo upravovat libovolný element v deque.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ **iterator** lze upravit hodnotu elementu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [začít](#begin).  
  
##  <a name="max_size"></a>  deque::max_size  
 Vrátí maximální délka deque.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální možné délku deque.  
  
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
  
##  <a name="op_at"></a>  deque::Operator]  
 Vrátí odkaz na element deque na zadané pozici.  
  
```  
reference operator[](size_type pos);

const_reference operator[](size_type pos) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Pozice elementu deque bude odkazovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na element, jejíž pozice je zadána v argumentu. Pokud je větší než velikost deque pozice zadána, výsledkem nedefinovaný.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vrátí hodnotu, která `operator[]` je přiřazena k `const_reference`, deque objekt nelze změnit. Pokud vrátí hodnotu, která `operator[]` je přiřazena k **odkaz**, deque objekt můžete upravit.  
  
 Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definován jako 1 nebo 2, Chyba za běhu dojde při pokusu o přístup k elementu mimo hranice deque.  V tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md) Další informace.  
  
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
  
##  <a name="op_eq"></a>  deque::Operator =  
 Nahradí elementy tento deque pomocí elementů z jiné deque.  
  
```  
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`right`|Deque, která poskytuje nový obsah.|  
  
### <a name="remarks"></a>Poznámky  
 První přepsání zkopíruje prvky na této deque z `right`, zdroj přiřazení. Druhý přepsání přesune prvky na této deque z `right`.  
  
 Elementy, které jsou součástí této deque před provedením operátor se odeberou.  
  
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
  
##  <a name="pointer"></a>  deque::Pointer  
 Poskytuje ukazatel na prvek v [deque](../standard-library/deque-class.md).  
  
```unstlib  
typedef typename Allocator::pointer pointer;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ **ukazatel** lze upravit hodnotu elementu. [Iterator](#iterator) se běžně používá pro přístup deque elementu.  
  
##  <a name="pop_back"></a>  deque::pop_back  
 Odstraní prvek na konec deque.  
  
```  
void pop_back();
```  
  
### <a name="remarks"></a>Poznámky  
 Posledním elementem nesmí být prázdný. `pop_back` nikdy vyvolá výjimku.  
  
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
  
##  <a name="pop_front"></a>  deque::pop_front  
 Odstraní prvek na začátek deque.  
  
```  
void pop_front();
```  
  
### <a name="remarks"></a>Poznámky  
 První prvek nesmí být prázdný. `pop_front` nikdy vyvolá výjimku.  
  
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
  
##  <a name="push_back"></a>  deque::push_back  
 Přidá prvek na konec deque.  
  
```  
void push_back(const Type& val);

void push_back(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`val`|Prvek přidán na konec deque.|  
  
### <a name="remarks"></a>Poznámky  
 Pokud je vyvolána výjimka, je ponechán deque v nezměněném stavu a je znovu vyvolány výjimku.  
  
##  <a name="push_front"></a>  deque::push_front  
 Přidá prvek na začátek deque.  
  
```  
    void push_front(const Type& val);

void push_front(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`val`|Prvek přidán na začátek deque.|  
  
### <a name="remarks"></a>Poznámky  
 Pokud je vyvolána výjimka, je ponechán deque v nezměněném stavu a je znovu vyvolány výjimku.  
  
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
  
##  <a name="rbegin"></a>  deque::rbegin  
 Vrátí iterovat prvním elementem v invertovaných deque.  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Zpětné iterator náhodný přístup adresování prvním elementem v invertovaných deque nebo řešení, co je posledním prvkem v unreversed deque.  
  
### <a name="remarks"></a>Poznámky  
 `rbegin` se používá s odstínech deque stejně jako [začít](#begin) se používá s deque.  
  
 Pokud vrátí hodnotu, která `rbegin` je přiřazena k `const_reverse_iterator`, deque objekt nelze změnit. Pokud vrátí hodnotu, která `rbegin` je přiřazena k `reverse_iterator`, je možné upravit objekt deque.  
  
 `rbegin` můžete použít k iteraci v rámci deque zpětné.  
  
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
  
##  <a name="reference"></a>  deque::Reference  
 Typ, který obsahuje odkaz na element uložené v deque.  
  
```  
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
  
##  <a name="rend"></a>  deque::rend  
 Vrátí iterátor, který řeší úspěšné posledním prvkem v invertovaných deque umístění.  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Zpětné iterator náhodný přístup, která řeší umístění úspěšné posledním prvkem v invertovaných deque (umístění, které měl před prvním elementem v unreversed deque).  
  
### <a name="remarks"></a>Poznámky  
 `rend` se používá s odstínech deque stejně jako [end](#end) se používá s deque.  
  
 Pokud vrátí hodnotu, která `rend` je přiřazena k `const_reverse_iterator`, deque objekt nelze změnit. Pokud vrátí hodnotu, která `rend` je přiřazena k `reverse_iterator`, je možné upravit objekt deque.  
  
 `rend` slouží k ověření, zda zpětné iterator dosáhne konce své deque.  
  
 Hodnoty vrácené `rend` by neměl být vyhodnoceny odkazy.  
  
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
  
##  <a name="resize"></a>  deque::Resize  
 Určuje novou velikost deque.  
  
```  
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```  
  
### <a name="parameters"></a>Parametry  
 `_Newsize`  
 Novou velikost deque.  
  
 `val`  
 Hodnota nové prvky, které mají být přidány do deque, pokud nová velikost je větší, původní velikost. Pokud hodnota je vynechán, nové prvky přiřazené výchozí hodnota pro třídu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud deque velikost je menší než požadovaná velikost `_Newsize`, jsou přidány elementy na deque dokud nedosáhne požadované velikosti.  
  
 Pokud deque velikost je větší než požadovaná velikost, jsou elementy nejbližší na konec deque odstranit, dokud deque dosáhne velikosti `_Newsize`.  
  
 Pokud existuje velikost deque je stejný jako požadovaná velikost, nebyla provedena žádná akce.  
  
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
  
##  <a name="reverse_iterator"></a>  deque::reverse_iterator  
 Typ, který poskytuje iterator náhodný přístup, který může číst nebo upravovat element v invertovaných deque.  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ `reverse_iterator` je použít k iteraci v rámci deque.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro rbegin –.  
  
##  <a name="shrink_to_fit"></a>  deque::shrink_to_fit  
 Zahození přebytečnou kapacitou.  
  
```  
void shrink_to_fit();
```  
  
### <a name="remarks"></a>Poznámky  
 Neexistuje žádný způsob přenosné k určení, zda `shrink_to_fit` snižuje úložiště používaný [deque](../standard-library/deque-class.md).  
  
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
  
##  <a name="size"></a>  deque::size  
 Vrátí počet prvků deque.  
  
```  
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
  
##  <a name="size_type"></a>  deque::size_type  
 Typ, který udává počet elementů v deque.  
  
```  
typedef typename Allocator::size_type size_type;  
```  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [velikost](#size).  
  
##  <a name="swap"></a>  deque::swap  
 Elementy dvě deques výměny.  
  
```  
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>  
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Deque poskytuje prvky, které mají být prohodily nebo deque, jehož elementy jsou k výměně s těmi deque `left`.  
  
 `left`  
 Deque, jehož elementy jsou k výměně s těmi deque `right`.  
  
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
  
##  <a name="value_type"></a>  deque::value_type  
 Typ, který představuje typ data uložená v deque.  
  
```  
typedef typename Allocator::value_type value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 `value_type` je synonymum pro parametr šablony **typu**.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)

