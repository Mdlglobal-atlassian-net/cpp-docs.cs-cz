---
title: 2. Direktivy
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 125d2d83b277e62d007e3a208e426ea717d52790
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882850"
---
# <a name="2-directives"></a>2. Direktivy

Direktivy jsou založené na direktivách `#pragma` definovaných ve standardech C a C++ .  Kompilátory, které podporují OpenMP C a C++ API, budou obsahovat možnost příkazového řádku, která aktivuje a povoluje výklad všech direktiv kompilátoru OpenMP.

## <a name="21-directive-format"></a>Formát direktivy 2,1

Syntaxe direktivy OpenMP je formálně určena gramatikou v [příloze C](c-openmp-c-and-cpp-grammar.md)a níže uvedená:

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

Každá direktiva začíná `#pragma omp`, aby se snížila pravděpodobnost konfliktu s jinými (neopenmp nebo od jiných rozšíření dodavatelů) direktiv pragma se stejnými názvy. Zbytek direktivy dodržuje konvence jazyka C a C++ standardů pro direktivy kompilátoru. Konkrétně lze použít prázdné znaky před a po `#`a někdy je nutné použít prázdné znaky k oddělení slov v direktivě. Tokeny předběžného zpracování za `#pragma omp` podléhají nahrazení makra.

V direktivách se rozlišují malá a velká písmena. Pořadí, ve kterém se klauzule zobrazují v direktivách, nejsou významné. Klauzule na direktivách mohou být podle potřeby opakovány v souladu s omezeními uvedenými v popisu každé klauzule. Pokud se v klauzuli zobrazí *Proměnná-list* , musí určovat jenom proměnné. Pro každou direktivu lze zadat pouze jeden *Název direktivy* .  Například následující direktiva není povolena:

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

Direktiva OpenMP se vztahuje na maximálně jeden následující příkaz, který musí být strukturovaným blokem.

## <a name="22-conditional-compilation"></a>2,2 Podmíněná kompilace

Název makra `_OPENMP` je definován implementacemi, které jsou v souladu s OpenMP, jako Desítková konstanta *YYYYMM*, což bude rok a měsíc schválené specifikace. Toto makro nesmí být předmětem `#define` nebo direktivy předběžného zpracování `#undef`.

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Pokud dodavatelé definují rozšíření na OpenMP, mohou určit další předdefinovaná makra.

## <a name="23-parallel-construct"></a>2,3 paralelní konstrukce

Následující direktiva definuje paralelní oblast, která je oblastí programu, který má být spuštěn více vlákny paralelně. Tato směrnice je základní konstrukcí, která spouští paralelní provádění.

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*Klauzule* je jedna z následujících:

- `if(` *skalárního výrazu* `)`
- `private(` *variabilní seznam* `)`
- `firstprivate(` *variabilní seznam* `)`
- `default(shared | none)`
- `shared(` *variabilní seznam* `)`
- `copyin(` *variabilní seznam* `)`
- *operátor* `reduction(` `:`*Variable seznam* `)`
- `num_threads(` *typu Integer-expression* `)`

Když se vlákno dostane do paralelní konstrukce, vytvoří se tým vláken, pokud je splněn jeden z následujících případů:

- Neexistuje žádná klauzule `if`.
- Výraz `if` se vyhodnocuje jako nenulová hodnota.

Toto vlákno se stal hlavním vláknem týmu, s číslem vlákna 0 a všemi vlákny v týmu, včetně hlavního vlákna, spustí oblast paralelně. Pokud je hodnota výrazu `if` nula, oblast je serializována.

Chcete-li určit počet vláken, která jsou požadována, budou v uvedeném pořadí považována za následující pravidla. Bude použito první pravidlo, jehož podmínka je splněna:

1. Pokud je přítomna klauzule `num_threads`, pak hodnota celočíselného výrazu je počet požadovaných vláken.

1. Pokud byla volána funkce knihovny `omp_set_num_threads`, pak hodnota argumentu v naposledy spuštěném volání je počet požadovaných vláken.

1. Pokud je definována proměnná prostředí `OMP_NUM_THREADS`, pak hodnota této proměnné prostředí je počet požadovaných vláken.

1. Pokud není použita žádná z výše uvedených metod, je počet požadovaných vláken definován implementací.

Pokud je k dispozici klauzule `num_threads`, nahradí se počet vláken požadovaných funkcí knihovny `omp_set_num_threads` nebo proměnnou prostředí `OMP_NUM_THREADS` jenom pro paralelní oblast, na kterou se aplikuje. Později nejsou ovlivněny paralelní oblasti.

Počet vláken, která spouštějí paralelní oblast, závisí také na tom, zda je povolena dynamická úprava počtu vláken. Pokud je dynamická úprava zakázána, pak požadovaný počet vláken spustí paralelní oblast. Pokud je dynamická úprava povolena, pak požadovaný počet vláken je maximální počet vláken, která mohou spustit paralelní oblast.

Pokud je k dispozici paralelní oblast v době, kdy je zakázána dynamická úprava počtu vláken, a počet vláken, která jsou požadována pro paralelní oblast, je větší než počet, který může systém run-time dodat, chování programu je definovaná implementace. Implementace může například přerušit provádění programu nebo může serializovat paralelní oblast.

Funkce knihovny `omp_set_dynamic` a proměnná prostředí `OMP_DYNAMIC` lze použít k povolení a zakázání dynamické úpravy počtu vláken.

Počet fyzických procesorů, které jsou ve skutečnosti hostiteli vláken, je definován implementací. Po vytvoření počet vláken v týmu zůstane konstantní po dobu trvání této paralelní oblasti. Dá se změnit buď explicitně uživatelem, nebo automaticky systémem za běhu z jedné paralelní oblasti na jinou.

Příkazy obsažené v dynamickém rozsahu paralelní oblasti jsou spouštěny každým vláknem a každé vlákno může spouštět cestu příkazů, které se liší od ostatních vláken. Direktivy, které se vyskytly mimo lexikální rozsah paralelní oblasti, se označují jako osamocené direktivy.

Na konci paralelní oblasti je předpokládaná bariéra. Pouze hlavní vlákno týmu pokračuje v provádění na konci paralelní oblasti.

