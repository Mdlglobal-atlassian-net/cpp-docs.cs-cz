---
title: hash_set – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 3bf4065b4c409e1baad3183cc8ccbd8c97d43d5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370605"
---
# <a name="hash_set-class"></a>hash_set – třída

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Třída kontejneru hash_set je rozšíření standardní knihovny Jazyka C++ a používá se pro ukládání a rychlé načítání dat z kolekce, ve které jsou jedinečné hodnoty prvků, ve kterých jsou jedinečné a slouží jako klíčové hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<Key>>
class hash_set
```

### <a name="parameters"></a>Parametry

*Klíč*\
Datový typ prvku, který má být uložen v hash_set.

*Vlastnosti*\
Typ, který obsahuje dva objekty funkce, jeden z třídy porovnat, který je binární predikát schopen porovnat dva element hodnoty jako klíče řazení k určení jejich relativní pořadí a `size_t`hash funkce, která je unární predikát mapování klíčových hodnot prvků neznatelná celá čísla typu . Tento argument je volitelný `hash_compare<Key, less<Key> >` a je výchozí hodnota.

*Přidělování*\
Typ, který představuje uložený objekt přidělování, který zapouzdřuje podrobnosti o přidělení hash_set a přidělení paměti. Tento argument je volitelný a `allocator<Key>`výchozí hodnota je .

## <a name="remarks"></a>Poznámky

Hash_set je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče. Dále je to jednoduchý asociativní kontejner, protože jeho hodnoty prvku jsou jeho hodnoty klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Hashed, protože jeho prvky jsou seskupeny do bloků na základě hodnoty funkce hash aplikované na klíčové hodnoty prvků.

- Jedinečný v tom smyslu, že každý z jeho prvků musí mít jedinečný klíč. Vzhledem k tomu, hash_set je také jednoduchý asociativní kontejner, jeho prvky jsou také jedinečné.

- Šablona třídy, protože funkce, které poskytuje, je obecná a tak nezávislá na konkrétním typu dat obsažených jako prvky nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Hlavní výhodou hašování nad tříděním je větší účinnost; úspěšné zapisování provádí vložení, odstranění a najde v konstantní mzda v průměru čas ve srovnání s časem úměrná logaritmu počtu prvků v kontejneru pro řazení techniky. Hodnotu prvku v sadě nelze změnit přímo. Místo toho musíte odstranit staré hodnoty a vložit prvky s novými hodnotami.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Hashed asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstraňování. Členské funkce, které explicitně podporují tyto operace jsou efektivní při použití s dobře navržené funkce hash, jejich provádění v čase, který je v průměru konstantní a není závislý na počtu prvků v kontejneru. Dobře navržená funkce hash vytváří rovnoměrné rozložení hodnot hash a minimalizuje počet kolizí, kde se říká, že ke kolizi dochází, když jsou odlišné hodnoty klíče mapovány na stejnou hodnotu hash. V nejhorším případě s nejhorší možnou funkcí hash je počet operací úměrný počtu prvků v sekvenci (lineární čas).

Hash_set by měl být asociativní kontejner volby při podmínky přisouvání hodnoty s jejich klíče jsou splněny aplikací. Prvky hash_set jsou jedinečné a slouží jako jejich vlastní klíče řazení. Model pro tento typ struktury je uspořádaný seznam slov, v němž se slova mohou vyskytovat pouze jednou. Pokud bylo povoleno více výskytů slov, pak by hash_multiset byla příslušnou strukturou kontejneru. Pokud hodnoty je třeba připojit k seznamu jedinečných klíčových slov, pak hash_map by vhodné struktury obsahovat tato data. Pokud místo toho klíče nejsou jedinečné, pak hash_multimap by kontejner volby.

Hash_set seřídí sekvenci, kterou `Traits` řídí voláním uloženého objektu hash typu [value_compare](#value_compare). K tomuto uloženému objektu lze přistupovat voláním key_comp členské [funkce](#key_comp). Takový objekt funkce se musí chovat stejně jako objekt třídy *hash_compare<Klíč, méně\<> > klíč.* Konkrétně pro všechny `key` hodnoty typu Key, vlastnost`key`volání( ) poskytuje rozdělení hodnot typu size_t.

Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. Výsledkem je řazení mezi prvky neekvivalentní. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát *f*( *x*, *y*) je objekt funkce, který má dva argumenty objekty x a y a vrácenou hodnotu true nebo false. Řazení uložené na hash_set je přísné slabé řazení, pokud je binární predikát nereflexivní, antisymetrický a tranzitivní a pokud je rovnocennost přenositá, kde jsou dva objekty *x* a *y* definovány jako rovnocenné, pokud jsou oba *f*( *x*, *y*) a *f*( *y*, *x*) false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

Skutečné pořadí prvků v řízené sekvenci závisí na funkci hash, funkci řazení a aktuální velikost tabulky hash uložené v objektu kontejneru. Nelze určit aktuální velikost tabulky hash, takže obecně nelze předpovědět pořadí prvků v řízené sekvenci. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Iterátor poskytované hash_set třídy je obousměrný iterátor, ale funkce členů třídy [vložit](#insert) a [hash_set](#hash_set) mají verze, které berou jako parametry šablony slabší vstupní iterátor, jehož požadavky na funkčnost jsou minimální než ty, které jsou zaručeny třídou obousměrné iterátory. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Jedná se o minimální sadu funkcí, ale stačí, abyste mohli smysluplně hovořit o řadě iterátorů [ `first`, `last`) v kontextu funkcí členů třídy.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[hash_set](#hash_set)|Konstrukce, `hash_set` který je prázdný nebo který je kopií celé `hash_set`nebo části některé jiné .|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který `allocator` představuje třídu `hash_set` pro objekt.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který `const` může `hash_set`číst prvek v .|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na **const** element v `hash_set`.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na **const** `hash_set` prvek uložený v a pro čtení a provádění **const** operací.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `hash_set`libovolný **prvek const** v .|
|[difference_type](#difference_type)|Podepsaný typ celé číslo, který lze použít k reprezentaci počtu prvků `hash_set` a v rozsahu mezi prvky, na které iterátory poukázaly.|
|[Iterace](#iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `hash_set`nebo upravovat libovolný prvek v rozhraní .|
|[key_compare](#key_compare)|Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení `hash_set`k určení relativní pořadí dvou prvků v .|
|[key_type](#key_type)|Typ, který popisuje objekt uložený jako `hash_set` prvek v jeho kapacitě jako klíč řazení.|
|[ukazatel](#pointer)|Typ, který poskytuje ukazatel na `hash_set`prvek v .|
|[Odkaz](#reference)|Typ, který poskytuje odkaz na prvek `hash_set`uložený v .|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo `hash_set`upravovat prvek v obráceném .|
|[size_type](#size_type)|Nepodepsaný podnosný typ, který může představovat počet prvků v . `hash_set`|
|[value_compare](#value_compare)|Typ, který poskytuje dva objekty funkce, binární predikát třídy `hash_set` porovnat, které lze porovnat dva elementové hodnoty a k určení jejich relativní pořadí a unární predikát, který zařazuje hodnoty prvků.|
|[value_type](#value_type)|Typ, který popisuje objekt uložený jako `hash_set` prvek v jeho kapacitě jako hodnotu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Začít](#begin)|Vrátí iterátor, který řeší první prvek `hash_set`v rozhraní .|
|[cbegin](#cbegin)|Vrátí const iterator adresující první `hash_set`prvek v rozhraní .|
|[cend](#cend)|Vrátí const iterátor, který řeší umístění, které následuje `hash_set`poslední prvek v .|
|[Jasné](#clear)|Vymaže všechny `hash_set`prvky .|
|[Počet](#count)|Vrátí počet prvků v `hash_set` klíči, jejichž klíč odpovídá klíči zadanému parametrem.|
|[crbegin](#crbegin)|Vrátí const iterator adresování první `hash_set`prvek v obrácené .|
|[crend](#crend)|Vrátí const iterator, který řeší umístění, které následuje `hash_set`poslední prvek v obráceném .|
|[místo](#emplace)|Vloží prvek vytvořený na místě `hash_set`do .|
|[emplace_hint](#emplace_hint)|Vloží prvek vytvořený na místě `hash_set`do aplikace s nápovědou k umístění.|
|[empty](#empty)|Testuje, `hash_set` pokud je prázdný.|
|[Konec](#end)|Vrátí iterátor, který řeší umístění, které následuje `hash_set`poslední prvek v rozhraní .|
|[equal_range](#equal_range)|Vrátí dvojici iterátorů respektive první prvek v `hash_set` klíč s klíčem, který je větší než zadaný klíč a na první prvek s `hash_set` klíčem, který je roven nebo větší než klíč.|
|[Vymazat](#erase)|Odebere prvek nebo rozsah prvků `hash_set` v a ze zadané pozice nebo odebere prvky, které odpovídají zadanému klíči.|
|[find](#find)|Vrátí iterátor adresování umístění prvku `hash_set` v, který má klíč ekvivalentní zadaný klíč.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objektu použitého `hash_set`k vytvoření .|
|[Vložit](#insert)|Vloží prvek nebo rozsah prvků do `hash_set`.|
|[key_comp](#key_comp)|Načte kopii objektu porovnání použitého `hash_set`k objednání klíčů v .|
|[lower_bound](#lower_bound)|Vrátí iterátor k prvnímu prvku `hash_set` v a s klíčem, který je roven nebo větší než zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délku `hash_set`.|
|[rbegin](#rbegin)|Vrátí iterátor adresující první prvek `hash_set`v obráceném .|
|[rend](#rend)|Vrátí iterátor, který řeší umístění, které následuje poslední `hash_set`prvek v obráceném .|
|[Velikost](#size)|Vrátí počet prvků v `hash_set`rozhraní .|
|[Swap](#swap)|Vyměňuje prvky `hash_set`dvou s.|
|[upper_bound](#upper_bound)|Vrátí iterátor prvnímu prvku v `hash_set` a, který s klíčem, který je roven nebo větší než zadaný klíč.|
|[value_comp](#value_comp)|Načte kopii objektu vlastností hash použitého k hodnotám `hash_set`klíče hash a objednaného prvku v rozhraní .|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[hash_set::operátor=](#op_eq)|Nahradí prvky a `hash_set` kopií jiného `hash_set`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> hash_set

**Obor názvů:** stdext

## <a name="hash_setallocator_type"></a><a name="allocator_type"></a>hash_set::allocator_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Typ, který představuje třídu alokátoru pro hash_set objekt.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type`je synonymem pro parametr šablony *Alokátor*.

