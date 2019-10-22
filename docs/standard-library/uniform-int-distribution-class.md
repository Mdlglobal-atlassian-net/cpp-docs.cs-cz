---
title: uniform_int_distribution – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::uniform_int_distribution
- random/std::uniform_int_distribution::reset
- random/std::uniform_int_distribution::a
- random/std::uniform_int_distribution::b
- random/std::uniform_int_distribution::param
- random/std::uniform_int_distribution::min
- random/std::uniform_int_distribution::max
- random/std::uniform_int_distribution::operator()
- random/std::uniform_int_distribution::param_type
- random/std::uniform_int_distribution::param_type::a
- random/std::uniform_int_distribution::param_type::b
- random/std::uniform_int_distribution::param_type::operator==
- random/std::uniform_int_distribution::param_type::operator!=
helpviewer_keywords:
- std::uniform_int_distribution [C++]
- std::uniform_int_distribution [C++], reset
- std::uniform_int_distribution [C++], a
- std::uniform_int_distribution [C++], b
- std::uniform_int_distribution [C++], param
- std::uniform_int_distribution [C++], min
- std::uniform_int_distribution [C++], max
- std::uniform_int_distribution [C++], param_type
- std::uniform_int_distribution [C++], param_type
ms.assetid: a1867dcd-3bd9-4787-afe3-4b62692c1d04
ms.openlocfilehash: 7e24c320e909bb2d0471acdd275f89c43d3e44de
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684517"
---
# <a name="uniform_int_distribution-class"></a>uniform_int_distribution – třída

Vygeneruje jednotný (každá hodnota je stejně pravděpodobná) rozdělení celého čísla v rámci výstupní oblasti, která je zahrnutá (včetně).

## <a name="syntax"></a>Syntaxe

```cpp
template<class IntType = int>
   class uniform_int_distribution {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructors and reset functions
   explicit uniform_int_distribution(
      result_type a = 0, result_type b = numeric_limits<result_type>::max());
   explicit uniform_int_distribution(const param_type& parm);
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

*IntType* \
Celočíselný typ výsledku, výchozí hodnota je **int**. Možné typy najdete v tématu [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje kompletní distribuci, která vytváří hodnoty celočíselného typu zadaného uživatelem s distribucí, takže každá hodnota je stejně pravděpodobná. Následující tabulka obsahuje odkazy na články týkající se jednotlivých členů.

||||
|-|-|-|
|[uniform_int_distribution](#uniform_int_distribution)|`uniform_int_distribution::a`|`uniform_int_distribution::param`|
|`uniform_int_distribution::operator()`|`uniform_int_distribution::b`|[param_type](#param_type)|

Člen vlastnosti `a()` vrátí aktuálně uloženou minimální hranici distribuce, zatímco `b()` vrátí aktuálně uloženou hodnotu Bound. Pro tuto třídu distribuce jsou tyto minimální a maximální hodnoty stejné jako ty, které vrací funkce Common Property `min()` a `max()`.

Člen vlastnosti `param()` nastaví nebo vrátí `param_type` uložený balíček parametrů distribuce.

Členské funkce `min()` a `max()` vracejí nejmenší možný výsledek a největší možný výsledek.

Členská funkce `reset()` zahodí všechny hodnoty uložené v mezipaměti, takže výsledek dalšího volání `operator()` nezávisí na hodnotách získaných z modulu před voláním.

Členské funkce `operator()` vrátí další vygenerovanou hodnotu založenou na modulu URNG, buď z aktuálního balíčku parametrů, nebo pomocí zadaného balíčku parametrů.

Další informace o třídách distribuce a jejich členech naleznete v tématu [\<random >](../standard-library/random.md).

## <a name="example"></a>Příklad

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const int a, const int b, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::uniform_int_distribution<> distr(a, b);

    std::cout << "lower bound == " << distr.a() << std::endl;
    std::cout << "upper bound == " << distr.b() << std::endl;

    // generate the distribution as a histogram
    std::map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    int a_dist = 1;
    int b_dist = 10;

    int samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter an integer value for the lower bound of the distribution: ";
    std::cin >> a_dist;
    std::cout << "Enter an integer value for the upper bound of the distribution: ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the lower bound of the distribution: 0
Enter an integer value for the upper bound of the distribution: 12
Enter an integer value for the sample count: 200
lower bound == 0
upper bound == 12
Distribution for 200 samples:
    0 :::::::::::::::
    1 :::::::::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::
    4 :::::::
    5 :::::::::::::::::::::
    6 :::::::::::::
    7 ::::::::::
    8 :::::::::::::::
    9 :::::::::::::
   10 ::::::::::::::::::::::
   11 :::::::::::::
   12 :::::::::::::::::
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<random >

**Obor názvů:** std

## <a name="uniform_int_distribution"></a>uniform_int_distribution::uniform_int_distribution

Sestaví rozdělení.

```cpp
explicit uniform_int_distribution(
   result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
explicit uniform_int_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*\*
Dolní mez pro náhodné hodnoty, včetně.

*b* \
Horní mez pro náhodné hodnoty, včetně.

*parametr* \
Struktura `param_type` používaná k sestavení distribuce.

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `a ≤ b`

První konstruktor vytvoří *objekt,* *jehož uložená hodnota obsahuje hodnotu a* a jejíž hodnota uložená *b* obsahuje hodnotu *b*.

Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry pro existující distribuci voláním členské funkce `param()`.

## <a name="param_type"></a>uniform_int_distribution::p aram_type

Ukládá parametry distribuce.

```cpp
struct param_type {
   typedef uniform_int_distribution<result_type> distribution_type;
   param_type(
      result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*\*
Dolní mez pro náhodné hodnoty, včetně.

*b* \
Horní mez pro náhodné hodnoty, včetně.

*pravé* \
Objekt `param_type`, který se má porovnat.

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `a ≤ b`

Tato struktura může být předána konstruktoru třídy distribuce při vytváření instance, do `param()` členské funkce pro nastavení uložených parametrů stávající distribuce a `operator()` k použití namísto uložených parametrů.

## <a name="see-also"></a>Viz také:

[\<random >](../standard-library/random.md)
