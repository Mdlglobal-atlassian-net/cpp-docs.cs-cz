---
title: '&lt;číselné&gt; funkce'
description: Popisuje šablony funkcí poskytované hlavičkou &lt;číselné&gt;ve C++ standardní knihovně.
ms.date: 10/30/2019
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::exclusive_scan
- numeric/std::gcd
- numeric/std::inclusive_scan
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::lcm
- numeric/std::partial_sum
- numeric/std::reduce
- numeric/std::transform_exclusive_scan
- numeric/std::transform_inclusive_scan
- numeric/std::transform_reduce
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
helpviewer_keywords:
- std::accumulate [C++]
- std::adjacent_difference [C++]
- std::exclusive_scan [C++]
- std::gcd [C++]
- std::inclusive_scan [C++]
- std::inner_product [C++]
- std::iota [C++]
- std::lcm [C++]
- std::partial_sum [C++]
- std::reduce [C++]
- std::transform_exclusive_scan [C++]
- std::transform_inclusive_scan [C++]
- std::transform_reduce [C++]
ms.openlocfilehash: 88a97a3d110c684090b78570077927e32541eed7
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627448"
---
# <a name="ltnumericgt-functions"></a>&lt;číselné&gt; funkce

## <a name="accumulate"></a>accumulate

Vypočítá součet všech prvků v zadaném rozsahu, včetně některých počátečních hodnot, díky výpočtu po sobě jdoucích částečných součtů. Nebo vypočítá výsledek po sobě jdoucích částečných výsledků zadané binární operace.

