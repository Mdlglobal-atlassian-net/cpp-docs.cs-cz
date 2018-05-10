---
title: hash_set – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- hash_set/stdext::hash_set
- hash_set/stdext::hash_set::allocator_type
- hash_set/stdext::hash_set::const_iterator
- hash_set/stdext::hash_set::const_pointer
- hash_set/stdext::hash_set::const_reference
- hash_set/stdext::hash_set::const_reverse_iterator
- hash_set/stdext::hash_set::difference_type
- hash_set/stdext::hash_set::iterator
- hash_set/stdext::hash_set::key_compare
- hash_set/stdext::hash_set::key_type
- hash_set/stdext::hash_set::pointer
- hash_set/stdext::hash_set::reference
- hash_set/stdext::hash_set::reverse_iterator
- hash_set/stdext::hash_set::size_type
- hash_set/stdext::hash_set::value_compare
- hash_set/stdext::hash_set::value_type
- hash_set/stdext::hash_set::begin
- hash_set/stdext::hash_set::cbegin
- hash_set/stdext::hash_set::cend
- hash_set/stdext::hash_set::clear
- hash_set/stdext::hash_set::count
- hash_set/stdext::hash_set::crbegin
- hash_set/stdext::hash_set::crend
- hash_set/stdext::hash_set::emplace
- hash_set/stdext::hash_set::emplace_hint
- hash_set/stdext::hash_set::empty
- hash_set/stdext::hash_set::end
- hash_set/stdext::hash_set::equal_range
- hash_set/stdext::hash_set::erase
- hash_set/stdext::hash_set::find
- hash_set/stdext::hash_set::get_allocator
- hash_set/stdext::hash_set::insert
- hash_set/stdext::hash_set::key_comp
- hash_set/stdext::hash_set::lower_bound
- hash_set/stdext::hash_set::max_size
- hash_set/stdext::hash_set::rbegin
- hash_set/stdext::hash_set::rend
- hash_set/stdext::hash_set::size
- hash_set/stdext::hash_set::swap
- hash_set/stdext::hash_set::upper_bound
- hash_set/stdext::hash_set::value_comp
dev_langs:
- C++
helpviewer_keywords:
- stdext::hash_set
- stdext::hash_set::allocator_type
- stdext::hash_set::const_iterator
- stdext::hash_set::const_pointer
- stdext::hash_set::const_reference
- stdext::hash_set::const_reverse_iterator
- stdext::hash_set::difference_type
- stdext::hash_set::iterator
- stdext::hash_set::key_compare
- stdext::hash_set::key_type
- stdext::hash_set::pointer
- stdext::hash_set::reference
- stdext::hash_set::reverse_iterator
- stdext::hash_set::size_type
- stdext::hash_set::value_compare
- stdext::hash_set::value_type
- stdext::hash_set::begin
- stdext::hash_set::cbegin
- stdext::hash_set::cend
- stdext::hash_set::clear
- stdext::hash_set::count
- stdext::hash_set::crbegin
- stdext::hash_set::crend
- stdext::hash_set::emplace
- stdext::hash_set::emplace_hint
- stdext::hash_set::empty
- stdext::hash_set::end
- stdext::hash_set::equal_range
- stdext::hash_set::erase
- stdext::hash_set::find
- stdext::hash_set::get_allocator
- stdext::hash_set::insert
- stdext::hash_set::key_comp
- stdext::hash_set::lower_bound
- stdext::hash_set::max_size
- stdext::hash_set::rbegin
- stdext::hash_set::rend
- stdext::hash_set::size
- stdext::hash_set::swap
- stdext::hash_set::upper_bound
- stdext::hash_set::value_comp
ms.assetid: c765c06e-cbb6-48c2-93ca-d15468eb28d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e2a6dc618795872e3587c1872c4fb020872861f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="hashset-class"></a>hash_set – třída

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Hash_set – třída kontejneru je rozšířením standardní knihovna C++ a slouží k ukládání a rychlé načítání dat z kolekce, ve kterém jsou jedinečné hodnoty elementů obsažených a slouží jako hodnoty klíče.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<Key>>
class hash_set
```

### <a name="parameters"></a>Parametry

`Key` Datový typ elementu k uložení do hash_set.

`Traits` Typ, který obsahuje dva objekty funkce, jeden třídy porovnat to znamená predikátu Binární možnost k porovnání dvou hodnot element jako klíči řazení určit jejich relativní pořadí a funkce hash klíče hodnoty unárních predikátem mapování elementů na nepodepsané celá čísla typu **size_t –**. Tento argument je volitelný a `hash_compare` *< klíč,* **méně ***\<klíč >>* je výchozí hodnota.

`Allocator` Typ, který představuje uložené allocator objekt, který zapouzdřuje informace o přidělení a zrušení přidělení paměti hash_set. Tento argument je volitelný a výchozí hodnota je **allocator ***\<klíč >.*

## <a name="remarks"></a>Poznámky

Hash_set je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče. Dále je to jednoduchý asociativní kontejner, protože jeho hodnoty prvku jsou jeho hodnoty klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Algoritmus hash, protože jeho prvky jsou seskupeny do sad na základě hodnoty hash funkci použité pro hodnoty klíče elementů.

- Jedinečný v tom smyslu, že každý z jeho prvků musí mít jedinečný klíč. Protože hash_set je také jednoduché asociativní kontejner, jeho prvky jsou také jedinečný.

- Šablony třídy protože poskytuje funkce je obecný a proto nezávislé na konkrétní typ data obsažená jako elementy nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Hlavní výhodou použití algoritmu hash přes řazení je vyšší efektivity; úspěšné algoritmu hash provádí vkládání, odstraňování a vyhledá v porovnání s čas konstantní Průměrná doba úměrná logaritmus počet elementů v kontejneru pro řazení techniky. Hodnotu prvku v sadě nelze změnit přímo. Místo toho musíte odstranit staré hodnoty a vložit prvky s novými hodnotami.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Hash asociativní kontejnery jsou optimalizované pro operace vyhledávání, vkládání a odebrání. Členské funkce, které explicitně podporují tyto operace jsou efektivní, pokud se používá s dobře navrženou hash funkce, provádět v čase, který je v průměru konstant a není závislá na počet elementů v kontejneru. Funkce dobře navrženou hash vytváří rovnoměrné rozdělení hodnot hash a minimalizuje počet kolizí, kde kolize říká, že je dojít, když odlišné hodnoty klíče jsou namapované na stejnou hodnotu hash. V nejhorším případě s funkci nejhorší možné hash počet operací je úměrná počet elementů v pořadí (lineární čas).

Hash_set by měl být kontejneru asociativní výběru aplikací jsou splněny podmínky přidružení hodnoty k jejich klíče. Elementy hash_set jsou jedinečné a sloužit jako vlastní řazení klíče. Model pro tento typ struktury je uspořádaný seznam slov, v němž se slova mohou vyskytovat pouze jednou. Pokud bylo povoleno více výskytů slova, hash_multiset by strukturu odpovídajícího kontejneru. Pokud hodnoty musí být připojen k seznam jedinečných klíčová slova, hash_map bude vhodné struktury tak, aby obsahovala tato data. Pokud místo toho nejsou klíče jedinečné, hash_multimap by kontejneru výběru.

Hash_set řadí pořadí jimi řídí voláním uložené hodnoty hash **vlastnosti** objektu typu [value_compare –](#value_compare). Tento objekt uložené přístupná voláním členské funkce [key_comp –](#key_comp). Funkce objektu musí chovají stejně jako objekt třídy *hash_compare < klíče méně\<klíč >>.* Konkrétně pro všechny hodnoty `key` typu klíč, volání znak ( `key` ) vypočítá distribuci hodnot size_t – typ.

Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To vede řazení mezi elementy, která není ekvivalentní. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Predikát binární *f*( *x*, *y*) je objekt funkce, která má dva objekty argument x a y a návratovou hodnotu PRAVDA nebo NEPRAVDA. Řazení hash_set uložené je striktní weak řazení Pokud binární predikát je Nereflexivní, antisymetrického a přenositelné a pokud ekvivalenční přenositelné, kde dva objekty *x* a *y* jsou definovány Chcete-li být ekvivalentní, když oba *f*( *x*, *y*) a *f*( *y*, *x*) jsou-li hodnotu false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

Skutečné pořadí prvků v řízené sekvenci závisí na funkci hash, funkci řazení a aktuální velikost tabulku hash uložené v objektu kontejneru. Aktuální velikost zatřiďovací tabulku nelze určit, takže nemůžete obecně předpovědět pořadí prvků v řízené sekvenci. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Iterator poskytované hash_set – třída je obousměrný iterator, ale členské funkce tříd [vložit](#insert) a [hash_set](#hash_set) mají verze, které jako parametry šablony trvat slabší vstupní iterator, požadavky na jejichž funkce jsou minimální více než ty, které zaručit třídou obousměrného iterátory. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální sadu funkcí, které, ale stačí mohli srozumitelně mluvit o rozsah iterátory [ `first`, `last`) v kontextu členské funkce tříd.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[hash_set](#hash_set)|Vytvoří `hash_set` který je prázdný nebo který je kopie všech nebo některých jiných součástí `hash_set`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type –](#allocator_type)|Typ, který reprezentuje `allocator` třídy pro `hash_set` objektu.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrné iterator, který může číst `const` element v `hash_set`.|
|[const_pointer](#const_pointer)|Typ, který poskytuje odkazy `const` element v `hash_set`.|
|[const_reference](#const_reference)|Typ, který obsahuje odkaz na `const` element uložené v `hash_set` pro čtení a provádění `const` operace.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrné iterator, který může číst všechny `const` element v `hash_set`.|
|[difference_type](#difference_type)|Typ se znaménkem, který můžete použít k reprezentování počet prvků `hash_set` v rozsahu mezi elementy, na kterou iterátory odkazuje.|
|[Iterator](#iterator)|Typ, který poskytuje obousměrné iterator, který může číst nebo upravovat libovolný element v `hash_set`.|
|[key_compare](#key_compare)|Typ, který poskytuje funkce objekt, který můžete porovnat dva klíče řazení k určení relativních pořadí dva elementy v `hash_set`.|
|[key_type](#key_type)|Typ, který popisuje objekt uložené jako element `hash_set` jako klíč řazení.|
|[Ukazatele](#pointer)|Typ, který poskytuje ukazatel na prvek v `hash_set`.|
|[Referenční dokumentace](#reference)|Typ, který obsahuje odkaz na element uložené v `hash_set`.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrné iterator, které můžou číst nebo upravte element v odstínech `hash_set`.|
|[size_type](#size_type)|Typ celé číslo bez znaménka, která představuje počet elementů ve `hash_set`.|
|[value_compare](#value_compare)|Typ, který poskytuje dva objekty funkce, binární predikátu porovnání – třída, která můžete porovnat dvě hodnoty elementu `hash_set` určit jejich relativní pořadí a unární operátor predikátu, vytvoří hodnotu hash elementy.|
|[value_type](#value_type)|Typ, který popisuje objekt uložené jako element `hash_set` jako hodnotu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Začátek](#begin)|Vrátí iterátor, který řeší prvním elementem v `hash_set`.|
|[cbegin –](#cbegin)|Vrátí const iterator adresování prvním elementem v `hash_set`.|
|[cend –](#cend)|Vrátí const iterator, která řeší úspěšné posledním prvkem v umístění `hash_set`.|
|[Zrušte zaškrtnutí](#clear)|Vymaže všechny elementy `hash_set`.|
|[Počet](#count)|Vrátí počet prvků v `hash_set` jejichž klíč odpovídá parametru zadaný klíč.|
|[crbegin](#crbegin)|Vrátí const iterator adresování prvním elementem v odstínech `hash_set`.|
|[crend –](#crend)|Vrátí const iterator, která řeší umístění úspěšné posledním prvkem v odstínech `hash_set`.|
|[emplace –](#emplace)|Vloží element v místě do zkonstruovat `hash_set`.|
|[emplace_hint –](#emplace_hint)|Vloží element v místě do zkonstruovat `hash_set`, s pomocným parametrem umístění.|
|[prázdný](#empty)|Pokud testy `hash_set` je prázdný.|
|[End](#end)|Vrátí iterátor, který řeší úspěšné posledním prvkem v umístění `hash_set`.|
|[equal_range](#equal_range)|Vrátí pár iterátory prvním elementem v v uvedeném pořadí `hash_set` s klíčem, který je větší, než je zadaný klíč a prvním elementem v `hash_set` s klíčem, který je rovna nebo větší než klíč.|
|[vymazání](#erase)|Odebere element nebo rozsah elementů v `hash_set` ze zadaných pozic nebo odebere elementy, které odpovídají zadaným klíčem.|
|[Najít](#find)|Vrátí iterovat adresování umístění elementu v `hash_set` který má klíč ekvivalentní k zadanému klíči.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objekt použitý k vytvoření `hash_set`.|
|[Vložení](#insert)|Vloží elementu nebo rozsahu prvků do `hash_set`.|
|[key_comp](#key_comp)|Načte kopii porovnání objekt použitý k pořadí klíčů v `hash_set`.|
|[lower_bound –](#lower_bound)|Vrátí iterovat prvním elementem v `hash_set` s klíčem, který je rovna nebo větší než je zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délka `hash_set`.|
|[rbegin –](#rbegin)|Vrátí iterovat adresování prvním elementem v odstínech `hash_set`.|
|[rend –](#rend)|Vrátí iterátor, který řeší umístění úspěšné posledním prvkem v odstínech `hash_set`.|
|[Velikost](#size)|Vrátí počet prvků v `hash_set`.|
|[Swap](#swap)|Výměny dva elementy `hash_set`s.|
|[upper_bound –](#upper_bound)|Vrátí iterovat prvním elementem v `hash_set` , s klíčem, který je rovna nebo větší než je zadaný klíč.|
|[value_comp](#value_comp)|Načte kopii objekt hash vlastnosti použít k hash a pořadí klíčové hodnoty v elementu `hash_set`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[hash_set::Operator =](#op_eq)|Nahradí elementy `hash_set` kopii jiného `hash_set`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<hash_set >

**Namespace:** stdext –

## <a name="allocator_type"></a>  hash_set::allocator_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který reprezentuje allocator – třída objektu hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Poznámky

**allocator_type –** je synonymum pro parametr šablony `Allocator`.

Další informace o `Allocator`, najdete v části poznámky [hash_set – třída](../standard-library/hash-set-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se příklad [get_allocator –](#get_allocator) pro příklad, který používá `allocator_type`.

## <a name="begin"></a>  hash_set::begin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterátor, který řeší prvním elementem v hash_set.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Adresování prvním elementem v hash_set nebo umístění úspěšné prázdný hash_set iterator obousměrné.

### <a name="remarks"></a>Poznámky

Pokud vrátí hodnotu, která **začít** je přiřazena k `const_iterator`, elementy v objektu hash_set nemůže být upraven. Pokud vrátí hodnotu, která **začít** je přiřazena k **iterator**, elementy v objektu hash_set je možné upravit.

### <a name="example"></a>Příklad

```cpp
// hash_set_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.begin( );
   cout << "The first element of hs1 is " << *hs1_Iter << endl;

   hs1_Iter = hs1.begin( );
   hs1.erase( hs1_Iter );

   // The following 2 lines would err because the iterator is const
   // hs1_cIter = hs1.begin( );
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.begin( );
   cout << "The first element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
