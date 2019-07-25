---
title: discrete_distribution – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::discrete_distribution
- random/std::discrete_distribution::reset
- random/std::discrete_distribution::probabilities
- random/std::discrete_distribution::param
- random/std::discrete_distribution::min
- random/std::discrete_distribution::max
- random/std::discrete_distribution::operator()
- random/std::discrete_distribution::param_type
- random/std::discrete_distribution::param_type::probabilities
- random/std::discrete_distribution::param_type::operator==
- random/std::discrete_distribution::param_type::operator!=
helpviewer_keywords:
- std::discrete_distribution [C++]
- std::discrete_distribution [C++], reset
- std::discrete_distribution [C++], probabilities
- std::discrete_distribution [C++], param
- std::discrete_distribution [C++], min
- std::discrete_distribution [C++], max
- std::discrete_distribution [C++], param_type
- std::discrete_distribution [C++], param_type
ms.assetid: 8c8ba8f8-c06f-4f07-b354-f53950142fcf
ms.openlocfilehash: ce668ebfdafc4a53bfc71ecf1f2fa76abb1c7532
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454383"
---
# <a name="discretedistribution-class"></a>discrete_distribution – třída

Vygeneruje diskrétní rozdělení celého čísla, které má v každém intervalu jednotnou šířku a jednotnou pravděpodobnost.

## <a name="syntax"></a>Syntaxe

```cpp
template<class IntType = int>
class discrete_distribution
   {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructor and reset functions
   discrete_distribution();
   template <class InputIterator>
   discrete_distribution(InputIterator firstW, InputIterator lastW);
   discrete_distribution(initializer_list<double> weightlist);
   template <class UnaryOperation>
   discrete_distribution(size_t count, double xmin, double xmax, UnaryOperation funcweight);
   explicit discrete_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<double> probabilities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*IntType*\
Celočíselný typ výsledku, výchozí hodnota je **int**. Možné typy naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato distribuce vzorkování má v každém intervalu jednotnou šířku jako intervaly s jednotnou pravděpodobností. Informace o dalších distribucích vzorkování naleznete v tématu Třída [piecewise_linear_distribution](../standard-library/piecewise-linear-distribution-class.md) a [Třída piecewise_constant_distribution](../standard-library/piecewise-constant-distribution-class.md).

Následující tabulka obsahuje odkazy na články týkající se jednotlivých členů:

|||
|-|-|
|[discrete_distribution](#discrete_distribution)|`discrete_distribution::param`|
|`discrete_distribution::operator()`|[param_type](#param_type)|

Funkce `vector<double> probabilities()` Property vrátí jednotlivé pravděpodobnosti pro každé vygenerované celé číslo.

Další informace o třídách distribuce a jejich členech naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="example"></a>Příklad

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const int s) {

    // uncomment to use a non-deterministic generator
    // random_device rd;
    // mt19937 gen(rd());
    mt19937 gen(1701);

    discrete_distribution<> distr({ 1, 2, 3, 4, 5 });

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "probabilities (value: probability):" << endl;
    vector<double> p = distr.probabilities();
    int counter = 0;
    for (const auto& n : p) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;

    // generate the distribution as a histogram
    map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << s << " samples:" << endl;
    for (const auto& elem : histogram) {
        cout << setw(5) << elem.first << ' ' << string(elem.second, ':') << endl;
    }
    cout << endl;
}

int main()
{
    int samples = 100;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the sample count: 100
min() == 0
max() == 4
probabilities (value: probability):
          0:   0.0666666667
          1:   0.1333333333
          2:   0.2000000000
          3:   0.2666666667
          4:   0.3333333333

Distribution for 100 samples:
    0 :::
    1 ::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::::::::::::::::
    4 ::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<náhodné >

**Obor názvů:** std

## <a name="discrete_distribution"></a>discrete_distribution::d iscrete_distribution

Sestaví rozdělení.

```cpp
// default constructor
discrete_distribution();

// construct using a range of weights, [firstW, lastW)
template <class InputIterator>
discrete_distribution(InputIterator firstW, InputIterator lastW);

// construct using an initializer list for range of weights
discrete_distribution(initializer_list<double> weightlist);

