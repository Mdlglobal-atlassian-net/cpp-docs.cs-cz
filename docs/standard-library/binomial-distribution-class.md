---
title: binomial_distribution – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::binomial_distribution
- random/std::binomial_distribution::reset
- random/std::binomial_distribution::p
- random/std::binomial_distribution::t
- random/std::binomial_distribution::param
- random/std::binomial_distribution::min
- random/std::binomial_distribution::max
- random/std::binomial_distribution::operator()
- random/std::binomial_distribution::param_type
- random/std::binomial_distribution::param_type::p
- random/std::binomial_distribution::param_type::t
- random/std::binomial_distribution::param_type::operator==
- random/std::binomial_distribution::param_type::operator!=
helpviewer_keywords:
- std::binomial_distribution [C++]
- std::binomial_distribution [C++], reset
- std::binomial_distribution [C++], p
- std::binomial_distribution [C++], t
- std::binomial_distribution [C++], param
- std::binomial_distribution [C++], min
- std::binomial_distribution [C++], max
- std::binomial_distribution [C++], param_type
- std::binomial_distribution [C++], param_type
ms.assetid: b7c8a26a-da8c-45a5-a3a8-208f7a3609ce
ms.openlocfilehash: e3d2d02bc6781ed447d7583ce15a60e983251350
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688375"
---
# <a name="binomial_distribution-class"></a>binomial_distribution – třída

Generuje binomické rozdělení.

## <a name="syntax"></a>Syntaxe

```cpp
template<class IntType = int>
class binomial_distribution
   {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructors and reset functions
   explicit binomial_distribution(result_type t = 1, double p = 0.5);
   explicit binomial_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type t() const;
   double p() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*IntType* \
Celočíselný typ výsledku, výchozí hodnota je **int**. Možné typy najdete v tématu [\<random >](../standard-library/random.md).

*URNG* \
Jednotný modul generátoru náhodných čísel. Možné typy najdete v tématu [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje distribuci, která vytváří hodnoty celočíselného typu zadaného uživatelem, nebo typ **int** , pokud není k dispozici, distribuované podle funkce rozdělení diskrétní distribuce. Následující tabulka obsahuje odkazy na články týkající se jednotlivých členů.

||||
|-|-|-|
|[binomial_distribution](#binomial_distribution)|`binomial_distribution::t`|`binomial_distribution::param`|
|`binomial_distribution::operator()`|`binomial_distribution::p`|[param_type](#param_type)|

Členy vlastnosti `t()` a `p()` vrátí aktuálně uložené hodnoty distribučního parametru *t* a *p* .

Člen vlastnosti `param()` nastaví nebo vrátí `param_type` uložený balíček parametrů distribuce.

Členské funkce `min()` a `max()` vracejí nejmenší možný výsledek a největší možný výsledek.

Členská funkce `reset()` zahodí všechny hodnoty uložené v mezipaměti, takže výsledek dalšího volání `operator()` nezávisí na hodnotách získaných z modulu před voláním.

Členské funkce `operator()` vrátí další vygenerovanou hodnotu založenou na modulu URNG, buď z aktuálního balíčku parametrů, nebo pomocí zadaného balíčku parametrů.

Další informace o třídách distribuce a jejich členech naleznete v tématu [\<random >](../standard-library/random.md).

Podrobné informace o funkci rozdělení binomické distribuce, která je diskrétní, najdete v článku [binomické rozdělení](https://go.microsoft.com/fwlink/p/?linkid=398469)Wolfram MathWorld.

## <a name="example"></a>Příklad

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const int t, const double p, const int& s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::binomial_distribution<> distr(t, p);

    std::cout << std::endl;
    std::cout << "p == " << distr.p() << std::endl;
    std::cout << "t == " << distr.t() << std::endl;

    // generate the distribution as a histogram
    std::map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Histogram for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    int    t_dist = 1;
    double p_dist = 0.5;
    int    samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter an integer value for t distribution (where 0 <= t): ";
    std::cin >> t_dist;
    std::cout << "Enter a double value for p distribution (where 0.0 <= p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(t_dist, p_dist, samples);
}
```

První spuštění:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for t distribution (where 0 <= t): 22
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .25
Enter an integer value for a sample count: 100

p == 0.25
t == 22
Histogram for 100 samples:
    1 :
    2 ::
    3 :::::::::::::
    4 ::::::::::::::
    5 :::::::::::::::::::::::::
    6 ::::::::::::::::::
    7 :::::::::::::
    8 ::::::
    9 ::::::
    11 :
    12 :
```

Druhý běh:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for t distribution (where 0 <= t): 22
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .5
Enter an integer value for a sample count: 100

p == 0.5
t == 22
Histogram for 100 samples:
    6 :
    7 ::
    8 :::::::::
    9 ::::::::::
    10 ::::::::::::::::
    11 :::::::::::::::::::
    12 :::::::::::
    13 :::::::::::::
    14 :::::::::::::::
    15 ::
    16 ::
```

Třetí běh:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for t distribution (where 0 <= t): 22
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .75
Enter an integer value for a sample count: 100

p == 0.75
t == 22
Histogram for 100 samples:
    13 ::::
    14 :::::::::::
    15 :::::::::::::::
    16 :::::::::::::::::::::
    17 ::::::::::::::
    18 :::::::::::::::::
    19 :::::::::::
    20 ::::::
    21 :
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<random >

**Obor názvů:** std

## <a name="binomial_distribution"></a>binomial_distribution::binomial_distribution

Sestaví rozdělení.

```cpp
explicit binomial_distribution(result_type t = 1, double p = 0.5);
explicit binomial_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*t* \
Parametr distribuce `t`.

*p* \
Parametr distribuce `p`.

*parametr* \
Struktura `param_type` používaná k sestavení distribuce.

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `0 ≤ t` a `0.0 ≤ p ≤ 1.0`

První konstruktor vytvoří objekt, jehož uložená hodnota *p* obsahuje hodnotu *p* a jehož uložená hodnota *t* obsahuje hodnotu *t*.

Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry pro existující distribuci voláním členské funkce `param()`.

## <a name="param_type"></a>binomial_distribution::p aram_type

Ukládá všechny parametry distribuce.

```cpp
struct param_type {
   typedef binomial_distribution<result_type> distribution_type;
   param_type(result_type t = 1, double p = 0.5);
   result_type t() const;
   double p() const;
   .....
   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*t* \
Parametr distribuce `t`.

*p* \
Parametr distribuce `p`.

*pravé* \
Objekt `param_type`, který se má porovnat.

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `0 ≤ t` a `0.0 ≤ p ≤ 1.0`

Tato struktura může být předána konstruktoru třídy distribuce při vytváření instance, do `param()` členské funkce pro nastavení uložených parametrů stávající distribuce a `operator()` k použití namísto uložených parametrů.

## <a name="see-also"></a>Viz také:

[\<random >](../standard-library/random.md)
