---
title: discrete_distribution – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af8f5c543847c91903c9cb4ddf2502c0cc59dfa0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="discretedistribution-class"></a>discrete_distribution – třída

Generuje rozdělení diskrétní celé číslo, na které má uniform šířkou intervalech pomocí uniform pravděpodobnosti v každém intervalu.

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

*IntType* výsledný typ celé číslo, výchozí nastavení je `int`. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Toto rozdělení vzorkování má uniform šířkou intervalech pomocí uniform pravděpodobnosti v každém intervalu. Informace o dalších vzorkování distribucích najdete v tématu [piecewise_linear_distribution – třída](../standard-library/piecewise-linear-distribution-class.md) a [piecewise_constant_distribution – třída](../standard-library/piecewise-constant-distribution-class.md).

Následující tabulka odkazy na články o jednotlivé členy:

|||
|-|-|
|[discrete_distribution](#discrete_distribution)|`discrete_distribution::param`|
|`discrete_distribution::operator()`|[param_type](#param_type)|

Funkce vlastnost `vector<double> probabilities()` vrátí jednotlivých pravděpodobností pro každý celé číslo vygenerovat.

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

**Záhlaví:** \<náhodných >

**Namespace:** – std

## <a name="discrete_distribution"></a>  discrete_distribution::discrete_distribution

Vytvoří rozdělení.

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

*firstW* první iterator v seznamu, ze kterého chcete vytvořit rozdělení.

*lastW* poslední iterator v seznamu, ze kterého chcete vytvořit distribuční (bez – včetně protože iterátory používají prázdný element end).

*weightlist* [initializer_list](../cpp/initializers.md) ze kterého chcete vytvořit rozdělení.

*počet* počet elementů v rozsahu distribuce. Pokud `count==0`, ekvivalentní výchozího konstruktoru (vždy vygeneruje nula).

*nízkou* nejnižší hodnotu v rozsahu distribuce.

*Vysoká* nejvyšší hodnotu v rozsahu distribuce.

*weightfunc* objekt reprezentující funkce pravděpodobnosti pro distribuci. Parametr i návratová hodnota musí být převoditelná na `double`.

*Parametr* `param_type` struktura použitý k vytvoření distribuce.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor vytvoří objekt, jehož hodnota pravděpodobnosti uložené má jeden element s hodnotou 1. Výsledkem bude distribuce, která generuje vždy nula.

Konstruktor iterator rozsah, který obsahuje parametry *firstW* a *lastW* vytvoří objekt distribuční pomocí hodnoty váhy převzetí pořadí interval z iterátory [ *firstW*, *lastW*).

Konstruktoru inicializátoru seznamu, který má *weightlist* parametr vytvoří objekt distribuční s váhou ze seznamu intializer *weightlist*.

Konstruktor, který má *počet*, *nízkou*, *vysokou*, a *weightfunc* na základě parametrů konstrukce inicializovat objekt distribuce na tato pravidla:

- Pokud *počet* < 1, **n** = 1 a jako takový je ekvivalentní výchozí konstruktor, vždy generování nula.
- Pokud *počet* > 0, **n** = *počet*. Poskytuje **d** = (*vysokou* - *nízkou*) nebo **n** je větší než nula, pomocí **d** uniform podrozsahů, každý váhy je přiřazen následujícím způsobem: `weight[k] = weightfunc(x)`, kde **x** = *nízkou* + **tisíc**  *  **d** + **d** / 2, pro **tisíc** = 0,..., **n** - 1.

Konstruktor, který má `param_type` parametr *parametr* vytvoří objekt distribuční pomocí *parametr* jako strukturu uložený parametr.

## <a name="param_type"></a>  discrete_distribution::param_type

Uloží všechny parametry rozdělení.

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

*firstW* první iterator v seznamu, ze kterého chcete vytvořit rozdělení.

*lastW* poslední iterator v seznamu, ze kterého chcete vytvořit distribuční (bez – včetně protože iterátory používají prázdný element end).

*weightlist* [initializer_list](../cpp/initializers.md) ze kterého chcete vytvořit rozdělení.

*počet* počet elementů v rozsahu distribuce. Pokud *počet* je 0, jde o ekvivalent výchozí konstruktor (vždy vygeneruje nula).

*nízkou* nejnižší hodnotu v rozsahu distribuce.

*Vysoká* nejvyšší hodnotu v rozsahu distribuce.

*weightfunc* objekt reprezentující funkce pravděpodobnosti pro distribuci. Parametr i návratová hodnota musí být převoditelná na `double`.

*pravé* `param_type` objekt k porovnání s to.

### <a name="remarks"></a>Poznámky

Tento parametr balíček se dá předat do `operator()` ke generování návratovou hodnotu.

## <a name="see-also"></a>Viz také

[\<náhodné >](../standard-library/random.md)<br/>