Pokud vlákno v týmu, který spouští paralelní oblast, narazí na další paralelní konstrukce, vytvoří nový tým a stane se hlavním členem tohoto nového týmu. Vnořené paralelní oblasti jsou serializovány ve výchozím nastavení. Výsledkem je, že ve výchozím nastavení je vnořená paralelní oblast spuštěna týmem tvořeným jedním vláknem. Výchozí chování může být změněno buď pomocí běhové funkce knihovny `omp_set_nested` nebo `OMP_NESTED`proměnné prostředí. Počet vláken v týmu, který spouští vnořenou paralelní oblast, je však definován jako implementace.

Omezení direktivy `parallel` jsou následující:

- V direktivě se může vyskytovat nejvýše jedna klauzule `if`.

- Není určeno, zda dojde k jakýmkoli vedlejším účinkům uvnitř výrazu if nebo výrazu `num_threads`.

- `throw` spuštěný v paralelní oblasti musí způsobit pokračování v dynamickém rozsahu stejného strukturovaného bloku a musí být zachyceno stejným vláknem, který vyvolal výjimku.

- V direktivě se může vyskytovat jenom jedna klauzule `num_threads`. Výraz `num_threads` je vyhodnocen mimo kontext paralelní oblasti a musí se vyhodnotit na kladnou celočíselnou hodnotu.

- Pořadí vyhodnocení `if` a `num_threads`ch klauzulí není určeno.

### <a name="cross-references"></a>Křížové odkazy

