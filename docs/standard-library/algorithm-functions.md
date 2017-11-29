---
title: '&lt;algoritmus&gt; funkce | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
ms.assetid: c10b0c65-410c-4c83-abf8-8b7f61bba8d0
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
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
ms.openlocfilehash: 2b70ab848071bb1196ceb57f986a6e74fe43d2de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltalgorithmgt-functions"></a>&lt;algoritmus&gt; funkce
||||  
|-|-|-|  
|[Přesunutí](#alg_move)|[adjacent_find –](#adjacent_find)|[all_of](#all_of)|  
|[any_of](#any_of)|[binary_search –](#binary_search)|[kopírování](#copy)|  
|[copy_backward –](#copy_backward)|[copy_if](#copy_if)|[copy_n](#copy_n)|  
|[počet](#count)|[count_if –](#count_if)|[stejné](#equal)|  
|[equal_range –](#equal_range)|[výplně](#fill)|[fill_n](#fill_n)|  
|[Najít](#find)|[find_end –](#find_end)|[find_first_of –](#find_first_of)|  
|[find_if –](#find_if)|[find_if_not –](#find_if_not)|[for_each –](#for_each)|  
|[Generovat](#generate)|[generate_n –](#generate_n)|[zahrnuje](#includes)|  
|[inplace_merge](#inplace_merge)|[is_heap](#is_heap)|[is_heap_until –](#is_heap_until)|  
|[is_partitioned](#is_partitioned)|[is_permutation](#is_permutation)|[is_sorted](#is_sorted)|  
|[is_sorted_until –](#is_sorted_until)|[iter_swap –](#iter_swap)|[lexicographical_compare –](#lexicographical_compare)|  
|[lower_bound –](#lower_bound)|[make_heap –](#make_heap)|[maximální počet](#max)|  
|[max_element –](#max_element)|[sloučení](#merge)|[min.](#min)|  
|[min_element –](#min_element)|[minmax](#minmax)|[minmax_element](#minmax_element)|  
|[Neshoda](#mismatch)|[move_backward](#move_backward)|[next_permutation –](#next_permutation)|  
|[none_of](#none_of)|[nth_element –](#nth_element)|[partial_sort –](#partial_sort)|  
|[partial_sort_copy –](#partial_sort_copy)|[oddíl](#partition)|[partition_copy –](#partition_copy)|  
|[partition_point](#partition_point)|[pop_heap –](#pop_heap)|[prev_permutation –](#prev_permutation)|  
|[push_heap –](#push_heap)|[random_shuffle –](#random_shuffle)|[odebrat](#remove)|  
|[remove_copy –](#remove_copy)|[remove_copy_if –](#remove_copy_if)|[remove_if –](#remove_if)|  
|[nahradit](#replace)|[replace_copy –](#replace_copy)|[replace_copy_if –](#replace_copy_if)|  
|[replace_if –](#replace_if)|[zpětné](#reverse)|[reverse_copy –](#reverse_copy)|  
|[Otočit](#rotate)|[rotate_copy –](#rotate_copy)|[hledání](#search)|  
|[search_n –](#search_n)|[set_difference –](#set_difference)|[set_intersection –](#set_intersection)|  
|[set_symmetric_difference –](#set_symmetric_difference)|[set_union –](#set_union)|[řazení](#sort)|  
|[sort_heap –](#sort_heap)|[stable_partition –](#stable_partition)|[stable_sort –](#stable_sort)|  
|[náhodný výběr](#shuffle)|[swap](#swap)|[swap_ranges –](#swap_ranges)|  
|[transformace](#transform)|[jedinečné](#unique)|[unique_copy –](#unique_copy)|  
|[upper_bound –](#upper_bound)|  
  
##  <a name="adjacent_find"></a>adjacent_find –  
 Vyhledá dva sousedící prvky, které jsou buď rovny, nebo splňují zadanou podmínku.  
  
```  
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
  `first`  
 Předat dál iterator adresování pozice první prvek v rozsahu prohledávání.  
  
 `last`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu prohledávání.  
  
 `comp`  
 Binární predikát poskytnutí podmínku, která má vyhovět hodnoty sousedících elementů v prohledávaný rozsah.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator na první prvek přiléhající pár, které jsou buď stejné navzájem (v první verzi) nebo která splňují zadanou podmínku poskytují binární predikát (v druhé verze), za předpokladu, že se nachází dvojici elementů. V opačném iterovat odkazující na `last` je vrácen.  
  
### <a name="remarks"></a>Poznámky  
 `adjacent_find` Algoritmus je algoritmus nonmutating pořadí. Rozsah má proběhnout, musí být platná; musí být všechny ukazatele dereferenceable a je dostupný z první poslední pozice podle Inkrementace. Čas složitost algoritmu je lineární počet elementů obsažených v rozsahu.  
  
 `operator==` Používá k určení nalezena shoda mezi elementy musí použít ekvivalenční vztah mezi jejími operandy.  
  
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
  
##  <a name="all_of"></a>all_of  
 Vrátí `true` při podmínku nachází na každý prvek v daném rozsahu.  
  
```  
template<class InputIterator, class Predicate>  
    bool all_of(  
        InputIterator first,   
        InputIterator last,   
        BinaryPredicatecomp);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterator, která určuje, kde začít vyhledávat podmínku. Iterace označí, kde rozsah elementy spustí.  
  
 `last`  
 Iterátor vstupní, který označuje konec rozsahu elementy, aby kontrolovat podmínku.  
  
 `comp`  
 Podmínku, kterou chcete otestovat. Toto je uživatelem definované funkce predikátu objekt, který definuje podmínku, která má vyhovět element probíhá kontrola. Predikát přijímá jeden argument a vrátí `true` nebo `false`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `true` v případě zjištění stavu na každý prvek v uvedených rozsahu, a `false` Pokud podmínka není zjištěna aspoň jednou.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí `true` pouze tehdy, pokud pro každou `N` v rozsahu `[0,Last - first)`, predikát `comp(*(_First + N))` je `true`.  
  
##  <a name="any_of"></a>any_of  
 Vrátí `true` Pokud je přítomen alespoň jednou v určeném rozsahu elementů podmínku.  
  
```  
template<class InputIterator, class UnaryPredicate>  
    bool any_of(  
        InputIterator first,   
        InputIterator last,   
        UnaryPredicate comp);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterator, která určuje, kde zahájí kontrolu rozsahu prvků podmínku.  
  
 `last`  
 Iterátor vstupní, který označuje konec rozsahu elementy, aby kontrolovat podmínku.  
  
 `comp`  
 Podmínku, kterou chcete otestovat. To zajišťuje objekt uživatelem definované funkce predikátu. Predikát definuje podmínku, která má element testuje vyhovět. Predikát přijímá jeden argument a vrátí `true` nebo `false`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `true` Pokud podmínka je zjištěna alespoň jednou v uvedených rozsahu `false` Pokud podmínka nikdy zjištěn.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí `true` pouze tehdy, pokud pro některé `N` v rozsahu  
  
 `[0, last - first)`, predikát `comp(*(first + N))` hodnotu true.  
  
##  <a name="binary_search"></a>binary_search –  
 Ověřuje, zda v seřazeném rozsahu existuje prvek, který je roven zadané hodnotě nebo je jí ekvivalentní ve smyslu určeném binárním predikátem.  
  
```  
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
 `first`  
 Předat dál iterator adresování pozice první prvek v rozsahu prohledávání.  
  
 `last`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu prohledávání.  
  
 `value`  
 Požadovaná hodnota odpovídala hodnota elementu nebo které musí splňovat podmínky s hodnotou elementu uvedená v predikátu binární.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém jeden element je menší než jiné. Binární predikát má dva argumenty a vrátí `true` při a `false` při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je nalezen element v rozsahu, která je rovna nebo ekvivalentní se zadanou hodnotou; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Seřazené zdrojový rozsah odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v pořadí, poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Seřazené oblasti musí každý být uspořádány podmínkou pro použití `binary_search` algoritmus v souladu s stejné řazení jako má být použita algoritmem seřadit kombinované rozsahy.  
  
 Zdrojových oblastí nejsou upraveném `binary_search`.  
  
 Musí být menší hodnota typy dopředného iterátory – než porovnatelný seřadit, tak, aby hodnotě dva elementy, může být bylo zjištěno, že jsou ekvivalentní (v tom smyslu, že ani je menší než druhá) nebo jedna je menší než druhý. To vede řazení mezi nonequivalent elementy  
  
 Složitost algoritmu je logaritmické pro iterátory náhodný přístup a lineární, jinak se počet kroků úměrná ( `last`  -  `first`).  
  
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
  
int main( )  
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
    if( binary_search(List1.begin(), List1.end(), 10) )  
        cout << "There is an element in list List1 with a value equal to 10."  
        << endl;  
    else  
        cout << "There is no element in list List1 with a value equal to 10."  
        << endl;  
  
    // a binary_search under the binary predicate greater  
    List1.sort(greater<int>());  
    if( binary_search(List1.begin(), List1.end(), 10, greater<int>()) )  
        cout << "There is an element in list List1 with a value greater than 10 "  
        << "under greater than." << endl;  
    else  
        cout << "No element in list List1 with a value greater than 10 "  
        << "under greater than." << endl;  
  
    // a binary_search under the user-defined binary predicate mod_lesser  
    vector<int> v1;  
  
    for( auto i = -2; i <= 4; ++i )  
    {  
        v1.push_back(i);  
    }  
  
    sort(v1.begin(), v1.end(), mod_lesser);  
  
    cout << "Ordered using mod_lesser, vector v1 = ( " ;  
    for( auto Iter : v1 )  
        cout << Iter << " ";  
    cout << ")" << endl;  
  
    if( binary_search(v1.begin(), v1.end(), -3, mod_lesser) )  
        cout << "There is an element with a value equivalent to -3 "  
        << "under mod_lesser." << endl;  
    else  
        cout << "There is not an element with a value equivalent to -3 "  
        << "under mod_lesser." << endl;  
}   
```  
  
##  <a name="copy"></a>kopírování  
 Přiřadí hodnoty prvků ze zdrojového rozsahu do cílového rozsahu a provede iterace přes zdrojové sekvence prvků a přiřadí je novým pozicím směrem dopředu.  
  
```  
template<class InputIterator, class OutputIterator>  
    OutputIterator copy(
        InputIterator first, 
        InputIterator last, 
        OutputIterator destBeg);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterovat pozice první prvek v zdrojový rozsah adres.  
  
 `last`  
 Vstupní iterovat pozice, který je jednou za poslední element v zdrojový rozsah adres.  
  
 *destBeg*  
 Iterátor výstup adresování pozice první prvek v cílové oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup adresování pozice, který je jednou za poslední element v cílovém rozsahu, který je, adresy iterator `result` + ( `last`  -   `first` ).  
  
### <a name="remarks"></a>Poznámky  
 Zdrojová oblast musí být platná a v cíli musí být dostatek místa na pro všechny prvky, které jsou kopírovány.  
  
 Vzhledem k tomu, že algoritmus kopie zdrojové elementy v pořadí od první prvek, cílový rozsah může dojít k překrytí s zdrojový rozsah zadaný `last` pozici rozsah zdrojových není obsažen v cílové oblasti. **kopírování** slouží k posunutí elementy na levé straně, ale není pravé, pokud neexistuje žádné překryv mezi zdrojové a cílové oblasti. Chcete-li posunutí doprava libovolný počet pozic, použijte [copy_backward –](../standard-library/algorithm-functions.md#copy_backward) algoritmus.  
  
 **Kopie** algoritmus pouze změní hodnoty ukazuje iterátory, přiřazení nové hodnoty na elementy v cílové oblasti. Nelze ho použít k vytvoření nových prvků a nelze vložit prvky do prázdného zásobníku přímo.  
  
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
  
##  <a name="copy_backward"></a>copy_backward –  
 Přiřadí hodnoty prvků ze zdrojového rozsahu do cílového rozsahu a provede iterace přes zdrojové sekvence prvků a přiřadí je novým pozicím směrem dozadu.  
  
```  
template<class BidirectionalIterator1, class BidirectionalIterator2>  
    BidirectionalIterator2 copy_backward(
        BidirectionalIterator1 first, 
        BidirectionalIterator1 last, 
        BidirectionalIterator2 destEnd);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Obousměrný iterátor, který adresuje umístění prvního prvku ve zdrojové oblasti.  
  
 `last`  
 Obousměrný iterátor, který adresuje umístění jedno místo za posledním prvkem ve zdrojové oblasti.  
  
 `destEnd`  
 Obousměrný iterátor, který adresuje umístění jedno místo za posledním prvkem v cílové oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup adresování pozice, který je jednou za poslední element v cílovém rozsahu, který je, adresy iterator `destEnd` -( `last`  -   `first` ).  
  
### <a name="remarks"></a>Poznámky  
 Zdrojová oblast musí být platná a v cíli musí být dostatek místa na pro všechny prvky, které jsou kopírovány.  
  
 `copy_backward` Algoritmus ukládá přísnější požadavky než algoritmus kopírování. Vstupní i výstupní iterátory musí být obousměrné.  
  
 `copy_backward` a [move_backward](../standard-library/algorithm-functions.md#move_backward) algoritmy jsou pouze standardní knihovna C++ algoritmy určení rozsahu výstup s iterovat odkazující na konci cílový rozsah.  
  
 Vzhledem k tomu, že algoritmus kopie zdrojové elementy v pořadí od posledním elementem, cílový rozsah může dojít k překrytí s zdrojový rozsah zadaný `first` pozici rozsah zdrojových není obsažen v cílové oblasti. `copy_backward`slouží k posunutí prvky vpravo, ale ne levé straně, pokud neexistuje žádné překryv mezi zdrojové a cílové oblasti. Chcete-li posunutí doleva libovolný počet pozic, použijte [kopie](../standard-library/algorithm-functions.md#copy) algoritmus.  
  
 `copy_backward` Algoritmus pouze změní hodnoty ukazuje iterátory, přiřazení nové hodnoty na elementy v cílové oblasti. Nelze ho použít k vytvoření nových prvků a nelze vložit prvky do prázdného zásobníku přímo.  
  
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
  
##  <a name="copy_if"></a>copy_if  
 V rozsahu prvků, zkopíruje prvky, které jsou `true` pro zadanou podmínku.  
  
```  
template<class InputIterator, class OutputIterator, class BinaryPredicate>  
    OutputIterator copy_if(  
        InputIterator first,   
        InputIterator last,  
        OutputIterator dest,  
        Predicate pred);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterator označující začátek rozsahu zkontrolujte podmínku.  
  
 `last`  
 Vstupní iterator, která určuje konec rozsahu.  
  
 `dest`  
 Iterator výstup určující cíl pro zkopírovaný elementy.  
  
 `_Pred`  
 Podmínka, pro kterou je testován každý element v rozsahu. Tato podmínka je poskytovaný objekt uživatelem definované funkce predikátu. Predikát přijímá jeden argument a vrátí `true` nebo `false`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup, který se rovná `dest` zvýší, když pro jednotlivé elementy, splňuje všechny podmínky. Jinými slovy, návratovou hodnotu minus `dest` rovná počet elementů zkopírovaných.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vyhodnotí  
  
 `if (_Pred(*_First + N)) * dest++ = *(_First + N))`  
  
 jednou pro každou `N` v rozsahu `[0, last - first)`, pro výhradně zvýšení hodnoty `N` od nejnižší možná hodnota. Pokud `dest` a `first` určit oblasti úložiště, `dest` nesmí být v rozsahu `[ first, last )`.  
  
##  <a name="copy_n"></a>copy_n  
 Zkopíruje zadaný počet prvků.  
  
```  
template<class InputIterator, class Size, class OutputIterator>  
    OutputIterator copy_n(
        InputIterator first, 
        Size count, 
        OutputIterator dest);  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Vstupní iterator, která určuje, kde kopírovat prvky z.  
  
 `count`  
 Typ podepsaný držitelem nebo bez znaménka celé číslo určující počet elementů pro kopírování.  
  
 `dest`  
 Iterator výstup, která určuje, kde kopírování elementů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí výstupu iterator, kde elementy byly zkopírovány do. Je stejný jako vrácená hodnota třetí parametr `dest`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vyhodnotí `*(dest + N) = *(first + N))` jednou pro každou `N` v rozsahu `[0, count)`, pro výhradně zvýšení hodnoty `N` od nejnižší možná hodnota. Pak vrátí `dest + N`. Pokud `dest` a `first` určit oblasti úložiště, `dest` nesmí být v rozsahu `[first, last)`.  
  
##  <a name="count"></a>počet  
 Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané hodnotě.  
  
```  
template<class InputIterator, class Type> 
    typename iterator_traits<InputIterator>::difference_type count(
        InputIterator first, 
        InputIterator last, 
        const Type& val);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterovat adresování pozice první prvek v rozsahu na Procházet.  
  
 `last`  
 Vstupní iterovat adresování pozici jeden za poslední element v rozsahu na Procházet.  
  
 `val`  
 Hodnota elementy, které se mají spočítat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Typ rozdíl **InputIterator** která vrátí počet prvků v rozsahu [ `first`, `last` ), mají hodnotu `val`.  
  
### <a name="remarks"></a>Poznámky  
 `operator==` Používá k určení shody mezi elementem a zadanou hodnotu musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Tento algoritmus je zobecněn počítat elementy, které splňují všechny predikát funkce šablony [count_if –](../standard-library/algorithm-functions.md#count_if).  
  
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
  
##  <a name="count_if"></a>count_if –  
 Vrátí počet prvků v rozsahu, jejichž hodnoty splňují zadanou podmínku.  
  
```  
template<class InputIterator, class Predicate>
    typename iterator_traits<InputIterator>::difference_type count_if(
        InputIterator first, 
        InputIterator last, 
        Predicate pred);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterovat adresování pozice první prvek v rozsahu prohledávání.  
  
 `last`  
 Vstupní iterovat adresování pozici jeden za poslední element v rozsahu prohledávání.  
  
 `_Pred`  
 Uživatelem definované funkce predikátu objekt, který definuje podmínku, která má uspokojit, pokud je element pro inventarizaci. Predikát jeden argument a vrátí **true** nebo **false**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů, které odpovídají podmínka uvedená v predikátu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce šablony je generalizace algoritmu [počet](../standard-library/algorithm-functions.md#count), nahraďte predikát "je rovno konkrétní hodnotu" s žádné predikátu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_count_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater10(int value)  
{  
    return value >10;  
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
  
##  <a name="equal"></a>stejné  
 Porovná dva rozsahy rovnosti nebo ekvivalenční v smyslu uvedená v binární predikátu elementu elementu.  
  
 Použití `std::equal` při porovnání prvků v kontejneru různé typy (například `vector` a `list`) nebo při porovnávání typů různých elementů, nebo když potřebujete porovnat dílčí rozsahy kontejnerů. Jinak při porovnání prvků stejného typu v stejného typu kontejneru, použijte jiný člen `operator==` poskytované pro každý kontejner.  
  
 Použijte přetížení duální rozsahy v C ++ 14 kódu, protože přetížení, která trvat jenom jeden iterator pro druhého rozsahu nerozpozná rozdíly, pokud je delší, než je první rozsah druhého rozsahu a způsobí nedefinované chování, pokud je kratší druhého rozsahu než první rozsah.  
  
```  
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
 `First1`  
 Vstupní iterovat adresování pozice první prvek v první oblasti, která má být testována.  
  
 `Last1`  
 Vstupní iterovat adresování pozice, jedna po posledním prvkem v první oblasti, která má být testována.  
  
 `First2`  
 Vstupní iterovat adresování pozice první prvek v druhého rozsahu má být testována.  
  
 `First2`  
 Vstupní iterovat adresování pozice jednoho po posledním prvkem v druhého rozsahu má být testována.  
  
 `Comp`  
 Uživatelem definované funkce predikátu objekt, který definuje podmínku, která má být splněny, pokud dva elementy musí být odebrána jako ekvivalentní. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** jenom v případě rozsahy jsou identické nebo ekvivalentní pod binární predikát srovnání elementu pomocí elementu; v opačném **false**.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah má proběhnout, musí být platná; musí být všechny iterátory dereferenceable a je dostupný z první poslední pozice podle Inkrementace.  
  
 Pokud jsou dva rozsahy stejnou délku, složitost čas algoritmu je lineární počet elementů obsažených v rozsahu. V opačném případě okamžitě funkce vrátí `false`.  
  
 Ani `operator==` ani predikát uživatelem definované je potřeba použít ekvivalenční vztah to symetrický, reflexivní a přenositelné mezí jejími operandy.  
  
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
  
##  <a name="equal_range"></a>equal_range –  
 Zadaný rozsah seřazený vyhledá Podoblast sady, ve kterém jsou všechny elementy ekvivalentní zadanou hodnotu.  
  
```  
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
 `first`  
 Předat dál iterator adresování pozice první prvek v rozsahu prohledávání.  
  
 `last`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu prohledávání.  
  
 `val`  
 Hodnota vyhledána v seřazené rozsahu.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém jeden element je menší než jiné.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pár dopředného iterátory, které určují Podoblast sady, obsažené v rozsahu vyhledávat, ve kterých jsou všechny prvky ekvivalentní `val` v tom smyslu, definované binární predikát použít (buď `comp` nebo výchozí, méně – než).  
  
 Pokud odpovídají žádné elementy v rozsahu `val`, vrácený dvojice dopředného iterátory jsou si rovny a určete bod, kde `val` může být vložen bez narušení pořadí rozsahu.  
  
### <a name="remarks"></a>Poznámky  
 První iterator dvojic vrácená algoritmem je [lower_bound –](../standard-library/algorithm-functions.md#lower_bound), a druhá iterator [upper_bound –](../standard-library/algorithm-functions.md#upper_bound).  
  
 Rozsah musí být seřazeny podle predikát poskytované `equal_range`. Například, pokud se chystáte použít delší – než predikátu, musí být v rozsahu seřazeny v sestupném pořadí.  
  
 Elementy v pravděpodobně prázdná Podoblast sady definované dvojice iterátory vrácený `equal_range` bude ekvivalentní `val` v tom smyslu, definované predikát použít.  
  
 Složitost algoritmu je logaritmické pro iterátory náhodný přístup a lineární, jinak se počet kroků úměrná ( `last`  -  `first`).  
  
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
  
template<class T> void dump_vector( const vector<T>& v, pair< typename vector<T>::iterator, typename vector<T>::iterator > range )  
{  
    // prints vector v with range delimited by [ and ]  
  
    for( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )  
    {  
        if( i == range.first )  
        {  
            cout << "[ ";  
        }  
        if( i == range.second )  
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
    for( vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )  
    {  
        cout << *i << " ";  
    }  
    cout << endl << endl;  
  
    pair< vector<T>::iterator, vector<T>::iterator > result  
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
    for( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )  
    {  
        cout << *i << " ";  
    }  
    cout << endl << endl;  
  
    pair< typename vector<T>::iterator, typename vector<T>::iterator > result  
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
    for( int i = -1; i <= 4; ++i )  
    {  
        v1.push_back(i);  
    }  
  
    for( int i =-3; i <= 0; ++i )  
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
  
##  <a name="fill"></a>výplně  
 Každému prvku v zadaném rozsahu přiřadí stejnou novou hodnotu.  
  
```  
template<class ForwardIterator, class Type>  
void fill(
    ForwardIterator first, 
    ForwardIterator last, 
    const Type& val);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Předat dál iterator adresování pozice první prvek v rozsahu na Procházet.  
  
 `last`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu na Procházet.  
  
 `val`  
 Hodnota, která má být přiřazena k prvkům v rozsahu [ `first`, `last`).  
  
### <a name="remarks"></a>Poznámky  
 Cílový rozsah musí být platná; všechny ukazatele musí být dereferenceable a je dostupný z první poslední pozice podle Inkrementace. Složitost je lineární s velikostí rozsahu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_fill.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( )   
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
  
##  <a name="fill_n"></a>fill_n  
 Přiřadí novou hodnotu na zadaný počet elementů v rozsahu od jazyka.  
  
```  
template<class OutputIterator, class Size, class Type>  
OutputIterator fill_n(
    OutputIterator First, 
    Size Count, 
    const Type& Val);   
```  
  
### <a name="parameters"></a>Parametry  
 `First`  
 Výstup iterovat adresování pozice první prvek v rozsahu přiřazení hodnota `Val`.  
  
 `Count`  
 Typ podepsaný držitelem nebo bez znaménka celé číslo určující počet elementů přiřadit hodnotu.  
  
 `Val`  
 Hodnota, která má být přiřazena k prvkům v rozsahu [ `First`, *první + počet*).  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud se naplní iterovat k elementu, který odpovídá posledním elementem `Count` > nula, v opačném případě první prvek.  
  
### <a name="remarks"></a>Poznámky  
 Cílový rozsah musí být platná; všechny ukazatele musí být dereferenceable a je dostupný z první poslední pozice podle Inkrementace. Složitost je lineární s velikostí rozsahu.  
  
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
  
##  <a name="find"></a>Najít  
 Vyhledá pozici prvního výskytu prvku v rozsahu, který má zadanou hodnotu.  
  
```  
template<class InputIterator, class T>  
InputIterator find(
    InputIterator first, 
    InputIterator last,   
    const T& val);  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Vstupní iterovat adresování pozice první prvek v rozsahu má být vyhledán zadanou hodnotu.  
  
 `last`  
 Vstupní iterovat adresování pozici jeden za poslední element v rozsahu má být vyhledán zadanou hodnotu.  
  
 `val`  
 Hodnota, která má být vyhledán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vstupní iterovat adresování první výskyt zadané hodnotě v prohledávaný rozsah. Pokud nebyl nalezen žádný prvek s hodnotou ekvivalentní, vrátí `last`.  
  
### <a name="remarks"></a>Poznámky  
 `operator==` Používá k určení shody mezi elementem a zadanou hodnotu musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Pro příklad kódu pomocí `find()`, najdete v části [find_if –](../standard-library/algorithm-functions.md#find_if).  
  
##  <a name="find_end"></a>find_end –  
 Vyhledá v rozsahu poslední dílčí sekvenci, která je shodná se zadanou sekvencí nebo která je ekvivalentní ve smyslu určeném binárním predikátem.  
  
```  
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
 `First1`  
 Předat dál iterator adresování pozice první prvek v rozsahu prohledávání.  
  
 `Last1`  
 Předat dál iterator adresování pozici jeden po posledním prvkem v rozsahu prohledávání.  
  
 `First2`  
 Předat dál iterator adresování pozice první prvek v rozsahu pro vyhledávání.  
  
 `Last2`  
 Předat dál iterator adresování pozici jeden po posledním prvkem v rozsahu pro vyhledávání.  
  
 `Comp`  
 Uživatelem definované funkce predikátu objekt, který definuje podmínku, která má být splněny, pokud dva elementy musí být odebrána jako ekvivalentní. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator adresování pozice první prvek poslední dalším v rámci [First1, Last1) odpovídající zadané pořadí [First2, Příjmení2).  
  
### <a name="remarks"></a>Poznámky  
 `operator==` Používá k určení shody mezi elementem a zadanou hodnotu musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Rozsahy odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci každé pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
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
  
int main( )  
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
  
##  <a name="find_first_of"></a>find_first_of –  
 Vyhledá první výskyt jedné z několika hodnot v cílovém rozsahu nebo první výskyt jednoho z několika prvků, které jsou ekvivalentní ve smyslu určeném binárním predikátem zadané sadě prvků.  
  
```  
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
  `first1`  
 Předat dál iterator adresování pozice první prvek v rozsahu prohledávání.  
  
 `last1`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu prohledávání.  
  
  `first2`  
 Předat dál iterator adresování pozice první prvek v rozsahu lze porovnat.  
  
 `last2`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu lze porovnat.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje podmínku, která má být splněny, pokud dva elementy musí být odebrána jako ekvivalentní. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator adresování pozice první prvek první dalším, který odpovídá zadané pořadí nebo které je ekvivalentní v smyslu uvedená v binární predikátu.  
  
### <a name="remarks"></a>Poznámky  
 `operator==` Používá k určení shody mezi elementem a zadanou hodnotu musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Rozsahy odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci každé pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
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
  
int main( )  
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
  
##  <a name="find_if"></a>find_if –  
 Vyhledá pozici prvního výskytu prvku v rozsahu, který splňuje zadanou podmínku.  
  
```  
template<class InputIterator, class Predicate>  
InputIterator find_if(
    InputIterator first, 
    InputIterator last, 
    Predicate pred);  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Vstupní iterovat adresování pozice první prvek v rozsahu prohledávání.  
  
 `last`  
 Vstupní iterovat adresování pozici jeden za poslední element v rozsahu prohledávání.  
  
 `pred`  
 Uživatelem definované funkce predikátu objekt nebo [výrazu lambda](../cpp/lambda-expressions-in-cpp.md) , který definuje podmínku, která má vyhovět prohledávaný pro element. Predikát jeden argument a vrátí `true` (uspokojit) nebo `false` (nejsou splněné). Podpis `pred` musí být efektivně `bool pred(const T& arg);`, kde `T` je typu, na kterou `InputIterator` lze implicitně převést při Zrušením odkazu. `const` – Klíčové slovo se zobrazí pouze k objasnění, že objekt funkce nebo lambda neměli upravovat argument.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vstupní iterator, který odkazuje na prvním elementem v rozsahu, který splňuje podmínka uvedená v predikátu (výsledkem predikát `true`). Pokud nebyl nalezen žádný prvek vyhovět predikátu, vrátí `last`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce šablony je generalizace algoritmu [najít](../standard-library/algorithm-functions.md#find), nahraďte predikát "je rovno konkrétní hodnotu" s žádné predikátu. Logická negace (Najít první prvek, který nesplňuje predikát), najdete v tématu [find_if_not –](../standard-library/algorithm-functions.md#find_if_not).  
  
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
  
##  <a name="find_if_not"></a>find_if_not –  
 Vrátí první prvek v zadaném rozsahu, který nesplňuje podmínku.  
  
```  
template<class InputIterator, class Predicate>  
InputIterator find_if_not(
    InputIterator first, 
    InputIterator last,   
    Predicate pred);  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Vstupní iterovat adresování pozice první prvek v rozsahu prohledávání.  
  
 `last`  
 Vstupní iterovat adresování pozici jeden za poslední element v rozsahu prohledávání.  
  
 `pred`  
 Uživatelem definované funkce predikátu objekt nebo [výrazu lambda](../cpp/lambda-expressions-in-cpp.md) , který definuje podmínku, která má nelze uspokojit prohledávaný pro element. Predikát jeden argument a vrátí `true` (uspokojit) nebo `false` (nejsou splněné). Podpis `pred` musí být efektivně `bool pred(const T& arg);`, kde `T` je typu, na kterou `InputIterator` lze implicitně převést při Zrušením odkazu. `const` – Klíčové slovo se zobrazí pouze k objasnění, že objekt funkce nebo lambda neměli upravovat argument.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vstupní iterator, který odkazuje na prvním elementem v rozsahu, který nesplňuje podmínka uvedená v predikátu (výsledkem predikát `false`). Pokud predikát splňují všechny elementy (výsledkem predikát `true` pro každý element), vrátí `last`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce šablony je generalizace algoritmu [najít](../standard-library/algorithm-functions.md#find), nahraďte predikát "je rovno konkrétní hodnotu" s žádné predikátu. Logická negace (Najít první prvek, který uspokojení predikát), najdete v tématu [find_if –](../standard-library/algorithm-functions.md#find_if).  
  
 Příklad kódu snadno přizpůsobitelné k `find_if_not()`, najdete v části [find_if –](../standard-library/algorithm-functions.md#find_if).  
  
##  <a name="for_each"></a>for_each –  
 Na každý prvek v pořadí dopředu v rozsahu použije zadaný objekt funkce a vrátí objekt funkce.  
  
```  
template<class InputIterator, class Function>  
Function for_each(
    InputIterator first, 
    InputIterator last, 
    Function _Func);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterovat adresování pozice první prvek v rozsahu ho zpracovat.  
  
 `last`  
 Zpracovat vstupní iterovat adresování pozici jeden za poslední element v rozsahu.  
  
 `_Func`  
 Uživatelem definované funkce objekt, který se použije pro každý prvek v rozsahu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopie objektu funkce po jeho použití na všechny elementy v rozsahu.  
  
### <a name="remarks"></a>Poznámky  
 Algoritmus `for_each` je velmi flexibilní, umožňuje úpravy jednotlivých prvků v rozsahu způsoby jiný, zadaného uživatelem. Šablonou funkce mohou být znovu použity ve formě modifikovaných předáním různé parametry. Uživatelem definované funkce může shromažďují informace v rámci vnitřní stav, které algoritmus může vrátit po zpracování všech elementů v rozsahu.  
  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v pořadí, poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Složitost je lineární s maximálně ( `last`  -   `first`) porovnání.  
  
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
   void operator ( ) ( Type& elem ) const  
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
   Average ( ) : num ( 0 ) , sum ( 0 )  
   {  
   }  
  
   // The function call to process the next elment  
   void operator ( ) ( int elem ) \  
   {  
      num++;      // Increment the element count  
      sum += elem;   // Add the value to the partial sum  
   }  
  
   // return Average  
   operator double ( )  
   {  
      return  static_cast <double> (sum) /  
      static_cast <double> (num);  
   }  
};  
  
int main( )  
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
   for_each ( v1.begin ( ) , v1.end ( ) , MultValue<int> ( -2 ) );  
  
   cout << "Multiplying the elements of the vector v1\n "  
        <<  "by the factor -2 gives:\n v1mod1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // The function object is templatized and so can be  
   // used again on the elements with a different Factor  
   for_each (v1.begin ( ) , v1.end ( ) , MultValue<int> (5 ) );  
  
   cout << "Multiplying the elements of the vector v1mod\n "  
        <<  "by the factor 5 gives:\n v1mod2 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // The local state of a function object can accumulate  
   // information about a sequence of actions that the  
   // return value can make available, here the Average  
   double avemod2 = for_each ( v1.begin ( ) , v1.end ( ) ,  
      Average ( ) );  
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
  
##  <a name="generate"></a>Generovat  
 Přiřadí hodnoty generované objektem funkce každému prvku v rozsahu.  
  
```  
template<class ForwardIterator, class Generator>  
void generate(
    ForwardIterator first, 
    ForwardIterator last, 
    Generator _Gen);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Předat dál iterator adresování pozice první prvek v rozsahu, ke které se mají přiřadit hodnoty.  
  
 `last`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu, ke které se mají přiřadit hodnoty.  
  
 `_Gen`  
 Objekt funkce která je volána bez argumentů používaný ke generování hodnot jednotlivých prvků v rozsahu přiřazení.  
  
### <a name="remarks"></a>Poznámky  
 Objekt funkce je volána pro každý prvek v rozsahu a není potřeba vrací stejnou hodnotu pokaždé, když je volána. Může, například čtení ze souboru nebo odkazovat na a upravit místní stavu. Typ výsledku použití generátoru musí být převoditelná na typ hodnoty dopředného iterátory pro rozsah.  
  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v pořadí, poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Složitost je lineární s přesně ( `last`  -   `first`) volání generátor nich vyžaduje.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_generate.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Assigning random values to vector integer elements  
   vector <int> v1 ( 5 );  
   vector <int>::iterator Iter1;  
   deque <int> deq1 ( 5 );  
   deque <int>::iterator d1_Iter;  
  
   generate ( v1.begin ( ), v1.end ( ) , rand );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Assigning random values to deque integer elements  
   generate ( deq1.begin ( ), deq1.end ( ) , rand );  
  
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
  
##  <a name="generate_n"></a>generate_n –  
 Přiřadí hodnoty generované funkce objektu na zadaný počet elementů v rozsahu a vrátí do pozice, jeden za poslední přiřazenou hodnotu.  
  
```  
template<class OutputIterator, class Diff, class Generator>  
void generate_n( 
    OutputIterator First, 
    Diff Count, 
    Generator Gen);  
```  
  
### <a name="parameters"></a>Parametry  
 `First`  
 Iterátor výstup adresování pozice první prvek v rozsahu, ke které se mají přiřadit hodnoty.  
  
 `Count`  
 Typ podepsaný držitelem nebo bez znaménka celé číslo určující počet elementů k jí přiřadit hodnotu generátor funkce.  
  
 `Gen`  
 Objekt funkce která je volána bez argumentů používaný ke generování hodnot jednotlivých prvků v rozsahu přiřazení.  
  
### <a name="remarks"></a>Poznámky  
 Objekt funkce je volána pro každý prvek v rozsahu a není potřeba vrací stejnou hodnotu pokaždé, když je volána. Může, například čtení ze souboru nebo odkazovat na a upravit místní stavu. Typ výsledku použití generátoru musí být převoditelná na typ hodnoty dopředného iterátory pro rozsah.  
  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v pořadí, poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Složitost je lineární s přesně `Count` volání generátor nich vyžaduje.  
  
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
  
##  <a name="includes"></a>zahrnuje  
 Ověřuje, zda jeden seřazený rozsah obsahuje všechny prvky obsažené ve druhém seřazeném rozsahu, kde kritérium pořadí nebo ekvivalence mezi prvky může být určeno binárním predikátem.  
  
```  
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
  `first1`  
 Vstupní iterovat adresování pozice první prvek v první dva seřazené zdrojových oblastí má být testována pro zda jsou všechny elementy druhého obsažené v prvním.  
  
 `last1`  
 Vstupní iterovat adresování pozici jeden za posledním elementem v první dva rozsahy seřazené zdroje k testování na tom, jestli jsou všechny elementy druhého obsažené v prvním.  
  
  `first2`  
 Vstupní iterovat adresování pozice první prvek za sekundu ze dvou po sobě jdoucích seřazené rozsahy zdroje pro testování na tom, jestli jsou všechny elementy druhého obsažené v prvním.  
  
 `last2`  
 Vstupní iterovat adresování jednoho pozice za posledním elementem za sekundu může být v rozmezí dvou po sobě jdoucích seřazené zdroje k testování na tom, jestli jsou všechny elementy druhého obsažené v prvním.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém jeden element je menší než jiné. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud první seřazené oblasti obsahuje všechny elementy ve druhé seřazené oblasti; jinak **false**.  
  
### <a name="remarks"></a>Poznámky  
 Dalším způsobem zamyslet nad tento test je, aby zjistil, zda druhý zdrojový rozsah je podmnožinou první zdrojový rozsah.  
  
 Seřazené zdrojových oblastí odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci každé pořadí poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Rozsahy musí každý být uspořádány jako předběžné podmínky k použití algoritmus zahrnuje v souladu s stejné řazení jako seřazená zdrojové se má použít algoritmem seřadit kombinované rozsahy.  
  
 Zdrojových oblastí se nemění algoritmem **sloučení**.  
  
 Typy hodnot ze vstupních iterátory musí být menší – než porovnatelný seřadit, tak, aby hodnotě dva elementy, může být bylo zjištěno, že jsou ekvivalentní (v tom smyslu, že ani je menší než druhá) nebo jedna je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Přesněji řečeno algoritmus ověřuje, zda mají všechny elementy v první seřazené oblasti v rámci zadaného predikátu Binární ekvivalentní řazení ty druhé seřazené oblasti.  
  
 Složitost algoritmu je lineární s maximálně 2 \* (( *Příjmení1 - first1*) – (* Příjmení2 - first2 *)) – 1 porovnání pro neprázdná zdrojových oblastí.  
  
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
  
int main( )  
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
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b );  
   vector <int>::iterator Iter2a,  Iter2b;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
   v2a.pop_back ( );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is v2a = ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is v2b = ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ;  
   vector <int>::iterator Iter3a, Iter3b;  
   reverse (v3a.begin( ), v3a.end( ) );  
   v3a.pop_back ( );  
   v3a.pop_back ( );  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is v3a = ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        <<  "binary predicate mod_lesser is v3b = ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To test for inclusion under an asscending order  
   // with the default binary predicate less <int> ( )  
   bool Result1;  
   Result1 = includes ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) );  
   if ( Result1 )  
      cout << "All the elements in vector v1b are "  
           << "contained in vector v1a." << endl;  
   else  
      cout << "At least one of the elements in vector v1b "  
           << "is not contained in vector v1a." << endl;  
  
   // To test for inclusion under descending  
   // order specify binary predicate greater<int>( )  
   bool Result2;  
   Result2 = includes ( v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) , greater <int> ( ) );  
   if ( Result2 )  
      cout << "All the elements in vector v2b are "  
           << "contained in vector v2a." << endl;  
   else  
      cout << "At least one of the elements in vector v2b "  
           << "is not contained in vector v2a." << endl;  
  
   // To test for inclusion under a user  
   // defined binary predicate mod_lesser  
   bool Result3;  
   Result3 = includes ( v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , mod_lesser );  
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
  
##  <a name="inplace_merge"></a>inplace_merge  
 Kombinuje prvky ze dvou po sobě následujících seřazených rozsahů do jednoho seřazeného rozsahu, kde kritérium pořadí může být určeno binárním predikátem.  
  
```  
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
  `first`  
 Obousměrné iterator, adresování pozice první prvek v první ze dvou po sobě jdoucích seřazené rozsahy kombinaci a do jednoho rozsahu seřazeny.  
  
 `middle`  
 Obousměrné iterator, adresování pozice první prvek za sekundu ze dvou po sobě jdoucích seřazené rozsahy kombinaci a do jednoho rozsahu seřazeny.  
  
 `last`  
 Obousměrné iterator, adresování pozici jeden za posledním elementem za sekundu ze dvou po sobě jdoucích seřazené rozsahy kombinaci a do jednoho rozsahu seřazeny.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém je větší než druhý jeden element. Binární predikát má dva argumenty a by měla vrátit **true** při prvním elementem je menší než druhý prvkem a **false** jinak.  
  
### <a name="remarks"></a>Poznámky  
 Seřazené po sobě jdoucích rozsahy odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci každé pořadí poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Seřazené po sobě jdoucích rozsahy musí každý být uspořádány podmínkou pro použití `inplace_merge` algoritmus v souladu s stejné řazení jako má být použita algoritmem seřadit kombinované rozsahy. Operace je stabilní jako relativní pořadí prvků v každém rozsahu uchování. Když jsou v obou zdrojových oblastí ekvivalentní elementy, je element že první oblasti, která předchází element ze druhý v kombinovaném rozsahu.  
  
 Složitost závisí na dostupné paměti, jak algoritmus přidělí paměť do vyrovnávací paměti. Pokud je k dispozici dostatek paměti, je nejlepší případ Lineární s (* poslední - nejprve*) – 1 porovnání; Pokud je k dispozici žádné pomocného paměti, je nejhorším případě *N* protokolu *(ne)*, kde  *N* = (* poslední - nejprve*).  
  
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
  
int main( )  
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
   break2 = find ( v2.begin ( ) , v2.end ( ) , -5 );  
   sort ( v2.begin ( ) , break2 , greater<int> ( ) );  
   sort ( break2 , v2.end ( ) , greater<int> ( ) );  
   cout << "Original vector v2 with subranges sorted by the\n "  
        << "binary predicate greater is v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Constructing vector v3 with ranges sorted by mod_lesser  
   vector <int> v3 ( v1 );  
   vector <int>::iterator break3;  
   break3 = find ( v3.begin ( ) , v3.end ( ) , -5 );  
   sort ( v3.begin ( ) , break3 , mod_lesser );  
   sort ( break3 , v3.end ( ) , mod_lesser );  
   cout << "Original vector v3 with subranges sorted by the\n "  
        << "binary predicate mod_lesser is v3 = ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
  
   vector <int>::iterator break1;  
   break1 = find (v1.begin ( ) , v1.end ( ) , -5 );  
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
  
##  <a name="is_heap"></a>is_heap  
 Vrátí `true` Pokud haldy formuláři elementů v zadaném rozsahu.  
  
```  
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
  `first`  
 Iterator náhodný přístup, označující začátek rozsahu zkontrolujte haldy.  
  
 `last`  
 Iterator náhodný přístup, která určuje konec rozsahu.  
  
 `comp`  
 Podmínku, kterou chcete testovat na elementy pořadí. Predikát binární přijímá jeden argument a vrátí `true` nebo `false`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `true` Pokud elementů v zadaném rozsahu formuláři na haldu `false` Pokud tomu tak není.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí první funkce šablony [is_heap_until –](../standard-library/algorithm-functions.md#is_heap_until) `(` `first ,` `last ) ==` `last`.  
  
 Vrátí druhou funkce šablony  
  
 `is_heap_until` `(`  `first` `,`  `last` `,`  `comp` `) ==`  `last`.  
  
##  <a name="is_heap_until"></a>is_heap_until –  
 Vrátí iterovat umístěný na prvním elementem v rozsahu [ `begin`, `end`) nevyhovuje haldě řazení podmínku, nebo `end` Pokud rozsahu forms haldy.  
  
```  
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
 `begin`  
 Iterator náhodný přístup, který určuje první prvek oblasti tak, aby kontrolovat haldy.  
  
 `end`  
 Iterator náhodný přístup, který určuje konec rozsahu zkontrolujte haldy.  
  
 `compare`  
 Predikát binární, který určuje striktní weak řazení podmínku, která definuje haldy. Výchozí hodnota predikátu při `compare` není zadán je `std::less<>`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `end` Pokud zadaný rozsah forms haldy nebo obsahuje jeden nebo méně elementů. V opačném případě vrátí iterace pro první prvek bylo zjištěno, který nesplňuje podmínky haldy.  
  
### <a name="remarks"></a>Poznámky  
 První šablona funkce vrací poslední iterator `next` v `[ begin , end ]` kde `[ begin , next)` je haldy seřazené podle objekt funkce `std::less<>`. Pokud vzdálenost `end - begin < 2`, funkce vrátí hodnotu `end`.  
  
 Druhá šablona funkce se chová stejně jako první, s tím rozdílem, že používá predikát `compare` místo `std::less<>` jako haldě řazení podmínku.  
  
##  <a name="is_partitioned"></a>is_partitioned  
 Vrátí `true` Pokud všechny elementy v daném rozsahu, který testovací `true` pro podmínku dřívější než žádné elementy, které testovací `false`.  
  
```  
template<class InputIterator, class BinaryPredicate>  
bool is_partitioned(  
    InputIterator first,   
    InputIterator last,  
    BinaryPredicate comp);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterator, která určuje, kde rozsah začne u podmínek.  
  
 `last`  
 Vstupní iterator, která určuje konec rozsahu.  
  
 `comp`  
 Podmínky, které chcete otestovat. To zajišťuje uživatelem definované funkce predikátu objekt, který definuje podmínku, která má vyhovět prohledávaný pro element. Predikát přijímá jeden argument a vrátí `true` nebo `false`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true, pokud všechny elementy v daném rozsahu, které testovací `true` pro podmínku dřívější než žádné elementy, které testovací `false`a v opačném případě vrátí `false`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí `true` pouze v případě všechny elementy ve `[` `first ,` `last )` jsou rozděleny do oddílů pomocí `comp`; to znamená, že všechny elementy `X` v `[` `first ,` `last )` pro které `comp (X)` je nastavena hodnota true předcházet všechny elementy `Y` pro kterou `comp (Y)` je `false`.  
  
##  <a name="is_permutation"></a>is_permutation  
 Vrátí hodnotu true, pokud obě rozsahy obsahují stejné prvky, zda jsou elementy ve stejném pořadí. Použijte přetížení duální rozsahy v C ++ 14 kódu, protože přetížení, která trvat jenom jeden iterator pro druhého rozsahu nerozpozná rozdíly, pokud je delší, než je první rozsah druhého rozsahu a způsobí nedefinované chování, pokud je kratší druhého rozsahu než první rozsah.  
  
```  
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
 `First1`  
 Iterator předat dál, která odkazuje na první prvek rozsahu.  
  
 `Last1`  
 Iterator předat dál, který odkazuje jeden za posledním elementem rozsahu.  
  
 `First2`  
 Iterator předat dál, která odkazuje na první prvek druhého rozsahu, použít pro porovnání.  
  
 `Last2`  
 Iterator předat dál, která odkazuje na jeden za posledním elementem druhého rozsahu, použít pro porovnání.  
  
 `Pred`  
 Predikát, který testů pro ekvivalenční a vrátí `bool`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud lze vyjádřit rozsahy tak, aby byly identické podle komparátoru predikát; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 `is_permutation`v nejhorším případě má kvadratické složitost.  
  
 První funkce šablony předpokládá, že jsou v rozsahu počínaje tolik elementy `First2` , protože v rozsahu určený hodnotou [ `First1`, `Last1`). Pokud jsou v druhého rozsahu další elementy, jsou ignorovány; Pokud je menší, nedefinované chování. Třetí šablony funkce (C ++ 14 a novější) neprovede tento předpokladů.  Obě vrací `true` pouze tehdy, pokud pro každý prvek X v rozsahu určený hodnotou [ `First1`, `Last1`) existuje tolik prvků Y ve stejném rozsahu, pro které X == Y, protože jsou v rozsahu počínaje `First2` nebo [ `First2, Last2).` tady, `operator==` pairwise porovnání mezí jejími operandy, musíte provést.  
  
 Funkce šablony druhé a čtvrté chovají stejně, s tím rozdílem, že nahrazují `operator==(X, Y)` s `Pred(X, Y)`. Chovat správně, musí být predikát symetrický, reflexivní a přenositelné.  
  
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
  
##  <a name="is_sorted"></a>is_sorted  
 Vrátí `true` Pokud elementů v zadaném rozsahu seřazená.  
  
```  
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
  `first`  
 Iterator předat dál, která určuje, kde začíná rozsahu ke kontrole.  
  
 `last`  
 Iterator předat dál, která určuje konec rozsahu.  
  
 `comp`  
 Podmínky pro testování k určení pořadí mezi dvěma prvky. Predikát přijímá jeden argument a vrátí `true` nebo `false`. Provede stejnou úlohu jako `operator<`.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí první funkce šablony [is_sorted_until –](http://msdn.microsoft.com/en-us/bbad99d0-deaa-4fe6-ae58-eb5b3e4dded0)`( first, last ) == last`. `operator<` Funkce provede porovnání pořadí.  
  
 Vrátí druhou funkce šablony `is_sorted_until( first, last , comp ) == last`. `comp` Funkce predikátu provede porovnání pořadí.  
  
##  <a name="is_sorted_until"></a>is_sorted_until –  
 Vrátí `ForwardIterator` , která je nastavena na poslední element, který je seřazená ze zadaného rozsahu.  
  
 Druhá verze vám umožňuje zadat `BinaryPredicate` funkci, která vrací `true` při dané dva elementy jsou seřazené podle a `false` jinak.  
  
```  
template<class ForwardIterator>  
    ForwardIterator is_sorted_until(  
        ForwardIterator first,   
        ForwardIterator last  
    );  
template<class ForwardIterator, class BinaryPredicate>  
    ForwardIterator is_sorted_until(  
        ForwardIterator first,   
        ForwardIterator last,   
        BinaryPredicate comp  
    );  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator předat dál, která určuje, kde začíná rozsahu ke kontrole.  
  
 `last`  
 Iterator předat dál, která určuje konec rozsahu.  
  
 `comp`  
 Podmínky pro testování k určení pořadí mezi dvěma prvky. Predikát přijímá jeden argument a vrátí `true` nebo `false`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `ForwardIterator` nastavena na poslední element seřazená. Seřazené pořadí spustí z `first`.  
  
### <a name="remarks"></a>Poznámky  
 První šablona funkce vrací poslední iterator `next` v `[` `first ,` `last ]` tak, aby `[` `first , next)` je seřazená posloupnost seřazené podle `operator<`. Pokud `distance()` `< 2` funkce vrátí hodnotu `last`.  
  
 Druhá šablona funkce se chová stejně, s tím rozdílem, že se nahradí `operator<(X, Y)` s `comp (X, Y)`.  
  
##  <a name="iter_swap"></a>iter_swap –  
 Vymění dvě hodnoty odkazované dvojicí zadaných iterátorů.  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
void iter_swap( ForwardIterator1 left, ForwardIterator2 right );  
  
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Jeden z dopředného iterátory, jehož hodnota je k výměně.  
  
 `right`  
 Druhý dopředného iterátory, jehož hodnota je k výměně.  
  
### <a name="remarks"></a>Poznámky  
 `swap`má být použit v preference k i **ter_swap**, který je zahrnutý ve verzi Standard C++ pro zpětnou kompatibilitu. Pokud `Fit1` a `Fit2` dopředného iterátory, jsou pak `iter_swap` ( `Fit1`, `Fit2` ), je ekvivalentní `swap` (* `Fit1`, \* `Fit2` ).  
  
 Hodnota typy vstupní dopředného iterátory musí mít stejnou hodnotu.  
  
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
  
int main( )  
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
   iter_swap ( deq1.begin ( ) , --deq1.end ( ) );  
  
   cout << "The deque of CInts with first & last elements swapped is:\n deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl;  
  
   // Swapping back first and last elements with swap  
   swap ( *deq1.begin ( ) , *(deq1.end ( ) -1 ) );  
  
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
  
   iter_swap ( v1.begin ( ) , deq2.begin ( ) );  
  
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
  
##  <a name="lexicographical_compare"></a>lexicographical_compare –  
 Porovná prvek po prvku mezi dvěma sekvencemi k určení, která z nich je menší.  
  
```  
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
  `first1`  
 Vstupní iterovat adresování pozice první prvek v první oblasti, která být porovnána.  
  
 `last1`  
 Vstupní iterovat adresování pozici jeden za poslední element v první oblasti, která být porovnána.  
  
  `first2`  
 Vstupní iterovat adresování pozice první prvek v druhého rozsahu být porovnána.  
  
 `last2`  
 Vstupní iterovat adresování pozici jeden za poslední element v druhého rozsahu být porovnána.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém jeden element je menší než jiné. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud první je rozsah lexicographically menší než druhého rozsahu; v opačném případě **false**.  
  
### <a name="remarks"></a>Poznámky  
 Lexicographical porovnání mezi pořadí porovná je elementu pomocí elementu dokud:  
  
-   Najde odpovídající dva elementy nerovné a výsledek jejich porovnání se provede na základě porovnání mezi pořadí.  
  
-   Nebyly nalezeny žádné nerovnosti, ale jeden sekvence má více elementů než druhý a je kratší pořadí je považováno za méně než delší pořadí.  
  
-   Nebyly nalezeny žádné nerovnosti a pořadí mít stejný počet elementů a proto jsou stejné pořadí a je výsledkem porovnání hodnota false.  
  
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
  
int main( )  
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
  
##  <a name="lower_bound"></a>lower_bound –  
 Najde pozici prvního prvku v seřazeném rozsahu, jehož hodnota je větší nebo rovna zadané hodnotě, kde kritérium pořadí může být určeno primárním predikátem.  
  
```  
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
 `first`  
 Předat dál iterator adresování pozice první prvek v rozsahu prohledávání.  
  
 `last`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu prohledávání.  
  
 `value`  
 Hodnota, jejíž první pozici nebo možné první pozici je hledán v seřazené rozsahu.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém jeden element je menší než jiné. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator na pozici prvního prvku v zadaného rozsahu s hodnotou, která je větší než nebo rovná zadanou hodnotou, tam, kde je zadán rovnocennosti s binárním predikátem.  
  
### <a name="remarks"></a>Poznámky  
 Seřazené zdrojový rozsah odkazuje musí být platná; musí být všechny iterátory dereferenceable a v rámci pořadí poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Seřazené oblasti je předběžné podmínky použití `lower_bound` a kde řazení je stejný jako zadaný pomocí binárního predikátu.  
  
 Rozsah se nemění algoritmem `lower_bound`.  
  
 Typy hodnot dopředného iterátorů musí být menší – než porovnatelný seřadit, tak, aby hodnotě dva elementy, může být bylo zjištěno, že jsou ekvivalentní (v tom smyslu, že ani je menší než druhá) nebo jedna je menší než druhý. To vede řazení mezi nonequivalent elementy  
  
 Složitost algoritmu je logaritmické pro iterátory náhodný přístup a lineární, jinak se počet kroků úměrná ( `last - first`).  
  
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
  
int main( )  
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
  
##  <a name="make_heap"></a>make_heap –  
 Převede prvky ze zadaného rozsahu do haldy, ve které je první prvek největší a pro kterou může být kritérium řazení určeno binárním predikátem.  
  
```  
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
  `first`  
 Adresování pozice první prvek v rozsahu, který má být převeden na haldu iterator náhodný přístup.  
  
 `last`  
 Adresování jednoho pozice po posledním element v rozsahu, který má být převeden na haldu iterator náhodný přístup.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém jeden element je menší než jiné. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="remarks"></a>Poznámky  
 Haldách mít dvě vlastnosti:  
  
-   První prvek je vždy na největší.  
  
-   Elementy může přidat nebo odebrat logaritmické včas.  
  
 Haldách jsou nejvhodnější způsob implementace priority fronty a jejich použití k implementaci adaptéru kontejneru standardní knihovna C++ [priority_queue – třída](../standard-library/priority-queue-class.md).  
  
 Složitost je lineární, které vyžadují 3 \* (* poslední - nejprve *) porovnání.  
  
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
  
##  <a name="max"></a>maximální počet  
 Porovná dva objekty a vrátí větší z nich, kde kritérium pořadí může být určeno binárním predikátem.  
  
```  
template<class Type>  
    const Type& max(  
        const Type& left,   
        const Type& right  
    );  
template<class Type, class Pr>  
    const Type& max(  
        const Type& left,   
        const Type& right,  
        BinaryPredicate comp  
    );  
template<class Type>   
    Type& max (  
        initializer_list<Type> _Ilist  
    );  
template<class Type, class Pr>   
    Type& max(  
        initializer_list<Type> _Ilist,   
        BinaryPredicate comp  
    );  
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 První dvě porovnávaných objektů.  
  
 `right`  
 Druhá dvě porovnávaných objektů.  
  
 `comp`  
 Binární predikát použit k porovnání dvou objektů.  
  
 `_IList`  
 Inicializátoru seznamu, který obsahuje objekty, které se má porovnat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Delší než dva objekty, pokud žádná není větší; v takovém případě vrátí první dva objekty. V případě initializer_list vrátí největší objektů v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 `max` Algoritmus neobvyklé v s objekty předány jako parametry. Většina algoritmy standardní knihovna C++ pracovat na celou řadu elementy, jejichž pozice je zadána iterátory předány jako parametry. Pokud potřebujete funkci, která pracuje na rozsahu prvků, použijte [max_element –](../standard-library/algorithm-functions.md#max_element) místo.  
  
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
  
int main( )  
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
  
##  <a name="max_element"></a>max_element –  
 Vyhledá první výskyt největšího prvku v zadaném rozsahu, kde kritérium pořadí může být určeno binárním predikátem.  
  
```  
template<class ForwardIterator>  
ForwardIterator max_element(ForwardIterator first, ForwardIterator last );  
  
template<class ForwardIterator, class BinaryPredicate>  
ForwardIterator max_element(ForwardIterator first, ForwardIterator last, BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Předat dál iterator adresování pozice první prvek v rozsahu má být vyhledán největší elementu.  
  
 `last`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu má být vyhledán největší elementu.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém je větší než druhý jeden element. Binární predikát má dva argumenty a by měla vrátit **true** při prvním elementem je menší než druhý prvkem a **false** jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator adresování pozici prvního výskytu největší elementu v rozsahu vyhledávat.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci každé pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Složitost je lineární: ( `last`  -   `first`) – 1 porovnání je vyžadováno pro neprázdný rozsah.  
  
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
  
int main( )  
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
  
   s1_R1_Iter = max_element ( s1.begin ( ) , s1.end ( ) );  
  
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
  
   v1_R1_Iter = max_element ( v1.begin ( ) , v1.end ( ) );  
   v1_R2_Iter = max_element ( v1.begin ( ) , v1.end ( ), mod_lesser);  
  
   cout << "The largest element in v1 is: " << *v1_R1_Iter << endl;  
   cout << "The largest element in v1 under the mod_lesser"  
        << "\n binary predicate is: " << *v1_R2_Iter << endl;  
}  
```  
  
##  <a name="merge"></a>sloučení  
 Spojuje všechny elementy ze dvou seřazené zdrojových oblastí do jednoho, seřazené cílové oblasti, kde toto kritérium řazení může být určena binárního predikátu.  
  
```  
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
  `first1`  
 Vstupní iterovat adresování pozice první prvek v první dva seřazené zdrojových oblastí kombinaci a do jednoho rozsahu seřazeny.  
  
 `last1`  
 Vstupní iterovat adresování pozici jeden za posledním elementem v první dva seřazené zdrojových oblastí kombinaci a do jednoho rozsahu seřazeny.  
  
  `first2`  
 Vstupní iterovat adresování pozice první prvek za sekundu ze dvou po sobě jdoucích seřazené zdrojových oblastí kombinaci a do jednoho rozsahu seřazeny.  
  
 `last2`  
 Vstupní iterovat adresování pozici jeden za posledním elementem za sekundu rozsahů dvě po sobě jdoucích seřazené zdroj kombinaci a do jednoho rozsahu seřazeny.  
  
 `result`  
 Iterátor výstup adresování pozice první prvek v cílové oblasti, kde jsou dva zdrojových oblastí a nelze jej zkombinovat do jednoho seřazené oblasti.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém je větší než druhý jeden element. Binární predikát má dva argumenty a by měla vrátit **true** při prvním elementem je menší než druhý prvkem a **false** jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup adresování pozice, jedna po posledním prvkem v seřazené cílový rozsah.  
  
### <a name="remarks"></a>Poznámky  
 Seřazené zdrojových oblastí odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci každé pořadí poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Rozsah cílových nesmí překrývat buď zdrojových oblastí a by měl být dostatečně velký, aby se tak, aby obsahovala cílový rozsah.  
  
 Seřazené zdrojových oblastí musí každý být uspořádány podmínkou pro použití **sloučení** algoritmus v souladu s stejné řazení jako má být použita algoritmem seřadit kombinované rozsahy.  
  
 Operace je stabilní jako relativní pořadí prvků v každém rozsahu se zachová cílový rozsah. Zdrojových oblastí se nemění algoritmem **sloučení**.  
  
 Typy hodnot ze vstupních iterátory musí být menší – než porovnatelný seřadit, tak, aby hodnotě dva elementy, může být bylo zjištěno, že jsou ekvivalentní (v tom smyslu, že ani je menší než druhá) nebo jedna je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou ekvivalentní elementy v obou zdrojových oblastí, před prvky v první oblasti elementy z druhého rozsahu zdroje v cílové oblasti.  
  
 Složitost algoritmu je lineární s maximálně (* Příjmení1 - first1*) – (* Příjmení2 - first2*) – 1 porovnání.  
  
 [List – třída](../standard-library/list-class.md) poskytuje členské funkce "sloučení" sloučit elementy dva seznamy.  
  
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
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vector v2 with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );  
   vector <int>::iterator Iter2a,  Iter2b, Iter2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vector v3 with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );  
   vector <int>::iterator Iter3a,  Iter3b, Iter3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        << "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        << "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To merge inplace in ascending order with default binary   
   // predicate less <int> ( )  
   merge ( v1a.begin ( ) , v1a.end ( ) , v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Merged inplace with default order,\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To merge inplace in descending order, specify binary   
   // predicate greater<int>( )  
   merge ( v2a.begin ( ) , v2a.end ( ) , v2b.begin ( ) , v2b.end ( ) ,  
       v2.begin ( ) ,  greater <int> ( ) );  
   cout << "Merged inplace with binary predicate greater specified,\n "  
        << "vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // Applying A user-defined (UD) binary predicate mod_lesser  
   merge ( v3a.begin ( ) , v3a.end ( ) , v3b.begin ( ) , v3b.end ( ) ,  
       v3.begin ( ) ,  mod_lesser );  
   cout << "Merged inplace with binary predicate mod_lesser specified,\n "  
        << "vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="min"></a>min.  
 Porovná dva objekty a vrátí menší z nich, kde kritérium pořadí může být určeno binárním predikátem.  
  
```  
template<class Type>  
    const Type& min(  
        const Type& left,   
        const Type& right  
    );  
template<class Type, class Pr>  
    const Type& min(  
        const Type& left,   
        const Type& right,  
        BinaryPredicate comp  
    );  
template<class Type>   
    Type min ( initializer_list<Type> _Ilist  
    );  
template<class Type, class Pr>    Type min (  
        initializer_list<Type> _Ilist,   
        BinaryPredicate comp  
    );  
  
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 První dvě porovnávaných objektů.  
  
 `right`  
 Druhá dvě porovnávaných objektů.  
  
 `comp`  
 Binární predikát použit k porovnání dvou objektů.  
  
 `_IList`  
 Initializer_list, který obsahuje členy, který se má porovnat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Menší dvou objektů, pokud žádná není menší; v takovém případě vrátí první dva objekty. V případě initializer_list vrátí nejmenší objektů v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 `min` Algoritmus neobvyklé v s objekty předány jako parametry. Většina algoritmy standardní knihovna C++ pracovat na celou řadu elementy, jejichž pozice je zadána iterátory předány jako parametry. Pokud potřebujete funkci, která používá rozsahu prvků, použijte [min_element –](../standard-library/algorithm-functions.md#min_element).  
  
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
  
int main( )  
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
  
##  <a name="min_element"></a>min_element –  
 Vyhledá první výskyt nejmenšího prvku v zadaném rozsahu, kde kritérium pořadí může být určeno binárním predikátem.  
  
```  
 template<class ForwardIterator>  
 ForwardIterator min_element(ForwardIterator first, ForwardIterator last );  
  
template<class ForwardIterator, class BinaryPredicate>  
ForwardIterator min_element(ForwardIterator first, ForwardIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Předat dál iterator adresování pozice první prvek v rozsahu má být vyhledán nejmenší elementu.  
  
 `last`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu má být vyhledán nejmenší elementu.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém je větší než druhý jeden element. Binární predikát má dva argumenty a by měla vrátit **true** při prvním elementem je menší než druhý prvkem a **false** jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator adresování pozici prvního výskytu nejmenší elementu v rozsahu vyhledávat.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci každé pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Složitost je lineární: ( `last`  -  `first`) – 1 porovnání je vyžadováno pro neprázdný rozsah.  
  
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
  
   s1_R1_Iter = min_element ( s1.begin ( ) , s1.end ( ) );  
  
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
  
   v1_R1_Iter = min_element ( v1.begin ( ) , v1.end ( ) );  
   v1_R2_Iter = min_element ( v1.begin ( ) , v1.end ( ), mod_lesser);  
  
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
  
##  <a name="minmax_element"></a>minmax_element  
 Provede práci provádí `min_element` a `max_element` jedno volání.  
  
```  
template<class ForwardIterator>  
    pair< ForwardIterator, ForwardIterator >  
        minmax_element(  
            ForwardIterator  first,   
            ForwardIterator Last  
                 );  
template<class ForwardIterator, class BinaryPredicate>  
    pair< ForwardIterator, ForwardIterator >  
        minmax_element(  
            ForwardIterator  first,   
            ForwardIterator Last,   
            BinaryPredicate  comp  
                );  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator předat dál, která určuje začátek rozsahu.  
  
 `last`  
 Iterator předat dál, která určuje konec rozsahu.  
  
 `comp`  
 Volitelné test, který používá k pořadí elementů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací  
  
 `pair<ForwardIterator, ForwardIterator>`  
  
 `(`[min_element –](../standard-library/algorithm-functions.md#min_element)`(first, last), `[max_element –](../standard-library/algorithm-functions.md#max_element)`(first, last))`.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí první funkce šablony  
  
 `pair<ForwardIterator,ForwardIterator>`  
  
 `(min_element(_First,Last), max_element(_First,Last))`.  
  
 Druhá šablona funkce se chová stejně, s tím rozdílem, že se nahradí `operator<(X, Y)` s `comp (X, Y)`.  
  
 Pokud je pořadí je prázdný, funkce provede maximálně `3 * (last - first - 1) / 2` porovnání.  
  
##  <a name="minmax"></a>minmax  
 Porovná dva vstupní parametry a vrací je jako pár, v pořadí podle menší na hodnotu větší.  
  
```  
template<class Type>  
    pair<const Type&, const Type&>  
        minmax(  
            const Type& left,   
            const Type& right  
        );  
template<class Type, class BinaryPredicate>  
    pair<const Type&, const Type&>  
        minmax(  
            const Type& left,  
            const Type& right,  
            BinaryPredicate comp  
        );  
template<class Type>     pair<Type&, Type&>         minmax(  
            initializer_list<Type> _Ilist  
        );  
template<class Type, class BinaryPredicate>   
    pair<Type&, Type&>         minmax(  
            initializer_list<Type> _Ilist,   
            BinaryPredicate comp  
        );  
  
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 První dvě porovnávaných objektů.  
  
 `right`  
 Druhá dvě porovnávaných objektů.  
  
 `comp`  
 Binární predikát použit k porovnání dvou objektů.  
  
 `_IList`  
 Initializer_list, který obsahuje členy, který se má porovnat.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí první funkce šablony `pair<const Type&, const Type&>( right , left )` Pokud `right` je menší než `left`. Funkce `pair<const Type&, const Type&>( left , right )`.  
  
 Druhý členská funkce vrátí pár kde první prvek je menší a druhý je větší srovnání predikátem `comp`.  
  
 Zbývající šablony funkcí chovají stejně, s tím rozdílem, že nahrazují `left` a `right` parametry s `_IList`.  
  
 Funkce provádí přesně jeden porovnání.  
  
##  <a name="mismatch"></a>Neshoda  
 Porovná dva rozsahy elementu pomocí elementu a vyhledá první pozici, kde dochází k rozdíl.  
  
 Použijte přetížení duální rozsahy v C ++ 14 kódu, protože přetížení, která trvat jenom jeden iterator pro druhého rozsahu nerozpozná rozdíly, pokud je delší, než je první rozsah druhého rozsahu a způsobí nedefinované chování, pokud je kratší druhého rozsahu než první rozsah.  
  
```  
 template<class InputIterator1, class InputIterator2> pair<InputIterator1, InputIterator2>>   
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
template<class InputIterator1, class InputIterator2> pair<InputIterator1, InputIterator2>>  
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
 `First1`  
 Vstupní iterovat adresování pozice první prvek v první oblasti, která má být testována.  
  
 `Last1`  
 Vstupní iterovat adresování pozice, jedna po posledním prvkem v první oblasti, která má být testována.  
  
 `First2`  
 Vstupní iterovat adresování pozice první prvek v druhého rozsahu má být testována.  
  
 `Last2`  
 Vstupní iterovat adresování pozice jednoho po posledním prvkem v druhého rozsahu má být testována.  
  
 `Comp`  
 Uživatelem definované funkce predikátu objekt, který porovnává aktuální prvky v každém rozsahu a určí, zda jsou ekvivalentní. Vrátí **true** při a **false** při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pár iterátory adresování pozic neshoda ve dvou oblastí, první součást iterator na pozici v rozsahu první a druhý iterator součást na pozici v druhého rozsahu. Pokud není žádný rozdíl mezi elementy v oblastech porovnání nebo binární predikátu v druhé verzi splňují všechny páry element ze dvou oblastí, potom první součást iterator odkazuje na pozici jeden za poslední element v prvním rozsah a druhý iterator součást do pozice, jeden za poslední element otestována druhého rozsahu.  
  
### <a name="remarks"></a>Poznámky  
 První funkce šablony předpokládá, že jsou v rozsahu od na first2, protože jsou v rozsahu určený hodnotou [first1, Příjmení1) počet elementů. Pokud existují další v druhého rozsahu, jsou ignorovány; Pokud máte menší nedefinované chování povede.  
  
 Rozsah má proběhnout, musí být platná; musí být všechny iterátory dereferenceable a je dostupný z první poslední pozice podle Inkrementace.  
  
 Čas složitost algoritmu je lineární počet elementů obsažených v kratší rozsahu.  
  
 Uživatelem definované predikátu není potřeba uplatňovat vztah ekvivalenční této symetrický, reflexivní a přenosné mezí jejími operandy.  
  
### <a name="example"></a>Příklad  
  Následující příklad ukazuje, jak používat neshoda. Přetížení 03 C ++ se zobrazí pouze kvůli ukazují, jak ji může vytvořit neočekávaný výsledek.  
  
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
  
##  <a name="alg_move"></a>  &lt;alg&gt; přesunout  
 Přesune prvky přidružené k určenému rozsahu.  
  
```  
template<class InputIterator, class OutputIterator>  
    OutputIterator move(  
        InputIterator first,   
        InputIterator last,  
        OutputIterator dest  
                  );  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterator, která určuje, kde má být zahájen celou škálu elementy přesunout.  
  
 `last`  
 Vstupní iterator, která určuje konec rozsahu prvků přesunout.  
  
 `dest`  
 Iterator výstup, který obsahuje přesunutý elementy.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vyhodnotí `*(dest + N) = move(*(first + N))` jednou pro každou `N` v rozsahu `[0, last - first)`, pro výhradně zvýšení hodnoty `N` od nejnižší možná hodnota. Pak vrátí `dest + N`. Pokud `dest` a `first` určit oblasti úložiště, `dest` nesmí být v rozsahu `[first, last)`.  
  
##  <a name="move_backward"></a>move_backward  
 Přesune prvky jednoho iterátoru do druhého. Pohyb začíná posledním prvkem v daném rozsahu a končí prvním prvkem v daném rozsahu.  
  
```  
template<class BidirectionalIterator1, class BidirectionalIterator2>  
   BidirectionalIterator2 move_backward(  
       BidirectionalIterator1 first,   
       BidirectionalIterator1 last,  
       BidirectionalIterator2 destEnd);
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterátor, který určuje začátek rozsahu přesunout elementy z.  
  
 `last`  
 Iterator, která určuje konec rozsahu přesunout elementy z. Tento element není přesunut.  
  
 `destEnd`  
 Obousměrný iterátor, který adresuje umístění jedno místo za posledním prvkem v cílové oblasti.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vyhodnotí `*(destEnd - N - 1) = move(*(last - N - 1))` jednou pro každou `N` v rozsahu `[0, last - first)`, pro výhradně zvýšení hodnoty `N` od nejnižší možná hodnota. Pak vrátí `destEnd - (last - first)`. Pokud `destEnd` a `first` určit oblasti úložiště, `destEnd` nesmí být v rozsahu `[first, last)`.  
  
 `move`a `move_backward` jsou funkčně rovnocenné pomocí `copy` a `copy_backward` s move iterator.  
  
##  <a name="next_permutation"></a>next_permutation –  
 Znovu uspořádá prvky v rozsahu tak, aby původní pořadí bylo nahrazeno lexikograficky následující větší permutací, pokud existuje, kde význam následujícího může být určen binárním predikátem.  
  
```  
template<class BidirectionalIterator>  
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last);  
  
template<class BidirectionalIterator, class BinaryPredicate>  
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Obousměrné iterator odkazující na pozici prvním elementem v rozsahu na být permutovanou funkci.  
  
 `last`  
 Obousměrné iterator odkazující na pozici jeden za poslední element v rozsahu na být permutovanou funkci.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje kritéria porovnání měly splňovat po sobě následujících elementů v řazení. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud lexicographically další Permutace existuje a má nahradit původní řazení rozsahu; v opačném případě **false**, v takovém případě řazení transformována do lexicographically nejmenší Permutace.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Predikát binární výchozí je menší než a elementy v rozsahu musí být menší než srovnatelné zajistit, že další Permutace dobře definované.  
  
 Složitost je lineární s maximálně (* poslední - nejprve *) / 2 prohození.  
  
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
  
int main( )  
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
  
   deq1Result = next_permutation ( deq1.begin ( ) , deq1.end ( ) );  
  
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
  
   next_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );  
  
   cout << "After the first next_permutation, vector v1 is:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   int iii = 1;  
   while ( iii <= 5 ) {  
      next_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );  
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
  
##  <a name="nth_element"></a>nth_element –  
 Oddíly rozsahu prvků, správně hledání  *n* element TD pořadí v rozsahu, aby všechny elementy úrovních před ním jsou menší než nebo rovna hodnotě ho a všechny elementy, které následují v pořadí Opětovná větší než nebo rovna hodnotě ho.  
  
```  
template<class RandomAccessIterator>  
void nth_element( RandomAccessIterator first, RandomAccessIterator _Nth, RandomAccessIterator last);  
  
 template<class RandomAccessIterator, class BinaryPredicate>  
 void nth_element( RandomAccessIterator first, RandomAccessIterator _Nth, RandomAccessIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Náhodným přístupem iterator adresování pozice první prvek v rozsahu k rozdělení na oddíly.  
  
 *_Nth*  
 Náhodným přístupem iterator adresování umístění prvku správné seřazení v hranice oddílu.  
  
 `last`  
 Náhodným přístupem iterator adresování pozici jeden za poslední element v rozsahu k rozdělení na oddíly.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje kritéria porovnání měly splňovat po sobě následujících elementů v řazení. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 `nth_element` Algoritmus není zaručeno, že buď straně elementů v dílčí rozsahy z  *n* element TD jsou seřazeny. Proto umožňuje záruky méně než `partial_sort`, který řadí elementy v rozsahu níže některé vybraný element a může být použita jako rychlejší alternativní k `partial_sort` při řazení nižší rozsah se nevyžaduje.  
  
 Elementy jsou ekvivalentní, ale nemusí nutně jít rovná, pokud je menší než druhý.  
  
 Průměr složitost řazení je lineární s ohledem na * poslední - nejprve *.  
  
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
  
##  <a name="none_of"></a>none_of  
 Vrátí `true` při podmínku nachází nikdy mezi elementy v daném rozsahu.  
  
```  
template<class InputIterator, class BinaryPredicate>  
bool none_of(InputIterator first, InputIterator last, BinaryPredicate comp);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterator, která určuje, kde má být zahájen Zkontrolujte řadu prvky pro podmínku.  
  
 `last`  
 Vstupní iterator, která určuje konec rozsahu prvků.  
  
 `comp`  
 Podmínky, které chcete otestovat. To zajišťuje uživatelem definované funkce predikátu objekt, který definuje podmínku. Predikát přijímá jeden argument a vrátí `true` nebo `false`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `true` Pokud podmínka není zjištěna alespoň jednou v uvedených rozsahu, a `false` v případě zjištění podmínku.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí `true` pouze tehdy, pokud pro některé `N` v rozsahu `[0, last - first)`, predikát `comp(*(first + N))` je vždy `false`.  
  
##  <a name="partial_sort"></a>partial_sort –  
 Uspořádá zadaný počet menších prvků v rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.  
  
```  
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
 `first`  
 Náhodným přístupem iterator adresování pozice první prvek v rozsahu k řazení.  
  
 `sortEnd`  
 Náhodným přístupem iterator adresování pozici jeden za poslední element v Podoblast sady který se má seřadit.  
  
 `last`  
 Náhodným přístupem iterator adresování pozici jeden za poslední element v rozsahu částečně řazení.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje kritéria porovnání měly splňovat po sobě následujících elementů v řazení. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Elementy jsou ekvivalentní, ale nemusí nutně jít rovná, pokud je menší než druhý. **Řazení** algoritmus není stabilní a není zaručeno, že relativní řazení ekvivalentní elementy se zachovají. Algoritmus `stable_sort` zachovat původní řazení.  
  
 Složitost průměrná částečné řazení je *O*(( `last` -  `first`) protokolu ( `sortEnd` -  `first`)).  
  
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
  
int main( )  
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
  
##  <a name="partial_sort_copy"></a>partial_sort_copy –  
 Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu, kde zdrojové prvky jsou seřazeny buď podle binárního predikátu „menší než“ nebo jiného určeného binárního predikátu.  
  
```  
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
  `first1`  
 Vstupní iterovat pozice první prvek v zdrojový rozsah adres.  
  
 `last1`  
 Vstupní iterovat pozice jeden za poslední element v zdrojový rozsah adres.  
  
  `first2`  
 Náhodným přístupem iterator adresování pozice první prvek v seřazené cílový rozsah.  
  
 `last2`  
 Náhodným přístupem iterator adresování pozice jeden za poslední element v seřazené cílový rozsah.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje podmínku, která má být splněny, pokud dva elementy musí být odebrána jako ekvivalentní. Binární predikát má dva argumenty a vrátí `true` při a `false` při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator náhodným přístupem adresování element v cílovém rozsahu jednu pozici za posledním elementem vložit z rozsahu zdroje.  
  
### <a name="remarks"></a>Poznámky  
 Zdrojové a cílové rozsahy se nesmí překrývat a musí být platné; musí být všechny ukazatele dereferenceable a v rámci každé pořadí poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Binární predikát musíte zadat striktní weak řazení tak, aby prvky, které nejsou ekvivalentní uspořádány, ale nejsou prvky, které jsou ekvivalentní. Dva elementy jsou ekvivalentní za méně než, ale nemusí nutně jít rovná, pokud je menší než druhý.  
  
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
  
##  <a name="partition"></a>oddíl  
 Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují.  
  
```  
template<class BidirectionalIterator, class Predicate>  
   BidirectionalIterator partition(  
      BidirectionalIterator first,   
      BidirectionalIterator last,   
      Predicate comp);
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Obousměrné iterator adresování pozice první prvek v rozsahu k rozdělení na oddíly.  
  
 `last`  
 Obousměrné iterator adresování pozici jeden za poslední element v rozsahu k rozdělení na oddíly.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje podmínku, která má uspokojit, pokud je element klasifikovat. Predikát přijímá jeden argument a vrátí **true** nebo **false**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Obousměrné iterator adresování pozice první prvek v rozsahu není vyhovět podmínka predikátu.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Elementy *a* a *b* jsou ekvivalentní, ale stejně nemusí nutně prokázat, pokud obě *Pr* ( *a*, *b*) je hodnota false a *Pr* ( *b*, *a*) Pokud je hodnota false, kde *Pr* je zadán parametr predikátu. **Oddílu** algoritmus není stabilní a není zaručeno, že relativní řazení ekvivalentní elementy se zachovají. Algoritmus **stable_ oddílu** zachovat původní řazení.  
  
 Složitost je lineární: existují ( `last`  -   `first`) aplikace `comp` a maximálně ( `last`  -   `first`) / 2 prohození.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_partition.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater5 ( int value ) {  
   return value >5;  
}  
  
int main( ) {  
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
  
##  <a name="partition_copy"></a>partition_copy –  
 Zkopíruje elementy, pro které je podmínku `true` do cílové a pro které podmínku `false` do jiného. Prvky musí pocházet ze zadaného rozsahu.  
  
```  
template<class InputIterator, class OutputIterator1, class OutputIterator2, class Predicate>  
    pair<OutputIterator1, OutputIterator2>  
        partition_copy(  
            InputIterator first,   
            InputIterator last,  
            OutputIterator1 dest1,   
            OutputIterator2 dest2,   
            Predicate pred  
        );  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterátor vstupní, který určuje začátek rozsahu u podmínek.  
  
 `last`  
 Vstupní iterator, která určuje konec rozsahu.  
  
 `dest1`  
 Iterátor výstup použít ke zkopírování elementy, které vrací hodnotu true pro podmínku testovat pomocí `_Pred`.  
  
 `dest2`  
 Iterátor výstup použít ke zkopírování elementy, které vrací hodnotu false pro podmínku testovat pomocí `_Pred`.  
  
 `_Pred`  
 Podmínky, které chcete otestovat. To zajišťuje uživatelem definované funkce predikátu objekt, který definuje podmínku, která má být testována. Predikát přijímá jeden argument a vrátí `true` nebo `false`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony zkopíruje každý prvek `X` v `[first,last)` k `*dest1++` Pokud `_Pred(X)` má hodnotu true, nebo `*dest2++` není-li. Vrátí `pair<OutputIterator1, OutputIterator2>(dest1, dest2)`.  
  
##  <a name="partition_point"></a>partition_point  
 Vrátí první prvek v zadaném rozsahu, který nesplňuje podmínku. Prvky jsou seřazeny tak, aby ty, které splňují podmínku, předcházely těm, které ji nesplňují.  
  
```  
template<class ForwardIterator, class Predicate>  
    ForwardIterator partition_point(  
        ForwardIterator first,   
        ForwardIterator last,  
        Predicate comp  
    );  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 A `ForwardIterator` určující spuštění rozsah pro kontrolu pro podmínku.  
  
 `last`  
 A `ForwardIterator` určující konec rozsahu.  
  
 `comp`  
 Podmínky, které chcete otestovat. To zajišťuje uživatelem definované funkce predikátu objekt, který definuje podmínku, která má vyhovět prohledávaný pro element. Predikát přijímá jeden argument a vrátí `true` nebo `false`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `ForwardIterator` který odkazuje na první prvek, který nesplňuje podmínky testována na `comp`, nebo vrátí `last` Pokud zprostředkovatele služeb nenajde.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vyhledá první iterator `it` v `[first, last)` pro kterou `comp(*it)` je `false`. Pořadí musí provést řazení podle `comp`.  
  
##  <a name="pop_heap"></a>pop_heap –  
 Odstraní největší prvek z přední části haldy až do předposlední pozice v rozsahu a ze zbývajících prvků vytvoří novou haldu.  
  
```  
template<class RandomAccessIterator>  
void pop_heap( RandomAccessIterator first, RandomAccessIterator last);  
  
template<class RandomAccessIterator, class BinaryPredicate>  
void pop_heap(RandomAccessIterator first, RandomAccessIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Náhodným přístupem iterator adresování pozice první prvek v haldě.  
  
 `last`  
 Náhodným přístupem iterator adresování pozice jeden za poslední element v haldě.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém jeden element je menší než jiné. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="remarks"></a>Poznámky  
 `pop_heap` Algoritmus je opakem operaci provést, algoritmem push_heap –, ve kterém se přidá prvek na pozici další poslední rozsahu haldě, který se skládá z předchozí prvky v rozsahu, v případě, pokud element, který se přidává do halda je větší než jeho prvky již v haldě.  
  
 Haldách mít dvě vlastnosti:  
  
-   První prvek je vždy na největší.  
  
-   Elementy může přidat nebo odebrat logaritmické včas.  
  
 Haldách jsou nejvhodnější způsob implementace priority fronty a jejich použití k implementaci adaptéru kontejneru standardní knihovna C++ [priority_queue – třída](../standard-library/priority-queue-class.md).  
  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Rozsah vyloučení nově přidaný prvek na konci musí být haldy.  
  
 Složitost je logaritmické, maximálně vyžadování protokolu (* poslední - nejprve *) porovnání.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_pop_heap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  {  
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
  
##  <a name="prev_permutation"></a>prev_permutation –  
 Změní elementy v rozsahu, takže původní řazení lexicographically předchozí větší Permutace nahrazuje, pokud existuje, kde může být smysl předchozího zadaným predikátu binární.  
  
```  
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
  `first`  
 Obousměrné iterator odkazující na pozici prvním elementem v rozsahu na být permutovanou funkci.  
  
 `last`  
 Obousměrné iterator odkazující na pozici jeden za poslední element v rozsahu na být permutovanou funkci.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje kritéria porovnání měly splňovat po sobě následujících elementů v řazení. Binární predikát má dva argumenty a vrátí `true` při a `false` při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud lexicographically předchozí Permutace existuje a má nahradit původní řazení o rozsahu. v opačném případě `false`, v takovém případě řazení transformována do lexicographically největší Permutace.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Predikát binární výchozí je menší než a elementy v rozsahu musí být menší – než srovnatelná zajistěte, aby byl předchozí Permutace dobře definované.  
  
 Složitost je lineární s maximálně ( `last`  -   `first`) / 2 prohození.  
  
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
  
   deq1Result = prev_permutation ( deq1.begin ( ) , deq1.end ( ) );  
  
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
  
   prev_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );  
  
   cout << "After the first prev_permutation, vector v1 is:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   int iii = 1;  
   while ( iii <= 5 ) {  
      prev_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );  
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
  
##  <a name="push_heap"></a>push_heap –  
 Přidá prvek, který je na konci rozsahu, do stávající haldy, která zahrnuje předchozí prvky daného rozsahu.  
  
```  
template<class RandomAccessIterator>  
void push_heap( RandomAccessIterator first, RandomAccessIterator last );  
  
template<class RandomAccessIterator, class BinaryPredicate>  
void push_heap( RandomAccessIterator first, RandomAccessIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Náhodným přístupem iterator adresování pozice první prvek v haldě.  
  
 `last`  
 Adresování jednoho pozice po posledním element v rozsahu, který má být převeden na haldu iterator náhodný přístup.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém jeden element je menší než jiné. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="remarks"></a>Poznámky  
 Element musí být nejprve zpět poslat na konec existující haldy a pak algoritmus se používá k přidání tohoto elementu existující haldě.  
  
 Haldách mít dvě vlastnosti:  
  
-   První prvek je vždy na největší.  
  
-   Elementy může přidat nebo odebrat logaritmické včas.  
  
 Haldách jsou nejvhodnější způsob implementace priority fronty a jejich použití k implementaci adaptéru kontejneru standardní knihovna C++ [priority_queue – třída](../standard-library/priority-queue-class.md).  
  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Rozsah vyloučení nově přidaný prvek na konci musí být haldy.  
  
 Složitost je logaritmické, maximálně vyžadování protokolu ( *poslední - nejprve*) porovnání.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_push_heap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( ) {  
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
  
##  <a name="random_shuffle"></a>random_shuffle –  
 Zastaralé funkce std::random_shuffle() nahrazuje [std::shuffle](../standard-library/algorithm-functions.md#shuffle). Příklad kódu a další informace najdete v tématu [ \<náhodných >](../standard-library/random.md) a zveřejňování Stackoverflow [proč std::random_shuffle metody se nepoužívají v C ++ 14?](http://go.microsoft.com/fwlink/?LinkId=397954).  
  
##  <a name="remove"></a>odebrat  
 Odstraní zadanou hodnotu z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.  
  
```  
template<class ForwardIterator, class Type>  
 ForwardIterator remove(ForwardIterator first, ForwardIterator last, const Type& val);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Předat dál iterator adresování pozice první prvek v rozsahu, ze kterého budou odebrány elementy.  
  
 `last`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu, ze kterého budou odebrány elementy.  
  
 `val`  
 Hodnota, která má být odebrána z rozsahu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator adresování nová koncová pozice upravené rozsahu, jedna po posledním element volné zadané hodnoty zbývajících pořadí.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Pořadí prvků neodeberou zůstane stabilní.  
  
 `operator==` Používá k určení rovnosti mezi elementy musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Složitost je lineární; Existují ( `last`  -   `first`) porovnání rovnosti.  
  
 [List – třída](../standard-library/list-class.md) má efektivnější členské funkce verzi **odebrat**, který také relinks ukazatele.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_remove.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
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
  
##  <a name="remove_copy"></a>remove_copy –  
 Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu. Prvky zadané hodnoty zkopírovány nejsou. Nenaruší pořadí zbývajících prvků a nevrátí konec nového cílového rozsahu.  
  
```  
template<class InputIterator, class OutputIterator, class Type>  
 OutputIterator remove_copy(InputIterator first, InputIterator last, OutputIterator result, const Type& val);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterovat adresování pozice první prvek v rozsahu, ze kterého budou odebrány elementy.  
  
 `last`  
 Vstupní iterovat adresování pozici jeden za poslední element v rozsahu, ze kterého budou odebrány elementy.  
  
 `result`  
 Iterátor výstup adresování pozice první prvek v cílový rozsah, do které budou odebrány elementy.  
  
 `val`  
 Hodnota, která má být odebrána z rozsahu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator adresování nová koncová pozice cílové oblasti, jedna po posledním elementu kopii volné zadané hodnoty zbývajících pořadí.  
  
### <a name="remarks"></a>Poznámky  
 Zdrojové a cílové oblasti odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Cílový rozsah tak, aby obsahovala zbývajících prvky, které budou zkopírovány po odebrání elementy zadaná hodnota musí být dostatek místa.  
  
 Pořadí prvků neodeberou zůstane stabilní.  
  
 `operator==` Používá k určení rovnosti mezi elementy musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Složitost je lineární; Existují ( `last`  -   `first`) porovnání rovnosti a maximálně ( `last`  -   `first`) přiřazení.  
  
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
  
##  <a name="remove_copy_if"></a>remove_copy_if –  
 Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu. Prvky splňující predikát zkopírovány nejsou. Nenaruší pořadí zbývajících prvků a nevrátí konec nového cílového rozsahu.  
  
```  
template<class InputIterator, class OutputIterator, class Predicate>  
OutputIterator remove_copy_if(InputIterator first, InputIterator Last, OutputIterator result, Predicate pred);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterovat adresování pozice první prvek v rozsahu, ze kterého budou odebrány elementy.  
  
 `last`  
 Vstupní iterovat adresování pozici jeden za poslední element v rozsahu, ze kterého budou odebrány elementy.  
  
 `result`  
 Iterátor výstup adresování pozice první prvek v cílový rozsah, do které budou odebrány elementy.  
  
 `_Pred`  
 Unární predikát, který musí být splněny, je že hodnota elementu má být nahrazen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator adresování nová koncová pozice cílové oblasti, jedna po posledním element volné elementů, které splňují predikát zbývajících pořadí.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah zdrojových odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Cílový rozsah tak, aby obsahovala zbývajících prvky, které budou zkopírovány po odebrání elementy zadaná hodnota musí být dostatek místa.  
  
 Pořadí prvků neodeberou zůstane stabilní.  
  
 `operator==` Používá k určení rovnosti mezi elementy musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Složitost je lineární: existují ( `last`  -   `first`) porovnání rovnosti a maximálně ( `last`  -   `first`) přiřazení.  
  
 Informace o chování těchto funkcí najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_remove_copy_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater6 ( int value ) {  
   return value >6;  
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
  
##  <a name="remove_if"></a>remove_if –  
 Odstraní prvky, které splňují predikát, z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.  
  
```  
template<class ForwardIterator, class Predicate>  
 ForwardIterator remove_if(ForwardIterator first, ForwardIterator last, Predicate pred);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Předat dál iterator odkazující na pozici prvním elementem v rozsahu, ze kterého budou odebrány elementy.  
  
 `last`  
 Předat dál iterator odkazující na pozici, jedna po posledním element v rozsahu, ze kterého budou odebrány elementy.  
  
 `_Pred`  
 Unární predikát, který musí být splněny, je že hodnota elementu má být nahrazen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator adresování nová koncová pozice upravené rozsahu, jedna po posledním element volné zadané hodnoty zbývajících pořadí.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Pořadí prvků neodeberou zůstane stabilní.  
  
 `operator==` Používá k určení rovnosti mezi elementy musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Složitost je lineární: existují ( `last`  -   `first`) porovnání rovnosti.  
  
 Seznam má efektivnější verze funkce člena odebrat, který relinks ukazatele.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_remove_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater6 ( int value ) {  
   return value >6;  
}  
  
int main( ) {  
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
  
##  <a name="replace"></a>nahradit  
 Zkontroluje každý prvek v rozsahu a nahradí jej, pokud odpovídá zadané hodnotě.  
  
```  
template<class ForwardIterator, class Type>  
void replace(ForwardIterator first, ForwardIterator last, const Type& _OldVal, const Type& _NewVal);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Předat dál iterator odkazující na pozici prvním elementem v rozsahu, ze kterého se nahrazují elementy.  
  
 `last`  
 Předat dál iterator odkazující na pozici, jedna po posledním element v rozsahu, ze kterého se nahrazují elementy.  
  
 `_OldVal`  
 Původní hodnoty elementů nahrazují.  
  
 `_NewVal`  
 Nová hodnota přiřazeny elementy původní hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Pořadí prvků není nahrazena zůstane stabilní.  
  
 `operator==` Používá k určení rovnosti mezi elementy musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Složitost je lineární; Existují ( `last`  -   `first`) porovnání rovnosti a maximálně ( `last`  -   `first`) přiřazení nové hodnoty.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_replace.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
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
  
##  <a name="replace_copy"></a>replace_copy –  
 Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu odpovídá zadané hodnotě.  
  
```  
 template<class InputIterator, class OutputIterator, class Type>  
 OutputIterator replace_copy(   
     InputIterator first,  
     InputIterator last,  
     OutputIterator result,  
     const Type& _OldVal,  
     const Type& _NewVal);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterovat odkazující na pozici prvním elementem v rozsahu, ze kterého se nahrazují elementy.  
  
 `last`  
 Vstupní iterovat odkazující na pozici jeden za poslední element v rozsahu, ze kterého se nahrazují elementy.  
  
 `result`  
 Iterátor výstup odkazující na prvním elementem v rozsahu cílového kde kopírovány změnit pořadí elementů.  
  
 `_OldVal`  
 Původní hodnoty elementů nahrazují.  
  
 `_NewVal`  
 Nová hodnota přiřazeny elementy původní hodnoty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup odkazující na pozici jeden za poslední element v rozsahu cílového do kde kopírovány změnit pořadí elementů.  
  
### <a name="remarks"></a>Poznámky  
 Zdrojové a cílové oblasti odkazuje se nesmí překrývat a musí být platný: musí být všechny ukazatele dereferenceable a v rámci daná pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Pořadí prvků není nahrazena zůstane stabilní.  
  
 `operator==` Používá k určení rovnosti mezi elementy musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Složitost je lineární: existují ( `last`  -   `first`) porovnání rovnosti a maximálně ( `last`  -   `first`) přiřazení nové hodnoty.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_replace_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
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
  
##  <a name="replace_copy_if"></a>replace_copy_if –  
 Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu splňuje zadaný predikát.  
  
```  
template<class InputIterator, class OutputIterator, class Predicate, class Type>  
OutputIterator replace_copy_if(  
    InputIterator first,  
    InputIterator last,  
    OutputIterator result,  
    Predicate pred,  
    const Type& val);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Vstupní iterovat odkazující na pozici prvním elementem v rozsahu, ze kterého se nahrazují elementy.  
  
 `last`  
 Vstupní iterovat odkazující na pozici jeden za poslední element v rozsahu, ze kterého se nahrazují elementy.  
  
 `result`  
 Iterátor výstup odkazující na pozice první prvek v cílový rozsah, do kterého jsou kopírovány elementy.  
  
 `_Pred`  
 Unární predikát, který musí být splněny, je že hodnota elementu má být nahrazen.  
  
 `val`  
 Nová hodnota přiřazeny elementy, jejichž stará hodnota splňuje predikátu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup odkazující na pozici jeden za poslední element v rozsahu cílového do kde kopírovány změnit pořadí elementů.  
  
### <a name="remarks"></a>Poznámky  
 Zdrojové a cílové oblasti odkazuje se nesmí překrývat a musí být platný: musí být všechny ukazatele dereferenceable a v rámci daná pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Pořadí prvků není nahrazena zůstane stabilní.  
  
 `operator==` Používá k určení rovnosti mezi elementy musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Složitost je lineární; Existují ( `last`  -   `first`) porovnání rovnosti a maximálně ( `last`  -   `first`) přiřazení nové hodnoty.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_replace_copy_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
bool greater6 ( int value ) {  
   return value >6;  
}  
  
int main( ) {  
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
  
##  <a name="replace_if"></a>replace_if –  
 Zkontroluje každý prvek v rozsahu a nahradí jej, pokud splňuje zadaný predikát.  
  
```  
template<class ForwardIterator, class Predicate, class Type>  
void replace_if(ForwardIterator first, ForwardIterator last, Predicate pred, const Type& val);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Předat dál iterator odkazující na pozici prvním elementem v rozsahu, ze kterého se nahrazují elementy.  
  
 `last`  
 Iterace odkazující na pozici, jedna po posledním element v rozsahu, ze kterého se nahrazují elementy.  
  
 `_Pred`  
 Unární predikát, který musí být splněny, je že hodnota elementu má být nahrazen.  
  
 `val`  
 Nová hodnota přiřazeny elementy, jejichž stará hodnota splňuje predikátu.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Pořadí prvků není nahrazena zůstane stabilní.  
  
 Algoritmus `replace_if` je generalizace algoritmu **nahradit**, povolení žádné predikát zadat místo rovnosti na zadaný konstantní hodnotu.  
  
 `operator==` Používá k určení rovnosti mezi elementy musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Složitost je lineární: existují ( `last`  -   `first`) porovnání rovnosti a maximálně ( `last`  -   `first`) přiřazení nové hodnoty.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_replace_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater6 ( int value ) {  
   return value >6;  
}  
  
int main( ) {  
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
  
##  <a name="reverse"></a>zpětné  
 Obrátí pořadí prvků v rozsahu.  
  
```  
template<class BidirectionalIterator>  
 void reverse(BidirectionalIterator first, BidirectionalIterator last);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Obousměrné iterator, který odkazuje na pozici prvním elementem v rozsahu, ve kterém elementy jsou právě permutovanou funkci.  
  
 `last`  
 Obousměrné iterator, který odkazuje na pozici jeden za poslední element v rozsahu, ve kterém elementy jsou právě permutovanou funkci.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah zdrojových odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_reverse.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
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
  
##  <a name="reverse_copy"></a>reverse_copy –  
 Obrátí pořadí prvků ve zdrojovém rozsahu při kopírování do cílového rozsahu.  
  
```  
template<class BidirectionalIterator, class OutputIterator>  
OutputIterator reverse_copy(   
    BidirectionalIterator  first,  
    BidirectionalIterator Last,  
    OutputIterator  result);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Obousměrné iterator, který odkazující na pozici první prvek v rámci kterého elementy jsou právě permutovanou funkci zdrojové oblasti.  
  
 `last`  
 Obousměrné iterator, který odkazuje na pozici jeden za poslední element ze zdrojové oblasti, ve kterém elementy jsou právě permutovanou funkci.  
  
 `result`  
 Iterátor výstup odkazující na pozice první prvek v cílový rozsah, do kterého jsou kopírovány elementy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup odkazující na pozici jeden za poslední element v rozsahu cílového do kde kopírovány změnit pořadí elementů.  
  
### <a name="remarks"></a>Poznámky  
 Zdrojové a cílové oblasti odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_reverse_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
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
  
##  <a name="rotate"></a>Otočit  
 Vymění prvky ve dvou sousedních rozsazích.  
  
```  
template<class ForwardIterator>  
 void rotate(ForwardIterator first, ForwardIterator middle, ForwardIterator last);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Předat dál iterator adresování pozice první prvek v rozsahu na otočen.  
  
 `middle`  
 Předat dál iterator definování hranice v rozsahu, který řeší pozice první prvek v druhé části rozsahu, jehož elementy jsou k výměně s těmi, která v první části rozsahu.  
  
`Last`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu na otočen.  
  
### <a name="remarks"></a>Poznámky  
 Rozsahy odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Složitost je lineární s maximálně ( `last`  -   `first`) prohození.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_rotate.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
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
  
   rotate ( v1.begin ( ) , v1.begin ( ) + 3 , v1.end ( ) );  
   cout << "After rotating, vector v1 is ( " ;  
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )  
      cout << *v1Iter1  << " ";  
   cout << ")." << endl;  
  
   cout << "The original deque d1 is ( " ;  
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )  
      cout << *d1Iter1  << " ";  
   cout << ")." << endl;  
  
   int iii = 1;  
   while ( iii <= d1.end ( ) - d1.begin ( ) ) {  
      rotate ( d1.begin ( ) , d1.begin ( ) + 1 , d1.end ( ) );  
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
  
##  <a name="rotate_copy"></a>rotate_copy –  
 Vymění prvky ve dvou sousedních rozsazích v rámci zdrojového rozsahu a zkopíruje výsledek do cílového rozsahu.  
  
```  
template<class ForwardIterator, class OutputIterator>  
OutputIterator rotate_copy(  
    ForwardIterator first,  
    ForwardIterator middle,  
    ForwardIterator last,  
    OutputIterator result );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Předat dál iterator adresování pozice první prvek v rozsahu na otočen.  
  
 `middle`  
 Předat dál iterator definování hranice v rozsahu, který řeší pozice první prvek v druhé části rozsahu, jehož elementy jsou k výměně s těmi, která v první části rozsahu.  
  
 _ `Last`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu na otočen.  
  
 `result`  
 Iterátor výstup adresování pozice první prvek v cílové oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup adresování pozici jeden za poslední element v cílové oblasti.  
  
### <a name="remarks"></a>Poznámky  
 Rozsahy odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Složitost je lineární s maximálně ( `last`  -   `first`) prohození.  
  
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
  
   rotate_copy ( v1.begin ( ) , v1.begin ( ) + 3 , v1.end ( ) , v2.begin ( ) );  
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
   while ( iii <= d1.end ( ) - d1.begin ( ) )  
   {  
      rotate_copy ( d1.begin ( ) , d1.begin ( ) + iii , d1.end ( ) , d2.begin ( ) );  
      cout << "After the rotation of a single deque element to the back,\n d2 is   ( " ;  
      for ( d2Iter = d2.begin( ) ; d2Iter != d2.end( ) ;d2Iter ++ )  
         cout << *d2Iter  << " ";  
      cout << ")." << endl;  
      iii++;  
   }  
}  
```  
  
##  <a name="search"></a>hledání  
 Vyhledá první výskyt sekvence v cílovém rozsahu, jejíž prvky jsou rovné prvkům v dané sekvenci prvků nebo jejíž prvky jsou ekvivalentní ve smyslu určeném binárním predikátem prvkům v dané sekvenci.  
  
```  
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
  `first1`  
 Předat dál iterator adresování pozice první prvek v rozsahu prohledávání.  
  
 `last1`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu prohledávání.  
  
  `first2`  
 Předat dál iterator adresování pozice první prvek v rozsahu lze porovnat.  
  
 `last2`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu lze porovnat.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje podmínku, která má být splněny, pokud dva elementy musí být odebrána jako ekvivalentní. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator adresování pozice první prvek první dalším, který odpovídá zadané pořadí nebo které je ekvivalentní v smyslu uvedená v binární predikátu.  
  
### <a name="remarks"></a>Poznámky  
 `operator==` Používá k určení shody mezi elementem a zadanou hodnotu musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Rozsahy odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci každé pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Průměrná složitost je lineární s ohledem na velikost vyhledávaná oblasti a nejhorší případu složitost je také Lineární s ohledem na velikost pořadí se hledají.  
  
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
  
int main( ) {  
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
  
##  <a name="search_n"></a>search_n –  
 Vyhledá první dílčí sekvenci v rozsahu zadaného počtu prvků s konkrétní hodnotou nebo vztahem k dané hodnotě podle binárního predikátu.  
  
```  
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
  `first1`  
 Předat dál iterator adresování pozice první prvek v rozsahu prohledávání.  
  
 `last1`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu prohledávání.  
  
 `count`  
 Velikost dalším prohledávaný pro.  
  
 `val`  
 Hodnota elementů v pořadí se hledají.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje podmínku, která má být splněny, pokud dva elementy musí být odebrána jako ekvivalentní. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator adresování pozice první prvek první dalším, který odpovídá zadané pořadí nebo které je ekvivalentní v smyslu uvedená v binární predikátu.  
  
### <a name="remarks"></a>Poznámky  
 `operator==` Používá k určení shody mezi elementem a zadanou hodnotu musí použít ekvivalenční vztah mezi jejími operandy.  
  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
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
  
int main( )   
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
  
##  <a name="set_difference"></a>set_difference –  
 Sjednotí všechny prvky, které patří do jednoho seřazeného zdrojového rozsahu, ale nikoli do druhého seřazeného zdrojového rozsahu, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.  
  
```  
 template<class InputIterator1, class InputIterator2, class OutputIterator>  
 OutputIterator set_difference(  
     InputIterator1  first1,  
     InputIterator1  last1,  
     InputIterator2  first2,  
     InputIterator2  last2,  
     OutputIterator  result  );  
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>  
OutputIterator set_difference(  
    InputIterator1  first1,  
    InputIterator1  last1,  
    InputIterator2  first2,  
    InputIterator2  last2,  
    OutputIterator  result,  
    BinaryPredicate  comp  );  
  
```  
  
### <a name="parameters"></a>Parametry  
 `first1`  
 Vstupní iterovat adresování pozice první prvek v první dva seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující rozdíl dvou zdrojových oblastí.  
  
 `last1`  
 Vstupní iterovat adresování pozici jeden za posledním elementem v první dva seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující rozdíl dvou zdrojových oblastí.  
  
 `first2`  
 Vstupní iterovat adresování pozice první prvek za sekundu ze dvou po sobě jdoucích seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující rozdíl dvou zdrojových oblastí.  
  
 `last2`  
 Vstupní iterovat adresování pozici jeden posledních posledním prvkem v druhé ze dvou po sobě jdoucích seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující rozdíl dvou zdrojových oblastí.  
  
 `result`  
 Iterátor výstup adresování pozice první prvek v cílové oblasti, kde mají být spojeny do jednoho seřazené oblasti představující rozdíl dvou zdrojových oblastí dvě zdrojových oblastí.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém je větší než druhý jeden element. Binární predikát má dva argumenty a by měla vrátit **true** při prvním elementem je menší než druhý prvkem a **false** jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup adresování pozice, jedna po posledním prvkem v seřazené cílový rozsah představující rozdíl dvou zdrojových oblastí.  
  
### <a name="remarks"></a>Poznámky  
 Seřazené zdrojových oblastí odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci každé pořadí poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Rozsah cílových nesmí překrývat buď zdrojových oblastí a by měl být dostatečně velký, aby se tak, aby obsahovala první zdrojový rozsah.  
  
 Seřazené zdrojových oblastí musí každý být uspořádány podmínkou pro použití `set_difference` algoritmus v souladu s stejné řazení jako má být použita algoritmem seřadit kombinované rozsahy.  
  
 Operace je stabilní jako relativní pořadí prvků v každém rozsahu se zachová cílový rozsah. Sloučením algoritmus se nemění zdrojových oblastí.  
  
 Hodnota typy vstupní iterátory musí být menší než-porovnatelný z hlediska mají být sdruženy do, tak, aby hodnotě dva elementy, může být zjištěno, že jsou ekvivalentní (v tom smyslu, že ani je menší než druhá) nebo jedna je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou ekvivalentní elementy v obou zdrojových oblastí, před prvky v první oblasti elementy z druhého rozsahu zdroje v cílové oblasti. Pokud zdrojových oblastí obsahovat duplikáty elementu tak, že existuje více v první zdrojový rozsah než za sekundu, pak cílový rozsah bude obsahovat číslo, pomocí kterého výskyty tyto prvky v první oblasti zdroj překročit výskytů Tyto prvky v druhé zdrojový rozsah.  
  
 Složitost algoritmu je lineární s maximálně 2 \* (( *Příjmení1 - first1*) – ( *Příjmení2 - first2*)) – 1 porovnání pro neprázdná zdrojových oblastí.  
  
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
  
int main( )  
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
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );  
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );  
   vector <int>::iterator Iter3a,  Iter3b, Iter3, Result3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser  );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To combine into a difference in asscending  
   // order with the default binary predicate less <int> ( )  
   Result1 = set_difference ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Set_difference of source ranges with default order,"  
        << "\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To combine into a difference in descending  
   // order specify binary predicate greater<int>( )  
   Result2 = set_difference ( v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );  
   cout << "Set_difference of source ranges with binary"  
        << "predicate greater specified,\n vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // To combine into a difference applying a user  
   // defined binary predicate mod_lesser  
   Result3 = set_difference (  v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );  
   cout << "Set_difference of source ranges with binary "  
        << "predicate mod_lesser specified,\n vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="set_intersection"></a>set_intersection –  
 Sjednotí všechny prvky, které náleží do obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.  
  
```  
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
  `first1`  
 Vstupní iterovat adresování pozice první prvek v první dva seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující průnik dvou zdrojových oblastí.  
  
 `last1`  
 Vstupní iterovat adresování pozici jeden za posledním elementem v první dva seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující průnik dvou zdrojových oblastí.  
  
  `first2`  
 Vstupní iterovat adresování pozice první prvek za sekundu ze dvou po sobě jdoucích seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující průnik dvou zdrojových oblastí.  
  
 `last2`  
 Vstupní iterovat adresování pozici jeden posledních posledním prvkem v druhé ze dvou po sobě jdoucích seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující průnik dvou zdrojových oblastí.  
  
 **_** *Výsledek*  
 Iterátor výstup adresování pozice první prvek v cílové oblasti, kde mají být spojeny do jednoho seřazené oblasti představující průnik dvou zdrojových oblastí dvě zdrojových oblastí.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém je větší než druhý jeden element. Binární predikát má dva argumenty a by měla vrátit **true** při prvním elementem je menší než druhý prvkem a **false** jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup adresování pozice, jedna po posledním prvkem v seřazené cílový rozsah představující průnik dvou zdrojových oblastí.  
  
### <a name="remarks"></a>Poznámky  
 Seřazené zdrojových oblastí odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci každé pořadí poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Rozsah cílových nesmí překrývat buď zdrojových oblastí a by měl být dostatečně velký, aby se tak, aby obsahovala cílový rozsah.  
  
 Rozsahy musí každý být uspořádány podmínkou pro aplikace algoritmu sloučení v souladu s stejné řazení jako seřazená zdrojové se má použít algoritmem seřadit kombinované rozsahy.  
  
 Operace je stabilní jako relativní pořadí prvků v každém rozsahu se zachová cílový rozsah. Zdrojových oblastí se nemění algoritmem.  
  
 Typy hodnot ze vstupních iterátory musí být menší – než porovnatelný seřadit, tak, aby hodnotě dva elementy, může být bylo zjištěno, že jsou ekvivalentní (v tom smyslu, že ani je menší než druhá) nebo jedna je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou ekvivalentní elementy v obou zdrojových oblastí, před prvky v první oblasti elementy z druhého rozsahu zdroje v cílové oblasti. Pokud zdrojových oblastí obsahovat duplikáty elementu, bude obsahovat cílový rozsah maximální počet prvků, které ke kterým došlo v obou zdrojových oblastí.  
  
 Složitost algoritmu je lineární s maximálně 2 \* (( *Příjmení1 - first1*) + ( *Příjmení2 - first2*)) – 1 porovnání pro neprázdná zdrojových oblastí.  
  
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
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );  
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        << "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        << "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );  
   vector <int>::iterator Iter3a,  Iter3b, Iter3, Result3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
           <<  "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To combine into an intersection in asscending order with the  
   // default binary predicate less <int> ( )  
   Result1 = set_intersection ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Intersection of source ranges with default order,"  
        << "\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; ++Iter1 )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To combine into an intersection in descending order, specify  
   // binary predicate greater<int>( )  
   Result2 = set_intersection ( v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );  
   cout << "Intersection of source ranges with binary predicate"  
        << " greater specified,\n vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; ++Iter2 )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // To combine into an intersection applying a user-defined  
   // binary predicate mod_lesser  
   Result3 = set_intersection ( v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );  
   cout << "Intersection of source ranges with binary predicate "  
        << "mod_lesser specified,\n vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; ++Iter3 )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="set_symmetric_difference"></a>set_symmetric_difference –  
 Sjednotí všechny prvky, které náleží do jednoho, ale nikoli obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.  
  
```  
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
  `first1`  
 Vstupní iterovat adresování pozice první prvek v první dva seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující symetrický rozdíl dvou zdrojových oblastí.  
  
 `last1`  
 Vstupní iterovat adresování pozici jeden za posledním elementem v první dva seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující symetrický rozdíl dvou zdrojových oblastí.  
  
  `first2`  
 Vstupní iterovat adresování pozice první prvek za sekundu ze dvou po sobě jdoucích seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující symetrický rozdíl dvou zdrojových oblastí.  
  
 `last2`  
 Vstupní iterovat adresování pozici jeden posledních posledním prvkem v druhé ze dvou po sobě jdoucích seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující symetrický rozdíl dvou zdrojových oblastí.  
  
 **_** *Výsledek*  
 Iterátor výstup adresování pozice první prvek v cílové oblasti, kde mají být spojeny do jednoho seřazené oblasti představující symetrický rozdíl dvou zdrojových oblastí dvě zdrojových oblastí.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém je větší než druhý jeden element. Binární predikát má dva argumenty a by měla vrátit **true** při prvním elementem je menší než druhý prvkem a **false** jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup adresování pozice jeden po posledním prvkem v seřazené cílový rozsah představující symetrický rozdíl dvou zdrojových oblastí.  
  
### <a name="remarks"></a>Poznámky  
 Seřazené zdrojových oblastí odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci každé pořadí poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Rozsah cílových nesmí překrývat buď zdrojových oblastí a by měl být dostatečně velký, aby se tak, aby obsahovala cílový rozsah.  
  
 Seřazené zdrojových oblastí musí každý být uspořádány podmínkou pro použití **sloučení** algoritmus v souladu s stejné řazení jako má být použita algoritmem seřadit kombinované rozsahy.  
  
 Operace je stabilní jako relativní pořadí prvků v každém rozsahu se zachová cílový rozsah. Sloučením algoritmus se nemění zdrojových oblastí.  
  
 Typy hodnot ze vstupních iterátory musí být menší – než porovnatelný seřadit, tak, aby hodnotě dva elementy, může být bylo zjištěno, že jsou ekvivalentní (v tom smyslu, že ani je menší než druhá) nebo jedna je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou ekvivalentní elementy v obou zdrojových oblastí, před prvky v první oblasti elementy z druhého rozsahu zdroje v cílové oblasti. Pokud zdrojových oblastí obsahovat duplikáty elementu, pak cílový rozsah bude obsahovat absolutní hodnotu čísla, pomocí kterého výskyty těchto elementů do jedné ze zdrojových oblastí překračuje výskyty těchto elementů ve zdroji druhý rozsah.  
  
 Složitost algoritmu je lineární s maximálně 2 \* ((*Příjmení1 - first1*) – (*Příjmení2 - first2*)) – 1 porovnání pro neprázdná zdrojových oblastí.  
  
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
  
int main( )  
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
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );  
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );  
   vector <int>::iterator Iter3a, Iter3b, Iter3, Result3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser  );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To combine into a symmetric difference in ascending  
   // order with the default binary predicate less <int> ( )  
   Result1 = set_symmetric_difference ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Set_symmetric_difference of source ranges with default order,"  
        << "\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To combine into a symmetric difference in descending  
   // order, specify binary predicate greater<int>( )  
   Result2 = set_symmetric_difference ( v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );  
   cout << "Set_symmetric_difference of source ranges with binary"  
        << "predicate greater specified,\n vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // To combine into a symmetric difference applying a user  
   // defined binary predicate mod_lesser  
   Result3 = set_symmetric_difference ( v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );  
   cout << "Set_symmetric_difference of source ranges with binary "  
        << "predicate mod_lesser specified,\n vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="set_union"></a>set_union –  
 Sjednotí všechny prvky, které náleží alespoň do jednoho ze dvou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.  
  
```  
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
  `first1`  
 Vstupní iterovat adresování pozice první prvek v první dva seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující sjednocení dvou zdrojových oblastí.  
  
 `last1`  
 Vstupní iterovat adresování pozici jeden za posledním elementem v první dva seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující sjednocení dvou zdrojových oblastí.  
  
  `first2`  
 Vstupní iterovat adresování pozice první prvek za sekundu ze dvou po sobě jdoucích seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující sjednocení dvou zdrojových oblastí.  
  
 `last2`  
 Vstupní iterovat adresování pozici jeden posledních posledním prvkem v druhé ze dvou po sobě jdoucích seřazené zdrojových oblastí spojené a rozděleny na jeden rozsah představující sjednocení dvou zdrojových oblastí.  
  
 **_** *Výsledek*  
 Iterátor výstup adresování pozice první prvek v cílové oblasti, kde mají být spojeny do jednoho seřazené oblasti představující sjednocení dvou zdrojových oblastí dvě zdrojových oblastí.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém je větší než druhý jeden element. Binární predikát má dva argumenty a by měla vrátit **true** při prvním elementem je menší než druhý prvkem a **false** jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup adresování pozice, jedna po posledním prvkem v seřazené cílový rozsah představující sjednocení dvou zdrojových oblastí.  
  
### <a name="remarks"></a>Poznámky  
 Seřazené zdrojových oblastí odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci každé pořadí poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Rozsah cílových nesmí překrývat buď zdrojových oblastí a by měl být dostatečně velký, aby se tak, aby obsahovala cílový rozsah.  
  
 Seřazené zdrojových oblastí musí každý být uspořádány podmínkou pro použití **sloučení** algoritmus v souladu s stejné řazení jako má být použita algoritmem seřadit kombinované rozsahy.  
  
 Operace je stabilní jako relativní pořadí prvků v každém rozsahu se zachová cílový rozsah. Zdrojových oblastí se nemění algoritmem **sloučení**.  
  
 Typy hodnot ze vstupních iterátory musí být menší – než porovnatelný seřadit, tak, aby hodnotě dva elementy, může být bylo zjištěno, že jsou ekvivalentní (v tom smyslu, že ani je menší než druhá) nebo jedna je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Pokud jsou ekvivalentní elementy v obou zdrojových oblastí, před prvky v první oblasti elementy z druhého rozsahu zdroje v cílové oblasti. Pokud zdrojových oblastí obsahovat duplikáty elementu, bude obsahovat cílový rozsah maximální počet prvků, které ke kterým došlo v obou zdrojových oblastí.  
  
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
  
int main( )  
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
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );  
   vector <int>::iterator Iter2a,  Iter2b, Iter2, Result2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );  
   vector <int>::iterator Iter3a, Iter3b, Iter3, Result3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser  );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To combine into a union in ascending order with the default   
    // binary predicate less <int> ( )  
   Result1 = set_union ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Union of source ranges with default order,"  
        << "\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To combine into a union in descending order, specify binary   
   // predicate greater<int>( )  
   Result2 = set_union (  v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );  
   cout << "Union of source ranges with binary predicate greater "  
        << "specified,\n vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // To combine into a union applying a user-defined  
   // binary predicate mod_lesser  
   Result3 = set_union ( v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );  
   cout << "Union of source ranges with binary predicate "  
        << "mod_lesser specified,\n vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="shuffle"></a>std::Shuffle  
 Prvky podle okolí posouvá (změní uspořádání) pro zadaný rozsah pomocí generování náhodných čísel.  
  
```  
template<class RandomAccessIterator, class UniformRandomNumberGenerator>  
void shuffle(RandomAccessIterator first,  
    RandomAccessIterator last,  
    UniformRandomNumberGenerator&& gen);  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Iterator na prvním elementem v rozsahu být nesprávně umístěný, včetně. Musí splňovat požadavky na `RandomAccessIterator` a `ValueSwappable`.  
  
 `last`  
 Iterator na posledním prvkem v rozsahu být nesprávně umístěný, výhradní. Musí splňovat požadavky na `RandomAccessIterator` a `ValueSwappable`.  
  
 `gen`  
 Generátoru náhodných čísel, `shuffle()` funkce bude používat pro operaci. Musí splňovat požadavky `UniformRandomNumberGenerator`.  
  
### <a name="remarks"></a>Poznámky  
 Další informace a ukázku kódu, který používá `shuffle()`, najdete v části [ \<náhodných >](../standard-library/random.md).  
  
##  <a name="sort"></a>řazení  
 Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.  
  
```  
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
 `first`  
 Náhodným přístupem iterator adresování pozice první prvek v rozsahu k řazení.  
  
 `last`  
 Náhodným přístupem iterator adresování pozici jeden za poslední element v rozsahu který se má seřadit.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje kritéria porovnání měly splňovat po sobě následujících elementů v řazení. Tento binární predikát má dva argumenty a vrátí `true` Pokud dva argumenty, které jsou v pořadí a `false` jinak. Tato funkce komparátoru musí použít striktní slabé řazení na páry elementů z pořadí. Další informace najdete v tématu [algoritmy](../standard-library/algorithms.md).  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Elementy jsou ekvivalentní, ale nemusí nutně jít rovná, pokud je menší než druhý. `sort` Algoritmus není stabilní a proto není zaručeno, že relativní řazení ekvivalentní elementy se zachovají. Algoritmus `stable_sort` zachovat původní řazení.  
  
 Průměr složitost řazení je *O*( *N* protokolu *N*), kde *N* =  *poslední – první*.  
  
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
  
int main( )  
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
  
##  <a name="sort_heap"></a>sort_heap –  
 Převede haldu na seřazený rozsah.  
  
```  
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
  `first`  
 Náhodným přístupem iterator adresování pozice první prvek v haldě cíl.  
  
 `last`  
 Adresování pozici jeden za poslední element v haldě cíl iterator náhodný přístup.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém jeden element je menší než jiné. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="remarks"></a>Poznámky  
 Haldách mít dvě vlastnosti:  
  
-   První prvek je vždy na největší.  
  
-   Elementy může přidat nebo odebrat logaritmické včas.  
  
 Po aplikaci, pokud tento algoritmus, rozsah byla použita k už není haldy.  
  
 Toto není stabilní řazení, protože není nutně zachovávané relativní pořadí ekvivalentní elementy.  
  
 Haldách jsou nejvhodnější způsob implementace priority fronty a jejich použití k implementaci adaptéru kontejneru standardní knihovna C++ [priority_queue – třída](../standard-library/priority-queue-class.md).  
  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Složitost je maximálně *N* protokolu *N*, kde *N* = ( *poslední - nejprve*).  
  
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
  
##  <a name="stable_partition"></a>stable_partition –  
 Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují. Relativní pořadí ekvivalentních prvků je zachováno.  
  
```  
template<class BidirectionalIterator, class Predicate>  
BidirectionalIterator stable_partition(  
    BidirectionalIterator first,  
    BidirectionalIterator last,  
    Predicate pred );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Obousměrné iterator adresování pozice první prvek v rozsahu k rozdělení na oddíly.  
  
 `last`  
 Obousměrné iterator adresování pozici jeden za poslední element v rozsahu k rozdělení na oddíly.  
  
 `_Pred`  
 Uživatelem definované funkce predikátu objekt, který definuje podmínku, která má uspokojit, pokud je element klasifikovat. Predikát jeden argument a vrátí **true** nebo **false**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Obousměrné iterator adresování pozice první prvek v rozsahu není vyhovět podmínka predikátu.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Elementy *a* a *b* jsou ekvivalentní, ale stejně nemusí nutně prokázat, pokud obě *Pr* ( *a*, *b*) je hodnota false a *Pr* ( *b*, *a*) Pokud je hodnota false, kde *Pr* je zadán parametr predikátu. **Stable_ oddílu** algoritmus stabilní a zaručí, že relativní řazení ekvivalentní elementy se zachovají. Algoritmus **oddílu** nemusí zachovat původní řazení.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_stable_partition.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater5 ( int value ) {  
   return value >5;  
}  
  
int main( ) {  
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
  
##  <a name="stable_sort"></a>stable_sort –  
 Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem a zachová relativní pořadí ekvivalentních prvků.  
  
```  
template<class BidirectionalIterator>  
 void stable_sort( BidirectionalIterator first, BidirectionalIterator last );  
  
template<class BidirectionalIterator, class BinaryPredicate>  
void stable_sort(   
    BidirectionalIterator first,  
    BidirectionalIterator last,   
    BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Obousměrné iterator adresování pozice první prvek v rozsahu k řazení.  
  
 `last`  
 Obousměrné iterator adresování pozici jeden za poslední element v rozsahu k řazení.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje kritéria porovnání měly splňovat po sobě následujících elementů v řazení. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace.  
  
 Elementy jsou ekvivalentní, ale nemusí nutně jít rovná, pokud je menší než druhý. **Řazení** algoritmus stabilní a zaručí, že relativní řazení ekvivalentní elementy se zachovají.  
  
 Spuštění složitosti `stable_sort` závisí na množství paměti k dispozici, ale je doporučené případ (přiděleno dostatek paměti) *O*( *N* protokolu *N*) a nejhorším případě je *O*( *N* (protokolu *N* ) 2), kde *N* =  *příjmení - jméno.* Obvykle **řazení** algoritmus je mnohem rychlejší než `stable_sort`.  
  
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
  
int main( )  
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
  
##  <a name="swap"></a>swap  
 První přepsání výměny hodnoty dva objekty. Druhý přepsání výměny hodnoty mezi dvěma poli objektů.  
  
```  
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
 `left`  
 Pro první přepsání tak, aby měl obsah vyměňují první objekt. Pro druhý přepsání objektů, které chcete mít jeho obsah vyměňují první pole.  
  
 `right`  
 Pro první přepsání druhý objekt, který má mít jeho obsah vyměňují. Pro druhý přepsání druhé pole objektů, které chcete mít jeho obsah vyměňují.  
  
### <a name="remarks"></a>Poznámky  
 První přetížení navržený pro použití na jednotlivých objektů. Druhý přetížení prohození obsah objektů mezi dvěma poli.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_swap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( )   
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
  
##  <a name="swap_ranges"></a>swap_ranges –  
 Vymění prvky z jednoho rozsahu za prvky druhého rozsahu o stejné velikosti.  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
ForwardIterator2 swap_ranges(   
   ForwardIterator1 first1,  
   ForwardIterator1 last1,  
   ForwardIterator2 first2 );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Předat dál iterator odkazující na první pozici první oblasti, jehož elementy jsou k výměně.  
  
 `last1`  
 Předat dál iterator odkazující na jednu za poslední pozice první oblasti, jehož elementy jsou k výměně.  
  
  `first2`  
 Předat dál iterator odkazující na první pozici druhého rozsahu, jehož elementy jsou k výměně.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator odkazující na jednu po posledním pozici druhého rozsahu, jehož elementy jsou k výměně.  
  
### <a name="remarks"></a>Poznámky  
 Rozsahy odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci každé pořadí se poslední pozice dosažitelný z první podle Inkrementace. Druhého rozsahu musí být větší než první rozsahu.  
  
 Složitost je lineární s `last1`  -   `first1` záměna provést. Pokud elementy z kontejnerů stejného typu se prohazují, je `swap` členské funkce kontejneru, v němž by měl použít, protože funkce člen má obvykle konstantní složitost.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// alg_swap_ranges.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
  
int main( )   
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
  
   swap_ranges ( v1.begin ( ) , v1.end ( ) , d1.begin ( ) );  
  
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
  
##  <a name="transform"></a>transformace  
 Aplikuje zadaný objekt funkce na každý prvek ve zdrojovém rozsahu nebo na dvojici prvků ze dvou zdrojových rozsahů a zkopíruje vrácené hodnoty objektu funkce do cílového rozsahu.  
  
```  
 template<class InputIterator, class OutputIterator, class UnaryFunction>  
 OutputIterator transform(  
    InputIterator first1,  
    InputIterator last1,  
    OutputIterator result,  
    UnaryFunction _Func );  
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryFunction>  
OutputIterator transform(   
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    OutputIterator result,  
    BinaryFunction _Func );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Vstupní iterovat adresování pozice první prvek v provozu na první rozsahu zdroje.  
  
 `last1`  
 Vstupní iterovat adresování pozici jeden za poslední element v první zdrojový rozsah zpracovat.  
  
  `first2`  
 Vstupní iterovat adresování pozice první prvek v druhé zdrojový rozsah ovládání na.  
  
 `result`  
 Iterátor výstup adresování pozice první prvek v cílové oblasti.  
  
 `_Func`  
 Unární uživatelem definované funkce objekt použitý v první verzi algoritmus, který se použije pro každý prvek v první zdrojový rozsah nebo použít v druhé verzi algoritmus, který se použije, ukládání popořadě objekt definovaný uživatelem binární – funkce (UD) , na dvě zdrojových oblastí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup adresování pozici jeden za poslední element v cílovém rozsahu, který přijímá výstup elementy transformovat objekt funkce.  
  
### <a name="remarks"></a>Poznámky  
 Rozsahy odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci každé pořadí poslední pozice musí být dosažitelný z první podle Inkrementace. Cílový rozsah musí být dostatečně velký, aby se tak, aby obsahovala transformovaných zdrojový rozsah.  
  
 Pokud `result` nastavena na hodnotu `first1` v první verzi algoritmus, pak zdrojové a cílové oblasti budou stejné a sekvenci se změní na místě. Ale `result` nemusí adres pozici v rozsahu [`first1` + 1, `last1`).  
  
 Složitost je lineární s maximálně (`last1` -  `first1`) porovnání.  
  
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
      Type operator ( ) ( Type& elem ) const   
      {  
         return elem * Factor;  
      }  
};  
  
int main( )  
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
   transform (v1.begin ( ) , v1.end ( ) , v1.begin ( ) , MultValue<int> ( 2 ) );  
   cout << "The elements of the vector v1 multiplied by 2 in place gives:"  
        << "\n v1mod = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Using transform to multiply each element by a factor of 5  
   transform ( v1.begin ( ) , v1.end ( ) , v2.begin ( ) , MultValue<int> ( 5 ) );  
  
   cout << "Multiplying the elements of the vector v1mod\n "  
        <<  "by the factor 5 & copying to v2 gives:\n v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // The second version of transform used to multiply the   
   // elements of the vectors v1mod & v2 pairwise  
   transform ( v1.begin ( ) , v1.end ( ) ,  v2.begin ( ) , v3.begin ( ) ,   
      multiplies <int> ( ) );  
  
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
  
##  <a name="unique"></a>jedinečné  
 Odstraní duplicitní prvky, které v zadaném rozsahu sousedí.  
  
```  
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
  `first`  
 Předat dál iterator adresování pozice první prvek v rozsahu vyhledávat duplicitní odebrání.  
  
 `last`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsahu vyhledávat duplicitní odebrání.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje podmínku, která má být splněny, pokud dva elementy musí být odebrána jako ekvivalentní. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator nové konec změny pořadí, které obsahuje žádné duplikáty po sobě jdoucích adresování jednoho pozice za posledním elementem neodeberou.  
  
### <a name="remarks"></a>Poznámky  
 Obě formy algoritmus odebrat druhý duplicitní po sobě jdoucích páru ekvivalentní elementy.  
  
 Operace algoritmu je stabilní, tak, aby relativní pořadí neodstraněných prvků se nezmění.  
  
 Rozsah odkazuje musí být platná. musí být všechny ukazatele dereferenceable a v rámci pořadí se poslední pozice dosažitelný z první podle Inkrementace. počet elementů v pořadí mu není změnit algoritmem **jedinečný** a prvky přesahuje za konec změny pořadí jsou dereferenceable, ale není zadaný.  
  
 Složitost je lineární, které vyžadují ( `last`  -   `first`) – 1 porovnání.  
  
 Seznam obsahuje člena efektivnější funkce "jedinečné", který může provádět lépe.  
  
 Tyto algoritmy nelze použít na asociativní kontejneru.  
  
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
  
int main( )  
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
   v1_NewEnd1 = unique ( v1.begin ( ) , v1.end ( ) );  
  
   cout << "Removing adjacent duplicates from vector v1 gives\n ( " ;  
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )  
      cout << *v1_Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove consecutive duplicates under the binary prediate mod_equals  
   v1_NewEnd2 = unique ( v1.begin ( ) , v1_NewEnd1 , mod_equal );  
  
   cout << "Removing adjacent duplicates from vector v1 under the\n "  
        << " binary predicate mod_equal gives\n ( " ;  
   for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )  
      cout << *v1_Iter2 << " ";  
   cout << ")." << endl;  
  
   // Remove elements if preceded by an element that was greater  
   v1_NewEnd3 = unique ( v1.begin ( ) , v1_NewEnd2, greater<int>( ) );  
  
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
  
##  <a name="unique_copy"></a>unique_copy –  
 Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu s výjimkou sousedících duplicitních prvků.  
  
```  
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
  `first`  
 Předat dál iterator pozice první prvek v zdrojový rozsah adres ke kopírování.  
  
 `last`  
 Předat dál iterator adresování pozici jeden za poslední element v rozsah zdrojových ke kopírování.  
  
 `result`  
 Iterátor výstup adresování pozice první prvek v cílovém rozsahu, který přijímá kopírování s po sobě jdoucích duplikáty odebrat.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje podmínku, která má být splněny, pokud dva elementy musí být odebrána jako ekvivalentní. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup adresování pozici jeden za poslední element v cílovém rozsahu, který přijímá kopírování s po sobě jdoucích duplikáty odebrat.  
  
### <a name="remarks"></a>Poznámky  
 Obě formy algoritmus odebrat druhý duplicitní po sobě jdoucích páru ekvivalentní elementy.  
  
 Operace algoritmu je stabilní, tak, aby relativní pořadí neodstraněných prvků se nezmění.  
  
 Rozsahy odkazuje musí být platná; musí být všechny ukazatele dereferenceable a v rámci posloupnosti je dostupný z první poslední pozice podle Inkrementace.  
  
 Složitost je lineární, které vyžadují ( `last`  -   `first`) porovnání.  
  
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
   v1_NewEnd1 = unique_copy ( v1.begin ( ) , v1.begin ( ) + 8, v1.begin ( ) + 8 );  
  
   cout << "Copying the first half of the vector to the second half\n "  
        << "while removing adjacent duplicates gives\n ( " ;  
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )  
      cout << *v1_Iter1 << " ";  
   cout << ")." << endl;  
  
   int iv;  
   for ( iv = 0 ; iv <= 7 ; iv++ )  
      v1.push_back( 10 );  
  
   // Remove consecutive duplicates under the binary prediate mod_equals  
   v1_NewEnd2 = unique_copy ( v1.begin ( ) , v1.begin ( ) + 14,   
      v1.begin ( ) + 14 , mod_equal );  
  
   cout << "Copying the first half of the vector to the second half\n "  
        << " removing adjacent duplicates under mod_equals gives\n ( " ;  
   for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )  
      cout << *v1_Iter2 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="upper_bound"></a>upper_bound –  
 Najde pozici prvního prvku v seřazeném rozsahu, který má hodnotu větší než zadaná hodnota, kde kritérium pořadí může být určeno binárním predikátem.  
  
```  
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
 `first`  
 Pozice první prvek v rozsahu prohledávání.  
  
 `last`  
 Pozice jeden za poslední element v rozsahu prohledávání.  
  
 `value`  
 Hodnota v seřazené rozsahu, který musí být překročen hodnotou elementu používala iterator vrátila.  
  
 `comp`  
 Uživatelem definované funkce predikátu objekt, který definuje smysl, ve kterém jeden element je menší než jiné. Binární predikát má dva argumenty a vrátí **true** při a **false** při není.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předat dál iterator na pozici první prvek, který obsahuje hodnotu větší než zadaná hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Seřazené zdrojový rozsah odkazuje musí být platná; musí být všechny iterátory dereferenceable a v rámci pořadí poslední pozice musí být dosažitelný z první podle Inkrementace.  
  
 Seřazené oblasti je podmínkou pro použití `upper_bound` a kde kritérium řazení je stejný jako u binární predikátu.  
  
 Není v rozsahu upraveném `upper_bound`.  
  
 Typy hodnot dopředného iterátorů musí být menší – než porovnatelný seřadit, tak, aby hodnotě dva elementy, může být bylo zjištěno, že jsou ekvivalentní (v tom smyslu, že ani je menší než druhá) nebo jedna je menší než druhý. To vede řazení mezi nonequivalent elementy  
  
 Složitost algoritmu je logaritmické pro iterátory náhodný přístup a lineární, jinak se počet kroků úměrná ( `last - first`).  
  
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
  
int main( )  
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
## <a name="see-also"></a>Viz také   
 [\<algoritmus >](../standard-library/algorithm.md)