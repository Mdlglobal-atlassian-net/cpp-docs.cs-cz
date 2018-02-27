---
title: "&lt;náhodné&gt; | Microsoft Docs"
ms.custom: 
ms.date: 08/24/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <random>
dev_langs:
- C++
helpviewer_keywords:
- random header
ms.assetid: 60afc25c-b162-4811-97c1-1b65398d4c57
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af48357ff276df90333d066cf6585a031b572914
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltrandomgt"></a>&lt;Náhodné&gt;
Definuje zařízení pro náhodné generování čísel, umožňující vytvoření jednotně distribuované náhodných čísel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <random>  
```  
  
## <a name="summary"></a>Souhrn  
 A *generátoru náhodných čísel* je objekt, který vytváří pořadí pseudonáhodného hodnot. Je generátor, která vytváří hodnoty, které jsou rovnoměrně rozložen v zadaném rozsahu *Uniform náhodné číslo generátor* (URNG). Šablony třídy slouží jako URNG se označuje jako *modul* Pokud třídy obsahuje některé běžné vlastnosti, které jsou popsány dále v tomto článku. Může být URNG – a většinou je – v kombinaci s *distribuční* pomocí předání URNG jako argument distribuční `operator()` k vytvoření hodnoty, které jsou distribuovány způsobem, který je definován rozdělení.  
  
 Tyto odkazy přejít na hlavní části v tomto článku:  
  
- [Příklady](#code)  
  
- [Seznam seřazený podle kategorií](#listing)  
  
- [Moduly a distribuce](#engdist)  
  
- [Poznámky](#comments)  
  
### <a name="quick-tips"></a>Rychlé tipy  
 Zde jsou některé tipy třeba vzít v úvahu při použití `<random>`:  
  
-   Pro většinu účelů vytvořit URNGs nezpracovaná bitů, které musí být ve tvaru podle distribuce. (Upozorňují na důležité výjimkou je [std::shuffle()](../standard-library/algorithm-functions.md#shuffle) protože přímo používá URNG.)  
  
-   Existenci jediné instance URNG nebo distribuční nelze bezpečně volat souběžně spustili URNG nebo distribuce je změny operaci. Další informace najdete v tématu [bezpečný přístup z více vláken ve standardní knihovna C++](../standard-library/thread-safety-in-the-cpp-standard-library.md).  
  
- [Předdefinované – definice TypeDef](#typedefs) z některé moduly jsou uvedeny; Toto je upřednostňovaný způsob, jak vytvořit URNG, pokud modul se používá.  
  
-   Nejužitečnější párování pro většinu aplikací je `mt19937` modul s `uniform_int_distribution`, jak je znázorněno [příklad kódu](#code) dále v tomto článku.  
  
 Celá řada možností zvolit v `<random>` záhlaví a kterýkoliv z nich je vhodnější zastaralé funkce C Runtime `rand()`. Informace o tom, co je problém se `rand()` a jak `<random>` řeší tyto nedostatky, najdete v části [toto video](http://go.microsoft.com/fwlink/p/?linkid=397615).  
  
##  <a name="code"></a> Příklady  
 Následující příklad kódu ukazuje, jak vygenerovat některé náhodná čísla v tomto případě pět z nich pomocí generátor vytvořené pomocí Nedeterministický počáteční hodnoty.  
  
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
  
 I když jedná se o vysoce kvalitního náhodná čísla a jiné pokaždé, když tento program běží, nejsou nemusí být v rozsahu užitečné. K řízení rozsahu, použijte rovnoměrné rozdělení, jak je znázorněno v následujícím kódu:  
  
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
  
 Další příklad kódu ukazuje realističtější sadu případy použití s jednotně distribuované generátory náhodných čísel pomíchané obsah vektor a pole.  
  
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
  
Tento kód ukazuje dva různé randomizations – náhodné vektoru celých čísel a náhodně pole indexovaná data – s funkcí šablony testu. První volání funkce testovací používá URNG kryptografických zabezpečení, Nedeterministický, není seedable, opakovatelných `random_device`. Druhý test spusťte používá `mersenne_twister_engine` jako URNG, s deterministickou konstantní seed 32-bit, což znamená, jsou opakovatelných výsledky. Třetí test spusťte semen `mersenne_twister_engine` s tím výsledkem Nedeterministický 32-bit z `random_device`. Čtvrtý testovacím běhu rozšíří na tomto pomocí [počáteční hodnoty pořadí](../standard-library/seed-seq-class.md) vyplněnou `random_device` výsledky, které efektivně poskytuje více než 32-bit Nedeterministický náhodnost (ale stále není crypto-secure). Další informace najdete v tématu na.  
  
##  <a name="listing"></a> Seznam seřazený podle kategorií  
  
###  <a name="urngs"></a> Uniform generátory náhodných čísel  
 Z hlediska tyto vlastnosti jsou často popsané URNGs:  
  
1. **Délka období**: jak velký počet iterací trvá opakování pořadí čísel vygenerovat. Delší, tím lépe.  
  
2. **Výkon**: jak rychle čísla mohou být generována a kolik paměti trvá. Menší tím lépe.  
  
3. **Kvalita**: jak blízko true náhodná čísla je generovaný pořadí. To se často označuje jako "*náhodnost*".  
  
 Následující části uvádějí uniform náhodné číslo generátory (URNGs) součástí `<random>` záhlaví.  
  
####  <a name="rd"></a> Nedeterministický generátor  
  
|||  
|-|-|  
|[random_device – třída](../standard-library/random-device-class.md)|Generuje náhodné pořadí není deterministický, kryptograficky zabezpečené pomocí externí zařízení. Obvykle používají pro počáteční hodnoty motoru. Nízký výkon, velmi vysoké kvality. Další informace najdete v tématu [poznámky](#comments).|  
  
####  <a name="typedefs"></a> Definice TypeDef modul s předdefinované parametry  
 Pro konkretizujete moduly a modul adaptéry. Další informace najdete v tématu [moduly a distribuce](#engdist).  
  
- `default_random_engine` Výchozí modul.   
 `typedef mt19937 default_random_engine;`  
  
- `knuth_b` Modul Knuth.   
 `typedef shuffle_order_engine<minstd_rand0, 256> knuth_b;`  
  
- `minstd_rand0` 1988 minimální standardní modul (Lewis, Goodman a Lukeš, 1969).   
 `typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;`  
  
- `minstd_rand` Aktualizovaný modul minimální standardní `minstd_rand0` (parku, Lukeš a Stockmeyer, 1993).   
 `typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;`  
  
- `mt19937` 32-bit Mersenne twister modul (Matsumoto a Nishimura, 1998).   
 `typedef mersenne_twister_engine<unsigned int, 32, 624, 397,      31, 0x9908b0df,      11, 0xffffffff,      7, 0x9d2c5680,      15, 0xefc60000,      18, 1812433253> mt19937;`  
  
- `mt19937_64` 64bitová verze Mersenne twister modul (Matsumoto a Nishimura 2000).   
 `typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,      31, 0xb5026f5aa96619e9ULL,      29, 0x5555555555555555ULL,      17, 0x71d67fffeda60000ULL,      37, 0xfff7eee000000000ULL,      43, 6364136223846793005ULL> mt19937_64;`  
  
- `ranlux24` 24-bit RANLUX engine (Martin Lüscher and Fred James, 1994).   
 `typedef discard_block_engine<ranlux24_base, 223, 23> ranlux24;`  
  
- `ranlux24_base` Použít jako základ pro `ranlux24`.   
 `typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`  
  
- `ranlux48` modul RANLUX 48bitové (Martin Lüscher a František James, 1994).   
 `typedef discard_block_engine<ranlux48_base, 389, 11> ranlux48;`  
  
- `ranlux48_base` Použít jako základ pro `ranlux48`.   
 `typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`  
  
####  <a name="eng"></a> Modul šablony  
 Modul šablon se používají jako samostatné URNGs nebo jako základní moduly předaný [modul adaptéry](#engadapt). Obvykle jsou vytvořena s [předdefinované modul typedef](#typedefs) a předaný [distribuční](#distributions). Další informace najdete v tématu [moduly a distribuce](#engdist) části.  
  
|||  
|-|-|  
|[linear_congruential_engine – třída](../standard-library/linear-congruential-engine-class.md)|Generuje náhodné pořadí pomocí lineární congruential algoritmu. Většina zneužívající vlastností prohlížeče a nejnižší kvality.|  
|[mersenne_twister_engine – třída](../standard-library/mersenne-twister-engine-class.md)|Generuje náhodné pořadí pomocí algoritmu twister Mersenne. Většina komplexní, a je nejvyšší kvality s výjimkou random_device – třída. Velmi vysoký výkon.|  
|[subtract_with_carry_engine – třída](../standard-library/subtract-with-carry-engine-class.md)|Generuje náhodné pořadí pomocí algoritmu subtract s carry. Zlepšení `linear_congruential_engine`, ale mnohem nižší kvality a výkonu než `mersenne_twister_engine`.|  
  
####  <a name="engadapt"></a> Modul adaptéru šablony  
 Modul adaptéry jsou šablony, které přizpůsobit další moduly (základní). Obvykle jsou vytvořena s [předdefinované modul typedef](#typedefs) a předaný [distribuční](#distributions). Další informace najdete v tématu [moduly a distribuce](#engdist) části.  
  
|||  
|-|-|  
|[discard_block_engine – třída](../standard-library/discard-block-engine-class.md)|Generuje náhodné pořadí zrušením hodnot vrácených jeho základní modul.|  
|[independent_bits_engine – třída](../standard-library/independent-bits-engine-class.md)|Generuje náhodné pořadí s zadaný počet bitů tak, že opětovné balení bits z hodnot vrácených jeho základní modul.|  
|[shuffle_order_engine – třída](../standard-library/shuffle-order-engine-class.md)|Generuje náhodné pořadí tak, že změna hodnot vrácených z jeho základní motoru.|  
  
 [[Modul šablony](#eng)]  
  
###  <a name="distributions"></a> Náhodné číslo distribuce  
 Následující části uvádějí distribuce součástí `<random>` záhlaví. Distribuce jsou následného zpracování mechanismus, obvykle pomocí URNG výstup jako vstup a výstup distribuci funkcí definovaných statistické hustoty pravděpodobnosti. Další informace najdete v tématu [moduly a distribuce](#engdist) části.  
  
#### <a name="uniform-distributions"></a>Uniform distribuce  
  
|||  
|-|-|  
|[uniform_int_distribution – třída](../standard-library/uniform-int-distribution-class.md)|Vytvoří distribuční uniform celočíselná hodnota v rozsahu v intervalu uzavřeno \[a, b] (inkluzivně inkluzivní).|  
|[uniform_real_distribution – třída](../standard-library/uniform-real-distribution-class.md)|Vytvoří uniform reálné distribuce (s plovoucí desetinnou čárkou) hodnotu mezi rozsahem v intervalu napůl otevřených [a b) (včetně výhradně).|  
|[generate_canonical](../standard-library/random-functions.md#generate_canonical)|Vytvoří rovnoměrné rozdělení real (plovoucí desetinnou čárkou) hodnoty dané přesnost napříč [0, 1) (včetně výhradně).|  
  
 [[Náhodné číslo distribuce](#distributions)]  
  
#### <a name="bernoulli-distributions"></a>Bernoulliho distribuce  
  
|||  
|-|-|  
|[bernoulli_distribution – třída](../standard-library/bernoulli-distribution-class.md)|Vytvoří Bernoulliho distribuce `bool` hodnoty.|  
|[binomial_distribution – třída](../standard-library/binomial-distribution-class.md)|Vytvoří binomické rozdělení hodnot celé číslo.|  
|[geometric_distribution – třída](../standard-library/geometric-distribution-class.md)|Vyprodukuje geometrické distribuce celočíselné hodnoty.|  
|[negative_binomial_distribution – třída](../standard-library/negative-binomial-distribution-class.md)|Vytvoří negativní binomické rozdělení hodnot celé číslo.|  
  
 [[Náhodné číslo distribuce](#distributions)]  
  
#### <a name="normal-distributions"></a>Normální distribuce  
  
|||  
|-|-|  
|[cauchy_distribution – třída](../standard-library/cauchy-distribution-class.md)|Vytvoří distribuční Cauchy hodnot real (plovoucí desetinnou čárkou).|  
|[chi_squared_distribution – třída](../standard-library/chi-squared-distribution-class.md)|Vytvoří rozdělení chí-kvadrát hodnot real (plovoucí desetinnou čárkou).|  
|[fisher_f_distribution – třída](../standard-library/fisher-f-distribution-class.md)|Vytvoří jako F-distribučního (také označované jako na Snedecor F distribuční nebo distribuce Fisherovy Snedecor) hodnot real (plovoucí desetinnou čárkou).|  
|[lognormal_distribution – třída](../standard-library/lognormal-distribution-class.md)|Vytvoří protokolu normálního rozdělení hodnot real (plovoucí desetinnou čárkou).|  
|[normal_distribution – třída](../standard-library/normal-distribution-class.md)|Vytvoří normální (Gaussovské) distribuční hodnot real (plovoucí desetinnou čárkou).|  
|[student_t_distribution – třída](../standard-library/student-t-distribution-class.md)|Vytvoří Studentova *t*-distribuční hodnot real (plovoucí desetinnou čárkou).|  
  
 [[Náhodné číslo distribuce](#distributions)]  
  
#### <a name="poisson-distributions"></a>Distribuce Poissonovo rozdělení  
  
|||  
|-|-|  
|[exponential_distribution – třída](../standard-library/exponential-distribution-class.md)|Vytvoří exponenciální rozdělení hodnot real (plovoucí desetinnou čárkou).|  
|[extreme_value_distribution – třída](../standard-library/extreme-value-distribution-class.md)|Vytvoří jako distribučního krajní hodnotu hodnot real (plovoucí desetinnou čárkou).|  
|[gamma_distribution – třída](../standard-library/gamma-distribution-class.md)|Vytvoří gama rozdělení hodnot real (plovoucí desetinnou čárkou).|  
|[poisson_distribution – třída](../standard-library/poisson-distribution-class.md)|Vytvoří hodnotu Poissonovo rozdělení hodnot celé číslo.|  
|[weibull_distribution – třída](../standard-library/weibull-distribution-class.md)|Vytvoří distribuční Weibullova hodnot real (plovoucí desetinnou čárkou).|  
  
 [[Náhodné číslo distribuce](#distributions)]  
  
#### <a name="sampling-distributions"></a>Distribuce vzorkování  
  
|||  
|-|-|  
|[discrete_distribution – třída](../standard-library/discrete-distribution-class.md)|Vytvoří distribuční diskrétní celé číslo.|  
|[piecewise_constant_distribution – třída](../standard-library/piecewise-constant-distribution-class.md)|Vytváří piecewise konstantní distribuční hodnot real (plovoucí desetinnou čárkou).|  
|[piecewise_linear_distribution – třída](../standard-library/piecewise-linear-distribution-class.md)|Vytváří piecewise lineární distribuční hodnot real (plovoucí desetinnou čárkou).|  
  
 [[Náhodné číslo distribuce](#distributions)]  
  
### <a name="utility-functions"></a>Pomocné funkce  
 Tato část obsahuje seznam funkcí obecné nástroje, které jsou součástí `<random>` záhlaví.  
  
|||  
|-|-|  
|[seed_seq – třída](../standard-library/seed-seq-class.md)|Generuje pořadí-tendenční kódované počáteční hodnoty. Umožňuje vyhnout replikace náhodných variate datových proudů. To užitečné, pokud instance mnoho URNGs z webů.|  
  
### <a name="operators"></a>Operátory  
 Operátory uvedené v této části je uveden seznam `<random>` záhlaví.  
  
|||  
|-|-|  
|`operator==`|Ověřuje, zda URNG na levé straně operátoru rovná modul na pravé straně.|  
|`operator!=`|Ověřuje, zda URNG na levé straně operátor není rovno modul na pravé straně.|  
|`operator<<`|Zapíše informace o stavu do datového proudu.|  
|`operator>>`|Extrahuje informace o stavu z datového proudu.|  
  
##  <a name="engdist"></a> Moduly a distribuce  
 Informace o každé z těchto kategorií třída šablony definovaný v následujících částech `<random>`. Jak z těchto kategorií šablonu – třída typu jako argument a používat názvy parametrů šablony sdílené k popisu vlastnosti typu, které jsou povoleny jako typ skutečné argument následujícím způsobem:  
  
- `IntType` označuje `short`, `int`, `long`, `long long`, `unsigned short`, `unsigned int`, `unsigned long`, nebo `unsigned long long`.  
  
- `UIntType` označuje `unsigned short`, `unsigned int`, `unsigned long`, nebo `unsigned long long`.  
  
- `RealType` označuje `float`, `double`, nebo `long double`.  
  
### <a name="engines"></a>Moduly  
 [Modul šablony](#eng) a [modul adaptéru šablony](#engadapt) jsou šablony, jejíž parametry přizpůsobit generátor vytvořili.  
  
 *Modul* třídu nebo šablony třídy, jejichž instance (generátory) fungovat jako zdroj náhodných čísel jednotně rozděluje mezi minimální a maximální hodnotou. *Modul adaptéru* přináší pořadí hodnot, které mají různé náhodnost vlastnosti hodnoty trvá vyprodukované náhodné číslo modul a použití algoritmu určitého druhu na tyto hodnoty.  
  
 Každý modul a modul adaptéru má následující členy:  
  
- `typedef` `numeric-type` `result_type` je typ, který se vrátí po použití generátoru `operator()`. `numeric-type` Se předá jako parametr šablony při vytváření instance.  
  
- `result_type operator()` Vrátí hodnoty, které jsou rovnoměrně mezi `min()` a `max()`.  
  
- `result_type min()` Vrátí minimální hodnotu, která se vrátí po použití generátoru `operator()`. Modul adaptéry používají základní modul `min()` výsledek.  
  
- `result_type max()` Vrátí maximální hodnotu, která se vrátí po použití generátoru `operator()`. Když `result_type` integrální (celé číslo s hodnotou) typu, `max()` je maximální hodnota, která lze ve skutečnosti vrátit (včetně); při `result_type` s plovoucí desetinnou čárkou (vracející reálné) typu `max()` je nejmenší hodnota větší než všechny hodnoty která se může vracet (bez – včetně). Modul adaptéry používají základní modul `max()` výsledek.  
  
- `void seed(result_type s)` doplňuje generátor s počáteční hodnotou `s`. Pro moduly, podpis je `void seed(result_type s = default_seed)` pro podpora výchozích parametrů (adaptéry modul definovat samostatné `void seed()`, najdete v části Další část).  
  
- `template <class Seq> void seed(Seq& q)` doplňuje generátor pomocí [seed_seq](../standard-library/seed-seq-class.md)`Seq`.  
  
-   Explicitní konstruktor s argumentem `result_type x` vytvářející generátor nasadí, jako kdyby pomocí volání metody `seed(x)`.  
  
-   Explicitní konstruktor s argumentem `seed_seq& seq` vytvářející generátor nasadí, jako kdyby pomocí volání metody `seed(seq)`.  
  
- `void discard(unsigned long long count)` efektivně volá `operator()` `count` krát a zahodí se všechny hodnoty.  
  
 **Modul adaptéry** kromě podpory těchto členů (`Engine` je první parametr šablony adaptéru modul určení základní modul typu):  
  
-   Výchozí konstruktor k chybě při inicializaci generátor jako z základní modul výchozí konstruktor.  
  
-   Explicitní konstruktor s argumentem `const Engine& eng`. Toto je pro podporu vytváření kopie použití základní stroje.  
  
-   Explicitní konstruktor s argumentem `Engine&& eng`. Toto je pro podporu vytváření přesunutí pomocí základní modul.  
  
- `void seed()` který inicializuje generátor s základní modul výchozí počáteční hodnoty.  
  
- `const Engine& base()` Vlastnost funkce, která vrátí základní modul, který byl použit k vytvoření generátor.  
  
 Každý motor udržuje *stavu* pořadí hodnot, které budou vytvořeny následující volání, která určují `operator()`. Stavy dvě generátory vytvořené z modulů stejného typu je možné porovnávat pomocí `operator==` a `operator!=`. Pokud se dva stavy porovnávat jako s rovnocennými, z nich vydá stejnou sekvenci hodnoty. Stav objektu lze uložit na datový proud jako posloupnost 32-bit nepodepsané hodnot pomocí `operator<<` generátoru. Stav není změnil uložením. Uložený stav může číst do generátor vytvořené z modul stejného typu pomocí `operator>>`.  
  
### <a name="distributions"></a>Distribuce  
 A [náhodné číslo distribuce](#distributions) je třídu nebo šablony třídy, jejichž instance transformace datového proudu jednotně distribuované náhodných čísel získané z modul do datového proudu náhodných čísel, které mají určitý distribuční. Každý distribuční má následující členy:  
  
- `typedef` `numeric-type` `result_type` je typ, který je vrácený distribuční `operator()`. `numeric-type` Se předá jako parametr šablony při vytváření instance.  
  
- `template <class URNG> result_type operator()(URNG& gen)` Vrátí hodnoty, které jsou distribuovány podle definice distribuční pomocí `gen` jako zdroj jednotně distribuované náhodných hodnot a uložená *parametry rozdělení*.  
  
- `template <class URNG> result_type operator()(URNG& gen, param_type p)` Vrátí hodnoty distribuován podle definice distribuční pomocí `gen` jako zdroj jednotně distribuované náhodných hodnot a struktura parametry `p`.  
  
- `typedef` `unspecified-type` `param_type` balíček parametry volitelně předaný `operator()` a použijí se místo uložené parametry ke generování hodnoty.  
  
-   A `const param&` konstruktor inicializuje uložené parametry z jeho argumentem.  
  
- `param_type param() const` Získá uložené parametry.  
  
- `void param(const param_type&)` Nastaví uložené parametry z jeho argumentem.  
  
- `result_type min()` Vrátí minimální hodnotu, která je vrácený distribuční `operator()`.  
  
- `result_type max()` Vrátí maximální hodnotu, která je vrácený distribuční `operator()`. Když `result_type` integrální (celé číslo s hodnotou) typu, `max()` je maximální hodnota, která lze ve skutečnosti vrátit (včetně); při `result_type` s plovoucí desetinnou čárkou (vracející reálné) typu `max()` je nejmenší hodnota větší než všechny hodnoty která se může vracet (bez – včetně).  
  
- `void reset()` zahodí všechny hodnoty v mezipaměti, aby výsledkem další volání `operator()` nezávisí na žádné hodnoty získané z modulu před voláním.  
  
 Struktura parametr je objekt, který ukládá veškeré potřebné pro distribuční parametry. Obsahuje:  
  
- `typedef` `distribution-type` `distribution_type`, což je typ jeho distribuci.  
  
-   Jeden nebo více konstruktory, které provést stejný parametr vypíše proveďte konstruktory distribuce.  
  
-   Stejný parametr přístup funguje jako distribuční.  
  
-   Operátory porovnání rovnosti a nerovnosti.  
  
 Další informace najdete v další části odkazu pod, propojený dříve v tomto článku.  
  
##  <a name="comments"></a> Poznámky  
 Existují dvě velmi užitečné URNGs v sadě Visual Studio –`mt19937` a `random_device`– jak je znázorněno v této tabulce porovnání:  
  
|URNG|Rychlý|Crypto-secure|Seedable|Deterministické|  
|----------|-----------|---------------------|---------------|--------------------|  
|`mt19937`|Ano|Ne|Ano|Ano<sup>*</sup>|  
|`random_device`|Ne|Ano|Ne|Ne|  
  
 <sup>* Pokud je zadaný s známé počáteční hodnoty.</sup>  
  
 I když standardní C++ ISO nevyžaduje `random_device` být kryptograficky zabezpečené, v sadě Visual Studio jsou implementované jako kryptograficky zabezpečené. (Termín "kryptograficky zabezpečené" neznamená záruky, ale odkazuje na minimální úroveň entropie – a tedy úroveň předvídatelnost – poskytuje daný náhodného přeskupování algoritmus. Další informace najdete v článku Wikipedia [kryptograficky zabezpečené generování pseudonáhodných čísel](http://go.microsoft.com/fwlink/p/?linkid=398017).) Vzhledem k tomu, že na Standard C++ ISO nevyžaduje to, může implementovat jiné platformy `random_device` jako jednoduchý pseudonáhodného generátoru čísel (není bezpečné kryptograficky) a pouze může být vhodné jako zdroj počáteční hodnoty pro jiný generátor. Podívejte se do dokumentace pro tyto platformy při použití `random_device` v kódu napříč platformami.  
  
 Podle definice `random_device` nejsou reprodukovatelné výsledky a vedlejším účinkem je, že může výrazně pomalejší než ostatní URNGs spustit. Většina aplikací, které nemusejí být kryptograficky zabezpečené pomocí `mt19937` nebo podobná modul, i když můžete chtít počáteční hodnoty ho pomocí volání `random_device`, jak je znázorněno [příklad kódu](#code).  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)

