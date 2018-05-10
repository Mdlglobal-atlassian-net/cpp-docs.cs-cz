---
title: hash_map – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- hash_map/stdext::hash_map
- hash_map/stdext::hash_map::allocator_type
- hash_map/stdext::hash_map::const_iterator
- hash_map/stdext::hash_map::const_pointer
- hash_map/stdext::hash_map::const_reference
- hash_map/stdext::hash_map::const_reverse_iterator
- hash_map/stdext::hash_map::difference_type
- hash_map/stdext::hash_map::iterator
- hash_map/stdext::hash_map::key_compare
- hash_map/stdext::hash_map::key_type
- hash_map/stdext::hash_map::mapped_type
- hash_map/stdext::hash_map::pointer
- hash_map/stdext::hash_map::reference
- hash_map/stdext::hash_map::reverse_iterator
- hash_map/stdext::hash_map::size_type
- hash_map/stdext::hash_map::value_type
- hash_map/stdext::hash_map::at
- hash_map/stdext::hash_map::begin
- hash_map/stdext::hash_map::cbegin
- hash_map/stdext::hash_map::cend
- hash_map/stdext::hash_map::clear
- hash_map/stdext::hash_map::count
- hash_map/stdext::hash_map::crbegin
- hash_map/stdext::hash_map::crend
- hash_map/stdext::hash_map::emplace
- hash_map/stdext::hash_map::emplace_hint
- hash_map/stdext::hash_map::empty
- hash_map/stdext::hash_map::end
- hash_map/stdext::hash_map::equal_range
- hash_map/stdext::hash_map::erase
- hash_map/stdext::hash_map::find
- hash_map/stdext::hash_map::get_allocator
- hash_map/stdext::hash_map::insert
- hash_map/stdext::hash_map::key_comp
- hash_map/stdext::hash_map::lower_bound
- hash_map/stdext::hash_map::max_size
- hash_map/stdext::hash_map::rbegin
- hash_map/stdext::hash_map::rend
- hash_map/stdext::hash_map::size
- hash_map/stdext::hash_map::swap
- hash_map/stdext::hash_map::upper_bound
- hash_map/stdext::hash_map::value_comp
dev_langs:
- C++
helpviewer_keywords:
- stdext::hash_map
- stdext::hash_map::allocator_type
- stdext::hash_map::const_iterator
- stdext::hash_map::const_pointer
- stdext::hash_map::const_reference
- stdext::hash_map::const_reverse_iterator
- stdext::hash_map::difference_type
- stdext::hash_map::iterator
- stdext::hash_map::key_compare
- stdext::hash_map::key_type
- stdext::hash_map::mapped_type
- stdext::hash_map::pointer
- stdext::hash_map::reference
- stdext::hash_map::reverse_iterator
- stdext::hash_map::size_type
- stdext::hash_map::value_type
- stdext::hash_map::at
- stdext::hash_map::begin
- stdext::hash_map::cbegin
- stdext::hash_map::cend
- stdext::hash_map::clear
- stdext::hash_map::count
- stdext::hash_map::crbegin
- stdext::hash_map::crend
- stdext::hash_map::emplace
- stdext::hash_map::emplace_hint
- stdext::hash_map::empty
- stdext::hash_map::end
- stdext::hash_map::equal_range
- stdext::hash_map::erase
- stdext::hash_map::find
- stdext::hash_map::get_allocator
- stdext::hash_map::insert
- stdext::hash_map::key_comp
- stdext::hash_map::lower_bound
- stdext::hash_map::max_size
- stdext::hash_map::rbegin
- stdext::hash_map::rend
- stdext::hash_map::size
- stdext::hash_map::swap
- stdext::hash_map::upper_bound
- stdext::hash_map::value_comp
ms.assetid: 40879dfc-51ba-4a59-9f9e-26208de568a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68d3ed6e9274fdfad38ad7ed8cdd9f8e83e0630a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="hashmap-class"></a>hash_map – třída

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Ukládá a rychle načítá data z kolekce, ve kterém je každý prvek pár, který má klíč řazení, jehož hodnota je jedinečný a hodnotu přidružená data.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<pair <const Key, Type>>>
class hash_map
```

### <a name="parameters"></a>Parametry

`Key` Typ klíčová data k uložení do hash_map.

`Type` Datový typ elementu k uložení do hash_map.

`Traits` Typ, který obsahuje dva objekty funkce, jeden z třída porovnání možnost k porovnání dvou hodnot element jako klíči řazení určit jejich relativní pořadí a hodnota hash funkce, která je predikát unární mapování hodnoty klíče elementů na nepodepsané celá čísla typu `size_t`. Tento argument je volitelný a hash_compare < `Key`, menší < `Key`>> je výchozí hodnota.

`Allocator` Typ, který představuje uložené allocator objekt, který zapouzdřuje podrobnosti o přidělení hash_map a zrušení přidělení paměti. Tento argument je volitelný a výchozí hodnota je allocator < pair < const `Key`, `Type`>>.

## <a name="remarks"></a>Poznámky

Hash_map je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Algoritmus hash, protože jeho prvky jsou seskupeny do sad na základě hodnoty hash funkci použité pro hodnoty klíče elementů.

- Jedinečný v tom smyslu, že každý z jeho prvků musí mít jedinečný klíč.

- Kontejner asociativních párů, protože jeho prvky hodnoty dat se liší od hodnot klíčů.

- Třída šablony, protože poskytuje obecné funkce a to nezávisle na určitém typu dat obsažených jako prvky nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Hlavní výhodou použití algoritmu hash přes řazení je vyšší efektivity; úspěšné algoritmu hash provádí vkládání, odstraňování a vyhledá v porovnání s čas konstantní Průměrná doba úměrná logaritmus počet elementů v kontejneru pro řazení techniky. Hodnota elementu v hash_map, ale není přidružené hodnoty klíče, může se změnit přímo. Namísto toho hodnoty klíčů přidružené ke starým prvkům musí být odstraněny a vloženy nové hodnoty klíče související s novými prvky.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Hash asociativní kontejnery jsou optimalizované pro operace vyhledávání, vkládání a odebrání. Členské funkce, které explicitně podporují tyto operace jsou efektivní, pokud se používá s dobře navrženou hash funkce, provádět v čase, který je v průměru konstant a není závislá na počet elementů v kontejneru. Funkce dobře navrženou hash vytváří rovnoměrné rozdělení hodnot hash a minimalizuje počet kolizí, kde kolize říká, že je dojít, když odlišné hodnoty klíče jsou namapované na stejnou hodnotu hash. V nejhorším případě s funkci nejhorší možné hash počet operací je úměrná počet elementů v pořadí (lineární čas).

Hash_map by měl být kontejneru asociativní výběru aplikací jsou splněny podmínky přidružení hodnoty k jejich klíče. Model pro tento typ struktura je seřazený seznam jednoznačně se vyskytující klíčová slova se přidružené řetězcové hodnoty, které poskytnete, Řekněme, definice. Pokud místo toho slova měl správné víc než jednu definici, tak, aby nebyly klíče jedinečné, hash_multimap by kontejneru výběru. Pokud na druhé straně byly ukládaného právě seznam slova, hash_set by správné kontejneru. Pokud bylo povoleno více výskytů slova, hash_multiset by strukturu odpovídajícího kontejneru.

Hash_map řadí pořadí jimi řídí voláním uložené hodnoty hash `Traits` objekt třídy [value_compare –](../standard-library/value-compare-class.md). Tento objekt uložené přístupná voláním členské funkce [key_comp –](#key_comp). Funkce objektu musí chovají stejně jako objekt třídy [hash_compare](../standard-library/hash-compare-class.md)< klíče méně\<klíč >>. Konkrétně pro všechny hodnoty `Key` typu `Key`, volání `Traits`( `Key` ) vypočítá distribuci hodnot typu `size_t`.

Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikátem f(x y) je objekt funkce, která má dva objekty argument `x` a `y` a návratová hodnota `true` nebo `false`. Řazení vynucená pro hash_map je striktní weak řazení Pokud binární predikát je Nereflexivní, antisymetrického a přenositelné a pokud ekvivalenční přenositelné, kde dva objekty x a y jsou definovány jako ekvivalentní po false f (x, y) a f (y, x). Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

Skutečné pořadí prvků v řízené sekvenci závisí na funkci hash, funkci řazení a aktuální velikost tabulku hash uložené v objektu kontejneru. Aktuální velikost zatřiďovací tabulku nelze určit, takže nemůžete obecně předpovědět pořadí prvků v řízené sekvenci. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Iterator poskytované hash_map – třída je obousměrný iterator, ale členské funkce tříd [vložit](#insert) a [hash_map](#hash_map) mají verze, které jako parametry šablony trvat slabší vstupní iterator, požadavky na jejichž funkce jsou minimální více než ty, které zaručit třídou obousměrného iterátory. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální sadu funkcí, které, ale stačí mohli srozumitelně mluvit o rozsah iterátory `[First, Last)` v kontextu členské funkce tříd.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[hash_map](#hash_map)|Vytvoří `hash_map` který je prázdný nebo který je kopie všech nebo některých jiných součástí `hash_map`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type –](#allocator_type)|Typ, který reprezentuje `allocator` třídy pro `hash_map` objektu.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrné iterator, který může číst `const` element v `hash_map`.|
|[const_pointer](#const_pointer)|Typ, který poskytuje odkazy `const` element v `hash_map`.|
|[const_reference](#const_reference)|Typ, který obsahuje odkaz na `const` element uložené v `hash_map` pro čtení a provádění `const` operace.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrné iterator, který může číst všechny `const` element v `hash_map`.|
|[difference_type](#difference_type)|Typ se znaménkem, který můžete použít k reprezentování počet prvků `hash_map` v rozsahu mezi elementy, na kterou iterátory odkazuje.|
|[Iterator](#iterator)|Typ, který poskytuje obousměrné iterator, který může číst nebo upravovat libovolný element v `hash_map`.|
|[key_compare](#key_compare)|Typ, který poskytuje funkce objekt, který můžete porovnat dva klíče řazení k určení relativních pořadí dva elementy v `hash_map`.|
|[key_type](#key_type)|Popisuje typ řazení klíče objektu, která se považuje za každý element `hash_map`.|
|[mapped_type](#mapped_type)|Typ, který představuje typ data uložená v `hash_map`.|
|[Ukazatele](#pointer)|Typ, který poskytuje ukazatel na prvek v `hash_map`.|
|[Referenční dokumentace](#reference)|Typ, který obsahuje odkaz na element uložené v `hash_map`.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrné iterator, které můžou číst nebo upravte element v odstínech `hash_map`.|
|[size_type](#size_type)|Typ celé číslo bez znaménka, která představuje počet elementů ve `hash_map`.|
|[value_type](#value_type)|Typ, který poskytuje funkce objekt, který můžete porovnat dva elementy jako klíči řazení určit jejich relativní pořadí v `hash_map`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[at](#at)|Vyhledá v elementu `hash_map` se zadanou hodnotou klíče.|
|[Začátek](#begin)|Vrátí iterovat adresování prvním elementem v `hash_map`.|
|[cbegin –](#cbegin)|Vrátí const iterator adresování prvním elementem v `hash_map`.|
|[cend –](#cend)|Vrátí const iterator, která řeší úspěšné posledním prvkem v umístění `hash_map`.|
|[Zrušte zaškrtnutí](#clear)|Vymaže všechny elementy `hash_map`.|
|[Počet](#count)|Vrátí počet prvků v `hash_map` jejichž klíč odpovídá parametru zadaný klíč.|
|[crbegin](#crbegin)|Vrátí const iterator adresování prvním elementem v odstínech `hash_map`.|
|[crend –](#crend)|Vrátí const iterator, která řeší umístění úspěšné posledním prvkem v odstínech `hash_map`.|
|[emplace –](#emplace)|Vloží element v místě do zkonstruovat `hash_map`.|
|[emplace_hint –](#emplace_hint)|Vloží element v místě do zkonstruovat `hash_map`, s pomocným parametrem umístění.|
|[prázdný](#empty)|Pokud testy `hash_map` je prázdný.|
|[End](#end)|Vrátí iterátor, který řeší úspěšné posledním prvkem v umístění `hash_map`.|
|[equal_range](#equal_range)|Vrátí pár iterátory, v uvedeném pořadí, na prvním elementem v `hash_map` s klíčem, který je větší, než je zadaný klíč a prvním elementem v `hash_map` s klíčem, který je rovna nebo větší než klíč.|
|[vymazání](#erase)|Odebere element nebo rozsah elementů v `hash_map` ze zadaných pozic|
|[Najít](#find)|Vrátí iterovat adresování umístění elementu v `hash_map` který má klíč ekvivalentní k zadanému klíči.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objekt použitý k vytvoření `hash_map`.|
|[Vložení](#insert)|Vloží elementu nebo rozsahu prvků do `hash_map`.|
|[key_comp](#key_comp)|Vrátí iterovat prvním elementem v `hash_map` s hodnotou klíče, která je rovna nebo větší než je zadaný klíč.|
|[lower_bound –](#lower_bound)|Vrátí iterovat prvním elementem v `hash_map` s hodnotou klíče, která je rovna nebo větší než je zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délka `hash_map`.|
|[rbegin –](#rbegin)|Vrátí iterovat adresování prvním elementem v odstínech `hash_map`.|
|[rend –](#rend)|Vrátí iterátor, který řeší umístění úspěšné posledním prvkem v odstínech `hash_map`.|
|[Velikost](#size)|Vrátí počet prvků v `hash_map`.|
|[Swap](#swap)|Výměny dva elementy `hash_map`s.|
|[upper_bound –](#upper_bound)|Vrátí iterovat prvním elementem v `hash_map` , s klíčem hodnotu, je větší než je zadaný klíč.|
|[value_comp](#value_comp)|Načte kopii porovnání objekt použitý k hodnoty element pořadí v `hash_map`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor&#91;&#93;](#op_at)|Vloží do elementu `hash_map` se zadanou hodnotou klíče.|
|[hash_map::operator=](#op_eq)|Nahradí elementy `hash_map` kopii jiného `hash_map`.|

## <a name="requirements"></a>Požadavky

**Header:** \<hash_map>

**Namespace:** stdext –

## <a name="allocator_type"></a>  hash_map::allocator_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ, který reprezentuje allocator – třída objektu hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Příklad

Podívejte se příklad [get_allocator –](#get_allocator) pro příklad použití `allocator_type`.

## <a name="at"></a>  hash_map::AT

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vyhledá element v hash_map se zadanou hodnotou klíče.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`key`|Hodnota klíče elementu, který má být nalezen.|

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu dat nalezen prvek.

### <a name="remarks"></a>Poznámky

Pokud není nalezena hodnota klíče argument, pak funkce vyvolá objekt třídy [out_of_range – třída](../standard-library/out-of-range-class.md).


### <a name="example"></a>Příklad

```cpp
// hash_map_at.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;

   // Insert data values
   hm1.insert ( cInt2Int ( 1, 10 ) );
   hm1.insert ( cInt2Int ( 2, 20 ) );
   hm1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The values of the mapped elements are:";
   for ( int i = 1 ; i <= hm1.size() ; i++ )
      cout << " " << hm1.at(i);
   cout << "." << endl;
}
```

## <a name="begin"></a>  hash_map::begin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí iterator adresování prvním elementem v hash_map.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrné iterator, který adresování prvním elementem v hash_map nebo umístění prázdný hash_map – úspěšné.

### <a name="example"></a>Příklad

```cpp
// hash_map_begin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 0, 0 ) );
   hm1.insert ( Int_Pair ( 1, 1 ) );
   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.begin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;

   hm1_Iter = hm1.begin ( );
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.begin ( );
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.begin( );
   cout << "The first element of hm1 is now "
        << hm1_cIter -> first << "." << endl;
}
```

```Output
The first element of hm1 is 0.
The first element of hm1 is now 1.
```

## <a name="cbegin"></a>  hash_map::cbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí const iterator adresování prvním elementem v hash_map.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const iterator obousměrného adresování prvním elementem v [hash_map](../standard-library/hash-map-class.md) nebo umístění úspěšné prázdnou `hash_map`.

### <a name="example"></a>Příklad

```cpp
// hash_map_cbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.cbegin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;
   }
