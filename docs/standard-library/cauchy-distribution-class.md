---
title: cauchy_distribution – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 61f055666a75d13b27f044589e3bd13a739ea7ec
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="cauchydistribution-class"></a>cauchy_distribution – třída

Generuje Cauchy distribuce.

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

*RealType* použije se výchozí hodnota s plovoucí desetinnou čárkou výsledný typ, `double`. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).

*URNG* uniform náhodné číslo generátor modul. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Šablony třídy popisuje distribuce, která vytváří hodnoty definované uživatelem s plovoucí desetinnou čárkou nebo typu `double` Pokud žádný je k dispozici, distribuovat podle Cauchy rozdělení. Následující tabulka odkazy na články o jednotlivé členy.

||||
|-|-|-|
|[cauchy_distribution](#cauchy_distribution)|`cauchy_distribution::a`|`cauchy_distribution::param`|
|`cauchy_distribution::operator()`|`cauchy_distribution::b`|[param_type](#param_type)|

Funkce vlastností `a()` a `b()` vrátit jejich příslušné hodnoty pro parametry uložené distribuční `a` a `b`.

Vlastnost člena `param()` Nastaví nebo vrátí `param_type` balíček parametr uložené distribuce.

`min()` a `max()` členské funkce vrátí nejmenší možný výsledek a největší možné výsledek, v uvedeném pořadí.

`reset()` – Členská funkce zahodí všechny hodnoty v mezipaměti, aby výsledkem další volání `operator()` nezávisí na žádné hodnoty získané z modulu před voláním.

`operator()` Členské funkce vrátí další generované hodnoty, které jsou založené na modulu URNG buď z aktuální parametr balíček nebo balíček zadaný parametr.

Další informace o distribučních třídy a jejich členové najdete v tématu [ \<náhodných >](../standard-library/random.md).

Podrobné informace o distribuci cauchy, najdete v článku Wolfram MathWorld [Cauchy distribuční](http://go.microsoft.com/fwlink/p/?linkid=400523).

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

Nejprve spusťte:

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

Druhý spusťte:

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

Třetí spusťte:

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

**Záhlaví:** \<náhodných >

**Namespace:** – std

## <a name="cauchy_distribution"></a>  cauchy_distribution::cauchy_distribution

Vytvoří rozdělení.

```cpp
explicit cauchy_distribution(result_type a = 0.0, result_type b = 1.0);
explicit cauchy_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

** `a` distribuční parametr.

*b* `b` distribuční parametr.

*Parametr* `param_type` struktura použitý k vytvoření distribuce.

### <a name="remarks"></a>Poznámky

**Předběžnou podmínku:** `0.0 < b`

První konstruktoru vytvoří objekt jehož uložené `a` hodnota obsahuje hodnotu *a* a jehož uložené `b` hodnota obsahuje hodnotu *b*.

Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuční voláním `param()` – členská funkce.

## <a name="param_type"></a>  cauchy_distribution::param_type

Uloží všechny parametry rozdělení.

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

** `a` distribuční parametr.

*b* `b` distribuční parametr.

*pravé* `param_type` objekt k porovnání s to.

### <a name="remarks"></a>Poznámky

**Předběžnou podmínku:** `0.0 < b`

Tato struktura mohou být předána do konstruktoru třídy distribuční při vytváření instancí, položky `param()` – členská funkce nastavit uložené parametrů z existující distribuční a to `operator()` má být použit místo uložené parametry.

## <a name="see-also"></a>Viz také

[\<náhodné >](../standard-library/random.md)<br/>
