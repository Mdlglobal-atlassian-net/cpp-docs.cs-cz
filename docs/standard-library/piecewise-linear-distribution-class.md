---
title: piecewise_linear_distribution – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::piecewise_linear_distribution
- random/std::piecewise_linear_distribution::reset
- random/std::piecewise_linear_distribution::intervals
- random/std::piecewise_linear_distribution::densities
- random/std::piecewise_linear_distribution::param
- random/std::piecewise_linear_distribution::min
- random/std::piecewise_linear_distribution::max
- random/std::piecewise_linear_distribution::operator()
- random/std::piecewise_linear_distribution::param_type
- random/std::piecewise_linear_distribution::param_type::intervals
- random/std::piecewise_linear_distribution::param_type::densities
- random/std::piecewise_linear_distribution::param_type::operator==
- random/std::piecewise_linear_distribution::param_type::operator!=
helpviewer_keywords:
- std::piecewise_linear_distribution [C++]
- std::piecewise_linear_distribution [C++], reset
- std::piecewise_linear_distribution [C++], intervals
- std::piecewise_linear_distribution [C++], densities
- std::piecewise_linear_distribution [C++], param
- std::piecewise_linear_distribution [C++], min
- std::piecewise_linear_distribution [C++], max
- std::piecewise_linear_distribution [C++], param_type
- std::piecewise_linear_distribution [C++], param_type
ms.assetid: cd141152-7163-4754-8f98-c6d6500005e0
ms.openlocfilehash: 9221daa002f19c3f73e65a49efb8da9c6f96b258
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455228"
---
# <a name="piecewiselineardistribution-class"></a>piecewise_linear_distribution – třída

Generuje konstantní lineární distribuci, která má různé intervaly s různou šířkou, lineární proměnlivou pravděpodobnost v každém intervalu.

## <a name="syntax"></a>Syntaxe

```cpp
template<class RealType = double>
class piecewise_linear_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   piecewise_linear_distribution();
   template <class InputIteratorI, class InputIteratorW>
   piecewise_linear_distribution(
      InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);
   template <class UnaryOperation>
   piecewise_linear_distribution(
      initializer_list<result_type> intervals, UnaryOperation weightfunc);
   template <class UnaryOperation>
   piecewise_linear_distribution(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   explicit piecewise_linear_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<result_type> intervals() const;
   vector<result_type> densities() const;
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

Tato distribuce vzorkování má různé intervaly s různou šířkou, lineární proměnlivou pravděpodobnost v každém intervalu. Informace o dalších distribucích vzorkování najdete v tématu [piecewise_linear_distribution](../standard-library/piecewise-constant-distribution-class.md) a [discrete_distribution](../standard-library/discrete-distribution-class.md).

Následující tabulka obsahuje odkazy na články týkající se jednotlivých členů:

||||
|-|-|-|
|[piecewise_linear_distribution](#piecewise_linear_distribution)|`piecewise_linear_distribution::intervals`|`piecewise_linear_distribution::param`|
|`piecewise_linear_distribution::operator()`|`piecewise_linear_distribution::densities`|[param_type](#param_type)|

Funkce `intervals()` Property`vector<result_type>` vrátí sadu se sadou uložených intervalů distribuce.

Funkce `densities()` Property`vector<result_type>` vrátí s uloženou hustotou pro každý interval sady, který je vypočítán podle vah uvedených v parametrech konstruktoru.

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

using namespace std;

void test(const int s) {

    // uncomment to use a non-deterministic generator
    // random_device rd;
    // mt19937 gen(rd());
    mt19937 gen(1701);

    // Three intervals, non-uniform: 0 to 1, 1 to 6, and 6 to 15
    vector<double> intervals{ 0, 1, 6, 15 };
    // weights determine the densities used by the distribution
    vector<double> weights{ 1, 5, 5, 10 };

    piecewise_linear_distribution<double> distr(intervals.begin(), intervals.end(), weights.begin());

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "intervals (index: interval):" << endl;
    vector<double> i = distr.intervals();
    int counter = 0;
    for (const auto& n : i) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;
    cout << "densities (index: density):" << endl;
    vector<double> d = distr.densities();
    counter = 0;
    for (const auto& n : d) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;

    // generate the distribution as a histogram
    map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << s << " samples:" << endl;
    for (const auto& elem : histogram) {
        cout << setw(5) << elem.first << '-' << elem.first + 1 << ' ' << string(elem.second, ':') << endl;
    }
    cout << endl;
}

int main()
{
    int samples = 100;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the sample count: 100
min() == 0
max() == 15
intervals (index: interval):
          0:   0.0000000000
          1:   1.0000000000
          2:   6.0000000000
          3:  15.0000000000
densities (index: density):
          0:   0.0645161290
          1:   0.3225806452
          2:   0.3225806452
          3:   0.6451612903
Distribution for 100 samples:
    0-1 :::::::::::::::::::::
    1-2 ::::::
    2-3 :::
    3-4 :::::::
    4-5 ::::::
    5-6 ::::::
    6-7 :::::
    7-8 ::::::::::
    8-9 ::::::::::
    9-10 ::::::
   10-11 ::::
   11-12 :::
   12-13 :::
   13-14 :::::
   14-15 :::::
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<náhodné >

**Obor názvů:** std

## <a name="piecewise_linear_distribution"></a>piecewise_linear_distribution::p iecewise_linear_distribution

Sestaví rozdělení.

```cpp
// default constructor
piecewise_linear_distribution();