The first element of hs1 is now 2
```

## <a name="cbegin"></a>  hash_set::cbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí const iterator, která řeší prvním elementem v hash_set.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const iterator obousměrného adresování prvním elementem v [hash_set](../standard-library/hash-set-class.md) nebo umístění úspěšné prázdnou `hash_set`.

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin`, elementů v `hash_set` objekt nelze změnit.

### <a name="example"></a>Příklad

```cpp
// hash_set_cbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cbegin( );
   cout << "The first element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
```

## <a name="cend"></a>  hash_set::cend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí const iterator, která řeší úspěšné posledním prvkem v hash_set umístění.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const iterator obousměrného, která řeší úspěšné posledním prvkem v umístění [hash_set](../standard-library/hash-set-class.md). Pokud `hash_set` je prázdný, pak `hash_set::cend == hash_set::begin`.

### <a name="remarks"></a>Poznámky

`cend` slouží k otestování, jestli iterovat byl dosažen konec jeho `hash_set`. Hodnoty vrácené `cend` by neměl být vyhodnoceny odkazy.

### <a name="example"></a>Příklad

```cpp
// hash_set_cend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cend( );
   hs1_cIter--;
   cout << "The last element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
```

## <a name="clear"></a>  hash_set::clear

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vymaže všechny elementy hash_set.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 1 );
   hs1.insert( 2 );

   cout << "The size of the hash_set is initially " << hs1.size( )
        << "." << endl;

   hs1.clear( );
   cout << "The size of the hash_set after clearing is "
        << hs1.size( ) << "." << endl;
}
```

```Output
The size of the hash_set is initially 2.
The size of the hash_set after clearing is 0.
```

## <a name="const_iterator"></a>  hash_set::const_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrné iterator, který může číst **const** element v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít k úpravě hodnota elementu.

### <a name="example"></a>Příklad

Podívejte se příklad [začít](#begin) pro příklad, který používá `const_iterator`.

## <a name="const_pointer"></a>  hash_set::const_pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje odkazy **const** element v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít k úpravě hodnota elementu.

Ve většině případů [const_iterator –](#const_iterator) se má použít pro přístup k elementům v **const** hash_set objektu.

## <a name="const_reference"></a>  hash_set::const_reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který obsahuje odkaz na **const** element uložené v hash_set pro čtení a provádění **const** operace.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_const_ref.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_set is 10.
```

