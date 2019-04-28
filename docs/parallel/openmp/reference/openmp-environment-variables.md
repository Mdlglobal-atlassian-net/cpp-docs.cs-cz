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
ms.openlocfilehash: 73fb11db14df22e5df95fdec556ccdfc16a935e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362631"
---
# <a name="openmp-environment-variables"></a>OpenMP – proměnné prostředí

Obsahuje odkazy na proměnné prostředí použít v rozhraní API OpenMP.

Implementace jazyka Visual C++, OpenMP standard zahrnuje následující proměnné prostředí. Tyto proměnné prostředí jsou načteny při spuštění programu a změny jejich hodnoty jsou ignorovány za běhu (například pomocí [_putenv _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Proměnná prostředí|Popis|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Upravuje chování [plán](openmp-clauses.md#schedule) klauzule při `schedule(runtime)` je zadán v `for` nebo `parallel for` – direktiva.|
|[OMP_NUM_THREADS](#omp-num-threads)|Nastaví maximální počet vláken v paralelní oblasti, pokud není přepsán [omp_set_num_threads –](openmp-functions.md#omp-set-num-threads) nebo [num_threads](openmp-clauses.md#num-threads).|
|[OMP_DYNAMIC](#omp-dynamic)|Určuje, zda OpenMP běhu můžete upravit počet vláken v paralelní oblasti.|
|[OMP_NESTED](#omp-nested)|Určuje, zda je vnořené paralelismu povoleno, není-li povolit nebo zakázat pomocí vnořených paralelismu `omp_set_nested`.|

## <a name="omp-dynamic"></a>OMP_DYNAMIC

Určuje, zda OpenMP běhu můžete upravit počet vláken v paralelní oblasti.

```
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Poznámky

`OMP_DYNAMIC` Proměnné prostředí můžete přepsat [omp_set_dynamic –](openmp-functions.md#omp-set-dynamic) funkce.

Je výchozí hodnotu v implementaci Visual C++ OpenMP standard `OMP_DYNAMIC=FALSE`.

Další informace najdete v tématu [4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Příklad

Nastaví zadáním následujícího příkazu `OMP_DYNAMIC` proměnné prostředí na hodnotu TRUE:

```
set OMP_DYNAMIC=TRUE
```

Následující příkaz zobrazí aktuální nastavení `OMP_DYNAMIC` proměnné prostředí:

```
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

Určuje, zda je vnořené paralelismu povoleno, není-li povolit nebo zakázat pomocí vnořených paralelismu `omp_set_nested`.

```
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Poznámky

`OMP_NESTED` Proměnné prostředí můžete přepsat [omp_set_nested –](openmp-functions.md#omp-set-nested) funkce.

Je výchozí hodnotu v implementaci Visual C++ OpenMP standard `OMP_DYNAMIC=FALSE`.

Další informace najdete v tématu [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Příklad

Nastaví zadáním následujícího příkazu `OMP_NESTED` proměnné prostředí na hodnotu TRUE:

```
set OMP_NESTED=TRUE
```

Následující příkaz zobrazí aktuální nastavení `OMP_NESTED` proměnné prostředí:

```
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

Nastaví maximální počet vláken v paralelní oblasti, pokud není přepsán [omp_set_num_threads –](openmp-functions.md#omp-set-num-threads) nebo [num_threads](openmp-clauses.md#num-threads).

```
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Parametry

*počet*<br/>
Maximální počet vláken, které chcete v paralelní oblasti až 64 v implementaci Visual C++.

### <a name="remarks"></a>Poznámky

`OMP_NUM_THREADS` Proměnné prostředí můžete přepsat [omp_set_num_threads –](openmp-functions.md#omp-set-num-threads) funkce nebo [num_threads](openmp-clauses.md#num-threads).

Výchozí hodnota `num` v jazyce Visual C++ implementace standardu OpenMP je počet virtuálních procesorů, včetně hyperthreadingem procesory.

Další informace najdete v tématu [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Příklad

Nastaví zadáním následujícího příkazu `OMP_NUM_THREADS` proměnnou prostředí, aby `16`:

```
set OMP_NUM_THREADS=16
```

Následující příkaz zobrazí aktuální nastavení `OMP_NUM_THREADS` proměnné prostředí:

```
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

Upravuje chování [plán](openmp-clauses.md#schedule) klauzule při `schedule(runtime)` je zadán v `for` nebo `parallel for` – direktiva.

```
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
(Volitelné) Určuje velikost iterací. *velikost* musí být kladné celé číslo. Výchozí hodnota je `1`, s výjimkou, kdy *typ* je statická. Není platná v případě *typ* je `runtime`.

*type*<br/>
Druh plánování buď `dynamic`, `guided`, `runtime`, nebo `static`.

### <a name="remarks"></a>Poznámky

Je výchozí hodnotu v implementaci Visual C++ OpenMP standard `OMP_SCHEDULE=static,0`.

Další informace najdete v tématu [4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Příklad

Nastaví zadáním následujícího příkazu `OMP_SCHEDULE` proměnné prostředí:

```
set OMP_SCHEDULE="guided,2"
```

Následující příkaz zobrazí aktuální nastavení `OMP_SCHEDULE` proměnné prostředí:

```
set OMP_SCHEDULE
```
