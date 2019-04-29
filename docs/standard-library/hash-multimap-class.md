---
title: hash_multimap – třída
ms.date: 10/18/2018
f1_keywords:
- hash_map/stdext::hash_multimap
- hash_map/stdext::hash_multimap::allocator_type
- hash_map/stdext::hash_multimap::const_iterator
- hash_map/stdext::hash_multimap::const_pointer
- hash_map/stdext::hash_multimap::const_reference
- hash_map/stdext::hash_multimap::const_reverse_iterator
- hash_map/stdext::hash_multimap::difference_type
- hash_map/stdext::hash_multimap::iterator
- hash_map/stdext::hash_multimap::key_compare
- hash_map/stdext::hash_multimap::key_type
- hash_map/stdext::hash_multimap::mapped_type
- hash_map/stdext::hash_multimap::pointer
- hash_map/stdext::hash_multimap::reference
- hash_map/stdext::hash_multimap::reverse_iterator
- hash_map/stdext::hash_multimap::size_type
- hash_map/stdext::hash_multimap::value_type
- hash_map/stdext::hash_multimap::begin
- hash_map/stdext::hash_multimap::cbegin
- hash_map/stdext::hash_multimap::cend
- hash_map/stdext::hash_multimap::clear
- hash_map/stdext::hash_multimap::count
- hash_map/stdext::hash_multimap::crbegin
- hash_map/stdext::hash_multimap::crend
- hash_map/stdext::hash_multimap::emplace
- hash_map/stdext::hash_multimap::emplace_hint
- hash_map/stdext::hash_multimap::empty
- hash_map/stdext::hash_multimap::end
- hash_map/stdext::hash_multimap::equal_range
- hash_map/stdext::hash_multimap::erase
- hash_map/stdext::hash_multimap::find
- hash_map/stdext::hash_multimap::get_allocator
- hash_map/stdext::hash_multimap::insert
- hash_map/stdext::hash_multimap::key_comp
- hash_map/stdext::hash_multimap::lower_bound
- hash_map/stdext::hash_multimap::max_size
- hash_map/stdext::hash_multimap::rbegin
- hash_map/stdext::hash_multimap::rend
- hash_map/stdext::hash_multimap::size
- hash_map/stdext::hash_multimap::swap
- hash_map/stdext::hash_multimap::upper_bound
- hash_map/stdext::hash_multimap::value_comp
helpviewer_keywords:
- stdext::hash_multimap
- stdext::hash_multimap::allocator_type
- stdext::hash_multimap::const_iterator
- stdext::hash_multimap::const_pointer
- stdext::hash_multimap::const_reference
- stdext::hash_multimap::const_reverse_iterator
- stdext::hash_multimap::difference_type
- stdext::hash_multimap::iterator
- stdext::hash_multimap::key_compare
- stdext::hash_multimap::key_type
- stdext::hash_multimap::mapped_type
- stdext::hash_multimap::pointer
- stdext::hash_multimap::reference
- stdext::hash_multimap::reverse_iterator
- stdext::hash_multimap::size_type
- stdext::hash_multimap::value_type
- stdext::hash_multimap::begin
- stdext::hash_multimap::cbegin
- stdext::hash_multimap::cend
- stdext::hash_multimap::clear
- stdext::hash_multimap::count
- stdext::hash_multimap::crbegin
- stdext::hash_multimap::crend
- stdext::hash_multimap::emplace
- stdext::hash_multimap::emplace_hint
- stdext::hash_multimap::empty
- stdext::hash_multimap::end
- stdext::hash_multimap::equal_range
- stdext::hash_multimap::erase
- stdext::hash_multimap::find
- stdext::hash_multimap::get_allocator
- stdext::hash_multimap::insert
- stdext::hash_multimap::key_comp
- stdext::hash_multimap::lower_bound
- stdext::hash_multimap::max_size
- stdext::hash_multimap::rbegin
- stdext::hash_multimap::rend
- stdext::hash_multimap::size
- stdext::hash_multimap::swap
- stdext::hash_multimap::upper_bound
- stdext::hash_multimap::value_comp
ms.assetid: f41a6db9-67aa-43a3-a3c5-dbfe9ec3ae7d
ms.openlocfilehash: 8510bbc89a22fe3eb8df6bbf8ce77db44c7a65a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405076"
---
# <a name="hashmultimap-class"></a>hash_multimap – třída

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Hash_multimap – třída kontejneru je rozšířením C++ standardní knihovnu a používá se pro ukládání a rychlé načítání dat z kolekce, ve kterém je každý prvek pár, který má klíč řazení, jehož hodnota nemusí být jedinečný a přidružená data hodnotu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare <Key, less <Key>>,
    class Allocator=allocator <pair  <const Key, Type>>>
