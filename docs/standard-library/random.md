---
title: '&lt;vybraných&gt;'
ms.date: 08/24/2017
f1_keywords:
- <random>
helpviewer_keywords:
- random header
ms.assetid: 60afc25c-b162-4811-97c1-1b65398d4c57
ms.openlocfilehash: 5738a1ea5ab950466f347090649e72471edf5608
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458297"
---
# <a name="ltrandomgt"></a>&lt;vybraných&gt;

Definuje zařízení pro generování náhodných čísel, což umožňuje vytváření rovnoměrně distribuovaných náhodných čísel.

## <a name="requirements"></a>Požadavky

**Záhlaví**: \<náhodný >

**Obor názvů:** std

> [!NOTE]
> Knihovna \<náhodného > používá příkaz #include < initializer_list >.

## <a name="summary"></a>Souhrn

*Generátor náhodných čísel* je objekt, který vytváří sekvenci pseudo náhodných hodnot. Generátor, který vytváří hodnoty, které jsou rovnoměrně distribuovány v zadaném rozsahu, představuje *jednotný generátor náhodných čísel* (URNG). Třída šablony navržená tak, aby fungovala jako URNG, je označována jako *modul* , pokud tato třída má určité společné vlastnosti, které jsou popsány dále v tomto článku. URNG může být – a obvykle je v kombinaci s *distribucí* předáním URNG jako argumentu distribučního prvku `operator()` k vytvoření hodnot, které jsou distribuovány způsobem, který je definován distribucí.

Tyto odkazy odkazují na hlavní části tohoto článku:

- [Příklady](#code)

- [Zařazení do kategorií](#listing)

- [Moduly a distribuce](#engdist)

- [Poznámky](#comments)

### <a name="quick-tips"></a>Rychlé tipy

Tady je několik tipů, které byste měli mít na \<paměti při použití náhodných >:

- Pro většinu účelů URNGs vyrábí nezpracované bity, které musí být ve tvaru podle distribucí. (Významnou výjimkou je to, že se jedná o výjimku [std:: náhodně ()](../standard-library/algorithm-functions.md#shuffle) , protože používá URNG přímo.)

- Jednu instanci URNG nebo distribuce nelze bezpečně volat souběžně, protože spuštění URNG nebo distribuce je úprava operace. Další informace najdete v tématu věnovaném [zabezpečení vlákna C++ ve standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md).

- K dispozici jsou [předdefinované definice typedefy](#typedefs) několika modulů. Toto je preferovaný způsob, jak vytvořit URNG, pokud se používá modul.

- Nejužitečnější párování pro většinu aplikací je `mt19937` modul s `uniform_int_distribution`, jak je znázorněno v [příkladu kódu](#code) dále v tomto článku.

Existuje mnoho možností, jak vybírat v \<hlavičce náhodného > a kterákoli z nich je vhodnější pro zastaralou funkci `rand()`běhového prostředí jazyka C. Informace o tom, co je chybné `rand()` a jak \<náhodná > řeší tyto nedostatky, najdete v [tomto videu](https://go.microsoft.com/fwlink/p/?linkid=397615).

## <a name="code"></a>4.6

Následující příklad kódu ukazuje, jak generovat náhodná čísla v tomto případě pět z nich pomocí generátoru vytvořeného pomocí nedeterministického počátečního naplnění.

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

I když se jedná o velmi kvalitní náhodná čísla a při každém spuštění tohoto programu se liší, nemusí být nutně ve vhodném rozsahu. Pro řízení rozsahu použijte jednotnou distribuci, jak je znázorněno v následujícím kódu:

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

Následující příklad kódu ukazuje realističtější sadu případů použití s jednotně distribuovanými generátory náhodných čísel, která převádí obsah vektoru a pole.

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

Tento kód ukazuje dva různé náhodné způsoby – náhodně vektor celých čísel a náhodné pole indexovaných dat – s funkcí šablony testu. První volání funkce test používá kryptografické a nedeterministické, neURNGelné `random_device`, nediskriminační a neopakující. Druhý testovací běh používá `mersenne_twister_engine` jako URNG a deterministické 32 konstanty, což znamená, že se výsledky opakují. Třetí testuje semena `mersenne_twister_engine` s 32 nedeterministickým `random_device`výsledkem. Čtvrtý běh testu se v této chvíli rozbalí pomocí [sekvence počáteční](../standard-library/seed-seq-class.md) hodnoty vyplněné `random_device` výsledky, což efektivně poskytne více než 32 nedeterministické náhodnosti (ale pořád není kryptografické zabezpečení). Další informace najdete v článku.

## <a name="listing"></a>Zařazení do kategorií

###  <a name="urngs"></a>Jednotné generátory náhodných čísel

URNGs jsou často popsané v těchto vlastnostech:

1. **Délka období**: Kolik iterací trvá k opakování posloupnosti vygenerovaných čísel. Čím je lepší.

2. **Výkon**: Jak rychle je možné vygenerovat čísla a kolik paměti bude trvat. Tím menší je lepší.

3. **Kvalita**: Jak blízko k hodnotě true náhodná čísla je vygenerovaná sekvence. Tato možnost se často nazývá "*náhodnost*".

V následujících částech je uveden seznam jednotných generátorů náhodných čísel (URNGs \<), které jsou k dispozici v hlavičce náhodného >.

####  <a name="rd"></a>Nedeterministický generátor

|||
|-|-|
|[random_device – třída](../standard-library/random-device-class.md)|Generuje nedeterministické a kryptograficky zabezpečené náhodné sekvence pomocí externího zařízení. Obvykle se používá k osazení stroje. Nízký výkon, velmi vysoká kvalita. Další informace najdete v tématu [poznámky](#comments).|

####  <a name="typedefs"></a>Modul definice typedef s předdefinovanými parametry

Pro vytváření instancí modulů a adaptérů stroje. Další informace najdete v tématu [moduly a distribuce](#engdist).

- `default_random_engine`Výchozí modul.

    ```cpp
    typedef mt19937 default_random_engine;
    ```

- `knuth_b`Modul Knuth

    ```cpp
    typedef shuffle_order_engine<minstd_rand0, 256> knuth_b;
    ```

- `minstd_rand0`1988 minimální standardní stroj (Lewis, Goodman a Miller, 1969).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
    ```

- `minstd_rand`Byl aktualizován minimální standardní `minstd_rand0` stroj (Park, Miller a Stockmeyer, 1993).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
    ```

- `mt19937`32-bit Mersenne Twister Engine (Matsumoto a Nishimura, 1998).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned int, 32, 624, 397,
        31, 0x9908b0df,
        11, 0xffffffff,
        7, 0x9d2c5680,
        15, 0xefc60000,
        18, 1812433253> mt19937;
    ```

- `mt19937_64`64-bit Mersenne Twister Engine (Matsumoto a Nishimura, 2000).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned long long, 64, 312, 156,
        31, 0xb5026f5aa96619e9ULL,
        29, 0x5555555555555555ULL,
        17, 0x71d67fffeda60000ULL,
        37, 0xfff7eee000000000ULL,
        43, 6364136223846793005ULL> mt19937_64;
    ```

- `ranlux24`RANLUX modul pro 24 bitů (Novák Lüscher a Fred James, 1994).

    ```cpp
    typedef discard_block_engine<ranlux24_base, 223, 23> ranlux24;
    ```

- `ranlux24_base`Používá se jako základ pro `ranlux24`.

    ```cpp
    typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;
    ```

- `ranlux48`48 stroj RANLUX (Martin Lüscher a Fred James, 1994).

    ```cpp
    typedef discard_block_engine<ranlux48_base, 389, 11> ranlux48;
    ```

- `ranlux48_base`Používá se jako základ pro `ranlux48`.

    ```cpp
    typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;
    ```

####  <a name="eng"></a>Šablony modulu

Šablony stroje se používají jako samostatné URNGs nebo jako základní moduly předané [adaptérům modulu](#engadapt). Obvykle jsou vytvořeny instance pomocí [předdefinované definice typu modulu](#typedefs) a předány do [distribuce](#distributions). Další informace najdete v části [moduly a distribuce](#engdist) .

|||
|-|-|
|[linear_congruential_engine – třída](../standard-library/linear-congruential-engine-class.md)|Generuje náhodnou posloupnost pomocí lineárního algoritmu algoritmu congruential. Nejvíce zjednodušený a nejnižší kvalita.|
|[mersenne_twister_engine – třída](../standard-library/mersenne-twister-engine-class.md)|Vygeneruje náhodnou posloupnost pomocí algoritmu Twister Mersenne. Nejsložitější a je nejvyšší kvalita s výjimkou třídy random_device. Velmi rychlý výkon.|
|[subtract_with_carry_engine – třída](../standard-library/subtract-with-carry-engine-class.md)|Vygeneruje náhodnou sekvenci pomocí algoritmu odečíst od-po přenosu. Zlepšení `linear_congruential_engine`, ale mnohem nižší kvality a `mersenne_twister_engine`výkonu.|

####  <a name="engadapt"></a>Šablony adaptérů pro moduly

Adaptéry pro modul jsou šablony, které přizpůsobují jiné (základní) moduly. Obvykle jsou vytvořeny instance pomocí [předdefinované definice typu modulu](#typedefs) a předány do [distribuce](#distributions). Další informace najdete v části [moduly a distribuce](#engdist) .

|||
|-|-|
|[discard_block_engine – třída](../standard-library/discard-block-engine-class.md)|Vygeneruje náhodnou sekvenci vyhozením hodnot vrácených základním modulem.|
|[independent_bits_engine – třída](../standard-library/independent-bits-engine-class.md)|Vygeneruje náhodnou sekvenci se zadaným počtem bitů pomocí opětovného sbalení bitů z hodnot vrácených jeho základním modulem.|
|[shuffle_order_engine – třída](../standard-library/shuffle-order-engine-class.md)|Vygeneruje náhodnou sekvenci změnou pořadí hodnot vrácených z jeho základního modulu.|

[[Šablony stroje](#eng)]

###  <a name="distributions"></a>Distribuce náhodných čísel

V následujících částech jsou uvedena distribuce uvedená v \<hlavičce náhodného >. Distribuce představují mechanismus následného zpracování, obvykle používá výstup URNG jako vstup a distribuuje výstup pomocí definované statistické funkce hustoty pravděpodobnosti. Další informace najdete v části [moduly a distribuce](#engdist) .

#### <a name="uniform-distributions"></a>Rovnoměrné distribuce

|||
|-|-|
|[uniform_int_distribution – třída](../standard-library/uniform-int-distribution-class.md)|Vytvoří jednotnou celočíselnou hodnotu rozdělení v rozsahu v uzavřeném intervalu \[a, b] (včetně (včetně).|
|[uniform_real_distribution – třída](../standard-library/uniform-real-distribution-class.md)|Vytvoří jednotnou hodnotu reálného (plovoucího)ho rozdělení v rozsahu v polovičním otevřeném intervalu [a, b) (včetně exkluzivních).|
|[generate_canonical](../standard-library/random-functions.md#generate_canonical)|Vytvoří rovnoměrné rozložení reálných hodnot (plovoucí desetinné čárky) dané přesnosti napříč [0, 1) (včetně exkluzivních).|

[[Distribuce náhodného čísla](#distributions)]

#### <a name="bernoulli-distributions"></a>Bernoulliho distribuce

|||
|-|-|
|[bernoulli_distribution – třída](../standard-library/bernoulli-distribution-class.md)|Vytvoří Bernoulliho rozdělení hodnot **bool** .|
|[binomial_distribution – třída](../standard-library/binomial-distribution-class.md)|Vytvoří binomické rozdělení celočíselných hodnot.|
|[geometric_distribution – třída](../standard-library/geometric-distribution-class.md)|Vytvoří geometrickou distribuci celočíselných hodnot.|
|[negative_binomial_distribution – třída](../standard-library/negative-binomial-distribution-class.md)|Vytvoří negativní binomické rozdělení celočíselných hodnot.|

[[Distribuce náhodného čísla](#distributions)]

#### <a name="normal-distributions"></a>Normální distribuce

|||
|-|-|
|[cauchy_distribution – třída](../standard-library/cauchy-distribution-class.md)|Vytvoří Cauchy distribuci reálných hodnot (s plovoucí desetinnou čárkou).|
|[chi_squared_distribution – třída](../standard-library/chi-squared-distribution-class.md)|Vytvoří rozdělení hodnot reálného (plovoucího bodu) na více než čtverce.|
|[fisher_f_distribution – třída](../standard-library/fisher-f-distribution-class.md)|Vytvoří F-Distribution (označuje se také jako distribuce v Snedecor F nebo Snedecor distribuce) reálného (plovoucího bodu).|
|[lognormal_distribution – třída](../standard-library/lognormal-distribution-class.md)|Vytvoří normální distribuci reálných hodnot (plovoucí desetinná čárka) protokolu.|
|[normal_distribution – třída](../standard-library/normal-distribution-class.md)|Vytvoří normální (Gaussovské) distribuci reálných hodnot (s plovoucí desetinnou čárkou).|
|[student_t_distribution – třída](../standard-library/student-t-distribution-class.md)|Vytvoří Studentova *t*-rozdělení reálných hodnot (s plovoucí desetinnou čárkou).|

[[Distribuce náhodného čísla](#distributions)]

#### <a name="poisson-distributions"></a>Poissonova distribuce

|||
|-|-|
|[exponential_distribution – třída](../standard-library/exponential-distribution-class.md)|Vytvoří exponenciální distribuci reálných hodnot (s plovoucí desetinnou čárkou).|
|[extreme_value_distribution – třída](../standard-library/extreme-value-distribution-class.md)|Vytvoří hodnotu distribuce reálných hodnot reálného (plovoucího bodu).|
|[gamma_distribution – třída](../standard-library/gamma-distribution-class.md)|Vytvoří gama distribuci reálných hodnot (s plovoucí desetinnou čárkou).|
|[poisson_distribution – třída](../standard-library/poisson-distribution-class.md)|Vytvoří Poissonova rozdělení celočíselných hodnot.|
|[weibull_distribution – třída](../standard-library/weibull-distribution-class.md)|Vytvoří distribuci hodnoty WEIBULL reálných hodnot (s plovoucí desetinnou čárkou).|

[[Distribuce náhodného čísla](#distributions)]

#### <a name="sampling-distributions"></a>Distribuce vzorkování

|||
|-|-|
|[discrete_distribution – třída](../standard-library/discrete-distribution-class.md)|Vytvoří diskrétní rozdělení celého čísla.|
|[piecewise_constant_distribution – třída](../standard-library/piecewise-constant-distribution-class.md)|Vytvoří konstantní konstantní distribuci reálných hodnot (s plovoucí desetinnou čárkou).|
|[piecewise_linear_distribution – třída](../standard-library/piecewise-linear-distribution-class.md)|Vytvoří konstantní lineární distribuci hodnot reálného (plovoucího bodu).|

[[Distribuce náhodného čísla](#distributions)]

### <a name="utility-functions"></a>Funkce nástrojů

V této části jsou uvedeny obecné funkce nástrojů, které \<jsou k dispozici v hlavičce náhodného >.

|||
|-|-|
|[seed_seq – třída](../standard-library/seed-seq-class.md)|Generuje neposunutou kódovaný počáteční sekvenci. Používá se k tomu, aby se zabránilo replikaci náhodných proudů variate. Užitečné v případě, že je z modulů vytvořena instance řady URNGs.|

### <a name="operators"></a>Operátory

V této části jsou uvedeny operátory poskytované v \<hlavičce náhodného >.

|||
|-|-|
|`operator==`|Testuje, zda je URNG na levé straně operátoru roven modulu na pravé straně.|
|`operator!=`|Testuje, zda je URNG na levé straně operátoru nerovno stroji na pravé straně.|
|`operator<<`|Zapisuje informace o stavu do datového proudu.|
|`operator>>`|Extrahuje informace o stavu z datového proudu.|

## <a name="engdist"></a>Moduly a distribuce

Informace o jednotlivých kategoriích tříd šablony definovaných v \<náhodných > naleznete v následujících oddílech. Obě tyto kategorie třídy šablony přebírají typ jako argument a používají názvy parametrů sdílené šablony k popisu vlastností typu, které jsou povoleny jako skutečný typ argumentu, následovně:

- `IntType` označuje **krátký**, **int**, **dlouhé**, **long long**, **unsigned short**,  **unsigned int**, **unsigned long**, nebo **unsigned long long**.

- `UIntType` označuje **unsigned short**, **unsigned int**, **unsigned long**, nebo **unsigned long long**.

- `RealType`označuje typ **float**, **Double**nebo **Long Double**.

### <a name="engines"></a>Motoru

[](#eng) Šablony a [šablony adaptérů stroje](#engadapt) jsou šablony, jejichž parametry přizpůsobují vytvořený generátor.

*Modul* je třída nebo třída šablony, jejíž instance (generátory) fungují jako zdroj náhodných čísel rovnoměrně distribuovaných mezi minimální a maximální hodnotou. *Adaptér* s modulem poskytuje sekvenci hodnot, které mají různé vlastnosti náhodnosti, a to prostřednictvím hodnot vyprodukovaných nějakým jiným modulem náhodného čísla a aplikováním algoritmu určitého typu na tyto hodnoty.

Každý modul a adaptér motoru má následující členy:

- `typedef`je typ, který je `operator()`vrácen generátorem. `numeric-type` `result_type` Objekt `numeric-type` je předán jako parametr šablony při vytváření instance.

- `result_type operator()`Vrátí hodnoty, které jsou rovnoměrně rozloženy `min()` mezi `max()`a.

- `result_type min()`Vrátí minimální hodnotu, která je vrácena generátorem `operator()`. Adaptéry modulu používají `min()` výsledek základního modulu.

- `result_type max()`Vrátí maximální hodnotu, která je vrácena generátorem `operator()`. Když `result_type` je celočíselný typ (s celočíselnou hodnotou) `max()` , je maximální hodnota, která může být vrácena (včetně); když `result_type` je typ s plovoucí desetinnou čárkou (s hodnotou reálné `max()` hodnoty), je nejmenší hodnota větší než všechny hodnoty. To může být vráceno (Nezahrnuto). Adaptéry modulu používají `max()` výsledek základního modulu.

- `void seed(result_type s)`semena generátoru s hodnotou počáteční `s`hodnoty. U modulů je `void seed(result_type s = default_seed)` podpis pro podporu výchozích parametrů (adaptéry modulu definují samostatné `void seed()`, viz další pododdíl).

- `template <class Seq> void seed(Seq& q)`Vytvoří semena generátoru pomocí [seed_seq](../standard-library/seed-seq-class.md)`Seq`.

- Explicitní konstruktor s argumentem `result_type x` , který vytváří generátor vynásobený jako if voláním. `seed(x)`

- Explicitní konstruktor s argumentem `seed_seq& seq` , který vytváří generátor vynásobený jako if voláním. `seed(seq)`

- `void discard(unsigned long long count)`efektivně volá `operator()` `count` časy a zahodí všechny hodnoty.

**Adaptéry adaptérů** dále podporují tyto členy (`Engine` jedná se o první parametr šablony adaptéru modulu, který určí typ základního motoru):

- Výchozí konstruktor pro inicializaci generátoru, jako by byl ze výchozího konstruktoru základního modulu.

- Explicitní konstruktor s argumentem `const Engine& eng`. To je podpora konstrukce kopírování pomocí základního modulu.

- Explicitní konstruktor s argumentem `Engine&& eng`. Tato možnost podporuje konstrukci přesunutí pomocí základního modulu.

- `void seed()`Inicializuje generátor se výchozí hodnotou počáteční hodnoty základního modulu.

- `const Engine& base()`funkce vlastnosti, která vrací základní modul, který byl použit k vytvoření generátoru.

Každý modul udržuje *stav* , který určuje sekvenci hodnot, které budou vygenerovány následnými voláními `operator()`. Stavy dvou generátorů vytvořených z motorů stejného typu lze porovnat pomocí `operator==` a. `operator!=` Pokud se dva stavy porovnají se stejnou hodnotou, vygenerují stejnou sekvenci hodnot. Stav objektu lze uložit do datového proudu jako sekvenci 32 hodnot bez znaménka pomocí `operator<<` generátoru. Stav se nemění tím, že ho uložíte. Uložený stav lze číst do generátoru vytvořeného z modulu stejného typu pomocí `operator>>`.

### <a name="distributions"></a>Distribuce

[Náhodné číselné distribuce](#distributions) jsou třídy nebo třídy šablony, jejichž instance transformují proud rovnoměrně distribuovaných náhodných čísel získaných z modulu do datového proudu náhodných čísel, která mají určitou distribuci. Každá distribuce má následující členy:

- `typedef`je typ, který je `operator()`vrácen funkcí distribuce. `numeric-type` `result_type` Objekt `numeric-type` je předán jako parametr šablony při vytváření instance.

- `template <class URNG> result_type operator()(URNG& gen)`Vrátí hodnoty, které jsou distribuovány podle definice distribuce, pomocí `gen` jako zdroje rovnoměrně distribuovaných náhodných hodnot a uložených *parametrů distribuce*.

- `template <class URNG> result_type operator()(URNG& gen, param_type p)`Vrátí hodnoty distribuované v souladu s definicí distribuce, a to `gen` pomocí jako zdroj rovnoměrně distribuovaných náhodných hodnot a struktury `p`parametrů.

- `typedef`je balíček parametrů volitelně předaných na `operator()` místo uložených parametrů, který slouží k vygenerování návratové hodnoty. `unspecified-type` `param_type`

- `const param&` Konstruktor inicializuje uložené parametry z jeho argumentu.

- `param_type param() const`Načte uložené parametry.

- `void param(const param_type&)`Nastaví uložené parametry z jejího argumentu.

- `result_type min()`Vrátí minimální hodnotu, která je vrácena funkcí distribuce `operator()`.

- `result_type max()`Vrátí maximální hodnotu vrácenou distribucí `operator()`. Když `result_type` je celočíselný typ (s celočíselnou hodnotou) `max()` , je maximální hodnota, která může být vrácena (včetně); když `result_type` je typ s plovoucí desetinnou čárkou (s hodnotou reálné `max()` hodnoty), je nejmenší hodnota větší než všechny hodnoty. To může být vráceno (Nezahrnuto).

- `void reset()`zahodí všechny hodnoty uložené v mezipaměti, takže výsledek dalšího volání `operator()` není závislý na všech hodnotách získaných z modulu před voláním.

Struktura parametru je objekt, který ukládá všechny parametry potřebné pro distribuci. Obsahuje:

- `typedef``distribution-type` ,což`distribution_type`je typ jeho distribuce.

- Jeden nebo více konstruktorů, které přijímají stejné seznamy parametrů jako konstruktory distribuce.

- Stejné funkce přístupu k parametrům jako distribuce.

- Operátory porovnání rovnosti a nerovnosti.

Další informace najdete v části referenční témata pod tímto článkem, která jsou propojená dříve v tomto článku.

## <a name="comments"></a>Mark

V aplikaci Visual Studio jsou dva vysoce užitečné URNGs –`mt19937` a `random_device`, jak je znázorněno v této srovnávací tabulce:

|URNG|Světl|Kryptografie – Secure|S vyplněnými daty|Deterministický|
|----------|-----------|---------------------|---------------|--------------------|
|`mt19937`|Ano|Ne|Ano|Ano<sup>*</sup>|
|`random_device`|Ne|Ano|Ne|Ne|

<sup>* Pokud je k dispozici se známým osivem.</sup>

I když standard C++ ISO nemusí `random_device` být kryptograficky zabezpečený, je v aplikaci Visual Studio implementována kryptograficky zabezpečena. (Pojem "kryptograficky zabezpečený" nezahrnuje záruky, ale odkazuje na minimální úroveň entropie, a proto úroveň předvídatelnosti, která poskytuje daný algoritmus náhodnosti. Další informace najdete v článku Wikipedii [Generátor pseudonáhodných čísel kryptograficky zabezpečený](https://go.microsoft.com/fwlink/p/?linkid=398017).) Vzhledem k tomu C++ , že standard ISO to nevyžaduje, můžou jiné platformy `random_device` implementovat jednoduchý generátor náhodných čísel (bez kryptografického zabezpečení) a můžou být vhodné jenom jako zdroj počátečních hodnot pro jiný generátor. Podívejte se na dokumentaci pro tyto platformy při `random_device` použití kódu pro různé platformy.

Podle definice `random_device` nejsou výsledky reprodukovatelné a vedlejším účinkem je, že může běžet výrazně pomaleji než jiné URNGs. Většina aplikací, které nejsou nutné pro kryptograficky zabezpečené použití `mt19937` nebo podobný modul, i když je vhodné je naplnit `random_device`voláním, jak je znázorněno v [příkladu kódu](#code).

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
