---
title: Funkce jazyka OpenMP | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/23/2018
ms.technology:
- cpp-parallel
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de3ea54a1526e7b340f804a21d990b6a691d0eee
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066419"
---
# <a name="openmp-functions"></a>Funkce jazyka OpenMP

Obsahuje odkazy na funkcí používaných v rozhraní API OpenMP.

Implementace jazyka Visual C++, OpenMP standard zahrnuje následující funkce.

|Funkce|Popis|
|--------|-----------|
|[omp_destroy_lock](#omp-destroy-lock)|Zruší inicializaci zámek.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Zruší inicializaci, vnořitelných zámek.|
|[omp_get_dynamic](#omp-get-dynamic)|Vrátí hodnotu určující, pokud počet vláken v nadcházející paralelních oblastí je upravit podle času spuštění.|
|[omp_get_max_threads](#omp-get-max-threads)|Vrátí celé číslo, které je roven nebo větší než počet vláken, která bude k dispozici, pokud paralelní oblasti bez [num_threads](openmp-clauses.md#num-threads) nebyly definované v tomto bodě v kódu.|
|[omp_get_nested](#omp-get-nested)|Vrátí hodnotu, která označuje, zda je povoleno vnořené paralelismu.|
|[omp_get_num_procs](#omp-get-num-procs)|Vrátí počet procesorů, které jsou k dispozici, když je tato funkce volána.|
|[omp_get_num_threads](#omp-get-num-threads)|Vrátí počet vláken v paralelní oblasti.|
|[omp_get_thread_num](#omp-get-thread-num)|Vrátí počet vláken vlákno provádění v rámci týmu jeho vlákna.|
|[omp_get_wtick](#omp-get-wtick)|Vrátí počet sekund mezi cykly hodin procesoru.|
|[omp_get_wtime](#omp-get-wtime)|Vrátí že hodnotu v sekundách času uplynulo v určitém okamžiku.|
|[omp_in_parallel](#omp-in-parallel)|Vrátí nenulovou hodnotu, je-li volat v rámci paralelní oblasti.|
|[omp_init_lock](#omp-init-lock)|Inicializuje jednoduchým zámkem.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Inicializuje zámek.|
|[omp_set_dynamic](#omp-set-dynamic)|Označuje, že počet vláken v nadcházející paralelních oblastí je upravit podle času spuštění.|
|[omp_set_lock](#omp-set-lock)|Bloky spouštění vlákna, dokud se zámek je k dispozici.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Bloky spouštění vlákna, dokud se zámek je k dispozici.|
|[omp_set_nested](#omp-set-nested)|Povolí vnořená paralelismu.|
|[omp_set_num_threads](#omp-set-num-threads)|Nastaví počet vláken v nadcházející paralelních oblastí, pokud nejsou přepsány [num_threads](openmp-clauses.md#num-threads) klauzuli.|
|[omp_test_lock](#omp-test-lock)|Pokusí se nastavit zámek, ale nebude blokovat spouštění vlákna.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Pokusí se nastavit, vnořitelných zámek, ale nebude blokovat spouštění vlákna.|
|[omp_unset_lock](#omp-unset-lock)|Uvolní zámek.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Uvolní, vnořitelných zámek.|

## <a name="omp-destroy-lock"></a>omp_destroy_lock

Zruší inicializaci zámek.

```
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnné typu [omp_lock_t](openmp-data-types.md#omp-lock-t) , který byl inicializován s [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.2.2 omp_destroy_lock a omp_destroy_nest_lock – funkce](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Příklad

Zobrazit [omp_init_lock](#omp-init-lock) pro příklad použití `omp_destroy_lock`.

## <a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock –

Zruší inicializaci, vnořitelných zámek.

```
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnné typu [omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t) , který byl inicializován s [omp_init_nest_lock –](#omp-init-nest-lock).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.2.2 omp_destroy_lock a omp_destroy_nest_lock – funkce](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Příklad

Zobrazit [omp_init_nest_lock –](#omp-init-nest-lock) pro příklad použití `omp_destroy_nest_lock`.

## <a name="omp-get-dynamic"></a>omp_get_dynamic –

Vrátí hodnotu určující, pokud počet vláken v nadcházející paralelních oblastí je upravit podle času spuštění.

```
int omp_get_dynamic();
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu znamená, že dynamicky upraví vlákna.

### <a name="remarks"></a>Poznámky

Dynamické přizpůsobení vláken není zadán s [omp_set_dynamic –](#omp-set-dynamic) a [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic).

Další informace najdete v tématu [3.1.7 omp_set_dynamic – funkce](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Příklad

Zobrazit [omp_set_dynamic –](#omp-set-dynamic) pro příklad použití `omp_get_dynamic`.

## <a name="omp-get-max-threads"></a>omp_get_max_threads –

Vrátí celé číslo, které je roven nebo větší než počet vláken, která bude k dispozici, pokud paralelní oblasti bez [num_threads](openmp-clauses.md#num-threads) nebyly definované v tomto bodě v kódu.

```
int omp_get_max_threads( )
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.1.3 omp_get_max_threads – funkce](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md).

### <a name="example"></a>Příklad

```
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

## <a name="omp-get-nested"></a>omp_get_nested –

Vrátí hodnotu, která označuje, zda je povoleno vnořené paralelismu.

```
int omp_get_nested( );
```

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota znamená, že je povolená vnořené paralelismu.

### <a name="remarks"></a>Poznámky

Vnořené paralelismu zadán s parametrem [omp_set_nested –](#omp-set-nested) a [OMP_NESTED](openmp-environment-variables.md#omp-nested).

Další informace najdete v tématu [3.1.10 omp_get_nested – funkce](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

### <a name="example"></a>Příklad

Zobrazit [omp_set_nested –](#omp-set-nested) pro příklad použití `omp_get_nested`.

## <a name="omp-get-num-procs"></a>omp_get_num_procs –

Vrátí počet procesorů, které jsou k dispozici, když je tato funkce volána.

```
int omp_get_num_procs();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.1.5 omp_get_num_procs – funkce](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).

### <a name="example"></a>Příklad

```
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

```
int omp_get_num_threads( );
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.1.2 omp_get_num_threads – funkce](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md).

### <a name="example"></a>Příklad

```
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

## <a name="omp-get-thread-num"></a>omp_get_thread_num –

Vrátí počet vláken vlákno provádění v rámci týmu jeho vlákna.

```
int omp_get_thread_num( );
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.1.4 omp_get_thread_num – funkce](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md).

### <a name="example"></a>Příklad

Zobrazit [paralelní](openmp-directives.md#parallel) pro příklad použití `omp_get_thread_num`.

## <a name="omp-get-wtick"></a>omp_get_wtick –

Vrátí počet sekund mezi cykly hodin procesoru.

```
double omp_get_wtick( );
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.3.2 omp_get_wtick – funkce](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md).

### <a name="example"></a>Příklad

Zobrazit [omp_get_wtime](#omp-get-wtime) pro příklad použití `omp_get_wtick`.

## <a name="omp-get-wtime"></a>omp_get_wtime

Vrátí že hodnotu v sekundách času uplynulo v určitém okamžiku.

```
double omp_get_wtime( );
```

### <a name="return-value"></a>Návratová hodnota

Vrátí že hodnotu v sekundách času uplynulo z některé libovolného, ale konzistentního bodu.

### <a name="remarks"></a>Poznámky

Při provádění programu, umožňující nadcházející porovnání zůstane tento bod konzistentní vzhledem k aplikacím.

Další informace najdete v tématu [3.3.1 omp_get_wtime – funkce](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md).

### <a name="example"></a>Příklad

```
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

Vrátí nenulovou hodnotu, je-li volat v rámci paralelní oblasti.

```
int omp_in_parallel( );
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.1.6 omp_in_parallel – funkce](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md).

### <a name="example"></a>Příklad

```
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

Inicializuje jednoduchým zámkem.

```
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnné typu [omp_lock_t](openmp-data-types.md#omp-lock-t).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.2.1 omp_init_lock a omp_init_nest_lock – funkce](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

### <a name="example"></a>Příklad

```
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

## <a name="omp-init-nest-lock"></a>omp_init_nest_lock –

Inicializuje zámek.

```
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnné typu [omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t).

### <a name="remarks"></a>Poznámky

Počáteční počet vnoření je nula.

Další informace najdete v tématu [3.2.1 omp_init_lock a omp_init_nest_lock – funkce](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

### <a name="example"></a>Příklad

```
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

## <a name="omp-set-dynamic"></a>omp_set_dynamic –

Označuje, že počet vláken v nadcházející paralelních oblastí je upravit podle času spuštění.

```
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Hodnota označující, pokud je možné upravit počet vláken v nadcházející paralelních oblastí modulem runtime.  Pokud nenulovou hodnotu, že modul runtime můžete upravit počet vláken, pokud je nula, modul runtime nebude dynamicky upravit počet vláken.

### <a name="remarks"></a>Poznámky

Počet vláken se nikdy nepřekročí hodnotu nastavenou [omp_set_num_threads –](#omp-set-num-threads) nebo [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads).

Použití [omp_get_dynamic –](#omp-get-dynamic) zobrazíte aktuální nastavení `omp_set_dynamic`.

Nastavení pro `omp_set_dynamic` přepíše nastavení jazyka [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic) proměnné prostředí.

Další informace najdete v tématu [3.1.7 omp_set_dynamic – funkce](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Příklad

```
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

Bloky spouštění vlákna, dokud se zámek je k dispozici.

```
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnné typu [omp_lock_t](openmp-data-types.md#omp-lock-t) , který byl inicializován s [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.2.3 omp_set_lock a omp_set_nest_lock – funkce](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Příklady

Zobrazit [omp_init_lock](#omp-init-lock) pro příklad použití `omp_set_lock`.

## <a name="omp-set-nest-lock"></a>omp_set_nest_lock –

Bloky spouštění vlákna, dokud se zámek je k dispozici.

```
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnné typu [omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t) , který byl inicializován s [omp_init_nest_lock –](#omp-init-nest-lock).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.2.3 omp_set_lock a omp_set_nest_lock – funkce](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Příklady

Zobrazit [omp_init_nest_lock –](#omp-init-nest-lock) pro příklad použití `omp_set_nest_lock`.

## <a name="omp-set-nested"></a>omp_set_nested –

Povolí vnořená paralelismu.

```
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Nenulová hodnota aktivuje vnořené paralelismu, nula zakazuje vnořené paralelismu.

### <a name="remarks"></a>Poznámky

OMP vnořené paralelismu, lze zapnout pomocí `omp_set_nested`, nebo nastavením [OMP_NESTED](openmp-environment-variables.md#omp-nested) proměnné prostředí.

Nastavení pro `omp_set_nested` přepíše nastavení jazyka `OMP_NESTED` proměnné prostředí.

Povolení proměnné prostředí můžete přerušit jinak provozní program, protože počet vláken zvyšuje exponenciálně při vnoření paralelních oblastí.  Například funkce, která recurses šestkrát s počtem vláken OMP nastavena na 4 vyžaduje 4 096 (4 k elektrické energie 6) vlákna. S výjimkou s aplikacemi vstupně-výstupní výkon aplikace obecně sníží, přetrénujte Pokud existují další vlákna než procesory.

Použití [omp_get_nested –](#omp-get-nested) zobrazíte aktuální nastavení `omp_set_nested`.

Další informace najdete v tématu [3.1.9 omp_set_nested – funkce](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).

### <a name="example"></a>Příklad

```
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

## <a name="omp-set-num-threads"></a>omp_set_num_threads –

Nastaví počet vláken v nadcházející paralelních oblastí, pokud nejsou přepsány [num_threads](openmp-clauses.md#num-threads) klauzuli.

```
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Parametry

*num_threads*<br/>
Počet vláken v paralelní oblasti.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.1.1 omp_set_num_threads – funkce](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).

### <a name="example"></a>Příklad

Zobrazit [omp_get_num_threads](#omp-get-num-threads) pro příklad použití `omp_set_num_threads`.

## <a name="omp-test-lock"></a>omp_test_lock

Pokusí se nastavit zámek, ale nebude blokovat spouštění vlákna.

```
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnné typu [omp_lock_t](openmp-data-types.md#omp-lock-t) , který byl inicializován s [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.2.5 omp_test_lock a omp_test_nest_lock – funkce](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

### <a name="example"></a>Příklad

```
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

## <a name="omp-test-nest-lock"></a>omp_test_nest_lock –

Pokusí se nastavit, vnořitelných zámek, ale nebude blokovat spouštění vlákna.

```
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnné typu [omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t) , který byl inicializován s [omp_init_nest_lock –](#omp-init-nest-lock).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.2.5 omp_test_lock a omp_test_nest_lock – funkce](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

### <a name="example"></a>Příklad

```
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

```
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnné typu [omp_lock_t](openmp-data-types.md#omp-lock-t) , který byl inicializován s [omp_init_lock](#omp-init-lock)vlastněné uživatelem vlákna a provádění ve funkci.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.2.4 omp_unset_lock a omp_unset_nest_lock – funkce](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Příklad

Zobrazit [omp_init_lock](#omp-init-lock) pro příklad použití `omp_unset_lock`.

## <a name="omp-unset-nest-lock"></a>omp_unset_nest_lock –

Uvolní, vnořitelných zámek.

```
void omp_unset_nest_lock( 
   omp_nest_lock_t *lock 
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnné typu [omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t) , který byl inicializován s [omp_init_nest_lock –](#omp-init-nest-lock)vlastněné uživatelem vlákna a provádění ve funkci.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.2.4 omp_unset_lock a omp_unset_nest_lock – funkce](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Příklad

Zobrazit [omp_init_nest_lock –](#omp-init-nest-lock) pro příklad použití `omp_unset_nest_lock`.