```cpp
template <class InputIterator, class Type>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init);

template <class InputIterator, class Type, class BinaryOperation>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parametry

*první* \
Vstupní iterátor adresující první prvek v rozsahu, který má být buď sečten, nebo sloučen pomocí *binary_op*.

*poslední* \
Vstupní iterátor adresující poslední prvek v rozsahu pro sečtení nebo kombinování pomocí *binary_op*, to je jedna pozice nad konečným prvkem, který je ve skutečnosti zahrnutý v iteraci akumulace.

*inicializace*\
Počáteční hodnota, na kterou jsou jednotlivé prvky v kombinaci, a pomocí *binary_op*.

*binary_op*\
Binární operace, která se má použít u každého prvku v zadaném rozsahu a výsledku jeho předchozích aplikací

### <a name="return-value"></a>Návratová hodnota

Součet *init* a všech prvků v zadaném rozsahu pro první funkci šablony, nebo pro druhou funkci šablony, výsledek použití binární operace *binary_op* místo operace Sum na (* PartialResult, *IN_ ITER*), kde *PartialResult* je výsledkem předchozích aplikací operace a *in_iter* je iterátor ukazující na další prvek v rozsahu.

### <a name="remarks"></a>Poznámky

Počáteční hodnota zajistí, že bude k dispozici správný výsledek, pokud je rozsah prázdný. v takovém případě se vrátí *init* . Binární operace nemusí být asociativní ani komutativní. Výsledek je inicializován na počáteční hodnotu *init* a pak *výsledek* = *binary_op*(*Result*, *in_iter*) se vypočítává iterativním rozsahem, kde *in_iter* je iterátor ukazující na každý. po sobě jdoucí prvek v rozsahu. Rozsah musí být platný a složitost je lineární s velikostí rozsahu. Návratový typ binárního operátoru musí být převoditelné na **typ** , aby se zajistilo uzavření během iterace.

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

## <a name="adjacent_difference"></a>adjacent_difference

Vypočítá po sobě následující rozdíly mezi každým prvkem a jeho předchůdcem ve vstupním rozsahu. Vrátí výstup výsledků do cílového rozsahu. Nebo vypočítá výsledek zobecněné procedury, kde je operace rozdílu nahrazena jinou zadanou binární operací.

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

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parametry

*exec*\
Zásady spouštění.

*první* \
Vstupní iterátor adresující první prvek ve vstupním rozsahu, jehož prvky mají být diferencovány s příslušnými předchůdci nebo ve kterém použije dvojice hodnot jiná zadaná binární operace.

*poslední* \
Vstupní iterátor adresující poslední prvek ve vstupním rozsahu, jehož prvky mají být diferencovány s příslušnými předchůdci nebo ve kterém použije dvojice hodnot jiná zadaná binární operace.

\ *výsledku*
Vstupní iterátor adresující první prvek v cílovém rozsahu, ve kterém se uloží série rozdílů nebo výsledky zadané operace.

*binary_op*\
Binární operace, která se má použít v zobecněné operaci nahrazující operaci odčítání v rozdílové proceduře.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující konec cílového rozsahu: `result` + (`last` - `first`).

### <a name="remarks"></a>Poznámky

*Výsledkem* výstupního iterátoru může být *stejný iterátor jako vstupní iterátor, aby*bylo možné vypočítat `adjacent_difference` hodnoty.

Pro sekvenci hodnot *a*1, *a*2, *a*3 ve vstupním rozsahu ukládá první funkce šablony po sobě jdoucí `adjacent_difference` hodnoty *a*1, *a*2- *a*1, a3- *a*2 v cílovém rozsahu.

Pro sekvenci hodnot *a*1, *a*2, *a*3 ve vstupním rozsahu ukládá druhá funkce šablony po sobě následující `adjacent_difference` hodnoty *a*1, *a*2 *binary_op* *a*1, *a*3 *binary_op* *a*2, v cílový rozsah.

Binární operace *binary_op* nemusí být asociativní ani komutativní, protože je zadané pořadí operací.

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

## <a name="exclusive_scan"></a>exclusive_scan

Vypočítá výhradní operaci součtu předpony pomocí `std::plus<>()` nebo zadaného binárního operátoru v rámci rozsahu s ohledem na počáteční hodnotu. Zapíše výsledky do rozsahu začínajícího v zadaném cíli. Exkluzivní celočíselná *předpona* znamená, že *n*-tý element input není zahrnutý do *n*-tého součtu. Přetížení, která zahrnují argument zásady spouštění, se spustí podle zadaných zásad.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init);

template<class InputIterator, class OutputIterator, class Type, class BinaryOperation>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parametry

*exec*\
Zásady spouštění.

*první* \
Vstupní iterátor adresující první prvek v rozsahu, který má být buď sečten, nebo sloučen pomocí *binary_op*.

*poslední* \
Vstupní iterátor adresující poslední prvek v rozsahu pro sečtení nebo kombinování pomocí *binary_op*, to je jedna pozice nad konečným prvkem, který je ve skutečnosti zahrnutý v iteraci akumulace.

\ *výsledku*
Výstupní iterátor adresující první prvek v cílovém rozsahu, ve kterém mají být uloženy řady součtů nebo výsledky zadané operace.

*inicializace*\
Počáteční hodnota, na kterou jsou jednotlivé prvky v kombinaci, a pomocí *binary_op*.

*binary_op*\
Binární operace, která se má použít u každého prvku v zadaném rozsahu a výsledku jeho předchozích aplikací

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující konec cílového rozsahu: *výsledek* + (*Poslední* - *první*).

## <a name="gcd"></a>GCD

Vypočítá největšího společného dělitele celých čísel m a n.

```cpp
template <class M, class N>
constexpr common_type_t<M,N> gcd(M m, N n);
```

### <a name="parameters"></a>Parametry

*m*, *n*\
Hodnoty integrálního typu.

### <a name="return-value"></a>Návratová hodnota

Vrátí největší společný dělitel absolutních hodnot *m* a *n*nebo nula, pokud jsou hodnoty *m* a *n* nula. Výsledky nejsou definovány, pokud absolutní hodnoty *m* nebo *n* nejsou reprezentovány jako hodnoty typu `common_type_t<M,N>`.

## <a name="inclusive_scan"></a>inclusive_scan

Vypočítá celkovou operaci součtu předpony pomocí `std::plus<>()` nebo zadaného binárního operátoru v rámci rozsahu s ohledem na počáteční hodnotu. Zapíše výsledky do rozsahu začínajícího v zadaném cíli. Celková *celočíselná předpona* znamená, že *n*-tý prvek input je zahrnut do *n*-tého součtu. Přetížení, která zahrnují argument zásady spouštění, se spustí podle zadaných zásad.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template<class InputIterator, class OutputIterator, class BinaryOperation>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class Type>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation, class Type>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    Type init);
```

### <a name="parameters"></a>Parametry

*exec*\
Zásady spouštění.

*první* \
Vstupní iterátor adresující první prvek v rozsahu, který má být buď sečten, nebo sloučen pomocí *binary_op*.

*poslední* \
Vstupní iterátor adresující poslední prvek v rozsahu pro sečtení nebo kombinování pomocí *binary_op*, to je jedna pozice nad konečným prvkem, který je ve skutečnosti zahrnutý v iteraci akumulace.

\ *výsledku*
Výstupní iterátor adresující první prvek v cílovém rozsahu, ve kterém mají být uloženy řady součtů nebo výsledky zadané operace.

*inicializace*\
Počáteční hodnota, na kterou jsou jednotlivé prvky v kombinaci, a pomocí *binary_op*.