class hash_multimap
```

### <a name="parameters"></a>Parametry

*Key*<br/>
Datový typ klíče, který bude uložen do hash_multimap.

*Typ*<br/>
Typ dat prvku, který bude uložen do hash_multimap.

*Osobnostní rysy*<br/>
Typ, který obsahuje dva objekty funkce, jeden z třídy *osobnostní rysy* , který je možné porovnat dvě hodnoty prvků jako klíče řazení pro určení jejich relativního pořadí a hashovací funkci, která je unární predikát mapování hodnot klíče prvků, které se celá čísla typu unsigned `size_t`. Tento argument je nepovinný a `hash_compare<Key, less<Key>>` je výchozí hodnota.

*Allocator –*<br/>
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navracení zpět paměti hash_multimap –. Tento argument je nepovinný a výchozí hodnota je `allocator<pair <const Key, Type>>`.

## <a name="remarks"></a>Poznámky

Hash_multimap je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Hodnoty hash, protože jeho prvky jsou seskupeny do intervalů podle hodnoty funkce hash u hodnoty klíče prvků.

- Vícenásobný, protože je prvky nemusí mít jedinečné klíče, takže jedna hodnota klíče může mít k sobě přidružených mnoho datových hodnot prvků.

- Kontejner asociativních párů, protože jeho prvky hodnoty se liší od hodnot klíčů.

- Třída šablony, protože poskytuje obecné funkce a to nezávisle na určitém typu dat obsažených jako prvky nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Hlavní výhodou hashování přes řazení je vyšší efektivity; úspěšné algoritmu hash provádí vkládání, odstraňování a vyhledá v konstantní průměrnou dobu mezi dobou úměrný logaritmu počtu prvků v kontejneru pro řazení techniky. Hodnotu prvku v hash_multimap, ale ne jeho přidruženou hodnotu klíče, lze změnit přímo. Namísto toho hodnoty klíčů přidružené ke starým prvkům musí být odstraněny a vloženy nové hodnoty klíče související s novými prvky.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Hodnoty hash asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstranění. Členské funkce, které explicitně podporují tyto operace jsou efektivní, při použití s dobře navržené hashovací funkce, prováděny v čase, který je v průměru konstantní a není závislá na počtu prvků v kontejneru. Dobře navržené hashovací funkce generuje jednotné distribuce hodnot hash a minimalizuje počet kolizí, kde ke kolizi říká, že je dojít, když odlišné hodnoty klíče jsou mapovány na stejnou hodnotu hash. V nejhorším případě s nejhorší funkce hash je to možné je počet operací úměrný počtu prvků v sekvenci (lineární čas).

Hash_multimap by měl být asociativní kontejner dle výběru, když jsou podmínky přiřazení hodnot k jejich klíčům splněny aplikací. Model pro tento typ struktury je uspořádaný seznam klíčových slov s přidruženými řetězcovými hodnotami poskytujícími (řekněme) definice, kde slova nebyla vždy jednoznačně definována. Pokud místo toho byla jedinečně definovaná klíčová slova tak, aby byly klíče jedinečné, hash_map – by zvoleným kontejnerem. Pokud na druhé straně uložen jen seznam slov, hash_set by tím správným kontejnerem. Pokud bylo povoleno více výskytů jednoho slova, hash_multiset by odpovídající strukturou kontejneru.

Hash_multimap seřadí sekvence pomocí volání uloženého hash `Traits` objekt typu [value_compare –](../standard-library/value-compare-class.md). Tento uložený objekt může získat přístup k voláním členské funkce [key_comp](../standard-library/hash-map-class.md#key_comp). Objekt funkce se musí chovat stejně jako objekt třídy [hash_compare –](../standard-library/hash-compare-class.md)`<Key, less<Key>>`. Konkrétně pro všechny hodnoty `Key` typu `Key`, volání `Traits (Key)` získá distribuci hodnot typu `size_t`.

Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. Výsledkem je řazení mezi neekvivalentních prvků. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát f (x, y) je objekt funkce, který má dva objekty argumentu `x` a `y` a vrácená hodnota **true** nebo **false**. Na hash_multimap je přísné slabé seřazení, pokud je binární predikát Nereflexivní, antisymetrický a tranzitivní a je-li ekvivalence tranzitivní, kde dva objekty `x` a `y` jsou definovány jako ekvivalentní, když oba f (x y) a jsou f (y, x) **false**. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

Skutečné pořadí prvků v řízené sekvenci závisí na hashovací funkci, funkci pořadí a aktuální velikost tabulky hash uloženou v objektu kontejneru. Nelze zjistit aktuální velikost tabulky hash, takže pořadí prvků v řízené sekvenci obecně nelze předvídat. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Iterátor poskytovaný třídou hash_multimap je obousměrný iterátor, ale členské funkce třídy [vložit](#insert) a [hash_multimap](#hash_multimap) mají verze, které jako parametry šablony berou slabší vstupní iterátor, jehož požadavky na funkce jsou minimálnější než ty zaručeny třídou obousměrných iterátorů. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní hash_multimap požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální hash_multimap funkcí, ale je dostatečná pro srozumitelnou komunikaci o rozsahu u iterátorů `[First, Last)` v rámci členských funkcí.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[hash_multimap](#hash_multimap)|Sestaví seznam určité velikosti nebo s prvky určité hodnoty nebo s konkrétní `allocator` nebo jako kopii jiného `hash_multimap`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje `allocator` třídy pro `hash_multimap` objektu.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `const` prvek `hash_multimap`.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na **const** prvek `hash_multimap`.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na **const** element uložené v `hash_multimap` pro čtení a provádění **const** operace.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může přečíst jakýkoli **const** prvek `hash_multimap`.|
|[difference_type](#difference_type)|Celočíselný typ se znaménkem, který slouží k vyjádření počtu prvků `hash_multimap` v rozsahu mezi prvky, na které odkazují iterátory.|
|[iterator](#iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v `hash_multimap`.|
|[key_compare](#key_compare)|Typ poskytující objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v `hash_multimap`.|
|[key_type](#key_type)|Typ, který popisuje řazení objektu klíče, který představuje každý prvek objektu `hash_multimap`.|
|[mapped_type](#mapped_type)|Typ, který představuje typ dat uložených v `hash_multimap`.|
|[pointer](#pointer)|Typ, který poskytuje ukazatel na prvek v `hash_multimap`.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na prvek uložený v `hash_multimap`.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném objektu `hash_multimap`.|
|[size_type](#size_type)|Typ celé číslo bez znaménka představující počet prvků v `hash_multimap`.|
|[value_type](#value_type)|Typ poskytující objekt funkce, který může porovnat dva prvky jako klíče řazení pro určení jejich relativního pořadí v `hash_multimap`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[začít](#begin)|Vrátí iterátor adresující první prvek `hash_multimap`.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor adresující první prvek `hash_multimap`.|
|[cend](#cend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v `hash_multimap`.|
|[clear](#clear)|Vymaže všechny prvky `hash_multimap`.|
|[Počet](#count)|Vrátí počet prvků v `hash_multimap` jejichž klíč odpovídá klíči se zadaným parametrem.|
|[crbegin](#crbegin)|Vrátí konstantní iterátor adresující první prvek v obráceném objektu `hash_multimap`.|
|[crend](#crend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu `hash_multimap`.|
|[emplace](#emplace)|Vloží vytvořený prvek na místo do `hash_multimap`.|
|[emplace_hint](#emplace_hint)|Vloží vytvořený prvek na místo do `hash_multimap`, s náznakem umístění.|
|[prázdný](#empty)|Testuje, zda `hash_multimap` je prázdný.|
|[ukončení](#end)|Vrátí iterátor adresující umístění následující po posledním prvku v `hash_multimap`.|
|[equal_range](#equal_range)|Vrátí iterátor adresující umístění následující po posledním prvku v `hash_multimap`.|
|[vymazání](#erase)|Odebere prvek nebo rozsah prvků `hash_multimap` od zadané pozice|
|[Najít](#find)|Vrátí iterátor adresující umístění prvku v `hash_multimap` , který má klíč odpovídající zadanému klíči.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu `allocator` objekt použitý k vytvoření `hash_multimap`.|
|[Vložit](#insert)|Vloží prvek nebo rozsah prvků do `hash_multimap` na určené pozici.|
|[key_comp](#key_comp)|Získá kopii objektu porovnání použitého pro seřazení klíčů v `hash_multimap`.|
|[lower_bound –](#lower_bound)|Vrátí iterátor na první prvek v `hash_multimap` , že hodnotou klíče, který je roven nebo větší než zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délku objektu `hash_multimap`.|
|[rbegin](#rbegin)|Vrátí iterátor adresující první prvek v obráceném objektu `hash_multimap`.|
|[rend –](#rend)|Vrátí iterátor adresující umístění následující po posledním prvku v obráceném objektu `hash_multimap`.|
|[Velikost](#size)|Určuje novou velikost `hash_multimap`.|
|[swap](#swap)|Vymění prvky dvou `hash_multimap`s.|
|[upper_bound](#upper_bound)|Vrátí iterátor na první prvek v `hash_multimap` , že hodnotou klíče, který je větší než zadaný klíč.|
|[value_comp](#value_comp)|Získá kopii objektu porovnání použitého pro seřazení hodnot prvků v `hash_multimap`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[hash_multimap::operator=](#op_eq)|Nahradí prvky objektu `hash_multimap` s kopií jiného `hash_multimap`.|

## <a name="requirements"></a>Požadavky

**Header:** \<hash_map>

**Namespace:** stdext

## <a name="allocator_type"></a>  hash_multimap::allocator_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který představuje třídu alokátoru pro objekt hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type` je synonymum pro parametr šablony `Allocator`.

