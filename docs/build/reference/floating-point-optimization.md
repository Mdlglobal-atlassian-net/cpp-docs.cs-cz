---
title: Microsoft Visual C++ plovoucí bodu optimalizace | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35c9263fa6252469124eefb0dfd575ef5bd2ac34
ms.sourcegitcommit: 5e932a0e110e80bc241e5f69e3a1a7504bfab1f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2018
ms.locfileid: "34422746"
---
# <a name="microsoft-visual-c-floating-point-optimization"></a>Optimalizace Microsoft Visual C++ s plovoucí desetinnou čárkou

Získáte popisovač pro optimalizaci s plovoucí desetinnou čárkou kódu pomocí Microsoft C++ compiler způsob správy sémantiku s plovoucí desetinnou čárkou. Vytvořte rychlé programy a zajistit, že pouze bezpečné optimalizace se provádí na kód s plovoucí desetinnou čárkou.

## <a name="optimization-of-floating-point-code-in-c"></a>Optimalizace s plovoucí desetinnou čárkou kódu v jazyce C++

Optimalizace C++ compiler nejen překládá zdrojového kódu do zkompilovaný kód, je uspořádá pokynů počítače tak, aby zlepšení efektivity a snížení velikosti. Mnoho běžných optimalizace bohužel nejsou nezbytně bezpečné při použití s plovoucí desetinnou čárkou výpočty. Dobrým příkladem tohoto můžete zobrazit s následujícím algoritmu sumarizační převzaty z David Goldberg, "Co každých počítače vědecký pracovník by měla vědět o aritmetiku", *Computing průzkumy*, března 1991, pg. 203:

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

Tato funkce přidává n **float** hodnoty v poli vektoru `A`. V rámci těla smyčky algoritmus vypočítá hodnotu "oprava", které se pak použije k dalším krokem souhrn. Tato metoda výrazně snižuje kumulativní zaokrouhlovací chyby ve srovnání se jednoduchý souhrn, a přitom zachovat O(n) čas složitost.

Kompilátor C++ naïve může předpokládat, že s plovoucí desetinnou čárkou aritmetické následuje stejná algebraických pravidla jako aritmetické reálné číslo. Takové kompilátoru může pak chybnou informací dokončete

> C = T - součet - Y == > (sum + Y) – součet - Y == > 0;

To znamená dosahovaný hodnota C je vždy konstantní nula. Pokud tato konstantní hodnota je pak se rozšíří do dalších výrazů, těla smyčky sníží jednoduchý souhrn. Přesný,

> Y = [i] - C == > Y = [i]<br/>T = součet + Y == > T = součet + [i]<br/>Součet = T == > součet = součet + [i]

Proto pro kompilátor naïve, logické transformace `KahanSum` by funkce:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0; // C, Y & T are now unused
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

I když transformovaných algoritmus je rychlejší a *je vůbec přesná reprezentace záměr pro programátory*. Oprava pečlivě vytvořený chyb úplně odebrala a jsme se ponechaná na jednoduchý, přímé sumarizační algoritmus s všechny související chybu.

Samozřejmě sofistikované kompilátoru C++ by vědět, že algebraických pravidla z reálného aritmetické se nevztahují obecně aritmetické s plovoucí desetinnou čárkou. Ale interpretovat i sofistikované kompilátoru C++ stále nesprávně pro programátory záměr.

Vezměte v úvahu běžné optimalizace, které se pokouší o uložení jako mnoho hodnot v registrech nejdříve (nazývané "enregistering" hodnotu). V `KahanSum` například optimalizace může pokus o enregister proměnné `C`, `Y` a `T` vzhledem k tomu, že se používají pouze v rámci těla smyčky. Pokud registrace přesnost 52bits (dvojité) namísto 23bits (jeden), tato optimalizace efektivně typ zvýší úroveň `C`, `Y` a `T` na typ **dvojité**. Pokud proměnná součet podobně není zpracovávány vnitřně zaregistrované, zůstane zakódována jednoduchou přesností. To transformuje sémantika `KahanSum` pro následující

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

I když `Y`, `T` a `C` se teď vypočítávají na vyšší přesností, toto nové kódování může vytvořit méně přesné výsledky v závislosti na hodnoty v `A[]`. Proto i zdánlivě neškodné optimalizace může mít negativní důsledky.

Tyto druhy problémů optimalizace nejsou omezeny na "složité" kód s plovoucí desetinnou čárkou. Při optimalizaci nesprávně, může selhat i jednoduché algoritmy s plovoucí desetinnou čárkou. Vezměte v úvahu jednoduchý, přímo sumarizační algoritmu:

```cpp
float Sum( const float A[], int n )
{
   float sum=0;
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

Protože některé jednotky s plovoucí desetinnou čárkou je schopná provádět více operací současně, můžete kompilátor zaujmout skalární snížení optimalizace. Tato optimalizace efektivně transformuje jednoduché funkce Sum z výše na následující:

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

Funkce teď udržuje čtyři samostatné panelu, které lze současně zpracovávat při každém kroku. I když optimalizované funkce je nyní mnohem rychlejší, můžou výrazně lišit z výsledků Neaktivní optimalizované optimalizované výsledky. Při provedení této změny, kompilátor předpokládá asociativní s plovoucí desetinnou čárkou přidání; To znamená že tyto dvě výrazy jsou ekvivalentní: `(a + b) + c == a + (b + c)`. Však asociativnost vždy nemá hodnotu true pro čísla s plovoucí desetinnou čárkou. Místo computing sumarizační jako:

```cpp
sum = A[0]+A[1]+A[2]+...+A[n-1];
```

funkci transformovaných teď vypočítá výsledek v podobě

```cpp
sum = (A[0]+A[4]+A[8]+...)
    + (A[1]+A[5]+A[9]+...)
    + (A[2]+A[6]+A[10]+...)
    + (A[3]+A[7]+A[11]+...);
