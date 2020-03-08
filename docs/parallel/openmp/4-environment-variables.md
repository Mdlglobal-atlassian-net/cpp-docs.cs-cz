---
title: 4. Proměnné prostředí
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: b41829fd9cf2f90312f669ef991f56dda02947f7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882851"
---
# <a name="4-environment-variables"></a>4. proměnné prostředí

Tato kapitola popisuje proměnné prostředí OpenMP C C++ a API (nebo podobné mechanizmy specifické pro platformu), které řídí provádění paralelního kódu.  Názvy proměnných prostředí musí být velká písmena. Hodnotám, které jsou přiřazeny, jsou nerozlišovat velká a malá písmena a mohou mít úvodní a koncové prázdné znaky.  Úpravy hodnot po spuštění programu jsou ignorovány.

Proměnné prostředí jsou následující:

- [OMP_SCHEDULE](#41-omp_schedule) nastaví typ časového plánu za běhu a velikost bloku dat.
- [OMP_NUM_THREADS](#42-omp_num_threads) nastaví počet vláken, která se mají použít při provádění.
- [OMP_DYNAMIC](#43-omp_dynamic) povoluje nebo zakazuje dynamickou úpravu počtu vláken.
- [OMP_NESTED](#44-omp_nested) povoluje nebo zakazuje vnořené paralelismuy.

Příklady v této kapitole ukazují, jak se tyto proměnné můžou nastavit v prostředích prostředí csh (UNIX C Shell). V prostředích Korn shell a DOS jsou akce podobné:

csh:  
`setenv OMP_SCHEDULE "dynamic"`

ksh:  
`export OMP_SCHEDULE="dynamic"`

DOS  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a>4,1 OMP_SCHEDULE

`OMP_SCHEDULE` se vztahuje pouze na direktivy `for` a `parallel for`, které mají `runtime`typu plán. Typ plánu a velikost bloku pro všechny takové smyčky lze nastavit v době běhu. Nastavte tuto proměnnou prostředí na libovolný rozpoznaný typ plánu a na nepovinný *chunk_size*.

Pro direktivy `for` a `parallel for`, které mají jiný typ plánu než `runtime`, `OMP_SCHEDULE` se ignoruje. Výchozí hodnota této proměnné prostředí je definovaná implementací. Pokud je nastaven volitelný *chunk_size* , hodnota musí být kladná. Pokud není nastavená *chunk_size* , předpokládá se hodnota 1, s výjimkou případů, kdy je plán `static`. Pro `static` plán je výchozí velikost bloku nastavená na prostor pro iteraci smyčky dělený počtem vláken, která se pro smyčku používají.

Příklad:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Křížové odkazy

- [pro](2-directives.md#241-for-construct) direktivu
- [Parallel for](2-directives.md#251-parallel-for-construct) – direktiva

## <a name="42-omp_num_threads"></a>4,2 OMP_NUM_THREADS

Proměnná prostředí `OMP_NUM_THREADS` nastaví výchozí počet vláken, která se mají použít při provádění. `OMP_NUM_THREADS` se ignoruje, pokud je toto číslo explicitně změněno voláním rutiny knihovny `omp_set_num_threads`. Ignoruje se také v případě, že je v direktivě `parallel` explicitní klauzule `num_threads`.

Hodnota proměnné prostředí `OMP_NUM_THREADS` musí být kladné celé číslo. Jeho efekt závisí na tom, zda je dynamická úprava počtu vláken povolena. Komplexní sadu pravidel o interakci mezi `OMP_NUM_THREADS` proměnnou prostředí a dynamickou úpravou vláken naleznete v [části 2,3](2-directives.md#23-parallel-construct).

Počet podprocesů, které se mají použít, je implementace definovaná v těchto případech:

- není zadaná proměnná prostředí `OMP_NUM_THREADS`,
- Zadaná hodnota není kladné celé číslo nebo
- hodnota je větší než maximální počet vláken, která může systém podporovat.

Příklad:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Křížové odkazy

- klauzule [num_threads](2-directives.md#23-parallel-construct)
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) funkce
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) funkce

## <a name="43-omp_dynamic"></a>4,3 OMP_DYNAMIC

Proměnná prostředí `OMP_DYNAMIC` povoluje nebo zakazuje dynamickou úpravu počtu vláken, která jsou k dispozici pro spuštění paralelních oblastí. `OMP_DYNAMIC` se ignoruje, pokud je dynamická úprava explicitně povolená nebo zakázaná voláním rutiny knihovny `omp_set_dynamic`. Jeho hodnota musí být `TRUE` nebo `FALSE`.

Pokud je `OMP_DYNAMIC` nastavené na `TRUE`, může být počet vláken, která se používají pro spouštění paralelních oblastí, upravený běhovým prostředím, aby se co nejlépe používaly systémové prostředky.  Pokud je `OMP_DYNAMIC` nastaveno na `FALSE`, je dynamická úprava zakázána. Výchozí podmínka je definovaná implementací.

Příklad:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Křížové odkazy

- [Paralelní oblasti](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) funkce

## <a name="44-omp_nested"></a>4,4 OMP_NESTED

Proměnná prostředí `OMP_NESTED` povoluje nebo zakazuje vnořené paralelismus, pokud není vnořený paralelismu povolený nebo zakázaný voláním rutiny knihovny `omp_set_nested`. Pokud je `OMP_NESTED` nastaveno na `TRUE`, je povolen vnořený paralelismus. Pokud je `OMP_NESTED` nastaveno na `FALSE`, je vnořený paralelismu zakázán. Výchozí hodnota je `FALSE`.

Příklad:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Křížové odkazy

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) funkce
