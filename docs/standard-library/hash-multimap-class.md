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
ms.openlocfilehash: 2fe9056996876d24fba285c0c7aaec8607b2509c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375437"
---
# <a name="hash_multimap-class"></a>hash_multimap – třída

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Třída kontejneru hash_multimap je rozšíření standardní knihovny Jazyka C++ a používá se pro ukládání a rychlé načítání dat z kolekce, ve kterém každý prvek je pár, který má klíč řazení, jehož hodnota nemusí být jedinečný a související hodnotu dat.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare <Key, less <Key>>,
    class Allocator=allocator <pair  <const Key, Type>>>
class hash_multimap
```

### <a name="parameters"></a>Parametry

*Klíč*\
Datový typ klíče, který má být uložen v hash_multimap.

*Typ*\
Datový typ prvku, který má být uložen v hash_multimap.

*Vlastnosti*\
Typ, který obsahuje dva objekty funkce, jeden z *vlastností třídy,* který je schopen porovnat dvě hodnoty prvků jako klíče řazení k určení jejich relativní pořadí a `size_t`hash funkce, která je unární predikát mapování klíčových hodnot prvků neznatelná celá čísla typu . Tento argument je volitelný `hash_compare<Key, less<Key>>` a je výchozí hodnota.

*Přidělování*\
Typ, který představuje uložený objekt přidělování, který zapouzdřuje podrobnosti o přidělení hash_multimap a přidělení paměti. Tento argument je volitelný a `allocator<pair <const Key, Type>>`výchozí hodnota je .

## <a name="remarks"></a>Poznámky

Hash_multimap je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Hashed, protože jeho prvky jsou seskupeny do bloků na základě hodnoty funkce hash aplikované na klíčové hodnoty prvků.

- Vícenásobný, protože je prvky nemusí mít jedinečné klíče, takže jedna hodnota klíče může mít k sobě přidružených mnoho datových hodnot prvků.

- Dvojice asociativní kontejner, protože jeho hodnoty prvků se liší od jeho hodnoty klíče.

- Šablona třídy, protože funkce, které poskytuje, je obecná a tak nezávislá na konkrétním typu dat obsažených jako prvky nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Hlavní výhodou hašování nad tříděním je větší účinnost; úspěšné zapisování provádí vložení, odstranění a najde v konstantní mzda v průměru čas ve srovnání s časem úměrná logaritmu počtu prvků v kontejneru pro řazení techniky. Hodnota prvku v hash_multimap, ale ne jeho přidružené hodnoty klíče, může být změněna přímo. Namísto toho hodnoty klíčů přidružené ke starým prvkům musí být odstraněny a vloženy nové hodnoty klíče související s novými prvky.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Hashed asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstraňování. Členské funkce, které explicitně podporují tyto operace jsou efektivní při použití s dobře navržené funkce hash, jejich provádění v čase, který je v průměru konstantní a není závislý na počtu prvků v kontejneru. Dobře navržená funkce hash vytváří rovnoměrné rozložení hodnot hash a minimalizuje počet kolizí, kde se říká, že ke kolizi dochází, když jsou odlišné hodnoty klíče mapovány na stejnou hodnotu hash. V nejhorším případě s nejhorší možnou funkcí hash je počet operací úměrný počtu prvků v sekvenci (lineární čas).

Hash_multimap by měl být asociativní kontejner volby při podmínky přisouvání hodnoty s jejich klíče jsou splněny aplikací. Model pro tento typ struktury je uspořádaný seznam klíčových slov s přidruženými řetězcovými hodnotami poskytujícími (řekněme) definice, kde slova nebyla vždy jednoznačně definována. Pokud místo toho klíčová slova byly jednoznačně definovány tak, aby klíče byly jedinečné, pak hash_map by kontejner volby. Pokud by na druhé straně byl uložen pouze seznam slov, pak by hash_set byl správný kontejner. Pokud bylo povoleno více výskytů slov, pak by hash_multiset byla příslušnou strukturou kontejneru.

Hash_multimap seřídí sekvenci, kterou `Traits` řídí voláním uloženého objektu hash typu [value_compare](../standard-library/value-compare-class.md). K tomuto uloženému objektu lze přistupovat voláním key_comp členské [funkce](../standard-library/hash-map-class.md#key_comp). Takový objekt funkce se musí chovat stejně jako objekt třídy [hash_compare](../standard-library/hash-compare-class.md)`<Key, less<Key>>`. Konkrétně pro všechny `Key` hodnoty `Key`typu `Traits (Key)` volání dává rozdělení hodnot `size_t`typu .

Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. Výsledkem je řazení mezi prvky neekvivalentní. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát f(x, y) je objekt funkce, `x` `y` který má dva objekty argumentů a vrácenou hodnotu **true** nebo **false**. Řazení uložené na hash_multimap je přísné slabé řazení, pokud binární predikát je nereflexivní, antisymetrické a tranzitivní a `x` `y` pokud je rovnocennost přenositá, kde jsou dva objekty a jsou definovány jako rovnocenné, když jsou oba f(x, y) a f(y, x) **false**. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

Skutečné pořadí prvků v řízené sekvenci závisí na funkci hash, funkci řazení a aktuální velikost tabulky hash uložené v objektu kontejneru. Nelze určit aktuální velikost tabulky hash, takže obecně nelze předpovědět pořadí prvků v řízené sekvenci. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Iterátor poskytované hash_multimap třídy je obousměrný iterátor, ale funkce členů třídy [vložit](#insert) a [hash_multimap](#hash_multimap) mít verze, které berou jako parametry šablony slabší vstupní iterátor, jehož požadavky na funkčnost jsou minimální než ty, které jsou zaručeny třídou obousměrné iterátory. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má své vlastní hash_multimap požadavků a algoritmy, které s nimi pracují, musí omezit své předpoklady na požadavky poskytované tímto typem iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Jedná se o minimální hash_multimap funkčnosti, ale stačí, abyste mohli smysluplně hovořit o `[First, Last)` řadě iterátorů v kontextu členských funkcí.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[hash_multimap](#hash_multimap)|Vytvoří seznam určité velikosti nebo s prvky určité hodnoty `allocator` nebo s konkrétní `hash_multimap`nebo jako kopie některé jiné .|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který `allocator` představuje třídu `hash_multimap` pro objekt.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který `const` může `hash_multimap`číst prvek v .|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na **const** element v `hash_multimap`.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na **const** `hash_multimap` prvek uložený v a pro čtení a provádění **const** operací.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `hash_multimap`libovolný **prvek const** v .|
|[difference_type](#difference_type)|Podepsaný typ celé číslo, který lze použít k reprezentaci počtu prvků `hash_multimap` a v rozsahu mezi prvky, na které iterátory poukázaly.|
|[Iterace](#iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `hash_multimap`nebo upravovat libovolný prvek v rozhraní .|
|[key_compare](#key_compare)|Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení `hash_multimap`k určení relativní pořadí dvou prvků v .|
|[key_type](#key_type)|Typ, který popisuje objekt klíče řazení, který `hash_multimap`představuje každý prvek .|
|[mapped_type](#mapped_type)|Typ, který představuje datový typ `hash_multimap`uložený v aplikaci .|
|[ukazatel](#pointer)|Typ, který poskytuje ukazatel na `hash_multimap`prvek v .|
|[Odkaz](#reference)|Typ, který poskytuje odkaz na prvek `hash_multimap`uložený v .|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo `hash_multimap`upravovat prvek v obráceném .|
|[size_type](#size_type)|Nepodepsaný podnosný typ, který může představovat počet prvků v . `hash_multimap`|
|[value_type](#value_type)|Typ, který poskytuje objekt funkce, který může porovnat dva prvky `hash_multimap`jako klíče řazení k určení jejich relativní pořadí v .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Začít](#begin)|Vrátí iterátor adresující první prvek `hash_multimap`v rozhraní .|
|[cbegin](#cbegin)|Vrátí const iterator adresující první `hash_multimap`prvek v rozhraní .|
|[cend](#cend)|Vrátí const iterátor, který řeší umístění, které následuje `hash_multimap`poslední prvek v .|
|[Jasné](#clear)|Vymaže všechny `hash_multimap`prvky .|
|[Počet](#count)|Vrátí počet prvků v `hash_multimap` klíči, jejichž klíč odpovídá klíči zadanému parametrem.|
|[crbegin](#crbegin)|Vrátí const iterator adresování první `hash_multimap`prvek v obrácené .|
|[crend](#crend)|Vrátí const iterator, který řeší umístění, které následuje `hash_multimap`poslední prvek v obráceném .|
|[místo](#emplace)|Vloží prvek vytvořený na místě `hash_multimap`do .|
|[emplace_hint](#emplace_hint)|Vloží prvek vytvořený na místě `hash_multimap`do aplikace s nápovědou k umístění.|
|[empty](#empty)|Testuje, `hash_multimap` pokud je prázdný.|
|[Konec](#end)|Vrátí iterátor, který řeší umístění, které následuje `hash_multimap`poslední prvek v rozhraní .|
|[equal_range](#equal_range)|Vrátí iterátor, který řeší umístění, které následuje `hash_multimap`poslední prvek v rozhraní .|
|[Vymazat](#erase)|Odstraní prvek nebo rozsah prvků v `hash_multimap` a ze zadaných pozic.|
|[find](#find)|Vrátí iterátor adresování umístění prvku `hash_multimap` v, který má klíč ekvivalentní zadaný klíč.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objektu použitého `hash_multimap`k vytvoření .|
|[Vložit](#insert)|Vloží prvek nebo rozsah prvků do `hash_multimap` zadané polohy.|
|[key_comp](#key_comp)|Načte kopii objektu porovnání použitého `hash_multimap`k objednání klíčů v .|
|[lower_bound](#lower_bound)|Vrátí iterátor prvnímu prvku v `hash_multimap` prvku, který má hodnotu klíče, která je stejná nebo větší než hodnota zadaného klíče.|
|[max_size](#max_size)|Vrátí maximální délku `hash_multimap`.|
|[rbegin](#rbegin)|Vrátí iterátor adresující první prvek `hash_multimap`v obráceném .|
|[rend](#rend)|Vrátí iterátor, který řeší umístění, které následuje poslední `hash_multimap`prvek v obráceném .|
|[Velikost](#size)|Určuje novou velikost pro `hash_multimap`.|
|[Swap](#swap)|Vyměňuje prvky `hash_multimap`dvou s.|
|[upper_bound](#upper_bound)|Vrátí iterátor prvnímu prvku v `hash_multimap` prvku, který má hodnotu klíče, která je větší než hodnota zadaného klíče.|
|[value_comp](#value_comp)|Načte kopii objektu porovnání použitého k `hash_multimap`pořadí hodnot prvků v rozhraní .|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[hash_multimap::operátor=](#op_eq)|Nahradí prvky a `hash_multimap` kopií jiného `hash_multimap`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<hash_map>

**Obor názvů:** stdext

## <a name="hash_multimapallocator_type"></a><a name="allocator_type"></a>hash_multimap::allocator_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, který představuje třídu alokátoru pro objekt hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type`je synonymem pro `Allocator`parametr šablony .

