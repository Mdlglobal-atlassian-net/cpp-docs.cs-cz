---
title: discrete_distribution – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 97ac9d7e8e00e5f81d974aa84befaad99881391d
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108756"
---
# <a name="discretedistribution-class"></a>discrete_distribution – třída

Generuje rozdělení samostatného celého čísla, která má šířku uniform intervalech pomocí jednotného pravděpodobnost v každém intervalu.

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

*IntType*<br/>
Typ výsledku celého čísla, výchozí hodnota je **int**. Možné typy, najdete v části [ \<náhodné >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Toto rozdělení vzorkování má jednotné šířkou intervalech pomocí jednotného pravděpodobnost v každém intervalu. Informace o dalších vzorkování distribucích najdete v tématu [piecewise_linear_distribution – třída](../standard-library/piecewise-linear-distribution-class.md) a [piecewise_constant_distribution – třída](../standard-library/piecewise-constant-distribution-class.md).

Následující tabulka odkazuje na články týkající se jednotlivých členů:

|||
|-|-|
|[discrete_distribution](#discrete_distribution)|`discrete_distribution::param`|
|`discrete_distribution::operator()`|[param_type](#param_type)|

Funkce vlastností `vector<double> probabilities()` vrátí jednotlivé pravděpodobnosti pro každé celé číslo, vygeneruje.

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

**Záhlaví:** \<náhodné >

**Namespace:** std

## <a name="discrete_distribution"></a>  discrete_distribution::discrete_distribution

Vytvoří rozložení.

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

*firstW*<br/>
První iterátor v seznamu, ze které k vytvoření distribuce.

*lastW*<br/>
Poslední iterátor v seznamu, ze kterého se má vytvořit distribuce (inkluzivní protože iterátorů, použijte prázdný element end).

*weightlist*<br/>
[Initializer_list](../cpp/initializers.md) odkud k vytvoření distribuce.

*Počet*<br/>
Počet prvků v rozsahu distribuce. Pokud `count==0`, ekvivalentní výchozí konstruktor (generuje vždy nula).

*Nízká*<br/>
Nejnižší hodnotu v rozsahu distribuce.

*Vysoká*<br/>
Nejvyšší číslo v rozsahu distribuce.

*weightfunc*<br/>
Objekt, který představuje funkci pravděpodobnosti pro distribuci. Parametr a vrácená hodnota musí být převeditelný na **double**.

*Parametr*<br/>
`param_type` Struktura používaná k vytvoření distribuce.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor vytvoří objekt, jehož hodnota pravděpodobnosti uložené má jeden prvek s hodnotou 1. Výsledkem bude distribuci, která generuje vždy nula.

Konstruktor rozsah iterátoru, který obsahuje parametry *firstW* a *lastW* vytvoří objekt distribuce pomocí hodnot váhu převzetí interval pořadí z iterátory [ *firstW*, *lastW*).

Inicializátor seznamu konstruktor, který má *weightlist* parametr vytvoří objekt distribuce s váhy ze seznamu intializer *weightlist*.

Konstruktor, který má *počet*, *nízké*, *vysokou*, a *weightfunc* na základě parametrů konstruktorů distribuce objekt inicializován v těchto pravidlech:

- Pokud *počet* < 1, **n** = 1 a proto je ekvivalentní výchozí konstruktor, generuje se vždy nula.
- Pokud *počet* > 0, **n** = *počet*. K dispozici **d** = (*vysokou* - *nízké*) / **n** je větší než nula, pomocí **d** jednotné podrozsahů, každý váha je přiřazena následujícím způsobem: `weight[k] = weightfunc(x)`, kde **x** = *nízké* + **k**  *  **d** + **d** / 2, pro **k** = 0,..., **n** - 1.

Konstruktor, který má `param_type` parametr *parametr* vytvoří objekt distribuce pomocí *parametr* jako struktury uloženými parametry.

## <a name="param_type"></a>  discrete_distribution::param_type

Obsahuje všechny parametry distribuce.

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

*firstW*<br/>
První iterátor v seznamu, ze které k vytvoření distribuce.

*lastW*<br/>
Poslední iterátor v seznamu, ze kterého se má vytvořit distribuce (inkluzivní protože iterátorů, použijte prázdný element end).

*weightlist*<br/>
[Initializer_list](../cpp/initializers.md) odkud k vytvoření distribuce.

*Počet*<br/>
Počet prvků v rozsahu distribuce. Pokud *počet* je 0, jedná se o ekvivalent výchozího konstruktoru (generuje vždy nula).

*Nízká*<br/>
Nejnižší hodnotu v rozsahu distribuce.

*Vysoká*<br/>
Nejvyšší číslo v rozsahu distribuce.

*weightfunc*<br/>
Objekt, který představuje funkci pravděpodobnosti pro distribuci. Parametr a vrácená hodnota musí být převeditelný na **double**.

*doprava*<br/>
`param_type` Objekt k porovnání s tím.

### <a name="remarks"></a>Poznámky

Tento balíček parametrů může být předán `operator()` ke generování návratovou hodnotu.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
