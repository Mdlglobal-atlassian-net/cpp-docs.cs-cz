---
title: cauchy_distribution – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::cauchy_distribution
- random/std::cauchy_distribution::reset
- random/std::cauchy_distribution::a
- random/std::cauchy_distribution::b
- random/std::cauchy_distribution::param
- random/std::cauchy_distribution::min
- random/std::cauchy_distribution::max
- random/std::cauchy_distribution::operator()
- random/std::cauchy_distribution::param_type
- random/std::cauchy_distribution::param_type::a
- random/std::cauchy_distribution::param_type::b
- random/std::cauchy_distribution::param_type::operator==
- random/std::cauchy_distribution::param_type::operator!=
helpviewer_keywords:
- std::cauchy_distribution [C++]
- std::cauchy_distribution [C++], reset
- std::cauchy_distribution [C++], a
- std::cauchy_distribution [C++], b
- std::cauchy_distribution [C++], param
- std::cauchy_distribution [C++], min
- std::cauchy_distribution [C++], max
- std::cauchy_distribution [C++], param_type
- std::cauchy_distribution [C++], param_type
ms.assetid: 21522351-f2f1-46d9-97f0-d358c932356c
ms.openlocfilehash: ea75395c14c0babf5a047e7ae8f937e2a237b445
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317126"
---
# <a name="cauchy_distribution-class"></a>cauchy_distribution – třída

Generuje Cauchyho rozdělení.

## <a name="syntax"></a>Syntaxe

```cpp
template<class RealType = double>
class cauchy_distribution {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   explicit cauchy_distribution(result_type a = 0.0, result_type b = 1.0);
   explicit cauchy_distribution(const param_type& parm);
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

*URNG*\
Jednotný generátor náhodných čísel. Možné typy naleznete v [ \<tématu náhodné>](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje rozdělení, které vytváří hodnoty uživatelem určeného typu s plovoucí desetinnou čárkou, nebo zadejte **double,** pokud není k dispozici žádná, distribuovaná podle Cauchyho distribuce. Následující tabulka odkazuje na články o jednotlivých členech.

||||
|-|-|-|
|[cauchy_distribution](#cauchy_distribution)|`cauchy_distribution::a`|`cauchy_distribution::param`|
|`cauchy_distribution::operator()`|`cauchy_distribution::b`|[param_type](#param_type)|

Vlastnost funguje `a()` `b()` a vrátí jejich příslušné hodnoty `a` `b`pro parametry uložené distribuce a .

Člen `param()` vlastnosti nastaví `param_type` nebo vrátí balíček parametrů uložené distribuce.

A `min()` `max()` členské funkce vrátí nejmenší možný výsledek a největší možný výsledek.

Členská `reset()` funkce zahodí všechny hodnoty uložené v mezipaměti, `operator()` takže výsledek dalšího volání nezávisí na žádné hodnoty získané z motoru před voláním.

Členské `operator()` funkce vrátí další vygenerovanou hodnotu na základě modulu URNG, buď z aktuálního balíčku parametrů, nebo ze zadaného balíčku parametrů.

Další informace o distribučních třídách a jejich členech naleznete [ \<v tématu Random>](../standard-library/random.md).

Podrobné informace o cauchy distribuce, viz Wolfram MathWorld článek [Cauchy Distribuce](https://go.microsoft.com/fwlink/p/?linkid=400523).

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

    std::cauchy_distribution<> distr(a, b);

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
    std::cout << "Enter a floating point value for the 'a' distribution parameter: ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the 'b' distribution parameter (must be greater than zero): ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

První spuštění:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter: 0
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
a() == 0.0000000000
b() == 1.0000000000
Distribution for 10 samples:
    1: -3.4650392984
    2: -2.6369564174
    3: -0.0786978867
    4: -0.0609632093
    5: 0.0589387400
    6: 0.0589539764
    7: 0.1004592006
    8: 1.0965724260
    9: 1.4389408122
    10: 2.5253154706
```

Druhý běh:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter: 0
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 10
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
a() == 0.0000000000
b() == 10.0000000000
Distribution for 10 samples:
    1: -34.6503929840
    2: -26.3695641736
    3: -0.7869788674
    4: -0.6096320926
    5: 0.5893873999
    6: 0.5895397637
    7: 1.0045920062
    8: 10.9657242597
    9: 14.3894081218
    10: 25.2531547063
```

Třetí běh:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter: 10
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 10
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
a() == 10.0000000000
b() == 10.0000000000
Distribution for 10 samples:
    1: -24.6503929840
    2: -16.3695641736
    3: 9.2130211326
    4: 9.3903679074
    5: 10.5893873999
    6: 10.5895397637
    7: 11.0045920062
    8: 20.9657242597
    9: 24.3894081218
    10: 35.2531547063
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné>

**Obor názvů:** std

## <a name="cauchy_distributioncauchy_distribution"></a><a name="cauchy_distribution"></a>cauchy_distribution::cauchy_distribution

Vytvoří rozdělení.

```cpp
explicit cauchy_distribution(result_type a = 0.0, result_type b = 1.0);
explicit cauchy_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*A*\
Parametr `a` distribuce.

*B*\
Parametr `b` distribuce.

*parm*\
Struktura `param_type` slouží k vytvoření distribuce.

### <a name="remarks"></a>Poznámky

**Předpokladem:**`0.0 < b`

První konstruktor zkonstruoval objekt, jehož `a` uložená hodnota obsahuje hodnotu *a* jejíž uložená `b` hodnota obsahuje hodnotu *b*.

Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parm*. Aktuální parametry existující distribuce můžete získat a nastavit `param()` voláním členské funkce.

## <a name="cauchy_distributionparam_type"></a><a name="param_type"></a>cauchy_distribution::param_type

Ukládá všechny parametry distribuce.

```cpp
struct param_type {
   typedef cauchy_distribution<result_type> distribution_type;
   param_type(result_type a = 0.0, result_type b = 1.0);
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

**Předpokladem:**`0.0 < b`

Tato struktura může být předána konstruktoru třídy distribuce `param()` při vytváření instancí, členské funkci pro `operator()` nastavení uložených parametrů existující distribuce a k použití namísto uložených parametrů.

## <a name="see-also"></a>Viz také

[\<náhodné>](../standard-library/random.md)
