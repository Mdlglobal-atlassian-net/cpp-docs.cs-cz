---
title: piecewise_linear_distribution – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::piecewise_linear_distribution
- random/std::piecewise_linear_distribution::reset
- random/std::piecewise_linear_distribution::intervals
- random/std::piecewise_linear_distribution::densities
- random/std::piecewise_linear_distribution::param
- random/std::piecewise_linear_distribution::min
- random/std::piecewise_linear_distribution::max
- random/std::piecewise_linear_distribution::operator()
- random/std::piecewise_linear_distribution::param_type
- random/std::piecewise_linear_distribution::param_type::intervals
- random/std::piecewise_linear_distribution::param_type::densities
- random/std::piecewise_linear_distribution::param_type::operator==
- random/std::piecewise_linear_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::piecewise_linear_distribution [C++]
- std::piecewise_linear_distribution [C++], reset
- std::piecewise_linear_distribution [C++], intervals
- std::piecewise_linear_distribution [C++], densities
- std::piecewise_linear_distribution [C++], param
- std::piecewise_linear_distribution [C++], min
- std::piecewise_linear_distribution [C++], max
- std::piecewise_linear_distribution [C++], param_type
- std::piecewise_linear_distribution [C++], param_type
ms.assetid: cd141152-7163-4754-8f98-c6d6500005e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b516478c72e92f63b898cc43aa4838ab72733a05
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="piecewiselineardistribution-class"></a>piecewise_linear_distribution – třída

Generuje piecewise lineární distribuce, který má různých šířka intervalech pomocí lineárně různých pravděpodobnosti v každém intervalu.

## <a name="syntax"></a>Syntaxe

```cpp
template<class RealType = double>
class piecewise_linear_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   piecewise_linear_distribution();
   template <class InputIteratorI, class InputIteratorW>
   piecewise_linear_distribution(
      InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);
   template <class UnaryOperation>
   piecewise_linear_distribution(
      initializer_list<result_type> intervals, UnaryOperation weightfunc);
   template <class UnaryOperation>
   piecewise_linear_distribution(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   explicit piecewise_linear_distribution(const param_type& parm);
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

`RealType` Typ výsledku, výchozí hodnota je procedura bodu `double`. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Toto rozdělení vzorkování má různých šířka intervalech pomocí lineárně různých pravděpodobnosti v každém intervalu. Informace o dalších vzorkování distribucích najdete v tématu [piecewise_linear_distribution](../standard-library/piecewise-constant-distribution-class.md) a [discrete_distribution](../standard-library/discrete-distribution-class.md).

Následující tabulka odkazy na články o jednotlivé členy:

||||
|-|-|-|
|[piecewise_linear_distribution](#piecewise_linear_distribution)|`piecewise_linear_distribution::intervals`|`piecewise_linear_distribution::param`|
|`piecewise_linear_distribution::operator()`|`piecewise_linear_distribution::densities`|[param_type](#param_type)|

Funkce vlastnost `intervals()` vrátí `vector<result_type>` sadou uložené intervaly rozdělení.

Funkce vlastnost `densities()` vrátí `vector<result_type>` s uložené densities – pro každou sadu interval, které se vypočítává podle váhy zadané v parametrech konstruktor.

Vlastnost člena `param()` Nastaví nebo vrátí `param_type` balíček parametr uložené distribuce.

`min()` a `max()` členské funkce vrátí nejmenší možný výsledek a největší možné výsledek, v uvedeném pořadí.

`reset()` – Členská funkce zahodí všechny hodnoty v mezipaměti, aby výsledkem další volání `operator()` nezávisí na žádné hodnoty získané z modulu před voláním.

`operator()` Členské funkce vrátí další generované hodnoty, které jsou založené na modulu URNG buď z aktuální parametr balíček nebo balíček zadaný parametr.

Další informace o distribučních třídy a jejich členové najdete v tématu [ \<náhodných >](../standard-library/random.md).

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
    vector<double> weights{ 1, 5, 5, 10 };

    piecewise_linear_distribution<double> distr(intervals.begin(), intervals.end(), weights.begin());

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
        cout << setw(5) << elem.first << '-' << elem.first + 1 << ' ' << string(elem.second, ':') << endl;
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
          0:   0.0645161290
          1:   0.3225806452
          2:   0.3225806452
          3:   0.6451612903
Distribution for 100 samples:
    0-1 :::::::::::::::::::::
    1-2 ::::::
    2-3 :::
    3-4 :::::::
    4-5 ::::::
    5-6 ::::::
    6-7 :::::
    7-8 ::::::::::
    8-9 ::::::::::
    9-10 ::::::
   10-11 ::::
   11-12 :::
   12-13 :::
   13-14 :::::
   14-15 :::::
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodných >

**Namespace:** – std

## <a name="piecewise_linear_distribution"></a>  piecewise_linear_distribution::piecewise_linear_distribution

Vytvoří rozdělení.

```cpp
// default constructor
piecewise_linear_distribution();

