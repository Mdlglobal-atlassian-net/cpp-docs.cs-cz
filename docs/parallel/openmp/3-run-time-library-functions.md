---
title: 3. Funkce knihovny prostředí Runtime
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 6155eb87bd7a1a0533caf99afb3db8417854df30
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882852"
---
# <a name="3-run-time-library-functions"></a>3. funkce běhové knihovny

Tato část popisuje funkce OpenMP C a C++ Run-Time Library. Hlavička **\<OMP. h >** deklaruje dva typy, několik funkcí, které lze použít k řízení a dotazování prostředí paralelního spuštění a funkce zámku, které lze použít k synchronizaci přístupu k datům.

Typ `omp_lock_t` je typ objektu schopný reprezentovat, že je k dispozici zámek, nebo že vlákno vlastní zámek. Tyto zámky se označují jako *jednoduché zámky*.

Typ `omp_nest_lock_t` je typ objektu schopný reprezentovat buď zámek, nebo identitu vlákna, které vlastní zámek, a *počet vnoření* (popsaných níže). Tyto zámky se označují jako *vnořené zámky*.

Funkce knihovny jsou externí funkce s propojením "C".

Popisy v této kapitole jsou rozdělené do následujících témat:

- [Funkce prostředí pro spuštění](#31-execution-environment-functions)
- [Funkce Lock](#32-lock-functions)
- [Rutiny časování](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>funkce prostředí pro spouštění 3,1

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

### <a name="311-omp_set_num_threads-function"></a>3.1.1 – funkce omp_set_num_threads

Funkce `omp_set_num_threads` nastaví výchozí počet vláken, která se mají použít pro pozdější paralelní oblasti, které neurčují klauzuli `num_threads`. Formát je následující:

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

Hodnota parametru *num_threads* musí být kladné celé číslo. Jeho efekt závisí na tom, zda je dynamická úprava počtu vláken povolena. Komplexní sadu pravidel o interakci mezi funkcí `omp_set_num_threads` a dynamickou úpravou vláken naleznete v [části 2,3](2-directives.md#23-parallel-construct).

Tato funkce má důsledky popsané výše při volání z části programu, kde funkce `omp_in_parallel` vrátí hodnotu nula. Pokud je volána z části programu, kde funkce `omp_in_parallel` vrátí nenulovou hodnotu, chování této funkce není definováno.

Toto volání má přednost před proměnnou prostředí `OMP_NUM_THREADS`. Výchozí hodnota pro počet vláken, která mohou být vytvořena voláním `omp_set_num_threads` nebo nastavením proměnné prostředí `OMP_NUM_THREADS` lze explicitně přepsat jednou `parallel` direktivou zadáním klauzule `num_threads`.

Další informace najdete v tématu [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Křížové odkazy

- [omp_set_dynamic](#317-omp_set_dynamic-function) funkce
- [omp_get_dynamic](#318-omp_get_dynamic-function) funkce
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) proměnná prostředí
- klauzule [num_threads](2-directives.md#23-parallel-construct)

### <a name="312-omp_get_num_threads-function"></a>3.1.2 omp_get_num_threads – funkce

Funkce `omp_get_num_threads` vrací počet vláken, která jsou aktuálně v týmu, spouštějící paralelní oblast, ze které se volá. Formát je následující:

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

Klauzule `num_threads`, funkce `omp_set_num_threads` a proměnná prostředí `OMP_NUM_THREADS` řídí počet vláken v týmu.

Pokud byl počet vláken explicitně nastaven uživatelem, je výchozí hodnota definována implementací. Tato funkce se váže k nejbližší nadřazené direktivě `parallel`. Pokud je volána z sériové části programu nebo z vnořené paralelní oblasti, která je serializována, tato funkce vrátí hodnotu 1.

Další informace najdete v tématu [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Křížové odkazy

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a>3.1.3 omp_get_max_threads funkce

Funkce `omp_get_max_threads` vrací celé číslo, které je zaručené aspoň tak velké jako počet vláken, která by se použila k vytvoření týmu, pokud by se v tomto okamžiku v kódu zobrazila paralelní oblast bez klauzule `num_threads`. Formát je následující:

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

Následující vyjadřuje dolní mez hodnoty `omp_get_max_threads`:

> *vlákna-použití-for-Next-team* <= `omp_get_max_threads`

Všimněte si, že pokud jiná paralelní oblast používá klauzuli `num_threads` pro vyžádání konkrétního počtu vláken, záruka dolní meze výsledku `omp_get_max_threads` již nedrží.

Návratovou hodnotu funkce `omp_get_max_threads` lze použít k dynamickému přidělení dostatečného úložiště pro všechna vlákna v týmu vytvořená v další paralelní oblasti.

#### <a name="cross-references"></a>Křížové odkazy

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a>3.1.4 omp_get_thread_num – funkce

Funkce `omp_get_thread_num` vrací číslo vlákna v rámci svého týmu vlákna, které provádí funkci. Číslo vlákna leží mezi 0 a `omp_get_num_threads()`-1 včetně. Hlavní vlákno týmu je vlákno 0.

Formát je následující:

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

Pokud je volána ze sériové oblasti, `omp_get_thread_num` vrátí hodnotu 0. Pokud je volána v rámci vnořené paralelní oblasti, která je serializována, tato funkce vrátí 0.

#### <a name="cross-references"></a>Křížové odkazy

- [omp_get_num_threads](#312-omp_get_num_threads-function) funkce

### <a name="315-omp_get_num_procs-function"></a>3.1.5 omp_get_num_procs – funkce

Funkce `omp_get_num_procs` vrátí počet procesorů, které jsou k dispozici pro program v době volání funkce. Formát je následující:

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a>3.1.6 omp_in_parallel – funkce

Funkce `omp_in_parallel` vrací nenulovou hodnotu, pokud je volána v dynamickém rozsahu paralelního provádění paralelních oblastí; v opačném případě vrátí 0. Formát je následující:

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Tato funkce vrací nenulovou hodnotu při volání z oblasti prováděné paralelně, včetně vnořených oblastí, které jsou serializovány.

### <a name="317-omp_set_dynamic-function"></a>3.1.7 omp_set_dynamic – funkce

Funkce `omp_set_dynamic` povoluje nebo zakazuje dynamickou úpravu počtu vláken dostupných pro provádění paralelních oblastí. Formát je následující:

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Pokud je *dynamic_threads* vyhodnocena jako nenulová hodnota, počet vláken, která se používají pro spuštění nadcházejících paralelních oblastí, lze automaticky upravit prostředím za běhu, aby se co nejlépe používaly systémové prostředky. V důsledku toho je počet vláken určený uživatelem maximální počet vláken. Počet vláken v týmu, který spouští paralelní oblast, zůstane pevně daný po dobu trvání této paralelní oblasti a je hlášena funkcí `omp_get_num_threads`.

Pokud je *dynamic_threads* vyhodnocena jako 0, je dynamická úprava zakázána.

Tato funkce má důsledky popsané výše při volání z části programu, kde funkce `omp_in_parallel` vrátí hodnotu nula. Pokud je volána z části programu, kde funkce `omp_in_parallel` vrátí nenulovou hodnotu, chování této funkce není definováno.

Volání `omp_set_dynamic` má přednost před proměnnou prostředí `OMP_DYNAMIC`.

Výchozí hodnota pro dynamickou úpravu vláken je definovaná implementací. V důsledku toho by uživatelské kódy, které závisí na konkrétním počtu vláken pro správné provedení, měly explicitně zakázat dynamická vlákna. Implementace se nevyžadují, aby poskytovaly možnost dynamického přizpůsobení počtu vláken, ale jsou potřeba k tomu, aby poskytovaly rozhraní pro podporu přenositelnosti napříč všemi platformami.

#### <a name="microsoft-specific"></a>specifické pro společnost Microsoft

Aktuální podpora `omp_get_dynamic` a `omp_set_dynamic` je následující:

Vstupní parametr `omp_set_dynamic` nemá vliv na zásady vláken a nemění počet vláken. `omp_get_num_threads` vždy vrátí buď uživatelem definované číslo, pokud je nastaveno, nebo výchozí číslo vlákna. V současné implementaci společnosti Microsoft `omp_set_dynamic(0)` vypne dynamické zřetězení, aby se existující sada vláken mohla znovu použít pro následující paralelní oblast. `omp_set_dynamic(1)` zapne dynamické zřetězení tím, že zahodí stávající sadu vláken a vytvoří novou sadu pro nadcházející paralelní oblast. Počet vláken v nové sadě je stejný jako stará sada a je založen na vrácené hodnotě `omp_get_num_threads`. Proto pro nejlepší výkon použijte `omp_set_dynamic(0)` k opakovanému použití stávajících vláken.

#### <a name="cross-references"></a>Křížové odkazy

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a>3.1.8 omp_get_dynamic – funkce

Funkce `omp_get_dynamic` vrací nenulovou hodnotu, pokud je povolena dynamická úprava vláken a vrátí hodnotu 0 v opačném případě. Formát je následující:

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Pokud implementace neimplementuje dynamickou úpravu počtu vláken, tato funkce vždycky vrátí 0. Další informace najdete v tématu [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Křížové odkazy

- Popis dynamického nastavení vlákna naleznete v tématu [omp_set_dynamic](#317-omp_set_dynamic-function).

### <a name="319-omp_set_nested-function"></a>3.1.9 omp_set_nested – funkce

Funkce `omp_set_nested` povoluje nebo zakazuje vnořené paralelismuy. Formát je následující:

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Pokud je *vnořené* vyhodnoceno jako 0, vnořený paralelismus je zakázán, což je výchozí a vnořené paralelní oblasti jsou serializovány a spouštěny aktuálním vláknem. V opačném případě je povolen vnořený paralelismus a paralelní oblasti, které jsou vnořené, mohou nasazovat další vlákna pro vytvoření vnořených týmů.

Tato funkce má důsledky popsané výše při volání z části programu, kde funkce `omp_in_parallel` vrátí hodnotu nula. Pokud je volána z části programu, kde funkce `omp_in_parallel` vrátí nenulovou hodnotu, chování této funkce není definováno.

Toto volání má přednost před proměnnou prostředí `OMP_NESTED`.

Je-li povolen vnořený paralelismus, je počet vláken použitých k provedení vnořených paralelních oblastí definován implementací. V důsledku toho implementace vyhovující OpenMP můžou serializovat vnořené paralelní oblasti i v případě, že je povolený vnořený paralelismu.

#### <a name="cross-references"></a>Křížové odkazy

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a>3.1.10 omp_get_nested – funkce

Funkce `omp_get_nested` vrací nenulovou hodnotu, pokud je povolen vnořený paralelismus a 0, pokud je zakázán. Další informace o vnořených paralelismuách naleznete v tématu [omp_set_nested](#319-omp_set_nested-function). Formát je následující:

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Pokud implementace neimplementuje vnořené paralelismus, tato funkce vždycky vrátí 0.

## <a name="32-lock-functions"></a>3,2 funkce zámku

Funkce popsané v této části pracují s zámky použitými pro synchronizaci.

Pro následující funkce musí mít proměnná zámku typ `omp_lock_t`. Tato proměnná musí být dostupná jenom prostřednictvím těchto funkcí. Všechny funkce zámku vyžadují argument, který má ukazatel na `omp_lock_t` typ.

- Funkce [omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) inicializuje jednoduchý zámek.
- Funkce [omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) odebere jednoduchý zámek.
- Funkce [omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) počká, dokud nebude k dispozici jednoduchý zámek.
- Funkce [omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) uvolní jednoduchý zámek.
- Funkce [omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) testuje jednoduchý zámek.

Pro následující funkce musí mít proměnná zámku typ `omp_nest_lock_t`.  Tato proměnná musí být dostupná jenom prostřednictvím těchto funkcí. Všechny funkce s vnořenými zámky vyžadují argument, který má ukazatel na `omp_nest_lock_t` typ.

- Funkce [omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) inicializuje vnořený zámek.
- Funkce [omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) odebere vnořený zámek.
- Funkce [omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) počká, dokud nebude k dispozici vnořený zámek.
- Funkce [omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) uvolní vnořený zámek.
- Funkce [omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) testuje vnořený zámek.

Funkce zámku OpenMP přistupují k proměnné zámku takovým způsobem, že vždy čtou a aktualizují nejaktuálnější hodnotu proměnné zámku. Proto není nutné, aby program OpenMP zahrnoval explicitní direktivy `flush`, aby se zajistilo, že hodnota proměnné zámku je konzistentní mezi různými vlákny. (Aby se hodnoty jiných proměnných shodovaly, může být potřeba direktivy `flush`.)

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 omp_init_lock a omp_init_nest_lock funkce

Tyto funkce poskytují pouze způsob inicializace zámku. Každá funkce inicializuje zámek spojený s parametrem *Lock* pro použití v nadcházejících voláních. Formát je následující:

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Počáteční stav je odemčený (to znamená, že zámek nevlastní žádné vlákno). Pro vnořený zámek je počáteční počet vnoření nula. Je nekompatibilní se voláním některé z těchto rutin s proměnnou zámku, která již byla inicializována.

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>funkce 3.2.2 omp_destroy_lock a omp_destroy_nest_lock

Tyto funkce zajistí, že odkaz na *Zámek proměnné není* inicializovaný. Formát je následující:

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

Není nekompatibilní s voláním některé z těchto rutin s proměnnou zámku, která je neinicializovaná nebo odemčená.

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 omp_set_lock a omp_set_nest_lock funkce

Každá z těchto funkcí blokuje vlákno vykonávající funkci, dokud není k dispozici zadaný zámek, a poté nastaví zámek. Pokud je odemčený, je k dispozici jednoduchý zámek. Vnořený zámek je k dispozici, pokud je odemčený nebo je již vlastněn vláknem, který funkci provádí. Formát je následující:

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Pro jednoduchý zámek musí argument funkce `omp_set_lock` odkazovat na inicializovaná proměnnou zámku. Vlastnictví zámku je uděleno vláknu, které provádí funkci.

Pro vnořený zámek musí argument funkce `omp_set_nest_lock` ukazovat na inicializovaná proměnnou zámku. Počet vnoření je zvýšen a vlákno je uděleno, nebo zachovává vlastnictví zámku.

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>funkce 3.2.4 omp_unset_lock a omp_unset_nest_lock

Tyto funkce poskytují prostředky pro uvolnění vlastnictví zámku. Formát je následující:

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

Argument pro každou z těchto funkcí musí odkazovat na inicializovaná proměnnou zámku, která je majetkem vlákna vykonávajícího funkci. Chování není definováno, pokud vlákno nevlastní zámek.

Pro jednoduchý zámek funkce `omp_unset_lock` uvolní vlákno, které spouští funkci z vlastnictví zámku.

Pro vnořování zámku funkce `omp_unset_nest_lock` sníží počet vnoření a uvolní vlákno vykonávající funkci z vlastnictví zámku, pokud je výsledný počet nula.

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 omp_test_lock a omp_test_nest_lock funkce

Tyto funkce se pokoušejí nastavit zámek, ale neblokují provádění vlákna. Formát je následující:

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

Argument musí ukazovat na inicializovaná proměnnou zámku. Tyto funkce se pokoušejí nastavit zámek stejným způsobem jako `omp_set_lock` a `omp_set_nest_lock`, s tím rozdílem, že neblokují provádění vlákna.

Pro jednoduchý zámek vrátí funkce `omp_test_lock` nenulovou hodnotu, pokud je zámek úspěšně nastaven. v opačném případě vrátí hodnotu nula.

Pro vnořený zámek vrátí funkce `omp_test_nest_lock` nový počet vnoření, pokud je zámek úspěšně nastaven. v opačném případě vrátí hodnotu nula.

## <a name="33-timing-routines"></a>rutiny časování 3,3

Funkce popsané v této části podporují přenosnou hodinovou časovač:

- Funkce [omp_get_wtime](#331-omp_get_wtime-function) vrací uplynulý čas na zdi.
- Funkce [omp_get_wtick](#332-omp_get_wtick-function) vrací sekundy mezi po sobě jdoucí takty.

### <a name="331-omp_get_wtime-function"></a>3.3.1 – funkce omp_get_wtime

Funkce `omp_get_wtime` vrací hodnotu s plovoucí desetinnou čárkou s dvojitou přesností, která se rovná uplynulé hodinové době v sekundách od času v minulosti.  Skutečný "čas v minulosti" je libovolný, ale během provádění aplikačního programu je zaručeno, že se nemění. Formát je následující:

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

Očekává se, že funkce bude použita k měření uplynulých časů, jak je znázorněno v následujícím příkladu:

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Počet vrácených časů je "doba na vlákno", což znamená, že nemusí být globálně konzistentní napříč všemi vlákny zapojenými do aplikace.

### <a name="332-omp_get_wtick-function"></a>3.3.2 omp_get_wtick funkce

Funkce `omp_get_wtick` vrací hodnotu s plovoucí desetinnou čárkou s dvojitou přesností, která se rovná počtu sekund mezi po sobě jdoucích taktech. Formát je následující:

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
