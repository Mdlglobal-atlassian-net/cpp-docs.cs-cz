---
title: negative_binomial_distribution – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::negative_binomial_distribution
- random/std::negative_binomial_distribution::reset
- random/std::negative_binomial_distribution::k
- random/std::negative_binomial_distribution::p
- random/std::negative_binomial_distribution::param
- random/std::negative_binomial_distribution::min
- random/std::negative_binomial_distribution::max
- random/std::negative_binomial_distribution::operator()
- random/std::negative_binomial_distribution::param_type
- random/std::negative_binomial_distribution::param_type::k
- random/std::negative_binomial_distribution::param_type::p
- random/std::negative_binomial_distribution::param_type::operator==
- random/std::negative_binomial_distribution::param_type::operator!=
helpviewer_keywords:
- std::negative_binomial_distribution [C++]
- std::negative_binomial_distribution [C++], reset
- std::negative_binomial_distribution [C++], k
- std::negative_binomial_distribution [C++], p
- std::negative_binomial_distribution [C++], param
- std::negative_binomial_distribution [C++], min
- std::negative_binomial_distribution [C++], max
- std::negative_binomial_distribution [C++], param_type
- std::negative_binomial_distribution [C++], param_type
ms.assetid: 7f5f0967-7fdd-4578-99d4-88f292b4fe9c
ms.openlocfilehash: 944081516a353b99c3de55a557e801e018a23508
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543868"
---
# <a name="negativebinomialdistribution-class"></a>negative_binomial_distribution – třída

Generuje negativní binomické rozdělení.

## <a name="syntax"></a>Syntaxe

```
template<class IntType = int>
class negative_binomial_distribution
{
public:
    // types
    typedef IntType result_type;
    struct param_type;

    // constructor and reset functions
    explicit negative_binomial_distribution(result_type k = 1, double p = 0.5);
    explicit negative_binomial_distribution(const param_type& parm);
    void reset();

    // generating functions
    template `<`class URNG>
    result_type operator()(URNG& gen);
    template `<`class URNG>
    result_type operator()(URNG& gen, const param_type& parm);

    // property functions
    result_type k() const;
    double p() const;
    param_type param() const;
    void param(const param_type& parm);
    result_type min() const;
    result_type max() const;
};
```

### <a name="parameters"></a>Parametry