## <a name="const_reverse_iterator"></a>  hash_set::const_reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrné iterator, který může číst všechny **const** element v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nelze změnit hodnotu elementu a je použít k iteraci v rámci hash_set pozpátku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rend](#rend) příklad toho, jak deklarace a používání `const_reverse_iterator`

## <a name="count"></a>  hash_set::Count

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí počet prvků v hash_set, jehož klíč odpovídá parametru zadaný klíč.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Klíč elementy lze porovnat z hash_set.

### <a name="return-value"></a>Návratová hodnota

1, pokud hash_set obsahuje element, jehož klíč řazení shoduje s klíčem parametr.

0, pokud hash_set neobsahuje element s odpovídající klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v následujícím rozsahu:

[ **lower_bound –** (_ *klíč* ), **upper_bound –** (\_ *klíč* )).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_set::count – členská funkce.

```cpp
// hash_set_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1;
    hash_set<int>::size_type i;

    hs1.insert(1);
    hs1.insert(1);

    // Keys must be unique in hash_set, so duplicates are ignored.
    i = hs1.count(1);
    cout << "The number of elements in hs1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hs1.count(2);
    cout << "The number of elements in hs1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hs1 with a sort key of 1 is: 1.
The number of elements in hs1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>  hash_set::crbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí const iterator adresování prvním elementem v invertovaných hash_set.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse obousměrného iterator adresování prvním elementem v odstínech [hash_set](../standard-library/hash-set-class.md) nebo řešení, co je posledním prvkem v unreversed `hash_set`.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s odstínech hash_set stejně jako [hash_set::begin](#begin) se používá s hash_set.

S návratovou hodnotou `crbegin`, `hash_set` objekt nelze změnit.

`crbegin` lze použít k iteraci v rámci `hash_set` zpětné.

### <a name="example"></a>Příklad

```cpp
// hash_set_crbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
```

## <a name="crend"></a>  hash_set::crend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí const iterator, která řeší úspěšné posledním prvkem v invertovaných hash_set umístění.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse iterator obousměrného, která řeší umístění úspěšné posledním prvkem v odstínech [hash_set](../standard-library/hash-set-class.md) (umístění, které měl před prvním elementem v unreversed `hash_set`).

### <a name="remarks"></a>Poznámky

`crend` se používá s odstínech `hash_set` stejně jako [hash_set::end](#end) se používá s `hash_set`.

S návratovou hodnotou `crend`, `hash_set` objekt nelze změnit.

`crend` můžete použít k testování na tom, jestli má zpětné iterator dosáhla konce jeho `hash_set`.

### <a name="example"></a>Příklad

```cpp
// hash_set_crend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
```

## <a name="difference_type"></a>  hash_set::difference_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ se znaménkem, který můžete použít k reprezentování počet elementů hash_set v rozsahu mezi elementy, na kterou iterátory odkazuje.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` Je typ vrácena, pokud odečtením nebo zvyšování prostřednictvím iterátory kontejneru. `difference_type` Se obvykle používá k reprezentování počet elementů v rozsahu [ `first`, `last`) mezi iterátory `first` a `last`, obsahuje element, na kterou odkazuje `first` a rozsah elementů než , ale bez zahrnutí elementu, na kterou odkazuje `last`.