Další informace o *alokátoru*naleznete v části Poznámky v tématu [hash_set třída.](../standard-library/hash-set-class.md)

### <a name="example"></a>Příklad

Viz příklad pro [get_allocator](#get_allocator) příklad, který používá `allocator_type`.

## <a name="hash_setbegin"></a><a name="begin"></a>hash_set::začátek

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí iterátor, který řeší první prvek v hash_set.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný itečelní objekt adresující první prvek v hash_set nebo umístění, které následuje prázdný hash_set.

### <a name="remarks"></a>Poznámky

Pokud `begin` je vrácená hodnota `const_iterator`přiřazena k , prvky v hash_set objektu nelze změnit. Pokud `begin` je vrácená hodnota `iterator`přiřazena k , prvky v hash_set objektu lze změnit.

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

## <a name="hash_setcbegin"></a><a name="cbegin"></a>hash_set::cbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí const iterator, který řeší první prvek v hash_set.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstovat obousměrný iterátor adresování první prvek v [hash_set](../standard-library/hash-set-class.md) nebo `hash_set`umístění, které následuje prázdné .

### <a name="remarks"></a>Poznámky

S vrácenou `cbegin`hodnotou , `hash_set` prvky v objektu nelze změnit.

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

## <a name="hash_setcend"></a><a name="cend"></a>hash_set::cenzura

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí const iterator, který řeší umístění, které následuje poslední prvek v hash_set.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstovat obousměrný iterátor, který řeší umístění, které následuje poslední prvek v [hash_set](../standard-library/hash-set-class.md). Pokud `hash_set` je prázdný, `hash_set::cend == hash_set::begin`pak .

### <a name="remarks"></a>Poznámky

`cend`se používá k testování, zda iterátor dosáhl `hash_set`konce svého . Hodnota vrácená `cend` by neměla být odkazována.

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

## <a name="hash_setclear"></a><a name="clear"></a>hash_set::vymazat

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vymaže všechny prvky hash_set.

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

## <a name="hash_setconst_iterator"></a><a name="const_iterator"></a>hash_set::const_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) `const_iterator`pro příklad, který používá .

## <a name="hash_setconst_pointer"></a><a name="const_pointer"></a>hash_set::const_pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Typ, který poskytuje ukazatel na **const** prvek v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku.

Ve většině případů [by měl](#const_iterator) být použit const_iterator pro přístup k prvkům v **objektu const** hash_set.

## <a name="hash_setconst_reference"></a><a name="const_reference"></a>hash_set::const_reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Typ, který poskytuje odkaz na **prvek const** uložený v hash_set pro čtení a provádění operací **const.**

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

## <a name="hash_setconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>hash_set::const_reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst libovolný **prvek const** v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a používá se k iterátu přes hash_set v opačném pořadí.

### <a name="example"></a>Příklad

Příklad pro [rend](#rend) najdete příklad, jak deklarovat a používat`const_reverse_iterator`

## <a name="hash_setcount"></a><a name="count"></a>hash_set::počet

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí počet prvků v hash_set jehož klíč odpovídá klíči zadanému parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč prvků, které mají být uzavřeno z hash_set.

### <a name="return-value"></a>Návratová hodnota

1 pokud hash_set obsahuje prvek, jehož klíč řazení odpovídá klíči parametru.

0, pokud hash_set neobsahuje prvek s odpovídající klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v následujícím rozsahu:

\[lower_bound(*klíč),* upper_bound(*klíč*).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_set::count členské funkce.

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

## <a name="hash_setcrbegin"></a><a name="crbegin"></a>hash_set::crbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí const iterator adresování první prvek v obrácené hash_set.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor adresování první prvek v obrácené [hash_set](../standard-library/hash-set-class.md) nebo řešení toho, co bylo poslední prvek v unreverse `hash_set`.

### <a name="remarks"></a>Poznámky

`crbegin`se používá s obráceným hash_set stejně [jako hash_set::begin](#begin) se používá s hash_set.

S vrácenou `crbegin`hodnotou `hash_set` aplikace nelze objekt změnit.

`crbegin`lze použít k iterovat přes `hash_set` dozadu.

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

## <a name="hash_setcrend"></a><a name="crend"></a>hash_set::crend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí const iterátor, který řeší umístění, které následuje poslední prvek v obráceném hash_set.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor, který řeší umístění, které následuje poslední prvek v obrácené [hash_set](../standard-library/hash-set-class.md) (umístění, `hash_set`které předcházelo první prvek v unreverse).

### <a name="remarks"></a>Poznámky

`crend`se používá s `hash_set` obráceným stejně [jako hash_set::end](#end) se používá s `hash_set`.

S vrácenou `crend`hodnotou `hash_set` aplikace nelze objekt změnit.

`crend`lze použít k testování, zda reverzní iterátor dosáhl `hash_set`konce svého .

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

## <a name="hash_setdifference_type"></a><a name="difference_type"></a>hash_set::difference_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Podepsaný typ celé číslo, který lze použít k reprezentaci počtu prvků hash_set v rozsahu mezi prvky, na které se iterátory upozorují.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Je `difference_type` typ vrácena při odečtení nebo zvýšení prostřednictvím iterátory kontejneru. Obvykle `difference_type` se používá k reprezentaci počtu prvků `first` `last`v rozsahu [ , `first` ) `last`mezi iterátory `first` a , zahrnuje prvek, na který se vztahuje, a rozsah prvků až do prvku, na který je však `last`nezahrnuto.

Všimněte `difference_type` si, že i když je k dispozici pro všechny iterátory, které splňují požadavky vstupní iterátor, který zahrnuje třídu obousměrné iterátory podporované reverzibilní kontejnery, jako je například set, odčítání mezi iterátory je podporován pouze náhodný přístup iterátory poskytované kontejneru náhodný přístup, jako je například vektor nebo deque.

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

## <a name="hash_setemplace"></a><a name="emplace"></a>hash_set::emplace

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vloží prvek vytvořený na místě do hash_set.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota prvku, který má být [hash_set](../standard-library/hash-set-class.md) vložen do `hash_set` hash_set pokud již obsahuje tento prvek nebo obecněji prvek, jehož klíč je ekvivalentní objednané.|

### <a name="return-value"></a>Návratová hodnota

Členská `emplace` funkce vrátí dvojici, jejíž **komponenta bool** vrátí **hodnotu true,** pokud byla vložení značka a **false,** pokud `hash_set` již obsahoval prvek, jehož klíč měl v řazení ekvivalentní hodnotu a jehož komponenta iterátoru vrací adresu, kde byl vložen nový prvek nebo kde byl již umístěn.

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

## <a name="hash_setemplace_hint"></a><a name="emplace_hint"></a>hash_set::emplace_hint

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vloží prvek vytvořený na místě do hash_set.

```cpp
template <class ValTy>
iterator emplace(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota prvku, který má být [hash_set](../standard-library/hash-set-class.md) vložen do `hash_set` hash_set pokud již obsahuje tento prvek nebo obecněji prvek, jehož klíč je ekvivalentní objednané.|
|*_Where*|Místo zahájení vyhledání správného bodu vložení. (Vložení může dojít v amortizované konstantní čas, namísto logaritmického času, pokud kurzor bezprostředně následuje *_Where*.)|

### <a name="return-value"></a>Návratová hodnota

Členská funkce [hash_set::emplace](#emplace) vrátí iterátor, který odkazuje na `hash_set`pozici, kde byl vložen nový prvek do , nebo kde je umístěn existující prvek s ekvivalentním řazením.

### <a name="remarks"></a>Poznámky

Vložení může dojít v amortizované konstantní čas, namísto logaritmického času, pokud kurzor bezprostředně následuje *_Where*.

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

## <a name="hash_setempty"></a><a name="empty"></a>hash_set::prázdné

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Testuje, zda je hash_set prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je hash_set prázdná; **false,** pokud hash_set není prázdný.

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

## <a name="hash_setend"></a><a name="end"></a>hash_set::konec

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí iterátor, který řeší umístění, které následuje poslední prvek v hash_set.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který řeší umístění, které následuje poslední prvek v hash_set. Pokud je hash_set prázdný, pak hash_set::end == hash_set::begin.

### <a name="remarks"></a>Poznámky

`end`se používá k testování, zda iterátor dosáhl konce svého hash_set. Hodnota vrácená `end` by neměla být odkazována.

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

## <a name="hash_setequal_range"></a><a name="equal_range"></a>hash_set::equal_range

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí dvojici iterátorů, respektive k prvnímu prvku v sadě hash s klíčem, který se rovná zadanému klíči, a prvnímu prvku v sadě hash s klíčem, který je větší než klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z hash_set prohledáván.

### <a name="return-value"></a>Návratová hodnota

Dvojice iterátorů, kde první je [lower_bound](../standard-library/set-class.md#lower_bound) klíče a druhá je [upper_bound](../standard-library/set-class.md#upper_bound) klíče.

Pro přístup k prvnímu iterátoru páru pr vráceného členovou funkcí použijte `pr`. **a**dereferencovat nižší mez iterátoru, použijte \*( `pr`. **první**). Chcete-li získat přístup k druhému iterátoru `pr` `pr`dvojice vrácené členovou funkcí, použijte . **druhé**, a pro dereferenci horní mez iterátoru, použijte \*( `pr`. **za druhé**).

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

## <a name="hash_seterase"></a><a name="erase"></a>hash_set::vymazat

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Odebere prvek nebo rozsah prvků v hash_set ze zadaných pozic nebo odebere prvky, které odpovídají zadanému klíči.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where*\
Umístění prvku, který má být odebrán z hash_set.

*První*\
Pozice prvního prvku odstraněného z hash_set.

*Poslední*\
Umístěte těsně za poslední prvek odstraněný z hash_set.

*Klíč*\
Klíč prvků, které mají být odebrány z hash_set.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který označuje první prvek zbývající za všechny prvky odebrány nebo ukazatel na konec hash_set pokud žádný takový prvek neexistuje. Pro třetí členskou funkci počet prvků, které byly odebrány z hash_set.

### <a name="remarks"></a>Poznámky

Členské funkce nikdy vyvolat výjimku.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_set::erase členské funkce.

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

## <a name="hash_setfind"></a><a name="find"></a>hash_set::najít

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí iterátor adresování umístění prvku v hash_set, který má klíč ekvivalentní zadaný klíč.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z hash_set prohledáván.

### <a name="return-value"></a>Návratová hodnota

Nebo `iterator` `const_iterator` který řeší umístění prvku ekvivalentní zadaný klíč nebo který řeší umístění, které následuje poslední prvek v hash_set pokud není nalezena žádná shoda pro klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který řeší prvek v hash_set `equivalent` jehož klíč řazení je klíč argumentu pod binární predikát, který indukuje řazení na základě méně než vztah srovnatelnosti.

Pokud `find` je vrácená hodnota `const_iterator`přiřazena aplikaci , nelze objekt hash_set změnit. Pokud `find` je vrácená hodnota `iterator`přiřazena aplikaci , lze změnit objekt hash_set.

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

## <a name="hash_setget_allocator"></a><a name="get_allocator"></a>hash_set::get_allocator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí kopii objektu alokátoru použitého k vytvoření hash_set.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný hash_set ke správě paměti, což je parametr šablony *Alokátor*.

Další informace o *alokátoru*naleznete v části Poznámky v tématu [hash_set třída.](../standard-library/hash-set-class.md)

### <a name="remarks"></a>Poznámky

Alokátory pro třídu hash_set určují, jak třída spravuje úložiště. Výchozí alokátory dodávané s třídami kontejneru standardní knihovny jazyka C++ jsou dostatečné pro většinu potřeb programování. Psaní a používání vlastní třídy přidělování je pokročilé téma jazyka C++.

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

## <a name="hash_sethash_set"></a><a name="hash_set"></a>hash_set::hash_set

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Konstrukce, `hash_set` který je prázdný nebo který je kopií celé `hash_set`nebo části některé jiné .

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
|*Al*|Třída alokátoru úložiště, která `hash_set` má být použita `Allocator`pro tento objekt, který je ve výchozím nastavení .|
|*Comp*|Funkce porovnání typu `const Traits` použitého k seřizování prvků v rozhraní `hash_set`, které jsou ve výchozím nastavení . `hash_compare`|
|*Právo*|Z `hash_set` nichž je `hash_set` konstruována kopie.|
|*První*|Umístění prvního prvku v rozsahu prvků, které mají být zkopírovány.|
|*Poslední*|Pozice první prvek mimo rozsah prvků, které mají být zkopírovány.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory uložit typ objektu alokátoru, který `hash_set` spravuje úložiště paměti pro a které mohou být později vráceny voláním [hash_set::get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují své hash_sets.

Všechny konstruktory uložit objekt `Traits` funkce typu, který se používá k `hash_set` vytvoření pořadí mezi klíči a které mohou být později vráceny voláním [hash_set::key_comp](#key_comp). Další informace `Traits` naleznete v tématu [hash_set třída.](../standard-library/hash-set-class.md)

První konstruktor vytvoří prázdnou počáteční `hash_set` Druhý určuje typ `Comp`funkce porovnání ( ) která má být použita při vytváření pořadí prvků a `Al`třetí explicitně určuje typ alokátoru ( ) který má být použit. Klíčové slovo `explicit` potlačí některé druhy automatického převodu typu.

Čtvrtý a pátý konstruktory zadat `hash_set` `Right`kopii .

Poslední šestý, sedmý a osmý konstruktory použít initializer_list pro prvky.

Poslední konstruktory zkopírují `First`rozsah `Last`[ `hash_set` , ) s rostoucí explicitní při určování typu funkce porovnání vlastností třídy a alokátoru.

Osmý konstruktor přesune `hash_set` `Right`.

Skutečné pořadí prvků v `hash_set` kontejneru závisí na funkci hash, funkci řazení a aktuální velikost tabulky hash a obecně nelze předpovědět, jak by to mohlo s kontejnerem set, kde bylo určeno pouze funkcí řazení.

## <a name="hash_setinsert"></a><a name="insert"></a>hash_set::vložit

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vloží prvek nebo rozsah prvků do `hash_set`.

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
|*Val*|Hodnota prvku, který má být `hash_set` vložen `hash_set` do, pokud již obsahuje tento prvek nebo obecněji prvek, jehož klíč je ekvivalentní objednané.|
|*Kde*|Místo zahájení vyhledání správného bodu vložení. (Vložení může dojít v amortizované konstantní čas, namísto logaritmického času, `_Where`pokud kurzor bezprostředně následuje .)|
|*První*|Pozice prvního prvku, který má `hash_set`být zkopírován z .|
|*Poslední*|Pozice těsně za poslední prvek, který `hash_set`má být zkopírován z .|
|*Ilist*|Seznam initializer_list, ze kterého chcete kopírovat prvky.|

### <a name="return-value"></a>Návratová hodnota

První `insert` členská funkce vrátí dvojici, jejíž **komponenta bool** vrátí `hash_set` **hodnotu true,** pokud byla vložení značka a **false,** pokud již obsahoval prvek, jehož klíč měl v řazení ekvivalentní hodnotu a jehož komponenta iterátoru vrací adresu, kde byl vložen nový prvek nebo kde byl již umístěn.

Chcete-li získat přístup k součásti iterátoru `pr` `pr.first` dvojice vrácené touto `*(pr.first)`členovou funkcí, použijte ji a chcete ji odkázat, použijte . Chcete-li získat přístup k `pr` **bool** součásti `pr.second`dvojice vrácené touto členovou funkcí, použijte a chcete-li na něj odkazovat, použijte `*(pr.second)`.

Druhá `insert` členská funkce vrátí iterátor, který odkazuje na pozici, kde `hash_set`byl vložen nový prvek do .

### <a name="remarks"></a>Poznámky

Třetí členská funkce vloží prvky do initializer_list.

Třetí členská funkce vloží posloupnost `hash_set` hodnot prvků do každého prvku, který je adresován iterátorem v rozsahu [ `First`, `Last`) zadaného `hash_set`prvku .

## <a name="hash_setiterator"></a><a name="iterator"></a>hash_set::iterátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Poznámky

Typ `iterator` lze změnit hodnotu prvku.

### <a name="example"></a>Příklad

Příklad [začátku](#begin) naleznete v příkladu, jak `iterator`deklarovat a používat .

## <a name="hash_setkey_comp"></a><a name="key_comp"></a>hash_set::key_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Načte kopii objektu vlastností hash použitého k hodnotám klíče hash a klíče prvku pořadí v hash_set.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který hash_set používá k objednání jeho prvků, což je *parametr šablony Vlastnosti*.

Další informace o *vlastnostech* naleznete v tématu [hash_set class.](../standard-library/hash-set-class.md)

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členovou funkci:

`bool operator( const Key& _xVal, const Key& _yVal );`

který vrátí `_xVal` **hodnotu true,** pokud `_yVal` předchází, a není rovna v pořadí řazení.

Všimněte si, že [key_compare](#key_compare) i [value_compare](#value_compare) jsou synonyma pro *vlastnosti*parametru šablony . Oba typy jsou k dispozici pro třídy hash_set a hash_multiset, kde jsou identické, pro kompatibilitu s hash_map a hash_multimap třídy, kde jsou odlišné.

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

## <a name="hash_setkey_compare"></a><a name="key_compare"></a>hash_set::key_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení k určení relativní pořadí dvou prvků v hash_set.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare`je synonymem pro parametr znakové *vlastnosti*šablony .

Další informace o *vlastnostech* naleznete v tématu [hash_set class.](../standard-library/hash-set-class.md)

Všimněte `key_compare` si, že oba a [value_compare](#value_compare) jsou synonyma pro *vlastnosti*parametru šablony . Oba typy jsou k dispozici pro set a vícesetové třídy, kde jsou identické, pro kompatibilitu s map a multimap třídy, kde jsou odlišné.

### <a name="example"></a>Příklad

Příklad pro [key_comp](#key_comp) příklad, jak deklarovat a používat `key_compare`.

## <a name="hash_setkey_type"></a><a name="key_type"></a>hash_set::key_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Typ, který popisuje objekt uložený jako prvek hash_set v jeho kapacitě jako klíč řazení.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type`je synonymem pro parametr šablony *Klíč*.

Další informace o *klíči*naleznete v části Poznámky v tématu [hash_set třídy.](../standard-library/hash-set-class.md)

Všimněte `key_type` si, že oba a [value_type](#value_type) jsou synonyma pro parametr šablony *Key*. Oba typy jsou k dispozici pro třídy hash_set a hash_multiset, kde jsou identické, pro kompatibilitu s hash_map a hash_multimap třídy, kde jsou odlišné.

### <a name="example"></a>Příklad

Příklad [value_type](#value_type) naleznete v příkladu, jak `key_type`deklarovat a používat .

## <a name="hash_setlower_bound"></a><a name="lower_bound"></a>hash_set::lower_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí iterátor pro první prvek v hash_set s klíčem, který je roven nebo větší než zadaný klíč.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z hash_set prohledáván.

### <a name="return-value"></a>Návratová hodnota

Nebo `iterator` `const_iterator` který řeší umístění prvku v hash_set, že s klíčem, který je roven nebo větší než klíč argumentu nebo který řeší umístění, které následuje poslední prvek v hash_set pokud není nalezena žádná shoda pro klíč.

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

## <a name="hash_setmax_size"></a><a name="max_size"></a>hash_set::max_size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí maximální délku hash_set.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka hash_set.

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

## <a name="hash_setoperator"></a><a name="op_eq"></a>hash_set::operátor=

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Nahradí prvky hash_set kopií jiného hash_set.

```cpp
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Právo*|[Hash_set](../standard-library/hash-set-class.md) zkopírován `hash_set`do .|

### <a name="remarks"></a>Poznámky

Po vymazání všech existujících `hash_set` `operator=` prvků v aplikaci zkopíruje `hash_set`nebo přesune obsah *vpravo* do .

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

## <a name="hash_setpointer"></a><a name="pointer"></a>hash_set::pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Typ, který poskytuje ukazatel na prvek v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze změnit hodnotu prvku.

Ve většině případů [iterátor](#iterator) by měl být použit pro přístup k prvkům v hash_set objektu.

## <a name="hash_setrbegin"></a><a name="rbegin"></a>hash_set::začátek

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí iterátor adresující první prvek v obráceném hash_set.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresování první prvek v obrácené hash_set nebo adresování, co bylo poslední prvek v hash_set.

### <a name="remarks"></a>Poznámky

`rbegin`se používá s obráceným hash_set stejně jako [začátek](#begin) se používá s hash_set.

Pokud `rbegin` je vrácená hodnota `const_reverse_iterator`přiřazena aplikaci , nelze hash_set objekt změnit. Pokud `rbegin` je vrácená hodnota `reverse_iterator`přiřazena k , lze změnit objekt hash_set.

`rbegin`lze itetovat přes hash_set dozadu.

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
   // through a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // through a hash_set in a reverse order
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

## <a name="hash_setreference"></a><a name="reference"></a>hash_set::odkaz

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Typ, který poskytuje odkaz na prvek uložený v hash_set.

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

## <a name="hash_setrend"></a><a name="rend"></a>hash_set::rend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí iterátor, který řeší umístění, které následuje poslední prvek v obráceném hash_set.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor, který řeší umístění, které následuje poslední prvek v obráceném hash_set (umístění, které předcházelo prvnímu prvku v neobrácenéhash_set).

### <a name="remarks"></a>Poznámky

`rend`se používá s obráceným hash_set [stejně](#end) jako konec se používá s hash_set.

Pokud `rend` je vrácená hodnota `const_reverse_iterator`přiřazena aplikaci , nelze hash_set objekt změnit. Pokud `rend` je vrácená hodnota `reverse_iterator`přiřazena k , lze změnit objekt hash_set. Hodnota vrácená `rend` by neměla být odkazována.

`rend`lze použít k testování, zda reverzní iterátor dosáhl konce svého hash_set.

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
   // through a hash_set in a forward order
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

## <a name="hash_setreverse_iterator"></a><a name="reverse_iterator"></a>hash_set::reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iterátu přes hash_set v opačném směru.

### <a name="example"></a>Příklad

Příklad pro [rbegin](#rbegin) naleznete v příkladu, `reverse_iterator`jak deklarovat a používat .

## <a name="hash_setsize"></a><a name="size"></a>hash_set::velikost

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí počet prvků v hash_set.

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

## <a name="hash_setsize_type"></a><a name="size_type"></a>hash_set::size_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Nepodepsaný podnosný typ, který může představovat počet prvků v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Příklad [velikosti](#size) naleznete v příkladu, jak deklarovat a používat`size_type`

## <a name="hash_setswap"></a><a name="swap"></a>hash_set::swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vyměňuje prvky dvou hash_sets.

```cpp
void swap(hash_set& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Argument hash_set poskytuje prvky, které mají být vyměněny za cílovou hash_set.

### <a name="remarks"></a>Poznámky

Členská funkce zruší platnost žádné odkazy, ukazatele nebo iterátory, které označují prvky ve dvou hash_sets jejichž prvky jsou vyměňovány.

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

## <a name="hash_setupper_bound"></a><a name="upper_bound"></a>hash_set::upper_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vrátí iterátor prvnímu prvku v hash_set který s klíčem, který je větší než zadaný klíč.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z hash_set prohledáván.

### <a name="return-value"></a>Návratová hodnota

Nebo `iterator` `const_iterator` který řeší umístění prvku v hash_set, který s klíčem, který je roven nebo větší než klíč argumentu, nebo který řeší umístění, které následuje poslední prvek v hash_set pokud pro klíč není nalezena žádná shoda.

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

## <a name="hash_setvalue_comp"></a><a name="value_comp"></a>hash_set::value_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Načte kopii objektu porovnání použitého k pořadí hodnot prvků v hash_set.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který hash_set používá k objednání jeho prvků, což je parametr šablony *Porovnat*.

Další informace o *porovnání*naleznete v části Poznámky v tématu [hash_set třída.](../standard-library/hash-set-class.md)

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členovou funkci:

`bool operator( const Key& _xVal, const Key& _yVal );`

který vrátí `_xVal` **hodnotu true,** pokud `_yVal` předchází, a není rovna v pořadí řazení.

Všimněte si, že [value_compare](../standard-library/set-class.md#value_compare) i [key_compare](../standard-library/set-class.md#key_compare) jsou synonyma pro parametr šablony *Porovnat*. Oba typy jsou k dispozici pro třídy hash_set a hash_multiset, kde jsou identické, pro kompatibilitu s hash_map a hash_multimap třídy, kde jsou odlišné.

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

## <a name="hash_setvalue_compare"></a><a name="value_compare"></a>hash_set::value_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Typ, který poskytuje dva objekty funkce, binární predikát třídy porovnat, které lze porovnat dva elementové hodnoty hash_set k určení jejich relativní pořadí a unární predikát, který hodnoty zatřídění prvky.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Poznámky

`value_compare`je synonymem pro parametr znakové *vlastnosti*šablony .

Další informace o *vlastnostech* naleznete v tématu [hash_set class.](../standard-library/hash-set-class.md)

Všimněte si, `value_compare` že oba [key_compare](#key_compare) a jsou synonyma pro *vlastnosti*parametru šablony . Oba typy jsou k dispozici pro třídy hash_set a hash_multiset, kde jsou identické, pro kompatibilitu s hash_map a hash_multimap třídy, kde jsou odlišné.

### <a name="example"></a>Příklad

Příklad pro [value_comp](#value_comp) příklad, jak deklarovat a používat `value_compare`.

## <a name="hash_setvalue_type"></a><a name="value_type"></a>hash_set::value_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Typ, který popisuje objekt uložený jako prvek hash_set v jeho kapacitě jako hodnotu.

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

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
