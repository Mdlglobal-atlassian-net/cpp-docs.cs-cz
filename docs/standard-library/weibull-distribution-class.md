---
title: weibull_distribution – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::weibull_distribution
- random/std::weibull_distribution::reset
- random/std::weibull_distribution::a
- random/std::weibull_distribution::b
- random/std::weibull_distribution::param
- random/std::weibull_distribution::min
- random/std::weibull_distribution::max
- random/std::weibull_distribution::operator()
- random/std::weibull_distribution::param_type
- random/std::weibull_distribution::param_type::a
- random/std::weibull_distribution::param_type::b
- random/std::weibull_distribution::param_type::operator==
- random/std::weibull_distribution::param_type::operator!=
helpviewer_keywords:
- std::weibull_distribution [C++]
- std::weibull_distribution [C++], reset
- std::weibull_distribution [C++], a
- std::weibull_distribution [C++], b
- std::weibull_distribution [C++], param
- std::weibull_distribution [C++], min
- std::weibull_distribution [C++], max
- std::weibull_distribution [C++], param_type
- std::weibull_distribution [C++], param_type
ms.assetid: f20b49d3-1b9a-41af-8db4-baf800eaa02b
ms.openlocfilehash: 01640cd700f54facba06f65f63e172abc668a5be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366381"
---
# <a name="weibull_distribution-class"></a>weibull_distribution – třída

Generuje weibullovu distribuci.

## <a name="syntax"></a>Syntaxe

```cpp
class weibull_distribution
   {
   public:
    // types
   typedef RealType result_type;
   struct param_type;

    // constructor and reset functions
   explicit weibull_distribution(result_type a = 1.0, result_type b = 1.0);
   explicit weibull_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
      result_type operator()(URNG& gen);
   template <class URNG>
      result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type a() const;
   result_type b() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*Skutečný typ*\
Typ výsledku s plovoucí desetinnou tázkem, výchozí hodnota **je double**. Možné typy naleznete v [ \<tématu náhodné>](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje rozdělení, které vytváří hodnoty uživatelem zadaného typu s plovoucí desetinnou čárkou, nebo zadejte **double,** pokud není k dispozici žádná, distribuovaná podle Weibullovy distribuce. Následující tabulka odkazuje na články o jednotlivých členech.

||||
|-|-|-|
|[weibull_distribution](#weibull_distribution)|`weibull_distribution::a`|`weibull_distribution::param`|
|`weibull_distribution::operator()`|`weibull_distribution::b`|[param_type](#param_type)|

Vlastnost funguje `a()` `b()` a vrátí jejich příslušné hodnoty pro uložené distribuční parametry *a* a *b*.

Člen `param()` vlastnosti nastaví `param_type` nebo vrátí balíček parametrů uložené distribuce.

A `min()` `max()` členské funkce vrátí nejmenší možný výsledek a největší možný výsledek.

Členská `reset()` funkce zahodí všechny hodnoty uložené v mezipaměti, `operator()` takže výsledek dalšího volání nezávisí na žádné hodnoty získané z motoru před voláním.

Členské `operator()` funkce vrátí další vygenerovanou hodnotu na základě modulu URNG, buď z aktuálního balíčku parametrů, nebo ze zadaného balíčku parametrů.

Další informace o distribučních třídách a jejich členech naleznete [ \<v tématu Random>](../standard-library/random.md).

Podrobné informace o distribuci Weibull naleznete v článku Wolfram MathWorld [Weibull Distribution](https://mathworld.wolfram.com/WeibullDistribution.html).

## <a name="example"></a>Příklad

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double a, const double b, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;
    std::mt19937 gen(1701);

    std::weibull_distribution<> distr(a, b);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "a() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.a() << std::endl;
    std::cout << "b() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.b() << std::endl;

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
    double a_dist = 0.0;
    double b_dist = 1;

    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the 'a' distribution parameter (must be greater than zero): ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the 'b' distribution parameter (must be greater than zero): ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

## <a name="output"></a>Výstup

První spuštění:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter (must be greater than zero): 1
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
a() == 1.0000000000
b() == 1.0000000000
Distribution for 10 samples:
    1: 0.0936880533
    2: 0.1225944894
    3: 0.6443593183
    4: 0.6551171649
    5: 0.7313457551
    6: 0.7313557977
    7: 0.7590097389
    8: 1.4466885214
    9: 1.6434088411
    10: 2.1201210996
```

Druhý běh:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter (must be greater than zero): .5
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 5.5
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
a() == 0.5000000000
b() == 5.5000000000
Distribution for 10 samples:
    1: 0.0482759823
    2: 0.0826617486
    3: 2.2835941207
    4: 2.3604817485
    5: 2.9417663742
    6: 2.9418471657
    7: 3.1685268104
    8: 11.5109922290
    9: 14.8543594043
    10: 24.7220241239
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné>

**Obor názvů:** std

## <a name="weibull_distributionweibull_distribution"></a><a name="weibull_distribution"></a>weibull_distribution::weibull_distribution

```cpp
explicit weibull_distribution(result_type a = 1.0, result_type b = 1.0);
explicit weibull_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*A*\
Parametr `a` distribuce.

*B*\
Parametr `b` distribuce.

*parm*\
Struktura `param_type` slouží k vytvoření distribuce.

### <a name="remarks"></a>Poznámky

**Předpokladem:** `0.0 < a` a`0.0 < b`

První konstruktor zkonstruoval objekt, jehož `a` uložená hodnota obsahuje hodnotu *a* jejíž uložená `b` hodnota obsahuje hodnotu *b*.

Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parm*. Aktuální parametry existující distribuce můžete získat a nastavit `param()` voláním členské funkce.

## <a name="weibull_distributionparam_type"></a><a name="param_type"></a>weibull_distribution::param_type

Ukládá parametry distribuce.

```cpp
struct param_type {
   typedef weibull_distribution<result_type> distribution_type;
   param_type(result_type a = 1.0, result_type b = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*A*\
Parametr `a` distribuce.

*B*\
Parametr `b` distribuce.

*Právo*\
Objekt `param_type` porovnat s tímto.

### <a name="remarks"></a>Poznámky

**Předpokladem:** `0.0 < a` a`0.0 < b`

Tato struktura může být předána konstruktoru třídy distribuce `param()` při vytváření instancí, členské funkci pro `operator()` nastavení uložených parametrů existující distribuce a k použití namísto uložených parametrů.

## <a name="see-also"></a>Viz také

[\<náhodné>](../standard-library/random.md)
