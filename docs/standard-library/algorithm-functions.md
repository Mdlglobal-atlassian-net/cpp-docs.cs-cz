---
title: '&lt;funkce&gt; algoritmu'
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
ms.openlocfilehash: cf6c1267b1dea86c2cad62708192a4c0a1970ed8
ms.sourcegitcommit: 610751254a01cba6ad15fb1e1764ecb2e71f66bf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313398"
---
# <a name="ltalgorithmgt-functions"></a>&lt;funkce&gt; algoritmu

## <a name="adjacent_find"></a>adjacent_find

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
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který chcete prohledat.

*posledního*\
Dopředný iterátor, který adresuje pozici jednu za posledním prvkem v rozsahu, který chcete prohledat.

*čekání*\
Binární predikát udávající podmínku, která má být splněna hodnotami sousedících prvků v prohledávaným rozsahu.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor k prvnímu z sousedících prvků, které jsou buď vzájemně rovny (v první verzi), nebo který vyhovuje podmínkám daným binárním predikátem (ve druhé verzi), za předpokladu, že je nalezena dvojice prvků. V opačném případě se vrátí iterátor ukazující na *Poslední* .

### <a name="remarks"></a>Poznámky

`adjacent_find` Algoritmus je neobdobný algoritmus sekvence. Rozsah, který má být prohledán, musí být platný. všechny ukazatele musí být možné odkázat a poslední pozice je dosažitelná z první pomocí přírůstku. Doba složitosti algoritmu je lineární v počtu prvků obsažených v rozsahu.

`operator==` Pro určení shody mezi prvky musí být mezi jeho operandy navzájem vztah rovnosti.

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
    list<int> L;
    list<int>::iterator Iter;
    list<int>::iterator result1, result2;

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
        cout << "There are two adjacent elements that are equal.\n"
            << "They have a value of "
            << *( result1 ) << "." << endl;

    result2 = adjacent_find( L.begin( ), L.end( ), twice );
    if ( result2 == L.end( ) )
        cout << "There are not two adjacent elements where the "
            << "second is twice the first." << endl;
    else
    {
        cout << "There are two adjacent elements where "
            << "the second is twice the first.\n"
            << "They have values of " << *(result2++)
            << " & " << *result2 << "." << endl;
    }
}
```

```Output
L = ( 50 40 10 20 20 )
There are two adjacent elements that are equal.
They have a value of 20.
There are two adjacent elements where the second is twice the first.
They have values of 10 & 20.
```

## <a name="all_of"></a>all_of

Vrátí **hodnotu pravda** , pokud je podmínka přítomna na každém prvku v daném rozsahu.

```cpp
template<class InputIterator, class UnaryPredicate>
bool all_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool all_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor, který označuje, kde má začít kontrolovat podmínku. Iterátory, kde začíná rozsah prvků.

*posledního*\
Vstupní iterátor, který označuje konec rozsahu prvků pro kontrolu podmínky.

*čekání*\
Podmínka, která se má testovat. Toto je objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněna kontrolovaným prvkem. Unární predikát přijímá jeden argument a vrátí **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu true** , pokud je zjištěna podmínka u každého prvku v uvedeném rozsahu nebo pokud je rozsah prázdný, a jinak **false** .

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí **hodnotu true** pouze v případě, že `N` pro každý z `[0, last - first)`rozsahu má predikát `pred(*(first + N))` **hodnotu true**.

### <a name="example"></a>Příklad

```cpp
// alg_all_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 50, 40, 10, 20, 20 };
    list<int>::iterator iter;

    cout << "li = ( ";
    for (iter = li.begin(); iter != li.end(); iter++)
        cout << *iter << " ";
    cout << ")" << endl;

    // Check if all elements in li are even.
    auto is_even = [](int elem){ return !(elem % 2); };
    if (all_of(li.begin(), li.end(), is_even))
        cout << "All the elements are even numbers.\n";
    else
        cout << "Not all the elements are even numbers.\n";
}
```

```Output
li = ( 50 40 10 20 20 )
All the elements are even numbers.
```

## <a name="any_of"></a>any_of

Vrátí **hodnotu pravda** , pokud je v zadaném rozsahu prvků alespoň jednou podmínka přítomna.

```cpp
template<class InputIterator, class UnaryPredicate>
bool any_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool any_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor, který označuje, kde začít kontrolovat rozsah prvků pro podmínku.

*posledního*\
Vstupní iterátor, který označuje konec rozsahu prvků pro kontrolu podmínky.

*čekání*\
Podmínka, která se má testovat. Toto je poskytováno uživatelem definovaným objektovou funkcí predikátu. Predikát definuje podmínku, která má být splněna testovaným prvkem. Unární predikát přijímá jeden argument a vrátí **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu true** , pokud je podmínka zjištěna alespoň jednou v zadaném rozsahu, **false** , pokud není podmínka nikdy zjištěna.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí **hodnotu true** pouze v případě, že `N` u některých v rozsahu

`[0, last - first)`, predikát `pred(*(first + N))` má hodnotu true.

### <a name="example"></a>Příklad

```cpp
// alg_any_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 51, 41, 11, 21, 20 };

    cout << "li = ( ";
    for (auto const& el : li)
        cout << el << " ";
    cout << ")" << endl;

    // Check if there is an even elememt in li.
    auto is_even = [](int const elem){ return !(elem % 2); };
    if (any_of(li.begin(), li.end(), is_even))
        cout << "There's an even element in li.\n";
    else
        cout << "There are no even elements in li.\n";
}
```

```Output
li = ( 51 41 11 21 20 )
There's an even element in li.
```

## <a name="binary_search"></a>binary_search

Ověřuje, zda v seřazeném rozsahu existuje prvek, který je roven zadané hodnotě nebo je jí ekvivalentní ve smyslu určeném binárním predikátem.

```cpp
template<class ForwardIterator, class Type>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class BinaryPredicate>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*první*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který chcete prohledat.

*posledního*\
Dopředný iterátor, který adresuje pozici jednu za posledním prvkem v rozsahu, který chcete prohledat.

*osa*\
Hodnota, která má být porovnána s hodnotou prvku nebo musí splňovat podmínku s hodnotou prvku zadanou binárním predikátem.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je nalezen element v rozsahu, který je roven zadané hodnotě nebo který je ekvivalentní. v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Odkazovaný seřazený zdrojový rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Seřazený rozsah musí být uspořádán jako předběžná podmínka pro použití `binary_search` algoritmu v souladu se stejným pořadím, jako má být použit algoritmem pro řazení kombinovaných rozsahů.

Zdrojové rozsahy nejsou změněny nástrojem `binary_search`.

Typy hodnot iterátorů dodávání musí být méně než srovnatelné, aby je bylo možné seřadit, takže vzhledem k dvěma prvkům lze určit, že jsou ekvivalentní (v tom smyslu, že ani jeden není menší než druhý) nebo že jeden je menší než druhý. Výsledkem je řazení mezi neekvivalentními prvky.

Složitost algoritmu je logaritmický pro iterátory s náhodným přístupem a v opačném případě lineární, přičemž počet kroků je úměrný`last`hodnotě ( - `first`).

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

    list<int> List1;

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

## <a name="clamp"></a>Clamp

Porovná hodnotu s horní a dolní mezí a vrátí odkaz na hodnotu, pokud je mezi hranicemi, nebo odkazem na horní nebo dolní mez, pokud je hodnota nad nebo pod nimi, v uvedeném pořadí.

```cpp
template<class Type>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper);

template<class Type, class Compare>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*osa*\
Hodnota, která má být porovnána s *horní* a *nižší*hodnotou.

*malým*\
Dolní mez hodnot, na které se má *hodnota* přichycení

*umístit*\
Horní mez hodnot, na které se má *hodnota* svorka

*čekání*\
Predikát použitý k porovnání *hodnoty* s *nižší* nebo *horní*. Relační predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je první v nějakém smyslu menší než druhý, a v opačném případě **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na *nižší* , pokud `value < lower`nebo odkaz na *horní* , pokud `upper < value`. V opačném případě vrátí odkaz na *hodnotu*.

### <a name="remarks"></a>Poznámky

Chování není definováno, pokud je *horní* než *nižší*.

## <a name="copy"></a>kopií

Přiřadí hodnoty prvků ze zdrojového rozsahu do cílového rozsahu a provede iterace přes zdrojové sekvence prvků a přiřadí je novým pozicím směrem dopředu.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator copy(
    InputIterator first,
    InputIterator last,
    OutputIterator destBeg);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor adresující pozici prvního prvku ve zdrojovém rozsahu.

*posledního*\
Vstupní iterátor adresující pozici, která je jedno za posledním prvkem zdrojového rozsahu.

*destBeg*\
Výstupní iterátor adresující pozici prvního prvku v cílovém rozsahu.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující pozici, která je jedno za posledním `result` prvkem v cílovém rozsahu, tj. adresy iterátoru + (*Poslední* - ).

### <a name="remarks"></a>Poznámky

Zdrojová oblast musí být platná a v cíli musí být dostatek místa na pro všechny prvky, které jsou kopírovány.

Vzhledem k tomu, že algoritmus kopíruje zdrojové prvky v pořadí začínajícím prvním prvkem, cílový rozsah se může překrývat se zdrojovým rozsahem, pokud *Poslední* pozice zdrojového rozsahu není obsažena v cílovém rozsahu. `copy`dá se použít k posunutí prvků doleva, ale ne vpravo, pokud není mezi zdrojovými a cílovými rozsahy žádná překrytí. Pokud chcete posunout vpravo libovolný počet pozic, použijte algoritmus [copy_backward](../standard-library/algorithm-functions.md#copy_backward) .

`copy` Algoritmus upravuje pouze hodnoty, na které odkazují iterátory, přiřazuje nové hodnoty prvkům v cílové oblasti. Nelze ho použít k vytvoření nových prvků a nelze vložit prvky do prázdného zásobníku přímo.

### <a name="example"></a>Příklad

```cpp
// alg_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="copy_backward"></a>copy_backward

Přiřadí hodnoty prvků ze zdrojového rozsahu do cílového rozsahu a provede iterace přes zdrojové sekvence prvků a přiřadí je novým pozicím směrem dozadu.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 copy_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>Parametry

*první*\
Obousměrný iterátor, který adresuje umístění prvního prvku ve zdrojové oblasti.

*posledního*\
Obousměrný iterátor, který adresuje umístění jedno místo za posledním prvkem ve zdrojové oblasti.

*destEnd*\
Obousměrný iterátor, který adresuje umístění jedno místo za posledním prvkem v cílové oblasti.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující pozici, která je jedno za posledním prvkem v cílové oblasti, tedy iterátor adres *destEnd* -(*Poslední* -  *).*

### <a name="remarks"></a>Poznámky

Zdrojová oblast musí být platná a v cíli musí být dostatek místa na pro všechny prvky, které jsou kopírovány.

Algoritmus ukládá přísnější požadavky než `copy` algoritmus. `copy_backward` Vstupní i výstupní iterátory musí být obousměrné.