- klauzule `private`, `firstprivate`, `default`, `shared`, `copyin`a `reduction` ([oddíl 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) proměnná prostředí
- funkce knihovny [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) proměnná prostředí
- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) funkce
- [OMP_NESTED](4-environment-variables.md#44-omp_nested) proměnná prostředí
- funkce knihovny [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)

## <a name="24-work-sharing-constructs"></a>2,4 konstrukce práce – sdílení

Konstruktor pro pracovní sdílení distribuuje provádění přidruženého příkazu mezi členy týmu, kteří ho narazí. Direktivy pro sdílení práce nespouštějí nová vlákna a pro vstup do konstrukce práce není k dispozici žádná nebariéra.

Sekvence konstrukcí a `barrier` direktiv pro sdílení práce musí být stejná pro každé vlákno v týmu.

OpenMP definuje následující konstruktory pro pracovní sdílení a tyto konstrukce jsou popsány v následujících částech:

- [pro](#241-for-construct) direktivu
- [Sections](#242-sections-construct) – direktiva
- [jedna](#243-single-construct) direktiva

### <a name="241-for-construct"></a>2.4.1 pro konstrukci

Direktiva `for` označuje iterační konstruktor pro sdílení, který určuje, že iterace přidružené smyčky budou spouštěny paralelně. Iterace smyčky `for` jsou distribuovány napříč vlákny, které již existují v týmu provádějícím paralelní konstrukci, ke které se váže. Syntaxe `for` konstrukce je následující:

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

Klauzule je jedna z následujících:

- `private(` *variabilní seznam* `)`
- `firstprivate(` *variabilní seznam* `)`
- `lastprivate(` *variabilní seznam* `)`
- *operátor* `reduction(` `:` *Variable seznam* `)`
- `ordered`
- `schedule(` *druh* [`,` *chunk_size*] `)`
- `nowait`

Direktiva `for` umisťuje omezení struktury odpovídající `for` smyčky. Konkrétně odpovídající `for` smyčka musí mít kanonický tvar:

`for (` *init-expr* `;` *var Logic-op b* `;` *incr-expr* `)`

*init-expr*<br/>
Jeden z následujících produktů:

- *var* = *kg*
- *var typu integer* * = .*

*incr – výraz*<br/>
Jeden z následujících produktů:

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
Celočíselná proměnná se znaménkem. Pokud by byla tato proměnná jinak sdílená, implicitně se pro dobu trvání `for`stane soukromou. Neupravujte tuto proměnnou v těle příkazu `for`. Není-li proměnná zadána `lastprivate`, její hodnota po neurčitém cyklu.

*logický operátor op*<br/>
Jeden z následujících produktů:

- `<`
- `<=`
- `>`
- `>=`

*9,1*, *b*a *incr*<br>
Nevariantní celočíselné výrazy ve smyčce Během hodnocení těchto výrazů nedochází k žádné synchronizaci, takže všechny hodnocené vedlejší účinky způsobují neurčité výsledky.

Kanonický tvar umožňuje vypočítat počet iterací smyčky při vstupu do smyčky. Tento výpočet je proveden s hodnotami v typu *var*, po celočíselných propagačních akcích. Zejména pokud hodnota *b* *`-` `+`* *incr* nemůže být reprezentovaná v tomto typu, výsledek je neurčitý. Pokud je *logicky-op* `<` nebo `<=`, pak *incr-expr* musí způsobit zvýšení *rozptylu* u každé iterace smyčky.   Pokud je *logická-op* `>` nebo `>=`, pak *incr-expr* musí způsobit, že *var vrátí var* pro každou iteraci smyčky.

Klauzule `schedule` určuje, jak jsou iterace `for` smyčky rozděleny mezi vlákna týmu. Správnost programu nesmí záviset na tom, které vlákno provádí určitou iteraci. Hodnota *chunk_size*, je-li zadána, musí být výrazem nevariantního celého čísla smyčky s kladnou hodnotou. Během vyhodnocování tohoto výrazu nedochází k žádné synchronizaci, takže všechny hodnocené vedlejší účinky způsobují neurčité výsledky. *Typ* plánu může být jedna z následujících hodnot:

Tabulka 2-1: hodnoty *druhu* klauzule `schedule`

|||
|-|-|
|static|Je-li zadána hodnota `schedule(static,` *chunk_size* `)`, jsou iterace rozděleny do bloků velikosti určeného *chunk_size*. Bloky jsou staticky přiřazené k vláknům v týmu v kruhovém dotazování v pořadí podle čísla vlákna. Pokud není zadána žádná *chunk_size* , je prostor iterace rozdělen do bloků, které mají přibližně stejnou velikost, s jedním blokem přiřazeným každému vláknu.|
|dynamické odkazy|Je-li zadána `schedule(dynamic,` *chunk_size* `)`, jsou iterace rozděleny do řady bloků dat, z nichž každá obsahuje *chunk_size* iterace. Každý blok je přiřazen k vláknu, které čeká na přiřazení. Vlákno spustí blok iterací a potom počká na další přiřazení, dokud nebudou žádné bloky dat nadále přiřazeny. Poslední blok, který má být přiřazen, může mít menší počet iterací. Pokud není zadána žádná *chunk_size* , výchozí hodnota je 1.|
|s asistencí|Pokud je zadána hodnota `schedule(guided,` *chunk_size* `)`, jsou iterace přiřazeny vláknům v blocích s klesajícími velikostmi. Když vlákno dokončí svůj přiřazený blok iterací, dynamicky se přiřadí další blok, dokud žádný nezůstane. U *chunk_size* 1 je velikost každého bloku přibližně přibližně počet nepřiřazených iterací dělený počtem vláken. Tyto velikosti se zkrátí téměř exponenciálně na 1. U *chunk_size* s hodnotou *k* větší než 1 se velikost zmenší skoro exponenciálně na *k*, s tím rozdílem, že poslední blok může mít méně než *k* iteracím. Pokud není zadána žádná *chunk_size* , výchozí hodnota je 1.|
|modul runtime|Pokud je zadána `schedule(runtime)`, rozhodnutí týkající se plánování bude odloženo do doby běhu. *Typ* a velikost plánu bloků lze vybrat v době běhu nastavením proměnné prostředí `OMP_SCHEDULE`. Pokud tato proměnná prostředí není nastavená, je výsledný plán definovaný jako implementace. Je-li zadána `schedule(runtime)`, nesmí být zadána *chunk_size* .|

V případě absence explicitně definované klauzule `schedule` je výchozí `schedule` definováno implementací.

Program, který odpovídá OpenMP, by neměl spoléhat na konkrétní plán na správné provedení. Program by neměl spoléhat na *druh* plánu přesně na popis uvedený výše, protože je možné mít variace v implementacích stejného *typu* plánu v různých kompilátorech. Popisy lze použít k výběru plánu, který je vhodný pro konkrétní situaci.

Klauzule `ordered` musí být přítomna, pokud se direktivy `ordered` vážou ke konstruktoru `for`.

Na konci `for` konstrukce je implicitní bariéra, pokud není zadána klauzule `nowait`.

Omezení direktivy `for` jsou následující:

- `for` smyčka musí být strukturovaným blokem, a navíc jeho provedení nesmí končit příkazem `break`.

- Hodnoty řídicích výrazů smyčky smyčky `for` přidružené k direktivě `for` musí být stejné pro všechna vlákna v týmu.

- Proměnná iterace smyčky `for` musí mít typ signed integer.

- V direktivě `for` se může vyskytovat jenom jedna klauzule `schedule`.

- V direktivě `for` se může vyskytovat jenom jedna klauzule `ordered`.

- V direktivě `for` se může vyskytovat jenom jedna klauzule `nowait`.

- Není zadán, pokud nebo jak často existují jakékoli vedlejší účinky v rámci *chunk_size*, *kg*, *b*nebo *incr* výrazů.

- Hodnota výrazu *chunk_size* musí být stejná pro všechna vlákna v týmu.

#### <a name="cross-references"></a>Křížové odkazy

- klauzule `private`, `firstprivate`, `lastprivate`a `reduction` ([section 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) proměnná prostředí
- [seřazená](#266-ordered-construct) konstrukce
- klauzule [plánu](d-using-the-schedule-clause.md)

### <a name="242-sections-construct"></a>2.4.2 – konstrukce oddílů

Direktiva `sections` identifikuje konstruktor neiteračního pracovního sdílení, který určuje sadu konstrukcí, které mají být rozděleny mezi vlákna v týmu. Každý oddíl je proveden jednou vláknem v týmu. Syntaxe direktivy `sections` je následující:

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

Klauzule je jedna z následujících:

- `private(` *variabilní seznam* `)`
- `firstprivate(` *variabilní seznam* `)`
- `lastprivate(` *variabilní seznam* `)`
- *operátor* `reduction(` `:`*Variable seznam* `)`
- `nowait`

V každé části předchází direktiva `section`, i když je direktiva `section` volitelná pro první oddíl. Direktivy `section` musí být v lexikálním rozsahu direktivy `sections`. Na konci `sections` konstrukce je implicitní bariéra, pokud není zadána `nowait`.

Omezení direktivy `sections` jsou následující:

- Direktiva `section` nesmí být uvedená mimo lexikální rozsah `sections` direktivy.

- V direktivě `sections` se může vyskytovat jenom jedna klauzule `nowait`.

#### <a name="cross-references"></a>Křížové odkazy

- klauzule `private`, `firstprivate`, `lastprivate`a `reduction` ([section 2.7.2](#272-data-sharing-attribute-clauses))

### <a name="243-single-construct"></a>2.4.3 Single – konstrukce

Direktiva `single` identifikuje konstruktor, který určuje, že přidružený strukturovaný blok je spuštěn pouze jedním vláknem v týmu (ne nutně hlavním vláknem). Syntaxe direktivy `single` je následující:

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

Klauzule je jedna z následujících:

- `private(` *variabilní seznam* `)`
- `firstprivate(` *variabilní seznam* `)`
- `copyprivate(` *variabilní seznam* `)`
- `nowait`

Pokud není zadána klauzule `nowait`, existuje implicitní bariéra za `single` konstrukce.

Omezení direktivy `single` jsou následující:

- V direktivě `single` se může vyskytovat jenom jedna klauzule `nowait`.
- Klauzule `copyprivate` nesmí být použita s klauzulí `nowait`.

#### <a name="cross-references"></a>Křížové odkazy

- klauzule `private`, `firstprivate`a `copyprivate` ([oddíl 2.7.2](#272-data-sharing-attribute-clauses))

## <a name="25-combined-parallel-work-sharing-constructs"></a>2,5 kombinovaných paralelních konstrukcí pro sdílení práce

Kombinování paralelních konstrukcí pro sdílení práce jsou zkratky pro určení paralelní oblasti, která má pouze jeden konstruktor pro sdílení práce. Sémantika těchto direktiv je stejná jako explicitní určení direktivy `parallel` následovaný jedinou konstrukcí pro sdílení práce.

V následujících částech jsou popsány kombinované paralelní konstrukce pro sdílení práce:

- [Parallel for](#251-parallel-for-construct) – direktiva
- [Parallel Sections](#252-parallel-sections-construct) – direktiva

### <a name="251-parallel-for-construct"></a>2.5.1 Parallel for – konstrukce

Direktiva `parallel for` je zástupce `parallel` oblasti, která obsahuje pouze jednu direktivu `for`. Syntaxe direktivy `parallel for` je následující:

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Tato direktiva umožňuje všechny klauzule direktivy `parallel` a direktiva `for`, s výjimkou klauzule `nowait`, se stejnými významy a omezeními. Sémantika se shoduje s explicitním určením `parallel` direktivy ihned následovaný direktivou `for`.

#### <a name="cross-references"></a>Křížové odkazy

- [Parallel](#23-parallel-construct) – direktiva
- [pro](#241-for-construct) direktivu
- [Klauzule atributů dat](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>konstrukce 2.5.2 Parallel oddíly

Direktiva `parallel sections` poskytuje zástupce pro určení `parallel` oblasti, která má pouze jednu direktivu `sections`. Sémantika se shoduje s explicitním určením `parallel` direktivy ihned následovaný direktivou `sections`. Syntaxe direktivy `parallel sections` je následující:

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*Klauzule* může být jednou z klauzulí přijatých direktivami `parallel` a `sections`, s výjimkou klauzule `nowait`.

#### <a name="cross-references"></a>Křížové odkazy

- [Parallel](#23-parallel-construct) – direktiva
- [Sections](#242-sections-construct) – direktiva

## <a name="26-master-and-synchronization-directives"></a>2,6 hlavní a synchronizační direktivy

Následující části popisují:

- [Hlavní](#261-master-construct) konstrukce
- [kritická](#262-critical-construct) konstrukce
- [bariéra](#263-barrier-directive) – direktiva
- [atomová](#264-atomic-construct) – konstrukce
- [flush](#265-flush-directive) – direktiva
- [seřazená](#266-ordered-construct) konstrukce

### <a name="261-master-construct"></a>2.6.1 – hlavní konstrukce

Direktiva `master` identifikuje konstrukce, která určuje strukturovaný blok, který je spuštěn hlavním vláknem týmu. Syntaxe direktivy `master` je následující:

```cpp
#pragma omp master new-linestructured-block
```

Jiná vlákna v týmu nespouštějí přidružený strukturovaný blok. Neexistuje žádná odvozená bariéra buď pro vstup, nebo pro ukončení z hlavní konstrukce.

### <a name="262-critical-construct"></a>2.6.2 – kritická konstrukce

Direktiva `critical` identifikuje konstrukce, která omezuje provádění přidruženého strukturovaného bloku na jedno vlákno v jednom okamžiku. Syntaxe direktivy `critical` je následující:

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

K identifikaci kritické oblasti lze použít volitelný *název* . Identifikátory používané k identifikaci kritické oblasti mají vnější propojení a jsou v oboru názvů, který je oddělený od názvových prostorů používaných popisky, značkami, členy a běžnými identifikátory.

Vlákno čeká na začátek kritické oblasti, dokud žádné jiné vlákno neprovádí kritickou oblast (kdekoli v programu) se stejným názvem. Všechny nepojmenované direktivy `critical` se mapují na stejný neurčený název.

### <a name="263-barrier-directive"></a>2.6.3 bariéra – direktiva

Direktiva `barrier` synchronizuje všechna vlákna v týmu. V případě, že každý podproces v týmu počká, až všichni ostatní dorazí na tento bod. Syntaxe direktivy `barrier` je následující:

```cpp
#pragma omp barrier new-line
```

Po zjištění, že všechna vlákna v týmu mají bariéru, každé vlákno v týmu začne provádět příkazy po paralelní direktivě bariéry. Vzhledem k tomu, že direktiva `barrier` nemá v rámci své syntaxe příkaz jazyka C, existují určitá omezení umístění v rámci programu. Další informace o formální gramatice naleznete v [příloze C](c-openmp-c-and-cpp-grammar.md). Následující příklad znázorňuje tato omezení.

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

### <a name="264-atomic-construct"></a>2.6.4 atomická konstrukce

Direktiva `atomic` zajišťuje, aby bylo konkrétní umístění v paměti Aktualizováno atomicky, nikoli vystavení pro možnost několika souběžných vláken pro zápis. Syntaxe direktivy `atomic` je následující:

```cpp
#pragma omp atomic new-lineexpression-stmt
```

Příkaz Expression musí mít jednu z následujících forem:

- *x binop* `=` *výraz*
- `++` *x*
- `++` *x*
- `--` *x*
- `--` *x*

V předchozích výrazech:

- *x* je výraz l-hodnoty se skalárním typem.

- *expr* je výraz s skalárním typem, který neodkazuje na objekt určený *x*.

- *binop* není přetížený operátor a je jedním z `+`, `*`, `-`, `/`, `&`, `^`, `|`, `<<`nebo `>>`.

I když je implementovaná implementace – definuje, jestli implementace nahrazuje všechny direktivy `atomic` `critical` direktivami, které mají stejný jedinečný *název*, `atomic` direktiva povoluje lepší optimalizaci. K dispozici jsou často pokyny k hardwaru, které mohou provádět atomickou aktualizaci s minimální režií.

Pouze zatížení a uložení objektu označeného *x* jsou atomické; vyhodnocení *výrazu* není atomické. Aby nedocházelo ke konfliktům časování, musí být všechny aktualizace umístění paralelně chráněny pomocí direktivy `atomic`, s výjimkou těch, které jsou známy bez konfliktu časování.

Omezení direktivy `atomic` jsou následující:

- Všechny atomické odkazy na umístění úložiště x v programu musí mít kompatibilní typ.

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

Direktiva `flush`, ať už explicitní nebo implicitní, určuje bod "křížového vlákna", ve kterém je implementace nezbytná, aby se zajistilo, že všechna vlákna v týmu mají konzistentní zobrazení určitých objektů (uvedených níže) v paměti. To znamená, že předchozí vyhodnocení výrazů, které odkazují na tyto objekty, jsou dokončená a následná hodnocení ještě nezačala. Například kompilátory musí obnovit hodnoty objektů z registru do paměti a hardware může potřebovat vyprázdnit vyrovnávací paměť pro zápis do paměti a znovu načíst hodnoty objektů z paměti.

Syntaxe direktivy `flush` je následující:

```cpp
#pragma omp flush [(variable-list)]  new-line
```

Pokud objekty, které vyžadují synchronizaci, mohou být označeny proměnnými, pak tyto proměnné lze zadat v volitelném *seznamu proměnných*. Pokud je v *seznamu proměnných*uveden ukazatel, je ukazatel sám vyprázdněn, nikoli objekt, na který odkazuje ukazatel.

Direktiva `flush` bez *seznamu proměnných* synchronizuje všechny sdílené objekty kromě nepřístupných objektů s automatickým trváním úložiště. (To může mít větší režii než `flush` se *seznamem proměnných*.) Direktiva `flush` bez *variabilního seznamu* je odvozena pro následující direktivy:

- `barrier`
- Při vstupu a výstupu z `critical`
- Při vstupu a výstupu z `ordered`
- Při vstupu a výstupu z `parallel`
- Při ukončení z `for`
- Při ukončení z `sections`
- Při ukončení z `single`
- Při vstupu a výstupu z `parallel for`
- Při vstupu a výstupu z `parallel sections`

Tato direktiva není zahrnuta, pokud je přítomna klauzule `nowait`. Je třeba poznamenat, že `flush` direktiva není předpokládaná pro žádnou z následujících možností:

- Při vstupu do `for`
- Při vstupu do nebo ukončení z `master`
- Při vstupu do `sections`
- Při vstupu do `single`

Odkaz, který přistupuje k hodnotě objektu s neúplným typem, se chová, jako by existovala direktiva `flush` určující tento objekt v předchozím bodu sekvence. Odkaz, který upravuje hodnotu objektu s typem, který je typu volatile, se chová stejně, jako kdyby existovala direktiva `flush` určující tento objekt v následném bodu sekvence.

Vzhledem k tomu, že direktiva `flush` nemá v rámci své syntaxe příkaz jazyka C, existují určitá omezení umístění v rámci programu. Další informace o formální gramatice naleznete v [příloze C](c-openmp-c-and-cpp-grammar.md). Následující příklad znázorňuje tato omezení.

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

Omezení direktivy `flush` jsou následující:

- Proměnná zadaná v direktivě `flush` nesmí mít odkazový typ.

### <a name="266-ordered-construct"></a>2.6.6 seřazený konstruktor

Strukturovaný blok, který následuje po direktivě `ordered`, se spustí v pořadí, ve kterém by se v sekvenční smyčce prováděly iterace. Syntaxe direktivy `ordered` je následující:

```cpp
#pragma omp ordered new-linestructured-block
```

Direktiva `ordered` musí být v dynamickém rozsahu `for` nebo konstrukce `parallel for`. Direktiva `for` nebo `parallel for`, na kterou musí vazba konstrukce `ordered` mít zadanou klauzuli `ordered`, jak je popsáno v [oddílu 2.4.1](#241-for-construct). Při provádění `for` nebo `parallel for` konstrukce s klauzulí `ordered` jsou rutiny `ordered` spouštěny výhradně v pořadí, ve kterém by byly spuštěny při sekvenčním provádění smyčky.

Omezení direktivy `ordered` jsou následující:

- Iterace smyčky s konstruktorem `for` nesmí provádět stejné seřazené direktivy více než jednou a nesmí provádět více než jednu direktivu `ordered`.

## <a name="27-data-environment"></a>2,7 data prostředí

V této části se seznámíte s direktivou a několika klauzulemi pro řízení datového prostředí během provádění paralelních oblastí, a to takto:

- Direktiva [threadprivate](#271-threadprivate-directive) je poskytována pro nastavení proměnných rozsahu souboru, oboru názvů nebo statických proměnných oboru bloku na vlákno.

- Klauzule, které mohou být zadány na direktivách pro řízení atributů sdílení proměnných po dobu trvání paralelních konstrukcí nebo konstrukcí pro sdílení práce, jsou popsány v [oddílu 2.7.2](#272-data-sharing-attribute-clauses).

### <a name="271-threadprivate-directive"></a>2.7.1 threadprivate – direktiva

Direktiva `threadprivate` zpřístupňuje pojmenované proměnné rozsahu souboru, oboru názvů nebo statických proměnných oboru bloku, které jsou uvedeny v *proměnné-list* Private pro vlákno. *Proměnná-list* je seznam proměnných oddělených čárkami, které nemají nekompletní typ. Syntaxe direktivy `threadprivate` je následující:

```cpp
#pragma omp threadprivate(variable-list) new-line
```

Každá kopie `threadprivate` proměnné je inicializována jednou, na nespecifikovaném místě v programu před prvním odkazem na tuto kopii, a běžným způsobem (tj. jako hlavní kopie by byla inicializována v rámci programu sériového spuštění). Všimněte si, že pokud je objekt odkazován v explicitním inicializátoru `threadprivate` proměnné a hodnota objektu je upravena před prvním odkazem na kopii proměnné, chování není určeno.

Stejně jako u libovolné privátní proměnné vlákno nesmí odkazovat na jinou kopii `threadprivate` objektu vlákna. V rámci sériových oblastí a hlavních oblastí programu budou odkazy na kopii objektu hlavního vlákna.

Po spuštění první paralelní oblasti budou data v `threadprivate`ch objektech zaručena, aby trvala pouze v případě, že byl mechanismus dynamických vláken zakázán a pokud počet vláken zůstane nezměněn pro všechny paralelní oblasti.

Omezení direktivy `threadprivate` jsou následující:

- Direktiva `threadprivate` pro proměnné rozsahu souboru nebo oboru názvů musí být mimo jakékoli definice nebo deklarace a musí obsahovat lexikální předcházet všechny odkazy na jakékoli proměnné v jejím seznamu.

- Každá proměnná v *seznamu proměnných* direktivy `threadprivate` v oboru názvů File nebo Namespace musí odkazovat na deklaraci proměnné v souboru nebo oboru názvů, který lexikální předchází direktivě.

- Direktiva `threadprivate` pro statické proměnné rozsahu bloku musí být uvedena v oboru proměnné, nikoli ve vnořeném oboru. Direktiva musí odcházet před všemi odkazy na všechny proměnné v jejím seznamu.

- Každá proměnná v *seznamu proměnných* direktivy `threadprivate` v oboru bloku musí odkazovat na deklaraci proměnné ve stejném oboru, který je lexikální před direktivou. Deklarace proměnné musí používat specifikátor třídy úložiště static.

- Pokud je proměnná určena v direktivě `threadprivate` v jedné jednotce překladu, musí být zadána v direktivě `threadprivate` v každé jednotce překladu, ve které je deklarována.

- `threadprivate` proměnná se nesmí vyskytovat v žádné klauzuli s výjimkou klauzule `copyin`, `copyprivate`, `schedule`, `num_threads`nebo `if`.

- Adresa `threadprivate` proměnné není konstanta adresy.

- Proměnná `threadprivate` nesmí mít nekompletní typ ani odkazový typ.

- `threadprivate` proměnná s typem třídy bez POD musí mít přístupný, nejednoznačný kopírovací konstruktor, pokud je deklarovaný s explicitním inicializátorem.

Následující příklad ukazuje, jak změnit proměnnou, která se zobrazí v inicializátoru, může způsobit nespecifikované chování a také jak se tomuto problému vyhnout pomocí pomocných objektů a kopírovacího konstruktoru.

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

- [Dynamická vlákna](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) proměnná prostředí

### <a name="272-data-sharing-attribute-clauses"></a>klauzule atributu 2.7.2 pro sdílení dat

Několik direktiv přijímá klauzule, které umožňují uživateli řídit atributy sdílení proměnných po dobu trvání oblasti. Klauzule atributu sdílení se vztahují pouze na proměnné v lexikálním rozsahu direktivy, pro kterou se zobrazí klauzule. U všech direktiv nejsou povoleny všechny následující klauzule. Seznam klauzulí, které jsou platné pro konkrétní direktivu, jsou popsány s direktivou.

Pokud je proměnná viditelná, když dojde k paralelnímu nebo pracovnímu konstruktoru sdílení a proměnná není určena v klauzuli atributu sdílení nebo direktivě `threadprivate`, pak je proměnná sdílená. Statické proměnné deklarované v dynamickém rozsahu paralelní oblasti jsou sdílené. Paměť přidělená haldě (například použití `malloc()` v C nebo C++ v operátoru `new` v C++) je sdílená. (Ukazatel na tuto paměť ale může být buď privátní, nebo sdílený.) Proměnné s automatickou dobou trvání úložiště deklarované v dynamickém rozsahu paralelní oblasti jsou soukromé.

Většina klauzulí akceptuje argument *variabilního seznamu* , což je seznam proměnných oddělených čárkami, které jsou viditelné. Pokud proměnná odkazovaná v klauzuli atributu Data Sharing má typ odvozený ze šablony a v programu nejsou žádné další odkazy na tuto proměnnou, chování není definováno.

Všechny proměnné, které se zobrazují v klauzulích direktivy, musí být viditelné. Klauzule mohou být podle potřeby opakovány, ale žádnou proměnnou nelze zadat ve více než jedné klauzuli, s výjimkou, že proměnnou lze zadat jak v `firstprivate`, tak v klauzuli `lastprivate`.

Následující části popisují klauzule atributů pro sdílení dat:

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [sdíleného](#2724-shared)
- [default](#2725-default)
- [reduction](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

Klauzule `private` deklaruje proměnné v variabilním seznamu jako soukromé pro každé vlákno v týmu. Syntaxe klauzule `private` je následující:

```cpp
private(variable-list)
```

Chování proměnné zadané v klauzuli `private` je následující. Nový objekt s automatickým trváním úložiště je přidělen pro konstrukci. Velikost a zarovnání nového objektu jsou určeny typem proměnné. K tomuto přidělení dojde jednou pro každé vlákno v týmu a v případě potřeby je vyvolán výchozí konstruktor pro objekt třídy. v opačném případě je počáteční hodnota neurčitá.  Původní objekt odkazovaný proměnnou má neurčitou hodnotu po vstupu do konstrukce, nesmí být upraven v dynamickém rozsahu konstrukce a má po ukončení konstrukce neurčitou hodnotu.

V lexikálním rozsahu konstrukce direktivy odkazuje proměnná na nový privátní objekt přidělený vláknem.

Omezení pro `private` klauzuli jsou následující:

- Proměnná s typem třídy, která je zadána v klauzuli `private`, musí mít přístupný, nejednoznačný výchozí konstruktor.

- Proměnná zadaná v klauzuli `private` nesmí mít `const`kvalifikovaný typ, pokud nemá typ třídy s členem `mutable`.

- Proměnná zadaná v klauzuli `private` nesmí mít nekompletní typ ani odkazový typ.

- Proměnné, které se zobrazují v klauzuli `reduction` direktivy `parallel`, nelze zadat v klauzuli `private` v direktivě sdílení práce, která se váže k paralelní konstrukci.

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

Klauzule `firstprivate` poskytuje nadmnožinu funkcí poskytovaných klauzulí `private`. Syntaxe klauzule `firstprivate` je následující:

```cpp
firstprivate(variable-list)
```

Proměnné zadané v *variabilním seznamu* mají sémantiku klauzule `private`, jak je popsáno v [oddílu 2.7.2.1](#2721-private). Inicializace nebo konstrukce se stane, jako kdyby byla provedena jednou pro vlákno, před provedením konstrukce vlákna. V případě klauzule `firstprivate` u paralelní konstrukce je počáteční hodnota nového privátního objektu hodnotou původního objektu, který existuje bezprostředně před paralelní konstrukcí vlákna, který ho zaznamená. V případě klauzule `firstprivate` v konstruktoru pro sdílení práce je počáteční hodnota nového soukromého objektu pro každé vlákno, který spouští konstruktor Work-Sharing, hodnotou původního objektu, který existuje před bodem v čase, kdy stejné vlákno narazí na konstruktor Work-Sharing. Kromě toho pro C++ objekty je nový privátní objekt pro každé vlákno zkopírován z původního objektu.

Omezení pro `firstprivate` klauzuli jsou následující:

- Proměnná zadaná v klauzuli `firstprivate` nesmí mít nekompletní typ ani odkazový typ.

- Proměnná s typem třídy, která je zadána jako `firstprivate`, musí mít přístupný, nejednoznačný kopírovací konstruktor.

- Proměnné, které jsou soukromé v rámci paralelní oblasti nebo které se zobrazují v klauzuli `reduction` direktivy `parallel`, nelze zadat v klauzuli `firstprivate` v direktivě sdílení práce, která se váže k paralelní konstrukci.

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

Klauzule `lastprivate` poskytuje nadmnožinu funkcí poskytovaných klauzulí `private`. Syntaxe klauzule `lastprivate` je následující:

```cpp
lastprivate(variable-list)
```

Proměnné zadané v *proměnné-list* mají sémantiku klauzule `private`. Je-li v direktivě, která identifikuje konstruktor pro sdílení práce, uvedena klauzule `lastprivate`, je hodnota každé `lastprivate` proměnné z sekvenčně poslední iterace přidružené smyčky nebo lexikálního posledního oddílu přiřazena k původnímu objektu proměnné. Proměnné, které nemají přiřazenou hodnotu poslední iterací `for` nebo `parallel for`nebo lexikálním posledním oddílem `sections` nebo direktivy `parallel sections`, mají po konstruktoru neurčité hodnoty. Nepřiřazené podobjekty mají také neurčitou hodnotu za konstrukcí.

Omezení pro `lastprivate` klauzuli jsou následující:

- Všechna omezení pro `private` použít.

- Proměnná s typem třídy, která je zadána jako `lastprivate`, musí mít přístupnou, nejednoznačný operátor přiřazení kopie.

- Proměnné, které jsou soukromé v rámci paralelní oblasti nebo které se zobrazují v klauzuli `reduction` direktivy `parallel`, nelze zadat v klauzuli `lastprivate` v direktivě sdílení práce, která se váže k paralelní konstrukci.

#### <a name="2724-shared"></a>2.7.2.4 shared

Tato klauzule sdílí proměnné, které se zobrazí v *seznamu variabilních* vláken mezi všemi vlákny v týmu. Všechna vlákna v rámci týmu mají přístup ke stejné oblasti úložiště pro proměnné `shared`.

Syntaxe klauzule `shared` je následující:

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 default

Klauzule `default` umožňuje uživateli ovlivnit atributy pro sdílení dat proměnných. Syntaxe klauzule `default` je následující:

```cpp
default(shared | none)
```

Určení `default(shared)` je ekvivalentní k explicitnímu výpisu všech aktuálně viditelných proměnných v klauzuli `shared`, pokud není `threadprivate` nebo `const`kvalifikované. Pokud není k dispozici explicitní klauzule `default`, výchozí chování je stejné jako při určení `default(shared)`.

Určení `default(none)` vyžaduje, aby alespoň jedna z následujících podmínek měla být pravdivá pro každý odkaz na proměnnou v lexikálním rozsahu paralelní konstrukce:

- Proměnná je explicitně uvedena v klauzuli atributu pro sdílení dat konstrukce, která obsahuje odkaz.

- Proměnná je deklarována v rámci paralelní konstrukce.

- Proměnná je `threadprivate`.

- Proměnná má `const`kvalifikovaný typ.

- Proměnná je řídicí proměnná smyčky pro smyčku `for`, která bezprostředně následuje `for` nebo `parallel for` direktiva a odkaz na proměnnou se zobrazí uvnitř smyčky.

Zadání proměnné v klauzuli `firstprivate`, `lastprivate`nebo `reduction` uzavřené direktivy způsobí implicitní odkaz na proměnnou v ohraničujícím kontextu. Tyto implicitní odkazy se vztahují i na výše uvedené požadavky.

V direktivě `parallel` se dá zadat jenom jedna klauzule `default`.

Výchozí atribut pro sdílení dat proměnné lze přepsat pomocí klauzulí `private`, `firstprivate`, `lastprivate`, `reduction`a `shared`, jak je znázorněno v následujícím příkladu:

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

Tato klauzule provádí snížení skalárních proměnných, které se zobrazí v *variabilním seznamu*s operátorem *op*. Syntaxe klauzule `reduction` je následující:

`reduction(` *op* `:` *Variable seznam* `)`

Pro příkaz s jedním z následujících forem je obvykle zadáno snížení:

- *x* `=` *×* *op* – *výraz*
- *x* *binop* `=` *výraz*
- *x* `=` *expr* *op* *x* (s výjimkou odčítání)
- `++` *x*
- `++` *x*
- `--` *x*
- `--` *x*

kde:

*znak*<br/>
Jedna z proměnných omezení uvedených v seznamu.

*seznam proměnných*<br/>
Čárkami oddělený seznam skalárních proměnných snižování.

*výrazu*<br/>
Výraz s skalárním typem, který neodkazuje na *x*.

*evřít*<br/>
Není přetížený operátor, ale jedna z `+`, `*`, `-`, `&`, `^`, `|`, `&&`nebo `||`.

*binop*<br/>
Není přetížený operátor, ale jedna z `+`, `*`, `-`, `&`, `^`nebo `|`.

Následuje příklad klauzule `reduction`:

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

Jak je znázorněno v příkladu, operátor může být skrytý uvnitř volání funkce. Uživatel by měl být pečlivý, aby operátor zadaný v klauzuli `reduction` odpovídal operaci snížení.

I když pravý operand operátoru `||` nemá v tomto příkladu žádné vedlejší účinky, jsou povoleny, ale měli byste je používat opatrně. V tomto kontextu se může při paralelním provádění zabývat vedlejším účinkem, který neproběhne během sekvenčního provádění smyčky. K tomuto rozdílu může dojít, protože pořadí provádění iterací je neurčité.

Operátor slouží k určení počáteční hodnoty všech privátních proměnných používaných kompilátorem pro účely zmenšení a určení operátoru finalizace. Zadáním operátoru explicitně umožníte, aby příkaz krácení byl mimo lexikální rozsah konstrukce. V direktivě může být zadán libovolný počet klauzulí `reduction`, ale proměnná se může zobrazit nejvýše v jedné klauzuli `reduction` této direktivy.

Soukromá kopie každé proměnné v *variabilním seznamu* je vytvořena, jedna pro každé vlákno, jako kdyby byla použita klauzule `private`. Soukromá kopie je inicializována podle operátoru (viz následující tabulka).

Na konci oblasti, pro kterou byla zadána klauzule `reduction`, je původní objekt aktualizován tak, aby odrážel výsledek kombinování jeho původní hodnoty s konečnou hodnotou každé z privátních kopií pomocí zadaného operátoru. Operátory redukce jsou všechny asociativní (s výjimkou odčítání) a kompilátor může volně znovu přidružit výpočet konečné hodnoty. (K vytvoření konečné hodnoty se přidají částečné výsledky snížení odčítání.)

Hodnota původního objektu se projeví neurčité, když první vlákno dosáhne obsažené klauzule a zůstane tak, dokud není dokončeno vyvýšení výpočtu.  Obvykle se výpočet na konci konstrukce dokončí. Pokud je však klauzule `reduction` použita u konstrukce, ke které je použita také `nowait`, hodnota původního objektu zůstane neurčitá, dokud nebude provedena synchronizace bariéry, aby bylo zajištěno, že všechna vlákna dokončí klauzuli `reduction`.

Následující tabulka uvádí platné operátory a jejich kanonické inicializační hodnoty. Skutečná inicializační hodnota bude konzistentní s datovým typem proměnné omezení.

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

Omezení pro `reduction` klauzuli jsou následující:

- Typ proměnných v klauzuli `reduction` musí být platný pro operátor redukce, s výjimkou toho, že typy ukazatelů a typy odkazů nejsou nikdy povoleny.

- Proměnná zadaná v klauzuli `reduction` nesmí být kvalifikována `const`.

- Proměnné, které jsou soukromé v rámci paralelní oblasti nebo které se zobrazují v klauzuli `reduction` direktivy `parallel`, nelze zadat v klauzuli `reduction` v direktivě sdílení práce, která se váže k paralelní konstrukci.

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

Klauzule `copyin` poskytuje mechanismus pro přiřazení stejné hodnoty k `threadprivate` proměnných pro každé vlákno v týmu, který provádí paralelní oblast. Pro každou proměnnou určenou v klauzuli `copyin` je hodnota proměnné v hlavním vlákně týmu zkopírována, stejně jako při přiřazení, k kopiím soukromého vlákna na začátku paralelní oblasti. Syntaxe klauzule `copyin` je následující:

```cpp

copyin(
variable-list
)
```

Omezení pro `copyin` klauzuli jsou následující:

- Proměnná, která je určená v klauzuli `copyin`, musí mít přístupný, nejednoznačný operátor přiřazení kopie.

- Proměnná, která je určená v klauzuli `copyin`, musí být proměnná `threadprivate`.

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

Klauzule `copyprivate` poskytuje mechanismus pro použití soukromé proměnné pro vysílání hodnoty od jednoho člena týmu do ostatních členů. Je alternativou k použití sdílené proměnné pro hodnotu, pokud by byla taková sdílená proměnná obtížné (například v rekurzi vyžadující jinou proměnnou na každé úrovni). Klauzule `copyprivate` se může vyskytovat pouze v direktivě `single`.

Syntaxe klauzule `copyprivate` je následující:

```cpp

copyprivate(
variable-list
)
```

Účinek klauzule `copyprivate` na proměnné v jejím seznamu proměnných probíhá po spuštění strukturovaného bloku přidruženého k konstruktoru `single` a předtím, než kterýkoli z vláken v týmu opustí bariéru na konci konstrukce. Potom ve všech ostatních vláknech v týmu, pro každou proměnnou v *seznamu proměnná-list*, tato proměnná se bude definovat (jako if přiřazením) s hodnotou odpovídající proměnné ve vlákně, které spustilo strukturovaný blok konstrukce.

Omezení klauzule `copyprivate` jsou následující:

- Proměnná zadaná v klauzuli `copyprivate` nesmí být uvedena v klauzuli `private` nebo `firstprivate` pro stejnou direktivu `single`.

- Pokud je v dynamickém rozsahu paralelní oblasti zjištěna direktiva `single` s klauzulí `copyprivate`, všechny proměnné určené v klauzuli `copyprivate` musí být v ohraničujícím kontextu privátní.

- Proměnná, která je určená v klauzuli `copyprivate`, musí mít přístup k nejednoznačnému operátoru přiřazení kopie.

## <a name="28-directive-binding"></a>2,8 – vazba direktiv

Dynamická vazba direktiv musí splňovat následující pravidla:

- Direktivy `for`, `sections`, `single`, `master`a `barrier` se vážou k dynamicky ohraničujícímu `parallel`, pokud existuje, bez ohledu na hodnotu jakékoliv `if` klauzule, která může být v dané direktivě přítomna. Pokud není v současné době prováděna žádná paralelní oblast, jsou direktivy spouštěny týmem, který se skládá pouze z hlavního vlákna.

- Direktiva `ordered` se váže k dynamicky ohraničujícímu `for`.

- Direktiva `atomic` vynutila výhradní přístup s ohledem na direktivy `atomic` ve všech vláknech, nikoli jenom na aktuální tým.

- Direktiva `critical` vynutila výhradní přístup s ohledem na direktivy `critical` ve všech vláknech, nikoli jenom na aktuální tým.

- Direktiva nemůže nikdy vytvořit vazby na žádnou direktivu mimo nejbližší dynamicky ohraničující `parallel`.

## <a name="29-directive-nesting"></a>2,9 – vnořování direktiv

Dynamické vnořování direktiv musí splňovat následující pravidla:

- Direktiva `parallel` dynamicky uvnitř jiného `parallel` logicky vytvoří nový tým, který se skládá pouze z aktuálního vlákna, pokud není povolen vnořený paralelismu.

- direktivy `for`, `sections`a `single`, které jsou vázány na stejný `parallel`, nejsou povoleny uvnitř sebe.

- direktivy `critical` se stejným názvem nemůžou být vnořené uvnitř sebe. Všimněte si, že toto omezení není dostačující, aby se zabránilo zablokování.

- direktivy `for`, `sections`a `single` nejsou povolené v dynamickém rozsahu `critical`, `ordered`a `master`ch oblastí, pokud se direktivy vážou ke stejnému `parallel` jako oblasti.

- direktivy `barrier` nejsou povolené v dynamickém rozsahu `for`, `ordered`, `sections`, `single`, `master`a `critical`ch oblastech, pokud se direktivy vážou ke stejnému `parallel` jako oblasti.

- direktivy `master` nejsou povolené v dynamickém rozsahu `for`, `sections`a direktivy `single`, pokud se direktivy `master` vážou ke stejnému `parallel` jako direktivy pro sdílení práce.

- direktivy `ordered` nejsou povoleny v dynamickém rozsahu `critical`ch oblastí, pokud se direktivy vážou ke stejnému `parallel` jako oblasti.

- Jakákoli direktiva, která je povolena při dynamickém spuštění uvnitř paralelní oblasti, je povolena také při spuštění mimo paralelní oblast. Při dynamickém provedení mimo uživatelem zadanou paralelní oblast je direktiva spuštěna týmem, který se skládá pouze z hlavního vlákna.