Všimněte si, že i když `difference_type` je k dispozici pro všechny iterátory, které splňují požadavky vstupní iterator, který obsahuje třídu obousměrného iterátory nepodporuje reverzibilního kontejnery, jako je sada, odčítání mezi iterátory pouze iterátory náhodný přístup poskytuje náhodný přístup kontejneru, například vektoru nebo deque podporována.

### <a name="example"></a>Příklad

```cpp
// hash_set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter, hs1_bIter, hs1_eIter;

   hs1.insert( 20 );
   hs1.insert( 10 );
   hs1.insert( 20 );   // Won't insert as hash_set elements are unique

   hs1_bIter = hs1.begin( );
   hs1_eIter = hs1.end( );

   hash_set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( hs1_bIter, hs1_eIter, 5 );
   df_typ10 = count( hs1_bIter, hs1_eIter, 10 );
   df_typ20 = count( hs1_bIter, hs1_eIter, 20 );

   // The keys, and hence the elements, of a hash_set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_set hs1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_set hs1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_set hs1.\n";

   // Count the number of elements in a hash_set
   hash_set <int>::difference_type  df_count = 0;
   hs1_Iter = hs1.begin( );
   while ( hs1_Iter != hs1_eIter)
   {
      df_count++;
      hs1_Iter++;
   }

   cout << "The number of elements in the hash_set hs1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_set hs1.
The number '10' occurs 1 times in hash_set hs1.
The number '20' occurs 1 times in hash_set hs1.
The number of elements in the hash_set hs1 is: 2.
```

## <a name="emplace"></a>  hash_set::emplace

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vloží element sestavený na místě do hash_set.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`val`|Hodnota elementu, který má být vložen do [hash_set](../standard-library/hash-set-class.md) Pokud `hash_set` již obsahuje daný element nebo více obecně element, jehož klíč je ekvivalentně řazení.|

### <a name="return-value"></a>Návratová hodnota

`emplace` – Členská funkce vrátí pár jejichž `bool` vrátí součást `true` Pokud vložení zkontrolujte a `false` Pokud `hash_set` už obsažený element, jehož klíč měl ekvivalentní hodnotu v pořadí a jehož iterator součást vrátí adresu vloženy nového elementu nebo kde byl element již nachází.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.emplace(move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="emplace_hint"></a>  hash_set::emplace_hint

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vloží element sestavený na místě do hash_set.

```cpp
template <class ValTy>
iterator emplace(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`val`|Hodnota elementu, který má být vložen do [hash_set](../standard-library/hash-set-class.md) Pokud `hash_set` již obsahuje daný element nebo více obecně element, jehož klíč je ekvivalentně řazení.|
|`_Where`|Místo zahájení vyhledání správného bodu vložení. (Vložení se může objevit v amortizovaný konstantní čas, místo logaritmické čas, pokud bod vložení následuje `_Where`.)|

### <a name="return-value"></a>Návratová hodnota

[Hash_set::emplace](#emplace) – členská funkce vrátí iterátor, který odkazuje na pozici, kde byl nový element vložený do `hash_set`, nebo kde se nachází existující element s ekvivalentní řazení.

### <a name="remarks"></a>Poznámky

Vložení se může objevit v amortizovaný konstantní čas, místo logaritmické čas, pokud bod vložení následuje `_Where`.

### <a name="example"></a>Příklad

```cpp
// hash_set_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.insert(hs3.begin(), move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="empty"></a>  hash_set::Empty

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Testy, pokud hash_set je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud hash_set je prázdná. **false** Pokud je hash_set neprázdný.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2;
   hs1.insert ( 1 );

   if ( hs1.empty( ) )
      cout << "The hash_set hs1 is empty." << endl;
   else
      cout << "The hash_set hs1 is not empty." << endl;

   if ( hs2.empty( ) )
      cout << "The hash_set hs2 is empty." << endl;
   else
      cout << "The hash_set hs2 is not empty." << endl;
}
```

```Output
The hash_set hs1 is not empty.
The hash_set hs2 is empty.
```

## <a name="end"></a>  hash_set::end

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterátor, který řeší úspěšné posledním prvkem v hash_set umístění.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Iterator obousměrného, která řeší úspěšné posledním prvkem v hash_set umístění. Pokud hash_set je prázdný, hash_set::end == hash_set::begin.

### <a name="remarks"></a>Poznámky

**end** slouží k otestování, jestli iterovat dosáhne konce své hash_set. Hodnoty vrácené **end** by neměl být vyhodnoceny odkazy.

### <a name="example"></a>Příklad

```cpp
// hash_set_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: iterator hs1_Iter;
   hash_set <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.end( );
   hs1_Iter--;
   cout << "The last element of hs1 is " << *hs1_Iter << endl;

   hs1.erase( hs1_Iter );

   // The following 3 lines would err because the iterator is const:
   // hs1_cIter = hs1.end( );
   // hs1_cIter--;
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.end( );
   hs1_cIter--;
   cout << "The last element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