```

```Output
The first element of hm1 is 2.
```

## <a name="cend"></a>  hash_map::cend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí const iterator, která řeší úspěšné posledním prvkem v hash_map – umístění.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const iterator obousměrného, která řeší úspěšné posledním prvkem v umístění [hash_map](../standard-library/hash-map-class.md). Pokud `hash_map` je prázdný, pak `hash_map::cend == hash_map::begin`.

### <a name="remarks"></a>Poznámky

`cend` slouží k otestování, jestli iterovat byl dosažen konec jeho `hash_map`.

Hodnoty vrácené `cend` by neměl být vyhodnoceny odkazy.

### <a name="example"></a>Příklad

```cpp
// hash_map_cend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.cend( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;
   }
```

```Output
The value of last element of hm1 is 30.
```

## <a name="clear"></a>  hash_map::clear

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vymaže všechny elementy hash_map.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_map::clear – členská funkce.

```cpp
// hash_map_clear.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 4));

    i = hm1.size();
    cout << "The size of the hash_map is initially "
         << i << "." << endl;

    hm1.clear();
    i = hm1.size();
    cout << "The size of the hash_map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the hash_map is initially 2.
The size of the hash_map after clearing is 0.
```

## <a name="const_iterator"></a>  hash_map::const_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ, který poskytuje obousměrné iterator, který může číst **const** element v hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít k úpravě hodnota elementu.

`const_iterator` Definovaný hash_map – body na elementy, které jsou objekty [value_type](#value_type), která je typu `pair` *\< ***const klíč, typ*** >*, jehož první člen je klíčem k elementu a jehož sekundu člen je namapované datum uchovávat elementem.

K dereference `const_iterator` `cIter` odkazující na prvek v hash_map, použijte **->** operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `cIter` **-> nejprve**, což je totéž jako (\* `cIter`) **.first**. Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `cIter` **-> sekundu**, což je totéž jako (\* `cIter`) **.second**.

### <a name="example"></a>Příklad

Podívejte se příklad [začít](#begin) pro příklad použití `const_iterator`.

## <a name="const_pointer"></a>  hash_map::const_pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ, který poskytuje odkazy **const** element v hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít k úpravě hodnota elementu.

Ve většině případů [iterator](#iterator) se má použít pro přístup k elementům v hash_map objektu.

## <a name="const_reference"></a>  hash_map::const_reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ, který obsahuje odkaz na **const** element uložené v hash_map – pro čtení a provádění **const** operace.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_map_const_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map<int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of the first element in the hash_map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of the first element in the hash_map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the hash_map is 1.
The data value of the first element in the hash_map is 10.
```