```

Pro některé hodnoty `A[]`, toto různých uspořádání operací přidání může vést k neočekávaným výsledkům. Pro další zkomplikovat záleží, některé programátory rozhodnout předvídat takové optimalizace a je správně kompenzovat. V takovém případě můžete program vytvořit pole `A` v jiném pořadí tak, aby součet optimalizované vytváří očekávané výsledky. Kromě toho může být v mnoha případech přesnost optimalizované výsledku "Zavřít dostatečně". To platí hlavně při optimalizaci poskytuje poutavé rychlost výhody. Video hry, například vyžadovat jako mnohem rychlost co možná ale často nevyžadují vysokou přesné výpočty s plovoucí desetinnou čárkou. Osoby provádějící kompilátoru musí proto poskytují mechanismus pro programátory v jazyce k řízení často různorodých cílů rychlost a pružnost.

Některé kompilátory vyřešit tím, že poskytuje samostatné přepínač pro každý typ optimalizace kompromis mezi rychlostí a přesnosti. To umožňuje vývojářům zakázat optimalizace, které jsou příčinou změn s plovoucí desetinnou čárkou přesnost pro jejich konkrétní aplikace. Když toto řešení může nabízí vysoký stupeň kontroly nad kompilátor, zavádí několik dalších potíží:

- Často je jasné který přepne Pokud chcete povolit nebo zakázat.
- Zakázáním všech jeden optimalizace může nepříznivě ovlivnit výkon kódu bez s plovoucí desetinnou čárkou.
- Každý další přepínače způsobuje mnoho nové přepínače kombinace; počet kombinací rychle stane nepraktické.

Proto při poskytování oddělenými přepínači pro každý optimalizace se může zdát přitažlivými, pomocí těchto kompilátory může být pracné a nespolehlivé.

Nabízí mnoho kompilátory C++ *konzistence* s plovoucí desetinnou čárkou modelu (prostřednictvím **/Op** nebo **/fltconsistency** přepínače) což umožňuje vývojáři k vytvoření programy kompatibilní s striktní sémantiku s plovoucí desetinnou čárkou. Po zapojení, tento model zabrání kompilátor pomocí většina optimalizace na výpočty s plovoucí desetinnou čárkou současně tyto optimalizace pro jiný bod plovoucí kód. Model konzistence, ale má světlý straně. Chcete-li předvídatelný výsledky na různé FPU architektury, téměř všechny implementace **/Op** zaokrouhlí zprostředkující výrazy uživateli Zadaná přesnost; například vezměte v úvahu následující výraz:

```cpp
float a, b, c, d, e;
// . . .
a = b * c + d * e;
```

Chcete-li vytvořit opakovatelné a konzistentní výsledky v rámci **/Op**, získá tento výraz vyhodnocen jako by se měla implementovat následujícím způsobem:

```cpp
float x = b  *c;
float y = d * e;
a = x + y;
```

Konečný výsledek teď setká s jednoduchou přesností zaokrouhlovací chyby *na každý krok při vyhodnocování výrazu*. I když tento interpretace není výhradně dojít k porušení pravidel sémantiku C++, je téměř žádné nejlepší způsob, jak vyhodnotit výrazy s plovoucí desetinnou čárkou. Je obecně k výpočtu mezilehlých výsledků v horní přesnost, jako je praktické více žádoucí. Pro instanci, je lepší výpočetní výraz `a = b * c + d * e` v vyšší přesností jako v

```cpp
double x = b * c;
double y = d * e;
double z = x + y;
a = (float)z;
```

nebo ještě lepší

```cpp
long double x = b * c;
long double y = d * e
long double z = x + y;
a = (float)z;
```

Při výpočtu mezilehlých výsledků v vyšší přesností, je výrazně přesnější konečný výsledek. Přijetím modelu konzistence je ironically, pravděpodobnost chyby vyšší, přesněji, když uživatel se pokouší snížit chyba zakázáním unsafe optimalizace. Proto modelu konzistence může vážně snížit efektivitu a současně poskytují žádná záruka vyšší přesnosti. Závažných číselnou programátorům asi není jako velmi dobré kompromis a je hlavním důvodem modelu není obecně dobře přijímání.

Počínaje verzí 8.0 (Visual C++ 2005®), Microsoft C++ kompilátoru poskytuje mnohem lepší alternativou. Umožňuje programátorům vyberte jeden z režimů tři obecné s plovoucí desetinnou čárkou: fp: přesné, fp:fast a fp: strict.

- V části fp: přesné, pouze bezpečné optimalizace se provádí na kód s plovoucí desetinnou čárkou a na rozdíl od **/Op**, zprostředkující výpočty se provádí konzistentně na nejvyšší praktické přesnost.
- režim FP:Fast zmírní s plovoucí desetinnou čárkou pravidla, aby vám umožnil agresivnější optimalizace za cenu přesnost.
- FP: striktní režim poskytuje obecné správnost fp: přesné při povolení sémantiku fp výjimky a zabráněním neplatný transformace případě FPU prostředí změn (např. změny k registraci přesnost, zaokrouhlení směr atd.).

Sémantika výjimek plovoucí desetinné čárky je řízena nezávisle přepínač příkazového řádku nebo kompilátoru pragma; ve výchozím nastavení, jsou zakázané výjimek plovoucí desetinné čárky sémantiku pod fp: přesné a povolení pod fp: strict. Kompilátor také umožňuje řídit FPU prostředí velkých a malých písmen a určité s plovoucí desetinnou čárkou konkrétní optimalizace, jako je například staženiny. Tento model jednoduché poskytuje vývojářům značnou část kontrolu nad kompilace kódu s plovoucí desetinnou čárkou bez zatížení příliš mnoho přepínače kompilátoru nebo potenciálního nežádoucí vedlejší účinky.

## <a name="the-fpprecise-mode-for-floating-point-semantics"></a>Fp: přesné režim pro sémantiku s plovoucí desetinnou čárkou

Je výchozí režim s plovoucí desetinnou čárkou sémantiku fp: přesné. Pokud je vybraný tento režim, kompilátor výhradně dodržuje sada pravidel zabezpečení při optimalizaci operace s plovoucí desetinnou čárkou. Tato pravidla povolte kompilátoru generovat kód pro efektivní počítače při zachování přesnost výpočty s plovoucí desetinnou čárkou. Pro usnadnění provozní fast programy, fp: přesné modelu zakáže sémantiku výjimek plovoucí desetinné čárky (i když se může být explicitně povoleno). Microsoft má vybrané fp: přesné jako výchozí režim s plovoucí desetinnou čárkou, protože se tím vytvoří rychlé a přesné programy.

Explicitně požádat o fp: přesné režimu pomocí kompilátoru příkazového řádku, použijte [/fp: přesné](fp-specify-floating-point-behavior.md) přepínače:

> cl /fp: přesné source.cpp

To dává pokyn kompilátoru používat fp: přesné sémantiku při generování kódu pro soubor source.cpp. Fp: přesné modelu lze také vyvolat na jednotlivých pomocí funkcí pomocí [float_control – Direktiva pragma kompilátoru](#the-float-control-pragma).

V části fp: přesné režimu, kompilátor nikdy provede všechny optimalizace, které perturb přesnost výpočty s plovoucí desetinnou čárkou. Kompilátor vždy zaokrouhlí správně v přiřazení, přiřadí typ ukazatel a volání funkce a zprostředkující zaokrouhlení konzistentně proběhne na stejné přesnost jako FPU Registry. Bezpečné optimalizace, jako je například staženiny, jsou povolené ve výchozím nastavení. Ve výchozím nastavení je zakázána sémantiku výjimky a FPU prostředí velkých a malých písmen.

|FP: přesné sémantiku|Vysvětlení|
|-|-|
|Zaokrouhlení sémantiku|Explicitní zaokrouhlení v přiřazení, přiřadí typ ukazatel a volání funkce. Zprostředkující výrazy se vyhodnotí na přesnost registrace.|
|Algebraických transformace|Stoprocentní asociativní, jiný obchod s plovoucí desetinnou čárkou algebra, pokud transformace záruku, že vždy získáte stejné výsledky.|
|Staženiny|Povolené ve výchozím nastavení. Další informace najdete v tématu [fp_contract – Direktiva pragma](#the-fp-contract-pragma).|
|Pořadí vyhodnocení s plovoucí desetinnou čárkou|Kompilátor může změnit pořadí vyhodnocení výrazů s plovoucí desetinnou čárkou, za předpokladu, že nejsou změněna konečných výsledků.|
|FPU prostředí přístup|Zakázané ve výchozím nastavení. Další informace najdete v tématu [fenv_access – Direktiva pragma](#the-fenv-access-pragma). Se předpokládá výchozí přesnost a režim zaokrouhlení.|
|Sémantika výjimek plovoucí desetinné čárky|Zakázané ve výchozím nastavení. Další informace najdete v tématu [/fp: kromě](fp-specify-floating-point-behavior.md).|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpprecise"></a>Zaokrouhlení sémantiku pro s plovoucí desetinnou čárkou výrazy v části fp: přesné

Fp: přesné model vždycky provádí zprostředkující výpočtů v nejvyšší praktické přesnost explicitně zaokrouhlení pouze v určitých bodech při vyhodnocení výrazu. Zaokrouhlení na přesnost zadán uživatel vždy dojde v čtyři místa: (a) při přiřazení, (b) při přiřazení typu se provádí, (c) při hodnotu s plovoucí desetinnou čárkou je předat jako argument funkce a (d) při vrácená hodnota s plovoucí desetinnou čárkou funkce. Protože zprostředkující výpočty se vždycky provádí na přesnost registrace, přesnost mezilehlých výsledků je platforma závislých (i když přesnost bude vždy přesné jako zadaný uživatel přesnost).

Vezměte v úvahu výraz přiřazení v následujícím kódu. Výraz na pravé straně přiřazení operátor '=' bude počítaný na přesnost zaregistrovat a explicitně zaokrouhlené na typ na levé straně přiřazení.

```cpp
float a, b, c, d;
double x;
...
x = a*b + c*d;
```

se vypočítá jako

```cpp
float a, b, c, d;
double x;
...
register tmp1 = a*b;
register tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