The last element of hs1 is now 2
```

## <a name="equal_range"></a>  hash_set::equal_range

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí pár iterátory v uvedeném pořadí prvním elementem v hodnotu hash nastavit s klíčem, který se rovná zadaný klíč a první prvek v hash nastavit s klíčem, který je větší než klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

`key` Argument klíč, který se má porovnat s klíč řazení elementu z hash_set prohledávaný.

### <a name="return-value"></a>Návratová hodnota

Pár iterátory, kde je první [lower_bound –](../standard-library/set-class.md#lower_bound) klíč a druhý je [upper_bound –](../standard-library/set-class.md#upper_bound) klíče.

Pro přístup první iterator pár pr vrácené funkcí člen, použít `pr`. **první**a pokud chcete dereference iterator dolní mez, použijte \*( `pr`. **nejprve**). Pro přístup k druhý iterator páru `pr` vrácené funkcí člen, použijte `pr`. **druhý**a pokud chcete dereference iterator horní mez, použijte \*( `pr`. **druhý**).

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_set<int> IntHSet;
   IntHSet hs1;
   hash_set <int> :: const_iterator hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hs1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hs1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hs1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hs1.end( ) ) && ( p2.second == hs1.end( ) ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than or equal to 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the hash_set hs1 is: 30.
The lower bound of the element with a key of 20 in the hash_set hs1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_set hs1 doesn't have an element with a key greater than or equal to 40.
```

## <a name="erase"></a>  hash_set::Erase

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Odebere element nebo rozsah elementů v hash_set ze zadaných pozic nebo odebere prvky, které odpovídají zadaným klíčem.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

`_Where` Pozice elementu, který má být odebrán z hash_set.

`first` Pozice první prvek odebrán z hash_set.

`last` Pozice bezprostředně za posledním elementem odebrán z hash_set.

`key` Klíč elementů má být odebrán z hash_set.

### <a name="return-value"></a>Návratová hodnota

Pro první dva členské funkce obousměrné iterator, označí první prvek zbývající nad rámec žádné elementy, odebrat nebo odkazy na konec hash_set, pokud neexistuje žádný takový prvek. Třetí funkce člen, počet elementů, které byly odebrány z hash_set.

### <a name="remarks"></a>Poznámky

Členské funkce nikdy vyvolat výjimku.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_set::erase – členská funkce.

```cpp
// hash_set_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1, hs2, hs3;
    hash_set<int>::iterator pIter, Iter1, Iter2;
    int i;
    hash_set<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hs1.insert (i);
        hs2.insert (i * i);
        hs3.insert (i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hs1.begin();
    hs1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_set hs1 is:";
    for (pIter = hs1.begin(); pIter != hs1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hs2.begin();
    Iter2 = --hs2.end();
    hs2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_set hs2 is:";
    for (pIter = hs2.begin(); pIter != hs2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hs3.erase(2);

    cout << "After the element with a key of 2 is deleted, "
         << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hs3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hs3.begin();
    hs3.erase(Iter1);

    cout << "After another element (unique for hash_set) with a key "
         << endl;
    cout  << "equal to that of the 2nd element is deleted, "
          << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_set hs1 is: 1 3 4.
After the middle two elements are deleted, the hash_set hs2 is: 16 4.
After the element with a key of 2 is deleted, the hash_set hs3 is: 0 1 3.
The number of elements removed from hs3 is: 1.
After another element (unique for hash_set) with a key
equal to that of the 2nd element is deleted, the hash_set hs3 is: 0 3.
```

## <a name="find"></a>  hash_set::Find

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterovat adresování umístění elementu v hash_set, s klíčem ekvivalentní k zadanému klíči.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Argument klíč odpovídala klíč řazení elementu z hash_set být vyhledán.

### <a name="return-value"></a>Návratová hodnota

**Iterator** nebo `const_iterator` , který se týká umístění element ekvivalentní k zadanému klíči nebo který adres umístění posledním prvkem v hash_set úspěšné, pokud není nalezena žádná shoda pro klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který řeší element v hash_set, jehož klíč řazení je **ekvivalentní** argument klíč v predikátu Binární indukuje řazení na základě méně – než srovnání vztah.

Pokud vrátí hodnotu, která **najít** je přiřazena k `const_iterator`, hash_set objekt nelze změnit. Pokud vrátí hodnotu, která **najít** je přiřazena k **iterator**, objekt hash_set je možné upravit.

### <a name="example"></a>Příklad

