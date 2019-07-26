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
ms.openlocfilehash: 2022031a52efbc8e8064ae23e14ae19e4aefb77c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448675"
---
# <a name="hashmultimap-class"></a>hash_multimap – třída

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Třída kontejneru hash_multimap je rozšíření C++ standardní knihovny, které se používá pro úložiště a rychlé načítání dat z kolekce, ve které je každý prvek dvojice, která má klíč řazení, jehož hodnota nemusí být jedinečná a přidružená datová hodnota.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare <Key, less <Key>>,
    class Allocator=allocator <pair  <const Key, Type>>>
class hash_multimap
```

### <a name="parameters"></a>Parametry

*Zkrat*\
Klíčový datový typ, který se uloží do hash_multimap.

*Textový*\
Typ dat prvku, který bude uložen v hash_multimap.

*Traits*\
Typ, který obsahuje dva objekty funkce, jeden z *vlastností* třídy, které jsou schopny porovnat dvě hodnoty prvků jako klíče řazení pro určení jejich relativního pořadí a funkci hash, která je unárním predikátem mapování hodnot klíčů prvků na celá čísla bez znaménka Zadejte `size_t`. Tento argument je nepovinný a `hash_compare<Key, less<Key>>` je výchozí hodnota.

*Dělující*\
Typ, který představuje uložený objekt přidělování, který zapouzdřuje informace o přidělování hash_multimap's a navracení paměti. Tento argument je nepovinný a výchozí hodnota je `allocator<pair <const Key, Type>>`.

## <a name="remarks"></a>Poznámky

Hash_multimap je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Hash, protože jeho prvky jsou seskupeny do kontejnerů na základě hodnoty funkce hash použité pro klíčové hodnoty prvků.

- Vícenásobný, protože je prvky nemusí mít jedinečné klíče, takže jedna hodnota klíče může mít k sobě přidružených mnoho datových hodnot prvků.

- Kontejner asociativní podle páru, protože jeho hodnoty prvků jsou odlišné od hodnot klíčů.

- Třída šablony, protože poskytuje obecné funkce a to nezávisle na určitém typu dat obsažených jako prvky nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Hlavní výhodou použití algoritmu hash pro řazení je vyšší efektivita; úspěšné hashování provádí vložení, odstranění a vyhledá v konstantním průměrném čase v porovnání s časem, který je úměrný logaritmu počtu prvků v kontejneru pro řazení technik. Hodnota prvku v hash_multimap, ale ne jeho přidružená hodnota klíče, může být změněna přímo. Namísto toho hodnoty klíčů přidružené ke starým prvkům musí být odstraněny a vloženy nové hodnoty klíče související s novými prvky.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Asociativní kontejnery s algoritmem hash jsou optimalizované pro operace vyhledávání, vkládání a odebírání. Členské funkce, které explicitně podporují tyto operace, jsou efektivní při použití s dobře navrženou funkcí hash a jejich provádění v čase s průměrnou konstantou a nezávisle na počtu prvků v kontejneru. Dobře navržená funkce hash vytváří jednotnou distribuci hodnot hash a minimalizuje počet kolizí, kde je zřejmé, že se vyskytne při mapování jedinečných klíčových hodnot na stejnou hodnotu hash. V nejhorším případě s nejhorší možnou funkcí hash je počet operací úměrný počtu prvků v sekvenci (lineární čas).

Hash_multimap by měl být asociativní kontejner výběru, pokud podmínky přidružování hodnot k jejich klíčům jsou splněné aplikací. Model pro tento typ struktury je uspořádaný seznam klíčových slov s přidruženými řetězcovými hodnotami poskytujícími (řekněme) definice, kde slova nebyla vždy jednoznačně definována. Pokud místo toho byla klíčová slova definována jedinečně, takže klíče byly jedinečné, pak by měl být hash_map kontejnerem volby. Pokud na druhé straně je jenom uložený seznam slov, pak bude hash_set správným kontejnerem. Pokud bylo povoleno více výskytů slov, pak bude hash_multiset odpovídající strukturou kontejneru.

Hash_multimap objedná sekvenci, kterou řídí, voláním uloženého `Traits` objektu hash typu [value_compare](../standard-library/value-compare-class.md). K tomuto uloženému objektu je možné přistupovat voláním členské funkce [key_comp](../standard-library/hash-map-class.md#key_comp). Takový objekt funkce se musí chovat stejně jako objekt třídy [hash_compare](../standard-library/hash-compare-class.md)`<Key, less<Key>>`. Konkrétně pro všechny `Key` hodnoty typu `Key`je volání `Traits (Key)` výsledkem distribuce hodnot typu `size_t`.

Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. Výsledkem je řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát f (x, y) je objekt funkce, který `x` má dva objekty argumentu a `y` a návratovou hodnotu **true** nebo **false**. Řazení uložené na hash_multimap je přísné slabé seřazení, pokud je binární predikát Nereflexivní, antisymetrický a tranzitivní a je-li ekvivalence tranzitivní, kde jsou dva `x` objekty `y` a jsou definovány tak, aby byly ekvivalentní při použití f (x , y) a f (y, x) jsou **false**. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

Skutečné pořadí prvků v řízené sekvenci závisí na funkci hash, funkci řazení a aktuální velikosti zatřiďovací tabulky uložené v objektu kontejneru. Nelze určit aktuální velikost zatřiďovací tabulky, takže nemůžete obecné předpovědět pořadí prvků v řízené sekvenci. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Iterátor poskytnutý třídou hash_multimap je obousměrný iterátor, ale funkce členských funkcí [INSERT](#insert) a [hash_multimap](#hash_multimap) mají verze, které přebírají jako parametry šablony slabší vstupní iterátor, jehož požadavky na funkce jsou více než ty, které jsou zaručené třídou Obousměrných iterátorů. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní hash_multimap požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky poskytované tímto typem iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Jedná se o minimální hash_multimap funkce, ale stačí, abyste se mohli lépe spojit s rozsahem iterátorů `[First, Last)` v kontextu členských funkcí.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[hash_multimap](#hash_multimap)|Sestaví seznam konkrétní velikosti nebo s prvky konkrétní hodnoty nebo s určitou `allocator` nebo jinou kopií. `hash_multimap`|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje `allocator` třídu `hash_multimap` pro objekt.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `const` element `hash_multimap`v.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na prvek const v.  `hash_multimap`|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na prvek **const** uložený v a `hash_multimap` pro čtení a provádění operací **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst libovolný  element const v `hash_multimap`.|
|[difference_type](#difference_type)|Typ se znaménkem typu Integer, který lze použít k reprezentaci počtu prvků `hash_multimap` v rozsahu mezi prvky, na které odkazují iterátory.|
|[iterator](#iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v `hash_multimap`.|
|[key_compare](#key_compare)|Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v `hash_multimap`.|
|[key_type](#key_type)|Typ, který popisuje objekt klíče řazení, který představuje jednotlivé prvky `hash_multimap`.|
|[mapped_type](#mapped_type)|Typ, který představuje datový typ uložený v `hash_multimap`.|
|[pointer](#pointer)|Typ, který poskytuje ukazatel na prvek v `hash_multimap`.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na prvek uložený v `hash_multimap`.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném pořadí `hash_multimap`.|
|[size_type](#size_type)|Typ unsigned integer, který může představovat počet prvků v `hash_multimap`.|
|[value_type](#value_type)|Typ, který poskytuje objekt funkce, který může porovnat dva prvky jako klíče řazení pro určení jejich relativního pořadí v `hash_multimap`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[ifunctiondiscovery](#begin)|Vrátí iterátor adresující první prvek v `hash_multimap`.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor adresující první prvek v `hash_multimap`.|
|[cend](#cend)|Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v `hash_multimap`.|
|[jejich](#clear)|Smaže všechny prvky `hash_multimap`.|
|[výpočtu](#count)|Vrátí počet prvků, `hash_multimap` jejichž klíč odpovídá klíči určenému parametrem.|
|[crbegin](#crbegin)|Vrátí konstantní iterátor adresující první prvek v obráceném pořadí `hash_multimap`.|
|[crend](#crend)|Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v obráceném pořadí `hash_multimap`.|
|[emplace](#emplace)|Vloží prvek konstruovaný na místo `hash_multimap`.|
|[emplace_hint](#emplace_hint)|Vloží prvek konstruovaný do a `hash_multimap`s pomocným parametrem umístění.|
|[empty](#empty)|Testuje, zda `hash_multimap` je objekt prázdný.|
|[účelu](#end)|Vrátí iterátor, který adresuje umístění následující po posledním prvku v `hash_multimap`.|
|[equal_range](#equal_range)|Vrátí iterátor, který adresuje umístění následující po posledním prvku v `hash_multimap`.|
|[ověřování](#erase)|Odebere prvek nebo rozsah prvků v `hash_multimap` zadaném umístění.|
|[najít](#find)|Vrátí iterátor adresující umístění elementu v `hash_multimap` , který má klíč odpovídající zadanému klíči.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objektu použitou k `hash_multimap`vytvoření.|
|[zadat](#insert)|Vloží prvek nebo rozsah prvků do `hash_multimap` zadané pozice.|
|[key_comp](#key_comp)|Načte kopii objektu porovnání, která se používá k řazení klíčů v `hash_multimap`.|
|[lower_bound](#lower_bound)|Vrátí iterátor na první prvek v `hash_multimap` , který má hodnotu klíče, která je rovna nebo větší než zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délku `hash_multimap`.|
|[rbegin](#rbegin)|Vrátí iterátor adresující první prvek v obráceném pořadí `hash_multimap`.|
|[rend](#rend)|Vrátí iterátor, který adresuje umístění následující po posledním prvku v obráceném pořadí `hash_multimap`.|
|[hodnota](#size)|Určuje novou velikost pro `hash_multimap`.|
|[swap](#swap)|Vyměňuje prvky dvou `hash_multimap`s.|
|[upper_bound](#upper_bound)|Vrátí iterátor na první prvek v `hash_multimap` , který má hodnotu klíče, která je větší než zadaný klíč.|
|[value_comp](#value_comp)|Načte kopii objektu porovnání, která se používá k seřazení hodnot prvků v `hash_multimap`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[hash_multimap::operator=](#op_eq)|Nahradí prvky a `hash_multimap` jinou `hash_multimap`kopií.|

## <a name="requirements"></a>Požadavky

**Header:** \<hash_map>

**Obor názvů:** stdext

## <a name="allocator_type"></a>hash_multimap::allocator_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ, který představuje třídu přidělování pro objekt hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type`je synonymum pro parametr `Allocator`šablony.