Má být zaokrouhleno explicitně mezilehlých výsledků, zavést typecast. Například pokud je předchozí kód upravit přidáním explicitního přiřazení typu, zprostředkující výrazu (c * d) se zaokrouhlí na typ typecast.

```cpp
float a, b, c, d;
double x;
// . . .
x = a*b + (float)(c*d);
```

se vypočítá jako

```cpp
float a, b, c, d;
double x;
// . . .
register tmp1 = a*b;
float tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

Jeden vyplývá této metody zaokrouhlení je, že některé zdánlivě ekvivalentní transformace nemají ve skutečnosti identické sémantiku. Například následující transformace rozdělí výraz jedné přiřazení do dvou výrazů přiřazení.

```cpp
float a, b, c, d;
// . . .
a = b*(c+d);
```

není ekvivalentní

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

není ekvivalentní

```cpp
a = b*(a=c+d);
```

Tyto kódování nemají ekvivalentní sémantiku, protože každý druhý kódování mít zavedená další přiřazení operace, a proto další zaokrouhlení bodu.

Když funkce vrátí hodnotu s plovoucí desetinnou čárkou, hodnota se zaokrouhlí na typ funkce. Pokud hodnotu s plovoucí desetinnou čárkou je jako parametr předaný funkci, hodnota se zaokrouhlí na typ parametru. Příklad:

```cpp
float sumsqr(float a, float b)
{
   return a*a + b*b;
}
```

se vypočítá jako

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

se vypočítá jako

```cpp
float x, y, z;
double c;
...
register tmp1 = w*x;
register tmp2 = tmp1+y;
float tmp3 = tmp2;
c = symsqr( tmp3, z);
```

### <a name="architecture-specific-rounding-under-fpprecise"></a>Architektura konkrétní zaokrouhlení pod fp: přesné

|Procesor|Zaokrouhlení přesnost pro zprostředkující výrazy|
|-|-|
|x86|Zprostředkující výrazy se vypočítávají v výchozí přesnost 53 bitů s rozsahem rozšířené poskytované exponent 16 bitů. Když tyto 53:16 hodnoty jsou "uniknout" do paměti (jak může dojít během volání funkce), bude se rozšířené exponentu rozsahu zúžit 11 bits. To znamená uniknout hodnoty jsou převést na formát standardní dvojitou přesností s pouze exponentem 11 bitů.<br/>Uživatel může přepnout na rozšířené 64-bit přesnost pro zprostředkující zaokrouhlení změnou pomocí aplikace word s plovoucí desetinnou čárkou řízení `_controlfp` a povolením přístupu prostředí FPU (najdete v části [fenv_access – Direktiva pragma](#the-fenv-access-pragma)). Ale bude stále při rozšířené přesnost register hodnoty jsou uniknout do paměti, zaokrouhlen mezilehlých výsledků a dvojitou přesností.<br/>Tato konkrétní sémantického se mohou změnit.|
|amd64|Sémantika FP na amd64 je poněkud liší od jiných platforem. Z důvodů výkonu zprostředkující operace se vypočítávají v co nejširší přesnost buď operand místo v co nejširší přesnost k dispozici.  Pokud chcete vynutit výpočty počítaný přesností širší než operandy, uživatelé musí zavádět přetypování operace na alespoň jeden operand dílčí výrazu.<br/>Tato konkrétní sémantického se mohou změnit.|

### <a name="algebraic-transformations-under-fpprecise"></a>Algebraických transformace pod fp: přesné

Když fp: přesné režim zapnutý, kompilátor nikdy Provede algebraických transformace *není-li konečný výsledek prokazatelně identické*. Řadu známých algebraických pravidla pro reálné číslo aritmetické není vždy držitelem pro aritmetické operace s plovoucí desetinnou čárkou. Například následující výrazy jsou ekvivalentní Reals, ale nemusí nutně prokázat u obtékaných objektů.

|Formulář|Popis|
|-|-|
|`(a+b)+c = a+(b+c)`|Asociativní pravidlo pro přidání|
|`(a*b)*c = a*(b*c)`|Asociativní pravidlo pro násobení|
|`a*(b+c) = a*b + b*c`|Distribuce násobení přes přidání|
|`(a+b)(a-b) = a*a-b*b`|Algebraických řešení|
|`a/b = a*(1/b)`|Dělení multiplicative inverzní|
|`a*1.0 = a`|Multiplikativní identity|

Jak je znázorněno v příkladu Úvod pomocí funkce `KahanSum`, kompilátor může zvážit vytvoření výrazně rychlejší programy provedením různé algebraických transformace. I když optimalizace závisí na takových algebraických transformace jsou téměř vždy nesprávné, existují situace, pro které jsou naprosto bezpečné. Například je někdy žádoucí nahradit dělení *konstantní* hodnotu s násobení podle multiplikativní inverzní konstanty:

```cpp
const double four = 4.0;
double a, b;
...