```cpp
// hash_set_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.find( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // The element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.find( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a>  hash_set::get_allocator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí kopii allocator objekt použitý k vytvoření hash_set.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Allocator slouží ke správě paměti, což je parametr šablony hash_set `Allocator`.

Další informace o `Allocator`, najdete v části poznámky [hash_set – třída](../standard-library/hash-set-class.md) tématu.

### <a name="remarks"></a>Poznámky

Alokátorů pro hash_set – Třída zadejte, jak třída spravuje úložiště. Alokátorů výchozí součástí standardní knihovna C++ – třídy kontejnerů postačí pro většinu programovacích potřeb. Psaní a pomocí vlastní allocator – třída je rozšířená C++.

### <a name="example"></a>Příklad

```cpp
// hash_set_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_set <int, hash_compare <int, less<int> > > hs1;
   hash_set <int,  hash_compare <int, greater<int> > > hs2;
   hash_set <double, hash_compare <double,
      less<double> >, allocator<double> > hs3;

   hash_set <int, hash_compare <int,
      greater<int> > >::allocator_type hs2_Alloc;
   hash_set <double>::allocator_type hs3_Alloc;
   hs2_Alloc = hs2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs3.max_size( ) <<  "." << endl;

   // The following lines create a hash_set hs4
   // with the allocator of hash_set hs1.
   hash_set <int>::allocator_type hs4_Alloc;
   hash_set <int> hs4;
   hs4_Alloc = hs2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hs2_Alloc == hs4_Alloc )
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

## <a name="hash_set"></a>  hash_set::hash_set

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vytvoří `hash_set` který je prázdný nebo který je kopie všech nebo některých jiných součástí `hash_set`.

```cpp
hash_set();

explicit hash_set(
    const Traits& Comp);

hash_set(
    const Traits& Comp,
    const Allocator& Al);

hash_set(
    const hash_set<Key, Traits, Allocator>& Right);

hash_set(
    hash_set&& Right);

hash_set(
    initializer_list<Type> IList);

hash_set(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_set(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_set(
 InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_set(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_set(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`Al`|Allocator – třída úložiště má být použit pro toto `hash_set` objekt, který se standardně `Allocator`.|
|`Comp`|Funkci porovnání typu `const Traits` sloužící k uspořádání elementů v `hash_set`, což výchozí nastavení `hash_compare`.|
|`Right`|`hash_set` z nich konstruovaný objekt `hash_set` má být kopie.|
|`First`|Pozice první prvek v rozsahu elementy, které se mají zkopírovat.|
|`Last`|Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.|

### <a name="remarks"></a>Poznámky

Typ allocator objekt, který spravuje paměti úložiště pro ukládání všechny konstruktory `hash_set` a který se může vracet později voláním [hash_set::get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializovat jejich hash_sets.

Všechny konstruktory uložit objekt funkce typu `Traits` který se používá k navázání pořadí mezi klíče `hash_set` a který se může vracet později voláním [hash_set::key_comp](#key_comp). Další informace o `Traits` najdete v článku [hash_set – třída](../standard-library/hash-set-class.md) tématu.

První konstruktoru vytvoří prázdný počáteční `hash_set` druhý určuje typ funkce porovnání ( `Comp`) pro použití při vytváření pořadí elementy a třetí explicitně určuje typ allocator ( `Al`) jako použít. Klíčové slovo `explicit` potlačí některé druhy automatického převodu typu.

Konstruktory čtvrté a páté zadejte kopii `hash_set` `Right`.

Poslední šestinu, sedmý a osmou konstruktory použít initializer_list pro elementy.

Poslední konstruktory zkopírujte rozsahu [ `First`, `Last`) z `hash_set` se zvýšeným explicitness v určení typu funkci porovnání vlastnosti třídy a přidělení.

Osmého konstruktor přesune `hash_set` `Right`.

Skutečné pořadí prvků v `hash_set` kontejneru závisí na funkci hash, funkci řazení a aktuální velikost hash tabulky a nelze, předpovědět obecně platí, jako to bylo možné v kontejneru sady, kde bylo zjištěno nalezením řazení funkce samostatně.

## <a name="insert"></a>  hash_set::Insert

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vloží elementu nebo rozsahu prvků do `hash_set`.

```cpp
pair<iterator, bool> insert(
    const value_type& Val);

iterator insert(
    iterator Where,
    const value_type& Val);

void insert(
    initializer_list<value_type> IList)
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`Val`|Hodnota elementu, který má být vložen do `hash_set` Pokud `hash_set` již obsahuje daný element nebo více obecně element, jehož klíč je ekvivalentně řazení.|
|`Where`|Místo zahájení vyhledání správného bodu vložení. (Vložení se může objevit v amortizovaný konstantní čas, místo logaritmické čas, pokud bod vložení následuje `_Where`.)|
|`First`|Pozice první prvek, který se má zkopírovat z `hash_set`.|
|`Last`|Pozice bezprostředně za posledním elementem zkopírovány z `hash_set`.|
|`IList`|Seznam initializer_list, ze kterého chcete kopírovat prvky.|

### <a name="return-value"></a>Návratová hodnota

První `insert` – členská funkce vrátí pár jejichž `bool` vrátí součást `true` Pokud vložení zkontrolujte a `false` Pokud `hash_set` už obsažený element, jehož klíč měl ekvivalentní hodnotu v pořadí, a součást jejichž iterator vrátí adresu vloženy nového elementu nebo kde byl element již nachází.

Pro přístup k iterator součást pár `pr` vrácené funkcí tento člen, použijte `pr.first` a pokud chcete ho dereference, použijte `*(pr.first)`. Abyste měli přístup `bool` součásti z dvojice `pr` vrácené funkcí tento člen, použijte `pr.second`a pokud chcete ho dereference, použijte `*(pr.second)`.

Druhý `insert` – členská funkce vrátí iterátor, který odkazuje na pozici, kde byl nový element vložený do `hash_set`.

### <a name="remarks"></a>Poznámky

Třetí členská funkce vloží elementy initializer_list.

Třetí členská funkce vloží pořadí hodnot element do `hash_set` odpovídající každý prvek řešené pomocí iterace v rozsahu [ `First`, `Last`) ze zadané `hash_set`.

## <a name="iterator"></a>  hash_set::iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrné iterator, který může číst nebo upravovat libovolný element v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Poznámky

Typ **iterator** lze upravit hodnotu elementu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin) příklad toho, jak deklarace a používání **iterator**.

## <a name="key_comp"></a>  hash_set::key_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Načte kopii objekt hash vlastnosti použít k hash a pořadí element hodnoty klíče v hash_set.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce využívající hash_set pořadí jeho prvky, což je parametr šablony `Traits`.

Další informace o `Traits` najdete v článku [hash_set – třída](../standard-library/hash-set-class.md) tématu.

### <a name="remarks"></a>Poznámky