Další informace `Allocator`naleznete v části Poznámky v tématu [hash_multimap třída.](../standard-library/hash-multimap-class.md)

### <a name="example"></a>Příklad

Viz příklad pro [get_allocator](#get_allocator) příklad `allocator_type`pomocí .

## <a name="hash_multimapbegin"></a><a name="begin"></a>hash_multimap::začátek

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí iterátor adresování první prvek v hash_multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný itečelní objekt adresující první prvek v hash_multimap nebo umístění, které následuje prázdný hash_multimap.

### <a name="remarks"></a>Poznámky

Pokud `begin` je vrácená hodnota `const_iterator`přiřazena aplikaci , nelze prvky v hash_multimap objektu změnit. Pokud `begin` je vrácená hodnota `iterator`přiřazena k , prvky v objektu hash_multimap lze změnit.

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

## <a name="hash_multimapcbegin"></a><a name="cbegin"></a>hash_multimap::cbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí const iterator adresování první prvek v hash_multimap.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstovat obousměrný iterátor adresování první prvek v [hash_multimap](../standard-library/hash-multimap-class.md) nebo `hash_multimap`umístění, které následuje prázdné .

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

## <a name="hash_multimapcend"></a><a name="cend"></a>hash_multimap::cenzura

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí const iterator, který řeší umístění, které následuje poslední prvek v hash_multimap.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstovat obousměrný iterátor, který řeší umístění, které následuje poslední prvek v [hash_multimap](../standard-library/hash-multimap-class.md). Pokud `hash_multimap` je prázdný, `hash_multimap::cend == hash_multimap::begin`pak .

### <a name="remarks"></a>Poznámky

`cend`se používá k testování, zda iterátor dosáhl konce svého hash_multimap.

Hodnota vrácená `cend` by neměla být odkazována.

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

## <a name="hash_multimapclear"></a><a name="clear"></a>hash_multimap::vymazat

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vymaže všechny prvky hash_multimap.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_multimap::clear členské funkce.

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

## <a name="hash_multimapconst_iterator"></a><a name="const_iterator"></a>hash_multimap::const_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek v hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

Definované `const_iterator` hash_multimap odkazuje na objekty [value_type](#value_type), `pair<const Key, Type>`které jsou typu . Hodnota klíče je k dispozici prostřednictvím první dvojice členů a hodnota mapovaného prvku je k dispozici prostřednictvím druhého člena dvojice.

Chcete-li `const_iterator` `cIter` odkazovat na odkaz ukazující na `->` prvek v hash_multimap, použijte operátor.

Chcete-li získat přístup k hodnotě `cIter->first`klíče pro `(*cIter).first`prvek, použijte , což je ekvivalentní . Chcete-li získat přístup k hodnotě mapované základny pro prvek, použijte `cIter->second`, což je ekvivalentní `(*cIter).second`.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) `const_iterator`pro příklad pomocí .

## <a name="hash_multimapconst_pointer"></a><a name="const_pointer"></a>hash_multimap::const_pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje ukazatel na **const** prvek v hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku.

Ve většině případů [iterátor](#iterator) by měl být použit pro přístup k prvkům v hash_multimap objektu.

## <a name="hash_multimapconst_reference"></a><a name="const_reference"></a>hash_multimap::const_reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje odkaz na **prvek const** uložený v hash_multimap pro čtení a provádění operací **const.**

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

## <a name="hash_multimapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>hash_multimap::const_reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst libovolný **prvek const** v hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a používá se k iterátu prostřednictvím hash_multimap v opačném pořadí.

Definované `const_reverse_iterator` hash_multimap odkazuje na objekty [value_type](#value_type), `pair<const Key, Type>`které jsou typu , jehož první člen je klíčem k prvku a jehož druhý člen je mapované datum držené elementem.

Chcete-li `const_reverse_iterator` `crIter` odkazovat na odkaz ukazující na `->` prvek v hash_multimap, použijte operátor.

Chcete-li získat přístup k hodnotě `crIter->first`klíče pro `(*crIter).first`prvek, použijte , což je ekvivalentní . Chcete-li získat přístup k hodnotě mapované základny pro prvek, použijte `crIter->second`, což je ekvivalentní `(*crIter).second`.

### <a name="example"></a>Příklad

Příklad pro [rend](#rend) naleznete v příkladu, jak `const_reverse_iterator`deklarovat a používat .

## <a name="hash_multimapcount"></a><a name="count"></a>hash_multimap::počet

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí počet prvků v hash_multimap jehož klíč odpovídá klíči zadanému parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč prvků, které mají být uzavřeno z hash_multimap.

### <a name="return-value"></a>Návratová hodnota

1 pokud hash_multimap obsahuje prvek, jehož klíč řazení odpovídá klíči parametru; 0, pokud hash_multimap neobsahuje prvek s odpovídající klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v rozsahu

**[lower_bound (** `key` **), upper_bound (** `key` **)**

které mají *klíč*hodnoty klíče .

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_multimap::count členské funkce.

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

## <a name="hash_multimapcrbegin"></a><a name="crbegin"></a>hash_multimap::crbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí const iterator adresování první prvek v obrácené hash_multimap.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor adresování první prvek v obrácené [hash_multimap](../standard-library/hash-multimap-class.md) nebo řešení toho, co bylo poslední prvek v unreverse `hash_multimap`.

### <a name="remarks"></a>Poznámky

`crbegin`se používá s obráceným hash_multimap stejně `hash_multimap`jako [hash_multimap::begin](#begin) se používá s .

S vrácenou `crbegin`hodnotou `hash_multimap` aplikace nelze objekt změnit.

`crbegin`lze použít k iterovat přes `hash_multimap` dozadu.

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

## <a name="hash_multimapcrend"></a><a name="crend"></a>hash_multimap::crend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí const iterátor, který řeší umístění, které následuje poslední prvek v obráceném hash_multimap.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor, který řeší umístění, které následuje poslední prvek v obrácené [masce hash_multimap](../standard-library/hash-multimap-class.md) `hash_multimap`(umístění, které předcházelo první prvek v unreverse).

### <a name="remarks"></a>Poznámky

`crend`se používá s obráceným hash_multimap stejně jako [hash_multimap:end](#end) se používá s hash_multimap.

S vrácenou `crend`hodnotou `hash_multimap` aplikace nelze objekt změnit.

`crend`lze použít k testování, zda reverzní iterátor dosáhl konce svého hash_multimap.

Hodnota vrácená `crend` by neměla být odkazována.

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

## <a name="hash_multimapdifference_type"></a><a name="difference_type"></a>hash_multimap::difference_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Podepsaný typ celé číslo, který lze použít k reprezentaci počtu prvků hash_multimap v rozsahu mezi prvky, na které se iterátory upozorují.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Je `difference_type` typ vrácena při odečtení nebo zvýšení prostřednictvím iterátory kontejneru. Obvykle `difference_type` se používá k reprezentaci počtu prvků v rozsahu *[ první, poslední)* mezi iterátory `first` a `last`, zahrnuje prvek, na který `first` se vztahuje, a rozsah prvků až do prvku, na který je však `last`nezahrnuto.

Všimněte `difference_type` si, že i když je k dispozici pro všechny iterátory, které splňují požadavky vstupní iterátor, který zahrnuje třídu obousměrné iterátory podporované reverzibilní kontejnery, jako je například set, odčítání mezi iterátory je podporován pouze náhodný přístup iterátory poskytované kontejneru s náhodným přístupem, jako je vektor.

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

## <a name="hash_multimapemplace"></a><a name="emplace"></a>hash_multimap::emplace

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vloží prvek vytvořený na místě do hash_multimap.

```cpp
template <class ValTy>
iterator emplace(ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota použitá k přesunutí konstrukce prvku, který má být vložen do [hash_multimap](../standard-library/hash-multimap-class.md).|

### <a name="return-value"></a>Návratová hodnota

Členská `emplace` funkce vrátí iterátor, který odkazuje na pozici, kde byl vložen nový prvek.

### <a name="remarks"></a>Poznámky

[hash_multimap::value_type](#value_type) prvku je pár, takže hodnota prvku bude uspořádaný pár s první komponentou rovnající se hodnotě klíče a druhou komponentou rovnající se hodnotě dat prvku.

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

## <a name="hash_multimapemplace_hint"></a><a name="emplace_hint"></a>hash_multimap::emplace_hint

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vloží prvek vytvořený na místě do hash_multimap s nápovědou k umístění.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota slouží k přesunutí konstrukce prvek, který [hash_multimap](../standard-library/hash-multimap-class.md) má `hash_multimap` být vložen do hash_multimap pokud již obsahuje tento prvek (nebo obecněji prvek, jehož klíč je ekvivalentní objednané).|
|*_Where*|Nápověda týkající se místa, kde chcete začít hledat správný bod vložení.|

### <a name="return-value"></a>Návratová hodnota

Členská funkce [hash_multimap::emplace](#emplace) vrátí iterátor, který odkazuje na pozici, kde `hash_multimap`byl vložen nový prvek do .

### <a name="remarks"></a>Poznámky

[hash_multimap::value_type](#value_type) prvku je pár, takže hodnota prvku bude uspořádaný pár s první komponentou rovnající se hodnotě klíče a druhou komponentou rovnající se hodnotě dat prvku.

Vložení může dojít v amortizované konstantní čas, namísto logaritmického času, pokud kurzor bezprostředně následuje *_Where*.

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

## <a name="hash_multimapempty"></a><a name="empty"></a>hash_multimap::prázdný

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Testuje, zda je hash_multimap prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je hash_multimap prázdný; **false,** pokud hash_multimap není prázdný.

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

## <a name="hash_multimapend"></a><a name="end"></a>hash_multimap::konec

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí iterátor, který řeší umístění, které následuje poslední prvek v hash_multimap.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který řeší umístění, které následuje poslední prvek v hash_multimap. Pokud je hash_multimap prázdný, pak hash_multimap::end == hash_multimap::begin.

### <a name="remarks"></a>Poznámky

`end`se používá k testování, zda iterátor dosáhl konce svého hash_multimap.

Hodnota vrácená `end` by neměla být odkazována.

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

## <a name="hash_multimapequal_range"></a><a name="equal_range"></a>hash_multimap::equal_range

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí dvojici iterátorů respektive první prvek v hash_multimap s klíčem, který je větší než zadaný klíč a první prvek v hash_multimap s klíčem, který je roven nebo větší než klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z hash_multimap prohledáván.

### <a name="return-value"></a>Návratová hodnota

Dvojice iterátorů tak, že první je [lower_bound](#lower_bound) klíče a druhý je [upper_bound](#upper_bound) klíče.

Chcete-li získat přístup k prvnímu iterátoru `pr` `pr`dvojice vrácené členovou funkcí, použijte . **nejprve** a dereference dolní mez iterátoru, použití \*( `pr`. **první**). Chcete-li získat přístup k druhému iterátoru `pr` `pr`dvojice vrácené členovou funkcí, použijte . **a** pro dereferenci horní mez iterátoru, použití \*( `pr`. **za druhé**).

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

## <a name="hash_multimaperase"></a><a name="erase"></a>hash_multimap::vymazat

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Odebere prvek nebo rozsah prvků v hash_multimap ze zadaných pozic nebo odebere prvky, které odpovídají zadanému klíči.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where*\
Umístění prvku, který má být odebrán z hash_multimap.

*První*\
Pozice prvního prvku odstraněného z hash_multimap.

*Poslední*\
Umístěte těsně za poslední prvek odstraněný z hash_multimap.

*Klíč*\
Klíč prvků, které mají být odstraněny z hash_multimap.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který označuje první prvek zbývající za všechny prvky odebrány nebo ukazatel na konec hash_multimap pokud žádný takový prvek neexistuje.

Pro třetí členskou funkci vrátí počet prvků, které byly odebrány z hash_multimap.

### <a name="remarks"></a>Poznámky

Členské funkce nikdy vyvolat výjimku.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_multimap::erase členské funkce.

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

## <a name="hash_multimapfind"></a><a name="find"></a>hash_multimap::najít

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí iterátor adresování první umístění prvku v hash_multimap, který má klíč ekvivalentní zadaný klíč.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč, který má být porovnán s klíčem řazení prvku z hash_multimap prohledáván.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který řeší první umístění prvku se zadaným klíčem nebo umístění, které následuje poslední prvek v hash_multimap pokud pro klíč není nalezena žádná shoda.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který řeší prvek v hash_multimap `equivalent` jehož klíč řazení je klíč argumentu pod binární predikát, který indukuje řazení na základě méně než vztah srovnatelnosti.

Pokud `find` je vrácená hodnota `const_iterator`přiřazena aplikaci , nelze objekt hash_multimap změnit. Pokud `find` je vrácená hodnota `iterator`přiřazena aplikaci , lze změnit hash_multimap objekt.

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

## <a name="hash_multimapget_allocator"></a><a name="get_allocator"></a>hash_multimap::get_allocator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí kopii objektu alokátoru použitého ke vytvoření hash_multimap.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný hash_multimap.

### <a name="remarks"></a>Poznámky

Alokátory pro třídu hash_multimap určují, jak třída spravuje úložiště. Výchozí alokátory dodávané s třídami kontejneru standardní knihovny jazyka C++ jsou dostatečné pro většinu potřeb programování. Psaní a používání vlastní třídy přidělování je pokročilé téma jazyka C++.

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

## <a name="hash_multimaphash_multimap"></a><a name="hash_multimap"></a>hash_multimap::hash_multimap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vytvoří hash_multimap, která je prázdná nebo je kopií celého jiného hash_multimap nebo jeho části.

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
|*Al*|Třída alokátoru úložiště, která má být použita `Allocator`pro tento hash_multimap objekt, který je ve výchozím nastavení .|
|*Comp*|Funkce porovnání typu `const Traits` použitého k seřizování prvků `Traits`v mapě, která je ve výchozím nastavení .|
|*Právo*|Objekt map, ze kterého je kopií vytvořen objekt set.|
|*První*|Umístění prvního prvku v rozsahu prvků, které mají být zkopírovány.|
|*Poslední*|Pozice první prvek mimo rozsah prvků, které mají být zkopírovány.|
|*Ilist*|Initializer_list kopírovat.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory uložit typ objektu alokátoru, který spravuje úložiště paměti pro hash_multimap a které mohou být později vráceny voláním [get_allocator](#get_allocator). Alokátor parametr je často vynechán v deklaraci třídy a preprocessing makra se používají k nahrazení alternativní přidělování.

Všechny konstruktory inicializují své hash_multimap.

Všechny konstruktory uložit objekt `Traits` funkce typu, který se používá k vytvoření pořadí mezi klíči hash_multimap a může být později vrácena voláním [key_comp](#key_comp).

První tři konstruktory určují prázdnou počáteční hash_multimap; druhý určuje typ funkce porovnání (*Comp),* která má být použita při stanovení pořadí prvků, a třetí`_Al`výslovně specifikuje typ alokátoru ( ) který má být použit. Klíčové `explicit` slovo potlačí určité druhy automatického převodu typu.

Čtvrtý konstruktor určuje kopii hash_multimap `Right`.

Další tři konstruktory zkopírují rozsah `First, Last)` mapy s rostoucí explicitní při určování typu `Traits` funkce porovnání třídy a alokátoru.

Osmý konstruktor přesune `Right`hash_multimap .

Poslední tři konstruktory používají initializer_list.

## <a name="hash_multimapinsert"></a><a name="insert"></a>hash_multimap::vložit

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

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
|*Val*|Hodnota prvku, který má být vložen do hash_multimap, pokud již obsahuje tento prvek, nebo obecněji, pokud již obsahuje prvek, jehož klíč je ekvivalentní objednané.|
|*Kde*|Nápověda o tom, kde začít hledat správný bod vložení.|
|*První*|Pozice prvního prvku, který má být zkopírován z mapy.|
|*Poslední*|Pozice těsně za poslední prvek, který má být zkopírován z mapy.|

### <a name="return-value"></a>Návratová hodnota

První dvě `insert` členské funkce vrátí iterátor, který odkazuje na pozici, kde byl vložen nový prvek.

Třetí členská funkce používá initializer_list pro prvky, které mají být vloženy.

Čtvrtá členská funkce vloží posloupnost hodnot elementu do mapy, která odpovídá každému prvku `[First, Last)` adresovanému iterátorem v rozsahu zadané sady.

Poslední dvě `insert` členské funkce se chovají stejně jako první dvě, s tím rozdílem, že se move-construct vložené hodnoty.

### <a name="remarks"></a>Poznámky

Value_type [value_type](#value_type) prvku je pár, takže hodnota prvku bude uspořádaný pár, ve kterém první komponenta se rovná hodnotě klíče a druhá komponenta se rovná hodnotě dat prvku.

Vložení může dojít v amortizované konstantní čas `insert`pro verzi nápovědy , namísto logaritmického času, pokud kurzor bezprostředně následuje *Kde*.

## <a name="hash_multimapiterator"></a><a name="iterator"></a>hash_multimap::iterátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Poznámky

Definované `iterator` hash_multimap odkazuje na objekty [value_type](#value_type), `pair` \< které jsou typu **const Key, Type**>, jehož první člen je klíčem k prvku a jehož druhý člen je mapované základny držené elementem.

Chcete-li odkazovat **na iterátor** `Iter` směřující na prvek `->` v hash_multimap, použijte operátor.

Chcete-li získat přístup k hodnotě `Iter`  -> klíče pro prvek, použijte **nejprve**, což je ekvivalentní (\* `Iter`). **nejprve**. Chcete-li získat přístup k hodnotě mapované základny pro prvek, použijte `Iter`  ->  **second**, což je ekvivalentní (\* `Iter`). **nejprve**.

Typ `iterator` lze změnit hodnotu prvku.

### <a name="example"></a>Příklad

Příklad [začátku](#begin) naleznete v příkladu, jak `iterator`deklarovat a používat .

## <a name="hash_multimapkey_comp"></a><a name="key_comp"></a>hash_multimap::key_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Načte kopii objektu porovnání použitého k objednání klíčů v hash_multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který hash_multimap používá k objednání jeho prvků.

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členovou funkci

**bool operátor (const Key&** `left` **, const Key&** `right` **);**

který vrátí `left` **hodnotu true,** pokud `right` předchází, a není rovna v pořadí řazení.

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

## <a name="hash_multimapkey_compare"></a><a name="key_compare"></a>hash_multimap::key_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení k určení relativní pořadí dvou prvků v hash_multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare`je synonymem pro parametr znakové *vlastnosti*šablony .

Další informace o *vlastnostech* naleznete v tématu [hash_multimap třída.](../standard-library/hash-multimap-class.md)

### <a name="example"></a>Příklad

Příklad pro [key_comp](#key_comp) příklad, jak deklarovat a používat `key_compare`.

## <a name="hash_multimapkey_type"></a><a name="key_type"></a>hash_multimap::key_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, který popisuje objekt klíče řazení, který představuje každý prvek hash_multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type`je synonymem pro parametr šablony *Klíč*.

Další informace o *klíči*naleznete v části Poznámky v tématu [hash_multimap třída.](../standard-library/hash-multimap-class.md)

### <a name="example"></a>Příklad

Příklad [value_type](#value_type) naleznete v příkladu, jak `key_compare`deklarovat a používat .

## <a name="hash_multimaplower_bound"></a><a name="lower_bound"></a>hash_multimap::lower_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí iterátor prvnímu prvku v hash_multimap s klíčem, který je roven nebo větší než zadaný klíč.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z hash_multimap prohledáván.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator,](#const_iterator) který řeší umístění prvku v hash_multimap s klíčem, který je roven nebo větší než klíč argumentu nebo který řeší umístění, které následuje poslední prvek v hash_multimap pokud pro klíč není nalezena žádná shoda.

Pokud `lower_bound` je vrácená hodnota `const_iterator`přiřazena aplikaci , nelze objekt hash_multimap změnit. Pokud `lower_bound` je vrácená hodnota `iterator`přiřazena aplikaci , lze změnit hash_multimap objekt.

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

## <a name="hash_multimapmapped_type"></a><a name="mapped_type"></a>hash_multimap::mapped_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, který představuje datový typ uložený v hash_multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Poznámky

`mapped_type`je synonymem pro parametr šablony *Type*.

Další informace o *tématu Typ* naleznete v tématu [hash_multimap třída.](../standard-library/hash-multimap-class.md)

### <a name="example"></a>Příklad

Příklad [value_type](#value_type) naleznete v příkladu, jak `key_type`deklarovat a používat .

## <a name="hash_multimapmax_size"></a><a name="max_size"></a>hash_multimap::max_size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

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

## <a name="hash_multimapoperator"></a><a name="op_eq"></a>hash_multimap::operátor=

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Nahradí prvky hash_multimap kopií jiného hash_multimap.

```cpp
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Právo*|Hash_multimap [hash_multimap](../standard-library/hash-multimap-class.md) zkopírován `hash_multimap`do .|

### <a name="remarks"></a>Poznámky

Po vymazání všech existujících `hash_multimap` `operator=` prvků v aplikaci zkopíruje `hash_multimap`nebo přesune obsah *vpravo* do .

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

## <a name="hash_multimappointer"></a><a name="pointer"></a>hash_multimap::pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje ukazatel na prvek v hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze změnit hodnotu prvku.

Ve většině případů [iterátor](#iterator) by měl být použit pro přístup k prvkům v hash_multimap objektu.

## <a name="hash_multimaprbegin"></a><a name="rbegin"></a>hash_multimap::začátek

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí iterátor adresující první prvek v obráceném hash_multimap.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresování první prvek v obrácené hash_multimap nebo adresování, co bylo poslední prvek v unreverse hash_multimap.

### <a name="remarks"></a>Poznámky

`rbegin`se používá s obráceným hash_multimap stejně jako [začátek](#begin) se používá s hash_multimap.

Pokud `rbegin` je vrácená hodnota `const_reverse_iterator`přiřazena aplikaci , nelze objekt hash_multimap změnit. Pokud `rbegin` je vrácená hodnota `reverse_iterator`přiřazena k , pak hash_multimap objekt upravil.

`rbegin`lze použít k iterátu přes hash_multimap dozadu.

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

## <a name="hash_multimapreference"></a><a name="reference"></a>hash_multimap::odkaz

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

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

## <a name="hash_multimaprend"></a><a name="rend"></a>hash_multimap::rend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí iterátor, který řeší umístění, které následuje poslední prvek v obráceném hash_multimap.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor, který řeší umístění, které následuje poslední prvek v obráceném hash_multimap (umístění, které předcházelo prvnímu prvku v neobrácené hash_multimap).

### <a name="remarks"></a>Poznámky

`rend`se používá s obráceným hash_multimap [stejně](#end) jako konec se používá s hash_multimap.

Pokud `rend` je vrácená hodnota přiřazena [const_reverse_iterator](#const_reverse_iterator), nelze objekt hash_multimap změnit. Pokud `rend` je vrácená hodnota přiřazena [reverse_iterator](#reverse_iterator), lze změnit objekt hash_multimap.

`rend`lze použít k testování, zda reverzní iterátor dosáhl konce svého hash_multimap.

Hodnota vrácená `rend` by neměla být odkazována.

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

## <a name="hash_multimapreverse_iterator"></a><a name="reverse_iterator"></a>hash_multimap::reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iterátu přes hash_multimap v opačném směru.

Definované `reverse_iterator` hash_multimap odkazuje na objekty [value_type](#value_type), `pair` \< které jsou typu **const Key, Type**>. Hodnota klíče je k dispozici prostřednictvím první dvojice členů a hodnota mapovaného prvku je k dispozici prostřednictvím druhého člena dvojice.

### <a name="example"></a>Příklad

Příklad pro [rbegin](#rbegin) naleznete v příkladu, `reverse_iterator`jak deklarovat a používat .

## <a name="hash_multimapsize"></a><a name="size"></a>hash_multimap::velikost

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí počet prvků v hash_multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka hash_multimap.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_multimap::size členské funkce.

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

## <a name="hash_multimapsize_type"></a><a name="size_type"></a>hash_multimap::size_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Nepodepsaný čtyřčíselný typ, který počítá počet prvků v hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Příklad [velikosti](#size) naleznete v příkladu, jak deklarovat a používat`size_type`

## <a name="hash_multimapswap"></a><a name="swap"></a>hash_multimap::swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vyměňuje prvky dvou hash_multimaps.

```cpp
void swap(hash_multimap& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
hash_multimap, že prvky, které mají být vyměněny, nebo hash_multimap jejichž prvky mají být vyměněny za prvky hash_multimap.

### <a name="remarks"></a>Poznámky

Členská funkce zruší platnost žádné odkazy, ukazatele nebo iterátory, které označují prvky ve dvou hash_multimaps jejichž prvky jsou vyměňovány.

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

## <a name="hash_multimapupper_bound"></a><a name="upper_bound"></a>hash_multimap::upper_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Vrátí iterátor prvnímu prvku v hash_multimap s klíčem, který je větší než zadaný klíč.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z hash_multimap prohledáván.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator,](#const_iterator) který řeší umístění prvku v hash_multimap s klíčem, který je větší než klíč argumentu, nebo který řeší umístění, které následuje poslední prvek v hash_multimap pokud pro klíč není nalezena žádná shoda.

Pokud `upper_bound` je vrácená hodnota `const_iterator`přiřazena aplikaci , nelze objekt hash_multimap změnit. Pokud `upper_bound` je vrácená hodnota `iterator`přiřazena , lze změnit objekt hash_multimap.

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

## <a name="hash_multimapvalue_comp"></a><a name="value_comp"></a>hash_multimap::value_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Členská funkce vrátí objekt funkce, který určuje pořadí prvků v hash_multimap porovnáním jejich klíčových hodnot.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce porovnání, který hash_multimap používá k objednání jeho prvků.

### <a name="remarks"></a>Poznámky

Pro hash_multimap *m*, jestliže dva prvky *e1* (*k1*, *d1*) a *e2*(*k2*, *d2*) jsou objekty typu [value_type](#value_type), `m.value_comp()(e1, e2)` kde *k1* a *k2* jsou jejich klíče typu [key_type](#key_type) a *d1* a *d2* jsou jejich údaje typu [mapped_type](#mapped_type), pak jsou ekvivalentní . `m.key_comp()(k1, k2)` Uložený objekt definuje členovou funkci

`bool operator( value_type& left, value_type& right);`

který vrátí **hodnotu true,** pokud hodnota klíče `left` předchází `right` a není rovna hodnotě klíče v pořadí řazení.

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

## <a name="hash_multimapvalue_type"></a><a name="value_type"></a>hash_multimap::value_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](../standard-library/unordered-multimap-class.md).

Typ, který představuje typ objektu uloženého v hash_multimap.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Poznámky

`value_type`je prohlášena\<za pár const [key_type](#key_type)\<, [mapped_type](#mapped_type)> a nikoli key_type, mapped_type>, protože klíče asociativního kontejneru nelze měnit pomocí nestálého iterátoru nebo odkazu.

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

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
