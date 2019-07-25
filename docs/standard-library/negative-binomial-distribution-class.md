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
ms.openlocfilehash: 11e705629675903803f7230d540417846417cc77
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456963"
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

*IntType*\
Celočíselný typ výsledku, výchozí hodnota je **int**. Možné typy naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Třída šablony popisuje distribuci, která vytváří hodnoty celočíselného typu zadaného uživatelem, nebo typ **int** , pokud není k dispozici, distribuované podle funkce rozdělení negativní binomické distribuce. Následující tabulka obsahuje odkazy na články týkající se jednotlivých členů.

||||
|-|-|-|
|[negative_binomial_distribution](#negative_binomial_distribution)|`negative_binomial_distribution::k`|`negative_binomial_distribution::param`|
|`negative_binomial_distribution::operator()`|`negative_binomial_distribution::p`|[param_type](#param_type)|

Členy `k()` vlastnosti a `p()` vrátí aktuálně uložené hodnoty distribučních parametrů *k* a *p* v uvedeném pořadí.

Člen `param()` vlastnosti nastaví nebo `param_type` vrátí uložený balíček parametrů distribuce.

Členské funkce `max()` a vracejí nejmenší možný výsledek a největší možný výsledek, v uvedeném pořadí. `min()`

Členská funkce zahodí všechny hodnoty uložené v mezipaměti, takže výsledek dalšího `operator()` volání není závislý na všech hodnotách získaných z modulu před voláním. `reset()`

`operator()` Členské funkce vrátí další vygenerovanou hodnotu založenou na modulu URNG, buď z aktuálního balíčku parametrů, nebo pomocí zadaného balíčku parametrů.

Další informace o třídách distribuce a jejich členech naleznete v tématu [ \<Random >](../standard-library/random.md).

Podrobné informace o funkci rozdělení negativní binomické distribuce, která je samostatnou pravděpodobností, najdete v článku Wolfram MathWorld [negativně binomické rozdělení](https://go.microsoft.com/fwlink/p/?linkid=400516).

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

První spuštění:

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

Druhý běh:

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

**Hlavička:** \<náhodné >

**Obor názvů:** std

## <a name="negative_binomial_distribution"></a>negative_binomial_distribution::negative_binomial_distribution

Sestaví rozdělení.

```cpp
explicit negative_binomial_distribution(result_type k = 1, double p = 0.5);
explicit negative_binomial_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*k*\
Parametr `k` distribuce.

*trub*\
Parametr `p` distribuce.

*parametr*\
Struktura parametrů používaná k sestavení distribuce.

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `0.0 < k` a`0.0 < p ≤ 1.0`

První konstruktor vytvoří objekt `p` , jehož uložená hodnota obsahuje hodnotu *p* a jejíž uložená `k` hodnota obsahuje hodnotu *k*.

Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuce voláním `param()` členské funkce.

## <a name="param_type"></a>  negative_binomial_distribution::param_type

Ukládá parametry distribuce.

struct param_type {typedef negative_binomial_distribution`<`result_type > distribution_type; param_type (result_type k = 1, Double p = 0,5); result_type k () const; Double p () const;

   bool – operátor = = (const param_type & Right) const; bool – operátor! = (const param_type & Right) const; };

### <a name="parameters"></a>Parametry

*k*\
Parametr `k` distribuce.

*trub*\
Parametr `p` distribuce.

*Kliknutím*\
`param_type` Struktura použitá k porovnání

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `0.0 < k` a`0.0 < p ≤ 1.0`

Tuto strukturu lze předat konstruktoru třídy distribuce při vytváření instance, `param()` členské funkci pro nastavení uložených parametrů stávající distribuce a k `operator()` použití namísto uložených parametrů.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)