Objekt uložené definuje – členská funkce:

**BOOL – operátor**( **const klíč &** _ *xVal*, **const klíč &** \_ `yVal`);

která vrací **true** Pokud `_xVal` předchází a není rovno `_yVal` v pořadí řazení.

Všimněte si, že oba [key_compare –](#key_compare) a [value_compare –](#value_compare) jsou synonyma pro parametr šablony **vlastnosti**. Oba typy jsou uvedené pro třídy hash_set a hash_multiset tam, kde jsou stejné pro kompatibilitu s třídy hash_map a hash_multimap tam, kde jsou odlišné.

### <a name="example"></a>Příklad

```cpp
// hash_set_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > >hs1;
   hash_set<int, hash_compare < int, less<int> > >::key_compare kc1
          = hs1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hs1."
        << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hs2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="key_compare"></a>  hash_set::key_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje funkce objekt, který můžete porovnat dva klíče řazení pro určení pořadí, relativní ze dvou prvků v hash_set.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare` je synonymum pro parametr šablony `Traits`.

Další informace o `Traits` najdete v článku [hash_set – třída](../standard-library/hash-set-class.md) tématu.

Všimněte si, že oba `key_compare` a [value_compare –](#value_compare) jsou synonyma pro parametr šablony **vlastnosti**. Oba typy jsou uvedené pro sady a multiset třídy, tam, kde jsou identické, zajištění kompatibility se službou mapy a multimap třídy, které jsou jedinečné.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [key_comp –](#key_comp) příklad toho, jak deklarace a používání `key_compare`.

## <a name="key_type"></a>  hash_set::key_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který popisuje objekt uložené jako element hash_set jako klíč řazení.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

**key_type –** je synonymum pro parametr šablony `Key`.

Další informace o `Key`, najdete v části poznámky [hash_set – třída](../standard-library/hash-set-class.md) tématu.

Všimněte si, že oba `key_type` a [value_type](#value_type) jsou synonyma pro parametr šablony **klíč**. Oba typy jsou uvedené pro třídy hash_set a hash_multiset tam, kde jsou stejné pro kompatibilitu s třídy hash_map a hash_multimap tam, kde jsou odlišné.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_type](#value_type) příklad toho, jak deklarace a používání `key_type`.

## <a name="lower_bound"></a>  hash_set::lower_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterovat prvním elementem v hash_set s klíčem, který je rovna nebo větší než je zadaný klíč.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

`key` Argument klíč, který se má porovnat s klíč řazení elementu z hash_set prohledávaný.

### <a name="return-value"></a>Návratová hodnota

**Iterator** nebo `const_iterator` , který se týká umístění elementu v hash_set, že klíčem, která je rovna nebo větší než argument klíč nebo který adres umístění posledním prvkem v hash_set úspěšné, pokud žádné odpovídají pro klíč nebyl nalezen.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.lower_bound( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator that addresses the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.lower_bound( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a>  hash_set::max_size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí maximální délka hash_set.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možné délku hash_set.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::size_type i;

   i = hs1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_set is " << i << "." << endl;
}
```

## <a name="op_eq"></a>  hash_set::Operator =

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Elementy hash_set nahradí kopii jiného hash_set.

```cpp
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`right`|[Hash_set](../standard-library/hash-set-class.md) se zkopírují `hash_set`.|

### <a name="remarks"></a>Poznámky

Po vymazání v žádné stávající elementy `hash_set`, `operator=` buď kopíruje nebo přesouvá obsah `right` do `hash_set`.

### <a name="example"></a>Příklad

```cpp
// hash_set_operator_as.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<int> v1, v2, v3;
   hash_set<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>  hash_set::Pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje ukazatel na prvek v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ **ukazatel** lze upravit hodnotu elementu.

Ve většině případů [iterator](#iterator) se má použít pro přístup k elementům v hash_set objektu.

## <a name="rbegin"></a>  hash_set::rbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterator adresování prvním elementem v invertovaných hash_set.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Iterator zpětné obousměrného adresování prvním elementem v invertovaných hash_set nebo řešení, co je posledním prvkem v unreversed hash_set.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s odstínech hash_set stejně jako [začít](#begin) se používá s hash_set.

Pokud vrátí hodnotu, která `rbegin` je přiřazena k `const_reverse_iterator`, pak hash_set objekt nelze změnit. Pokud vrátí hodnotu, která `rbegin` je přiřazena k `reverse_iterator`, pak je možné upravit objekt hash_set.

`rbegin` můžete použít k iteraci v rámci hash_set zpětné.

### <a name="example"></a>Příklad

```cpp
// hash_set_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // begin can be used to start an iteration
   // throught a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // throught a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << endl;

   // A hash_set element can be erased by dereferencing to its key
   hs1_rIter = hs1.rbegin( );
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_set is "<< *hs1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
The hash_set is: 10 20 30
The reversed hash_set is: 30 20 10
After the erasure, the first element in the reversed hash_set is 20.
```

## <a name="reference"></a>  hash_set::Reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který obsahuje odkaz na element v hash_set uložené.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_set can be changed
   // by operating on its (non-const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_set is now "
        << *hs1.begin() << "." << endl;
}
```

```Output
The first element in the hash_set is 10.
The first element in the hash_set is now 15.
```

## <a name="rend"></a>  hash_set::rend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterátor, který řeší úspěšné posledním prvkem v invertovaných hash_set umístění.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Iterator zpětné obousměrného, která řeší umístění úspěšné posledním prvkem v invertovaných hash_set (umístění, které měl před prvním elementem v unreversed hash_set).

### <a name="remarks"></a>Poznámky

`rend` se používá s odstínech hash_set stejně jako [end](#end) se používá s hash_set.

Pokud vrátí hodnotu, která `rend` je přiřazena k `const_reverse_iterator`, pak hash_set objekt nelze změnit. Pokud vrátí hodnotu, která `rend` je přiřazena k `reverse_iterator`, pak je možné upravit objekt hash_set. Hodnoty vrácené `rend` by neměl být vyhodnoceny odkazy.

`rend` slouží k testování, aby se jestli zpětné iterator dosáhne konce své hash_set.

### <a name="example"></a>Příklad

```cpp
// hash_set_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // throught a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << "." << endl;

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_set is " << *hs1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
The hash_set is: 10 20 30 .
The reversed hash_set is: 30 20 10 .
After the erasure, the last element in the reversed hash_set is 20.
```

## <a name="reverse_iterator"></a>  hash_set::reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrné iterator, které můžou číst nebo upravte element v invertovaných hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` je použít k iteraci v rámci hash_set pozpátku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rbegin –](#rbegin) příklad toho, jak deklarace a používání `reverse_iterator`.

## <a name="size"></a>  hash_set::size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí počet prvků hash_set.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka hash_set.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: size_type i;

   hs1.insert( 1 );
   i = hs1.size( );
   cout << "The hash_set length is " << i << "." << endl;

   hs1.insert( 2 );
   i = hs1.size( );
   cout << "The hash_set length is now " << i << "." << endl;
}
```

```Output
The hash_set length is 1.
The hash_set length is now 2.
```

## <a name="size_type"></a>  hash_set::size_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ celé číslo bez znaménka, která představuje počet elementů ve hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Podívejte se na příklad pro [velikost](#size) příklad toho, jak deklarace a používání `size_type`

## <a name="swap"></a>  hash_set::swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Elementy dvě hash_sets výměny.

```cpp
void swap(hash_set& right);
```

### <a name="parameters"></a>Parametry

`right` Hash_set – argument poskytování elementy pro si místo se hash_set cíl.

### <a name="remarks"></a>Poznámky

Členská funkce by způsobila neplatnost žádné odkazy, ukazatele nebo iterátory, které určit elementů ve dvou hash_sets, jehož elementy jsou během výměny.

### <a name="example"></a>Příklad

```cpp
// hash_set_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   hash_set <int>::iterator hs1_Iter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );
   hs2.insert( 100 );
   hs2.insert( 200 );
   hs3.insert( 300 );

   cout << "The original hash_set hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hs1.swap( hs2 );

   cout << "After swapping with hs2, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hs1, hs3 );

   cout << "After swapping with hs3, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_set hs1 is: 10 20 30.
After swapping with hs2, list hs1 is: 200 100.
After swapping with hs3, list hs1 is: 300.
```

## <a name="upper_bound"></a>  hash_set::upper_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterovat prvním elementem v hash_set, s klíčem, který je větší než je zadaný klíč.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

`key` Argument klíč, který se má porovnat s klíč řazení elementu z hash_set prohledávaný.

### <a name="return-value"></a>Návratová hodnota

**Iterator** nebo `const_iterator` , který se týká umístění elementu v hash_set, že klíčem, která je rovna nebo větší než argument klíč nebo který adres umístění posledním prvkem v hash_set úspěšné, pokud žádné odpovídají pro klíč nebyl nalezen.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "The first element of hash_set hs1 with a key greater "
        << "than 20 is: " << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_set hs1 with a key > 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.begin( );
   hs1_RcIter = hs1.upper_bound( *hs1_AcIter );
   cout << "The first element of hs1 with a key greater than "
        << endl << "that of the initial element of hs1 is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The first element of hash_set hs1 with a key greater than 20 is: 30.
The hash_set hs1 doesn't have an element with a key greater than 30.
The first element of hs1 with a key greater than
that of the initial element of hs1 is: 20.
```

## <a name="value_comp"></a>  hash_set::value_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Načte kopii porovnání objekt použitý k hodnoty element pořadí v hash_set.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce využívající hash_set pořadí jeho prvky, což je parametr šablony `Compare`.

Další informace o `Compare`, najdete v části poznámky [hash_set – třída](../standard-library/hash-set-class.md) tématu.

### <a name="remarks"></a>Poznámky

Objekt uložené definuje – členská funkce:

**BOOL – operátor**( **const klíč &** _ *xVal*, **const klíč &** \_ `yVal`);

která vrací **true** Pokud `_xVal` předchází a není rovno `_yVal` v pořadí řazení.

Všimněte si, že oba [value_compare –](../standard-library/set-class.md#value_compare) a [key_compare –](../standard-library/set-class.md#key_compare) jsou synonyma pro parametr šablony `Compare`. Oba typy jsou uvedené pro třídy hash_set a hash_multiset tam, kde jsou stejné pro kompatibilitu s třídy hash_map a hash_multimap tam, kde jsou odlišné.

### <a name="example"></a>Příklad

```cpp
// hash_set_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > > hs1;
   hash_set <int, hash_compare < int, less<int> >  >::value_compare
      vc1 = hs1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hs1."
           << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::value_compare
      vc2 = hs2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="value_compare"></a>  hash_set::value_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje dva objekty funkce binární predikátu porovnání třída, která můžete porovnat dvě hodnoty element hash_set určit jejich relativní pořadí a predikát unární, který vytvoří hodnotu hash elementy.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Poznámky

**value_compare –** je synonymum pro parametr šablony `Traits`.

Další informace o `Traits` najdete v článku [hash_set – třída](../standard-library/hash-set-class.md) tématu.

Všimněte si, že oba [key_compare –](#key_compare) a **value_compare –** jsou synonyma pro parametr šablony **vlastnosti**. Oba typy jsou uvedené pro třídy hash_set a hash_multiset tam, kde jsou stejné pro kompatibilitu s třídy hash_map a hash_multimap tam, kde jsou odlišné.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_comp –](#value_comp) příklad toho, jak deklarace a používání `value_compare`.

## <a name="value_type"></a>  hash_set::value_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který popisuje objekt uložené jako element hash_set jako hodnotu.

```cpp
typedef Key value_type;
```

### <a name="example"></a>Příklad

```cpp
// hash_set_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;

   hash_set <int> :: value_type hsvt_Int;   // Declare value_type
   hsvt_Int = 10;             // Initialize value_type

   hash_set <int> :: key_type hskt_Int;   // Declare key_type
   hskt_Int = 20;             // Initialize key_type

   hs1.insert( hsvt_Int );         // Insert value into hs1
   hs1.insert( hskt_Int );         // Insert key into hs1

   // A hash_set accepts key_types or value_types as elements
   cout << "The hash_set has elements:";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( ); hs1_Iter++)
      cout << " " << *hs1_Iter;
   cout << "." << endl;
}
```

```Output
The hash_set has elements: 10 20.
```

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
