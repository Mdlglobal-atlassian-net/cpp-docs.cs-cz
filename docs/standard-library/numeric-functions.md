---
title: '&lt;číselné&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::partial_sum
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
helpviewer_keywords:
- std::accumulate [C++]
- std::adjacent_difference [C++]
- std::inner_product [C++]
- std::iota [C++]
- std::partial_sum [C++]
ms.openlocfilehash: 6df37cf4f6c8afe09f25550d4fc0d9acb553ac52
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236547"
---
# <a name="ltnumericgt-functions"></a>&lt;číselné&gt; funkce

||||
|-|-|-|
|[accumulate](#accumulate)|[adjacent_difference](#adjacent_difference)|[inner_product](#inner_product)|
|[iota](#iota)|[partial_sum](#partial_sum)|

## <a name="accumulate"></a>  accumulate

Vypočítá součet všech prvků v zadaném rozsahu, včetně některých počátečních hodnot výpočtem po sobě jdoucích částečných součtů nebo vypočítá výsledek po sobě jdoucích částečných výsledků podobně získaných pomocí zadané binární operace, než součtem.

```cpp
template <class InputIterator, class Type>
Type accumulate(InputIterator first, InputIterator last, Type val);

template <class InputIterator, class Type, class BinaryOperation>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type val,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor adresující první prvek v rozsahu třeba sečítá nebo zkombinován podle zadané binární operace.

*last*<br/>
Vstupní iterátor adresující poslední prvek v rozsahu se sčítat ani zkombinován podle zadané binární operace, které je o jednu pozici za posledním prvkem, který je skutečně zahrnut do iterovaného souhrnu.

*Val*<br/>
Počáteční hodnota, ke kterému každý element je pak přidat nebo v kombinaci s podle zadané binární operace.

*binary_op*<br/>
Binární operace, která se použije na každý prvek v zadaném rozsahu a výsledek jeho předchozími verzemi.

### <a name="return-value"></a>Návratová hodnota

Součet *val* a všechny prvky v zadaném rozsahu pro první funkce šablony, nebo jako druhá funkce šablony, výsledek použití binární operace místo operace součtu, zadaný do (  *PartialResult, \*Iter*), kde *PartialResult* je výsledkem předchozí žádosti operace a `Iter` je iterátorem ukazujícím na prvek v rozsahu.

### <a name="remarks"></a>Poznámky

Počáteční hodnota zajistí, že bude dobře definovaných výsledek při rozsahu je prázdný, v takovém případě *val* je vrácena. Binární operace nemusí být asociativní ani komutativní. Výsledkem je inicializován na počáteční hodnotu *val* a potom *výsledek*  =  `binary_op` ( *výsledek*, <strong>\*</strong> `Iter`) se počítá interaktivně pomocí rozsahu, kde `Iter` je iterátorem ukazujícím na po sobě jdoucích prvek v rozsahu. Rozsah musí být platná a složitost je lineární s velikostí rozsahu. Návratový typ binárního operátoru musí být převeditelný na **typ** zajistit, že během iterace.

### <a name="example"></a>Příklad

```cpp
// numeric_accum.cpp
// compile with: /EHsc
#include <vector>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2(20);
   vector <int>::iterator iter1, iter2;

   int i;
   for (i = 1; i < 21; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   // The first member function for the accumulated sum
   int total;
   total = accumulate(v1.begin(), v1.end(), 0);

   cout << "The sum of the integers from 1 to 20 is: "
        << total << "." << endl;

   // Constructing a vector of partial sums
   int j = 0, partotal;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      partotal = accumulate(v1.begin(), iter1 + 1, 0);
      v2[j] = partotal;
      j++;
   }

   cout << "The vector of partial sums is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function for the accumulated product
   vector <int> v3, v4(10);
   vector <int>::iterator iter3, iter4;

   int s;
   for (s = 1; s < 11; s++)
   {
      v3.push_back(s);
   }

   cout << "The original vector v3 is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl;

   int ptotal;
   ptotal = accumulate(v3.begin(), v3.end(), 1, multiplies<int>());

   cout << "The product of the integers from 1 to 10 is: "
        << ptotal << "." << endl;

   // Constructing a vector of partial products
   int k = 0, ppartotal;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++) {
      ppartotal = accumulate(v3.begin(), iter3 + 1, 1, multiplies<int>());
      v4[k] = ppartotal;
      k++;
   }

   cout << "The vector of partial products is:\n ( " ;
   for (iter4 = v4.begin(); iter4 != v4.end(); iter4++)
      cout << *iter4 << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The sum of the integers from 1 to 20 is: 210.
The vector of partial sums is:
( 1 3 6 10 15 21 28 36 45 55 66 78 91 105 120 136 153 171 190 210 ).

The original vector v3 is:
( 1 2 3 4 5 6 7 8 9 10 ).
The product of the integers from 1 to 10 is: 3628800.
The vector of partial products is:
( 1 2 6 24 120 720 5040 40320 362880 3628800 ).
```

## <a name="adjacent_difference"></a>  adjacent_difference

Vypočítá po sobě následující rozdíly mezi každým prvkem a jeho předchůdcem ve vstupním rozsahu a vydá výsledky do cílového rozsahu nebo vypočte výsledek zobecněné procedury, kde je operace rozdílu nahrazena jinou zadanou binární operací.

```cpp
template <class InputIterator, class OutIterator>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIterator, class BinaryOperation>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor adresující první prvek ve vstupním rozsahu, jehož prvky mají být diferencovány s příslušnými předchůdci nebo ve kterém použije dvojice hodnot jiná zadaná binární operace.

*last*<br/>
Vstupní iterátor adresující poslední prvek ve vstupním rozsahu, jehož prvky mají být diferencovány s příslušnými předchůdci nebo ve kterém použije dvojice hodnot jiná zadaná binární operace.

*výsledek*<br/>
Vstupní iterátor adresující první prvek v cílovém rozsahu, ve kterém se uloží série rozdílů nebo výsledky zadané operace.

*binary_op*<br/>
Binární operace, která se použije v zobecněné operaci nahrazující operace odčítání v rozdílové proceduře.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterace adresující konec cílového rozsahu: `result` + ( `last`  -  `first`).

### <a name="remarks"></a>Poznámky

Výstupní iterátor _ *výsledek* může být stejným iterátorem jako vstupní iterátor * první, * tak, aby `adjacent_difference`mohou být vypočítány na místě.

Pro sekvenci hodnot *a*1, *a*2, *a*3, ukládá ve vstupním rozsahu, první funkce šablony po sobě jdoucích `partial_difference`s *a*1 , *a*2 - *a*1, a3 – *a*2 v cílovém rozsahu.

Pro sekvenci hodnot *a*1, *a*2, *a*3, ukládá ve vstupním rozsahu, druhá funkce šablony po sobě jdoucích `partial_difference`s *a* 1, *a*2 `binary_op` *a*1, *a*3 `binary_op` *a*2 v cílovém rozsahu.

Binární operace `binary_op` nemusí být asociativní ani komutativní, protože se vztahuje pořadí operací je zcela určeno.

### <a name="example"></a>Příklad

```cpp
// numeric_adj_diff.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend, LIterend2;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t * t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the adjacent_differences of
   // elements in a list output to a vector
   VIterend = adjacent_difference ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "Output vector containing adjacent_differences is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the adjacent products of the elements in a list
   VIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the adjacent products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of adjacent_differences in place
   LIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "In place output adjacent_differences in list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend2 ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="inner_product"></a>  inner_product –

Vypočítá součet prvků produktu ve dvou rozsazích a přidá ji do zadané počáteční hodnotě nebo vypočítá výsledek zobecněné procedury, kde jsou binární operace součtu a produktu nahrazeny jinými zadanými binárními operacemi.

```cpp
template <class InputIterator1, class InputIterator2, class Type>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             val);

