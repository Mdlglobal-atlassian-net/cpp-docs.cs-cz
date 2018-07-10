---
title: hash_multimap – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c3b9e3ba7a7929158adacfab889007cb518c54b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849064"
---
# <a name="hashmultimap-class"></a>hash_multimap – třída

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Hash_multimap – třída kontejneru je rozšířením standardní knihovna C++ a slouží k ukládání a rychlé načítání dat z kolekce, ve kterém je každý prvek pár, který má klíč řazení, jehož hodnota nemusí být jedinečný a hodnotu přidružená data.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare <Key, less <Key>>,
    class Allocator=allocator <pair  <const Key, Type>>>
class hash_multimap
```

### <a name="parameters"></a>Parametry

`Key` Typ klíče dat k uložení do hash_multimap.

`Type` Datový typ elementu k uložení do hash_multimap.

`Traits` Typ, který obsahuje dva objekty funkce, jeden třídy `Traits` , je možné k porovnání dvou hodnot element jako klíči řazení určit jejich relativní pořadí a hodnoty hash funkci, která je unární operátor hodnoty klíče predikátem mapování elementů na nepodepsané celá čísla z typ **size_t –**. Tento argument je volitelný a `hash_compare<Key, less<Key>>` je výchozí hodnota.

`Allocator` Typ, který představuje uložené allocator objekt, který zapouzdřuje informace o přidělení a zrušení přidělení paměti hash_multimap. Tento argument je volitelný a výchozí hodnota je `allocator<pair <const Key, Type>>`.

## <a name="remarks"></a>Poznámky

Hash_multimap je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Algoritmus hash, protože jeho prvky jsou seskupeny do sad na základě hodnoty hash funkci použité pro hodnoty klíče elementů.

- Vícenásobný, protože je prvky nemusí mít jedinečné klíče, takže jedna hodnota klíče může mít k sobě přidružených mnoho datových hodnot prvků.

- Pár asociativní kontejner, protože její hodnota elementu se liší od jeho klíčové hodnoty.

- Třída šablony, protože poskytuje obecné funkce a to nezávisle na určitém typu dat obsažených jako prvky nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Hlavní výhodou použití algoritmu hash přes řazení je vyšší efektivity; úspěšné algoritmu hash provádí vkládání, odstraňování a vyhledá v porovnání s čas konstantní Průměrná doba úměrná logaritmus počet elementů v kontejneru pro řazení techniky. Hodnota elementu v hash_multimap, ale není přidružené hodnoty klíče, může se změnit přímo. Namísto toho hodnoty klíčů přidružené ke starým prvkům musí být odstraněny a vloženy nové hodnoty klíče související s novými prvky.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Hash asociativní kontejnery jsou optimalizované pro operace vyhledávání, vkládání a odebrání. Členské funkce, které explicitně podporují tyto operace jsou efektivní, pokud se používá s dobře navrženou hash funkce, provádět v čase, který je v průměru konstant a není závislá na počet elementů v kontejneru. Funkce dobře navrženou hash vytváří rovnoměrné rozdělení hodnot hash a minimalizuje počet kolizí, kde kolize říká, že je dojít, když odlišné hodnoty klíče jsou namapované na stejnou hodnotu hash. V nejhorším případě s funkci nejhorší možné hash počet operací je úměrná počet elementů v pořadí (lineární čas).

Hash_multimap by měl být kontejneru asociativní výběru aplikací jsou splněny podmínky přidružení hodnoty k jejich klíče. Model pro tento typ struktury je uspořádaný seznam klíčových slov s přidruženými řetězcovými hodnotami poskytujícími (řekněme) definice, kde slova nebyla vždy jednoznačně definována. Pokud místo toho klíčová slova byly definovány jedinečně, tak, aby klíče byly jedinečné, hash_map by kontejneru výběru. Pokud na druhé straně byly ukládaného právě seznam slova, hash_set by správné kontejneru. Pokud bylo povoleno více výskytů slova, hash_multiset by strukturu odpovídajícího kontejneru.

Hash_multimap řadí pořadí jimi řídí voláním uložené hodnoty hash `Traits` objektu typu [value_compare –](../standard-library/value-compare-class.md). Tento objekt uložené přístupná voláním členské funkce [key_comp –](../standard-library/hash-map-class.md#key_comp). Funkce objektu musí chovají stejně jako objekt třídy [hash_compare](../standard-library/hash-compare-class.md)`<Key, less<Key>>`. Konkrétně pro všechny hodnoty `Key` typu `Key`, volání `Traits (Key)` vypočítá distribuci hodnot typu `size_t`.

Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To vede řazení mezi elementy, která není ekvivalentní. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát f (x, y) je objekt funkce, která má dva objekty argument `x` a `y` a návratová hodnota `true` nebo `false`. Řazení vynucená pro hash_multimap je striktní weak řazení Pokud binární predikát je Nereflexivní, antisymetrického a přenositelné a pokud ekvivalenční přenositelné, kde dva objekty `x` a `y` jsou definovány jako ekvivalentní při obou f (x y) a f (y, x) jsou `false`. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

Skutečné pořadí prvků v řízené sekvenci závisí na funkci hash, funkci řazení a aktuální velikost tabulku hash uložené v objektu kontejneru. Aktuální velikost zatřiďovací tabulku nelze určit, takže nemůžete obecně předpovědět pořadí prvků v řízené sekvenci. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Iterator poskytované hash_multimap – třída je obousměrný iterator, ale členské funkce tříd [vložit](#insert) a [hash_multimap](#hash_multimap) mají verze, které jako parametry šablony trvat slabší vstup iterator, jejichž požadavky na funkce jsou minimální více než ty, které zaručit třídou iterátory obousměrné. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterator má svou vlastní hash_multimap požadavky a algoritmy, které pracují s nimi musí omezit jejich předpoklady pro splnění požadavků poskytované daný typ iterator. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální hash_multimap funkcí, ale stačí mohli srozumitelně mluvit o rozsah iterátory `[First, Last)` v kontextu členské funkce.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[hash_multimap](#hash_multimap)|Vytvoří seznam určité velikosti nebo elementy konkrétní hodnotu nebo s konkrétní `allocator` nebo jako kopii některé jiné `hash_multimap`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type –](#allocator_type)|Typ, který reprezentuje `allocator` třídy pro `hash_multimap` objektu.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrné iterator, který může číst `const` element v `hash_multimap`.|
|[const_pointer](#const_pointer)|Typ, který poskytuje odkazy `const` element v `hash_multimap`.|
|[const_reference](#const_reference)|Typ, který obsahuje odkaz na `const` element uložené v `hash_multimap` pro čtení a provádění `const` operace.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrné iterator, který může číst všechny `const` element v `hash_multimap`.|
|[difference_type](#difference_type)|Typ se znaménkem, který můžete použít k reprezentování počet prvků `hash_multimap` v rozsahu mezi elementy, na kterou iterátory odkazuje.|
|[Iterator](#iterator)|Typ, který poskytuje obousměrné iterator, který může číst nebo upravovat libovolný element v `hash_multimap`.|
|[key_compare](#key_compare)|Typ, který poskytuje funkce objekt, který můžete porovnat dva klíče řazení k určení relativních pořadí dva elementy v `hash_multimap`.|
|[key_type](#key_type)|Typ, který popisuje řazení klíče objektu, která se považuje za každý element `hash_multimap`.|
|[mapped_type](#mapped_type)|Typ, který představuje typ data uložená v `hash_multimap`.|
|[Ukazatele](#pointer)|Typ, který poskytuje ukazatel na prvek v `hash_multimap`.|
|[Referenční dokumentace](#reference)|Typ, který obsahuje odkaz na element uložené v `hash_multimap`.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrné iterator, které můžou číst nebo upravte element v odstínech `hash_multimap`.|
|[size_type](#size_type)|Typ celé číslo bez znaménka, která představuje počet elementů ve `hash_multimap`.|
|[value_type](#value_type)|Typ, který poskytuje funkce objekt, který můžete porovnat dva elementy jako klíči řazení určit jejich relativní pořadí v `hash_multimap`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Začátek](#begin)|Vrátí iterovat adresování prvním elementem v `hash_multimap`.|
|[cbegin –](#cbegin)|Vrátí const iterator adresování prvním elementem v `hash_multimap`.|
|[cend –](#cend)|Vrátí const iterator, která řeší úspěšné posledním prvkem v umístění `hash_multimap`.|
|[Zrušte zaškrtnutí](#clear)|Vymaže všechny elementy `hash_multimap`.|
|[Počet](#count)|Vrátí počet prvků v `hash_multimap` jejichž klíč odpovídá parametru zadaný klíč.|
|[crbegin](#crbegin)|Vrátí const iterator adresování prvním elementem v odstínech `hash_multimap`.|
|[crend –](#crend)|Vrátí const iterator, která řeší umístění úspěšné posledním prvkem v odstínech `hash_multimap`.|
|[emplace –](#emplace)|Vloží element v místě do zkonstruovat `hash_multimap`.|
|[emplace_hint –](#emplace_hint)|Vloží element v místě do zkonstruovat `hash_multimap`, s pomocným parametrem umístění.|
|[prázdný](#empty)|Pokud testy `hash_multimap` je prázdný.|
|[End](#end)|Vrátí iterátor, který řeší úspěšné posledním prvkem v umístění `hash_multimap`.|
|[equal_range](#equal_range)|Vrátí iterátor, který řeší úspěšné posledním prvkem v umístění `hash_multimap`.|
|[vymazání](#erase)|Odebere element nebo rozsah elementů v `hash_multimap` ze zadaných pozic|
|[Najít](#find)|Vrátí iterovat adresování umístění elementu v `hash_multimap` který má klíč ekvivalentní k zadanému klíči.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objekt použitý k vytvoření `hash_multimap`.|
|[Vložení](#insert)|Vloží elementu nebo rozsahu prvků do `hash_multimap` na zadané pozici.|
|[key_comp](#key_comp)|Načte kopii porovnání objekt použitý k pořadí klíčů v `hash_multimap`.|
|[lower_bound –](#lower_bound)|Vrátí iterovat prvním elementem v `hash_multimap` , s klíčem hodnotu, na kterou je rovna nebo větší než je zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délka `hash_multimap`.|
|[rbegin –](#rbegin)|Vrátí iterovat adresování prvním elementem v odstínech `hash_multimap`.|
|[rend –](#rend)|Vrátí iterátor, který řeší umístění úspěšné posledním prvkem v odstínech `hash_multimap`.|
|[Velikost](#size)|Určuje novou velikost `hash_multimap`.|
|[Swap](#swap)|Výměny dva elementy `hash_multimap`s.|
|[upper_bound –](#upper_bound)|Vrátí iterovat prvním elementem v `hash_multimap` , s klíčem hodnotu, je větší než je zadaný klíč.|
|[value_comp](#value_comp)|Načte kopii porovnání objekt použitý k hodnoty element pořadí v `hash_multimap`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[hash_multimap::operator=](#op_eq)|Nahradí elementy `hash_multimap` kopii jiného `hash_multimap`.|

## <a name="requirements"></a>Požadavky

**Header:** \<hash_map>

**Namespace:** stdext –

## <a name="allocator_type"></a>  hash_multimap::allocator_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který reprezentuje allocator – třída objektu hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type` je synonymum pro parametr šablony `Allocator`.

