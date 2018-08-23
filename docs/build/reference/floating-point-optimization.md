---
title: Microsoft Visual C++ plovoucí desetinnou čárkou optimalizace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 082cd3a7721f1bc72899130159b724b292e5e217
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595045"
---
# <a name="microsoft-visual-c-floating-point-optimization"></a>Microsoft Visual C++ s plovoucí desetinnou čárkou optimalizace

Získejte popisovač pro optimalizaci plovoucí desetinné čárky kód pomocí kompilátoru Microsoft C++ způsob správy sémantiku plovoucí desetinné čárky. Vytvoření rychlé programy přitom zajistit, aby byly provedeny pouze bezpečné optimalizace plovoucí desetinné čárky kód.

## <a name="optimization-of-floating-point-code-in-c"></a>Optimalizace plovoucí desetinné čárky kód v jazyce C++

Optimalizující kompilátor C++ nejen převádí zdrojový kód do strojového kódu, uspořádá strojové instrukce v takovým způsobem zvýšit efektivitu a/nebo zmenšete velikost. Mnoho běžných optimalizace bohužel nejsou nutně bezpečné, při použití u výpočtů s plovoucí desetinnou čárkou. Vhodným Příkladem takových uvidíte následující algoritmus sčítání z David Goldberg, "Co každých počítači mezi odborníky přes by měl vědět o aritmetiku", *computingu zjišťování*, 1991 dne, pg. 203:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0, C=0, Y, T;
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = T;
   }
   return sum;
}
```

Tato funkce přidává n **float** hodnoty ve vektoru pole `A`. V těle smyčky algoritmus vypočítává "opravy" hodnotu, která se pak použije k dalšímu kroku souhrn. Tato metoda výrazně snižuje kumulativní zaokrouhlovací chyby než jednoduchý souhrn, při zachování O(n) čas složitost.

Kompilátor C++ naivní předpokládat, že aritmetické operace s plovoucí desetinnou čárkou následuje algebraických stejná pravidla jako aritmetický reálné číslo. Takový kompilátor může poté chybně uzavřít, který

> C = T - součet - Y == > (součet + Y) - součet - Y == > 0;

To znamená, že zjištěné hodnota c je vždy nulovou konstantou. Tato konstanta je pak šířený do dalších výrazů, tělo smyčky se sníží jednoduchý souhrn. Abychom byli přesní,

> Y = [i] - C == > Y = [i]<br/>T = sum + Y == > T = sum + [i]<br/>Součet = T == > součet = sum + [i]

Proto pro kompilátor naivní logické transformace `KahanSum` by byla funkce:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0; // C, Y & T are now unused
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

I když transformovaný algoritmus je rychlejší, *je vůbec přesnou reprezentací programátora záměr*. Oprava chyb pečlivě vytvořený úplně odebrala a jsme už zbývá algoritmus sčítání jednoduchý, s přímým přístupem s všechny související chyby.

Samozřejmě sofistikované kompilátor C++ by vědět, že algebraických pravidla z reálného aritmetické operace se nevztahují obecně aritmetické operace s plovoucí desetinnou čárkou. Však interpretace i propracované kompilátor C++ stále nesprávně programátora záměr.

Vezměte v úvahu běžné optimalizace, která se pokusí uchovávat tolik hodnoty v registrech nejvíce (nazývané "enregistering" hodnotu). V `KahanSum` například tato optimalizace se můžou pokusit zaregistrace proměnné `C`, `Y` a `T` vzhledem k tomu slouží jenom v těle smyčky. Pokud registrace přesnost je 52bits (double) namísto 23bits (single), tyto optimalizace efektivně typ podporuje `C`, `Y` a `T` na typ **double**. Pokud součet proměnná není rovněž uloženy v registrech procesoru, bude se dál kódovaný v a jednoduchou přesností. To transformuje sémantika `KahanSum` následující

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0;
   double C=0, Y, T; // now held in-register
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = (float) T;
   }
   return sum;
}
```

I když `Y`, `T` a `C` se nyní zpracovávají na vyšší přesnost toto nové kódování může vytvořit méně přesné výsledky v závislosti na hodnotách v `A[]`. I zdánlivě neškodné optimalizace může mít negativní důsledky.

Tyto druhy problémů optimalizace nejsou omezené na "složité" kód s plovoucí desetinnou čárkou. Dokonce i jednoduchý algoritmy s plovoucí desetinnou čárkou může selhat při optimalizaci nesprávně. Vezměte v úvahu jednoduché, souhrn přímo algoritmus:

```cpp
float Sum( const float A[], int n )
{
   float sum=0;
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

Protože některé jednotek s plovoucí desetinnou čárkou jsou schopny současně provádí více operací, kompilátor zvolit zapojení optimalizace snížení skaláru. Tato optimalizace efektivně transformuje jednoduchou funkci Sum výše na následující:

```cpp
float Sum( const float A[], int n )
{
   int n4 = n-n%4; // or n4=n4&(~3)
   int i;
   float sum=0, sum1=0, sum2=0, sum3=0;
   for (i=0; i<n4; i+=4)
   {
      sum = sum + A[i];
      sum1 = sum1 + A[i+1];
      sum2 = sum2 + A[i+2];
      sum3 = sum3 + A[i+3];
   }
   sum = sum + sum1 + sum2 + sum3;
   for (; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

Funkce teď udržuje čtyři samostatné panelu, které lze současně zpracovávat v každém kroku. I když optimalizovaného funkce je teď mnohem rychlejší, může být poměrně liší od výsledků neoptimalizované optimalizované výsledky. Při provádění této změny, kompilátor předpokládá, že asociativní s plovoucí desetinnou čárkou přidání; To znamená že těchto dvou výrazů jsou ekvivalentní: `(a + b) + c == a + (b + c)`. Ale asociativity vždy neobsahuje hodnotu true pro čísla s plovoucí desetinnou čárkou. Místo computingu součtem jako:

```cpp
sum = A[0]+A[1]+A[2]+...+A[n-1];
```

transformovaný funkce nyní vypočítá výsledek jako

```cpp
sum = (A[0]+A[4]+A[8]+...)
    + (A[1]+A[5]+A[9]+...)
    + (A[2]+A[6]+A[10]+...)
    + (A[3]+A[7]+A[11]+...);
```

Pro některé hodnoty `A[]`, tento různé řazení operace sčítání může vést k neočekávaným výsledkům. Další zpracovávaný, někteří programátoři můžete předvídat tyto optimalizace a jako kompenzaci za je odpovídajícím způsobem. V takovém případě program můžete vytvořit pole `A` v jiném pořadí tak, aby součet optimalizované vytváří očekávané výsledky. Kromě toho může být v mnoha případech nemusí být optimalizované výsledek "dostatečně blízko". To platí zejména při optimalizaci výhody poutavé rychlost. Videohry, například vyžadovat jako nejvíce mnohem rychlejší, ale nevyžadují často s velmi přesnými výpočtů s plovoucí desetinnou čárkou. Tvůrci kompilátoru musí proto poskytují mechanismus pro programátory řídit často různorodými cíle rychlost a přesnost.

Některé kompilátory vyřešit tím, že poskytuje samostatné přepínač pro každý typ optimalizace kompromis mezi rychlostí a přesností. To umožňuje vývojářům zakázat optimalizace, které způsobují změny přesnost s plovoucí desetinnou čárkou pro jejich konkrétní aplikaci. Když toto řešení může nabízí vysoký stupeň kontroly nad kompilátor, zavádí několik dalších problémů:

- Je často nejasné, který přepne k povolení nebo zakázání.
- Zakázání optimalizace jedné může nepříznivě ovlivnit výkon kódu bez s plovoucí desetinnou čárkou.
- Každý další přepínače s sebou nese náklady mnoho nový přepínač kombinací; počet kombinací rychle nepraktický.

Proto při poskytování oddělenými přepínači pro každý optimalizace se může zdát přitažlivými, pomocí těchto kompilátory může být náročné a nespolehlivé.

Nabízí mnoho kompilátorů jazyka C++ *konzistence* s plovoucí desetinnou čárkou modelu (prostřednictvím **/Op** nebo **/fltconsistency** přepnout) umožňující vývojářům vytváření programů kompatibilní s striktní sémantiku plovoucí desetinné čárky. Když zapojení, tento model zabrání kompilátor pomocí většiny optimalizací na výpočtů s plovoucí desetinnou čárkou zároveň umožní tyto optimalizace kódu bez neplovoucí desetinnou čárkou. Model pro zajištění konzistence, má ale tmavý straně. Aby mohla vrátit předvídatelné výsledky v různých architekturách FPU, téměř všechny implementace **/Op** round přechodných výrazů pro uživatele Zadaná přesnost; Zvažte například následující výraz:

```cpp
float a, b, c, d, e;
// . . .
a = b * c + d * e;
```

Aby bylo možné vytvořit konzistentní a opakovatelné výsledky v rámci **/Op**, získá tento výraz vyhodnocen jako kdyby byly implementován takto:

```cpp
float x = b  *c;
float y = d * e;
a = x + y;
```

Konečný výsledek nyní vykazuje chyby zaokrouhlení jednoduchou přesností *v každém kroku při vyhodnocování výrazu*. I když se toto vyhodnocení nedojde k narušení výhradně všechna pravidla sémantiku C++, je téměř nikdy nejlepší způsob, jak vyhodnocení výrazů s plovoucí desetinnou čárkou. Je obecně lepší pro výpočet mezilehlých výsledků v vysoká přesnost je praktické. Například by bylo lepší pro výpočet výraz `a = b * c + d * e` vyšší přesnost jako v

```cpp
double x = b * c;
double y = d * e;
double z = x + y;
a = (float)z;
```

nebo ještě lépe

```cpp
long double x = b * c;
long double y = d * e
long double z = x + y;
a = (float)z;
```

Při výpočtu mezilehlých výsledků v vyšší přesnost, konečný výsledek je výrazně přesnější. Přijetím modelu konzistence se ironically, pravděpodobnost chyby zvýší, přesně, když uživatel se snaží snížit chyby zakázáním optimalizací unsafe. Proto modelu konzistence může vážně snížit efektivitu při současném poskytování neposkytujeme záruku její vyšší přesnost. Závažné číselné programátorům nebude jevit jako velmi dobré kompromis a je primárním důvodem, proč modelu není obecně dobře přijímání.

Od verze 8.0 (Visual C++ 2005®), Microsoft C++ kompilátor poskytuje mnohem lepší alternativou. Umožňuje programátorům vyberte jednu ze tří režimů obecné s plovoucí desetinnou čárkou: fp: precise, FP: Fast a fp: strict.

- V části fp: precise, pouze bezpečné optimalizace se provádí na kód s plovoucí desetinnou čárkou a na rozdíl od **/Op**, zprostředkující výpočty probíhají konzistentně na nejvyšší praktické přesnosti.
- režim FP: Fast zmírňuje umožňující agresivnější optimalizace ovšem na úkor přesnosti s plovoucí desetinnou čárkou pravidla.
- FP: strict režim poskytuje obecné správnost fp: precise při povolení sémantiku fp výjimky a brání nedovolenému transformace za přítomnosti FPU prostředí změny (např. změny do registru přesnost, zaokrouhlení směrem atd).

Sémantiku výjimky s plovoucí desetinnou čárkou mohou být řízena nezávisle na sobě přepínač příkazového řádku nebo pragma kompilátoru; ve výchozím nastavení, jsou zakázané sémantiku výjimky s plovoucí desetinnou čárkou v rámci fp: precise a povolený v části fp: strict. Kompilátor poskytuje také řídit FPU prostředí citlivosti a některé konkrétní optimalizace s plovoucí desetinnou čárkou, jako je například staženiny. Tento model přímočaré vývojářům poskytuje značnou míru kontroly nad kompilace kód s plovoucí desetinnou čárkou bez režie příliš mnoho přepínače kompilátoru nebo potenciálního zákazníka nežádoucí vedlejší účinky.

## <a name="the-fpprecise-mode-for-floating-point-semantics"></a>Fp: precise režim pro sémantiku plovoucí desetinné čárky

Výchozí režim sémantiku plovoucí desetinné čárky je fp: precise. Vyberete tento režim kompilátoru výhradně používá sadu pravidel bezpečnosti při optimalizaci operací s plovoucí desetinnou čárkou. Tato pravidla povolení kompilátoru generovat efektivní strojového kódu při zachování přesnost výpočtů s plovoucí desetinnou čárkou. Pro usnadnění výrobní rychlé programy, fp: precise modelu zakáže sémantiku výjimky s plovoucí desetinnou čárkou (i když se může být explicitně povolené). Microsoft má vybraný fp: precise jako výchozí režim s plovoucí desetinnou čárkou, protože tak vzniká rychlé a přesné programy.

Explicitně požádat o fp: precise režimu pomocí kompilátoru příkazového řádku, použijte [/FP: precise](fp-specify-floating-point-behavior.md) přepnout:

> cl/FP: precise source.cpp

Toto dá pokyn kompilátoru, aby použil fp: precise sémantiku při generování kódu pro soubor source.cpp. Fp: precise modelu může být vyvoláno také na jednotlivých podle funkcí pomocí [float_control – Direktiva pragma kompilátoru](#the-float-control-pragma).

V části fp: precise režimu, kompilátor nikdy provádí žádné optimalizace, které perturb přesnost výpočtů s plovoucí desetinnou čárkou. Kompilátor bude správně zaokrouhlovat vždy v přiřazení, zaokrouhlovat a volání funkcí a zprostředkujících zaokrouhlení konzistentně proběhne na stejnou přesnost jako FPU Registry. Bezpečné optimalizace, jako je například staženiny, jsou ve výchozím nastavení povolené. Ve výchozím nastavení je zakázána sémantiku výjimky a FPU prostředí citlivosti.

|FP: precise sémantiku|Vysvětlení|
|-|-|
|Zaokrouhlení sémantiku|Zaokrouhlovat explicitní zaokrouhlení na přiřazení a volání funkce. Přechodných výrazů se dá vyhodnotit za registr přesnosti.|
|Algebraický transformace|Striktní dodržování asociativní, – a distributivních algebraický s plovoucí desetinnou čárkou, pokud transformace je zaručeno, že vždy vytvářejí stejné výsledky.|
|Staženiny|Povolené ve výchozím nastavení. Další informace najdete v části [fp_contract – Direktiva pragma](#the-fp-contract-pragma).|
|Pořadí vyhodnocení s plovoucí desetinnou čárkou|Kompilátor může změnit pořadí vyhodnocování výrazů s plovoucí desetinnou čárkou, za předpokladu, že se nezmění konečných výsledků.|
|Přístup k prostředí FPU|Ve výchozím nastavení zakázané. Další informace najdete v části [– Direktiva pragma fenv_access](#the-fenv-access-pragma). Předpokládá se výchozí přesnost a režim zaokrouhlení.|
|Sémantiku výjimky s plovoucí desetinnou čárkou|Ve výchozím nastavení zakázané. Další informace najdete v tématu [/FP: except](fp-specify-floating-point-behavior.md).|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpprecise"></a>Zaokrouhlení sémantika výrazů s plovoucí desetinnou čárkou v rámci fp: precise

Fp: precise modelu provádí zprostředkující výpočtů na nejvyšší praktické přesnost, zaokrouhlení explicitně pouze v určitých bodech ve vyhodnocení výrazu. Zaokrouhlení na uživatelem zadaných přesnost vždy vyvolá se v čtyři místa: (a) při přiřazení, (b) Pokud se provádí zadání, (c) při hodnotu s plovoucí desetinnou čárkou je předán jako argument funkce a (d) Pokud je vrácená hodnota s plovoucí desetinnou čárkou funkce. Protože zprostředkující výpočty se vždy provádějí v registru přesnosti, přesnost mezilehlých výsledků je závislý na platformě (i když hodnota precision vždy být přesné jako zadaný uživatel přesnosti).

Vezměte v úvahu výraz přiřazení v následujícím kódu. Výraz na pravé straně přiřazení operátoru '=' se vypočítá v registru přesnosti a explicitně zaokrouhlí na typ levá strana příkazu přiřazení.

```cpp
float a, b, c, d;
double x;
...
x = a*b + c*d;
```

je vypočítán jako

```cpp
float a, b, c, d;
double x;
...
register tmp1 = a*b;
register tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

Explicitně zaokrouhlit přechodný výsledek, zavádí typecast. Například pokud se předchozí kód změní tak, že přidáte explicitně přetypovat, zprostředkujícího výrazu (c * d) se zaokrouhlí na typ typecast.

```cpp
float a, b, c, d;
double x;
// . . .
x = a*b + (float)(c*d);
```

je vypočítán jako

```cpp
float a, b, c, d;
double x;
// . . .
register tmp1 = a*b;
float tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

Jeden důsledkem této zaokrouhlení metody je, že některé zdánlivě ekvivalentní transformace ve skutečnosti nemají stejné sémantiky. Například následující transformace rozdělí výraz jedné přiřazení do dvou výrazů přiřazení.

```cpp
float a, b, c, d;
// . . .
a = b*(c+d);
```

je ekvivalentní k

```cpp
float a, b, c, d;
// . . .
a = c+d;
a = b*a;
```

Podobně:

```cpp
a = b*(c+d);
```

je ekvivalentní k

```cpp
a = b*(a=c+d);
```

Těchto kódováních nemají ekvivalentní sémantiku, protože druhý kódování každého zavedli operace další přiřazení, a proto další zaokrouhlení bodu.

Když se funkce vrátí hodnotu s plovoucí desetinnou čárkou, hodnota se zaokrouhlí na typ funkce. Pokud hodnotu s plovoucí desetinnou čárkou je předán jako parametr do funkce, hodnota se zaokrouhlí na typ parametru. Příklad:

```cpp
float sumsqr(float a, float b)
{
   return a*a + b*b;
}
```

je vypočítán jako

```cpp
float sumsqr(float a, float b)
{
    register tmp3 = a*a;
    register tmp4 = b*b;
    register tmp5 = tmp3+tmp4;
    return (float) tmp5;
}
```

Podobně:

```cpp
float w, x, y, z;
double c;
...
c = symsqr(w*x+y, z);
```

je vypočítán jako

```cpp
float x, y, z;
double c;
...
register tmp1 = w*x;
register tmp2 = tmp1+y;
float tmp3 = tmp2;
c = symsqr( tmp3, z);
```

### <a name="architecture-specific-rounding-under-fpprecise"></a>Specifické pro architekturu zaokrouhlení pod fp: precise

|Procesor|Zaokrouhlování přechodných výrazů přesnost|
|-|-|
|x86|Přechodných výrazů se vypočítávají na 53bitovou přesnost s rozsahem rozšířené poskytované exponent 16 bitů. Když tyto 53:16 hodnoty jsou "přesahovat" do paměti (protože může dojít během volání funkce), rozšířených exponentu rozsah se zúžit 11 bits. To znamená přesahovat hodnoty jsou přetypovat na formát standardní dvojité přesnosti s pouze 11bitový exponent.<br/>Uživatel může přepnout na rozšířené 64 bitů přesnosti pro zprostředkující zaokrouhlení změnou slovo s plovoucí desetinnou čárkou ovládacímu prvku pomocí `_controlfp` a tím, že umožňuje přístup k prostředí FPU (viz [– Direktiva pragma fenv_access](#the-fenv-access-pragma)). Ale když rozšířené přesnost register hodnoty jsou přesahovat do paměti, mezilehlých výsledků stále se zaokrouhlí na dvojitou přesností.<br/>Tento konkrétní sémantické se může změnit.|
|amd64|FP sémantiky amd64 se poněkud liší od jiných platforem. Z důvodů výkonu zprostředkující operací se vypočítávají v nejširší přesnost jeden z operandů místo v nejširší přesnosti, která je k dispozici.  Pokud chcete vynutit výpočty vypočítání větší přesností než operandy, uživatelé potřebují zavést operace přetypování na alespoň jeden operand v dílčí výraz.<br/>Tento konkrétní sémantické se může změnit.|

### <a name="algebraic-transformations-under-fpprecise"></a>Algebraický transformace v části fp: precise

Při fp: precise režim zapnutý, kompilátor provede nikdy algebraických transformace *Pokud konečný výsledek je prokazatelně identické*. Řadu známých algebraických pravidla pro aritmetické reálné číslo není vždy držitelem pro aritmetické operace s plovoucí desetinnou čárkou. Například následující výrazy jsou ekvivalentní Reals, ale ne nutně float.

|Formulář|Popis|
|-|-|
|`(a+b)+c = a+(b+c)`|Asociativní pravidlo pro přidání|
|`(a*b)*c = a*(b*c)`|Asociativní pravidlo pro násobení|
|`a*(b+c) = a*b + b*c`|Distribuce násobení přes sčítání|
|`(a+b)(a-b) = a*a-b*b`|Které budou zohledňovat algebraických|
|`a/b = a*(1/b)`|Dělení multiplicative inverzní|
|`a*1.0 = a`|Multiplikativní identity|

Jak je znázorněno v příkladu seznámení s funkcí `KahanSum`, kompilátor může zvážit provést různé algebraických transformací, abyste mohli vytvářet programy výrazně rychlejší. I když optimalizace závisí na těchto algebraických transformace jsou téměř vždy nesprávná, existují situace, které jsou zcela bezpečné. Například někdy je třeba nahradit dělení *konstantní* hodnotu s násobení hodnotou násobení inverzní konstanty:

```cpp
const double four = 4.0;
double a, b;
...

a = b/four;
```

Může se transformuje na

```cpp
const double four = 4.0;
const double tmp0 = 1/4.0;
double a, b;
...
a = b*tmp0;
```

Důvodem je bezpečné transformace, že Optimalizátor můžete určit v době kompilace, že hodnota x / 4.0 == x*(1/4.0) pro všechny hodnoty s plovoucí desetinnou čárkou z x, včetně nekonečno a NaN. Nahrazením operace dělení násobení, kompilátor může uložit několik cyklů – zejména u FPUs, které nejsou přímo implementace dělení, ale vyžadují kompilátor generovat kombinaci převrácenou hodnotu přiblížení a vynásobit přidat pokyny. Kompilátor může provést takovou optimalizaci pod fp: precise jenom v případě, že nahrazení násobení vytváří přesně stejný výsledek jako rozdělení. Kompilátor mohou také provádět jednoduché transformace v části fp: precise, pokud jsou stejné výsledky. Zde jsou některé z nich:

|Formulář|Popis
|-|-|
|`(a+b) == (b+a)`|Komutativní pravidlo pro přidání|
|`(a*b) == (b*a)`|Komutativní pravidlo pro násobení|
|`1.0*x*y == x*1.0*y == x*y*1.0 == x*y`|Násobení hodnotou 1,0|
|`x/1.0*y == x*y/1.0 == x*y`|Dělení hodnotou 1,0|
|`2.0*x == x+x`|Násobení hodnotou 2.0|

### <a name="contractions-under-fpprecise"></a>Staženiny pod fp: precise

Klíčovou funkcí architektury mnoho moderní jednotek s plovoucí desetinnou čárkou je schopnost provádět násobení, za nímž následuje doplněk jako jednu operaci s žádná chyba zprostředkující zaokrouhlení. Třeba společnosti Intel Itanium architekturu poskytuje pokyny pro každou z těchto operací Ternární zkombinovat (*b + c), (* b-c) a (c-a * b), do jednoho instrukcí s plovoucí desetinnou čárkou (fma, fms a fnma v uvedeném pořadí). Tyto instrukce s jednoduchou jsou rychlejší než provádění samostatné násobit a přidat pokyny a jsou přesnější, protože neexistuje žádný zprostředkující zaokrouhlení tohoto produktu. Tato optimalizace můžete výrazně zrychlit funkce obsahující několik prokládané násobit a přidat operace. Představte si třeba následující algoritmus, který vypočítá součin dvou vektorů n rozměrný.

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

Tento výpočet lze provést řadu vynásobit přidat pokyny ve formátu p = p + x [i] * y [i].

Rozpor mezi optimalizace je možné řídit nezávisle na sobě, pomocí `fp_contract` – Direktiva pragma kompilátoru. Ve výchozím nastavení fp: precise model umožňuje staženiny protože pomáhají zvýšit přesnost a rychlost. V části fp: precise, kompilátor nikdy smlouvě výraz s explicitní zaokrouhlení.
Příklady

```cpp
float a, b, c, d, e, t;
...
d = a*b + c;         // may be contracted
d += a*b;            // may be contracted
d = a*b + e*d;       // may be contracted into a mult followed by a mult-add
etc...

d = (float)a*b + c;  // won't be contracted because of explicit rounding

t = a*b;             // (this assignment rounds a*b to float)
d = t + c;           // won't be contracted because of rounding of a*b
```

### <a name="order-of-floating-point-expression-evaluation-under-fpprecise"></a>Pořadí vyhodnocení výrazů s plovoucí desetinnou čárkou v rámci fp: precise

Optimalizace, které se zachovat pořadí vyhodnocování výrazů s plovoucí desetinnou čárkou jsou vždy bezpečné a jsou proto povoleném fp: precise režimu. Vezměte v úvahu následující funkci, která vypočítá součin dvou vektorů n rozměrný v a jednoduchou přesností. První blok kódu níže původní funkce jako může být zakódován programátor, postupuje podle stejné funkce po částečné rozvinutí smyčky optimalizaci.

```cpp
//original function
float dotProduct( float x[], float y[], int n )
{
   float p=0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}

//after a partial loop-unrolling
float dotProduct( float x[], float y[], int n )
{
   int n4= n/4*4; // or n4=n&(~3);
   float p=0;
   int i;

   for (i=0; i<n4; i+=4)
   {
      p+=x[i]*y[i];
      p+=x[i+1]*y[i+1];
      p+=x[i+2]*y[i+2];
      p+=x[i+3]*y[i+3];
   }

   // last n%4 elements
   for (; i<n; i++)
      p+=x[i]*y[i];

   return p;
}
```

Hlavní výhodou této optimalizace je, že ji snižuje počet podmíněného větvení smyčky co 75 %. Zvýšením počtu operací v těle smyčky, kompilátor může nyní mít také další příležitosti k optimalizaci dále. Například může být některé FPUs může provádět vynásobit přidat v p += x [i] * y [i] při načítání současně hodnoty x [i + 1] a y [i + 1] pro použití v dalším kroku. Tento typ optimalizace je zcela bezpečné pro přístup z výpočtů s plovoucí desetinnou čárkou, vzhledem k tomu zachovává pořadí operací.

Často je výhodné pro kompilátor přeuspořádat celé operace. aby bylo možné vytvářet kód rychleji. Vezměte v úvahu následující kód:

```cpp
double a, b, c, d;
double x, y, z;
...
x = a*a*a + b*b*b + c*c*c;
...
y = a*a + b*b + c*c;
...
z = a + b + c;
```

Sémantické pravidel C++ označují, že program mohou být vráceny výsledky jako by se nejprve vypočítané x, potom y a nakonec. Předpokládejme, že kompilátor má pouze čtyři registry k dispozici s plovoucí desetinnou čárkou. Pokud kompilátor musí vypočítat x, y a v pořadí, rozhodnout pro generování kódu s tuto sémantiku:

```cpp
double a, b, c, d;
double x, y, z;
register r0, r1, r2, r3;
...
// Compute x
r0 = a;         // r1 = a*a*a
r1 = r0*r0;
r1 = r1*r0;
r0 = b;         // r2 = b*b*b
r2 = r0*r0;
r2 = r2*r0;
r0 = c;         // r3 = c*c*c
r3 = r0*r0;
r3 = r3*r0;
r0 = r1 + r2;
r0 = r0 + r3;
x = r0;         // x = r1+r2+r3
// . . .
// Compute y
r0 = a;         // r1 = a*a
r1 = r0*r0;
r0 = b;         // r2 = b*b
r2 = r0*r0;
r0 = c;         // r3 = c*c
r3 = r0*r0;
r0 = r1 + r2;
r0 = r0 + r3;
y = r0;         // y = r1+r2+r3
// . . .
// Compute z
r1 = a;
r2 = b;
r3 = c;
r0 = r1 + r2;
r0 = r0 + r3;
z = r0;         // z = r1+r2+r3
```

Existuje několik jasně redundantní operací se toto kódování. Pokud kompilátor výhradně dodržuje pravidla sémantického jazyka C++, úpravě tohoto pořadí je nezbytné, protože program může být přístup k FPU prostředí mezi každé přiřazení. Však výchozí nastavení pro fp: precise povolit, aby kompilátor optimalizoval jakoby program nemá přístup k prostředí, což umožňuje změnit pořadí těchto výrazů. Pak je můžete odebrat propouštění výpočtem tří hodnot v obráceném pořadí, následujícím způsobem:

```cpp
double a, b, c, d;
double x, y, z;
register r0, r1, r2, r3;
...
// Compute z
r1 = a;
r2 = b;
r3 = c;
r0 = r1+r2;
r0 = r0+r3;
z = r0;
...
// Compute y
r1 = r1*r1;
r2 = r2*r2;
r3 = r3*r3;
r0 = r1+r2;
r0 = r0+r3;
y = r0;
...
// Compute x
r0 = a;
r1 = r1*r0;
r0 = b;
r2 = r2*r0;
r0 = c;
r3 = r3*r0;
r0 = r1+r2;
r0 = r0+r3;
x = r0;
```

Toto kódování je jasně vynikající s téměř 40 % snížení počtu fp instrukcí. Výsledky pro x, y a jsou stejné jako předtím, ale vypočítanou méně režie.

V části fp: precise, kompilátor může také *prokládání* běžné dílčí výrazy tak, aby vytvářet kód rychleji. Například kód pro výpočet kořeny kvadratické rovnice může být napsán takto:

```cpp
double a, b, c, root0, root1;
...
root0 = (-b + sqrt(b*b-4*a*c))/(2*a);
root1 = (-b - sqrt(b*b-4*a*c))/(2*a);
```

I když tyto výrazy se liší pouze v rámci jedné operace, programátor může mít jej tímto způsobem zajistit, že každá hodnota kořenové se vypočítá na nejvyšší praktické přesnost. V části fp: precise, kompilátoru je umožněno prokládání výpočtu root0 a root1 odebrat běžné dílčí výrazy bez ztráty přesnosti. Například následující odebrala několik redundantní kroky při vytváření přesně stejnou odpověď.

```cpp
double a, b, c, root0, root1;
...
register tmp0 = -b;
register tmp1 = sqrt(b*b-4*a*c);
register tmp2 = 2*a;
root0 = (tmp0+tmp1)/tmp2;
root1 = (tmp0-tmp1)/tmp2;
```

Další optimalizace může pokus o přesunutí hodnocení některých výrazů nezávislé. Vezměte v úvahu následující algoritmus, který obsahuje podmíněnou větev v těle smyčky.

```cpp
vector<double> a(n);
double d, s;
// . . .
for (int i=0; i<n; i++)
{
   if (abs(d)>1.0)
      s = s+a[i]/d;
   else
      s = s+a[i]*d;
}
```

Kompilátor může rozpoznat, která hodnota výrazu (abs(d) > 1) je invariantní v těle smyčky. To umožňuje kompilátoru "zahrnul" if příkaz mimo tělo smyčky, transformace ve výše uvedeném kódu na následující:

```cpp
vector<double> a(n);
double d, s;
// . . .
if (abs(d)>1.0)
   for (int i=0; i<n; i++)
      s = s+a[i]/d;
else
   for (int i=0; i<n; i++)
      s = s+a[i]*d;
```

Po transformaci již není podmíněná větev v některém z smyček, tedy výrazně zlepšuje celkový výkon smyčky. Tento typ optimalizace je zcela bezpečné protože vyhodnocení výrazu (abs(d) > 1.0) je nezávisle na jiných výrazech.

Za přítomnosti přístup k prostředí FPU nebo výjimky s plovoucí desetinnou čárkou jsou tyto typy optimalizace contraindicated, protože mění sémantické toku. Tyto optimalizace jsou pouze k dispozici v rámci fp: precise režimu vzhledem k tomu, že jsou ve výchozím nastavení zakázán přístup k prostředí FPU a sémantiku výjimky s plovoucí desetinnou čárkou. Funkce, které přístup k prostředí FPU explicitně zakázat tyto optimalizace s použitím `fenv_access` – Direktiva pragma kompilátoru. Podobně by měl používat funkce pomocí výjimek s plovoucí desetinnou čárkou `float_control(except ... )` kompilátoru – Direktiva pragma (nebo použijte **/FP: s výjimkou** přepínač příkazového řádku).

Stručně řečeno, fp: precise režim umožňuje kompilátoru můžete změnit pořadí vyhodnocování výrazů s plovoucí desetinnou čárkou, za předpokladu, že konečných výsledků se nezmění a výsledky nejsou závislé na FPU prostředí nebo na výjimky s plovoucí desetinnou čárkou.

### <a name="fpu-environment-access-under-fpprecise"></a>Přístup k prostředí FPU pod fp: precise

Když fp: precise režim zapnutý, kompilátor předpokládá, že program přístup nebo alter FPU prostředí. Jak bylo uvedeno výše, tento předpoklad umožňuje kompilátoru změnit pořadí nebo přesunutí operací s plovoucí desetinnou čárkou ke zvýšení efektivity za fp: precise.

Některé programy mohou měnit s plovoucí desetinnou čárkou zaokrouhlení směrem s použitím `_controlfp` funkce. Například některé programy compute horní a dolní hranice chyba na aritmetické operace pomocí provádí výpočet dvakrát, nejprve při zaokrouhlení směrem k záporné nekonečno, pak při zaokrouhlení směrem k kladné nekonečno. Vzhledem k tomu, FPU poskytuje pohodlný způsob, jak ovládací prvek zaokrouhlení, programátor můžete změnit úpravou prostředí FPU režimu zaokrouhlování. Následující kód vypočítá platí, že přesné znění chybové svázán s plovoucí desetinnou čárkou násobení změnou FPU prostředí.

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -&infin;
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );    // round to +&infin;
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

V rámci fp: precise, kompilátor vždy předpokládá FPU výchozího prostředí se tak Optimalizátor je zdarma pro ignorování volání `_controlfp` a snížit výše přiřazení k cUpper = cLower = * b; by to jasně poskytovat nesprávné výsledky. Aby tyto optimalizace povolit přístup k prostředí FPU pomocí `fenv_access` – Direktiva pragma kompilátoru.

Další programy můžou snažit detekce určitých s plovoucí desetinnou čárkou chyby kontrolou FPU stavového slova. Následující kód například vyhledá dělení nulou a nepřesné podmínky

```cpp
double a, b, c, r;
float x;
// . . .
_clearfp();
r = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_ZERODIVIDE)
   handle divide by zero as a special case
_clearfp();
x = r;
if (_statusfp() & _SW_INEXACT)
   handle inexact error as a special case
etc...
```

V části fp: precise, optimalizace, které Změna pořadí vyhodnocování výrazů může změnit body, na kterých dojde k určité chybě. Programy přístup k stavového slova by měl povolit FPU přístup k prostředí pomocí `fenv_access` – Direktiva pragma kompilátoru.

Další informace najdete v části [– Direktiva pragma fenv_access](#the-fenv-access-pragma).

### <a name="floating-point-exception-semantics-under-fpprecise"></a>Sémantiku výjimky s plovoucí desetinnou čárkou v rámci fp: precise

Ve výchozím nastavení, jsou zakázané sémantiku výjimky s plovoucí desetinnou čárkou v rámci fp: precise. Většina programátorů C++ raději zpracování výjimek s plovoucí desetinnou čárkou podmínky bez použití systému nebo výjimky jazyka C++. Kromě toho zakázání sémantiku výjimky s plovoucí desetinnou čárkou umožňuje jak bylo uvedeno dříve, kompilátor větší flexibilitu při optimalizaci operací s plovoucí desetinnou čárkou. Použít buď **/FP: s výjimkou** přepnout nebo `float_control` direktivy pragma povolí sémantiku výjimky s plovoucí desetinnou čárkou, při použití fp: precise modelu.

Další informace najdete v části [povoluje sémantiku výjimky s plovoucí desetinnou čárkou](#enabling-floating-point-exception-semantics).

## <a name="the-fpfast-mode-for-floating-point-semantics"></a>Režim FP: Fast pro sémantiku plovoucí desetinné čárky

Když je povolený režim FP: Fast, kompilátor zmírňuje pravidla tohoto fp: precise používá při optimalizaci operací s plovoucí desetinnou čárkou. Tento režim se umožňuje kompilátoru optimalizovat kód s plovoucí desetinnou čárkou rychlost na úkor přesnosti s plovoucí desetinnou čárkou a správnosti. Programy, které nespoléhejte na s velmi přesnými výpočtů s plovoucí desetinnou čárkou může docházet k vylepšení rychlosti významné povolením FP: Fast režimu.

Režim s plovoucí desetinnou čárkou FP: Fast se aktivuje pomocí [Fast](fp-specify-floating-point-behavior.md) přepínač příkazového řádku kompilátoru následujícím způsobem:

> source.cpp Fast cl

V tomto příkladu instruuje kompilátor, aby používají sémantiku FP: Fast při generování kódu pro soubor source.cpp. FP: Fast modelu může být vyvoláno také na jednotlivých podle funkcí pomocí `float_control` – Direktiva pragma kompilátoru.

Další informace najdete v části [float_control – Direktiva pragma](#the-float-control-pragma).

V režimu FP: Fast kompilátor může provádět optimalizace, které změnit přesnost výpočtů s plovoucí desetinnou čárkou. Kompilátor nemůže správně zaokrouhlit na přiřazení, zaokrouhlovat nebo volání funkce a zprostředkující zaokrouhlení vždy se neprovede. S plovoucí desetinnou čárkou konkrétní optimalizace, jako je například staženiny, vždy povolena. Sémantiku výjimky s plovoucí desetinnou čárkou a citlivosti prostředí FPU jsou zakázaná a není k dispozici.

|Sémantika FP: Fast|Vysvětlení
|-|-|
|Zaokrouhlení sémantiku|Zaokrouhlovat explicitní zaokrouhlení na přiřazení a volání funkce mohou být ignorovány.<br/>Přechodných výrazů může se zaokrouhlí na menší než registrace přesnost podle požadavků na výkon.|
|Algebraický transformace|Kompilátor může transformovat výrazy podle reálné číslo asociativní, distributivních algebraický; Tyto transformace nemusí být přesné nebo správný.|
|Staženiny|Vždy povolena; nelze zakázat – Direktiva pragma `fp_contract`|
|Pořadí vyhodnocení s plovoucí desetinnou čárkou|Kompilátor může změnit pořadí vyhodnocování výrazů s plovoucí desetinnou čárkou i v případě, že tyto změny mohou změnit konečných výsledků.|
|Přístup k prostředí FPU|Zakázané. Není k dispozici|
|Sémantiku výjimky s plovoucí desetinnou čárkou|Zakázané. Není k dispozici|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpfast"></a>Zaokrouhlení sémantika výrazů s plovoucí desetinnou čárkou v rámci FP: Fast

Na rozdíl od fp: precise modelu, model FP: Fast provádí pomocné výpočty v nejpohodlnější přesnosti. Zaokrouhlení na přiřazení, zaokrouhlovat a nemusí vždy dojít k volání funkce. Například první funkce níže představuje tří proměnných jednoduchou přesnost (`C`, `Y` a `T`). Kompilátor může rozhodnout zaregistrace tyto proměnné, výsledkem bude zvýšení úrovně typ `C`, `Y` a `T` na dvojitou přesností.

Původní funkce:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0, C=0, Y, T;
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = T;
   }
   return sum;
}
```

Proměnné uloženy v registrech procesoru:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0;
   double C=0, Y, T; // now held in-register
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = (float) T;
   }
   return sum;
}
```

V tomto příkladu má FP: Fast subverted záměr původní funkce. Poslední optimalizované výsledek, uložené v proměnné `sum`, může být poměrně perturbed z správný výsledek.

V části FP: Fast kompilátor obvykle pokusí udržovat minimální Zadaná přesnost ve zdrojovém kódu. Se ale v některých případech kompilátor může rozhodnout provést přechodných výrazů v *nižší přesnost* než zadané ve zdrojovém kódu. Například první blok kódu níže volá dvojité přesnosti verzi funkce druhou odmocninu. V části FP: Fast, v některých případech, například když výsledek a operandy funkce jsou explicitně přetypovat na jednoduchou přesností, nahraďte volání dvojité přesnosti kompilátor rozhodnout `sqrt` pomocí volání do jedné přesnosti `sqrtf`funkce. Protože přetypování Ujistěte se, že hodnota přicházející do `sqrt` a hodnota už jsou zaokrouhleny na jednoduchou přesnost, pouze změní na místě zaokrouhlení. Pokud byla zadána hodnota přicházející do sqrt hodnotu dvojité přesnosti a kompilátor provést tuto transformaci až polovinu bitů přesnosti mohou být nesprávné.

Původní – funkce

```cpp
double sqrt(double);
// . . .
double a, b, c;
float f1, f2;
// . . .
float length = (float)sqrt((float)(a*a + b*b + c*c));
float sum = (float) ((double)f1 + (double)f2);
```

Optimalizované – funkce

```cpp
float sqrtf(float)...
// . . .
double a, b, c;
float f1, f2;
// . . .
double tmp0 = a*a + b*b + c*c;
float tmp1 = tmp0;    // round of parameter value
float length = sqrtf(tmp1); // rounded sqrt result
float sum = f1 + f2;
```

I když zapříčinit, tyto optimalizace může být zvláště užitečné při cílení na procesory, které poskytují a jednoduchou přesností, vnitřní verze funkcí, jako například `sqrt`. Právě přesně Když kompilátor použije tyto optimalizace je závislá platforma a kontext.

Kromě toho neexistuje žádné garantované konzistenci pro přesnost zprostředkující výpočty, které mohou být provedeny na libovolné úrovni přesnosti k dispozici pro kompilátor. Ačkoli kompilátor se pokusí o alespoň udržovat úroveň přesnosti, jak je uvedeno v kódu, umožňuje FP: Fast Optimalizátor, aby jeho přetypování směrem dolů zprostředkující výpočty cílem vytvořit rychlejší a menší strojového kódu. Například kompilátor může dál optimalizovat kód výše má být zaokrouhleno některé zprostředkující součinů na jednoduchou přesnost.

```cpp
float sqrtf(float)...
// . . .
double a, b, c;
float f1, f2;
// . . .
float tmp0 = a*a;     // round intermediate a*a to single-precision
float tmp1 = b*b;     // round intermediate b*b to single-precision
double tmp2 = c*c;    // do NOT round intermediate c*c to single-precision
float tmp3 = tmp0 + tmp1 + tmp2;
float length = sqrtf(tmp3);
float sum = f1 + f2;
```

Tento druh zaokrouhlování další může způsobit pomocí nižší přesnost s plovoucí desetinnou čárkou jednotka, jako je například SSE2, provádět některé zprostředkující výpočty. Přesnost, zaokrouhlení FP: Fast je proto platforma závislé; kód, který zkompiluje dobře pro jeden procesor nemusí nutně fungovat dobře pro jiný procesor. Je ponecháno na uživatele a zjistí, pokud rychlost výhody převáží nad žádné problémy s přesností.

Pokud FP: Fast optimalizace je zvláště problematický pro konkrétní funkci, s plovoucí desetinnou čárkou režimu můžete místně přešla na fp: precise pomocí `float_control` – Direktiva pragma kompilátoru.


### <a name="algebraic-transformations-under-fpfast"></a>Algebraický transformace v části FP: Fast

Režim FP: Fast umožňuje kompilátoru provést některé, nebezpečné algebraických transformace na plovoucí bodu výrazy. Například může být následující unsafe optimalizace pracující na základě FP: Fast.

||||
|-|-|-|
|Původní kód|Krok #1|Krok #2
|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = y – a – b;`<br/><br/>`c = x – z;`<br/><br/>`c = x * z;`<br/><br/>`c = x - z;`<br/><br/>`c = x + z;`<br/><br/>`c = z-x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x – 0;`<br/><br/>`c = x * 0;`<br/><br/>`c = x - 0;`<br/><br/>`c = x + 0;`<br/><br/>`c = 0 - x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x;`<br/><br/>`c = 0;`<br/><br/>`c = x;`<br/><br/>`c = x;`<br/><br/>`c = -x;`|

V kroku 1, který dodržuje kompilátor `z = y – a – b` se vždy rovná nule. I když je to technicky neplatný pozorování, připouští FP: Fast. Kompilátor poté rozšíří konstantní hodnotu nula každé následné využívání proměnné z. V kroku 2, kompilátor dále optimalizuje pozorováním, který `x - 0 == x`, `x * 0 == 0`atd. Znovu i když tyto poznámky nejsou striktně platný, jsou povolené v rámci FP: Fast. Optimalizovaný kód je teď mnohem rychlejší, ale může také být výrazně méně přesný nebo ještě není správný.

Optimalizátorem některý z těchto pravidel algebraických (unsafe) se použijí, když je povolený režim FP: Fast:

|||
|-|-|
|Formulář|Popis|
|`(a + b) + c = a + (b + c)`|Asociativní pravidlo pro přidání|
|`(a * b) * c = a * (b * c)`|Asociativní pravidlo pro násobení|
|`a * (b + c) = a * b + b * c`|Distribuce násobení přes sčítání|
|`(a + b)(a - b) = a * a - b * b`|Které budou zohledňovat algebraických|
|`a / b = a * (1 / b)`|Dělení multiplicative inverzní|
|`a * 1.0 = a, a / 1.0 = a`|Multiplikativní identity|
|`a ± 0.0 = a, 0.0 - a = -a`|Additive identity|
|`a / a = 1.0, a - a = 0.0`|Zrušení|

Pokud FP: Fast optimalizace je zvláště problematický pro určitou funkci, s plovoucí desetinnou čárkou režimu můžete místně přešla na fp: precise pomocí `float_control` – Direktiva pragma kompilátoru.

### <a name="order-of-floating-point-expression-evaluation-under-fpfast"></a>Pořadí vyhodnocení výrazů s plovoucí desetinnou čárkou v rámci FP: Fast

Na rozdíl od fp: precise, FP: Fast umožňuje kompilátoru změnit pořadí operací s plovoucí desetinnou čárkou tak, aby vytvářet kód rychleji. Díky tomu se nemusí některé optimalizace za FP: Fast zachovat zamýšleném pořadí výrazy. Zvažte například následující funkci, která vypočítá součin dvou vektorů n rozměrný.

```cpp
float dotProduct( float x[], float y[],
                  int n )
{
   float p=0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

V části FP: Fast, optimalizátor může provádět skalární snížení `dotProduct` pracovat efektivně transformace funkce takto:

```cpp
float dotProduct( float x[], float y[],int n )
{
    int n4= n/4*4; // or n4=n&(~3);
    float p=0, p2=0, p3=0, p4=0;
    int i;

    for (i=0; i<n4; i+=4)
    {
        p+=x[i]*y[i];
        p2+=x[i+1]*y[i+1];
        p3+=x[i+2]*y[i+2];
        p4+=x[i+3]*y[i+3];
    }
    p+=p2+p3+p4;

    // last n%4 elements
    for (; i<n; i++)
    p+=x[i]*y[i];

    return p;
}
```

V optimalizovanou verzi funkce jsou čtyři samostatný produkt panelu provést současně a pak navzájem sečteny. Tato optimalizace můžete urychlit výpočet `dotProduct` až může být proto nepřesné jde o vykreslení zbytečné faktor čtyři v závislosti na cílový procesor, ale konečný výsledek. Pokud tyto optimalizace jsou obzvláště problematické pro jednu funkci nebo jednotce překladu, se místně přepnout režim s plovoucí desetinnou čárkou, do fp: precise pomocí `float_control` – Direktiva pragma kompilátoru.

## <a name="the-fpstrict-mode-for-floating-point-semantics"></a>Fp: strict režim pro sémantiku plovoucí desetinné čárky

Když fp: striktním režimu je povolené, kompilátor používá stejné pravidla tohoto fp: precise používá při optimalizaci operací s plovoucí desetinnou čárkou. Tento režim také povolí sémantiku výjimky s plovoucí desetinnou čárkou a citlivost na FPU prostředí a zakáže některé optimalizace, jako je například staženiny. Je nejpřísnější provozní režim.

Fp: přísný režim s plovoucí desetinnou čárkou se aktivuje pomocí [/FP: strict](fp-specify-floating-point-behavior.md) přepínač příkazového řádku kompilátoru následujícím způsobem:

> cl/FP: strict source.cpp

V tomto příkladu dává pokyn kompilátoru, aby použil fp: strict sémantiku při generování kódu pro soubor source.cpp. Fp: strict modelu může být vyvoláno také na jednotlivých podle funkcí pomocí `float_control` – Direktiva pragma kompilátoru.

Další informace najdete v části [float_control – Direktiva pragma](#the-float-control-pragma).

V části fp: striktním režimu, kompilátor nikdy provádí žádné optimalizace, které perturb přesnost výpočtů s plovoucí desetinnou čárkou. Kompilátor bude správně zaokrouhlovat vždy v přiřazení, zaokrouhlovat a volání funkcí a zprostředkujících zaokrouhlení konzistentně proběhne na stejnou přesnost jako FPU Registry. Ve výchozím nastavení jsou povolené sémantiku výjimky s plovoucí desetinnou čárkou a FPU prostředí citlivosti. Některé optimalizace, jako je například staženiny, jsou zakázané, protože kompilátor nemůže zaručit správnosti ve všech případech.

|FP: strict sémantiku|Vysvětlení|
|-|-|
|Zaokrouhlení sémantiku|Zaokrouhlovat explicitní zaokrouhlení na přiřazení a volání funkce<br/>Přechodných výrazů se dá vyhodnotit za registr přesnosti.<br/>Stejné jako fp: precise|
|Algebraický transformace|Striktní dodržování asociativní, – a distributivních algebraický s plovoucí desetinnou čárkou, pokud transformace je zaručeno, že vždy vytvářejí stejné výsledky.<br/>Stejné jako fp: precise|
|Staženiny|Vždy zakázáno|
|Pořadí vyhodnocení s plovoucí desetinnou čárkou|Kompilátor nebude změnit pořadí vyhodnocování výrazů s plovoucí desetinnou čárkou|
|Přístup k prostředí FPU|Vždy povolena.|
|Sémantiku výjimky s plovoucí desetinnou čárkou|Ve výchozím nastavení povoleno.|

### <a name="floating-point-exception-semantics-under-fpstrict"></a>Sémantiku výjimky s plovoucí desetinnou čárkou v rámci fp: strict

Ve výchozím nastavení, sémantiku výjimky s plovoucí desetinnou čárkou jsou povoleny v rámci fp: strict modelu. Zakázat tyto sémantiku, použijte buď **/FP: except –** přepnout nebo zavést `float_control(except, off)` – Direktiva pragma.

Další informace najdete v částech [povoluje sémantiku výjimky s plovoucí desetinnou čárkou](#enabling-floating-point-exception-semantics) a [float_control – direktiva Pragma](#the-float-control-pragma).

## <a name="the-fenvaccess-pragma"></a>Fenv_access – Direktiva pragma

Použití:

```cpp
#pragma fenv_access( [ on  | off ] )
```

[Fenv_access](../../preprocessor/fenv-access.md) – Direktiva pragma umožňuje kompilátoru provést některé optimalizace, které může pokazit FPU příznak testy a změně režimu FPU. Když stav `fenv_access` je zakázaná, můžete předpokládat kompilátor režimy výchozí FPU jsou aktivní a nejsou testovány FPU příznaky. Ve výchozím nastavení, je zakázán přístup prostředí pro fp: precise režimu, i když může být explicitně povoleno, pomocí této direktivy pragma. V části fp: strict, `fenv_access` vždy zapnutá a nejde zakázat. V části FP: Fast `fenv_access` vždy zakázaná a není možné.

Jak je popsáno ve formátu: přesné části někteří programátoři mohou změnit s plovoucí desetinnou čárkou pomocí zaokrouhlení směrem `_controlfp` funkce. Můžete třeba k výpočtu chyby horní a dolní hranice na aritmetické operace, některé programy provést výpočet dvakrát, nejprve při zaokrouhlení směrem k záporné nekonečno, pak při zaokrouhlení směrem k kladné nekonečno. Vzhledem k tomu, FPU poskytuje pohodlný způsob, jak ovládací prvek zaokrouhlení, programátor můžete změnit úpravou prostředí FPU režimu zaokrouhlování. Následující kód vypočítá platí, že přesné znění chybové svázán s plovoucí desetinnou čárkou násobení změnou FPU prostředí.

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -infinity
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );       // round to +infinity
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

Pokud je zakázán, `fenv_access` – Direktiva pragma umožňuje kompilátoru předpokládat, že výchozí prostředí FPU; proto je zdarma pro ignorování volání Optimalizátor `_controlfp` a snížit výše přiřazení `cUpper = cLower = a*b`. Když je povoleno, ale `fenv_access` brání tyto optimalizace.

Programy mohou také zkontrolujte stavové slovo FPU ke zjištění určité chyby s plovoucí desetinnou čárkou. Následující kód například vyhledá dělení nulou a nepřesné podmínky

```cpp
double a, b, c, r;
float x;
// . . .
_clearfp();
r = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_ZERODIVIDE)
   handle divide by zero as a special case
_clearfp();
x = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_INEXACT)
   handle inexact error as a special case
etc...
```

Když `fenv_access` je zakázaná, kompilátor může změnit pořadí provádění výrazů s plovoucí desetinnou čárkou, proto pravděpodobně funkci kontroly stavu FPU. Povolení `fenv_access` brání tyto optimalizace.

## <a name="the-fpcontract-pragma"></a>Fp_contract – Direktiva pragma

Použití:

```cpp
#pragma fp_contract( [ on | off ] )
```

Jak je popsáno v fp: precise části rozpor mezi je základní architektury funkce pro mnoho moderní jednotek s plovoucí desetinnou čárkou. Staženiny umožňují provádět násobení, za nímž následuje doplněk jako jednu operaci s žádná chyba zprostředkující zaokrouhlení. Tyto instrukce s jednoduchou jsou rychlejší než provádění samostatné násobit a přidat pokyny a jsou přesnější, protože neexistuje žádný zprostředkující zaokrouhlení tohoto produktu. Smluvní operace můžete vypočítá hodnotu `(a*b+c)` jakoby byly operace vypočítané s nekonečnou přesností a zaokrouhlí nejbližší číslo s plovoucí desetinnou čárkou. Tato optimalizace můžete výrazně zrychlit funkce obsahující několik prokládané násobit a přidat operace. Představte si třeba následující algoritmus, který vypočítá součin dvou vektorů n rozměrný.

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

Tento výpočet lze provést řadu vynásobit přidat pokyny ve formátu `p = p + x[i]*y[i]`.

[Fp_contract](../../preprocessor/fp-contract.md) – Direktiva pragma Určuje, zda může být zakázku výrazů s plovoucí desetinnou čárkou. Ve výchozím nastavení fp: precise režim umožňuje staženiny protože pomáhají zvýšit přesnost a rychlost. Pro režim FP: Fast jsou vždy povoleny staženiny. Nicméně, protože staženiny může pokazit explicitní zjišťování chybové stavy, `fp_contract` – Direktiva pragma je vždy zakázaná v části fp: striktním režimu. Příklady výrazů, které mohou být při zakázku `fp_contract` – Direktiva pragma je povoleno:

```cpp
float a, b, c, d, e, t;
...
d = a*b + c;         // may be contracted
d += a*b;            // may be contracted
d = a*b + e*d;       // may be contracted into a mult followed by a mult-add etc...

d = (float)a*b + c;  // won't be contracted because of explicit rounding

t = a*b;             // (this assignment rounds a*b to float)
d = t + c;           // won't be contracted because of rounding of a*b
```

## <a name="the-floatcontrol-pragma"></a>Float_control – Direktiva pragma

**/FP: precise**, **Fast**, **/FP: strict** a **/FP: s výjimkou** přepínače řídit sémantiku plovoucí desetinné čárky na souboru po souboru základ. [Float_control](../../preprocessor/float-control.md) – Direktiva pragma poskytuje takový ovládací prvek na základě funkce funkce.

Použití:

```cpp
#pragma float_control(push)
#pragma float_control(pop)
#pragma float_control( precise, on | off [, push] )
#pragma float_control( except, on | off [, push] )
```

Pragmas `float_control(push)` a `float_control(pop)` v uvedeném pořadí se službami push a vyvolat přes pop aktuální stav s plovoucí desetinnou čárkou režimu a možnost výjimky do zásobníku. Všimněte si, že stav `fenv_access` a `fp_contract` nejsou ovlivněny – Direktiva pragma `pragma float_control(push/pop)`.

Volání direktivy pragma `float_control(precise, on)` vám umožní a `float_control(precise, off)` dojde k zakázání sémantiku přesné režimu. Podobně, direktivy pragma `float_control(except, on)` vám umožní a `float_control(except, off)` dojde k zakázání sémantiku výjimky. Sémantiku výjimky. možné povolit jenom v případě přesné sémantiku jsou také povoleny. Pokud volitelný `push` argument je k dispozici, stavy `float_control` možnosti jsou vloženy před změnou sémantiku.

### <a name="setting-the-floating-point-semantic-mode-on-a-function-by-function-basis"></a>Nastavení s plovoucí desetinnou čárkou sémantické režimu na základě podle funkcí

Přepínače příkazového řádku jsou ve skutečnosti sdružená vlastnost nastavující pragmas s plovoucí desetinnou čárkou čtyři různé hodnoty. Explicitně vybrat konkrétní s plovoucí desetinnou čárkou sémantické režimu na základě funkce funkce, vyberte jednotlivé čtyři pragma s plovoucí desetinnou čárkou možnost, jak je popsáno v následující tabulce:

||||||
|-|-|-|-|-|
||float_control(Precise)|float_control(EXCEPT)|fp_contract|fenv_access|
|/ FP: strict|on|on|Vypnout|on|
|/ FP: strict/FP: except-|on|Vypnout|Vypnout|on|
|/ FP: precise|on|Vypnout|on|Vypnout|
|/ FP: precise/FP: except|on|on|on|Vypnout|
|Fast|Vypnout|Vypnout|on|Vypnout|

Například následující explicitně povoluje sémantiku FP: Fast.

```cpp
#pragma float_control( except, off )   // disable exception semantics
#pragma float_control( precise, off )  // disable precise semantics
#pragma fp_contract(on)                // enable contractions
#pragma fenv_access(off)               // disable fpu environment sensitivity
```

> [!Note]
> Před vypnutím "přesné" sémantiku musí být vypnutý sémantiku výjimky.

## <a name="enabling-floating-point-exception-semantics"></a>Povolení sémantiku výjimky s plovoucí desetinnou čárkou

Některé výjimek s plovoucí desetinnou čárkou podmínkách, například při dělení nulou, může způsobit FPU signál hardwarové výjimky. Výjimky s plovoucí desetinnou čárkou jsou ve výchozím nastavení zakázané. Změnou FPU řídicí slovo s jsou povolené výjimky s plovoucí desetinnou čárkou `_controlfp` funkce. Například následující kód umožní výjimky s plovoucí desetinnou čárkou dělení nulou:

```cpp
_clearfp(); // always call _clearfp before
            // enabling/unmasking a FPU exception
_controlfp( _EM_ZERODIVIDE, _MCW_EM );
```

Když je povolená výjimka dělení nulou, všechny operace dělení s jmenovatel rovnou na nulu, způsobí výjimku FPU má být signalizován.

Chcete-li obnovit řídicí slovo FPU výchozí režim, zavolejte `_controlfp(_CW_DEFAULT, ~0)`.

Povolení sémantiku výjimky s plovoucí desetinnou čárkou s **/FP: except** příznak není totéž jako povolení výjimky s plovoucí desetinnou čárkou. Pokud se povolí sémantiku výjimky s plovoucí desetinnou čárkou, kompilátor musí odpovídat možnost, že všechny operace s plovoucí desetinnou čárkou může vyvolat výjimku. Vzhledem k tomu, FPU je samostatný procesor, pokyny k provádění na FPU lze provést současně pokyny na jiné jednotky.

Obrysů výjimek plovoucí desetinné čárky FPU se zastavit provádění problematický instrukce a pak signálu výjimečné podmínce nastavením FPU stavového slova. Jakmile procesor dosáhne další pokyn s plovoucí desetinnou čárkou, nejprve zkontroluje pro čekající FPU výjimky. Pokud existuje čekající výjimky, procesor ho traps voláním obslužnou rutinu výjimky, které jsou k dispozici v operačním systému. To znamená, že při operaci s plovoucí desetinnou čárkou, zaznamená výjimečné podmínce, odpovídající výjimky nebudou zjištěna, dokud provedením další operace s plovoucí desetinnou čárkou. Například následující kód traps dělení nulou výjimka:

```cpp
double a, b, c;
// . . .
// ...unmasking of FPU exceptions omitted...
__try
{
   b/c; // assume c==0.0
   printf("This line shouldn't be reached when c==0.0\n");
   c = 2.0*b;
}
__except( EXCEPTION_EXECUTE_HANDLER )
{
   printf("SEH Exception Detected\n");
}
// . . .
```

Pokud dojde k podmínku dělení nulou ve výrazu = b a c, FPU nebude depeše/vyvolat výjimku až do další operace s plovoucí desetinnou čárkou ve výrazu 2.0 * b. Výsledkem je následující výstup:

```Output
This line shouldn't be reached when c==0.0
SEH Exception Detected
```

Printf odpovídající na první řádek výstupu by neměl bylo dosaženo. bylo dosaženo, protože nebyla vyvolána s plovoucí desetinnou čárkou výjimka způsobené výraz b a c, až do dosažení spuštění 2.0 * b. Aby se vyvolala výjimka právě po provedení b a c, musí kompilátor zavést instrukce "Čekání":

```cpp
// . . .
   __try
   {
      b/c; // assume this expression will cause a "divide-by-zero" exception
      __asm fwait;
      printf("This line shouldn't be reached when c==0.0\n");
      c = 2.0*b;
   }
// . . .
```

Tento pokyn "Počkejte" vynutí procesoru k synchronizaci se stavem FPU a zpracovávat všechny výjimky, čekající na vyřízení. Kompilátor vygeneruje jenom ty "Počkejte" pokyny obrysů sémantiku plovoucí desetinné čárky. Když tyto sémantiku jsou zakázaná, protože jsou ve výchozím nastavení, programy setkat synchronicity chyby, podobně jako výše, při použití výjimek plovoucí desetinné čárky.

Pokud se povolí sémantiku plovoucí desetinné čárky, kompilátor nebude uvozovat jenom "Čekání" pokyny, ji bude také zabránění kompilátoru neoprávněně optimalizace plovoucí desetinné čárky kód za přítomnosti výjimky. To zahrnuje všechny transformace, které mění body, na kterých jsou výjimky vyvolány. Z důvodu tyto faktory povoluje sémantiku plovoucí desetinné čárky může se výrazně snížil efektivitu generované strojového kódu, proto došlo ke snížení výkonu aplikace.

Sémantiku výjimky s plovoucí desetinnou čárkou jsou povolené ve výchozím nastavení v části fp: strict režimu. Povolit tyto sémantiku ve formátu: precise režimu, přidejte **/FP: s výjimkou** přepínat do příkazového řádku kompilátoru. Sémantiku výjimky s plovoucí desetinnou čárkou také lze povolit a na jednotlivých podle funkcí pomocí zakázáno `float_control` direktivy pragma.

### <a name="floating-point-exceptions-as-c-exceptions"></a>Výjimky s plovoucí desetinnou čárkou jako výjimek jazyka C++

Jako s všechny hardwarové výjimky výjimky s plovoucí desetinnou čárkou vnitřně nevyvolá výjimky jazyka C++, ale místo toho aktivovat strukturovaných výjimek. K mapování strukturované výjimky s plovoucí desetinnou čárkou na výjimky jazyka C++, můžete uživatelům zavést vlastní translator výjimky SEH. Nejprve zavést odpovídající jednotlivé výjimky s plovoucí desetinnou čárkou výjimky jazyka C++:

```cpp
class float_exception : public std::exception {};

class fe_denormal_operand : public float_exception {};
class fe_divide_by_zero : public float_exception {};
class fe_inexact_result : public float_exception {};
class fe_invalid_operation : public float_exception {};
class fe_overflow : public float_exception {};
class fe_stack_check : public float_exception {};
class fe_underflow : public float_exception {};
```

Zaveďte funkce překladu, který zjistí s plovoucí desetinnou čárkou výjimku SEH a odpovídající výjimku C++. Chcete-li tuto funkci použít, nastavte translator obslužná rutina strukturované výjimky pro aktuální vlákno procesu s [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) funkce v knihovně modulu runtime.

```cpp
void se_fe_trans_func( unsigned int u, EXCEPTION_POINTERS* pExp )
{
    switch (u)
    {
    case STATUS_FLOAT_DENORMAL_OPERAND:   throw fe_denormal_operand();
    case STATUS_FLOAT_DIVIDE_BY_ZERO:     throw fe_divide_by_zero();
   etc...
    };
}
// . . .
_set_se_translator(se_fe_trans_func);
```

Po inicializaci toto mapování výjimky s plovoucí desetinnou čárkou se bude chovat jako by byly výjimky jazyka C++. Příklad:

```cpp
try
{
   // floating-point code that might throw divide-by-zero
   // or other floating-point exception
}
catch(fe_divide_by_zero)
{
    cout << "fe_divide_by_zero exception detected" << endl;
}
catch(float_exception)
{
    cout << "float_exception exception detected" << endl;
}
```

## <a name="references"></a>Odkazy

[Co mezi odborníky přes každých počítač by měl vědět o aritmetické operace s plovoucí desetinnou čárkou](http://pages.cs.wisc.edu/~david/courses/cs552/S12/handouts/goldberg-floating-point.pdf) podle Davida Goldberg.

## <a name="see-also"></a>Viz také:

[Optimalizace kódu](optimizing-your-code.md)<br/>
