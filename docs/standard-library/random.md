---
title: '&lt;Náhodné&gt;'
ms.date: 08/24/2017
f1_keywords:
- <random>
helpviewer_keywords:
- random header
ms.assetid: 60afc25c-b162-4811-97c1-1b65398d4c57
ms.openlocfilehash: 540daa5bafa28b1d56c55daf33f0b5f5461c8ed6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320236"
---
# <a name="ltrandomgt"></a>&lt;Náhodné&gt;

Definuje zařízení pro generování náhodných čísel, což umožňuje vytváření rovnoměrně distribuovaných náhodných čísel.

## <a name="requirements"></a>Požadavky

**Záhlaví** \<: náhodné>

**Obor názvů:** std

> [!NOTE]
> Knihovna \<náhodných> používá příkaz "#include <initializer_list>".

## <a name="summary"></a>Souhrn

*Generátor náhodných čísel* je objekt, který vytváří posloupnost pseudonáhodných hodnot. Generátor, který vytváří hodnoty, které jsou rovnoměrně distribuovány v zadaném rozsahu je *jednotný generátor náhodných čísel* (URNG). Šablona třídy určené k funkci URNG se označuje jako *modul,* pokud tato třída má určité společné vlastnosti, které jsou popsány dále v tomto článku. URNG může být – a obvykle je – v kombinaci s *rozdělením* předáním URNG jako argument distribuce `operator()` k vytvoření hodnoty, které jsou distribuovány způsobem, který je definován rozdělení.

Tyto odkazy přejít na hlavní části tohoto článku:

- [Příklady](#code)

- [Zařazení do kategorií](#listing)

- [Motory a rozvody](#engdist)

- [Poznámky](#comments)

### <a name="quick-tips"></a>Rychlé tipy

Zde je několik tipů, které \<je třeba mít na paměti při použití náhodných>:

- Pro většinu účelů urngy vyrábět nezpracované bity, které musí být tvarovány distribuce. (Významná výjimka je [std::shuffle(),](../standard-library/algorithm-functions.md#shuffle) protože používá urng přímo.)

- Jeden instanci URNG nebo distribuce nelze bezpečně volat souběžně, protože spuštění URNG nebo distribuce je modifikující operace. Další informace naleznete [v tématu Bezpečnost vláken ve standardní knihovně jazyka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md).

- Jsou k dispozici [předdefinované typedefs](#typedefs) několika motorů; toto je upřednostňovaný způsob, jak vytvořit URNG, pokud je používán modul.

- Nejužitečnější párování pro většinu `mt19937` aplikací `uniform_int_distribution`je modul s , jak je znázorněno v [příkladu kódu](#code) dále v tomto článku.

Existuje mnoho možností, z \<čeho si můžete vybrat v náhodném> záhlaví, a `rand()`některý z nich je vhodnější než zastaralé c runtime funkce . Informace o tom, co `rand()` je \<špatného a jak náhodné> řeší tyto nedostatky, naleznete v [tomto videu](https://go.microsoft.com/fwlink/p/?linkid=397615).

## <a name="examples"></a><a name="code"></a>Příklady

Následující příklad kódu ukazuje, jak generovat některá náhodná čísla v tomto případě pět z nich pomocí generátoru vytvořeného s nedeterministickým semenem.

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

I když se jedná o vysoce kvalitní náhodná čísla a liší se pokaždé, když je tento program spuštěn, nejsou nutně v užitečném rozsahu. Chcete-li řídit rozsah, použijte rovnoměrné rozložení, jak je znázorněno v následujícím kódu:

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

Další příklad kódu ukazuje realističtější sadu případů použití s jednotně distribuovanými generátory náhodných čísel, které zamíjejí obsah vektoru a pole.

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

Tento kód ukazuje dvě různé randomizace – randomizujte vektor celých čísel a zamíchejte pole indexovaných dat – pomocí funkce testovací šablony. První volání testovací funkce používá krypto-secure, non-deterministické, neseedable, non-opakovatelné URNG `random_device`. Druhý test spustit `mersenne_twister_engine` používá jako URNG, s deterministický 32bitové konstantní osivo, což znamená, že výsledky jsou opakovatelné. Třetí test spustit `mersenne_twister_engine` semena s 32bitový nedeterministický výsledek z `random_device`. Čtvrtý test spustit rozšiřuje na to pomocí sekvence `random_device` [osiva](../standard-library/seed-seq-class.md) naplněné výsledky, které účinně dává více než 32bitové nedeterministické náhodnosti (ale stále není krypto-secure). Další informace naleznete v textu.

## <a name="categorized-listing"></a><a name="listing"></a>Zařazení do kategorií

### <a name="uniform-random-number-generators"></a><a name="urngs"></a>Generátory jednotných náhodných čísel

URNGs jsou často popsány z hlediska těchto vlastností:

1. **Délka období**: Kolik iterací je zapotřebí k opakování sekvence generovaných čísel. Čím déle, tím lépe.

2. **Výkon**: Jak rychle lze čísla generovat a kolik paměti je potřeba. Čím menší, tím lepší.

3. **Kvalita:** Jak blízko k skutečné náhodná čísla generované sekvence je. To se často nazývá "*náhodnost*".

V následujících částech jsou uvedeny jednotné generátory náhodných \<čísel (URNGs) uvedené v záhlaví náhodných>.

#### <a name="non-deterministic-generator"></a><a name="rd"></a>Nedeterministický generátor

|||
|-|-|
|[třída random_device](../standard-library/random-device-class.md)|Generuje nedeterministickou, kryptograficky zabezpečenou náhodnou sekvenci pomocí externího zařízení. Obvykle se používá k osivu motoru. Nízký výkon, velmi vysoká kvalita. Další informace naleznete v [tématu Poznámky](#comments).|

#### <a name="engine-typedefs-with-predefined-parameters"></a><a name="typedefs"></a>Modul typedefs s předdefinovanými parametry

Pro vytváření konkretizací motorů a adaptérů motoru. Další informace naleznete v [tématu Motory a distribuce](#engdist).

- `default_random_engine`Výchozí modul.

    ```cpp
    typedef mt19937 default_random_engine;
    ```

- `knuth_b`Knuth motor.

    ```cpp
    typedef shuffle_order_engine<minstd_rand0, 256> knuth_b;
    ```

- `minstd_rand0`1988 minimální standardní motor (Lewis, Goodman a Miller, 1969).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
    ```

- `minstd_rand`Byl aktualizován `minstd_rand0` minimální standardní motor (Park, Miller a Stockmeyer, 1993).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
    ```

- `mt19937`32-bit Mersenne twister motor (Matsumoto a Nishimura, 1998).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned int, 32, 624, 397,
        31, 0x9908b0df,
        11, 0xffffffff,
        7, 0x9d2c5680,
        15, 0xefc60000,
        18, 1812433253> mt19937;
    ```

- `mt19937_64`64-bit Mersenne twister motor (Matsumoto a Nishimura, 2000).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned long long, 64, 312, 156,
        31, 0xb5026f5aa96619e9ULL,
        29, 0x5555555555555555ULL,
        17, 0x71d67fffeda60000ULL,
        37, 0xfff7eee000000000ULL,
        43, 6364136223846793005ULL> mt19937_64;
    ```

- `ranlux24`24bitový motor RANLUX (Martin Lüscher a Fred James, 1994).

    ```cpp
    typedef discard_block_engine<ranlux24_base, 223, 23> ranlux24;
    ```

- `ranlux24_base`Používá se jako `ranlux24`základ pro .

    ```cpp
    typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;
    ```

- `ranlux48`48bitový motor RANLUX (Martin Lüscher a Fred James, 1994).

    ```cpp
    typedef discard_block_engine<ranlux48_base, 389, 11> ranlux48;
    ```

- `ranlux48_base`Používá se jako `ranlux48`základ pro .

    ```cpp
    typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;
    ```

#### <a name="engine-templates"></a><a name="eng"></a>Šablony motorů

Šablony motorů se používají jako samostatné urngy nebo jako základní motory předávané [adaptérům motoru](#engadapt). Obvykle jsou konsitovány s [předdefinovaným typem motoru](#typedefs) a předány [do distribuce](#distributions). Další informace naleznete v části [Motory a distribuce.](#engdist)

|||
|-|-|
|[linear_congruential_engine – třída](../standard-library/linear-congruential-engine-class.md)|Generuje náhodnou sekvenci pomocí lineárního shodného algoritmu. Nejvíce zjednodušující a nejnižší kvality.|
|[mersenne_twister_engine – třída](../standard-library/mersenne-twister-engine-class.md)|Generuje náhodnou sekvenci pomocí mersennetwister algoritmus. Nejsložitější, a je nejvyšší kvalita s výjimkou random_device třídy. Velmi rychlý výkon.|
|[subtract_with_carry_engine třída](../standard-library/subtract-with-carry-engine-class.md)|Generuje náhodné sekvence pomocí algoritmu odečíst s nést. Zlepšení na `linear_congruential_engine`, ale mnohem nižší `mersenne_twister_engine`kvalitu a výkon než .|

#### <a name="engine-adaptor-templates"></a><a name="engadapt"></a>Šablony adaptéru motoru

Adaptéry motoru jsou šablony, které přizpůsobují jiné (základní) motory. Obvykle jsou konsitovány s [předdefinovaným typem motoru](#typedefs) a předány [do distribuce](#distributions). Další informace naleznete v části [Motory a distribuce.](#engdist)

|||
|-|-|
|[třída discard_block_engine](../standard-library/discard-block-engine-class.md)|Generuje náhodnou sekvenci zahozením hodnot vrácených jeho základním motorem.|
|[independent_bits_engine třída](../standard-library/independent-bits-engine-class.md)|Generuje náhodnou sekvenci se zadaným počtem bitů přebalením bitů z hodnot vrácených jeho základním motorem.|
|[shuffle_order_engine – třída](../standard-library/shuffle-order-engine-class.md)|Generuje náhodné sekvence změnou pořadí hodnoty vrácené z jeho základní motor.|

[[Šablony motorů](#eng)]

### <a name="random-number-distributions"></a><a name="distributions"></a>Distribuce náhodných čísel

V následujících částech jsou uvedeny \<distribuce uvedené v záhlaví náhodné>. Distribuce jsou mechanismus následného zpracování, obvykle používající výstup URNG jako vstup a distribuci výstupu definovanou statistickou hustotou pravděpodobnosti funkce. Další informace naleznete v části [Motory a distribuce.](#engdist)

#### <a name="uniform-distributions"></a>Jednotné rozdělení

|||
|-|-|
|[uniform_int_distribution třída](../standard-library/uniform-int-distribution-class.md)|Vytvoří jednotné celočíselné rozdělení hodnoty v rozsahu \[v uzavřeném intervalu a, b] (včetně včetně).|
|[uniform_real_distribution třída](../standard-library/uniform-real-distribution-class.md)|Vytvoří jednotné rozdělení skutečné hodnoty (s plovoucí desetinnou desetinnou hodnotou) v rozsahu v intervalu polovičního otevření [a, b) (včetně výhradní).|
|[generate_canonical](../standard-library/random-functions.md#generate_canonical)|Vytváří rovnoměrné rozdělení reálných (plovoucí bod) hodnoty dané přesnosti napříč [0, 1) (včetně výhradní).|

[[Distribuce náhodných čísel](#distributions)]

#### <a name="bernoulli-distributions"></a>Bernoulli distribuce

|||
|-|-|
|[bernoulli_distribution – třída](../standard-library/bernoulli-distribution-class.md)|Vytváří Bernoulliho rozdělení **bool** hodnot.|
|[binomial_distribution – třída](../standard-library/binomial-distribution-class.md)|Vytvoří binomické rozdělení celé hodnoty.|
|[geometric_distribution – třída](../standard-library/geometric-distribution-class.md)|Vytvoří geometrické rozdělení celé hodnoty.|
|[negative_binomial_distribution třída](../standard-library/negative-binomial-distribution-class.md)|Vytvoří záporné binomické rozdělení hodnot celého čísla.|

[[Distribuce náhodných čísel](#distributions)]

#### <a name="normal-distributions"></a>Normální distribuce

|||
|-|-|
|[cauchy_distribution – třída](../standard-library/cauchy-distribution-class.md)|Vytvoří Cauchyrozdělení reálných (plovoucí desetinná hodnota) hodnoty.|
|[třída chi_squared_distribution](../standard-library/chi-squared-distribution-class.md)|Vytvoří chí-kvadrát rozdělení reálných (plovoucí bod) hodnoty.|
|[fisher_f_distribution – třída](../standard-library/fisher-f-distribution-class.md)|Vytváří F-rozdělení (také známý jako Snedecor f rozdělení nebo Fisher-Snedecor distribuce) reálných (plovoucí bod) hodnoty.|
|[lognormal_distribution – třída](../standard-library/lognormal-distribution-class.md)|Vytvoří normální rozdělení normálního log u reálných hodnot (s plovoucí desetinnou tázkou).|
|[normal_distribution – třída](../standard-library/normal-distribution-class.md)|Vytvoří normální (Gaussovy) rozdělení reálných (plovoucí chodů) hodnot.|
|[student_t_distribution – třída](../standard-library/student-t-distribution-class.md)|Vytvoří studenta *t-rozdělení*reálných (plovoucí bod) hodnoty.|

[[Distribuce náhodných čísel](#distributions)]

#### <a name="poisson-distributions"></a>Poissonovo rozdělení

|||
|-|-|
|[exponential_distribution – třída](../standard-library/exponential-distribution-class.md)|Vytvoří exponenciální rozdělení reálných hodnot (s plovoucí desetinnou tázkou).|
|[extreme_value_distribution – třída](../standard-library/extreme-value-distribution-class.md)|Vytvoří extrémní rozložení hodnoty reálných hodnot (s plovoucí desetinnou tázkou).|
|[gamma_distribution – třída](../standard-library/gamma-distribution-class.md)|Vytvoří gama rozdělení reálných hodnot (s plovoucí desetinnou tázkou).|
|[poisson_distribution – třída](../standard-library/poisson-distribution-class.md)|Vytvoří Poissonovo rozdělení hodnot celého čísla.|
|[weibull_distribution – třída](../standard-library/weibull-distribution-class.md)|Vytvoří Weibullovu distribuci reálných hodnot (s plovoucí desetinnou tálicí).|

[[Distribuce náhodných čísel](#distributions)]

#### <a name="sampling-distributions"></a>Distribuce vzorkování

|||
|-|-|
|[discrete_distribution třída](../standard-library/discrete-distribution-class.md)|Vytvoří diskrétní rozložení celého čísla.|
|[piecewise_constant_distribution – třída](../standard-library/piecewise-constant-distribution-class.md)|Vytvoří postupné konstantní rozdělení reálných hodnot (s plovoucí desetinnou tázkou).|
|[piecewise_linear_distribution třída](../standard-library/piecewise-linear-distribution-class.md)|Vytvoří postupné lineární rozdělení reálných hodnot (s plovoucí desetinnou čárkou).|

[[Distribuce náhodných čísel](#distributions)]

### <a name="utility-functions"></a>Užitné funkce

V této části jsou uvedeny \<obecné funkce nástrojů uvedené v záhlaví náhodné>.

|||
|-|-|
|[seed_seq třída](../standard-library/seed-seq-class.md)|Generuje nezkreslenou sekvenci míchaných semen. Používá se k zabránění replikaci náhodných variačních proudů. Užitečné, když mnoho URNGs jsou konsitovány z motorů.|

### <a name="operators"></a>Operátory

V této části jsou uvedeny operátory uvedené v \<záhlaví náhodné>.

|||
|-|-|
|`operator==`|Testuje, zda urng na levé straně operátoru se rovná motoru na pravé straně.|
|`operator!=`|Testuje, zda urng na levé straně operátoru není rovna motoru na pravé straně.|
|`operator<<`|Zapisuje informace o stavu do datového proudu.|
|`operator>>`|Extrahuje informace o stavu z datového proudu.|

## <a name="engines-and-distributions"></a><a name="engdist"></a>Motory a rozvody

Informace o jednotlivých kategoriích šablon tříd definovaných \<v náhodných> naleznete v následujících částech. Obě tyto kategorie šablony třídy přebírají typ jako argument a používají názvy parametrů sdílené šablony k popisu vlastností typu, které jsou povoleny jako skutečný typ argumentu, a to následovně:

- `IntType`označuje **krátký**, **int**, **dlouhý**, **dlouhý**, **nepodepsaný krátký**, **nepodepsaný int**, **nepodepsaný dlouhý**nebo **nepodepsaný dlouhý**.

- `UIntType`označuje **neznaménkem krátký**, **nepodepsaný int**, **neznatídlouhý**nebo **neznatit dlouhý**.

- `RealType`označuje **plovoucí**, **dvojité**nebo **dlouhé dvojité**.

### <a name="engines"></a>Motory

[Šablony motorů](#eng) a [Šablony adaptéru motoru](#engadapt) jsou šablony, jejichž parametry přizpůsobit generátor vytvořil.

*Motor* je šablona třídy nebo třídy, jejíž instance (generátory) fungují jako zdroj náhodných čísel rovnoměrně rozdělených mezi minimální a maximální hodnotu. *Adaptér motoru* poskytuje posloupnost hodnot, které mají různé vlastnosti náhodnosti tím, že hodnoty vyrobené některé jiné náhodné číslo motoru a použití algoritmu nějakého druhu na tyto hodnoty.

Každý motor a adaptér motoru má následující členy:

- `typedef`je typ, který je vrácen generátoru `operator()` `numeric-type` `result_type` Je `numeric-type` předán jako parametr šablony při vytváření instancí.

- `result_type operator()`vrátí hodnoty, které jsou `min()` `max()`rovnoměrně rozděleny mezi a .

- `result_type min()`vrátí minimální hodnotu vrácenou hodnotou `operator()`generátoru . Adaptéry motoru používají výsledek `min()` základního motoru.

- `result_type max()`vrátí maximální hodnotu vrácenou hodnotou `operator()`generátoru . Když `result_type` je integrální (celočíselné `max()` hodnoty) typ, je maximální hodnota, která může být skutečně vrácena (včetně); když `result_type` je typ s plovoucí desetinnou `max()` desetinnou a skutečnou hodnotou je nejmenší hodnota větší než všechny hodnoty, které lze vrátit (bez zahrnutí). Adaptéry motoru používají výsledek `max()` základního motoru.

- `void seed(result_type s)`osivo generátoru `s`s hodnotou osiva . U motorů je `void seed(result_type s = default_seed)` podpis určen pro podporu výchozích parametrů `void seed()`(adaptéry motoru definují samostatný , viz další pododdíl).

- `template <class Seq> void seed(Seq& q)`generátor pomocí [seed_seq](../standard-library/seed-seq-class.md)`Seq`.

- Explicitní konstruktor s `result_type x` argumentem, který vytvoří generátor `seed(x)`osiva jako by voláním .

- Explicitní konstruktor s `seed_seq& seq` argumentem, který vytvoří generátor `seed(seq)`osiva jako by voláním .

- `void discard(unsigned long long count)`efektivně volá `operator()` `count` časy a zahodí každou hodnotu.

**Adaptéry motoru** navíc podporují`Engine` tyto členy ( je prvním parametrem šablony adaptéru motoru, který označí typ základního motoru):

- Výchozí konstruktor pro inicializaci generátoru, jako by z výchozího konstruktoru základního motoru.

- Explicitní konstruktor s `const Engine& eng`argumentem . To to je na podporu kopírování konstrukce pomocí základního motoru.

- Explicitní konstruktor s `Engine&& eng`argumentem . To je na podporu přesunout konstrukci pomocí základního motoru.

- `void seed()`který inicializuje generátor s výchozí hodnotou osiva základního motoru.

- `const Engine& base()`vlastnost, která vrací základní motor, který byl použit k vytvoření generátoru.

Každý modul udržuje *stav,* který určuje pořadí hodnot, které budou `operator()`generovány následnými voláními . Stavy dvou generátorů, které byly konsitovány z motorů `operator==` `operator!=`stejného typu, lze porovnat pomocí a . Pokud se oba stavy porovnávají jako rovné, vygenerují stejnou posloupnost hodnot. Stav objektu lze uložit do datového proudu jako posloupnost 32bitových `operator<<` nepodepsaných hodnot pomocí generátoru. Uložením se stav nezmění. Uložený stav lze číst do generátoru instancizovat z `operator>>`motoru stejného typu pomocí .

### <a name="distributions"></a>Distribuce

[Distribuce náhodných čísel](#distributions) je šablona třídy nebo třídy, jejíž instance transformují proud rovnoměrně distribuovaných náhodných čísel získaných z motoru na proud náhodných čísel, které mají určité rozdělení. Každá distribuce má následující členy:

- `typedef`je typ, který je vrácen a distribuce `operator()` `numeric-type` `result_type` Je `numeric-type` předán jako parametr šablony při vytváření instancí.

- `template <class URNG> result_type operator()(URNG& gen)`vrátí hodnoty, které jsou distribuovány podle definice `gen` distribuce, pomocí jako zdroj rovnoměrně distribuovaných *náhodných*hodnot a uložených parametrů distribuce .

- `template <class URNG> result_type operator()(URNG& gen, param_type p)`vrátí hodnoty distribuované v souladu `gen` s definicí distribuce, které se používají `p`jako zdroj jednotně distribuovaných náhodných hodnot a struktury parametrů .

- `typedef`je balíček parametrů volitelně `operator()` předán a používá se místo uložených parametrů ke generování jeho návratové hodnoty. `unspecified-type` `param_type`

- Konstruktor `const param&` inicializuje uložené parametry z jeho argumentu.

- `param_type param() const`získá uložené parametry.

- `void param(const param_type&)`nastaví uložené parametry z jeho argumentu.

- `result_type min()`vrátí minimální hodnotu vrácenou hodnotou `operator()`distribuce .

- `result_type max()`vrátí maximální hodnotu vrácenou hodnotou `operator()`distribuce . Když `result_type` je integrální (celočíselné `max()` hodnoty) typ, je maximální hodnota, která může být skutečně vrácena (včetně); když `result_type` je typ s plovoucí desetinnou `max()` desetinnou a skutečnou hodnotou je nejmenší hodnota větší než všechny hodnoty, které lze vrátit (bez zahrnutí).

- `void reset()`zahodí všechny hodnoty uložené v mezipaměti, takže `operator()` výsledek dalšího volání nezávisí na žádné hodnoty získané z motoru před voláním.

Struktura parametrů je objekt, který ukládá všechny parametry potřebné pro distribuci. Obsahuje následující:

- `typedef``distribution-type` , což je typ jeho `distribution_type`distribuce.

- Jeden nebo více konstruktorů, které mají stejné seznamy parametrů jako konstruktory distribuce.

- Stejné funkce přístupu k parametru jako distribuce.

- Operátory porovnání rovnosti a nerovnosti.

Další informace naleznete v referenčních dílčích tématech pod tímto tématem, které byly propojeny dříve v tomto článku.

## <a name="remarks"></a><a name="comments"></a>Poznámky

Existují dva velmi užitečné URNGs`mt19937` v `random_device`sadě Visual Studio – a – jak je znázorněno v této tabulce porovnání:

|URNG|Rychle|Krypto-bezpečné|Seedable|Deterministická|
|----------|-----------|---------------------|---------------|--------------------|
|`mt19937`|Ano|Ne|Ano|Ano<sup>*</sup>|
|`random_device`|Ne|Ano|Ne|Ne|

<sup>* Je-li opatřeno známým semenem.</sup>

Přestože norma ISO C++ `random_device` nevyžaduje kryptograficky zabezpečené, v sadě Visual Studio je implementována tak, aby byla kryptograficky zabezpečená. (Termín "kryptograficky bezpečné" neznamená záruky, ale odkazuje na minimální úroveň entropie - a proto úroveň předvídatelnosti - daný randomizační algoritmus poskytuje. Další informace naleznete v článku Wikipedie [Cryptographically secure pseudorandom number generator](https://go.microsoft.com/fwlink/p/?linkid=398017).) Vzhledem k tomu, že norma ISO C++ to nevyžaduje, mohou jiné platformy implementovat `random_device` jako jednoduchý generátor pseudonáhodných čísel (není kryptograficky zabezpečený) a mohou být vhodné pouze jako zdroj osiva pro jiný generátor. Při použití `random_device` v kódu pro různé platformy naleznete dokumentaci pro tyto platformy.

Podle definice `random_device` výsledky nejsou reprodukovatelné a vedlejším účinkem je, že může běžet výrazně pomaleji než ostatní URNGs. Většina aplikací, které nemusí být kryptograficky zabezpečené použití `mt19937` nebo podobný modul, i `random_device`když můžete chtít osiva s voláním , jak je znázorněno v [příkladu kódu](#code).

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)