// constructs using a range of intervals, [firstI, lastI), with
// matching weights starting at firstW
template <class InputIteratorI, class InputIteratorW>
piecewise_linear_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);

// constructs using an initializer list for range of intervals,
// with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_linear_distribution(initializer_list<RealType>
intervals, UnaryOperation weightfunc);

// constructs using an initializer list for range of count intervals,
// distributed uniformly over [xmin,xmax] with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_linear_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);

// constructs from an existing param_type structure
explicit piecewise_linear_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*firstI* vstupní iterator prvním elementem v rozsahu distribuce.

*lastI* vstupní iterator posledním prvkem v rozsahu distribuce.

*firstW* vstupní iterator prvním elementem v rozsahu váhu.

*intervaly* [initializer_list](../cpp/initializers.md) s intervalů rozdělení.

*počet* počet elementů v rozsahu distribuce.

*Hodnoty xMin* nejnižší hodnotu v rozsahu distribuce.

*xMax* nejvyšší hodnotu v rozsahu distribuce. Musí být větší než *hodnoty xmin*.

*weightfunc* objekt reprezentující funkce pravděpodobnosti pro distribuci. Parametr i návratová hodnota musí být převoditelná na `double`.

*Parametr* strukturu parametr použitý k vytvoření distribuce.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor nastavuje parametry, uložené, aby jednoho intervalu 0 až 1 s hustoty pravděpodobnosti 1.

Konstruktor rozsah iterátorů

```cpp
template <class InputIteratorI, class InputIteratorW>
piecewise_linear_distribution(
    InputIteratorI firstI,
    InputIteratorI lastI,
    InputIteratorW firstW);
```

Vytvoří objekt distribuční s itnervals z iterátory přes sekvenci [ `firstI`, `lastI`) a odpovídající vážené pořadí počínaje `firstW`.

V konstruktoru inicializátoru seznamu

```cpp
template <class UnaryOperation>
piecewise_linear_distribution(
    initializer_list<result_type> intervals,
    UnaryOperation weightfunc);
```

Vytvoří objekt distribuční s intervaly ze seznamu intializer `intervals` a váhu generované z funkce `weightfunc`.

Konstruktor definovaný jako

```cpp
template <class UnaryOperation>
piecewise_linear_distribution(
    size_t count,
    result_type xmin,
    result_type xmax,
    UnaryOperation weightfunc);
```

Vytvoří objekt distribuční s `count` intervaly distribuované jednotně přes [ `xmin,xmax`], přiřazení v každém intervalu provede podle funkce `weightfunc`, a `weightfunc` musíte přijmout jeden parametr a vraťte se mají hodnoty, i jsou převést na `double`. **Předběžnou:**`xmin < xmax`.

Konstruktor definovaný jako

```cpp
explicit piecewise_linear_distribution(const param_type& parm);
```

Vytvoří objekt distribuční pomocí `parm` jako strukturu uložený parametr.

## <a name="param_type"></a>  piecewise_linear_distribution::param_type

Uloží všechny parametry rozdělení.

```cpp
struct param_type {
   typedef piecewise_linear_distribution<result_type> distribution_type;
   param_type();
   template <class IterI, class IterW>
   param_type(
      IterI firstI, IterI lastI, IterW firstW);
   template <class UnaryOperation>
   param_type(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   std::vector<result_type> densities() const;
   std::vector<result_type> intervals() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

Naleznete na stránce parametry konstruktor pro [piecewise_linear_distribution](#piecewise_linear_distribution).

### <a name="remarks"></a>Poznámky

**Předběžnou podmínku:** `xmin < xmax`

Tato struktura mohou být předána do konstruktoru třídy distribuční při vytváření instancí, položky `param()` – členská funkce nastavit uložené parametrů z existující distribuční a to `operator()` má být použit místo uložené parametry.

## <a name="see-also"></a>Viz také

[\<náhodné >](../standard-library/random.md)<br/>
