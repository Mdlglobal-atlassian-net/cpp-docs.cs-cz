---
title: piecewise_constant_distribution – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::piecewise_constant_distribution
- random/std::piecewise_constant_distribution::reset
- random/std::piecewise_constant_distribution::intervals
- random/std::piecewise_constant_distribution::densities
- random/std::piecewise_constant_distribution::param
- random/std::piecewise_constant_distribution::min
- random/std::piecewise_constant_distribution::max
- random/std::piecewise_constant_distribution::operator()
- random/std::piecewise_constant_distribution::param_type
- random/std::piecewise_constant_distribution::param_type::intervals
- random/std::piecewise_constant_distribution::param_type::densities
- random/std::piecewise_constant_distribution::param_type::operator==
- random/std::piecewise_constant_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::piecewise_constant_distribution [C++]
- std::piecewise_constant_distribution [C++], reset
- std::piecewise_constant_distribution [C++], intervals
- std::piecewise_constant_distribution [C++], densities
- std::piecewise_constant_distribution [C++], param
- std::piecewise_constant_distribution [C++], min
- std::piecewise_constant_distribution [C++], max
- std::piecewise_constant_distribution [C++], param_type
- std::piecewise_constant_distribution [C++], param_type
ms.assetid: 2c9a21fa-623e-4d63-b827-3f1556b6dedb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 875df2d76f10b1d8319df0e82541ddf73e9d8c2c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963534"
---
# <a name="piecewiseconstantdistribution-class"></a>piecewise_constant_distribution – třída

Generuje konstantní konstantní distribuci, která se má různé šířka intervalech pomocí jednotného pravděpodobnost v každém intervalu.

## <a name="syntax"></a>Syntaxe

```cpp
template<class RealType = double>
class piecewise_constant_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   piecewise_constant_distribution();
   template <class InputIteratorI, class InputIteratorW>
   piecewise_constant_distribution(
       InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);
   template <class UnaryOperation>
   piecewise_constant_distribution(
      initializer_list<result_type> intervals, UnaryOperation weightfunc);
   template <class UnaryOperation>
   piecewise_constant_distribution(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   explicit piecewise_constant_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<result_type> intervals() const;
   vector<result_type> densities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*RealType* typu výsledku, výchozí hodnota s plovoucí desetinnou čárkou **double**. Možné typy, najdete v části [ \<náhodné >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Toto rozdělení vzorkování má různé šířka intervalech pomocí jednotného pravděpodobnost v každém intervalu. Informace o dalších vzorkování distribucích najdete v tématu [piecewise_linear_distribution – třída](../standard-library/piecewise-linear-distribution-class.md) a [discrete_distribution –](../standard-library/discrete-distribution-class.md).

Následující tabulka odkazuje na články týkající se jednotlivých členů:

||||
|-|-|-|
|[piecewise_constant_distribution](#piecewise_constant_distribution)|`piecewise_constant_distribution::intervals`|`piecewise_constant_distribution::param`|
|`piecewise_constant_distribution::operator()`|`piecewise_constant_distribution::densities`|[param_type](#param_type)|

Funkce vlastností `intervals()` vrátí `vector<result_type>` sadu uložených intervalech distribuce.

Funkce vlastností `densities()` vrátí `vector<result_type>` s uložené densities – pro každou sadu interval, které se počítají podle váhy součástí parametry konstruktoru.

Vlastnost člena `param()` Nastaví nebo vrátí `param_type` uložené distribuční balíček parametrů.

`min()` a `max()` členské funkce vrátí nejmenší možné výsledek a největší výsledek je to možné, v uvedeném pořadí.

`reset()` Členská funkce odstraní všechny hodnoty uložené v mezipaměti tak, aby výsledek dalšího volání do `operator()` nezávisí na žádné hodnoty získané z modulu před voláním.

`operator()` Členské funkce vrátí další vygenerovanou hodnotu založená na modulu URNG z aktuálního balíčku parametrů nebo balíček zadaný parametr.

Další informace o distribuci třídy a jejich členy, naleznete v tématu [ \<náhodné >](../standard-library/random.md).

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

    // Three intervals, non-uniform: 0 to 1, 1 to 6, and 6 to 15
    vector<double> intervals{ 0, 1, 6, 15 };
    // weights determine the densities used by the distribution
    vector<double> weights{ 1, 5, 10 };

    piecewise_constant_distribution<double> distr(intervals.begin(), intervals.end(), weights.begin());

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "intervals (index: interval):" << endl;
    vector<double> i = distr.intervals();
    int counter = 0;
    for (const auto& n : i) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;
    cout << "densities (index: density):" << endl;
    vector<double> d = distr.densities();
    counter = 0;
    for (const auto& n : d) {
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
        cout << setw(5) << elem.first << '-' << elem.first+1 << ' ' << string(elem.second, ':') << endl;
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
max() == 15
intervals (index: interval):
          0:   0.0000000000
          1:   1.0000000000
          2:   6.0000000000
          3:  15.0000000000
densities (index: density):
          0:   0.0625000000
          1:   0.0625000000
          2:   0.0694444444
Distribution for 100 samples:
    0-1 :::::::
    1-2 ::::::
    2-3 :::::
    3-4 ::::::
    4-5 :::::::
    5-6 ::::::
    6-7 :::
    7-8 ::::::::::
    8-9 ::::::
    9-10 ::::::::::::
    10-11 :::::
    11-12 ::::::
    12-13 :::::::::
    13-14 ::::
    14-15 ::::::::
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné >

**Namespace:** std

## <a name="piecewise_constant_distribution"></a>  piecewise_constant_distribution::piecewise_constant_distribution

Vytvoří rozložení.

```cpp
// default constructor
piecewise_constant_distribution();

