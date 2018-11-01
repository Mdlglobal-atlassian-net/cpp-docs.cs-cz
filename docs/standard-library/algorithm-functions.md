---
title: '&lt;algoritmus&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- algorithm/std::adjacent_find
- algorithm/std::all_of
- algorithm/std::any_of
- algorithm/std::binary_search
- algorithm/std::copy
- algorithm/std::copy_backward
- algorithm/std::copy_if
- algorithm/std::copy_n
- algorithm/std::equal
- algorithm/std::equal_range
- algorithm/std::fill
- algorithm/std::fill_n
- algorithm/std::find
- algorithm/std::find_end
- algorithm/std::find_first_of
- algorithm/std::find_if
- algorithm/std::find_if_not
- algorithm/std::for_each
- algorithm/std::generate
- algorithm/std::generate_n
- algorithm/std::includes
- algorithm/std::inplace_merge
- algorithm/std::is_heap
- algorithm/std::is_heap_until
- algorithm/std::is_partitioned
- algorithm/std::is_permutation
- algorithm/std::is_sorted
- algorithm/std::is_sorted_until
- algorithm/std::iter_swap
- algorithm/std::lexicographical_compare
- algorithm/std::lower_bound
- algorithm/std::make_heap
- algorithm/std::max
- algorithm/std::max_element
- algorithm/std::merge
- algorithm/std::min
- algorithm/std::minmax
- algorithm/std::minmax_element
- algorithm/std::min_element
- algorithm/std::mismatch
- algorithm/std::move
- algorithm/std::move_backward
- algorithm/std::next_permutation
- algorithm/std::none_of
- algorithm/std::nth_element
- algorithm/std::partial_sort
- algorithm/std::partial_sort_copy
- algorithm/std::partition
- algorithm/std::partition_point
- algorithm/std::pop_heap
- algorithm/std::prev_permutation
- algorithm/std::push_heap
- algorithm/std::random_shuffle
- algorithm/std::remove
- algorithm/std::remove_copy
- algorithm/std::remove_copy_if
- algorithm/std::remove_if
- algorithm/std::replace
- algorithm/std::replace_copy
- algorithm/std::replace_copy_if
- algorithm/std::replace_if
- algorithm/std::reverse
- algorithm/std::reverse_copy
- algorithm/std::rotate
- algorithm/std::rotate_copy
- algorithm/std::search
- algorithm/std::search_n
- algorithm/std::set_difference
- algorithm/std::set_intersection
- algorithm/std::set_symmetric_difference
- algorithm/std::set_union
- algorithm/std::shuffle
- algorithm/std::sort
- algorithm/std::sort_heap
- algorithm/std::stable_partition
- algorithm/std::stable_sort
- algorithm/std::swap_ranges
- algorithm/std::transform
- algorithm/std::unique
- algorithm/std::unique_copy
- algorithm/std::upper_bound
- xutility/std::copy
- xutility/std::copy_backward
- xutility/std::copy_n
- xutility/std::count
- xutility/std::equal
- xutility/std::fill
- xutility/std::fill_n
- xutility/std::find
- xutility/std::is_permutation
- xutility/std::lexicographical_compare
- xutility/std::move
- xutility/std::move_backward
- xutility/std::reverse
- xutility/std::rotate
- algorithm/std::count_if
- algorithm/std::partition_copy
- algorithm/std::swap
ms.assetid: c10b0c65-410c-4c83-abf8-8b7f61bba8d0
helpviewer_keywords:
- std::adjacent_find [C++]
- std::all_of [C++]
- std::any_of [C++]
- std::binary_search [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_if [C++]
- std::copy_n [C++]
- std::equal [C++]
- std::equal_range [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::find_end [C++]
- std::find_first_of [C++]
- std::find_if [C++]
- std::find_if_not [C++]
- std::for_each [C++]
- std::generate [C++]
- std::generate_n [C++]
- std::includes [C++]
- std::inplace_merge [C++]
- std::is_heap [C++]
- std::is_heap_until [C++]
- std::is_partitioned [C++]
- std::is_permutation [C++]
- std::is_sorted [C++]
- std::is_sorted_until [C++]
- std::iter_swap [C++]
- std::lexicographical_compare [C++]
- std::lower_bound [C++]
- std::make_heap [C++]
- std::max [C++]
- std::max_element [C++]
- std::merge [C++]
- std::min [C++]
- std::minmax [C++]
- std::minmax_element [C++]
- std::min_element [C++]
- std::mismatch [C++]
- std::move [C++]
- std::move_backward [C++]
- std::next_permutation [C++]
- std::none_of [C++]
- std::nth_element [C++]
- std::partial_sort [C++]
- std::partial_sort_copy [C++]
- std::partition [C++]
- std::partition_point [C++]
- std::pop_heap [C++]
- std::prev_permutation [C++]
- std::push_heap [C++]
- std::random_shuffle [C++]
- std::remove [C++]
- std::remove_copy [C++]
- std::remove_copy_if [C++]
- std::remove_if [C++]
- std::replace [C++]
- std::replace_copy [C++]
- std::replace_copy_if [C++]
- std::replace_if [C++]
- std::reverse [C++]
- std::reverse_copy [C++]
- std::rotate [C++]
- std::rotate_copy [C++]
- std::search [C++]
- std::search_n [C++]
- std::set_difference [C++]
- std::set_intersection [C++]
- std::set_symmetric_difference [C++]
- std::set_union [C++]
- std::shuffle [C++]
- std::sort [C++]
- std::sort_heap [C++]
- std::stable_partition [C++]
- std::stable_sort [C++]
- std::swap_ranges [C++]
- std::transform [C++]
- std::unique [C++]
- std::unique_copy [C++]
- std::upper_bound [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_n [C++]
- std::count [C++]
- std::equal [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::is_permutation [C++]
- std::lexicographical_compare [C++]
- std::move [C++]
- std::move_backward [C++]
- std::reverse [C++]
- std::rotate [C++]
- std::count_if [C++]
- std::partition_copy [C++]
- std::swap [C++]
ms.openlocfilehash: fb928edf603a5eec2acf1ac53bcd73360a876735
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630958"
---
# <a name="ltalgorithmgt-functions"></a>&lt;algoritmus&gt; funkce

||||
|-|-|-|
|[Přesunutí](#alg_move)|[adjacent_find](#adjacent_find)|[all_of](#all_of)|
|[any_of](#any_of)|[binary_search](#binary_search)|[kopírování](#copy)|
|[copy_backward](#copy_backward)|[copy_if](#copy_if)|[copy_n](#copy_n)|
|[Počet](#count)|[count_if](#count_if)|[rovno](#equal)|
|[equal_range](#equal_range)|[Výplň](#fill)|[fill_n](#fill_n)|
|[Najít](#find)|[find_end –](#find_end)|[find_first_of](#find_first_of)|
|[find_if](#find_if)|[find_if_not](#find_if_not)|[for_each](#for_each)|
|[Generovat](#generate)|[generate_n](#generate_n)|[zahrnuje](#includes)|
|[inplace_merge –](#inplace_merge)|[is_heap](#is_heap)|[is_heap_until –](#is_heap_until)|
|[is_partitioned](#is_partitioned)|[is_permutation](#is_permutation)|[is_sorted](#is_sorted)|
|[is_sorted_until –](#is_sorted_until)|[iter_swap](#iter_swap)|[lexicographical_compare](#lexicographical_compare)|
|[lower_bound –](#lower_bound)|[make_heap](#make_heap)|[max](#max)|
|[max_element](#max_element)|[sloučení](#merge)|[min](#min)|
|[min_element](#min_element)|[minmax](#minmax)|[minmax_element](#minmax_element)|
|[Neshoda](#mismatch)|[move_backward](#move_backward)|[next_permutation](#next_permutation)|
|[none_of](#none_of)|[nth_element –](#nth_element)|[partial_sort](#partial_sort)|
|[partial_sort_copy](#partial_sort_copy)|[oddíl](#partition)|[partition_copy –](#partition_copy)|
|[partition_point](#partition_point)|[pop_heap –](#pop_heap)|[prev_permutation](#prev_permutation)|
|[push_heap –](#push_heap)|[random_shuffle](#random_shuffle)|[remove](#remove)|
|[remove_copy](#remove_copy)|[remove_copy_if](#remove_copy_if)|[remove_if](#remove_if)|
|[nahradit](#replace)|[replace_copy –](#replace_copy)|[replace_copy_if –](#replace_copy_if)|
|[replace_if –](#replace_if)|[reverzní](#reverse)|[reverse_copy –](#reverse_copy)|
|[Otočit o](#rotate)|[rotate_copy –](#rotate_copy)|[search](#search)|
|[search_n](#search_n)|[set_difference](#set_difference)|[set_intersection](#set_intersection)|
|[set_symmetric_difference](#set_symmetric_difference)|[set_union](#set_union)|[Řazení](#sort)|
|[sort_heap –](#sort_heap)|[stable_partition –](#stable_partition)|[stable_sort](#stable_sort)|
|[Shuffle](#shuffle)|[Prohození](#swap)|[swap_ranges](#swap_ranges)|
|[Transformace](#transform)|[unique](#unique)|[unique_copy](#unique_copy)|
|[upper_bound –](#upper_bound)|

## <a name="adjacent_find"></a>  adjacent_find –

Vyhledá dva sousedící prvky, které jsou buď rovny, nebo splňují zadanou podmínku.

```cpp
template<class ForwardIterator>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator , class BinaryPredicate>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu pro hledání.

*poslední*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v oblasti pro hledání.

*Kompozice*<br/>
Binární predikát, který poskytuje podmínku, která má být splněno hodnoty sousedících prvků v prohledávaný rozsah.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor na první prvek dvojice sousední, které jsou buď rovny k sobě navzájem (v první verzi) nebo splňujících tuto podmínku Dal binárním predikátem (v druhém verzi), za předpokladu, že najde dvojici prvků. V opačném případě iterátorem ukazujícím *poslední* je vrácena.

### <a name="remarks"></a>Poznámky

`adjacent_find` Algoritmus je algoritmus nonmutating pořadí. Rozsah pro hledání musí být platný; všechny odkazy musí být možné zrušit referenci a poslední pozice je dosažitelná z první pomocí přírůstků. Čas složitost algoritmu je lineární počet elementů obsažených v rozsahu.

`operator==` Používá k určení shody mezi elementy musí uložit vztahu ekvivalence mezí jejími operandy.

### <a name="example"></a>Příklad

```cpp
// alg_adj_fnd.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

// Returns whether second element is twice the first
bool twice (int elem1, int elem2 )
{
   return elem1 * 2 == elem2;
}

int main()
{
   using namespace std;
   list <int> L;
   list <int>::iterator Iter;
   list <int>::iterator result1, result2;

   L.push_back( 50 );
   L.push_back( 40 );
   L.push_back( 10 );
   L.push_back( 20 );
   L.push_back( 20 );

   cout << "L = ( " ;
   for ( Iter = L.begin( ) ; Iter != L.end( ) ; Iter++ )
      cout << *Iter << " ";
   cout << ")" << endl;

   result1 = adjacent_find( L.begin( ), L.end( ) );
   if ( result1 == L.end( ) )
      cout << "There are not two adjacent elements that are equal."
           << endl;
   else
      cout << "There are two adjacent elements that are equal."
           << "\n They have a value of "
           <<  *( result1 ) << "." << endl;

   result2 = adjacent_find( L.begin( ), L.end( ), twice );
   if ( result2 == L.end( ) )
      cout << "There are not two adjacent elements where the "
           << " second is twice the first." << endl;
   else
      cout << "There are two adjacent elements where "
           << "the second is twice the first."
           << "\n They have values of " << *(result2++);
      cout << " & " << *result2 << "." << endl;
}
```

```Output
L = ( 50 40 10 20 20 )
There are two adjacent elements that are equal.
They have a value of 20.
There are two adjacent elements where the second is twice the first.
They have values of 10 & 20.
```

## <a name="all_of"></a>  all_of

Vrátí **true** když podmínka je k dispozici u každého prvku v zadaném rozsahu.

```cpp
template<class InputIterator, class Predicate>
bool all_of(
    InputIterator first,
    InputIterator last,
    BinaryPredicatecomp);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor, který označuje, kde začít kontrolují určitou podmínku. Iterátoru označuje, kde celou řadu prvků spustí.

*poslední*<br/>
Vstupní iterátor, který označuje konec rozsahu prvků, které se kontrolují určitou podmínku.

*Kompozice*<br/>
Podmínka pro testování. Toto je objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být uspokojen prvkem kontroluje. Predikát přijímá jeden argument a vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** Pokud podmínka zjistí na každý prvek v zadaném rozsahu a **false** Pokud podmínka není zjištěna aspoň jednou.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí **true** pouze tehdy, pokud pro každou `N` v rozsahu `[0,Last - first)`, predikát `comp(*(_First + N))` je **true**.

## <a name="any_of"></a>  any_of

Vrátí **true** Pokud je alespoň jednou v zadaném rozsahu prvků přítomna podmínka.

```cpp
template<class InputIterator, class UnaryPredicate>
bool any_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate comp);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor, který označuje, kde zahájí kontrolu rozsahu prvků podmínku.

*poslední*<br/>
Vstupní iterátor, který označuje konec rozsahu prvků, které se kontrolují určitou podmínku.

*Kompozice*<br/>
Podmínka pro testování. To poskytuje objekt funkce predikátu definovaný uživatelem. Predikát definuje podmínku, která má vyhovět pomocí elementu testován. Predikát přijímá jeden argument a vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** Pokud podmínka zjistí alespoň jednou v zadaném rozsahu **false** Pokud podmínka se nikdy detekuje.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí **true** pouze tehdy, pokud u některých `N` v rozsahu

`[0, last - first)`, predikát `comp(*(first + N))` má hodnotu true.

## <a name="binary_search"></a>  binary_search –

Ověřuje, zda v seřazeném rozsahu existuje prvek, který je roven zadané hodnotě nebo je jí ekvivalentní ve smyslu určeném binárním predikátem.

```cpp
template<class ForwardIterator, class Type>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator,  class Type,  class BinaryPredicate>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate comp);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu pro hledání.

*poslední*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v oblasti pro hledání.

*value*<br/>
Hodnota požadovaná k porovnání s hodnotou elementu nebo která musí splňovat podmínku s hodnotou elementu zadanou binárním predikátem.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je nalezen element v rozsahu, který je rovna nebo ekvivalentní se zadanou hodnotou; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Odkazovaný seřazený zdrojový rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci jednoho pořadí, musí být poslední pozice dosažitelná z první pomocí přírůstků.

Seřazený rozsah musí každý uspořádat podmínkou pro použití `binary_search` algoritmus ve stejném pořadí jako se používá algoritmus k seřazení kombinovaných rozsahů.

Zdrojové rozsahy nejsou upravil `binary_search`.

Typy hodnot iterátorů předání musí být menší – než srovnatelná s hodnotou příkazu, tak aby byly uvedeny dva elementy, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý) nebo že jeden je menší než ten druhý. Výsledkem je řazení mezi neekvivalentními prvky

Složitost algoritmu je logaritmický pro iterátory s náhodným přístupem a v opačném případě lineární, přičemž počet kroků je přímo úměrný (`last` - `first`).

### <a name="example"></a>Příklad

```cpp
// alg_bin_srch.cpp
// compile with: /EHsc
#include <list>
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    list <int> List1;

    List1.push_back( 50 );
    List1.push_back( 10 );
    List1.push_back( 30 );
    List1.push_back( 20 );
    List1.push_back( 25 );
    List1.push_back( 5 );

    List1.sort();

    cout << "List1 = ( " ;
    for ( auto Iter : List1 )
        cout << Iter << " ";
    cout << ")" << endl;

    // default binary search for 10
    if ( binary_search(List1.begin(), List1.end(), 10) )
        cout << "There is an element in list List1 with a value equal to 10."
        << endl;
    else
        cout << "There is no element in list List1 with a value equal to 10."
        << endl;

    // a binary_search under the binary predicate greater
    List1.sort(greater<int>());
    if ( binary_search(List1.begin(), List1.end(), 10, greater<int>()) )
        cout << "There is an element in list List1 with a value greater than 10 "
        << "under greater than." << endl;
    else
        cout << "No element in list List1 with a value greater than 10 "
        << "under greater than." << endl;

    // a binary_search under the user-defined binary predicate mod_lesser
    vector<int> v1;

    for ( auto i = -2; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    sort(v1.begin(), v1.end(), mod_lesser);

    cout << "Ordered using mod_lesser, vector v1 = ( " ;
    for ( auto Iter : v1 )
        cout << Iter << " ";
    cout << ")" << endl;

    if ( binary_search(v1.begin(), v1.end(), -3, mod_lesser) )
        cout << "There is an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
    else
        cout << "There is not an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
}
```

## <a name="copy"></a>  kopírování

Přiřadí hodnoty prvků ze zdrojového rozsahu do cílového rozsahu a provede iterace přes zdrojové sekvence prvků a přiřadí je novým pozicím směrem dopředu.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator copy(
    InputIterator first,
    InputIterator last,
    OutputIterator destBeg);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku ve zdrojové oblasti.

*poslední*<br/>
Vstupní iterátor adresující pozici, která je jedno místo za posledním prvkem ve zdrojové oblasti.

*destBeg*<br/>
Výstupní iterace adresující pozici prvního prvku v cílové oblasti.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterace adresující pozici, která je jedno místo za posledním prvkem v cílové oblasti, tedy, iterátor adresuje `result` + (*poslední* - *první*).

### <a name="remarks"></a>Poznámky

Zdrojová oblast musí být platná a v cíli musí být dostatek místa na pro všechny prvky, které jsou kopírovány.

Protože algoritmus kopíruje zdrojové prvky v pořadí od prvního prvku, cílová oblast se může překrývat se zdrojové oblasti *poslední* pozice zdrojové oblasti není obsažena v cílovém umístění rozsah. `copy` můžete použít k posunu prvků na levé straně, ale nikoli vpravo, pokud neexistuje žádné překrytí mezi zdrojovou a cílovou oblastí. Chcete-li posunout doprava libovolný počet pozic, použijte [copy_backward](../standard-library/algorithm-functions.md#copy_backward) algoritmus.

`copy` Algoritmus upravuje pouze hodnoty odkazované iterátory, přiřazuje nové hodnoty prvkům v cílové oblasti. Nelze ho použít k vytvoření nových prvků a nelze vložit prvky do prázdného zásobníku přímo.

### <a name="example"></a>Příklad

```cpp
// alg_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
      v1.push_back( 10 * i );

   int ii;
   for ( ii = 0 ; ii <= 10 ; ii++ )
      v2.push_back( 3 * ii );

   cout << "v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // To copy the first 3 elements of v1 into the middle of v2
   copy( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 4 );

   cout << "v2 with v1 insert = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // To shift the elements inserted into v2 two positions
   // to the left
   copy( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 2 );

   cout << "v2 with shifted insert = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;
}
```

```Output
v1 = ( 0 10 20 30 40 50 )
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )
v2 with shifted insert = ( 0 3 0 10 20 10 20 21 24 27 30 )
```

## <a name="copy_backward"></a>  copy_backward

Přiřadí hodnoty prvků ze zdrojového rozsahu do cílového rozsahu a provede iterace přes zdrojové sekvence prvků a přiřadí je novým pozicím směrem dozadu.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 copy_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Obousměrný iterátor, který adresuje umístění prvního prvku ve zdrojové oblasti.

*poslední*<br/>
Obousměrný iterátor, který adresuje umístění jedno místo za posledním prvkem ve zdrojové oblasti.

*destEnd*<br/>
Obousměrný iterátor, který adresuje umístění jedno místo za posledním prvkem v cílové oblasti.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterace adresující pozici, která je jedno místo za posledním prvkem v cílové oblasti, tedy, iterátor adresuje *destEnd* -(*poslední* - *první*).

### <a name="remarks"></a>Poznámky

Zdrojová oblast musí být platná a v cíli musí být dostatek místa na pro všechny prvky, které jsou kopírovány.

`copy_backward` Algoritmus vyžaduje přísnější požadavky než algoritmus kopírování. Vstupní i výstupní iterátory musí být obousměrné.

`copy_backward` a [move_backward](../standard-library/algorithm-functions.md#move_backward) algoritmy jsou jediné algoritmy standardní knihovny C++ vyznačením výstupní oblasti s iterátorem ukazujícím na konec cílové oblasti.

Protože algoritmus kopíruje zdrojové prvky v pořadí od posledního prvku, cílová oblast se může překrývat se zdrojové oblasti *první* pozice zdrojové oblasti není obsažena v cílovém umístění rozsah. `copy_backward` můžete použít k posunu prvků doprava, ale nikoli vlevo, pokud neexistuje žádné překrytí mezi zdrojovou a cílovou oblastí. Chcete-li posunout vlevo libovolný počet pozic, použijte [kopírování](../standard-library/algorithm-functions.md#copy) algoritmus.

`copy_backward` Algoritmus upravuje pouze hodnoty odkazované iterátory, přiřazuje nové hodnoty prvkům v cílové oblasti. Nelze ho použít k vytvoření nových prvků a nelze vložit prvky do prázdného zásobníku přímo.

### <a name="example"></a>Příklad

```cpp
// alg_copy_bkwd.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 5 ; ++i )
      v1.push_back( 10 * i );

   int ii;
   for ( ii = 0 ; ii <= 10 ; ++ii )
      v2.push_back( 3 * ii );

   cout << "v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; ++Iter1 )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // To copy_backward the first 3 elements of v1 into the middle of v2
   copy_backward( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 7 );

   cout << "v2 with v1 insert = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // To shift the elements inserted into v2 two positions
   // to the right
   copy_backward( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 9 );

   cout << "v2 with shifted insert = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
      cout << *Iter2 << " ";
   cout << ")" << endl;
}
```

## <a name="copy_if"></a>  copy_if

V rozsahu prvků, zkopíruje prvky, které jsou **true** pro zadanou podmínku.

```cpp
template<class InputIterator, class OutputIterator, class BinaryPredicate>
OutputIterator copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator dest,
    Predicate pred);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor, který označuje začátek rozsahu ke kontrole stavu.

*poslední*<br/>
Vstupní iterátor, který označuje konec rozsahu.

*cíl*<br/>
Výstupní iterátor, který určuje cíl pro zkopírované elementy.

*_Pred*<br/>
Podmínka, proti kterému je testován každý prvek v rozsahu. Tato podmínka poskytuje objekt funkce predikátu definovaný uživatelem. Predikát přijímá jeden argument a vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor, který se rovná *dest* hodnota zvýšena jednou pro každý prvek, který splňuje podmínku. Jinými slovy, návratová hodnota minus *dest* se rovná počtu zkopírované elementy.

### <a name="remarks"></a>Poznámky

Funkce šablony vyhodnocuje

`if (pred(*_First + N)) * dest++ = *(_First + N))`

jednou pro každé `N` v rozsahu `[0, last - first)`, pro přísné zvýšení hodnot `N` počínaje nejnižší hodnotou. Pokud *dest* a *první* určují oblasti úložiště, *dest* nesmí být v rozsahu `[ first, last )`.

## <a name="copy_n"></a>  copy_n

Zkopíruje zadaný počet prvků.

```cpp
template<class InputIterator, class Size, class OutputIterator>
OutputIterator copy_n(
    InputIterator first,
    Size count,
    OutputIterator dest);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor, který určuje, kam chcete kopírovat prvky z.

*Počet*<br/>
Typ celého čísla se znaménkem nebo bez znaménka určující počet prvků ke zkopírování.

*cíl*<br/>
Výstupní iterátor, který označuje, kde pro kopírování prvků do.

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor výstupu, kde prvky byly zkopírovány do. Je stejný jako vrácené hodnoty třetí parametr *dest*.

### <a name="remarks"></a>Poznámky

Funkce šablony vyhodnocuje `*(dest + N) = *(first + N))` jednou pro každé `N` v rozsahu `[0, count)`, pro přísné zvýšení hodnot `N` počínaje nejnižší hodnotou. Potom vrátí `dest + N`. Pokud *dest* a *první* určují oblasti úložiště, *dest* nesmí být v rozsahu `[first, last)`.

## <a name="count"></a>  Počet

Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané hodnotě.

```cpp
template<class InputIterator, class Type>
typename iterator_traits<InputIterator>::difference_type count(
    InputIterator first,
    InputIterator last,
    const Type& val);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor adresující pozici prvního prvku v rozsahu Procházet.

*poslední*<br/>
Vstupní iterátor adresuje umístění jedno místo za posledním prvkem v rozsahu Procházet.

*Val*<br/>
Hodnota prvků, které se mají spočítat.

### <a name="return-value"></a>Návratová hodnota

Typ rozdílu `InputIterator` , která vrátí počet prvků v rozsahu [ *první*, *poslední* ), které mají hodnotu *val*.

### <a name="remarks"></a>Poznámky

`operator==` Používá k určení shody mezi prvkem a zadaná hodnota musí uložit vztahu ekvivalence mezí jejími operandy.

Tento algoritmus je zobecněný počet prvků, které splňují všechny predikátu pomocí funkce šablony [count_if](../standard-library/algorithm-functions.md#count_if).

### <a name="example"></a>Příklad

```cpp
// alg_count.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result;
    result = count(v1.begin(), v1.end(), 10);
    cout << "The number of 10s in v2 is: " << result << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of 10s in v2 is: 3.
```

## <a name="count_if"></a>  count_if –

Vrátí počet prvků v rozsahu, jehož hodnoty splňují zadanou podmínku.

```cpp
template<class InputIterator, class Predicate>
typename iterator_traits<InputIterator>::difference_type count_if(
    InputIterator first,
    InputIterator last,
    Predicate pred);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor adresující pozici prvního prvku v rozsahu pro hledání.

*poslední*<br/>
Vstupní iterátor adresuje umístění jedno místo za posledním prvkem v oblasti pro hledání.

*_Pred*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splnit, pokud je prvek, které se mají spočítat. Predikát přijímá jeden argument a vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které splňují podmínka uvedená v predikátu.

### <a name="remarks"></a>Poznámky

Tuto funkci je generalizace algoritmus [počet](../standard-library/algorithm-functions.md#count), nahrazení predikátu "se rovná určitou hodnotu" s predikátem, za jakékoli.

### <a name="example"></a>Příklad

```cpp
// alg_count_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater10(int value)
{
    return value > 10;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(), greater10);
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of elements in v1 greater than 10 is: 2.
```

## <a name="equal"></a>  rovno

Porovná dva rozsahy prvek po prvku pro zjištění rovnosti, nebo ekvivalentnosti ve smyslu určeném binárním predikátem.

Použití `std::equal` při porovnání prvků v kontejneru různých typů (například `vector` a `list`) nebo při porovnávání typů různých prvků, nebo pokud potřebujete porovnat dílčí rozsahy kontejnerů. Jinak použijte pro porovnání prvků stejného typu v rámci stejného typu kontejneru, bez členů `operator==` , který je k dispozici pro každý kontejner.

Použití duální rozsahy přetížení v C ++ 14 kódu, protože přetížení, která trvat jenom jeden iterátor pro druhého rozsahu nebudou zjištěny rozdíly, pokud druhá oblast je delší než první oblast a způsobí nedefinované chování, pokud je kratší druhého rozsahu než první oblast.

```cpp
template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1  First1,
    InputIterator1  Last1,
    InputIterator2  First2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1  First1,
    InputIterator1  Last1,
    InputIterator2  First2,
    BinaryPredicate Comp); // C++14

template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1  First1,
    InputIterator1  Last1,
    InputIterator2  First2,
    InputIterator2  Last2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1  First1,
    InputIterator1  Last1,
    InputIterator2  First2,
    InputIterator2  Last2,
    BinaryPredicate Comp);
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Vstupní iterátor adresující pozici prvního prvku v první oblasti, která má být testována.

*Příjmení1*<br/>
Vstupní iterátor adresuje umístění jedno místo za poslední prvek v první oblasti, která má být testována.

*first2*<br/>
Vstupní iterátor adresující pozici prvního prvku v druhé rozsahu má být testována.

*first2*<br/>
Vstupní iterátor adresuje umístění jedno místo za posledním prvkem v druhého rozsahu má být testována.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněny, pokud jsou dva prvky mají být provedeny, jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** pouze v případě tyto rozsahy následují stejné nebo ekvivalentní podle binárního predikátu srovnání prvek po prvku; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Rozsah pro hledání musí být platný; všech iterátorů musí být možné zrušit referenci a poslední pozice je dosažitelná z první pomocí přírůstků.

Pokud jsou dva rozsahy adres stejné délky, čas složitost algoritmu je lineární počet elementů obsažených v rozsahu. V opačném případě okamžitě vrátí funkce **false**.

Ani `operator==` ani predikátu definovaný uživatelem je potřeba uložit vztahu ekvivalence to symetrický, reflexivní a tranzitivní mezí jejími operandy.

### <a name="example"></a>Příklad

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector<int> v1 { 0, 5, 10, 15, 20, 25 };
    vector<int> v2 { 0, 5, 10, 15, 20, 25 };
    vector<int> v3 { 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50 };

    // Using range-and-a-half equal:
    bool b = equal(v1.begin(), v1.end(), v2.begin());
    cout << "v1 and v2 are equal: "
       << b << endl; // true, as expected

    b = equal(v1.begin(), v1.end(), v3.begin());
    cout << "v1 and v3 are equal: "
       << b << endl; // true, surprisingly

    // Using dual-range equal:
    b = equal(v1.begin(), v1.end(), v3.begin(), v3.end());
    cout << "v1 and v3 are equal with dual-range overload: "
       << b << endl; // false

    return 0;
}

```

## <a name="equal_range"></a>  equal_range –

Zadaný seřazeném rozsahu nalezne Podrozsah, ve kterém jsou elementy ekvivalentní dané hodnotě.

```cpp
template<class ForwardIterator, class Type>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& val);

template<class ForwardIterator, class Type, class Predicate>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& val,
    Predicate comp);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu pro hledání.

*poslední*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v oblasti pro hledání.

*Val*<br/>
Hodnota prohledávána v rozsahu příkazu.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný.

### <a name="return-value"></a>Návratová hodnota

Pár dopředných iterátorů, které určují Podrozsah obsažený v oblasti hledání, ve které jsou všechny prvky ekvivalentní *val* ve smyslu definovaném použitým binárním predikátem (buď *comp* nebo výchozí, méně-než).

Pokud žádné prvky v rozsahu jsou rovnocenné *val*, vrácený pár předaných iterátorů je stejný a určuje bod kam *val* by mohlo být vloženo bez narušení pořadí rozsahu.

### <a name="remarks"></a>Poznámky

První iterace dvojice vrácené algoritmem je [lower_bound](../standard-library/algorithm-functions.md#lower_bound), a druhá iterace je [upper_bound](../standard-library/algorithm-functions.md#upper_bound).

Rozsah musí být seřazen podle předchozího prvku pro `equal_range`. Například, pokud se chystáte použít větší-než predikát, rozsah musí být seřazen v sestupném pořadí.

Elementy v možném prázdném podrozsahu definované párem iterátorů vrácené pomocí `equal_range` bude odpovídat *val* ve smyslu definovaném použitým predikátem.

Složitost algoritmu je logaritmický pro iterátory s náhodným přístupem a v opačném případě lineární, přičemž počet kroků je přímo úměrný (*poslední* - *první*).

### <a name="example"></a>Příklad

```cpp
// alg_equal_range.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>()
#include <iostream>
#include <string>
using namespace std;

template<class T> void dump_vector( const vector<T>& v, pair<typename vector<T>::iterator, typename vector<T>::iterator> range )
{
    // prints vector v with range delimited by [ and ]

    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        if ( i == range.first )
        {
            cout << "[ ";
        }
        if ( i == range.second )
        {
            cout << "] ";
        }

        cout << *i << " ";
    }
    cout << endl;
}

template<class T> void equal_range_demo( const vector<T>& original_vector, T val )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end() );
    cout << "Vector sorted by the default binary predicate <:" << endl << '\t';
    for ( vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<vector<T>::iterator, vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), val );

    cout << "Result of equal_range with val = " << val << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

template<class T, class F> void equal_range_demo( const vector<T>& original_vector, T val, F pred, string predname )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end(), pred );
    cout << "Vector sorted by the binary predicate " << predname << ":" << endl << '\t';
    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<typename vector<T>::iterator, typename vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), val, pred );

    cout << "Result of equal_range with val = " << val << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

// Return whether absolute value of elem1 is less than absolute value of elem2
bool abs_lesser( int elem1, int elem2 )
{
    return abs(elem1) < abs(elem2);
}

// Return whether string l is shorter than string r
bool shorter_than(const string& l, const string& r)
{
    return l.size() < r.size();
}

int main()
{
    vector<int> v1;

    // Constructing vector v1 with default less than ordering
    for ( int i = -1; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    for ( int i =-3; i <= 0; ++i )
    {
        v1.push_back( i );
    }

    equal_range_demo( v1, 3 );
    equal_range_demo( v1, 3, greater<int>(), "greater" );
    equal_range_demo( v1, 3, abs_lesser, "abs_lesser" );

    vector<string> v2;

    v2.push_back("cute");
    v2.push_back("fluffy");
    v2.push_back("kittens");
    v2.push_back("fun");
    v2.push_back("meowmeowmeow");
    v2.push_back("blah");

    equal_range_demo<string>( v2, "fred" );
    equal_range_demo<string>( v2, "fred", shorter_than, "shorter_than" );
}

```

## <a name="fill"></a>  Výplň

Každému prvku v zadaném rozsahu přiřadí stejnou novou hodnotu.

```cpp
template<class ForwardIterator, class Type>
void fill(
    ForwardIterator first,
    ForwardIterator last,
    const Type& val);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu na Procházet.

*poslední*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu na Procházet.

*Val*<br/>
Hodnota, kterou chcete přiřadit elementům v rozsahu [ *první*, *poslední*).

### <a name="remarks"></a>Poznámky

Cílový rozsah musí být platný; všechny odkazy musí být možné zrušit referenci a poslední pozice je dosažitelná z první pomocí přírůstků. Složitost je lineární s velikostí rozsahu.

### <a name="example"></a>Příklad

```cpp
// alg_fill.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // Fill the last 5 positions with a value of 2
   fill( v1.begin( ) + 5, v1.end( ), 2 );

   cout << "Modified v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 30 35 40 45 )
Modified v1 = ( 0 5 10 15 20 2 2 2 2 2 )
```

## <a name="fill_n"></a>  fill_n

Přiřadí novou hodnotu na zadaný počet prvků v rozsahu, který začíná konkrétním elementem.

```cpp
template<class OutputIterator, class Size, class Type>
OutputIterator fill_n(
    OutputIterator First,
    Size Count,
    const Type& Val);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Výstupní iterace adresující pozici prvního prvku v rozsahu má být přiřazena hodnota *Val*.

*Počet*<br/>
Typ celého čísla se znaménkem nebo bez znaménka určující počet prvků, které má být přiřazena hodnota.

*Val*<br/>
Hodnota, kterou chcete přiřadit elementům v rozsahu [ *první*, *první + počet*).

### <a name="return-value"></a>Návratová hodnota

Iterátor na prvek, který následuje po posledním prvku vyplněna, pokud *počet* > nula, jinak první prvek.

### <a name="remarks"></a>Poznámky

Cílový rozsah musí být platný; všechny odkazy musí být možné zrušit referenci a poslední pozice je dosažitelná z první pomocí přírůstků. Složitost je lineární s velikostí rozsahu.

### <a name="example"></a>Příklad

```cpp
// alg_fill_n.cpp
// compile using /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector <int> v;

    for ( auto i = 0 ; i < 9 ; ++i )
        v.push_back( 0 );

    cout << "  vector v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the first 3 positions with a value of 1, saving position.
    auto pos = fill_n( v.begin(), 3, 1 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the next 3 positions with a value of 2, using last position.
    fill_n( pos, 3, 2 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the last 3 positions with a value of 3, using relative math.
    fill_n( v.end()-3, 3, 3 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;
}

```

## <a name="find"></a>  Najít

Vyhledá pozici prvního výskytu prvku v rozsahu, který má zadanou hodnotu.

```cpp
template<class InputIterator, class T>
InputIterator find(
    InputIterator first,
    InputIterator last,
    const T& val);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor adresující pozici prvního prvku v rozsahu pro hledání pro zadanou hodnotu.

*poslední*<br/>
Vstupní iterátor adresující jedna pozice za posledním prvkem v oblasti pro hledání pro zadanou hodnotu.

*Val*<br/>
Hodnota má být vyhledán.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první výskyt zadané hodnotě v prohledávaný rozsah. Pokud není nalezen žádný element s odpovídající hodnotu, vrátí *poslední*.

### <a name="remarks"></a>Poznámky

`operator==` Používá k určení shody mezi prvkem a zadaná hodnota musí uložit vztahu ekvivalence mezí jejími operandy.

Příklad použití kódu `find()`, naleznete v tématu [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="find_end"></a>  find_end –

Vyhledá v rozsahu poslední dílčí sekvenci, která je shodná se zadanou sekvencí nebo která je ekvivalentní ve smyslu určeném binárním predikátem.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_end(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    ForwardIterator2 Last2);

template<class ForwardIterator1, class ForwardIterator2, class Pred>
ForwardIterator1 find_end(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    ForwardIterator2 Last2,
    Pred Comp);
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu pro hledání.

*Příjmení1*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v oblasti pro hledání.

*first2*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu pro hledání.

*Příjmení2*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v oblasti pro hledání.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněny, pokud jsou dva prvky mají být provedeny, jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje umístění prvního prvku poslední dílčí sekvenci v rámci [First1, Last1), který odpovídá zadané posloupnosti [First2, Příjmení2).

### <a name="remarks"></a>Poznámky

`operator==` Používá k určení shody mezi prvkem a zadaná hodnota musí uložit vztahu ekvivalence mezí jejími operandy.

Rozsahy odkazuje musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci každé posloupnosti je poslední pozice dosažitelná z první pomocí přírůstků.

### <a name="example"></a>Příklad

```cpp
// alg_find_end.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
   return 2 * elem1 == elem2;
}

int main()
{
   using namespace std;
   vector <int> v1, v2;
   list <int> L1;
   vector <int>::iterator Iter1, Iter2;
   list <int>::iterator L1_Iter, L1_inIter;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   int ii;
   for ( ii = 1 ; ii <= 4 ; ii++ )
   {
      L1.push_back( 5 * ii );
   }

   int iii;
   for ( iii = 2 ; iii <= 4 ; iii++ )
   {
      v2.push_back( 10 * iii );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "List L1 = ( " ;
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
      cout << *L1_Iter << " ";
   cout << ")" << endl;

   cout << "Vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
      cout << ")" << endl;

   // Searching v1 for a match to L1 under identity
   vector <int>::iterator result1;
   result1 = find_end ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

   if ( result1 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is a match of L1 in v1 that begins at "
           << "position "<< result1 - v1.begin( ) << "." << endl;

   // Searching v1 for a match to L1 under the binary predicate twice
   vector <int>::iterator result2;
   result2 = find_end ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

   if ( result2 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is a sequence of elements in v1 that "
           << "are equivalent to those\n in v2 under the binary "
           << "predicate twice and that begins at position "
           << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 5 10 15 20 )
Vector v2 = ( 20 30 40 )
There is a match of L1 in v1 that begins at position 7.
There is a sequence of elements in v1 that are equivalent to those
in v2 under the binary predicate twice and that begins at position 8.
```

## <a name="find_first_of"></a>  find_first_of

Vyhledá první výskyt jedné z několika hodnot v cílovém rozsahu nebo první výskyt jednoho z několika prvků, které jsou ekvivalentní ve smyslu určeném binárním predikátem zadané sadě prvků.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_first_of(
    ForwardIterator1  first1,
    ForwardIterator1 Last1,
    ForwardIterator2  first2,
    ForwardIterator2 Last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 find_first_of(
    ForwardIterator1  first1,
    ForwardIterator1 Last1,
    ForwardIterator2  first2,
    ForwardIterator2 Last2,
    BinaryPredicate  comp);
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu pro hledání.

*Příjmení1*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v oblasti pro hledání.

*first2*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu lze porovnat.

*Příjmení2*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu lze porovnat.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněny, pokud jsou dva prvky mají být provedeny, jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje umístění prvního prvku první dílčí sekvenci, který odpovídá zadané posloupnosti nebo, který je ekvivalentní ve smyslu určeném binárním predikátem.

### <a name="remarks"></a>Poznámky

`operator==` Používá k určení shody mezi prvkem a zadaná hodnota musí uložit vztahu ekvivalence mezí jejími operandy.

Rozsahy odkazuje musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci každé posloupnosti je poslední pozice dosažitelná z první pomocí přírůstků.

### <a name="example"></a>Příklad

```cpp
// alg_find_first_of.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
   return 2 * elem1 == elem2;
}

int main()
{
   using namespace std;
   vector <int> v1, v2;
   list <int> L1;
   vector <int>::iterator Iter1, Iter2;
   list <int>::iterator L1_Iter, L1_inIter;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   int ii;
   for ( ii = 3 ; ii <= 4 ; ii++ )
   {
      L1.push_back( 5 * ii );
   }

   int iii;
   for ( iii = 2 ; iii <= 4 ; iii++ )
   {
      v2.push_back( 10 * iii );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "List L1 = ( " ;
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
      cout << *L1_Iter << " ";
   cout << ")" << endl;

   cout << "Vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
      cout << ")" << endl;

   // Searching v1 for first match to L1 under identity
   vector <int>::iterator result1;
   result1 = find_first_of ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

   if ( result1 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is at least one match of L1 in v1"
           << "\n and the first one begins at "
           << "position "<< result1 - v1.begin( ) << "." << endl;

   // Searching v1 for a match to L1 under the binary predicate twice
   vector <int>::iterator result2;
   result2 = find_first_of ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

   if ( result2 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is a sequence of elements in v1 that "
           << "are equivalent\n to those in v2 under the binary "
           << "predicate twice\n and the first one begins at position "
           << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 15 20 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
and the first one begins at position 3.
There is a sequence of elements in v1 that are equivalent
to those in v2 under the binary predicate twice
and the first one begins at position 2.
```

## <a name="find_if"></a>  find_if

Vyhledá pozici prvního výskytu prvku v rozsahu, který splňuje zadanou podmínku.

```cpp
template<class InputIterator, class Predicate>
InputIterator find_if(
    InputIterator first,
    InputIterator last,
    Predicate pred);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor adresující pozici prvního prvku v rozsahu pro hledání.

*poslední*<br/>
Vstupní iterátor adresuje umístění jedno místo za posledním prvkem v oblasti pro hledání.

*Před*<br/>
Objekt funkce predikátu definovaný uživatelem nebo [výraz lambda](../cpp/lambda-expressions-in-cpp.md) , který definuje podmínku, která má být splněno elementu vyhledávaná. Predikát přijímá jeden argument a vrátí **true** (splněno) nebo **false** (nejsou splněny). Podpis *před* musí být efektivně `bool pred(const T& arg);`, kde `T` je typ, ke které `InputIterator` lze implicitně převést při dereferenci. **Const** – klíčové slovo je zobrazena pouze pro ilustraci, že objekt funkce nebo výrazu lambda nesmí změnit argument.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor odkazující na první prvek v rozsahu, který splňuje podmínka uvedená v predikátu (predikát výsledkem **true**). Pokud není nalezen žádný element na splňují predikát, vrátí *poslední*.

### <a name="remarks"></a>Poznámky

Tuto funkci je generalizace algoritmus [najít](../standard-library/algorithm-functions.md#find), nahrazení predikátu "se rovná určitou hodnotu" s predikátem, za jakékoli. Logická negace (vyhledejte první prvek, který nesplňuje predikát), naleznete v části [find_if_not](../standard-library/algorithm-functions.md#find_if_not).

### <a name="example"></a>Příklad

```cpp
// cl.exe /W4 /nologo /EHsc /MTd
#include <vector>
#include <algorithm>
#include <iostream>
#include <string>

using namespace std;

template <typename S> void print(const S& s) {
for (const auto& p : s) {
        cout << "(" << p << ") ";
    }
    cout << endl;
}

// Test std::find()
template <class InputIterator, class T>
void find_print_result(InputIterator first, InputIterator last, const T& value) {

    // call <algorithm> std::find()
    auto p = find(first, last, value);

    cout << "value " << value;
    if (p == last) {
        cout << " not found." << endl;
    } else {
        cout << " found." << endl;
    }
}

// Test std::find_if()
template <class InputIterator, class Predicate>
void find_if_print_result(InputIterator first, InputIterator last,
    Predicate Pred, const string& Str) {

    // call <algorithm> std::find_if()
    auto p = find_if(first, last, Pred);

    if (p == last) {
        cout << Str << " not found." << endl;
    } else {
        cout << "first " << Str << " found: " << *p << endl;
    }
}

// Function to use as the UnaryPredicate argument to find_if() in this example
bool is_odd_int(int i) {
    return ((i % 2) != 0);
}

int main()
{
    // Test using a plain old array.
    const int x[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
    cout << "array x[] contents: ";
    print(x);
    // Using non-member std::begin()/std::end() to get input iterators for the plain old array.
    cout << "Test std::find() with array..." << endl;
    find_print_result(begin(x), end(x), 10);
    find_print_result(begin(x), end(x), 42);
    cout << "Test std::find_if() with array..." << endl;
    find_if_print_result(begin(x), end(x), is_odd_int, "odd integer"); // function name
    find_if_print_result(begin(x), end(x), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");

    // Test using a vector.
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back((i + 1) * 10);
    }
    cout << endl << "vector v contents: ";
    print(v);
    cout << "Test std::find() with vector..." << endl;
    find_print_result(v.begin(), v.end(), 20);
    find_print_result(v.begin(), v.end(), 12);
    cout << "Test std::find_if() with vector..." << endl;
    find_if_print_result(v.begin(), v.end(), is_odd_int, "odd integer");
    find_if_print_result(v.begin(), v.end(), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");
}

```

## <a name="find_if_not"></a>  find_if_not

Vrátí první prvek v zadaném rozsahu, který nesplňuje podmínku.

```cpp
template<class InputIterator, class Predicate>
InputIterator find_if_not(
    InputIterator first,
    InputIterator last,
    Predicate pred);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor adresující pozici prvního prvku v rozsahu pro hledání.

*poslední*<br/>
Vstupní iterátor adresuje umístění jedno místo za posledním prvkem v oblasti pro hledání.

*Před*<br/>
Objekt funkce predikátu definovaný uživatelem nebo [výraz lambda](../cpp/lambda-expressions-in-cpp.md) , který definuje podmínku, která má nesmí být splněno elementu vyhledaly. Predikát přijímá jeden argument a vrátí **true** (splněno) nebo **false** (nejsou splněny). Podpis *před* musí být efektivně `bool pred(const T& arg);`, kde `T` je typ, ke které `InputIterator` lze implicitně převést při dereferenci. **Const** – klíčové slovo je zobrazena pouze pro ilustraci, že objekt funkce nebo výrazu lambda nesmí změnit argument.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor odkazující na první prvek v rozsahu, který nesplňuje podmínka uvedená v predikátu (predikát výsledkem **false**). Pokud všechny prvky splňují predikát (predikát výsledkem **true** pro každý prvek), vrátí *poslední*.

### <a name="remarks"></a>Poznámky

Tuto funkci je generalizace algoritmus [najít](../standard-library/algorithm-functions.md#find), nahrazení predikátu "se rovná určitou hodnotu" s predikátem, za jakékoli. Logická negace (vyhledejte první prvek, které splňují predikát), naleznete v části [find_if](../standard-library/algorithm-functions.md#find_if).

Příklad kódu, který je snadno přizpůsobitelná pro `find_if_not()`, naleznete v tématu [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="for_each"></a>  for_each

Na každý prvek v pořadí dopředu v rozsahu použije zadaný objekt funkce a vrátí objekt funkce.

```cpp
template<class InputIterator, class Function>
Function for_each(
    InputIterator first,
    InputIterator last,
    Function func);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor adresující pozici prvního prvku v rozsahu, který chcete ho zpracovat.

*poslední*<br/>
Vstupní iterátor adresuje umístění jedno místo za posledním prvkem v rozsahu zpracovat.

*_Func*<br/>
Uživatelem definované funkce objektu, který se aplikuje na každý prvek v rozsahu.

### <a name="return-value"></a>Návratová hodnota

Kopie objektu funkce po použití na všechny prvky v rozsahu.

### <a name="remarks"></a>Poznámky

Algoritmus `for_each` je velmi flexibilní, což umožňuje změnu jednotlivých prvků v rozsahu způsoby jiný, zadané uživatelem. Šablonou funkce mohou být znovu použity v upravené podobě předáním různé parametry. Uživatelem definované funkce může shromažďovat informace v rámci vnitřní stav, který algoritmus může vrátit po zpracování všech prvků v rozsahu.

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci jednoho pořadí, musí být poslední pozice dosažitelná z první pomocí přírůstků.

Složitost je lineární s maximálně ( *poslední* -  *první*) porovnání.

### <a name="example"></a>Příklad

```cpp
// alg_for_each.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
private:
   Type Factor;   // The value to multiply by
public:
   // Constructor initializes the value to multiply by
   MultValue ( const Type& val ) : Factor ( val ) {
   }

   // The function call for the element to be multiplied
   void operator( ) ( Type& elem ) const
   {
      elem *= Factor;
   }
};

// The function object to determine the average
class Average
{
private:
   long num;      // The number of elements
   long sum;      // The sum of the elements
public:
   // Constructor initializes the value to multiply by
   Average( ) : num ( 0 ) , sum ( 0 )
   {
   }

   // The function call to process the next elment
   void operator( ) ( int elem ) \
   {
      num++;      // Increment the element count
      sum += elem;   // Add the value to the partial sum
   }

   // return Average
   operator double( )
   {
      return  static_cast <double> (sum) /
      static_cast <double> (num);
   }
};

int main()
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   // Constructing vector v1
   int i;
   for ( i = -4 ; i <= 2 ; i++ )
   {
      v1.push_back(  i );
   }

   cout << "Original vector  v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Using for_each to multiply each element by a Factor
   for_each ( v1.begin( ), v1.end( ), MultValue<int> ( -2 ) );

   cout << "Multiplying the elements of the vector v1\n "
        <<  "by the factor -2 gives:\n v1mod1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // The function object is templatized and so can be
   // used again on the elements with a different Factor
   for_each (v1.begin( ), v1.end( ), MultValue<int> (5 ) );

   cout << "Multiplying the elements of the vector v1mod\n "
        <<  "by the factor 5 gives:\n v1mod2 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // The local state of a function object can accumulate
   // information about a sequence of actions that the
   // return value can make available, here the Average
   double avemod2 = for_each ( v1.begin( ), v1.end( ),
      Average( ) );
   cout << "The average of the elements of v1 is:\n Average ( v1mod2 ) = "
        << avemod2 << "." << endl;
}
```

```Output
Original vector  v1 = ( -4 -3 -2 -1 0 1 2 ).
Multiplying the elements of the vector v1
by the factor -2 gives:
v1mod1 = ( 8 6 4 2 0 -2 -4 ).
Multiplying the elements of the vector v1mod
by the factor 5 gives:
v1mod2 = ( 40 30 20 10 0 -10 -20 ).
The average of the elements of v1 is:
Average ( v1mod2 ) = 10.
```

## <a name="generate"></a>  Generovat

Přiřadí hodnoty generované objektem funkce každému prvku v rozsahu.

```cpp
template<class ForwardIterator, class Generator>
void generate(
    ForwardIterator first,
    ForwardIterator last,
    Generator _Gen);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, do které se mají přiřadit hodnoty.

*poslední*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za poslední prvek v rozsahu, do které se mají přiřadit hodnoty.

*_Gen*<br/>
Objekt funkce, která je volána bez argumentů, který se používá ke generování hodnoty, které mají být přiřazená jednotlivých prvků v rozsahu.

### <a name="remarks"></a>Poznámky

Funkce objektu je vyvolán pro každý prvek v rozsahu a nemusí vrátit se stejnou hodnotou pokaždé, když je volána. To může, například čtení ze souboru nebo odkazovat na a upravit místní stavu. Typ výsledku generátoru musí být převeditelný na typ hodnoty dopředných iterátorů pro rozsah.

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci jednoho pořadí, musí být poslední pozice dosažitelná z první pomocí přírůstků.

Složitost je lineární, přičemž přesně ( `last`  -   `first`) volání generátoru požadovaným.

### <a name="example"></a>Příklad

```cpp
// alg_generate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

int main()
{
   using namespace std;

   // Assigning random values to vector integer elements
   vector <int> v1 ( 5 );
   vector <int>::iterator Iter1;
   deque <int> deq1 ( 5 );
   deque <int>::iterator d1_Iter;

   generate ( v1.begin( ), v1.end( ), rand );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Assigning random values to deque integer elements
   generate ( deq1.begin( ), deq1.end( ), rand );

   cout << "Deque deq1 is ( " ;
   for ( d1_Iter = deq1.begin( ) ; d1_Iter != deq1.end( ) ; d1_Iter++ )
      cout << *d1_Iter << " ";
   cout << ")." << endl;
}
```

```Output
Vector v1 is ( 41 18467 6334 26500 19169 ).
Deque deq1 is ( 15724 11478 29358 26962 24464 ).
```

## <a name="generate_n"></a>  generate_n

Přiřadí hodnoty generované objektem funkce zadaný počet prvků v rozsahu a vrátí jedna pozice za poslední přiřazenou hodnotou.

```cpp
template<class OutputIterator, class Diff, class Generator>
void generate_n(
    OutputIterator First,
    Diff Count,
    Generator Gen);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Výstupní iterace adresující pozici prvního prvku v rozsahu, do které se mají přiřadit hodnoty.

*Počet*<br/>
Typ celého čísla se znaménkem nebo bez znaménka určující počet prvků, které má být přiřazena hodnota generátoru funkcí.

*Obecné*<br/>
Objekt funkce, která je volána bez argumentů, který se používá ke generování hodnoty, které mají být přiřazená jednotlivých prvků v rozsahu.

### <a name="remarks"></a>Poznámky

Funkce objektu je vyvolán pro každý prvek v rozsahu a nemusí vrátit se stejnou hodnotou pokaždé, když je volána. To může, například čtení ze souboru nebo odkazovat na a upravit místní stavu. Typ výsledku generátoru musí být převeditelný na typ hodnoty dopředných iterátorů pro rozsah.

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci jednoho pořadí, musí být poslední pozice dosažitelná z první pomocí přírůstků.

Složitost je lineární, přičemž přesně `Count` volání generátoru požadovaným.

### <a name="example"></a>Příklad

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <deque>
#include <iostream>
#include <string>
#include <algorithm>
#include <random>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const int elemcount = 5;
    vector<int> v(elemcount);
    deque<int> dq(elemcount);

    // Set up random number distribution
    random_device rd;
    mt19937 engine(rd());
    uniform_int_distribution<int> dist(-9, 9);

    // Call generate_n, using a lambda for the third parameter
    generate_n(v.begin(), elemcount, [&](){ return dist(engine); });
    print("vector v is: ", v);

    generate_n(dq.begin(), elemcount, [&](){ return dist(engine); });
    print("deque dq is: ", dq);
}

```

## <a name="includes"></a>  zahrnuje

Ověřuje, zda jeden seřazený rozsah obsahuje všechny prvky obsažené ve druhém seřazeném rozsahu, kde kritérium pořadí nebo ekvivalence mezi prvky může být určeno binárním predikátem.

```cpp
template<class InputIterator1, class InputIterator2>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate comp );
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku v prvních dvou seřazených zdrojových rozsahů má být testována pro Určuje, zda jsou všechny prvky druhé obsaženy v prvním.

*Příjmení1*<br/>
Vstupní iterátor adresuje umístění jedno místo za posledním prvkem v první ze dvou seřazených zdrojových rozsahů ověřovat, jestli jsou všechny prvky druhé obsaženy v prvním.

*first2*<br/>
Vstupní iterátor adresující pozici prvního prvku v druhé dvě po sobě jdoucích seřazené zdrojových rozsahů do ověřovat, jestli jsou všechny prvky druhé obsaženy v prvním.

*Příjmení2*<br/>
Vstupní iterátor, který adresuje umístění jedno místo za posledním prvkem v druhé dvě po sobě následujících seřazených zdrojových rozsahů do ověřovat, jestli jsou všechny prvky druhé obsaženy v prvním.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud první seřazený rozsah obsahuje všechny prvky v druhém seřazeném rozsahu; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Dalším způsobem, jak si můžete představit tento test je, že to bylo zjištěno, zda druhý zdrojový rozsah je podmnožinou první zdrojové oblasti.

Musí být platný; seřazených zdrojových rozsahů, které odkazuje všechny odkazy musí být možné nepřímo odkazovat a v rámci každé posloupnosti, musí být poslední pozice dosažitelná z první pomocí přírůstků.

Seřazených zdrojových rozsahů musí každý být uspořádány podmínkou použití algoritmu obsahuje ve stejném pořadí jako se používá algoritmus k seřazení kombinovaných rozsahů.

Zdrojové rozsahy nejsou změněn pomocí algoritmu `merge`.

Typy hodnot iterátorů vstupu musí být menší – než srovnatelná s hodnotou příkazu, tak aby byly uvedeny dva elementy, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý) nebo že jeden je menší než ten druhý. To má za výsledek řazení mezi neekvivalentními prvky. Přesněji řečeno algoritmus testuje, jestli všechny prvky první seřazený rozsah pod zadanou binárním predikátem mají ekvivalentní řazení na hodnoty v druhém seřazeném rozsahu.

Složitost algoritmu je lineární s maximálně 2 \* (( *Příjmení1 - first1*) – (* Příjmení2 - first2 *)) – 1 porovnání pro prázdný zdrojových rozsahů.

### <a name="example"></a>Příklad

```cpp
// alg_includes.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main()
{
   using namespace std;
   vector <int> v1a, v1b;
   vector <int>::iterator Iter1a,  Iter1b;

   // Constructing vectors v1a & v1b with default less-than ordering
   int i;
   for ( i = -2 ; i <= 4 ; i++ )
   {
      v1a.push_back(  i );
   }

   int ii;
   for ( ii =-2 ; ii <= 3 ; ii++ )
   {
      v1b.push_back(  ii  );
   }

   cout << "Original vector v1a with range sorted by the\n "
        << "binary predicate less than is v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is v1b = ( " ;
   for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b );
   vector <int>::iterator Iter2a,  Iter2b;
   sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
   sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );
   v2a.pop_back( );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is v2a = ( " ;
   for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is v2b = ( " ;
   for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ;
   vector <int>::iterator Iter3a, Iter3b;
   reverse (v3a.begin( ), v3a.end( ) );
   v3a.pop_back( );
   v3a.pop_back( );
   sort ( v3a.begin( ), v3a.end( ), mod_lesser );
   sort ( v3b.begin( ), v3b.end( ), mod_lesser );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is v3a = ( " ;
   for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        <<  "binary predicate mod_lesser is v3b = ( " ;
   for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To test for inclusion under an asscending order
   // with the default binary predicate less <int>( )
   bool Result1;
   Result1 = includes ( v1a.begin( ), v1a.end( ),
      v1b.begin( ), v1b.end( ) );
   if ( Result1 )
      cout << "All the elements in vector v1b are "
           << "contained in vector v1a." << endl;
   else
      cout << "At least one of the elements in vector v1b "
           << "is not contained in vector v1a." << endl;

   // To test for inclusion under descending
   // order specify binary predicate greater<int>( )
   bool Result2;
   Result2 = includes ( v2a.begin( ), v2a.end( ),
      v2b.begin( ), v2b.end( ), greater <int>( ) );
   if ( Result2 )
      cout << "All the elements in vector v2b are "
           << "contained in vector v2a." << endl;
   else
      cout << "At least one of the elements in vector v2b "
           << "is not contained in vector v2a." << endl;

   // To test for inclusion under a user
   // defined binary predicate mod_lesser
   bool Result3;
   Result3 = includes ( v3a.begin( ), v3a.end( ),
      v3b.begin( ), v3b.end( ), mod_lesser );
   if ( Result3 )
      cout << "All the elements in vector v3b are "
           << "contained under mod_lesser in vector v3a."
           << endl;
   else
      cout << "At least one of the elements in vector v3b is "
           << " not contained under mod_lesser in vector v3a."
           << endl;
}
```

```Output
Original vector v1a with range sorted by the
binary predicate less than is v1a = ( -2 -1 0 1 2 3 4 ).
Original vector v1b with range sorted by the
binary predicate less than is v1b = ( -2 -1 0 1 2 3 ).
Original vector v2a with range sorted by the
binary predicate greater is v2a = ( 4 3 2 1 0 -1 ).
Original vector v2b with range sorted by the
binary predicate greater is v2b = ( 3 2 1 0 -1 -2 ).
Original vector v3a with range sorted by the
binary predicate mod_lesser is v3a = ( 0 1 2 3 4 ).
Original vector v3b with range sorted by the
binary predicate mod_lesser is v3b = ( 0 -1 1 -2 2 3 ).
All the elements in vector v1b are contained in vector v1a.
At least one of the elements in vector v2b is not contained in vector v2a.
At least one of the elements in vector v3b is  not contained under mod_lesser in vector v3a.
```

## <a name="inplace_merge"></a>  inplace_merge –

Kombinuje prvky ze dvou po sobě následujících seřazených rozsahů do jednoho seřazeného rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class BidirectionalIterator>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class BidirectionalIterator, class Predicate>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Predicate comp);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Obousměrný iterátor, který adresuje umístění prvního prvku v prvních dvou po sobě jdoucích seřazené rozsahy kombinovat a rozděleny na jeden rozsah.

*střední*<br/>
Obousměrný iterátor, který adresuje umístění prvního prvku v druhé dvě po sobě jdoucích seřazené rozsahy kombinovat a rozděleny na jeden rozsah.

*poslední*<br/>
Obousměrný iterátor, který adresuje umístění jedno místo za posledním prvkem v druhé dvě po sobě jdoucích seřazené rozsahy kombinovat a rozděleny na jeden rozsah.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je větší než jiný. Binární predikát přijímá dva argumenty a by měl vrátit **true** při prvním prvkem je menší než druhý prvek a **false** jinak.

### <a name="remarks"></a>Poznámky

Seřazený po sobě jdoucích rozsahy odkazuje musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci každé posloupnosti, musí být poslední pozice dosažitelná z první pomocí přírůstků.

Seřazený po sobě jdoucích rozsahy musí každý uspořádat podmínkou pro použití `inplace_merge` algoritmus ve stejném pořadí jako se používá algoritmus k seřazení kombinovaných rozsahů. Operace není stabilní, jak se zachová relativní pořadí prvků v rámci každé oblasti. Když jsou ekvivalentní elementy v obou zdrojových rozsahů, je element že první rozsah předchází elementu druhého kombinované rozsahu.

Složitost závisí na dostupné paměti algoritmu přiděluje paměť pro dočasné vyrovnávací paměti. Pokud je k dispozici dostatek paměti, je lineární s nejlepší případ (* naposledy - nejprve *) – 1 porovnání; Pokud není k dispozici žádné pomocné paměti, nejhorším případě je *N* protokolu *(N)*, kde  *N* = (* naposledy - nejprve*).

### <a name="example"></a>Příklad

```cpp
// alg_inplace_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      //For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main()
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1, Iter2, Iter3;

   // Constructing vector v1 with default less-than ordering
   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii =-5 ; ii <= 0 ; ii++ )
   {
      v1.push_back(  ii  );
   }

   cout << "Original vector v1 with subranges sorted by the\n "
        <<  "binary predicate less than is  v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // Constructing vector v2 with ranges sorted by greater
   vector <int> v2 ( v1 );
   vector <int>::iterator break2;
   break2 = find ( v2.begin( ), v2.end( ), -5 );
   sort ( v2.begin( ), break2 , greater<int>( ) );
   sort ( break2 , v2.end( ), greater<int>( ) );
   cout << "Original vector v2 with subranges sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Constructing vector v3 with ranges sorted by mod_lesser
   vector <int> v3 ( v1 );
   vector <int>::iterator break3;
   break3 = find ( v3.begin( ), v3.end( ), -5 );
   sort ( v3.begin( ), break3 , mod_lesser );
   sort ( break3 , v3.end( ), mod_lesser );
   cout << "Original vector v3 with subranges sorted by the\n "
        << "binary predicate mod_lesser is v3 = ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;

   vector <int>::iterator break1;
   break1 = find (v1.begin( ), v1.end( ), -5 );
   inplace_merge ( v1.begin( ), break1, v1.end( ) );
   cout << "Merged inplace with default order,\n vector v1mod = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To merge inplace in descending order, specify binary
   // predicate greater<int>( )
   inplace_merge ( v2.begin( ), break2 , v2.end( ) , greater<int>( ) );
   cout << "Merged inplace with binary predicate greater specified,\n "
        << "vector v2mod = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Applying a user defined (UD) binary predicate mod_lesser
   inplace_merge ( v3.begin( ), break3, v3.end( ), mod_lesser );
   cout << "Merged inplace with binary predicate mod_lesser specified,\n "
        << "vector v3mod = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 with subranges sorted by the
binary predicate less than is  v1 = ( 0 1 2 3 4 5 -5 -4 -3 -2 -1 0 )
Original vector v2 with subranges sorted by the
binary predicate greater is v2 = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Original vector v3 with subranges sorted by the
binary predicate mod_lesser is v3 = ( 0 1 2 3 4 5 0 -1 -2 -3 -4 -5 )
Merged inplace with default order,
vector v1mod = ( -5 -4 -3 -2 -1 0 0 1 2 3 4 5 )
Merged inplace with binary predicate greater specified,
vector v2mod = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Merged inplace with binary predicate mod_lesser specified,
vector v3mod = ( 0 0 1 -1 2 -2 3 -3 4 -4 5 -5 )
```

## <a name="is_heap"></a>  is_heap

Vrátí **true** Pokud prvky v zadaném rozsahu tvoří haldu.

```cpp
template<class RandomAccessIterator>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Iterátor náhodného přístupu, který označuje začátek rozsahu ke kontrole haldy.

*poslední*<br/>
Iterátor náhodného přístupu, který označuje konec rozsahu.

*Kompozice*<br/>
Podmínky testování pořadí elementů. Binární predikát přijímá jeden argument a vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** Pokud prvky v zadaném rozsahu tvoří haldu, **false** Pokud tomu tak není.

### <a name="remarks"></a>Poznámky

První šablona funkce vrátí [is_heap_until –](../standard-library/algorithm-functions.md#is_heap_until)`(first , last) == last`.

Druhá funkce šablony vrátí

`is_heap_until(first, last, comp) == last`.

## <a name="is_heap_until"></a>  is_heap_until –

Vrátí iterátor umístěný na první prvek v rozsahu [ `begin`, `end`), který nesplňuje haldy řazení podmínku, nebo *end* Pokud rozsahu tvoří haldu.

```cpp
template<class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    RandomAccessIterator begin,
    RandomAccessIterator end);

template<class RandomAccessIterator, class BinaryPredicate>
RandomAccessIterator is_heap_until(
    RandomAccessIterator begin,
    RandomAccessIterator end,
    BinaryPredicate compare);
```

### <a name="parameters"></a>Parametry

*začít*<br/>
Iterátor náhodného přístupu, který určuje první prvek rozsahu ke kontrole haldy.

*ukončení*<br/>
Iterátor náhodného přístupu určuje konec rozsahu, který chcete vyhledat haldu.

*compare*<br/>
Binární predikát, který určuje přísné slabé seřazení podmínku, která definuje haldu. Výchozí hodnota predikátu při *porovnání* nezadáte je `std::less<>`.

### <a name="return-value"></a>Návratová hodnota

Vrátí *end* Pokud zadaný rozsah tvoří haldu nebo obsahuje jeden nebo menší počet prvků. V opačném případě vrátí že iterátor pro první prvek nalezen, která nesplňuje podmínku haldy.

### <a name="remarks"></a>Poznámky

První šablona funkce vrátí poslední iterátoru `next` v `[ begin , end ]` kde `[ begin , next)` je haldy seřazené podle objektu funkce `std::less<>`. Pokud vzdálenost `end - begin < 2`, funkce vrátí *end*.

Druhá funkce šablony se chová stejně jako první, s tím rozdílem, že používá predikát `compare` místo `std::less<>` jako haldy řazení podmínku.

## <a name="is_partitioned"></a>  is_partitioned

Vrátí **true** Pokud všechny prvky v zadaném rozsahu, který test **true** pro podmínku, předcházejí prvkům, které testují **false**.

```cpp
template<class InputIterator, class BinaryPredicate>
bool is_partitioned(
    InputIterator first,
    InputIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor, který označuje, kde se oblast začne kontrolují určitou podmínku.

*poslední*<br/>
Vstupní iterátor, který označuje konec rozsahu.

*Kompozice*<br/>
Podmínka pro testování. To poskytuje objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněno elementu vyhledávaná. Predikát přijímá jeden argument a vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud všechny prvky v zadaném rozsahu, které testují **true** pro podmínku, předcházejí prvkům, které testují **false**a v opačném případě vrátí **false**.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí **true** pouze tehdy, pokud všechny prvky v `[` `first ,` `last )` dělí podle *kompozice*; to znamená, že všechny prvky `X` v `[` `first ,` `last )` pro kterou `comp (X)` je nastavena hodnota true předcházet všechny prvky `Y` pro kterou `comp (Y)` je **false**.

## <a name="is_permutation"></a>  is_permutation

Vrátí true, pokud oba rozsahy obsahují stejné prvky, zda jsou elementy ve stejném pořadí. Použití duální rozsahy přetížení v C ++ 14 kódu, protože přetížení, která trvat jenom jeden iterátor pro druhého rozsahu nebudou zjištěny rozdíly, pokud druhá oblast je delší než první oblast a způsobí nedefinované chování, pokud je kratší druhého rozsahu než první oblast.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2);

template<class ForwardIterator1, class ForwardIterator2, class Predicate>
bool is_permutation(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    Predicate Pred);

// C++14
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    ForwardIterator2 Last2);

template<class ForwardIterator1, class ForwardIterator2, class Predicate>
bool is_permutation(
    ForwardIterator1 First1,
    ForwardIterator1 Last1,
    ForwardIterator2 First2,
    ForwardIterator2 Last2,
    Predicate Pred);
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Dopředný iterátor odkazující na první prvek rozsahu.

*Příjmení1*<br/>
Dopředný iterátor, který odkazuje na jedno místo za posledním prvkem rozsahu.

*first2*<br/>
Dopředný iterátor odkazující na první prvek druhého rozsahu, použít pro porovnání.

*Příjmení2*<br/>
Dopředný iterátor, který odkazuje na jedno místo za posledním prvkem druhého rozsahu, použít pro porovnání.

*Před*<br/>
Predikát, který testuje pro ekvivalenci a vrátí **bool**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** při rozsahy můžete změnit jejich uspořádání proto podle Komparátor predikátu identické; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

`is_permutation` v nejhorším případě má kvadratické složitost.

První šablona funkce předpokládá, že jsou v rozsahu od na tolik elementů *First2* jako v rozsahu určeném [ `First1`, `Last1`). Pokud existuje více elementů v druhého rozsahu, jsou ignorovány; Pokud jsou nižší, dojde k nedefinovanému chování. Třetí funkce šablony (C ++ 14 a novější) neprovede tento předpoklad.  Oba vracejí **true** pouze tehdy, pokud pro každý prvek X v rozsahu určeném [ `First1`, `Last1`) existují tolik elementů Y ve stejném rozsahu, pro které X == Y, protože jsou v rozsahu od na *First2* nebo [ `First2, Last2).` tady `operator==` musí provést porovnání pairwise mezí jejími operandy.

Druhá a čtvrtá šablona funkce se chovají stejně, s tím rozdílem, že nahradit `operator==(X, Y)` s `Pred(X, Y)`. Chovat správně, musí být predikát symetrický, reflexivní a tranzitivní.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat `is_permutation`:

```cpp
#include <vector>
#include <iostream>
#include <algorithm>
#include <string>

using namespace std;

int main()
{
    vector<int> vec_1{ 2, 3, 0, 1, 4, 5 };
    vector<int> vec_2{ 5, 4, 0, 3, 1, 2 };

    vector<int> vec_3{ 4, 9, 13, 3, 6, 5 };
    vector<int> vec_4{ 7, 4, 11, 9, 2, 1 };

    cout << "(1) Compare using built-in == operator: ";
    cout << boolalpha << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // true

    cout << "(2) Compare after modifying vec_2: ";
    vec_2[0] = 6;
    cout << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // false

    // Define equivalence as "both are odd or both are even"
    cout << "(3) vec_3 is a permutation of vec_4: ";
    cout << is_permutation(vec_3.begin(), vec_3.end(),
        vec_4.begin(), vec_4.end(),
        [](int lhs, int rhs) { return lhs % 2 == rhs % 2; }) << endl; // true

    // Initialize a vector using the 's' string literal to specify a std::string
    vector<string> animals_1{ "dog"s, "cat"s, "bird"s, "monkey"s };
    vector<string> animals_2{ "donkey"s, "bird"s, "meerkat"s, "cat"s };

    // Define equivalence as "first letters are equal":
    bool is_perm = is_permutation(animals_1.begin(), animals_1.end(), animals_2.begin(), animals_2.end(),
        [](const string& lhs, const string& rhs)
    {
        return lhs[0] == rhs[0]; //std::string guaranteed to have at least a null terminator
    });

    cout << "animals_2 is a permutation of animals_1: " << is_perm << endl; // true

    cout << "Press a letter" << endl;
    char c;
    cin >> c;

    return 0;
}

```

## <a name="is_sorted"></a>  is_sorted

Vrátí **true** Pokud prvky v zadaném rozsahu jsou v seřazeném pořadí.

```cpp
template<class ForwardIterator>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class BinaryPredicate>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který označuje, kde začíná rozsahu, který chcete zkontrolovat.

*poslední*<br/>
Dopředný iterátor, který označuje konec rozsahu.

*Kompozice*<br/>
Chcete-li určit pořadí mezi dvěma prvky testovanou podmínku. Predikát přijímá jeden argument a vrátí **true** nebo **false**. Provede stejnou úlohu jako `operator<`.

### <a name="remarks"></a>Poznámky

První šablona funkce vrátí [is_sorted_until –](#is_sorted_until)`( first, last ) == last`. `operator<` Funkce provádí porovnání pořadí.

Druhá funkce šablony vrátí `is_sorted_until( first, last , comp ) == last`. *Comp* funkce predikátu provádí porovnání pořadí.

## <a name="is_sorted_until"></a>  is_sorted_until –

Vrátí `ForwardIterator` , která je nastavena na poslední prvek, který je v seřazeném pořadí ze zadaného rozsahu.

Druhá verze umožňuje poskytovat `BinaryPredicate` funkce, která vrací **true** při dva dané prvky jsou v seřazeném pořadí a **false** jinak.

```cpp
template<class ForwardIterator>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last);
template<class ForwardIterator, class BinaryPredicate>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který označuje, kde začíná rozsahu, který chcete zkontrolovat.

*poslední*<br/>
Dopředný iterátor, který označuje konec rozsahu.

*Kompozice*<br/>
Chcete-li určit pořadí mezi dvěma prvky testovanou podmínku. Predikát přijímá jeden argument a vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí `ForwardIterator` nastavena na poslední prvek v seřazeném pořadí. Seřazená sekvence začíná od *první*.

### <a name="remarks"></a>Poznámky

První šablona funkce vrátí poslední iterátoru `next` v `[` `first ,` `last ]` tak, aby `[` `first , next)` je seřazená posloupnost seřazené podle `operator<`. Pokud `distance()` `< 2` funkce vrátí *poslední*.

Druhá funkce šablony se chová stejně s tím rozdílem, že ji nahradí `operator<(X, Y)` s `comp (X, Y)`.

## <a name="iter_swap"></a>  iter_swap –

Vymění dvě hodnoty odkazované dvojicí zadaných iterátorů.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
void iter_swap( ForwardIterator1 left, ForwardIterator2 right );

```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Jeden z dopředných iterátorů, jehož hodnota je mají vyměnit.

*doprava*<br/>
Druhý dopředných iterátorů, jehož hodnota je mají vyměnit.

### <a name="remarks"></a>Poznámky

`swap` má použít v preference pro můžu **ter_swap**, která byla součástí standardu jazyka C++ z důvodu zpětné kompatibility. Pokud `Fit1` a `Fit2` dopředných iterátorů, jsou pak `iter_swap` ( `Fit1`, `Fit2` ), je ekvivalentní `swap` ( \* `Fit1`, \* `Fit2` ).

Typy hodnot iterátorů předání vstupních musí mít stejnou hodnotu.

### <a name="example"></a>Příklad

```cpp
// alg_iter_swap.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt&   operator=( const CInt& rhs ) { m_nVal =
   rhs.m_nVal; return *this; }
   bool operator<( const CInt& rhs ) const
      { return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
   osIn << "CInt(" << rhs.m_nVal << ")";
   return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main()
{
   CInt c1 = 5, c2 = 1, c3 = 10;
   deque<CInt> deq1;
   deque<CInt>::iterator d1_Iter;

   deq1.push_back ( c1 );
   deq1.push_back ( c2 );
   deq1.push_back ( c3 );

   cout << "The original deque of CInts is deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   // Exchanging first and last elements with iter_swap
   iter_swap ( deq1.begin( ), --deq1.end( ) );

   cout << "The deque of CInts with first & last elements swapped is:\n deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   // Swapping back first and last elements with swap
   swap ( *deq1.begin( ), *(deq1.end( ) -1 ) );

   cout << "The deque of CInts with first & last elements swapped back is:\n deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   // Swapping a vector element with a deque element
   vector <int> v1;
   vector <int>::iterator Iter1;
   deque <int> deq2;
   deque <int>::iterator d2_Iter;

   int i;
   for ( i = 0 ; i <= 3 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii = 4 ; ii <= 5 ; ii++ )
   {
      deq2.push_back( ii );
   }

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Deque deq2 is ( " ;
   for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
      cout << *d2_Iter << " ";
   cout << ")." << endl;

   iter_swap ( v1.begin( ), deq2.begin( ) );

   cout << "After exchanging first elements,\n vector v1 is: v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl << " & deque deq2 is: deq2 = ( ";
   for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
      cout << *d2_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The original deque of CInts is deq1 = ( CInt(5), CInt(1), CInt(10) ).
The deque of CInts with first & last elements swapped is:
deq1 = ( CInt(10), CInt(1), CInt(5) ).
The deque of CInts with first & last elements swapped back is:
deq1 = ( CInt(5), CInt(1), CInt(10) ).
Vector v1 is ( 0 1 2 3 ).
Deque deq2 is ( 4 5 ).
After exchanging first elements,
vector v1 is: v1 = ( 4 1 2 3 ).
& deque deq2 is: deq2 = ( 0 5 ).
```

## <a name="lexicographical_compare"></a>  lexicographical_compare –

Porovná prvek po prvku mezi dvěma sekvencemi k určení, která z nich je menší.

```cpp
template<class InputIterator1, class InputIterator2>
bool lexicographical_compare(
    InputIterator1  first1,
    InputIterator1 Last1,
    InputIterator2  first2,
    InputIterator2 Last2  );

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool lexicographical_compare(
    InputIterator1  first1,
    InputIterator1 Last1,
    InputIterator2  first2,
    InputIterator2 Last2,
    BinaryPredicate  comp  );

```

### <a name="parameters"></a>Parametry

*first1*<br/>
Vstupní iterátor adresuje umístění prvního prvku v první oblasti, která chcete porovnat.

*Příjmení1*<br/>
Vstupní iterátor adresující jedna pozice za posledním prvkem v první oblasti, která k porovnání.

*first2*<br/>
Vstupní iterátor adresující pozici prvního prvku v druhé rozsahu k porovnání.

*Příjmení2*<br/>
Vstupní iterátor adresuje umístění jedno místo za posledním prvek v druhého rozsahu k porovnání.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud první oblast je méně lexikografický, než druhého rozsahu; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Lexicographical porovnání mezi sekvencemi porovnává je prvek po prvku do:

- Najde odpovídající prvky dvou nerovnost a výsledek jejich porovnání se bere jako výsledek porovnání mezi sekvencí.

- Nebyly nalezeny žádné nerovnosti, ale jeden sekvence má více elementů než druhý a kratší pořadí se považuje za menší než delší pořadí.

- Nebyly nalezeny žádné nerovností a zadané posloupnosti mají stejný počet prvků a proto jsou si rovny sekvencí a výsledkem porovnání je false.

### <a name="example"></a>Příklad

```cpp
// alg_lex_comp.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
   return 2 * elem1 < elem2;
}

int main()
{
   using namespace std;
   vector <int> v1, v2;
   list <int> L1;
   vector <int>::iterator Iter1, Iter2;
   list <int>::iterator L1_Iter, L1_inIter;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }
   int ii;
   for ( ii = 0 ; ii <= 6 ; ii++ )
   {
      L1.push_back( 5 * ii );
   }

   int iii;
   for ( iii = 0 ; iii <= 5 ; iii++ )
   {
      v2.push_back( 10 * iii );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "List L1 = ( " ;
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
      cout << *L1_Iter << " ";
   cout << ")" << endl;

   cout << "Vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
      cout << ")" << endl;

   // Self lexicographical_comparison of v1 under identity
   bool result1;
   result1 = lexicographical_compare (v1.begin( ), v1.end( ),
                  v1.begin( ), v1.end( ) );
   if ( result1 )
      cout << "Vector v1 is lexicographically_less than v1." << endl;
   else
      cout << "Vector v1 is not lexicographically_less than v1." << endl;

   // lexicographical_comparison of v1 and L2 under identity
   bool result2;
   result2 = lexicographical_compare (v1.begin( ), v1.end( ),
                  L1.begin( ), L1.end( ) );
   if ( result2 )
      cout << "Vector v1 is lexicographically_less than L1." << endl;
   else
      cout << "Vector v1 is lexicographically_less than L1." << endl;

   bool result3;
   result3 = lexicographical_compare (v1.begin( ), v1.end( ),
                  v2.begin( ), v2.end( ), twice );
   if ( result3 )
      cout << "Vector v1 is lexicographically_less than v2 "
           << "under twice." << endl;
   else
      cout << "Vector v1 is not lexicographically_less than v2 "
           << "under twice." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 )
List L1 = ( 0 5 10 15 20 25 30 )
Vector v2 = ( 0 10 20 30 40 50 )
Vector v1 is not lexicographically_less than v1.
Vector v1 is lexicographically_less than L1.
Vector v1 is not lexicographically_less than v2 under twice.
```

## <a name="lower_bound"></a>  lower_bound –

Najde pozici prvního prvku v seřazeném rozsahu, jehož hodnota je větší nebo rovna zadané hodnotě, kde kritérium pořadí může být určeno primárním predikátem.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator lower_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value );

template<class ForwardIterator, class Type, class BinaryPredicate>
ForwardIterator lower_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate comp );

```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu pro hledání.

*poslední*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v oblasti pro hledání.

*value*<br/>
Hodnota, jejíž první pozice nebo možná první pozice je prohledávána v rozsahu příkazu.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor v pozici prvního prvku v seřazeném rozsahu s hodnotou, která je větší než nebo rovna zadané hodnotě, kde rovnost je zadána binárním predikátem.

### <a name="remarks"></a>Poznámky

Odkazovaný seřazený zdrojový rozsah musí být platný; všech iterátorů musí být možné nepřímo odkazovat a v rámci sekvence musí být poslední pozice dosažitelná z první pomocí přírůstků.

Seřazený rozsah je podmínkou pro použití `lower_bound` a kde řazení je stejné jako u binárního predikátu.

Rozsah nebyl změněn pomocí algoritmu `lower_bound`.

Typy hodnot iterátorů předání musí být menší – než srovnatelná s hodnotou příkazu, tak aby byly uvedeny dva elementy, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý) nebo že jeden je menší než ten druhý. Výsledkem je řazení mezi neekvivalentními prvky

Složitost algoritmu je logaritmický pro iterátory s náhodným přístupem a v opačném případě lineární, přičemž počet kroků je přímo úměrný (`last - first`).

### <a name="example"></a>Příklad

```cpp
// alg_lower_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back(  i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back(  ii  );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        <<  "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate lower_bound

    vector<int>::iterator Result;

    // lower_bound of 3 in v1 with default binary predicate less<int>()
    Result = lower_bound(v1.begin(), v1.end(), 3);
    cout << "The lower_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = lower_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The lower_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v3 with the binary predicate  mod_lesser
    Result = lower_bound(v3.begin(), v3.end(), 3,  mod_lesser);
    cout << "The lower_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}

```

## <a name="make_heap"></a>  make_heap –

Převede prvky ze zadaného rozsahu do haldy, ve které je první prvek největší a pro kterou může být kritérium řazení určeno binárním predikátem.

```cpp
template<class RandomAccessIterator>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate comp );

```

### <a name="parameters"></a>Parametry

*první*<br/>
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v rozsahu, který chcete převést na haldu.

*poslední*<br/>
Iterátor náhodného přístupu, který adresuje umístění jedno místo za poslední prvek v rozsahu, který chcete převést na haldu.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="remarks"></a>Poznámky

Haldy má dvě vlastnosti:

- Vždy je největší první prvek.

- Elementy mohou přidat nebo odebrat logaritmické včas.

Haldy jsou ideální způsob, jak implementovat prioritní fronty a používají se v implementaci adaptér kontejneru standardní knihovny C++ [priority_queue – třída](../standard-library/priority-queue-class.md).

Složitost je lineární, které vyžadují 3 \* (* naposledy - nejprve *) porovnání.

### <a name="example"></a>Příklad

```cpp
// alg_make_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   random_shuffle( v1.begin( ), v1.end( ) );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Make v1 a heap with default less than ordering
   make_heap ( v1.begin( ), v1.end( ) );
   cout << "The heaped version of vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Make v1 a heap with greater than ordering
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The greater-than heaped version of v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="max"></a>  max

Porovná dva objekty a vrátí větší z nich, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class Type>
constexpr Type& max(
    const Type& left,
    const Type& right);
template<class Type, class Pr>
constexpr Type& max(
    const Type& left,
    const Type& right,
    BinaryPredicate comp);
template<class Type>
constexpr Type& max (
    initializer_list<Type> );
template<class Type, class Pr>
constexpr Type& max(
    initializer_list<Type> ,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
První dva objekty, který se porovnává.

*doprava*<br/>
Druhý dvou porovnávaných objektů.

*Kompozice*<br/>
Binární predikát, který používá k porovnání dvou objektů.

*_IList*<br/>
Inicializační seznam, který obsahuje objekty, které chcete porovnat.

### <a name="return-value"></a>Návratová hodnota

Delší než dva objekty, pokud ani jeden není větší; v takovém případě vrátí první dva objekty. V případě seznam initializer_list vrátí nejlepší objektů v seznamu.

### <a name="remarks"></a>Poznámky

`max` Algoritmus neobvyklé tím, že objekty, které jsou předány jako parametry. Většina algoritmů standardní knihovny C++ pracovaly na rozsahu prvků, jejichž pozice je určená iterátorů, které jsou předány jako parametry. Pokud potřebujete funkci, která funguje v rozsahu prvků, použijte [max_element](../standard-library/algorithm-functions.md#max_element) místo. Visual Studio 2017 umožňuje **constexpr** na přetížení, která přijmout objekt initializer_list.

### <a name="example"></a>Příklad

```cpp
// alg_max.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt&   operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      {return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether absolute value of elem1 is greater than
// absolute value of elem2
bool abs_greater ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = -elem1;
   if ( elem2 < 0 )
      elem2 = -elem2;
   return elem1 < elem2;
};

int main()
{
   int a = 6, b = -7;
   // Return the integer with the larger absolute value
   const int& result1 = max(a, b, abs_greater);
   // Return the larger integer
   const int& result2 = max(a, b);

   cout << "Using integers 6 and -7..." << endl;
   cout << "The integer with the greater absolute value is: "
        << result1 << "." << endl;
   cout << "The integer with the greater value is: "
        << result2 << "." << endl;
   cout << endl;

// Comparing the members of an initializer_list
const int& result3 = max({ a, b });
const int& result4 = max({ a, b }, abs_greater);

cout << "Comparing the members of an initializer_list..." << endl;
cout << "The member with the greater value is: " << result3 << endl;
cout << "The integer with the greater absolute value is: " << result4 << endl;

   // Comparing set containers with elements of type CInt
   // using the max algorithm
   CInt c1 = 1, c2 = 2, c3 = 3;
   set<CInt> s1, s2, s3;
   set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

   s1.insert ( c1 );
   s1.insert ( c2 );
   s2.insert ( c2 );
   s2.insert ( c3 );

   cout << "s1 = (";
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter << ",";
   s1_Iter = --s1.end( );
   cout << " " << *s1_Iter << " )." << endl;

   cout << "s2 = (";
   for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
      cout << " " << *s2_Iter << ",";
   s2_Iter = --s2.end( );
   cout << " " << *s2_Iter << " )." << endl;

   s3 = max ( s1, s2 );
   cout << "s3 = max ( s1, s2 ) = (";
   for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
      cout << " " << *s3_Iter << ",";
   s3_Iter = --s3.end( );
   cout << " " << *s3_Iter << " )." << endl << endl;

   // Comparing vectors with integer elements using the max algorithm
   vector <int> v1, v2, v3, v4, v5;
   vector <int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

   int i;
   for ( i = 0 ; i <= 2 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii = 0 ; ii <= 2 ; ii++ )
   {
      v2.push_back( ii );
   }

   int iii;
   for ( iii = 0 ; iii <= 2 ; iii++ )
   {
      v3.push_back( 2 * iii );
   }

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   cout << "Vector v3 is ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;

   v4 = max ( v1, v2 );
   v5 = max ( v1, v3 );

   cout << "Vector v4 = max (v1,v2) is ( " ;
   for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
      cout << *Iter4 << " ";
   cout << ")." << endl;

   cout << "Vector v5 = max (v1,v3) is ( " ;
   for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
      cout << *Iter5 << " ";
   cout << ")." << endl;
}
```

```Output
Using integers 6 and -7...
The integer with the greater absolute value is: -7
The integer with the greater value is: 6.
Comparing the members of an initializer_list...The member with the greater value is: 6The integer wiht the greater absolute value is: -7
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = max ( s1, s2 ) = ( CInt( 2 ), CInt( 3 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = max (v1,v2) is ( 0 1 2 ).
Vector v5 = max (v1,v3) is ( 0 2 4 ).
```

## <a name="max_element"></a>  max_element –

Vyhledá první výskyt největšího prvku v zadaném rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator max_element(ForwardIterator first, ForwardIterator last );

template<class ForwardIterator, class BinaryPredicate>
constexpr ForwardIterator max_element(ForwardIterator first, ForwardIterator last, BinaryPredicate comp );

```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu má být vyhledán největšího prvku.

*poslední*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za poslední prvek v rozsahu má být vyhledán největšího prvku.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je větší než jiný. Binární predikát přijímá dva argumenty a by měl vrátit **true** při prvním prvkem je menší než druhý prvek a **false** jinak.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor adresující pozici první výskyt největšího prvku v rozsahu prohledávat.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci každé posloupnosti je poslední pozice dosažitelná z první pomocí přírůstků.

Složitost je lineární: (`last` - `first`) + 1 porovnání jsou požadovány pro prázdný rozsah.

### <a name="example"></a>Příklad

```cpp
// alg_max_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt& operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      {return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<(ostream& osIn, const CInt& rhs)
{
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether modulus of elem1 is greater than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main()
{
   // Searching a set container with elements of type CInt
   // for the maximum element
   CInt c1 = 1, c2 = 2, c3 = -3;
   set<CInt> s1;
   set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

   s1.insert ( c1 );
   s1.insert ( c2 );
   s1.insert ( c3 );

   cout << "s1 = (";
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter << ",";
   s1_Iter = --s1.end( );
   cout << " " << *s1_Iter << " )." << endl;

   s1_R1_Iter = max_element ( s1.begin( ), s1.end( ) );

   cout << "The largest element in s1 is: " << *s1_R1_Iter << endl;
   cout << endl;

   // Searching a vector with elements of type int for the maximum
   // element under default less than & mod_lesser binary predicates
   vector <int> v1;
   vector <int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

   int i;
   for ( i = 0 ; i <= 3 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii = 1 ; ii <= 4 ; ii++ )
   {
      v1.push_back( - 2 * ii );
   }

   cout << "Vector v1 is ( " ;
   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << " ";
   cout << ")." << endl;

   v1_R1_Iter = max_element ( v1.begin( ), v1.end( ) );
   v1_R2_Iter = max_element ( v1.begin( ), v1.end( ), mod_lesser);

   cout << "The largest element in v1 is: " << *v1_R1_Iter << endl;
   cout << "The largest element in v1 under the mod_lesser"
        << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

## <a name="merge"></a>  sloučení

Kombinuje všechny prvky ze dvou seřazených zdrojových rozsahů do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    BinaryPredicate comp );

```

### <a name="parameters"></a>Parametry

*first1*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku v první ze dvou seřazených zdrojových rozsahů do kombinované a rozděleny na jeden rozsah.

*Příjmení1*<br/>
Vstupní iterátor, který adresuje umístění jedno místo za posledním prvkem v první ze dvou seřazených zdrojových rozsahů do kombinované a rozděleny na jeden rozsah.

*first2*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku v druhé dvě po sobě následujících seřazených zdrojových rozsahů kombinovat a rozděleny na jeden rozsah.

*Příjmení2*<br/>
Vstupní iterátor, který adresuje umístění jedno místo za posledním prvkem v druhé dvě po sobě následujících seřazených zdrojových rozsahů kombinovat a rozděleny na jeden rozsah.

*výsledek*<br/>
Výstupní iterace adresující pozici prvního prvku v cílové oblasti, kde jsou dva zdrojových rozsahů a nelze jej zkombinovat do jednoho seřazeného rozsahu.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je větší než jiný. Binární predikát přijímá dva argumenty a by měl vrátit **true** při prvním prvkem je menší než druhý prvek a **false** jinak.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresuje umístění jedno místo za posledním prvkem v seřazeného cílového rozsahu.

### <a name="remarks"></a>Poznámky

Musí být platný; seřazených zdrojových rozsahů, které odkazuje všechny odkazy musí být možné nepřímo odkazovat a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstků.

Cílový rozsah nesmí překrývat buď zdrojových rozsahů a by měl být dostatečně velký, aby se tak, aby obsahovala cílového rozsahu.

Seřazených zdrojových rozsahů musí každý uspořádat podmínkou pro použití `merge` algoritmus ve stejném pořadí jako se používá algoritmus k seřazení kombinovaných rozsahů.

Operace není stabilní, jako relativní pořadí prvků v rámci každé oblasti se zachovají v cílové oblasti. Zdrojové rozsahy nejsou změněn pomocí algoritmu `merge`.

Typy hodnot iterátorů vstupu musí být menší – než srovnatelná s hodnotou příkazu, tak aby byly uvedeny dva elementy, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý) nebo že jeden je menší než ten druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou ekvivalentní elementy v obou zdrojových rozsahů, před prvky v první oblasti prvky z druhého rozsahu zdroje v cílové oblasti.

Složitost algoritmu je lineární s maximálně (* Příjmení1 - first1 *) – (* Příjmení2 - first2*) + 1 porovnání.

[List – třída](../standard-library/list-class.md) poskytuje členské funkce "sloučit" prvky dvou seznamů.

### <a name="example"></a>Příklad

```cpp
// alg_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 ) {
   if (elem1 < 0)
      elem1 = - elem1;
   if (elem2 < 0)
      elem2 = - elem2;
   return elem1 < elem2;
}

int main() {
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a,  Iter1b, Iter1;

   // Constructing vector v1a and v1b with default less than ordering
   int i;
   for ( i = 0 ; i <= 5 ; i++ )
      v1a.push_back(  i );

   int ii;
   for ( ii =-5 ; ii <= 0 ; ii++ )
      v1b.push_back(  ii  );

   cout << "Original vector v1a with range sorted by the\n "
        << "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        << "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vector v2 with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );
   vector <int>::iterator Iter2a,  Iter2b, Iter2;
   sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
   sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vector v3 with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );
   vector <int>::iterator Iter3a,  Iter3b, Iter3;
   sort ( v3a.begin( ), v3a.end( ), mod_lesser );
   sort ( v3b.begin( ), v3b.end( ), mod_lesser );

   cout << "Original vector v3a with range sorted by the\n "
        << "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        << "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To merge inplace in ascending order with default binary
   // predicate less <int>( )
   merge ( v1a.begin( ), v1a.end( ), v1b.begin( ), v1b.end( ), v1.begin( ) );
   cout << "Merged inplace with default order,\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To merge inplace in descending order, specify binary
   // predicate greater<int>( )
   merge ( v2a.begin( ), v2a.end( ), v2b.begin( ), v2b.end( ),
       v2.begin( ),  greater <int>( ) );
   cout << "Merged inplace with binary predicate greater specified,\n "
        << "vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // Applying A user-defined (UD) binary predicate mod_lesser
   merge ( v3a.begin( ), v3a.end( ), v3b.begin( ), v3b.end( ),
       v3.begin( ),  mod_lesser );
   cout << "Merged inplace with binary predicate mod_lesser specified,\n "
        << "vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="min"></a>  min

Porovná dva objekty a vrátí menší z nich, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class Type>
constexpr const Type& min(
    const Type& left,
    const Type& right);
template<class Type, class Pr>
constexpr const Type& min(
    const Type& left,
    const Type& right,
    BinaryPredicate comp);
template<class Type>
constexpr Type min(
    initializer_list<Type> );
template<class Type, class Pr>
constexpr Type min(
    initializer_list<Type>,
    BinaryPredicate comp);

```

### <a name="parameters"></a>Parametry

*doleva*<br/>
První dva objekty, který se porovnává.

*doprava*<br/>
Druhý dvou porovnávaných objektů.

*Kompozice*<br/>
Binární predikát, který používá k porovnání dvou objektů.

*_IList*<br/>
Objekt initializer_list obsahující členy, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Menší než délka dvou objektů, pokud ani jeden není menší; v takovém případě vrátí první dva objekty. V případě seznam initializer_list vrátí nejmenší objektů v seznamu.

### <a name="remarks"></a>Poznámky

`min` Algoritmus neobvyklé tím, že objekty, které jsou předány jako parametry. Většina algoritmů standardní knihovny C++ pracovaly na rozsahu prvků, jejichž pozice je určená iterátorů, které jsou předány jako parametry. Pokud potřebujete funkci, která využívá celou řadu prvků, použijte [min_element](../standard-library/algorithm-functions.md#min_element). [constexpr](../cpp/constexpr-cpp.md) s povoleným `initializer_list` přetížení v sadě Visual Studio 2017.

### <a name="example"></a>Příklad

```cpp
// alg_min.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<(ostream& osIn, const CInt& rhs);

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
       return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Comparing integers directly using the min algorithm with
    // binary predicate mod_lesser & with default less than
    int a = 6, b = -7, c = 7 ;
    const int& result1 = min ( a, b, mod_lesser );
    const int& result2 = min ( b, c );

    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result1 << "." << endl;
    cout << "The lesser of the integers -7 & 7 is: "
        << result2 << "." << endl;
    cout << endl;

// Comparing the members of an initializer_list
    const int& result3 = min({ a, c });
    const int& result4 = min({ a, b }, mod_lesser);

    cout << "The lesser of the integers 6 & 7 is: "
        << result3 << "." << endl;
    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result4 << "." << endl;
    cout << endl;

    // Comparing set containers with elements of type CInt
       // using the min algorithm
    CInt c1 = 1, c2 = 2, c3 = 3;
    set<CInt> s1, s2, s3;
    set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s2.insert ( c2 );
    s2.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
        cout << " " << *s1_Iter << " )." << endl;

    cout << "s2 = (";
    for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
        cout << " " << *s2_Iter << ",";
    s2_Iter = --s2.end( );
    cout << " " << *s2_Iter << " )." << endl;

    s3 = min ( s1, s2 );
    cout << "s3 = min ( s1, s2 ) = (";
    for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
        cout << " " << *s3_Iter << ",";
    s3_Iter = --s3.end( );
    cout << " " << *s3_Iter << " )." << endl << endl;

    // Comparing vectors with integer elements using min algorithm
    vector <int> v1, v2, v3, v4, v5;
    vector <int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

    int i;
    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
    {
        v2.push_back( ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 2 ; iii++ )
    {
        v3.push_back( 2 * iii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "Vector v3 is ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;

    v4 = min ( v1, v2 );
    v5 = min ( v1, v3 );

    cout << "Vector v4 = min ( v1,v2 ) is ( " ;
    for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
        cout << *Iter4 << " ";
    cout << ")." << endl;

    cout << "Vector v5 = min ( v1,v3 ) is ( " ;
    for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
        cout << *Iter5 << " ";
    cout << ")." << endl;
}
```

```Output
The mod_lesser of the integers 6 & -7 is: 6.
The lesser of the integers -7 & 7 is: -7.
The lesser of the integers 6 & 7 is: 6.The mod_lesser of the integers 6 & -7 is: 6.
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = min ( s1, s2 ) = ( CInt( 1 ), CInt( 2 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = min ( v1,v2 ) is ( 0 1 2 ).
Vector v5 = min ( v1,v3 ) is ( 0 1 2 ).
```

## <a name="min_element"></a>  min_element –

Vyhledá první výskyt nejmenšího prvku v zadaném rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator min_element(ForwardIterator first, ForwardIterator last );

template<class ForwardIterator, class BinaryPredicate>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate comp);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu má být vyhledán nejmenší element.

*poslední*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za poslední prvek v rozsahu má být vyhledán nejmenší element.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je větší než jiný. Binární predikát přijímá dva argumenty a by měl vrátit **true** při prvním prvkem je menší než druhý prvek a **false** jinak.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor adresující pozici první výskyt nejmenšího prvku v rozsahu prohledávat.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci každé posloupnosti je poslední pozice dosažitelná z první pomocí přírůstků.

Složitost je lineární: (`last` - `first`) + 1 porovnání jsou požadovány pro prázdný rozsah.

### <a name="example"></a>Příklad

```cpp
// alg_min_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt& operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      {return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main()
{
   // Searching a set container with elements of type CInt
   // for the minimum element
   CInt c1 = 1, c2 = 2, c3 = -3;
   set<CInt> s1;
   set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

   s1.insert ( c1 );
   s1.insert ( c2 );
   s1.insert ( c3 );

   cout << "s1 = (";
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter << ",";
   s1_Iter = --s1.end( );
   cout << " " << *s1_Iter << " )." << endl;

   s1_R1_Iter = min_element ( s1.begin( ), s1.end( ) );

   cout << "The smallest element in s1 is: " << *s1_R1_Iter << endl;
   cout << endl;

   // Searching a vector with elements of type int for the maximum
   // element under default less than & mod_lesser binary predicates
   vector <int> v1;
   vector <int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

   int i;
   for ( i = 0 ; i <= 3 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii = 1 ; ii <= 4 ; ii++ )
   {
      v1.push_back( - 2 * ii );
   }

   cout << "Vector v1 is ( " ;
   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << " ";
   cout << ")." << endl;

   v1_R1_Iter = min_element ( v1.begin( ), v1.end( ) );
   v1_R2_Iter = min_element ( v1.begin( ), v1.end( ), mod_lesser);

   cout << "The smallest element in v1 is: " << *v1_R1_Iter << endl;
   cout << "The smallest element in v1 under the mod_lesser"
        << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

```Output
s1 = ( CInt( -3 ), CInt( 1 ), CInt( 2 ) ).
The smallest element in s1 is: CInt( -3 )

Vector v1 is ( 0 1 2 3 -2 -4 -6 -8 ).
The smallest element in v1 is: -8
The smallest element in v1 under the mod_lesser
binary predicate is: 0
```

## <a name="minmax_element"></a>  minmax_element

Provádí práci vykonávanou `min_element` a `max_element` v jednom volání.

```cpp
template<class ForwardIterator>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator Last);
template<class ForwardIterator, class BinaryPredicate>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator  first,
    ForwardIterator Last,
    BinaryPredicate  comp);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který označuje začátek rozsahu.

*poslední*<br/>
Dopředný iterátor, který označuje konec rozsahu.

*Kompozice*<br/>
Volitelné test, který používá pořadí elementů.

### <a name="return-value"></a>Návratová hodnota

Vrací

`pair<ForwardIterator, ForwardIterator>`

`(` [min_element –](../standard-library/algorithm-functions.md#min_element)`(first, last), `[max_element](../standard-library/algorithm-functions.md#max_element)`(first, last))`.

### <a name="remarks"></a>Poznámky

První šablona funkce vrátí

`pair<ForwardIterator,ForwardIterator>`

`(min_element(_First,Last), max_element(_First,Last))`.

Druhá funkce šablony se chová stejně s tím rozdílem, že ji nahradí `operator<(X, Y)` s `comp (X, Y)`.

Pokud je pořadí je prázdný, funkce provádí maximálně `3 * (last - first - 1) / 2` porovnání.

## <a name="minmax"></a>  minmax

Porovná dva vstupní parametry a vrátí je jako dvojici v pořadí podle nižší úrovně k vyšší.

```cpp
template<class Type>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right);
template<class Type, class BinaryPredicate>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right,
    BinaryPredicate comp);
template<class Type>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> );
template<class Type, class BinaryPredicate>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type>,
    BinaryPredicate comp);

```

### <a name="parameters"></a>Parametry

*doleva*<br/>
První dva objekty, který se porovnává.

*doprava*<br/>
Druhý dvou porovnávaných objektů.

*Kompozice*<br/>
Binární predikát, který používá k porovnání dvou objektů.

*_IList*<br/>
Objekt initializer_list obsahující členy, který se má porovnat.

### <a name="remarks"></a>Poznámky

První šablona funkce vrátí `pair<const Type&, const Type&>( right , left )` Pokud *správné* je menší než *levé*. V opačném případě vrátí `pair<const Type&, const Type&>( left , right )`.

Druhá členská funkce vrátí pár, kde první prvek je menší než a větší srovnání predikát druhá *comp*.

Zbývající šablony funkce se chovají stejně, s tím rozdílem, že nahradit *levé* a *správné* parametry s *_IList*.

Funkce provádí porovnání přesně jeden.

## <a name="mismatch"></a>  Neshoda

Porovná dva rozsahy prvek po prvku a vyhledá první pozici, kde dochází k rozdíl.

Použití duální rozsahy přetížení v C ++ 14 kódu, protože přetížení, která trvat jenom jeden iterátor pro druhého rozsahu nebudou zjištěny rozdíly, pokud druhá oblast je delší než první oblast a způsobí nedefinované chování, pokud je kratší druhého rozsahu než první oblast.

```cpp
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 First1,
    InputIterator1 Last1,
    InputIterator2 First2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 First1,
    InputIterator1 Last1,
    InputIterator2 First2,
    BinaryPredicate Comp );

//C++14
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 First1,
    InputIterator1 Last1,
    InputIterator2 First2,
    InputIterator2 Last2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 First1,
    InputIterator1 Last1,
    InputIterator2 First2,
    InputIterator2 Last2,
    BinaryPredicate Comp);
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Vstupní iterátor adresující pozici prvního prvku v první oblasti, která má být testována.

*Příjmení1*<br/>
Vstupní iterátor adresuje umístění jedno místo za poslední prvek v první oblasti, která má být testována.

*first2*<br/>
Vstupní iterátor adresující pozici prvního prvku v druhé rozsahu má být testována.

*Příjmení2*<br/>
Vstupní iterátor adresuje umístění jedno místo za posledním prvkem v druhého rozsahu má být testována.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který porovná aktuální prvkům v každé oblasti a určuje, zda jsou ekvivalentní. Vrátí **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

Pár iterátorů adresování pozice neshoda ve dvou rozsazích, první komponenta iterace na pozici v oblasti první a druhý iterátor komponenty na pozici v druhého rozsahu. Pokud není žádný rozdíl mezi prvky v rozsahu porovnání nebo binárním predikátem v druhém verzi splňují všechny páry element ze dvou oblastí, potom první komponenta iterátoru odkazuje na umístění jedno místo za posledním prvkem v prvním rozsah a druhá komponenta iterátor, který má umístění jedno místo za posledním prvkem testovány v druhého rozsahu.

### <a name="remarks"></a>Poznámky

První šablona funkce předpokládá, že jsou v rozsahu od first2 jako v rozsahu určeném [first1, Příjmení1) počet elementů. Pokud existují další do druhého rozsahu, jsou ignorovány; Pokud jsou menší bude způsobit nedefinované chování.

Rozsah pro hledání musí být platný; všech iterátorů musí být možné zrušit referenci a poslední pozice je dosažitelná z první pomocí přírůstků.

Čas složitost algoritmu je lineární počet elementů obsažených v oblasti kratší.

Predikátu definovaný uživatelem, není potřeba ukládat vztahu ekvivalence tento symetrický, reflexivní a přenosné mezí jejími operandy.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat neshoda. C ++ 03 přetížení se zobrazí pouze, aby bylo možné předvést, jak je vyhodnocen na neočekávaný výsledek.

```cpp
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>
#include <string>
#include <utility>

using namespace std;

// Return whether first element is twice the second
// Note that this is not a symmetric, reflexive and transitive equivalence.
// mismatch and equal accept such predicates, but is_permutation does not.
bool twice(int elem1, int elem2)
{
    return elem1 == elem2 * 2;
}

void PrintResult(const string& msg, const pair<vector<int>::iterator, vector<int>::iterator>& result,
    const vector<int>& left, const vector<int>& right)
{
    // If either iterator stops before reaching the end of its container,
    // it means a mismatch was detected.
    if (result.first != left.end() || result.second != right.end())
    {
        string leftpos(result.first == left.end() ? "end" : to_string(*result.first));
        string rightpos(result.second == right.end() ? "end" : to_string(*result.second));
        cout << msg << "mismatch. Left iterator at " << leftpos
            << " right iterator at " << rightpos << endl;
    }
    else
    {
        cout << msg << " match." << endl;
    }
}

int main()
{

    vector<int> vec_1{ 0, 5, 10, 15, 20, 25 };
    vector<int> vec_2{ 0, 5, 10, 15, 20, 25, 30 };

    // Testing different length vectors for mismatch (C++03)
    auto match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin());
    bool is_mismatch = match_vecs.first != vec_1.end();
    cout << "C++03: vec_1 and vec_2 are a mismatch: " << boolalpha << is_mismatch << endl;

    // Using dual-range overloads:

    // Testing different length vectors for mismatch (C++14)
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14: vec_1 and vec_2: ", match_vecs, vec_1, vec_2);

    // Identify point of mismatch between vec_1 and modified vec_2.
    vec_2[3] = 42;
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14 vec_1 v. vec_2 modified: ", match_vecs, vec_1, vec_2);

    // Test vec_3 and vec_4 for mismatch under the binary predicate twice (C++14)
    vector<int> vec_3{ 10, 20, 30, 40, 50, 60 };
    vector<int> vec_4{ 5, 10, 15, 20, 25, 30 };
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. vec_4 with pred: ", match_vecs, vec_3, vec_4);

    vec_4[5] = 31;
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. modified vec_4 with pred: ", match_vecs, vec_3, vec_4);

    // Compare a vector<int> to a list<int>
    list<int> list_1{ 0, 5, 10, 15, 20, 25 };
    auto match_vec_list = mismatch(vec_1.begin(), vec_1.end(), list_1.begin(), list_1.end());
    is_mismatch = match_vec_list.first != vec_1.end() || match_vec_list.second != list_1.end();
    cout << "vec_1 and list_1 are a mismatch: " << boolalpha << is_mismatch << endl;

    char c;
    cout << "Press a key" << endl;
    cin >> c;

}

/*
Output:
C++03: vec_1 and vec_2 are a mismatch: false
C++14: vec_1 and vec_2: mismatch. Left iterator at end right iterator at 30
C++14 vec_1 v. vec_2 modified: mismatch. Left iterator at 15 right iterator at 42
C++14 vec_3 v. vec_4 with pred:  match.
C++14 vec_3 v. modified vec_4 with pred: mismatch. Left iterator at 60 right iterator at 31
C++14: vec_1 and list_1 are a mismatch: false
Press a key
*/

```

## <a name="alg_move"></a>  &lt;alg&gt; přesunout

Přesune prvky přidružené k určenému rozsahu.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator move(
    InputIterator first,
    InputIterator last,
    OutputIterator dest);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor, který označuje, kde začít rozsahu prvků, které chcete přesunout.

*poslední*<br/>
Vstupní iterátor, který označuje konec rozsahu prvků, které se přesunout.

*cíl*<br/>
Výstupní iterátor, který bude obsahovat přesunutých prvků.

### <a name="remarks"></a>Poznámky

Funkce šablony vyhodnocuje `*(dest + N) = move(*(first + N))` jednou pro každé `N` v rozsahu `[0, last - first)`, pro přísné zvýšení hodnot `N` počínaje nejnižší hodnotou. Potom vrátí `dest + N`. Pokud `dest` a *první* určují oblasti úložiště, *dest* nesmí být v rozsahu `[first, last)`.

## <a name="move_backward"></a>  move_backward

Přesune prvky jednoho iterátoru do druhého. Pohyb začíná posledním prvkem v daném rozsahu a končí prvním prvkem v daném rozsahu.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
   BidirectionalIterator2 move_backward(
       BidirectionalIterator1 first,
       BidirectionalIterator1 last,
       BidirectionalIterator2 destEnd);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Iterátor, který označuje začátek rozsahu se mají přesunout prvky z.

*poslední*<br/>
Iterátor, který označuje konec rozsahu se mají přesunout prvky z. Tento prvek nebyl přesunut.

*destEnd*<br/>
Obousměrný iterátor, který adresuje umístění jedno místo za posledním prvkem v cílové oblasti.

### <a name="remarks"></a>Poznámky

Funkce šablony vyhodnocuje `*(destEnd - N - 1) = move(*(last - N - 1))` jednou pro každé `N` v rozsahu `[0, last - first)`, pro přísné zvýšení hodnot `N` počínaje nejnižší hodnotou. Potom vrátí `destEnd - (last - first)`. Pokud *destEnd* a *první* určují oblasti úložiště, *destEnd* nesmí být v rozsahu `[first, last)`.

`move` a `move_backward` jsou funkčně ekvivalentní použití `copy` a `copy_backward` s iterátorem pohybu.

## <a name="next_permutation"></a>  next_permutation –

Znovu uspořádá prvky v rozsahu tak, aby původní pořadí bylo nahrazeno lexikograficky následující větší permutací, pokud existuje, kde význam následujícího může být určen binárním predikátem.

```cpp
template<class BidirectionalIterator>
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last, BinaryPredicate comp);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Obousměrný iterátor odkazující na pozici prvního prvku v rozsahu pro být permutovanou funkci.

*poslední*<br/>
Obousměrný iterátor odkazující na umístění jedno místo za posledním prvkem v rozsahu pro být permutovanou funkci.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání vyhovět pomocí po sobě jdoucí prvky v pořadí. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

**true** Pokud lexikograficky následující permutaci existuje a byl nahrazen původní pořadí rozsah; v opačném případě **false**, v takovém případě řazení se transformuje na lexikograficky nejmenší permutaci.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Výchozí binární predikát je menší než a prvky v rozsahu musí být menší než srovnatelné – pomáhat zajistit, že další permutaci dobře definované.

Složitost je lineární s maximálně (* naposledy - nejprve *) / 2 Zamění.

### <a name="example"></a>Příklad

```cpp
// alg_next_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt&   operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      { return ( m_nVal < rhs.m_nVal );}
   friend   ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main()
{
   // Reordering the elements of type CInt in a deque
   // using the prev_permutation algorithm
   CInt c1 = 5, c2 = 1, c3 = 10;
   bool deq1Result;
   deque<CInt> deq1, deq2, deq3;
   deque<CInt>::iterator d1_Iter;

   deq1.push_back ( c1 );
   deq1.push_back ( c2 );
   deq1.push_back ( c3 );

   cout << "The original deque of CInts is deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   deq1Result = next_permutation ( deq1.begin( ), deq1.end( ) );

   if ( deq1Result )
      cout << "The lexicographically next permutation "
           << "exists and has\nreplaced the original "
           << "ordering of the sequence in deq1." << endl;
   else
      cout << "The lexicographically next permutation doesn't "
           << "exist\n and the lexicographically "
           << "smallest permutation\n has replaced the "
           << "original ordering of the sequence in deq1." << endl;

   cout << "After one application of next_permutation,\n deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl << endl;

   // Permuting vector elements with binary function mod_lesser
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = -3 ; i <= 3 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   next_permutation ( v1.begin( ), v1.end( ), mod_lesser );

   cout << "After the first next_permutation, vector v1 is:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   int iii = 1;
   while ( iii <= 5 ) {
      next_permutation ( v1.begin( ), v1.end( ), mod_lesser );
      cout << "After another next_permutation of vector v1,\n v1 =   ( " ;
      for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
         cout << *Iter1  << " ";
      cout << ")." << endl;
      iii++;
   }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 5 ), CInt( 1 ), CInt( 10 ) ).
The lexicographically next permutation exists and has
replaced the original ordering of the sequence in deq1.
After one application of next_permutation,
deq1 = ( CInt( 5 ), CInt( 10 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first next_permutation, vector v1 is:
v1 = ( -3 -2 -1 0 1 3 2 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 2 1 3 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 2 3 1 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 3 1 2 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 3 2 1 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 1 0 2 3 ).
```

## <a name="nth_element"></a>  nth_element –

Rozdělí rozsah prvků a správně určí *n*-tém prvku sekvence v rozsahu tak, aby všechny prvky před tímto prvkem byly menší nebo rovny a všechny prvky, které na něho v pořadí jsou větší th nebo rovny.

```cpp
template<class RandomAccessIterator>
void nth_element( RandomAccessIterator first, RandomAccessIterator _Nth, RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void nth_element( RandomAccessIterator first, RandomAccessIterator _Nth, RandomAccessIterator last, BinaryPredicate comp);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Iterátor s náhodným přístupem adresuje umístění prvního prvku v rozsahu k rozdělení na oddíly.

*_Nth*<br/>
Náhodný přístup iterátor adresující umístění prvku správné seřazení na hranici oddílu.

*poslední*<br/>
Náhodným přístupem iterátor, který adresuje umístění jedno místo za poslední prvek v rozsahu k rozdělení na oddíly.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání vyhovět pomocí po sobě jdoucí prvky v pořadí. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

`nth_element` Algoritmus nezaručuje, že buď na straně prvky v oblasti dílčí sady *n*tý prvek jsou seřazeny. Proto je záruky méně než `partial_sort`, který uspořádá prvky v rozsahu pod některé zvolený element a může sloužit jako rychlejší alternativa k `partial_sort` při řazení spodní hranice se nevyžaduje.

Prvky jsou ekvivalentní, ale ne nutně stejné, pokud je menší než ten druhý.

Průměr řazení složitost je lineární s ohledem na * nejprve naposledy - *.

### <a name="example"></a>Příklad

```cpp
// alg_nth_elem.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 ) {
   return elem1 > elem2;
}

int main() {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
      v1.push_back( 3 * i );

   int ii;
   for ( ii = 0 ; ii <= 5 ; ii++ )
      v1.push_back( 3 * ii + 1 );

   int iii;
   for ( iii = 0 ; iii <= 5 ; iii++ )
      v1.push_back( 3 * iii +2 );

   cout << "Original vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   nth_element(v1.begin( ), v1.begin( ) + 3, v1.end( ) );
   cout << "Position 3 partitioned vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order, specify binary predicate
   nth_element( v1.begin( ), v1.begin( ) + 4, v1.end( ),
          greater<int>( ) );
   cout << "Position 4 partitioned (greater) vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   random_shuffle( v1.begin( ), v1.end( ) );
   cout << "Shuffled vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // A user-defined (UD) binary predicate can also be used
   nth_element( v1.begin( ), v1.begin( ) + 5, v1.end( ), UDgreater );
   cout << "Position 5 partitioned (UDgreater) vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

## <a name="none_of"></a>  none_of

Vrátí **true** při je nikdy přítomna podmínka pohyb mezi elementy v daném rozsahu.

```cpp
template<class InputIterator, class BinaryPredicate>
bool none_of(InputIterator first, InputIterator last, BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor, který označuje, kde začít kontrolovat rozsah prvků podmínku.

*poslední*<br/>
Vstupní iterátor, který označuje konec rozsahu prvků.

*Kompozice*<br/>
Podmínka pro testování. To poskytuje objekt funkce predikátu definovaný uživatelem, který definuje podmínku. Predikát přijímá jeden argument a vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** Pokud podmínka není zjištěna alespoň jednou v zadaném rozsahu a **false** Pokud je zjištěn stav.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí **true** pouze tehdy, pokud u některých `N` v rozsahu `[0, last - first)`, predikát `comp(*(first + N))` je vždy **false**.

## <a name="partial_sort"></a>  partial_sort –

Uspořádá zadaný počet menších prvků v rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.

```cpp
template<class RandomAccessIterator>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last
    BinaryPredicate comp);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Iterátor s náhodným přístupem adresuje umístění prvního prvku v rozsahu který se má seřadit.

*sortEnd*<br/>
Náhodným přístupem iterátor, který adresuje umístění jedno místo za posledním prvkem v dílčí sadu který se má seřadit.

*poslední*<br/>
Iterátor s náhodným přístupem adresuje umístění jedno místo za posledním prvkem v rozsahu do částečně seřazeny.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání vyhovět pomocí po sobě jdoucí prvky v pořadí. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Prvky jsou ekvivalentní, ale ne nutně stejné, pokud je menší než ten druhý. `sort` Algoritmus není stabilní a nezaručuje, že relativní pořadí ekvivalentních prvků se zachovají. Algoritmus `stable_sort` zachovat původní pořadí.

Je složitost průměrné částečné řazení *O*((`last`- `first`) protokolu (`sortEnd`- `first`)).

### <a name="example"></a>Příklad

```cpp
// alg_partial_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
   return elem1 > elem2;
}

int main()
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   int ii;
   for ( ii = 0 ; ii <= 5 ; ii++ )
   {
      v1.push_back( 2 * ii +1 );
   }

   cout << "Original vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   partial_sort(v1.begin( ), v1.begin( ) + 6, v1.end( ) );
   cout << "Partially sorted vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To partially sort in descending order, specify binary predicate
   partial_sort(v1.begin( ), v1.begin( ) + 4, v1.end( ), greater<int>( ) );
   cout << "Partially resorted (greater) vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // A user-defined (UD) binary predicate can also be used
   partial_sort(v1.begin( ), v1.begin( ) + 8, v1.end( ),
UDgreater );
   cout << "Partially resorted (UDgreater) vector:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector:
v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Partially sorted vector:
v1 = ( 0 1 2 3 4 5 10 8 6 7 9 11 )
Partially resorted (greater) vector:
v1 = ( 11 10 9 8 0 1 2 3 4 5 6 7 )
Partially resorted (UDgreater) vector:
v1 = ( 11 10 9 8 7 6 5 4 0 1 2 3 )
```

## <a name="partial_sort_copy"></a>  partial_sort_copy –

Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu, kde zdrojové prvky jsou seřazeny buď podle binárního predikátu „menší než“ nebo jiného určeného binárního predikátu.

```cpp
template<class InputIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2 );

template<class InputIterator, class RandomAccessIterator, class BinaryPredicate>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2,
    BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku ve zdrojové oblasti.

*Příjmení1*<br/>
Vstupní iterátor, který adresuje umístění jedno místo za posledním prvkem ve zdrojové oblasti.

*first2*<br/>
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v seřazeného cílového rozsahu.

*Příjmení2*<br/>
Iterátor náhodného přístupu, který adresuje umístění jedno místo za posledním prvkem v seřazeného cílového rozsahu.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněny, pokud jsou dva prvky mají být provedeny, jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

Iterátor pro náhodný přístup adresující prvek v cílovém rozsahu jednu pozici za posledním prvkem, vložit ze zdrojového rozsahu.

### <a name="remarks"></a>Poznámky

Zdrojové a cílové rozsahy se nesmí překrývat a musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstků.

Binární predikát, musíte zadat přísné slabé seřazení, tak, že jsou řazeny prvky, které nejsou ekvivalentní, ale nejsou prvky, které jsou ekvivalentní. Dva prvky jsou ekvivalentní za méně než, ale ne nutně stejné, pokud je menší než ten druhý.

### <a name="example"></a>Příklad

```cpp
// alg_partial_sort_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    list<int> list1;
    vector<int>::iterator iter1, iter2;
    list<int>::iterator list1_Iter, list1_inIter;

    int i;
    for (i = 0; i <= 9; i++)
        v1.push_back(i);

    random_shuffle(v1.begin(), v1.end());

    list1.push_back(60);
    list1.push_back(50);
    list1.push_back(20);
    list1.push_back(30);
    list1.push_back(40);
    list1.push_back(10);

    cout << "Vector v1 = ( " ;
    for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;

    cout << "List list1 = ( " ;
    for (list1_Iter = list1.begin();
         list1_Iter!= list1.end();
         list1_Iter++)
        cout << *list1_Iter << " ";
    cout << ")" << endl;

    // Copying a partially sorted copy of list1 into v1
    vector<int>::iterator result1;
    result1 = partial_sort_copy(list1.begin(), list1.end(),
             v1.begin(), v1.begin() + 3);

    cout << "List list1 Vector v1 = ( " ;
    for (iter1 = v1.begin() ; iter1 != v1.end() ; iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;
    cout << "The first v1 element one position beyond"
         << "\n the last L 1 element inserted was " << *result1
         << "." << endl;

    // Copying a partially sorted copy of list1 into v2
    int ii;
    for (ii = 0; ii <= 9; ii++)
        v2.push_back(ii);

    random_shuffle(v2.begin(), v2.end());
    vector<int>::iterator result2;
    result2 = partial_sort_copy(list1.begin(), list1.end(),
             v2.begin(), v2.begin() + 6);

    cout << "List list1 into Vector v2 = ( " ;
    for (iter2 = v2.begin() ; iter2 != v2.end(); iter2++)
        cout << *iter2 << " ";
    cout << ")" << endl;
    cout << "The first v2 element one position beyond"
         << "\n the last L 1 element inserted was " << *result2
         << "." << endl;
}
```

## <a name="partition"></a>  oddíl

Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují.

```cpp
template<class BidirectionalIterator, class Predicate>
BidirectionalIterator partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    Predicate comp);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Obousměrný iterátor adresuje umístění prvního prvku v rozsahu k rozdělení na oddíly.

*poslední*<br/>
Obousměrný iterátor adresuje umístění jedno místo za poslední prvek v rozsahu k rozdělení na oddíly.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněny, pokud element má být klasifikované. Predikát přijímá jeden argument a vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor adresuje umístění prvního prvku v rozsahu pro nejsou splněna podmínka predikátu.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Elementy *a* *b* jsou ekvivalentní, ale stejně nemusí nutně prokázat, pokud obě *Pr* ( *a*, *b*) je hodnota false a *Pr* ( *b*, *a*) Pokud je hodnota false, kde *Pr* je zadán parametr predikátu. `partition` Algoritmus není stabilní a nezaručuje, že relativní pořadí ekvivalentních prvků se zachovají. Algoritmus `stable_ partition` zachovat původní pořadí.

Složitost je lineární: existují (`last` - `first`) aplikace *kompozice* a nejvýše (`last` - `first`) / 2 Zamění.

### <a name="example"></a>Příklad

```cpp
// alg_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value ) {
   return value > 5;
}

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 10 ; i++ )
   {
      v1.push_back( i );
   }
   random_shuffle( v1.begin( ), v1.end( ) );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Partition the range with predicate greater10
   partition ( v1.begin( ), v1.end( ), greater5 );
   cout << "The partitioned set of elements in v1 is: ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="partition_copy"></a>  partition_copy –

Zkopíruje prvky, pro které je podmínka **true** do jednoho cíle a pro které je podmínka **false** do jiného. Prvky musí pocházet ze zadaného rozsahu.

```cpp
template<class InputIterator, class OutputIterator1, class OutputIterator2, class Predicate>
pair<OutputIterator1, OutputIterator2>
    partition_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator1 dest1,
    OutputIterator2 dest2,
    Predicate pred);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor, který označuje začátek rozsahu mají kontrolují určitou podmínku.

*poslední*<br/>
Vstupní iterátor, který označuje konec rozsahu.

*dest1*<br/>
Výstupní iterátor použije ke zkopírování prvků, které vrátí hodnotu true pro podmínku testovány pomocí systému *_Pred*.

*dest2*<br/>
Výstupní iterátor použije ke zkopírování prvků, které vrací hodnotu false pro podmínku testovány pomocí systému *_Pred*.

*_Pred*<br/>
Podmínka pro testování. To poskytuje objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být testována. Predikát přijímá jeden argument a vrátí **true** nebo **false**.

### <a name="remarks"></a>Poznámky

Funkce šablony zkopíruje každý prvek `X` v `[first,last)` k `*dest1++` Pokud `_Pred(X)` má hodnotu true, nebo `*dest2++` Pokud tomu tak není. Vrátí `pair<OutputIterator1, OutputIterator2>(dest1, dest2)`.

## <a name="partition_point"></a>  partition_point

Vrátí první prvek v zadaném rozsahu, který nesplňuje podmínku. Prvky jsou seřazeny tak, aby ty, které splňují podmínku, předcházely těm, které ji nesplňují.

```cpp
template<class ForwardIterator, class Predicate>
ForwardIterator partition_point(
    ForwardIterator first,
    ForwardIterator last,
    Predicate comp);
```

### <a name="parameters"></a>Parametry

*první*<br/>
A `ForwardIterator` , který označuje začátek rozsahu mají kontrolují určitou podmínku.

*poslední*<br/>
A `ForwardIterator` , který označuje konec rozsahu.

*Kompozice*<br/>
Podmínka pro testování. To poskytuje objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněno elementu vyhledávaná. Predikát přijímá jeden argument a vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí `ForwardIterator` odkazující na první prvek, který nesplňuje podmínku testovaných funkcí *kompozice*, nebo vrátí *poslední* Pokud jeden není nalezena.

### <a name="remarks"></a>Poznámky

Funkce šablony najde první iterace `it` v `[first, last)` pro kterou `comp(*it)` je **false**. Sekvence musejí být seřazeny podle *comp*.

## <a name="pop_heap"></a>  pop_heap –

Odstraní největší prvek z přední části haldy až do předposlední pozice v rozsahu a ze zbývajících prvků vytvoří novou haldu.

```cpp
template<class RandomAccessIterator>
void pop_heap( RandomAccessIterator first, RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void pop_heap(RandomAccessIterator first, RandomAccessIterator last, BinaryPredicate comp);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v haldě.

*poslední*<br/>
Iterátor náhodného přístupu, který adresuje umístění jedno místo za posledním prvkem v haldě.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="remarks"></a>Poznámky

`pop_heap` Algoritmus je inverzní operace prováděné push_heap – algoritmus, ve kterém je element na pozici další poslední rozsahu do haldy, která zahrnuje předchozí prvky v rozsahu, v případě, když elementu se přidávají do haldy je větší než všechny prvky již v haldě.

Haldy má dvě vlastnosti:

- Vždy je největší první prvek.

- Elementy mohou přidat nebo odebrat logaritmické včas.

Haldy jsou ideální způsob, jak implementovat prioritní fronty a používají se v implementaci adaptér kontejneru standardní knihovny C++ [priority_queue – třída](../standard-library/priority-queue-class.md).

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Oblast s výjimkou nově přidaný prvek na konci musí být haldu.

Složitost se používá logaritmické, maximálně vyžadování protokolu (* naposledy - nejprve *) porovnání.

### <a name="example"></a>Příklad

```cpp
// alg_pop_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()  {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 1 ; i <= 9 ; i++ )
      v1.push_back( i );

   // Make v1 a heap with default less than ordering
   random_shuffle( v1.begin( ), v1.end( ) );
   make_heap ( v1.begin( ), v1.end( ) );
   cout << "The heaped version of vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Add an element to the back of the heap
   v1.push_back( 10 );
   push_heap( v1.begin( ), v1.end( ) );
   cout << "The reheaped v1 with 10 added is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove the largest element from the heap
   pop_heap( v1.begin( ), v1.end( ) );
   cout << "The heap v1 with 10 removed is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl << endl;

   // Make v1 a heap with greater-than ordering with a 0 element
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
   v1.push_back( 0 );
   push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The 'greater than' reheaped v1 puts the smallest "
        << "element first:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Application of pop_heap to remove the smallest element
   pop_heap( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The 'greater than' heaped v1 with the smallest element\n "
        << "removed from the heap is: ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="prev_permutation"></a>  prev_permutation –

Znovu uspořádá prvky v rozsahu tak, aby původní pořadí bylo nahrazeno lexikograficky předchozí větší permutací pokud existuje, kde představu o předchozí může být určen binárním predikátem.

```cpp
template<class BidirectionalIterator>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate comp);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Obousměrný iterátor odkazující na pozici prvního prvku v rozsahu pro být permutovanou funkci.

*poslední*<br/>
Obousměrný iterátor odkazující na umístění jedno místo za posledním prvkem v rozsahu pro být permutovanou funkci.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání vyhovět pomocí po sobě jdoucí prvky v pořadí. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

**true** Pokud lexikograficky předchozí permutaci existuje a byl nahrazen původní pořadí rozsah; v opačném případě **false**, v takovém případě řazení se transformuje na lexikograficky největší permutaci.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Výchozí binární predikát je menší než a prvky v rozsahu musí být menší – než srovnatelná s hodnotou Ujistěte se, že předchozí permutaci dobře definované.

Složitost je lineární, přičemž maximální (`last` -  `first`) / 2 Zamění.

### <a name="example"></a>Příklad

```cpp
// alg_prev_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt {
public:
   CInt( int n = 0 ) : m_nVal( n ){}
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
   CInt&   operator=( const CInt& rhs ) {m_nVal =
   rhs.m_nVal; return *this;}
   bool operator<( const CInt& rhs ) const
      {return ( m_nVal < rhs.m_nVal );}
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
   int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs ) {
   osIn << "CInt( " << rhs.m_nVal << " )";
   return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 ) {
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
};

int main() {
   // Reordering the elements of type CInt in a deque
   // using the prev_permutation algorithm
   CInt c1 = 1, c2 = 5, c3 = 10;
   bool deq1Result;
   deque<CInt> deq1, deq2, deq3;
   deque<CInt>::iterator d1_Iter;

   deq1.push_back ( c1 );
   deq1.push_back ( c2 );
   deq1.push_back ( c3 );

   cout << "The original deque of CInts is deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl;

   deq1Result = prev_permutation ( deq1.begin( ), deq1.end( ) );

   if ( deq1Result )
      cout << "The lexicographically previous permutation "
           << "exists and has \nreplaced the original "
           << "ordering of the sequence in deq1." << endl;
   else
      cout << "The lexicographically previous permutation doesn't "
           << "exist\n and the lexicographically "
           << "smallest permutation\n has replaced the "
           << "original ordering of the sequence in deq1." << endl;

   cout << "After one application of prev_permutation,\n deq1 = (";
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
      cout << " " << *d1_Iter << ",";
   d1_Iter = --deq1.end( );
   cout << " " << *d1_Iter << " )." << endl << endl;

   // Permutating vector elements with binary function mod_lesser
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = -3 ; i <= 3 ; i++ )
      v1.push_back( i );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );

   cout << "After the first prev_permutation, vector v1 is:\n v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   int iii = 1;
   while ( iii <= 5 ) {
      prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );
      cout << "After another prev_permutation of vector v1,\n v1 =   ( " ;
      for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
         cout << *Iter1  << " ";
      cout << ")." << endl;
      iii++;
   }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 1 ), CInt( 5 ), CInt( 10 ) ).
The lexicographically previous permutation doesn't exist
and the lexicographically smallest permutation
has replaced the original ordering of the sequence in deq1.
After one application of prev_permutation,
deq1 = ( CInt( 10 ), CInt( 5 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first prev_permutation, vector v1 is:
v1 = ( -3 -2 0 3 2 1 -1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 3 -1 2 1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 3 -1 1 2 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 3 1 -1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 -1 3 1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 -1 1 3 ).
```

## <a name="push_heap"></a>  push_heap –

Přidá prvek, který je na konci rozsahu, do stávající haldy, která zahrnuje předchozí prvky daného rozsahu.

```cpp
template<class RandomAccessIterator>
void push_heap( RandomAccessIterator first, RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void push_heap( RandomAccessIterator first, RandomAccessIterator last, BinaryPredicate comp);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v haldě.

*poslední*<br/>
Iterátor náhodného přístupu, který adresuje umístění jedno místo za poslední prvek v rozsahu, který chcete převést na haldu.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="remarks"></a>Poznámky

Element musí nejprve být posunut zpět na konec existující haldu a poté algoritmus se používá k přidání tohoto prvku do stávající haldy.

Haldy má dvě vlastnosti:

- Vždy je největší první prvek.

- Elementy mohou přidat nebo odebrat logaritmické včas.

Haldy jsou ideální způsob, jak implementovat prioritní fronty a používají se v implementaci adaptér kontejneru standardní knihovny C++ [priority_queue – třída](../standard-library/priority-queue-class.md).

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Oblast s výjimkou nově přidaný prvek na konci musí být haldu.

Složitost se používá logaritmické, maximálně vyžadování protokolu ( *naposledy - nejprve*) porovnání.

### <a name="example"></a>Příklad

```cpp
// alg_push_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 1 ; i <= 9 ; i++ )
      v1.push_back( i );

   random_shuffle( v1.begin( ), v1.end( ) );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Make v1 a heap with default less than ordering
   make_heap ( v1.begin( ), v1.end( ) );
   cout << "The heaped version of vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Add an element to the heap
   v1.push_back( 10 );
   cout << "The heap v1 with 10 pushed back is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   push_heap( v1.begin( ), v1.end( ) );
   cout << "The reheaped v1 with 10 added is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl << endl;

   // Make v1 a heap with greater than ordering
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The greater-than heaped version of v1 is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   v1.push_back(0);
   cout << "The greater-than heap v1 with 11 pushed back is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "The greater than reheaped v1 with 11 added is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="random_shuffle"></a>  random_shuffle –

Zastaralé funkce std::random_shuffle() nahrazuje [std::shuffle](../standard-library/algorithm-functions.md#shuffle). Příklad kódu a další informace najdete v tématu [ \<náhodné >](../standard-library/random.md) a účtování Stackoverflow [Proč jsou metody std::random_shuffle zastaralé v C ++ 14?](http://go.microsoft.com/fwlink/p/?linkid=397954).

## <a name="remove"></a>  odebrat

Odstraní zadanou hodnotu z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator remove(ForwardIterator first, ForwardIterator last, const Type& val);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, ze kterého budou odebrány elementy.

*poslední*<br/>
Dopředný iterátor, který adresuje umístění jedno za posledním prvkem v rozsahu, ze kterého budou odebrány elementy.

*Val*<br/>
Hodnota, která se má odebrat z rozsahu.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor adresující nová koncová pozice upravený rozsah, jedno místo za posledním prvkem pořadí zbývajících zadanou hodnotu.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Pořadí prvků neodeberou zůstává stabilní.

`operator==` Používá k určení rovnosti mezi elementy musí uložit vztahu ekvivalence mezí jejími operandy.

Složitost je lineární; Existují (`last` - `first`) porovnání rovnosti.

[List – třída](../standard-library/list-class.md) má mnohem efektivnější členské funkce verzi `remove`, což také relinks ukazatele.

### <a name="example"></a>Příklad

```cpp
// alg_remove.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1, Iter2, new_end;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );
   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove elements with a value of 7
   new_end = remove ( v1.begin( ), v1.end( ), 7 );

   cout << "Vector v1 with value 7 removed is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To change the sequence size, use erase
   v1.erase (new_end, v1.end( ) );

   cout << "Vector v1 resized with value 7 removed is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="remove_copy"></a>  remove_copy –

Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu. Prvky zadané hodnoty zkopírovány nejsou. Nenaruší pořadí zbývajících prvků a nevrátí konec nového cílového rozsahu.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator remove_copy(InputIterator first, InputIterator last, OutputIterator result, const Type& val);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku v rozsahu, ze kterého budou odebrány elementy.

*poslední*<br/>
Vstupní iterátor adresující jedna pozice za posledním prvkem v rozsahu, ze kterého budou odebrány elementy.

*výsledek*<br/>
Výstupní iterace adresující pozici prvního prvku v cílovém rozsahu, do které budou odebrány elementy.

*Val*<br/>
Hodnota, která se má odebrat z rozsahu.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor adresující nová koncová pozice cílového rozsahu, jedno místo za posledním prvkem kopii pořadí zbývajících zadanou hodnotu.

### <a name="remarks"></a>Poznámky

Zdrojové a cílové rozsahy odkazuje musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

V cílové oblasti tak, aby obsahovala zbývajících prvků, které se zkopírují po odebrání elementů zadaná hodnota musí být dostatek místa.

Pořadí prvků neodeberou zůstává stabilní.

`operator==` Používá k určení rovnosti mezi elementy musí uložit vztahu ekvivalence mezí jejími operandy.

Složitost je lineární; Existují (`last` - `first`) porovnání rovnosti a maximálně (`last` - `first`) přiřazení.

### <a name="example"></a>Příklad

```cpp
// alg_remove_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2(10);
   vector <int>::iterator Iter1, Iter2, new_end;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle (v1.begin( ), v1.end( ) );
   cout << "The original vector v1 is:     ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove elements with a value of 7
   new_end = remove_copy ( v1.begin( ), v1.end( ), v2.begin( ), 7 );

   cout << "Vector v1 is left unchanged as ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is a copy of v1 with the value 7 removed:\n ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;
}
```

## <a name="remove_copy_if"></a>  remove_copy_if –

Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu. Prvky splňující predikát zkopírovány nejsou. Nenaruší pořadí zbývajících prvků a nevrátí konec nového cílového rozsahu.

```cpp
template<class InputIterator, class OutputIterator, class Predicate>
OutputIterator remove_copy_if(InputIterator first, InputIterator Last, OutputIterator result, Predicate pred);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku v rozsahu, ze kterého budou odebrány elementy.

*poslední*<br/>
Vstupní iterátor adresující jedna pozice za posledním prvkem v rozsahu, ze kterého budou odebrány elementy.

*výsledek*<br/>
Výstupní iterace adresující pozici prvního prvku v cílovém rozsahu, do které budou odebrány elementy.

*_Pred*<br/>
Unární predikát, který musí být splněny, je hodnota elementu se nahradí.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor adresující nová koncová pozice cílového rozsahu, jedno místo za posledním prvkem pořadí zbývajících zdarma prvky splňující predikát.

### <a name="remarks"></a>Poznámky

Odkazovaný zdrojový rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

V cílové oblasti tak, aby obsahovala zbývajících prvků, které se zkopírují po odebrání elementů zadaná hodnota musí být dostatek místa.

Pořadí prvků neodeberou zůstává stabilní.

`operator==` Používá k určení rovnosti mezi elementy musí uložit vztahu ekvivalence mezí jejími operandy.

Složitost je lineární: existují (`last` - `first`) porovnání rovnosti a maximálně (`last` - `first`) přiřazení.

Informace o chování těchto funkcí najdete v tématu [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// alg_remove_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
   return value > 6;
}

int main() {
   using namespace std;
   vector <int> v1, v2(10);
   vector <int>::iterator Iter1, Iter2, new_end;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );
   cout << "The original vector v1 is:      ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove elements with a value greater than 6
   new_end = remove_copy_if ( v1.begin( ), v1.end( ),
      v2.begin( ), greater6 );

   cout << "After the appliation of remove_copy_if to v1,\n "
        << "vector v1 is left unchanged as ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is a copy of v1 with values greater "
        << "than 6 removed:\n ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != new_end ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;
}
```

## <a name="remove_if"></a>  remove_if –

Odstraní prvky, které splňují predikát, z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.

```cpp
template<class ForwardIterator, class Predicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor odkazující na pozici prvního prvku v rozsahu, ze kterého budou odebrány elementy.

*poslední*<br/>
Dopředný iterátor odkazující na jedna pozice za posledním prvkem v rozsahu, ze kterého budou odebrány elementy.

*_Pred*<br/>
Unární predikát, který musí být splněny, je hodnota elementu se nahradí.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor adresující nová koncová pozice upravený rozsah, jedno místo za posledním prvkem pořadí zbývajících zadanou hodnotu.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Pořadí prvků neodeberou zůstává stabilní.

`operator==` Používá k určení rovnosti mezi elementy musí uložit vztahu ekvivalence mezí jejími operandy.

Složitost je lineární: existují (`last` - `first`) porovnání rovnosti.

Seznam obsahuje efektivnější verze členské funkce odebrání, které relinks ukazatele.

### <a name="example"></a>Příklad

```cpp
// alg_remove_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
   return value > 6;
}

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2, new_end;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );
   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Remove elements satisfying predicate greater6
   new_end = remove_if (v1.begin( ), v1.end( ), greater6 );

   cout << "Vector v1 with elements satisfying greater6 removed is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To change the sequence size, use erase
   v1.erase (new_end, v1.end( ) );

   cout << "Vector v1 resized elements satisfying greater6 removed is\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="replace"></a>  nahradit

Zkontroluje každý prvek v rozsahu a nahradí jej, pokud odpovídá zadané hodnotě.

```cpp
template<class ForwardIterator, class Type>
void replace(
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor odkazující na pozici prvního prvku v rozsahu, ze kterého se nahrazují elementy.

*poslední*<br/>
Dopředný iterátor odkazující na jedna pozice za posledním prvkem v rozsahu, ze kterého se nahrazují elementy.

*_OldVal*<br/>
Původní hodnota prvky se nahradí.

*_NewVal*<br/>
Nová hodnota elementy s hodnotou staré přiřazení.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Pořadí prvků není nahrazena zůstává stabilní.

`operator==` Používá k určení rovnosti mezi elementy musí uložit vztahu ekvivalence mezí jejími operandy.

Složitost je lineární; Existují (`last` - `first`) porovnání rovnosti a maximálně (`last` - `first`) přiřazení nové hodnoty.

### <a name="example"></a>Příklad

```cpp
// alg_replace.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle (v1.begin( ), v1.end( ) );
   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements with a value of 7 with a value of 700
   replace (v1.begin( ), v1.end( ), 7 , 700);

   cout << "The vector v1 with a value 700 replacing that of 7 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="replace_copy"></a>  replace_copy –

Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu odpovídá zadané hodnotě.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator replace_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor odkazující na pozici prvního prvku v rozsahu, ze kterého se nahrazují elementy.

*poslední*<br/>
Vstupní iterátor odkazující na umístění jedno místo za posledním prvkem v rozsahu, ze kterého se nahrazují elementy.

*výsledek*<br/>
Výstupní iterátor odkazující na první prvek v cílovém rozsahu, do které zkopíroval upravený sekvence prvků.

*_OldVal*<br/>
Původní hodnota prvky se nahradí.

*_NewVal*<br/>
Nová hodnota elementy s hodnotou staré přiřazení.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor odkazující na umístění jedno místo za posledním prvkem v cílovém rozsahu, do které zkopíroval upravený sekvence prvků.

### <a name="remarks"></a>Poznámky

Odkazovaný zdrojové a cílové rozsahy se nesmí překrývat a musí být platné: všechny odkazy musí být možné nepřímo odkazovat a v rámci sekvencí je poslední pozice dosažitelná z první pomocí přírůstků.

Pořadí prvků není nahrazena zůstává stabilní.

`operator==` Používá k určení rovnosti mezi elementy musí uložit vztahu ekvivalence mezí jejími operandy.

Složitost je lineární: existují (`last` - `first`) porovnání rovnosti a maximálně (`last` - `first`) přiřazení nové hodnoty.

### <a name="example"></a>Příklad

```cpp
// alg_replace_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;
   list <int> L1 (15);
   vector <int>::iterator Iter1;
   list <int>::iterator L_Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );

   int iii;
   for ( iii = 0 ; iii <= 15 ; iii++ )
      v1.push_back( 1 );

   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements in one part of a vector with a value of 7
   // with a value of 70 and copy into another part of the vector
   replace_copy ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -15, 7 , 70);

   cout << "The vector v1 with a value 70 replacing that of 7 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements in a vector with a value of 70
   // with a value of 1 and copy into a list
   replace_copy ( v1.begin( ), v1.begin( ) + 14,L1.begin( ), 7 , 1);

   cout << "The list copy L1 of v1 with the value 0 replacing "
        << "that of 7 is:\n ( " ;
   for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
      cout << *L_Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="replace_copy_if"></a>  replace_copy_if –

Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu splňuje zadaný predikát.

```cpp
template<class InputIterator, class OutputIterator, class Predicate, class Type>
OutputIterator replace_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Predicate pred,
    const Type& val);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor odkazující na pozici prvního prvku v rozsahu, ze kterého se nahrazují elementy.

*poslední*<br/>
Vstupní iterátor odkazující na umístění jedno místo za posledním prvkem v rozsahu, ze kterého se nahrazují elementy.

*výsledek*<br/>
Výstupní iterátor odkazující na pozici prvního prvku v cílovém rozsahu, do které se kopírují prvky.

*_Pred*<br/>
Unární predikát, který musí být splněny, je hodnota elementu se nahradí.

*Val*<br/>
Nová hodnota přiřazením na elementy, jejichž původní hodnota splňuje predikát.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor odkazující na umístění jedno místo za posledním prvkem v cílovém rozsahu, do které zkopíroval upravený sekvence prvků.

### <a name="remarks"></a>Poznámky

Odkazovaný zdrojové a cílové rozsahy se nesmí překrývat a musí být platné: všechny odkazy musí být možné nepřímo odkazovat a v rámci sekvencí je poslední pozice dosažitelná z první pomocí přírůstků.

Pořadí prvků není nahrazena zůstává stabilní.

`operator==` Používá k určení rovnosti mezi elementy musí uložit vztahu ekvivalence mezí jejími operandy.

Složitost je lineární; Existují (`last` - `first`) porovnání rovnosti a maximálně (`last` - `first`) přiřazení nové hodnoty.

### <a name="example"></a>Příklad

```cpp
// alg_replace_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
   return value > 6;
}

int main() {
   using namespace std;
   vector <int> v1;
   list <int> L1 (13);
   vector <int>::iterator Iter1;
   list <int>::iterator L_Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );

   int iii;
   for ( iii = 0 ; iii <= 13 ; iii++ )
      v1.push_back( 1 );

   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements with a value of 7 in the 1st half of a vector
   // with a value of 70 and copy it into the 2nd half of the vector
   replace_copy_if ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -14,
      greater6 , 70);

   cout << "The vector v1 with values of 70 replacing those greater"
        << "\n than 6 in the 1st half & copied into the 2nd half is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements in a vector with a value of 70
   // with a value of 1 and copy into a list
   replace_copy_if ( v1.begin( ), v1.begin( ) + 13,L1.begin( ),
      greater6 , -1 );

   cout << "A list copy of vector v1 with the value -1\n replacing "
        << "those greater than 6 is:\n ( " ;
   for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
      cout << *L_Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="replace_if"></a>  replace_if –

Zkontroluje každý prvek v rozsahu a nahradí jej, pokud splňuje zadaný predikát.

```cpp
template<class ForwardIterator, class Predicate, class Type>
void replace_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred,
    const Type& val);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor odkazující na pozici prvního prvku v rozsahu, ze kterého se nahrazují elementy.

*poslední*<br/>
Iterátorem ukazujícím na jednu pozici za posledním prvkem v rozsahu, ze kterého se nahrazují elementy.

*_Pred*<br/>
Unární predikát, který musí být splněny, je hodnota elementu se nahradí.

*Val*<br/>
Nová hodnota přiřazením na elementy, jejichž původní hodnota splňuje predikát.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Pořadí prvků není nahrazena zůstává stabilní.

Algoritmus `replace_if` je generalizace algoritmus `replace`, povolení žádné predikátu zadání místo rovnosti na zadanou hodnotu konstanty.

`operator==` Používá k určení rovnosti mezi elementy musí uložit vztahu ekvivalence mezí jejími operandy.

Složitost je lineární: existují (`last` - `first`) porovnání rovnosti a maximálně (`last` - `first`) přiřazení nové hodnoty.

### <a name="example"></a>Příklad

```cpp
// alg_replace_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
   return value > 6;
}

int main() {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
      v1.push_back( 7 );

   random_shuffle ( v1.begin( ), v1.end( ) );
   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Replace elements satisfying the predicate greater6
   // with a value of 70
   replace_if ( v1.begin( ), v1.end( ), greater6 , 70);

   cout << "The vector v1 with a value 70 replacing those\n "
        << "elements satisfying the greater6 predicate is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="reverse"></a>  reverzní

Obrátí pořadí prvků v rozsahu.

```cpp
template<class BidirectionalIterator>
void reverse(BidirectionalIterator first, BidirectionalIterator last);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Obousměrný iterátor odkazující na pozici prvního prvku v rozsahu, ve kterém prvky jsou právě permutovanou funkci.

*poslední*<br/>
Obousměrný iterátor odkazující na umístění jedno místo za posledním prvkem v rozsahu, ve kterém prvky jsou právě permutovanou funkci.

### <a name="remarks"></a>Poznámky

Odkazovaný zdrojový rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

### <a name="example"></a>Příklad

```cpp
// alg_reverse.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Reverse the elements in the vector
   reverse (v1.begin( ), v1.end( ) );

   cout << "The modified vector v1 with values reversed is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 0 1 2 3 4 5 6 7 8 9 ).
The modified vector v1 with values reversed is:
( 9 8 7 6 5 4 3 2 1 0 ).
```

## <a name="reverse_copy"></a>  reverse_copy –

Obrátí pořadí prvků ve zdrojovém rozsahu při kopírování do cílového rozsahu.

```cpp
template<class BidirectionalIterator, class OutputIterator>
OutputIterator reverse_copy(
    BidirectionalIterator first,
    BidirectionalIterator Last,
    OutputIterator result);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Obousměrný iterátor odkazující na pozici první prvek ve zdrojovém rozsahu, ve kterém prvky jsou právě permutovanou funkci.

*poslední*<br/>
Obousměrný iterátor odkazující na umístění jedno místo za posledním prvkem ve zdrojové oblasti, ve kterém prvky jsou právě permutovanou funkci.

*výsledek*<br/>
Výstupní iterátor odkazující na pozici prvního prvku v cílovém rozsahu, do které se kopírují prvky.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor odkazující na umístění jedno místo za posledním prvkem v cílovém rozsahu, do které zkopíroval upravený sekvence prvků.

### <a name="remarks"></a>Poznámky

Zdrojové a cílové rozsahy odkazuje musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

### <a name="example"></a>Příklad

```cpp
// alg_reverse_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1, v2( 10 );
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = 0 ; i <= 9 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Reverse the elements in the vector
   reverse_copy (v1.begin( ), v1.end( ), v2.begin( ) );

   cout << "The copy v2 of the reversed vector v1 is:\n ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   cout << "The original vector v1 remains unmodified as:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;
}
```

## <a name="rotate"></a>  Otočit o

Vymění prvky ve dvou sousedních rozsazích.

```cpp
template<class ForwardIterator>
void rotate(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu obměnit.

*střední*<br/>
Dopředný iterátor, který definuje hranici rozsahu, který adresuje umístění prvního prvku v druhé části rozsahu, jehož prvky mají vyměnit s těmi v první části rozsahu.

*poslední*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu obměnit.

### <a name="remarks"></a>Poznámky

Rozsahy odkazuje musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Složitost je lineární s maximálně (`last` - `first`) Zamění.

### <a name="example"></a>Příklad

```cpp
// alg_rotate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;
   deque <int> d1;
   vector <int>::iterator v1Iter1;
   deque<int>::iterator d1Iter1;

   int i;
   for ( i = -3 ; i <= 5 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii =0 ; ii <= 5 ; ii++ )
   {
      d1.push_back( ii );
   }

   cout << "Vector v1 is ( " ;
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
      cout << *v1Iter1  << " ";
   cout << ")." << endl;

   rotate ( v1.begin( ), v1.begin( ) + 3 , v1.end( ) );
   cout << "After rotating, vector v1 is ( " ;
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
      cout << *v1Iter1  << " ";
   cout << ")." << endl;

   cout << "The original deque d1 is ( " ;
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
      cout << *d1Iter1  << " ";
   cout << ")." << endl;

   int iii = 1;
   while ( iii <= d1.end( ) - d1.begin( ) ) {
      rotate ( d1.begin( ), d1.begin( ) + 1 , d1.end( ) );
      cout << "After the rotation of a single deque element to the back,\n d1 is   ( " ;
      for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
         cout << *d1Iter1  << " ";
      cout << ")." << endl;
      iii++;
   }
}
```

```Output
Vector v1 is ( -3 -2 -1 0 1 2 3 4 5 ).
After rotating, vector v1 is ( 0 1 2 3 4 5 -3 -2 -1 ).
The original deque d1 is ( 0 1 2 3 4 5 ).
After the rotation of a single deque element to the back,
d1 is   ( 1 2 3 4 5 0 ).
After the rotation of a single deque element to the back,
d1 is   ( 2 3 4 5 0 1 ).
After the rotation of a single deque element to the back,
d1 is   ( 3 4 5 0 1 2 ).
After the rotation of a single deque element to the back,
d1 is   ( 4 5 0 1 2 3 ).
After the rotation of a single deque element to the back,
d1 is   ( 5 0 1 2 3 4 ).
After the rotation of a single deque element to the back,
d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="rotate_copy"></a>  rotate_copy –

Vymění prvky ve dvou sousedních rozsazích v rámci zdrojového rozsahu a zkopíruje výsledek do cílového rozsahu.

```cpp
template<class ForwardIterator, class OutputIterator>
OutputIterator rotate_copy(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last,
    OutputIterator result );

```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu obměnit.

*střední*<br/>
Dopředný iterátor, který definuje hranici rozsahu, který adresuje umístění prvního prvku v druhé části rozsahu, jehož prvky mají vyměnit s těmi v první části rozsahu.

_ *Poslední* dopředný iterátor adresuje umístění jedno místo za posledním prvkem v rozsahu otočen.

*výsledek*<br/>
Výstupní iterace adresující pozici prvního prvku v cílové oblasti.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterace adresující jedna pozice za posledním prvkem v cílové oblasti.

### <a name="remarks"></a>Poznámky

Rozsahy odkazuje musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Složitost je lineární s maximálně (`last` - `first`) Zamění.

### <a name="example"></a>Příklad

```cpp
// alg_rotate_copy.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1 , v2 ( 9 );
   deque <int> d1 , d2 ( 6 );
   vector <int>::iterator v1Iter , v2Iter;
   deque<int>::iterator d1Iter , d2Iter;

   int i;
   for ( i = -3 ; i <= 5 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii =0 ; ii <= 5 ; ii++ )
      d1.push_back( ii );

   cout << "Vector v1 is ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
      cout << *v1Iter  << " ";
   cout << ")." << endl;

   rotate_copy ( v1.begin( ), v1.begin( ) + 3 , v1.end( ), v2.begin( ) );
   cout << "After rotating, the vector v1 remains unchanged as:\n v1 = ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
      cout << *v1Iter  << " ";
   cout << ")." << endl;

   cout << "After rotating, the copy of vector v1 in v2 is:\n v2 = ( " ;
   for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ;v2Iter ++ )
      cout << *v2Iter  << " ";
   cout << ")." << endl;

   cout << "The original deque d1 is ( " ;
   for ( d1Iter = d1.begin( ) ; d1Iter != d1.end( ) ;d1Iter ++ )
      cout << *d1Iter  << " ";
   cout << ")." << endl;

   int iii = 1;
   while ( iii <= d1.end( ) - d1.begin( ) )
   {
      rotate_copy ( d1.begin( ), d1.begin( ) + iii , d1.end( ), d2.begin( ) );
      cout << "After the rotation of a single deque element to the back,\n d2 is   ( " ;
      for ( d2Iter = d2.begin( ) ; d2Iter != d2.end( ) ;d2Iter ++ )
         cout << *d2Iter  << " ";
      cout << ")." << endl;
      iii++;
   }
}
```

## <a name="search"></a>  Hledání

Vyhledá první výskyt sekvence v cílovém rozsahu, jejíž prvky jsou rovné prvkům v dané sekvenci prvků nebo jejíž prvky jsou ekvivalentní ve smyslu určeném binárním predikátem prvkům v dané sekvenci.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class Predicate>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2
    Predicate comp);

```

### <a name="parameters"></a>Parametry

*first1*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu pro hledání.

*Příjmení1*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v oblasti pro hledání.

*first2*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu lze porovnat.

*Příjmení2*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu lze porovnat.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněny, pokud jsou dva prvky mají být provedeny, jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje umístění prvního prvku první dílčí sekvenci, který odpovídá zadané posloupnosti nebo, který je ekvivalentní ve smyslu určeném binárním predikátem.

### <a name="remarks"></a>Poznámky

`operator==` Používá k určení shody mezi prvkem a zadaná hodnota musí uložit vztahu ekvivalence mezí jejími operandy.

Rozsahy odkazuje musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci každé posloupnosti je poslední pozice dosažitelná z první pomocí přírůstků.

Průměrná složitost je lineární s ohledem na velikost prohledávaného rozsahu a nejhorší případ složitost je lineární s ohledem na velikost pořadí vyhledávaná také.

### <a name="example"></a>Příklad

```cpp
// alg_search.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice (int elem1, int elem2 )
{
   return 2 * elem1 == elem2;
}

int main() {
   using namespace std;
   vector <int> v1, v2;
   list <int> L1;
   vector <int>::iterator Iter1, Iter2;
   list <int>::iterator L1_Iter, L1_inIter;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   int ii;
   for ( ii = 4 ; ii <= 5 ; ii++ )
   {
      L1.push_back( 5 * ii );
   }

   int iii;
   for ( iii = 2 ; iii <= 4 ; iii++ )
   {
      v2.push_back( 10 * iii );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "List L1 = ( " ;
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
      cout << *L1_Iter << " ";
   cout << ")" << endl;

   cout << "Vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
      cout << ")" << endl;

   // Searching v1 for first match to L1 under identity
   vector <int>::iterator result1;
   result1 = search (v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

   if ( result1 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is at least one match of L1 in v1"
           << "\n and the first one begins at "
           << "position "<< result1 - v1.begin( ) << "." << endl;

   // Searching v1 for a match to L1 under the binary predicate twice
   vector <int>::iterator result2;
   result2 = search  (v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

   if ( result2 == v1.end( ) )
      cout << "There is no match of L1 in v1."
           << endl;
   else
      cout << "There is a sequence of elements in v1 that "
           << "are equivalent\n to those in v2 under the binary "
           << "predicate twice\n and the first one begins at position "
           << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 20 25 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
and the first one begins at position 4.
There is a sequence of elements in v1 that are equivalent
to those in v2 under the binary predicate twice
and the first one begins at position 2.
```

## <a name="search_n"></a>  search_n –

Vyhledá první dílčí sekvenci v rozsahu zadaného počtu prvků s konkrétní hodnotou nebo vztahem k dané hodnotě podle binárního predikátu.

```cpp
template<class ForwardIterator1, class Diff2, class Type>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& val);

template<class ForwardIterator1, class Diff2, class Type, class BinaryPredicate>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& val,
    BinaryPredicate comp);

```

### <a name="parameters"></a>Parametry

*first1*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu pro hledání.

*Příjmení1*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v oblasti pro hledání.

*Počet*<br/>
Velikost k dílčí sekvenci vyhledaly.

*Val*<br/>
Hodnota prvků v sekvenci vyhledaly.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněny, pokud jsou dva prvky mají být provedeny, jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje umístění prvního prvku první dílčí sekvenci, který odpovídá zadané posloupnosti nebo, který je ekvivalentní ve smyslu určeném binárním predikátem.

### <a name="remarks"></a>Poznámky

`operator==` Používá k určení shody mezi prvkem a zadaná hodnota musí uložit vztahu ekvivalence mezí jejími operandy.

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Složitost je lineární s ohledem na velikost hledaný.

### <a name="example"></a>Příklad

```cpp
// alg_search_n.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is 1/2 of the first
bool one_half ( int elem1, int elem2 )
{
   return elem1 == 2 * elem2;
}

int main()
{
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   for ( i = 0 ; i <= 2 ; i++ )
   {
      v1.push_back( 5  );
   }

   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   for ( i = 0 ; i <= 2 ; i++ )
   {
      v1.push_back( 10  );
   }

   cout << "Vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // Searching v1 for first match to (5 5 5) under identity
   vector <int>::iterator result1;
   result1 = search_n ( v1.begin( ), v1.end( ), 3, 5 );

   if ( result1 == v1.end( ) )
      cout << "There is no match for a sequence ( 5 5 5 ) in v1."
           << endl;
   else
      cout << "There is at least one match of a sequence ( 5 5 5 )"
           << "\n in v1 and the first one begins at "
           << "position "<< result1 - v1.begin( ) << "." << endl;

   // Searching v1 for first match to (5 5 5) under one_half
   vector <int>::iterator result2;
   result2 = search_n (v1.begin( ), v1.end( ), 3, 5, one_half );

   if ( result2 == v1.end( ) )
      cout << "There is no match for a sequence ( 5 5 5 ) in v1"
           << " under the equivalence predicate one_half." << endl;
   else
      cout << "There is a match of a sequence ( 5 5 5 ) "
           << "under the equivalence\n predicate one_half "
           << "in v1 and the first one begins at "
           << "position "<< result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 5 5 5 0 5 10 15 20 25 10 10 10 )
There is at least one match of a sequence ( 5 5 5 )
in v1 and the first one begins at position 6.
There is a match of a sequence ( 5 5 5 ) under the equivalence
predicate one_half in v1 and the first one begins at position 15.
```

## <a name="set_difference"></a>  set_difference –

Sjednotí všechny prvky, které patří do jednoho seřazeného zdrojového rozsahu, ale nikoli do druhého seřazeného zdrojového rozsahu, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_difference(
    InputIterator1  first1,
    InputIterator1  last1,
    InputIterator2  first2,
    InputIterator2  last2,
    OutputIterator  result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator set_difference(
    InputIterator1  first1,
    InputIterator1  last1,
    InputIterator2  first2,
    InputIterator2  last2,
    OutputIterator  result,
    BinaryPredicate  comp );
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku v prvních dvou seřazených zdrojových rozsahů spojené a rozděleny na jeden rozsah představující rozdíl dvou zdrojových rozsahů.

*Příjmení1*<br/>
Vstupní iterátor adresuje umístění jedno místo za posledním prvkem v první ze dvou seřazených zdrojových rozsahů spojené a rozděleny na jeden rozsah představující rozdíl dvou zdrojových rozsahů.

*first2*<br/>
Vstupní iterátor adresující pozici prvního prvku v druhé dvě po sobě jdoucích seřazené zdrojových rozsahů spojené a rozděleny na jeden rozsah představující rozdíl dvou zdrojových rozsahů.

*Příjmení2*<br/>
Vstupní iterátor adresující poslední jedna pozice po posledním prvku v druhé dvě po sobě jdoucích seřazené zdrojových rozsahů spojené a rozděleny na jeden rozsah představující rozdíl dvou zdrojových rozsahů.

*výsledek*<br/>
Výstupní iterace adresující pozici prvního prvku v cílové oblasti, ve kterém mají být spojeny do jednoho seřazeného rozsahu představuje rozdíl dvou zdrojových rozsahů dvou zdrojových rozsahů.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je větší než jiný. Binární predikát přijímá dva argumenty a by měl vrátit **true** při prvním prvkem je menší než druhý prvek a **false** jinak.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresuje umístění jedno místo za posledním prvkem v seřazeného cílového rozsahu, který představuje rozdíl dvou zdrojových rozsahů.

### <a name="remarks"></a>Poznámky

Musí být platný; seřazených zdrojových rozsahů, které odkazuje všechny odkazy musí být možné nepřímo odkazovat a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstků.

Cílový rozsah nesmí překrývat buď zdrojových rozsahů a by měl být dostatečně velký, aby se tak, aby obsahovala první zdrojové oblasti.

Seřazených zdrojových rozsahů musí každý uspořádat podmínkou pro použití `set_difference` algoritmus ve stejném pořadí jako se používá algoritmus k seřazení kombinovaných rozsahů.

Operace není stabilní, jako relativní pořadí prvků v rámci každé oblasti se zachovají v cílové oblasti. Zdrojové rozsahy nejsou změněna sloučení algoritmus.

Typy hodnot iterátorů vstupu musí být menší než porovnatelný z hlediska povolujeme, tak aby byly uvedeny dva elementy, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý) nebo že jeden je menší než ten druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou ekvivalentní elementy v obou zdrojových rozsahů, před prvky v první oblasti prvky z druhého rozsahu zdroje v cílové oblasti. Pokud zdrojové rozsahy obsahují duplicitní element tak, že existuje více v první zdrojový rozsah než za sekundu, pak cílového rozsahu bude obsahovat čísla, podle kterého překročit výskyty tyto prvky z prvního zdrojového rozsahu výskytů Tyto prvky ve druhém zdrojovém rozsahu.

Složitost algoritmu je lineární s maximálně 2 \* (( *Příjmení1 - first1*) – ( *Příjmení2 - first2*)) – 1 porovnání pro prázdný zdrojových rozsahů.

### <a name="example"></a>Příklad

```cpp
// alg_set_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
   if (elem1 < 0)
      elem1 = - elem1;
   if (elem2 < 0)
      elem2 = - elem2;
   return elem1 < elem2;
}

int main()
{
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;

   // Constructing vectors v1a & v1b with default less-than ordering
   int i;
   for ( i = -1 ; i <= 4 ; i++ )
   {
      v1a.push_back(  i );
   }

   int ii;
   for ( ii =-3 ; ii <= 0 ; ii++ )
   {
      v1b.push_back(  ii  );
   }

   cout << "Original vector v1a with range sorted by the\n "
        <<  "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;
   sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
   sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );
   vector <int>::iterator Iter3a,  Iter3b, Iter3, Result3;
   sort ( v3a.begin( ), v3a.end( ), mod_lesser );
   sort ( v3b.begin( ), v3b.end( ), mod_lesser  );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To combine into a difference in asscending
   // order with the default binary predicate less <int>( )
   Result1 = set_difference ( v1a.begin( ), v1a.end( ),
      v1b.begin( ), v1b.end( ), v1.begin( ) );
   cout << "Set_difference of source ranges with default order,"
        << "\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To combine into a difference in descending
   // order specify binary predicate greater<int>( )
   Result2 = set_difference ( v2a.begin( ), v2a.end( ),
      v2b.begin( ), v2b.end( ),v2.begin( ), greater <int>( ) );
   cout << "Set_difference of source ranges with binary"
        << "predicate greater specified,\n vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // To combine into a difference applying a user
   // defined binary predicate mod_lesser
   Result3 = set_difference (  v3a.begin( ), v3a.end( ),
      v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
   cout << "Set_difference of source ranges with binary "
        << "predicate mod_lesser specified,\n vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="set_intersection"></a>  set_intersection –

Sjednotí všechny prvky, které náleží do obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    BinaryPredicate comp );
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku v prvních dvou seřazených zdrojových rozsahů spojené a rozděleny na jeden rozsah představující průnik dvou zdrojových rozsahů.

*Příjmení1*<br/>
Vstupní iterátor adresuje umístění jedno místo za posledním prvkem v první ze dvou seřazených zdrojových rozsahů spojené a rozděleny na jeden rozsah představující průnik dvou zdrojových rozsahů.

*first2*<br/>
Vstupní iterátor adresující pozici prvního prvku v druhé dvě po sobě jdoucích seřazené zdrojových rozsahů spojené a rozděleny na jeden rozsah představující průnik dvou zdrojových rozsahů.

*Příjmení2*<br/>
Vstupní iterátor adresující poslední jedna pozice po posledním prvku v druhé dvě po sobě jdoucích seřazené zdrojových rozsahů spojené a rozděleny na jeden rozsah představující průnik dvou zdrojových rozsahů.

**_** *Výsledek* výstupní iterace adresující pozici prvního prvku v cílové oblasti, kde obě zdrojové rozsahy mají být spojeny do jednoho seřazeného rozsahu představující průnik dvou zdroje rozsahy.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je větší než jiný. Binární predikát přijímá dva argumenty a by měl vrátit **true** při prvním prvkem je menší než druhý prvek a **false** jinak.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresuje umístění jedno místo za posledním prvkem v seřazeného cílového rozsahu představující průnik dvou zdrojových rozsahů.

### <a name="remarks"></a>Poznámky

Musí být platný; seřazených zdrojových rozsahů, které odkazuje všechny odkazy musí být možné nepřímo odkazovat a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstků.

Cílový rozsah nesmí překrývat buď zdrojových rozsahů a by měl být dostatečně velký, aby se tak, aby obsahovala cílového rozsahu.

Seřazených zdrojových rozsahů musí každý být uspořádány podmínkou použití algoritmu sloučení ve stejném pořadí jako se používá algoritmus k seřazení kombinovaných rozsahů.

Operace není stabilní, jako relativní pořadí prvků v rámci každé oblasti se zachovají v cílové oblasti. Zdrojové rozsahy nejsou změněn pomocí algoritmu.

Typy hodnot iterátorů vstupu musí být menší – než srovnatelná s hodnotou příkazu, tak aby byly uvedeny dva elementy, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý) nebo že jeden je menší než ten druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou ekvivalentní elementy v obou zdrojových rozsahů, před prvky v první oblasti prvky z druhého rozsahu zdroje v cílové oblasti. Pokud zdrojových rozsahů obsahují duplicitní položky prvku, cílová oblast bude obsahovat maximální počet prvků, které se vyskytují v obou zdrojových rozsahů.

Složitost algoritmu je lineární s maximálně 2 \* (( *Příjmení1 - first1*) + ( *Příjmení2 - first2*)) – 1 porovnání pro prázdný zdrojových rozsahů.

### <a name="example"></a>Příklad

```cpp
// alg_set_intersection.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 ) {
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main() {
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;

   // Constructing vectors v1a & v1b with default less than ordering
   int i;
   for ( i = -1 ; i <= 3 ; i++ )
      v1a.push_back( i );

   int ii;
   for ( ii =-3 ; ii <= 1 ; ii++ )
      v1b.push_back( ii );

   cout << "Original vector v1a with range sorted by the\n "
        <<  "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;
   sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
   sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

   cout << "Original vector v2a with range sorted by the\n "
        << "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        << "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
   vector <int>::iterator Iter3a,  Iter3b, Iter3, Result3;
   sort ( v3a.begin( ), v3a.end( ), mod_lesser );
   sort ( v3b.begin( ), v3b.end( ), mod_lesser );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
           <<  "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To combine into an intersection in asscending order with the
   // default binary predicate less <int>( )
   Result1 = set_intersection ( v1a.begin( ), v1a.end( ),
      v1b.begin( ), v1b.end( ), v1.begin( ) );
   cout << "Intersection of source ranges with default order,"
        << "\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; ++Iter1 )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To combine into an intersection in descending order, specify
   // binary predicate greater<int>( )
   Result2 = set_intersection ( v2a.begin( ), v2a.end( ),
      v2b.begin( ), v2b.end( ),v2.begin( ), greater <int>( ) );
   cout << "Intersection of source ranges with binary predicate"
        << " greater specified,\n vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; ++Iter2 )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // To combine into an intersection applying a user-defined
   // binary predicate mod_lesser
   Result3 = set_intersection ( v3a.begin( ), v3a.end( ),
      v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
   cout << "Intersection of source ranges with binary predicate "
        << "mod_lesser specified,\n vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; ++Iter3 )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="set_symmetric_difference"></a>  set_symmetric_difference –

Sjednotí všechny prvky, které náleží do jednoho, ale nikoli obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    BinaryPredicate comp );

```

### <a name="parameters"></a>Parametry

*first1*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku v prvních dvou seřazených zdrojových rozsahů spojené a rozděleny na jeden rozsah představující symetrický rozdíl dvou zdrojových rozsahů.

*Příjmení1*<br/>
Vstupní iterátor adresuje umístění jedno místo za posledním prvkem v první ze dvou seřazených zdrojových rozsahů spojené a rozděleny na jeden rozsah představující symetrický rozdíl dvou zdrojových rozsahů.

*first2*<br/>
Vstupní iterátor adresující pozici prvního prvku v druhé dvě po sobě jdoucích seřazené zdrojových rozsahů spojené a rozděleny na jeden rozsah představující symetrický rozdíl dvou zdrojových rozsahů.

*Příjmení2*<br/>
Vstupní iterátor adresující poslední jedna pozice po posledním prvku v druhé dvě po sobě jdoucích seřazené zdrojových rozsahů spojené a rozděleny na jeden rozsah představující symetrický rozdíl dvou zdrojových rozsahů.

**_** *Výsledek* výstupní iterace adresující pozici prvního prvku v cílové oblasti, kde obě zdrojové rozsahy mají být spojeny do jednoho seřazeného rozsahu představující symetrický rozdíl dvou zdrojové rozsahy.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je větší než jiný. Binární predikát přijímá dva argumenty a by měl vrátit **true** při prvním prvkem je menší než druhý prvek a **false** jinak.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresuje umístění jedno místo za posledním prvkem v seřazeného cílového rozsahu představující symetrický rozdíl dvou zdrojových rozsahů.

### <a name="remarks"></a>Poznámky

Musí být platný; seřazených zdrojových rozsahů, které odkazuje všechny odkazy musí být možné nepřímo odkazovat a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstků.

Cílový rozsah nesmí překrývat buď zdrojových rozsahů a by měl být dostatečně velký, aby se tak, aby obsahovala cílového rozsahu.

Seřazených zdrojových rozsahů musí každý uspořádat podmínkou pro použití `merge*` algoritmus ve stejném pořadí jako se používá algoritmus k seřazení kombinovaných rozsahů.

Operace není stabilní, jako relativní pořadí prvků v rámci každé oblasti se zachovají v cílové oblasti. Zdrojové rozsahy nejsou změněna sloučení algoritmus.

Typy hodnot iterátorů vstupu musí být menší – než srovnatelná s hodnotou příkazu, tak aby byly uvedeny dva elementy, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý) nebo že jeden je menší než ten druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou ekvivalentní elementy v obou zdrojových rozsahů, před prvky v první oblasti prvky z druhého rozsahu zdroje v cílové oblasti. Pokud zdrojové rozsahy obsahují duplicitní hodnoty elementu, pak cílového rozsahu bude obsahovat absolutní hodnotu čísla, podle kterého překračuje výskyty tyto prvky do jedné zdrojové rozsahy výskytů tyto elementy ve druhém zdrojovém rozsah.

Složitost algoritmu je lineární s maximálně 2 \* ((*Příjmení1 - first1*) – (*Příjmení2 - first2*)) – 1 porovnání pro prázdný zdrojových rozsahů.

### <a name="example"></a>Příklad

```cpp
// alg_set_sym_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main()
{
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;

   // Constructing vectors v1a & v1b with default less-than ordering
   int i;
   for ( i = -1 ; i <= 4 ; i++ )
   {
      v1a.push_back(  i );
   }

   int ii;
   for ( ii =-3 ; ii <= 0 ; ii++ )
   {
      v1b.push_back(  ii  );
   }

   cout << "Original vector v1a with range sorted by the\n "
        <<  "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;
   sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
   sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );
   vector <int>::iterator Iter3a, Iter3b, Iter3, Result3;
   sort ( v3a.begin( ), v3a.end( ), mod_lesser );
   sort ( v3b.begin( ), v3b.end( ), mod_lesser  );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To combine into a symmetric difference in ascending
   // order with the default binary predicate less <int>( )
   Result1 = set_symmetric_difference ( v1a.begin( ), v1a.end( ),
      v1b.begin( ), v1b.end( ), v1.begin( ) );
   cout << "Set_symmetric_difference of source ranges with default order,"
        << "\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To combine into a symmetric difference in descending
   // order, specify binary predicate greater<int>( )
   Result2 = set_symmetric_difference ( v2a.begin( ), v2a.end( ),
      v2b.begin( ), v2b.end( ),v2.begin( ), greater <int>( ) );
   cout << "Set_symmetric_difference of source ranges with binary"
        << "predicate greater specified,\n vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // To combine into a symmetric difference applying a user
   // defined binary predicate mod_lesser
   Result3 = set_symmetric_difference ( v3a.begin( ), v3a.end( ),
      v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
   cout << "Set_symmetric_difference of source ranges with binary "
        << "predicate mod_lesser specified,\n vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="set_union"></a>  set_union –

Sjednotí všechny prvky, které náleží alespoň do jednoho ze dvou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    BinaryPredicate comp );
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku v prvních dvou seřazených zdrojových rozsahů spojené a rozděleny na jeden rozsah představující sjednocení dvou zdrojových rozsahů.

*Příjmení1*<br/>
Vstupní iterátor adresuje umístění jedno místo za posledním prvkem v první ze dvou seřazených zdrojových rozsahů spojené a rozděleny na jeden rozsah představující sjednocení dvou zdrojových rozsahů.

*first2*<br/>
Vstupní iterátor adresující pozici prvního prvku v druhé dvě po sobě jdoucích seřazené zdrojových rozsahů spojené a rozděleny na jeden rozsah představující sjednocení dvou zdrojových rozsahů.

*Příjmení2*<br/>
Vstupní iterátor adresující poslední jedna pozice po posledním prvku v druhé dvě po sobě jdoucích seřazené zdrojových rozsahů spojené a rozděleny na jeden rozsah představující sjednocení dvou zdrojových rozsahů.

**_** *Výsledek* výstupní iterace adresující pozici prvního prvku v cílové oblasti, kde obě zdrojové rozsahy mají být spojeny do jednoho seřazeného rozsahu představující sjednocení dvou zdrojových rozsahů.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je větší než jiný. Binární predikát přijímá dva argumenty a by měl vrátit **true** při prvním prvkem je menší než druhý prvek a **false** jinak.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresuje umístění jedno místo za posledním prvkem v seřazeného cílového rozsahu představující sjednocení dvou zdrojových rozsahů.

### <a name="remarks"></a>Poznámky

Musí být platný; seřazených zdrojových rozsahů, které odkazuje všechny odkazy musí být možné nepřímo odkazovat a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstků.

Cílový rozsah nesmí překrývat buď zdrojových rozsahů a by měl být dostatečně velký, aby se tak, aby obsahovala cílového rozsahu.

Seřazených zdrojových rozsahů musí každý uspořádat podmínkou pro použití `merge` algoritmus ve stejném pořadí jako se používá algoritmus k seřazení kombinovaných rozsahů.

Operace není stabilní, jako relativní pořadí prvků v rámci každé oblasti se zachovají v cílové oblasti. Zdrojové rozsahy nejsou změněn pomocí algoritmu `merge`.

Typy hodnot iterátorů vstupu musí být menší – než srovnatelná s hodnotou příkazu, tak aby byly uvedeny dva elementy, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý) nebo že jeden je menší než ten druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou ekvivalentní elementy v obou zdrojových rozsahů, před prvky v první oblasti prvky z druhého rozsahu zdroje v cílové oblasti. Pokud zdrojových rozsahů obsahují duplicitní položky prvku, cílová oblast bude obsahovat maximální počet prvků, které se vyskytují v obou zdrojových rozsahů.

Složitost algoritmu je lineární s maximálně 2 \* (( *Příjmení1 - first1*) – ( *Příjmení2 - first2*)) – 1 porovnání.

### <a name="example"></a>Příklad

```cpp
// alg_set_union.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 < elem2;
}

int main()
{
   using namespace std;
   vector <int> v1a, v1b, v1 ( 12 );
   vector <int>::iterator Iter1a, Iter1b, Iter1, Result1;

   // Constructing vectors v1a & v1b with default less than ordering
   int i;
   for ( i = -1 ; i <= 3 ; i++ )
   {
      v1a.push_back(  i );
   }

   int ii;
   for ( ii =-3 ; ii <= 1 ; ii++ )
   {
      v1b.push_back(  ii  );
   }

   cout << "Original vector v1a with range sorted by the\n "
        <<  "binary predicate less than is  v1a = ( " ;
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
      cout << *Iter1a << " ";
   cout << ")." << endl;

   cout << "Original vector v1b with range sorted by the\n "
        <<  "binary predicate less than is  v1b = ( " ;
   for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
      cout << *Iter1b << " ";
   cout << ")." << endl;

   // Constructing vectors v2a & v2b with ranges sorted by greater
   vector <int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
   vector <int>::iterator Iter2a,  Iter2b, Iter2, Result2;
   sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
   sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

   cout << "Original vector v2a with range sorted by the\n "
        <<  "binary predicate greater is   v2a =  ( " ;
   for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
      cout << *Iter2a << " ";
   cout << ")." << endl;

   cout << "Original vector v2b with range sorted by the\n "
        <<  "binary predicate greater is   v2b =  ( " ;
   for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
      cout << *Iter2b << " ";
   cout << ")." << endl;

   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );
   vector <int>::iterator Iter3a, Iter3b, Iter3, Result3;
   sort ( v3a.begin( ), v3a.end( ), mod_lesser );
   sort ( v3b.begin( ), v3b.end( ), mod_lesser  );

   cout << "Original vector v3a with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3a =  ( " ;
   for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
      cout << *Iter3a << " ";
   cout << ")." << endl;

   cout << "Original vector v3b with range sorted by the\n "
        <<  "binary predicate mod_lesser is   v3b =  ( " ;
   for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
      cout << *Iter3b << " ";
   cout << ")." << endl;

   // To combine into a union in ascending order with the default
    // binary predicate less <int>( )
   Result1 = set_union ( v1a.begin( ), v1a.end( ),
      v1b.begin( ), v1b.end( ), v1.begin( ) );
   cout << "Union of source ranges with default order,"
        << "\n vector v1mod =  ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // To combine into a union in descending order, specify binary
   // predicate greater<int>( )
   Result2 = set_union (  v2a.begin( ), v2a.end( ),
      v2b.begin( ), v2b.end( ),v2.begin( ), greater <int>( ) );
   cout << "Union of source ranges with binary predicate greater "
        << "specified,\n vector v2mod  = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // To combine into a union applying a user-defined
   // binary predicate mod_lesser
   Result3 = set_union ( v3a.begin( ), v3a.end( ),
      v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
   cout << "Union of source ranges with binary predicate "
        << "mod_lesser specified,\n vector v3mod  = ( " ; ;
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

## <a name="shuffle"></a>  std::Shuffle

Prvky podle okolí posouvá (změní uspořádání) pro zadaný rozsah s použitím generátor náhodných čísel.

```cpp
template<class RandomAccessIterator, class UniformRandomNumberGenerator>
void shuffle(RandomAccessIterator first,
    RandomAccessIterator last,
    UniformRandomNumberGenerator&& gen);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Iterátor na první prvek v rozsahu přeházenou metodou Shuffle, včetně. Musí splňovat požadavky `RandomAccessIterator` a `ValueSwappable`.

*poslední*<br/>
Iterátor na poslední prvek v rozsahu přeházenou metodou Shuffle, vylučují. Musí splňovat požadavky `RandomAccessIterator` a `ValueSwappable`.

*Obecné*<br/>
Generátor náhodných čísel, která `shuffle()` funkce bude používat pro operaci. Musí splňovat požadavky `UniformRandomNumberGenerator`.

### <a name="remarks"></a>Poznámky

Další informace a ukázku kódu, který používá `shuffle()`, naleznete v tématu [ \<náhodné >](../standard-library/random.md).

## <a name="sort"></a>  Řazení

Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.

```cpp
template<class RandomAccessIterator>
   void sort(
      RandomAccessIterator first,
      RandomAccessIterator last);

template<class RandomAccessIterator, class Predicate>
   void sort(
      RandomAccessIterator first,
      RandomAccessIterator last,
      Predicate comp);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Iterátor s náhodným přístupem adresuje umístění prvního prvku v rozsahu který se má seřadit.

*poslední*<br/>
Iterátor s náhodným přístupem adresuje umístění jedno místo za poslední prvek v rozsahu který se má seřadit.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání vyhovět pomocí po sobě jdoucí prvky v pořadí. Tento binární predikát přijímá dva argumenty a vrací **true** Pokud jsou dva argumenty v pořadí a **false** jinak. Tato funkce porovnání musí uložit přísné slabé seřazení na dvojice prvků z posloupnosti. Další informace najdete v tématu [algoritmy](../standard-library/algorithms.md).

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Prvky jsou ekvivalentní, ale ne nutně stejné, pokud je menší než ten druhý. `sort` Algoritmus není stabilní a proto nezaručuje, že budou zachovány relativní pořadí ekvivalentních prvků. Algoritmus `stable_sort` zachovat původní pořadí.

Průměrná složitost řazení *O*( *N* protokolu *N*), kde *N* =  *poslední – první*.

### <a name="example"></a>Příklad

```cpp
// alg_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
   return elem1 > elem2;
}

int main()
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   int ii;
   for ( ii = 0 ; ii <= 5 ; ii++ )
   {
      v1.push_back( 2 * ii + 1 );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order. specify binary predicate
   sort( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "Resorted (greater) vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // A user-defined (UD) binary predicate can also be used
   sort( v1.begin( ), v1.end( ), UDgreater );
   cout << "Resorted (UDgreater) vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Sorted vector v1 = ( 0 1 2 3 4 5 6 7 8 9 10 11 )
Resorted (greater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
Resorted (UDgreater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
```

## <a name="sort_heap"></a>  sort_heap –

Převede haldu na seřazený rozsah.

```cpp
template<class RandomAccessIterator>
   void sort_heap(
      RandomAccessIterator first,
      RandomAccessIterator last);

template<class RandomAccessIterator, class Predicate>
   void sort_heap(
      RandomAccessIterator first,
      RandomAccessIterator last,
      Predicate comp);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Iterátor pro náhodný přístup adresuje umístění prvního prvku v cílové haldy.

*poslední*<br/>
Iterátor pro náhodný přístup adresuje umístění jedno za posledním prvkem v cílové haldy.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="remarks"></a>Poznámky

Haldy má dvě vlastnosti:

- Vždy je největší první prvek.

- Elementy mohou přidat nebo odebrat logaritmické včas.

Po aplikaci, pokud tento algoritmus, rozsahu byla použita k už není haldu.

Toto není stabilní řazení, protože relativní pořadí ekvivalentních prvků nutně nezachová.

Haldy jsou ideální způsob, jak implementovat prioritní fronty a používají se v implementaci adaptér kontejneru standardní knihovny C++ [priority_queue – třída](../standard-library/priority-queue-class.md).

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Složitost je nejvíce *N* protokolu *N*, kde *N* = ( *naposledy - nejprve*).

### <a name="example"></a>Příklad

```cpp
// alg_sort_heap.cpp
// compile with: /EHsc
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>
#include <string>
#include <vector>
using namespace std;

void print(const string& s, const vector<int>& v) {
    cout << s << ": ( ";

    for (auto i = v.begin(); i != v.end(); ++i) {
        cout << *i << " ";
    }

    cout << ")" << endl;
}

int main() {
    vector<int> v;
    for (int i = 1; i <= 9; ++i) {
        v.push_back(i);
    }
    print("Initially", v);

    random_shuffle(v.begin(), v.end());
    print("After random_shuffle", v);

    make_heap(v.begin(), v.end());
    print("     After make_heap", v);

    sort_heap(v.begin(), v.end());
    print("     After sort_heap", v);

    random_shuffle(v.begin(), v.end());
    print("             After random_shuffle", v);

    make_heap(v.begin(), v.end(), greater<int>());
    print("After make_heap with greater<int>", v);

    sort_heap(v.begin(), v.end(), greater<int>());
    print("After sort_heap with greater<int>", v);
}
```

## <a name="stable_partition"></a>  stable_partition –

Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují. Relativní pořadí ekvivalentních prvků je zachováno.

```cpp
template<class BidirectionalIterator, class Predicate>
BidirectionalIterator stable_partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    Predicate pred );

```

### <a name="parameters"></a>Parametry

*první*<br/>
Obousměrný iterátor adresuje umístění prvního prvku v rozsahu k rozdělení na oddíly.

*poslední*<br/>
Obousměrný iterátor adresuje umístění jedno místo za poslední prvek v rozsahu k rozdělení na oddíly.

*_Pred*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněny, pokud element má být klasifikované. Predikát přijímá jeden argument a vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor adresuje umístění prvního prvku v rozsahu pro nejsou splněna podmínka predikátu.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Elementy *a* *b* jsou ekvivalentní, ale stejně nemusí nutně prokázat, pokud obě *Pr* ( *a*, *b*) je hodnota false a *Pr* ( *b*, *a*) Pokud je hodnota false, kde *Pr* je zadán parametr predikátu. `stable_ partition` Algoritmus je stabilní a zaručuje, že relativní pořadí ekvivalentních prvků se zachovají. Algoritmus `partition` nemusí zachovat původní pořadí.

### <a name="example"></a>Příklad

```cpp
// alg_stable_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value ) {
   return value > 5;
}

int main() {
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2, result;

   int i;
   for ( i = 0 ; i <= 10 ; i++ )
      v1.push_back( i );

   int ii;
   for ( ii = 0 ; ii <= 4 ; ii++ )
      v1.push_back( 5 );

   random_shuffle(v1.begin( ), v1.end( ) );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Partition the range with predicate greater10
   result = stable_partition (v1.begin( ), v1.end( ), greater5 );
   cout << "The partitioned set of elements in v1 is:\n ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "The first element in v1 to fail to satisfy the"
        << "\n predicate greater5 is: " << *result << "." << endl;
}
```

## <a name="stable_sort"></a>  stable_sort

Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem a zachová relativní pořadí ekvivalentních prvků.

```cpp
template<class BidirectionalIterator>
void stable_sort( BidirectionalIterator first, BidirectionalIterator last );

template<class BidirectionalIterator, class BinaryPredicate>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate comp );

```

### <a name="parameters"></a>Parametry

*první*<br/>
Obousměrný iterátor adresuje umístění prvního prvku v rozsahu který se má seřadit.

*poslední*<br/>
Obousměrný iterátor adresuje umístění jedno místo za poslední prvek v rozsahu který se má seřadit.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání vyhovět pomocí po sobě jdoucí prvky v pořadí. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků.

Prvky jsou ekvivalentní, ale ne nutně stejné, pokud je menší než ten druhý. `sort` Algoritmus je stabilní a zaručuje, že relativní pořadí ekvivalentních prvků se zachovají.

Za běhu složitost `stable_sort` závisí na množství paměti k dispozici, ale nejlepší případ (zadaný dostatek paměti) má *O*( *N* protokolu *N*) a nejhorší případ je *O*( *N* (protokolu *N* ) 2), kde *N* =  *příjmení - jméno.* Obvykle `sort` algoritmus je výrazně rychlejší než `stable_sort`.

### <a name="example"></a>Příklad

```cpp
// alg_stable_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater (int elem1, int elem2 )
{
   return elem1 > elem2;
}

int main()
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 2 * i  );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   stable_sort(v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order, specify binary predicate
   stable_sort(v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "Resorted (greater) vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // A user-defined (UD) binary predicate can also be used
   stable_sort(v1.begin( ), v1.end( ), UDgreater );
   cout << "Resorted (UDgreater) vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 0 2 4 6 8 10 )
Sorted vector v1 = ( 0 0 2 2 4 4 6 6 8 8 10 10 )
Resorted (greater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
Resorted (UDgreater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
```

## <a name="swap"></a>  Prohození

První přepsání vymění hodnoty dvou objektů. Druhý přepsání vymění hodnoty mezi dvěma poli objektů.

```cpp
template<class Type>
   void swap(
      Type& left,
      Type& right);
template<class Type, size_t N>
   void swap(
      Type (& left)[N],
      Type (& right)[N]);\r

```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Pro první přepsání první objekt k jeho obsahem vyměňují. Pro druhý přepsání první pole objektů, které chcete mít svůj obsah si vyměňují.

*doprava*<br/>
Pro první přepsání druhý objekt k jeho obsahem vyměňují. Pro druhý přepsání druhé pole objektů, které chcete mít svůj obsah si vyměňují.

### <a name="remarks"></a>Poznámky

První přetížení je navržená pro provoz na jednotlivé objekty. Druhé přetížení Zamění obsah objektů mezi dvěma poli.

### <a name="example"></a>Příklad

```cpp
// alg_swap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
   using namespace std;
   vector <int> v1, v2;
   vector <int>::iterator Iter1, Iter2, result;

   for ( int i = 0 ; i <= 10 ; i++ )
   {
      v1.push_back( i );
   }

   for ( int ii = 0 ; ii <= 4 ; ii++ )
   {
      v2.push_back( 5 );
   }

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   swap( v1, v2 );

   cout << "Vector v1 is ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   cout << "Vector v2 is ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
Vector v2 is ( 5 5 5 5 5 ).
Vector v1 is ( 5 5 5 5 5 ).
Vector v2 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
```

## <a name="swap_ranges"></a>  swap_ranges –

Vymění prvky z jednoho rozsahu za prvky druhého rozsahu o stejné velikosti.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
   ForwardIterator1 first1,
   ForwardIterator1 last1,
   ForwardIterator2 first2 );

```

### <a name="parameters"></a>Parametry

*first1*<br/>
Dopředný iterátor odkazující na první pozici první rozsahu, jehož prvky se mají vyměnit.

*Příjmení1*<br/>
Dopředný iterátor odkazující na jedno místo za posledním pozici první rozsahu, jehož prvky se mají vyměnit.

*first2*<br/>
Dopředný iterátor odkazující na první pozici druhého rozsahu, jehož prvky se mají vyměnit.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor odkazující na jedno místo za posledním pozici druhého rozsahu, jehož prvky se mají vyměnit.

### <a name="remarks"></a>Poznámky

Rozsahy odkazuje musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci každé posloupnosti je poslední pozice dosažitelná z první pomocí přírůstků. Druhého rozsahu musí být velké až v první oblasti.

Složitost je lineární s *Příjmení1* - *first1* záměna provést. Pokud prvky z kontejnerů stejného typu se prohazují, je `swap` členská funkce z tohoto kontejneru je třeba použít, protože členskou funkci obvykle má konstantní složitost.

### <a name="example"></a>Příklad

```cpp
// alg_swap_ranges.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
   using namespace std;
   vector <int> v1;
   deque <int> d1;
   vector <int>::iterator v1Iter1;
   deque<int>::iterator d1Iter1;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( i );
   }

   int ii;
   for ( ii =4 ; ii <= 9 ; ii++ )
   {
      d1.push_back( 6 );
   }

   cout << "Vector v1 is ( " ;
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
      cout << *v1Iter1  << " ";
   cout << ")." << endl;

   cout << "Deque d1 is  ( " ;
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
      cout << *d1Iter1  << " ";
   cout << ")." << endl;

   swap_ranges ( v1.begin( ), v1.end( ), d1.begin( ) );

   cout << "After the swap_range, vector v1 is ( " ;
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
      cout << *v1Iter1 << " ";
   cout << ")." << endl;

   cout << "After the swap_range deque d1 is   ( " ;
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
      cout << *d1Iter1 << " ";
   cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 ).
Deque d1 is  ( 6 6 6 6 6 6 ).
After the swap_range, vector v1 is ( 6 6 6 6 6 6 ).
After the swap_range deque d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="transform"></a>  Transformace

Aplikuje zadaný objekt funkce na každý prvek ve zdrojovém rozsahu nebo na dvojici prvků ze dvou zdrojových rozsahů a zkopíruje vrácené hodnoty objektu funkce do cílového rozsahu.

```cpp
template<class InputIterator, class OutputIterator, class UnaryFunction>
OutputIterator transform(
    InputIterator first1,
    InputIterator last1,
    OutputIterator result,
    UnaryFunction func );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryFunction>
OutputIterator transform(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    OutputIterator result,
    BinaryFunction func );
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku v první zdrojového rozsahu do ho zpracovat.

*Příjmení1*<br/>
Vstupní iterátor adresující jedna pozice za posledním prvkem ve zdrojové oblasti první zpracovat.

*first2*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku v druhé zdrojové oblasti ho zpracovat.

*výsledek*<br/>
Výstupní iterace adresující pozici prvního prvku v cílové oblasti.

*_Func*<br/>
Unární uživatelem definované funkce objektu se používá v první verzi algoritmus, který se použije na každý prvek v první zdrojové oblasti nebo definované uživatelem (UD) objekt binární funkce používá v druhém verzi algoritmus, který se použije ukládání, v pořadí dopředu , do dvou zdrojových rozsahů.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterace adresující jedna pozice za posledním prvkem v cílovém rozsahu, který přijímá výstup elementy transformovány sadou objektu funkce.

### <a name="remarks"></a>Poznámky

Rozsahy odkazuje musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstků. Cílový rozsah musí být dostatečně velký, aby se tak, aby obsahovala transformovaný zdrojové oblasti.

Pokud *výsledek* nastavena na hodnotu *first1* v první verzi algoritmus, pak zdrojovou a cílovou oblastí budou stejné a pořadí bude změněn na místě. Ale *výsledek* nemusí vyřešit pozice v rozsahu [`first1` + 1, `last1`).

Složitost je lineární s maximálně (`last1` - `first1`) porovnání.

### <a name="example"></a>Příklad

```cpp
// alg_transform.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
   private:
      Type Factor;   // The value to multiply by
   public:
      // Constructor initializes the value to multiply by
      MultValue ( const Type& val ) : Factor ( val ) {
      }

      // The function call for the element to be multiplied
      Type operator( ) ( Type& elem ) const
      {
         return elem * Factor;
      }
};

int main()
{
   using namespace std;
   vector <int> v1, v2 ( 7 ), v3 ( 7 );
   vector <int>::iterator Iter1, Iter2 , Iter3;

   // Constructing vector v1
   int i;
   for ( i = -4 ; i <= 2 ; i++ )
   {
      v1.push_back(  i );
   }

   cout << "Original vector  v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Modifying the vector v1 in place
   transform (v1.begin( ), v1.end( ), v1.begin( ), MultValue<int> ( 2 ) );
   cout << "The elements of the vector v1 multiplied by 2 in place gives:"
        << "\n v1mod = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")." << endl;

   // Using transform to multiply each element by a factor of 5
   transform ( v1.begin( ), v1.end( ), v2.begin( ), MultValue<int> ( 5 ) );

   cout << "Multiplying the elements of the vector v1mod\n "
        <<  "by the factor 5 & copying to v2 gives:\n v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")." << endl;

   // The second version of transform used to multiply the
   // elements of the vectors v1mod & v2 pairwise
   transform ( v1.begin( ), v1.end( ),  v2.begin( ), v3.begin( ),
      multiplies <int>( ) );

   cout << "Multiplying elements of the vectors v1mod and v2 pairwise "
        <<  "gives:\n v3 = ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")." << endl;
}
```

```Output
Original vector  v1 = ( -4 -3 -2 -1 0 1 2 ).
The elements of the vector v1 multiplied by 2 in place gives:
v1mod = ( -8 -6 -4 -2 0 2 4 ).
Multiplying the elements of the vector v1mod
by the factor 5 & copying to v2 gives:
v2 = ( -40 -30 -20 -10 0 10 20 ).
Multiplying elements of the vectors v1mod and v2 pairwise gives:
v3 = ( 320 180 80 20 0 20 80 ).
```

## <a name="unique"></a>  Jedinečný

Odstraní duplicitní prvky, které v zadaném rozsahu sousedí.

```cpp
template<class ForwardIterator>
   ForwardIterator unique(
      ForwardIterator first,
      ForwardIterator last);

template<class ForwardIterator, class Predicate>
   ForwardIterator unique(
      ForwardIterator first,
      ForwardIterator last,
      Predicate comp);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který chcete vyhledávat duplicitní odebrání.

*poslední*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu, který chcete vyhledávat odstranění duplicit.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněny, pokud jsou dva prvky mají být provedeny, jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který nový konec upravené sekvenci, která obsahuje žádné duplicitní hodnoty po sobě jdoucích adresuje umístění jedno místo za posledním prvkem neodeberou.

### <a name="remarks"></a>Poznámky

Obě formy algoritmu. Odeberte duplicitní druhý po sobě jdoucích páru stejných prvků.

Operace algoritmus je stabilní, aby relativní pořadí prvků obnovil se nemění.

Odkazovaný rozsah musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci pořadí se poslední pozice dosažitelná z první pomocí přírůstků. počet prvků v sekvenci mu nezmění algoritmem `unique` a elementů přesahuje za konec změny pořadí jsou možné zrušit referenci, ale není zadaný.

Složitost je lineární, které vyžadují (`last` - `first`) + 1 porovnání.

Seznam poskytuje efektivnější členské funkce "unique", který může provádět lepší.

Tyto algoritmy nelze použít na asociativní kontejner.

### <a name="example"></a>Příklad

```cpp
// alg_unique.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 )
{
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 == elem2;
};

int main()
{
   vector <int> v1;
   vector <int>::iterator v1_Iter1, v1_Iter2, v1_Iter3,
         v1_NewEnd1, v1_NewEnd2, v1_NewEnd3;

   int i;
   for ( i = 0 ; i <= 3 ; i++ )
   {
      v1.push_back( 5 );
      v1.push_back( -5 );
   }

   int ii;
   for ( ii = 0 ; ii <= 3 ; ii++ )
   {
      v1.push_back( 4 );
   }
   v1.push_back( 7 );

   cout << "Vector v1 is ( " ;
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
      cout << *v1_Iter1 << " ";
   cout << ")." << endl;

   // Remove consecutive duplicates
   v1_NewEnd1 = unique ( v1.begin( ), v1.end( ) );

   cout << "Removing adjacent duplicates from vector v1 gives\n ( " ;
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
      cout << *v1_Iter1 << " ";
   cout << ")." << endl;

   // Remove consecutive duplicates under the binary prediate mod_equals
   v1_NewEnd2 = unique ( v1.begin( ), v1_NewEnd1 , mod_equal );

   cout << "Removing adjacent duplicates from vector v1 under the\n "
        << " binary predicate mod_equal gives\n ( " ;
   for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
      cout << *v1_Iter2 << " ";
   cout << ")." << endl;

   // Remove elements if preceded by an element that was greater
   v1_NewEnd3 = unique ( v1.begin( ), v1_NewEnd2, greater<int>( ) );

   cout << "Removing adjacent elements satisfying the binary\n "
        << " predicate mod_equal from vector v1 gives ( " ;
   for ( v1_Iter3 = v1.begin( ) ; v1_Iter3 != v1_NewEnd3 ; v1_Iter3++ )
      cout << *v1_Iter3 << " ";
   cout << ")." << endl;
}
```

```Output
Vector v1 is ( 5 -5 5 -5 5 -5 5 -5 4 4 4 4 7 ).
Removing adjacent duplicates from vector v1 gives
( 5 -5 5 -5 5 -5 5 -5 4 7 ).
Removing adjacent duplicates from vector v1 under the
  binary predicate mod_equal gives
( 5 4 7 ).
Removing adjacent elements satisfying the binary
  predicate mod_equal from vector v1 gives ( 5 7 ).
```

## <a name="unique_copy"></a>  unique_copy –

Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu s výjimkou sousedících duplicitních prvků.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator unique_copy( InputIterator first,
    InputIterator last,
    OutputIterator result );

template<class InputIterator, class OutputIterator, class BinaryPredicate>
OutputIterator unique_copy( InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryPredicate comp );
```

### <a name="parameters"></a>Parametry

*první*<br/>
Dopředný iterátor, který adresuje umístění prvního prvku ve zdrojovém rozsahu ke zkopírování.

*poslední*<br/>
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem ve zdrojovém rozsahu ke zkopírování.

*výsledek*<br/>
Výstupní iterace adresující pozici prvního prvku v cílovém rozsahu, který se přidává kopie s po sobě jdoucích duplicity se odeberou.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněny, pokud jsou dva prvky mají být provedeny, jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterace adresující jedna pozice za posledním prvkem v cílovém rozsahu, který se přidává kopie s po sobě jdoucích duplicity se odeberou.

### <a name="remarks"></a>Poznámky

Obě formy algoritmu. Odeberte duplicitní druhý po sobě jdoucích páru stejných prvků.

Operace algoritmus je stabilní, aby relativní pořadí prvků obnovil se nemění.

Rozsahy odkazuje musí být platný; všechny odkazy musí být možné nepřímo odkazovat a v rámci posloupnosti je poslední pozice dosažitelná z první pomocí přírůstků.

Složitost je lineární, které vyžadují (`last` - `first`) porovnání.

### <a name="example"></a>Příklad

```cpp
// alg_unique_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 ) {
   if ( elem1 < 0 )
      elem1 = - elem1;
   if ( elem2 < 0 )
      elem2 = - elem2;
   return elem1 == elem2;
};

int main() {
   vector <int> v1;
   vector <int>::iterator v1_Iter1, v1_Iter2,
         v1_NewEnd1, v1_NewEnd2;

   int i;
   for ( i = 0 ; i <= 1 ; i++ ) {
      v1.push_back( 5 );
      v1.push_back( -5 );
   }

   int ii;
   for ( ii = 0 ; ii <= 2 ; ii++ )
      v1.push_back( 4 );
   v1.push_back( 7 );

   int iii;
   for ( iii = 0 ; iii <= 5 ; iii++ )
      v1.push_back( 10 );

   cout << "Vector v1 is\n ( " ;
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
      cout << *v1_Iter1 << " ";
   cout << ")." << endl;

   // Copy first half to second, removing consecutive duplicates
   v1_NewEnd1 = unique_copy ( v1.begin( ), v1.begin( ) + 8, v1.begin( ) + 8 );

   cout << "Copying the first half of the vector to the second half\n "
        << "while removing adjacent duplicates gives\n ( " ;
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
      cout << *v1_Iter1 << " ";
   cout << ")." << endl;

   int iv;
   for ( iv = 0 ; iv <= 7 ; iv++ )
      v1.push_back( 10 );

   // Remove consecutive duplicates under the binary prediate mod_equals
   v1_NewEnd2 = unique_copy ( v1.begin( ), v1.begin( ) + 14,
      v1.begin( ) + 14 , mod_equal );

   cout << "Copying the first half of the vector to the second half\n "
        << " removing adjacent duplicates under mod_equals gives\n ( " ;
   for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
      cout << *v1_Iter2 << " ";
   cout << ")." << endl;
}
```

## <a name="upper_bound"></a>  upper_bound –

Najde pozici prvního prvku v seřazeném rozsahu, který má hodnotu větší než zadaná hodnota, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class ForwardIterator, class Type>
   ForwardIterator upper_bound(
      ForwardIterator first,
      ForwardIterator last,
      const Type& value);

template<class ForwardIterator, class Type, class Predicate>
   ForwardIterator upper_bound(
      ForwardIterator first,
      ForwardIterator last,
      const Type& value,
      Predicate comp);

```

### <a name="parameters"></a>Parametry

*první*<br/>
Pozice prvního prvku v rozsahu, který chcete prohledat.

*poslední*<br/>
Jedna pozice za posledním prvkem v rozsahu, který chcete prohledat.

*value*<br/>
Hodnota v seřazeném rozsahu, který musí být překročena hodnotou elementu řešenou vráceným iterátorem.

*Kompozice*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který na pozici prvního prvku, který má hodnotu větší než zadanou hodnotou.

### <a name="remarks"></a>Poznámky

Odkazovaný seřazený zdrojový rozsah musí být platný; všech iterátorů musí být možné nepřímo odkazovat a v rámci sekvence musí být poslední pozice dosažitelná z první pomocí přírůstků.

Seřazený rozsah je podmínkou pro použití `upper_bound` a kde kritérium řazení je stejné jako u binárního predikátu.

Rozsah nebyl změněn pomocí `upper_bound`.

Typy hodnot iterátorů předání musí být menší – než srovnatelná s hodnotou příkazu, tak aby byly uvedeny dva elementy, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý) nebo že jeden je menší než ten druhý. Výsledkem je řazení mezi neekvivalentními prvky

Složitost algoritmu je logaritmický pro iterátory s náhodným přístupem a v opačném případě lineární, přičemž počet kroků je přímo úměrný (`last - first`).

### <a name="example"></a>Příklad

```cpp
// alg_upper_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back(  i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back(  ii  );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        <<  "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate upper_bound

    vector<int>::iterator Result;

    // upper_bound of 3 in v1 with default binary predicate less<int>()
    Result = upper_bound(v1.begin(), v1.end(), 3);
    cout << "The upper_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = upper_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The upper_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v3 with the binary predicate  mod_lesser
    Result = upper_bound(v3.begin(), v3.end(), 3,  mod_lesser);
    cout << "The upper_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}

```

## <a name="see-also"></a>Viz také:

[\<algoritmus >](../standard-library/algorithm.md)<br/>