template <class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             val,
    BinaryOperation1  binary_op1,
    BinaryOperation2  binary_op2);
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Vstupní iterátor adresující první prvek v první rozsahu, jehož vnitřní nebo produkt zobecněný vnitřní pomocí druhého rozsahu se vypočítat.

*last1*<br/>
Vstupní iterátor adresující poslední prvek v první rozsahu, jehož vnitřní nebo produkt zobecněný vnitřní pomocí druhého rozsahu se vypočítat.

*first2*<br/>
Vstupní iterátor adresující první prvek v druhého rozsahu, jehož vnitřní nebo produkt zobecněný vnitřní s prvním rozsah má vypočítat.

*Val*<br/>
Počáteční hodnotu, ke kterému vnitřní nebo produkt zobecněný vnitřní mezi oblastí se má přidat.

*binary_op1*<br/>
Binární operace, která nahrazuje produktu vnitřní operace součtu element-wise produkty v generalizace vnitřní produktu.

*binary_op2*<br/>
Binární operace, která nahrazuje vnitřní produktu element-wise operace násobení v generalizace vnitřní produktu.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí součet element-wise produkty a přidá do ní zadaná počáteční hodnota. Ano pro rozsahy hodnot *a*i a *b*i, vrátí hodnotu:

`val` + ( *a*1 \* *b*1) + ( *a*2 \* *b*2) +... + ( *a*n \* *b*n)

