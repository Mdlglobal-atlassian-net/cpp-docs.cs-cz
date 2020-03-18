---
title: piecewise_constant_distribution – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::piecewise_constant_distribution
- random/std::piecewise_constant_distribution::reset
- random/std::piecewise_constant_distribution::intervals
- random/std::piecewise_constant_distribution::densities
- random/std::piecewise_constant_distribution::param
- random/std::piecewise_constant_distribution::min
- random/std::piecewise_constant_distribution::max
- random/std::piecewise_constant_distribution::operator()
- random/std::piecewise_constant_distribution::param_type
- random/std::piecewise_constant_distribution::param_type::intervals
- random/std::piecewise_constant_distribution::param_type::densities
- random/std::piecewise_constant_distribution::param_type::operator==
- random/std::piecewise_constant_distribution::param_type::operator!=
helpviewer_keywords:
- std::piecewise_constant_distribution [C++]
- std::piecewise_constant_distribution [C++], reset
- std::piecewise_constant_distribution [C++], intervals
- std::piecewise_constant_distribution [C++], densities
- std::piecewise_constant_distribution [C++], param
- std::piecewise_constant_distribution [C++], min
- std::piecewise_constant_distribution [C++], max
- std::piecewise_constant_distribution [C++], param_type
- std::piecewise_constant_distribution [C++], param_type
ms.assetid: 2c9a21fa-623e-4d63-b827-3f1556b6dedb
ms.openlocfilehash: db537e7cfab70c2ac4e235a752216b892882f8cf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446195"
---
# <a name="piecewise_constant_distribution-class"></a>piecewise_constant_distribution – třída

Generuje konstantní konstantní distribuci, která má v každém intervalu různé intervaly s různou šířkou s jednotnou pravděpodobností.

## <a name="syntax"></a>Syntaxe

```cpp
template<class RealType = double>
class piecewise_constant_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   piecewise_constant_distribution();
   template <class InputIteratorI, class InputIteratorW>
   piecewise_constant_distribution(
       InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);
   template <class UnaryOperation>
   piecewise_constant_distribution(
      initializer_list<result_type> intervals, UnaryOperation weightfunc);
   template <class UnaryOperation>
   piecewise_constant_distribution(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   explicit piecewise_constant_distribution(const param_type& parm);
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
Typ výsledku s plovoucí desetinnou čárkou, výchozí hodnota je **Double**. Možné typy naleznete v tématu [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato distribuce vzorkování má v každém intervalu různou šířku intervalu s jednotnou pravděpodobností. Informace o dalších distribucích vzorkování naleznete v tématu [Piecewise_linear_distribution Class](../standard-library/piecewise-linear-distribution-class.md) a [discrete_distribution](../standard-library/discrete-distribution-class.md).

Následující tabulka obsahuje odkazy na články týkající se jednotlivých členů:

||||
|-|-|-|
|[piecewise_constant_distribution](#piecewise_constant_distribution)|`piecewise_constant_distribution::intervals`|`piecewise_constant_distribution::param`|
|`piecewise_constant_distribution::operator()`|`piecewise_constant_distribution::densities`|[param_type](#param_type)|

Funkce Property `intervals()` vrátí `vector<result_type>` se sadou uložených intervalů distribuce.

Funkce Property `densities()` vrátí `vector<result_type>` s uloženými hustotami pro každý interval sady, který je vypočítán podle vah uvedených v parametrech konstruktoru.

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

using namespace std;

void test(const int s) {

    // uncomment to use a non-deterministic generator
    // random_device rd;
    // mt19937 gen(rd());
    mt19937 gen(1701);

    // Three intervals, non-uniform: 0 to 1, 1 to 6, and 6 to 15
    vector<double> intervals{ 0, 1, 6, 15 };
    // weights determine the densities used by the distribution
    vector<double> weights{ 1, 5, 10 };

    piecewise_constant_distribution<double> distr(intervals.begin(), intervals.end(), weights.begin());

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
        cout << setw(5) << elem.first << '-' << elem.first+1 << ' ' << string(elem.second, ':') << endl;
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
          0:   0.0625000000
          1:   0.0625000000
          2:   0.0694444444
Distribution for 100 samples:
    0-1 :::::::
    1-2 ::::::
    2-3 :::::
    3-4 ::::::
    4-5 :::::::
    5-6 ::::::
    6-7 :::
    7-8 ::::::::::
    8-9 ::::::
    9-10 ::::::::::::
    10-11 :::::
    11-12 ::::::
    12-13 :::::::::
    13-14 ::::
    14-15 ::::::::
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodný >

**Obor názvů:** std

## <a name="piecewise_constant_distribution"></a>piecewise_constant_distribution::p iecewise_constant_distribution

Sestaví rozdělení.

```cpp
// default constructor
piecewise_constant_distribution();