*binary_op*\
Binární operace, která se má použít u každého prvku v zadaném rozsahu a výsledku jeho předchozích aplikací

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující konec cílového rozsahu: *výsledek* + (*Poslední* - *první*).

## <a name="inner_product"></a>inner_product

Vypočítá součet elementu v rámci produktu dvou rozsahů a přidá jej k zadané počáteční hodnotě nebo vypočítá výsledek zobecněné procedury, kde jsou souhrn a operace binárního produktu nahrazeny jinými zadanými binárními operacemi.

```cpp
template <class InputIterator1, class InputIterator2, class Type>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init);

template <class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);
```

### <a name="parameters"></a>Parametry

*first1* \
Vstupní iterátor adresující první prvek v prvním rozsahu, jehož vnitřní produkt nebo zobecněný vnitřní produkt s druhým rozsahem mají být počítány.

*last1* \
Vstupní iterátor adresující poslední prvek v prvním rozsahu, jehož vnitřní produkt nebo zobecněný vnitřní produkt s druhým rozsahem mají být počítány.

*first2* \
Vstupní iterátor adresující první prvek ve druhém rozsahu, jehož vnitřní produkt nebo zobecněný vnitřní produkt s prvním rozsahem je vypočítáván.

*inicializace*\
Počáteční hodnota, na kterou se má přidat vnitřní produkt nebo zobecněný vnitřní produkt mezi rozsahy.

*binary_op1*\
Binární operace, která nahrazuje interní operaci součinu součtu, která se použije u produktů, které jsou v generalizi, v generalizi vnitřního produktu.

*binary_op2*\
Binární operace, která nahrazuje prvek vnitřního produktu, který se má vynásobit ve generalizaci vnitřního produktu.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí součet součinů prvků a přidá je do zadané počáteční hodnoty. Takže pro rozsahy hodnot *a*i a *b*i vrátí:

*init* + (*a*1 \* *b*1) + (*a*2 \* *b*2) +... + (*a*n \* *b*n)

iterativním nahrazením *init* pomocí *init* + (*a*i \* *b*i).

Druhá členská funkce vrátí:

*init* *binary_op1* (*a*1 *binary_op2* *b*1) *binary_op1* (*a*2 *binary_op2* *b*2) *binary_op1* ... *binary_op1* (*a*n *binary_op2* *b*n)

iterativním nahrazením *init* pomocí *init* *binary_op1* (*a*i *binary_op2* *b*i).

### <a name="remarks"></a>Poznámky

Počáteční hodnota zajistí, že bude k dispozici dobře definovaný výsledek, pokud je rozsah prázdný. V takovém případě se vrátí *init* . Binární operace nemusejí být asociativní ani komutativní. Rozsah musí být platný a složitost je lineární s velikostí rozsahu. Návratový typ binárního operátoru musí být převoditelné na **typ** , aby se zajistilo uzavření během iterace.

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

## <a name="iota"></a>p

Ukládá počáteční hodnotu počínaje prvním prvkem a naplňuje po sobě jdoucí přírůstky dané hodnoty (`value++`) v každém elementu v intervalu `[first,  last)`.

```cpp
template <class ForwardIterator, class Type>
void iota(ForwardIterator first, ForwardIterator last, Type value);
```

### <a name="parameters"></a>Parametry

*první* \
Vstupní iterátor adresující první prvek v rozsahu, který má být vyplněn.

*poslední* \
Vstupní iterátor adresující poslední prvek v rozsahu, který má být vyplněn.

*hodnota* \
Počáteční hodnota, která má být uložena v prvním prvku a v případě pozdějšího zvýšení pro pozdější prvky.

### <a name="example"></a>Příklad

Následující příklad ukazuje některé použití funkce `iota` vyplněním [seznamu](../standard-library/list.md) celých čísel a následně vyplněním [vektoru](../standard-library/vector.md) pomocí `list`, aby bylo možné použít funkci [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle) .

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

## <a name="lcm"></a>chyb

```cpp
template <class M, class N>
constexpr common_type_t<M,N> lcm(M m, N n);
```

## <a name="partial_sum"></a>partial_sum

Vypočítá sérii součtů ve vstupním rozsahu od prvního prvku po *n*-tý prvek a uloží výsledek každého součtu v *n*-té elementu cílového rozsahu. Nebo vypočítá výsledek zobecněné procedury, kde je operace součtu nahrazena jinou zadanou binární operací.

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

*první* \
Vstupní iterátor adresující první prvek v rozsahu, u kterého bude proveden částečný součet nebo který bude zkombinován podle zadané binární operace.

