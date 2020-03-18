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
ms.openlocfilehash: 838427320fcb68cedb97b36156fc18002ed962d8
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417003"
---
# <a name="openmp-environment-variables"></a>OpenMP – proměnné prostředí

Obsahuje odkazy na proměnné prostředí používané v rozhraní OpenMP API.

Visual C++ implementace standardu OpenMP zahrnuje následující proměnné prostředí. Tyto proměnné prostředí jsou čteny při spuštění programu a změny jejich hodnot jsou ignorovány za běhu (například pomocí [_putenv _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Proměnná prostředí|Popis|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Upraví chování klauzule [Schedule](openmp-clauses.md#schedule) , pokud je `schedule(runtime)` zadáno v direktivě `for` nebo `parallel for`.|
|[OMP_NUM_THREADS](#omp-num-threads)|Nastaví maximální počet vláken v paralelní oblasti, pokud není přepsána [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) nebo [num_threads](openmp-clauses.md#num-threads).|
|[OMP_DYNAMIC](#omp-dynamic)|Určuje, zda může doba běhu OpenMP upravit počet vláken v paralelní oblasti.|
|[OMP_NESTED](#omp-nested)|Určuje, jestli je povolený vnořený paralelismu, pokud není povolený nebo zakázaný vnořený paralelismu s `omp_set_nested`.|

## <a name="omp-dynamic"></a>OMP_DYNAMIC

Určuje, zda může doba běhu OpenMP upravit počet vláken v paralelní oblasti.

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Poznámky

Proměnnou prostředí `OMP_DYNAMIC` lze přepsat funkcí [omp_set_dynamic](openmp-functions.md#omp-set-dynamic) .

Výchozí hodnota v rámci Visual C++ implementace Standard OpenMP je `OMP_DYNAMIC=FALSE`.

Další informace najdete v tématu [4,3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Příklad

Následující příkaz nastaví proměnnou prostředí `OMP_DYNAMIC` na hodnotu TRUE:

```cmd
set OMP_DYNAMIC=TRUE
```

Následující příkaz zobrazí aktuální nastavení proměnné prostředí `OMP_DYNAMIC`:

```cmd
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

Určuje, jestli je povolený vnořený paralelismu, pokud není povolený nebo zakázaný vnořený paralelismu s `omp_set_nested`.

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Poznámky

Proměnnou prostředí `OMP_NESTED` lze přepsat funkcí [omp_set_nested](openmp-functions.md#omp-set-nested) .

Výchozí hodnota v rámci Visual C++ implementace Standard OpenMP je `OMP_DYNAMIC=FALSE`.

Další informace najdete v tématu [4,4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Příklad

Následující příkaz nastaví proměnnou prostředí `OMP_NESTED` na hodnotu TRUE:

```cmd
set OMP_NESTED=TRUE
```

Následující příkaz zobrazí aktuální nastavení proměnné prostředí `OMP_NESTED`:

```cmd
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

Nastaví maximální počet vláken v paralelní oblasti, pokud není přepsána [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) nebo [num_threads](openmp-clauses.md#num-threads).

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Parametry

*počet*<br/>
Maximální počet vláken, která chcete v paralelní oblasti, až 64 v rámci Visual C++ implementace.

### <a name="remarks"></a>Poznámky

Proměnnou prostředí `OMP_NUM_THREADS` lze přepsat funkcí [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) nebo [num_threads](openmp-clauses.md#num-threads).

Výchozí hodnota `num` v rámci Visual C++ implementace Standard OpenMP je počet virtuálních procesorů, včetně procesorů s vlákny.

Další informace najdete v tématu [4,2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Příklad

Následující příkaz nastaví proměnnou prostředí `OMP_NUM_THREADS` na `16`:

```cmd
set OMP_NUM_THREADS=16
```

Následující příkaz zobrazí aktuální nastavení proměnné prostředí `OMP_NUM_THREADS`:

```cmd
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

Upraví chování klauzule [Schedule](openmp-clauses.md#schedule) , pokud je `schedule(runtime)` zadáno v direktivě `for` nebo `parallel for`.

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Volitelné Určuje velikost iterací. *Velikost* musí být kladné celé číslo. Výchozí hodnota je `1`s výjimkou případu, kdy je *typ* statický. Neplatný, pokud je *typ* `runtime`.

*type*<br/>
Typ plánování, buď `dynamic`, `guided`, `runtime`nebo `static`.

### <a name="remarks"></a>Poznámky

Výchozí hodnota v rámci Visual C++ implementace Standard OpenMP je `OMP_SCHEDULE=static,0`.

Další informace najdete v tématu [4,1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Příklad

Následující příkaz nastaví proměnnou prostředí `OMP_SCHEDULE`:

```cmd
set OMP_SCHEDULE="guided,2"
```

Následující příkaz zobrazí aktuální nastavení proměnné prostředí `OMP_SCHEDULE`:

```cmd
set OMP_SCHEDULE
```