// construct using unary operation function
template <class UnaryOperation>
discrete_distribution(size_t count, double low, double high, UnaryOperation weightfunc);

// construct from an existing param_type structure
explicit discrete_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*firstW*\
První iterátor v seznamu, ze kterého se má vytvořit distribuce.

*lastW*\
Poslední iterátor v seznamu, ze kterého se má sestavit rozdělení (nezahrnuje se, protože iterátory používají prázdný element pro konec).

*weightlist*\
[Initializer_list](../cpp/initializers.md) , ze kterého se má sestavit rozdělení.

*výpočtu*\
Počet prvků v rozsahu distribuce. IF `count==0`, ekvivalent k výchozímu konstruktoru (vždy generuje nulu).

*slab*\
Nejnižší hodnota v rozsahu distribuce.

*maximální*\
Nejvyšší hodnota v rozsahu distribuce.

*weightfunc*\
Objekt představující funkci pravděpodobnosti pro rozdělení. Parametr i návratová hodnota musí být převoditelné na **typ Double**.

*parametr*\
`param_type` Struktura použitá k sestavení distribuce.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor vytvoří objekt, jehož uložená hodnota pravděpodobnosti má jeden prvek s hodnotou 1. Výsledkem bude distribuce, která vždy vygeneruje nulu.

Konstruktor rozsahu iterátoru, který má parametry *firstW* a *lastW* , vytvoří distribuční objekt pomocí hodnot váhy převzatých z iterátorů v intervalu sekvence [*firstW*, *lastW*).

Konstruktor seznamu inicializátorů, který má parametr *weightlist* , vytvoří distribuční objekt s závaží ze seznamu inicializátorů *weightlist*.

Konstruktor, který má parametry *Count*, *low*, *High*a *weightfunc* , vytvoří objekt distribuce inicializovaný na základě těchto pravidel:

- Pokud je *počet* < 1, **n** = 1 a jako takový je ekvivalentní výchozímu konstruktoru, vždy vygeneruje nula.
- Pokud je *počet* > 0, **n** = *počet*. Poskytnutá hodnota **d** = (*Vysoká* - *Nízká*)/ **n** je větší než nula **, přičemž používá v** nich rovnoměrné dílčí rozsahy, každá váha je `weight[k] = weightfunc(x)`přiřazena následujícím způsobem:, kde **x** = *Nízká*  +  **k**     d d/2, pro k = 0,..., n-1. +  * 

Konstruktor, který má `param_type` parametr *parametr* , vytvoří distribuční objekt jako uloženou strukturu parametrů pomocí *parametr* .

## <a name="param_type"></a>discrete_distribution::p aram_type

Ukládá všechny parametry distribuce.

```cpp
struct param_type {
   typedef discrete_distribution<result_type> distribution_type;
   param_type();

   // construct using a range of weights, [firstW, lastW)
   template <class InputIterator>
   param_type(InputIterator firstW, InputIterator lastW);

   // construct using an initializer list for range of weights
   param_type(initializer_list<double> weightlist);

   // construct using unary operation function
   template <class UnaryOperation>
   param_type(size_t count, double low, double high, UnaryOperation weightfunc);

   std::vector<double> probabilities() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*firstW*\
První iterátor v seznamu, ze kterého se má vytvořit distribuce.

*lastW*\
Poslední iterátor v seznamu, ze kterého se má sestavit rozdělení (nezahrnuje se, protože iterátory používají prázdný element pro konec).

*weightlist*\
[Initializer_list](../cpp/initializers.md) , ze kterého se má sestavit rozdělení.

*výpočtu*\
Počet prvků v rozsahu distribuce. Pokud je *počet* 0, jedná se o ekvivalent výchozího konstruktoru (vždy generuje nulu).

*slab*\
Nejnižší hodnota v rozsahu distribuce.

*maximální*\
Nejvyšší hodnota v rozsahu distribuce.

*weightfunc*\
Objekt představující funkci pravděpodobnosti pro rozdělení. Parametr i návratová hodnota musí být převoditelné na **typ Double**.

*Kliknutím*\
`param_type` Objekt, který se má porovnat.

### <a name="remarks"></a>Poznámky

Tento balíček parametrů lze předat `operator()` pro vygenerování návratové hodnoty.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)