a = b/four;
```

Může být uvedeny ve

```cpp
const double four = 4.0;
const double tmp0 = 1/4.0;
double a, b;
...
a = b*tmp0;
```

Je to bezpečné transformace, proto Optimalizátor můžete určit při kompilaci tohoto x / 4.0 == x*(1/4.0) pro všechny s plovoucí desetinnou čárkou hodnoty x, včetně nekonečno a NaN. Nahrazením operace dělení násobení, můžete kompilátor uložit několik cyklů – zejména u FPUs, které neimplementují přímo dělení, ale vyžadují kompilátoru generovat kombinaci vzájemné aproximace a přidat násobení pokyny. Kompilátor může provádět takové optimalizace pod fp: přesné jenom v případě, že násobení nahrazení vytváří přesně stejný výsledek jako rozdělení. Kompilátor také provádět trivial transformace pod fp: přesné, zadaný výsledky jsou identické. Mezi ně patří:

|Formulář|Popis
|-|-|
|`(a+b) == (b+a)`|Komutativní pravidlo pro přidání|
|`(a*b) == (b*a)`|Komutativní pravidlo pro násobení|
|`1.0*x*y == x*1.0*y == x*y*1.0 == x*y`|Násobení podle 1.0|
|`x/1.0*y == x*y/1.0 == x*y`|Dělení 1.0|
|`2.0*x == x+x`|Násobení podle 2.0|

### <a name="contractions-under-fpprecise"></a>Staženiny pod fp: přesné

Klíčovou funkcí architektury mnoho moderní jednotky s plovoucí desetinnou čárkou je schopnost provádět násobení, následuje přidání jako najednou k žádné chybě zprostředkující zaokrouhlení. Například, architektura Itanium společnosti Intel poskytuje pokyny pro každou z těchto operací Ternární kombinovat (*b + c), (* b-c) a (c-a * b), do jednoho s plovoucí desetinnou čárkou instrukce (FMA – fms a fnma v uvedeném pořadí). Tyto pokyny jednoho jsou rychleji než provádění samostatné násobení a přidat pokyny a jsou přesnější, protože neexistuje žádný zprostředkující zaokrouhlení produktu. Tato optimalizace můžete výrazně urychlit funkce obsahující několik prokládaný násobkem a přidání operací. Zvažte například následující algoritmus, který vypočítá tečkou součin dvou n dimenzí vektory.

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

Tento výpočet lze provést řadu násobení přidat pokyny ve formátu p = p + x [i] * y [i].

Optimalizace zmenšení lze určit nezávisle tak, pomocí `fp_contract` – Direktiva pragma kompilátoru. Ve výchozím nastavení fp: přesné modelu umožňuje staženiny vzhledem k tomu, že zlepšit přesnost a rychlost. V části fp: přesné, kompilátor se nikdy smlouvy výraz s explicitní zaokrouhlení.
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

### <a name="order-of-floating-point-expression-evaluation-under-fpprecise"></a>Pořadí vyhodnocení výrazu s plovoucí desetinnou čárkou v části fp: přesné

Optimalizace, které zachovat pořadí vyhodnocení výrazu s plovoucí desetinnou čárkou jsou vždy zabezpečené a jsou proto povoleném fp: přesné režimu. Vezměte v úvahu následující funkci, která vypočítá tečkou součin dvou n dimenzí vektorů v jednoduchou přesností. První blok kódu níže původní funkce jako může být zakódován pomocí programátory, následuje stejnou funkci po částečné rozvinutí smyčky optimalizace.

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

Hlavní výhodou tato optimalizace je to, že snižuje počet podmíněného větvení smyčky co nejvíce 75 %. Zvýšením počtu operace v rámci těla smyčky také kompilátor může mít teď většího počtu možností k optimalizaci Další. Například může být schopni provést některé FPUs násobení přidat v p += x [i] * y [i] při načítání současně hodnoty x [i + 1.] a y [i + 1] pro použití v dalším kroku. Tento typ optimalizace je perfektně bezpečné pro výpočty s plovoucí desetinnou čárkou, protože uchovává pořadí operací.

Často je výhodné pro kompilátor ke změně pořadí celý operations Chcete-li vytvořit rychlejší kódu. Vezměte v úvahu následující kód:

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

Sémantické pravidel C++ znamenat, že program by měl vytvořit výsledky jako, pokud nejprve počítaný x, potom y a nakonec. Předpokládejme, že kompilátor má pouze čtyři registry k dispozici s plovoucí desetinnou čárkou. Pokud kompilátor je nucen se výpočetní x, y a v pořadí, může zvolit pro generování kódu s následující sémantiku:

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

Existuje několik jasně redundantní operací se toto kódování. Pokud kompilátor striktně dodržovat sémantického pravidel C++, toto řazení je nutné, protože program může být přístup mezi FPU prostředí každé přiřazení. Však výchozí nastavení pro fp: přesné povolení kompilátoru optimalizovat jakoby program nemá přístup k prostředí, díky kterému jej chcete změnit pořadí těchto výrazů. Pak je můžete odebrat zálohování u výpočetních tří hodnot v obráceném pořadí, a to takto:

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

Toto kódování je jasně nadřízená, má snížit počet fp pokyny téměř 40 %. Výsledky pro x, y a jsou stejné jako předtím, ale s menší nároky na počítaný.

V části fp: přesné, kompilátor může také *prokládání* běžné dílčí výrazy, aby bylo dosaženo rychlejší kódu. Kód k výpočtu kořeny Kvadratická rovnice například může zapsat takto:

```cpp
double a, b, c, root0, root1;
...
root0 = (-b + sqrt(b*b-4*a*c))/(2*a);
root1 = (-b - sqrt(b*b-4*a*c))/(2*a);
```

I když tyto výrazy liší pouze jednu operaci, programátorů zapsat je tento způsob, jak zajistit, že bude každý kořenový hodnotu vypočítat v nejvyšší praktické přesnost. V části fp: přesné, kompilátor je zdarma prokládání výpočet root0 a root1 odebrat běžné dílčí výrazy bez ztráty přesnost. Například následující odebrala několik redundantní kroky při vytváření přesně stejnou odpovědí.

```cpp
double a, b, c, root0, root1;
...
register tmp0 = -b;
register tmp1 = sqrt(b*b-4*a*c);
register tmp2 = 2*a;
root0 = (tmp0+tmp1)/tmp2;
root1 = (tmp0-tmp1)/tmp2;
```

Další optimalizace může pokus o přesunutí vyhodnocení výrazů určité nezávislé. Vezměte v úvahu následující algoritmus, který obsahuje větve podmíněného v rámci těla smyčky.

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

Kompilátor může zjistit, která hodnota výrazu (abs(d) > 1) je neutrální v rámci těla smyčky. To umožňuje kompilátor "Zdvihadlo" if mimo těla smyčky transformace ve výše uvedeném kódu do následující příkaz:

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

Po transformaci již není podmíněného větve v některém z smyček, což značně zvyšuje celkový výkon smyčky. Tento typ optimalizace je perfektně bezpečné protože vyhodnocování výrazu (abs(d) > 1.0) je nezávislý na jiné výrazy.

Případě FPU prostředí přístup nebo s plovoucí desetinnou čárkou výjimky jsou tyto typy optimalizace contraindicated vzhledem k tomu, že se změní sémantického toku. Tyto optimalizace jsou k dispozici v části fp pouze: přesné režimu vzhledem k tomu, že je ve výchozím nastavení zakázána FPU prostředí přístup a sémantiku výjimek plovoucí desetinné čárky. Funkce, které získal přístup k prostředí FPU explicitně zakázat tyto optimalizace pomocí `fenv_access` – Direktiva pragma kompilátoru. Podobně, měli používat funkce použití s plovoucí desetinnou čárkou výjimek `float_control(except ... )` kompilátoru – Direktiva pragma (nebo použijte **/fp: kromě** přepínač příkazového řádku).

V souhrnu fp: přesné režim umožňuje kompilátoru ke změně pořadí vyhodnocení výrazů s plovoucí desetinnou čárkou za předpokladu, že nejsou změněna konečných výsledků a výsledky nejsou závislé na prostředí FPU nebo s plovoucí desetinnou čárkou výjimky.

### <a name="fpu-environment-access-under-fpprecise"></a>Přístup k prostředí FPU pod fp: přesné

Když fp: přesné režim zapnutý, kompilátor předpokládá, že program přístup nebo alter FPU prostředí. Jak jsme uvedli dříve, tento předpoklad umožňuje kompilátoru přeskupování nebo přesunout s plovoucí desetinnou čárkou operace ke zlepšení efektivity pod fp: přesné.

Některé programy mohou pomocí příkazu alter s plovoucí desetinnou čárkou zaokrouhlení směr `_controlfp` funkce. Například některé programy výpočetní horní a dolní hranice chyba na aritmetické operace provedením výpočet dvakrát, nejprve při zaokrouhlení směrem záporné nekonečno, pak při zaokrouhlení směrem kladné nekonečno. Vzhledem k tomu, že FPU nabízí pohodlný způsob, jak řídit zaokrouhlení, programátorem rozhodnout změnit režim zaokrouhlení změnou FPU prostředí. Následující kód vypočítá, že chybu přesný hranice elementu s plovoucí desetinnou čárkou násobení změnou FPU prostředí.

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -&infin;
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );    // round to +&infin;
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

V části fp: přesné, kompilátor vždy se předpokládá výchozí FPU prostředí, tak, aby Optimalizátor volné ignorovat volání `_controlfp` a snížit výše přiřazení k cUpper = cLower = * b; to by jasně poskytují nesprávné výsledky. Aby takové optimalizace FPU prostředí přístup povolit pomocí `fenv_access` – Direktiva pragma kompilátoru.

Další programy můžou snažit detekce určitých s plovoucí desetinnou čárkou chyby kontrolou FPU stavového slova. Následující kód například vyhledá dělení nulou a nepřesný podmínky

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

V části fp: přesné, optimalizace, které změní pořadí vyhodnocení výrazu může změnit body, ve kterých se zobrazují určitým chybám. Přístup k stavového slova programy měli povolit FPU prostředí přístup pomocí `fenv_access` – Direktiva pragma kompilátoru.

Další informace najdete v tématu [fenv_access – Direktiva pragma](#the-fenv-access-pragma).

### <a name="floating-point-exception-semantics-under-fpprecise"></a>Sémantika výjimek plovoucí desetinné čárky pod fp: přesné

Ve výchozím nastavení, jsou zakázané výjimek plovoucí desetinné čárky sémantiku pod fp: přesné. Většina programátory v jazyce C++ přednost zpracování výjimečných podmínek s plovoucí desetinnou čárkou bez použití systému nebo výjimky jazyka C++. Kromě toho zakázání výjimek plovoucí desetinné čárky sémantiku umožňuje jak jsme uvedli dříve, kompilátoru větší flexibilitu při optimalizaci operace s plovoucí desetinnou čárkou. Použijte buď **/fp: kromě** přepínač nebo `float_control` – Direktiva pragma povolit sémantiku výjimek plovoucí desetinné čárky, při použití fp: přesné modelu.

Další informace najdete v tématu [povolení výjimek plovoucí desetinné čárky sémantiku](#enabling-floating-point-exception-semantics).

## <a name="the-fpfast-mode-for-floating-point-semantics"></a>Režim fp:fast pro sémantiku s plovoucí desetinnou čárkou

Když je povolený režim fp:fast, kompilátor zmírní pravidla této fp: přesné používá při optimalizaci operace s plovoucí desetinnou čárkou. Tento režim je umožňuje kompilátoru optimalizovat s plovoucí desetinnou čárkou kód pro rychlost za cenu s plovoucí desetinnou čárkou přesnost a správnost. Programy, které nespoléhejte na vysoce přesné výpočty s plovoucí desetinnou čárkou může dojít k významné rychlost zlepšování povolením fp:fast režimu.

Je povolený režim s plovoucí desetinnou čárkou fp:fast, pomocí [/fp:fast](fp-specify-floating-point-behavior.md) přepínač příkazového řádku kompilátoru následujícím způsobem:

> cl /fp:fast source.cpp

Tento příklad instruuje kompilátor, aby používají sémantiku fp:fast při generování kódu pro soubor source.cpp. Fp:fast model vyvolat taky na jednotlivých pomocí funkcí pomocí `float_control` – Direktiva pragma kompilátoru.

Další informace najdete v tématu [float_control – Direktiva pragma](#the-float-control-pragma).

V režimu fp:fast může provádět kompilátor optimalizace, které alter přesnost výpočty s plovoucí desetinnou čárkou. Kompilátor nemusí správně zaokrouhlit na přiřazení, přiřadí typ ukazatel nebo volání funkce a zprostředkující zaokrouhlení nebude vždy provést. S plovoucí desetinnou čárkou konkrétní optimalizace, jako je například staženiny, vždy povolena. Sémantika výjimek plovoucí desetinné čárky a citlivosti FPU prostředí jsou zakázaná a není k dispozici.

|Sémantika FP:Fast|Vysvětlení
|-|-|
|Zaokrouhlení sémantiku|Explicitní zaokrouhlení v přiřazení, přiřadí typ ukazatel a volání funkce může být ignorovány.<br/>Zprostředkující výrazy může zaokrouhlené na menší než zaregistrovat přesnost podle požadavků na výkon.|
|Algebraických transformace|Kompilátor může transformace výrazy podle reálné číslo asociativní, rozdělovací algebra; Tyto transformace nemusí být přesné nebo správný.|
|Staženiny|Vždy povolena; nelze zakázat pomocí – Direktiva pragma `fp_contract`|
|Pořadí vyhodnocení s plovoucí desetinnou čárkou|Kompilátor může změnit pořadí vyhodnocení výrazů s plovoucí desetinnou čárkou, i když tyto změny mohou změnit konečných výsledků.|
|FPU prostředí přístup|Zakázané. Není k dispozici|
|Sémantika výjimek plovoucí desetinné čárky|Zakázané. Není k dispozici|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpfast"></a>Zaokrouhlení sémantiku pro s plovoucí desetinnou čárkou výrazy v části fp:fast

Na rozdíl od fp: přesné model modelu fp:fast provede zprostředkující výpočtů v nejvhodnější přesnost. Zaokrouhlení v přiřazení, přiřadí typ ukazatel a nemusí vždy dojít k volání funkce. Například první funkce níže představuje tři jednoduchou přesností proměnné (`C`, `Y` a `T`). Kompilátor rozhodnout enregister tyto proměnné, platí typu povýšení `C`, `Y` a `T` na dvojitou přesností.

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

Zpracovávány vnitřně zaregistrované proměnné:

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

V tomto příkladu má fp:fast subverted záměr původní funkce. Konečné optimalizované výsledek, uchovávat v proměnné `sum`, může být poměrně perturbed z správný výsledek.

V části fp:fast kompilátor pokusí obvykle udržovat alespoň přesnost určeného zdrojového kódu. V některých případech ale kompilátor rozhodnout provést zprostředkující výrazy na *nižší přesnost* než je zadáno ve zdrojovém kódu. Například první blok kódu níže volá Dvojitá přesnost verzi druhou odmocninu funkce. V části fp:fast, v některých případech, například když výsledek a operandy funkce jsou explicitně převést na jednoduchou přesností kompilátor rozhodnout nahradit volání Dvojitá přesnost `sqrt` s jednoduchou přesností volání`sqrtf`funkce. Protože přetypování zajistěte, aby hodnota přejdete do `sqrt` a hodnotu, než dorazí jsou zaokrouhleny na jednom přesnost, tak pouze změní na místě zaokrouhlení. Pokud hodnota přicházející do sqrt byla hodnotu dvojitou přesností a kompilátor provedena tato transformace, až polovinu bits přesnost může být nesprávný.

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

Optimalizované funkce

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

I když méně přesný optimalizace může být obzvláště užitečné při cílení na procesory, které poskytují jednoduchou přesností, vnitřní verze funkcí, jako například `sqrt`. Právě přesněji při kompilátor použije tyto optimalizace je platformy a kontext závislé.

Kromě toho je žádné zaručenou konzistenci pro přesnost zprostředkující výpočtů, které se dají provést na všechny dostupné pro kompilátor přesnost úrovni. I když kompilátor se pokusí o zachovali alespoň úroveň přesnost podle specifikace kód, umožňuje fp:fast Optimalizátor k přetypování dolů zprostředkující výpočty Chcete-li vytvořit počítač kódu rychlejší nebo menší. Například kompilátor může dál optimalizovat kód z výše má být zaokrouhleno některé z mezilehlých součinů pro jednoduchou přesností.

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

Tento druh další zaokrouhlení může být důsledkem pomocí nižší přesnost s plovoucí desetinnou čárkou jednotky, například SSE2, k provedení některé z mezilehlých výpočty. Přesnost fp:fast zaokrouhlení je proto platformy závislých; kód, který se zkompiluje i pro jeden procesor nemusí nutně fungovat i pro jiné procesoru. Je ponechán na uživatele a zjistí, pokud rychlost výhody převáží nad potíže přesnost.

Pokud je fp:fast optimalizace pro konkrétní funkci obzvláště problematické, s plovoucí desetinnou čárkou režimu lze místně přepnout fp: přesné pomocí `float_control` – Direktiva pragma kompilátoru.


### <a name="algebraic-transformations-under-fpfast"></a>V části fp:fast algebraických transformace

Režim fp:fast umožňuje kompilátoru k provedení určité, unsafe algebraických transformace na plovoucí bodu výrazy. Následující unsafe optimalizace může například být použit v rámci fp:fast.

||||
|-|-|-|
|Původní kód|Krok #1|Krok #2
|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = y – a – b;`<br/><br/>`c = x – z;`<br/><br/>`c = x * z;`<br/><br/>`c = x - z;`<br/><br/>`c = x + z;`<br/><br/>`c = z-x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x – 0;`<br/><br/>`c = x * 0;`<br/><br/>`c = x - 0;`<br/><br/>`c = x + 0;`<br/><br/>`c = 0 - x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x;`<br/><br/>`c = 0;`<br/><br/>`c = x;`<br/><br/>`c = x;`<br/><br/>`c = -x;`|

