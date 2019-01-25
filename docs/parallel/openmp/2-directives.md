---
title: 2. Direktivy
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: bf96d5ee6963a76c2b2462d5b3a0639c1141ea15
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894239"
---
# <a name="2-directives"></a>2. Direktivy

Direktivy jsou založeny na `#pragma` direktivy definované ve standardech C a C++.  Kompilátory, které podporují OpenMP – C a C++ API bude zahrnovat možnost příkazového řádku, který aktivuje a umožňuje výklad všechny direktivy OpenMP kompilátoru.

## <a name="21-directive-format"></a>2.1 formát direktivy

Syntaxe direktivy OpenMP formálně určené gramatiku v [dodatku C](c-openmp-c-and-cpp-grammar.md)a neformálně následujícím způsobem:

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

Jednotlivé direktivy začíná `#pragma omp`, abyste snížili riziko je v konfliktu s další direktivy pragma (-OpenMP – nebo dodavatele rozšíření OpenMP) se stejnými názvy. Zbytek této direktivy dodržovat konvence standardů C a C++ pro direktivy kompilátoru. Zejména prázdné místo je možné před a po `#`, a v některých případech prázdné místo musí použít k oddělení slov v direktivě. Následující tokeny předzpracování `#pragma omp` se vztahují nahrazení makra.

Direktivy jsou malá a velká písmena. Pořadí, v jakém klauzule uvedeny ve směrnicích není důležité. Klauzule direktivami může opakovat podle potřeby vztahují omezení uvedená v popisu jednotlivým klauzulím. Pokud *seznamu proměnné* se zobrazí v klauzuli, musí určovat pouze proměnné. Pouze jeden *název směrnice* jednu direktivu lze určit.  Například následující direktiva není dovolená:

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

Direktivě OpenMP se vztahuje na maximálně jeden následující příkaz, který musí být strukturovaný blok.

## <a name="22-conditional-compilation"></a>2.2 Podmíněná kompilace

`_OPENMP` – Makro název je definován implementací CLS OpenMP jako desítkovou konstantu *yyyymm*, která bude roku a měsíce specifikace schválené. Toto makro nesmí být předmět `#define` nebo `#undef` direktiva předzpracování.

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Pokud dodavatelů definovat rozšíření pro OpenMP, určují další předdefinovaná makra.

## <a name="23-parallel-construct"></a>2.3 parallel – konstrukce

Následující direktiva definuje paralelní oblasti, která je oblast programu, který se má provádět mnoho vláken současně. Tato direktiva je základní koncept, který se spustí paralelní zpracování.

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*Klauzule* je jedním z následujících akcí:

- `if(` *Skalární výraz* `)`
- `private(` *Proměnná list* `)`
- `firstprivate(` *Proměnná list* `)`
- `default(shared | none)`
- `shared(` *Proměnná list* `)`
- `copyin(` *Proměnná list* `)`
- `reduction(` *operátor* `:` *seznamu proměnné*  `)`
- `num_threads(` *integer-expression* `)`

Když vlákno dostane do paralelní konstrukce, tým vláken se vytvoří, pokud je splněna jedna z následujících případech:

- Ne `if` je přítomna klauzule.
- `if` Výraz vyhodnocen nenulovou hodnotu.

Toto vlákno se stane hlavní vlákno tým s počtem vláken 0, a všechna vlákna v týmu, včetně hlavní vlákno paralelně spustit oblast. Pokud hodnota `if` výraz je nula, je serializován v oblasti.

Pokud chcete zjistit počet vláken, které jsou požadovány, tato pravidla se budou považovat za v pořadí. První pravidlo, jehož podmínka je splněna se použijí:

1. Pokud `num_threads` je přítomna klauzule, pak hodnota celočíselný výraz je počet vláken požadovaný.

1. Pokud `omp_set_num_threads` byla volána funkce knihovny, pak je počet vláken požadované hodnoty argumentu v nedávno provedených volání.

1. Pokud proměnná prostředí `OMP_NUM_THREADS` je definována hodnota této proměnné prostředí je počet vláken požadovaný.

1. Pokud žádná z výše uvedených metod se používá, počet vláken požadovaný je definováno implementací.

Pokud `num_threads` je přítomna klauzule pak nahrazuje počet vláken požadoval `omp_set_num_threads` funkce knihovny nebo `OMP_NUM_THREADS` proměnné prostředí pouze pro paralelní oblasti, použije se na. Později paralelních oblastí nejsou vliv.

Počet vláken, které jsou spouštěny paralelní oblasti také závisí na tom, zda je povolena dynamické úpravy počtu vláken. Pokud je zakázané dynamické úpravy, požadovaný počet vláken spustí paralelní oblasti. Pokud je povolené dynamické úpravy požadovaný počet vláken je maximální počet vláken, která se dá provádět paralelní oblasti.

Pokud při dynamické úpravy počtu vláken je zakázaná, a počet vláken, které jsou požadované pro paralelní oblasti je větší než číslo, které můžete zadat systému za běhu je zjištěna paralelní oblasti, je chování programu definované implementací. Implementace může například přerušit provádění programu, nebo ji může serializovat paralelní oblasti.

`omp_set_dynamic` Funkce knihovny a `OMP_DYNAMIC` proměnnou prostředí je možné povolit nebo zakázat dynamické úpravy počtu vláken.

Počet fyzických procesorů ve skutečnosti hostování vlákna v daném okamžiku je definován implementací. Po vytvoření zůstává po dobu trvání tohoto paralelní oblasti konstantní počet vláken v týmu. Lze jej změnit buď explicitně uživatelem, nebo automaticky za běhu systému z jedné paralelní oblasti do jiného.

Příkazy obsažené v dynamický rozsah paralelní oblasti jsou spouštěny jednotlivými vlákny a každé vlákno může spustit cestu příkazy, které se liší od jiných vláken. Došlo k mimo lexikální rozsah paralelní oblasti direktivy jsou označovány jako osamocený direktivy.

Není k dispozici implicitní barrier na konci paralelní oblasti. Pouze hlavní vlákno tým pokračuje v provádění na konci paralelní oblasti.

Pokud vlákno v tým provádí paralelní oblasti zaznamená jiné paralelní konstrukce, vytvoří nový tým a stane se hlavní tento nový tým. Ve výchozím nastavení jsou serializovat vnořený paralelních oblastí. Ve výchozím nastavení, proto vnořené paralelní oblasti provádí týmem, který se skládá z jednoho vlákna. Výchozí chování může změnit pomocí funkce knihovny prostředí runtime `omp_set_nested` nebo proměnnou prostředí `OMP_NESTED`. Počet vláken v týmu, které jsou spuštěny paralelní vnořené oblasti je však definován implementací.

