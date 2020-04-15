---
title: OpenMP – proměnné prostředí
ms.date: 03/20/2019
f1_keywords:
- OpenMP environment variables
- OMP_DYNAMIC
- OMP_NESTED
- OMP_NUM_THREADS
- OMP_SCHEDULE
helpviewer_keywords:
- OpenMP environment variables
- OMP_DYNAMIC OpenMP environment variable
- OMP_NESTED OpenMP environment variable
- OMP_NUM_THREADS OpenMP environment variable
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
ms.openlocfilehash: bee9b0fbdf147ee962ff92d0b3b9ff57d4209f84
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363877"
---
# <a name="openmp-environment-variables"></a>OpenMP – proměnné prostředí

Obsahuje odkazy na proměnné prostředí používané v rozhraní OpenMP API.

Implementace standardu OpenMP v jazyce Visual C++ zahrnuje následující proměnné prostředí. Tyto proměnné prostředí jsou čteny při spuštění programu a změny jejich hodnot jsou ignorovány za běhu (například pomocí [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Proměnná prostředí|Popis|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Upravuje chování [klauzule schedule,](openmp-clauses.md#schedule) když `schedule(runtime)` je zadán `for` `parallel for` v nebo směrnice.|
|[OMP_NUM_THREADS](#omp-num-threads)|Nastaví maximální počet podprocesů v paralelní oblasti, pokud není přepsán [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) nebo [num_threads](openmp-clauses.md#num-threads).|
|[OMP_DYNAMIC](#omp-dynamic)|Určuje, zda může doba běhu OpenMP upravit počet vláken v paralelní oblasti.|
|[OMP_NESTED](#omp-nested)|Určuje, zda je povoleno vnořené paralelismu, pokud vnořený paralelismus není povolen nebo zakázán s `omp_set_nested`.|

## <a name="omp_dynamic"></a><a name="omp-dynamic"></a>OMP_DYNAMIC

Určuje, zda může doba běhu OpenMP upravit počet vláken v paralelní oblasti.

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Poznámky

Proměnnou `OMP_DYNAMIC` prostředí lze přepsat funkcí [omp_set_dynamic.](openmp-functions.md#omp-set-dynamic)

Výchozí hodnota v implementaci visual c++ standardu `OMP_DYNAMIC=FALSE`OpenMP je .

Další informace naleznete v [tématu 4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Příklad

Následující příkaz nastaví proměnnou prostředí na `OMP_DYNAMIC` HODNOTU PRAVDA:

```cmd
set OMP_DYNAMIC=TRUE
```

Následující příkaz zobrazuje aktuální nastavení `OMP_DYNAMIC` proměnné prostředí:

```cmd
set OMP_DYNAMIC
```

## <a name="omp_nested"></a><a name="omp-nested"></a>OMP_NESTED

Určuje, zda je povoleno vnořené paralelismu, pokud vnořený paralelismus není povolen nebo zakázán s `omp_set_nested`.

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Poznámky

Proměnnou `OMP_NESTED` prostředí lze přepsat funkcí [omp_set_nested.](openmp-functions.md#omp-set-nested)

Výchozí hodnota v implementaci visual c++ standardu `OMP_DYNAMIC=FALSE`OpenMP je .

Další informace naleznete v tématu [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Příklad

Následující příkaz nastaví proměnnou prostředí na `OMP_NESTED` HODNOTU PRAVDA:

```cmd
set OMP_NESTED=TRUE
```

Následující příkaz zobrazuje aktuální nastavení `OMP_NESTED` proměnné prostředí:

```cmd
set OMP_NESTED
```

## <a name="omp_num_threads"></a><a name="omp-num-threads"></a>OMP_NUM_THREADS

Nastaví maximální počet podprocesů v paralelní oblasti, pokud není přepsán [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) nebo [num_threads](openmp-clauses.md#num-threads).

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Parametry

*num*<br/>
Maximální počet podprocesů, které chcete v paralelní oblasti, až 64 v implementaci Visual C++.

### <a name="remarks"></a>Poznámky

Proměnnou `OMP_NUM_THREADS` prostředí lze přepsat funkcí [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) nebo [num_threads](openmp-clauses.md#num-threads).

Výchozí hodnota `num` v implementaci visual c++ standardu OpenMP je počet virtuálních procesorů, včetně procesorů hyperthreading.

Další informace naleznete v [tématu 4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Příklad

Následující příkaz nastaví proměnnou `OMP_NUM_THREADS` prostředí na `16`:

```cmd
set OMP_NUM_THREADS=16
```

Následující příkaz zobrazuje aktuální nastavení `OMP_NUM_THREADS` proměnné prostředí:

```cmd
set OMP_NUM_THREADS
```

## <a name="omp_schedule"></a><a name="omp-schedule"></a>OMP_SCHEDULE

Upravuje chování [klauzule schedule,](openmp-clauses.md#schedule) když `schedule(runtime)` je zadán `for` `parallel for` v nebo směrnice.

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
(Nepovinné) Určuje velikost iterací. *velikost* musí být kladné celé číslo. Výchozí hodnota `1`je , s výjimkou případů, kdy je *typ* statický. Neplatí, *type* pokud `runtime`je typ .

*Typ*<br/>
Druh `dynamic`plánování , , `guided` `runtime`, `static`nebo .

### <a name="remarks"></a>Poznámky

Výchozí hodnota v implementaci visual c++ standardu `OMP_SCHEDULE=static,0`OpenMP je .

Další informace naleznete v [tématu 4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Příklad

Následující příkaz nastavuje proměnnou `OMP_SCHEDULE` prostředí:

```cmd
set OMP_SCHEDULE="guided,2"
```

Následující příkaz zobrazuje aktuální nastavení `OMP_SCHEDULE` proměnné prostředí:

```cmd
set OMP_SCHEDULE
```
