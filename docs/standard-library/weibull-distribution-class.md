---
title: weibull_distribution – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b651f4117cae6d3b4ed72d22ace5194e5d24446
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957669"
---
# <a name="weibulldistribution-class"></a>weibull_distribution – třída

Generuje rozdělení WEIBULL.

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

*RealType* typu s plovoucí desetinnou čárkou výsledku, výchozí hodnota je **double**. Možné typy, najdete v části [ \<náhodné >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Třída šablony popisuje distribuci, která vytváří hodnoty plovoucí desetinnou čárkou uživatelem zadaného typu nebo typu **double** Pokud se žádný nezadá, které jsou rozděleny podle rozdělení Weibull. Následující tabulka odkazuje na články týkající se jednotlivých členů.

||||
|-|-|-|
|[weibull_distribution](#weibull_distribution)|`weibull_distribution::a`|`weibull_distribution::param`|
|`weibull_distribution::operator()`|`weibull_distribution::b`|[param_type](#param_type)|

Funkce vlastností `a()` a `b()` vrátit jejich příslušné hodnoty pro parametry uložené distribuční *a* a *b*.

Vlastnost člena `param()` Nastaví nebo vrátí `param_type` uložené distribuční balíček parametrů.

`min()` a `max()` členské funkce vrátí nejmenší možné výsledek a největší výsledek je to možné, v uvedeném pořadí.

`reset()` Členská funkce odstraní všechny hodnoty uložené v mezipaměti tak, aby výsledek dalšího volání do `operator()` nezávisí na žádné hodnoty získané z modulu před voláním.

`operator()` Členské funkce vrátí další vygenerovanou hodnotu založená na modulu URNG z aktuálního balíčku parametrů nebo balíček zadaný parametr.

Další informace o distribuci třídy a jejich členy, naleznete v tématu [ \<náhodné >](../standard-library/random.md).

Podrobné informace o rozdělení Weibull, najdete v článku Wolfram MathWorld [rozdělení Weibull](http://go.microsoft.com/fwlink/p/?linkid=401115).

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

Nejprve spusťte:

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

Druhé spuštění:

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

**Záhlaví:** \<náhodné >

**Namespace:** std

## <a name="weibull_distribution"></a>  weibull_distribution::weibull_distribution

```cpp
explicit weibull_distribution(result_type a = 1.0, result_type b = 1.0);
explicit weibull_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*a*  
`a` Parametru distribuce.

*b*  
`b` Parametru distribuce.

*Parametr*  
`param_type` Struktura používaná k vytvoření distribuce.

### <a name="remarks"></a>Poznámky

**Předpoklad:** `0.0 < a` a `0.0 < b`

První konstruktoru vytvoří objekt jehož uložené `a` hodnota obsahuje hodnotu *a* a jehož uložené `b` hodnota obsahuje hodnotu *b*.

Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuční voláním `param()` členskou funkci.

## <a name="param_type"></a>  weibull_distribution::param_type

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

*a*  
`a` Parametru distribuce.

*b*  
`b` Parametru distribuce.

*doprava*  
`param_type` Objekt k porovnání s tím.

### <a name="remarks"></a>Poznámky

**Předpoklad:** `0.0 < a` a `0.0 < b`

Tato struktura může být předán konstruktoru třídy distribuce při vytváření instance, do `param()` členskou funkci pro nastavení uložené parametry existující distribuční a k `operator()` použije místo uložené parametry.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