Další informace o `Allocator`, najdete v části poznámky [hash_multimap – třída](../standard-library/hash-multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_allocator –](#get_allocator) pro příklad použití `allocator_type`.

## <a name="begin"></a>  hash_multimap::begin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí iterator adresování prvním elementem v hash_multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Adresování prvním elementem v hash_multimap nebo umístění úspěšné prázdný hash_multimap iterator obousměrné.

### <a name="remarks"></a>Poznámky

Pokud vrátí hodnotu, která **začít** je přiřazena k `const_iterator`, elementy v objektu hash_multimap nemůže být upraven. Pokud vrátí hodnotu, která **začít** je přiřazena k **iterator**, elementy v objektu hash_multimap je možné upravit.

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

Vrátí const iterator adresování prvním elementem v hash_multimap.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const iterator obousměrného adresování prvním elementem v [hash_multimap](../standard-library/hash-multimap-class.md) nebo umístění úspěšné prázdnou `hash_multimap`.

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

Vrátí const iterator, která řeší úspěšné posledním prvkem v hash_multimap umístění.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const iterator obousměrného, která řeší úspěšné posledním prvkem v umístění [hash_multimap](../standard-library/hash-multimap-class.md). Pokud `hash_multimap` je prázdný, pak `hash_multimap::cend == hash_multimap::begin`.

### <a name="remarks"></a>Poznámky

`cend` slouží k ověření, zda iterovat dosáhne konce své hash_multimap.

Hodnoty vrácené `cend` by neměl být vyhodnoceny odkazy.

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

Vymaže všechny elementy hash_multimap.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_multimap::clear – členská funkce.

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

Typ, který poskytuje obousměrné iterator, který může číst **const** element v hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít k úpravě hodnota elementu.

`const_iterator` Definované body hash_multimap objektů [value_type](#value_type), které jsou typu `pair` *\< ***constKey, typ*** >*. Hodnota klíče je k dispozici prostřednictvím první člen pár a hodnota namapované elementu je k dispozici prostřednictvím druhý člen, které odpovídá páru.

K dereference `const_iterator` `cIter` odkazující na prvek v hash_multimap, použijte **->** operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `cIter`  ->  **první**, což je totéž jako (\* `cIter`). **první**. Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `cIter`  ->  **druhý**, což je totéž jako (\* `cIter`). **první**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin) pro příklad použití `const_iterator`.

## <a name="const_pointer"></a>  hash_multimap::const_pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje odkazy **const** element v hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít k úpravě hodnota elementu.

Ve většině případů [iterator](#iterator) se má použít pro přístup k elementům v hash_multimap objektu.

## <a name="const_reference"></a>  hash_multimap::const_reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který obsahuje odkaz na **const** element uložené v hash_multimap pro čtení a provádění **const** operace.

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

Typ, který poskytuje obousměrné iterator, který může číst všechny **const** element v hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nelze změnit hodnotu elementu a je použít k iteraci v rámci hash_multimap pozpátku.

`const_reverse_iterator` Definované body hash_multimap objektů [value_type](#value_type), které jsou typu `pair` * \< * **const klíč, zadejte >**, jejichž první člen je klíčem k elementu a jehož druhý člen trvá namapované datum elementem.

K dereference `const_reverse_iterator` `crIter` odkazující na prvek v hash_multimap, použijte **->** operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `crIter`  ->  **první**, což je totéž jako (\* `crIter`). **první**. Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `crIter`  ->  **druhý**, což je totéž jako (\* `crIter`). **první**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rend](#rend) příklad toho, jak deklarace a používání `const_reverse_iterator`.

## <a name="count"></a>  hash_multimap::Count

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí počet prvků v hash_multimap, jehož klíč odpovídá parametru zadaný klíč.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Klíč elementy lze porovnat z hash_multimap.

### <a name="return-value"></a>Návratová hodnota

1, pokud hash_multimap obsahuje element, jehož klíč řazení shoduje s klíčem parametr; 0, pokud hash_multimap neobsahuje element s odpovídající klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v rozsahu

**[lower_bound – (** `key` **), upper_bound – (** `key` **))**

které mají hodnotu klíče `key`.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_multimap::count – členská funkce.

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

Vrátí const iterator adresování prvním elementem v invertovaných hash_multimap.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse obousměrného iterator adresování prvním elementem v odstínech [hash_multimap](../standard-library/hash-multimap-class.md) nebo řešení, co je posledním prvkem v unreversed `hash_multimap`.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s odstínech hash_multimap stejně jako [hash_multimap::begin](#begin) se používá s `hash_multimap`.

S návratovou hodnotou `crbegin`, `hash_multimap` objekt nelze změnit.

`crbegin` lze použít k iteraci v rámci `hash_multimap` zpětné.

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

Vrátí const iterator, která řeší úspěšné posledním prvkem v invertovaných hash_multimap umístění.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse iterator obousměrného, která řeší umístění úspěšné posledním prvkem v odstínech [hash_multimap](../standard-library/hash-multimap-class.md) (umístění, které měl před prvním elementem v unreversed `hash_multimap`).

### <a name="remarks"></a>Poznámky

`crend` se používá s odstínech hash_multimap stejně jako [hash_multimap::end](#end) se používá s hash_multimap.

S návratovou hodnotou `crend`, `hash_multimap` objekt nelze změnit.

`crend` slouží k testování, aby se jestli zpětné iterator dosáhne konce své hash_multimap.

Hodnoty vrácené `crend` by neměl být vyhodnoceny odkazy.

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

Typ se znaménkem, který můžete použít k reprezentování počet elementů hash_multimap v rozsahu mezi elementy, na kterou iterátory odkazuje.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` Je typ vrácena, pokud odečtením nebo zvyšování prostřednictvím iterátory kontejneru. `difference_type` Se obvykle používá k reprezentování počet elementů v rozsahu *[první, poslední)* mezi iterátory `first` a `last`, obsahuje element, na kterou odkazuje `first` a rozsahu elementy až do, s výjimkou elementu na kterou odkazuje `last`.

Všimněte si, že i když `difference_type` je k dispozici pro všechny iterátory, které splňují požadavky vstupní iterator, který obsahuje třídu obousměrného iterátory nepodporuje reverzibilního kontejnery, jako je sada, odčítání mezi iterátory pouze iterátory náhodný přístup poskytuje náhodný přístup kontejner například vektoru podporována.

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

Vloží element sestavený na místě do hash_multimap.

```cpp
template <class ValTy>
iterator emplace(ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`val`|Hodnota používá k přesunu vytvořit element, který má být vložen do [hash_multimap](../standard-library/hash-multimap-class.md).|

### <a name="return-value"></a>Návratová hodnota

`emplace` – Členská funkce vrátí iterátor, který odkazuje na pozici, kde byla vložena nového elementu.

### <a name="remarks"></a>Poznámky

[Hash_multimap::value_type](#value_type) elementu je pár, aby bude použita hodnota elementu dvojici seřazené s první součást, která je rovna hodnotě klíče a druhá součást, která je rovna hodnotě dat prvku.

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

Vloží element sestavený na místě do hash_multimap, s pomocným parametrem umístění.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`val`|Hodnota používá k přesunu vytvořit element, který má být vložen do [hash_multimap](../standard-library/hash-multimap-class.md) Pokud `hash_multimap` již obsahuje tohoto elementu (nebo, obecně platí, element, jehož klíč je ekvivalentně řazení).|
|`_Where`|Nápovědu ohledně místní zahájeno hledání správné bod vložení.|

### <a name="return-value"></a>Návratová hodnota

[Hash_multimap::emplace](#emplace) – členská funkce vrátí iterátor, který odkazuje na pozici, kde byl nový element vložený do `hash_multimap`.

### <a name="remarks"></a>Poznámky

[Hash_multimap::value_type](#value_type) elementu je pár, aby bude použita hodnota elementu dvojici seřazené s první součást, která je rovna hodnotě klíče a druhá součást, která je rovna hodnotě dat prvku.

Vložení se může objevit v amortizovaný konstantní čas, místo logaritmické čas, pokud bod vložení následuje `_Where`.

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

Testy, pokud hash_multimap je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud hash_multimap je prázdná. **false** Pokud je hash_multimap neprázdný.

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

Vrátí iterátor, který řeší úspěšné posledním prvkem v hash_multimap umístění.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Iterator obousměrného, která řeší úspěšné posledním prvkem v hash_multimap umístění. Pokud hash_multimap je prázdný, hash_multimap::end == hash_multimap::begin.

### <a name="remarks"></a>Poznámky

**end** slouží k otestování, jestli iterovat dosáhne konce své hash_multimap.

Hodnoty vrácené **end** by neměl být vyhodnoceny odkazy.

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

Vrátí funkce pár iterátory prvním elementem v hash_multimap s klíčem, který je větší než je zadaný klíč a prvním elementem v hash_multimap s klíčem, který je rovna nebo větší než klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

`key` Argument klíč, který se má porovnat s klíč řazení elementu z hash_multimap prohledávaný.

### <a name="return-value"></a>Návratová hodnota

Pár iterátory tak, aby první je [lower_bound –](#lower_bound) klíč a druhý je [upper_bound –](#upper_bound) klíče.

Pro přístup k první iterator páru `pr` vrácené funkcí člen, použijte `pr`. **první** a pokud chcete dereference iterator dolní mez, použijte \*( `pr`. **nejprve**). Pro přístup k druhý iterator páru `pr` vrácené funkcí člen, použijte `pr`. **druhý** a pokud chcete dereference iterator horní mez, použijte \*( `pr`. **druhý**).

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

   cout << "The lower bound of the element with "
        << "a key of 2\n in the hash_multimap hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2\n in the hash_multimap hm1 is: "
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

## <a name="erase"></a>  hash_multimap::Erase

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Odebere element nebo rozsah elementů v hash_multimap ze zadaných pozic nebo odebere prvky, které odpovídají zadaným klíčem.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

`_Where` Pozice elementu, který má být odebrán z hash_multimap.

`first` Pozice první prvek odebrán z hash_multimap.

`last` Pozice bezprostředně za posledním elementem odebrán z hash_multimap.

`key` Klíč elementů má být odebrán z hash_multimap.

### <a name="return-value"></a>Návratová hodnota

Pro první dva členské funkce obousměrné iterator, označí první prvek zbývající nad rámec žádné elementy, odebrat nebo odkazy na konec hash_multimap, pokud neexistuje žádný takový prvek.

Pro třetí – členská funkce vrátí počet prvků, které byly odebrány z hash_multimap.

### <a name="remarks"></a>Poznámky

Členské funkce nikdy vyvolat výjimku.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_multimap::erase – členská funkce.

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
         << " the hash_multimap hm3 is:";
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
    cout  << " 2nd element is deleted, "
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

Vrátí iterovat adresování první umístění elementu v hash_multimap, s klíčem ekvivalentní k zadanému klíči.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Klíč pro klíč řazení elementu z hash_multimap prohledávaný odpovídala.

### <a name="return-value"></a>Návratová hodnota

Iterator, která řeší první umístění element se zadaným klíčem nebo umístění posledním prvkem v hash_multimap úspěšné, pokud není nalezena žádná shoda pro klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který řeší element v hash_multimap, jehož klíč řazení je **ekvivalentní** k argumentu na méně než vztah srovnání na základě klíčů v predikátu Binární indukuje řazení.

Pokud vrátí hodnotu, která **najít** je přiřazena k `const_iterator`, hash_multimap objekt nelze změnit. Pokud vrátí hodnotu, která **najít** je přiřazena k **iterator**, objekt hash_multimap je možné upravit.

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

Vrátí kopii allocator objekt použitý k vytvoření hash_multimap.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Allocator používané hash_multimap.

### <a name="remarks"></a>Poznámky

Alokátorů pro hash_multimap – Třída zadejte, jak třída spravuje úložiště. Alokátorů výchozí součástí standardní knihovna C++ – třídy kontejnerů postačí pro většinu programovacích potřeb. Psaní a pomocí vlastní allocator – třída je rozšířená C++.

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

Vytvoří hash_multimap, který je prázdný nebo je kopírování všech nebo součástí některých jiných hash_multimap.

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
|`Al`|Allocator – třída úložiště má být použit pro tento objekt hash_multimap, kde je použit výchozí `Allocator`.|
|`Comp`|Funkci porovnání typu `const Traits` sloužící k uspořádání elementy v mapě, který se standardně `Traits`.|
|`Right`|Objekt map, ze kterého je kopií vytvořen objekt set.|
|`First`|Pozice první prvek v rozsahu elementy, které se mají zkopírovat.|
|`Last`|Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.|
|`IList`|Initializer_list zkopírovat z.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládání typu allocator objektu, který spravuje úložiště paměti pro hash_multimap a který se může vracet později voláním [get_allocator –](#get_allocator). Parametr allocator je často vynechán v deklaracích třídy a používají se k nahrazení alternativní alokátorů předběžného zpracování makra.

Všechny konstruktory inicializovat jejich hash_multimap.

Všechny konstruktory uložit objekt funkce typu `Traits` který se používá k navázání pořadí mezi klíči hash_multimap a mohou být vráceny později voláním [key_comp –](#key_comp).

První tři konstruktory zadat prázdný počáteční hash_multimap; druhý určuje typ funkce porovnání ( `Comp`) pro použití při vytváření pořadí elementy a třetí explicitně určuje typ allocator ( `_Al`) má být použit. Klíčové slovo `explicit` potlačí určité druhy převod automatické typu.

Čtvrtý konstruktor určuje kopii hash_multimap `Right`.

Zkopírujte následující tři konstruktory rozsahu `First, Last)` mapy se zvýšeným explicitness v určení typu funkci porovnání třídy **vlastnosti** a přidělení.

Osmého konstruktor přesune hash_multimap `Right`.

Poslední tři konstruktory použijte initializer_list.

## <a name="insert"></a>  hash_multimap::Insert

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vloží do hash_multimap elementu nebo rozsahu prvků.

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
|`Val`|Hodnota elementu, který má být vložena do hash_multimap, pokud již obsahuje daný element nebo obecně platí, pokud ji už obsahuje element, jehož klíč je ekvivalentně řazení.|
|`Where`|Nápovědu o tom, kde spustit hledání správné bod vložení.|
|`First`|Pozice první prvek, který se má zkopírovat z mapy.|
|`Last`|Pozice bezprostředně za posledním elementem zkopírovány z mapy.|

### <a name="return-value"></a>Návratová hodnota

První dvě `insert` členské funkce vrátí iterátor, který odkazuje na pozici, kde byla vložena nového elementu.

Třetí členská funkce používá initializer_list pro elementy má být vložen.

Čtvrtý – členská funkce vloží pořadí hodnot element do mapu, která odpovídá každý prvek řešené pomocí iterace v rozsahu `[First, Last)` zadané sady.

Poslední dva `insert` členské funkce chovají stejně jako první dvě kromě toho, že jejich přesunutí – konstrukce zadaná hodnota.

### <a name="remarks"></a>Poznámky

[Value_type](#value_type) elementu je pár, tak, aby hodnota elementu bude dvojici seřazený, ve kterém se rovná hodnotě klíče první součástí a druhá součást je stejná jako hodnota dat prvku.

Vložení se může objevit v amortizovaný konstantní dobu pomocný parametr verze `insert`, místo logaritmické čas, pokud bod vložení následuje `Where`.

## <a name="iterator"></a>  hash_multimap::iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který poskytuje obousměrné iterator, který může číst nebo upravovat libovolný element v hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Poznámky

**Iterator** definované body hash_multimap objektů [value_type](#value_type), které jsou typu `pair` \< **const klíč, typ**>, jejíž první člen je klíčem k elementu a jehož sekundu člen je namapované datum uchovávat elementem.

K dereference **iterator** `Iter` odkazující na prvek v hash_multimap, použijte **->** operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `Iter`  ->  **první**, což je totéž jako (\* `Iter`). **první**. Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `Iter`  ->  **druhý**, což je totéž jako (\* `Iter`). **první**.

Typ **iterator** lze upravit hodnotu elementu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin) příklad toho, jak deklarace a používání **iterator**.

## <a name="key_comp"></a>  hash_multimap::key_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Načte kopii porovnání objekt použitý k pořadí klíčů v hash_multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce hash_multimap používá pořadí jejích elementů.

### <a name="remarks"></a>Poznámky

Definuje objekt uložené – členská funkce

**BOOL – operátor (const klíč &** `left` **, const klíč &** `right` **);**

která vrací **true** Pokud `left` předchází a není rovno `right` v pořadí řazení.

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

Typ, který poskytuje funkce objekt, který můžete porovnat dva klíče řazení pro určení pořadí, relativní ze dvou prvků v hash_multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

**key_compare –** je synonymum pro parametr šablony `Traits`.

Další informace o `Traits` najdete v článku [hash_multimap – třída](../standard-library/hash-multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [key_comp –](#key_comp) příklad toho, jak deklarace a používání `key_compare`.

## <a name="key_type"></a>  hash_multimap::key_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Typ, který popisuje řazení klíče objektu, která se považuje za každý prvek hash_multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type` je synonymum pro parametr šablony `Key`.

Další informace o `Key`, najdete v části poznámky [hash_multimap – třída](../standard-library/hash-multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_type](#value_type) příklad toho, jak deklarace a používání `key_compare`.

## <a name="lower_bound"></a>  hash_multimap::lower_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí iterovat prvním elementem v hash_multimap s klíčem, který je rovna nebo větší než je zadaný klíč.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Argument klíč, který se má porovnat s klíč řazení elementu z hash_multimap prohledávaný.

### <a name="return-value"></a>Návratová hodnota

[Iterator](#iterator) nebo [const_iterator –](#const_iterator) , který se týká umístění elementu v hash_multimap s klíčem, která je rovna nebo větší než argument klíč nebo, který se týká umístění poslední úspěšné element v hash_multimap, pokud není nalezena žádná shoda pro klíč.

Pokud vrátí hodnotu, která `lower_bound` je přiřazena k `const_iterator`, hash_multimap objekt nelze změnit. Pokud vrátí hodnotu, která `lower_bound` je přiřazena k **iterator**, je možné upravit objekt hash_multimap.

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
        << endl << " that of the last element is: "
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

Typ, který představuje typ data uložená v hash_multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Poznámky

`mapped_type` je synonymum pro parametr šablony `Type`.

Další informace o `Type` najdete v článku [hash_multimap – třída](../standard-library/hash-multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_type](#value_type) příklad toho, jak deklarace a používání `key_type`.

## <a name="max_size"></a>  hash_multimap::max_size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí maximální délka hash_multimap.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možné délku hash_multimap.

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

## <a name="op_eq"></a>  hash_multimap::Operator =

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Elementy hash_multimap nahradí kopii jiného hash_multimap.

```cpp
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`right`|[Hash_multimap](../standard-library/hash-multimap-class.md) se zkopírují `hash_multimap`.|

### <a name="remarks"></a>Poznámky

Po vymazání v žádné stávající elementy `hash_multimap`, `operator=` buď kopíruje nebo přesouvá obsah `right` do `hash_multimap`.

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

Typ **ukazatel** lze upravit hodnotu elementu.

Ve většině případů [iterator](#iterator) se má použít pro přístup k elementům v hash_multimap objektu.

## <a name="rbegin"></a>  hash_multimap::rbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Vrátí iterator adresování prvním elementem v invertovaných hash_multimap.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Iterator zpětné obousměrného adresování prvním elementem v invertovaných hash_multimap nebo řešení, co je posledním prvkem v unreversed hash_multimap.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s odstínech hash_multimap stejně jako [začít](#begin) se používá s hash_multimap.

Pokud vrátí hodnotu, která `rbegin` je přiřazena k `const_reverse_iterator`, pak hash_multimap objekt nelze změnit. Pokud vrátí hodnotu, která `rbegin` je přiřazena k `reverse_iterator`, pak je možné upravit objekt hash_multimap.

`rbegin` můžete použít k iteraci v rámci hash_multimap zpětné.

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
   cout << "After the erasure, the first element"
        << "\n in the reversed hash_multimap is "
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

Typ, který obsahuje odkaz na element uložené v hash_multimap.

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

Vrátí iterátor, který řeší úspěšné posledním prvkem v invertovaných hash_multimap umístění.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Iterator zpětné obousměrného, která řeší umístění úspěšné posledním prvkem v invertovaných hash_multimap (umístění, které měl před prvním elementem v unreversed hash_multimap).

### <a name="remarks"></a>Poznámky

`rend` se používá s odstínech hash_multimap stejně jako [end](#end) se používá s hash_multimap.

Pokud vrátí hodnotu, která `rend` je přiřazena k [const_reverse_iterator –](#const_reverse_iterator), pak hash_multimap objekt nelze změnit. Pokud vrátí hodnotu, která `rend` je přiřazena k [reverse_iterator –](#reverse_iterator), pak je možné upravit objekt hash_multimap.

`rend` slouží k testování, aby se jestli zpětné iterator dosáhne konce své hash_multimap.

Hodnoty vrácené `rend` by neměl být vyhodnoceny odkazy.

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

Typ, který poskytuje obousměrné iterator, které můžou číst nebo upravte element v invertovaných hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iteraci v rámci hash_multimap pozpátku.

`reverse_iterator` Definované body hash_multimap objektů [value_type](#value_type), které jsou typu `pair` \< **const klíč, typ**>. Hodnota klíče je k dispozici prostřednictvím první člen pár a hodnota namapované elementu je k dispozici prostřednictvím druhý člen, které odpovídá páru.

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

Následující příklad ukazuje použití hash_multimap::size – členská funkce.

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

Spočítá počet elementů v hash_multimap typ celé číslo bez znaménka.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Podívejte se na příklad pro [velikost](#size) příklad toho, jak deklarace a používání `size_type`

## <a name="swap"></a>  hash_multimap::swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](../standard-library/unordered-multimap-class.md).

Elementy dvě hash_multimaps výměny.

```cpp
void swap(hash_multimap& right);
```

### <a name="parameters"></a>Parametry

`right` Hash_multimap – poskytuje prvky, které mají být prohodily nebo hash_multimap, jehož elementy jsou k výměně s těmi hash_multimap.

### <a name="remarks"></a>Poznámky

Členská funkce by způsobila neplatnost žádné odkazy, ukazatele nebo iterátory, které určit elementů ve dvou hash_multimaps, jehož elementy jsou během výměny.

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

Vrátí iterator na prvním elementem v hash_multimap s klíčem, který je větší než je zadaný klíč.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Argument klíč, který se má porovnat s klíč řazení elementu z hash_multimap prohledávaný.

### <a name="return-value"></a>Návratová hodnota

[Iterator](#iterator) nebo [const_iterator –](#const_iterator) , který se týká umístění elementu v hash_multimap s klíčem, který je větší než argument klíč nebo který adres úspěšné posledním prvkem v umístění hash_multimap, pokud není nalezena žádná shoda pro klíč.

Pokud vrátí hodnotu, která `upper_bound` je přiřazena k `const_iterator`, hash_multimap objekt nelze změnit. Pokud vrátí hodnotu, která `upper_bound` je přiřazena k **iterator**, objekt hash_multimap je možné upravit.

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
   cout << "The first element of hash_multimap hm1\n with a key "
        << " greater than 2 is: "
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
        << endl << " that of the initial element of hm1 is: "
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

Členská funkce vrátí objekt funkce, který určuje pořadí prvků v hash_multimap tak, že porovnáte jejich hodnoty klíče.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce porovnání hash_multimap používá pořadí jejích elementů.

### <a name="remarks"></a>Poznámky

Pro hash_multimap *m*, pokud dva elementy *e*1 ( *tisíc*1 *, d*1) a *e*2 ( *tisíc*2 *, d*2) jsou objekty typu [value_type](#value_type), kde *tisíc*1 a *tisíc*2 jsou jejich klíče typu [key_type –](#key_type) a `d`1 a `d`2 jsou jejich data typu [mapped_type –](#mapped_type), pak *m.*`value_comp`() ( *e*1 *, e*2) je ekvivalentní *m.*`key_comp`() ( *tisíc*1 *, tisíc*2). Definuje objekt uložené – členská funkce

**BOOL – operátor**( **value_type &**`left`, **value_type &** `right`);

která vrací **true** Pokud klíčovou hodnotu `left` předchází a není roven hodnotě klíče `right` v pořadí řazení.

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

`value_type` je deklarován jako dvojice\<const [key_type –](#key_type), [mapped_type –](#mapped_type)> a není spárujte\<key_type –, mapped_type – > protože asociativní kontejneru klíčů se nesmí měnit. pomocí nonconstant iterator nebo odkaz.

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
   // explicitely to avoid implicit type conversion
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

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