Další informace o `Allocator`naleznete v části poznámky v tématu [Třída hash_multimap](../standard-library/hash-multimap-class.md) .

### <a name="example"></a>Příklad

Příklad použití `allocator_type`naleznete v příkladu pro [get_allocator](#get_allocator) .

## <a name="begin"></a>hash_multimap:: begin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor adresující první prvek v hash_multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který adresuje první prvek v hash_multimap nebo umístění, které je úspěšné pro prázdné hash_multimap.

### <a name="remarks"></a>Poznámky

Pokud `begin` je vrácená hodnota přiřazena `const_iterator`k, prvky v objektu hash_multimap nelze upravovat. Pokud `begin` je vrácená hodnota přiřazena `iterator`k, lze upravit prvky v objektu hash_multimap.

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

## <a name="cbegin"></a>hash_multimap:: cbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí konstantní iterátor adresující první prvek v hash_multimap.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní obousměrný iterátor, který adresuje první prvek v [hash_multimap](../standard-library/hash-multimap-class.md) nebo je v umístění úspěšné `hash_multimap`.

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

## <a name="cend"></a>hash_multimap:: cend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v hash_multimap.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní obousměrný iterátor, který adresuje umístění následující po posledním prvku v [hash_multimap](../standard-library/hash-multimap-class.md). Pokud je prázdný, pak `hash_multimap::cend == hash_multimap::begin`. `hash_multimap`

### <a name="remarks"></a>Poznámky

`cend`slouží k otestování, zda iterátor dosáhl konce jeho hash_multimap.

Hodnota vrácená `cend` by neměla být zpětně odkazovaná.

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

## <a name="clear"></a>hash_multimap:: Clear

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Smaže všechny prvky hash_multimap.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce hash_multimap:: Clear.

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

## <a name="const_iterator"></a>hash_multimap::const_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst prvek **const** v hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít pro úpravu hodnoty prvku.

Definice hash_multimap odkazuje na objekty [value_type](#value_type), které jsou typu `pair<const Key, Type>`. `const_iterator` Hodnota klíče je k dispozici prostřednictvím prvního páru členů a hodnota mapovaného prvku je k dispozici prostřednictvím druhého člena dvojice.

Chcete-li odkázat `const_iterator` `cIter` na ukazatel ukazující na prvek v hash_multimap, použijte `->` operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `cIter->first`, který je `(*cIter).first`ekvivalentní. Pro přístup k hodnotě mapovaného pro datum elementu použijte `cIter->second`, který je `(*cIter).second`ekvivalentní.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začátek](#begin) příkladu pomocí `const_iterator`.

## <a name="const_pointer"></a>  hash_multimap::const_pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje ukazatel na prvek **const** v hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít pro úpravu hodnoty prvku.

Ve většině případů by měl být použit [iterátor](#iterator) pro přístup k prvkům v objektu hash_multimap.

## <a name="const_reference"></a>hash_multimap::const_reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje odkaz na prvek **const** uložený v hash_multimap pro čtení a provádění operací **const** .

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

## <a name="const_reverse_iterator"></a>hash_multimap::const_reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst libovolný  element const v hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a použít k iteraci přes hash_multimap v obráceném pořadí.

Definice hash_multimap odkazuje na objekty [value_type](#value_type), které jsou typu `pair<const Key, Type>`, jejichž první člen je klíč k elementu a jehož druhým členem je mapované datum uchovávané prvkem. `const_reverse_iterator`

Chcete-li odkázat `const_reverse_iterator` `crIter` na ukazatel ukazující na prvek v hash_multimap, použijte `->` operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `crIter->first`, který je `(*crIter).first`ekvivalentní. Pro přístup k hodnotě mapovaného pro datum elementu použijte `crIter->second`, který je `(*crIter).second`ekvivalentní.

### <a name="example"></a>Příklad

Příklad, jak deklarovat [](#rend) a používat, `const_reverse_iterator`naleznete v příkladu pro rend.

## <a name="count"></a>hash_multimap:: Count

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí počet prvků v hash_multimap, jejichž klíč odpovídá klíči určenému parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*zkrat*\
Klíč prvků, které mají být porovnány s hash_multimap.

### <a name="return-value"></a>Návratová hodnota

1, pokud hash_multimap obsahuje element, jehož klíč řazení odpovídá klíči parametru; 0, pokud hash_multimap neobsahuje element se shodným klíčem.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v rozsahu.

**[lower_bound (** `key` **); Upper_bound (** `key` **))**

který má *klíč*hodnoty klíče.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce hash_multimap:: Count.

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

## <a name="crbegin"></a>hash_multimap:: crbegin –

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí konstantní iterátor adresující první prvek v obráceném hash_multimapě.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor, který adresuje první prvek v obráceném [hash_multimap](../standard-library/hash-multimap-class.md) nebo řeší, co byl poslední prvek v neobráceném pořadí `hash_multimap`.

### <a name="remarks"></a>Poznámky

`crbegin`se používá s obráceným hash_multimap stejně jako [hash_multimap:: begin](#begin) se používá s `hash_multimap`.

S návratovou hodnotou `crbegin` `hash_multimap` nelze objekt upravit.

`crbegin`lze použít k iteraci `hash_multimap` zpětně.

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

## <a name="crend"></a>hash_multimap:: crend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v obráceném hash_multimapě.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor, který adresuje umístění následující po posledním prvku v obráceném [hash_multimap](../standard-library/hash-multimap-class.md) (umístění, které předchází prvnímu prvku v opačném případě `hash_multimap`).

### <a name="remarks"></a>Poznámky

`crend`se používá s obráceným hash_multimap stejně jako [hash_multimap:: end](#end) se používá s hash_multimap.

S návratovou hodnotou `crend` `hash_multimap` nelze objekt upravit.

`crend`dá se použít k otestování, jestli reverzní iterátor dosáhl konce jeho hash_multimap.

Hodnota vrácená `crend` by neměla být zpětně odkazovaná.

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
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ se znaménkem typu Integer, který lze použít k reprezentaci počtu prvků hash_multimap v rozsahu mezi prvky, na které odkazují iterátory.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` Je typ vrácený při odečítání nebo přírůstcích pomocí iterátorů kontejneru. `first` `first` `last`  Obvykle se používá k reprezentaci počtu prvků v rozsahu [First, Last) mezi iterátory a, zahrnuje element, na který se odkazuje, a rozsah prvků až do, ale ne. `difference_type` zahrnutí prvku, na `last`který ukazuje.

Všimněte si, `difference_type` že i když je k dispozici pro všechny iterátory, které splňují požadavky vstupního iterátoru, což zahrnuje třídu Obousměrných iterátorů podporovaných vratnými kontejnery, jako je například set, odečítání mezi iterátory je pouze podporováno iterátory náhodného přístupu, které jsou poskytovány kontejnerem s náhodným přístupem, jako je například Vector.

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

## <a name="emplace"></a>hash_multimap:: emplace

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vloží prvek konstruovaný na místo do hash_multimap.

```cpp
template <class ValTy>
iterator emplace(ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*počítává*|Hodnota použitá k přesunutí konstrukce elementu, který má být vložen do objektu [hash_multimap](../standard-library/hash-multimap-class.md).|

### <a name="return-value"></a>Návratová hodnota

`emplace` Členská funkce vrátí iterátor, který odkazuje na pozici, kam byl nový prvek vložen.

### <a name="remarks"></a>Poznámky

[Hash_multimap:: value_type](#value_type) elementu je dvojice, takže hodnota elementu bude seřazená dvojice s první komponentou, která se rovná hodnotě klíče a druhá komponenta se rovná hodnotě dat elementu.

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

## <a name="emplace_hint"></a>hash_multimap::emplace_hint

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vloží prvek konstruovaný na místo do hash_multimap s pomocným parametrem umístění.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*počítává*|Hodnota, která se používá k přesunutí konstrukce elementu, který má být [](../standard-library/hash-multimap-class.md) vložen do objektu `hash_multimap` hash_multimap, pokud již tento prvek neobsahuje (nebo obecněji je prvek, jehož klíč je ekvivalentně seřazen).|
|*_Where*|Nápověda týkající se místa, kde lze začít hledat správný bod vložení.|

### <a name="return-value"></a>Návratová hodnota

Členská funkce [hash_multimap:: emplace](#emplace) Vrátí iterátor, který odkazuje na pozici, kam byl nový element vložen do `hash_multimap`.

### <a name="remarks"></a>Poznámky

[Hash_multimap:: value_type](#value_type) elementu je dvojice, takže hodnota elementu bude seřazená dvojice s první komponentou, která se rovná hodnotě klíče a druhá komponenta se rovná hodnotě dat elementu.

Vložení se může vyskytnout v konstantním času v čase, namísto logaritmické doby, pokud se bod vložení hned sleduje podle *_Where*.

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

## <a name="empty"></a>hash_multimap:: Empty

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Testuje, zda je hash_multimap prázdné.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je hash_multimap prázdné; **false** , pokud je hash_multimap neprázdné.

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

## <a name="end"></a>hash_multimap:: end

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor, který adresuje umístění následující po posledním prvku v objektu hash_multimap.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který adresuje umístění následující po posledním prvku v hash_multimap. Pokud je hash_multimap prázdné, potom hash_multimap:: end = = hash_multimap:: begin.

### <a name="remarks"></a>Poznámky

`end`slouží k otestování, zda iterátor dosáhl konce jeho hash_multimap.

Hodnota vrácená `end` by neměla být zpětně odkazovaná.

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

## <a name="equal_range"></a>hash_multimap::equal_range

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí dvojici iterátorů v uvedeném pořadí na první prvek v hash_multimap s klíčem, který je větší než zadaný klíč a na první prvek v hash_multimap s klíčem, který je roven nebo větší než klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*zkrat*\
Klíč argumentu, který se má porovnat s klíčem řazení prvku z prohledávané hash_multimapy.

### <a name="return-value"></a>Návratová hodnota

Pár iterátorů, jako je první [lower_bound](#lower_bound) klíče a druhý je [Upper_bound](#upper_bound) klíče.

Pro přístup k prvnímu iterátoru páru `pr` vráceného členskou funkcí použijte `pr`. **nejprve** a pro zpětnou vazbu dolního iterátoru použijte \*( `pr`. **první**). Pro přístup k druhému iterátoru páru `pr` vráceného členskou funkcí použijte `pr`. **sekundy** a pro zpětnou vazbu horního iterátoru, \*použijte `pr`(. **sekundy**).

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

## <a name="erase"></a>hash_multimap:: Erase

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Odebere prvek nebo rozsah prvků v objektu hash_multimap ze zadané pozice nebo odstraní prvky, které odpovídají zadanému klíči.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozice prvku, který má být odebrán z hash_multimap.

*první*\
Pozice prvního prvku byla odebrána z hash_multimap.

*posledního*\
Pozice hned za posledním prvkem odebraným z hash_multimap.

*zkrat*\
Klíč prvků, které mají být odebrány z hash_multimap.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který určuje první prvek zbývající za odebranými prvky, nebo ukazatel na konec hash_multimap, pokud žádný takový prvek neexistuje.

Třetí členská funkce vrátí počet prvků, které byly odebrány z hash_multimap.

### <a name="remarks"></a>Poznámky

Členské funkce nikdy nevyvolají výjimku.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce hash_multimap:: Erase.

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

## <a name="find"></a>hash_multimap:: Find

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor adresující první umístění elementu v hash_multimap, který má klíč shodný se zadaným klíčem.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*zkrat*\
Klíč, který má být porovnán klíčem řazení prvku z hash_multimap.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který adresuje první umístění elementu se zadaným klíčem, nebo umístění, které následuje po posledním prvku v hash_multimap, pokud se pro klíč nenajde žádná shoda.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který adresuje element v hash_multimap, jehož klíč řazení je `equivalent` klíč k argumentu v rámci binárního predikátu, který vystaví řazení na základě vztahu menšího než srovnatelnosti.

Pokud `find` je vrácená hodnota přiřazena `const_iterator`k, objekt hash_multimap nelze změnit. Pokud `find` je vrácená hodnota přiřazena `iterator`k, lze objekt hash_multimap upravit.

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

## <a name="get_allocator"></a>hash_multimap::get_allocator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí kopii objektu přidělování, která se používá k vytvoření hash_multimap.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný hash_multimapem.

### <a name="remarks"></a>Poznámky

Přidělování pro třídu hash_multimap určují, jak Třída spravuje úložiště. Výchozí přidělující třídy kontejnerů C++ standardní knihovny jsou dostačující pro většinu programovacích potřeb. Psaní a používání vlastního třídy přidělování je pokročilým C++ tématem.

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

## <a name="hash_multimap"></a>hash_multimap::hash_multimap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vytvoří hash_multimap, který je prázdný nebo je kopií všech nebo částí nějakého jiného hash_multimap.

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
|*VŠ*|Třída přidělování úložiště, která se má použít pro tento objekt hash_multimap, který má `Allocator`výchozí hodnotu.|
|*Zajištění*|Funkce porovnání typu `const Traits` sloužící k uspořádání prvků v mapě, což je `Traits`výchozí hodnota.|
|*Kliknutím*|Objekt map, ze kterého je kopií vytvořen objekt set.|
|*První*|Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.|
|*Posledního*|Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.|
|*IList*|Initializer_list, ze kterého se má kopírovat.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají typ objektu přidělování, který spravuje paměťové úložiště pro hash_multimap a který lze později vrátit voláním [get_allocator](#get_allocator). Parametr přidělování je často v deklaracích tříd vynechán a makra předběžného zpracování se používají k nahrazení alternativních přidělování.

Všechny konstruktory inicializují své hash_multimap.

Všechny konstruktory ukládají objekt funkce typu `Traits` , který se používá k navázání objednávky mezi klíči hash_multimap a může být později vrácen voláním [key_comp](#key_comp).

První tři konstruktory určují prázdné počáteční hash_multimap; druhý určuje typ funkce porovnání (*comp*), která se použije při vytváření pořadí prvků, a třetí explicitně určuje typ přidělujícího prvku (`_Al`), který se má použít. Klíčové slovo `explicit` potlačí určité druhy automatických převodů typu.

Čtvrtý konstruktor určuje kopii hash_multimap `Right`.

Následující tři konstruktory kopírují rozsah `First, Last)` mapy se zvýšením explicitního určení typu funkce porovnání třídy `Traits` a přidělování.

Osmý konstruktor přesune hash_multimap `Right`.

Poslední tři konstruktory používají initializer_list.

## <a name="insert"></a>hash_multimap:: INSERT

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vloží prvek nebo rozsah prvků do objektu hash_multimap.

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
|*Počítává*|Hodnota elementu, který má být vložen do hash_multimap, pokud již tento prvek neobsahuje, nebo obecněji, pokud již neobsahuje prvek, jehož klíč je ekvivalentní objednaný.|
|*,*|Pomocný parametr, kde začít hledat správný bod vložení|
|*První*|Pozice prvního prvku, který má být zkopírován z mapy.|
|*Posledního*|Pozice bezprostředně za posledním prvkem, který má být zkopírován z mapy.|

### <a name="return-value"></a>Návratová hodnota

První dvě `insert` členské funkce vrátí iterátor, který odkazuje na pozici, kam byl nový prvek vložen.

Třetí členská funkce používá initializer_list pro prvky, které mají být vloženy.

Čtvrtá členská funkce vloží sekvenci hodnot prvků do mapy, která odpovídá každému prvku, který je adresován iterátorem v rozsahu `[First, Last)` zadané sady.

Poslední dvě `insert` členské funkce se chovají stejně jako první dva, s tím rozdílem, že přesouvají-vytvoří vloženou hodnotu.

### <a name="remarks"></a>Poznámky

[Value_type](#value_type) elementu je pár, takže hodnota elementu bude seřazená dvojice, ve které je první komponenta rovna hodnotě klíče a druhá součást je rovna hodnotě dat elementu.

Vložení se může vyskytnout v konstantním konstantním čase pro verzi `insert`pomocného parametru, namísto logaritmické doby, pokud kurzor okamžitě následuje *tam, kde*.

## <a name="iterator"></a>hash_multimap:: iterátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Poznámky

[](#value_type) `pair` \< Hash_multimap odkazuje na objekty value_type, které jsou typu const Key, Type >, jehož prvním členem je klíč k elementu a jehož druhým členem je mapované datum uchovávané `iterator` element.

Chcete-li odkázat na **iterátor** `Iter` ukazující na prvek v `->` hash_multimap, použijte operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `Iter`  ->  **nejprve**, který je ekvivalentní (\* `Iter`). **nejprve**. Chcete-li získat přístup k hodnotě mapovaného pole datum pro element `Iter`, použijte  ->  **druhý**, který je ekvivalentní\* ( `Iter`). **nejprve**.

Typ `iterator` lze použít pro úpravu hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začátek](#begin) příkladu, jak deklarovat a použít `iterator`.

## <a name="key_comp"></a>hash_multimap::key_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Načte kopii objektu porovnání, která se používá k řazení klíčů v hash_multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který hash_multimap používá k seřazení jeho prvků.

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci.

**bool – operátor (const Key &** `left` **, const Key &** `right` **);**

který vrátí **hodnotu true** , pokud `left` předchází a není rovno `right` v pořadí řazení.

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

## <a name="key_compare"></a>hash_multimap::key_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v hash_multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare`je synonymem *vlastností*parametrů šablony.

Další informace o *vlastnostích* naleznete v tématu [třídy hash_multimap](../standard-library/hash-multimap-class.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat [](#key_comp) a používat `key_compare`, naleznete v příkladu pro key_comp.

## <a name="key_type"></a>  hash_multimap::key_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ, který popisuje objekt klíče řazení, který představuje každý prvek hash_multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type`je synonymum pro *klíč*parametru šablony.

Další informace o *klíči*naleznete v části poznámky v tématu [Třída hash_multimap](../standard-library/hash-multimap-class.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat [](#value_type) a používat `key_compare`, naleznete v příkladu pro value_type.

## <a name="lower_bound"></a>hash_multimap::lower_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor na první prvek v hash_multimap s klíčem, který je větší nebo roven zadanému klíči.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*zkrat*\
Klíč argumentu, který se má porovnat s klíčem řazení prvku z prohledávané hash_multimapy.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator](#const_iterator) , které řeší umístění elementu v hash_multimap s klíčem, který je roven nebo větší než klíč argumentu nebo který řeší umístění, které následuje po posledním prvku v hash_multimap, pokud není shoda Nalezeno pro klíč.

Pokud `lower_bound` je vrácená hodnota přiřazena `const_iterator`k, objekt hash_multimap nelze změnit. Pokud `lower_bound` je vrácená hodnota přiřazena `iterator`k, lze objekt hash_multimap upravit.

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

## <a name="mapped_type"></a>hash_multimap::mapped_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ, který představuje datový typ uložený ve hash_multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Poznámky

`mapped_type`je synonymum pro *typ*parametru šablony.

Další informace o *typu* najdete v tématu [Třída hash_multimap](../standard-library/hash-multimap-class.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat [](#value_type) a používat `key_type`, naleznete v příkladu pro value_type.

## <a name="max_size"></a>hash_multimap::max_size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí maximální délku hash_multimap.

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

## <a name="op_eq"></a>hash_multimap:: operator =

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Nahradí prvky hash_multimap kopií jiného hash_multimap.

```cpp
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Kliknutím*|[Hash_multimap](../standard-library/hash-multimap-class.md) , který se kopíruje `hash_multimap`do.|

### <a name="remarks"></a>Poznámky

Po vymazání všech existujících prvků `hash_multimap`v, `operator=` buď zkopíruje nebo přesune `hash_multimap`obsah *přímo* do.

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

## <a name="pointer"></a>hash_multimap::p ointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje ukazatel na prvek v hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze použít pro úpravu hodnoty prvku.

Ve většině případů by měl být použit [iterátor](#iterator) pro přístup k prvkům v objektu hash_multimap.

## <a name="rbegin"></a>hash_multimap:: rbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor adresující první prvek v obráceném hash_multimapě.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor, který adresuje první prvek v obráceném hash_multimap nebo řeší, co byl posledním prvkem v neobráceném hash_multimap.

### <a name="remarks"></a>Poznámky

`rbegin`se používá s obráceným hash_multimap stejně jako [Begin](#begin) se používá s hash_multimap.

Pokud `rbegin` je vrácená hodnota přiřazena `const_reverse_iterator`k, nelze objekt hash_multimap změnit. Pokud `rbegin` je vrácená hodnota přiřazena `reverse_iterator`k, lze objekt hash_multimap upravit.

`rbegin`dá se použít k iteraci hash_multimap dozadu.

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

## <a name="reference"></a>hash_multimap:: Reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje odkaz na prvek uložený v objektu hash_multimap.

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

## <a name="rend"></a>hash_multimap:: rend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor, který adresuje umístění následující po posledním prvku v obráceném hash_multimapě.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Zpětný obousměrný iterátor, který adresuje umístění následující po posledním prvku v obráceném hash_multimap (umístění, které předchází prvnímu prvku v neobráceném hash_multimap).

### <a name="remarks"></a>Poznámky

`rend`se používá s obráceným hash_multimap jako [End](#end) se používá s hash_multimap.

Pokud `rend` je vrácená hodnota přiřazena k [const_reverse_iterator](#const_reverse_iterator), objekt hash_multimap nelze změnit. Pokud `rend` je vrácená hodnota přiřazena k [reverse_iterator](#reverse_iterator), lze objekt hash_multimap upravit.

`rend`dá se použít k otestování, jestli reverzní iterátor dosáhl konce jeho hash_multimap.

Hodnota vrácená `rend` by neměla být zpětně odkazovaná.

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

## <a name="reverse_iterator"></a>hash_multimap::reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném hash_multimapě.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iterování přes hash_multimap v obráceném pořadí.

[](#value_type) `pair` \< Definice hash_multimap odkazuje na objekty value_type, které jsou typu const Key, zadejte >. `reverse_iterator` Hodnota klíče je k dispozici prostřednictvím prvního páru členů a hodnota mapovaného prvku je k dispozici prostřednictvím druhého člena dvojice.

### <a name="example"></a>Příklad

Příklad, jak deklarovat [](#rbegin) a používat `reverse_iterator`, naleznete v příkladu pro rbegin.

## <a name="size"></a>hash_multimap:: size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí počet prvků v hash_multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka hash_multimap.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce hash_multimap:: size.

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

## <a name="size_type"></a>hash_multimap::size_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ unsigned integer, který počítá počet prvků v hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Podívejte se na příklad pro [Velikost](#size) pro příklad, jak deklarovat a použít`size_type`

## <a name="swap"></a>  hash_multimap::swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vyměňuje prvky dvou hash_multimaps.

```cpp
void swap(hash_multimap& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Hash_multimap poskytuje prvky, které mají být měněny, nebo hash_multimap, jejichž prvky mají být vyměňovány pomocí těch hash_multimap.

### <a name="remarks"></a>Poznámky

Členská funkce neověřuje žádné odkazy, ukazatele nebo iterátory, které určují elementy ve dvou hash_multimaps, jejichž prvky se vyměňují.

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

## <a name="upper_bound"></a>hash_multimap::upper_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Vrátí iterátor na první prvek v hash_multimap s klíčem, který je větší než zadaný klíč.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*zkrat*\
Klíč argumentu, který se má porovnat s klíčem řazení prvku z prohledávané hash_multimapy.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator](#const_iterator) , které řeší umístění elementu v hash_multimap s klíčem, který je větší než klíč argumentu, nebo který řeší umístění, které následuje po posledním prvku v hash_multimap, pokud není nalezena shoda pro zkrat.

Pokud `upper_bound` je vrácená hodnota přiřazena `const_iterator`k, objekt hash_multimap nelze změnit. Pokud `upper_bound` je vrácená hodnota přiřazena `iterator`k, lze objekt hash_multimap upravit.

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

## <a name="value_comp"></a>hash_multimap::value_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Členská funkce vrátí objekt funkce, který určuje pořadí prvků v hash_multimap porovnáním jejich hodnot klíče.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce porovnání, který hash_multimap používá k seřazení jeho prvků.

### <a name="remarks"></a>Poznámky

Pro hash_multimap *m*, pokud dva prvky *E1* (*K1*, *D1*) a *E2*(*K2*, *D2*) jsou objekty typu [value_type](#value_type), kde *K1* a *K2* jsou jejich klíče typu [key_type](#key_type) a *D1* a *D2* jsou jejich data typu [mapped_type](#mapped_type) `m.value_comp()(e1, e2)` `m.key_comp()(k1, k2)`a pak jsou ekvivalentní. Uložený objekt definuje členskou funkci.

`bool operator( value_type& left, value_type& right);`

Vrátí hodnotu **true** , pokud hodnota `left` klíče předchází a není rovna hodnotě `right` klíče v pořadí řazení.

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

## <a name="value_type"></a>hash_multimap::value_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multimap třída](../standard-library/unordered-multimap-class.md).

Typ, který představuje typ objektu uložený ve hash_multimap.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Poznámky

`value_type`je deklarován jako párování\<const [key_type](#key_type), [mapped_type](#mapped_type)> a NOT\<párové key_type, mapped_type >, protože klíče asociativního kontejneru se nesmí měnit pomocí nekonstantního iterátoru nebo odkazu.

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

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