// constructs using a range of intervals, [firstI, lastI), with
// matching weights starting at firstW
template <class InputIteratorI, class InputIteratorW>
piecewise_constant_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);

// constructs using an initializer list for range of intervals,
// with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_constant_distribution(initializer_list<RealType>
intervals, UnaryOperation weightfunc);

// constructs using an initializer list for range of count intervals,
// distributed uniformly over [xmin,xmax] with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_constant_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);

// constructs from an existing param_type structure
explicit piecewise_constant_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor prvního prvku v rozsahu distribuce.

*poslední*\
Vstupní iterátor posledního prvku v rozsahu distribuce.

*firstW*\
Vstupní iterátor prvního prvku v rozsahu vah.

*intervaly*\
[Initializer_list](../cpp/initializers.md) s intervaly distribuce.

*počet*\
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
piecewise_constant_distribution(InputIteratorI firstI, InputIteratorI lastI,
    InputIteratorW firstW);
```

sestaví distribuční objekt s itnervals z iterátorů přes sekvenci [`firstI`, `lastI`) a v pořadí podle `firstW`má stejnou sekvenci váhy.

Konstruktor seznamu inicializátorů

```cpp
template <class UnaryOperation>
piecewise_constant_distribution(initializer_list<result_type>
intervals,
    UnaryOperation weightfunc);
```

Vytvoří distribuční objekt s intervaly ze seznamu inicializačních *intervalů* a vah vygenerovaných funkcí *weightfunc*.

Konstruktor definovaný jako

```cpp
template <class UnaryOperation>
piecewise_constant_distribution(size_t count, result_type xmin, result_type xmax,
    UnaryOperation weightfunc);
```

sestaví distribuční objekt s intervaly *počtu* distribuovaně rovnoměrně přes [`xmin,xmax`], přiřazování každé váhy intervalu podle funkce *weightfunc*a *weightfunc* musí přijmout jeden parametr a vracet návratovou hodnotu, obě jsou převoditelné na `double`. **Předběžná podmínka:** `xmin < xmax`

Konstruktor definovaný jako

```cpp
explicit piecewise_constant_distribution(const param_type& parm);
```

Vytvoří objekt distribuce s použitím *parametr* jako struktury uložených parametrů.

## <a name="param_type"></a>piecewise_constant_distribution::p aram_type

Ukládá všechny parametry distribuce.

```cpp
struct param_type {
   typedef piecewise_constant_distribution<result_type> distribution_type;
   param_type();
   template <class IterI, class IterW>
   param_type(IterI firstI, IterI lastI, IterW firstW);
   template <class UnaryOperation>
   param_type(size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   std::vector<result_type> densities() const;
   std::vector<result_type> intervals() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

Podívejte se na parametry konstruktoru pro [piecewise_constant_distribution](#piecewise_constant_distribution).

### <a name="remarks"></a>Poznámky

**Předběžná podmínka:** `xmin < xmax`

Tato struktura může být předána konstruktoru třídy distribuce při vytváření instance, do `param()` členské funkce pro nastavení uložených parametrů stávající distribuce a `operator()` k použití namísto uložených parametrů.

## <a name="see-also"></a>Viz také

[\<náhodný >](../standard-library/random.md)\
[piecewise_linear_distribution](../standard-library/piecewise-linear-distribution-class.md)