V kroku 1, který dodržuje kompilátor `z = y – a – b` se vždy rovná nule. I když je technicky neplatný pozorování, je povoleno pod fp:fast. Kompilátor potom rozšíří konstantní hodnotu nula pro všechny následné použití proměnné z. V kroku 2, kompilátor další optimalizuje tím, který sledování `x - 0 == x`, `x * 0 == 0`atd. Znovu i když tyto připomínky nejsou nezbytně platné, je povoleno, fp:fast. Optimalizovaný kód je mnohem rychlejší, ale také může být výrazně méně přesný nebo i není správný.

Některé z těchto pravidel algebraických (unsafe) může být použit podle okně Optimalizace když je povolený režim fp:fast:

|||
|-|-|
|Formulář|Popis|
|`(a + b) + c = a + (b + c)`|Asociativní pravidlo pro přidání|
|`(a * b) * c = a * (b * c)`|Asociativní pravidlo pro násobení|
|`a * (b + c) = a * b + b * c`|Distribuce násobení přes přidání|
|`(a + b)(a - b) = a * a - b * b`|Algebraických řešení|
|`a / b = a * (1 / b)`|Dělení multiplicative inverzní|
|`a * 1.0 = a, a / 1.0 = a`|Multiplikativní identity|
|`a ± 0.0 = a, 0.0 - a = -a`|Doplňkové identity|
|`a / a = 1.0, a - a = 0.0`|Zrušení|

