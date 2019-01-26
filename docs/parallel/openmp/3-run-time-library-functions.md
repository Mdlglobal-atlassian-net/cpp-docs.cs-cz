---
title: 3. Funkce knihovny run-time
ms.date: 01/17/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 7d48338683037c06ca208bff32c5c2e9b546a9fe
ms.sourcegitcommit: 774db6a005a85e2a1268ca34309b993792701819
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065019"
---
# <a name="3-run-time-library-functions"></a>3. Funkce knihovny run-time

Tato část popisuje funkce knihovny run-time OpenMP – C a C++. Záhlaví  **\<omp.h >** deklaruje dva typy, několik funkcí, které můžete použít k řízení a zadat dotaz na prostředí paralelní zpracování a uzamčení funkce, které slouží k synchronizaci přístupu k datům.

Typ `omp_lock_t` typ objektu, který je schopný reprezentovat, je k dispozici zámek, nebo vlákna je vlastníkem zámku. Tyto zámky se označují jako *jednoduché zámky*.

Typ `omp_nest_lock_t` je schopný reprezentovat buď typ objektu zámek je k dispozici, nebo identitu vlákna, která vlastní zámek a *vnoření počet* (popsaných níže). Tyto zámky se označují jako *vnořitelných zámků*.

Funkce knihovny jsou externí funkce s propojením "C".

Popisy v této kapitole jsou rozdělené do následujících témat:

- [Funkce spouštěcího prostředí](#31-execution-environment-functions)
- [Funkce zamykání](#32-lock-functions)
- [Rutiny časování](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 funkce spouštěcího prostředí

Funkce popsané v této části vliv a sledovat vlákna, procesory a paralelní prostředí:

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

### <a name="311-ompsetnumthreads-function"></a>3.1.1 omp_set_num_threads – funkce

`omp_set_num_threads` Funkce nastaví výchozí počet vláken pro později paralelních oblastí, které nechcete zadat `num_threads` klauzuli. Formát je následujícím způsobem:

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

Hodnota parametru *num_threads* musí být kladné celé číslo. Jeho dopad závisí na tom, zda je povolena dynamické úpravy počtu vláken. Pro komplexní sadu pravidel o interakci mezi `omp_set_num_threads` funkce a dynamické úpravy vláken, najdete v části 2.3.

Tato funkce má důsledky je popsáno výše, při volání z část programu, kde `omp_in_parallel` vrátí funkce hodnotu nula. Pokud je volána z část programu, kde `omp_in_parallel` funkce vrátí nenulovou hodnotu, nedefinované chování této funkce.

Toto volání má vyšší prioritu než `OMP_NUM_THREADS` proměnné prostředí. Výchozí hodnota pro počet vláken, které mohou být stanoveny voláním `omp_set_num_threads` nebo nastavením `OMP_NUM_THREADS` proměnné prostředí, můžete explicitně přepsat v rámci jednoho `parallel` direktiv tak, že zadáte `num_threads` klauzuli.

#### <a name="cross-references"></a>Křížové odkazy

- [omp_set_dynamic](#317-omp_set_dynamic-function) function
- [omp_get_dynamic](#318-omp_get_dynamic-function) function
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) proměnné prostředí
- [num_threads](2-3-parallel-construct.md) – klauzule

### <a name="312-ompgetnumthreads-function"></a>3.1.2 omp_get_num_threads – funkce

`omp_get_num_threads` Funkce vrátí počet vláken aktuálně tým provádí paralelní oblasti, ve kterém je volána. Formát je následujícím způsobem:

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

`num_threads` Klauzule `omp_set_num_threads` funkce a `OMP_NUM_THREADS` proměnnou prostředí řídí počet vláken v týmu.

Pokud počet vláken není nastavený explicitně uživatelem, výchozí hodnota je definován implementací. Tato funkce vytvoří vazbu na nejbližší uzavírající `parallel` směrnice. Pokud je volána z sériového portu část programu nebo z vnořené paralelní oblasti, která je serializovaná, tato funkce vrátí hodnotu 1.

#### <a name="cross-references"></a>Křížové odkazy

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-3-parallel-construct.md)
- [parallel](2-3-parallel-construct.md)

### <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads – funkce

`omp_get_max_threads` Funkce vrátí celé číslo, které se musí být přinejmenším stejně velká jako počet vláken, která se použije k vytvoření týmu, pokud paralelní oblasti bez `num_threads` klauzule chtěli vidět v tomto bodě v kódu. Formát je následujícím způsobem:

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

Následující vyjadřuje dolní mez na hodnotě `omp_get_max_threads`:

```

threads-used-for-next-team
<= omp_get_max_threads
```

Všimněte si, že pokud jiné paralelní oblasti používá `num_threads` klauzule požádat o určitý počet vláken, záruka na dolní mez výsledek `omp_get_max_threads` žádné dlouhé blokování.

`omp_get_max_threads` Návratové hodnoty funkce je možné dynamicky přidělit dostatečné úložiště pro všechna vlákna v týmu, vytvořené na další paralelní oblasti.

#### <a name="cross-references"></a>Křížové odkazy

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-3-parallel-construct.md)

### <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num – funkce

`omp_get_thread_num` Funkce vrací číslo vlákna, v rámci jeho týmu vlákna provádění funkce. Vlákno číslo leží mezi 0 a `omp_get_num_threads()`-1 (včetně). Hlavní vlákno týmu je vlákno 0.

Formát je následujícím způsobem:

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

Pokud je volána ze sériového portu oblasti `omp_get_thread_num` vrátí hodnotu 0. Je-li volat v rámci vnořených paralelní oblasti, která je serializovaná, tato funkce vrátí 0.

#### <a name="cross-references"></a>Křížové odkazy

- [omp_get_num_threads](#312-omp_get_num_threads-function) – funkce

### <a name="315-ompgetnumprocs-function"></a>3.1.5 omp_get_num_procs – funkce

`omp_get_num_procs` Funkce vrací počet procesorů, které jsou k dispozici pro program v době je tato funkce volána. Formát je následujícím způsobem:

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel – funkce

`omp_in_parallel` Funkce vrátí nenulovou hodnotu, pokud je volána v rámci dynamický rozsah paralelní oblasti paralelně prováděných; v opačném případě vrátí hodnotu 0. Formát je následujícím způsobem:

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Tato funkce vrátí nenulovou hodnotu při volání z v rámci oblasti spouští paralelně, včetně vnořených oblastí, které se serializují.

### <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic – funkce

`omp_set_dynamic` Funkce povolí nebo zakáže dynamické úpravy počtu vláken, které jsou k dispozici pro provádění paralelních oblastí. Formát je následujícím způsobem:

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Pokud *dynamic_threads* vyhodnotí na nenulovou hodnotu, počet vláken, která se používají k provádění paralelních oblastí nadcházející může upravit automaticky běhové prostředí tak, aby co nejlépe využívat systémové prostředky. V důsledku toho je počet vláken, které uživatel zadá maximální počet vláken. Počet vláken v týmu provádí paralelní oblasti zůstane po dobu trvání tohoto paralelní oblasti a je ohlášena `omp_get_num_threads` funkce.

Pokud *dynamic_threads* vyhodnotí na hodnotu 0, dynamické úpravy zakázána.

Tato funkce má důsledky je popsáno výše, při volání z část programu, kde `omp_in_parallel` vrátí funkce hodnotu nula. Pokud je volána z část programu, kde `omp_in_parallel` funkce vrátí nenulovou hodnotu, nedefinované chování této funkce.

Volání `omp_set_dynamic` má vyšší prioritu než `OMP_DYNAMIC` proměnné prostředí.

Výchozí nastavení pro dynamické úpravy vlákna, je definováno implementací. V důsledku toho uživatel kódy, které závisí na konkrétní počet vláken pro správné spuštění by měly explicitně zakázat dynamické vlákna. Implementace není potřeba poskytovat schopnost dynamicky upravit počet vláken, ale musí se poskytuje rozhraní pro podporu přenositelnost na všech platformách.

#### <a name="cross-references"></a>Křížové odkazy

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic – funkce

`omp_get_dynamic` Funkce vrací nenulovou hodnotu, pokud je povolené dynamické přizpůsobení vlákna a v opačném případě vrátí 0. Formát je následujícím způsobem:

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Implementace neimplementuje dynamické úpravy počtu vláken, tato funkce vždy vrátí hodnotu 0.

#### <a name="cross-references"></a>Křížové odkazy

- Popis nastavení dynamické vlákno, naleznete v tématu [omp_set_dynamic –](#317-omp_set_dynamic-function).

### <a name="319-ompsetnested-function"></a>3.1.9 omp_set_nested – funkce

`omp_set_nested` Funkce povolí nebo zakáže vnořené paralelismu. Formát je následujícím způsobem:

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Pokud *vnořené* vyhodnocen na hodnotu 0, vnořené paralelismu zakázána, což je výchozí a vnořené paralelních oblastí jsou serializovat a spuštění aktuálního vlákna. V opačném případě je povoleno vnořené paralelismu a paralelních oblastí, které jsou vnořené můžou nasadit další vlákna do formulářů vnořeného týmy.

Tato funkce má důsledky je popsáno výše, při volání z část programu, kde `omp_in_parallel` vrátí funkce hodnotu nula. Pokud je volána z část programu, kde `omp_in_parallel` funkce vrátí nenulovou hodnotu, nedefinované chování této funkce.

Toto volání má vyšší prioritu než `OMP_NESTED` proměnné prostředí.

Pokud je povoleno vnořené paralelismu, počet podprocesů používaný k provedení vnořených paralelních oblastí je definované implementací. V důsledku toho jsou povoleny OpenMP vyhovující implementace k serializaci vnořených paralelních oblastí, i když je povolena vnořené paralelismu.

#### <a name="cross-references"></a>Křížové odkazy

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested – funkce

`omp_get_nested` Funkce vrátí nenulovou hodnotu, pokud je povolené vnořené paralelismu a 0, pokud je zakázaná. Další informace o vnořených paralelismu, naleznete v tématu [omp_set_nested –](#319-omp_set_nested-function). Formát je následujícím způsobem:

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Implementace neimplementuje vnořené paralelismu, tato funkce vždy vrátí hodnotu 0.

## <a name="32-lock-functions"></a>3.2 funkce zamykání

Funkce popsané v této části manipulovat s zámky používán k synchronizaci.

Pro následující funkce, proměnná zámku musí být typu `omp_lock_t`. Tato proměnná musí být přístupný pouze prostřednictvím těchto funkcí. Všechny funkce zamykání vyžaduje argument, který se má ukazatel na `omp_lock_t` typu.

- [Omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) funkce inicializuje jednoduchým zámkem.
- [Omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) funkce odstraní jednoduchým zámkem.
- [Omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) funkce počká, dokud jednoduchým zámkem je k dispozici.
- [Omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) funkce uvolní jednoduchým zámkem.
- [Omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) otestuje jednoduchým zámkem.

Pro následující funkce, proměnná zámku musí být typu `omp_nest_lock_t`.  Tato proměnná musí být přístupný pouze prostřednictvím těchto funkcí. Všechny funkce, vnořitelných zámku musí argument, který se má ukazatel na `omp_nest_lock_t` typu.

- [Omp_init_nest_lock –](#321-omp_init_lock-and-omp_init_nest_lock-functions) funkce inicializuje, vnořitelných zámek.
- [Omp_destroy_nest_lock –](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) funkce odstraní, vnořitelných zámek.
- [Omp_set_nest_lock –](#323-omp_set_lock-and-omp_set_nest_lock-functions) funkce počká, dokud, vnořitelných zámek je k dispozici.
- [Omp_unset_nest_lock –](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) funkce uvolní, vnořitelných zámek.
- [Omp_test_nest_lock –](#325-omp_test_lock-and-omp_test_nest_lock-functions) funkce testuje, vnořitelných zámek.

Funkce jazyka OpenMP zámek přístup k proměnné zámek takovým způsobem, jsou vždy číst a aktualizovat aktuální hodnotu proměnné zámku. Proto není nutné pro aplikaci OpenMP zahrnout explicitní `flush` direktivy, abyste měli jistotu, že hodnota proměnné zámek je konzistentní mezi vlákny. (Může být potřeba `flush` direktivy, aby byly hodnoty jiné proměnné konzistentní.)

### <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock a omp_init_nest_lock – funkce

Tyto funkce jsou pouze prostředkem inicializaci zámek. Každá funkce inicializuje zámek spojené s parametrem *Zámek* pro použití v budoucích volání. Formát je následujícím způsobem:

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Počáteční stav se odemkne (to znamená, že žádné vlákno vlastníkem zámku). Pro zámek, vnořitelných počáteční počet vnoření je nula. Jde volat některý z těchto rutin s proměnnou zámek, který už je inicializovaný nedodržující předpisy.

### <a name="322-ompdestroylock-and-ompdestroynestlock-functions"></a>3.2.2 omp_destroy_lock a omp_destroy_nest_lock – funkce

Tyto funkce Ujistěte se, že odkázáno zamknout proměnné *Zámek* není inicializován. Formát je následujícím způsobem:

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

Je kompatibilní volat některý z těchto rutin s proměnnou zámku, která má neinicializované nebo odemknout.

### <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 omp_set_lock a omp_set_nest_lock – funkce

Každá z těchto funkcí blokuje vlákno provádění funkce, dokud se zadaný zámek je k dispozici a pak nastaví zámek. Jednoduchým zámkem je k dispozici, pokud je odemknuté. Vnořitelných zámek je k dispozici, pokud je odemčený, nebo pokud je již vlastněn vlákno provádění funkce. Formát je následujícím způsobem:

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Pro jednoduchým zámkem, že argument `omp_set_lock` funkce musí ukazovat na proměnnou inicializované zámku. Vlákna, které spouští funkci uděleno vlastnictví zámku.

Pro zámkem, že argument `omp_set_nest_lock` funkce musí ukazovat na proměnnou inicializované zámku. Je zvýšen počet vnoření a vlákna je udělen nebo udržuje vlastnictví zámku.

### <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 omp_unset_lock a omp_unset_nest_lock – funkce

Tyto funkce prostředkem uvolnění vlastnictví zámku. Formát je následujícím způsobem:

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

Argument pro každý z těchto funkcí musí ukazovat na proměnnou inicializované zámek vlastněný vláknem provádění funkce. Pokud vlákno nevlastní zámek. tohoto, není chování definováno.

Pro jednoduché Zámek `omp_unset_lock` funkce uvolní vlákno provádění funkce z vlastnictví zámku.

Pro zámek, vnořitelných `omp_unset_nest_lock` funkce sníží počet vnoření a verzí vlákno provádění funkce z vlastnictví zámku, pokud výsledný počet je nula.

### <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock a omp_test_nest_lock – funkce

Tyto funkce pokus o nastavení zámku ale nedošlo k blokování provádění vlákna. Formát je následujícím způsobem:

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

Argument musí ukazovat na proměnnou inicializované zámku. Tyto funkce se pokusí nastavit zámek stejným způsobem jako `omp_set_lock` a `omp_set_nest_lock`, s tím rozdílem, že nedošlo k blokování provádění vlákna.

Pro jednoduché Zámek `omp_test_lock` funkce vrací nenulovou hodnotu, pokud je úspěšně nastavené uzamčení; v opačném případě vrátí 0.

Pro zámek, vnořitelných `omp_test_nest_lock` funkce vrací nový počet vnoření, pokud je úspěšně nastavené uzamčení; v opačném případě vrátí 0.

## <a name="33-timing-routines"></a>3.3 rutiny časování

Funkce popsané v této části podporují přenosné plánovače časovače:

- [Omp_get_wtime](#331-omp_get_wtime-function) funkce vrátí skutečný uplynulý čas.
- [Omp_get_wtick –](#332-omp_get_wtick-function) funkce vrátí sekund mezi po sobě jdoucích taktů.

### <a name="331-ompgetwtime-function"></a>3.3.1 omp_get_wtime – funkce

`omp_get_wtime` Funkce vrátí dvojité přesnosti s plovoucí desetinnou čárkou hodnota bodu rovnou skutečný uplynulý čas v sekundách, protože některé "čas v minulosti".  Skutečný "čas v minulosti" je volitelný, ale má zaručeno nebudou je moci měnit během provádění programu aplikace. Formát je následujícím způsobem:

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

Předpokládá se, že funkce se použije k měření uplynulého času, jak je znázorněno v následujícím příkladu:

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Vrátí časy jsou "vlákno times" ve kterém je určený, že nemusí být globálně konzistentní v rámci všech vláken součástí aplikace.

### <a name="332-ompgetwtick-function"></a>3.3.2 omp_get_wtick – funkce

`omp_get_wtick` Funkce vrátí hodnotu dvojité přesnosti s plovoucí desetinnou čárkou bodu rovna počtu sekund mezi po sobě jdoucích taktů. Formát je následujícím způsobem:

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