Využívejte iterativní nahrazením *val* s `val` + ( *a*i \* *b*i ).

Druhá členská funkce vrátí:

`val` *binary_op1* ( *a*1 *binary_op2* *b*1 ) *binary_op1* ( *a*2 *binary_op2* *b*2 ) *binary_op1* ... *binary_op1* ( *a*n *binary_op2* *b*n )

Využívejte iterativní nahrazením *val* s `val` *binary_op1* ( *a*i *binary_op2* *b*i ).

### <a name="remarks"></a>Poznámky

Počáteční hodnota zajistí, že bude dobře definovaných výsledek při rozsahu je prázdný, v takovém případě *val* je vrácena. Binární operace nemusí být asociativní ani komutativní. Rozsah musí být platná a složitost je lineární s velikostí rozsahu. Návratový typ binárního operátoru musí být převeditelný na **typ** zajistit, že během iterace.

### <a name="example"></a>Příklad

```cpp
// numeric_inner_prod.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main()
{
   using namespace std;

   vector <int> v1, v2(7), v3(7);
   vector <int>::iterator iter1, iter2, iter3;

   int i;
   for (i = 1; i <= 7; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   list <int> l1, l2(7);
   list <int>::iterator lIter1, lIter2;

   int t;
   for (t = 1; t <= 7; t++)
   {
      l1.push_back(t);
   }

   cout << "The original list l1 is:\n ( " ;
   for (lIter1 = l1.begin(); lIter1 != l1.end(); lIter1++)
      cout << *lIter1 << " ";
   cout << ")." << endl;

   // The first member function for the inner product
   int inprod;
   inprod = inner_product(v1.begin(), v1.end(), l1.begin(), 0);

   cout << "The inner_product of the vector v1 and the list l1 is: "
        << inprod << "." << endl;

   // Constructing a vector of partial inner_products between v1 & l1
   int j = 0, parinprod;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++) {
      parinprod = inner_product(v1.begin(), iter1 + 1, l1.begin(), 0);
      v2[j] = parinprod;
      j++;
   }

   cout << "Vector of partial inner_products between v1 & l1 is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function used to compute
   // the product of the element-wise sums
   int inprod2;
   inprod2 = inner_product (v1.begin(), v1.end(),
      l1.begin(), 1, multiplies<int>(), plus<int>());

   cout << "The sum of the element-wise products of v1 and l1 is: "
        << inprod2 << "." << endl;

   // Constructing a vector of partial sums of element-wise products
   int k = 0, parinprod2;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      parinprod2 =
         inner_product(v1.begin(), iter1 + 1, l1.begin(), 1,
         multiplies<int>(), plus<int>());
      v3[k] = parinprod2;
      k++;
   }

   cout << "Vector of partial sums of element-wise products is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl << endl;
}
```

## <a name="iota"></a>  iota

Obsahuje počáteční hodnotu počínaje prvním prvkem a následně postupné přírůstky tuto hodnotu (` value++`) v každém z prvků intervalu `[ first,  last)`.