*poslední* \
Vstupní iterátor adresující poslední prvek v rozsahu, u kterého bude proveden částečný součet nebo který bude zkombinován podle zadané binární operace, který se nachází o jednu pozici za posledním prvkem, který je skutečně zahrnut do iterovaného souhrnu.

\ *výsledku*
Výstupní iterátor adresující první prvek cílového rozsahu pro uložení řady částečných součtů nebo po sobě jdoucích výsledků zadané binární operace.

*binary_op*\
Binární operace, která se má použít v zobecněné operaci nahrazující operaci součtu v postupu částečného součtu.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující konec cílového rozsahu: *výsledek* + (*Poslední* - *první*).

### <a name="remarks"></a>Poznámky

*Výsledkem* výstupního iterátoru může být *stejný iterátor jako vstupní iterátor, aby*bylo možné vypočítat částečné součty.

Pro sekvenci hodnot *a*1, *a*2,... *x ve*vstupním rozsahu ukládá první funkce šablony po sobě jdoucí částečné součty do cílového rozsahu. *N*-tý element je*dán (1*+ *a*2 + *a*3 +... + *a*n).

Pro sekvenci hodnot *a*1, *a*2, *a*3 ve vstupním rozsahu ukládá druhá funkce šablony po sobě jdoucí částečné výsledky do cílového rozsahu. *N*-tý element je dán ((... ((*a*1 *binary_op* *a*2) *binary_op* *a*3) *binary_op* ...) *binary_op* *a*n).

Binární operace *binary_op* nemusí být asociativní ani komutativní, protože je zadané pořadí operací.

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

## <a name="reduce"></a>úrovně

Omezí všechny prvky v zadaném rozsahu, případně včetně některých počátečních hodnot, díky výpočtu součtů v libovolném a možném permuted pořadí. Nebo se zkracuje pomocí výpočtu výsledků zadané binární operace. Přetížení, která zahrnují argument zásady spouštění, se spustí podle zadaných zásad.

```cpp
template<class InputIterator>
typename iterator_traits<InputIterator>::value_type reduce(
    InputIterator first,
    InputIterator last);

template<class InputIterator, class Type>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init);

template<class InputIterator, class Type, class BinaryOperation>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator>
typename iterator_traits<ForwardIterator>::value_type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Type>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parametry

*exec*\
Zásady spouštění.

*první* \
Vstupní iterátor adresující první prvek v rozsahu, který má být buď sečten, nebo sloučen pomocí *binary_op*.

*poslední* \
Vstupní iterátor adresující poslední prvek v rozsahu pro sečtení nebo kombinování pomocí *binary_op*, to je jedna pozice nad konečným prvkem, který je ve skutečnosti zahrnutý v iteraci akumulace.

\ *výsledku*
Výstupní iterátor adresující první prvek v cílovém rozsahu, ve kterém mají být uloženy řady součtů nebo výsledky zadané operace.

*inicializace*\
Počáteční hodnota, na kterou jsou jednotlivé prvky v kombinaci, a pomocí *binary_op*.

*binary_op*\
Binární operace, která se má použít u každého prvku v zadaném rozsahu a výsledku jeho předchozích aplikací

### <a name="return-value"></a>Návratová hodnota

Výsledek použití *binary_op* nebo `std::plus<>()` k *inicializaci* a všech prvků v zadaném rozsahu na (* PartialResult, *in_iter*), kde *PartialResult* je výsledkem předchozích aplikací operace a *in_iter* je iterátor ukazující na některý prvek v rozsahu. V přetížení, které nespecifikují *init*, je použitá hodnota *init* ekvivalentní `typename iterator_traits<InputIterator>::value_type{}`.

### <a name="remarks"></a>Poznámky

Pokud je *binary_op* asociativní a komutativní, chování `reduce` není deterministické. Chování není definováno, pokud *binary_op* upraví libovolný element, nebo zruší platnost libovolného iterátoru v intervalu \[*First*, *Last*] včetně.

## <a name="transform_exclusive_scan"></a>transform_exclusive_scan

Transformuje prvky rozsahu se zadaným unárním operátorem a poté vypočítá výhradní operaci součtu předpony pomocí `std::plus<>()` nebo zadaného binárního operátoru v rozsahu, s ohledem na počáteční hodnotu. Zapíše výsledky do rozsahu začínajícího v zadaném cíli. Exkluzivní celočíselná *předpona* znamená, že *n*-tý element input není zahrnutý do *n*-tého součtu. Přetížení, která zahrnují argument zásady spouštění, se spustí podle zadaných zásad. Suma se dá provést v libovolném pořadí.

```cpp
template<class InputIterator, class OutputIterator, class Type, class BinaryOperation, class UnaryOperation>
OutputIterator transform_exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>Parametry