## <a name="const_reverse_iterator"></a>  hash_map::const_reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ, který poskytuje obousměrné iterator, který může číst všechny **const** element v hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse)iterator const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nelze změnit hodnotu elementu a je použít k iteraci v rámci hash_map pozpátku.

`const_reverse_iterator` Definovaný hash_map – body na elementy, které jsou objekty [value_type](#value_type), která je typu `pair` \< **const klíč, typ**>, jejíž první člen je klíčem k Tento prvek a jehož druhý člen, je namapované datum uchovávat elementem.

K dereference `const_reverse_iterator` `crIter` odkazující na prvek v hash_map, použijte **->** operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `crIter`  ->  **první**, což je totéž jako (\* `crIter`) **.first**. Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `crIter`  ->  **druhý**, což je totéž jako (\* `crIter`). **první**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rend](#rend) příklad toho, jak deklarace a používání `const_reverse_iterator`.

## <a name="count"></a>  hash_map::Count

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí počet prvků v hash_map, jehož klíč odpovídá parametru zadaný klíč.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Hodnota klíče elementů lze porovnat z hash_map.

### <a name="return-value"></a>Návratová hodnota

1, pokud hash_map – obsahuje element, jehož klíč řazení shoduje s klíčem parametr; 0, pokud hash_map neobsahuje element s odpovídající klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků *x* v rozsahu

[ `lower_bound` (_ *Klíč* ), `upper_bound` (\_ *klíč* ))

což je 0 nebo 1 v případě hash_map, což je jedinečný asociativní kontejner.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_map::count – členská funkce.

```cpp
// hash_map_count.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair (1, 1));
    hm1.insert(Int_Pair (2, 1));
    hm1.insert(Int_Pair (1, 4));
    hm1.insert(Int_Pair (2, 1));

    // Keys must be unique in hash_map, so duplicates are ignored
    i = hm1.count(1);
    cout << "The number of elements in hm1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hm1.count(2);
    cout << "The number of elements in hm1 with a sort key of 2 is: "
         << i << "." << endl;

    i = hm1.count(3);
    cout << "The number of elements in hm1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hm1 with a sort key of 1 is: 1.
The number of elements in hm1 with a sort key of 2 is: 1.
The number of elements in hm1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  hash_map::crbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí const iterator adresování prvním elementem v invertovaných hash_map.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse obousměrného iterator adresování prvním elementem v odstínech [hash_map](../standard-library/hash-map-class.md) nebo řešení, co je posledním prvkem v unreversed `hash_map`.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s odstínech hash_map – stejně jako [začít](#begin) se používá s `hash_map`.

S návratovou hodnotou `crbegin`, `hash_map` objekt nelze změnit.

`crbegin` lze použít k iteraci v rámci `hash_map` zpětné.

### <a name="example"></a>Příklad

```cpp
// hash_map_crbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crbegin( );
   cout << "The first element of the reversed hash_map hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_map hm1 is 3.
```

## <a name="crend"></a>  hash_map::crend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí const iterator, která řeší úspěšné posledním prvkem v invertovaných hash_map – umístění.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse iterator obousměrného, která řeší umístění úspěšné posledním prvkem v odstínech [hash_map](../standard-library/hash-map-class.md) (umístění, které měl před prvním elementem v unreversed `hash_map`).

### <a name="remarks"></a>Poznámky

`crend` se používá s odstínech `hash_map` stejně jako [hash_map::end](#end) se používá s `hash_map`.

S návratovou hodnotou `crend`, `hash_map` objekt nelze změnit.

`crend` můžete použít k testování na tom, jestli má zpětné iterator dosáhla konce jeho `hash_map`.

Hodnoty vrácené `crend` by neměl být vyhodnoceny odkazy.

### <a name="example"></a>Příklad

```cpp
// hash_map_crend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crend( );
   hm1_crIter--;
   cout << "The last element of the reversed hash_map hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_map hm1 is 3.
```

## <a name="difference_type"></a>  hash_map::difference_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ se znaménkem, který můžete použít k reprezentování počet elementů hash_map v rozsahu mezi elementy, na kterou iterátory odkazuje.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="example"></a>Příklad

```cpp
// hash_map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 3, 20 ) );

   // The following won't insert, because map keys are unique
   hm1.insert ( Int_Pair ( 2, 30 ) );

   hash_map <int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;
   hm1_bIter = hm1.begin( );
   hm1_eIter = hm1.end( );

   // Count the number of elements in a hash_map
   hash_map <int, int>::difference_type  df_count = 0;
   hm1_Iter = hm1.begin( );
   while ( hm1_Iter != hm1_eIter)
   {
      df_count++;
      hm1_Iter++;
   }

   cout << "The number of elements in the hash_map hm1 is: "
        << df_count << "." << endl;

   cout  << "The keys of the mapped elements are:";
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;
         hm1_Iter++)
      cout << " " << hm1_Iter-> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;
         hm1_Iter++)
      cout << " " << hm1_Iter-> second;
   cout << "." << endl;
}
```

```Output
The number of elements in the hash_map hm1 is: 3.
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 20.
```

## <a name="emplace"></a>  hash_map::emplace

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vloží element sestavený na místě do hash_map.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`val`|Hodnota používá k přesunu vytvořit element, který má být vložen do [hash_map](../standard-library/hash-map-class.md) Pokud `hash_map` již obsahuje tohoto elementu (nebo, obecně platí, element, jehož klíč je ekvivalentně řazení).|

### <a name="return-value"></a>Návratová hodnota

`emplace` – Členská funkce vrátí pár, jejichž součástí bool vrátí hodnotu true, pokud došlo vložení a false, pokud `hash_map` už obsažený element, jehož klíč měl ekvivalentní hodnotu v pořadí a vrátí jejichž iterator součást adres vloženy nového elementu nebo kde byl element již nachází.

Pro přístup k iterator součást pár `pr` vrácené funkcí tento člen, použijte `pr.first`a pokud chcete ho dereference, použijte `*(pr.first)`. Abyste měli přístup `bool` součásti z dvojice `pr` vrácené funkcí tento člen, použijte `pr.second`a pokud chcete ho dereference, použijte `*(pr.second)`.

### <a name="remarks"></a>Poznámky

[Hash_map::value_type](#value_type) elementu je pár, aby bude použita hodnota elementu dvojici seřazené s první součást, která je rovna hodnotě klíče a druhá součást, která je rovna hodnotě dat prvku.

### <a name="example"></a>Příklad

```cpp
// hash_map_emplace.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(move(is1));
    cout << "After the emplace insertion, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
 1 => a