```cpp
template <class ForwardIterator, class Type>
void iota(ForwardIterator first, ForwardIterator last, Type value);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor adresující první prvek v rozsahu pro vyplnění.

*last*<br/>
Vstupní iterátor adresující poslední prvek v rozsahu pro vyplnění.

*value*<br/>
Počáteční hodnotu pro uložení v prvním prvku a postupně přírůstek pro následné prvky.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje některá použití pro `iota` funkce vyplněním [seznamu](../standard-library/list.md) celých čísel a potom naplnění [vektoru](../standard-library/vector.md) s `list` tak, aby [random_ Shuffle](../standard-library/algorithm-functions.md#random_shuffle) funkci lze použít.

```cpp
// compile by using: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <numeric>
#include <list>
#include <vector>
#include <iostream>

using namespace std;

int main(void)
{
    list <int> intList(10);
    vector <list<int>::iterator> intVec(intList.size());

    // Fill the list
    iota(intList.begin(), intList.end(), 0);

    // Fill the vector with the list so we can shuffle it
    iota(intVec.begin(), intVec.end(), intList.begin());

    random_shuffle(intVec.begin(), intVec.end());

    // Output results
    cout << "Contents of the integer list: " << endl;
    for (auto i: intList) {
        cout << i << ' ';
    }
    cout << endl << endl;

    cout << "Contents of the integer list, shuffled by using a vector: " << endl;
    for (auto i: intVec) {
        cout << *i << ' ';
    }
    cout << endl;
}
```

## <a name="partial_sum"></a>  partial_sum

Vypočítá sérii součtů ve vstupním rozsahu od prvního prvku po *můžu*tý prvek a uloží výsledek každého součtu v *můžu*-tém prvku cílového rozsahu nebo vypočítá výsledek zobecněné procedury, kde je operace součtu nahrazena jinou zadanou binární operací.

```cpp
template <class InputIterator, class OutIt>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIt, class Fn2>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Vstupní iterátor adresující první prvek v rozsahu, u kterého bude proveden částečný součet nebo který bude zkombinován podle zadané binární operace.

*last*<br/>
Vstupní iterátor adresující poslední prvek v rozsahu, u kterého bude proveden částečný součet nebo který bude zkombinován podle zadané binární operace, který se nachází o jednu pozici za posledním prvkem, který je skutečně zahrnut do iterovaného souhrnu.

*výsledek*<br/>
Vstupní iterátor adresující první prvek v cílovém rozsahu, ve kterém se uloží série částečných součtů nebo výsledky zadané operace.

*binary_op*<br/>
Binární operace, která se použije v zobecněné operaci nahrazující operace součtu v proceduře částečného součtu.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterace adresující konec cílového rozsahu: `result` + (`last` - `first`),

### <a name="remarks"></a>Poznámky

Výstupní iterátor *výsledek* může být stejným iterátorem jako vstupní iterátor *první*, takže částečné součty mohou být vypočítány na místě.

Pro pořadí hodnot *a*1, *a*2, *a*3, ve vstupní rozsah, první funkce šablony ukládá následných částečné součtů v cílové oblasti, kde *i*je dán element TD ((( *a*1 + *a*2) + *a*3) *a*i).

Pro pořadí hodnot *a*1, *a*2, *a*3, ve vstupní rozsah, druhý funkce šablony ukládá následných částečné součtů v cílové oblasti, kde je element i-tým daný podle ((( *a*1 `binary_op` *a*2) `binary_op` *a*3) *a*i).

Binární operace *binary_op* nemusí být asociativní ani komutativní, protože se vztahuje pořadí operací je zcela určeno.

### <a name="example"></a>Příklad

```cpp
// numeric_partial_sum.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the partial sums of
   // elements in a list output to a vector
   VIterend = partial_sum ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "The output vector containing the partial sums is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the partial product of the elements in a list
   VIterend2 = partial_sum ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the partial products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of partial sums in place
   LIterend = partial_sum ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "The in place output partial_sum list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="see-also"></a>Viz také:

[\<číselné >](../standard-library/numeric.md)<br/>