*exec*\
Zásady spouštění.

*první* \
Vstupní iterátor adresující první prvek v rozsahu, který má být buď sečten, nebo sloučen pomocí *binary_op*.

*poslední* \
Vstupní iterátor adresující poslední prvek v rozsahu pro sečtení nebo kombinování pomocí *binary_op*, to je jedna pozice nad konečným prvkem, který je ve skutečnosti zahrnutý v iteraci akumulace.

\ *výsledku*
Výstupní iterátor adresující první prvek v cílovém rozsahu, ve kterém mají být uloženy řady součtů nebo výsledky zadané operace.

*inicializace*\
Počáteční hodnota, na kterou jsou jednotlivé prvky v kombinaci, a pomocí *binary_op*.

*binary_op*\
Binární operace, která se má použít u každého prvku v zadaném rozsahu a výsledku jeho předchozích aplikací

*unary_op*\
Unární operace, která se má použít u každého prvku v zadaném rozsahu.

## <a name="transform_inclusive_scan"></a>transform_inclusive_scan

Transformuje prvky rozsahu pomocí zadaného unárního operátoru a potom vypočítá operaci součtu vnitřních předpon pomocí `std::plus<>()` nebo zadaného binárního operátoru v rozsahu s ohledem na počáteční hodnotu. Zapíše výsledky do rozsahu začínajícího v zadaném cíli. Celková *celočíselná předpona* znamená, že *n*-tý prvek input je zahrnut do *n*-tého součtu. Přetížení, která zahrnují argument zásady spouštění, se spustí podle zadaných zásad. Suma se dá provést v libovolném pořadí.

```cpp
template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation, class Type>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation, class Type>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);
```

### <a name="parameters"></a>Parametry

*exec*\
Zásady spouštění.

*první* \
Vstupní iterátor adresující první prvek v rozsahu, který má být buď sečten, nebo sloučen pomocí *binary_op*.

*poslední* \
Vstupní iterátor adresující poslední prvek v rozsahu pro sečtení nebo kombinování pomocí *binary_op*, to je jedna pozice nad konečným prvkem, který je ve skutečnosti zahrnutý v iteraci akumulace.

\ *výsledku*
Výstupní iterátor adresující první prvek v cílovém rozsahu, ve kterém mají být uloženy řady součtů nebo výsledky zadané operace.

*binary_op*\
Binární operace, která se má použít u každého prvku v zadaném rozsahu a výsledku jeho předchozích aplikací

*unary_op*\
Unární operace, která se má použít u každého prvku v zadaném rozsahu.

*inicializace*\
Počáteční hodnota, na kterou jsou jednotlivé prvky v kombinaci, a pomocí *binary_op*.

## <a name="transform_reduce"></a>transform_reduce

Transformuje rozsah prvků a pak použije funktor, který zmenší transformované elementy v libovolném pořadí. Efektivně `transform` následovaný `reduce`.

```cpp
template<class InputIterator1, class InputIterator2, class Type>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init);

template<class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class InputIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>Parametry

*exec*\
Zásady spouštění.

*první* \
Vstupní iterátor adresující první prvek v rozsahu, který má být buď sečten, nebo sloučen pomocí *binary_op*.

*first1* \
Vstupní iterátor adresující první prvek v rozsahu, který má být buď sečten, nebo sloučen pomocí *binary_op1*.

*poslední* \
Vstupní iterátor adresující poslední prvek v rozsahu pro sečtení nebo kombinování pomocí *binary_op*, to je jedna pozice nad konečným prvkem, který je ve skutečnosti zahrnutý v iteraci akumulace.

*last1* \
Vstupní iterátor adresující poslední prvek v rozsahu pro sečtení nebo kombinování pomocí *binary_op1*, to je jedna pozice nad konečným prvkem, který je ve skutečnosti zahrnutý v iteraci akumulace.

\ *výsledku*
Výstupní iterátor adresující první prvek v cílovém rozsahu, ve kterém mají být uloženy řady součtů nebo výsledky zadané operace.

*inicializace*\
Počáteční hodnota, na kterou jsou jednotlivé prvky v kombinaci, a pomocí *binary_op*.

*binary_op*\
Binární operace, která se má použít u každého prvku v zadaném rozsahu a výsledku jeho předchozích aplikací

*unary_op*\
Unární operace, která se má použít u každého prvku v zadaném rozsahu.

### <a name="return-value"></a>Návratová hodnota

Převedený výsledek se transformuje.
