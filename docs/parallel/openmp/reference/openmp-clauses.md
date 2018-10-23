---
title: OpenMP – klauzule | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OpenMP clauses
- copyin
- copyprivate
- default
- firstprivate
- if
- lastprivate
- nowait
- num_threads
- ordered
- private
- reduction
- schedule
- shared
dev_langs:
- C++
helpviewer_keywords:
- OpenMP clauses
- copyin OpenMP clause
- copyprivate OpenMP clause
- default OpenMP clause
- defaults, OpenMP clause
- firstprivate OpenMP clause
- if OpenMP clause
- lastprivate OpenMP clause
- nowait OpenMP clause
- num_threads OpenMP clause
- ordered OpenMP clause
- private OpenMP clause
- reduction OpenMP clause
- schedule OpenMP clause
- shared OpenMP clause
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d19a2b1859012a56bdaf3c454f8b92758179bed9
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49809067"
---
# <a name="openmp-clauses"></a>OpenMP – klauzule

Obsahuje odkazy na použité v rozhraní API OpenMP – klauzule.

Jazyk Visual C++ podporuje následující klauzule OpenMP:

Klauzule                             | Popis
---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[copyin](#copyin)                  | Umožňuje vláken pro přístup k hodnotě hlavní vlákno, [threadprivate](openmp-directives.md#threadprivate) proměnné.
[copyprivate](#copyprivate)        | Určuje, že jeden nebo více proměnných by měl být sdílena mezi všemi vlákny.
[default](#default-openmp)         | Určuje chování bez ohledu na obor proměnné v paralelní oblasti.
[firstprivate](#firstprivate)      | Určuje, že každé vlákno má svoji vlastní instanci proměnné. proto, že proměnné by měl inicializovat pomocí hodnoty proměnné, protože existuje před paralelní konstrukce.
[if](#if-openmp)                   | Určuje, zda smyčku budou spuštěny paralelně nebo postupně.
[lastprivate](#lastprivate)        | Určuje, že verze nadřazeného objektu context proměnné je nastavena na soukromou verzi podle toho, která vlákno spustí poslední iterace (konstrukci smyčky for-loop) nebo poslední část (#pragma oddílů).
[nowait](#nowait)                  | Přepíše překážkou implicitní v direktivě.
[num_threads](#num-threads)        | Nastaví počet vláken v týmu vlákna.
[Řazení](#ordered-openmp-clauses) | Vyžaduje na paralelní [pro](openmp-directives.md#for-openmp) příkaz Pokud [seřazené](openmp-directives.md#ordered-openmp-directives) – direktiva se má použít ve smyčce.
[private](#private-openmp)         | Určuje, že každé vlákno má svoji vlastní instanci proměnné.
[reduction](#reduction)            | Určuje, že jeden nebo více proměnných, které jsou privátní pro každé vlákno je předmětem operaci snížení na konci paralelní oblasti.
[schedule](#schedule)              | Platí pro [pro](openmp-directives.md#for-openmp) směrnice.
[Sdílet](#shared-openmp)           | Určuje, že jeden nebo více proměnných by měl být sdílena mezi všemi vlákny.

## <a name="copyin"></a>copyin

Umožňuje vláken pro přístup k hodnotě hlavní vlákno, [threadprivate](openmp-directives.md#threadprivate) proměnné.

```
copyin(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
`threadprivate` Proměnné, která bude inicializován hodnotou proměnné v hlavním vlákně, protože existuje před paralelní konstrukce.

### <a name="remarks"></a>Poznámky

`copyin` platí pro následující direktivy:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Oddíly](openmp-directives.md#sections-openmp)

Další informace najdete v tématu [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md).

### <a name="example"></a>Příklad

Zobrazit [threadprivate](openmp-directives.md#threadprivate) pro příklad použití `copyin`.

## <a name="copyprivate"></a>copyprivate

Určuje, že jeden nebo více proměnných by měl být sdílena mezi všemi vlákny.

```
copyprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Jeden nebo více proměnných sdílet. Pokud je zadán více než jednu proměnnou, oddělte názvy proměnných čárkou.

### <a name="remarks"></a>Poznámky

`copyprivate` platí pro [jeden](openmp-directives.md#single) směrnice.

Další informace najdete v tématu [2.7.2.8 copyprivate](../../../parallel/openmp/2-7-2-8-copyprivate.md).

### <a name="example"></a>Příklad

```
// omp_copyprivate.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

float x, y, fGlobal = 1.0;
#pragma omp threadprivate(x, y)

float get_float() {
   fGlobal += 0.001;
   return fGlobal;
}

void use_float(float f, int t) {
   printf_s("Value = %f, thread = %d\n", f, t);
}

void CopyPrivate(float a, float b) {
   #pragma omp single copyprivate(a, b, x, y)
   {
      a = get_float();
      b = get_float();
      x = get_float();
      y = get_float();
    }

   use_float(a, omp_get_thread_num());
   use_float(b, omp_get_thread_num());
   use_float(x, omp_get_thread_num());
   use_float(y, omp_get_thread_num());
}

int main() {
   float a = 9.99, b = 123.456;

   printf_s("call CopyPrivate from a single thread\n");
   CopyPrivate(9.99, 123.456);

   printf_s("call CopyPrivate from a parallel region\n");
   #pragma omp parallel
   {
      CopyPrivate(a, b);
   }
}
```

```Output
call CopyPrivate from a single thread
Value = 1.001000, thread = 0
Value = 1.002000, thread = 0
Value = 1.003000, thread = 0
Value = 1.004000, thread = 0
call CopyPrivate from a parallel region
Value = 1.005000, thread = 0
Value = 1.005000, thread = 1
Value = 1.006000, thread = 0
Value = 1.006000, thread = 1
Value = 1.007000, thread = 0
Value = 1.007000, thread = 1
Value = 1.008000, thread = 0
Value = 1.008000, thread = 1
```

## <a name="default-openmp"></a>Výchozí (OpenMP)

Určuje chování bez ohledu na obor proměnné v paralelní oblasti.

```
default(shared | none)
```

### <a name="remarks"></a>Poznámky

`shared`, což je v platnosti Pokud `default` klauzule není uvedený, znamená to, že všechny proměnné v paralelní oblasti zpracovávány jako by to byly zadány s [sdílené](#shared-openmp) klauzuli. `none` znamená, že všechny proměnné, používat v paralelní oblasti, která nejsou obor [privátní](#private-openmp), [sdílené](#shared-openmp), [snížení](#reduction), [firstprivate](#firstprivate), nebo [lastprivate](#lastprivate) klauzule způsobí chybu kompilátoru.

`default` platí pro následující direktivy:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Oddíly](openmp-directives.md#sections-openmp)

Další informace najdete v tématu [2.7.2.5 výchozí](../../../parallel/openmp/2-7-2-5-default.md).

### <a name="example"></a>Příklad

Zobrazit [privátní](#private-openmp) pro příklad použití `default`.

## <a name="firstprivate"></a>firstprivate

Určuje, že každé vlákno má svoji vlastní instanci proměnné. proto, že proměnné by měl inicializovat pomocí hodnoty proměnné, protože existuje před paralelní konstrukce.

```
firstprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
U instancí v každé vlákno a které proměnné se inicializuje s hodnotu proměnné, protože existuje před paralelní konstrukce. Pokud je zadán více než jednu proměnnou, oddělte názvy proměnných čárkou.

### <a name="remarks"></a>Poznámky

`firstprivate` platí pro následující direktivy:

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [Oddíly](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

Další informace najdete v tématu [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md).

### <a name="example"></a>Příklad

Příklad použití `firstprivate`, podívejte se na příklad v [privátní](#private-openmp).

## <a name="if-openmp"></a>Pokud (OpenMP)

Určuje, zda smyčku budou spuštěny paralelně nebo postupně.

```
if(expression)
```

### <a name="parameters"></a>Parametry

*Výraz*<br/>
Celočíselný výraz, který, pokud se vyhodnotí jako true (nenulový), způsobí, že kód v paralelní oblasti spustit paralelně. Pokud je výraz vyhodnocen jako na hodnotu false (nula), paralelní oblasti provádí postupně (jedno vlákno).

### <a name="remarks"></a>Poznámky

`if` platí pro následující direktivy:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Oddíly](openmp-directives.md#sections-openmp)

Další informace najdete v tématu [2.3 parallel – konstrukce](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Příklad

```
// omp_if.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void test(int val)
{
    #pragma omp parallel if (val)
    if (omp_in_parallel())
    {
        #pragma omp single
        printf_s("val = %d, parallelized with %d threads\n",
                 val, omp_get_num_threads());
    }
    else
    {
        printf_s("val = %d, serialized\n", val);
    }
}

int main( )
{
    omp_set_num_threads(2);
    test(0);
    test(2);
}
```

```Output
val = 0, serialized
val = 2, parallelized with 2 threads
```

## <a name="lastprivate"></a>lastprivate

Určuje, že verze nadřazeného objektu context proměnné je nastavena na soukromou verzi podle toho, která vlákno spustí poslední iterace (konstrukci smyčky for-loop) nebo poslední část (#pragma oddílů).

```
lastprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Proměnné, která je nastavena na soukromou verzi podle toho, která vlákna spustí poslední iterace (konstrukci smyčky for-loop) nebo poslední část (#pragma oddílů).

### <a name="remarks"></a>Poznámky

`lastprivate` platí pro následující direktivy:

- [for](openmp-directives.md#for-openmp)
- [Oddíly](openmp-directives.md#sections-openmp)

Další informace najdete v tématu [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).

### <a name="example"></a>Příklad

Zobrazit [plán](#schedule) pro příklad použití `lastprivate` klauzuli.

## <a name="nowait"></a>nowait

Přepíše překážkou implicitní v direktivě.

```
nowait
```

### <a name="remarks"></a>Poznámky

`nowait` platí pro následující direktivy:

- [for](openmp-directives.md#for-openmp)
- [Oddíly](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

Další informace najdete v tématu [2.4.1 for – konstrukce](../../../parallel/openmp/2-4-1-for-construct.md), [2.4.2 sections – konstrukce](../../../parallel/openmp/2-4-2-sections-construct.md), a [2.4.3 jeden vytvořit](../../../parallel/openmp/2-4-3-single-construct.md).

### <a name="example"></a>Příklad

```
// omp_nowait.cpp
// compile with: /openmp /c
#include <stdio.h>

#define SIZE 5

void test(int *a, int *b, int *c, int size)
{
    int i;
    #pragma omp parallel
    {
        #pragma omp for nowait
        for (i = 0; i < size; i++)
            b[i] = a[i] * a[i];

        #pragma omp for nowait
        for (i = 0; i < size; i++)
            c[i] = a[i]/2;
    }
}

int main( )
{
    int a[SIZE], b[SIZE], c[SIZE];
    int i;

    for (i=0; i<SIZE; i++)
        a[i] = i;

    test(a,b,c, SIZE);

    for (i=0; i<SIZE; i++)
        printf_s("%d, %d, %d\n", a[i], b[i], c[i]);
}
```

```Output
0, 0, 0
1, 1, 0
2, 4, 1
3, 9, 1
4, 16, 2
```

## <a name="num-threads"></a>num_threads

Nastaví počet vláken v týmu vlákna.

```
num_threads(num)
```

### <a name="parameters"></a>Parametry

*počet*<br/>
Počet vláken

### <a name="remarks"></a>Poznámky

`num_threads` Klauzule má stejné funkce jako [omp_set_num_threads –](../../../parallel/openmp/reference/omp-set-num-threads.md) funkce.

`num_threads` platí pro následující direktivy:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Oddíly](openmp-directives.md#sections-openmp)

Další informace najdete v tématu [2.3 parallel – konstrukce](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Příklad

Zobrazit [paralelní](openmp-directives.md#parallel) pro příklad použití `num_threads` klauzuli.

## <a name="ordered-openmp-clauses"></a>ordered (klauzule OpenMP)

Vyžaduje na paralelní [pro](openmp-directives.md#for-openmp) příkaz Pokud [seřazené](openmp-directives.md#ordered-openmp-directives) – direktiva se má použít ve smyčce.

```
ordered
```

### <a name="remarks"></a>Poznámky

`ordered` platí pro [pro](openmp-directives.md#for-openmp) směrnice.

Další informace najdete v tématu [2.4.1 for – konstrukce](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Příklad

Zobrazit [seřazené](openmp-directives.md#ordered-openmp-directives) pro příklad použití `ordered` klauzuli.

## <a name="private-openmp"></a>privátní (OpenMP)

Určuje, že každé vlákno má svoji vlastní instanci proměnné.

```
private(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
U instancí v každém vlákně proměnné.

### <a name="remarks"></a>Poznámky

`private` platí pro následující direktivy:

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [Oddíly](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

Další informace najdete v tématu [2.7.2.1 privátní](../../../parallel/openmp/2-7-2-1-private.md).

### <a name="example"></a>Příklad

```C
// openmp_private.c
// compile with: /openmp
#include <windows.h>
#include <assert.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SLEEP_THREAD 1
#define NUM_LOOPS 2

enum Types {
   ThreadPrivate,
   Private,
   FirstPrivate,
   LastPrivate,
   Shared,
   MAX_TYPES
};

int nSave[NUM_THREADS][MAX_TYPES][NUM_LOOPS] = {{0}};
int nThreadPrivate;

#pragma omp threadprivate(nThreadPrivate)
#pragma warning(disable:4700)

int main() {
   int nPrivate = NUM_THREADS;
   int nFirstPrivate = NUM_THREADS;
   int nLastPrivate = NUM_THREADS;
   int nShared = NUM_THREADS;
   int nRet = 0;
   int i;
   int j;
   int nLoop = 0;

   nThreadPrivate = NUM_THREADS;
   printf_s("These are the variables before entry "
           "into the parallel region.\n");
   printf_s("nThreadPrivate = %d\n", nThreadPrivate);
   printf_s("      nPrivate = %d\n", nPrivate);
   printf_s(" nFirstPrivate = %d\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d\n", nLastPrivate);
   printf_s("       nShared = %d\n\n", nShared);
   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel copyin(nThreadPrivate) private(nPrivate) shared(nShared) firstprivate(nFirstPrivate)
   {
      #pragma omp for schedule(static) lastprivate(nLastPrivate)
      for (i = 0 ; i < NUM_THREADS ; ++i) {
         for (j = 0 ; j < NUM_LOOPS ; ++j) {
            int nThread = omp_get_thread_num();
            assert(nThread < NUM_THREADS);

            if (nThread == SLEEP_THREAD)
               Sleep(100);
            nSave[nThread][ThreadPrivate][j] = nThreadPrivate;
            nSave[nThread][Private][j] = nPrivate;
            nSave[nThread][Shared][j] = nShared;
            nSave[nThread][FirstPrivate][j] = nFirstPrivate;
            nSave[nThread][LastPrivate][j] = nLastPrivate;
            nThreadPrivate = nThread;
            nPrivate = nThread;
            nShared = nThread;
            nLastPrivate = nThread;
            --nFirstPrivate;
         }
      }
   }

   for (i = 0 ; i < NUM_LOOPS ; ++i) {
      for (j = 0 ; j < NUM_THREADS ; ++j) {
         printf_s("These are the variables at entry of "
                  "loop %d of thread %d.\n", i + 1, j);
         printf_s("nThreadPrivate = %d\n",
                  nSave[j][ThreadPrivate][i]);
         printf_s("      nPrivate = %d\n",
                  nSave[j][Private][i]);
         printf_s(" nFirstPrivate = %d\n",
                  nSave[j][FirstPrivate][i]);
         printf_s("  nLastPrivate = %d\n",
                  nSave[j][LastPrivate][i]);
         printf_s("       nShared = %d\n\n",
                  nSave[j][Shared][i]);
      }
   }

   printf_s("These are the variables after exit from "
            "the parallel region.\n");
   printf_s("nThreadPrivate = %d (The last value in the "
            "master thread)\n", nThreadPrivate);
   printf_s("      nPrivate = %d (The value prior to "
            "entering parallel region)\n", nPrivate);
   printf_s(" nFirstPrivate = %d (The value prior to "
            "entering parallel region)\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d (The value from the "
            "last iteration of the loop)\n", nLastPrivate);
   printf_s("       nShared = %d (The value assigned, "
            "from the delayed thread, %d)\n\n",
            nShared, SLEEP_THREAD);
}
```

```Output
These are the variables before entry into the parallel region.
nThreadPrivate = 4
      nPrivate = 4
nFirstPrivate = 4
  nLastPrivate = 4
       nShared = 4

These are the variables at entry of loop 1 of thread 0.
nThreadPrivate = 4
      nPrivate = 1310720
nFirstPrivate = 4
  nLastPrivate = 1245104
       nShared = 3

These are the variables at entry of loop 1 of thread 1.
nThreadPrivate = 4
      nPrivate = 4488
nFirstPrivate = 4
  nLastPrivate = 19748
       nShared = 0

These are the variables at entry of loop 1 of thread 2.
nThreadPrivate = 4
      nPrivate = -132514848
nFirstPrivate = 4
  nLastPrivate = -513199792
       nShared = 4

These are the variables at entry of loop 1 of thread 3.
nThreadPrivate = 4
      nPrivate = 1206
nFirstPrivate = 4
  nLastPrivate = 1204
       nShared = 2

These are the variables at entry of loop 2 of thread 0.
nThreadPrivate = 0
      nPrivate = 0
nFirstPrivate = 3
  nLastPrivate = 0
       nShared = 0

These are the variables at entry of loop 2 of thread 1.
nThreadPrivate = 1
      nPrivate = 1
nFirstPrivate = 3
  nLastPrivate = 1
       nShared = 1

These are the variables at entry of loop 2 of thread 2.
nThreadPrivate = 2
      nPrivate = 2
nFirstPrivate = 3
  nLastPrivate = 2
       nShared = 2

These are the variables at entry of loop 2 of thread 3.
nThreadPrivate = 3
      nPrivate = 3
nFirstPrivate = 3
  nLastPrivate = 3
       nShared = 3

These are the variables after exit from the parallel region.
nThreadPrivate = 0 (The last value in the master thread)
      nPrivate = 4 (The value prior to entering parallel region)
nFirstPrivate = 4 (The value prior to entering parallel region)
  nLastPrivate = 3 (The value from the last iteration of the loop)
       nShared = 1 (The value assigned, from the delayed thread, 1)
```

## <a name="reduction"></a>snížení

Určuje, že jeden nebo více proměnných, které jsou privátní pro každé vlákno je předmětem operaci snížení na konci paralelní oblasti.

```
reduction(operation:var)
```

### <a name="parameters"></a>Parametry

*Operace*<br/>
Operátor pro tuto operaci provést na proměnných (`var`) na konci paralelní oblasti.

*var*<br/>
Jeden nebo více proměnných na základě které chcete provést snížení skaláru. Pokud je zadán více než jednu proměnnou, oddělte názvy proměnných čárkou.

### <a name="remarks"></a>Poznámky

`reduction` platí pro následující direktivy:

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [Oddíly](openmp-directives.md#sections-openmp)

Další informace najdete v tématu [2.7.2.6 snížení](../../../parallel/openmp/2-7-2-6-reduction.md).

### <a name="example"></a>Příklad

```
// omp_reduction.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SUM_START   1
#define SUM_END     10
#define FUNC_RETS   {1, 1, 1, 1, 1}

int bRets[5] = FUNC_RETS;
int nSumCalc = ((SUM_START + SUM_END) * (SUM_END - SUM_START + 1)) / 2;

int func1( ) {return bRets[0];}
int func2( ) {return bRets[1];}
int func3( ) {return bRets[2];}
int func4( ) {return bRets[3];}
int func5( ) {return bRets[4];}

int main( )
{
    int nRet = 0,
        nCount = 0,
        nSum = 0,
        i,
        bSucceed = 1;

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel reduction(+ : nCount)
    {
        nCount += 1;

        #pragma omp for reduction(+ : nSum)
        for (i = SUM_START ; i <= SUM_END ; ++i)
            nSum += i;

        #pragma omp sections reduction(&& : bSucceed)
        {
            #pragma omp section
            {
                bSucceed = bSucceed && func1( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func2( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func3( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func4( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func5( );
            }
        }
    }

    printf_s("The parallel section was executed %d times "
             "in parallel.\n", nCount);
    printf_s("The sum of the consecutive integers from "
             "%d to %d, is %d\n", 1, 10, nSum);

    if (bSucceed)
        printf_s("All of the functions, func1 through "
                 "func5 succeeded!\n");
    else
        printf_s("One or more of the functions, func1 "
                 "through func5 failed!\n");

    if (nCount != NUM_THREADS)
    {
        printf_s("ERROR: For %d threads, %d were counted!\n",
                 NUM_THREADS, nCount);
        nRet |= 0x1;
   }

    if (nSum != nSumCalc)
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                "but %d was reported!\n",
                SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x10;
    }

    if (bSucceed != (bRets[0] && bRets[1] &&
                     bRets[2] && bRets[3] && bRets[4]))
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                 "but %d was reported!\n",
                 SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x100;
    }
}
```

```Output
The parallel section was executed 4 times in parallel.
The sum of the consecutive integers from 1 to 10, is 55
All of the functions, func1 through func5 succeeded!
```

## <a name="schedule"></a>Plán

Platí pro [pro](openmp-directives.md#for-openmp) směrnice.

```
schedule(type[,size])
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Typ plánování:

- `dynamic`
- `guided`
- `runtime`
- `static`

*Velikost*<br/>
(Volitelné) Určuje velikost iterací. `size` musí být celé číslo. Není platná v případě `type` je `runtime`.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [2.4.1 for – konstrukce](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Příklad

```cpp
// omp_schedule.cpp
// compile with: /openmp
#include <windows.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define STATIC_CHUNK 5
#define DYNAMIC_CHUNK 5
#define NUM_LOOPS 20
#define SLEEP_EVERY_N 3

int main( )
{
    int nStatic1[NUM_LOOPS],
        nStaticN[NUM_LOOPS];
    int nDynamic1[NUM_LOOPS],
        nDynamicN[NUM_LOOPS];
    int nGuided[NUM_LOOPS];

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel
    {
        #pragma omp for schedule(static, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStatic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(static, STATIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStaticN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, DYNAMIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamicN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(guided)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nGuided[i] = omp_get_thread_num( );
        }
    }

    printf_s("------------------------------------------------\n");
    printf_s("| static | static | dynamic | dynamic | guided |\n");
    printf_s("|    1   |    %d   |    1    |    %d    |        |\n",
             STATIC_CHUNK, DYNAMIC_CHUNK);
    printf_s("------------------------------------------------\n");

    for (int i=0; i<NUM_LOOPS; ++i)
    {
        printf_s("|    %d   |    %d   |    %d    |    %d    |"
                 "    %d   |\n",
                 nStatic1[i], nStaticN[i],
                 nDynamic1[i], nDynamicN[i], nGuided[i]);
    }

    printf_s("------------------------------------------------\n");
}
```

```Output
------------------------------------------------
| static | static | dynamic | dynamic | guided |
|    1   |    5   |    1    |    5    |        |
------------------------------------------------
|    0   |    0   |    0    |    2    |    1   |
|    1   |    0   |    3    |    2    |    1   |
|    2   |    0   |    3    |    2    |    1   |
|    3   |    0   |    3    |    2    |    1   |
|    0   |    0   |    2    |    2    |    1   |
|    1   |    1   |    2    |    3    |    3   |
|    2   |    1   |    2    |    3    |    3   |
|    3   |    1   |    0    |    3    |    3   |
|    0   |    1   |    0    |    3    |    3   |
|    1   |    1   |    0    |    3    |    2   |
|    2   |    2   |    1    |    0    |    2   |
|    3   |    2   |    1    |    0    |    2   |
|    0   |    2   |    1    |    0    |    3   |
|    1   |    2   |    2    |    0    |    3   |
|    2   |    2   |    2    |    0    |    0   |
|    3   |    3   |    2    |    1    |    0   |
|    0   |    3   |    3    |    1    |    1   |
|    1   |    3   |    3    |    1    |    1   |
|    2   |    3   |    3    |    1    |    1   |
|    3   |    3   |    0    |    1    |    3   |
------------------------------------------------

```

## <a name="shared-openmp"></a>sdílené (OpenMP)

Určuje, že jeden nebo více proměnných by měl být sdílena mezi všemi vlákny.

```
shared(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Jeden nebo více proměnných sdílet. Pokud je zadán více než jednu proměnnou, oddělte názvy proměnných čárkou.

### <a name="remarks"></a>Poznámky

Dalším způsobem, jak sdílet proměnné mezi vlákny je [copyprivate](#copyprivate) klauzuli.

`shared` platí pro následující direktivy:

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [Oddíly](openmp-directives.md#sections-openmp)

Další informace najdete v tématu [2.7.2.4 sdílené](../../../parallel/openmp/2-7-2-4-shared.md).

### <a name="example"></a>Příklad

Zobrazit [privátní](#private-openmp) pro příklad použití `shared`.