Pokud je obzvláště problematické pro určité funkce optimalizace fp:fast, s plovoucí desetinnou čárkou režimu lze místně přepnout fp: přesné pomocí `float_control` – Direktiva pragma kompilátoru.

### <a name="order-of-floating-point-expression-evaluation-under-fpfast"></a>Pořadí vyhodnocení výrazu s plovoucí desetinnou čárkou v části fp:fast

Na rozdíl od fp: přesné, umožňuje fp:fast kompilátoru ke změně pořadí s plovoucí desetinnou čárkou operace, aby bylo dosaženo rychlejší kódu. Proto nemusí některé optimalizace pod fp:fast zachovat zamýšlené order výrazů. Zvažte následující funkce, která vypočítá tečkou součin dvou n dimenzí vektory.

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

V části fp:fast, mohou provádět Optimalizátor skalární snížení `dotProduct` funkce efektivně transformace funkce následujícím způsobem:

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

Ve verzi optimalizované funkce jsou čtyři samostatný produkt panelu provést současně a pak přidá společně. Tato optimalizace můžete urychlit výpočet z `dotProduct` pomocí méně než mohou být faktor čtyři v závislosti na cílový procesor, ale konečný výsledek tak nepřesné, vykreslení nepoužitelné. Pokud tyto optimalizace jsou obzvláště problematické jedné funkce nebo překlad jednotky, s plovoucí desetinnou čárkou režimu lze místně přepnout fp: přesné pomocí `float_control` – Direktiva pragma kompilátoru.

## <a name="the-fpstrict-mode-for-floating-point-semantics"></a>Fp: striktní režim pro sémantiku s plovoucí desetinnou čárkou

Když fp: striktní režim zapnutý, kompilátor dodržuje stejné pravidla této fp: přesné používá při optimalizaci operace s plovoucí desetinnou čárkou. Tento režim taky umožňuje sémantiku výjimek plovoucí desetinné čárky a citlivost na FPU prostředí a zakáže určité optimalizace například staženiny. Je nejpřísnějším provozní režim.

Fp: striktní režim s plovoucí desetinnou čárkou je povolit pomocí [/fp: striktní](fp-specify-floating-point-behavior.md) přepínač příkazového řádku kompilátoru následujícím způsobem:

> cl /fp: striktní source.cpp

Tento příklad dává pokyn kompilátoru používat fp: striktní sémantiku při generování kódu pro soubor source.cpp. Fp: striktní modelu lze také vyvolat na jednotlivých pomocí funkcí pomocí `float_control` – Direktiva pragma kompilátoru.