Další informace o `Allocator`, najdete v části poznámky [hash_multimap – třída](../standard-library/hash-multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_allocator](#get_allocator) příklad použití `allocator_type`.

## <a name="begin"></a>  hash_multimap::begin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor adresující první prvek hash_multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor adresující první prvek v hash_multimap nebo adresující prázdný hash_multimap – umístění.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `begin` je přiřazena `const_iterator`, prvků v objektu hash_multimap nelze upravit. Pokud návratová hodnota `begin` je přiřazena `iterator`, prvků v objektu hash_multimap – je možné upravit.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_begin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 0, 0 ) );
   hm1.insert ( Int_Pair ( 1, 1 ) );
   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.begin ( );
   cout << "The first element of hm1 is " << hm1_cIter -> first
        << "." << endl;

   hm1_Iter = hm1.begin ( );
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.begin ( );
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.begin( );
   cout << "The first element of hm1 is now " << hm1_cIter -> first
        << "." << endl;
}
```

```Output
The first element of hm1 is 0.
The first element of hm1 is now 1.
```

## <a name="cbegin"></a>  hash_multimap::cbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí konstantní iterátor adresující první prvek hash_multimap.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor const adresující první prvek v [hash_multimap](../standard-library/hash-multimap-class.md) nebo umístění následující po prázdná `hash_multimap`.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_cbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
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

## <a name="cend"></a>  hash_multimap::cend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí konstantní iterátor adresující umístění následující po posledním prvku v hash_multimap.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor const adresující umístění následující po posledním prvku v [hash_multimap](../standard-library/hash-multimap-class.md). Pokud `hash_multimap` je prázdný, pak `hash_multimap::cend == hash_multimap::begin`.

### <a name="remarks"></a>Poznámky

`cend` slouží k otestování, zda iterátor dosáhl konce jeho hash_multimap.

Hodnota vrácená `cend` by neměla být dereferencována.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_cend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
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

## <a name="clear"></a>  hash_multimap::clear

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vymaže všechny prvky hash_multimap.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_multimap::clear členskou funkci.

```cpp
// hash_multimap_clear.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 4));

    i = hm1.size();
    cout << "The size of the hash_multimap is initially "
         << i  << "." << endl;

    hm1.clear();
    i = hm1.size();
    cout << "The size of the hash_multimap after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the hash_multimap is initially 2.
The size of the hash_multimap after clearing is 0.
```

## <a name="const_iterator"></a>  hash_multimap::const_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

`const_iterator` Určené hash_multimap – odkazuje na objekty [value_type](#value_type), které jsou typu `pair<const Key, Type>`. Hodnota klíče je k dispozici prostřednictvím první pár členů, hodnota elementu pro mapovanou je k dispozici druhý člen, které odpovídá páru licencí.

Ke zrušení `const_iterator` `cIter` odkazující na prvek v hash_multimap, použijte `->` operátor.

Chcete-li přistupovat k hodnotě klíče pro element, použijte `cIter->first`, což je totéž jako `(*cIter).first`. Chcete-li získat přístup k hodnotě z namapované datum pro element, použijte `cIter->second`, což je totéž jako `(*cIter).second`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin) příklad použití `const_iterator`.

## <a name="const_pointer"></a>  hash_multimap::const_pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje ukazatel **const** prvek hash_multimap –.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku.

Ve většině případů [iterátoru](#iterator) by měla sloužit pro přístup k prvkům v objektu hash_multimap.

## <a name="const_reference"></a>  hash_multimap::const_reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje odkaz na **const** prvek uložený v hash_multimap – pro čtení a provádění **const** operace.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multimap_const_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin() -> second );

   cout << "The data value of 1st element in the hash_multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of 1st element in the hash_multimap is 10.
```

## <a name="const_reverse_iterator"></a>  hash_multimap::const_reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje obousměrný iterátor, který může přečíst jakýkoli **const** prvek hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` hodnotu prvku nelze změnit a použít k iteraci v rámci hash_multimap – v opačném pořadí.