// constructs using a range of intervals, [firstI, lastI), with
// matching weights starting at firstW
template <class InputIteratorI, class InputIteratorW>
piecewise_constant_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);

// constructs using an initializer list for range of intervals,
// with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_constant_distribution(initializer_list<RealType>
intervals, UnaryOperation weightfunc);

// constructs using an initializer list for range of count intervals,
// distributed uniformly over [xmin,xmax] with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_constant_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);

// constructs from an existing param_type structure
explicit piecewise_constant_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*firstI* vstupní iterátor první prvek v rozsahu distribuce.

*lastI* vstupní iterátor po posledním prvku v rozsahu distribuce.

*firstW* vstupní iterátor první prvek v rozsahu váhy.

*intervaly* [initializer_list](../cpp/initializers.md) intervaly distribuce.

*počet* počet prvků v rozsahu distribuce.

*Hodnoty xMin* nejnižší hodnotu v rozsahu distribuce.

*xMax* nejvyšší číslo v rozsahu distribuce. Musí být větší než *hodnoty xmin*.

*weightfunc* objekt reprezentující funkce pravděpodobnosti pro distribuci. Parametr a vrácená hodnota musí být převeditelný na **double**.

*Parametr* parametr struktury použité k vytvoření distribuce.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor nastaví uložené parametry tak, aby se jeden intervalu 0 až 1 s hustoty pravděpodobnosti. 1.

Konstruktor rozsah iterátoru
```cpp
template <class InputIteratorI, class InputIteratorW>
piecewise_constant_distribution(InputIteratorI firstI, InputIteratorI lastI,
    InputIteratorW firstW);
```

Vytvoří objekt distribuce s itnervals z iterátory nad sekvence [ `firstI`, `lastI`) a odpovídající váha pořadí od `firstW`.

Inicializátor konstruktoru seznamu
```cpp
template <class UnaryOperation>
piecewise_constant_distribution(initializer_list<result_type>
intervals,
    UnaryOperation weightfunc);
```

Vytvoří objekt distribuce intervaly ze seznamu intializer *intervalech* a váhy generované funkce *weightfunc*.

Definován jako konstruktor
```cpp
template <class UnaryOperation>
piecewise_constant_distribution(size_t count, result_type xmin, result_type xmax,
    UnaryOperation weightfunc);
```

Vytvoří objekt distribuce s *počet* intervalech distribuovaná rovnoměrně více než [ `xmin,xmax`], přiřazení v každém intervalu oceňuje podle funkce *weightfunc*, a  *weightfunc* musí přijímat jeden parametr a musí mít návratovou hodnotu, které jsou lze převést na `double`. **Předběžné podmínky:** `xmin < xmax`

Definován jako konstruktor
```cpp
explicit piecewise_constant_distribution(const param_type& parm);
```

Vytvoří objekt distribuce pomocí *parametr* jako struktury uloženými parametry.

## <a name="param_type"></a>  piecewise_constant_distribution::param_type

Obsahuje všechny parametry distribuce.

```cpp
struct param_type {
   typedef piecewise_constant_distribution<result_type> distribution_type;
   param_type();
   template <class IterI, class IterW>
   param_type(IterI firstI, IterI lastI, IterW firstW);
   template <class UnaryOperation>
   param_type(size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   std::vector<result_type> densities() const;
   std::vector<result_type> intervals() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

Najdete v parametrech konstruktoru [piecewise_constant_distribution –](#piecewise_constant_distribution).

### <a name="remarks"></a>Poznámky

**Předběžné podmínky:** `xmin < xmax`

Tato struktura může být předán konstruktoru třídy distribuce při vytváření instance, do `param()` členskou funkci pro nastavení uložené parametry existující distribuční a k `operator()` použije místo uložené parametry.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
[piecewise_linear_distribution](../standard-library/piecewise-linear-distribution-class.md)<br/>
