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
ms.openlocfilehash: e8c0da199d8a1e9ba388b960fe07ab6ad6fcf4bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375469"
---
# <a name="hash_map-class"></a>hash_map – třída

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Ukládá a načítá data rychle z kolekce, ve kterém každý prvek je pár, který má klíč řazení, jehož hodnota je jedinečná a související hodnotu dat.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<pair <const Key, Type>>>
class hash_map
```

### <a name="parameters"></a>Parametry

*Klíč*\
Datový typ klíče, který má být uložen v hash_map.

*Typ*\
Datový typ prvku, který má být uložen v hash_map.

*Vlastnosti*\
Typ, který obsahuje dva objekty funkce, jeden z třídy porovnat schopen porovnat dvě hodnoty elementu jako klíče řazení k určení jejich relativní pořadí a hash `size_t`funkce, která je unární predikát mapování klíčových hodnot prvků neznatelná celá čísla typu . Tento argument je volitelný `Key`a hash_compare `Key`<, výchozí hodnotou je menší<> > .

*Přidělování*\
Typ, který představuje uložený objekt přidělování, který zapouzdřuje podrobnosti o přidělení hash_map a přidělení paměti. Tento argument je volitelný a výchozí hodnotou\<je alokátor dvojice <const `Key`, `Type`>>.

## <a name="remarks"></a>Poznámky

Hash_map je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Hashed, protože jeho prvky jsou seskupeny do bloků na základě hodnoty funkce hash aplikované na klíčové hodnoty prvků.

- Jedinečný v tom smyslu, že každý z jeho prvků musí mít jedinečný klíč.

- Kontejner asociativních párů, protože jeho prvky hodnoty dat se liší od hodnot klíčů.

- Šablona třídy, protože funkce, které poskytuje, je obecná a tak nezávislá na konkrétním typu dat obsažených jako prvky nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Hlavní výhodou hašování nad tříděním je větší účinnost; úspěšné zapisování provádí vložení, odstranění a najde v konstantní mzda v průměru čas ve srovnání s časem úměrná logaritmu počtu prvků v kontejneru pro řazení techniky. Hodnota prvku v hash_map, ale není jeho přidruženou hodnotou klíče, může být změněna přímo. Namísto toho hodnoty klíčů přidružené ke starým prvkům musí být odstraněny a vloženy nové hodnoty klíče související s novými prvky.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Hashed asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstraňování. Členské funkce, které explicitně podporují tyto operace jsou efektivní při použití s dobře navržené funkce hash, jejich provádění v čase, který je v průměru konstantní a není závislý na počtu prvků v kontejneru. Dobře navržená funkce hash vytváří rovnoměrné rozložení hodnot hash a minimalizuje počet kolizí, kde se říká, že ke kolizi dochází, když jsou odlišné hodnoty klíče mapovány na stejnou hodnotu hash. V nejhorším případě s nejhorší možnou funkcí hash je počet operací úměrný počtu prvků v sekvenci (lineární čas).

Hash_map by měl být asociativní kontejner volby při podmínky přisouvání hodnoty s jejich klíče jsou splněny aplikací. Model pro tento typ struktury je seřazený seznam jedinečně se vyskytujících klíčových slov s přidruženými řetězcovými hodnotami, které poskytují například definice. Pokud místo toho slova měla více než jednu správnou definici, takže klíče nebyly jedinečné, pak by hash_multimap byl kontejner volby. Pokud by na druhé straně byl uložen pouze seznam slov, pak by hash_set byl správný kontejner. Pokud bylo povoleno více výskytů slov, pak by hash_multiset byla příslušnou strukturou kontejneru.

Hash_map seřadí sekvenci, kterou řídí, voláním *objektu* vlastností hash třídy [value_compare](../standard-library/value-compare-class.md). K tomuto uloženému objektu lze přistupovat voláním key_comp členské [funkce](#key_comp). Takový objekt funkce se musí chovat stejně [hash_compare](../standard-library/hash-compare-class.md) jako objekt\<třídy hash_compare<Klíč, méně>> klíč. Konkrétně pro všechny hodnoty *Klíč* typu `Traits` *Klíč*, volání ( `Key` ) `size_t`dává rozdělení hodnot typu .

Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát f(x y) je objekt funkce, `x` `y` který má dva objekty argumentů a vrácenou hodnotu **true** nebo **false**. Řazení uložené na hash_map je přísné slabé řazení, pokud binární predikát je nereflexivní, antisymetrické a tranzitivní a pokud je ekvivalence přenositá, kde jsou dva objekty x a y definovány jako ekvivalentní, pokud jsou f(x, y) a f(y, x) false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

Skutečné pořadí prvků v řízené sekvenci závisí na funkci hash, funkci řazení a aktuální velikost tabulky hash uložené v objektu kontejneru. Nelze určit aktuální velikost tabulky hash, takže obecně nelze předpovědět pořadí prvků v řízené sekvenci. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Iterátor poskytované hash_map třídy je obousměrný iterátor, ale funkce členů třídy [insert](#insert) a [hash_map](#hash_map) mají verze, které berou jako parametry šablony slabší vstupní iterátor, jehož požadavky na funkčnost jsou minimální než ty, které jsou zaručeny třídou obousměrných iterátorů. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální sada funkcí, ale stačí, abyste mohli smysluplně hovořit o rozsahu `[First, Last)` iterátorů v kontextu funkcí členů třídy.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[hash_map](#hash_map)|Konstrukce, `hash_map` který je prázdný nebo který je kopií celé `hash_map`nebo části některé jiné .|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který `allocator` představuje třídu `hash_map` pro objekt.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který `const` může `hash_map`číst prvek v .|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na **const** element v `hash_map`.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na **const** `hash_map` prvek uložený v a pro čtení a provádění **const** operací.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `hash_map`libovolný **prvek const** v .|
|[difference_type](#difference_type)|Podepsaný typ celé číslo, který lze použít k reprezentaci počtu prvků `hash_map` a v rozsahu mezi prvky, na které iterátory poukázaly.|
|[Iterace](#iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `hash_map`nebo upravovat libovolný prvek v rozhraní .|
|[key_compare](#key_compare)|Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení `hash_map`k určení relativní pořadí dvou prvků v .|
|[key_type](#key_type)|Typ popisuje objekt klíče řazení, který představuje `hash_map`každý prvek .|
|[mapped_type](#mapped_type)|Typ, který představuje datový typ `hash_map`uložený v aplikaci .|
|[ukazatel](#pointer)|Typ, který poskytuje ukazatel na `hash_map`prvek v .|
|[Odkaz](#reference)|Typ, který poskytuje odkaz na prvek `hash_map`uložený v .|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo `hash_map`upravovat prvek v obráceném .|
|[size_type](#size_type)|Nepodepsaný podnosný typ, který může představovat počet prvků v . `hash_map`|
|[value_type](#value_type)|Typ, který poskytuje objekt funkce, který může porovnat dva prvky `hash_map`jako klíče řazení k určení jejich relativní pořadí v .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Na](#at)|Najde prvek v `hash_map` a s zadanou hodnotou klíče.|
|[Začít](#begin)|Vrátí iterátor adresující první prvek `hash_map`v rozhraní .|
|[cbegin](#cbegin)|Vrátí const iterator adresující první `hash_map`prvek v rozhraní .|
|[cend](#cend)|Vrátí const iterátor, který řeší umístění, které následuje `hash_map`poslední prvek v .|
|[Jasné](#clear)|Vymaže všechny `hash_map`prvky .|
|[Počet](#count)|Vrátí počet prvků v `hash_map` klíči, jejichž klíč odpovídá klíči zadanému parametrem.|
|[crbegin](#crbegin)|Vrátí const iterator adresování první `hash_map`prvek v obrácené .|
|[crend](#crend)|Vrátí const iterator, který řeší umístění, které následuje `hash_map`poslední prvek v obráceném .|
|[místo](#emplace)|Vloží prvek vytvořený na místě `hash_map`do .|
|[emplace_hint](#emplace_hint)|Vloží prvek vytvořený na místě `hash_map`do aplikace s nápovědou k umístění.|
|[empty](#empty)|Testuje, `hash_map` pokud je prázdný.|
|[Konec](#end)|Vrátí iterátor, který řeší umístění, které následuje `hash_map`poslední prvek v rozhraní .|
|[equal_range](#equal_range)|Vrátí dvojici iterátorů, respektive první prvek v `hash_map` klíč, který je větší než zadaný klíč a `hash_map` první prvek v s klíčem, který je roven nebo větší než klíč.|
|[Vymazat](#erase)|Odstraní prvek nebo rozsah prvků v `hash_map` a ze zadaných pozic.|
|[find](#find)|Vrátí iterátor adresování umístění prvku `hash_map` v, který má klíč ekvivalentní zadaný klíč.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objektu použitého `hash_map`k vytvoření .|
|[Vložit](#insert)|Vloží prvek nebo rozsah prvků do `hash_map`.|
|[key_comp](#key_comp)|Vrátí iterátor k prvnímu prvku `hash_map` v a s hodnotou klíče, která je rovna nebo větší než hodnota zadaného klíče.|
|[lower_bound](#lower_bound)|Vrátí iterátor k prvnímu prvku `hash_map` v a s hodnotou klíče, která je rovna nebo větší než hodnota zadaného klíče.|
|[max_size](#max_size)|Vrátí maximální délku `hash_map`.|
|[rbegin](#rbegin)|Vrátí iterátor adresující první prvek `hash_map`v obráceném .|
|[rend](#rend)|Vrátí iterátor, který řeší umístění, které následuje poslední `hash_map`prvek v obráceném .|
|[Velikost](#size)|Vrátí počet prvků v `hash_map`rozhraní .|
|[Swap](#swap)|Vyměňuje prvky `hash_map`dvou s.|
|[upper_bound](#upper_bound)|Vrátí iterátor prvnímu prvku v `hash_map` prvku, který má hodnotu klíče, která je větší než hodnota zadaného klíče.|
|[value_comp](#value_comp)|Načte kopii objektu porovnání použitého k `hash_map`pořadí hodnot prvků v rozhraní .|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor&#91;&#93;](#op_at)|Vloží prvek do `hash_map` a se zadanou hodnotou klíče.|
|[hash_map::operátor=](#op_eq)|Nahradí prvky a `hash_map` kopií jiného `hash_map`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<hash_map>

**Obor názvů:** stdext

## <a name="hash_mapallocator_type"></a><a name="allocator_type"></a>hash_map::allocator_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Typ, který představuje třídu alokátoru pro objekt hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Příklad

Viz příklad pro [get_allocator](#get_allocator) `allocator_type`příklad pomocí aplikace .

## <a name="hash_mapat"></a><a name="at"></a>hash_map::at

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Najde prvek v hash_map s zadanou hodnotou klíče.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*key*|Hodnota klíče prvku, který má být nalezen.|

### <a name="return-value"></a>Návratová hodnota

Odkaz na datovou hodnotu nalezeného prvku.

### <a name="remarks"></a>Poznámky

Pokud není nalezena hodnota klíče argumentu, pak funkce vyvolá objekt třídy [out_of_range Class](../standard-library/out-of-range-class.md).

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

## <a name="hash_mapbegin"></a><a name="begin"></a>hash_map::začátek

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí iterátor adresující první prvek v hash_map.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný itečelní objekt adresující první prvek v hash_map nebo umístění, které následuje prázdný hash_map.

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

## <a name="hash_mapcbegin"></a><a name="cbegin"></a>hash_map::cbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí const iterator adresování první prvek v hash_map.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstovat obousměrný iterátor adresování první prvek v [hash_map](../standard-library/hash-map-class.md) nebo `hash_map`umístění, které následuje prázdné .

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

## <a name="hash_mapcend"></a><a name="cend"></a>hash_map::cenzura

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí const iterator, který řeší umístění, které následuje poslední prvek v hash_map.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstovat obousměrný iterátor, který řeší umístění, které následuje poslední prvek v [hash_map](../standard-library/hash-map-class.md). Pokud `hash_map` je prázdný, `hash_map::cend == hash_map::begin`pak .

### <a name="remarks"></a>Poznámky

`cend`se používá k testování, zda iterátor dosáhl `hash_map`konce svého .

Hodnota vrácená `cend` by neměla být odkazována.

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

## <a name="hash_mapclear"></a><a name="clear"></a>hash_map::vymazat

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vymaže všechny prvky hash_map.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_map::clear členské funkce.

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

## <a name="hash_mapconst_iterator"></a><a name="const_iterator"></a>hash_map::const_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek v hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

Definované `const_iterator` hash_map odkazuje na prvky, které jsou objekty [value_type](#value_type), který je typu `pair< const Key, Type >`, jehož první člen je klíčem k prvku a jehož druhý člen je mapované datum držené elementem.

Chcete-li `const_iterator` `cIter` odkazovat na odkaz ukazující na `->` prvek v hash_map, použijte operátor.

Chcete-li získat přístup k hodnotě `cIter->first`klíče pro `(*cIter).first`prvek, použijte , což je ekvivalentní . Chcete-li získat přístup k hodnotě mapované základny pro prvek, použijte `cIter->second`, což je ekvivalentní `(*cIter).second`.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) pro příklad pomocí `const_iterator`.

## <a name="hash_mapconst_pointer"></a><a name="const_pointer"></a>hash_map::const_pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Typ, který poskytuje ukazatel na **const** prvek v hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku.

Ve většině případů [iterátor](#iterator) by měl být použit pro přístup k prvkům v hash_map objektu.

## <a name="hash_mapconst_reference"></a><a name="const_reference"></a>hash_map::const_reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Typ, který poskytuje odkaz na **prvek const** uložený v hash_map pro čtení a provádění operací **const.**

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

## <a name="hash_mapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>hash_map::const_reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst libovolný **prvek const** v hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse)iterator const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a používá se k iterátu přes hash_map v opačném směru.

Definované `const_reverse_iterator` hash_map odkazuje na prvky, které jsou objekty [value_type](#value_type), který je typu `pair` \< **const Key, Type**>, jehož první člen je klíčem k prvku a jehož druhý člen je mapované základny držené elementem.

Chcete-li `const_reverse_iterator` `crIter` odkazovat na odkaz ukazující na **->** prvek v hash_map, použijte operátor.

Chcete-li získat přístup k hodnotě `crIter`  -> klíče pro prvek,\* `crIter`použijte **nejprve**, což je ekvivalentní ( **).** Chcete-li získat přístup k hodnotě mapované základny pro prvek, použijte `crIter`  ->  **second**, což je ekvivalentní (\* `crIter`). **nejprve**.

### <a name="example"></a>Příklad

Příklad pro [rend](#rend) naleznete v příkladu, jak `const_reverse_iterator`deklarovat a používat .

## <a name="hash_mapcount"></a><a name="count"></a>hash_map::počet

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí počet prvků v hash_map jehož klíč odpovídá klíči zadanému parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Hodnota klíče prvků, které mají být spárovány z hash_map.

### <a name="return-value"></a>Návratová hodnota

1 pokud hash_map obsahuje prvek, jehož klíč řazení odpovídá klíči parametru; 0, pokud hash_map neobsahuje prvek s odpovídající klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků *x* v rozsahu

\[lower_bound(*klíč*), upper_bound(*klíč*)

což je 0 nebo 1 v případě hash_map, což je jedinečný asociativní kontejner.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_map::count členské funkce.

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

## <a name="hash_mapcrbegin"></a><a name="crbegin"></a>hash_map::crbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí const iterator adresování první prvek v obrácené hash_map.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor adresování první prvek v obrácené [hash_map](../standard-library/hash-map-class.md) nebo řešení toho, co bylo poslední prvek v unreverse `hash_map`.

### <a name="remarks"></a>Poznámky

`crbegin`se používá s obráceným [begin](#begin) hash_map stejně `hash_map`jako begin se používá s .

S vrácenou `crbegin`hodnotou `hash_map` aplikace nelze objekt změnit.

`crbegin`lze použít k iterovat přes `hash_map` dozadu.

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

## <a name="hash_mapcrend"></a><a name="crend"></a>hash_map::crend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí const iterátor, který řeší umístění, které následuje poslední prvek v obráceném hash_map.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor, který řeší umístění, které následuje poslední prvek v obrácené [masovém](../standard-library/hash-map-class.md) hash_map `hash_map`(umístění, které předcházelo první prvek v unreverse).

### <a name="remarks"></a>Poznámky

`crend`se používá s `hash_map` obráceným stejně [jako hash_map::end](#end) se používá s `hash_map`.

S vrácenou `crend`hodnotou `hash_map` aplikace nelze objekt změnit.

`crend`lze použít k testování, zda reverzní iterátor dosáhl `hash_map`konce svého .

Hodnota vrácená `crend` by neměla být odkazována.

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

## <a name="hash_mapdifference_type"></a><a name="difference_type"></a>hash_map::difference_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Podepsaný typ celé číslo, který lze použít k reprezentaci počtu prvků hash_map v rozsahu mezi prvky, na které se iterátory upozorují.

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

## <a name="hash_mapemplace"></a><a name="emplace"></a>hash_map::emplace

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vloží prvek vytvořený na místě do hash_map.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota slouží k přesunutí konstrukce prvek, který [hash_map](../standard-library/hash-map-class.md) má `hash_map` být vložen do hash_map pokud již obsahuje tento prvek (nebo obecněji prvek, jehož klíč je ekvivalentní objednané).|

### <a name="return-value"></a>Návratová hodnota

Členská `emplace` funkce vrátí dvojici, jejíž komponenta bool vrátí hodnotu true, pokud byl proveden vložení, a false, pokud `hash_map` již obsahoval prvek, jehož klíč měl v řazení ekvivalentní hodnotu a jehož komponenta iterátoru vrací adresu, kde byl vložen nový prvek nebo kde byl již umístěn.

Chcete-li získat přístup k součásti iterátoru `pr` `pr.first`dvojice vrácené touto členovou funkcí, použijte a pro její odkaz použijte `*(pr.first)`. Chcete-li získat přístup k `pr` **bool** součásti `pr.second`dvojice vrácené touto členovou funkcí, použijte a chcete-li na něj odkazovat, použijte `*(pr.second)`.

### <a name="remarks"></a>Poznámky

[hash_map::value_type](#value_type) prvku je pár, takže hodnota prvku bude uspořádaný pár s první komponentou rovnající se hodnotě klíče a druhou komponentou rovnající se hodnotě dat prvku.

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

## <a name="hash_mapemplace_hint"></a><a name="emplace_hint"></a>hash_map::emplace_hint

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vloží prvek vytvořený na místě do hash_map s nápovědou k umístění.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota slouží k přesunutí konstrukce prvek, který [hash_map](../standard-library/hash-map-class.md) má `hash_map` být vložen do hash_map pokud již obsahuje tento prvek (nebo obecněji prvek, jehož klíč je ekvivalentní objednané).|
|*_Where*|Nápověda týkající se místa, kde chcete začít hledat správný bod vložení.|

### <a name="return-value"></a>Návratová hodnota

Členská funkce [hash_multimap::emplace](../standard-library/hash-multimap-class.md#emplace) vrátí iterátor, který odkazuje na `hash_map`pozici, kde byl vložen nový prvek do , nebo kde je umístěn existující prvek s ekvivalentním řazením.

### <a name="remarks"></a>Poznámky

[hash_map::value_type](#value_type) prvku je pár, takže hodnota prvku bude uspořádaný pár s první komponentou rovnající se hodnotě klíče a druhou komponentou rovnající se hodnotě dat prvku.

Vložení může dojít v amortizované konstantní čas, namísto logaritmického času, pokud kurzor bezprostředně následuje *_Where*.

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

## <a name="hash_mapempty"></a><a name="empty"></a>hash_map::prázdný

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Testuje, pokud je hash_map prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je hash_map prázdná; **false,** pokud hash_map není prázdný.

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

## <a name="hash_mapend"></a><a name="end"></a>hash_map::konec

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí iterátor, který řeší umístění, které následuje poslední prvek v hash_map.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který řeší umístění, které následuje poslední prvek v hash_map. Pokud je hash_map prázdný, pak hash_map::end == hash_map::begin.

### <a name="remarks"></a>Poznámky

`end`se používá k testování, zda iterátor dosáhl konce svého hash_map.

Hodnota vrácená `end` by neměla být odkazována.

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

## <a name="hash_mapequal_range"></a><a name="equal_range"></a>hash_map::equal_range

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí dvojici iterátorů respektive první prvek v hash_map s klíčem, který je větší než zadaný klíč a první prvek v hash_map s klíčem, který je roven nebo větší než klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*\
Hodnota klíče argumentu, která má být porovnána s klíčem řazení prvku z hash_map prohledávány.

### <a name="return-value"></a>Návratová hodnota

Dvojice iterátorů tak, že první je [lower_bound](#lower_bound) klíče a druhý je [upper_bound](#upper_bound) klíče.

Chcete-li získat přístup k prvnímu iterátoru `pr` `pr`dvojice vrácené členovou funkcí, použijte . **nejprve** a dereference dolní mez iterátoru, použití \*( `pr`. **první**). Chcete-li získat přístup k druhému iterátoru `pr` `pr`dvojice vrácené členovou funkcí, použijte . **a** pro dereferenci horní mez iterátoru, použití \*( `pr`. **za druhé**).

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

## <a name="hash_maperase"></a><a name="erase"></a>hash_map::vymazat

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Odebere prvek nebo rozsah prvků v hash_map ze zadaných pozic nebo odebere prvky, které odpovídají zadanému klíči.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozice prvku, který má být odebrán z hash_map.

*První*\
Pozice prvního prvku odebrána z hash_map.

*Poslední*\
Umístěte těsně za poslední prvek odstraněný z hash_map.

*Klíč*\
Hodnota klíče prvků, které mají být odebrány z hash_map.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který označuje první prvek zbývající za všechny prvky odebrány nebo ukazatel na konec hash_map pokud žádný takový prvek neexistuje.

Pro třetí členskou funkci vrátí počet prvků, které byly odebrány z hash_map.

### <a name="remarks"></a>Poznámky

Členské funkce nikdy vyvolat výjimku.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_map::erase členské funkce.

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

## <a name="hash_mapfind"></a><a name="find"></a>hash_map::najít

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí iterátor adresující umístění prvku v hash_map, který má klíč ekvivalentní zadanému klíči.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Hodnota klíče, která má být porovnána s klíčem řazení prvku z hash_map prohledávány.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který řeší umístění prvku se zadaným klíčem nebo umístění, které následuje poslední prvek v hash_map pokud pro klíč není nalezena žádná shoda.

### <a name="remarks"></a>Poznámky

`find`vrátí iterátor, který řeší prvek v hash_map jehož klíč řazení je ekvivalentní klíč argumentu pod binární predikát, který indukuje řazení na základě méně než vztah srovnatelnosti.

Pokud `find` je vrácená hodnota přiřazena [const_iterator](#const_iterator), nelze objekt hash_map změnit. Pokud `find` je vrácená hodnota přiřazena [iterátoru](#iterator), lze hash_map objekt změnit

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

## <a name="hash_mapget_allocator"></a><a name="get_allocator"></a>hash_map::get_allocator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí kopii objektu alokátoru použitého ke vytvoření hash_map.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný hash_map.

### <a name="remarks"></a>Poznámky

Alokátory pro třídu hash_map určují, jak třída spravuje úložiště. Výchozí alokátory dodávané s třídami kontejneru standardní knihovny jazyka C++ jsou dostatečné pro většinu potřeb programování. Psaní a používání vlastní třídy přidělování je pokročilé téma jazyka C++.

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

## <a name="hash_maphash_map"></a><a name="hash_map"></a>hash_map::hash_map

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vytvoří hash_map, která je prázdná nebo je kopií celého jiného hash_map nebo jeho části.

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
|*Al*|Třída alokátoru úložiště, která má být použita `Allocator`pro tento hash_map objekt, který je ve výchozím nastavení .|
|*Comp*|Funkce porovnání typu const `Traits` slouží k pořadí prvků v hash_map, který výchozí . `hash_compare`|
|*Právo*|hash_map, které je vytvořená mapa kopie.|
|*První*|Umístění prvního prvku v rozsahu prvků, které mají být zkopírovány.|
|*Poslední*|Pozice první prvek mimo rozsah prvků, které mají být zkopírovány.|
|*Ilist*|Initializer_list|

### <a name="remarks"></a>Poznámky

Všechny konstruktory uložit typ objektu alokátoru, který spravuje úložiště paměti pro hash_map a může být později vrácena voláním [get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují své hash_map.

Všechny konstruktory uložit objekt `Traits` funkce typu, který se používá k vytvoření pořadí mezi klíči hash_map a které mohou být později vráceny voláním [key_comp](#key_comp).

První tři konstruktory určují prázdnou počáteční hash_map, navíc druhá určuje typ funkce porovnání (*Comp),* která má být použita při stanovení pořadí prvků a třetí explicitně určuje typ alokátoru (*Al*), který má být použit. Klíčové slovo **explicitní** potlačí určité druhy automatického převodu typu.

Čtvrtý konstruktor určuje kopii hash_map *Right*.

Další tři konstruktory zkopírují rozsah `[First, Last)` hash_map s rostoucí explicitní při určování typu `Traits` funkce porovnání třídy a alokátoru.

Poslední konstruktor přesune hash_map *Doprava*.

## <a name="hash_mapinsert"></a><a name="insert"></a>hash_map::vložit

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

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
|*Val*|Hodnota prvku, který má být vložen do hash_map, pokud hash_map již obsahuje tento prvek (nebo obecněji prvek, jehož klíč je rovnocenně objednán).|
|*_Where*|Nápověda týkající se místa, kde chcete začít hledat správný bod vložení.|
|*První*|Pozice prvního prvku, který má být zkopírován z hash_map.|
|*Poslední*|Pozice těsně za poslední prvek, který má být zkopírován z hash_map.|

### <a name="return-value"></a>Návratová hodnota

První `insert` členská funkce vrátí dvojici, jejíž komponenta bool vrátí hodnotu true, pokud byl proveden vložení, a false, pokud hash_map již obsahoval prvek, jehož klíč měl ekvivalentní hodnotu v řazení a jehož komponenta iterátoru vrátí adresu, kde byl vložen nový prvek nebo kde byl již umístěn prvek.

Chcete-li získat přístup k součásti iterátoru `pr` `pr`dvojice vrácené touto členovou funkcí, použijte . **a**chcete-li na něj \* `pr`odkazovat, použijte ( . **první**). Chcete-li získat přístup k `pr` **bool** součásti `pr`dvojice vrácené touto člennou funkcí, použijte . **a**pro dereferencování použijte \* `pr`( . **za druhé**).

Druhá `insert` členská funkce, verze nápovědy, vrátí iterátor, který odkazuje na pozici, kde byl vložen nový prvek do hash_map.

Poslední dvě `insert` členské funkce se chovají stejně jako první dvě, s tím rozdílem, že přesunou tahovku vvloženou hodnotu.

### <a name="remarks"></a>Poznámky

Value_type [value_type](../standard-library/map-class.md#value_type) prvku je pár, takže hodnota prvku bude uspořádaný pár s první komponentou rovnající se hodnotě klíče a druhou komponentou rovnající se hodnotě dat prvku.

Vložení může dojít v amortizované konstantní čas pro nápovědu verzi vložit, namísto logaritmického času, pokud kurzor bezprostředně následuje *_Where*.

Třetí členská funkce vloží posloupnost hodnot prvků do hash_map odpovídající každému prvku adresovanému iterátorem v rozsahu *[First, Last)* zadané sady.

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

## <a name="hash_mapiterator"></a><a name="iterator"></a>hash_map::iterátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Poznámky

Definované `iterator` hash_map odkazuje na prvky, které jsou objekty [value_type](#value_type), který je typu **dvojice\<const Key, Type>,** jehož první člen je klíčem k prvku a jehož druhý člen je mapované základny držené elementem.

Chcete-li odkazovat **na iterátor** `Iter` ukazující na prvek `->` v multimap, použijte operátor.

Chcete-li získat přístup k hodnotě `Iter`  -> klíče pro prvek, použijte **nejprve**, což je ekvivalentní (\* `Iter`). **nejprve**. Chcete-li získat přístup k hodnotě mapované základny pro prvek, použijte `Iter`  ->  **second**, což je ekvivalentní (\* `Iter`). **druhé**.

Typ `iterator` lze změnit hodnotu prvku.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) pro příklad, `iterator`jak deklarovat a používat .

## <a name="hash_mapkey_comp"></a><a name="key_comp"></a>hash_map::key_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Načte kopii objektu porovnání použitého k objednání klíčů v hash_map.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který hash_map používá k objednání jeho prvků.

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členovou funkci

**bool operátor** **(const Key&** `left` **, const Key&);** `right`

, který `left` vrátí **hodnotu true,** pokud předchází a není rovna `right` v pořadí řazení.

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

## <a name="hash_mapkey_compare"></a><a name="key_compare"></a>hash_map::key_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení k určení relativní pořadí dvou prvků v mapě.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare`je synonymem pro `Traits`parametr šablony .

