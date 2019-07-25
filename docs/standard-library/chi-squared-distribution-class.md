---
title: chi_squared_distribution – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::chi_squared_distribution
- random/std::chi_squared_distribution::reset
- random/std::chi_squared_distribution::n
- random/std::chi_squared_distribution::param
- random/std::chi_squared_distribution::min
- random/std::chi_squared_distribution::max
- random/std::chi_squared_distribution::operator()
- random/std::chi_squared_distribution::param_type
- random/std::chi_squared_distribution::param_type::n
- random/std::chi_squared_distribution::param_type::operator==
- random/std::chi_squared_distribution::param_type::operator!=
helpviewer_keywords:
- std::chi_squared_distribution [C++]
- std::chi_squared_distribution [C++], reset
- std::chi_squared_distribution [C++], n
- std::chi_squared_distribution [C++], param
- std::chi_squared_distribution [C++], min
- std::chi_squared_distribution [C++], max
- std::chi_squared_distribution [C++], param_type
- std::chi_squared_distribution [C++], param_type
ms.assetid: 9b603fbe-cafd-4a92-b8c5-a434d60b8122
ms.openlocfilehash: 2eac3324516cf88a114064cf0145593c7bf4806b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459467"
---
# <a name="chisquareddistribution-class"></a>chi_squared_distribution – třída

Vygeneruje rozdělení chí-kvadrát.

## <a name="syntax"></a>Syntaxe

```cpp
template<class RealType = double>
class chi_squared_distribution {
public:
    // types
    typedef RealType result_type;
    struct param_type;

    // constructor and reset functions
    explicit chi_squared_distribution(RealType n = 1);
    explicit chi_squared_distribution(const param_type& parm);
    void reset();

    // generating functions
    template <class URNG>
    result_type operator()(URNG& gen);
    template <class URNG>
    result_type operator()(URNG& gen, const param_type& parm);

    // property functions
    RealType n() const;
    param_type param() const;
    void param(const param_type& parm);
    result_type min() const;
    result_type max() const;
};
```

### <a name="parameters"></a>Parametry

*RealType*\
Typ výsledku s plovoucí desetinnou čárkou, výchozí hodnota je **Double**. Možné typy naleznete v tématu [ \<Random >](../standard-library/random.md).

*URNG*\
Jednotný modul generátoru náhodných čísel. Možné typy naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Třída šablony popisuje distribuci, která vytváří hodnoty typu s plovoucí desetinnou čárkou, nebo typ **Double** , pokud není k dispozici, distribuované podle rozdělení chí-kvadrát. Následující tabulka obsahuje odkazy na články týkající se jednotlivých členů.

||||
|-|-|-|
|[chi_squared_distribution](../standard-library/chi-squared-distribution-class.md)|`chi_squared_distribution::n`|`chi_squared_distribution::param`|
|`chi_squared_distribution::operator()`||[param_type](#param_type)|

Funkce `n()` Property vrátí hodnotu pro uložený parametr `n`distribuce.

Člen `param()` vlastnosti nastaví nebo `param_type` vrátí uložený balíček parametrů distribuce.

Členské funkce `max()` a vracejí nejmenší možný výsledek a největší možný výsledek, v uvedeném pořadí. `min()`

Členská funkce zahodí všechny hodnoty uložené v mezipaměti, takže výsledek dalšího `operator()` volání není závislý na všech hodnotách získaných z modulu před voláním. `reset()`

`operator()` Členské funkce vrátí další vygenerovanou hodnotu založenou na modulu URNG, buď z aktuálního balíčku parametrů, nebo pomocí zadaného balíčku parametrů.

Další informace o třídách distribuce a jejich členech naleznete v tématu [ \<Random >](../standard-library/random.md).

Podrobné informace o rozdělení chí-kvadrát naleznete v článku Wolfram MathWorld article [chí-kvadráted Distribution](https://go.microsoft.com/fwlink/p/?linkid=400528).

## <a name="example"></a>Příklad

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double n, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;
    std::mt19937 gen(1701);

    std::chi_squared_distribution<> distr(n);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "n() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.n() << std::endl;

    // generate the distribution as a histogram
    std::map<double, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        std::cout << std::fixed << std::setw(11) << ++counter << ": "
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double n_dist = 0.5;
    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the \'n\' distribution parameter (must be greater than zero): ";
    std::cin >> n_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(n_dist, samples);
}
```

První spuštění:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .5
Enter an integer value for the sample count: 10

min() == 4.94066e-324
max() == 1.79769e+308
n() == 0.5000000000
Distribution for 10 samples:
    1: 0.0007625595
    2: 0.0016895062
    3: 0.0058683478
    4: 0.0189647765
    5: 0.0556619371
    6: 0.1448191353
    7: 0.1448245325
    8: 0.1903494379
    9: 0.9267525768
    10: 1.5429743723
```

Druhý běh:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .3333
Enter an integer value for the sample count: 10

min() == 4.94066e-324
max() == 1.79769e+308
n() == 0.3333000000
Distribution for 10 samples:
    1: 0.0000148725
    2: 0.0000490528
    3: 0.0003175988
    4: 0.0018454535
    5: 0.0092808795
    6: 0.0389540735
    7: 0.0389562514
    8: 0.0587028468
    9: 0.6183666639
    10: 1.3552086624
```

Třetí běh:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1000
Enter an integer value for the sample count: 10

min() == 4.94066e-324
max() == 1.79769e+308
n() == 1000.0000000000
Distribution for 10 samples:
    1: 958.5284624473
    2: 958.7882787809
    3: 963.0667684792
    4: 987.9638091514
    5: 1016.2433493745
    6: 1021.9337111110
    7: 1021.9723046240
    8: 1035.7622110505
    9: 1043.8725156645
    10: 1054.7051509381
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<náhodné >

**Obor názvů:** std

## <a name="chi_squared_distribution"></a>chi_squared_distribution::chi_squared_distribution

Sestaví rozdělení.

```cpp
explicit chi_squared_distribution(result_type n = 1.0);
explicit chi_squared_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*n*\
Parametr `n` distribuce.

*parametr*\
Struktura parametrů používaná k sestavení distribuce.

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `0.0 < n`

První konstruktor vytvoří objekt, jehož uložená `n` hodnota obsahuje hodnotu *n*.

Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuce voláním `param()` členské funkce.

## <a name="param_type"></a>chi_squared_distribution::p aram_type

Ukládá parametry distribuce.

```cpp
struct param_type {
   typedef chi_squared_distribution<result_type> distribution_type;
   param_type(result_type n = 1.0);
   result_type n() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*n*\
Parametr `n` distribuce.

*Kliknutím*\
`param_type` Objekt, který se má porovnat.

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `0.0 < n`

Tuto strukturu lze předat konstruktoru třídy distribuce při vytváření instance, `param()` členské funkci pro nastavení uložených parametrů stávající distribuce a k `operator()` použití namísto uložených parametrů.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)
