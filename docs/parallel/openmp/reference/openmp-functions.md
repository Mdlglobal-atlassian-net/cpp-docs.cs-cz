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
ms.openlocfilehash: 0475a83ba259ed00bbcb9ddaba99a1556b35f613
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317139"
---
# <a name="openmp-functions"></a>Funkce jazyka OpenMP

Obsahuje odkazy na funkce používané v rozhraní OpenMP API.

Implementace standardu OpenMP v jazyce Visual C++ zahrnuje následující funkce a datové typy.

Pro spuštění prostředí:

|Funkce|Popis|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|Nastaví počet podprocesů v nadcházejících paralelních oblastech, pokud není [přepsána klauzulí num_threads.](openmp-clauses.md#num-threads)|
|[omp_get_num_threads](#omp-get-num-threads)|Vrátí počet podprocesů v paralelní oblasti.|
|[omp_get_max_threads](#omp-get-max-threads)|Vrátí celé číslo, které je stejné nebo větší než počet podprocesů, které by byly k dispozici, pokud paralelní oblast bez [num_threads](openmp-clauses.md#num-threads) byly definovány v tomto bodě v kódu.|
|[omp_get_thread_num](#omp-get-thread-num)|Vrátí číslo vlákna podprocesu provádění v rámci svého týmu podprocesu.|
|[omp_get_num_procs](#omp-get-num-procs)|Vrátí počet procesorů, které jsou k dispozici při volání funkce.|
|[omp_in_parallel](#omp-in-parallel)|Vrátí nenulovou, pokud je volána z paralelní oblasti.|
|[omp_set_dynamic](#omp-set-dynamic)|Označuje, že počet vláken, které jsou k dispozici v nadcházejících paralelních oblastech, lze upravit podle doby spuštění.|
|[omp_get_dynamic](#omp-get-dynamic)|Vrátí hodnotu, která označuje, zda počet vláken, které jsou k dispozici v nadcházejících paralelních oblastech, lze upravit podle doby běhu.|
|[omp_set_nested](#omp-set-nested)|Umožňuje vnořený paralelismus.|
|[omp_get_nested](#omp-get-nested)|Vrátí hodnotu, která označuje, zda je povolen vnořený paralelismus.|

Pro zámek:

|Funkce|Popis|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|Inicializuje jednoduchý zámek.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Inicializuje zámek.|
|[omp_destroy_lock](#omp-destroy-lock)|Uninitializes zámek.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Uninitializes nestabilní zámek.|
|[omp_set_lock](#omp-set-lock)|Blokuje provádění podprocesu, dokud není k dispozici zámek.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Blokuje provádění podprocesu, dokud není k dispozici zámek.|
|[omp_unset_lock](#omp-unset-lock)|Uvolní zámek.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Uvolní nestabilní zámek.|
|[omp_test_lock](#omp-test-lock)|Pokusí se nastavit zámek, ale neblokuje spuštění vlákna.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Pokusí se nastavit zámek nestable, ale neblokuje spuštění podprocesu.|

|Datový typ|Popis|
|---------|-----------|
|`omp_lock_t`|Typ, který má stav zámku, zda je zámek k dispozici nebo zda vlákno vlastní zámek.|
|`omp_nest_lock_t`|Typ, který obsahuje jednu z následujících částí informace o zámku: zda zámek je k dispozici a identity podprocesu, který vlastní zámek a počet vnoření.|

Pro časovací rutiny:

|Funkce|Popis|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|Vrátí hodnotu v sekundách doby, která uplynula od určitého bodu.|
|[omp_get_wtick](#omp-get-wtick)|Vrátí počet sekund mezi tiky hodin procesoru.|

## <a name="omp_destroy_lock"></a><a name="omp-destroy-lock"></a>omp_destroy_lock

Uninitializes zámek.

```cpp
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Proměnná typu, `omp_lock_t` která byla inicializována pomocí [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu 3.2.2 omp_destroy_lock a omp_destroy_nest_lock funkce](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Příklad

Příklad [omp_init_lock](#omp-init-lock) použití `omp_destroy_lock`naleznete omp_init_lock .

## <a name="omp_destroy_nest_lock"></a><a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

Uninitializes nestabilní zámek.

```cpp
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Proměnná typu, `omp_nest_lock_t` která byla inicializována pomocí [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu 3.2.2 omp_destroy_lock a omp_destroy_nest_lock funkce](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Příklad

Příklad použití `omp_destroy_nest_lock` [aplikace naleznete omp_init_nest_lock.](#omp-init-nest-lock)

## <a name="omp_get_dynamic"></a><a name="omp-get-dynamic"></a>omp_get_dynamic

Vrátí hodnotu, která označuje, zda počet vláken, které jsou k dispozici v nadcházejících paralelních oblastech, lze upravit podle doby běhu.

```cpp
int omp_get_dynamic();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota znamená, že vlákna budou dynamicky upravena.

### <a name="remarks"></a>Poznámky

Dynamické nastavení závitů je specifikováno [omp_set_dynamic](#omp-set-dynamic) a [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic).

Další informace naleznete v tématu [3.1.7 omp_set_dynamic funkce](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Příklad

Příklad [omp_set_dynamic](#omp-set-dynamic) použití `omp_get_dynamic`naleznete omp_set_dynamic .

## <a name="omp_get_max_threads"></a><a name="omp-get-max-threads"></a>omp_get_max_threads

Vrátí celé číslo, které je stejné nebo větší než počet podprocesů, které by byly k dispozici, pokud paralelní oblast bez [num_threads](openmp-clauses.md#num-threads) byly definovány v tomto bodě v kódu.

```cpp
int omp_get_max_threads( )
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [3.1.3 omp_get_max_threads funkce](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md).

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

## <a name="omp_get_nested"></a><a name="omp-get-nested"></a>omp_get_nested

Vrátí hodnotu, která označuje, zda je povolen vnořený paralelismus.

```cpp
int omp_get_nested( );
```

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota znamená, že je povolen vnořený paralelismus.

### <a name="remarks"></a>Poznámky

Vnořený paralelismus je určen s [omp_set_nested](#omp-set-nested) a [OMP_NESTED](openmp-environment-variables.md#omp-nested).

Další informace naleznete v tématu [3.1.10 omp_get_nested funkce](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

### <a name="example"></a>Příklad

Příklad [omp_set_nested](#omp-set-nested) použití `omp_get_nested`naleznete omp_set_nested .

## <a name="omp_get_num_procs"></a><a name="omp-get-num-procs"></a>omp_get_num_procs

Vrátí počet procesorů, které jsou k dispozici při volání funkce.

```cpp
int omp_get_num_procs();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [3.1.5 omp_get_num_procs funkce](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).

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

## <a name="omp_get_num_threads"></a><a name="omp-get-num-threads"></a>omp_get_num_threads

Vrátí počet podprocesů v paralelní oblasti.

```cpp
int omp_get_num_threads( );
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [3.1.2 omp_get_num_threads funkce](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md).

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

## <a name="omp_get_thread_num"></a><a name="omp-get-thread-num"></a>omp_get_thread_num

Vrátí číslo vlákna podprocesu provádění v rámci svého týmu podprocesu.

```cpp
int omp_get_thread_num( );
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [3.1.4 omp_get_thread_num funkce](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md).

### <a name="example"></a>Příklad

Viz [paralelní](openmp-directives.md#parallel) příklad použití `omp_get_thread_num`.

## <a name="omp_get_wtick"></a><a name="omp-get-wtick"></a>omp_get_wtick

Vrátí počet sekund mezi tiky hodin procesoru.

```cpp
double omp_get_wtick( );
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [3.3.2 omp_get_wtick funkce](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md).

### <a name="example"></a>Příklad

Příklad [omp_get_wtime](#omp-get-wtime) použití `omp_get_wtick`naleznete omp_get_wtime .

## <a name="omp_get_wtime"></a><a name="omp-get-wtime"></a>omp_get_wtime

Vrátí hodnotu v sekundách doby, která uplynula od určitého bodu.

```cpp
double omp_get_wtime( );
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu v sekundách času, který uplynul od některé libovolné, ale konzistentní bod.

### <a name="remarks"></a>Poznámky

Tento bod zůstane konzistentní během provádění programu, takže nadcházející porovnání možné.

Další informace naleznete v tématu [3.3.1 omp_get_wtime funkce](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md).

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

## <a name="omp_in_parallel"></a><a name="omp-in-parallel"></a>omp_in_parallel

Vrátí nenulovou, pokud je volána z paralelní oblasti.

```cpp
int omp_in_parallel( );
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [3.1.6 omp_in_parallel funkce](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md).

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

## <a name="omp_init_lock"></a><a name="omp-init-lock"></a>omp_init_lock

Inicializuje jednoduchý zámek.

```cpp
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Proměnná typu `omp_lock_t`.

### <a name="remarks"></a>Poznámky

Další informace naleznete v [omp_init_lock a omp_init_nest_lock funkcích 3.2.1](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

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

## <a name="omp_init_nest_lock"></a><a name="omp-init-nest-lock"></a>omp_init_nest_lock

Inicializuje zámek.

```cpp
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Proměnná typu `omp_nest_lock_t`.

### <a name="remarks"></a>Poznámky

Počáteční počet vnoření je nula.

Další informace naleznete v [omp_init_lock a omp_init_nest_lock funkcích 3.2.1](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

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

## <a name="omp_set_dynamic"></a><a name="omp-set-dynamic"></a>omp_set_dynamic

Označuje, že počet vláken, které jsou k dispozici v nadcházejících paralelních oblastech, lze upravit podle doby spuštění.

```cpp
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Hodnota, která označuje, zda počet podprocesů, které jsou k dispozici v nadcházejících paralelních oblastech, lze upravit pomocí běhu. Pokud je nenulová, může za běhu upravit počet podprocesů, pokud je nula, runtime dynamicky neupraví počet vláken.

### <a name="remarks"></a>Poznámky

Počet vláken nikdy nepřekročí hodnotu nastavenou [omp_set_num_threads](#omp-set-num-threads) nebo [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads).

Pomocí [omp_get_dynamic](#omp-get-dynamic) můžete zobrazit `omp_set_dynamic`aktuální nastavení .

Nastavení pro `omp_set_dynamic` přepíše nastavení [proměnné prostředí OMP_DYNAMIC.](openmp-environment-variables.md#omp-dynamic)

Další informace naleznete v tématu [3.1.7 omp_set_dynamic funkce](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

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

## <a name="omp_set_lock"></a><a name="omp-set-lock"></a>omp_set_lock

Blokuje provádění podprocesu, dokud není k dispozici zámek.

```cpp
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Proměnná typu, `omp_lock_t` která byla inicializována pomocí [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu 3.2.3 omp_set_lock a omp_set_nest_lock funkce](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Příklady

Příklad [omp_init_lock](#omp-init-lock) použití `omp_set_lock`naleznete omp_init_lock .

## <a name="omp_set_nest_lock"></a><a name="omp-set-nest-lock"></a>omp_set_nest_lock

Blokuje provádění podprocesu, dokud není k dispozici zámek.

```cpp
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Proměnná typu, `omp_nest_lock_t` která byla inicializována pomocí [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu 3.2.3 omp_set_lock a omp_set_nest_lock funkce](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Příklady

Příklad použití `omp_set_nest_lock` [aplikace naleznete omp_init_nest_lock.](#omp-init-nest-lock)

## <a name="omp_set_nested"></a><a name="omp-set-nested"></a>omp_set_nested

Umožňuje vnořený paralelismus.

```cpp
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Nenulová hodnota umožňuje vnořený paralelismus, zatímco nula zakáže vnořený paralelismus.

### <a name="remarks"></a>Poznámky

Vnořený paralelismus OMP lze `omp_set_nested`zapnout pomocí , nebo nastavením proměnné [prostředí OMP_NESTED.](openmp-environment-variables.md#omp-nested)

Nastavení pro `omp_set_nested` přepíše nastavení proměnné `OMP_NESTED` prostředí.

Povolení proměnné prostředí může přerušit jinak operační program, protože počet vláken se exponenciálně zvyšuje při vnoření paralelních oblastí. Například funkce, která recurses šestkrát s počtem podprocesů OMP nastavena na 4 vyžaduje 4 096 (4 k výkonu 6) podprocesů. S výjimkou aplikací vázaných na vstupně-výstupní chod se výkon aplikace obecně snižuje, pokud existuje více vláken než procesorů.

Pomocí [omp_get_nested](#omp-get-nested) můžete zobrazit `omp_set_nested`aktuální nastavení .

Další informace naleznete v tématu [3.1.9 omp_set_nested funkce](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).

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

## <a name="omp_set_num_threads"></a><a name="omp-set-num-threads"></a>omp_set_num_threads

Nastaví počet podprocesů v nadcházejících paralelních oblastech, pokud není [přepsána klauzulí num_threads.](openmp-clauses.md#num-threads)

```cpp
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Parametry

*num_threads*<br/>
Počet podprocesů v paralelní oblasti.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [3.1.1 omp_set_num_threads funkce](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).

### <a name="example"></a>Příklad

Příklad použití `omp_set_num_threads` [aplikace naleznete omp_get_num_threads.](#omp-get-num-threads)

## <a name="omp_test_lock"></a><a name="omp-test-lock"></a>omp_test_lock

Pokusí se nastavit zámek, ale neblokuje spuštění vlákna.

```cpp
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Proměnná typu, `omp_lock_t` která byla inicializována pomocí [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu 3.2.5 omp_test_lock a omp_test_nest_lock funkce](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

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

## <a name="omp_test_nest_lock"></a><a name="omp-test-nest-lock"></a>omp_test_nest_lock

Pokusí se nastavit zámek nestable, ale neblokuje spuštění podprocesu.

```cpp
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Proměnná typu, `omp_nest_lock_t` která byla inicializována pomocí [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu 3.2.5 omp_test_lock a omp_test_nest_lock funkce](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

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

## <a name="omp_unset_lock"></a><a name="omp-unset-lock"></a>omp_unset_lock

Uvolní zámek.

```cpp
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Proměnná typu, `omp_lock_t` která byla inicializována [pomocí omp_init_lock](#omp-init-lock), vlastněná podprocesem a provádění ve funkci.

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu 3.2.4 omp_unset_lock a omp_unset_nest_lock funkce](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Příklad

Příklad [omp_init_lock](#omp-init-lock) použití `omp_unset_lock`naleznete omp_init_lock .

## <a name="omp_unset_nest_lock"></a><a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

Uvolní nestabilní zámek.

```cpp
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*Zámek*<br/>
Proměnná typu, `omp_nest_lock_t` která byla inicializována s [omp_init_nest_lock](#omp-init-nest-lock), vlastněná podprocesem a provádění ve funkci.

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu 3.2.4 omp_unset_lock a omp_unset_nest_lock funkce](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Příklad

Příklad použití `omp_unset_nest_lock` [aplikace naleznete omp_init_nest_lock.](#omp-init-nest-lock)