```

## <a name="emplace_hint"></a>  hash_map::emplace_hint

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vloží element sestavený na místě do hash_map – s pomocným parametrem umístění.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`val`|Hodnota používá k přesunu vytvořit element, který má být vložen do [hash_map](../standard-library/hash-map-class.md) Pokud `hash_map` již obsahuje tohoto elementu (nebo, obecně platí, element, jehož klíč je ekvivalentně řazení).|
|`_Where`|Nápovědu ohledně místní zahájeno hledání správné bod vložení.|

### <a name="return-value"></a>Návratová hodnota

[Hash_multimap::emplace](../standard-library/hash-multimap-class.md#emplace) – členská funkce vrátí iterátor, který odkazuje na pozici, kde byl nový element vložený do `hash_map`, nebo kde se nachází existující element s ekvivalentní řazení.

### <a name="remarks"></a>Poznámky

[Hash_map::value_type](#value_type) elementu je pár, aby bude použita hodnota elementu dvojici seřazené s první součást, která je rovna hodnotě klíče a druhá součást, která je rovna hodnotě dat prvku.

Vložení se může objevit v amortizovaný konstantní čas, místo logaritmické čas, pokud bod vložení následuje `_Where`.

### <a name="example"></a>Příklad

```cpp
// hash_map_emplace_hint.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(hm1.begin(), move(is1));
    cout << "After the emplace, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
 1 => a
```

## <a name="empty"></a>  hash_map::Empty

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Testy, pokud hash_map je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud hash_map je prázdná. **false** Pokud je hash_map neprázdný.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_map_empty.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2;

   typedef pair <int, int> Int_Pair;
   hm1.insert ( Int_Pair ( 1, 1 ) );

   if ( hm1.empty( ) )
      cout << "The hash_map hm1 is empty." << endl;
   else
      cout << "The hash_map hm1 is not empty." << endl;

   if ( hm2.empty( ) )
      cout << "The hash_map hm2 is empty." << endl;
   else
      cout << "The hash_map hm2 is not empty." << endl;
}
```

```Output
The hash_map hm1 is not empty.
The hash_map hm2 is empty.
```

## <a name="end"></a>  hash_map::end

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí iterátor, který řeší úspěšné posledním prvkem v hash_map – umístění.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Iterator obousměrného, která řeší úspěšné posledním prvkem v hash_map – umístění. Pokud hash_map je prázdný, hash_map::end == hash_map::begin.

### <a name="remarks"></a>Poznámky

**end** slouží k otestování, jestli iterovat dosáhne konce své hash_map.

Hodnoty vrácené **end** by neměl být vyhodnoceny odkazy.

### <a name="example"></a>Příklad

```cpp
// hash_map_end.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;

   hm1_Iter = hm1.end( );
   hm1_Iter--;
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.end ( );
   // hm1_cIter--;
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is now "
        << hm1_cIter -> second << "." << endl;
}
```

```Output
The value of last element of hm1 is 30.
The value of last element of hm1 is now 20.
```

## <a name="equal_range"></a>  hash_map::equal_range

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí funkce pár iterátory prvním elementem v hash_map s klíčem, který je větší než je zadaný klíč a prvním elementem v hash_map s klíčem, který je rovna nebo větší než klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

`key` Hodnota klíče argument být porovnána s klíč řazení elementu z hash_map být vyhledán.

### <a name="return-value"></a>Návratová hodnota