Další informace `Traits` naleznete v tématu [hash_map Třída.](../standard-library/hash-map-class.md)

### <a name="example"></a>Příklad

Příklad pro [key_comp](#key_comp) naleznete příklad deklarace `key_compare`a používání .

## <a name="hash_mapkey_type"></a><a name="key_type"></a>hash_map::key_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Typ popisuje objekt klíče řazení, který představuje každý prvek hash_map.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type`je synonymem pro `Key`parametr šablony .

Další informace `Key`naleznete v části Poznámky v tématu [hash_map třída.](../standard-library/hash-map-class.md)

### <a name="example"></a>Příklad

Příklad pro [value_type](#value_type) například, jak deklarovat a používat `key_type`.

## <a name="hash_maplower_bound"></a><a name="lower_bound"></a>hash_map::lower_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí iterátor prvnímu prvku v hash_map s hodnotou klíče, která je rovna nebo větší než hodnota zadaného klíče.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Hodnota klíče argumentu, která má být porovnána s klíčem řazení prvku z hash_map prohledávány.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator,](#const_iterator) který řeší umístění prvku v hash_map, který s klíčem, který je roven nebo větší než klíč argumentu, nebo který řeší umístění, které následuje poslední prvek v hash_map pokud pro klíč není nalezena žádná shoda.

Pokud `lower_bound` je vrácená hodnota `const_iterator`přiřazena aplikaci , nelze objekt hash_map změnit. Pokud `lower_bound` je vrácená hodnota `iterator`přiřazena , lze změnit objekt hash_map.

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

## <a name="hash_mapmapped_type"></a><a name="mapped_type"></a>hash_map::mapped_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Typ, který představuje datový typ uložený v hash_map.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Poznámky

Typ `mapped_type` je synonymem pro `Type`parametr šablony .

Další informace `Type` naleznete v tématu [hash_map Třída.](../standard-library/hash-map-class.md)

### <a name="example"></a>Příklad

Příklad pro [value_type](#value_type) například, jak deklarovat a používat `key_type`.

## <a name="hash_mapmax_size"></a><a name="max_size"></a>hash_map::max_size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

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

## <a name="hash_mapoperator"></a><a name="op_at"></a>hash_map::operátor[]

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vloží prvek do `hash_map` a se zadanou hodnotou klíče.

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

`operator[]`mohou být použity k `hash_map m` vložení prvků do

`m[ key] = DataValue`;

kde DataValue je hodnota `mapped_type` prvku s hodnotou *klíče*.

Při `operator[]` použití vložení prvků vrácený odkaz neznamená, zda vložení mění již existující prvek nebo vytváří nový. Členské funkce [najít](../standard-library/map-class.md#find) a [vložit](../standard-library/map-class.md#insert) lze určit, zda prvek s zadaným klíčem je již přítomen před vložením.

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

## <a name="hash_mapoperator"></a><a name="op_eq"></a>hash_map::operátor=

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Nahradí prvky hash_map kopií jiného hash_map.

```cpp
hash_map& operator=(const hash_map& right);

hash_map& operator=(hash_map&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Právo*|[Třída hash_map](../standard-library/hash-map-class.md) zkopírována do . `hash_map`|

### <a name="remarks"></a>Poznámky

Po vymazání všech existujících `hash_map` `operator=` prvků v aplikaci zkopíruje `hash_map`nebo přesune obsah *vpravo* do .

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

## <a name="hash_mappointer"></a><a name="pointer"></a>hash_map::pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Typ, který poskytuje ukazatel na prvek v hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze změnit hodnotu prvku.

Ve většině případů [iterátor](#iterator) by měl být použit pro přístup k prvkům v hash_map objektu.

## <a name="hash_maprbegin"></a><a name="rbegin"></a>hash_map::rbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí iterátor adresování první prvek v obrácené mašveru hash_map.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresování první prvek v obrácené hash_map nebo adresování, co bylo poslední prvek v unreverse hash_map.

### <a name="remarks"></a>Poznámky

`rbegin`se používá s obráceným hash_map stejně jako [začátek](#begin) se používá s hash_map.

Pokud `rbegin` je vrácená hodnota přiřazena [const_reverse_iterator](#const_reverse_iterator), nelze objekt hash_map změnit. Pokud `rbegin` je vrácená hodnota přiřazena [reverse_iterator](#reverse_iterator), lze změnit objekt hash_map.

`rbegin`lze itetovat přes hash_map dozadu.

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

## <a name="hash_mapreference"></a><a name="reference"></a>hash_map::odkaz

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

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

## <a name="hash_maprend"></a><a name="rend"></a>hash_map::rend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí iterátor, který řeší umístění, které následuje poslední prvek v obráceném hash_map.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor, který řeší umístění, které následuje poslední prvek v obráceném hash_map (umístění, které předcházelo prvnímu prvku v neobráceném hash_map).

### <a name="remarks"></a>Poznámky

`rend`se používá s obráceným hash_map [stejně](#end) jako konec se používá s hash_map.

Pokud `rend` je vrácená hodnota přiřazena [const_reverse_iterator](#const_reverse_iterator), nelze objekt hash_map změnit. Pokud `rend` je vrácená hodnota přiřazena [reverse_iterator](#reverse_iterator), lze změnit objekt hash_map.

`rend`lze použít k testování, zda reverzní iterátor dosáhl konce svého hash_map.

Hodnota vrácená `rend` by neměla být odkazována.

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

## <a name="hash_mapreverse_iterator"></a><a name="reverse_iterator"></a>hash_map::reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném hash_map.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` nemůže změnit hodnotu prvku a používá se k iterátu přes hash_map v opačném směru.

Definované `reverse_iterator` hash_map odkazuje na prvky, které jsou objekty [value_type](#value_type), který je typu **dvojice\<const Key, Typ>**, jehož první člen je klíčem k prvku a jehož druhý člen je mapované základny držené elementem.

Chcete-li `reverse_iterator` `rIter` odkazovat na odkaz ukazující na prvek v hash_map, použijte operátor ->.

Chcete-li získat přístup k hodnotě `rIter`  -> klíče pro prvek, použijte **nejprve**, což je ekvivalentní (\* `rIter`). **nejprve**. Chcete-li získat přístup k hodnotě mapované základny pro prvek, použijte `rIter`  ->  **second**, což je ekvivalentní (\* `rIter`). **nejprve**.

### <a name="example"></a>Příklad

Příklad pro [rbegin](#rbegin) pro příklad, jak `reverse_iterator`deklarovat a používat .

## <a name="hash_mapsize"></a><a name="size"></a>hash_map::velikost

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí počet prvků v hash_map.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka hash_map.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_map::size členské funkce.

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

## <a name="hash_mapsize_type"></a><a name="size_type"></a>hash_map::size_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Nepodepsaný podnosný typ, který může představovat počet prvků v hash_map.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Příklad [velikosti](#size) naleznete v příkladu, jak deklarovat a používat`size_type`

## <a name="hash_mapswap"></a><a name="swap"></a>hash_map::swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vyměňuje prvky dvou hash_maps.

```cpp
void swap(hash_map& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Argument hash_map poskytuje prvky, které mají být vyměněny za cílovou hash_map.

### <a name="remarks"></a>Poznámky

Členská funkce zruší platnost žádné odkazy, ukazatele nebo iterátory, které označují prvky ve dvou hash_maps jejichž prvky jsou vyměňovány.

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

## <a name="hash_mapupper_bound"></a><a name="upper_bound"></a>hash_map::upper_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí iterátor prvnímu prvku v hash_map, který s klíčem s hodnotou, která je větší než hodnota zadaného klíče.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Hodnota klíče argumentu, která má být porovnána s hodnotou klíče řazení prvku z hash_map prohledávány.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator,](#const_iterator) který řeší umístění prvku v hash_map, který s klíčem, který je větší než klíč argumentu, nebo který řeší umístění, které následuje poslední prvek v hash_map pokud pro klíč není nalezena žádná shoda.

Pokud je vrácená hodnota `const_iterator`přiřazena aplikaci , nelze hash_map objekt změnit. Pokud je vrácená hodnota `iterator`přiřazena k aplikaci , lze změnit hash_map objekt.

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

## <a name="hash_mapvalue_comp"></a><a name="value_comp"></a>hash_map::value_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Vrátí objekt funkce, který určuje pořadí prvků v hash_map porovnáním jejich hodnot klíče.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce porovnání, který hash_map používá k objednání jeho prvků.

### <a name="remarks"></a>Poznámky

Pro hash_map *m*, jestliže dva prvky *e1* (*k1*, *d1*) a *e2* (*k2*, *d2*) jsou objekty typu [value_type](#value_type), `m.value_comp()(e1, e2)` kde *k1* a *k2* jsou jejich klíče typu [key_type](#key_type) a *d1* a *d2* jsou jejich údaje typu [mapped_type](#mapped_type), pak jsou ekvivalentní . `m.key_comp()(k1, k2)` Uložený objekt definuje členovou funkci

`bool operator(value_type& left, value_type& right);`

který vrátí **hodnotu true,** pokud hodnota klíče `left` předchází `right` a není rovna hodnotě klíče v pořadí řazení.

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

## <a name="hash_mapvalue_type"></a><a name="value_type"></a>hash_map::value_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](../standard-library/unordered-map-class.md).

Typ, který představuje typ objektu uloženého v hash_map.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Poznámky

`value_type`je prohlášena `pair<const key_type, mapped_type>` za, a nikoli `pair<key_type, mapped_type>` proto, že klíče asociativní kontejneru nelze změnit pomocí nekonstantní iterátor nebo odkaz.

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

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
