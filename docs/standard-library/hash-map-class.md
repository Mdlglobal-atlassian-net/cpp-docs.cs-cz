---
title: hash_map – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 4e13402fbff40ff810e71f78f43060cb59f03cd9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441638"
---
# <a name="hash_map-class"></a>hash_map – třída

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Rychle ukládá a načítá data z kolekce, ve které je každý prvek dvojice, která má klíč řazení, jehož hodnota je jedinečná a přidružená hodnota dat.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<pair <const Key, Type>>>
class hash_map
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíčový datový typ, který bude uložen v hash_map.

*Zadejte*\
Typ dat prvku, který bude uložen v hash_map.

\ *vlastností*
Typ, který obsahuje dva objekty funkce, jeden z porovnání třídy může porovnat dvě hodnoty prvků jako klíče řazení pro určení jejich relativního pořadí a funkci hash, která je unárním predikátem mapování hodnot klíčů prvků na nepodepsaná celá čísla typu `size_t`. Tento argument je nepovinný a hash_compare <`Key`. výchozí hodnota je menší <`Key`> >.

\ *přidělování*
Typ, který představuje uložený objekt přidělování, který zapouzdřuje informace o přidělování a navracení paměti hash_map. Tento argument je nepovinný a výchozí hodnota je\<párování < const `Key`, `Type`> >.

## <a name="remarks"></a>Poznámky

Hash_map je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Hash, protože jeho prvky jsou seskupeny do kontejnerů na základě hodnoty funkce hash použité pro klíčové hodnoty prvků.

- Jedinečný v tom smyslu, že každý z jeho prvků musí mít jedinečný klíč.

- Kontejner asociativních párů, protože jeho prvky hodnoty dat se liší od hodnot klíčů.

- Šablona třídy, protože funkce, které poskytuje, jsou obecné a nezávisle na konkrétním typu dat obsažených jako elementy nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Hlavní výhodou použití algoritmu hash pro řazení je vyšší efektivita; úspěšné hashování provádí vložení, odstranění a vyhledá v konstantním průměrném čase v porovnání s časem, který je úměrný logaritmu počtu prvků v kontejneru pro řazení technik. Hodnota prvku v hash_map, ale ne jeho přidružená hodnota klíče, může být změněna přímo. Namísto toho hodnoty klíčů přidružené ke starým prvkům musí být odstraněny a vloženy nové hodnoty klíče související s novými prvky.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Asociativní kontejnery s algoritmem hash jsou optimalizované pro operace vyhledávání, vkládání a odebírání. Členské funkce, které explicitně podporují tyto operace, jsou efektivní při použití s dobře navrženou funkcí hash a jejich provádění v čase s průměrnou konstantou a nezávisle na počtu prvků v kontejneru. Dobře navržená funkce hash vytváří jednotnou distribuci hodnot hash a minimalizuje počet kolizí, kde je zřejmé, že se vyskytne při mapování jedinečných klíčových hodnot na stejnou hodnotu hash. V nejhorším případě s nejhorší možnou funkcí hash je počet operací úměrný počtu prvků v sekvenci (lineární čas).

Hash_map by měl být asociativní kontejner výběru, pokud podmínky přidružování hodnot k jejich klíčům jsou splněné aplikací. Model pro tento typ struktury je uspořádaný seznam jednoznačně se vyskytujících klíčových slov s přidruženými řetězcovými hodnotami, které poskytují, říká, definice. Pokud místo toho měla slova více než jednu správnou definici, takže klíče nebyly jedinečné, pak hash_multimap by měl být zvoleným kontejnerem. Pokud na druhé straně je jenom uložený seznam slov, hash_set by byl správným kontejnerem. Pokud bylo povoleno více výskytů slov, bude hash_multiset příslušná struktura kontejneru.

