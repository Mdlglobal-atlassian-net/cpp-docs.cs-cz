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
ms.openlocfilehash: 752226c9cacfdd36b93890502d62187f7b44a8da
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454942"
---
# <a name="uniformrealdistribution-class"></a>uniform_real_distribution – třída

Generuje jednotný (každá hodnota je stejně pravděpodobná) rozdělení plovoucí desetinné čárky v rámci výstupní oblasti, která je zapsána jako výhradní.

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

*RealType*\
Typ výsledku s plovoucí desetinnou čárkou, výchozí hodnota je **Double**. Možné typy naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Třída šablony popisuje kompletní distribuci, která vytváří hodnoty celočíselně zadaného typu s plovoucí desetinnou čárkou s distribucí, aby každá hodnota byla stejně pravděpodobná. Následující tabulka obsahuje odkazy na články týkající se jednotlivých členů.

||||
|-|-|-|
|[uniform_real_distribution](#uniform_real_distribution)|`uniform_real_distribution::a`|`uniform_real_distribution::param`|
|`uniform_real_distribution::operator()`|`uniform_real_distribution::b`|[param_type](#param_type)|

Člen `a()` vlastnosti vrátí aktuálně uloženou minimální hranici distribuce, zatímco `b()` vrátí aktuálně uloženou maximální vazbu. Pro tuto třídu distribuce jsou tyto minimální a maximální hodnoty stejné jako ty, které jsou vráceny funkcemi `min()` společných vlastností a `max()` popsány v [ \<tématu náhodné >](../standard-library/random.md) .

Člen `param()` vlastnosti nastaví nebo `param_type` vrátí uložený balíček parametrů distribuce.

Členské funkce `max()` a vracejí nejmenší možný výsledek a největší možný výsledek, v uvedeném pořadí. `min()`

Členská funkce zahodí všechny hodnoty uložené v mezipaměti, takže výsledek dalšího `operator()` volání není závislý na všech hodnotách získaných z modulu před voláním. `reset()`

`operator()` Členské funkce vrátí další vygenerovanou hodnotu založenou na modulu URNG, buď z aktuálního balíčku parametrů, nebo pomocí zadaného balíčku parametrů.

Další informace o třídách distribuce a jejich členech naleznete v tématu [ \<Random >](../standard-library/random.md).

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

**Hlavička:** \<náhodné >

**Obor názvů:** std

## <a name="uniform_real_distribution"></a>uniform_real_distribution::uniform_real_distribution

Sestaví rozdělení.

```cpp
explicit uniform_real_distribution(result_type a = 0.0, result_type b = 1.0);
explicit uniform_real_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*určitého*\
Dolní mez pro náhodné hodnoty, včetně.

*b*\
Horní mez pro náhodné hodnoty, exkluzivní.

*parametr*\
`param_type` Struktura použitá k sestavení distribuce.

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `a < b`

První konstruktor vytvoří objekt, jehož uložená hodnota *a* drží hodnotu *a* a jehož uložená hodnota *b* drží hodnotu *b*.

Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuce voláním `param()` členské funkce.

## <a name="param_type"></a>  uniform_real_distribution::param_type

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

*určitého*\
Dolní mez pro náhodné hodnoty, včetně.

*b*\
Horní mez pro náhodné hodnoty, exkluzivní.

*Kliknutím*\
`param_type` Objekt, který se má porovnat.

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `a < b`

Tuto strukturu lze předat konstruktoru třídy distribuce při vytváření instance, `param()` členské funkci pro nastavení uložených parametrů stávající distribuce a k `operator()` použití namísto uložených parametrů.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)