Algoritmy a [move_backward](../standard-library/algorithm-functions.md#move_backward) jsou jediné C++ standardní algoritmy knihovny označující výstupní rozsah s iterátorem ukazujícím na konec cílového rozsahu. `copy_backward`

Vzhledem k tomu, že algoritmus kopíruje zdrojové prvky v pořadí od posledního prvku, cílový rozsah se může překrývat s rozsahem zdroje, zadaný *první* pozice zdrojového rozsahu není obsažena v cílovém rozsahu. `copy_backward`dá se použít k posunu prvků doprava, ale ne vlevo, pokud nedojde k překrytí mezi zdrojovým a cílovým rozsahem. Pokud chcete posunout vlevo libovolný počet pozic, použijte algoritmus [copy](../standard-library/algorithm-functions.md#copy) .

`copy_backward` Algoritmus upravuje pouze hodnoty, na které odkazují iterátory, přiřazuje nové hodnoty prvkům v cílové oblasti. Nelze ho použít k vytvoření nových prvků a nelze vložit prvky do prázdného zásobníku přímo.

### <a name="example"></a>Příklad

```cpp
// alg_copy_bkwd.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="copy_if"></a>copy_if

V rozsahu prvků zkopíruje prvky, které jsou pro zadanou podmínku **pravdivé** .

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator dest,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor, který označuje začátek rozsahu pro kontrolu podmínky.

*posledního*\
Vstupní iterátor, který označuje konec rozsahu.

*propojovací*\
Výstupní iterátor, který označuje cíl kopírovaných prvků.

*čekání*\
Podmínka, proti které je testován každý prvek v rozsahu. Tento stav je poskytován uživatelem definovaným objektovou funkcí predikátu. Unární predikát přijímá jeden argument a vrátí **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor, který se u každého prvku, který splňuje podmínku, zvyšuje jako *cílový* . Jinými slovy, návratová hodnota minus *cíl* se rovná počtu zkopírovaných prvků.

### <a name="remarks"></a>Poznámky

Funkce šablony vyhodnocuje

`if (pred(*first + N)) * dest++ = *(first + N))`

jednou pro každou `N` v rozsahu `[0, last - first)`, `N` pro striktní zvýšení hodnot od nejnižší hodnoty. Pokud *cíl* a *první* označení oblastí úložiště, *cíl* nesmí být v rozsahu `[ first, last )`.

## <a name="copy_n"></a>copy_n

Zkopíruje zadaný počet prvků.

```cpp
template<class InputIterator, class Size, class OutputIterator>
OutputIterator copy_n(
    InputIterator first,
    Size count,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class Size, class ForwardIterator2>
ForwardIterator2 copy_n(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    Size count,
    ForwardIterator2 dest);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor, který určuje, odkud kopírovat prvky.

*výpočtu*\
Typ signed nebo unsigned integer určující počet prvků, které mají být zkopírovány.

*propojovací*\
Výstupní iterátor, který označuje, kam kopírovat prvky.

### <a name="return-value"></a>Návratová hodnota

Vrátí výstupní iterátor, do kterého byly prvky zkopírovány. Je stejná jako vrácená hodnota parametru *cíl* .

### <a name="remarks"></a>Poznámky

Funkce šablony je `*(dest + N) = *(first + N))` vyhodnocena jednou `N` v rozsahu `[0, count)`, pro striktní zvýšení hodnot `N` od nejnižší hodnoty. Pak se vrátí `dest + N`. Pokud *cíl* a *první* označení oblastí úložiště, *cíl* nesmí být v rozsahu `[first, last)`.

### <a name="example"></a>Příklad

```cpp
// alg_copy_n.cpp
// compile with: cl /EHsc /W4 alg_copy_n.cpp
#include <algorithm>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    string s1{"dandelion"};
    string s2{"badger"};

    cout << s1 << " + " << s2 << " = ";

    // Copy the first 3 letters from s1
    // to the first 3 positions in s2
    copy_n(s1.begin(), 3, s2.begin());

    cout << s2 << endl;
}
```

```Output
dandelion + badger = danger
```

## <a name="count"></a>výpočtu

Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané hodnotě.

```cpp
template<class InputIterator, class Type>
typename iterator_traits<InputIterator>::difference_type count(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
typename iterator_traits<ForwardIterator>::difference_type
count(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor adresující pozici prvního prvku v rozsahu, který chcete procházet.

*posledního*\
Vstupní iterátor adresující pozici jednu za poslední prvek v rozsahu, který chcete procházet.

*osa*\
Hodnota prvků, které se mají spočítat.

### <a name="return-value"></a>Návratová hodnota

Rozdílový `InputIterator` typ, který počítá počet prvků v rozsahu [*First*, *Last*), které mají hodnotu *hodnoty.*

### <a name="remarks"></a>Poznámky

`operator==` Pro určení shody mezi elementem a zadanou hodnotou musí být mezi jeho operandy vztah rovnosti.

Tento algoritmus je zobecněn pro počítání prvků, které splňují libovolný predikát, pomocí funkce šablony [count_if](../standard-library/algorithm-functions.md#count_if).

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

## <a name="count_if"></a>count_if

Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané podmínce.

```cpp
template<class InputIterator, class UnaryPredicate>
typename iterator_traits<InputIterator>::difference_type count_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
typename iterator_traits<ForwardIterator>::difference_type
count_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor adresující pozici prvního prvku v rozsahu, který má být prohledán.

*posledního*\
Vstupní iterátor adresující pozici jednu za poslední prvek v rozsahu, který chcete prohledat.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněna, pokud se má spočítat element. Unární predikát přijímá jeden argument a vrátí **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které splní podmínku určenou predikátem.

### <a name="remarks"></a>Poznámky

Tato funkce šablony je generalizace [počtu](../standard-library/algorithm-functions.md#count)algoritmů a nahrazuje predikát "rovná se konkrétní hodnotě" s libovolným predikátem.

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

## <a name="equal"></a>výši

Porovná dva rozsahy element podle elementu pro rovnost nebo ekvivalenci ve smyslu určeném binárním predikátem.

Použijte `std::equal` při porovnávání prvků v různých typech kontejnerů (například `vector` a `list`) nebo při porovnávání různých typů prvků, nebo pokud potřebujete porovnat dílčí rozsahy kontejnerů. V opačném případě při porovnávání prvků stejného typu ve stejném typu kontejneru použijte nečlen `operator==` , který je k dispozici pro každý kontejner.

Používejte přetížení dvojího rozsahu v kódu C++ 14, protože přetížení, která přijímají pouze jeden iterátor pro druhý rozsah, nebudou detekovat rozdíly, pokud je druhý rozsah delší než první rozsah a výsledkem bude nedefinované chování, pokud je druhý rozsah kratší. než první rozsah.

```cpp
template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred); // C++14

template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Vstupní iterátor adresující pozici prvního prvku v prvním rozsahu, který má být testován.

*last1*\
Vstupní iterátor adresující pozici jednu za poslední prvek v prvním rozsahu, který má být testován.

*first2*\
Vstupní iterátor adresující pozici prvního prvku v druhém rozsahu, který má být testován.

*last2*\
Vstupní iterátor adresující pozici jednoho za poslední prvek v druhém rozsahu, který má být testován.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněna, pokud mají být provedeny dva prvky jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud a pouze v případě, že jsou rozsahy identické nebo ekvivalentní pod binárním predikátem při porovnání elementu podle elementu; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Rozsah, který má být prohledán, musí být platný. všechny iterátory musí být možné odkázat a poslední pozice je dosažitelná z první pomocí přírůstku.

Pokud jsou tyto dva rozsahy stejné, pak je složitá doba složitosti algoritmu lineární v počtu prvků obsažených v rozsahu. V opačném případě funkce okamžitě vrátí **hodnotu false**.

`operator==` Ani uživatelsky definovaný predikát není vyžadován k zavedení vztahu rovnosti, který je symetrický, reflexivní a tranzitivní mezi jeho operandy.

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

## <a name="equal_range"></a>equal_range

V případě seřazeného rozsahu nalezne dílčí rozsah, ve kterém jsou všechny prvky ekvivalentní dané hodnotě.

```cpp
template<class ForwardIterator, class Type>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*první*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který chcete prohledat.

*posledního*\
Dopředný iterátor, který adresuje pozici jednu za posledním prvkem v rozsahu, který chcete prohledat.

*osa*\
Hledaná hodnota v seřazeném rozsahu.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Relační predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

Pár dopředných iterátorů, které určují dílčí rozsah obsažený v zobrazeném rozsahu, ve kterém jsou všechny prvky ekvivalentní *hodnotě* ve smyslu definovaném použitým binárním predikátem (buď *před* , nebo výchozí, méně než).

Nejsou-li žádné prvky v rozsahu ekvivalentní *hodnotě*, dopředné iterátory v vrácené dvojici jsou stejné a zadejte bod, do kterého může být *hodnota* vložena bez narušení pořadí rozsahu.

### <a name="remarks"></a>Poznámky

První iterátor páru vráceného algoritmem je [lower_bound](../standard-library/algorithm-functions.md#lower_bound)a druhý iterátor je [Upper_bound](../standard-library/algorithm-functions.md#upper_bound).

Rozsah musí být seřazen podle predikátu, který je k `equal_range`dispozici. Pokud například použijete větší predikát, musí být rozsah seřazen v sestupném pořadí.

Prvky v možném prázdném dílčím rozsahu definované dvojicí iterátorů vrácených `equal_range` pomocí budou ekvivalentní *hodnotě* ve smyslu definovaném použitým predikátem.

Složitost algoritmu je logaritmický pro iterátory s náhodným přístupem a v opačném případě lineární, přičemž počet kroků je úměrný (*Poslední* - *první*).

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

template<class T> void equal_range_demo( const vector<T>& original_vector, T value )
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
        = equal_range( v.begin(), v.end(), value );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

template<class T, class F> void equal_range_demo( const vector<T>& original_vector, T value, F pred, string predname )
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
        = equal_range( v.begin(), v.end(), value, pred );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
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

## <a name="fill"></a>vyplnění

Každému prvku v zadaném rozsahu přiřadí stejnou novou hodnotu.

```cpp
template<class ForwardIterator, class Type>
void fill(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void fill(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který chcete procházet.

*posledního*\
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu, který chcete procházet.

*osa*\
Hodnota, která má být přiřazena k prvkům v rozsahu [*First*, *Last*).

### <a name="remarks"></a>Poznámky

Cílový rozsah musí být platný; všechny ukazatelé musí být možné odkázat a poslední pozice je dosažitelná z první pomocí přírůstku. Složitost je lineární s velikostí rozsahu.

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
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="fill_n"></a>fill_n

Přiřadí novou hodnotu zadanému počtu prvků v rozsahu, který začíná konkrétním prvkem.

```cpp
template<class OutputIterator, class Size, class Type>
OutputIterator fill_n(
    OutputIterator first,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator fill_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    const Type& value);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Výstupní iterátor adresující pozici prvního prvku v rozsahu, který má být přiřazena hodnota *hodnoty.*

*výpočtu*\
Typ podepsaný nebo unsigned integer určující počet prvků, které mají být přiřazeny hodnoty.

*osa*\
Hodnota, která má být přiřazena k prvkům v rozsahu [*First*, *First + Count*).

### <a name="return-value"></a>Návratová hodnota

Iterátor na prvek, který následuje poslední prvek vyplněný, pokud je *počet* > nula, jinak první prvek.

### <a name="remarks"></a>Poznámky

Cílový rozsah musí být platný; všechny ukazatelé musí být možné odkázat a poslední pozice je dosažitelná z první pomocí přírůstku. Složitost je lineární s velikostí rozsahu.

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
    vector<int> v;

    for ( auto i = 0 ; i < 9 ; ++i )
        v.push_back( 0 );

    cout << " vector v = ( " ;
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

## <a name="find"></a>najít

Vyhledá pozici prvního výskytu prvku v rozsahu, který má zadanou hodnotu.

```cpp
template<class InputIterator, class Type>
InputIterator find(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor adresující pozici prvního prvku v rozsahu, který má být prohledán pro zadanou hodnotu.

*posledního*\
Vstupní iterátor adresující pozici jednu za poslední prvek v rozsahu, který má být prohledán pro zadanou hodnotu.

*osa*\
Hodnota, která má být prohledána.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první výskyt zadané hodnoty v prohledávané oblasti. Pokud není nalezen žádný element s ekvivalentní hodnotou, vrátí *Poslední*.

### <a name="remarks"></a>Poznámky

`operator==` Pro určení shody mezi elementem a zadanou hodnotou musí být mezi jeho operandy vztah rovnosti.

Příklad kódu použití `find()`naleznete v tématu [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="find_end"></a>find_end

Vyhledá v rozsahu poslední dílčí sekvenci, která je shodná se zadanou sekvencí nebo která je ekvivalentní ve smyslu určeném binárním predikátem.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class Pred>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Pred pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*first1*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který chcete prohledat.

*last1*\
Dopředný iterátor, který adresuje pozici jednu za posledním prvkem v rozsahu, který chcete prohledat.

*first2*\
Dopředný iterátor, který adresuje umístění prvního prvku v hledaném rozsahu.

*last2*\
Dopředný iterátor, který adresuje pozici jednu za posledním prvkem v hledaném rozsahu.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněna, pokud mají být provedeny dva prvky jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje umístění prvního prvku poslední dílčí sekvence v rámci [first1, last1), který odpovídá zadané sekvenci [First2, last2).

### <a name="remarks"></a>Poznámky

`operator==` Pro určení shody mezi elementem a zadanou hodnotou musí být mezi jeho operandy vztah rovnosti.

Odkazované rozsahy musí být platné. všechny ukazatele musí být možné odkázat a v rámci každé sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

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
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

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
    vector<int>::iterator result1;
    result1 = find_end ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a match of L1 in v1 that begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
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

## <a name="find_first_of"></a>find_first_of

Vyhledá první výskyt jedné z několika hodnot v cílovém rozsahu nebo první výskyt jednoho z několika prvků, které jsou ekvivalentní ve smyslu určeném binárním predikátem zadané sadě prvků.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*first1*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který chcete prohledat.

*last1*\
Dopředný iterátor, který adresuje pozici jednu za posledním prvkem v rozsahu, který chcete prohledat.

*first2*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který má být porovnán.

*last2*\
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu, který má být porovnán.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněna, pokud mají být provedeny dva prvky jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje umístění prvního prvku první dílčí sekvence, který odpovídá zadané sekvenci nebo který je ekvivalentní ve smyslu určeném binárním predikátem.

### <a name="remarks"></a>Poznámky

`operator==` Pro určení shody mezi elementem a zadanou hodnotou musí být mezi jeho operandy vztah rovnosti.

Odkazované rozsahy musí být platné. všechny ukazatele musí být možné odkázat a v rámci každé sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

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
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

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
    vector<int>::iterator result1;
    result1 = find_first_of ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
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

## <a name="find_if"></a>find_if

Vyhledá pozici prvního výskytu prvku v rozsahu, který splňuje zadanou podmínku.

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující pozici prvního prvku v rozsahu, který má být prohledán.

*posledního*\
Vstupní iterátor adresující pozici jednu za poslední prvek v rozsahu, který chcete prohledat.

*čekání*\
Objekt funkce predikátu definovaný uživatelem nebo [výraz lambda](../cpp/lambda-expressions-in-cpp.md) definující podmínku, která má být splněna prvkem, který má být vyhledán. Unární predikát přijímá jediný argument a vrátí **hodnotu true** , pokud je splněna, nebo **false** , pokud není splněna. Signatura `InputIterator` předchází *musí být* `bool pred(const T& arg);`, kde `T` je typ, na který lze implicitně převést při zpětném odkazování. Klíčové  slovo const je zobrazeno pouze k ilustraci, že objekt funkce nebo výraz lambda by neměl upravovat argument.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor, který odkazuje na první prvek v rozsahu, který splňuje podmínku určenou predikátem (výsledkem predikátu je **true**). Pokud nebyl nalezen žádný element pro splnění predikátu, vrátí *Poslední*.

### <a name="remarks"></a>Poznámky

Tato funkce šablony je generalizace algoritmu [find](../standard-library/algorithm-functions.md#find)a nahrazuje predikát "rovná se konkrétní hodnotě" s libovolným predikátem. Pro logický opak (najít první prvek, který nesplňuje predikát), viz [find_if_not](../standard-library/algorithm-functions.md#find_if_not).

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

## <a name="find_if_not"></a>find_if_not

Vrátí první prvek v zadaném rozsahu, který nesplňuje podmínku.

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if_not(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if_not(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující pozici prvního prvku v rozsahu, který má být prohledán.

*posledního*\
Vstupní iterátor adresující pozici jednu za poslední prvek v rozsahu, který chcete prohledat.

*čekání*\
Objekt funkce predikátu definovaný uživatelem nebo [výraz lambda](../cpp/lambda-expressions-in-cpp.md) definující podmínku, která nebude splněna prvkem, který je prohledáván. Unární predikát přijímá jediný argument a vrátí **hodnotu true** , pokud je splněna, nebo **false** , pokud není splněna. Signatura `InputIterator` předchází *musí být* `bool pred(const T& arg);`, kde `T` je typ, na který lze implicitně převést při zpětném odkazování. Klíčové  slovo const je zobrazeno pouze k ilustraci, že objekt funkce nebo výraz lambda by neměl upravovat argument.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor, který odkazuje na první prvek v rozsahu, který nesplňuje podmínku určenou predikátem (výsledkem predikátu je **false**). Pokud všechny prvky vyhoví predikát (výsledkem predikátu je **hodnota true** pro každý prvek), vrátí *Poslední*.

### <a name="remarks"></a>Poznámky

Tato funkce šablony je generalizace algoritmu [find](../standard-library/algorithm-functions.md#find)a nahrazuje predikát "rovná se konkrétní hodnotě" s libovolným predikátem. Pro logický opak (najít první prvek, který splňuje predikát), viz [find_if](../standard-library/algorithm-functions.md#find_if).

Příklad kódu, který lze `find_if_not()`snadno upravit, naleznete v tématu [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="for_each"></a>for_each

Na každý prvek v pořadí dopředu v rozsahu použije zadaný objekt funkce a vrátí objekt funkce.

```cpp
template<class InputIterator, class Function>
Function for_each(
    InputIterator first,
    InputIterator last,
    Function func);

template<class ExecutionPolicy, class ForwardIterator, class Function>
void for_each(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Function func);
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující pozici prvního prvku v rozsahu, ve kterém má být provozován.

*posledního*\
Vstupní iterátor adresující pozici jednu za poslední prvek v rozsahu, na kterém je provozován.

*kláves*\
Uživatelem definovaný objekt funkce, který je použit pro každý prvek v rozsahu.

### <a name="return-value"></a>Návratová hodnota

Kopie objektu funkce poté, co byla použita na všechny prvky v rozsahu.

### <a name="remarks"></a>Poznámky

Algoritmus `for_each` je velmi flexibilní a umožňuje úpravu každého prvku v rámci rozsahu v různých uživatelsky definovaných způsobech. Funkce založena se dají znovu použít v upraveném formuláři předáním různých parametrů. Uživatelsky definované funkce mohou shromažďovat informace v rámci vnitřního stavu, který algoritmus může vracet po zpracování všech prvků v rozsahu.

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Složitost je lineární s nejvyšším (*posledním* -  *)* porovnáním.

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
    MultValue ( const Type& value ) : Factor ( value ) {
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
    void operator( ) ( int elem )
    {
        num++;      // Increment the element count
        sum += elem;   // Add the value to the partial sum
    }

    // return Average
    operator double( )
    {
        return static_cast<double> (sum) /
            static_cast<double> (num);
    }
};

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Using for_each to multiply each element by a Factor
    for_each ( v1.begin( ), v1.end( ), MultValue<int> ( -2 ) );

    cout << "Multiplying the elements of the vector v1\n "
            << "by the factor -2 gives:\n v1mod1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // The function object is templatized and so can be
    // used again on the elements with a different Factor
    for_each (v1.begin( ), v1.end( ), MultValue<int> (5 ) );

    cout << "Multiplying the elements of the vector v1mod\n "
            << "by the factor 5 gives:\n v1mod2 = ( " ;
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
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
Multiplying the elements of the vector v1
by the factor -2 gives:
v1mod1 = ( 8 6 4 2 0 -2 -4 ).
Multiplying the elements of the vector v1mod
by the factor 5 gives:
v1mod2 = ( 40 30 20 10 0 -10 -20 ).
The average of the elements of v1 is:
Average ( v1mod2 ) = 10.
```

## <a name="for_each_n"></a>for_each_n

```cpp
template<class InputIterator, class Size, class Function>
InputIterator for_each_n(
    InputIterator first,
    Size n,
    Function f);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Function>
ForwardIterator for_each_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size n,
    Function f);
```

## <a name="generate"></a>vytváří

Přiřadí hodnoty generované objektem funkce každému prvku v rozsahu.

```cpp
template<class ForwardIterator, class Generator>
void generate(
    ForwardIterator first,
    ForwardIterator last,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Generator>
void generate(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    Generator gen);
```

### <a name="parameters"></a>Parametry

*první*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, do kterého mají být hodnoty přiřazeny.

*posledního*\
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu, do kterého mají být hodnoty přiřazeny.

*pole*\
Objekt funkce, který je volán bez argumentů, který slouží ke generování hodnot, které mají být přiřazeny ke každému prvku v rozsahu.

### <a name="remarks"></a>Poznámky

Objekt funkce je vyvolán pro každý prvek v rozsahu a nemusí vracet stejnou hodnotu pokaždé, když je volána. Může například číst ze souboru nebo odkazovat na a upravit místní stav. Typ výsledku generátoru musí být převoditelné na typ hodnoty pro dopředné iterátory daného rozsahu.

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Složitost je lineární, kde je požadováno přesně `last`(  -  `first`) volání generátoru.

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
    vector<int> v1 ( 5 );
    vector<int>::iterator Iter1;
    deque<int> deq1 ( 5 );
    deque<int>::iterator d1_Iter;

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

## <a name="generate_n"></a>generate_n

Přiřadí hodnoty generované objektem funkce na zadaný počet prvků v rozsahu a vrátí na pozici jednu za poslední přiřazenou hodnotou.

```cpp
template<class OutputIterator, class Diff, class Generator>
void generate_n(
    OutputIterator first,
    Diff count,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Generator>
ForwardIterator generate_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    Generator gen);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Výstupní iterátor adresující pozici prvního prvku v rozsahu, do kterého mají být hodnoty přiřazeny.

*výpočtu*\
Podepsaný nebo unsigned integer typ určující počet prvků, které mají být přiděleny hodnotou funkcí generátoru.

*pole*\
Objekt funkce, který je volán bez argumentů, který slouží ke generování hodnot, které mají být přiřazeny ke každému prvku v rozsahu.

### <a name="remarks"></a>Poznámky

Objekt funkce je vyvolán pro každý prvek v rozsahu a nemusí vracet stejnou hodnotu pokaždé, když je volána. Může například číst ze souboru nebo odkazovat na a upravit místní stav. Typ výsledku generátoru musí být převoditelné na typ hodnoty pro dopředné iterátory daného rozsahu.

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Složitost je lineární, přičemž přesně `count` volá generátor, který je požadován.

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

template <typename C>
void print(const string& s, const C& c)
{
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

## <a name="includes"></a>zahrnující

Ověřuje, zda jeden seřazený rozsah obsahuje všechny prvky obsažené ve druhém seřazeném rozsahu, kde kritérium pořadí nebo ekvivalence mezi prvky může být určeno binárním predikátem.

```cpp
template<class InputIterator1, class InputIterator2>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class Compare>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Vstupní iterátor adresující pozici prvního prvku v prvním ze dvou seřazených zdrojových rozsahů, které mají být testovány, zda jsou všechny prvky druhého obsaženy v prvním.

*last1*\
Vstupní iterátor adresující pozici jednu za poslední prvek v prvním ze dvou seřazených zdrojových rozsahů, které mají být testovány, zda jsou všechny prvky druhého obsaženy v prvním.

*first2*\
Vstupní iterátor adresující pozici prvního prvku v druhé ze dvou po sobě jdoucích zdrojových rozsahů, které mají být testovány, zda jsou všechny prvky druhého obsaženy v prvním.

*last2*\
Vstupní iterátor adresující pozici jednoho za poslední prvek v druhé ze dvou po sobě jdoucích zdrojových rozsahů, které mají být testovány, zda jsou všechny prvky druhého obsaženy v prvním.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Relační predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud první seřazený rozsah obsahuje všechny prvky ve druhém seřazeném rozsahu; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Dalším způsobem, jak si představit tento test, je, že se určilo, jestli je druhý zdrojový rozsah podmnožinou prvního zdrojového rozsahu.

Odkazované zdrojové rozsahy musí být platné; všechny ukazatele musí být možné odkázat a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Seřazené zdrojové rozsahy musí být uspořádány jako předběžná podmínka pro použití algoritmu v souladu se stejným pořadím, jaké má algoritmus použít k řazení kombinovaných rozsahů.

Zdrojové rozsahy nejsou tímto algoritmem `merge`změněny.

Typy hodnot vstupních iterátorů musí být menší než srovnatelné, aby bylo možné je seřadit, což znamená, že vzhledem k dvěma prvkům je možné určit, že jsou ekvivalentní (v tom smyslu, že ani jeden není menší než druhý) nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Přesněji, algoritmus testuje, zda všechny prvky v prvním seřazeném rozsahu v rámci zadaného binárního predikátu mají stejné řazení jako v druhém seřazeném rozsahu.

Složitost algoritmu je lineární s při nejvíce `2 * ((last1 - first1) - (last2 - first2)) - 1` porovnávání pro neprázdné zdrojové rozsahy.

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
    vector<int> v1a, v1b;
    vector<int>::iterator Iter1a, Iter1b;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -2 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-2 ; ii <= 3 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b );
    vector<int>::iterator Iter2a, Iter2b;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );
    v2a.pop_back( );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) ;
    vector<int>::iterator Iter3a, Iter3b;
    reverse (v3a.begin( ), v3a.end( ) );
    v3a.pop_back( );
    v3a.pop_back( );
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To test for inclusion under an asscending order
    // with the default binary predicate less<int>( )
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
        v2b.begin( ), v2b.end( ), greater<int>( ) );
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
At least one of the elements in vector v3b is not contained under mod_lesser in vector v3a.
```

## <a name="inplace_merge"></a>inplace_merge

Kombinuje prvky ze dvou po sobě následujících seřazených rozsahů do jednoho seřazeného rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class BidirectionalIterator>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class BidirectionalIterator, class Compare>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);

template<class ExecutionPolicy, class BidirectionalIterator>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator, class Compare>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Obousměrný iterátor adresující pozici prvního prvku v prvním ze dvou po sobě jdoucích rozsahů, které budou kombinovány a seřazeny do jednoho rozsahu.

*Blízký*\
Obousměrný iterátor, který adresování pozice prvního prvku v druhé ze dvou po sobě jdoucích rozsahů bude kombinován a seřazen do jednoho rozsahu.

*posledního*\
Obousměrný iterátor, který adresuje pozici jednu za poslední prvek v druhé ze dvou po sobě jdoucích rozsahů, které budou kombinovány a seřazeny do jednoho rozsahu.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Relační predikát přijímá dva argumenty a by měl vracet **hodnotu true** , pokud je první prvek menší než druhý prvek a jinak **false** .

### <a name="remarks"></a>Poznámky

Odkazovaná po sobě jdoucí rozsahy musí být platné. všechny ukazatele musí být možné odkázat a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Seřazené po sobě jdoucí rozsahy musí být uspořádány jako předběžná podmínka pro použití `inplace_merge` algoritmu v souladu se stejným pořadím, jaké má použít algoritmus k řazení kombinovaných rozsahů. Operace je stabilní, protože relativní pořadí prvků v rámci jednotlivých rozsahů je zachováno. V případě, že existují ekvivalentní prvky ve zdrojovém rozsahu, element je první rozsah před prvek od druhé v kombinovaném rozsahu.

Složitost závisí na dostupné paměti, protože algoritmus přiděluje paměť do dočasné vyrovnávací paměti. Je-li k dispozici dostatek paměti, nejlepším případem `(last - first) - 1` je lineární porovnávání, pokud není k dispozici žádná pomocná paměť `N log(N)`, nejhorší případ je, kde *N* = *Poslední* - byl*první*.

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
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, Iter3;

    // Constructing vector v1 with default less-than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
    {
        v1.push_back( ii );
    }

    cout << "Original vector v1 with subranges sorted by the\n "
            << "binary predicate less than is v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2 ( v1 );
    vector<int>::iterator break2;
    break2 = find ( v2.begin( ), v2.end( ), -5 );
    sort ( v2.begin( ), break2 , greater<int>( ) );
    sort ( break2 , v2.end( ), greater<int>( ) );
    cout << "Original vector v2 with subranges sorted by the\n "
            << "binary predicate greater is v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3 ( v1 );
    vector<int>::iterator break3;
    break3 = find ( v3.begin( ), v3.end( ), -5 );
    sort ( v3.begin( ), break3 , mod_lesser );
    sort ( break3 , v3.end( ), mod_lesser );
    cout << "Original vector v3 with subranges sorted by the\n "
            << "binary predicate mod_lesser is v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")" << endl;

    vector<int>::iterator break1;
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
binary predicate less than is v1 = ( 0 1 2 3 4 5 -5 -4 -3 -2 -1 0 )
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

## <a name="is_heap"></a>is_heap

Vrátí **hodnotu true** , pokud prvky v zadaném rozsahu tvoří haldu.

```cpp
template<class RandomAccessIterator>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Iterátor náhodného přístupu, který označuje začátek rozsahu pro kontrolu haldy.

*posledního*\
Iterátor náhodného přístupu, který označuje konec rozsahu.

*čekání*\
Podmínka, která má být testována pro řazení prvků. Relační predikát přijímá dva argumenty a vrací **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu true** , pokud prvky v zadaném rozsahu tvoří haldu, **false** , pokud ne.

### <a name="remarks"></a>Poznámky

První funkce šablony vrátí [is_heap_until](../standard-library/algorithm-functions.md#is_heap_until)`(first , last) == last`.

Druhá funkce šablony vrátí

`is_heap_until(first, last, pred) == last`.

## <a name="is_heap_until"></a>is_heap_until

Vrátí iterátor umístěný v prvním prvku v rozsahu [ `first`, `last`), který nesplňuje podmínku řazení haldy, nebo *ukončí* , pokud rozsah tvoří haldu.

```cpp
template<class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Iterátor náhodného přístupu, který určuje první prvek rozsahu pro kontrolu haldy.

*posledního*\
Iterátor náhodného přístupu, který určuje konec rozsahu pro kontrolu haldy.

*čekání*\
Binární predikát, který určuje přísnou slabou podmínku řazení definující haldu. Výchozí predikát je `std::less<>` v případě, že není zadán parametr *před* .

### <a name="return-value"></a>Návratová hodnota

Vrátí *Poslední* , pokud zadaný rozsah tvoří haldu nebo obsahuje jeden nebo méně prvků. V opačném případě vrátí iterátor pro první nalezený prvek, který nesplňuje podmínky haldy.

### <a name="remarks"></a>Poznámky

První funkce šablony vrátí poslední `next` iterátor v `[first, last)` místě, kde `[first, next)` je halda seřazená pomocí objektu `std::less<>`Function. Pokud je vzdálenost `last - first` menší než 2, funkce vrátí *Poslední*.

Druhá funkce šablony se chová stejně jako první, s tím rozdílem, že používá predikát *před* , nikoli `std::less<>` jako podmínku řazení haldy.

## <a name="is_partitioned"></a>is_partitioned

Vrátí **hodnotu true** , pokud všechny prvky v zadaném rozsahu, které testuje **hodnotu true** pro podmínku, předcházejí všem prvkům, které testují **false**.

```cpp
template<class InputIterator, class UnaryPredicate>
bool is_partitioned(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool is_partitioned(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor, který označuje, kde rozsah začíná kontrolovat podmínku.

*posledního*\
Vstupní iterátor, který označuje konec rozsahu.

*čekání*\
Podmínka, která se má testovat. Toto je poskytováno uživatelem definovaný objekt funkce predikátu, který definuje podmínku, která má být splněna prvkem, který je prohledáván. Unární predikát přijímá jeden argument a vrátí **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu pravda** , pokud všechny prvky v zadaném rozsahu, které test **true** pro podmínku předchází všem prvkům, které testují **hodnotu false**, a v opačném případě vrátí **hodnotu false**.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí **hodnotu true** pouze v případě, že `[first, last)` jsou všechny prvky v děleny *před*; to znamená, `X` že `[first, last)` všechny prvky `pred (X)` v, pro které je pravdivá `Y` , se vyskytnou před všemi prvky, pro které je **false**. `pred (Y)`

## <a name="is_permutation"></a>is_permutation

Vrátí hodnotu true, pokud oba rozsahy obsahují stejné prvky, bez ohledu na to, zda jsou prvky ve stejném pořadí. Používejte přetížení dvojího rozsahu v kódu C++ 14, protože přetížení, která přijímají pouze jeden iterátor pro druhý rozsah, nebudou detekovat rozdíly, pokud je druhý rozsah delší než první rozsah a výsledkem bude nedefinované chování, pokud je druhý rozsah kratší. než první rozsah.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate Pred);

// C++14
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*first1*\
Dopředný iterátor, který odkazuje na první prvek rozsahu.

*last1*\
Dopředný iterátor, který odkazuje na jeden za poslední prvek rozsahu.

*first2*\
Dopředný iterátor, který odkazuje na první prvek druhého rozsahu, který se používá pro porovnání.

*last2*\
Dopředný iterátor, který odkazuje na jeden za poslední prvek druhého rozsahu, který se používá pro porovnání.

*čekání*\
Predikát, který testuje rovnost a vrací **bool**.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud lze rozsahy uspořádat tak, aby byly identické podle predikátu komparátor; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

`is_permutation`má v nejhorším případě kvadratickou složitost.

První funkce šablony předpokládá, že existuje tolik prvků v rozsahu, který začíná na *First2* , protože v rozsahu, který je určen `[first1, last1)`. Pokud je ve druhém rozsahu více prvků, jsou ignorovány; Pokud je k dispozici méně, dojde k nedefinovanému chování. Třetí funkce šablony (C++ 14 a novější) neprovádí tento předpoklad. Obě vrátí **hodnotu true** pouze v případě, že pro každý element X v rozsahu `[first1, last1)` určeném je to mnoho elementů Y ve stejném rozsahu, pro který je X = = Y, jak je v rozsahu  od First2 `[first2, last2)`nebo. V `operator==` tomto příkladu musí probíhat srovnávací porovnání mezi operandy.

Druhá a čtvrtá funkce šablony se chovají stejně, s tím rozdílem, `operator==(X, Y)` že `Pred(X, Y)`nahrazují. Aby bylo možné správně fungovat, musí být predikát symetrický, reflexivní a tranzitivní.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `is_permutation`:

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

## <a name="is_sorted"></a>is_sorted

Vrátí **hodnotu true** , pokud prvky v zadaném rozsahu jsou v seřazeném pořadí.

```cpp
template<class ForwardIterator>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který označuje, kde začíná rozsah kontroly.

*posledního*\
Dopředný iterátor, který označuje konec rozsahu.

*čekání*\
Podmínka, která má být testována k určení objednávky mezi dvěma prvky. Relační predikát přijímá dva argumenty a vrací **hodnotu true** nebo **false**. Tím se provede stejný úkol jako `operator<`.

### <a name="remarks"></a>Poznámky

První funkce šablony vrátí [is_sorted_until](#is_sorted_until)`( first, last ) == last`. `operator<` Funkce provede porovnání pořadí.

Druhá funkce šablony vrátí `is_sorted_until( first, last , pred ) == last`. Funkce predikátu *před* provádí porovnání pořadí.

## <a name="is_sorted_until"></a>is_sorted_until

Vrátí hodnotu `ForwardIterator` , která je nastavena na poslední prvek v setříděném pořadí ze zadaného rozsahu.

Druhá verze umožňuje poskytnout objekt funkce porovnání, který vrací **hodnotu true** , pokud dva dané prvky jsou v seřazeném pořadí, a jinak **false** .

```cpp
template<class ForwardIterator>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který označuje, kde začíná rozsah kontroly.

*posledního*\
Dopředný iterátor, který označuje konec rozsahu.

*čekání*\
Podmínka, která má být testována k určení objednávky mezi dvěma prvky. Relační predikát přijímá dva argumenty a vrací **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

`ForwardIterator` Vrátí sadu na poslední prvek v setříděném pořadí. Seřazená sekvence začíná *první*.

### <a name="remarks"></a>Poznámky

První funkce šablony vrátí poslední `next` iterátor v `[first, last]` , `[first, next)` takže se jedná o seřazenou sekvenci seřazenou podle `operator<`. Pokud `distance()` je menší než 2, funkce vrátí *Poslední*.

Druhá funkce šablony se chová stejně, s tím rozdílem, že `operator<(X, Y)` nahrazuje `pred(X, Y)`.

## <a name="iter_swap"></a>iter_swap

Vymění dvě hodnoty odkazované dvojicí zadaných iterátorů.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
void iter_swap( ForwardIterator1 left, ForwardIterator2 right );
```

### <a name="parameters"></a>Parametry

*zbývá*\
Jeden z předávacích iterátorů, jejichž hodnota má být vyměněna.

*Kliknutím*\
Druhá z dopředných iterátorů, jejichž hodnota má být vyměněna.

### <a name="remarks"></a>Poznámky

`swap`by měla být použita v předvolbách **iter_swap**, která byla součástí C++ standardu pro zpětnou kompatibilitu. Pokud `Fit1` `iter_swap( Fit1, Fit2 )` `swap( *Fit1, *Fit2 )`a `Fit2` jsou iterátory dopředné, je ekvivalentem.

Typy hodnot vstupních iterátorů pro vstup musí mít stejnou hodnotu.

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
    vector<int> v1;
    vector<int>::iterator Iter1;
    deque<int> deq2;
    deque<int>::iterator d2_Iter;

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

## <a name="lexicographical_compare"></a>lexicographical_compare

Porovná prvek po prvku mezi dvěma sekvencemi k určení, která z nich je menší.

```cpp
template<class InputIterator1, class InputIterator2>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class Compare>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Vstupní iterátor adresující pozici prvního prvku v prvním rozsahu, který má být porovnán.

*last1*\
Vstupní iterátor adresující pozici jednu za poslední prvek v prvním rozsahu, který má být porovnán.

*first2*\
Vstupní iterátor adresující pozici prvního prvku v druhém rozsahu, který má být porovnán.

*last2*\
Vstupní iterátor adresující pozici jednu za poslední prvek v druhém rozsahu, který se má porovnat.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Relační predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je první rozsah lexikograficky menší než druhý rozsah; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání lexicographical mezi sekvencemi porovnává jejich element podle prvku až do:

- Najde dva odpovídající elementy nerovné a výsledek jejich porovnání je proveden jako výsledek porovnání mezi sekvencemi.

- Nebyly nalezeny žádné nerovnosti, ale jedna sekvence obsahuje více prvků než druhá a kratší sekvence je považována za méně než delší sekvence.

- Nebyly nalezeny žádné nerovnosti a sekvence mají stejný počet prvků, takže sekvence jsou stejné a výsledek porovnání je **false**.

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
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

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

## <a name="lower_bound"></a>lower_bound

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
    BinaryPredicate pred );
```

### <a name="parameters"></a>Parametry

*první*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který chcete prohledat.

*posledního*\
Dopředný iterátor, který adresuje pozici jednu za posledním prvkem v rozsahu, který chcete prohledat.

*osa*\
Hodnota, jejíž první pozice nebo možná první pozice je prohledávána v seřazeném rozsahu.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor na pozici prvního prvku v seřazeném rozsahu s hodnotou, která je větší než nebo rovna zadané hodnotě, kde rovnocennost je určena binárním predikátem.

### <a name="remarks"></a>Poznámky

Odkazovaný seřazený zdrojový rozsah musí být platný; všechny iterátory musí být možné odkázat a v rámci sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Seřazený rozsah je předběžnou podmínkou použití `lower_bound` a tam, kde je řazení stejné jako pro zadání pomocí binárního predikátu.

Rozsah není změněn algoritmem `lower_bound`.

Typy hodnot iterátorů dopředných iterátorů vyžadují, aby byly objednány méně než porovnatelné, což znamená, že vzhledem k dvěma prvkům lze určit, že jsou ekvivalentní (v tom smyslu, že ani jeden není menší než druhý) nebo že jeden je menší než druhý. Výsledkem je řazení mezi neekvivalentními prvky.

Složitost algoritmu je logaritmický pro iterátory s náhodným přístupem a v opačném případě lineární, přičemž počet kroků je úměrný`last - first`hodnotě ().

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
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
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
        << "binary predicate mod_lesser is v3 = ( " ;
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

    // lower_bound of 3 in v3 with the binary predicate mod_lesser
    Result = lower_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The lower_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```

## <a name="make_heap"></a>make_heap

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
    BinaryPredicate pred );
```

### <a name="parameters"></a>Parametry

*první*\
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v rozsahu, který má být převeden na haldu.

*posledního*\
Iterátor náhodného přístupu, který adresuje pozici jednu za posledním prvkem v rozsahu, který se má převést na haldu.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="remarks"></a>Poznámky

Haldy mají dvě vlastnosti:

- První prvek je vždy největší.

- Prvky lze přidat nebo odebrat ve logaritmických čase.

Haldy představují ideální způsob implementace front priorit a používají se v implementaci C++ [třídy priority_queue](../standard-library/priority-queue-class.md)kontejnerů standardní knihovny.

Složitost je lineární, vyžaduje `3 * (last - first)` porovnání.

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
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="max"></a>počet

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
    BinaryPredicate pred);
template<class Type>
constexpr Type& max (
    initializer_list<Type> ilist);
template<class Type, class Pr>
constexpr Type& max(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*zbývá*\
První ze dvou porovnávaných objektů.

*Kliknutím*\
Druhý ze dvou porovnávaných objektů.

*čekání*\
Binární predikát, který slouží k porovnání dvou objektů.

*podklauzule*\
Seznam inicializátorů obsahující objekty, které mají být porovnány.

### <a name="return-value"></a>Návratová hodnota

Větší z těchto dvou objektů, pokud ani není větší; v takovém případě vrátí první z těchto dvou objektů. V případě initializer_list vrací největší z objektů v seznamu.

### <a name="remarks"></a>Poznámky

Algoritmus `max` je neobvyklý v případě, že objekty předány jako parametry. Většina C++ standardních algoritmů knihovny funguje na rozsahu prvků, jejichž pozice je určena iterátory předanými jako parametry. Pokud potřebujete funkci, která pracuje na rozsahu prvků, použijte místo toho [max_element](../standard-library/algorithm-functions.md#max_element) . Visual Studio 2017 umožňuje **constexpr** v přetíženích, která přebírají initializer_list.

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
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

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

## <a name="max_element"></a>max_element

Vyhledá první výskyt největšího prvku v zadaném rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který má být prohledán pro největší prvek.

*posledního*\
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu, který má být prohledán pro největší prvek.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Relační predikát přijímá dva argumenty a by měl vracet **hodnotu true** , pokud je první prvek menší než druhý prvek a jinak **false** .

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje umístění prvního výskytu největšího prvku v prohledávané oblasti.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; u všech ukazatelů musí být možné provést zpětnou odkazování, protože poslední pozice je dosažitelná od první po zvýšení.

Složitost je lineární: `(last - first) - 1` pro neprázdný rozsah jsou vyžadovány porovnání.

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
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

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

## <a name="merge"></a>sloučení

Kombinuje všechny prvky ze dvou seřazených zdrojových rozsahů do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Vstupní iterátor adresující pozici prvního prvku v prvním ze dvou seřazených zdrojových rozsahů, které mají být kombinovány a seřazeny do jednoho rozsahu.

*last1*\
Vstupní iterátor adresující pozici jednu za poslední prvek v prvním ze dvou seřazených zdrojových rozsahů, které mají být kombinovány a seřazeny do jednoho rozsahu.

*first2*\
Vstupní iterátor adresující pozici prvního prvku za sekundu dvou po sobě jdoucích zdrojových rozsahů, které mají být kombinovány a seřazeny do jednoho rozsahu.

*last2*\
Vstupní iterátor adresující pozici jednu za poslední prvek za sekundu dvou po sobě jdoucích zdrojových rozsahů, které mají být kombinovány a seřazeny do jednoho rozsahu.

*vyústit*\
Výstupní iterátor adresující pozici prvního prvku v cílové oblasti, kde jsou dva zdrojové rozsahy sloučeny do jednoho seřazeného rozsahu.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Relační predikát přijímá dva argumenty a by měl vracet **hodnotu true** , pokud je první prvek menší než druhý prvek, a jinak **false** .

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující pozici jednu za poslední prvek v seřazeném cílovém rozsahu.

### <a name="remarks"></a>Poznámky

Odkazované zdrojové rozsahy musí být platné; u všech ukazatelů musí být možné provést zpětnou odkazování a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Cílový rozsah by neměl překrývat žádnou ze zdrojových rozsahů a měl by být dostatečně velký, aby obsahoval cílový rozsah.

Seřazené zdrojové rozsahy musí být uspořádány jako předběžná podmínka pro použití `merge` algoritmu v souladu se stejným pořadím, jaké má použít algoritmus k řazení kombinovaných rozsahů.

Operace je stabilní, protože relativní pořadí prvků v rámci jednotlivých rozsahů je zachováno v cílovém rozsahu. Zdrojové rozsahy nejsou tímto algoritmem `merge`změněny.

Typy hodnot vstupních iterátorů musí být menší než srovnatelné, aby bylo možné je seřadit, což znamená, že vzhledem k dvěma prvkům je možné určit, že jsou ekvivalentní (v tom smyslu, že ani jeden není menší než druhý) nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou v obou zdrojových oblastech ekvivalentní prvky, prvky v prvním rozsahu předcházejí prvky z druhého zdrojového rozsahu v cílovém rozsahu.

Složitost algoritmu je lineární s nejvyšším `(last1 - first1) - (last2 - first2) - 1` porovnáním.

[Třída list](../standard-library/list-class.md) poskytuje členskou funkci Merge pro sloučení prvků dvou seznamů.

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
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1;

    // Constructing vector v1a and v1b with default less than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3a( v1a ), v3b( v1b ) , v3( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To merge inplace in ascending order with default binary
    // predicate less<int>( )
    merge ( v1a.begin( ), v1a.end( ), v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Merged inplace with default order,\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To merge inplace in descending order, specify binary
    // predicate greater<int>( )
    merge ( v2a.begin( ), v2a.end( ), v2b.begin( ), v2b.end( ),
        v2.begin( ), greater<int>( ) );
    cout << "Merged inplace with binary predicate greater specified,\n "
            << "vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // Applying A user-defined (UD) binary predicate mod_lesser
    merge ( v3a.begin( ), v3a.end( ), v3b.begin( ), v3b.end( ),
        v3.begin( ), mod_lesser );
    cout << "Merged inplace with binary predicate mod_lesser specified,\n "
            << "vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="min"></a>dlouhé

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
    BinaryPredicate pred);

template<class Type>
constexpr Type min(
    initializer_list<Type> ilist);

template<class Type, class Pr>
constexpr Type min(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*zbývá*\
První ze dvou porovnávaných objektů.

*Kliknutím*\
Druhý ze dvou porovnávaných objektů.

*čekání*\
Binární predikát, který slouží k porovnání dvou objektů.

*podklauzule*\
Obsahující `initializer_list` členy, které mají být porovnány.

### <a name="return-value"></a>Návratová hodnota

Menší z těchto dvou objektů, pokud ani není menší; v takovém případě vrátí první z těchto dvou objektů. V případě `initializer_list`, vrátí nejméně objekty v seznamu.

### <a name="remarks"></a>Poznámky

Algoritmus `min` je neobvyklý v případě, že objekty předány jako parametry. Většina C++ standardních algoritmů knihovny funguje na rozsahu prvků, jejichž pozice je určena iterátory předanými jako parametry. Pokud potřebujete funkci, která používá rozsah prvků, použijte [Min_element](../standard-library/algorithm-functions.md#min_element). u`initializer_list` přetížení v aplikaci Visual Studio 2017 byl povolen [Modifikátor constexpr](../cpp/constexpr-cpp.md) .

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
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

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

## <a name="min_element"></a>min_element

Vyhledá první výskyt nejmenšího prvku v zadaném rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který má být prohledán pro nejmenší prvek.

*posledního*\
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu, který se má vyhledat u nejmenšího prvku.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Relační predikát přijímá dva argumenty a by měl vracet **hodnotu true** , pokud je první prvek menší než druhý prvek, a jinak **false** .

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje umístění prvního výskytu nejmenšího prvku v prohledávané oblasti.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; u všech ukazatelů musí být možné provést zpětnou odkazování, protože poslední pozice je dosažitelná od první po zvýšení.

Složitost je lineární: `(last - first) - 1` pro neprázdný rozsah jsou vyžadovány porovnání.

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
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

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

## <a name="minmax_element"></a>minmax_element

Provede práci prováděnou `min_element` a `max_element` v jednom volání.

```cpp
template<class ForwardIterator>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který označuje začátek rozsahu.

*posledního*\
Dopředný iterátor, který označuje konec rozsahu.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Relační predikát přijímá dva argumenty a by měl vracet **hodnotu true** , pokud je první menší než druhý, a jinak **false** .

### <a name="return-value"></a>Návratová hodnota

Vrací

`pair<ForwardIterator, ForwardIterator>( min_element(first, last), max_element(first, last))`.

### <a name="remarks"></a>Poznámky

První funkce šablony vrátí

`pair<ForwardIterator,ForwardIterator>(min_element(first,last), max_element(first,last))`.

Druhá funkce šablony se chová stejně, s tím rozdílem, že `operator<(X, Y)` nahrazuje `pred(X, Y)`.

Pokud sekvence není prázdná, funkce provádí nejvíce `3 * (last - first - 1) / 2` porovnávání.

## <a name="minmax"></a>minmax

Porovná dva vstupní parametry a vrátí je jako dvojici v pořadí od menšího po větší.

```cpp
template<class Type>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right);

template<class Type, class BinaryPredicate>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);

template<class Type>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist);

template<class Type, class BinaryPredicate>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*zbývá*\
První ze dvou porovnávaných objektů.

*Kliknutím*\
Druhý ze dvou porovnávaných objektů.

*čekání*\
Binární predikát, který slouží k porovnání dvou objektů.

*podklauzule*\
Obsahující `initializer_list` členy, které mají být porovnány.

### <a name="remarks"></a>Poznámky

První funkce šablony vrátí `pair<const Type&, const Type&>( right, left )` , pokud je *právo* menší než *levé*. V opačném případě `pair<const Type&, const Type&>( left, right )`vrátí.

Druhá členská funkce vrátí dvojici, kde je první prvek menší a druhá je větší, pokud je porovnána s predikátem *před*.

Zbývající funkce šablony se chovají stejně, s tím rozdílem, že nahrazují *levé* a *pravé* parametry pomocí *INLIST*.

Funkce provádí přesně jedno porovnání.

## <a name="mismatch"></a>shod

Porovná dva rozsahy element podle prvku a vyhledá první pozici, kde dojde k rozdílu.

Používejte přetížení dvojího rozsahu v kódu C++ 14, protože přetížení, která přijímají pouze jeden iterátor pro druhý rozsah, nebudou detekovat rozdíly, pokud je druhý rozsah delší než první rozsah a výsledkem bude nedefinované chování, pokud je druhý rozsah kratší. než první rozsah.

```cpp
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred );

//C++14
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

//C++17
template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Vstupní iterátor adresující pozici prvního prvku v prvním rozsahu, který má být testován.

*last1*\
Vstupní iterátor adresující pozici jednu za poslední prvek v prvním rozsahu, který má být testován.

*first2*\
Vstupní iterátor adresující pozici prvního prvku v druhém rozsahu, který má být testován.

*last2*\
Vstupní iterátor adresující pozici jednoho za poslední prvek v druhém rozsahu, který má být testován.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který porovnává aktuální prvky v jednotlivých rozsahech a určuje, zda jsou ekvivalentní. Vrátí **hodnotu true** , pokud je splněná, a **hodnotu false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

Pár iterátorů, které řeší pozice neshody ve dvou rozsahech, první komponenta iterátoru pozice v prvním rozsahu a druhá iterátora komponenty na pozici v druhém rozsahu. Pokud není rozdíl mezi prvky v porovnáních rozsahů nebo v případě, že binární predikát v druhé verzi je splněn všemi páry prvků ze dvou rozsahů, pak první iterátor komponenty ukazuje na pozici jednu za posledním prvkem v prvním Rozsah a druhý iterátor součásti, které mají být umístěny do posledního testovaného prvku v druhém rozsahu.

### <a name="remarks"></a>Poznámky

První funkce šablony předpokládá, že existuje tolik prvků v rozsahu, který začíná na First2, protože jsou v rozsahu určeném [first1, last1). Pokud ve druhém rozsahu existuje víc, ignorují se. v případě, že je k dispozici méně, bude výsledkem nedefinované chování.

Rozsah, který má být prohledán, musí být platný. všechny iterátory musí být možné odkázat a poslední pozice je dosažitelná z první pomocí přírůstku.

Doba složitosti algoritmu je lineární v počtu elementů obsažených v kratším rozsahu.

Uživatelsky definovaný predikát není vyžadován k zavedení vztahu rovnosti, který je symetrický, reflexivní a tranzitivní mezi jeho operandy.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat neshodu. Přetížení jazyka C++ 03 je zobrazeno pouze za účelem předvedení toho, jak může způsobit neočekávaný výsledek.

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
```

```Output
C++03: vec_1 and vec_2 are a mismatch: false
C++14: vec_1 and vec_2: mismatch. Left iterator at end right iterator at 30
C++14 vec_1 v. vec_2 modified: mismatch. Left iterator at 15 right iterator at 42
C++14 vec_3 v. vec_4 with pred: match.
C++14 vec_3 v. modified vec_4 with pred: mismatch. Left iterator at 60 right iterator at 31
C++14: vec_1 and list_1 are a mismatch: false
Press a key
```

## <a name="alg_move"></a>&lt;ALGpřesunout&gt;

Přesune prvky přidružené k určenému rozsahu.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator move(
    InputIterator first,
    InputIterator last,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 move(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor, který označuje, kde začít rozsah prvků, které mají být přesunuty.

*posledního*\
Vstupní iterátor, který označuje konec rozsahu prvků, které mají být přesunuty.

*propojovací*\
Výstupní iterátor, který má obsahovat přesunuté elementy.

### <a name="remarks"></a>Poznámky

Funkce šablony je `*(dest + N) = move(*(first + N))` vyhodnocena jednou `N` v rozsahu `[0, last - first)`, pro striktní zvýšení hodnot `N` od nejnižší hodnoty. Pak se vrátí `dest + N`. Pokud `dest` a *nejdříve* určíte oblasti úložiště, *cíl* nesmí být v rozsahu `[first, last)`.

## <a name="move_backward"></a>move_backward

Přesune prvky jednoho iterátoru do druhého. Pohyb začíná posledním prvkem v daném rozsahu a končí prvním prvkem v daném rozsahu.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 move_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>Parametry

*první*\
Iterátor, který označuje začátek rozsahu, z něhož se mají přesunout prvky.

*posledního*\
Iterátor, který označuje konec rozsahu, z něhož se mají přesunout prvky. Tento prvek není přesunut.

*destEnd*\
Obousměrný iterátor, který adresuje umístění jedno místo za posledním prvkem v cílové oblasti.

### <a name="remarks"></a>Poznámky

Funkce šablony je `*(destEnd - N - 1) = move(*(last - N - 1))` vyhodnocena jednou `N` v rozsahu `[0, last - first)`, pro striktní zvýšení hodnot `N` od nejnižší hodnoty. Pak se vrátí `destEnd - (last - first)`. Pokud *destEnd* a *First* určí oblasti úložiště, *destEnd* nesmí být v rozsahu `[first, last)`.

`move`a `move_backward` jsou funkčně ekvivalentní s použitím `copy` a `copy_backward` s iterátorem přesunutí.

## <a name="next_permutation"></a>next_permutation

Znovu uspořádá prvky v rozsahu tak, aby původní pořadí bylo nahrazeno lexikograficky následující větší permutací, pokud existuje, kde význam následujícího může být určen binárním predikátem.

```cpp
template<class BidirectionalIterator>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*první*\
Obousměrný iterátor ukazující na pozici prvního prvku v rozsahu, který má být permuted.

*posledního*\
Obousměrný iterátor ukazující na pozici jeden za posledním prvkem v rozsahu, který má být permuted.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání, které se má splnit po sobě jdoucích prvků v řazení. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud lexikograficky další permutace existuje a nahradilo původní řazení rozsahu; v opačném případě **false**, v takovém případě je řazení transformované na lexikograficky nejmenší permutaci.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Výchozí binární predikát je menší než a elementy v rozsahu musí být menší než srovnatelné, aby bylo zajištěno, že je následující permutace správně definovaná.

Složitost je lineární s největší `(last - first) / 2` swapy.

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
    CInt( int n = 0 ) : m_nVal( n ) {}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ) {}
    CInt& operator=( const CInt& rhs ) {m_nVal =
        rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        { return ( m_nVal < rhs.m_nVal ); }
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
    vector<int> v1;
    vector<int>::iterator Iter1;

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
            cout << *Iter1 << " ";
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

## <a name="nth_element"></a>nth_element

Rozdělí rozsah prvků na oddíly a správně vyhledá *n*-tý prvek sekvence v rozsahu tak, aby všechny prvky před ním byly menší nebo rovny hodnotě a všechny prvky, které následují v sekvenci, jsou větší než nebo rovny.

```cpp
template<class RandomAccessIterator>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v rozsahu, který se má rozdělit na oddíly.

*člen*\
Iterátor náhodného přístupu, který adresuje pozici prvku pro správné objednání na hranici oddílu.

*posledního*\
Iterátor náhodného přístupu, který adresuje umístění jedno za posledním prvkem v rozsahu, který se má rozdělit na oddíly.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání, které se má splnit po sobě jdoucích prvků v řazení. Relační predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Algoritmus nezaručuje, že prvky v dílčích rozsahech v rámci n elementu jsou seřazeny.  `nth_element` Proto má méně záruky než `partial_sort`, které řadí prvky v rozsahu pod nějaký vybraný prvek a lze jej použít jako rychlejší `partial_sort` alternativu, pokud není vyžadováno řazení dolního rozsahu.

Prvky jsou ekvivalentní, ale nejsou nutně stejné, pokud není ani méně než druhá.

Průměr složitosti řazení je lineární vzhledem k *Last-First*.

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
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="none_of"></a>none_of

Vrátí **hodnotu pravda** , pokud není podmínka nikdy obsažena v rámci prvků v daném rozsahu.

```cpp
template<class InputIterator, class UnaryPredicate>
bool none_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool none_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor, který označuje, kde začít kontrolovat rozsah prvků pro podmínku.

*posledního*\
Vstupní iterátor, který označuje konec rozsahu prvků.

*čekání*\
Podmínka, která se má testovat. Toto je poskytováno uživatelem definovaný objekt funkce predikátu, který definuje podmínku. Unární predikát přijímá jeden argument a vrátí **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu true** , pokud podmínka není v zadaném rozsahu zjištěna alespoň jednou, a **hodnota false** , pokud je zjištěna podmínka.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí **hodnotu true** pouze v případě, že `N` pro některé v `[0, last - first)`rozsahu je predikát `pred(*(first + N))` vždy **false**.

## <a name="partial_sort"></a>partial_sort

Uspořádá zadaný počet menších prvků v rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.

```cpp
template<class RandomAccessIterator>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v rozsahu, který má být seřazen.

*sortEnd*\
Iterátor náhodného přístupu, který adresuje umístění jedno místo za posledním prvkem v podrozsahu, který má být seřazen.

*posledního*\
Iterátor náhodného přístupu, který adresuje pozici jednu za posledním prvkem v rozsahu, který má být částečně seřazen.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání, které se má splnit po sobě jdoucích prvků v řazení. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Prvky jsou ekvivalentní, ale nejsou nutně stejné, pokud není ani méně než druhá. `sort` Algoritmus není stabilní a nezaručuje, že se zachová relativní pořadí ekvivalentních prvků. Algoritmus `stable_sort` zachovává toto původní řazení.

Průměrná složitost částečného řazení je *O*((`last`) protokolu (`sortEnd`- - `first`(`first`)).

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
    vector<int> v1;
    vector<int>::iterator Iter1;

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
    partial_sort(v1.begin( ), v1.begin( ) + 8, v1.end( ), UDgreater );
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

## <a name="partial_sort_copy"></a>partial_sort_copy

Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu, kde zdrojové prvky jsou seřazeny buď podle binárního predikátu „menší než“ nebo jiného určeného binárního predikátu.

```cpp
template<class InputIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2 );

template<class InputIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Vstupní iterátor adresující pozici prvního prvku ve zdrojovém rozsahu.

*last1*\
Vstupní iterátor adresující pozici jednu za poslední prvek ve zdrojovém rozsahu.

*first2*\
Iterátor náhodného přístupu, který řeší umístění prvního prvku v seřazeném cílovém rozsahu.

*last2*\
Iterátor náhodného přístupu, který adresuje pozici jednu za posledním prvkem v seřazeném rozsahu cíle.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání, které se má splnit po sobě jdoucích prvků v řazení. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

Iterátor náhodného přístupu, který adresuje prvek v cílovém rozsahu, který má jednu pozici nad rámec posledního elementu vloženého ze zdrojového rozsahu.

### <a name="remarks"></a>Poznámky

Zdrojové a cílové rozsahy se nesmí překrývat a musí být platné. u všech ukazatelů musí být možné provést zpětnou odkazování a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Binární predikát musí poskytovat přísné slabé řazení, aby prvky, které nejsou ekvivalentní, byly seřazeny, ale prvky, které jsou ekvivalentní, nejsou. Dva prvky jsou ekvivalentní menší než, ale nemusí být nutně stejné, pokud není ani méně než druhá.

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

## <a name="partition"></a>rozdělován

Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují.

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator partition(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Obousměrný iterátor, který adresuje umístění prvního prvku v rozsahu, který se má rozdělit na oddíly.

*posledního*\
Obousměrný iterátor, který adresuje pozici jednu za posledním prvkem v rozsahu, který se má rozdělit na oddíly.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněna, je-li prvek klasifikován. Unární predikát přijímá jeden argument a vrátí **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který adresuje umístění prvního prvku v rozsahu, který nesplňuje podmínky predikátu.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Prvky *a* a *b* jsou ekvivalentní, ale nemusí být nutně stejné, pokud `pred( a, b )` jsou obě hodnoty `pred( b, a )` false a má hodnotu false, kde *před* je predikát určený parametrem. `partition` Algoritmus není stabilní a nezaručuje, že se zachová relativní pořadí ekvivalentních prvků. Algoritmus `stable_partition` zachovává toto původní řazení.

Složitost je lineární: existují `(last - first)` *aplikace s* nejvyšším `(last - first)/2` a maximálně zahozením.

### <a name="example"></a>Příklad

```cpp
// alg_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="partition_copy"></a>partition_copy

Zkopíruje prvky, pro které je podmínka **pravdivá** , do jednoho cíle a pro který je podmínka **NEPRAVDA** , na druhou. Prvky musí pocházet ze zadaného rozsahu.

```cpp
template<class InputIterator, class OutputIterator1, class OutputIterator2, class UnaryPredicate>
pair<OutputIterator1, OutputIterator2> partition_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator1 dest1,
    OutputIterator2 dest2,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
pair<ForwardIterator1, ForwardIterator2> partition_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    ForwardIterator1 out_true,
    ForwardIterator2 out_false,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor, který označuje začátek rozsahu pro kontrolu podmínky.

*posledního*\
Vstupní iterátor, který označuje konec rozsahu.

*dest1*\
Výstupní iterátor, který slouží ke kopírování prvků, které vracejí hodnotu true pro podmínku testovaný pomocí *před*.

*dest2*\
Výstupní iterátor, který se používá ke kopírování prvků, které vrací hodnotu false pro podmínku testovaný pomocí *před*.

*čekání*\
Podmínka, která se má testovat. Toto je poskytováno uživatelem definovaný objekt funkce predikátu, který definuje podmínku, která má být testována. Unární predikát přijímá jeden argument a vrátí **hodnotu true** nebo **false**.

### <a name="remarks"></a>Poznámky

Funkce šablony kopíruje každý prvek `X` v `[first,last)` , `*dest1++` Pokud `pred(X)` má hodnotu true, nebo `*dest2++` na ne. Vrátí `pair<OutputIterator1, OutputIterator2>(dest1, dest2)`.

## <a name="partition_point"></a>partition_point

Vrátí první prvek v zadaném rozsahu, který nesplňuje podmínku. Prvky jsou seřazeny tak, aby ty, které splňují podmínku, předcházely těm, které ji nesplňují.

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator partition_point(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*první*\
`ForwardIterator` , Který označuje začátek rozsahu pro kontrolu podmínky.

*posledního*\
`ForwardIterator` , Který označuje konec rozsahu.

*čekání*\
Podmínka, která se má testovat. Toto je poskytováno uživatelem definovaný objekt funkce predikátu, který definuje podmínku, která má být splněna prvkem, který je prohledáván. Unární predikát přijímá jeden argument a vrátí **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Vrátí, který odkazuje na první prvek, který nesplňuje podmínku testovaný před, nebo vrátí *Poslední* , pokud nebyl nalezen.  `ForwardIterator`

### <a name="remarks"></a>Poznámky

Funkce šablony `it` vyhledá první iterátor v `[first, last)` pro, který `pred(*it)` je **nepravdivý**. Sekvence musí být seřazena *před*.

## <a name="pop_heap"></a>pop_heap

Odstraní největší prvek z přední části haldy až do předposlední pozice v rozsahu a ze zbývajících prvků vytvoří novou haldu.

```cpp
template<class RandomAccessIterator>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*první*\
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v haldě.

*posledního*\
Iterátor náhodného přístupu, který adresuje umístění jedno za poslední prvek v haldě.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="remarks"></a>Poznámky

`pop_heap` Algoritmus je inverzní k operaci prováděné algoritmem push_heap, ve které se element na konci rozsahu přidá do haldy, která se skládá z předchozích prvků v rozsahu, v případě, že je prvek přidaný do halda je větší než všechny prvky, které jsou již v haldě.

Haldy mají dvě vlastnosti:

- První prvek je vždy největší.

- Prvky lze přidat nebo odebrat ve logaritmických čase.

Haldy představují ideální způsob implementace front priorit a používají se v implementaci C++ [třídy priority_queue](../standard-library/priority-queue-class.md)kontejnerů standardní knihovny.

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Rozsah kromě nově přidaného prvku na konci musí být halda.

Složitost je logaritmická, což vyžaduje nejvíce `log (last - first)` porovnání.

### <a name="example"></a>Příklad

```cpp
// alg_pop_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="prev_permutation"></a>prev_permutation

Změní pořadí prvků v rozsahu tak, aby původní řazení bylo nahrazeno lexikograficky předchozí větší permutací, pokud existuje, kde je možné zadat smysl předchozí s binárním predikátem.

```cpp
template<class BidirectionalIterator>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*první*\
Obousměrný iterátor ukazující na pozici prvního prvku v rozsahu, který má být permuted.

*posledního*\
Obousměrný iterátor ukazující na pozici jeden za posledním prvkem v rozsahu, který má být permuted.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání, které se má splnit po sobě jdoucích prvků v řazení. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud lexikograficky předchozí permutace existuje a nahradilo původní řazení rozsahu; v opačném případě **false**, v takovém případě je řazení transformované na lexikograficky největší permutaci.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Výchozí binární predikát je menší než a elementy v rozsahu musí být menší než srovnatelné, aby bylo zajištěno, že předchozí permutace je správně definována.

Složitost je lineární, s největší (`last` - `first`)/2 swapy.

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

int main()
{
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
    vector<int> v1;
    vector<int>::iterator Iter1;

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
            cout << *Iter1 << " ";
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

## <a name="push_heap"></a>push_heap

Přidá prvek, který je na konci rozsahu, do stávající haldy, která zahrnuje předchozí prvky daného rozsahu.

```cpp
template<class RandomAccessIterator>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*první*\
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v haldě.

*posledního*\
Iterátor náhodného přístupu, který adresuje pozici jednu za posledním prvkem v rozsahu, který se má převést na haldu.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="remarks"></a>Poznámky

Element musí být nejprve vrácen na konec existující haldy a poté algoritmus použit k přidání tohoto elementu do existující haldy.

Haldy mají dvě vlastnosti:

- První prvek je vždy největší.

- Prvky lze přidat nebo odebrat ve logaritmických čase.

Haldy představují ideální způsob implementace front priorit a používají se v implementaci C++ [třídy priority_queue](../standard-library/priority-queue-class.md)kontejnerů standardní knihovny.

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Rozsah kromě nově přidaného prvku na konci musí být halda.

Složitost je logaritmická, což vyžaduje nejvíce `log(last - first)` porovnání.

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
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="random_shuffle"></a>random_shuffle

Funkce std:: random_shuffle () je zastaralá, Nahrazená [std:: náhodně](../standard-library/algorithm-functions.md#shuffle). Příklad kódu a další informace naleznete v tématu [ \<náhodné >](../standard-library/random.md) a Stack Overflow post, [Proč jsou metody std:: random_shuffle zastaralé v c++ 14?](https://go.microsoft.com/fwlink/p/?linkid=397954).

## <a name="remove"></a>odebrány

Odstraní zadanou hodnotu z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator remove(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator remove(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, ze kterého se odstraňují prvky.

*posledního*\
Dopředný iterátor, který adresuje umístění jeden za posledním prvkem v rozsahu, ze kterého se odstraňují prvky.

*osa*\
Hodnota, která má být odebrána z rozsahu.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje novou koncovou pozici upravovaného rozsahu, jeden za posledním prvkem zbývající sekvence bez zadané hodnoty.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Pořadí prvků, které se neodebraly, zůstává stabilní.

`operator==` Pro určení rovnosti mezi prvky musí být vztah mezi jeho operandy.

Složitost je lineární; Existují porovnání (`last` - )prorovnost`first`.

[Třída list](../standard-library/list-class.md) má efektivnější verzi `remove`členské funkce, která také přepojí ukazatele.

### <a name="example"></a>Příklad

```cpp
// alg_remove.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, new_end;

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

## <a name="remove_copy"></a>remove_copy

Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu. Prvky zadané hodnoty zkopírovány nejsou. Nenaruší pořadí zbývajících prvků a nevrátí konec nového cílového rozsahu.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator remove_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 remove_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& value);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor adresující pozici prvního prvku v rozsahu, ze kterého se odstraňují prvky.

*posledního*\
Vstupní iterátor adresující pozici jednu za poslední prvek v rozsahu, ze kterého se odstraňují prvky.

*vyústit*\
Výstupní iterátor adresující pozici prvního prvku v cílovém rozsahu, do kterého se prvky odstraňují.

*osa*\
Hodnota, která má být odebrána z rozsahu.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje novou koncovou pozici cílového rozsahu, jeden za poslední prvek kopie zbytkové sekvence bez zadané hodnoty.

### <a name="remarks"></a>Poznámky

Odkazované zdrojové a cílové rozsahy musí být platné. všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

V cílovém rozsahu musí být dostatek místa, aby obsahovalo zbytkové prvky, které budou zkopírovány po odebrání prvků zadané hodnoty.

Pořadí prvků, které se neodebraly, zůstává stabilní.

`operator==` Pro určení rovnosti mezi prvky musí být vztah mezi jeho operandy.

Složitost je lineární; Existují porovnání (`last` - `last` - ) pro přiřazení rovnosti a nanejvýš (`first`).`first`

### <a name="example"></a>Příklad

```cpp
// alg_remove_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

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

## <a name="remove_copy_if"></a>remove_copy_if

Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu s výjimkou prvků, které odpovídají predikátu. Prvky jsou zkopírovány bez narušení pořadí zbývajících prvků. Vrátí konec nového cílového rozsahu.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator remove_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 remove_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor adresující pozici prvního prvku v rozsahu, ze kterého se odstraňují prvky.

*posledního*\
Vstupní iterátor adresující pozici jednu za poslední prvek v rozsahu, ze kterého se odstraňují prvky.

*vyústit*\
Výstupní iterátor adresující pozici prvního prvku v cílovém rozsahu, do kterého se prvky odstraňují.

*čekání*\
Unární predikát, který musí být splněn, je hodnota elementu, která má být nahrazena.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje novou koncovou pozici cílového rozsahu, jeden za posledním prvkem zbývající sekvence bez prvků, které odpovídají predikátu.

### <a name="remarks"></a>Poznámky

Odkazovaný zdrojový rozsah musí být platný. všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

V cílovém rozsahu musí být dostatek místa, aby obsahovalo zbytkové prvky, které budou zkopírovány po odebrání prvků zadané hodnoty.

Pořadí prvků, které se neodebraly, zůstává stabilní.

`operator==` Pro určení rovnosti mezi prvky musí být vztah mezi jeho operandy.

Složitost je lineární: existují porovnávací (`last` - `last` - `first`) pro přiřazení rovnosti a maximálně (`first`).

Informace o tom, jak se tyto funkce chovají, najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

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

## <a name="remove_if"></a>remove_if

Odstraní prvky, které splňují predikát, z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor ukazující na pozici prvního prvku v rozsahu, ze kterého se odebírají prvky.

*posledního*\
Dopředný iterátor ukazující na pozici jeden za posledním prvkem v rozsahu, ze kterého se odstraňují prvky.

*čekání*\
Unární predikát, který musí být splněn, je hodnota elementu, která má být nahrazena.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje novou koncovou pozici upravovaného rozsahu, jeden za posledním prvkem zbývající sekvence bez zadané hodnoty.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Pořadí prvků, které se neodebraly, zůstává stabilní.

`operator==` Pro určení rovnosti mezi prvky musí být vztah mezi jeho operandy.

Složitost je lineární: existují (`last` - `first`) porovnání pro rovnost.

Seznam má efektivnější verzi členské funkce, která odpojí ukazatele.

### <a name="example"></a>Příklad

```cpp
// alg_remove_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, new_end;

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

## <a name="replace"></a>náhrady

Zkontroluje každý prvek v rozsahu a nahradí jej, pokud odpovídá zadané hodnotě.

```cpp
template<class ForwardIterator, class Type>
void replace(
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void replace(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor ukazující na pozici prvního prvku v rozsahu, ze kterého se nahrazují prvky.

*posledního*\
Dopředný iterátor ukazující na pozici jeden za posledním prvkem v rozsahu, ze kterého se nahrazují prvky.

*oldVal*\
Stará hodnota prvků, které mají být nahrazeny.

*newVal*\
Nová hodnota, která je přiřazena k prvkům se starou hodnotou.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Pořadí prvků, které nejsou nahrazené, zůstává stabilní.

`operator==` Pro určení rovnosti mezi prvky musí být vztah mezi jeho operandy.

Složitost je lineární; k dispozici`last`jsou ( - `first`) porovnání pro rovnost a maximálně`last`( - `first`) přiřazení nových hodnot.

### <a name="example"></a>Příklad

```cpp
// alg_replace.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="replace_copy"></a>replace_copy

Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu odpovídá zadané hodnotě.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator replace_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 replace_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor ukazující na pozici prvního prvku v rozsahu, ze kterého se nahrazují prvky.

*posledního*\
Vstupní iterátor ukazující na pozici jeden za posledním prvkem v rozsahu, ze kterého se nahrazují prvky.

*vyústit*\
Výstupní iterátor ukazující na první prvek v cílovém rozsahu, do kterého se kopíruje upravená sekvence elementů.

*oldVal*\
Stará hodnota prvků, které mají být nahrazeny.

*newVal*\
Nová hodnota, která je přiřazena k prvkům se starou hodnotou.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor ukazující na pozici jednu za posledním prvkem v cílovém rozsahu, do kterého se kopíruje změněné pořadí elementů.

### <a name="remarks"></a>Poznámky

Odkazované zdrojové a cílové rozsahy se nesmí překrývat a musí být oba platné: všechny ukazatele musí být zpětně zaměřené a v rámci sekvencí je poslední pozice dosažitelná od prvního po zvýšení.

Pořadí prvků, které nejsou nahrazené, zůstává stabilní.

`operator==` Pro určení rovnosti mezi prvky musí být vztah mezi jeho operandy.

Složitost je lineární:`last`existují ( - `first`) porovnání pro rovnost a maximálně (`last` - `first`) přiřazení nových hodnot.

### <a name="example"></a>Příklad

```cpp
// alg_replace_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (15);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

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

## <a name="replace_copy_if"></a>replace_copy_if

Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu splňuje zadaný predikát.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate, class Type>
OutputIterator replace_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate, class Type>
ForwardIterator2 replace_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor ukazující na pozici prvního prvku v rozsahu, ze kterého se nahrazují prvky.

*posledního*\
Vstupní iterátor ukazující na pozici jeden za posledním prvkem v rozsahu, ze kterého se nahrazují prvky.

*vyústit*\
Výstupní iterátor ukazující na pozici prvního prvku v cílovém rozsahu, do kterého se prvky kopírují.

*čekání*\
Unární predikát, který musí být splněn, je hodnota elementu, která má být nahrazena.

*osa*\
Nová hodnota, která je přiřazena k prvkům, jejichž stará hodnota splňuje predikát.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor ukazující na pozici jednu za posledním prvkem v cílovém rozsahu, do kterého se kopíruje změněné pořadí elementů.

### <a name="remarks"></a>Poznámky

Odkazované zdrojové a cílové rozsahy se nesmí překrývat a musí být oba platné: všechny ukazatele musí být zpětně zaměřené a v rámci sekvencí je poslední pozice dosažitelná od prvního po zvýšení.

Pořadí prvků, které nejsou nahrazené, zůstává stabilní.

`operator==` Pro určení rovnosti mezi prvky musí být vztah mezi jeho operandy.

Složitost je lineární; k dispozici`last`jsou ( - `first`) porovnání pro rovnost a maximálně`last`( - `first`) přiřazení nových hodnot.

### <a name="example"></a>Příklad

```cpp
// alg_replace_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (13);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

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

## <a name="replace_if"></a>replace_if

Zkontroluje každý prvek v rozsahu a nahradí jej, pokud splňuje zadaný predikát.

```cpp
template<class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor ukazující na pozici prvního prvku v rozsahu, ze kterého se nahrazují prvky.

*posledního*\
Iterátor ukazující na pozici jeden za posledním prvkem v rozsahu, ze kterého se nahrazují prvky.

*čekání*\
Unární predikát, který musí být splněn, je hodnota elementu, která má být nahrazena.

*osa*\
Nová hodnota, která je přiřazena k prvkům, jejichž stará hodnota splňuje predikát.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Pořadí prvků, které nejsou nahrazené, zůstává stabilní.

Algoritmus `replace_if` je generalizace algoritmu `replace`, která umožňuje zadat libovolný predikát namísto rovnosti na zadanou konstantní hodnotu.

`operator==` Pro určení rovnosti mezi prvky musí být vztah mezi jeho operandy.

Složitost je lineární:`last`existují ( - `first`) porovnání pro rovnost a maximálně (`last` - `first`) přiřazení nových hodnot.

### <a name="example"></a>Příklad

```cpp
// alg_replace_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="reverse"></a>zpět

Obrátí pořadí prvků v rozsahu.

```cpp
template<class BidirectionalIterator>
void reverse(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator>
void reverse(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Obousměrný iterátor ukazující na pozici prvního prvku v rozsahu, ve kterém jsou elementy permuted.

*posledního*\
Obousměrný iterátor ukazující na pozici jeden za posledním prvkem v rozsahu, ve kterém jsou elementy permuted.

### <a name="remarks"></a>Poznámky

Odkazovaný zdrojový rozsah musí být platný. všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

### <a name="example"></a>Příklad

```cpp
// alg_reverse.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="reverse_copy"></a>reverse_copy

Obrátí pořadí prvků ve zdrojovém rozsahu při kopírování do cílového rozsahu.

```cpp
template<class BidirectionalIterator, class OutputIterator>
OutputIterator reverse_copy(
    BidirectionalIterator first,
    BidirectionalIterator last,
    OutputIterator result);

template<class ExecutionPolicy, class BidirectionalIterator, class ForwardIterator>
ForwardIterator reverse_copy(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    ForwardIterator result);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Obousměrný iterátor ukazující na pozici prvního prvku ve zdrojové oblasti, ve kterém jsou elementy permuted.

*posledního*\
Obousměrný iterátor ukazující na pozici jeden za posledním prvkem ve zdrojové oblasti, ve kterém se prvky permuted.

*vyústit*\
Výstupní iterátor ukazující na pozici prvního prvku v cílovém rozsahu, do kterého se prvky kopírují.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor ukazující na pozici jednu za posledním prvkem v cílovém rozsahu, do kterého se kopíruje změněné pořadí elementů.

### <a name="remarks"></a>Poznámky

Odkazované zdrojové a cílové rozsahy musí být platné. všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

### <a name="example"></a>Příklad

```cpp
// alg_reverse_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2( 10 );
    vector<int>::iterator Iter1, Iter2;

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

## <a name="rotate"></a>před

Vymění prvky ve dvou sousedních rozsazích.

```cpp
template<class ForwardIterator>
void rotate(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator rotate(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který se má otočit.

*Blízký*\
Dopředný iterátor definující hranici v rozsahu, který řeší pozici prvního prvku v druhé části rozsahu, jehož prvky mají být vyměňovány pomocí těch v první části rozsahu.

*posledního*\
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu, který se má otočit.

### <a name="remarks"></a>Poznámky

Odkazované rozsahy musí být platné. všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Složitost je lineární s nanejvýš (`last` - `first`) swapy.

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
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
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
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    rotate ( v1.begin( ), v1.begin( ) + 3 , v1.end( ) );
    cout << "After rotating, vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) ) {
        rotate ( d1.begin( ), d1.begin( ) + 1 , d1.end( ) );
        cout << "After the rotation of a single deque element to the back,\n d1 is   ( " ;
        for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
            cout << *d1Iter1 << " ";
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

## <a name="rotate_copy"></a>rotate_copy

Vymění prvky ve dvou sousedních rozsazích v rámci zdrojového rozsahu a zkopíruje výsledek do cílového rozsahu.

```cpp
template<class ForwardIterator, class OutputIterator>
OutputIterator rotate_copy(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last,
    OutputIterator result );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 rotate_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 middle,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který se má otočit.

*Blízký*\
Dopředný iterátor definující hranici v rozsahu, který řeší pozici prvního prvku v druhé části rozsahu, jehož prvky mají být vyměňovány pomocí těch v první části rozsahu.

*posledního*\
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu, který se má otočit.

*vyústit*\
Výstupní iterátor adresující pozici prvního prvku v cílovém rozsahu.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující pozici jednu za poslední prvek v cílovém rozsahu.

### <a name="remarks"></a>Poznámky

Odkazované rozsahy musí být platné. všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Složitost je lineární s nanejvýš (`last` - `first`) swapy.

### <a name="example"></a>Příklad

```cpp
// alg_rotate_copy.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1 , v2 ( 9 );
    deque<int> d1 , d2 ( 6 );
    vector<int>::iterator v1Iter , v2Iter;
    deque<int>::iterator d1Iter , d2Iter;

    int i;
    for ( i = -3 ; i <= 5 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii =0 ; ii <= 5 ; ii++ )
        d1.push_back( ii );

    cout << "Vector v1 is ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    rotate_copy ( v1.begin( ), v1.begin( ) + 3 , v1.end( ), v2.begin( ) );
    cout << "After rotating, the vector v1 remains unchanged as:\n v1 = ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    cout << "After rotating, the copy of vector v1 in v2 is:\n v2 = ( " ;
    for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ;v2Iter ++ )
        cout << *v2Iter << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter = d1.begin( ) ; d1Iter != d1.end( ) ;d1Iter ++ )
        cout << *d1Iter << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) )
    {
        rotate_copy ( d1.begin( ), d1.begin( ) + iii , d1.end( ), d2.begin( ) );
        cout << "After the rotation of a single deque element to the back,\n d2 is   ( " ;
        for ( d2Iter = d2.begin( ) ; d2Iter != d2.end( ) ;d2Iter ++ )
            cout << *d2Iter << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

## <a name="sample"></a>vzorku

```cpp
template<class PopulationIterator, class SampleIterator, class Distance, class UniformRandomBitGenerator>
SampleIterator sample(
    PopulationIterator first,
    PopulationIterator last,
    SampleIterator out,
    Distance n,
    UniformRandomBitGenerator&& g);
```

## <a name="search"></a>nápovědě

Vyhledá první výskyt sekvence v cílovém rozsahu, jejíž prvky jsou rovné prvkům v dané sekvenci prvků nebo jejíž prvky jsou ekvivalentní ve smyslu určeném binárním predikátem prvkům v dané sekvenci.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template <class ForwardIterator, class Searcher>
ForwardIterator search(
    ForwardIterator first,
    ForwardIterator last,
    const Searcher& searcher);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který chcete prohledat.

*last1*\
Dopředný iterátor, který adresuje pozici jednu za posledním prvkem v rozsahu, který chcete prohledat.

*first2*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který má být porovnán.

*last2*\
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu, který má být porovnán.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněna, pokud mají být provedeny dva prvky jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

*vyhledávač*\
Vyhledávací modul, který zapouzdřuje vzor, který se má hledat, a vyhledávací algoritmus, který se má použít.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje umístění prvního prvku první dílčí sekvence, který odpovídá zadané sekvenci nebo který je ekvivalentní ve smyslu určeném binárním predikátem.

### <a name="remarks"></a>Poznámky

`operator==` Pro určení shody mezi elementem a zadanou hodnotou musí být mezi jeho operandy vztah rovnosti.

Odkazované rozsahy musí být platné. u všech ukazatelů musí být možné provést zpětnou odkazování, protože poslední pozice je dosažitelná od první po zvýšení.

Průměrná složitost je lineární vzhledem k velikosti vyhledávaného rozsahu a nejhorší složitost velkých a malých písmen je také lineární vzhledem k velikosti prohledávané sekvence.

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

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

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
    vector<int>::iterator result1;
    result1 = search (v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = search (v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

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

## <a name="search_n"></a>search_n

Vyhledá první dílčí sekvenci v rozsahu zadaného počtu prvků s konkrétní hodnotou nebo vztahem k dané hodnotě podle binárního predikátu.

```cpp
template<class ForwardIterator1, class Diff2, class Type>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value);

template<class ForwardIterator1, class Diff2, class Type, class BinaryPredicate>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type, class BinaryPredicate>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který chcete prohledat.

*last1*\
Dopředný iterátor, který adresuje pozici jednu za posledním prvkem v rozsahu, který chcete prohledat.

*výpočtu*\
Velikost prohledávané dílčí sekvence.

*osa*\
Hodnota prvků ve prohledávané sekvenci.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněna, pokud mají být provedeny dva prvky jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje umístění prvního prvku první dílčí sekvence, který odpovídá zadané sekvenci nebo který je ekvivalentní ve smyslu určeném binárním predikátem.

### <a name="remarks"></a>Poznámky

`operator==` Pro určení shody mezi elementem a zadanou hodnotou musí být mezi jeho operandy vztah rovnosti.

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Složitost je lineární vzhledem k velikosti prohledávané.

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
    vector<int> v1, v2;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 5 );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 10 );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Searching v1 for first match to (5 5 5) under identity
    vector<int>::iterator result1;
    result1 = search_n ( v1.begin( ), v1.end( ), 3, 5 );

    if ( result1 == v1.end( ) )
        cout << "There is no match for a sequence ( 5 5 5 ) in v1."
            << endl;
    else
        cout << "There is at least one match of a sequence ( 5 5 5 )"
            << "\n in v1 and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for first match to (5 5 5) under one_half
    vector<int>::iterator result2;
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

## <a name="set_difference"></a>set_difference

Sjednotí všechny prvky, které patří do jednoho seřazeného zdrojového rozsahu, ale nikoli do druhého seřazeného zdrojového rozsahu, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Vstupní iterátor adresující pozici prvního prvku v prvním ze dvou seřazených zdrojových rozsahů, které budou Spojené a seřazené do jednoho rozsahu, který představuje rozdíl dvou zdrojových rozsahů.

*last1*\
Vstupní iterátor adresující pozici jednu za poslední prvek v prvním ze dvou seřazených zdrojových rozsahů, které budou Spojené a seřazené do jednoho rozsahu, který představuje rozdíl dvou zdrojových rozsahů.

*first2*\
Vstupní iterátor adresující pozici prvního prvku v druhé ze dvou po sobě jdoucích zdrojových rozsahů, které jsou spojené a seřazené do jednoho rozsahu, který představuje rozdíl dvou zdrojových rozsahů.

*last2*\
Vstupní iterátor adresující pozici jednu za poslední prvek za sekundu dvou po sobě jdoucích zdrojových rozsahů, které jsou spojené a seřazené do jednoho rozsahu, který představuje rozdíl dvou zdrojových rozsahů.

*vyústit*\
Výstupní iterátor adresující pozici prvního prvku v cílové oblasti, kde jsou dva zdrojové rozsahy spojené do jednoho seřazeného rozsahu, který představuje rozdíl dvou zdrojových rozsahů.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a by měl vracet **hodnotu true** , pokud je první prvek menší než druhý prvek a jinak **false** .

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující pozici jednu za poslední prvek v seřazeném cílovém rozsahu, který představuje rozdíl dvou zdrojových rozsahů.

### <a name="remarks"></a>Poznámky

Odkazované zdrojové rozsahy musí být platné; u všech ukazatelů musí být možné provést zpětnou odkazování a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Cílový rozsah by neměl překrývat žádnou ze zdrojových rozsahů a měl by být dostatečně velký, aby obsahoval první zdrojový rozsah.

Seřazené zdrojové rozsahy musí být uspořádány jako předběžná podmínka pro použití `set_difference` algoritmu v souladu se stejným pořadím, jaké má použít algoritmus k řazení kombinovaných rozsahů.

Operace je stabilní, protože relativní pořadí prvků v rámci jednotlivých rozsahů je zachováno v cílovém rozsahu. Sloučení algoritmů nemění zdrojové rozsahy.

Typy hodnot vstupních iterátorů musí být seřazeny méně než, aby bylo možné je seřadit, což znamená, že vzhledem k dvěma prvkům je možné určit, že jsou ekvivalentní (v tom smyslu, že ani jeden není menší než druhý) nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou v obou zdrojových oblastech ekvivalentní prvky, prvky v prvním rozsahu předcházejí prvky z druhého zdrojového rozsahu v cílovém rozsahu. Pokud zdrojové rozsahy obsahují duplicity elementu, jako je více v prvním zdrojovém rozsahu než v druhém, pak cílový rozsah bude obsahovat číslo, pomocí kterého budou výskyty těchto prvků v prvním zdrojovém rozsahu překračovat výskyty Tyto prvky ve druhém zdrojovém rozsahu.

Složitost algoritmu je lineární s při nejvíce `2 * ((last1 - first1) - (last2 - first2)) - 1` porovnávání pro neprázdné zdrojové rozsahy.

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
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a difference in asscending
    // order with the default binary predicate less<int>( )
    Result1 = set_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a difference in descending
    // order specify binary predicate greater<int>( )
    Result2 = set_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_intersection"></a>set_intersection

Sjednotí všechny prvky, které náleží do obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result);

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Vstupní iterátor adresující pozici prvního prvku v prvním ze dvou seřazených zdrojových rozsahů, které budou Spojené a seřazené do jednoho rozsahu, který představuje průnik dvou zdrojových rozsahů.

*last1*\
Vstupní iterátor adresující pozici jednu za poslední prvek v prvním ze dvou seřazených zdrojových rozsahů, které budou Spojené a seřazené do jednoho rozsahu, který představuje průnik dvou zdrojových rozsahů.

*first2*\
Vstupní iterátor adresující pozici prvního prvku v druhé ze dvou po sobě jdoucích zdrojových rozsahů, které jsou spojené a seřazené do jednoho rozsahu, který představuje průnik dvou zdrojových rozsahů.

*last2*\
Vstupní iterátor adresující pozici jednu za poslední prvek v druhé ze dvou po sobě následujících seřazených zdrojových rozsahů, které jsou spojené a seřazené do jednoho rozsahu, který představuje průnik dvou zdrojových rozsahů.

*vyústit*\
Výstupní iterátor adresující pozici prvního prvku v cílové oblasti, kde jsou dva zdrojové rozsahy spojené s jedním seřazeným rozsahem, který představuje průnik dvou zdrojových rozsahů.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a by měl vracet **hodnotu true** , pokud je první prvek menší než druhý prvek a jinak **false** .

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující pozici jednu za poslední prvek v seřazeném cílovém rozsahu, který představuje průnik dvou zdrojových rozsahů.

### <a name="remarks"></a>Poznámky

Odkazované zdrojové rozsahy musí být platné; u všech ukazatelů musí být možné provést zpětnou odkazování a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Cílový rozsah by neměl překrývat žádnou ze zdrojových rozsahů a měl by být dostatečně velký, aby obsahoval cílový rozsah.

Seřazené zdrojové rozsahy musí být uspořádány jako předběžná podmínka pro použití algoritmu sloučení v souladu se stejným pořadím, jaké má použít algoritmus k řazení kombinovaných rozsahů.

Operace je stabilní, protože relativní pořadí prvků v rámci jednotlivých rozsahů je zachováno v cílovém rozsahu. Zdrojové rozsahy nejsou tímto algoritmem změněny.

Typy hodnot vstupních iterátorů musí být menší než srovnatelné, aby bylo možné je seřadit, což znamená, že vzhledem k dvěma prvkům je možné určit, že jsou ekvivalentní (v tom smyslu, že ani jeden není menší než druhý) nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou v obou zdrojových oblastech ekvivalentní prvky, prvky v prvním rozsahu předcházejí prvky z druhého zdrojového rozsahu v cílovém rozsahu. Pokud zdrojové rozsahy obsahují duplicity elementu, bude cílový rozsah obsahovat maximální počet prvků, které se vyskytují v obou zdrojových oblastech.

Složitost algoritmu je lineární s při nejvíce `2 * ((last1 - first1) + (last2 - first2)) - 1` porovnávání pro neprázdné zdrojové rozsahy.

### <a name="example"></a>Příklad

```cpp
// alg_set_intersection.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
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
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into an intersection in asscending order with the
    // default binary predicate less<int>( )
    Result1 = set_intersection ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Intersection of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; ++Iter1 )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into an intersection in descending order, specify
    // binary predicate greater<int>( )
    Result2 = set_intersection ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Intersection of source ranges with binary predicate"
            << " greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into an intersection applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_intersection ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Intersection of source ranges with binary predicate "
            << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; ++Iter3 )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_symmetric_difference"></a>set_symmetric_difference

Sjednotí všechny prvky, které náleží do jednoho, ale nikoli obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Vstupní iterátor adresující pozici prvního prvku v prvním ze dvou seřazených zdrojových rozsahů, které budou Spojené a seřazeny do jednoho rozsahu představujícího symetrický rozdíl dvou zdrojových rozsahů.

*last1*\
Vstupní iterátor adresující pozici jednu za poslední prvek v prvním ze dvou seřazených zdrojových rozsahů, které budou Spojené a seřazené do jednoho rozsahu představujícího symetrický rozdíl dvou zdrojových rozsahů.

*first2*\
Vstupní iterátor adresující pozici prvního prvku v druhé ze dvou po sobě jdoucích zdrojových rozsahů, které jsou spojené a seřazené do jednoho rozsahu představujícího symetrický rozdíl dvou zdrojových rozsahů.

*last2*\
Vstupní iterátor adresující pozici jednu za poslední prvek v druhé ze dvou po sobě jdoucích zdrojových rozsahů, které jsou spojené a seřazené v jednom rozsahu, který představuje symetrický rozdíl dvou zdrojových rozsahů.

*vyústit*\
Výstupní iterátor adresující pozici prvního prvku v cílové oblasti, kde jsou dva zdrojové rozsahy spojené s jedním seřazeným rozsahem, který představuje symetrický rozdíl dvou zdrojových rozsahů.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a by měl vracet **hodnotu true** , pokud je první prvek menší než druhý prvek a jinak **false** .

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující pozici jednu za poslední prvek v seřazeném cílovém rozsahu představující symetrický rozdíl dvou zdrojových rozsahů.

### <a name="remarks"></a>Poznámky

Odkazované zdrojové rozsahy musí být platné; u všech ukazatelů musí být možné provést zpětnou odkazování a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Cílový rozsah by neměl překrývat žádnou ze zdrojových rozsahů a měl by být dostatečně velký, aby obsahoval cílový rozsah.

Seřazené zdrojové rozsahy musí být uspořádány jako předběžná podmínka pro použití `merge*` algoritmu v souladu se stejným pořadím, jaké má použít algoritmus k řazení kombinovaných rozsahů.

Operace je stabilní, protože relativní pořadí prvků v rámci jednotlivých rozsahů je zachováno v cílovém rozsahu. Sloučení algoritmů nemění zdrojové rozsahy.

Typy hodnot vstupních iterátorů musí být menší než srovnatelné, aby bylo možné je seřadit, což znamená, že vzhledem k dvěma prvkům je možné určit, že jsou ekvivalentní (v tom smyslu, že ani jeden není menší než druhý) nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou v obou zdrojových oblastech ekvivalentní prvky, prvky v prvním rozsahu předcházejí prvky z druhého zdrojového rozsahu v cílovém rozsahu. Pokud zdrojové rozsahy obsahují duplicity elementu, pak cílový rozsah bude obsahovat absolutní hodnotu čísla, o které výskyty těchto prvků v jednom ze zdrojových rozsahů překročí výskyt těchto prvků v druhém zdroji. oblasti.

Složitost algoritmu je lineární s při nejvíce `2 * ((last1 - first1) - (last2 - first2)) - 1` porovnávání pro neprázdné zdrojové rozsahy.

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
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in ascending
    // order with the default binary predicate less<int>( )
    Result1 = set_symmetric_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_symmetric_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in descending
    // order, specify binary predicate greater<int>( )
    Result2 = set_symmetric_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_symmetric_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_symmetric_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_symmetric_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_union"></a>set_union

Sjednotí všechny prvky, které náleží alespoň do jednoho ze dvou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Vstupní iterátor adresující pozici prvního prvku v prvním ze dvou seřazených zdrojových rozsahů, které budou Spojené a seřazené do jednoho rozsahu představujícího sjednocení dvou zdrojových rozsahů.

*last1*\
Vstupní iterátor adresující pozici jednu za poslední prvek v prvním ze dvou seřazených zdrojových rozsahů, které budou Spojené a seřazené do jednoho rozsahu představujícího sjednocení dvou zdrojových rozsahů.

*first2*\
Vstupní iterátor adresující pozici prvního prvku v druhé ze dvou po sobě jdoucích zdrojových rozsahů, které jsou spojené a seřazené do jednoho rozsahu představujícího sjednocení dvou zdrojových rozsahů.

*last2*\
Vstupní iterátor adresující pozici jednu za poslední prvek v druhé ze dvou po sobě jdoucích zdrojových rozsahů, které jsou spojené a seřazené do jednoho rozsahu představujícího sjednocení dvou zdrojových rozsahů.

*vyústit*\
Výstupní iterátor adresující pozici prvního prvku v cílové oblasti, kde jsou dva zdrojové rozsahy spojené do jednoho seřazeného rozsahu představujícího sjednocení dvou zdrojových rozsahů.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Binární predikát přijímá dva argumenty a by měl vracet **hodnotu true** , pokud je první prvek menší než druhý prvek a jinak **false** .

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující pozici jednu za poslední prvek v seřazeném cílovém rozsahu, který představuje sjednocení dvou zdrojových rozsahů.

### <a name="remarks"></a>Poznámky

Odkazované zdrojové rozsahy musí být platné; u všech ukazatelů musí být možné provést zpětnou odkazování a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Cílový rozsah by neměl překrývat žádnou ze zdrojových rozsahů a měl by být dostatečně velký, aby obsahoval cílový rozsah.

Seřazené zdrojové rozsahy musí být uspořádány jako předběžná podmínka pro použití `merge` algoritmu v souladu se stejným pořadím, jaké má použít algoritmus k řazení kombinovaných rozsahů.

Operace je stabilní, protože relativní pořadí prvků v rámci jednotlivých rozsahů je zachováno v cílovém rozsahu. Zdrojové rozsahy nejsou tímto algoritmem `merge`změněny.

Typy hodnot vstupních iterátorů musí být menší než srovnatelné, aby bylo možné je seřadit, což znamená, že vzhledem k dvěma prvkům je možné určit, že jsou ekvivalentní (v tom smyslu, že ani jeden není menší než druhý) nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou v obou zdrojových oblastech ekvivalentní prvky, prvky v prvním rozsahu předcházejí prvky z druhého zdrojového rozsahu v cílovém rozsahu. Pokud zdrojové rozsahy obsahují duplicity elementu, bude cílový rozsah obsahovat maximální počet prvků, které se vyskytují v obou zdrojových oblastech.

Složitost algoritmu je lineární s nejvyšším `2 * ((last1 - first1) - (last2 - first2)) - 1` porovnáním.

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
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a union in ascending order with the default
        // binary predicate less<int>( )
    Result1 = set_union ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Union of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a union in descending order, specify binary
    // predicate greater<int>( )
    Result2 = set_union ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Union of source ranges with binary predicate greater "
         << "specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a union applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_union ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Union of source ranges with binary predicate "
         << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="shuffle"></a>náhodný

Rozmístí prvky pro daný rozsah pomocí generátoru náhodných čísel (mění uspořádání).

```cpp
template<class RandomAccessIterator, class UniformRandomNumberGenerator>
void shuffle(
    RandomAccessIterator first,
    RandomAccessIterator last,
    UniformRandomNumberGenerator&& gen);
```

### <a name="parameters"></a>Parametry

*první*\
Iterátor na první prvek v rozsahu, který má být zamezit, včetně. Musí splňovat požadavky `RandomAccessIterator` a `ValueSwappable`.

*posledního*\
Iterátor k poslednímu prvku v rozsahu, který má být v rozsahu bezho výběru, exkluzivní. Musí splňovat požadavky `RandomAccessIterator` a `ValueSwappable`.

*pole*\
Generátor náhodných čísel, který `shuffle()` funkce použije pro operaci. Musí splňovat požadavky `UniformRandomNumberGenerator`.

### <a name="remarks"></a>Poznámky

Další informace a ukázka kódu, který používá `shuffle()`, naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="sort"></a>druhu

Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.

```cpp
template<class RandomAccessIterator>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v rozsahu, který má být seřazen.

*posledního*\
Iterátor náhodného přístupu, který adresuje pozici jednu za posledním prvkem v rozsahu, který má být seřazen.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání, které se má splnit po sobě jdoucích prvků v řazení. Tento binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud jsou dva argumenty v pořadí, a jinak **false** . Tato funkce komparátor musí pro páry prvků z sekvence vytvořit přísné slabé řazení. Další informace najdete v tématu [algoritmy](../standard-library/algorithms.md).

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Prvky jsou ekvivalentní, ale nejsou nutně stejné, pokud není ani méně než druhá. `sort` Algoritmus není stabilní, takže nezaručuje, že se zachová relativní pořadí ekvivalentních prvků. Algoritmus `stable_sort` zachovává toto původní řazení.

Průměr složitosti řazení je, kde `O( N log N )` *N* = *Poslední* - byl*první*.

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
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="sort_heap"></a>sort_heap

Převede haldu na seřazený rozsah.

```cpp
template<class RandomAccessIterator>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*první*\
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v cílové haldě.

*posledního*\
Iterátor náhodného přístupu, který adresuje umístění jedno za poslední prvek v cílové haldě.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Relační predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="remarks"></a>Poznámky

Haldy mají dvě vlastnosti:

- První prvek je vždy největší.

- Prvky lze přidat nebo odebrat ve logaritmických čase.

Po použití aplikace v případě, že tento algoritmus, rozsah, na který byl použit, již není halda.

Nejedná se o stabilní řazení, protože relativní pořadí ekvivalentních prvků není nutně zachováno.

Haldy představují ideální způsob implementace front priorit a používají se v implementaci C++ [třídy priority_queue](../standard-library/priority-queue-class.md)kontejnerů standardní knihovny.

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

`N log N`Složitost je maximálně, kde *N* = *Poslední* -  *.*

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

void print(const string& s, const vector<int>& v)
{
    cout << s << ": ( ";

    for (auto i = v.begin(); i != v.end(); ++i)
    {
        cout << *i << " ";
    }

    cout << ")" << endl;
}

int main()
{
    vector<int> v;
    for (int i = 1; i <= 9; ++i)
    {
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

## <a name="stable_partition"></a>stable_partition

Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují. Relativní pořadí ekvivalentních prvků je zachováno.

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred );

template<class ExecutionPolicy, class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Obousměrný iterátor, který adresuje umístění prvního prvku v rozsahu, který se má rozdělit na oddíly.

*posledního*\
Obousměrný iterátor, který adresuje pozici jednu za posledním prvkem v rozsahu, který se má rozdělit na oddíly.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněna, je-li prvek klasifikován. Unární predikát přijímá jediný argument a vrátí **hodnotu true** , pokud je splněna, nebo **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který adresuje umístění prvního prvku v rozsahu, který nesplňuje podmínky predikátu.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Prvky *a* a *b* jsou ekvivalentní, ale nemusí být nutně stejné, pokud `pred( a, b )` jsou obě hodnoty `pred( b, a )` false a má hodnotu false, kde *před* je predikát určený parametrem. `stable_partition` Algoritmus je stabilní a zaručuje, že relativní pořadí ekvivalentních prvků bude zachováno. Algoritmus `partition` nutně nezachovává toto původní řazení.

### <a name="example"></a>Příklad

```cpp
// alg_stable_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

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

## <a name="stable_sort"></a>stable_sort

Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem a zachová relativní pořadí ekvivalentních prvků.

```cpp
template<class BidirectionalIterator>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last );

template<class BidirectionalIterator, class Compare>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last,
    Compare pred );

template<class ExecutionPolicy, class RandomAccessIterator>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Obousměrný iterátor, který adresuje pozici prvního prvku v rozsahu, který má být seřazen.

*posledního*\
Obousměrný iterátor, který adresuje pozici jednu za posledním prvkem v rozsahu, který má být seřazen.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání, které se má splnit po sobě jdoucích prvků v řazení. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="remarks"></a>Poznámky

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Prvky jsou ekvivalentní, ale nejsou nutně stejné, pokud není ani méně než druhá. `sort` Algoritmus je stabilní a zaručuje, že relativní pořadí ekvivalentních prvků bude zachováno.

`stable_sort` Složitá -  doba běhu závisí na množství dostupné paměti, ale nejlepšího případu ( `O(N log N)` `O(N (log N)^2)`s ohledem na dostatek paměti) a nejhorším případem, kdy *N* = *Poslední*  *nejprve*. Algoritmus je obvykle mnohem rychlejší než `stable_sort`. `sort`

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
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
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

## <a name="swap"></a>adresu

První přepsání vyměňuje hodnoty dvou objektů. Druhé přepsání vyměňuje hodnoty mezi dvěma poli objektů.

```cpp
template<class Type>
void swap(
    Type& left,
    Type& right);
template<class Type, size_t N>
void swap(
    Type (& left)[N],
    Type (& right)[N]);
```

### <a name="parameters"></a>Parametry

*zbývá*\
Pro první přepsání první objekt, na který má být vyměněn obsah. Pro druhé přepsání první pole objektů, u kterých má být obsah vyměněn.

*Kliknutím*\
Pro první přepsání má druhý objekt vyměňováný obsah. Pro druhé přepsání bude druhé pole objektů vyměněno jeho obsah.

### <a name="remarks"></a>Poznámky

První přetížení je navrženo pro provoz na jednotlivých objektech. Druhé přetížení zamění obsah objektů mezi dvěma poli.

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
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

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

## <a name="swap_ranges"></a>swap_ranges

Vymění prvky z jednoho rozsahu za prvky druhého rozsahu o stejné velikosti.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
   ForwardIterator1 first1,
   ForwardIterator1 last1,
   ForwardIterator2 first2 );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Dopředný iterátor ukazující na první pozici prvního rozsahu, jehož prvky mají být vyměněny.

*last1*\
Dopředný iterátor ukazující na jednu za poslední pozicí prvního rozsahu, jehož prvky mají být vyměněny.

*first2*\
Dopředný iterátor ukazující na první pozici druhého rozsahu, jehož prvky mají být vyměněny.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor ukazující na jednu za poslední pozici druhého rozsahu, jehož prvky mají být vyměněny.

### <a name="remarks"></a>Poznámky

Odkazované rozsahy musí být platné. u všech ukazatelů musí být možné provést zpětnou odkazování, protože poslední pozice je dosažitelná od první po zvýšení. Druhý rozsah musí být stejně velký jako první rozsah.

Složitost je lineární s provedenými swapy *last1* - *first1* . Pokud jsou prvky z kontejnerů stejného typu měněny, `swap` měly by být použity členské funkce z tohoto kontejneru, protože členská funkce má obvykle složitost konstanty.

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
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
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
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "Deque d1 is  ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
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

## <a name="transform"></a>převedení

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

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryOperation>
ForwardIterator2 transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryOperation op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class BinaryOperation>
ForwardIterator transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*first1*\
Vstupní iterátor adresující pozici prvního prvku v prvním zdrojovém rozsahu, na kterém má být provozován.

*last1*\
Vstupní iterátor adresující pozici jednu za poslední prvek v prvním zdrojovém rozsahu provozovaném na.

*first2*\
Vstupní iterátor adresující pozici prvního prvku v druhém zdrojovém rozsahu, na kterém má být provozován.

*vyústit*\
Výstupní iterátor adresující pozici prvního prvku v cílovém rozsahu.

*kláves*\
Uživatelem definovaný unární objekt funkce, který je použit v první verzi algoritmu, který je použit pro každý prvek v prvním zdrojovém rozsahu nebo v objektu binární funkce (UD), který je použit ve druhé verzi algoritmu, který je použit jako párový, v dopředné objednávce , do dvou zdrojových rozsahů.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující pozici jednu za poslední prvek v cílovém rozsahu, který přijímá výstupní prvky transformované objektem funkce.

### <a name="remarks"></a>Poznámky

Odkazované rozsahy musí být platné. u všech ukazatelů musí být možné provést zpětnou odkazování a v rámci každé sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku. Cílový rozsah musí být dostatečně velký, aby obsahoval transformované zdrojové rozsahy.

Pokud je *výsledek* nastaven na hodnotu *first1* v první verzi algoritmu, budou zdrojové a cílové rozsahy stejné a pořadí bude upraveno. Ale *výsledek* nesmí adresovat pozici v rozsahu [`first1` + 1, `last1`).

Složitost je lineární s porovnáním nejvíc (`last1` - `first1`).

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
    MultValue ( const Type& value ) : Factor ( value ) { }

    // The function call for the element to be multiplied
    Type operator( ) ( Type& elem ) const
    {
        return elem * Factor;
    }
};

int main()
{
    using namespace std;
    vector<int> v1, v2 ( 7 ), v3 ( 7 );
    vector<int>::iterator Iter1, Iter2 , Iter3;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
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
            << "by the factor 5 & copying to v2 gives:\n v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // The second version of transform used to multiply the
    // elements of the vectors v1mod & v2 pairwise
    transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin( ),
        multiplies<int>( ) );

    cout << "Multiplying elements of the vectors v1mod and v2 pairwise "
            << "gives:\n v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

```Output
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
The elements of the vector v1 multiplied by 2 in place gives:
v1mod = ( -8 -6 -4 -2 0 2 4 ).
Multiplying the elements of the vector v1mod
by the factor 5 & copying to v2 gives:
v2 = ( -40 -30 -20 -10 0 10 20 ).
Multiplying elements of the vectors v1mod and v2 pairwise gives:
v3 = ( 320 180 80 20 0 20 80 ).
```

## <a name="unique"></a>tabulka

Odstraní duplicitní prvky, které v zadaném rozsahu sousedí.

```cpp
template<class ForwardIterator>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který adresuje umístění prvního prvku v rozsahu, který má být prohledán pro odstranění duplicitních dat.

*posledního*\
Dopředný iterátor, který adresuje umístění jedno místo za posledním prvkem v rozsahu, který má být prohledán pro odstranění duplicitních dat.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněna, pokud mají být provedeny dva prvky jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor k novému konci upravené sekvence, která neobsahuje žádné po sobě jdoucí duplicity, která řeší pozici jednu za poslední prvek, který se neodebral.

### <a name="remarks"></a>Poznámky

Obě formy algoritmu odstraňují druhou kopii po sobě jdoucích dvojic stejného prvku.

Operace algoritmu je stabilní, takže se nemění relativní pořadí neodstraněných prvků.

Odkazovaný rozsah musí být platný; všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku. počet prvků v sekvenci není změněn algoritmem `unique` a elementy za koncem upravené sekvence jsou dereferenceované, ale nejsou určeny.

Složitost je lineární, vyžaduje `(last - first) - 1` porovnání.

Seznam poskytuje efektivnější členskou funkci "Unique", která může fungovat lépe.

Tyto algoritmy nelze použít u asociativního kontejneru.

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
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2, v1_Iter3,
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

## <a name="unique_copy"></a>unique_copy

Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu s výjimkou sousedících duplicitních prvků.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result );

template<class InputIterator, class OutputIterator, class BinaryPredicate>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryPredicate pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 unique_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryPredicate>
ForwardIterator2 unique_copy(ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Průměrná*\
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který adresuje umístění prvního prvku ve zdrojovém rozsahu, který se má zkopírovat.

*posledního*\
Dopředný iterátor, který adresuje umístění jednu za poslední prvek ve zdrojovém rozsahu, který se má zkopírovat.

*vyústit*\
Výstupní iterátor adresující pozici prvního prvku v cílovém rozsahu, který přijímá kopii se odebranými po sobě jdoucích duplicit.

*čekání*\
Objekt funkce predikátu definovaný uživatelem, který definuje podmínku, která má být splněna, pokud mají být provedeny dva prvky jako ekvivalentní. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující pozici jednu za poslední prvek v cílovém rozsahu, který přijímá kopii se odebranými po sobě jdoucích duplicit.

### <a name="remarks"></a>Poznámky

Obě formy algoritmu odstraňují druhou kopii po sobě jdoucích dvojic stejného prvku.

Operace algoritmu je stabilní, takže se nemění relativní pořadí neodstraněných prvků.

Odkazované rozsahy musí být platné. všechny ukazatele musí být možné odkázat a v rámci sekvence je poslední pozice dosažitelná z první pomocí přírůstku.

Složitost je lineární, vyžadování (`last` - `first`) porovnání.

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
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2,
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

## <a name="upper_bound"></a>upper_bound

Najde pozici prvního prvku v seřazeném rozsahu, který má hodnotu větší než zadaná hodnota, kde kritérium pořadí může být určeno binárním predikátem.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*první*\
Pozice prvního prvku v rozsahu, který má být prohledán.

*posledního*\
Pozice za posledním prvkem v rozsahu, který má být prohledán.

*osa*\
Hodnota v seřazeném rozsahu, která musí být překročena hodnotou prvku řešeného iterátorem vráceného.

*čekání*\
Objekt funkce predikátu porovnání definovaný uživatelem, který definuje smysl, ve kterém jeden prvek je menší než jiný. Relační predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor na pozici prvního prvku, který má hodnotu větší než zadaná hodnota.

### <a name="remarks"></a>Poznámky

Odkazovaný seřazený zdrojový rozsah musí být platný; všechny iterátory musí být možné odkázat a v rámci sekvence musí být poslední pozice dosažitelná z první pomocí přírůstku.

Seřazený rozsah je podmínkou pro použití `upper_bound` a kde kritérium řazení je stejné jako určené predikátem porovnání.

Rozsah není upraven nástrojem `upper_bound`.

Typy hodnot iterátorů dopředných iterátorů vyžadují, aby byly objednány méně než porovnatelné, což znamená, že vzhledem k dvěma prvkům lze určit, že jsou ekvivalentní (v tom smyslu, že ani jeden není menší než druhý) nebo že jeden je menší než druhý. Výsledkem je řazení mezi neekvivalentními prvky.

Složitost algoritmu je logaritmický pro iterátory s náhodným přístupem a v opačném případě lineární, přičemž počet kroků je úměrný`last - first`hodnotě ().

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
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
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
        << "binary predicate mod_lesser is v3 = ( " ;
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

    // upper_bound of 3 in v3 with the binary predicate mod_lesser
    Result = upper_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The upper_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```
