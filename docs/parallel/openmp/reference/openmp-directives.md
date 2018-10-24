---
title: Direktivy jazyka OpenMP | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OpenMP directives
- atomic
- barrier
- critical
- flush
- for
- master
- ordered
- parallel
- section
- SECTIONS
- single
- threadprivate
dev_langs:
- C++
helpviewer_keywords:
- OpenMP directives
- atomic OpenMP directive
- barrier OpenMP directive
- critical OpenMP directive
- flush OpenMP directive
- for OpenMP directive
- master OpenMP directive
- ordered OpenMP directive
- parallel OpenMP directive
- sections OpenMP directive
- single OpenMP directive
- threadprivate OpenMP directive
ms.assetid: 0562c263-344c-466d-843e-de830d918940
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d92d196cc38e6033c6f16332e4977f2481c4496
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990331"
---
# <a name="openmp-directives"></a>Direktivy jazyka OpenMP

Obsahuje odkazy na direktivy použité v rozhraní API OpenMP.

Jazyk Visual C++ podporuje následující direktivy OpenMP:

– Direktiva                             | Popis
------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[atomic](#atomic)                     | Určuje, že umístění v paměti, která bude aktualizována atomicky.
[barrier](#barrier)                   | Synchronizuje všechna vlákna v týmu; všechna vlákna pozastaví při bariéry, dokud všechna vlákna provést odbourejte překážky bránící.
[critical](#critical)                 | Určuje, že kód je pouze spustit v jednom vlákně najednou.
[Vyprázdnění](#flush-openmp)                | Určuje, že všechna vlákna stejným zobrazení paměti pro všechny sdílené objekty.
[for](#for-openmp)                    | Způsobí, že práci `for` smyčky uvnitř paralelní oblasti rozdělit mezi vlákny.
[master](#master)                     | Určuje, že by se měl spustit pouze hlavní vlákno části programu.
[Řazení](#ordered-openmp-directives) | Určuje, že kód v části paralelizované `for` smyčky by měl být spuštěn jako sekvenční smyčka.
[parallel](#parallel)                 | Definuje paralelní oblasti, což je kód, který spustí paralelně několik vláken.
[Oddíly](#sections-openmp)          | Identifikuje části kódu k rozdělení mezi všemi vlákny.
[single](#single)                     | Umožňuje určit, že část kódu by měl být provedeny v jednom vlákně, ne tedy nutně hlavní vlákno.
[threadprivate](#threadprivate)       | Určuje, že proměnná je privátní pro vlákno.

## <a name="atomic"></a>Atomic

Určuje, že umístění v paměti, která bude aktualizována atomicky.

```
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Parametry

*Výraz*<br/>
Příkaz, který obsahuje hodnoty lvalue, jehož umístění paměti, které chcete chránit proti více než jeden zápis. Další informace o platný výraz formuláře naleznete v tématu Specifikace OpenMP.

### <a name="remarks"></a>Poznámky

`atomic` Podporuje bez klauzule OpenMP – direktiva.

Další informace najdete v tématu [vytvořit 2.6.4 atomic](../../../parallel/openmp/2-6-4-atomic-construct.md).

### <a name="example"></a>Příklad

```
// omp_atomic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define MAX 10

int main() {
   int count = 0;
   #pragma omp parallel num_threads(MAX)
   {
      #pragma omp atomic
      count++;
   }
   printf_s("Number of threads: %d\n", count);
}
```

```Output
Number of threads: 10
```

## <a name="barrier"></a>Barrier

Synchronizuje všechna vlákna v týmu; všechna vlákna pozastaví při bariéry, dokud všechna vlákna provést odbourejte překážky bránící.

```
#pragma omp barrier
```

### <a name="remarks"></a>Poznámky

`barrier` Podporuje bez klauzule OpenMP – direktiva.

Další informace najdete v tématu [2.6.3 barrier – direktiva](../../../parallel/openmp/2-6-3-barrier-directive.md).

### <a name="example"></a>Příklad

Pro ukázku toho, jak používat `barrier`, naleznete v tématu [hlavní](#master).

## <a name="critical"></a>Kritická

Určuje, že kód provádí pouze v jednom vlákně najednou.

```
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Jméno*<br/>
(Volitelné) Název pro identifikaci kritický kód. Poznámka: Tento název musí být uzavřen v závorkách.

### <a name="remarks"></a>Poznámky

`critical` Podporuje bez klauzule OpenMP – direktiva.

Další informace najdete v tématu [2.6.2 důležité vytvořit](../../../parallel/openmp/2-6-2-critical-construct.md).

### <a name="example"></a>Příklad

```
// omp_critical.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>

#define SIZE 10

int main()
{
    int i;
    int max;
    int a[SIZE];

    for (i = 0; i < SIZE; i++)
    {
        a[i] = rand();
        printf_s("%d\n", a[i]);
    }

    max = a[0];
    #pragma omp parallel for num_threads(4)
        for (i = 1; i < SIZE; i++)
        {
            if (a[i] > max)
            {
                #pragma omp critical
                {
                    // compare a[i] and max again because max
                    // could have been changed by another thread after
                    // the comparison outside the critical section
                    if (a[i] > max)
                        max = a[i];
                }
            }
        }

    printf_s("max = %d\n", max);
}
```

```Output
41
18467
6334
26500
19169
15724
11478
29358
26962
24464
max = 29358
```

## <a name="flush-openmp"></a>Flush (OpenMP)

Určuje, že všechna vlákna stejným zobrazení paměti pro všechny sdílené objekty.

```
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Parametry

*var*<br/>
(Volitelné) Čárkou oddělený seznam proměnných, které představují objekty, které chcete synchronizovat. Pokud `var` není zadán, vyprázdní všechny paměti.

### <a name="remarks"></a>Poznámky

`flush` Podporuje bez klauzule OpenMP – direktiva.

Další informace najdete v tématu [2.6.5 flush – direktiva](../../../parallel/openmp/2-6-5-flush-directive.md).

### <a name="example"></a>Příklad

```
// omp_flush.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void read(int *data) {
   printf_s("read data\n");
   *data = 1;
}

void process(int *data) {
   printf_s("process data\n");
   (*data)++;
}

int main() {
   int data;
   int flag;

   flag = 0;

   #pragma omp parallel sections num_threads(2)
   {
      #pragma omp section
      {
         printf_s("Thread %d: ", omp_get_thread_num( ));
         read(&data);
         #pragma omp flush(data)
         flag = 1;
         #pragma omp flush(flag)
         // Do more work.
      }

      #pragma omp section
      {
         while (!flag) {
            #pragma omp flush(flag)
         }
         #pragma omp flush(data)

         printf_s("Thread %d: ", omp_get_thread_num( ));
         process(&data);
         printf_s("data = %d\n", data);
      }
   }
}
```

```Output
Thread 0: read data
Thread 1: process data
data = 2
```

## <a name="for-openmp"></a>pro (OpenMP)

Způsobí, že práci `for` smyčky uvnitř paralelní oblasti rozdělit mezi vlákny.

```
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Volitelné) Nula nebo více klauzulí. Naleznete v části poznámky pro seznam klauzule podporované službou `for`.

*for_statement*<br/>
A `for` smyčky. Způsobí nedefinované chování, pokud uživatel kód v `for` změní indexovaná proměnná smyčky.

### <a name="remarks"></a>Poznámky

`for` Podporuje následující klauzule OpenMP – direktiva:

- [firstprivate](../../../parallel/openmp/reference/firstprivate.md)
- [lastprivate](../../../parallel/openmp/reference/lastprivate.md)
- [nowait](../../../parallel/openmp/reference/nowait.md)
- [Řazení](../../../parallel/openmp/reference/ordered-openmp-directives.md)
- [private](../../../parallel/openmp/reference/private-openmp.md)
- [reduction](../../../parallel/openmp/reference/reduction.md)
- [schedule](../../../parallel/openmp/reference/schedule.md)

Pokud `parallel` je také zadána, `clauses` může být jakékoli klauzule přijal `parallel` nebo `for` direktivy, s výjimkou `nowait`.

Další informace najdete v tématu [2.4.1 for – konstrukce](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Příklad

```
// omp_for.cpp
// compile with: /openmp
#include <stdio.h>
#include <math.h>
#include <omp.h>

#define NUM_THREADS 4
#define NUM_START 1
#define NUM_END 10

int main() {
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;
   int nThreads = 0, nTmp = nStart + nEnd;
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *
                               unsigned(abs(nTmp))) / 2;
   int nSumCalc = uTmp;

   if (nTmp < 0)
      nSumCalc = -nSumCalc;

   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)
   {
      #pragma omp master
      nThreads = omp_get_num_threads();

      #pragma omp for
      for (i=nStart; i<=nEnd; ++i) {
            #pragma omp atomic
            nSum += i;
      }
   }

   if  (nThreads == NUM_THREADS) {
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);
      nRet = 0;
   }
   else {
      printf_s("Expected %d OpenMP threads, but %d were used.\n",
               NUM_THREADS, nThreads);
      nRet = 1;
   }

   if (nSum != nSumCalc) {
      printf_s("The sum of %d through %d should be %d, "
               "but %d was reported!\n",
               NUM_START, NUM_END, nSumCalc, nSum);
      nRet = 1;
   }
   else
      printf_s("The sum of %d through %d is %d\n",
               NUM_START, NUM_END, nSum);
}
```

```Output
4 OpenMP threads were used.
The sum of 1 through 10 is 55
```

## <a name="master"></a>Hlavní

Určuje, že by se měl spustit pouze hlavní vlákno části programu.

```
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Poznámky

`master` Podporuje bez klauzule OpenMP – direktiva.

[Jeden](#single) umožňuje určit, že část kódu by měl být provedeny v jednom vlákně, ne tedy nutně hlavní vlákno.

Další informace najdete v tématu [2.6.1 master konstrukce](../../../parallel/openmp/2-6-1-master-construct.md).

### <a name="example"></a>Příklad

```
// omp_master.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>

int main( )
{
    int a[5], i;

    #pragma omp parallel
    {
        // Perform some computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] = i * i;

        // Print intermediate results.
        #pragma omp master
            for (i = 0; i < 5; i++)
                printf_s("a[%d] = %d\n", i, a[i]);

        // Wait.
        #pragma omp barrier

        // Continue with the computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] += i;
    }
}
```

```Output
a[0] = 0
a[1] = 1
a[2] = 4
a[3] = 9
a[4] = 16
```

## <a name="ordered-openmp-directives"></a>ordered (direktivy OpenMP)

Určuje, že kód v části paralelizované `for` smyčky by měl být spuštěn jako sekvenční smyčka.

```
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Poznámky

`ordered` Direktiva musí být v rámci dynamický rozsah [pro](#for-openmp) nebo `parallel for` vytvořit pomocí `ordered` klauzuli.

`ordered` Podporuje bez klauzule OpenMP – direktiva.

Další informace najdete v tématu [2.6.6 ordered – konstrukce](../../../parallel/openmp/2-6-6-ordered-construct.md).

### <a name="example"></a>Příklad

```
// omp_ordered.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

static float a[1000], b[1000], c[1000];

void test(int first, int last)
{
    #pragma omp for schedule(static) ordered
    for (int i = first; i <= last; ++i) {
        // Do something here.
        if (i % 2)
        {
            #pragma omp ordered
            printf_s("test() iteration %d\n", i);
        }
    }
}

void test2(int iter)
{
    #pragma omp ordered
    printf_s("test2() iteration %d\n", iter);
}

int main( )
{
    int i;
    #pragma omp parallel
    {
        test(1, 8);
        #pragma omp for ordered
        for (i = 0 ; i < 5 ; i++)
            test2(i);
    }
}
```

```Output
test() iteration 1
test() iteration 3
test() iteration 5
test() iteration 7
test2() iteration 0
test2() iteration 1
test2() iteration 2
test2() iteration 3
test2() iteration 4
```

## <a name="parallel"></a>paralelní

Definuje paralelní oblasti, což je kód, který spustí paralelně několik vláken.

```
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Volitelné) Nula nebo více klauzulí.  Naleznete v části poznámky pro seznam klauzule podporované službou `parallel`.

### <a name="remarks"></a>Poznámky

`parallel` Podporuje následující klauzule OpenMP – direktiva:

- [copyin](../../../parallel/openmp/reference/copyin.md)
- [default](../../../parallel/openmp/reference/default-openmp.md)
- [firstprivate](../../../parallel/openmp/reference/firstprivate.md)
- [if](../../../parallel/openmp/reference/if-openmp.md)
- [num_threads](../../../parallel/openmp/reference/num-threads.md)
- [private](../../../parallel/openmp/reference/private-openmp.md)
- [reduction](../../../parallel/openmp/reference/reduction.md)
- [Sdílet](../../../parallel/openmp/reference/shared-openmp.md)

`parallel` Můžete také použít s [oddíly](#sections-openmp) a [pro](#for-openmp) direktivy.

Další informace najdete v tématu [2.3 parallel – konstrukce](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak nastavit počet vláken a definovat paralelní oblasti. Počet vláken je ve výchozím nastavení rovna počtu logických procesorů v počítači. Například pokud máte počítače s jednoho fyzického procesoru, s povoleným hyperthreadingem, bude mít dva logické procesory a dvěma vlákny.

```
// omp_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(4)
   {
      int i = omp_get_thread_num();
      printf_s("Hello from thread %d\n", i);
   }
}
```

```Output
Hello from thread 0
Hello from thread 1
Hello from thread 2
Hello from thread 3
```

### <a name="comment"></a>Komentář

Všimněte si, že pořadí výstup se může lišit na různých strojích.

## <a name="sections-openmp"></a>oddíly (OpenMP)

Identifikuje části kódu k rozdělení mezi všemi vlákny.

```
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   } 
}
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Volitelné) Nula nebo více klauzulí. Naleznete v části poznámky pro seznam klauzule podporované službou `sections`.

### <a name="remarks"></a>Poznámky

`sections` Směrnice může obsahovat nula nebo více `section` direktivy.

`sections` Podporuje následující klauzule OpenMP – direktiva:

- [firstprivate](../../../parallel/openmp/reference/firstprivate.md)
- [lastprivate](../../../parallel/openmp/reference/lastprivate.md)
- [nowait](../../../parallel/openmp/reference/nowait.md)
- [private](../../../parallel/openmp/reference/private-openmp.md)
- [reduction](../../../parallel/openmp/reference/reduction.md)

Pokud `parallel` je také zadána, `clauses` může být jakékoli klauzule přijal `parallel` nebo `sections` direktivy, s výjimkou `nowait`.

Další informace najdete v tématu [2.4.2 sections – konstrukce](../../../parallel/openmp/2-4-2-sections-construct.md).

### <a name="example"></a>Příklad

```
// omp_sections.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
    #pragma omp parallel sections num_threads(4)
    {
        printf_s("Hello from thread %d\n", omp_get_thread_num());
        #pragma omp section
        printf_s("Hello from thread %d\n", omp_get_thread_num());
    }
}
```

```Output
Hello from thread 0
Hello from thread 0
```

## <a name="single"></a>Jeden

Umožňuje určit, že část kódu by měl být provedeny v jednom vlákně, ne tedy nutně hlavní vlákno.

```
#pragma omp single [clauses] 
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Volitelné) Nula nebo více klauzulí. Naleznete v části poznámky pro seznam klauzule podporované službou `single`.

### <a name="remarks"></a>Poznámky

`single` Podporuje následující klauzule OpenMP – direktiva:

- [copyprivate](../../../parallel/openmp/reference/copyprivate.md)
- [firstprivate](../../../parallel/openmp/reference/firstprivate.md)
- [nowait](../../../parallel/openmp/reference/nowait.md)
- [private](../../../parallel/openmp/reference/private-openmp.md)

[Hlavní](#master) umožňuje určit, že část kódu by měl provést pouze v hlavní vlákno.

Další informace najdete v tématu [2.4.3 jeden vytvořit](../../../parallel/openmp/2-4-3-single-construct.md).

### <a name="example"></a>Příklad

```cpp
// omp_single.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(2)
   {
      #pragma omp single
      // Only a single thread can read the input.
      printf_s("read input\n");

      // Multiple threads in the team compute the results.
      printf_s("compute results\n");

      #pragma omp single
      // Only a single thread can write the output.
      printf_s("write output\n");
    }
}
```

```Output
read input
compute results
compute results
write output
```

## <a name="threadprivate"></a>threadprivate

Určuje, že proměnná je privátní pro vlákno.

```
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Čárkou oddělený seznam proměnných, které chcete označit jako soukromé ve vlákně. `var` musí být globální nebo obor názvů rozsahem proměnné nebo statické místní proměnné.

### <a name="remarks"></a>Poznámky

`threadprivate` Podporuje bez klauzule OpenMP – direktiva.

Další informace najdete v tématu [2.7.1 threadprivate – direktiva](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

`threadprivate` Podle směrnice [vlákno](../../../cpp/thread.md) atribut, pomocí [__declspec](../../../cpp/declspec.md) – klíčové slovo; omezení `__declspec(thread)` platí pro `threadprivate`.

Nemůžete použít `threadprivate` v žádné knihovny DLL, která se načtou prostřednictvím [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya).  Tento zákaz zahrnuje knihovny DLL, které načítají s [/delayload (Import odloženého načtení)](../../../build/reference/delayload-delay-load-import.md), který také používá `LoadLibrary`.

Můžete použít `threadprivate` v knihovně DLL, která je staticky načtená při spouštění procesu.

Protože `threadprivate` vychází `__declspec(thread)`, `threadprivate` proměnné budou existovat v jakékoli vlákno spuštění v procesu, nejen vlákna, které jsou součástí týmu vlákna vytvořený službou paralelní oblasti.  Mějte na paměti tato implementace podrobností Můžete si všimnout, například, že konstruktory pro `threadprivate` uživatelem definovaný typ, se nazývají další často, než očekáváte.

A `threadprivate` proměnnou typu destructable nemusí mít jeho destruktor volá.  Příklad:

```
struct MyType
{
    ~MyType();
};

MyType threaded_var;
#pragma omp threadprivate(threaded_var)
int main()
{
    #pragma omp parallel
    {}
}
```

Uživatelé nemají žádnou kontrolu, když se ukončí vlákna tvořící paralelní oblasti.  Pokud tato vlákna při ukončení procesu, vlákna nebudete nijak upozorněni o ukončení procesu a destruktor se nebude volat pro `threaded_var` v libovolném vlákně kromě toho, který ukončí (tady, primární vlákno).  Takže kód by neměl spolehnout na řádné zničení `threadprivate` proměnné.

### <a name="example"></a>Příklad

Pro ukázkový používání `threadprivate`, naleznete v tématu [privátní](../../../parallel/openmp/reference/private-openmp.md).
