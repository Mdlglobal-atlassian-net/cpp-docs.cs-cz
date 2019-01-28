---
title: 4. Proměnné prostředí
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: 558b835c36253fb67339fba9b46cb0170dd6d1d0
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087194"
---
# <a name="4-environment-variables"></a>4. Proměnné prostředí

Tato kapitola popisuje rozhraní API C++ a C OpenMP – proměnné prostředí (nebo podobné mechanismy specifické pro platformu), které nastavují spuštění paralelního kódu.  Názvy proměnných prostředí musí být uváděny velkými písmeny. Hodnoty přiřazené k jejich jsou malá a velká písmena a může obsahovat úvodní a koncové prázdné znaky.  Úpravy hodnot po spuštění programu se ignorují.

Proměnné prostředí jsou následující:

- [OMP_SCHEDULE](#41-omp_schedule) nastaví velikost typu a bloků dat za běhu plánu.
- [OMP_NUM_THREADS](#42-omp_num_threads) nastaví počet vláken během provádění.
- [OMP_DYNAMIC](#43-omp_dynamic) povolí nebo zakáže dynamické úpravy počtu vláken.
- [OMP_NESTED](#44-omp_nested) povolí nebo zakáže vnořené paralelismu.

Příklady v této kapitole pouze ukazují, jak tyto proměnné může být nastaveno v prostředích Unix C prostředí (kontextová nápověda). V prostředí DOS a Korn prostředí jsou podobné akce:

Kontextová nápověda:  
`setenv OMP_SCHEDULE "dynamic"`

ksh:  
`export OMP_SCHEDULE="dynamic"`

DOS:  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE` platí jenom pro `for` a `parallel for` direktivy, které mají typ plánu `runtime`. Plán typ a bloků velikosti takové smyčky můžete nastavit v době běhu. Nastavení této proměnné prostředí na libovolný typ rozpoznaný plánu a volitelně *chunk_size*.

Pro `for` a `parallel for` direktivy, které mají typ plánu jiné než `runtime`, `OMP_SCHEDULE` se ignoruje. Výchozí hodnota pro tuto proměnnou prostředí je definován implementací. Pokud volitelný *chunk_size* nastaven, hodnota musí být kladná. Pokud *chunk_size* není nastaven, je použita hodnota 1, s výjimkou případu, kdy plán `static`. Pro `static` , výchozí velikost bloku je naplánováno do prostoru iterace smyčky vydělí počtem vláken u smyčky.

Příklad:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Křížové odkazy

- [pro](2-directives.md#241-for-construct) – direktiva
- [paralelní pro](2-directives.md#251-parallel-for-construct) – direktiva

## <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS

`OMP_NUM_THREADS` Proměnné prostředí nastavuje výchozí počet vláken během provádění. `OMP_NUM_THREADS` se ignoruje, pokud toto číslo je explicitně změněno pomocí volání `omp_set_num_threads` rutina knihovny. Je také ignoruje, pokud je explicitní `num_threads` klauzuli `parallel` směrnice.

Hodnota `OMP_NUM_THREADS` proměnné prostředí musí být kladné celé číslo. Jeho dopad závisí na tom, zda je povolena dynamické úpravy počtu vláken. Pro komplexní sadu pravidel o interakci mezi `OMP_NUM_THREADS` prostředí najdete v článku proměnné a dynamické úpravy vláken, [části 2.3](2-directives.md#23-parallel-construct).

Počet vláken je implementace definováno, pokud:

- `OMP_NUM_THREADS` proměnná prostředí není zadán,
- Zadaná hodnota není kladné celé číslo, nebo
- hodnota je větší než maximální počet vláken, která může systém podporovat.

Příklad:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Křížové odkazy

- [num_threads](2-directives.md#23-parallel-construct) – klauzule
- [omp_set_num_threads –](3-run-time-library-functions.md#311-omp_set_num_threads-function) – funkce
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) function

## <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC

`OMP_DYNAMIC` Proměnnou prostředí povolí nebo zakáže dynamické úpravy počtu vláken, které jsou k dispozici k provádění paralelních oblastí. `OMP_DYNAMIC` se ignoruje, pokud je dynamické úpravy explicitně povoleno nebo zakázáno voláním `omp_set_dynamic` rutina knihovny. Musí být jeho hodnota `TRUE` nebo `FALSE`.

Pokud `OMP_DYNAMIC` je nastavena na `TRUE`, počet vláken, která se používají k provádění paralelních oblastí může být upravit tak, že prostředí runtime tak, aby co nejlépe využívat systémové prostředky.  Pokud `OMP_DYNAMIC` je nastavena na `FALSE`, dynamické přizpůsobení je zakázaná. Výchozí stav je definován implementací.

Příklad:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Křížové odkazy

- [Paralelních oblastí](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) function

## <a name="44-ompnested"></a>4.4 OMP_NESTED

`OMP_NESTED` Proměnnou prostředí povolí nebo zakáže vnořené paralelismu, pokud je povoleno nebo zakázáno voláním vnořené paralelismu `omp_set_nested` rutina knihovny. Pokud `OMP_NESTED` je nastavena na `TRUE`, je povoleno vnořené paralelismu. Pokud `OMP_NESTED` je nastavena na `FALSE`vnořené paralelismu je zakázaná. Výchozí hodnota je `FALSE`.

Příklad:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Křížových odkazů

- [omp_set_nested –](3-run-time-library-functions.md#319-omp_set_nested-function) – funkce