// constructs using a range of intervals, [firstI, lastI), with
// matching weights starting at firstW
template <class InputIteratorI, class InputIteratorW>
piecewise_linear_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);

// constructs using an initializer list for range of intervals,
// with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_linear_distribution(initializer_list<RealType>
intervals, UnaryOperation weightfunc);

// constructs using an initializer list for range of count intervals,
// distributed uniformly over [xmin,xmax] with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_linear_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);

// constructs from an existing param_type structure
explicit piecewise_linear_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor prvního prvku v rozsahu distribuce.

*Poslední*\
Vstupní iterátor posledního prvku v rozsahu distribuce.

*firstW*\
Vstupní iterátor prvního prvku v rozsahu vah.

*období*\
[Initializer_list](../cpp/initializers.md) s intervaly distribuce.

*výpočtu*\
Počet prvků v rozsahu distribuce.

*xmin*\
Nejnižší hodnota v rozsahu distribuce.

*xmax*\
Nejvyšší hodnota v rozsahu distribuce. Musí být větší než *XMin*.

*weightfunc*\
Objekt představující funkci pravděpodobnosti pro rozdělení. Parametr i návratová hodnota musí být převoditelné na **typ Double**.

*parametr*\
Struktura parametrů používaná k sestavení distribuce.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor nastaví uložené parametry tak, aby byl jeden interval, 0 až 1, s hustotou pravděpodobnosti 1.

Konstruktor rozsahu iterátoru

```cpp
template <class InputIteratorI, class InputIteratorW>
piecewise_linear_distribution(
    InputIteratorI firstI,
    InputIteratorI lastI,
    InputIteratorW firstW);
```

sestaví objekt distribuce s itnervals z iterátorů přes sekvenci [ `firstI`, `lastI`) a stejnou sekvenci váhy začínající na *firstW*.

Konstruktor seznamu inicializátorů

```cpp
template <class UnaryOperation>
piecewise_linear_distribution(
    initializer_list<result_type> intervals,
    UnaryOperation weightfunc);
```

Vytvoří distribuční objekt s intervaly ze seznamu inicializačních *intervalů* a vah vygenerovaných funkcí *weightfunc*.

Konstruktor definovaný jako

```cpp
template <class UnaryOperation>
piecewise_linear_distribution(
    size_t count,
    result_type xmin,
    result_type xmax,
    UnaryOperation weightfunc);
```

sestaví distribuční objekt s intervaly *počtu* distribuovaně rovnoměrně přes `xmin,xmax`[], přiřazování každé váhy intervalu podle funkce *weightfunc*a *weightfunc* musí přijmout jeden parametr a vracet hodnota, kterou lze převést na `double`hodnotu. **Předběžná podmínka:** `xmin < xmax`.

Konstruktor definovaný jako

```cpp
explicit piecewise_linear_distribution(const param_type& parm);
```

Vytvoří objekt distribuce s použitím *parametr* jako struktury uložených parametrů.

## <a name="param_type"></a>piecewise_linear_distribution::p aram_type

Ukládá všechny parametry distribuce.

```cpp
struct param_type {
   typedef piecewise_linear_distribution<result_type> distribution_type;
   param_type();
   template <class IterI, class IterW>
   param_type(
      IterI firstI, IterI lastI, IterW firstW);
   template <class UnaryOperation>
   param_type(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   std::vector<result_type> densities() const;
   std::vector<result_type> intervals() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

Viz parametry konstruktoru pro [piecewise_linear_distribution](#piecewise_linear_distribution).

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `xmin < xmax`

Tuto strukturu lze předat konstruktoru třídy distribuce při vytváření instance, `param()` členské funkci pro nastavení uložených parametrů stávající distribuce a k `operator()` použití namísto uložených parametrů.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)
