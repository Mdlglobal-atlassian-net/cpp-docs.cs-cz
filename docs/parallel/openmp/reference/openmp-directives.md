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
ms.openlocfilehash: bfd2cec32acdd6431a571916f1c80e1700ef3af7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441782"
---
# <a name="openmp-directives"></a>Direktivy jazyka OpenMP

Obsahuje odkazy na direktivy používané v rozhraní OpenMP API.

Vizuál C++ podporuje následující direktivy OpenMP.

Pro paralelní práci – sdílení:

|– Direktiva|Popis|
|---------|-----------|
|[parallel](#parallel)|Definuje paralelní oblast, což je kód, který bude spuštěn paralelně více vlákny.|
|[for](#for-openmp)|Způsobí, že práce ve smyčce `for` uvnitř paralelní oblasti bude rozdělena mezi vlákna.|
|[řezů](#sections-openmp)|Identifikuje oddíly kódu, které mají být rozděleny mezi všechna vlákna.|
|[single](#single)|Umožňuje určit, že oddíl kódu by měl být spuštěn v jednom vlákně, nemusí nutně být hlavním vláknem.|

Pro hlavní a následující synchronizaci:

|– Direktiva|Popis|
|---------|-----------|
|[master](#master)|Určuje, že by měl být spuštěn pouze hlavní podproces programu.|
|[critical](#critical)|Určuje, že kód je spuštěn pouze v jednom vlákně.|
|[barrier](#barrier)|Synchronizuje všechna vlákna v týmu; všechna vlákna se pozastaví na bariérě, dokud všechna vlákna nespustí bariéru.|
|[atomic](#atomic)|Určuje, že umístění v paměti, které se bude aktualizovat atomicky.|
|[zaznamenány](#flush-openmp)|Určuje, že všechna vlákna mají stejné zobrazení paměti pro všechny sdílené objekty.|
|[objednávek](#ordered-openmp-directives)|Určuje, že kód pod paralelně `for` smyčkou by měl být proveden jako sekvenční smyčka.|

Pro datové prostředí:

|– Direktiva|Popis|
|---------|-----------|
|[threadprivate](#threadprivate)|Určuje, že proměnná je soukromá pro vlákno.|

## <a name="atomic"></a>Atomic

Určuje, že umístění v paměti, které se bude aktualizovat atomicky.

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Parametry

*vyjádření*<br/>
Příkaz, který má *lvalue*, jejichž umístění paměti chcete chránit před více než jedním zápisem.

### <a name="remarks"></a>Poznámky

Direktiva `atomic` nepodporuje žádné klauzule.

Další informace naleznete v tématu [2.6.4 Atomic konstrukce](../../../parallel/openmp/2-6-4-atomic-construct.md).

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

## <a name="barrier"></a>bariéra

Synchronizuje všechna vlákna v týmu; všechna vlákna se pozastaví na bariérě, dokud všechna vlákna nespustí bariéru.

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>Poznámky

Direktiva `barrier` nepodporuje žádné klauzule.

Další informace najdete v tématu [direktiva 2.6.3 bariéry](../../../parallel/openmp/2-6-3-barrier-directive.md).

### <a name="example"></a>Příklad

Ukázku použití `barrier`naleznete v části [Master](#master).

## <a name="critical"></a>kritické

Určuje, že kód je spuštěn pouze v jednom vlákně.

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Jméno*<br/>
Volitelné Název pro identifikaci kritického kódu. Název musí být uzavřen v závorkách.

### <a name="remarks"></a>Poznámky

Direktiva `critical` nepodporuje žádné klauzule.

Další informace naleznete v tématu [2.6.2 Critical konstrukce](../../../parallel/openmp/2-6-2-critical-construct.md).

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

## <a name="flush-openmp"></a>zaznamenány

Určuje, že všechna vlákna mají stejné zobrazení paměti pro všechny sdílené objekty.

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Parametry

*var*<br/>
Volitelné Seznam proměnných oddělených čárkami, které reprezentují objekty, které chcete synchronizovat. Pokud není zadán *var* , je vyprázdněna veškerá paměť.

### <a name="remarks"></a>Poznámky

Direktiva `flush` nepodporuje žádné klauzule.

Další informace naleznete v tématu [direktiva aplikace 2.6.5 flush](../../../parallel/openmp/2-6-5-flush-directive.md).

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

## <a name="for-openmp"></a>for

Způsobí, že práce ve smyčce `for` uvnitř paralelní oblasti bude rozdělena mezi vlákna.

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Parametry

*platný*<br/>
Volitelné Nula nebo více klauzulích naleznete v části **poznámky** .

*for_statement*<br/>
Smyčka `for`. Nedefinované chování bude mít za následek, že uživatelský kód ve smyčce `for` změní indexovou proměnnou.

### <a name="remarks"></a>Poznámky

Direktiva `for` podporuje následující klauzule:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [objednávek](openmp-clauses.md#ordered-openmp-clauses)
- [schedule](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

Pokud je zadána také možnost `parallel`, `clauses` může být libovolná klauzule přijatá direktivami `parallel` nebo `for` s výjimkou `nowait`.

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

## <a name="master"></a>hlavní

Určuje, že by měl být spuštěn pouze hlavní podproces programu.

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Poznámky

Direktiva `master` nepodporuje žádné klauzule.

[Jediná](#single) Direktiva umožňuje určit, že část kódu by měla být spuštěna v jednom vlákně, nemusí nutně být hlavním vláknem.

Další informace najdete v tématu [2.6.1 Master konstrukce](../../../parallel/openmp/2-6-1-master-construct.md).

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

## <a name="ordered-openmp-directives"></a>objednávek

Určuje, že kód pod paralelně `for` smyčkou by měl být proveden jako sekvenční smyčka.

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Poznámky

Direktiva `ordered` musí být v dynamickém rozsahu [pro](#for-openmp) nebo `parallel for` konstrukce s klauzulí `ordered`.

Direktiva `ordered` nepodporuje žádné klauzule.

Další informace naleznete v tématu [2.6.6ED konstrukce](../../../parallel/openmp/2-6-6-ordered-construct.md).

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

## <a name="parallel"></a>zpracování

Definuje paralelní oblast, což je kód, který bude spuštěn paralelně více vlákny.

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*platný*<br/>
Volitelné Nula nebo více klauzulích naleznete v části **poznámky** .

### <a name="remarks"></a>Poznámky

Direktiva `parallel` podporuje následující klauzule:

- [Přestože](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [sdíleného](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel` lze také použít spolu s direktivami [oddílů](#sections-openmp) [a.](#for-openmp)

Další informace najdete v tématu [2,3 paralelní konstrukce](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak nastavit počet vláken a definovat paralelní oblast. Počet podprocesů je ve výchozím nastavení stejný jako počet logických procesorů v počítači. Například pokud máte počítač s jedním fyzickým procesorem s povoleným podprocesem, bude mít dva logické procesory a dvě vlákna. Pořadí výstupu se může v různých počítačích lišit.

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

## <a name="sections-openmp"></a>řezů

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

*platný*<br/>
Volitelné Nula nebo více klauzulích naleznete v části **poznámky** .

### <a name="remarks"></a>Poznámky

Direktiva `sections` může obsahovat nula nebo více direktiv `section`.

Direktiva `sections` podporuje následující klauzule:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

Pokud je zadána také možnost `parallel`, `clauses` může být libovolná klauzule přijatá direktivami `parallel` nebo `sections` s výjimkou `nowait`.

Další informace naleznete v části [2.4.2 konstrukce](../../../parallel/openmp/2-4-2-sections-construct.md).

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

## <a name="single"></a>konkrétní

Umožňuje určit, že oddíl kódu by měl být spuštěn v jednom vlákně, nemusí nutně být hlavním vláknem.

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*platný*<br/>
Volitelné Nula nebo více klauzulích naleznete v části **poznámky** .

### <a name="remarks"></a>Poznámky

Direktiva `single` podporuje následující klauzule:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

[Hlavní](#master) Direktiva umožňuje určit, že oddíl kódu by měl být proveden pouze v hlavním vlákně.

Další informace naleznete v části [2.4.3 Single konstrukcí](../../../parallel/openmp/2-4-3-single-construct.md).

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

Určuje, že proměnná je soukromá pro vlákno.

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Seznam proměnných oddělených čárkami, které chcete nastavit jako soukromé pro vlákno. *var* musí být buď proměnná s oborem názvů (Global), nebo místní statická proměnná.

### <a name="remarks"></a>Poznámky

Direktiva `threadprivate` nepodporuje žádné klauzule.

Direktiva `threadprivate` je založena na atributu [thread](../../../cpp/thread.md) pomocí klíčového slova [__declspec](../../../cpp/declspec.md) ; limity `__declspec(thread)` platí pro `threadprivate`. Například proměnná `threadprivate` bude existovat v jakémkoli vlákně spuštěném v procesu, nikoli pouze vlákna, která jsou součástí týmu vláken vytvořeného pomocí paralelní oblasti. Uvědomte si tyto podrobnosti implementace; Můžete si všimnout, že konstruktory pro `threadprivate` uživatelsky definovaného typu jsou volány častěji.

Můžete použít `threadprivate` v knihovně DLL, která je staticky načtena při spuštění procesu, ale nelze použít `threadprivate` v žádné knihovně DLL, která bude načtena prostřednictvím funkce [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) , jako je například knihovna DLL, které jsou načteny pomocí [/DELAYLOAD (import zpožděného načtení)](../../../build/reference/delayload-delay-load-import.md), který také používá `LoadLibrary`.

U `threadprivate` proměnné typu *zničitelné* není zaručeno, že by měl být volán destruktor. Příklad:

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

Uživatelé nemají žádnou kontrolu nad tím, kdy skončí vlákna tvořící paralelní oblast. Pokud tato vlákna existují po ukončení procesu, vlákna nebudou informována o ukončení procesu a destruktor nebude volán pro `threaded_var` v jakémkoli vlákně s výjimkou toho, který ukončuje (zde primární vlákno). Takže kód by neměl počítat se správným zničením `threadprivate` proměnných.

Další informace najdete v tématu [direktiva 2.7.1 threadprivate](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

### <a name="example"></a>Příklad

Ukázku použití `threadprivate`naleznete v tématu [Private](openmp-clauses.md#private-openmp).
