---
title: Funkce jazyka OpenMP
ms.date: 03/20/2019
f1_keywords:
- OpenMP functions
- omp_destroy_lock
- omp_destroy_nest_lock
- omp_get_dynamic
- omp_get_max_threads
- omp_get_nested
- omp_get_num_procs
- omp_get_num_threads
- omp_get_thread_num
- omp_get_wtick
- omp_get_wtime
- omp_in_parallel
- omp_init_lock
- omp_init_nest_lock
- omp_set_dynamic
- omp_set_lock
- omp_set_nest_lock
- omp_set_nested
- omp_set_num_threads
- omp_test_lock
- omp_test_nest_lock
- omp_unset_lock
- omp_unset_nest_lock
helpviewer_keywords:
- OpenMP functions
- omp_destroy_lock OpenMP function
- omp_destroy_nest_lock OpenMP function
- omp_get_dynamic OpenMP function
- omp_get_max_threads OpenMP function
- omp_get_nested OpenMP function
- omp_get_num_procs OpenMP function
- omp_get_num_threads OpenMP function
- omp_get_thread_num OpenMP function
- omp_get_wtick OpenMP function
- omp_get_wtime OpenMP function
- omp_in_parallel OpenMP function
- omp_init_lock OpenMP function
- omp_init_nest_lock OpenMP function
- omp_set_dynamic OpenMP function
- omp_set_lock OpenMP function
- omp_set_nest_lock OpenMP function
- omp_set_nested OpenMP function
- omp_set_num_threads OpenMP function
- omp_test_lock OpenMP function
- omp_test_nest_lock OpenMP function
- omp_unset_lock OpenMP function
- omp_unset_nest_lock OpenMP function
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
ms.openlocfilehash: 4508c683ff5d4bece290b7fef2bbd83ae8023eac
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882893"
---
# <a name="openmp-functions"></a>Funkce jazyka OpenMP

Obsahuje odkazy na funkce používané v rozhraní OpenMP API.

Visual C++ implementace standardu OpenMP zahrnuje následující funkce a datové typy.

Pro provádění prostředí:

|Funkce|Popis|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|Nastaví počet vláken v nadcházejících paralelních oblastech, pokud není přepsána klauzulí [num_threads](openmp-clauses.md#num-threads) .|
|[omp_get_num_threads](#omp-get-num-threads)|Vrátí počet vláken v paralelní oblasti.|
|[omp_get_max_threads](#omp-get-max-threads)|Vrátí celé číslo, které je větší nebo rovno počtu vláken, která by byla k dispozici, pokud byla v tomto okamžiku v kódu definována paralelní oblast bez [num_threads](openmp-clauses.md#num-threads) .|
|[omp_get_thread_num](#omp-get-thread-num)|Vrátí počet vláken, které se spouští v rámci svého týmu vláken.|
|[omp_get_num_procs](#omp-get-num-procs)|Vrátí počet procesorů, které jsou k dispozici při volání funkce.|
|[omp_in_parallel](#omp-in-parallel)|Vrátí nenulovou hodnotu, pokud je volána v rámci paralelní oblasti.|
|[omp_set_dynamic](#omp-set-dynamic)|Označuje, že počet vláken, která jsou k dispozici v nadcházejících paralelních oblastech, lze upravit za běhu.|
|[omp_get_dynamic](#omp-get-dynamic)|Vrátí hodnotu, která označuje, zda počet vláken, která jsou k dispozici v nadcházejících paralelních oblastech, lze upravit za běhu.|
|[omp_set_nested](#omp-set-nested)|Povoluje vnořené paralelismus.|
|[omp_get_nested](#omp-get-nested)|Vrátí hodnotu, která označuje, zda je povolen vnořený paralelismus.|

Pro zámek:

|Funkce|Popis|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|Inicializuje jednoduchý zámek.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Inicializuje zámek.|
|[omp_destroy_lock](#omp-destroy-lock)|Zruší inicializaci zámku.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Zruší inicializaci vnořeného zámku.|
|[omp_set_lock](#omp-set-lock)|Blokuje spuštění vlákna, dokud není k dispozici zámek.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Blokuje spuštění vlákna, dokud není k dispozici zámek.|
|[omp_unset_lock](#omp-unset-lock)|Uvolní zámek.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Uvolňuje vnořený zámek.|
|[omp_test_lock](#omp-test-lock)|Pokusí se nastavit zámek, ale neblokuje provádění vlákna.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Pokusí se nastavit vnořený zámek, ale neblokuje provádění vlákna.|

|Typ dat|Popis|
|---------|-----------|
|`omp_lock_t`|Typ, který obsahuje stav zámku, zda je zámek k dispozici nebo pokud vlákno vlastní zámek.|
|`omp_nest_lock_t`|Typ, který obsahuje jednu z následujících částí informací o zámku: zda je zámek k dispozici, a identitu vlákna, které vlastní zámek a počet vnoření.|

Pro časové rutiny:

|Funkce|Popis|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|Vrátí hodnotu v sekundách doby uplynulou od určitého bodu.|
|[omp_get_wtick](#omp-get-wtick)|Vrátí počet sekund mezi takty procesoru.|

## <a name="omp-destroy-lock"></a>omp_destroy_lock

Zruší inicializaci zámku.

```cpp
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnná typu `omp_lock_t`, která byla inicializována s [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [3.2.2 omp_destroy_lock a omp_destroy_nest_lock Functions](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Příklad

Příklad použití `omp_destroy_lock`naleznete v tématu [omp_init_lock](#omp-init-lock) .

## <a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

Zruší inicializaci vnořeného zámku.

```cpp
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnná typu `omp_nest_lock_t`, která byla inicializována s [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [3.2.2 omp_destroy_lock a omp_destroy_nest_lock Functions](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Příklad

Příklad použití `omp_destroy_nest_lock`naleznete v tématu [omp_init_nest_lock](#omp-init-nest-lock) .

## <a name="omp-get-dynamic"></a>omp_get_dynamic

Vrátí hodnotu, která označuje, zda počet vláken, která jsou k dispozici v nadcházejících paralelních oblastech, lze upravit za běhu.

```cpp
int omp_get_dynamic();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota znamená, že vlákna budou dynamicky upravována.

### <a name="remarks"></a>Poznámky

Dynamická úprava vláken je určena pomocí [omp_set_dynamic](#omp-set-dynamic) a [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic).

Další informace najdete v tématu [funkce 3.1.7 omp_set_dynamic](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Příklad

Příklad použití `omp_get_dynamic`naleznete v tématu [omp_set_dynamic](#omp-set-dynamic) .

## <a name="omp-get-max-threads"></a>omp_get_max_threads

Vrátí celé číslo, které je větší nebo rovno počtu vláken, která by byla k dispozici, pokud byla v tomto okamžiku v kódu definována paralelní oblast bez [num_threads](openmp-clauses.md#num-threads) .

```cpp
int omp_get_max_threads( )
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu o [funkci 3.1.3 omp_get_max_threads](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md).

### <a name="example"></a>Příklad

```cpp
// omp_get_max_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(8);
    printf_s("%d\n", omp_get_max_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));
}
```

```Output
8
8
8
8
8
```

## <a name="omp-get-nested"></a>omp_get_nested

Vrátí hodnotu, která označuje, zda je povolen vnořený paralelismus.

```cpp
int omp_get_nested( );
```

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota znamená, že je povoleno vnořené paralelismus.

### <a name="remarks"></a>Poznámky

Vnořený paralelismus je určen pomocí [omp_set_nested](#omp-set-nested) a [OMP_NESTED](openmp-environment-variables.md#omp-nested).

Další informace najdete v tématu [funkce 3.1.10 omp_get_nested](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

### <a name="example"></a>Příklad

Příklad použití `omp_get_nested`naleznete v tématu [omp_set_nested](#omp-set-nested) .

## <a name="omp-get-num-procs"></a>omp_get_num_procs

Vrátí počet procesorů, které jsou k dispozici při volání funkce.

```cpp
int omp_get_num_procs();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce 3.1.5 omp_get_num_procs](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).

### <a name="example"></a>Příklad

```cpp
// omp_get_num_procs.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    printf_s("%d\n", omp_get_num_procs( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_procs( ));
        }
}
```

```Output
// Expect the following output when the example is run on a two-processor machine:
2
2
```

## <a name="omp-get-num-threads"></a>omp_get_num_threads

Vrátí počet vláken v paralelní oblasti.

```cpp
int omp_get_num_threads( );
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.1.2 omp_get_num_threads Function](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md).

### <a name="example"></a>Příklad

```cpp
// omp_get_num_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_num_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));
}
```

```Output
1
4
1
3
1
```

## <a name="omp-get-thread-num"></a>omp_get_thread_num

Vrátí počet vláken, které se spouští v rámci svého týmu vláken.

```cpp
int omp_get_thread_num( );
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce 3.1.4 omp_get_thread_num](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md).

### <a name="example"></a>Příklad

Příklad použití `omp_get_thread_num`naleznete v tématu [Parallel](openmp-directives.md#parallel) .

## <a name="omp-get-wtick"></a>omp_get_wtick

Vrátí počet sekund mezi takty procesoru.

```cpp
double omp_get_wtick( );
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [3.3.2 omp_get_wtick Function](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md).

### <a name="example"></a>Příklad

Příklad použití `omp_get_wtick`naleznete v tématu [omp_get_wtime](#omp-get-wtime) .

## <a name="omp-get-wtime"></a>omp_get_wtime

Vrátí hodnotu v sekundách doby uplynulou od určitého bodu.

```cpp
double omp_get_wtime( );
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu v sekundách doby uplynulé z libovolného libovolného, ale konzistentního bodu.

### <a name="remarks"></a>Poznámky

Tento bod zůstane v průběhu provádění programu konzistentní, takže je možné provést budoucí porovnání.

Další informace najdete v tématu [3.3.1 omp_get_wtime Function](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md).

### <a name="example"></a>Příklad

```cpp
// omp_get_wtime.cpp
// compile with: /openmp
#include "omp.h"
#include <stdio.h>
#include <windows.h>

int main() {
    double start = omp_get_wtime( );
    Sleep(1000);
    double end = omp_get_wtime( );
    double wtick = omp_get_wtick( );

    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",
             start, end, end - start);

    printf_s("wtick = %.16g\n1/wtick = %.16g\n",
             wtick, 1.0 / wtick);
}
```

```Output
start = 594255.3671159324
end = 594256.3664474116
diff = 0.9993314791936427
wtick = 2.793651148400146e-007
1/wtick = 3579545
```

## <a name="omp-in-parallel"></a>omp_in_parallel

Vrátí nenulovou hodnotu, pokud je volána v rámci paralelní oblasti.

```cpp
int omp_in_parallel( );
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce 3.1.6 omp_in_parallel](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md).

### <a name="example"></a>Příklad

```cpp
// omp_in_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_in_parallel( ));

    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_in_parallel( ));
        }
}
```

```Output
0
1
```

## <a name="omp-init-lock"></a>omp_init_lock

Inicializuje jednoduchý zámek.

```cpp
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnná typu `omp_lock_t`.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [3.2.1 omp_init_lock a omp_init_nest_lock Functions](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

### <a name="example"></a>Příklad

```cpp
// omp_init_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t my_lock;

int main() {
   omp_init_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num( );
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_lock(&my_lock);
         printf_s("Thread %d - starting locked region\n", tid);
         printf_s("Thread %d - ending locked region\n", tid);
         omp_unset_lock(&my_lock);
      }
   }

   omp_destroy_lock(&my_lock);
}
```

```Output
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
```

## <a name="omp-init-nest-lock"></a>omp_init_nest_lock

Inicializuje zámek.

```cpp
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnná typu `omp_nest_lock_t`.

### <a name="remarks"></a>Poznámky

Počáteční počet vnoření je nula.

Další informace naleznete v tématu [3.2.1 omp_init_lock a omp_init_nest_lock Functions](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

### <a name="example"></a>Příklad

```cpp
// omp_init_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t my_lock;

void Test() {
   int tid = omp_get_thread_num( );
   omp_set_nest_lock(&my_lock);
   printf_s("Thread %d - starting nested locked region\n", tid);
   printf_s("Thread %d - ending nested locked region\n", tid);
   omp_unset_nest_lock(&my_lock);
}

int main() {
   omp_init_nest_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_nest_lock(&my_lock);
            if (i % 3)
               Test();
            omp_unset_nest_lock(&my_lock);
        }
    }

    omp_destroy_nest_lock(&my_lock);
}
```

```Output
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
```

## <a name="omp-set-dynamic"></a>omp_set_dynamic

Označuje, že počet vláken, která jsou k dispozici v nadcházejících paralelních oblastech, lze upravit za běhu.

```cpp
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Parametry

*počítává*<br/>
Hodnota, která označuje, zda počet vláken, která jsou k dispozici v nadcházejících paralelních oblastech, může být upraven modulem runtime. Pokud je nenulové, modul runtime může upravit počet vláken, pokud je nula, modul runtime nebude dynamicky upravovat počet vláken.

### <a name="remarks"></a>Poznámky

Počet vláken nikdy nebude překročit hodnotu nastavenou [omp_set_num_threads](#omp-set-num-threads) nebo [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads).

Pomocí [omp_get_dynamic](#omp-get-dynamic) můžete zobrazit aktuální nastavení `omp_set_dynamic`.

Nastavení `omp_set_dynamic` přepíše nastavení proměnné prostředí [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic) .

Další informace najdete v tématu [funkce 3.1.7 omp_set_dynamic](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Příklad

```cpp
// omp_set_dynamic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_dynamic(9);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_dynamic( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_dynamic( ));
        }
}
```

```Output
1
1
```

## <a name="omp-set-lock"></a>omp_set_lock

Blokuje spuštění vlákna, dokud není k dispozici zámek.

```cpp
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnná typu `omp_lock_t`, která byla inicializována s [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [3.2.3 omp_set_lock a omp_set_nest_lock Functions](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Příklady

Příklad použití `omp_set_lock`naleznete v tématu [omp_init_lock](#omp-init-lock) .

## <a name="omp-set-nest-lock"></a>omp_set_nest_lock

Blokuje spuštění vlákna, dokud není k dispozici zámek.

```cpp
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnná typu `omp_nest_lock_t`, která byla inicializována s [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [3.2.3 omp_set_lock a omp_set_nest_lock Functions](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Příklady

Příklad použití `omp_set_nest_lock`naleznete v tématu [omp_init_nest_lock](#omp-init-nest-lock) .

## <a name="omp-set-nested"></a>omp_set_nested

Povoluje vnořené paralelismus.

```cpp
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Parametry

*počítává*<br/>
Nenulová hodnota umožňuje vnořené paralelismus, zatímco nula zakazuje vnořené paralelismuy.

### <a name="remarks"></a>Poznámky

Vnořený paralelismus OMP lze zapnout pomocí `omp_set_nested`nebo nastavením proměnné prostředí [OMP_NESTED](openmp-environment-variables.md#omp-nested) .

Nastavení `omp_set_nested` přepíše nastavení proměnné prostředí `OMP_NESTED`.

Povolení proměnné prostředí může poškodit jiný operační program, protože počet vláken se při vnořování paralelních oblastí zvyšuje exponenciálně. Například funkce, která přepracuje šest časů s počtem vláken OMP nastavených na 4, vyžaduje 4 096 (4 až 6) vláken. S výjimkou aplikací vázaných na vstupně-výstupní operace může výkon aplikace obecně snižovat, pokud je k dispozici více vláken než procesory.

Pomocí [omp_get_nested](#omp-get-nested) můžete zobrazit aktuální nastavení `omp_set_nested`.

Další informace najdete v tématu [funkce 3.1.9 omp_set_nested](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).

### <a name="example"></a>Příklad

```cpp
// omp_set_nested.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_nested(1);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_nested( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_nested( ));
        }
}
```

```Output
1
1
```

## <a name="omp-set-num-threads"></a>omp_set_num_threads

Nastaví počet vláken v nadcházejících paralelních oblastech, pokud není přepsána klauzulí [num_threads](openmp-clauses.md#num-threads) .

```cpp
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Parametry

*num_threads*<br/>
Počet vláken v paralelní oblasti.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce 3.1.1 omp_set_num_threads](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).

### <a name="example"></a>Příklad

Příklad použití `omp_set_num_threads`naleznete v tématu [omp_get_num_threads](#omp-get-num-threads) .

## <a name="omp-test-lock"></a>omp_test_lock

Pokusí se nastavit zámek, ale neblokuje provádění vlákna.

```cpp
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnná typu `omp_lock_t`, která byla inicializována s [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce 3.2.5 omp_test_lock a omp_test_nest_lock](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

### <a name="example"></a>Příklad

```cpp
// omp_test_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t simple_lock;

int main() {
    omp_init_lock(&simple_lock);

    #pragma omp parallel num_threads(4)
    {
        int tid = omp_get_thread_num();

        while (!omp_test_lock(&simple_lock))
            printf_s("Thread %d - failed to acquire simple_lock\n",
                     tid);

        printf_s("Thread %d - acquired simple_lock\n", tid);

        printf_s("Thread %d - released simple_lock\n", tid);
        omp_unset_lock(&simple_lock);
    }

    omp_destroy_lock(&simple_lock);
}
```

```Output
Thread 1 - acquired simple_lock
Thread 1 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - acquired simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - acquired simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - released simple_lock
Thread 3 - failed to acquire simple_lock
Thread 3 - acquired simple_lock
Thread 3 - released simple_lock
```

## <a name="omp-test-nest-lock"></a>omp_test_nest_lock

Pokusí se nastavit vnořený zámek, ale neblokuje provádění vlákna.

```cpp
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnná typu `omp_nest_lock_t`, která byla inicializována s [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce 3.2.5 omp_test_lock a omp_test_nest_lock](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

### <a name="example"></a>Příklad

```cpp
// omp_test_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t nestable_lock;

int main() {
   omp_init_nest_lock(&nestable_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num();
      while (!omp_test_nest_lock(&nestable_lock))
         printf_s("Thread %d - failed to acquire nestable_lock\n",
                tid);

      printf_s("Thread %d - acquired nestable_lock\n", tid);

      if (omp_test_nest_lock(&nestable_lock)) {
         printf_s("Thread %d - acquired nestable_lock again\n",
                tid);
         printf_s("Thread %d - released nestable_lock\n",
                tid);
         omp_unset_nest_lock(&nestable_lock);
      }

      printf_s("Thread %d - released nestable_lock\n", tid);
      omp_unset_nest_lock(&nestable_lock);
   }

   omp_destroy_nest_lock(&nestable_lock);
}
```

```Output
Thread 1 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock again
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - acquired nestable_lock
Thread 2 - acquired nestable_lock again
Thread 2 - released nestable_lock
Thread 2 - released nestable_lock
```

## <a name="omp-unset-lock"></a>omp_unset_lock

Uvolní zámek.

```cpp
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnná typu `omp_lock_t`, která byla inicializována s [omp_init_lock](#omp-init-lock), vlastněna vláknem a prováděna ve funkci.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce 3.2.4 omp_unset_lock a omp_unset_nest_lock](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Příklad

Příklad použití `omp_unset_lock`naleznete v tématu [omp_init_lock](#omp-init-lock) .

## <a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

Uvolňuje vnořený zámek.

```cpp
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnná typu `omp_nest_lock_t`, která byla inicializována s [omp_init_nest_lock](#omp-init-nest-lock), vlastněna vláknem a prováděna ve funkci.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce 3.2.4 omp_unset_lock a omp_unset_nest_lock](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Příklad

Příklad použití `omp_unset_nest_lock`naleznete v tématu [omp_init_nest_lock](#omp-init-nest-lock) .
