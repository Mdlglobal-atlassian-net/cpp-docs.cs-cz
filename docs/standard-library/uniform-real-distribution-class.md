---
title: uniform_real_distribution – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::uniform_real_distribution
- random/std::uniform_real_distribution::reset
- random/std::uniform_real_distribution::a
- random/std::uniform_real_distribution::b
- random/std::uniform_real_distribution::param
- random/std::uniform_real_distribution::min
- random/std::uniform_real_distribution::max
- random/std::uniform_real_distribution::operator()
- random/std::uniform_real_distribution::param_type
- random/std::uniform_real_distribution::param_type::a
- random/std::uniform_real_distribution::param_type::b
- random/std::uniform_real_distribution::param_type::operator==
- random/std::uniform_real_distribution::param_type::operator!=
helpviewer_keywords:
- std::uniform_real_distribution [C++]
- std::uniform_real_distribution [C++], reset
- std::uniform_real_distribution [C++], a
- std::uniform_real_distribution [C++], b
- std::uniform_real_distribution [C++], param
- std::uniform_real_distribution [C++], min
- std::uniform_real_distribution [C++], max
- std::uniform_real_distribution [C++], param_type
- std::uniform_real_distribution [C++], param_type
ms.assetid: 5cf906fd-0319-4984-b21b-98425cd7532d
ms.openlocfilehash: 4f293f73eb1fa8a38bf06692ef5b7938faeab0d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367275"
---
# <a name="uniform_real_distribution-class"></a>uniform_real_distribution – třída

Generuje jednotné (každá hodnota je stejně pravděpodobné) rozložení s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou třídou v rámci výstupní rozsah, který je včetně výhradní.

## <a name="syntax"></a>Syntaxe

```cpp
template<class RealType = double>
   class uniform_real_distribution {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructors and reset functions
   explicit uniform_real_distribution(
      result_type a = 0.0, result_type b = 1.0);
   explicit uniform_real_distribution(const param_type& parm);
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

Šablona třídy popisuje výhradní distribuci, která vytváří hodnoty uživatelem určeného integrálního typu s plovoucí desetinnou čárkou s rozdělením tak, aby každá hodnota byla stejně pravděpodobná. Následující tabulka odkazuje na články o jednotlivých členech.

||||
|-|-|-|
|[uniform_real_distribution](#uniform_real_distribution)|`uniform_real_distribution::a`|`uniform_real_distribution::param`|
|`uniform_real_distribution::operator()`|`uniform_real_distribution::b`|[param_type](#param_type)|

Člen `a()` vlastnosti vrátí aktuálně uloženou minimální vazbu distribuce, zatímco `b()` vrátí aktuálně uloženou maximální vazbu. Pro tuto třídu distribuce tyto minimální a maximální hodnoty jsou `min()` stejné `max()` jako ty vrácené funkce common vlastností a popsané v [ \<náhodném>](../standard-library/random.md) tématu.

Člen `param()` vlastnosti nastaví `param_type` nebo vrátí balíček parametrů uložené distribuce.

A `min()` `max()` členské funkce vrátí nejmenší možný výsledek a největší možný výsledek.

Členská `reset()` funkce zahodí všechny hodnoty uložené v mezipaměti, `operator()` takže výsledek dalšího volání nezávisí na žádné hodnoty získané z motoru před voláním.

Členské `operator()` funkce vrátí další vygenerovanou hodnotu na základě modulu URNG, buď z aktuálního balíčku parametrů, nebo ze zadaného balíčku parametrů.

Další informace o distribučních třídách a jejich členech naleznete [ \<v tématu Random>](../standard-library/random.md).

## <a name="example"></a>Příklad

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double a, const double b, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::uniform_real_distribution<> distr(a,b);

    std::cout << "lower bound == " << distr.a() << std::endl;
    std::cout << "upper bound == " << distr.b() << std::endl;

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
            << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double a_dist = 1.0;
    double b_dist = 1.5;

    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the lower bound of the distribution: ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the upper bound of the distribution: ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the lower bound of the distribution: 0
Enter a floating point value for the upper bound of the distribution: 1
Enter an integer value for the sample count: 10
lower bound == 0
upper bound == 1
Distribution for 10 samples:
          1: 0.0288609485
          2: 0.2007994386
          3: 0.3027480117
          4: 0.4124758695
          5: 0.4413777133
          6: 0.4846447405
          7: 0.6225745916
          8: 0.6880935217
          9: 0.7541936723
         10: 0.8795716566
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné>

**Obor názvů:** std

## <a name="uniform_real_distributionuniform_real_distribution"></a><a name="uniform_real_distribution"></a>uniform_real_distribution::uniform_real_distribution

Vytvoří rozdělení.

```cpp
explicit uniform_real_distribution(result_type a = 0.0, result_type b = 1.0);
explicit uniform_real_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*A*\
Dolní mez pro náhodné hodnoty včetně.

*B*\
Horní mez pro náhodné hodnoty, výhradní.

*parm*\
Struktura `param_type` slouží k vytvoření distribuce.

### <a name="remarks"></a>Poznámky

**Předpokladem:**`a < b`

První konstruktor zkonstruoval objekt, jehož *uložená* hodnota obsahuje hodnotu *a* jejíž uložená hodnota *b* obsahuje hodnotu *b*.

Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parm*. Aktuální parametry existující distribuce můžete získat a nastavit `param()` voláním členské funkce.

## <a name="uniform_real_distributionparam_type"></a><a name="param_type"></a>uniform_real_distribution::param_type

Ukládá všechny parametry distribuce.

```cpp
struct param_type {
   typedef uniform_real_distribution<result_type> distribution_type;
   param_type(result_type a = 0.0, result_type b = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*A*\
Dolní mez pro náhodné hodnoty včetně.

*B*\
Horní mez pro náhodné hodnoty, výhradní.

*Právo*\
Objekt `param_type` porovnat s tímto.

### <a name="remarks"></a>Poznámky

**Předpokladem:**`a < b`

Tato struktura může být předána konstruktoru třídy distribuce `param()` při vytváření instancí, členské funkci pro `operator()` nastavení uložených parametrů existující distribuce a k použití namísto uložených parametrů.

## <a name="see-also"></a>Viz také

[\<náhodné>](../standard-library/random.md)