Pár iterátory tak, aby první je [lower_bound –](#lower_bound) klíč a druhý je [upper_bound –](#upper_bound) klíče.

Pro přístup k první iterator páru `pr` vrácené funkcí člen, použijte `pr`. **první** a pokud chcete dereference iterator dolní mez, použijte \*( `pr`. **nejprve**). Pro přístup k druhý iterator páru `pr` vrácené funkcí člen, použijte `pr`. **druhý** a pokud chcete dereference iterator horní mez, použijte \*( `pr`. **druhý**).

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_map_equal_range.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_map <int, int> IntMap;
   IntMap hm1;
   hash_map <int, int> :: const_iterator hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = hm1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the hash_map hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the hash_map hm1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   hm1_RcIter = hm1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << hm1_RcIter -> second << "," << endl
        << " matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = hm1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )
      cout << "The hash_map hm1 doesn't have an element "
             << "with a key less than 40." << endl;
   else
      cout << "The element of hash_map hm1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the hash_map hm1 is: 20.
The upper bound of the element with a key of 2 in the hash_map hm1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
 matching the 2nd element of the pair returned by equal_range( 2 ).
The hash_map hm1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>  hash_map::Erase

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Odebere element nebo rozsah elementů v hash_map ze zadaných pozic nebo odebere prvky, které odpovídají zadaným klíčem.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

`_Where` Pozice elementu, který má být odebrán z hash_map.

`first` Pozice první prvek odebrán z hash_map.

`last` Pozice bezprostředně za posledním elementem odebrán z hash_map.

`key` Hodnota klíče elementů má být odebrán z hash_map.

### <a name="return-value"></a>Návratová hodnota

Pro první dva členské funkce obousměrné iterator, označí první prvek zbývající nad rámec žádné elementy, odebrat nebo ukazatel na konec hash_map, pokud neexistuje žádný takový prvek.

Pro třetí – členská funkce vrátí počet prvků, které byly odebrány z hash_map –.

### <a name="remarks"></a>Poznámky

Členské funkce nikdy vyvolat výjimku.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_map::erase – členská funkce.

```cpp
// hash_map_erase.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1, hm2, hm3;
    hash_map<int, int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_map<int, int>::size_type n;
    typedef pair<int, int> Int_Pair;

    for (i = 1; i < 5; i++)
    {
        hm1.insert(Int_Pair (i, i));
        hm2.insert(Int_Pair (i, i*i));
        hm3.insert(Int_Pair (i, i-1));
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hm1.begin();
    hm1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_map hm1 is:";
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hm2.begin();
    Iter2 = --hm2.end();
    hm2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_map hm2 is:";
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hm3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_map hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hm3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hm3.begin();
    hm3.erase(Iter1);

    cout << "After another element with a key equal to that"
         << endl;
    cout  << "of the 2nd element is deleted, "
          << "the hash_map hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_map hm1 is: 1 3 4.
After the middle two elements are deleted, the hash_map hm2 is: 1 16.
After the element with a key of 2 is deleted,
the hash_map hm3 is: 0 2 3.
The number of elements removed from hm3 is: 1.
After another element with a key equal to that
of the 2nd element is deleted, the hash_map hm3 is: 0 3.
```

## <a name="find"></a>  hash_map::Find

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí iterovat adresování umístění elementu v hash_map, s klíčem ekvivalentní k zadanému klíči.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Hodnota klíče odpovídala klíč řazení elementu z hash_map být vyhledán.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který adresy umístění element se zadaným klíčem nebo umístění posledním prvkem v hash_map – úspěšné, pokud není nalezena žádná shoda pro klíč.

### <a name="remarks"></a>Poznámky

**Najít** vrátí iterátor, který řeší element v hash_map, jehož klíč řazení je ekvivalentní argument klíč v predikátu Binární indukuje řazení podle menší než srovnání vztah.

Pokud vrátí hodnotu, která **najít** je přiřazena k [const_iterator –](#const_iterator), hash_map objekt nelze změnit. Pokud návratová hodnota **najít** je přiřazena k [iterator](#iterator), je možné upravit hash_map – objekt

### <a name="example"></a>Příklad

```cpp
// hash_map_find.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.find( 2 );
   cout << "The element of hash_map hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.find( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_map can be found
   // using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1.find( hm1_AcIter -> first );
   cout << "The element of hm1 with a key matching "
        << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The element of hash_map hm1 with a key of 2 is: 20.
The hash_map hm1 doesn't have an element with a key of 4.
The element of hm1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a>  hash_map::get_allocator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí kopii allocator objekt použitý k vytvoření hash_map.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Allocator používané hash_map.

### <a name="remarks"></a>Poznámky

Alokátorů pro hash_map – Třída zadejte, jak třída spravuje úložiště. Alokátorů výchozí součástí standardní knihovna C++ – třídy kontejnerů postačí pro většinu programovacích potřeb. Psaní a pomocí vlastní allocator – třída je rozšířená C++.

### <a name="example"></a>Příklad

```cpp
// hash_map_get_allocator.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int>::allocator_type hm1_Alloc;
   hash_map <int, int>::allocator_type hm2_Alloc;
   hash_map <int, double>::allocator_type hm3_Alloc;
   hash_map <int, int>::allocator_type hm4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   hash_map <int, int> hm1;
   hash_map <int, int> hm2;
   hash_map <int, double> hm3;

   hm1_Alloc = hm1.get_allocator( );
   hm2_Alloc = hm2.get_allocator( );
   hm3_Alloc = hm3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hm2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hm3.max_size( ) <<  "." << endl;

   // The following line creates a hash_map hm4
   // with the allocator of hash_map hm1.
   hash_map <int, int> hm4( less<int>( ), hm1_Alloc );

   hm4_Alloc = hm4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( hm1_Alloc == hm4_Alloc )
   {
      cout << "The allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="hash_map"></a>  hash_map::hash_map

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Hash_map –, který je prázdný nebo je kopírování všech nebo součástí některých jiných hash_map – vytvoří.

```cpp
hash_map();

explicit hash_map(
    const Traits& Comp);

hash_map(
    const Traits& Comp,
    const Allocator& Al);

hash_map(
    const hash_map& Right);

hash_map(
    hash_map&& Right);

hash_map(
    initializer_list<Type> IList);hash_map(initializer_list<Type> IList,
    const key_compare& Comp);

hash_map(
    initializer_list<Type> IList,
    const key_compare& Comp,
    const allocator_type& Al);

template <class InputIterator>
hash_map(
 InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_map(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_map(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`Al`|Allocator – třída úložiště má být použit pro tento objekt hash_map – použije se výchozí hodnota **Allocator**.|
|`Comp`|Funkci porovnání typu const `Traits` sloužící k uspořádání elementy v hash_map, který se standardně `hash_compare`.|
|`Right`|Hash_map –, které má být kopie sestavené mapy.|
|`First`|Pozice první prvek v rozsahu elementy, které se mají zkopírovat.|
|`Last`|Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.|
|`IList`|Initializer_list|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládat typu allocator objektu, který spravuje úložiště paměti pro hash_map – a mohou být vráceny později voláním [get_allocator –](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializovat jejich hash_map.

Všechny konstruktory uložit objekt funkce typu `Traits` který se používá k navázání pořadí mezi klíči hash_map a který se může vracet později voláním [key_comp –](#key_comp).

První tři konstruktory zadat prázdný počáteční hash_map –, navíc druhý určuje typ funkce porovnání ( `Comp`) pro použití při vytváření pořadí elementy a třetí explicitně určuje typ allocator ( `Al`) k použití. Klíčové slovo `explicit` potlačí určité druhy převod automatické typu.

Čtvrtý konstruktor určuje kopii hash_map `Right`.

Zkopírujte následující tři konstruktory rozsahu `[First, Last)` z hash_map se zvýšeným explicitness v určení typu funkci porovnání třídy `Traits` a přidělení.

Poslední konstruktor přesune hash_map `Right`.

## <a name="insert"></a>  hash_map::Insert

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vloží do hash_map – element nebo rozsah elementů.

```cpp
pair <iterator, bool> insert(
    const value_type& val);

iterator insert(
    const_iterator _Where,
    const value_type& val);

template <class InputIterator>
void insert(
    InputIterator first,
    InputIterator last);

template <class ValTy>
pair <iterator, bool>
insert(
    ValTy&& val);

template <class ValTy>
iterator insert(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`val`|Hodnota elementu vložit do hash_map – Pokud hash_map – již obsahuje daný element (nebo, obecně platí, element, jehož klíč je ekvivalentně řazení).|
|`_Where`|Nápovědu ohledně místní zahájeno hledání správné bod vložení.|
|`first`|Pozice první prvek, který se má zkopírovat z hash_map –.|
|`last`|Pozice bezprostředně za posledním elementem zkopírovány z hash_map.|

### <a name="return-value"></a>Návratová hodnota

První **vložit** – členská funkce vrátí pár jejichž bool součást vrací hodnotu true, pokud se vložení učiněna a hodnotu false, pokud hash_map už obsažený element, jehož klíč měl ekvivalentní hodnotu v pořadí a jehož iterátorů součást vrátí adresu vloženy nového elementu nebo kde byl element již nachází.

Pro přístup k iterator součást pár `pr` vrácené funkcí tento člen, použijte `pr`. **první**a pokud chcete ho dereference, použijte \*( `pr`. **nejprve**). Abyste měli přístup `bool` součásti z dvojice `pr` vrácené funkcí tento člen, použijte `pr`. **druhý**a pokud chcete ho dereference, použijte \*( `pr`. **druhý**).

Druhý **vložit** – členská funkce pomocný parametr verze, vrátí iterátor, který odkazuje na pozici, kde nového elementu vložení do hash_map.

Poslední dva **vložit** členské funkce chovají stejně jako první dvě, s tím rozdílem, že se přesouvají vytvořit zadaná hodnota.

### <a name="remarks"></a>Poznámky

[Value_type](../standard-library/map-class.md#value_type) elementu je pár, aby bude použita hodnota elementu dvojici seřazené s první součást, která je rovna hodnotě klíče a druhá součást, která je rovna hodnotě dat prvku.

Vložení se může objevit v amortizovaný konstantní dobu pomocný parametr verzi vložení, místo logaritmické čas, pokud bod vložení následuje `_Where`.

Třetí členská funkce vloží do hash_map, odpovídající každý prvek řešené pomocí iterace v rozsahu pořadí hodnot element *[First, Last)* zadané sady.

### <a name="example"></a>Příklad

```cpp
// hash_map_insert.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int>::iterator hm1_pIter, hm2_pIter;

    hash_map<int, int> hm1, hm2;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(3, 30));
    hm1.insert(Int_Pair(4, 40));

    cout<< "The original elements (Key => Value) of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << " " << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    pair< hash_map<int,int>::iterator, bool > pr;
    pr = hm1.insert(Int_Pair(1, 10));

    if (pr.second == true)
    {
        cout<< "The element 10 was inserted in hm1 successfully."
            << endl;
    }
    else
    {
        cout<< "The element 10 already exists in hm1\n with a key value of"
            << "((pr.first) -> first)= "<<(pr.first)-> first
            << "."<< endl;
    }

    // The hint version of insert
    hm1.insert(--hm1.end(), Int_Pair(5, 50));

    cout<< "After the insertions, the elements of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << " " << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    hm2.insert(Int_Pair(10, 100));

    // The templatized version inserting a range
    hm2.insert( ++hm1.begin(), --hm1.end() );

    cout<< "After the insertions, the elements of hm2 are:";
    for (hm2_pIter = hm2.begin(); hm2_pIter != hm2.end(); hm2_pIter++)
        cout << endl << " " << hm2_pIter -> first << " => "
             << hm2_pIter->second;
    cout << endl;

    // The templatized versions move constructing elements
    hash_map<int, string> hm3, hm4;
    pair<int, string> is1(1, "a"), is2(2, "b");

    hm3.insert(move(is1));
    cout << "After the move insertion, hm3 contains:" << endl
      << " " << hm3.begin()->first
      << " => " << hm3.begin()->second
      << endl;

    hm4.insert(hm4.begin(), move(is2));
    cout << "After the move insertion, hm4 contains:" << endl
      << " " << hm4.begin()->first
      << " => " << hm4.begin()->second
      << endl;
}
```

```Output
The original elements (Key => Value) of hm1 are:
 1 => 10
 2 => 20
 3 => 30
 4 => 40
The element 10 already exists in hm1
 with a key value of((pr.first) -> first)= 1.
After the insertions, the elements of hm1 are:
 1 => 10
 2 => 20
 3 => 30
 4 => 40
 5 => 50
After the insertions, the elements of hm2 are:
 2 => 20
 10 => 100
 3 => 30
 4 => 40
After the move insertion, hm3 contains:
 1 => a
After the move insertion, hm4 contains:
 2 => b
```

## <a name="iterator"></a>  hash_map::iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ, který poskytuje obousměrné iterator, který může číst nebo upravovat libovolný element v hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Poznámky

**Iterator** definovaný hash_map – body na elementy, které jsou objekty [value_type](#value_type), která je typu **pár\<const klíč, zadejte >,** jejichž první člen klíč elementu a jehož druhý člen, je namapované datum držené elementu.

K dereference **iterator** `Iter` odkazující na element v multimap, použijte **->** operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `Iter`  ->  **první**, což je totéž jako (\* `Iter`). **první**. Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `Iter`  ->  **druhý**, což je totéž jako (\* `Iter`). **druhý**.

Typ **iterator** lze upravit hodnotu elementu.

### <a name="example"></a>Příklad

Viz příklad pro [začít](#begin) příklad toho, jak deklarace a používání **iterator**.

## <a name="key_comp"></a>  hash_map::key_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Načte kopii porovnání objekt použitý k pořadí klíčů v hash_map.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce hash_map – používá k uspořádání jejích elementů.

### <a name="remarks"></a>Poznámky

Definuje objekt uložené – členská funkce

**BOOL – operátor**( **const klíč &** `left` **, const klíč &** `right`);

který vrací **true** Pokud `left` předchází a není rovno `right` v pořadí řazení.

### <a name="example"></a>Příklad

```cpp
// hash_map_key_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_map <int, int, hash_compare<int, less<int> > > hm1;
   hash_map <int, int, hash_compare<int, less<int> > >::key_compare
      kc1 = hm1.key_comp( ) ;

   // Operator stored in kc1 tests order & returns bool value
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true,"
           << "\n where kc1 is the function object of hm1"
           << " of type key_compare." << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false"
           << "\n where kc1 is the function object of hm1"
           << " of type key_compare." << endl;
   }

   hash_map <int, int, hash_compare<int, greater<int> > > hm2;
   hash_map <int, int, hash_compare<int, greater<int> > >
      ::key_compare kc2 = hm2.key_comp( );

   // Operator stored in kc2 tests order & returns bool value
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true,"
           << "\n where kc2 is the function object of hm2"
           << " of type key_compare." << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false,"
           << "\n where kc2 is the function object of hm2"
           << " of type key_compare." << endl;
   }
}
```

## <a name="key_compare"></a>  hash_map::key_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ, který poskytuje funkce objekt, který můžete porovnat dva klíče řazení k určení relativních pořadí dva elementy v mapě.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare` je synonymum pro parametr šablony `Traits`.

Další informace o `Traits` najdete v článku [hash_map – třída](../standard-library/hash-map-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se příklad [key_comp –](#key_comp) příklad toho, jak deklarace a používání `key_compare`.

## <a name="key_type"></a>  hash_map::key_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ popisuje řazení klíče objektu, která se považuje za každý prvek hash_map.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type` je synonymum pro parametr šablony `Key`.

Další informace o `Key`, najdete v části poznámky [hash_map – třída](../standard-library/hash-map-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se příklad [value_type](#value_type) příklad toho, jak deklarace a používání `key_type`.

## <a name="lower_bound"></a>  hash_map::lower_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí iterovat prvním elementem v hash_map s hodnotou klíče, která je rovna nebo větší než je zadaný klíč.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Hodnota klíče argument být porovnána s klíč řazení elementu z hash_map být vyhledán.

### <a name="return-value"></a>Návratová hodnota

[Iterator](#iterator) nebo [const_iterator –](#const_iterator) , který se týká umístění elementu v hash_map, že klíčem, která je rovna nebo větší než argument klíč nebo, který se týká umístění úspěšné poslední element v hash_map, pokud není nalezena žádná shoda pro klíč.

Pokud vrátí hodnotu, která `lower_bound` je přiřazena k `const_iterator`, hash_map objekt nelze změnit. Pokud vrátí hodnotu, která `lower_bound` je přiřazena k **iterator**, objekt hash_map – můžete upravit.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_map_lower_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.lower_bound( 2 );
   cout << "The first element of hash_map hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1. lower_bound ( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // An element at a specific location in the hash_map can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1. lower_bound ( hm1_AcIter -> first );
   cout << "The element of hm1 with a key matching "
        << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key of 2 is: 20.
The hash_map hm1 doesn't have an element with a key of 4.
The element of hm1 with a key matching that of the last element is: 30.
```

## <a name="mapped_type"></a>  hash_map::mapped_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ, který představuje typ data uložená v hash_map.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Poznámky

Typ `mapped_type` je synonymum pro parametr šablony `Type`.

Další informace o `Type` najdete v článku [hash_map – třída](../standard-library/hash-map-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se příklad [value_type](#value_type) příklad toho, jak deklarace a používání `key_type`.

## <a name="max_size"></a>  hash_map::max_size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí maximální délka hash_map.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možné délku hash_map.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_map_max_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: size_type i;

   i = hm1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="op_at"></a>  hash_map::Operator]

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vloží do elementu `hash_map` se zadanou hodnotou klíče.

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`key`|Hodnota klíče elementu, který chcete vložit.|

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu dat vloženého prvku.

### <a name="remarks"></a>Poznámky

Pokud není nalezena hodnota klíče argumentu, je vložen spolu s výchozí hodnotou datového typu.

`operator[]` slouží k vložení prvků do `hash_map m` pomocí

`m[ key] = DataValue`;

kde DataValue je hodnota `mapped_type` elementu s hodnotou klíče `key`.

Při použití `operator[]` Pokud chcete vložit elementy, vrácený odkaz neindikuje, zda je vložení změna dříve vytvořený element nebo vytvořením nové. Členské funkce [najít](../standard-library/map-class.md#find) a [vložit](../standard-library/map-class.md#insert) slouží k určení, zda element se zadaným klíčem již nachází před vložení.

### <a name="example"></a>Příklad

```cpp
// hash_map_op_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;
   hash_map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a hash_map using the operator[] member function
   hm1[ 1 ] = 10;

   // Compare other ways to insert objects into a hash_map
   hm1.insert ( hash_map <int, int> :: value_type ( 2, 20 ) );
   hm1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   hm1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   hm1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // opperator[] will also insert by moving a key
   hash_map <string, int> hm2;
   string str("a");
   hm2[move(str)] = 1;
   cout << "The moved key is " << hm2.begin()->first
      << ", with value " << hm2.begin()->second << endl;
}
```

## <a name="op_eq"></a>  hash_map::Operator =

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Elementy hash_map – nahradí kopii jiného hash_map.

```cpp
hash_map& operator=(const hash_map& right);

hash_map& operator=(hash_map&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`right`|[Hash_map – třída](../standard-library/hash-map-class.md) se zkopírují `hash_map`.|

### <a name="remarks"></a>Poznámky

Po vymazání v žádné stávající elementy `hash_map`, `operator=` buď kopíruje nebo přesouvá obsah `right` do `hash_map`.

### <a name="example"></a>Příklad

```cpp
// hash_map_operator_as.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map<int, int> v1, v2, v3;
   hash_map<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
}
```

## <a name="pointer"></a>  hash_map::Pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ, který poskytuje ukazatel na prvek v hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ **ukazatel** lze upravit hodnotu elementu.

Ve většině případů [iterator](#iterator) se má použít pro přístup k elementům v hash_map objektu.

## <a name="rbegin"></a>  hash_map::rbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí iterator adresování prvním elementem v invertovaných hash_map.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Iterator zpětné obousměrného adresování prvním elementem v invertovaných hash_map nebo řešení, co je posledním prvkem v unreversed hash_map.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s odstínech hash_map – stejně jako [začít](#begin) se používá s hash_map.

Pokud vrátí hodnotu, která `rbegin` je přiřazena k [const_reverse_iterator –](#const_reverse_iterator), pak hash_map objekt nelze změnit. Pokud vrátí hodnotu, která `rbegin` je přiřazena k [reverse_iterator –](#reverse_iterator), pak objekt hash_map – můžete upravit.

`rbegin` můžete použít k iteraci v rámci hash_map zpětné.

### <a name="example"></a>Příklad

```cpp
// hash_map_rbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: reverse_iterator hm1_rIter;
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rbegin( );
   cout << "The first element of the reversed hash_map hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_map in a forward order
   cout << "The hash_map is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_map in a reverse order
   cout << "The reversed hash_map is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_map element can be erased by dereferencing to its key
   hm1_rIter = hm1.rbegin( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_map is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_map hm1 is 3.
The hash_map is: 1 2 3 .
The reversed hash_map is: 3 2 1 .
After the erasure, the first element in the reversed hash_map is 2.
```

## <a name="reference"></a>  hash_map::Reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ, který obsahuje odkaz na element uložené v hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_map_reference.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of first element in the hash_map is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_map is 1.
The data value of first element in the hash_map is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>  hash_map::rend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí iterátor, který řeší úspěšné posledním prvkem v invertovaných hash_map – umístění.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Iterator zpětné obousměrného, která řeší umístění úspěšné posledním prvkem v invertovaných hash_map (umístění, které měl před prvním elementem v unreversed hash_map).

### <a name="remarks"></a>Poznámky

`rend` se používá s odstínech hash_map – stejně jako [end](#end) se používá s hash_map.

Pokud vrátí hodnotu, která `rend` je přiřazena k [const_reverse_iterator –](#const_reverse_iterator), pak hash_map objekt nelze změnit. Pokud vrátí hodnotu, která `rend` je přiřazena k [reverse_iterator –](#reverse_iterator), pak objekt hash_map – můžete upravit.

`rend` slouží k testování, aby se jestli zpětné iterator dosáhne konce své hash_map.

Hodnoty vrácené `rend` by neměl být vyhodnoceny odkazy.

### <a name="example"></a>Příklad

```cpp
// hash_map_rend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: reverse_iterator hm1_rIter;
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "The last element of the reversed hash_map hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_map in a forward order
   cout << "The hash_map is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( );
   hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_map in a reverse order
   cout << "The reversed hash_map is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( );
      hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_map element can be erased by dereferencing to its key
   hm1_rIter = --hm1.rend( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed hash_map is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_map hm1 is 1.
The hash_map is: 1 2 3 .
The reversed hash_map is: 3 2 1 .
After the erasure, the last element in the reversed hash_map is 2.
```

## <a name="reverse_iterator"></a>  hash_map::reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ, který poskytuje obousměrné iterator, které můžou číst nebo upravit v invertovaných hash_map – element.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` nelze změnit hodnotu elementu a je použít k iteraci v rámci hash_map pozpátku.

`reverse_iterator` Definovaný hash_map – body na elementy, které jsou objekty [value_type](#value_type), která je typu **pár\<const klíč, zadejte >**, jehož první člen je klíčem k elementu a jejichž sekundu člen je namapované datum uchovávat elementem.

K dereference `reverse_iterator` `rIter` odkazující na prvek v hash_map, použijte -> – operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `rIter`  ->  **první**, což je totéž jako (\* `rIter`). **první**. Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `rIter`  ->  **druhý**, což je totéž jako (\* `rIter`). **první**.

### <a name="example"></a>Příklad

Podívejte se příklad [rbegin –](#rbegin) příklad toho, jak deklarace a používání `reverse_iterator`.

## <a name="size"></a>  hash_map::size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí počet prvků hash_map.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka hash_map.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_map::size – členská funkce.

```cpp
// hash_map_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1, hm2;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    i = hm1.size();
    cout << "The hash_map length is " << i << "." << endl;

    hm1.insert(Int_Pair(2, 4));
    i = hm1.size();
    cout << "The hash_map length is now " << i << "." << endl;
}
```

```Output
The hash_map length is 1.
The hash_map length is now 2.
```

## <a name="size_type"></a>  hash_map::size_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ celé číslo bez znaménka, která představuje počet elementů ve hash_map –.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Podívejte se příklad [velikost](#size) příklad toho, jak deklarace a používání `size_type`

## <a name="swap"></a>  hash_map::swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Elementy dvě hash_maps výměny.

```cpp
void swap(hash_map& right);
```

### <a name="parameters"></a>Parametry

`right` Hash_map – argument poskytování elementy pro si místo se hash_map cíl.

### <a name="remarks"></a>Poznámky

Členská funkce by způsobila neplatnost žádné odkazy, ukazatele nebo iterátory, které určit elementů ve dvou hash_maps, jehož elementy jsou během výměny.

### <a name="example"></a>Příklad

```cpp
// hash_map_swap.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   hash_map <int, int>::iterator hm1_Iter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm2.insert ( Int_Pair ( 10, 100 ) );
   hm2.insert ( Int_Pair ( 20, 200 ) );
   hm3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   // hm2 is said to be the argument hash_map;
   // hm1 is said to be the target hash_map
   hm1.swap( hm2 );

   cout << "After swapping with hm2, hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hm1, hm3 );

   cout << "After swapping with hm3, hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original hash_map hm1 is: 10 20 30.
After swapping with hm2, hash_map hm1 is: 100 200.
After swapping with hm3, hash_map hm1 is: 300.
```

## <a name="upper_bound"></a>  hash_map::upper_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí iterovat prvním elementem v hash_map, pomocí klíče s hodnotou, která je větší než je zadaný klíč.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Hodnota argumentu klíče který se má porovnat s hodnotou klíče řazení elementu z hash_map být vyhledán.

### <a name="return-value"></a>Návratová hodnota

[Iterator](#iterator) nebo [const_iterator –](#const_iterator) , který se týká umístění elementu v hash_map, která s klíčem, který je větší než klíč argument, nebo že řeší úspěšné posledním prvkem v umístění hash_map –, pokud není nalezena žádná shoda pro klíč.

Pokud návratová hodnota je přiřazen k `const_iterator`, hash_map objekt nelze změnit. Pokud návratová hodnota je přiřazen k **iterator**, objekt hash_map – můžete upravit.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_map_upper_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.upper_bound( 2 );
   cout << "The first element of hash_map hm1 with a key "
        << "greater than 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   hm1_RcIter = hm1. upper_bound ( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key > 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_map can be found
   // using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.begin( );
   hm1_RcIter = hm1. upper_bound ( hm1_AcIter -> first );
   cout << "The 1st element of hm1 with a key greater than "
        << "that\n of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key greater than 2 is: 30.
The hash_map hm1 doesn't have an element with a key greater than 4.
The 1st element of hm1 with a key greater than that
 of the initial element of hm1 is: 20.
```

## <a name="value_comp"></a>  hash_map::value_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Vrátí objekt funkce, který určuje pořadí prvků v hash_map tak, že porovnáte jejich hodnoty klíče.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce porovnání hash_map – používá k uspořádání jejích elementů.

### <a name="remarks"></a>Poznámky

Pro hash_map *m*, pokud dva elementy *e*1 *(KB*1 *, d*1 *)* a *e*2 *(KB*2 *, d*2 *)* jsou objekty typu [value_type](#value_type), kde *tisíc*1 a *tisíc*2 jsou jejich klíče typu [key_type –](#key_type) a `d`1 a `d`2 jsou jejich data typu [mapped_type –](#mapped_type), pak *m.*  `value_comp` *() (e*1 *, e*2 *)* je ekvivalentní *m.* `key_comp` *() (KB*1 *, tisíc*2 *)*. Definuje objekt uložené – členská funkce

**BOOL – operátor**( **value_type &** `left`, **value_type &** `right`) **;**

která vrací **true** Pokud klíčovou hodnotu `left` předchází a není roven hodnotě klíče `right` v pořadí řazení.

### <a name="example"></a>Příklad

```cpp
// hash_map_value_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_map <int, int, hash_compare<int, less<int> > > hm1;
   hash_map <int, int, hash_compare<int, less<int> > >
   ::value_compare vc1 = hm1.value_comp( );
   pair< hash_map<int,int>::iterator, bool > pr1, pr2;

   pr1= hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );
   pr2= hm1.insert ( hash_map <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *pr1.first, *pr2.first ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1 ( *pr2.first, *pr1.first ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."
           << endl;
   }
}
```

## <a name="value_type"></a>  hash_map::value_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](../standard-library/unordered-map-class.md).

Typ, který představuje typ objektu uloženého ve hash_map.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Poznámky

`value_type` je deklarován jako `pair`  *\< * **const**[key_type –](#key_type), [mapped_type –](#mapped_type)*> * a ne `pair`  **\<key_type –, mapped_type – >** protože asociativní kontejneru klíčů se nesmí měnit pomocí nonconstant iterator nebo odkaz.

### <a name="example"></a>Příklad

```cpp
// hash_map_value_type.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;
   hash_map <int, int> :: key_type key1;
   hash_map <int, int> :: mapped_type mapped1;
   hash_map <int, int> :: value_type value1;
   hash_map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitely to avoid implicit type conversion
   hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a hash_map
   hm1.insert ( cInt2Int ( 2, 20 ) );
   hm1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( hm1.begin( ) -> first );
   mapped1 = ( hm1.begin( ) -> second );

   cout << "The key of first element in the hash_map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the hash_map is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the hash_map is 1.
The data value of first element in the hash_map is 10.
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
```

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