*IntType*<br/>
Typ výsledku celého čísla, výchozí hodnota je **int**. Možné typy, najdete v části [ \<náhodné >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Třída šablony popisuje distribuci, která vytváří hodnoty uživatelem zadaného celočíselný typ nebo typ **int** Pokud se žádný nezadá, rozděleny podle funkce diskrétní pravděpodobnost negativní binomické rozdělení. Následující tabulka odkazuje na články týkající se jednotlivých členů.

||||
|-|-|-|
|[negative_binomial_distribution –](#negative_binomial_distribution)|`negative_binomial_distribution::k`|`negative_binomial_distribution::param`|
|`negative_binomial_distribution::operator()`|`negative_binomial_distribution::p`|[param_type](#param_type)|

Členy vlastnosti `k()` a `p()` vrátit aktuálně uložené distribuci hodnot parametrů *k* a *p* v uvedeném pořadí.

Vlastnost člena `param()` Nastaví nebo vrátí `param_type` uložené distribuční balíček parametrů.

`min()` a `max()` členské funkce vrátí nejmenší možné výsledek a největší výsledek je to možné, v uvedeném pořadí.

`reset()` Členská funkce odstraní všechny hodnoty uložené v mezipaměti tak, aby výsledek dalšího volání do `operator()` nezávisí na žádné hodnoty získané z modulu před voláním.

`operator()` Členské funkce vrátí další vygenerovanou hodnotu založená na modulu URNG z aktuálního balíčku parametrů nebo balíček zadaný parametr.

Další informace o distribuci třídy a jejich členy, naleznete v tématu [ \<náhodné >](../standard-library/random.md).

Podrobné informace o funkci diskrétní pravděpodobnost negativní binomické rozdělení, najdete v článku Wolfram MathWorld [negativní binomické rozdělení](http://go.microsoft.com/fwlink/p/?linkid=400516).

## <a name="example"></a>Příklad

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const int k, const double p, const int& s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::negative_binomial_distribution<> distr(k, p);

    std::cout << std::endl;
    std::cout << "k == " << distr.k() << std::endl;
    std::cout << "p == " << distr.p() << std::endl;

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
    int    k_dist = 1;
    double p_dist = 0.5;
    int    samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter an integer value for k distribution (where 0 < k): ";
    std::cin >> k_dist;
    std::cout << "Enter a double value for p distribution (where 0.0 < p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(k_dist, p_dist, samples);
}

```

Nejprve spusťte:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for k distribution (where 0 `<` k): 1
Enter a double value for p distribution (where 0.0 `<`p `<`= 1.0): .5
Enter an integer value for a sample count: 100

k == 1
p == 0.5
Histogram for 100 samples:
    0 :::::::::::::::::::::::::::::::::::::::::::
    1 ::::::::::::::::::::::::::::::::
    2 ::::::::::::
    3 :::::::
    4 ::::
    5 ::
```

Druhé spuštění:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for k distribution (where 0 `<` k): 100
Enter a double value for p distribution (where 0.0 `<` p <= 1.0): .667
Enter an integer value for a sample count: 100

k == 100
p == 0.667
Histogram for 100 samples:
    31 ::
    32 :
    33 ::
    34 :
    35 ::
    37 ::
    38 :
    39 :
    40 ::
    41 :::
    42 :::
    43 :::::
    44 :::::
    45 ::::
    46 ::::::
    47 ::::::::
    48 :::
    49 :::
    50 :::::::::
    51 :::::::
    52 ::
    53 :::
    54 :::::
    56 ::::
    58 :
    59 :::::
    60 ::
    61 :
    62 ::
    64 :
    69 ::::
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné >

**Namespace:** std

## <a name="negative_binomial_distribution"></a>  negative_binomial_distribution::negative_binomial_distribution

Vytvoří rozložení.

```cpp
explicit negative_binomial_distribution(result_type k = 1, double p = 0.5);
explicit negative_binomial_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*k*<br/>
`k` Parametru distribuce.

*p*<br/>
`p` Parametru distribuce.

*Parametr*<br/>
Struktura parametr použít k vytvoření distribuce.

### <a name="remarks"></a>Poznámky

**Předpoklad:** `0.0 < k` a `0.0 < p ≤ 1.0`

První konstruktor vytvoří objekt, jehož uložené `p` hodnota obsahuje hodnotu *p* a jehož uložená `k` hodnota obsahuje hodnotu *k*.

Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuční voláním `param()` členskou funkci.

## <a name="param_type"></a>  negative_binomial_distribution::param_type

Ukládá parametry distribuce.

param_type – struktura {negative_binomial_distribution – definice typedef`<`result_type > distribution_type; param_type – (result_type tisíc = 1, dvakrát p = 0,5); result_type k() const; dvakrát p() const;

   BOOL – operátor == (const param_type – & rava) const; BOOL – operátor! = (const param_type – & pravé) const; };

### <a name="parameters"></a>Parametry

*k*<br/>
`k` Parametru distribuce.

*p*<br/>
`p` Parametru distribuce.

*doprava*<br/>
`param_type` Strukturu použit k porovnání.

### <a name="remarks"></a>Poznámky

**Předpoklad:** `0.0 < k` a `0.0 < p ≤ 1.0`

Tato struktura může být předán konstruktoru třídy distribuce při vytváření instance, do `param()` členskou funkci pro nastavení uložené parametry existující distribuční a k `operator()` použije místo uložené parametry.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
