---
title: bernoulli_distribution – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::bernoulli_distribution
- random/std::bernoulli_distribution::reset
- random/std::bernoulli_distribution::p
- random/std::bernoulli_distribution::param
- random/std::bernoulli_distribution::min
- random/std::bernoulli_distribution::max
- random/std::bernoulli_distribution::operator()
- random/std::bernoulli_distribution::param_type
- random/std::bernoulli_distribution::param_type::p
- random/std::bernoulli_distribution::param_type::operator==
- random/std::bernoulli_distribution::param_type::operator!=
helpviewer_keywords:
- std::bernoulli_distribution [C++]
- std::bernoulli_distribution [C++], reset
- std::bernoulli_distribution [C++], p
- std::bernoulli_distribution [C++], param
- std::bernoulli_distribution [C++], min
- std::bernoulli_distribution [C++], max
- std::bernoulli_distribution [C++], param_type
- std::bernoulli_distribution [C++], param_type
ms.assetid: 586bcde1-95ca-411a-bf17-4aaf19482f34
ms.openlocfilehash: faadc99b6351af884331e6658e1e11de8def2195
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447776"
---
# <a name="bernoullidistribution-class"></a>bernoulli_distribution – třída

Generuje Bernoulliho rozdělení.

## <a name="syntax"></a>Syntaxe

```cpp
class bernoulli_distribution
   {
public:
   // types
   typedef bool result_type;
   struct param_type;

   // constructors and reset functions
   explicit bernoulli_distribution(double p = 0.5);
   explicit bernoulli_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   double p() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*URNG*\
Jednotný modul generátoru náhodných čísel. Možné typy naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Třída popisuje distribuci, která vytváří hodnoty typu **bool**, distribuované podle funkce Bernoulliho rozdělení diskrétní distribuce. Následující tabulka obsahuje odkazy na články týkající se jednotlivých členů.

||||
|-|-|-|
|[bernoulli_distribution](#bernoulli_distribution)|`bernoulli_distribution::p`|`bernoulli_distribution::param`|
|`bernoulli_distribution::operator()`||[param_type](#param_type)|

Člen `p()` vlastnosti vrátí aktuálně uloženou hodnotu `p`distribučního parametru.

Člen `param()` vlastnosti nastaví nebo `param_type` vrátí uložený balíček parametrů distribuce.

Členské funkce `max()` a vracejí nejmenší možný výsledek a největší možný výsledek, v uvedeném pořadí. `min()`

Členská funkce zahodí všechny hodnoty uložené v mezipaměti, takže výsledek dalšího `operator()` volání není závislý na všech hodnotách získaných z modulu před voláním. `reset()`

`operator()` Členské funkce vrátí další vygenerovanou hodnotu založenou na modulu URNG, buď z aktuálního balíčku parametrů, nebo pomocí zadaného balíčku parametrů.

Další informace o třídách distribuce a jejich členech naleznete v tématu [ \<Random >](../standard-library/random.md).

Podrobné informace o funkci rozdělení dílčí pravděpodobnosti distribuce naleznete v článku o [Bernoulliho distribuci](https://go.microsoft.com/fwlink/p/?linkid=398467)v Wolfram MathWorld.

## <a name="example"></a>Příklad

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double p, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::bernoulli_distribution distr(p);

    std::cout << "p == " << distr.p() << std::endl;

    // generate the distribution as a histogram
    std::map<bool, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Histogram for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::boolalpha << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double p_dist = 0.5;
    int samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a double value for p distribution (where 0.0 <= p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(p_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .45
Enter an integer value for a sample count: 100
p == 0.45
Histogram for 100 samples:
false :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
true :::::::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<náhodné >

**Obor názvů:** std

## <a name="bernoulli_distribution"></a>bernoulli_distribution::bernoulli_distribution

Sestaví rozdělení.

```cpp
explicit bernoulli_distribution(double p = 0.5);
explicit bernoulli_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*trub*\
Uložený `p` parametr distribuce.

*parametr*\
`param_type` Struktura použitá k sestavení distribuce.

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `0.0 ≤ p ≤ 1.0`

První konstruktor vytvoří objekt, jehož uložená `p` hodnota obsahuje hodnotu *p*.

Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuce voláním `param()` členské funkce.

## <a name="param_type"></a>bernoulli_distribution::p aram_type

Obsahuje parametry distribuce.

struct param_type {typedef bernoulli_distribution distribution_type; param_type (Double p = 0,5); dvojitá p () const;

   bool – operátor = = (const param_type & Right) const; bool – operátor! = (const param_type & Right) const; };

### <a name="parameters"></a>Parametry

*trub*\
Uložený `p` parametr distribuce.

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `0.0 ≤ p ≤ 1.0`

Tuto strukturu lze předat konstruktoru třídy distribuce při vytváření instance, `param()` členské funkci pro nastavení uložených parametrů stávající distribuce a k `operator()` použití namísto uložených parametrů.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)
