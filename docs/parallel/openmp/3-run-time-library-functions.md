---
title: 3. Funkce knihovny prostředí Runtime
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 767c006b0a2d81af4d1f8f2e23f84d7847326f31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370272"
---
# <a name="3-run-time-library-functions"></a>3. Funkce knihovny run-time

Tato část popisuje funkce knihovny OpenMP C a C++. Hlavička ** \<omp.h>** deklaruje dva typy, několik funkcí, které lze použít k řízení a dotazování paralelní spuštění prostředí a uzamčení funkce, které lze použít k synchronizaci přístupu k datům.

Typ `omp_lock_t` je typ objektu, který může představovat, že zámek je k dispozici nebo že vlákno vlastní zámek. Tyto zámky jsou označovány jako *jednoduché zámky*.

Typ `omp_nest_lock_t` je typ objektu, který může představovat buď, že zámek je k dispozici, nebo identitu podprocesu, který vlastní zámek a *počet vnoření* (je popsáno níže). Tyto zámky jsou označovány jako *nestabilní zámky*.

Funkce knihovny jsou externí funkce s vazbou "C".

Popisy v této kapitole jsou rozděleny do následujících témat:

- [Funkce prostředí provádění](#31-execution-environment-functions)
- [Funkce zámku](#32-lock-functions)
- [Časovací rutiny](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 Funkce prostředí provádění

Funkce popsané v této části ovlivňují a monitorují vlákna, procesory a paralelní prostředí:

- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_get_max_threads](#313-omp_get_max_threads-function)
- [omp_get_thread_num](#314-omp_get_thread_num-function)
- [omp_get_num_procs](#315-omp_get_num_procs-function)
- [omp_in_parallel](#316-omp_in_parallel-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [omp_get_dynamic](#318-omp_get_dynamic-function)
- [omp_set_nested](#319-omp_set_nested-function)
- [omp_get_nested](#3110-omp_get_nested-function)

### <a name="311-omp_set_num_threads-function"></a><a name="311-omp_set_num_threads-function"></a>3.1.1 omp_set_num_threads funkce

Funkce `omp_set_num_threads` nastaví výchozí počet podprocesů pro pozdější paralelní oblasti, `num_threads` které neurčují klauzuli. Formát je následující:

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

Hodnota parametru *num_threads* musí být kladné celé číslo. Jeho účinek závisí na tom, zda je povoleno dynamické nastavení počtu vláken. Komplexní soubor pravidel týkajících se interakce `omp_set_num_threads` mezi funkcí a dynamickým nastavením závitů naleznete [v části 2.3](2-directives.md#23-parallel-construct).

Tato funkce má účinky popsané výše při volání z `omp_in_parallel` části programu, kde funkce vrátí nulu. Pokud je volána z části programu, `omp_in_parallel` kde funkce vrátí nenulovou hodnotu, chování této funkce není definováno.

Toto volání má `OMP_NUM_THREADS` přednost před proměnnou prostředí. Výchozí hodnotu pro počet podprocesů, které mohou `omp_set_num_threads` být vytvořeny `OMP_NUM_THREADS` voláním nebo nastavením proměnné `parallel` prostředí, lze `num_threads` explicitně přepsat na jednu direktivu zadáním klauzule.

Další informace naleznete [v tématu omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Křížové odkazy

- [omp_set_dynamic](#317-omp_set_dynamic-function) funkce
- [omp_get_dynamic](#318-omp_get_dynamic-function) funkce
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) proměnné prostředí
- [num_threads](2-directives.md#23-parallel-construct) doložka

### <a name="312-omp_get_num_threads-function"></a><a name="312-omp_get_num_threads-function"></a>3.1.2 omp_get_num_threads funkce

Funkce `omp_get_num_threads` vrátí počet podprocesů aktuálně v týmu provádění paralelní oblasti, ze které je volána. Formát je následující:

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

Klauzule, `num_threads` `omp_set_num_threads` funkce a `OMP_NUM_THREADS` proměnná prostředí řídí počet vláken v týmu.

Pokud počet podprocesů nebyl explicitně nastaven uživatelem, výchozí hodnota je definována implementací. Tato funkce se váže na `parallel` nejbližší ohraničující směrnice. Pokud volána ze sériové části programu nebo z vnořené paralelní oblasti, která je serializována, tato funkce vrátí 1.

Další informace naleznete [v tématu omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Křížové odkazy

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a><a name="313-omp_get_max_threads-function"></a>3.1.3 omp_get_max_threads funkce

Funkce `omp_get_max_threads` vrátí celé číslo, které je zaručeno, že je alespoň tak velký jako počet podprocesů, které `num_threads` by byly použity k vytvoření týmu, pokud paralelní oblast bez klauzule byly vidět v tomto okamžiku v kódu. Formát je následující:

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

Následující vyjadřuje dolní mez hodnoty `omp_get_max_threads`:

> *závity použité pro další tým* <= `omp_get_max_threads`

Všimněte si, že `num_threads` pokud jiná paralelní oblast používá klauzuli k vyžádání určitého `omp_get_max_threads` počtu podprocesů, záruka na dolní hranici výsledku již nedrží.

Vrácená `omp_get_max_threads` hodnota funkce lze dynamicky přidělit dostatečné úložiště pro všechna vlákna v týmu vytvořeném v další paralelní oblasti.

#### <a name="cross-references"></a>Křížové odkazy

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a><a name="314-omp_get_thread_num-function"></a>3.1.4 omp_get_thread_num funkce

Funkce `omp_get_thread_num` vrátí číslo vlákna v rámci svého týmu, podprocesu provádění funkce. Číslo vlákna leží `omp_get_num_threads()`mezi 0 a -1, včetně. Hlavní vlákno týmu je podproces 0.

Formát je následující:

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

Pokud volána ze `omp_get_thread_num` sériové oblasti, vrátí 0. Pokud volána z vnořené paralelní oblasti, která je serializována, tato funkce vrátí 0.

#### <a name="cross-references"></a>Křížové odkazy

- [omp_get_num_threads](#312-omp_get_num_threads-function) funkce

### <a name="315-omp_get_num_procs-function"></a><a name="315-omp_get_num_procs-function"></a>3.1.5 omp_get_num_procs funkce

Funkce `omp_get_num_procs` vrátí počet procesorů, které jsou k dispozici pro program v době, kdy je funkce volána. Formát je následující:

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a><a name="316-omp_in_parallel-function"></a>3.1.6 omp_in_parallel funkce

Funkce `omp_in_parallel` vrátí nenulovou hodnotu, pokud je volána v rámci dynamického rozsahu paralelní oblasti, která se provádí paralelně; v opačném případě vrátí 0. Formát je následující:

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Tato funkce vrátí nenulovou hodnotu při volání z v rámci oblasti provádění paralelně, včetně vnořené oblasti, které jsou serializovány.

### <a name="317-omp_set_dynamic-function"></a><a name="317-omp_set_dynamic-function"></a>3.1.7 omp_set_dynamic funkce

Funkce `omp_set_dynamic` umožňuje nebo zakazuje dynamické nastavení počtu podprocesů, které jsou k dispozici pro spuštění paralelních oblastí. Formát je následující:

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Pokud *dynamic_threads* vyhodnotí na nenulovou hodnotu, počet podprocesů, které se používají pro provádění nadcházející paralelní oblasti mohou být upraveny automaticky prostředí za běhu, aby co nejlépe využívat systémové prostředky. V důsledku toho je počet podprocesů určených uživatelem maximální počet podprocesů. Počet podprocesů v týmu provádějící paralelní oblast zůstane pevná po dobu trvání `omp_get_num_threads` této paralelní oblasti a je hlášena funkce.

Pokud *dynamic_threads* vyhodnotí 0, dynamické úpravy je zakázáno.

Tato funkce má účinky popsané výše při volání z `omp_in_parallel` části programu, kde funkce vrátí nulu. Pokud je volána z části programu, `omp_in_parallel` kde funkce vrátí nenulovou hodnotu, chování této funkce není definováno.

Volání `omp_set_dynamic` má přednost před `OMP_DYNAMIC` proměnnou prostředí.

Výchozí hodnota pro dynamické nastavení podprocesů je definována implementací. V důsledku toho uživatelské kódy, které závisí na určitý počet podprocesů pro správné spuštění by měl explicitně zakázat dynamická vlákna. Implementace nejsou nutné k poskytování možnosti dynamicky upravit počet podprocesů, ale jsou nutné poskytnout rozhraní pro podporu přenositelnost napříč všemi platformami.

#### <a name="microsoft-specific"></a>specifické pro společnost Microsoft

Současná podpora `omp_get_dynamic` `omp_set_dynamic` a je následující:

Vstupní parametr `omp_set_dynamic` do nemá vliv na zásady podprocesu a nemění počet podprocesů. `omp_get_num_threads`vždy vrátí buď uživatelem definované číslo, pokud je nastaveno, nebo výchozí číslo vlákna. V aktuální implementaci `omp_set_dynamic(0)` společnosti Microsoft vypne dynamické podprocesy tak, aby existující sadu vláken lze znovu použít pro následující paralelní oblasti. `omp_set_dynamic(1)`zapne dynamické podprocesy zahozením existující sady vláken a vytvořením nové sady pro nadcházející paralelní oblast. Počet podprocesů v nové sadě je stejný jako stará sada a je `omp_get_num_threads`založen na vrácené hodnotě . Proto pro nejlepší výkon, použijte `omp_set_dynamic(0)` k opětovnému použití existující podprocesy.

#### <a name="cross-references"></a>Křížové odkazy

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a><a name="318-omp_get_dynamic-function"></a>3.1.8 omp_get_dynamic funkce

Funkce `omp_get_dynamic` vrátí nenulovou hodnotu, pokud je povolena dynamická úprava podprocesů, a jinak vrátí hodnotu 0. Formát je následující:

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Pokud implementace neimplementuje dynamické úpravy počtu podprocesů, tato funkce vždy vrátí 0. Další informace naleznete [v tématu omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Křížové odkazy

- Popis dynamického nastavení závitu naleznete [v omp_set_dynamic](#317-omp_set_dynamic-function).

### <a name="319-omp_set_nested-function"></a><a name="319-omp_set_nested-function"></a>3.1.9 omp_set_nested funkce

Funkce `omp_set_nested` povolí nebo zakáže vnořený paralelismus. Formát je následující:

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Pokud *vnořené* vyhodnotí 0, vnořené paralelismus je zakázáno, což je výchozí a vnořené paralelní oblasti jsou serializovány a provedeny aktuální vlákno. V opačném případě je povoleno vnořené paralelismu a paralelní oblasti, které jsou vnořené může nasadit další vlákna tvořit vnořené týmy.

Tato funkce má účinky popsané výše při volání z `omp_in_parallel` části programu, kde funkce vrátí nulu. Pokud je volána z části programu, `omp_in_parallel` kde funkce vrátí nenulovou hodnotu, chování této funkce není definováno.

Toto volání má `OMP_NESTED` přednost před proměnnou prostředí.

Je-li povoleno vnořené paralelismus, počet podprocesů používaných ke spuštění vnořené paralelní oblasti je implementován. V důsledku toho openmp kompatibilní implementace mohou serializovat vnořené paralelní oblasti i v případě, že je povolen vnořený paralelismus.

#### <a name="cross-references"></a>Křížové odkazy

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a><a name="3110-omp_get_nested-function"></a>3.1.10 omp_get_nested funkce

Funkce `omp_get_nested` vrátí nenulovou hodnotu, pokud je povolen vnořený paralelismus, a 0, pokud je zakázán. Další informace o vnořené paralelismu naleznete [v tématu omp_set_nested](#319-omp_set_nested-function). Formát je následující:

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Pokud implementace neimplementuje vnořený paralelismus, tato funkce vždy vrátí 0.

## <a name="32-lock-functions"></a>3.2 Funkce zámku

Funkce popsané v této části manipulovat zámky používané pro synchronizaci.

Pro následující funkce musí mít proměnná lock typ `omp_lock_t`. Tato proměnná musí být přístupná pouze prostřednictvím těchto funkcí. Všechny funkce zámku vyžadují argument, `omp_lock_t` který má ukazatel na text.

- Funkce [omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) inicializuje jednoduchý zámek.
- Funkce [omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) odstraní jednoduchý zámek.
- Funkce [omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) čeká, dokud není k dispozici jednoduchý zámek.
- Funkce [omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) uvolní jednoduchý zámek.
- Funkce [omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) testuje jednoduchý zámek.

Pro následující funkce musí mít proměnná lock typ `omp_nest_lock_t`.  Tato proměnná musí být přístupná pouze prostřednictvím těchto funkcí. Všechny funkce nestabilní zámek vyžadují argument, `omp_nest_lock_t` který má ukazatel na text.

- Funkce [omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) inicializuje zámek nestable.
- Funkce [omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) odstraní nestabilní zámek.
- Funkce [omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) čeká, dokud není k dispozici zámek nestable.
- Funkce [omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) uvolní zámek nestable.
- Funkce [omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) testuje nestabilní zámek.

Funkce zámku OpenMP přistupují k proměnné zámku tak, že vždy čtou a aktualizují nejaktuálnější hodnotu proměnné zámku. Proto není nutné, aby program OpenMP obsahoval `flush` explicitní direktivy, aby se ujistil, že hodnota proměnné zámku je konzistentní mezi různými vlákny. (Může být potřeba, `flush` aby směrnice odpovídaly hodnotám jiných proměnných.)

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a><a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 omp_init_lock a omp_init_nest_lock funkce

Tyto funkce poskytují jediný způsob inicializace zámku. Každá funkce inicializuje zámek přidružený k *zámku* parametrů pro použití v nadcházejících voláních. Formát je následující:

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Počáteční stav je odemčen (to znamená, že zámek nevlastní žádné vlákno). Pro nestabilní zámek počáteční počet vnoření je nula. Je nekompatibilní volat některou z těchto rutin s proměnnou zámku, která již byla inicializována.

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a><a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 omp_destroy_lock a omp_destroy_nest_lock funkce

Tyto funkce ujistěte se, že ukázal na zámek *proměnné* zámku je neinicializován. Formát je následující:

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

Je nekompatibilní volat některou z těchto rutin s proměnnou zámku, která je neinicializovaná nebo odemčená.

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a><a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 omp_set_lock a omp_set_nest_lock funkce

Každá z těchto funkcí blokuje podproces provádění funkce, dokud zadaný zámek je k dispozici a potom nastaví zámek. Jednoduchý zámek je k dispozici, pokud je odemčený. Nestabilní zámek je k dispozici, pokud je odemčený nebo pokud je již vlastněn vláknem provádějícím funkci. Formát je následující:

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Pro jednoduchý zámek argument `omp_set_lock` funkce musí směřovat na inicializovanou proměnnou zámku. Vlastnictví zámku je uděleno podprocesu vykonávajícímu funkci.

Pro nestabilní zámek argument `omp_set_nest_lock` funkce musí směřovat na inicializovanou proměnnou zámku. Počet vnoření se zvětšuje a vlákno je uděleno nebo udržuje vlastnictví zámku.

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a><a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>3.2.4 omp_unset_lock a omp_unset_nest_lock funkce

Tyto funkce poskytují prostředky uvolnění vlastnictví zámku. Formát je následující:

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

Argument pro každou z těchto funkcí musí ukazovat na inicializovanou proměnnou zámku vlastněnou podprocesem provádějícím funkci. Chování není definována, pokud vlákno nevlastní tento zámek.

Pro jednoduchý zámek `omp_unset_lock` funkce uvolní vlákno provádění funkce z vlastnictví zámku.

Pro nestabilní zámek `omp_unset_nest_lock` funkce sníží počet vnoření a uvolní vlákno provádění funkce z vlastnictví zámku, pokud výsledný počet je nula.

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a><a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 omp_test_lock a omp_test_nest_lock funkce

Tyto funkce se pokusí nastavit zámek, ale neblokují spuštění vlákna. Formát je následující:

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

Argument musí ukazovat na inicializovanou proměnnou zámku. Tyto funkce se pokusí nastavit zámek `omp_set_lock` stejným `omp_set_nest_lock`způsobem jako a , s tím rozdílem, že neblokují spuštění vlákna.

Pro jednoduchý zámek `omp_test_lock` funkce vrátí nenulovou hodnotu, pokud je zámek úspěšně nastaven; v opačném případě vrátí nulu.

Pro nestabilní zámek `omp_test_nest_lock` funkce vrátí nový počet vnoření, pokud je zámek úspěšně nastaven; v opačném případě vrátí nulu.

## <a name="33-timing-routines"></a>3.3 Časovací rutiny

Funkce popsané v této části podporují přenosný časovač nástěnných hodin:

- Funkce [omp_get_wtime](#331-omp_get_wtime-function) vrátí uplynulý čas nástěnných hodin.
- Funkce [omp_get_wtick](#332-omp_get_wtick-function) vrátí sekundy mezi po sobě jdoucími tiky hodin.

### <a name="331-omp_get_wtime-function"></a><a name="331-omp_get_wtime-function"></a>3.3.1 omp_get_wtime funkce

Funkce `omp_get_wtime` vrátí hodnotu s dvojitou přesností s plovoucí desetinnou hodnotou rovnou uplynulé době nástěnných hodin v sekundách od určitého "času v minulosti".  Skutečné "čas v minulosti" je libovolný, ale je zaručeno, že se nezmění během provádění aplikačního programu. Formát je následující:

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

Předpokládá se, že funkce bude použita k měření uplynulých časů, jak je znázorněno v následujícím příkladu:

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Vrácené časy jsou "za vlákno časy", což znamená, že nemusí být globálně konzistentní ve všech vláknech, které se účastní aplikace.

### <a name="332-omp_get_wtick-function"></a><a name="332-omp_get_wtick-function"></a>3.3.2 omp_get_wtick funkce

Funkce `omp_get_wtick` vrátí hodnotu s dvojitou přesností s plovoucí desetinnou hodnotou rovnající se počtu sekund mezi po sobě jdoucími značkami hodin. Formát je následující:

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