Další informace najdete v tématu [float_control – Direktiva pragma](#the-float-control-pragma).

V části fp: striktní režim kompilátor nikdy provede všechny optimalizace, které perturb přesnost výpočty s plovoucí desetinnou čárkou. Kompilátor vždy zaokrouhlí správně v přiřazení, přiřadí typ ukazatel a volání funkce a zprostředkující zaokrouhlení konzistentně proběhne na stejné přesnost jako FPU Registry. Ve výchozím nastavení jsou povolené sémantiku výjimek plovoucí desetinné čárky a FPU prostředí velkých a malých písmen. Některé optimalizace, jako je například staženiny, jsou zakázané, protože kompilátor nemůže zaručit správnost v každém případě.

|FP: striktní sémantiku|Vysvětlení|
|-|-|
|Zaokrouhlení sémantiku|Explicitní zaokrouhlení v přiřazení, přiřadí typ ukazatel a volání funkce<br/>Zprostředkující výrazy se vyhodnotí na přesnost registrace.<br/>Stejné jako fp: přesné|
|Algebraických transformace|Stoprocentní asociativní, jiný obchod s plovoucí desetinnou čárkou algebra, pokud transformace záruku, že vždy získáte stejné výsledky.<br/>Stejné jako fp: přesné|
|Staženiny|Vždy zakázáno|
|Pořadí vyhodnocení s plovoucí desetinnou čárkou|Kompilátor nezmění pořadí vyhodnocení výrazů s plovoucí desetinnou čárkou|
|FPU prostředí přístup|Vždy povolena.|
|Sémantika výjimek plovoucí desetinné čárky|Ve výchozím nastavení povoleno.|

### <a name="floating-point-exception-semantics-under-fpstrict"></a>Sémantika výjimek plovoucí desetinné čárky pod fp: striktní

Ve výchozím nastavení, jsou povolené výjimek plovoucí desetinné čárky sémantiku pod fp: striktní modelu. Pokud chcete zakázat tyto sémantiku, použijte buď **/fp: kromě-** přepínač nebo zavést `float_control(except, off)` – Direktiva pragma.

Další informace najdete v části [povolení výjimek plovoucí desetinné čárky sémantiku](#enabling-floating-point-exception-semantics) a [float_control – direktiva Pragma](#the-float-control-pragma).

## <a name="the-fenvaccess-pragma"></a>Fenv_access – Direktiva pragma

Použití:

```cpp
#pragma fenv_access( [ on  | off ] )
```

[Fenv_access –](../../preprocessor/fenv-access.md) – Direktiva pragma umožňuje kompilátor, aby byl určité optimalizace, které může podkopat FPU příznak testy a FPU režim změny. Pokud stav `fenv_access` je zakázaná, můžete předpokládat kompilátor režimů FPU výchozí jsou platná a zda nejsou testovány FPU příznaky. Ve výchozím nastavení, prostředí přístup je zakázán pro fp: přesné režimu, i když může být explicitně povoleno, pomocí této – Direktiva pragma. V části fp: striktní, `fenv_access` je vždy povolena a nedá se zakázat. V části fp:fast `fenv_access` je vždy zakázané a nemůže být povolena.

Jak je popsáno v fp: přesné části některé programátory může změnit s plovoucí desetinnou čárkou pomocí směr zaokrouhlení `_controlfp` funkce. Třeba k výpočtu chyby horní a dolní hranice v aritmetické operace, některé programy proveďte výpočet dvakrát, nejprve při zaokrouhlení směrem záporné nekonečno, pak při zaokrouhlení směrem kladné nekonečno. Vzhledem k tomu, že FPU nabízí pohodlný způsob, jak řídit zaokrouhlení, programátorem rozhodnout změnit režim zaokrouhlení změnou FPU prostředí. Následující kód vypočítá, že chybu přesný hranice elementu s plovoucí desetinnou čárkou násobení změnou FPU prostředí.

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -infinity
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );       // round to +infinity
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

Pokud je zakázáno, `fenv_access` – Direktiva pragma umožňuje kompilátoru předpokládat, že prostředí FPU výchozí; proto je bezplatná ignorovat volání Optimalizátor `_controlfp` a snížit výše přiřazení `cUpper = cLower = a*b`. Když je povolené, ale `fenv_access` brání takové optimalizace.

Programy může také zkontrolovat stavového slova FPU ke zjištění určitým chybám s plovoucí desetinnou čárkou. Následující kód například vyhledá dělení nulou a nepřesný podmínky

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

Když `fenv_access` je zakázaná, může kompilátor změnit pořadí provádění výrazů s plovoucí desetinnou čárkou, proto pravděpodobně subverting FPU stav kontroly. Povolení `fenv_access` brání takové optimalizace.

## <a name="the-fpcontract-pragma"></a>Fp_contract – Direktiva pragma

Použití:

```cpp
#pragma fp_contract( [ on | off ] )
```

Jak je popsáno v fp: přesné části zmenšení je základní architektury funkce pro mnoho moderní jednotky s plovoucí desetinnou čárkou. Staženiny umožňují provádět násobení, následuje přidání jako najednou k žádné chybě zprostředkující zaokrouhlení. Tyto pokyny jednoho jsou rychleji než provádění samostatné násobení a přidat pokyny a jsou přesnější, protože neexistuje žádný zprostředkující zaokrouhlení produktu. Smluvní operace můžete vypočítá hodnotu `(a*b+c)` jako by byly obě operace vypočtenou hodnotu nekonečné přesnost a zaokrouhlí nejbližší číslo s plovoucí desetinnou čárkou. Tato optimalizace můžete výrazně urychlit funkce obsahující několik prokládaný násobkem a přidání operací. Zvažte například následující algoritmus, který vypočítá tečkou součin dvou n dimenzí vektory.

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

Tento výpočet lze provést řadu násobení přidat pokyny formuláře `p = p + x[i]*y[i]`.

[Fp_contract –](../../preprocessor/fp-contract.md) – Direktiva pragma Určuje, zda může být sjednané výrazy s plovoucí desetinnou čárkou. Ve výchozím nastavení fp: přesné režim umožňuje staženiny vzhledem k tomu, že zlepšit přesnost a rychlost. Pro režim fp:fast jsou povoleny vždy staženiny. Nicméně, protože staženiny můžete podkopat explicitní zjišťování chybové stavy `fp_contract` – Direktiva pragma není k dispozici vždy za fp: striktní režim. Příklady výrazů, které mohou být uzavřeny při `fp_contract` – Direktiva pragma zapnutá:

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

**/Fp: přesné**, **/fp:fast**, **/fp: striktní** a **/fp: kromě** přepínače řízení s plovoucí desetinnou čárkou sémantiku na soubor po souboru základ. [Float_control –](../../preprocessor/float-control.md) – Direktiva pragma poskytuje takové řízení na základě pomocí funkcí.

Použití:

```cpp
#pragma float_control(push)
#pragma float_control(pop)
#pragma float_control( precise, on | off [, push] )
#pragma float_control( except, on | off [, push] )
```

Pragmas `float_control(push)` a `float_control(pop)` v uvedeném pořadí vložit a aktuální stav režimu s plovoucí desetinnou čárkou a možnost výjimka do zásobníku. Všimněte si, že stav `fenv_access` a `fp_contract` – Direktiva pragma neovlivní `pragma float_control(push/pop)`.

Volání – Direktiva pragma `float_control(precise, on)` povolí a `float_control(precise, off)` vypne sémantiku přesné režimu. Podobně Direktiva pragma `float_control(except, on)` povolí a `float_control(except, off)` vypne sémantiku výjimka. Výjimka sémantiku lze povolit pouze pokud sémantiku přesné jsou také povolené. Když nepovinný `push` argument je k dispozici, stavy `float_control` možnosti odesílají před změna sémantiku.

### <a name="setting-the-floating-point-semantic-mode-on-a-function-by-function-basis"></a>Nastavení s plovoucí desetinnou čárkou sémantického režimu na základě podle funkcí

Přepínače příkazového řádku jsou ve skutečnosti sdružená vlastnost nastavující hodnoty čtyř různých s plovoucí desetinnou čárkou direktivy. Chcete-li explicitně zvolte konkrétní s plovoucí desetinnou čárkou sémantického režim na základě funkce funkce, vyberte všechny čtyři direktivy s plovoucí desetinnou čárkou možnost, jak je popsáno v následující tabulce:

||||||
|-|-|-|-|-|
||float_control(Precise)|float_control(EXCEPT)|fp_contract|fenv_access|
|/FP: striktní|on|on|Vypnout|on|
|/FP: striktní /fp: kromě-|on|Vypnout|Vypnout|on|
|/FP: přesné|on|Vypnout|on|Vypnout|
|/FP: přesné /fp: kromě|on|on|on|Vypnout|
|/FP:Fast|Vypnout|Vypnout|on|Vypnout|

Například následující explicitně umožňuje fp:fast sémantiku.

```cpp
#pragma float_control( except, off )   // disable exception semantics
#pragma float_control( precise, off )  // disable precise semantics
#pragma fp_contract(on)                // enable contractions
#pragma fenv_access(off)               // disable fpu environment sensitivity
```

> [!Note]
> Výjimka sémantiku musí být vypnutý předtím, než vypnete "přesné" sémantiku.

## <a name="enabling-floating-point-exception-semantics"></a>Povolení sémantiku výjimek plovoucí desetinné čárky

Určité výjimečných s plovoucí desetinnou čárkou podmínky, jako je například dělení nulou, může způsobit FPU signál výjimky hardwaru. Ve výchozím nastavení jsou zakázány s plovoucí desetinnou čárkou výjimky. S plovoucí desetinnou čárkou výjimky jsou povolené změnou FPU kontrolní slovo s `_controlfp` funkce. Následující kód například umožňuje výjimek plovoucí desetinné čárky dělení nulou:

```cpp
_clearfp(); // always call _clearfp before
            // enabling/unmasking a FPU exception
_controlfp( _EM_ZERODIVIDE, _MCW_EM );
```

Při dělení nulou výjimka je povoleno, všechny operace dělení s jmenovatel rovná nule, způsobí výjimku FPU signál.

Chcete-li obnovit FPU kontrolní slovo výchozí režim, volejte `_controlfp(_CW_DEFAULT, ~0)`.

Povolení výjimek plovoucí desetinné čárky sémantiku s **/fp: kromě** příznak není totéž jako povolení s plovoucí desetinnou čárkou výjimky. Pokud sémantiku výjimek plovoucí desetinné čárky jsou povolené, kompilátor musí odpovídat možnost, všechny operace s plovoucí desetinnou čárkou může vyvolat výjimku. Vzhledem k tomu, že FPU je jednotka samostatné procesoru, pokyny provádění na FPU lze provádět souběžně pokyny na jiné jednotky.

Pokud je povoleno výjimek plovoucí desetinné čárky, bude FPU zastavení provádění problematické pokyn a pak signál podmínku výjimečných nastavením FPU stavového slova. Pokud procesor dosáhne další s plovoucí desetinnou čárkou pokyn, nejprve zkontroluje pro čekající FPU výjimky. Pokud existuje čekající výjimky, procesor ho traps voláním obslužnou rutinu výjimky, které poskytuje operační systém. To znamená, že při operaci s plovoucí desetinnou čárkou, zaznamená se výjimečně vysoké počty podmínka, odpovídající výjimce nebudou zjištěna, dokud provedením další operace s plovoucí desetinnou čárkou. Například následující kód traps dělení nulou výjimka:

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

Pokud dojde k podmínku dělení nulou ve výrazu b, c = FPU nebude depeše/vyvolat výjimku až další operace s plovoucí desetinnou čárkou ve výrazu 2.0 * b. Výsledkem je následující výstup:

```Output
This line shouldn't be reached when c==0.0
SEH Exception Detected
```

Printf odpovídající první řádek výstupu by neměl bylo dosaženo; bylo dosaženo, protože s plovoucí desetinnou čárkou výjimka způsobené výraz b, c nebyla vyvolána, dokud provádění dosaženo 2.0 * b. Pro vyvolání výjimky jenom po provedení b, c, kompilátor musí zavádět instrukce "Čekání":

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

Tento pokyn "Počkejte" vynutí procesor pro synchronizaci se stavem FPU a zpracování všech výjimek, čekající na vyřízení. Kompilátor vygeneruje jenom tyto "Počkejte" pokyny pokud sémantiku s plovoucí desetinnou čárkou jsou povolené. Když tyto sémantiku jsou zakázané, protože jsou ve výchozím nastavení, programy setkat synchronicity chyby podobné výše, při použití s plovoucí desetinnou čárkou výjimky.

Pokud sémantiku s plovoucí desetinnou čárkou jsou povolené, kompilátor pouze nezavedou "Čekání" pokyny, nebude také možné kompilátor nelegálního optimalizace s plovoucí desetinnou čárkou kódu případě možné výjimky. To zahrnuje všechny transformace, které se příkazu alter body, na kterých jsou výjimky vyvolány. Z důvodu tyto faktory mohou povolení s plovoucí desetinnou čárkou sémantiku výrazně snížit efektivitu generovaný kód počítače proto došlo ke snížení výkonu aplikace.

Sémantika výjimek plovoucí desetinné čárky jsou povolené ve výchozím nastavení v části fp: striktní režim. Chcete-li povolit tyto sémantiku ve formátu: přesné režimu, přidat **/fp: kromě** přepínače kompilátoru příkazového řádku. Sémantika výjimek plovoucí desetinné čárky také lze povolit a zakázat v jednotlivých pomocí funkcí pomocí `float_control` – Direktiva pragma.

### <a name="floating-point-exceptions-as-c-exceptions"></a>S plovoucí desetinnou čárkou výjimky jako výjimky jazyka C++

Jako s všechny výjimky hardwaru, s plovoucí desetinnou čárkou výjimky vnitřně nezpůsobí výjimku C++, ale místo toho aktivovat strukturovaného výjimek. Mapovat s plovoucí desetinnou čárkou strukturovaných výjimky výjimky jazyka C++, uživatelé můžou představovat vlastní překladač výjimka SEH. Nejprve zavést odpovídající každé výjimek plovoucí desetinné čárky C++ výjimka:

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

Potom zavést překlad funkci, která bude zjišťovat s plovoucí desetinnou čárkou SEH výjimky a výjimku odpovídající výjimce C++. Chcete-li tuto funkci použít, nastavte překladač obslužná rutina strukturovaná výjimky pro aktuální vlákno proces s [_set_se_translator –](../../c-runtime-library/reference/set-se-translator.md) funkce z knihovny za běhu.

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

Po inicializaci toto mapování s plovoucí desetinnou čárkou výjimky budou chovat, jako by byly výjimky jazyka C++. Příklad:

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

[Co každý počítač vědecký pracovník byste se měli seznámit s plovoucí desetinnou čárkou aritmetické](http://pages.cs.wisc.edu/~david/courses/cs552/S12/handouts/goldberg-floating-point.pdf) podle David Goldberg.

## <a name="see-also"></a>Viz také

[Optimalizace kódu](optimizing-your-code.md)<br/>