Hash_map řadí sekvenci, kterou ovládá, voláním uloženého objektu zatřiďovacích *vlastností* třídy [value_compare](../standard-library/value-compare-class.md). K tomuto uloženému objektu je možné přistupovat voláním členské funkce [key_comp](#key_comp). Takový objekt funkce se musí chovat stejně jako objekt třídy [hash_compare](../standard-library/hash-compare-class.md)< klíč, méně\<klíče > >. Konkrétně pro všechny hodnoty *klíče* typu *klíč*, volání `Traits`(`Key`) poskytuje distribuci hodnot typu `size_t`.

Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát f (x y) je objekt funkce, který má dva objekty argumentu `x` a `y` a návratovou hodnotu **true** nebo **false**. Řazení uložené na hash_map je přísné slabé seřazení, pokud je binární predikát Nereflexivní, antisymetrický a tranzitivní a je-li ekvivalence tranzitivní, kde jsou dva objekty x a y definovány jako ekvivalentní, když mají hodnoty f (x, y) i f (y, x) hodnotu false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

Skutečné pořadí prvků v řízené sekvenci závisí na funkci hash, funkci řazení a aktuální velikosti zatřiďovací tabulky uložené v objektu kontejneru. Nelze určit aktuální velikost zatřiďovací tabulky, takže nemůžete obecné předpovědět pořadí prvků v řízené sekvenci. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Iterátor poskytnutý hash_map třídou je obousměrný iterátor, ale členské funkce třídy [vkládají](#insert) a [hash_map](#hash_map) mají verze, které přebírají jako parametry šablony slabší vstupní iterátor, jehož požadavky na funkce jsou více minimální než ty, které jsou zaručeny třídou Obousměrných iterátorů. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální sada funkcí, ale je dostatečná pro to, aby bylo možné mluvit smysluplně o rozsahu iterátorů `[First, Last)` v kontextu funkcí členských tříd.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[hash_map](#hash_map)|Vytvoří `hash_map`, který je prázdný nebo který je kopií všech nebo částí jiných `hash_map`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje třídu `allocator` pro objekt `hash_map`.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `const` prvek v `hash_map`.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na prvek **const** v `hash_map`.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na prvek **const** uložený v `hash_map` pro čtení a provádění operací **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst libovolný prvek **const** v `hash_map`.|
|[difference_type](#difference_type)|Typ se znaménkem typu Integer, který lze použít k reprezentaci počtu prvků `hash_map` v rozsahu mezi prvky, na které odkazují iterátory.|
|[iterátor](#iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v `hash_map`.|
|[key_compare](#key_compare)|Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v `hash_map`.|
|[key_type](#key_type)|Typ popisuje objekt třídicího klíče, který představuje jednotlivé prvky `hash_map`.|
|[mapped_type](#mapped_type)|Typ, který představuje datový typ uložený v `hash_map`.|
|[ukazatele](#pointer)|Typ, který poskytuje ukazatel na prvek v `hash_map`.|
|[odkaz](#reference)|Typ, který poskytuje odkaz na prvek uložený v `hash_map`.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném `hash_map`.|
|[size_type](#size_type)|Typ unsigned integer, který může představovat počet prvků v `hash_map`.|
|[value_type](#value_type)|Typ, který poskytuje objekt funkce, který může porovnat dva prvky jako klíče řazení pro určení jejich relativního pořadí v `hash_map`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Počínaje](#at)|Vyhledá prvek v `hash_map` se zadanou hodnotou klíče.|
|[ifunctiondiscovery](#begin)|Vrátí iterátor adresující první prvek v `hash_map`.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor adresující první prvek v `hash_map`.|
|[cend](#cend)|Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v `hash_map`.|
|[jejich](#clear)|Smaže všechny prvky `hash_map`.|
|[count](#count)|Vrátí počet prvků v `hash_map`, jejichž klíč odpovídá klíči určenému parametrem.|
|[crbegin –](#crbegin)|Vrátí konstantní iterátor adresující první prvek v obráceném `hash_map`.|
|[crend](#crend)|Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v obráceném `hash_map`.|
|[emplace](#emplace)|Vloží prvek konstruovaný na místo do `hash_map`.|
|[emplace_hint](#emplace_hint)|Vloží prvek konstruovaný na místo do `hash_map`s pomocným parametrem umístění.|
|[obsahovat](#empty)|Testuje, zda je `hash_map` prázdné.|
|[účelu](#end)|Vrátí iterátor, který adresuje umístění následující po posledním prvku v `hash_map`.|
|[equal_range](#equal_range)|Vrátí dvojici iterátorů v uvedeném pořadí na první prvek v `hash_map` s klíčem, který je větší než zadaný klíč a na první prvek v `hash_map` s klíčem, který je roven nebo větší než klíč.|
|[ověřování](#erase)|Odebere prvek nebo rozsah prvků v `hash_map` ze zadané pozice.|
|[find](#find)|Vrátí iterátor adresující umístění elementu v `hash_map`, který má klíč shodný se zadaným klíčem.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu `allocator`, který se používá k vytvoření `hash_map`.|
|[zadat](#insert)|Vloží prvek nebo rozsah prvků do `hash_map`.|
|[key_comp](#key_comp)|Vrátí iterátor na první prvek v `hash_map` s hodnotou klíče, která je větší nebo rovna hodnotě zadaného klíče.|
|[lower_bound](#lower_bound)|Vrátí iterátor na první prvek v `hash_map` s hodnotou klíče, která je větší nebo rovna hodnotě zadaného klíče.|
|[max_size](#max_size)|Vrátí maximální délku `hash_map`.|
|[rbegin](#rbegin)|Vrátí iterátor adresující první prvek v obráceném `hash_map`.|
|[rend](#rend)|Vrátí iterátor, který adresuje umístění následující po posledním prvku v obráceném `hash_map`.|
|[hodnota](#size)|Vrátí počet prvků v `hash_map`.|
|[adresu](#swap)|Vyměňuje prvky dvou `hash_map`s.|
|[upper_bound](#upper_bound)|Vrátí iterátor na první prvek v `hash_map`, který má hodnotu klíče, která je větší než zadaný klíč.|
|[value_comp](#value_comp)|Načte kopii objektu porovnání, která se používá k seřazení hodnot prvků v `hash_map`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[podnikatel&#91;&#93;](#op_at)|Vloží prvek do `hash_map` se zadanou hodnotou klíče.|
|[hash_map:: operator =](#op_eq)|Nahradí prvky `hash_map` kopií jiného `hash_map`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<hash_map >

**Obor názvů:** stdext

## <a name="allocator_type"></a>hash_map:: allocator_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ, který představuje třídu přidělování pro objekt hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Příklad

Příklad použití `allocator_type`naleznete v tématu příklad pro [get_allocator](#get_allocator) .

## <a name="at"></a>hash_map:: at

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vyhledá prvek v hash_map se zadanou hodnotou klíče.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*key*|Hodnota klíče elementu, který má být nalezen.|

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu dat nalezeného prvku.

### <a name="remarks"></a>Poznámky

Pokud hodnota klíče argumentu nebyla nalezena, funkce vyvolá objekt třídy [Out_of_range třídy](../standard-library/out-of-range-class.md).

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

## <a name="begin"></a>hash_map:: begin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí iterátor adresující první prvek v hash_map.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který adresuje první prvek v hash_map nebo umístění, které je úspěšně prázdné hash_map.

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

## <a name="cbegin"></a>hash_map:: cbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí konstantní iterátor adresující první prvek v hash_map.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní obousměrný iterátor, který adresuje první prvek v [hash_map](../standard-library/hash-map-class.md) nebo umístění, které je úspěšně prázdné `hash_map`.

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

## <a name="cend"></a>hash_map:: cend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v hash_map.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní obousměrný iterátor, který adresuje umístění následující po posledním prvku v [hash_map](../standard-library/hash-map-class.md). Pokud je `hash_map` prázdné, `hash_map::cend == hash_map::begin`.

### <a name="remarks"></a>Poznámky

`cend` slouží k otestování, zda iterátor dosáhl konce jeho `hash_map`.

Hodnota vrácená `cend` by neměla být zpětně odkazovaná.

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

## <a name="clear"></a>hash_map:: Clear

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Smaže všechny prvky hash_map.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce hash_map:: Clear.

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

## <a name="const_iterator"></a>hash_map:: const_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst prvek **const** v hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít pro úpravu hodnoty prvku.

`const_iterator` definované pomocí hash_map odkazuje na prvky, které jsou objekty [value_type](#value_type), které jsou typu `pair< const Key, Type >`, jejichž prvním členem je klíč k elementu a jehož druhým členem je mapované datum uchovávané prvkem.

Chcete-li přesměrovat `const_iterator` `cIter` ukazovat na prvek v hash_map, použijte operátor `->`.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `cIter->first`, který je ekvivalentní `(*cIter).first`. Pro přístup k hodnotě mapovaného pole Datum elementu použijte `cIter->second`, který je ekvivalentní `(*cIter).second`.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) příkladu pomocí `const_iterator`.

## <a name="const_pointer"></a>hash_map:: const_pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ, který poskytuje ukazatel na prvek **const** v hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít pro úpravu hodnoty prvku.

Ve většině případů by měl být použit [iterátor](#iterator) pro přístup k prvkům v objektu hash_map.

## <a name="const_reference"></a>hash_map:: const_reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ, který poskytuje odkaz na prvek **const** uložený v hash_map pro čtení a provádění operací **const** .

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

## <a name="const_reverse_iterator"></a>hash_map:: const_reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst libovolný prvek **const** v hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse)iterator const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a používá se k iterování skrze hash_map v opačném případě.

`const_reverse_iterator` definované pomocí hash_map Points na prvky, které jsou objekty [value_type](#value_type), které jsou typu `pair`\< **const Key, Type**>, jehož prvním členem je klíč k elementu a druhý člen je mapované datum uchovávané prvkem.

Chcete-li přesměrovat `const_reverse_iterator` `crIter` ukazovat na prvek v hash_map, použijte operátor **->** .

Chcete-li získat přístup k hodnotě klíče pro element, použijte **nejprve**`crIter` -> , který je ekvivalentní (\* `crIter`) **. First**. Pro přístup k hodnotě mapovaného pole pro prvek použijte `crIter` -> **Second**, který je ekvivalentní (\* `crIter`). **nejprve**.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a použít `const_reverse_iterator`, naleznete v příkladu pro [rend](#rend) .

## <a name="count"></a>hash_map:: Count

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí počet prvků v hash_map, jejichž klíč odpovídá klíči určenému parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Hodnota klíče prvků, které mají být porovnány od hash_map.

### <a name="return-value"></a>Návratová hodnota

1 Pokud hash_map obsahuje element, jehož klíč řazení odpovídá klíči parametru; 0, pokud hash_map neobsahuje element se shodným klíčem.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků *x* v rozsahu.

\[ lower_bound (*klíč*), Upper_bound (*klíč*))

což je 0 nebo 1 v případě hash_map, což je jedinečný asociativní kontejner.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce hash_map:: Count.

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

## <a name="crbegin"></a>hash_map:: crbegin –

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí konstantní iterátor adresující první prvek v obráceném hash_map.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor, který adresuje první prvek v obráceném [hash_map](../standard-library/hash-map-class.md) nebo řeší, co byl posledním prvkem v neobráceném `hash_map`.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s obráceným hash_map stejně jako [Begin](#begin) se používá s `hash_map`.

S návratovou hodnotou `crbegin`nelze změnit objekt `hash_map`.

`crbegin` lze použít k iteraci `hash_map` zpět.

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

## <a name="crend"></a>hash_map:: crend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v obráceném hash_map.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor, který adresuje umístění následující po posledním prvku v obráceném [hash_map](../standard-library/hash-map-class.md) (umístění, které předchází prvnímu prvku v neobráceném `hash_map`).

### <a name="remarks"></a>Poznámky

`crend` se používá s obráceným `hash_map` stejně jako [hash_map:: end](#end) se používá s `hash_map`.

S návratovou hodnotou `crend`nelze změnit objekt `hash_map`.

`crend` lze použít k otestování, zda reverzní iterátor dosáhl konce jeho `hash_map`.

Hodnota vrácená `crend` by neměla být zpětně odkazovaná.

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

## <a name="difference_type"></a>hash_map::d ifference_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ se znaménkem typu Integer, který lze použít k reprezentaci počtu prvků hash_map v rozsahu mezi prvky, na které odkazují iterátory.

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

## <a name="emplace"></a>hash_map:: emplace

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vloží prvek konstruovaný na místo do hash_map.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*počítává*|Hodnota, která se používá k přesunutí konstrukce elementu, který má být vložen do [hash_map](../standard-library/hash-map-class.md) , pokud `hash_map` již tento prvek neobsahuje (nebo obecněji je prvek, jehož klíč je ekvivalentně seřazen).|

### <a name="return-value"></a>Návratová hodnota

Členská funkce `emplace` vrátí dvojici, jejíž logická komponenta vrátí hodnotu true, pokud bylo provedeno vložení, a hodnotu false, pokud `hash_map` již obsahovala element, jehož klíč má ekvivalentní hodnotu v pořadí řazení a jehož komponenta iterátoru vrátí adresu, kam byl vložen nový prvek nebo kde byl prvek již umístěn.

Chcete-li získat přístup k součásti iterátoru páru `pr` vráceného touto členskou funkcí, použijte `pr.first`a k jeho zpětnému odkazování použijte `*(pr.first)`. Chcete-li získat přístup ke komponentě **bool** páru `pr` vrácený touto členskou funkcí, použijte `pr.second`a k jejímu odkázání použijte `*(pr.second)`.

### <a name="remarks"></a>Poznámky

[Hash_map:: value_type](#value_type) elementu je dvojice, takže hodnota elementu bude seřazená dvojice s první komponentou, která se rovná hodnotě klíče a druhá komponenta se rovná hodnotě dat elementu.

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

## <a name="emplace_hint"></a>hash_map:: emplace_hint

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vloží prvek konstruovaný na místo do hash_map s pomocným parametrem umístění.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*počítává*|Hodnota, která se používá k přesunutí konstrukce elementu, který má být vložen do [hash_map](../standard-library/hash-map-class.md) , pokud `hash_map` již tento prvek neobsahuje (nebo obecněji je prvek, jehož klíč je ekvivalentně seřazen).|
|*_Where*|Nápověda týkající se místa, kde lze začít hledat správný bod vložení.|

### <a name="return-value"></a>Návratová hodnota

Členská funkce [hash_multimap:: emplace](../standard-library/hash-multimap-class.md#emplace) vrací iterátor, který odkazuje na pozici, kam byl nový element vložen do `hash_map`nebo kde se nachází existující element s ekvivalentním řazením.

### <a name="remarks"></a>Poznámky

[Hash_map:: value_type](#value_type) elementu je dvojice, takže hodnota elementu bude seřazená dvojice s první komponentou, která se rovná hodnotě klíče a druhá komponenta se rovná hodnotě dat elementu.

Vložení se může vyskytnout v konstantním čase, namísto logaritmické doby, pokud se kurzor okamžitě *_Where*.

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

## <a name="empty"></a>hash_map:: Empty

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Testuje, zda je hash_map prázdné.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je hash_map prázdné. **false** , pokud je hash_map neprázdné.

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

## <a name="end"></a>hash_map:: end

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí iterátor, který adresuje umístění následující po posledním prvku v hash_map.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který adresuje umístění následující po posledním prvku v hash_map. Pokud je hash_map prázdné, pak hash_map:: end = = hash_map:: begin.

### <a name="remarks"></a>Poznámky

`end` slouží k otestování, zda iterátor dosáhl konce jeho hash_map.

Hodnota vrácená `end` by neměla být zpětně odkazovaná.

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

## <a name="equal_range"></a>hash_map:: equal_range

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí dvojici iterátorů v uvedeném pořadí na první prvek v hash_map s klíčem, který je větší než zadaný klíč a na první prvek v hash_map s klíčem, který je roven nebo větší než klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Hodnota klíče argumentu, která má být porovnána s klíčem řazení prvku z vyhledaného hash_map.

### <a name="return-value"></a>Návratová hodnota

Pár iterátorů, jako je první [lower_bound](#lower_bound) klíče a druhý je [Upper_bound](#upper_bound) klíče.

Chcete-li získat přístup k prvnímu iterátoru páru `pr` vráceném členskou funkcí, použijte `pr`. **nejprve** a pro zpětnou vazbu dolního iterátoru použijte \*(`pr`. **první**). Pro přístup k druhému iterátoru páru `pr` vráceném členskou funkcí použijte `pr`. **sekundy** a pro zpětnou vazbu horního iterátoru, použijte \*(`pr`. **sekundy**).

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
        << "matching the 2nd element of the pair"
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

## <a name="erase"></a>hash_map:: Erase

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Odebere prvek nebo rozsah prvků v hash_map ze zadané pozice nebo odstraní prvky, které odpovídají zadanému klíči.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozice prvku, který má být odebrán z hash_map.

*první*\
Pozice prvního prvku byla odebrána z hash_map.

*poslední*\
Pozice bezprostředně za posledním prvkem odebraným z hash_map.

\ *klíčů*
Hodnota klíče prvků, které mají být odebrány z hash_map.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který určuje první prvek zbývající za odebranými prvky, nebo ukazatel na konec hash_map, pokud žádný takový prvek neexistuje.

Třetí členská funkce vrátí počet prvků, které byly odebrány z hash_map.

### <a name="remarks"></a>Poznámky

Členské funkce nikdy nevyvolají výjimku.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce hash_map:: Erase.

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

## <a name="find"></a>hash_map:: Find

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí iterátor adresující umístění elementu v hash_map, který má klíč shodný se zadaným klíčem.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Hodnota klíče, která má být porovnána klíčem řazení prvku z hledaného hash_map.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který adresuje umístění elementu se zadaným klíčem, nebo umístění, které následuje po posledním prvku v hash_map, pokud se pro klíč nenajde shoda.

### <a name="remarks"></a>Poznámky

`find` Vrátí iterátor, který adresuje prvek v hash_map, jehož klíč řazení je ekvivalentem klíče argumentu v binárním predikátu, který vystaví řazení na základě vztahu menšího, než je srovnatelnost.

Pokud je vrácená hodnota `find` přiřazená k [const_iterator](#const_iterator), objekt hash_map nelze upravit. Pokud je vrácená hodnota `find` přiřazena [iterátoru](#iterator), lze objekt hash_map upravit.

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

## <a name="get_allocator"></a>hash_map:: get_allocator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí kopii objektu přidělování, která se používá k vytvoření hash_map.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný hash_map.

### <a name="remarks"></a>Poznámky

Přidělování pro třídu hash_map určují, jak Třída spravuje úložiště. Výchozí přidělující třídy kontejnerů C++ standardní knihovny jsou dostačující pro většinu programovacích potřeb. Psaní a používání vlastního třídy přidělování je pokročilým C++ tématem.

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

## <a name="hash_map"></a>hash_map:: hash_map

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vytvoří hash_map, který je prázdný nebo je kopií všech nebo částí jiných hash_map.

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
|*VŠ*|Třída přidělování úložiště, která se má použít pro tento objekt hash_map, který má výchozí hodnotu `Allocator`.|
|*Zajištění*|Funkce porovnání typu const `Traits` slouží k uspořádání prvků v hash_map, které mají výchozí hodnotu `hash_compare`.|
|*Kliknutím*|Hash_map, ze kterého má být vytvořená mapa kopie.|
|*První*|Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.|
|*Posledního*|Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.|
|*IList*|Initializer_list|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají typ objektu přidělování, který spravuje úložiště paměti pro hash_map a může být později vrácen voláním [get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují své hash_map.

Všechny konstruktory ukládají objekt funkce typu `Traits`, který se používá k navázání objednávky mezi klíči hash_map a které mohou být později vráceny voláním [key_comp](#key_comp).

První tři konstruktory určují prázdné počáteční hash_map, navíc druhý určuje typ funkce porovnání (*comp*), která se použije při stanovení pořadí prvků, a třetí explicitně určuje typ přidělujícího objektu (*Al*), který se má použít. Klíčové slovo **Explicit** potlačí určité druhy automatických převodů typu.

Čtvrtý konstruktor určuje kopii hash_map *vpravo*.

Následující tři konstruktory kopírují rozsah `[First, Last)` hash_map se zvýšením explicitního určení typu funkce porovnání třídy `Traits` a přidělování.

Poslední konstruktor přesune *pravé*hash_map.

## <a name="insert"></a>hash_map:: INSERT

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vloží prvek nebo rozsah prvků do hash_map.

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
|*počítává*|Hodnota prvku, který má být vložen do hash_map, pokud hash_map již tento prvek neobsahuje (nebo všeobecně obecně, element, jehož klíč je ekvivalentně seřazen).|
|*_Where*|Nápověda týkající se místa, kde lze začít hledat správný bod vložení.|
|*první*|Pozice prvního prvku, který má být zkopírován z hash_map.|
|*posledního*|Pozice bezprostředně za posledním prvkem, který má být zkopírován z hash_map.|

### <a name="return-value"></a>Návratová hodnota

První `insert` členská funkce vrátí dvojici, jejíž logická komponenta vrátí hodnotu true, pokud bylo provedeno vložení, a hodnotu false, pokud hash_map již obsahovala element, jehož klíč měl ekvivalentní hodnotu v pořadí řazení a jehož komponenta iterátoru vrátí adresu, kam byl vložen nový prvek nebo kde již byl prvek umístěn.

Pro přístup k součásti iterátoru páru `pr` vrácené touto členskou funkcí použijte `pr`. **nejprve**a k jejímu odkázání použijte \*(`pr`. **první**). Chcete-li získat přístup ke komponentě **bool** páru `pr` vrácená touto členskou funkcí, použijte `pr`. za **druhé**a pro její odkázání použijte \*(`pr`. **sekundy**).

Druhá členská funkce `insert`, verze nápovědy, vrátí iterátor, který odkazuje na pozici, kam byl nový prvek vložen do hash_map.

Poslední dvě `insert` členské funkce se chovají stejně jako první dvě, s tím rozdílem, že přesouvá konstrukce vložené hodnoty.

### <a name="remarks"></a>Poznámky

[Value_type](../standard-library/map-class.md#value_type) prvku je dvojice, takže hodnota elementu bude seřazená dvojice s první komponentou rovnající se hodnotě klíče a druhá komponenta se rovná hodnotě dat elementu.

Vložení se může vyskytnout v konstantním konstantním čase pro verzi pomocného parametru INSERT, namísto logaritmické doby, pokud se bod vložení hned *_Where*.

Třetí členská funkce vloží sekvenci hodnot prvků do hash_map odpovídající každému prvku, který je adresován v rozsahu *[First, Last)* zadané sady.

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

    cout << "The original elements (Key => Value) of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << " " << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    pair< hash_map<int,int>::iterator, bool > pr;
    pr = hm1.insert(Int_Pair(1, 10));

    if (pr.second == true)
    {
        cout << "The element 10 was inserted in hm1 successfully."
            << endl;
    }
    else
    {
        cout << "The element 10 already exists in hm1\n"
            << "with a key value of "
            << "((pr.first) -> first) = " << (pr.first)->first
            << "." << endl;
    }

    // The hint version of insert
    hm1.insert(--hm1.end(), Int_Pair(5, 50));

    cout << "After the insertions, the elements of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    hm2.insert(Int_Pair(10, 100));

    // The templatized version inserting a range
    hm2.insert( ++hm1.begin(), --hm1.end() );

    cout << "After the insertions, the elements of hm2 are:";
    for (hm2_pIter = hm2.begin(); hm2_pIter != hm2.end(); hm2_pIter++)
        cout << endl << hm2_pIter -> first << " => "
             << hm2_pIter->second;
    cout << endl;

    // The templatized versions move constructing elements
    hash_map<int, string> hm3, hm4;
    pair<int, string> is1(1, "a"), is2(2, "b");

    hm3.insert(move(is1));
    cout << "After the move insertion, hm3 contains:" << endl
      << hm3.begin()->first
      << " => " << hm3.begin()->second
      << endl;

    hm4.insert(hm4.begin(), move(is2));
    cout << "After the move insertion, hm4 contains:" << endl
      << hm4.begin()->first
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
with a key value of ((pr.first) -> first) = 1.
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

## <a name="iterator"></a>hash_map:: iterátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Poznámky

`iterator` definované pomocí hash_map Points na prvky, které jsou objekty [value_type](#value_type), které jsou typu **páry\<const key, Type >,** jehož prvním členem je klíč k elementu a druhý člen je mapovaným argumentem, který je držen prvkem.

Chcete-li přesměrovat **iterátor**`Iter` odkazovat na prvek v multimap, použijte operátor `->`.

Chcete-li získat přístup k hodnotě klíče pro element, použijte **nejprve**`Iter` -> , který je ekvivalentní (\* `Iter`). **nejprve**. Pro přístup k hodnotě mapovaného pole pro prvek použijte `Iter` -> **Second**, který je ekvivalentní (\* `Iter`). **sekunda**.

Typ `iterator` lze použít pro úpravu hodnoty prvku.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) pro příklad, jak deklarovat a použít `iterator`.

## <a name="key_comp"></a>hash_map:: key_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Načte kopii objektu porovnání, která se používá k řazení klíčů v hash_map.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který hash_map používá k seřazení jeho prvků.

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci.

**bool – operátor**( **const Key &** `left` **, const Key &** `right`);

Vrátí **hodnotu true** , pokud `left` předchází a není rovna `right` v pořadí řazení.

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

## <a name="key_compare"></a>hash_map:: key_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v mapě.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare` je synonymum pro parametr šablony `Traits`.

Další informace o `Traits` naleznete v tématu [hash_map třídy](../standard-library/hash-map-class.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `key_compare`, naleznete v tématu příklad pro [key_comp](#key_comp) .

## <a name="key_type"></a>hash_map:: key_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ popisuje objekt třídicího klíče, který představuje jednotlivé prvky hash_map.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type` je synonymum pro parametr šablony `Key`.

Další informace o `Key`naleznete v části poznámky v tématu [hash_map třídy](../standard-library/hash-map-class.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `key_type`, naleznete v tématu příklad pro [value_type](#value_type) .

## <a name="lower_bound"></a>hash_map:: lower_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí iterátor na první prvek v hash_map s hodnotou klíče, která je větší nebo rovna hodnotě zadaného klíče.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Hodnota klíče argumentu, která má být porovnána s klíčem řazení prvku z vyhledaného hash_map.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator](#const_iterator) , které řeší umístění elementu v hash_map, který má klíč, který je roven nebo větší než klíč argumentu nebo který řeší umístění, které následuje po posledním prvku v hash_map, pokud se pro klíč nenašly žádné shody.

Pokud je vrácená hodnota `lower_bound` přiřazená k `const_iterator`, objekt hash_map nelze upravit. Pokud je vrácená hodnota `lower_bound` přiřazena k `iterator`, lze objekt hash_map upravit.

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

## <a name="mapped_type"></a>hash_map:: mapped_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ, který představuje datový typ uložený v hash_map.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Poznámky

Typ `mapped_type` je synonymum pro parametr šablony `Type`.

Další informace o `Type` naleznete v tématu [hash_map třídy](../standard-library/hash-map-class.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `key_type`, naleznete v tématu příklad pro [value_type](#value_type) .

## <a name="max_size"></a>hash_map:: max_size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí maximální délku hash_map.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka hash_map.

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

## <a name="op_at"></a>hash_map:: operator [] – operátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vloží prvek do `hash_map` se zadanou hodnotou klíče.

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*key*|Hodnota klíče prvku, který má být vložen.|

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu dat vloženého prvku.

### <a name="remarks"></a>Poznámky

Pokud není nalezena hodnota klíče argumentu, je vložen spolu s výchozí hodnotou datového typu.

`operator[]` lze použít k vložení prvků do `hash_map m` pomocí

`m[ key] = DataValue`;

kde DataValue je hodnota `mapped_type` elementu s klíčovou hodnotou *Key*.

Při použití `operator[]` pro vložení prvků, vrácený odkaz neurčuje, zda vložení mění existující prvek nebo vytváří nový. Členské funkce [find](../standard-library/map-class.md#find) a [INSERT](../standard-library/map-class.md#insert) lze použít k určení, zda je prvek se zadaným klíčem již přítomen před vložením.

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

   // operator[] will also insert by moving a key
   hash_map <string, int> hm2;
   string str("a");
   hm2[move(str)] = 1;
   cout << "The moved key is " << hm2.begin()->first
      << ", with value " << hm2.begin()->second << endl;
}
```

## <a name="op_eq"></a>hash_map:: operator =

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Nahradí prvky hash_map kopií jiného hash_map.

```cpp
hash_map& operator=(const hash_map& right);

hash_map& operator=(hash_map&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Kliknutím*|[Třída hash_map](../standard-library/hash-map-class.md) se kopíruje do `hash_map`.|

### <a name="remarks"></a>Poznámky

Po vymazání všech existujících prvků v `hash_map``operator=` buď zkopírování nebo přesunutí obsahu *přímo* do `hash_map`.

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

## <a name="pointer"></a>hash_map::p ointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ, který poskytuje ukazatel na prvek v hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze použít pro úpravu hodnoty prvku.

Ve většině případů by měl být použit [iterátor](#iterator) pro přístup k prvkům v objektu hash_map.

## <a name="rbegin"></a>hash_map:: rbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí iterátor adresující první prvek v obráceném hash_map.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor, který adresuje první prvek v obráceném hash_map nebo řeší, co byl posledním prvkem v neobráceném hash_map.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s obráceným hash_map stejně jako [Begin](#begin) se používá s hash_map.

Pokud je vrácená hodnota `rbegin` přiřazena k [const_reverse_iterator](#const_reverse_iterator), nelze objekt hash_map změnit. Pokud je vrácená hodnota `rbegin` přiřazena k [reverse_iterator](#reverse_iterator), lze objekt hash_map upravit.

`rbegin` lze použít k iteraci hash_map zpět.

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

## <a name="reference"></a>hash_map:: Reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ, který poskytuje odkaz na prvek uložený v hash_map.

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

## <a name="rend"></a>hash_map:: rend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí iterátor, který adresuje umístění následující po posledním prvku v obráceném hash_map.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Zpětný obousměrný iterátor, který adresuje umístění následující po posledním prvku v obráceném hash_map (umístění, které předchází prvnímu prvku v neobráceném hash_map).

### <a name="remarks"></a>Poznámky

`rend` se používá s obráceným hash_map stejně jako [End](#end) se používá s hash_map.

Pokud je vrácená hodnota `rend` přiřazena k [const_reverse_iterator](#const_reverse_iterator), nelze objekt hash_map změnit. Pokud je vrácená hodnota `rend` přiřazena k [reverse_iterator](#reverse_iterator), lze objekt hash_map upravit.

`rend` lze použít k otestování, zda reverzní iterátor dosáhl konce jeho hash_map.

Hodnota vrácená `rend` by neměla být zpětně odkazovaná.

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

## <a name="reverse_iterator"></a>hash_map:: reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` nemůže změnit hodnotu prvku a používá se k iterování skrze hash_map v opačném případě.

`reverse_iterator` definované pomocí hash_map Points na prvky, které jsou objekty [value_type](#value_type), které jsou typu **páry\<const key, Type >** , jehož prvním členem je klíč k elementu a druhý člen je mapovaným argumentem, který je držen prvkem.

Chcete-li přesměrovat `reverse_iterator` `rIter` ukazovat na prvek v hash_map, použijte operátor->.

Chcete-li získat přístup k hodnotě klíče pro element, použijte **nejprve**`rIter` -> , který je ekvivalentní (\* `rIter`). **nejprve**. Pro přístup k hodnotě mapovaného pole pro prvek použijte `rIter` -> **Second**, který je ekvivalentní (\* `rIter`). **nejprve**.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `reverse_iterator`, naleznete v tématu příklad pro [rbegin](#rbegin) .

## <a name="size"></a>hash_map:: size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí počet prvků v hash_map.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka hash_map.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce hash_map:: size.

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

## <a name="size_type"></a>hash_map:: size_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ unsigned integer, který může představovat počet prvků v hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Viz příklad pro [Velikost](#size) pro příklad, jak deklarovat a použít `size_type`

## <a name="swap"></a>hash_map:: swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vyměňuje prvky dvou hash_maps.

```cpp
void swap(hash_map& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Argument hash_map poskytnutí prvků, které mají být nahrazeny cílovým hash_map.

### <a name="remarks"></a>Poznámky

Členská funkce neověřuje žádné odkazy, ukazatele nebo iterátory, které určují elementy ze dvou hash_maps, jejichž prvky se vyměňují.

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

## <a name="upper_bound"></a>hash_map:: upper_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí iterátor na první prvek v hash_map, který má klíč s hodnotou, která je větší než zadaný klíč.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Hodnota klíče argumentu, která má být porovnána s hodnotou klíče řazení prvku z vyhledaného hash_map.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator](#const_iterator) , které řeší umístění elementu v hash_map s klíčem, který je větší než klíč argumentu, nebo který řeší umístění, které následuje po posledním prvku v hash_map, pokud se pro klíč nenajde žádná shoda.

Pokud je vrácená hodnota přiřazena k `const_iterator`, nelze objekt hash_map změnit. Pokud je vrácená hodnota přiřazena k `iterator`, lze objekt hash_map upravit.

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
   cout << "The 1st element of hm1 with a key greater than that\n"
        << "of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key greater than 2 is: 30.
The hash_map hm1 doesn't have an element with a key greater than 4.
The 1st element of hm1 with a key greater than that
of the initial element of hm1 is: 20.
```

## <a name="value_comp"></a>hash_map:: value_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Vrátí objekt funkce, který určuje pořadí prvků v hash_map porovnáním jejich hodnot klíče.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce porovnání, který hash_map používá k seřazení jeho prvků.

### <a name="remarks"></a>Poznámky

Pro hash_map *m*platí, že pokud jsou dva prvky *E1* (*K1*, *D1*) a *E2* (*K2*, *D2*) objekty typu [value_type](#value_type), kde *K1* a *k2* jsou jejich klíče typu [key_type](#key_type) a *D1* a *D2* jsou jejich data typu [mapped_type](#mapped_type), pak `m.value_comp()(e1, e2)` odpovídá `m.key_comp()(k1, k2)`. Uložený objekt definuje členskou funkci.

`bool operator(value_type& left, value_type& right);`

Vrátí hodnotu **true** , pokud hodnota klíče `left` předchází a není rovna hodnotě klíče `right` v pořadí řazení.

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

## <a name="value_type"></a>hash_map:: value_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](../standard-library/unordered-map-class.md).

Typ, který představuje typ objektu uložený v hash_map.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Poznámky

`value_type` je deklarována jako `pair<const key_type, mapped_type>` a nikoli `pair<key_type, mapped_type>`, protože klíče asociativního kontejneru nelze změnit pomocí nekonstantního iterátoru nebo odkazu.

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
   // explicitly to avoid implicit type conversion
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

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