Omezení `parallel` směrnice jsou následující:

- Maximálně jednu `if` klauzule se může objevit v direktivě.

- To má tento parametr zadán, zda všechny na straně účinky uvnitř if výraz nebo `num_threads` dojde k výraz.

- A `throw` provést uvnitř paralelní oblasti musíte zajistit, aby v provádění pokračovat v rámci dynamický rozsah stejné strukturovaný blok, a musí být zachycena ve stejném vlákně, které vyvolalo výjimku.

- Pouze jeden `num_threads` klauzule se může objevit v direktivě. `num_threads` Výraz je vyhodnocen mimo kontext paralelní oblasti a musí být kladná celočíselná hodnota.

- Pořadí vyhodnocování `if` a `num_threads` není zadána klauzule.

### <a name="cross-references"></a>Křížové odkazy

- `private`, `firstprivate`, `default`, `shared`, `copyin`, a `reduction` klauzule ([části 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_NUM_THREADS](4-2-omp-num-threads.md) proměnné prostředí
- [omp_set_dynamic –](3-1-7-omp-set-dynamic-function.md) funkce knihovny
- [OMP_DYNAMIC](4-3-omp-dynamic.md) proměnné prostředí
- [omp_set_nested –](3-1-9-omp-set-nested-function.md) – funkce
- [OMP_NESTED](4-4-omp-nested.md) proměnné prostředí
- [omp_set_num_threads –](3-1-1-omp-set-num-threads-function.md) funkce knihovny

## <a name="24-work-sharing-constructs"></a>2.4 konstrukce pro sdílení práce

Konstruktoru work-sharing distribuuje provádění asociovaný příkaz mezi členy týmu, na které ho. Direktiv pro sdílení práce není spuštění nového vlákna a neexistuje žádný implicitní bariéry při vstupu do konstruktoru work-sharing.

Vytvoří posloupnost sdílení práce a `barrier` direktivy došlo k musí být stejná pro každé vlákno v týmu.

OpenMP – definuje následující konstrukce pro sdílení práce, a tyto konstruktory jsou popsány v následující části:

- [pro](#241-for-construct) – direktiva
- [oddíly](#242-sections-construct) – direktiva
- [jeden](#243-single-construct) – direktiva

### <a name="241-for-construct"></a>2.4.1 for – konstrukce

`for` – Direktiva určuje iterativní konstruktoru work-sharing, která určuje, že iterací smyčky související se spustí paralelně. Iterace `for` smyčky jsou distribuovány napříč vlákny, které již existují v týmu provádí paralelní konstrukce, ke kterému se váže. Syntaxe `for` konstruktor je následujícím způsobem:

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

V klauzuli je jedním z následujících akcí:

- `private(` *Proměnná list* `)`
- `firstprivate(` *Proměnná list* `)`
- `lastprivate(` *Proměnná list* `)`
- `reduction(` *operátor* `:` *seznamu proměnné* `)`
- `ordered`
- `schedule(` *druh* [`,` *chunk_size*] `)`
- `nowait`

`for` Směrnice umístí omezení na strukturu odpovídající `for` smyčky. Konkrétně odpovídající `for` smyčky musí mít kanonický tvar:

`for (` *Init-expr* `;` *var logické op b* `;` *incr – výraz* `)`

*init-expr*<br/>
Jeden z následujících postupů:

- *var* = *lb*
- *integer-type var* = *lb*

*incr-expr*<br/>
Jeden z následujících postupů:

- `++` *var*
- *var* `++`
- `--` *var*
- *var* `--`
- *var* `+=` *incr*
- *var* `-=` *incr*
- *var* `=` *var* `+` *incr*
- *var* `=` *incr* `+` *var*
- *var* `=` *var* `-` *incr*

*var*<br/>
Proměnná celé číslo se znaménkem. Pokud tato proměnná by jinak sdílet, je implicitně k privátní po dobu trvání `for`. Neprovádějte žádné změny této proměnné v těle `for` příkazu. Pokud není zadána proměnná `lastprivate`, jeho hodnota po neurčitou smyčky.

*logical-op*<br/>
Jeden z následujících postupů:

- `<`
- `<=`
- `>`
- `>=`

*LB*, *b*, a *incr*<br>
Smyčka výrazy invariantní celé číslo. Neexistuje žádná synchronizace během vyhodnocování těchto výrazů, takže všechny vyhodnocené vedlejší účinky neurčitý výsledky.

Kanonický tvar umožňuje počtu iterací smyčky vypočítání při vstupu do smyčky. Tento výpočet se provádí s hodnotami typu *var*, po zvýšení úrovně celého čísla. V případě hodnoty *b* `-` *lb* `+` *incr* nemůže být vyjádřena v tom, že typ výsledku je neurčité. Další, pokud *logické op* je `<` nebo `<=`, pak *incr expr* musíte zajistit, aby *var* zvýšit při každé iteraci smyčky.   Pokud *logické op* je `>` nebo `>=`, pak *incr expr* musíte zajistit, aby *var* získat menší při každé iteraci smyčky.

`schedule` Klauzule určuje, jak iterací `for` smyčky jsou rozděleny mezi vlákny týmu. Správnost programu nesmí být závislá na které vlákno provede konkrétní iteraci. Hodnota *chunk_size*, je-li zadána, musí být výraz smyčky invariantní celé číslo s kladnou hodnotu. Neexistuje žádná synchronizace během vyhodnocení tohoto výrazu, takže všechny vyhodnocené vedlejší účinky neurčitý výsledky. Plán *druh* může být jedna z následujících hodnot:

Tabulka 2-1: `schedule` klauzule *druh* hodnoty

|||
|-|-|
|static|Když `schedule(static,` *chunk_size* `)` je zadaný počet iterací jsou rozdělené do bloků velikosti určené *chunk_size*. Bloky dat se staticky přiřadí vlákna v týmu v vždy střídat dokola v pořadí podle počtu vláken. Pokud ne *chunk_size* určena, iteraci místo je rozděleno do bloků dat, které jsou přibližně stejnou velikost, s jeden blok přiřazená každé vlákno.|
|dynamické odkazy|Když `schedule(dynamic,` *chunk_size* `)` je zadaný počet iterací jsou rozdělené do řady bloků, každý obsahující *chunk_size* iterací. Každý blok je přiřazená vlákna, který čeká na přiřazení. Vlákno provede blok iterací a pak počká na další zadání žádné bloky dat i nadále možné přiřadit. Poslední blok dat, který má být přiřazena může mít menší počet iterací. Pokud ne *chunk_size* není zadán, výchozí hodnotu 1.|
|s asistencí|Když `schedule(guided,` *chunk_size* `)` je zadaný počet iterací jsou přiřazená vlákna v blocích s snížení velikosti. Po dokončení své přiřazené bloku iterací vlákno jí dynamicky přiřazena jiného bloku, dokud je ponecháno žádné. Pro *chunk_size* 1, velikost každého bloku je přibližně počet nepřiřazených iterací vydělí počtem vláken. Tyto velikosti téměř exponenciálně zmenšit na hodnotu 1. Pro *chunk_size* s hodnotou *k* větší než 1, téměř exponenciálně pro snížení velikosti *k*, s tím rozdílem, že poslední blok dat může být kratší než *k* iterací. Pokud ne *chunk_size* není zadán, výchozí hodnotu 1.|
|modul runtime|Když `schedule(runtime)` není zadána, rozhodnutí týkající se plánování je odložena až do modulu runtime. Plán *druh* a velikost bloky dat může být vybrána v době běhu nastavením proměnné prostředí `OMP_SCHEDULE`. Pokud tato proměnná prostředí není nastavená, výsledný plán je definován implementací. Když `schedule(runtime)` není zadána, *chunk_size* nesmí být zadaný.|

Chybí explicitně definovanou `schedule` klauzule, výchozí `schedule` je definováno implementací.

Aplikace kompatibilní s OpenMP neměli byste tedy spoléhat na konkrétní plán pro správné spuštění. Program, neměli byste tedy spoléhat na plánu *druh* odpovídající přesně popisu výše uvedené, protože je možné mít odchylky v implementacích stejného plánu *druh* napříč Různé kompilátory. Popis je možné vybrat plán, který je vhodný pro konkrétní situaci.

`ordered` Klauzule musí být použit, pokud `ordered` direktivy svázat `for` vytvořit.

Na konci je implicitní bariéry `for` vytvořit, není-li `nowait` není zadána klauzule.

Omezení `for` směrnice jsou následující:

- `for` Smyčky musí být strukturovaný blok, a kromě toho nesmí být jeho spuštění ukončen `break` příkazu.

- Hodnoty smyčky řídit výrazy `for` smyčky přidružené `for` direktiva musí být stejný pro všechny vlákna v týmu.

- `for` Proměnná iterace smyčky musí být typu celé číslo se znaménkem.

- Pouze jeden `schedule` klauzule se může objevit v `for` směrnice.

- Pouze jeden `ordered` klauzule se může objevit v `for` směrnice.

- Pouze jeden `nowait` klauzule se může objevit v `for` směrnice.

- Je neurčená if nebo jak často se žádné vedlejší efekty v rámci *chunk_size*, *lb*, *b*, nebo *incr* výrazy dojít.

- Hodnota *chunk_size* výraz musí být stejný pro všechny vlákna v týmu.

#### <a name="cross-references"></a>Křížové odkazy

- `private`, `firstprivate`, `lastprivate`, a `reduction` klauzule ([části 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_SCHEDULE](4-1-omp-schedule.md) proměnné prostředí
- [seřazené](#266-ordered-construct) sestavení
- [plán](d-using-the-schedule-clause.md) – klauzule

### <a name="242-sections-construct"></a>2.4.2 oddíly konstrukce

`sections` – Direktiva určuje noniterative konstruktoru work-sharing, který určuje sadu konstrukce, které jsou k rozdělení mezi vlákny v týmu. Každá část je spuštěna jednou vláknem v týmu. Syntaxe `sections` direktivy je následující:

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

V klauzuli je jedním z následujících akcí:

- `private(` *Proměnná list* `)`
- `firstprivate(` *Proměnná list* `)`
- `lastprivate(` *Proměnná list* `)`
- `reduction(` *operátor* `:` *seznamu proměnné*  `)`
- `nowait`

Každý oddíl předchází `section` směrnice, i když `section` – direktiva je nepovinné pro první část. `section` Direktivy musí být použit v lexikálním rozsahu `sections` směrnice. Na konci je implicitní bariéry `sections` sestavit, pokud `nowait` určena.

Omezení `sections` směrnice jsou následující:

- A `section` – direktiva nesmí objevit mimo lexikální rozsah `sections` směrnice.

- Pouze jeden `nowait` klauzule se může objevit v `sections` směrnice.

#### <a name="cross-references"></a>Křížové odkazy

- `private`, `firstprivate`, `lastprivate`, a `reduction` klauzule ([části 2.7.2](#272-data-sharing-attribute-clauses))

### <a name="243-single-construct"></a>2.4.3 single – konstrukce

`single` – Direktiva určuje konstrukce, která určuje, že přidružené strukturovaný blok provádí pouze jedno vlákno v týmu (ne tedy nutně hlavní vlákno). Syntaxe `single` direktivy je následující:

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

V klauzuli je jedním z následujících akcí:

- `private(` *Proměnná list* `)`
- `firstprivate(` *Proměnná list* `)`
- `copyprivate(` *Proměnná list* `)`
- `nowait`

Je implicitní barrier po `single` vytvořit, není-li `nowait` není zadána klauzule.

Omezení `single` směrnice jsou následující:

- Pouze jeden `nowait` klauzule se může objevit v `single` směrnice.
- `copyprivate` Klauzule se nesmí používat s `nowait` klauzuli.

#### <a name="cross-references"></a>Křížové odkazy

- `private`, `firstprivate`, a `copyprivate` klauzule ([části 2.7.2](#272-data-sharing-attribute-clauses))

## <a name="25-combined-parallel-work-sharing-constructs"></a>2.5 kombinované paralelní konstrukce pro sdílení práce

Kombinované paralelní konstrukce pro sdílení práce jsou zástupci pro určení, který má pouze jeden konstruktoru work-sharing paralelní oblasti. Sémantika tyto směrnice jsou stejné jako pro explicitní určení `parallel` směrnice následovaný jeden konstruktoru work-sharing.

Následující části popisují kombinované paralelní konstrukce pro sdílení práce:

- [paralelní pro](#251-parallel-for-construct) – direktiva
- [Parallel sections –](#252-parallel-sections-construct) – direktiva

### <a name="251-parallel-for-construct"></a>2.5.1 parallel for – konstrukce

`parallel for` – Direktiva je zkratka pro `parallel` oblast, která obsahuje pouze jedinou `for` směrnice. Syntaxe `parallel for` direktivy je následující:

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Tato direktiva umožňuje všechny klauzulích `parallel` směrnice a `for` direktiv, s výjimkou `nowait` klauzule identické význam a omezení. Sémantika je stejný jako explicitní určení `parallel` směrnice okamžitě následovat `for` – direktiva.

#### <a name="cross-references"></a>Křížové odkazy

- [paralelní](#23-parallel-construct) – direktiva
- [pro](#241-for-construct) – direktiva
- [Klauzule atributů pro data](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>2.5.2 parallel oddíly konstrukce

`parallel sections` – Direktiva poskytuje místní formulář pro zadávání `parallel` oblasti, která má pouze jeden `sections` směrnice. Sémantika je stejný jako explicitní určení `parallel` směrnice okamžitě následovat `sections` – direktiva. Syntaxe `parallel sections` direktivy je následující:

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*Klauzule* může být jedna z klauzule přijal `parallel` a `sections` direktivy, s výjimkou `nowait` klauzuli.

#### <a name="cross-references"></a>Křížové odkazy

- [paralelní](#23-parallel-construct) – direktiva
- [oddíly](#242-sections-construct) – direktiva

## <a name="26-master-and-synchronization-directives"></a>2.6 hlavní a synchronizační direktivy

V následujících částech:

- [hlavní](#261-master-construct) sestavení
- [kritické](#262-critical-construct) sestavení
- [bariéra](#263-barrier-directive) – direktiva
- [Atomic](#264-atomic-construct) sestavení
- [vyprázdnění](#265-flush-directive) – direktiva
- [seřazené](#266-ordered-construct) sestavení

### <a name="261-master-construct"></a>2.6.1 master – konstrukce

`master` – Direktiva určuje konstrukce, která určuje strukturovaný blok, který se spouští hlavní vlákno týmu. Syntaxe `master` direktivy je následující:

```cpp
#pragma omp master new-linestructured-block
```

Ostatní vlákna v týmu není spuštění přidružené strukturovaný blok. Neexistuje žádný implicitní barrier buď na položku a nebo opuštění master – konstrukce.

### <a name="262-critical-construct"></a>2.6.2 critical – konstrukce

`critical` – Direktiva určuje konstrukce, která omezuje spuštění přidružené strukturovaný blok na jedno vlákno v čase. Syntaxe `critical` direktivy je následující:

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

Volitelně *název* slouží k identifikaci důležité oblasti. Identifikátory, které slouží k identifikaci důležité oblasti mají vnější propojení a jsou v oboru názvů, která je oddělená od obory názvů používané popisky, značky, členy a běžnými identifikátory.

Vlákno čeká na začátku důležité oblasti žádné vlákno provádí důležité oblasti (kdekoli v programu) se stejným názvem. Všechny nepojmenované `critical` direktivy namapovat na stejnou neurčené název.

### <a name="263-barrier-directive"></a>2.6.3 barrier – direktiva

`barrier` – Direktiva synchronizuje všechna vlákna v týmu. Vyskytne-li tuto možnost, každé vlákno v týmu čeká na všechny ostatní dosáhli tohoto bodu. Syntaxe `barrier` direktivy je následující:

```cpp
#pragma omp barrier new-line
```

Po všech vláken v týmu došlo k bariéry, začne každé vlákno v týmu, spouštět příkazy po barrier – direktiva paralelně. Vzhledem k tomu, `barrier` nemá direktivě příkaz jazyka C jako součást syntaxe, platí určitá omezení na jeho umístění v rámci programu. Další informace o formální gramatiku, naleznete v tématu [dodatku C](c-openmp-c-and-cpp-grammar.md). Následující příklad znázorňuje tato omezení.

```cpp
/* ERROR - The barrier directive cannot be the immediate
*          substatement of an if statement
*/
if (x!=0)
   #pragma omp barrier
...

/* OK - The barrier directive is enclosed in a
*      compound statement.
*/
if (x!=0) {
   #pragma omp barrier
}
```

### <a name="264-atomic-construct"></a>2.6.4 atomic – konstrukce

`atomic` Směrnice zajišťuje atomicky, aktualizaci umístění konkrétní paměťové místo vystavení možnost více souběžných vláken pro zápis. Syntaxe `atomic` direktivy je následující:

```cpp
#pragma omp atomic new-lineexpression-stmt
```

Příkaz výrazu musí mít jednu z následujících forem:

- *x binop* `=` *výraz*
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

V předchozích výrazů:

- *x* je výraz l-hodnota s skalárního typu.

- *výraz* je výraz s skalárního typu a neodkazuje objektu určeném *x*.

- *binop* není přetíženého operátoru a je jedním z `+`, `*`, `-`, `/`, `&`, `^`, `|`, `<<`, nebo `>>`.

I když je definováno implementací Určuje, zda implementace nahradí všechny `atomic` direktivy s `critical` direktivy, které mají stejný jedinečný *název*, `atomic` povolení lepší optimalizace – direktiva . Často hardwarové pokyny jsou k dispozici, které můžete provádět atomické aktualizace s minimálními nároky.

Zatížení a úložiště objektu určeném *x* jsou atomické, vyhodnocení *expr* není atomické. Aby nedošlo ke konfliktům časování, by měly být chráněné všechny aktualizace umístění paralelně s `atomic` direktiv, kromě těch, které jsou známé jako zdarma ke konfliktům časování.

Omezení `atomic` směrnice jsou následující:

- Musí mít kompatibilní typ atomic všude, kde x umístění úložiště v celém programu.

#### <a name="examples"></a>Příklady

```cpp
extern float a[], *p = a, b;
/* Protect against races among multiple updates. */
#pragma omp atomic
a[index[i]] += b;
/* Protect against races with updates through a. */
#pragma omp atomic
p[i] -= 1.0f;

extern union {int n; float x;} u;
/* ERROR - References through incompatible types. */
#pragma omp atomic
u.n++;
#pragma omp atomic
u.x -= 1.0f;
```

### <a name="265-flush-directive"></a>2.6.5 flush – direktiva

`flush` Direktiva, zda explicitní nebo implicitní, určuje bod sekvence "mezi vlákny" jakou implementace je potřeba k tomu, že všechna vlákna v týmu mají konzistentní zobrazení určité objekty (uvedené níže) v paměti. To znamená, že předchozí vyhodnocení výrazů, které odkazují na tyto objekty jsou dokončeny, a ještě nezačali následné hodnocení. Například kompilátory musíte obnovit hodnoty objekty z registrů na paměť a hardware mohou potřebovat k vyprázdnění vyrovnávacích pamětí zápisu na paměť a znovu načíst hodnoty objekty z paměti.

Syntaxe `flush` direktivy je následující:

```cpp
#pragma omp flush [(variable-list)]  new-line
```

Pokud objekty, které vyžadují synchronizaci můžete všechny označeny proměnné a pak tyto proměnné lze zadat volitelný *seznamu proměnné*. Pokud je k dispozici v ukazatel *seznamu proměnné*, vyprázdní ukazatel sám, nikoli objekt ukazatel odkazuje na.

A `flush` direktiv bez *seznamu proměnné* synchronizuje všechny sdílené objekty s výjimkou v případě nepřístupných objektů s automatickým trváním úložiště. (To je pravděpodobně mají další režii než kolekce `flush` s *seznamu proměnné*.) A `flush` direktiv bez *seznamu proměnné* implicitní pro následující direktivy:

- `barrier`
- Na vstupu a výstupu z `critical`
- Na vstupu a výstupu z `ordered`
- Na vstupu a výstupu z `parallel`
- Při ukončení z `for`
- Při ukončení z `sections`
- Při ukončení z `single`
- Na vstupu a výstupu z `parallel for`
- Na vstupu a výstupu z `parallel sections`

Direktiva není zahrnuta, pokud `nowait` je přítomna klauzule. Je třeba poznamenat, který `flush` – direktiva není určen pro některý z následujících akcí:

- Vstup `for`
- Položky nebo ukončení `master`
- Vstup `sections`
- Vstup `single`

Odkaz, který přistupuje k hodnotě objektu s typem přechodný se chová jako by byly `flush` směrnice zadání tohoto objektu na předchozí bod sekvence. Odkaz, který změní hodnotu objektu s typem přechodný se chová jako by byly `flush` směrnice zadání tohoto objektu v okamžiku, následné pořadí.

Vzhledem k tomu, `flush` nemá direktivě příkaz jazyka C jako součást syntaxe, platí určitá omezení na jeho umístění v rámci programu. Další informace o formální gramatiku, naleznete v tématu [dodatku C](c-openmp-c-and-cpp-grammar.md). Následující příklad znázorňuje tato omezení.

```cpp
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

Omezení `flush` směrnice jsou následující:

- Zadané v proměnné `flush` direktiva nesmí mít typ odkazu.

### <a name="266-ordered-construct"></a>2.6.6 pořadí konstrukce

Následující strukturovaný blok `ordered` – direktiva je provedeny v pořadí, ve kterém by byl proveden iterací v sekvenčních smyčkách. Syntaxe `ordered` direktivy je následující:

```cpp
#pragma omp ordered new-linestructured-block
```

`ordered` Direktiva musí být v rámci dynamický rozsah `for` nebo `parallel for` vytvořit. `for` Nebo `parallel for` direktiv, ke kterému `ordered` musí mít konstruktor vytvoří vazbu `ordered` klauzule zadat, jak je popsáno v [části 2.4.1](#241-for-construct). Za běhu `for` nebo `parallel for` vytvořit pomocí `ordered` klauzule `ordered` konstrukce jsou striktně provedeny v pořadí, ve kterém by být prováděna v sekvenční provádění smyčky.

Omezení `ordered` směrnice jsou následující:

- Iterace smyčky s `for` konstrukce nesmí stejného seřazeného – direktiva spouštění více než jednou a nesmí spuštění, více než jeden `ordered` směrnice.

## <a name="27-data-environment"></a>2.7 datové prostředí

Tato část představuje direktivu a několik klauzulí pro řízení prostředí dat během provádění paralelních oblastí, následujícím způsobem:

- A `threadprivate` – direktiva (viz následující část) je k dispozici tak, aby rozsahu souboru, rozsahu oboru názvů nebo oboru bloku statických proměnných místního vlákna.

- Klauzule, které může být určen direktivami řízení sdílení atributy proměnné po dobu trvání konstrukce paralelní nebo sdílení práce jsou popsány v [části 2.7.2](#272-data-sharing-attribute-clauses).

### <a name="271-threadprivate-directive"></a>2.7.1 threadprivate – direktiva

`threadprivate` – Direktiva vytvoří pojmenovaného rozsahu souboru, rozsahu oboru názvů nebo zadané v proměnné statického oboru bloku *seznamu proměnné* privátní ve vlákně. *seznamu proměnné* je čárkou oddělený seznam proměnných, které nemají neúplný typ. Syntaxe `threadprivate` direktivy je následující:

```cpp
#pragma omp threadprivate(variable-list) new-line
```

Každá kopie `threadprivate` proměnná je inicializována jednou, neurčené okamžiku v programu před první odkaz na tuto kopii a obvyklým způsobem (tj. jako hlavní kopie by být inicializovány v sériové provádění programu). Všimněte si, že pokud je objekt odkazuje na explicitní inicializátoru `threadprivate` proměnné a hodnoty objektu se upraví před první odkaz na kopii proměnné a pak chování není zadána.

Jak se žádné soukromé proměnné vlákno nesmí odkazovat na jiné vlákno kopii `threadprivate` objektu. Během sériových oblastech a hlavní oblasti program bude odkazy na hlavní podproces kopii objektu.

Po provedení první paralelní oblasti, data v `threadprivate` objekty je zaručeno, že zachování pouze pokud dynamický vlákna mechanismus je zakázané, a pokud počet vláken zůstávají beze změn pro všechny paralelní oblasti.

Omezení týkající `threadprivate` směrnice jsou následující:

- A `threadprivate` směrnice pro proměnné s rozsahem souboru nebo rozsahu oboru názvů musí být uvedena mimo všechny definice nebo deklarace a musí předcházet lexikálně všechny odkazy na některé z proměnné ve svém seznamu.

- Každou proměnnou v *seznamu proměnné* z `threadprivate` – direktiva v oboru souboru nebo oboru názvů musí odkazovat na deklaraci proměnné v oboru souboru nebo oboru názvů, který lexikálně předchází směrnice.

- A `threadprivate` směrnice pro proměnné, statické rozsahu bloku musí být uvedena v oboru proměnné a nejsou ve vnořeném oboru. Direktiva lexikálně musí předcházet všechny odkazy na některé z proměnné ve svém seznamu.

- Každou proměnnou v *seznamu proměnné* z `threadprivate` – direktiva v rozsahu bloku musí odkazovat na deklaraci proměnné ve stejném oboru, který předchází lexikálně směrnice. Deklarace proměnné musí používat specifikátor statickou třídu úložiště.

- Je-li proměnná zadána v `threadprivate` direktiv v jednotce překladu. jeden, musí se zadat v `threadprivate` direktiv v každé jednotce překladu, ve kterém je deklarována.

- A `threadprivate` proměnné nesmí objevit všechny klauzule except `copyin`, `copyprivate`, `schedule`, `num_threads`, nebo `if` klauzuli.

- Adresa `threadprivate` konstantu adresa není proměnná.

- A `threadprivate` proměnná nesmí být neúplný typ nebo typ odkazu.

- A `threadprivate` proměnná typu třídy než POD musí být přístupná a jednoznačná kopírovací konstruktor, pokud je deklarovaná s inicializátorem explicitní.

Následující příklad ukazuje, jak úpravy, které se zobrazí v inicializátoru proměnné může způsobit neurčené chování a také jak se vyhnout tomuto problému s použitím pomocného objektu a konstruktor kopírování.

```cpp
int x = 1;
T a(x);
const T b_aux(x); /* Capture value of x = 1 */
T b(b_aux);
#pragma omp threadprivate(a, b)

void f(int n) {
   x++;
   #pragma omp parallel for
   /* In each thread:
   * Object a is constructed from x (with value 1 or 2?)
   * Object b is copy-constructed from b_aux
   */
   for (int i=0; i<n; i++) {
      g(a, b); /* Value of a is unspecified. */
   }
}
```

#### <a name="cross-references"></a>Křížové odkazy

- [dynamické vláken](3-1-7-omp-set-dynamic-function.md)
- [OMP_DYNAMIC](4-3-omp-dynamic.md) proměnné prostředí

### <a name="272-data-sharing-attribute-clauses"></a>2.7.2 atribut data-sharing klauzule

Několik direktivy přijmout klauzule, které umožní uživateli řídit sdílení atributy proměnné po dobu trvání oblast. Sdílení klauzule atributů pro platí pouze pro proměnné v lexikálním rozsahu direktiva, na kterém se zobrazí v klauzuli. Některé z následujících doložek jsou povolené pro všechny direktivy. Seznam klauzule, které jsou platné pro konkrétní direktivu jsou popsány s direktivou.

Pokud je proměnná viditelná, když paralelní nebo dochází v konstruktoru work-sharing a proměnná není zadán v klauzuli sdílení atribut nebo `threadprivate` direktiv, pak proměnná se sdílí. Jsou sdílené statické proměnné deklarované v rámci dynamický rozsah paralelní oblasti. Přidělené paměti haldy (například pomocí `malloc()` v jazyce C nebo C++ nebo `new` operátor v jazyce C++) se sdílí. (Ukazatel na tuto paměť, ale může být buď privátní nebo sdílený.) Proměnné s automatickým trváním úložiště deklarované v rámci dynamický rozsah paralelní oblasti jsou privátní.

Většina klauzulí přijmout *seznamu proměnné* argument, který je čárkou oddělený seznam proměnných, které jsou viditelné. Pokud proměnná odkazuje na atribut klauzuli data-sharing se typu odvozeného ze šablony a neexistují žádné odkazy na tuto proměnnou v programu, není chování definováno.

Všechny proměnné, které se zobrazují v klauzulích direktiv musí být viditelná. Klauzule může opakovat podle potřeby, ale žádná proměnná je možné zadat více než jednu klauzuli, s tím rozdílem, že proměnné lze v obou `firstprivate` a `lastprivate` klauzuli.

Klauzule atributů pro sdílení dat v následujících částech:

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [Sdílet](#2724-shared)
- [default](#2725-default)
- [reduction](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

`private` Klauzule deklaruje proměnné v seznamu proměnné být privátní pro každé vlákno v týmu. Syntaxe `private` klauzule vypadá takto:

```cpp
private(variable-list)
```

Chování zadané v proměnné `private` klauzule vypadá takto. Nový objekt s automatickým trváním úložiště přidělené konstrukce. Typ proměnné jsou určeny velikost a zarovnání nového objektu. Toto přidělení akce proběhne jednou pro každé vlákno v týmu a vyvolání výchozího konstruktoru pro objekt třídy v případě potřeby; jinak je neurčité počáteční hodnota.  Původní objekt odkazuje proměnná má neurčitá hodnota při vstupu do konstrukce, nesmí být upraveno v rámci dynamický rozsah konstrukce a má neurčitá hodnota při ukončení z konstrukce.

Lexikální rozsah direktiv konstrukce proměnná odkazuje na nový objekt privátní přidělené vláknu.

Omezení týkající `private` klauzule jsou následující:

- Proměnná typu třídy, který je zadán v `private` klauzule musí mít přístupná a jednoznačná výchozí konstruktor.

- Proměnnou podle `private` nesmí mít klauzuli `const`-kvalifikovaný typ, pouze pokud má třída typ s `mutable` člena.

- Zadané v proměnné `private` klauzule nesmí mít neúplný typ nebo typ odkazu.

- Proměnné, které se zobrazují v `reduction` klauzuli `parallel` směrnice nelze zadat v `private` klauzuli direktivy sdílení práce, s vazbou na paralelní konstrukce.

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

`firstprivate` Klauzule nabízí nadmnožinu funkcí poskytovaných `private` klauzuli. Syntaxe `firstprivate` klauzule vypadá takto:

```cpp
firstprivate(variable-list)
```

Zadané v proměnné *seznamu proměnné* mají `private` klauzule sémantiku, jak je popsáno v [části 2.7.2.1](#2721-private). Inicializace nebo konstrukce se stane, jako kdyby byly provést jednou na vlákno, před spuštěním podprocesu konstrukce. Pro `firstprivate` klauzuli paralelní konstrukce, počáteční hodnota nový privátní objekt je hodnota původního objektu, který existuje bezprostředně před paralelní konstrukce pro vlákno, které nalezne ho. Pro `firstprivate` je počáteční hodnota pro každé vlákno, které provádí konstruktoru work-sharing nový objekt privátní klauzule v konstruktoru work-sharing hodnotu původní objekt, který existuje před bodu v čase, že stejné vlákno narazí konstruktoru Work-sharing. Kromě toho pro objekty C++, tento nový privátní objekt pro každé vlákno je vytvořený z původního objektu z kopie.

Omezení týkající `firstprivate` klauzule jsou následující:

- Zadané v proměnné `firstprivate` klauzule nesmí mít neúplný typ nebo typ odkazu.

- Proměnná typu třídy, který je zadán jako `firstprivate` musí mít konstruktor kopie přístupná a jednoznačná.

- Proměnné, které jsou v rámci paralelní oblasti privátní nebo které se objeví v `reduction` klauzuli `parallel` směrnice nelze zadat v `firstprivate` klauzuli direktivy sdílení práce, s vazbou na paralelní konstrukce.

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

`lastprivate` Klauzule nabízí nadmnožinu funkcí poskytovaných `private` klauzuli. Syntaxe `lastprivate` klauzule vypadá takto:

```cpp
lastprivate(variable-list)
```

Zadané v proměnné *seznamu proměnné* mají `private` klauzule sémantiku. Při `lastprivate` klauzule se zobrazí v direktivě, který identifikuje konstruktoru work-sharing, hodnotu každého `lastprivate` přiřadí proměnná z postupně poslední iterace přidružené smyčky nebo lexikálně poslední direktivu section proměnné původní objekt. Proměnné, které nejsou přiřazeny hodnoty podle poslední iterace `for` nebo `parallel for`, nebo lexikálně poslední část `sections` nebo `parallel sections` směrnice, mají neurčité hodnoty po vytvoření. Nepřiřazené podobjekty také mají neurčité hodnoty po vytvoření.

Omezení týkající `lastprivate` klauzule jsou následující:

- Všechna omezení pro `private` použít.

- Proměnná typu třídy, který je zadán jako `lastprivate` musí mít operátor přiřazení kopie přístupná a jednoznačná.

- Proměnné, které jsou v rámci paralelní oblasti privátní nebo které se objeví v `reduction` klauzuli `parallel` směrnice nelze zadat v `lastprivate` klauzuli direktivy sdílení práce, s vazbou na paralelní konstrukce.

#### <a name="2724-shared"></a>2.7.2.4 shared

Tato klauzule sdílí proměnné, které se zobrazují v *seznamu proměnné* mezi všemi vlákny v týmu. Všechna vlákna v rámci týmu přístup do stejné oblasti úložiště pro `shared` proměnné.

Syntaxe `shared` klauzule vypadá takto:

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 default

`default` Klauzule umožňuje uživateli ovlivňují atributy sdílení dat z proměnných. Syntaxe `default` klauzule vypadá takto:

```cpp
default(shared | none)
```

Určení `default(shared)` odpovídá explicitně uvedete seznam jednotlivých aktuálně viditelné proměnné v `shared` klauzule, pokud se nejedná `threadprivate` nebo `const`-kvalifikovaný. Chybí explicitní `default` klauzule, výchozí chování je stejné jako if `default(shared)` byly zadány.

Určení `default(none)` vyžaduje, aby aspoň jeden z následujících musí mít hodnotu true pro každý odkaz na proměnnou v lexikálním rozsahu paralelní konstrukce:

- Proměnná je explicitně uvedená v klauzuli data-sharing atribut konstruktoru, který obsahuje odkaz na.

- Proměnná je deklarována v rámci paralelní konstrukce.

- Proměnná je `threadprivate`.

- Obsahuje proměnnou `const`-kvalifikovaný typ.

- Proměnná je řídicí proměnná smyčky pro `for` smyčku, která bezprostředně následuje po `for` nebo `parallel for` směrnice a reference proměnné se zobrazí uvnitř smyčky.

Určení proměnné na `firstprivate`, `lastprivate`, nebo `reduction` klauzule uzavřené směrnice způsobí, že implicitní odkaz na proměnnou v nadřazeném kontextu. Tyto odkazy jsou implicitní jsou také v souladu s požadavky uvedené výše.

Pouze jeden `default` na může být zadána klauzule `parallel` směrnice.

Sdílení dat atribut lze přepsat pomocí výchozí proměnné `private`, `firstprivate`, `lastprivate`, `reduction`, a `shared` klauzule, jak je ukázáno v následujícím příkladu:

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

Tato klauzule provádí snížení na skalární proměnné, které se zobrazují v *seznamu proměnné*, spolu s operátorem *op*. Syntaxe `reduction` klauzule vypadá takto:

`reduction(` *op* `:` *seznamu proměnné* `)`

Snížení se obvykle zadává pro příkaz s jedním z následujících forem:

- *x* `=` *x* *op* *výraz*
- *x* *binop* `=` *výraz*
- *x* `=` *expr* *op* *x* (s výjimkou odčítání)
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

kde:

*x*<br/>
Jedna z proměnných snížení uvedený v seznamu.

*Proměnná list*<br/>
Čárkou oddělený seznam proměnných snížení skaláru.

*výraz*<br/>
Výraz s skalárního typu, který neodkazuje na *x*.

*OP*<br/>
Není přetíženého operátoru, ale jeden z `+`, `*`, `-`, `&`, `^`, `|`, `&&`, nebo `||`.

*binop*<br/>
Není přetíženého operátoru, ale jeden z `+`, `*`, `-`, `&`, `^`, nebo `|`.

Následující je příkladem `reduction` klauzule:

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

Jak je znázorněno v příkladu, mohou být skryty operátor uvnitř funkce volání. Uživatel by měl být opatrní, že operátor podle `reduction` klauzule odpovídá operaci snížení.

I když bude pravý operand `||` operátor v tomto příkladu nemá žádné vedlejší účinky, že už povolené, ale by měla být používána opatrně. V tomto kontextu vedlejší účinek, který má zaručeno, že ke kterým dojde během sekvenční provádění smyčky může dojít během paralelního provádění. Tento rozdíl situace může nastat, vzhledem k tomu, že je neurčité, pořadí spuštění iterace.

Operátor, který se používá k určení počáteční hodnoty žádné soukromé proměnné, které kompilátor použije pro snížení a na zjištění operátor finalizace. Odstranit explicitním zadáním operátor, který umožňuje snížení příkazu mimo lexikální rozsah konstrukce. Libovolný počet `reduction` klauzule může být určen v direktivě, ale proměnná se může vyskytovat nejvýše jedna `reduction` klauzule pro tuto direktivu.

Soukromou kopii každou proměnnou v *seznamu proměnné* vytvořen, jednou pro každé vlákno, jako kdyby `private` klauzule nepoužilo. Podle operátor, který je inicializován soukromou kopii (viz následující tabulka).

Na konci oblasti, pro kterou `reduction` byla zadána klauzule, původní objekt aktualizován, aby odrážel výsledek, který spojuje s konečnou hodnotu každého soukromé kopie pomocí operátoru zadán původní hodnotu. Operátory snížení jsou všechny asociativní (s výjimkou odčítání) a kompilátor může volně znovu přidružit výpočtu konečnou hodnotu. (Částečných výsledků snížení odčítání jsou přidány do formuláře konečná hodnota).

Při první vlákno dosáhne obsahující klauzuli a tak zůstane až do dokončení výpočtu snížení se stane neurčité hodnotě původního objektu.  Za normálních okolností bude dokončena na konci konstrukce; výpočtu ale pokud `reduction` na konstrukce, ke kterému se používá klauzuli `nowait` je také použít původní objekt zůstává hodnota neurčitý dokud barrier synchronizace byla provedena Ujistěte se, že všechna vlákna dokončila `reduction`klauzuli.

Následující tabulka uvádí, které jsou platné operátory a jejich hodnoty canonical inicializace. Hodnota vlastní inicializaci bude konzistentní s datovým typem redukční proměnná.

|Operátor|Inicializace|
|--------------|--------------------|
|`+`|0|
|`*`|1|
|`-`|0|
|`&`|~0|
|`|`|0|
|`^`|0|
|`&&`|1|
|`||`|0|

Omezení týkající `reduction` klauzule jsou následující:

- Typ proměnné `reduction` klauzule musí být platná pro operátor snížení, s tím rozdílem, že nikdy povolené typy ukazatele a typy odkazů.

- Proměnná, která je zadána v `reduction` nesmí mít klauzuli `const`-kvalifikovaný.

- Proměnné, které jsou v rámci paralelní oblasti privátní nebo které se objeví v `reduction` klauzuli `parallel` směrnice nelze zadat v `reduction` klauzuli direktivy sdílení práce, s vazbou na paralelní konstrukce.

   ```cpp
   #pragma omp parallel private(y)
   { /* ERROR - private variable y cannot be specified
                in a reduction clause */
      #pragma omp for reduction(+: y)
      for (i=0; i<n; i++)
         y += b[i];
   }

   /* ERROR - variable x cannot be specified in both
              a shared and a reduction clause */
   #pragma omp parallel for shared(x) reduction(+: x)
   ```

#### <a name="2727-copyin"></a>2.7.2.7 copyin

`copyin` Klauzule poskytuje mechanismus pro stejnou hodnotu přiřadit `threadprivate` proměnné pro každé vlákno v týmu provádí paralelní oblasti. Pro každou proměnnou podle `copyin` klauzule, hodnotu proměnné v hlavním vlákně tým zkopírován jako při přiřazení kopie privátní vlákno na začátku paralelní oblasti. Syntaxe `copyin` klauzule vypadá takto:

```cpp

copyin(
variable-list
)
```

Omezení týkající `copyin` klauzule jsou následující:

- Proměnná, která je zadána v `copyin` klauzule musí mít operátor přiřazení kopie přístupná a jednoznačná.

- Proměnná, která je zadána v `copyin` klauzule musí být `threadprivate` proměnné.

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

`copyprivate` Klauzule poskytuje mechanismus pro používat soukromé proměnné k ostatním členům vysílání hodnotu z jednoho člena týmu. Jde o alternativu k použití sdílené proměnné pro hodnotu při poskytování sdílené proměnné by bylo obtížné (například v rekurze vyžadující jinou proměnnou na každé úrovni). `copyprivate` Klauzule může vyskytovat jenom u `single` směrnice.

Syntaxe `copyprivate` klauzule vypadá takto:

```cpp

copyprivate(
variable-list
)
```

Vliv `copyprivate` klauzuli pro proměnné ve svém seznamu proměnné dojde poté, co provádění strukturovaný blok přidružené `single` sestavit, a před všechny vlákna v týmu ještě zbývá odbourejte překážky bránící na konci konstrukce. Pak na všechna vlákna v týmu pro každou proměnnou v *seznamu proměnné*, tato proměnná změní určené (jako přiřazení) s odpovídající hodnotou proměnné ve vlákně, který spouští konstrukce uživatele strukturované blok.

Omezení `copyprivate` klauzule jsou následující:

- Proměnná, která je zadána v `copyprivate` klauzule nesmí být v `private` nebo `firstprivate` klauzule pro stejný `single` – direktiva.

- Pokud `single` s `copyprivate` klauzule narazí na dynamický rozsah paralelní oblasti, všechny proměnné zadané v `copyprivate` klauzule musí být v rámci nadřazeného privátní.

- Proměnná, která je zadána v `copyprivate` klauzule musí mít přístupné jednoznačný kopírovacího operátoru přiřazení.

## <a name="28-directive-binding"></a>2.8 vazby direktiv

Dynamické vazby direktiv musí splňovat následující pravidla:

- `for`, `sections`, `single`, `master`, A `barrier` direktivy Svázat dynamicky uzavírající `parallel`, pokud existuje, bez ohledu na hodnotu kterékoli `if` klauzuli, která může být k dispozici na tomto směrnice. Je-li žádné paralelní oblasti se aktuálně zpracovává, direktivy jsou spuštěny týmem, který se skládá z pouze hlavní vlákno.

- `ordered` – Direktiva vytvoří vazbu dynamicky uzavírající `for`.

- `atomic` Vynucuje směrnice výhradní přístup k `atomic` direktivy ve všech vláknech, nikoli pouze aktuální týmu.

- `critical` Vynucuje směrnice výhradní přístup k `critical` direktivy ve všech vláknech, nikoli pouze aktuální týmu.

- Direktivu nikdy navázat žádné směrnice mimo nejbližšímu dynamicky uzavírající `parallel`.

## <a name="29-directive-nesting"></a>2.9 vnořování direktiv

Dynamického vnoření direktiv musí splňovat následující pravidla:

- A `parallel` direktiv dynamicky uvnitř jiného `parallel` logicky zavádí nový tým, který se skládá z aktuálního vlákna, není-li vnořené paralelismu je povolená.

- `for`, `sections`, a `single` direktivy, kteří jsou navázáni na stejný `parallel` nemohou být vnořená v sobě navzájem.

- `critical` direktivy se stejným názvem, nemohou být vnořená v sobě navzájem. Všimněte si, že toto omezení není dostatečné k zabránění vzájemnému zablokování.

- `for`, `sections`, a `single` direktivy nejsou povolené v dynamický rozsah `critical`, `ordered`, a `master` oblastech, pokud direktivy vytvořit vazbu na stejný `parallel` jako oblastí.

- `barrier` direktivy nejsou povolené v dynamický rozsah `for`, `ordered`, `sections`, `single`, `master`, a `critical` oblastech, pokud direktivy vytvořit vazbu na stejný `parallel` jako oblastí.

- `master` direktivy nejsou povolené v dynamický rozsah `for`, `sections`, a `single` direktivy Pokud `master` direktivy vytvořit vazbu na stejný `parallel` jako direktiv pro sdílení práce.

- `ordered` direktivy nejsou povoleny dynamické rozsahu `critical` oblastech, pokud direktivy vytvořit vazbu na stejný `parallel` jako oblastí.

- Směrnice, které je povoleno při provedení dynamicky v rámci paralelní oblasti je povolen také při spuštění mimo paralelní oblasti. Při spuštění dynamicky mimo paralelní oblasti zadaného uživatelem, direktiva provádí týmem, který se skládá z pouze hlavní vlákno.
