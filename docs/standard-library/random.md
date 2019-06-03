---
title: '&lt;náhodné&gt;'
ms.date: 08/24/2017
f1_keywords:
- <random>
helpviewer_keywords:
- random header
ms.assetid: 60afc25c-b162-4811-97c1-1b65398d4c57
ms.openlocfilehash: 3fd6272ebcb58d48cc943541f32d1195c3fab498
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450802"
---
# <a name="ltrandomgt"></a>&lt;náhodné&gt;

Definuje zařízení pro generování náhodných čísel, umožňující vytvoření rovnoměrně distribuovaných náhodných čísel.

## <a name="syntax"></a>Syntaxe

```cpp
#include <random>
```

## <a name="summary"></a>Souhrn

A *generátor náhodných čísel* je objekt, který generuje sekvenci pseudonáhodných hodnot. Generátor, který vytváří hodnoty, které jsou rovnoměrně rozloženy v zadaném rozsahu *jednotné generátor náhodných číslo* (URNG). Třída šablony slouží jako URNG se označuje jako *modul* Pokud tato třída má určité společné vlastnosti, které jsou popsány dále v tomto článku. Může být URNG – a je obvykle – v kombinaci s *distribuce* předáním URNG jako argumentu k distribučnímu `operator()` k vytvoření hodnot, které jsou distribuovány způsobem, který je definován distribucí.

Tyto odkazy, přejít na hlavní části tohoto článku:

- [Příklady](#code)

- [Seznam podle kategorií](#listing)

- [Moduly a distribuce](#engdist)

- [Poznámky](#comments)

### <a name="quick-tips"></a>Rychlé tipy

Tady je několik užitečných tipů k vzít v úvahu při použití \<náhodné >:

- Pro většinu účelů vytvářejí URNGs nezpracovaná bitů, které musí být ve tvaru pomocí distribucí. (Významné výjimku tvoří [std::shuffle()](../standard-library/algorithm-functions.md#shuffle) vzhledem k tomu používá URNG přímo.)

- Jediné instance URNG nebo distribuce nelze bezpečně volat souběžně spustili URNG nebo distribuce je změna operace. Další informace najdete v tématu [bezpečnost vlákna ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md).

- [Předdefinovaná funkce typedefs](#typedefs) z několika moduly jsou k dispozici; Toto je upřednostňovaný způsob, jak vytvořit URNG, pokud modul se používá.

- Nejužitečnější párování pro většinu aplikací je `mt19937` modul s `uniform_int_distribution`, jak je znázorněno [příklad kódu](#code) dále v tomto článku.

Existuje mnoho možností můžete vybírat z v \<náhodné > záhlaví a některý z nich je vhodnější než zastaralé funkce C Runtime `rand()`. Informace o čem je problém s `rand()` a jak \<náhodné > řeší tyto nedostatky, naleznete v tématu [toto video](https://go.microsoft.com/fwlink/p/?linkid=397615).

## <a name="code"></a> Příklady

Následující příklad kódu ukazuje, jak vygenerovat několik náhodných čísel v tomto případě pět z nich pomocí generátoru vytvořené pomocí Nedeterministický počáteční hodnoty.

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
                        // replace the call to rd() with a
                        // constant value to get repeatable
                        // results.

    for (int i = 0; i < 5; ++i) {
        cout << gen() << " "; // print the raw output of the generator.
    }
    cout << endl;
}
```

```Output
2430338871 3531691818 2723770500 3252414483 3632920437
```

Jedná se o vysoce kvalitní náhodná čísla a jiné pokaždé, když tento program běží, ale není nutně užitečné rozsahu. K řízení rozsahu, použijte rovnoměrné rozdělení, jak je znázorněno v následujícím kódu:

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
    uniform_int_distribution<> dist(1,6); // distribute results between 1 and 6 inclusive.

    for (int i = 0; i < 5; ++i) {
        cout << dist(gen) << " "; // pass the generator to the distribution.
    }
    cout << endl;
}
```

```Output
5 1 6 1 2
```

Následující příklad kódu ukazuje realističtější sadu případy použití s rovnoměrně distribuovaných generátorů náhodných čísel přesouvání obsahu vektoru a pole.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <array>
#include <iostream>
#include <random>
#include <string>
#include <vector>
#include <functional> // ref()

using namespace std;

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

template <class URNG>
void test(URNG& urng) {

    // Uniform distribution used with a vector
    // Distribution is [-5, 5] inclusive
    uniform_int_distribution<int> dist(-5, 5);
    vector<int> v;

    for (int i = 0; i < 20; ++i) {
        v.push_back(dist(urng));
    }

    cout << "Randomized vector: ";
    print(v);

    // Shuffle an array
    // (Notice that shuffle() takes a URNG, not a distribution)
    array<string, 26> arr = { { "H", "He", "Li", "Be", "B", "C", "N", "O", "F",
        "Ne", "Na", "Mg", "Al", "Si", "P", "S", "Cl", "Ar", "K", "Ca", "Sc",
        "Ti", "V", "Cr", "Mn", "Fe" } };

    shuffle(arr.begin(), arr.end(), urng);

    cout << "Randomized array: ";
    print(arr);
    cout << "--" << endl;
}

int main()
{
    // First run: non-seedable, non-deterministic URNG random_device
    // Slower but crypto-secure and non-repeatable.
    random_device rd;
    cout << "Using random_device URNG:" << endl;
    test(rd);

    // Second run: simple integer seed, repeatable results
    cout << "Using constant-seed mersenne twister URNG:" << endl;
    mt19937 engine1(12345);
    test(engine1);

    // Third run: random_device as a seed, different each run
    // (Desirable for most purposes)
    cout << "Using non-deterministic-seed mersenne twister URNG:" << endl;
    mt19937 engine2(rd());
    test(engine2);

    // Fourth run: "warm-up" sequence as a seed, different each run
    // (Advanced uses, allows more than 32 bits of randomness)
    cout << "Using non-deterministic-seed \"warm-up\" sequence mersenne twister URNG:" << endl;
    array<unsigned int, mt19937::state_size> seed_data;
    generate_n(seed_data.begin(), seed_data.size(), ref(rd));
    seed_seq seq(begin(seed_data), end(seed_data));
    mt19937 engine3(seq);
    test(engine3);
}
```

```Output
Using random_device URNG:
Randomized vector: 5 -4 2 3 0 5 -2 0 4 2 -1 2 -4 -3 1 4 4 1 2 -2
Randomized array: O Li V K C Ti N Mg Ne Sc Cl B Cr Mn Ca Al F P Na Be Si Ar Fe S He H
--
Using constant-seed mersenne twister URNG:
Randomized vector: 3 -1 -5 0 0 5 3 -4 -3 -4 1 -3 0 -3 -2 -4 5 1 -1 -1
Randomized array: Al O Ne Si Na Be C N Cr Mn H V F Sc Mg Fe K Ca S Ti B P Ar Cl Li He
--
Using non-deterministic-seed mersenne twister URNG:
Randomized vector: 5 -4 0 2 1 -2 4 4 -4 0 0 4 -5 4 -5 -1 -3 0 0 3
Randomized array: Si Fe Al Ar Na P B Sc H F Mg Li C Ti He N Mn Be O Ca Cr V K Ne Cl S
--
Using non-deterministic-seed "warm-up" sequence mersenne twister URNG:
Randomized vector: -1 3 -2 4 1 3 0 -5 5 -5 0 0 5 0 -3 3 -4 2 5 0
Randomized array: Si C Sc H Na O S Cr K Li Al Ti Cl B Mn He Fe Ne Be Ar V P Ca N Mg F
--
```

Tento kód ukazuje dva různé randomizations – náhodně vektor celých čísel a náhodné pole indexovaná data – pomocí šablony funkce test. První volání funkce test používá zabezpečení kryptografických, Nedeterministický, ne seedable, – a opakovatelné URNG `random_device`. Druhý testovací běh používá `mersenne_twister_engine` jako URNG, s deterministickou konstantní počáteční 32-bit, což znamená, že jsou opakovatelné výsledky. Třetí testovací běh rychlosti `mersenne_twister_engine` s 32-bit Nedeterministický výsledek z `random_device`. Čtvrtý testovacího běhu rozbalí na tomto pomocí [počáteční hodnoty pořadí](../standard-library/seed-seq-class.md) vyplněny `random_device` výsledky, které účinně poskytuje více než 32-bit Nedeterministický náhodnost (ale stále není crypto-secure). Další informace přečtěte si o.

## <a name="listing"></a> Seznam podle kategorií

###  <a name="urngs"></a> Jednotné generátory náhodných čísel

URNGs jsou často popisuje jako tyto vlastnosti:

1. **Délka období**: Kolik iterací trvá opakování pořadí generované čísel. Čím delší lepší.

2. **Výkon**: Jak rychle můžete generované čísel a kolik paměti používá. Nižší lepší.

3. **Kvalita**: Jak blízko true náhodných čísel je generovaný sekvenční. To se často nazývá "*náhodnost*".

V následujících částech jednotné generátorů náhodných čísel (URNGs) součástí \<náhodné > záhlaví.

####  <a name="rd"></a> Generátor Nedeterministický

|||
|-|-|
|[random_device – třída](../standard-library/random-device-class.md)|Generuje náhodné posloupnosti nedeterministické a kryptograficky zabezpečené pomocí externího zařízení. Obvykle používají pro modul. Nízký výkon, velmi vysokou kvalitu. Další informace najdete v tématu [poznámky](#comments).|

####  <a name="typedefs"></a> Definice TypeDef modulu s předdefinovanou parametry

Pro konkretizujete modulů a modul adaptéry. Další informace najdete v tématu [modulů a distribuce](#engdist).

- `default_random_engine` Výchozí web.

    ```cpp
    typedef mt19937 default_random_engine;
    ```

- `knuth_b` Knuth modul.

    ```cpp
    typedef shuffle_order_engine<minstd_rand0, 256> knuth_b;
    ```

- `minstd_rand0` 1988 minimální standard (Lewis, Goodman a modul Miller, 1969).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
    ```

- `minstd_rand` Aktualizovaný modul ochrany minimální standardní `minstd_rand0` (Park, Miller a Stockmeyer 1993).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
    ```

- `mt19937` 32bitová verze modulu twister Mersenne (Matsumoto a Nishimura 1998).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned int, 32, 624, 397,
        31, 0x9908b0df,
        11, 0xffffffff,
        7, 0x9d2c5680,
        15, 0xefc60000,
        18, 1812433253> mt19937;
    ```

- `mt19937_64` 64bitová verze modulu twister Mersenne (Matsumoto a Nishimura 2000).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned long long, 64, 312, 156,
        31, 0xb5026f5aa96619e9ULL,
        29, 0x5555555555555555ULL,
        17, 0x71d67fffeda60000ULL,
        37, 0xfff7eee000000000ULL,
        43, 6364136223846793005ULL> mt19937_64;
    ```

- `ranlux24` modul RANLUX 24-bit (Martin Lüscher a Fred James, 1994).

    ```cpp
    typedef discard_block_engine<ranlux24_base, 223, 23> ranlux24;
    ```

- `ranlux24_base` Použít jako základ pro `ranlux24`.

    ```cpp
    typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;
    ```

- `ranlux48` 48bitová RANLUX (Martin Lüscher a modul Fred James, 1994).

    ```cpp
    typedef discard_block_engine<ranlux48_base, 389, 11> ranlux48;
    ```

- `ranlux48_base` Použít jako základ pro `ranlux48`.

    ```cpp
    typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;
    ```

####  <a name="eng"></a> Modul šablon

Modul šablon se používají jako samostatné URNGs nebo jako základní moduly předán [modul adaptéry](#engadapt). Obvykle jsou vytvořeny pomocí [předdefinované definice typedef modulu](#typedefs) a předat [distribuce](#distributions). Další informace najdete v tématu [modulů a distribuce](#engdist) oddílu.

|||
|-|-|
|[linear_congruential_engine – třída](../standard-library/linear-congruential-engine-class.md)|Generuje náhodnou posloupnost pomocí lineárního algoritmu congruential. Většina zjednodušenou a nejnižší kvality.|
|[mersenne_twister_engine – třída](../standard-library/mersenne-twister-engine-class.md)|Vygeneruje náhodné pořadí pomocí algoritmu twister Mersenne. Nejsložitější, a je nejvyšší kvality, s výjimkou random_device – třída. Velmi rychlý výkon.|
|[subtract_with_carry_engine – třída](../standard-library/subtract-with-carry-engine-class.md)|Vygeneruje náhodné pořadí pomocí algoritmu subtract s carry. Zlepšení `linear_congruential_engine`, ale mnohem nižší kvality a výkonu než `mersenne_twister_engine`.|

####  <a name="engadapt"></a> Modul adaptér šablony

Modul adaptéry jsou šablony, které se přizpůsobí ostatních vyhledávacích strojů (základní). Obvykle jsou vytvořeny pomocí [předdefinované definice typedef modulu](#typedefs) a předat [distribuce](#distributions). Další informace najdete v tématu [modulů a distribuce](#engdist) oddílu.

|||
|-|-|
|[discard_block_engine – třída](../standard-library/discard-block-engine-class.md)|Generuje náhodné posloupnosti vypuštěním hodnoty vrácené základním modulem.|
|[independent_bits_engine – třída](../standard-library/independent-bits-engine-class.md)|Generuje náhodnou posloupnost pomocí zadaný počet bitů přebalením bitů z hodnot vrácených základním modulem.|
|[shuffle_order_engine – třída](../standard-library/shuffle-order-engine-class.md)|Generuje náhodné posloupnosti opětovným uspořádáním hodnot ze základního modulu.|

[[Modul šablon](#eng)]

###  <a name="distributions"></a> Náhodná čísla distribuce

V následujících částech distribuce podle \<náhodné > záhlaví. Distribuce jsou mechanismus následného zpracování, obvykle pomocí URNG výstup jako vstup a výstup distribuci funkcí definovaných statistické hustoty pravděpodobnosti. Další informace najdete v tématu [modulů a distribuce](#engdist) oddílu.

#### <a name="uniform-distributions"></a>Jednotné distribuce

|||
|-|-|
|[uniform_int_distribution – třída](../standard-library/uniform-int-distribution-class.md)|Vytvoří hodnotu rozdělení jednotného celého čísla v rozsahu v uzavřeném intervalu \[a, b] (včetně).|
|[uniform_real_distribution – třída](../standard-library/uniform-real-distribution-class.md)|Vytvoří jednotný reálném distribuce hodnoty (s plovoucí desetinnou čárkou) napříč rozsahem v částečně otevřený intervalu [a, b) (včetně exkluzivní).|
|[generate_canonical](../standard-library/random-functions.md#generate_canonical)|Vytvoří rovnoměrnou distribuci přenosu (plovoucí desetinná čárka) reálném hodnoty daného přesnosti napříč [0, 1) (včetně exkluzivní).|

[[Náhodných čísel distribuce](#distributions)]

#### <a name="bernoulli-distributions"></a>Bernoulliho rozdělení

|||
|-|-|
|[bernoulli_distribution – třída](../standard-library/bernoulli-distribution-class.md)|Generuje Bernoulliho rozdělení **bool** hodnoty.|
|[binomial_distribution – třída](../standard-library/binomial-distribution-class.md)|Generuje binomické rozdělení celočíselných hodnot.|
|[geometric_distribution – třída](../standard-library/geometric-distribution-class.md)|Generuje geometrické rozdělení celočíselných hodnot.|
|[negative_binomial_distribution – třída](../standard-library/negative-binomial-distribution-class.md)|Generuje negativní binomické rozdělení celočíselných hodnot.|

[[Náhodných čísel distribuce](#distributions)]

#### <a name="normal-distributions"></a>Normální distribuce

|||
|-|-|
|[cauchy_distribution – třída](../standard-library/cauchy-distribution-class.md)|Generuje Cauchy rozdělení hodnot real (plovoucí desetinná čárka).|
|[chi_squared_distribution – třída](../standard-library/chi-squared-distribution-class.md)|Generuje rozdělení chí-kvadrát hodnot real (plovoucí desetinná čárka).|
|[fisher_f_distribution – třída](../standard-library/fisher-f-distribution-class.md)|Vytvoří F – distribuce (označované také jako jeho Snedecor F rozdělení nebo distribuce Fisher Snedecor) hodnot real (plovoucí desetinná čárka).|
|[lognormal_distribution – třída](../standard-library/lognormal-distribution-class.md)|Vytvoří protokol normální rozdělení hodnot real (plovoucí desetinná čárka).|
|[normal_distribution – třída](../standard-library/normal-distribution-class.md)|Vytvoří normální (Gaussovy) distribuce hodnot real (plovoucí desetinná čárka).|
|[student_t_distribution – třída](../standard-library/student-t-distribution-class.md)|Vytvoří Student získal *t*– distribuce hodnot real (plovoucí desetinná čárka).|

[[Náhodných čísel distribuce](#distributions)]

#### <a name="poisson-distributions"></a>Poissonovo rozdělení

|||
|-|-|
|[exponential_distribution – třída](../standard-library/exponential-distribution-class.md)|Generuje exponenciální rozdělení hodnot real (plovoucí desetinná čárka).|
|[extreme_value_distribution – třída](../standard-library/extreme-value-distribution-class.md)|Generuje rozdělení extrémní hodnoty hodnot real (plovoucí desetinná čárka).|
|[gamma_distribution – třída](../standard-library/gamma-distribution-class.md)|Vytvoří funkce gamma distribuci hodnot real (plovoucí desetinná čárka).|
|[poisson_distribution – třída](../standard-library/poisson-distribution-class.md)|Generuje Poissonovo rozdělení celočíselných hodnot.|
|[weibull_distribution – třída](../standard-library/weibull-distribution-class.md)|Generuje rozdělení Weibull hodnot real (plovoucí desetinná čárka).|

[[Náhodných čísel distribuce](#distributions)]

#### <a name="sampling-distributions"></a>Distribuce vzorkování

|||
|-|-|
|[discrete_distribution – třída](../standard-library/discrete-distribution-class.md)|Generuje rozdělení samostatného celého čísla.|
|[piecewise_constant_distribution – třída](../standard-library/piecewise-constant-distribution-class.md)|Vytvoří konstantní konstantní distribuce hodnot real (plovoucí desetinná čárka).|
|[piecewise_linear_distribution – třída](../standard-library/piecewise-linear-distribution-class.md)|Generuje konstantní lineární rozdělení hodnot real (plovoucí desetinná čárka).|

[[Náhodných čísel distribuce](#distributions)]

### <a name="utility-functions"></a>Pomocné funkce

Tato část obsahuje seznam funkce obecné nástroje poskytované v \<náhodné > záhlaví.

|||
|-|-|
|[seed_seq – třída](../standard-library/seed-seq-class.md)|Generuje posloupnost-tendenční utajená počáteční hodnoty. Umožňuje zabránit replikaci s různými variantami náhodných datových proudů. Užitečné, pokud mnoho URNGs instance se vytvářejí z modulů.|

### <a name="operators"></a>Operátory

Tato část obsahuje seznam operátorů součástí \<náhodné > záhlaví.

|||
|-|-|
|`operator==`|Ověřuje, zda URNG na levé straně operátoru roven modulu na pravé straně.|
|`operator!=`|Ověřuje, zda URNG na levé straně operátoru není roven modulu na pravé straně.|
|`operator<<`|Zapíše informace o stavu do datového proudu.|
|`operator>>`|Extrahuje informace o stavu z datového proudu.|

## <a name="engdist"></a> Moduly a distribuce

Přečtěte si informace o každé z těchto kategorií třídy šablony definovaný v následujících částech \<náhodné >. Oba z těchto kategorií šablonu třídy zpracují typ jako argument a názvy parametrů šablony sdílené použít k podrobnému popisu vlastnosti typu, které jsou povoleny jako skutečné typ argumentu, následujícím způsobem:

- `IntType` označuje **krátký**, **int**, **dlouhé**, **long long**, **unsigned short**,  **unsigned int**, **unsigned long**, nebo **unsigned long long**.

- `UIntType` označuje **unsigned short**, **unsigned int**, **unsigned long**, nebo **unsigned long long**.

- `RealType` označuje **float**, **double**, nebo **long double**.

### <a name="engines"></a>Moduly

[Modul šablon](#eng) a [modul adaptér šablony](#engadapt) jsou šablony, jejíž parametry přizpůsobit generátor vytvořili.

*Modul* třídy nebo šablony třídy, jejíž instance (generátory) fungovat jako zdroj náhodných čísel rovnoměrně rozloženy mezi minimální a maximální hodnotou. *Modul adaptér* zajišťuje posloupnost hodnot, které mají různé náhodnost vlastnosti podle hodnot trvá vytvářených náhodných čísel modul a použití algoritmu určitého druhu na tyto hodnoty.

Každý modul a adaptér stroj má následující členy:

- `typedef` `numeric-type` `result_type` je typ, který je vrácena generátorem `operator()`. `numeric-type` Je předán jako parametr šablony při vytváření instance.

- `result_type operator()` Vrátí hodnoty, které jsou rovnoměrně rozloženy mezi `min()` a `max()`.

- `result_type min()` Vrátí minimální hodnotu, která je vrácena generátorem `operator()`. Modul adaptéry pomocí základního modulu `min()` výsledek.

- `result_type max()` Vrátí maximální hodnotu, která je vrácena generátorem `operator()`. Když `result_type` je integrálový typ (celé číslo s hodnotou), `max()` je maximální hodnota, která může být vrácena (včetně); když `result_type` s plovoucí desetinnou čárkou (vracející reálném) typ, `max()` je nejmenší hodnotu větší než všechny hodnoty který může být vrácen (inkluzivní). Modul adaptéry pomocí základního modulu `max()` výsledek.

- `void seed(result_type s)` nasazení nasazuje generátor s počáteční hodnotou `s`. Pro moduly, podpis je `void seed(result_type s = default_seed)` pro podpora výchozích parametrů (modul adaptéry definovat zvláštní `void seed()`, najdete v následující podčásti).

- `template <class Seq> void seed(Seq& q)` nasazení s použitím nasazuje generátor kódu [seed_seq –](../standard-library/seed-seq-class.md)`Seq`.

- Explicitní konstruktor s argumentem `result_type x` , který vytváří generátor nasazený jako kdyby volala `seed(x)`.

- Explicitní konstruktor s argumentem `seed_seq& seq` , který vytváří generátor nasazený jako kdyby volala `seed(seq)`.

- `void discard(unsigned long long count)` efektivně volá `operator()` `count` časy a zahodí každou hodnotu.

**Modul adaptéry** kromě podpory těchto členů (`Engine` je první parametr šablony modul adaptér, označující typ základního modulu):

- Výchozí konstruktor se inicializovat generátor kódu jakoby z základního modulu výchozí konstruktor.

- Explicitní konstruktor s argumentem `const Engine& eng`. To je podpora konstrukci kopie pomocí základního modulu.

- Explicitní konstruktor s argumentem `Engine&& eng`. To je podpora konstrukci přesunu pomocí základního modulu.

- `void seed()` který inicializuje generátor základního modulu hodnotu nasazení výchozí.

- `const Engine& base()` Vlastnosti funkce, která vrátí základní modul, který byl použit k sestavení kompletních generátor kódu.

Každý stroj udržuje *stavu* určující posloupnost hodnot, které budou generovány následnými výzvami pro `operator()`. Stavy dvou generátorů vytvořena z motorů stejného typu lze porovnat pomocí `operator==` a `operator!=`. Pokud porovnání dvou stavů je shodné, jejich vygenerují stejné pořadí hodnot. Stav objektu lze uložit do datového proudu jako sekvenci hodnot bez znaménka 32-bit pomocí `operator<<` generátoru. Stav se nezmění uložením. Uložený stav lze načíst do vytvoření instance z modulu stejného typu pomocí generátoru `operator>>`.

### <a name="distributions"></a>Distribuce

A [náhodné číslo distribuce](#distributions) je třída nebo třída šablony, jejíž instance transformují datový proud rovnoměrně distribuovaných náhodných čísel získaných z modulu na datový proud náhodných čísel, která mají zvláštní distribuci. Každá distribuce má následující členy:

- `typedef` `numeric-type` `result_type` je typ, který je vrácený distribuce `operator()`. `numeric-type` Je předán jako parametr šablony při vytváření instance.

- `template <class URNG> result_type operator()(URNG& gen)` Vrátí hodnoty, které jsou rozděleny podle definice distribuce pomocí `gen` jako zdroje rovnoměrně distribuovaných náhodných hodnot a uloženého *parametry distribuce*.

- `template <class URNG> result_type operator()(URNG& gen, param_type p)` Vrátí hodnoty definice distribuce pomocí `gen` jako zdroje rovnoměrně distribuovaných náhodných hodnot a parametrů struktury `p`.

- `typedef` `unspecified-type` `param_type` balíček parametrů volitelně předána `operator()` a použijí se místo uložené parametry pro generování hodnoty vrácení.

- A `const param&` konstruktor inicializuje uložených parametrů z argumentu.

- `param_type param() const` Získá uložené parametry.

- `void param(const param_type&)` Nastaví uložených parametrů z argumentu.

- `result_type min()` Vrátí minimální hodnotu, která je vrácena distribuce `operator()`.

- `result_type max()` Vrátí maximální hodnotu, která je vrácena distribuce `operator()`. Když `result_type` je integrálový typ (celé číslo s hodnotou), `max()` je maximální hodnota, která může být vrácena (včetně); když `result_type` s plovoucí desetinnou čárkou (vracející reálném) typ, `max()` je nejmenší hodnotu větší než všechny hodnoty který může být vrácen (inkluzivní).

- `void reset()` zahodí všechny hodnoty uložené v mezipaměti tak, aby výsledek dalšího volání do `operator()` nezávisí na žádné hodnoty získané z modulu před voláním.

Struktura parametru je objekt, který uchovává všechny parametry potřebné pro rozdělení. Obsahuje:

- `typedef` `distribution-type` `distribution_type`, což je typ distribuce.

- Jeden nebo více konstruktorů, které přijímají stejný parametr, jsou vypsány jako zkuste konstruktorů distribuce.

- Stejné funkce přístupu k parametrům jako v distribuci.

- Operátory porovnání rovnosti a nerovnosti.

Další informace najdete v další části odkaz pod touto propojenou dříve v tomto článku.

## <a name="comments"></a> Poznámky

Existují dva velmi užitečné URNGs v sadě Visual Studio –`mt19937` a `random_device`– jak je znázorněno v této tabulce porovnání:

|URNG|Rychlé|Crypto-secure|Seedable|Deterministické|
|----------|-----------|---------------------|---------------|--------------------|
|`mt19937`|Ano|Ne|Ano|Ano<sup>*</sup>|
|`random_device`|Ne|Ano|Ne|Ne|

<sup>* Pokud dodají známé počáteční hodnoty.</sup>

I když standardu ISO C++ nevyžaduje `random_device` bude kryptograficky zabezpečené a v sadě Visual Studio je potřebná k dosažení kryptograficky zabezpečené. (Termín "kryptograficky zabezpečené" neznamená záruky, ale odkazuje na minimální úroveň entropie – a proto se úroveň předvídatelnost – poskytuje algoritmu danou náhodné. Další informace najdete v článku na wikipedii [kryptograficky zabezpečené Generátor pseudonáhodných čísel](https://go.microsoft.com/fwlink/p/?linkid=398017).) Vzhledem k tomu, že standardu ISO C++ nevyžaduje, aby to, jiné platformy může implementovat `random_device` jako jednoduchý pseudonáhodného generátoru čísel (není bezpečné kryptograficky) a může pouze vhodné jako zdroj počáteční hodnoty pro generátor jiný. Vyhledejte v dokumentaci pro tyto platformy při použití `random_device` v multiplatformním kódem.

Podle definice `random_device` výsledky nejsou reprodukovatelné a vedlejší efekt je, že může výrazně pomalejší než ostatní URNGs spustit. Většina aplikací, které nemusejí být kryptograficky zabezpečené použití `mt19937` nebo podobná motoru, i když možná budete chtít naplnit voláním `random_device`, jak je znázorněno [příklad kódu](#code).

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
