---
title: Direktivy jazyka OpenMP
ms.date: 03/20/2019
f1_keywords:
- OpenMP directives
- atomic
- barrier
- critical
- flush
- for
- master
- parallel
- section
- single
- threadprivate
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
ms.openlocfilehash: 569419b3422b155afc6e9692efaecd4e5a06f188
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366446"
---
# <a name="openmp-directives"></a>Direktivy jazyka OpenMP

Obsahuje odkazy na direktivy používané v rozhraní OpenMP API.

Visual C++ podporuje následující direktivy OpenMP.

Pro paralelní sdílení práce:

|Směrnice|Popis|
|---------|-----------|
|[parallel](#parallel)|Definuje paralelní oblast, což je kód, který bude spuštěn více vlákny paralelně.|
|[pro](#for-openmp)|Způsobí, že práce `for` ve smyčce uvnitř paralelní oblasti, které mají být rozděleny mezi vlákna.|
|[Oddíly](#sections-openmp)|Identifikuje oddíly kódu, které mají být rozděleny mezi všechna vlákna.|
|[Jednoho](#single)|Umožňuje určit, že část kódu by měla být spuštěna v jednom vlákně, ne nutně v hlavním vlákně.|

Pro hlavní a synchronizační:

|Směrnice|Popis|
|---------|-----------|
|[master](#master)|Určuje, že pouze hlavní vlákno by mělo spustit část programu.|
|[Kritické](#critical)|Určuje, že kód je spouštěn pouze v jednom vlákně současně.|
|[Bariéra](#barrier)|Synchronizuje všechna vlákna v týmu; všechna vlákna se zastaví u bariéry, dokud všechna vlákna nespustí bariéru.|
|[atomic](#atomic)|Určuje, že umístění paměti, které bude aktualizovánatomicky.|
|[flush](#flush-openmp)|Určuje, že všechna vlákna mají stejné zobrazení paměti pro všechny sdílené objekty.|
|[Objednal](#ordered-openmp-directives)|Určuje, že kód v `for` rámci paralelizované smyčky by měl být proveden jako sekvenční smyčka.|

Pro datové prostředí:

|Směrnice|Popis|
|---------|-----------|
|[threadprivate](#threadprivate)|Určuje, že proměnná je soukromá pro vlákno.|

## <a name="atomic"></a><a name="atomic"></a>Atomové

Určuje, že umístění paměti, které bude aktualizovánatomicky.

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Parametry

*Výraz*<br/>
Příkaz, který má *lvalue*, jehož umístění paměti chcete chránit před více než jeden zápis.

### <a name="remarks"></a>Poznámky

Směrnice `atomic` nepodporuje žádné doložky.

Další informace naleznete v tématu [2.6.4 atomic construct](../../../parallel/openmp/2-6-4-atomic-construct.md).

### <a name="example"></a>Příklad

```cpp
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

## <a name="barrier"></a><a name="barrier"></a>Bariéra

Synchronizuje všechna vlákna v týmu; všechna vlákna se zastaví u bariéry, dokud všechna vlákna nespustí bariéru.

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>Poznámky

Směrnice `barrier` nepodporuje žádné doložky.

Další informace naleznete v směrnici [2.6.3 barrier .](../../../parallel/openmp/2-6-3-barrier-directive.md)

### <a name="example"></a>Příklad

Ukázka použití naleznete `barrier`v [části master](#master).

## <a name="critical"></a><a name="critical"></a>Kritické

Určuje, že kód je spouštěn pouze v jednom vlákně současně.

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Jméno*<br/>
(Nepovinné) Název k identifikaci kritického kódu. Název musí být uzavřen v závorce.

### <a name="remarks"></a>Poznámky

Směrnice `critical` nepodporuje žádné doložky.

Další informace naleznete v tématu [2.6.2 critical construct](../../../parallel/openmp/2-6-2-critical-construct.md).

### <a name="example"></a>Příklad

```cpp
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

## <a name="flush"></a><a name="flush-openmp"></a>Flush

Určuje, že všechna vlákna mají stejné zobrazení paměti pro všechny sdílené objekty.

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Parametry

*var*<br/>
(Nepovinné) Seznam proměnných oddělených čárkami, které představují objekty, které chcete synchronizovat. Pokud není zadán *var,* všechny paměti je vyprázdněna.

### <a name="remarks"></a>Poznámky

Směrnice `flush` nepodporuje žádné doložky.

Další informace naleznete v tématu [2.6.5 flush směrnice](../../../parallel/openmp/2-6-5-flush-directive.md).

### <a name="example"></a>Příklad

```cpp
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

## <a name="for"></a><a name="for-openmp"></a>Pro

Způsobí, že práce `for` ve smyčce uvnitř paralelní oblasti, které mají být rozděleny mezi vlákna.

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Nepovinné) Nula nebo více klauzulí naleznete v části **Poznámky.**

*for_statement*<br/>
Smyčka. `for` Nedefinované chování bude mít za `for` následek, pokud uživatelský kód ve smyčce změní proměnnou indexu.

### <a name="remarks"></a>Poznámky

Směrnice `for` podporuje následující ustanovení:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [Objednal](openmp-clauses.md#ordered-openmp-clauses)
- [Plán](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

Pokud `parallel` je také `clauses` zadán, může být `parallel` `for` jakékoli ustanovení `nowait`přijaté nebo směrnic, s výjimkou .

Další informace naleznete v tématu [2.4.1 pro konstrukci](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Příklad

```cpp
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

## <a name="master"></a><a name="master"></a>Hlavní

Určuje, že pouze hlavní vlákno by mělo spustit část programu.

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Poznámky

Směrnice `master` nepodporuje žádné doložky.

[Jedna](#single) směrnice umožňuje určit, že část kódu by měla být spuštěna v jednom vlákně, ne nutně hlavní vlákno.

Další informace naleznete v tématu [2.6.1 master construct](../../../parallel/openmp/2-6-1-master-construct.md).

### <a name="example"></a>Příklad

```cpp
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

## <a name="ordered"></a><a name="ordered-openmp-directives"></a>Objednal

Určuje, že kód v `for` rámci paralelizované smyčky by měl být proveden jako sekvenční smyčka.

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Poznámky

Směrnice `ordered` musí být v dynamickém [for](#for-openmp) rozsahu `parallel for` for `ordered` nebo konstrukce s klauzulí.

Směrnice `ordered` nepodporuje žádné doložky.

Další informace naleznete v tématu [2.6.6 objednané konstrukce](../../../parallel/openmp/2-6-6-ordered-construct.md).

### <a name="example"></a>Příklad

```cpp
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

## <a name="parallel"></a><a name="parallel"></a>Paralelní

Definuje paralelní oblast, což je kód, který bude spuštěn více vlákny paralelně.

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Nepovinné) Nula nebo více klauzulí naleznete v části **Poznámky.**

### <a name="remarks"></a>Poznámky

Směrnice `parallel` podporuje následující ustanovení:

- [if](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [Sdílené](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel`lze také použít se směrnicemi [for](#for-openmp) a [sections.](#sections-openmp)

Další informace naleznete v tématu [2.3 paralelní konstrukce](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Příklad

Následující ukázka ukazuje, jak nastavit počet podprocesů a definovat paralelní oblast. Počet podprocesů se ve výchozím nastavení rovná počtu logických procesorů v počítači. Například pokud máte počítač s jedním fyzickýprocesor, který má hyperthreading povolen, bude mít dva logické procesory a dvě vlákna. Pořadí výstupu se může lišit na různých strojích.

```cpp
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

## <a name="sections"></a><a name="sections-openmp"></a>Oddíly

Identifikuje oddíly kódu, které mají být rozděleny mezi všechna vlákna.

```cpp
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
(Nepovinné) Nula nebo více klauzulí naleznete v části **Poznámky.**

### <a name="remarks"></a>Poznámky

Směrnice `sections` může obsahovat `section` nula nebo více směrnic.

Směrnice `sections` podporuje následující ustanovení:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

Pokud `parallel` je také `clauses` zadán, může být `parallel` `sections` jakékoli ustanovení `nowait`přijaté nebo směrnic, s výjimkou .

Další informace naleznete v tématu [2.4.2 sekcí konstrukce](../../../parallel/openmp/2-4-2-sections-construct.md).

### <a name="example"></a>Příklad

```cpp
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

## <a name="single"></a><a name="single"></a>Jednoho

Umožňuje určit, že část kódu by měla být spuštěna v jednom vlákně, ne nutně v hlavním vlákně.

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Nepovinné) Nula nebo více klauzulí naleznete v části **Poznámky.**

### <a name="remarks"></a>Poznámky

Směrnice `single` podporuje následující ustanovení:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

[Hlavní](#master) směrnice umožňuje určit, že část kódu by měla být spuštěna pouze v hlavním vlákně.

Další informace naleznete v tématu [2.4.3 single construct](../../../parallel/openmp/2-4-3-single-construct.md).

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

## <a name="threadprivate"></a><a name="threadprivate"></a>threadprivate

Určuje, že proměnná je soukromá pro vlákno.

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Seznam proměnných oddělených čárkami, které chcete vytvořit jako soukromé pro vlákno. *var* musí být proměnná s rozsahem globálního nebo oboru názvů nebo místní statická proměnná.

### <a name="remarks"></a>Poznámky

Směrnice `threadprivate` nepodporuje žádné doložky.

Směrnice `threadprivate` je založena na atributu [podprocesu](../../../cpp/thread.md) pomocí klíčového slova [__declspec;](../../../cpp/declspec.md) omezení `__declspec(thread)` se `threadprivate`vztahují na . Například `threadprivate` proměnná bude existovat v libovolném vlákně spuštěném v procesu, nikoli pouze v těch vláknech, která jsou součástí týmu vláken zplozeného paralelní oblastí. Uvědomte si tento detail implementace; můžete si všimnout, že `threadprivate` konstruktory pro uživatelem definovaný typ jsou volány častěji než očekávané.

Můžete použít `threadprivate` v knihovně DLL, která je staticky načtena `threadprivate` při spuštění procesu, ale nelze použít v žádné knihovně DLL, která bude načtena `LoadLibrary`prostřednictvím [loadlibrary,](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) jako jsou knihovny DLL, které jsou načteny [s /DELAYLOAD (import zpoždění zatížení)](../../../build/reference/delayload-delay-load-import.md), který také používá .

Proměnná `threadprivate` *zničitelného* typu není zaručeno, že jeho destruktor volá. Příklad:

```cpp
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

Uživatelé nemají žádnou kontrolu nad tím, kdy budou ukončena vlákna tvořící paralelní oblast. Pokud tato vlákna existují při ukončení procesu, vlákna nebudou upozorněni na ukončení procesu a destruktor nebude volán v `threaded_var` žádném vlákně kromě toho, který ukončí (zde primární vlákno). Takže kód by neměl počítat `threadprivate` s řádným zničením proměnných.

Další informace naleznete v [tématu 2.7.1 threadprivate směrnice](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

### <a name="example"></a>Příklad

Ukázku použití `threadprivate`naleznete v [části Soukromé](openmp-clauses.md#private-openmp).