`const_reverse_iterator` Určené hash_multimap – odkazuje na objekty [value_type](#value_type), které jsou typu `pair<const Key, Type>`, jehož první člen je klíčem k elementu a jejichž druhé člen je namapované datum drží elementu.

Ke zrušení `const_reverse_iterator` `crIter` odkazující na prvek v hash_multimap, použijte `->` operátor.

Chcete-li přistupovat k hodnotě klíče pro element, použijte `crIter->first`, což je totéž jako `(*crIter).first`. Chcete-li získat přístup k hodnotě z namapované datum pro element, použijte `crIter->second`, což je totéž jako `(*crIter).second`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rend](#rend) příklad toho, jak deklarovat a použít `const_reverse_iterator`.

## <a name="count"></a>  hash_multimap::Count

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí počet prvků v hash_multimap, jejichž klíč odpovídá klíči se zadaným parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč prvky lze porovnat z hash_multimap.

### <a name="return-value"></a>Návratová hodnota

1, pokud hash_multimap obsahuje element, jejichž řazení klíč odpovídá klíči parametr; 0, pokud hash_multimap neobsahuje prvek s odpovídajícím klíčem.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v rozsahu

**[lower_bound (** `key` **), upper_bound (** `key` **))**

které mají hodnotu klíče *klíč*.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_multimap::count členskou funkci.

```cpp
// hash_multimap_count.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 1));
    hm1.insert(Int_Pair(1, 4));
    hm1.insert(Int_Pair(2, 1));

    // Elements do not need to have unique keys in hash_multimap,
    // so duplicates are allowed and counted
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
The number of elements in hm1 with a sort key of 1 is: 2.
The number of elements in hm1 with a sort key of 2 is: 2.
The number of elements in hm1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  hash_multimap::crbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí konstantní iterátor adresující první prvek v obráceném objektu hash_multimap.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor adresující první prvek v obráceném objektu [hash_multimap](../standard-library/hash-multimap-class.md) nebo co bylo posledním prvkem v neobráceném adresování `hash_multimap`.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s obrácený hash_multimap – stejně jako [hash_multimap::begin](#begin) se používá s `hash_multimap`.

S návratovou hodnotou `crbegin`, `hash_multimap` objekt nelze změnit.

`crbegin` můžete použít k iteraci v rámci `hash_multimap` zpětně.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_crbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
```

## <a name="crend"></a>  hash_multimap::crend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu hash_multimap.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor adresující umístění následující po posledním prvku v obráceném objektu [hash_multimap](../standard-library/hash-multimap-class.md) (umístění, ke které došlo před první prvek v neobráceném `hash_multimap`).

### <a name="remarks"></a>Poznámky

`crend` se používá s obrácený hash_multimap – stejně jako [hash_multimap::end](#end) se používá s hash_multimap.

S návratovou hodnotou `crend`, `hash_multimap` objekt nelze změnit.

`crend` slouží k otestování pro Určuje, zda zpětný iterátor dosáhl konce jeho hash_multimap.

Hodnota vrácená `crend` by neměla být dereferencována.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_crend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crend( );
   hm1_crIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 3.
```

## <a name="difference_type"></a>  hash_multimap::difference_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Celočíselný typ se znaménkem, který slouží k vyjádření počtu prvků hash_multimap – v rozsahu mezi prvky, na které odkazují iterátory.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` Typ dochází při přičítání nebo zvýšení prostřednictvím iterátorů kontejneru. `difference_type` Se obvykle používá k vyjádření počtu prvků v rozsahu *[jméno, příjmení)* mezi iterátory `first` a `last`, obsahuje element, na které odkazuje `first` a rozsah prvky až, ale bez zahrnutí elementu odkazované `last`.

Všimněte si, že i když `difference_type` je k dispozici pro všechny iterátory, které splňují požadavky na vstupní iterátor, který obsahuje třídou obousměrných iterátorů, které jsou podporovány reverzibilního kontejnery, jako je sada odčítání mezi iterátory pouze podporuje iterátory s náhodným přístupem k dispozici kontejnerem náhodného přístupu, jako je například vektoru.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_difference_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>
#include <algorithm>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(3, 20));

    // The following will insert, because map keys
    // do not need to be unique
    hm1.insert(Int_Pair(2, 30));

    hash_multimap<int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;
    hm1_bIter = hm1.begin();
    hm1_eIter = hm1.end();

    // Count the number of elements in a hash_multimap
    hash_multimap<int, int>::difference_type df_count = 0;
    hm1_Iter = hm1.begin();
    while (hm1_Iter != hm1_eIter)
    {
        df_count++;
        hm1_Iter++;
    }

    cout << "The number of elements in the hash_multimap hm1 is: "
         << df_count << "." << endl;

    cout << "The keys of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> first;
    cout << "." << endl;

    cout << "The values of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> second;
    cout << "." << endl;
}
```

```Output
The number of elements in the hash_multimap hm1 is: 4.
The keys of the mapped elements are: 1 2 2 3.
The values of the mapped elements are: 10 20 30 20.
```

## <a name="emplace"></a>  hash_multimap::emplace

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vloží vytvořený prvek na místo do hash_multimap.

```cpp
template <class ValTy>
iterator emplace(ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota použitá pro přesun vytvořit element, který má být vložen do [hash_multimap](../standard-library/hash-multimap-class.md).|

### <a name="return-value"></a>Návratová hodnota

`emplace` Členská funkce vrátí iterátor, který odkazuje na místo, kde byl vložen nový prvek.

### <a name="remarks"></a>Poznámky

[Hash_multimap::value_type](#value_type) elementu je pár, tak, aby hodnota elementu bude seřazená dvojice s první komponenta rovna hodnotě klíče a druhá komponenta rovna hodnotě dat tohoto prvku.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_emplace.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(move(is1));
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

## <a name="emplace_hint"></a>  hash_multimap::emplace_hint

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vloží vytvořený prvek na místo do hash_multimap – s náznakem umístění.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota použitá pro přesun vytvořit element, který má být vložen do [hash_multimap](../standard-library/hash-multimap-class.md) není-li `hash_multimap` již obsahuje tento prvek (nebo více obecně element, jehož klíč je ekvivalentně seřazen).|
|*_Where*|Doporučení týkající se místo zahájení vyhledání správného bodu vložení.|

### <a name="return-value"></a>Návratová hodnota

[Hash_multimap::emplace](#emplace) členská funkce vrátí iterátor, který odkazuje na místo, kde byl vložen nový prvek do `hash_multimap`.

### <a name="remarks"></a>Poznámky

[Hash_multimap::value_type](#value_type) elementu je pár, tak, aby hodnota elementu bude seřazená dvojice s první komponenta rovna hodnotě klíče a druhá komponenta rovna hodnotě dat tohoto prvku.

Vložení může dojít v amortizovaném konstantním času, namísto logaritmické času, pokud kurzor bezprostředně následuje po *_Where*.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_emplace_hint.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(hm1.begin(), move(is1));
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

## <a name="empty"></a>  hash_multimap::Empty

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Testuje, zda je hash_multimap je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud hash_multimap je prázdná. **false** Pokud hash_multimap je prázdný.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multimap_empty.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2;

   typedef pair <int, int> Int_Pair;
   hm1.insert ( Int_Pair ( 1, 1 ) );

   if ( hm1.empty( ) )
      cout << "The hash_multimap hm1 is empty." << endl;
   else
      cout << "The hash_multimap hm1 is not empty." << endl;

   if ( hm2.empty( ) )
      cout << "The hash_multimap hm2 is empty." << endl;
   else
      cout << "The hash_multimap hm2 is not empty." << endl;
}
```

```Output
The hash_multimap hm1 is not empty.
The hash_multimap hm2 is empty.
```

## <a name="end"></a>  hash_multimap::end

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor adresující umístění následující po posledním prvku v hash_multimap.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor adresující umístění následující po posledním prvku v hash_multimap. Pokud hash_multimap je prázdný, pak hash_multimap::end == hash_multimap::begin.

### <a name="remarks"></a>Poznámky

`end` slouží k otestování, zda iterátor dosáhl konce jeho hash_multimap.

Hodnota vrácená `end` by neměla být dereferencována.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_end.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
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

## <a name="equal_range"></a>  hash_multimap::equal_range

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí pár iterátorů v uvedeném pořadí na první prvek v hash_multimap s klíčem, který je větší než zadaný klíč a na první prvek v hash_multimap s klíčem, který je roven nebo větší než tento klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč argumentu k porovnání s klíči řazení prvek z hash_multimap vyhledávaná.

### <a name="return-value"></a>Návratová hodnota

Pár iterátorů tak, že je první [lower_bound](#lower_bound) klíče a druhá je [upper_bound](#upper_bound) klíče.

Pro přístup k první iterace dvojice `pr` vrácený členskou funkci, použijte `pr`. **první** a pokouší dereferencovat iterátoru dolní mez, použijte \*( `pr`. **nejprve**). Pro přístup k druhé iterátoru dvojice `pr` vrácený členskou funkci, použijte `pr`. **druhý** a pokouší dereferencovat iterátoru horní mez, použijte \*( `pr`. **za druhé**).

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multimap_equal_range.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multimap <int, int> IntMMap;
   IntMMap hm1;
   hash_multimap <int, int> :: const_iterator hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = hm1.equal_range( 2 );

   cout << "The lower bound of the element with a key of 2\n"
        << "in the hash_multimap hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with a key of 2\n"
        << "in the hash_multimap hm1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   hm1_RcIter = hm1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << hm1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair "
        << "returned by equal_range( 2 )." << endl;

   p2 = hm1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2
in the hash_multimap hm1 is: 20.
The upper bound of the element with a key of 2
in the hash_multimap hm1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The hash_multimap hm1 doesn't have an element with a key less than 4.
```

## <a name="erase"></a>  hash_multimap::erase

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Odebere prvek nebo rozsah prvků v hash_multimap – od zadané pozice nebo odebere prvky, které odpovídají zadanému klíči.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where*<br/>
Pozice prvku, který chcete odebrat z hash_multimap.

*první*<br/>
Pozice prvního prvku odebrán hash_multimap.

*last*<br/>
Pozice bezprostředně za posledním prvkem odebrán hash_multimap.

*key*<br/>
Klíč prvky, které mají být odebrány hash_multimap –.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který označí první prvek zbývající za jakýmikoli odstraněnými prvky nebo ukazatel na konci hash_multimap – Pokud žádný takový prvek neexistuje.

Třetí členská funkce vrátí počet prvků, které byly odebrány z hash_multimap –.

### <a name="remarks"></a>Poznámky

Členské funkce nikdy nevyvolají výjimku.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_multimap::erase členskou funkci.

```cpp
// hash_multimap_erase.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2, hm3;
    hash_multimap<int, int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multimap<int, int>::size_type n;
    typedef pair<int, int> Int_Pair;

    for (i = 1; i < 5; i++)
    {
        hm1.insert(Int_Pair (i, i) );
        hm2.insert(Int_Pair (i, i*i) );
        hm3.insert(Int_Pair (i, i-1) );
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hm1.begin();
    hm1.erase(Iter1);

    cout << "After the 2nd element is deleted, "
         << "the hash_multimap hm1 is:";
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hm2.begin();
    Iter2 = --hm2.end();
    hm2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_multimap hm2 is:";
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    hm3.insert(Int_Pair (2, 5));
    n = hm3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hm3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hm3.begin();
    hm3.erase(Iter1);

    cout << "After another element with a key equal to that of the"
         << endl;
    cout  << "2nd element is deleted, "
          << "the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_multimap hm1 is: 1 3 4.
After the middle two elements are deleted, the hash_multimap hm2 is: 1 16.
After the element with a key of 2 is deleted,
the hash_multimap hm3 is: 0 2 3.
The number of elements removed from hm3 is: 2.
After another element with a key equal to that of the
2nd element is deleted, the hash_multimap hm3 is: 0 3.
```

## <a name="find"></a>  hash_multimap::Find

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor adresující první umístění prvku v hash_multimap –, který má klíč odpovídající zadanému klíči.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč určený k porovnání s klíči řazení prvek z hash_multimap vyhledaly.

### <a name="return-value"></a>Návratová hodnota

Iterátor adresující první umístění prvku se zadaným klíčem nebo umístění následující po posledním prvku v hash_multimap – Pokud pro klíč není nalezena žádná shoda.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor adresující prvek v hash_multimap, jehož klíč řazení je `equivalent` na argument klíče pod binární predikát, který indukuje má za výsledek řazení podle méně než srovnání vztah.

Pokud návratová hodnota `find` přiřazen `const_iterator`, hash_multimap objekt nelze změnit. Pokud návratová hodnota `find` je přiřazena `iterator`, objekt hash_multimap lze upravit.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_find.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(3, 20));
    hm1.insert(Int_Pair(3, 30));

    hm1_RcIter = hm1.find(2);
    cout << "The element of hash_multimap hm1 with a key of 2 is: "
          << hm1_RcIter -> second << "." << endl;

    hm1_RcIter = hm1.find(3);
    cout << "The first element of hash_multimap hm1 with a key of 3 is: "
          << hm1_RcIter -> second << "." << endl;

    // If no match is found for the key, end() is returned
    hm1_RcIter = hm1.find(4);

    if (hm1_RcIter == hm1.end())
        cout << "The hash_multimap hm1 doesn't have an element "
             << "with a key of 4." << endl;
    else
        cout << "The element of hash_multimap hm1 with a key of 4 is: "
             << hm1_RcIter -> second << "." << endl;

    // The element at a specific location in the hash_multimap can be
    // found using a dereferenced iterator addressing the location
    hm1_AcIter = hm1.end();
    hm1_AcIter--;
    hm1_RcIter = hm1.find(hm1_AcIter -> first);
    cout << "The first element of hm1 with a key matching"
         << endl << "that of the last element is: "
         << hm1_RcIter -> second << "." << endl;

    // Note that the first element with a key equal to
    // the key of the last element is not the last element
    if (hm1_RcIter == --hm1.end())
        cout << "This is the last element of hash_multimap hm1."
             << endl;
    else
        cout << "This is not the last element of hash_multimap hm1."
             << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="get_allocator"></a>  hash_multimap::get_allocator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí kopii přidělování objektu používanou k vytvoření hash_multimap.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor použitý ve hash_multimap.

### <a name="remarks"></a>Poznámky

Alokátory pro hash_multimap – Třída zadejte, jak spravuje třídu úložiště. Výchozí alokátorů součástí třídy kontejneru standardní knihovny C++ postačí pro většinu programovacích potřeb. Psaní a použití vlastní třídu alokátoru je rozšířená C++.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_get_allocator.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int>::allocator_type hm1_Alloc;
   hash_multimap <int, int>::allocator_type hm2_Alloc;
   hash_multimap <int, double>::allocator_type hm3_Alloc;
   hash_multimap <int, int>::allocator_type hm4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> hm2;
   hash_multimap <int, double> hm3;

   hm1_Alloc = hm1.get_allocator( );
   hm2_Alloc = hm2.get_allocator( );
   hm3_Alloc = hm3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm3.max_size( ) <<  "." << endl;

   // The following line creates a hash_multimap hm4
   // with the allocator of hash_multimap hm1.
   hash_multimap <int, int> hm4( less<int>( ), hm1_Alloc );

   hm4_Alloc = hm4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
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

## <a name="hash_multimap"></a>  hash_multimap::hash_multimap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Hash_multimap –, který je prázdný nebo je kopií celého nebo součást některých hash_multimap vytvoří.

```cpp
hash_multimap();

explicit hash_multimap(
    const Compare& Comp);

hash_multimap(
    const Compare& Comp,
    const Allocator& Al);

hash_multimap(
    const hash_multimap& Right);

hash_multimap(
    hash_multimap&& Right);

hash_multimap(
    initializer_list<Type> IList);

hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last,
    const Compare& Comp);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last,
    const Compare& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Al*|Třída úložiště alokátoru má být použit pro tento objekt hash_multimap, kde je použit výchozí `Allocator`.|
|*Kompozice*|Funkce porovnání typu `const Traits` používají k seřazení prvků v objektu map, kde je použit výchozí `Traits`.|
|*doprava*|Objekt map, ze kterého je kopií vytvořen objekt set.|
|*první*|Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.|
|*poslední*|Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.|
|*IList*|Objekt initializer_list bude kopírováno.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají typ objektu allocator, který spravuje úložiště paměti pro hash_multimap – a, který lze později vrátit voláním [get_allocator](#get_allocator). Parametr allocator je často vynecháno v deklaracích třídy a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují své hash_multimap.

Všechny konstruktory ukládají objekt funkce typu `Traits` , který se používá k vytvoření pořadí mezi klíči objektu hash_multimap – a lze později vrátit voláním [key_comp](#key_comp).

První tři konstruktory určují prázdný počáteční hash_multimap; druhý určuje typ funkce porovnání (*kompozici*) který se má použít při stanovení pořadí prvků a třetí explicitně určuje typ alokátoru (`_Al`) který se má použít. Klíčové slovo `explicit` potlačí některé druhy automatického převodu typu.

Čtvrtý konstruktor určuje kopii hash_multimap `Right`.

Následující tři konstruktory kopírují rozsah `First, Last)` objektu map se zvyšující se explicitností v určování typu funkce porovnání třídy `Traits` a alokátorem.

Osmý konstruktor přesune hash_multimap `Right`.

Poslední tři konstruktory použijte seznam initializer_list.

## <a name="insert"></a>  hash_multimap::Insert

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vloží prvek nebo rozsah prvků do hash_multimap.

```cpp
iterator insert(
    const value_type& Val);

iterator insert(
    const_iterator Where,
    const value_type& Val);void insert(
    initializer_list<value_type> IList);

template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

template <class ValTy>
iterator insert(
    ValTy&& Val);

template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota element, který má být vložen do hash_multimap – Pokud už obsahuje tento element, nebo obecně platí, pokud ho již obsahuje prvek, jehož klíč je ekvivalentně seřazen.|
|*kde*|Nápovědu o tom, kde zahájení vyhledání správného bodu vložení.|
|*první*|Pozice prvního prvku, které se mají zkopírovat z mapy.|
|*poslední*|Pozice bezprostředně za posledním prvkem zkopírovány z mapy.|

### <a name="return-value"></a>Návratová hodnota

První dva `insert` členské funkce vrátí iterátor, který odkazuje na místo, kde byl vložen nový prvek.

Třetí členská funkce používá seznam initializer_list pro elementy vložit.

Čtvrtá členská funkce vloží sekvenci hodnot prvků do mapy, která odpovídá každému prvku určenému pomocí iterátoru v rozsahu `[First, Last)` zadané sady.

Poslední dva `insert` členské funkce se chovají stejně jako první dva, s tím rozdílem, že move konstrukce Vložená hodnota.

### <a name="remarks"></a>Poznámky

[Value_type](#value_type) elementu je pár, aby hodnota elementu bude seřazená dvojice, ve které je první komponenta rovna hodnotě klíče a druhá komponenta je rovna hodnotě dat tohoto prvku.

Vložení může dojít v amortizovaném konstantním času pro pomocný parametr verzi `insert`, namísto logaritmické času, pokud kurzor bezprostředně následuje po *kde*.

## <a name="iterator"></a>  hash_multimap::iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Poznámky

`iterator` Určené hash_multimap – odkazuje na objekty [value_type](#value_type), které jsou typu `pair` \< **const Key, typ**>, jehož první člen je klíčem k elementu a jejichž druhé člen je namapované datum drží elementu.

Ke zrušení **iterátoru** `Iter` odkazující na prvek v hash_multimap, použijte `->` operátor.

Chcete-li přistupovat k hodnotě klíče pro element, použijte `Iter`  ->  **první**, což je totéž jako (\* `Iter`). **první**. Chcete-li získat přístup k hodnotě z namapované datum pro element, použijte `Iter`  ->  **druhý**, což je totéž jako (\* `Iter`). **první**.

Typ `iterator` lze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin) příklad toho, jak deklarace a používání `iterator`.

## <a name="key_comp"></a>  hash_multimap::key_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Načte kopii objektu porovnání, použita pro seřazení klíčů v hash_multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, která používá hash_multimap řazení jeho prvky.

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci

**BOOL – operátor (const Key &** `left` **, const Key &** `right` **);**

který vrátí **true** Pokud `left` předchází a není rovno `right` v pořadí řazení.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_key_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::key_compare kc1 = hm1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }

   hash_multimap <int, int, hash_compare<int, greater<int>>> hm2;
   hash_multimap <int, int, hash_compare<int, greater<int>>
      >::key_compare kc2 = hm2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
}
```

## <a name="key_compare"></a>  hash_multimap::key_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ poskytující objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v hash_multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare` je synonymum pro parametr šablony *osobnostní rysy*.

Další informace o *osobnostní rysy* najdete v článku [hash_multimap – třída](../standard-library/hash-multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [key_comp](#key_comp) příklad toho, jak deklarace a používání `key_compare`.

## <a name="key_type"></a>  hash_multimap::key_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který popisuje řazení objektu klíče, který představuje každý prvek hash_multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type` je synonymum pro parametr šablony *klíč*.

Další informace o *klíč*, najdete v části poznámky [hash_multimap – třída](../standard-library/hash-multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_type](#value_type) příklad toho, jak deklarace a používání `key_compare`.

## <a name="lower_bound"></a>  hash_multimap::lower_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor na první prvek v hash_multimap s klíčem, který je roven nebo větší než zadaný klíč.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč argumentu k porovnání s klíči řazení prvek z hash_multimap vyhledávaná.

### <a name="return-value"></a>Návratová hodnota

[Iterátoru](#iterator) nebo [const_iterator](#const_iterator) , který adresuje umístění prvku v hash_multimap s klíčem, který je roven nebo větší než tento klíč argument nebo který adresuje umístění následující po posledním element v hash_multimap – Pokud pro klíč není nalezena žádná shoda.

Pokud návratová hodnota `lower_bound` přiřazen `const_iterator`, hash_multimap objekt nelze změnit. Pokud návratová hodnota `lower_bound` je přiřazena `iterator`, objekt hash_multimap lze upravit.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multimap_lower_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter,
      hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.lower_bound( 2 );
   cout << "The element of hash_multimap hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.lower_bound( 3 );
   cout << "The first element of hash_multimap hm1 with a key of 3 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1.lower_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key matching"
        << endl << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( hm1_RcIter == --hm1.end( ) )
      cout << "This is the last element of hash_multimap hm1."
           << endl;
   else
      cout << "This is not the last element of hash_multimap hm1."
           << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="mapped_type"></a>  hash_multimap::mapped_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který představuje typ dat uložených v hash_multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Poznámky

`mapped_type` je synonymum pro parametr šablony *typ*.

Další informace o *typ* najdete v článku [hash_multimap – třída](../standard-library/hash-multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_type](#value_type) příklad toho, jak deklarace a používání `key_type`.

## <a name="max_size"></a>  hash_multimap::max_size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí maximální délku objektu hash_multimap.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka hash_multimap.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multimap_max_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: size_type i;

   i = hm1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multimap is " << i << "." << endl;
}
```

## <a name="op_eq"></a>  hash_multimap::operator=

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Nahradí prvky objektu hash_multimap kopií jiného hash_multimap.

```cpp
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*doprava*|[Hash_multimap](../standard-library/hash-multimap-class.md) kopírovaná do `hash_multimap`.|

### <a name="remarks"></a>Poznámky

Po odstranění jakýchkoli prvků v `hash_multimap`, `operator=` kopíruje nebo přesouvá obsah *správné* do `hash_multimap`.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_operator_as.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> v1, v2, v3;
   hash_multimap<int, int>::iterator iter;

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

## <a name="pointer"></a>  hash_multimap::Pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje ukazatel na prvek v hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze použít ke změně hodnoty prvku.

Ve většině případů [iterátoru](#iterator) by měla sloužit pro přístup k prvkům v objektu hash_multimap.

## <a name="rbegin"></a>  hash_multimap::rbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor adresující první prvek v obráceném objektu hash_multimap.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresující první prvek v obráceném objektu hash_multimap nebo co bylo posledním prvkem v neobráceném hash_multimap adresování.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s obrácený hash_multimap – stejně jako [začít](#begin) se používá s hash_multimap.

Pokud návratová hodnota `rbegin` je přiřazen `const_reverse_iterator`, pak hash_multimap objekt nelze změnit. Pokud návratová hodnota `rbegin` je přiřazena `reverse_iterator`, pak objekt hash_multimap lze upravit.

`rbegin` můžete použít k iteraci v rámci hash_multimap zpětně.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_rbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = hm1.rbegin( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rbegin( );
   cout << "After the erasure, the first element\n"
        << "in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the first element
in the reversed hash_multimap is 2.
```

## <a name="reference"></a>  hash_multimap::Reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje odkaz na prvek uložený v hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multimap_reference.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of first element in the hash_multimap is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>  hash_multimap::rend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor adresující umístění následující po posledním prvku v obráceném objektu hash_multimap.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresující umístění následující po posledním prvku v obráceném objektu hash_multimap (umístění, ke které došlo před první prvek v neobráceném hash_multimap).

### <a name="remarks"></a>Poznámky

`rend` se používá s obrácený hash_multimap – stejně jako [end](#end) se používá s hash_multimap.

Pokud návratová hodnota `rend` je přiřazen [const_reverse_iterator](#const_reverse_iterator), pak hash_multimap objekt nelze změnit. Pokud návratová hodnota `rend` je přiřazena [reverse_iterator](#reverse_iterator), pak objekt hash_multimap lze upravit.

`rend` slouží k otestování pro Určuje, zda zpětný iterátor dosáhl konce jeho hash_multimap.

Hodnota vrácená `rend` by neměla být dereferencována.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_rend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = --hm1.rend( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 1.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the last element in the reversed hash_multimap is 2.
```

## <a name="reverse_iterator"></a>  hash_multimap::reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném objektu hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iteraci v rámci hash_multimap – v opačném pořadí.

`reverse_iterator` Určené hash_multimap – odkazuje na objekty [value_type](#value_type), které jsou typu `pair` \< **const Key, typ**>. Hodnota klíče je k dispozici prostřednictvím první pár členů, hodnota elementu pro mapovanou je k dispozici druhý člen, které odpovídá páru licencí.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rbegin –](#rbegin) příklad toho, jak deklarace a používání `reverse_iterator`.

## <a name="size"></a>  hash_multimap::size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí počet prvků hash_multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka hash_multimap.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_multimap::size členskou funkci.

```cpp
// hash_multimap_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    i = hm1.size();
    cout << "The hash_multimap length is " << i << "." << endl;

    hm1.insert(Int_Pair(2, 4));
    i = hm1.size();
    cout << "The hash_multimap length is now " << i << "." << endl;
}
```

```Output
The hash_multimap length is 1.
The hash_multimap length is now 2.
```

## <a name="size_type"></a>  hash_multimap::size_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ unsigned integer, která vrátí počet prvků v hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Podívejte se na příklad pro [velikost](#size) příklad toho, jak deklarace a používání `size_type`

## <a name="swap"></a>  hash_multimap::swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vymění prvky dvou hash_multimaps.

```cpp
void swap(hash_multimap& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Hash_multimap – poskytující prvky pro záměnu nebo hash_multimap, jehož prvky mají vyměnit s těmi hash_multimap.

### <a name="remarks"></a>Poznámky

Žádné odkazy, ukazatele nebo iterátory, které určují prvky ve dvou hash_multimaps, jehož prvky jsou během výměny nezruší platnost členskou funkci.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_swap.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   hash_multimap <int, int>::iterator hm1_Iter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm2.insert ( Int_Pair ( 10, 100 ) );
   hm2.insert ( Int_Pair ( 20, 200 ) );
   hm3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   hm1.swap( hm2 );

   cout << "After swapping with hm2, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hm1, hm3 );

   cout << "After swapping with hm3, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original hash_multimap hm1 is: 10 20 30.
After swapping with hm2, hash_multimap hm1 is: 100 200.
After swapping with hm3, hash_multimap hm1 is: 300.
```

## <a name="upper_bound"></a>  hash_multimap::upper_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor na první prvek v hash_multimap s klíčem, který je větší než zadaný klíč.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč argumentu k porovnání s klíči řazení prvek z hash_multimap vyhledávaná.

### <a name="return-value"></a>Návratová hodnota

[Iterátoru](#iterator) nebo [const_iterator](#const_iterator) , který adresuje umístění prvku v hash_multimap s klíčem, který je větší než tento klíč argument nebo který adresuje umístění následující po posledním prvku v hash_multimap –, pokud není nalezena žádná shoda pro klíč.

Pokud návratová hodnota `upper_bound` přiřazen `const_iterator`, hash_multimap objekt nelze změnit. Pokud návratová hodnota `upper_bound` je přiřazen `iterator`, hash_multimap objekt lze upravit.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multimap_upper_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm1.insert ( Int_Pair ( 3, 40 ) );

   hm1_RcIter = hm1.upper_bound( 1 );
   cout << "The 1st element of hash_multimap hm1 with "
        << "a key greater than 1 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.upper_bound( 2 );
   cout << "The first element of hash_multimap hm1\n"
        << "with a key greater than 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.begin( );
   hm1_RcIter = hm1.upper_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key greater than"
        << endl << "that of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of hash_multimap hm1 with a key greater than 1 is: 20.
The first element of hash_multimap hm1
with a key  greater than 2 is: 30.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key greater than
that of the initial element of hm1 is: 20.
```

## <a name="value_comp"></a>  hash_multimap::value_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Členská funkce vrátí objekt funkce, která určuje pořadí prvků v hash_multimap porovnáním jejich hodnoty klíče.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce porovnání, která používá hash_multimap řazení jeho prvky.

### <a name="remarks"></a>Poznámky

Pro hash_multimap *m*, pokud dva prvky *e1* (*k1*, *d1*) a *e2*(*k2* , *d2*) jsou objekty typu [value_type](#value_type), kde *k1* a *k2* jsou jejich klíče typu [key_type](#key_type) a *d1* a *d2* jsou jejich data typu [mapped_type](#mapped_type), pak `m.value_comp()(e1, e2)` je ekvivalentní `m.key_comp()(k1, k2)` . Uložený objekt definuje členskou funkci

`bool operator( value_type& left, value_type& right);`

který vrátí **true** Pokud hodnotu klíče `left` předchází a není rovno hodnotě klíče z `right` v pořadí řazení.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_value_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::value_compare vc1 = hm1.value_comp( );
   hash_multimap <int,int>::iterator Iter1, Iter2;

   Iter1= hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= hm1.insert ( hash_multimap <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *Iter1, *Iter2 ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does "
           << "not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1( *Iter2, *Iter1 ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does "
           << "not precede the element ( 1,10 )."
           << endl;
   }
}
```

## <a name="value_type"></a>  hash_multimap::value_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který představuje typ objektu uloženého ve hash_multimap.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Poznámky

`value_type` je deklarováno jako dvojice\<const [key_type](#key_type), [mapped_type](#mapped_type)> a ne spárujte\<key_type mapped_type > protože klíče asociativní kontejner se nesmí měnit. pomocí nekonstantním iterátoru nebo odkaz.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_value_type.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: key_type key1;
   hash_multimap <int, int> :: mapped_type mapped1;
   hash_multimap <int, int> :: value_type value1;
   hash_multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   hm1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( hm1.begin( ) -> first );
   mapped1 = ( hm1.begin( ) -> second );

   cout << "The key of first element in the hash_multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the hash_multimap is "
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
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
