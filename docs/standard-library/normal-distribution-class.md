---
title: normal_distribution – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::normal_distribution
- random/std::normal_distribution::reset
- random/std::normal_distribution::mean
- random/std::normal_distribution::stddev
- random/std::normal_distribution::param
- random/std::normal_distribution::min
- random/std::normal_distribution::max
- random/std::normal_distribution::operator()
- random/std::normal_distribution::param_type
- random/std::normal_distribution::param_type::mean
- random/std::normal_distribution::param_type::stddev
- random/std::normal_distribution::param_type::operator==
- random/std::normal_distribution::param_type::operator!=
helpviewer_keywords:
- std::normal_distribution [C++]
- std::normal_distribution [C++], reset
- std::normal_distribution [C++], mean
- std::normal_distribution [C++], stddev
- std::normal_distribution [C++], param
- std::normal_distribution [C++], min
- std::normal_distribution [C++], max
- std::normal_distribution [C++], param_type
- std::normal_distribution [C++], param_type
ms.assetid: bf92cdbd-bc72-4d4a-b588-173d748f0d7d
ms.openlocfilehash: d0de31a20e06d9b8ff3789cc7ae1928c9a7b6b7d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223607"
---
# <a name="normaldistribution-class"></a>normal_distribution – třída

Generuje normální rozdělení.

## <a name="syntax"></a>Syntaxe

```cpp
template<class RealType = double>
class normal_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructors and reset functions
   explicit normal_distribution(result_type mean = 0.0, result_type stddev = 1.0);
   explicit normal_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type mean() const;
   result_type stddev() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*RealType*<br/>
Výchozí hodnota typu s plovoucí desetinnou čárkou výsledku **double**. Možné typy, najdete v části [ \<náhodné >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Třída šablony popisuje distribuci, která vytváří hodnoty uživatelem zadaného celočíselný typ nebo typ **double** Pokud se žádný nezadá, které jsou rozděleny podle normální rozdělení. Následující tabulka odkazuje na články týkající se jednotlivých členů.

||||
|-|-|-|
|[normal_distribution](#normal_distribution)|`normal_distribution::mean`|`normal_distribution::param`|
|`normal_distribution::operator()`|`normal_distribution::stddev`|[param_type](#param_type)|

Funkce vlastností `mean()` a `stddev()` návratové hodnoty pro parametry uložené distribuce *znamenat* a *stddev* v uvedeném pořadí.

Vlastnost člena `param()` Nastaví nebo vrátí `param_type` uložené distribuční balíček parametrů.

`min()` a `max()` členské funkce vrátí nejmenší možné výsledek a největší výsledek je to možné, v uvedeném pořadí.

`reset()` Členská funkce odstraní všechny hodnoty uložené v mezipaměti tak, aby výsledek dalšího volání do `operator()` nezávisí na žádné hodnoty získané z modulu před voláním.

`operator()` Členské funkce vrátí další vygenerovanou hodnotu založená na modulu URNG z aktuálního balíčku parametrů nebo balíček zadaný parametr.

Další informace o distribuci třídy a jejich členy, naleznete v tématu [ \<náhodné >](../standard-library/random.md).

Podrobné informace o normální rozdělení, najdete v článku Wolfram MathWorld [normální rozdělení](http://go.microsoft.com/fwlink/p/?linkid=400924).

## <a name="example"></a>Příklad

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const double m, const double s, const int samples) {

    // uncomment to use a non-deterministic seed
    //    random_device gen;
    //    mt19937 gen(rd());
    mt19937 gen(1701);

    normal_distribution<> distr(m, s);

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "m() == " << fixed << setw(11) << setprecision(10) << distr.mean() << endl;
    cout << "s() == " << fixed << setw(11) << setprecision(10) << distr.stddev() << endl;

    // generate the distribution as a histogram
    map<double, int> histogram;
    for (int i = 0; i < samples; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << samples << " samples:" << endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        cout << fixed << setw(11) << ++counter << ": "
            << setw(14) << setprecision(10) << elem.first << endl;
    }
    cout << endl;
}

int main()
{
    double m_dist = 1;
    double s_dist = 1;
    int samples = 10;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter a floating point value for the 'mean' distribution parameter: ";
    cin >> m_dist;
    cout << "Enter a floating point value for the 'stddev' distribution parameter (must be greater than zero): ";
    cin >> s_dist;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(m_dist, s_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'mean' distribution parameter: 0
Enter a floating point value for the 'stddev' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
m() == 0.0000000000
s() == 1.0000000000
Distribution for 10 samples:
    1: -0.8845823965
    2: -0.1995761116
    3: -0.1162665130
    4: -0.0685154932
    5: 0.0403741461
    6: 0.1591327792
    7: 1.0414389924
    8: 1.5876269426
    9: 1.6362637713
    10: 2.7821317338
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné >

**Namespace:** std

## <a name="normal_distribution"></a>  normal_distribution::normal_distribution

Vytvoří rozložení.

```cpp
explicit normal_distribution(result_type mean = 0.0, result_type stddev = 1.0);
explicit normal_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*střední hodnotu*<br/>
`mean` Parametru distribuce.

*stddev*<br/>
`stddev` Parametru distribuce.

*Parametr*<br/>
Struktura parametr použít k vytvoření distribuce.

### <a name="remarks"></a>Poznámky

**Předběžné podmínky:** `0.0 < stddev`

První konstruktor vytvoří objekt, jehož uložené `mean` hodnota obsahuje hodnotu *znamenat* a jehož uložené `stddev` hodnota obsahuje hodnotu *stddev*.

Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuční voláním `param()` členskou funkci.

## <a name="param_type"></a>  normal_distribution::param_type

Ukládá parametry distribuce.

```cpp
struct param_type {
   typedef normal_distribution<result_type> distribution_type;
   param_type(result_type mean = 0.0, result_type stddev = 1.0);
   result_type mean() const;
   result_type stddev() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*střední hodnotu*<br/>
`mean` Parametru distribuce.

*stddev*<br/>
`stddev` Parametru distribuce.

*doprava*<br/>
`param_type` Strukturu použit k porovnání.

### <a name="remarks"></a>Poznámky

**Předběžné podmínky:** `0.0 < stddev`

Tato struktura může být předán konstruktoru třídy distribuce při vytváření instance, do `param()` členskou funkci pro nastavení uložené parametry existující distribuční a k `operator()` použije místo uložené parametry.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
