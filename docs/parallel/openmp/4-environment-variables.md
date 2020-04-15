---
title: 4. Proměnné prostředí
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: e93c59654c17ed6dbfb7483ac2dce716ce24b52a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370270"
---
# <a name="4-environment-variables"></a>4. Proměnné prostředí

Tato kapitola popisuje proměnné prostředí Rozhraní API OpenMP C a C++ (nebo podobné mechanismy specifické pro platformu), které řídí provádění paralelního kódu.  Názvy proměnných prostředí musí být velká písmena. Hodnoty, které jsou jim přiřazeny, jsou nerozlišující malá a velká písmena a mohou mít úvodní a koncové prázdné místo.  Změny hodnot po spuštění programu jsou ignorovány.

Proměnné prostředí jsou následující:

- [OMP_SCHEDULE](#41-omp_schedule) nastaví typ plánu běhu a velikost bloku dat.
- [OMP_NUM_THREADS](#42-omp_num_threads) nastaví počet podprocesů, které mají být používány během provádění.
- [OMP_DYNAMIC](#43-omp_dynamic) povolí nebo zakáže dynamické nastavení počtu podprocesů.
- [OMP_NESTED](#44-omp_nested) povolí nebo zakáže vnořený paralelismus.

Příklady v této kapitole pouze ukazují, jak mohou být tyto proměnné nastaveny v prostředí unixového prostředí C (csh). V prostředí Korn shell a DOS jsou akce podobné:

csh:  
`setenv OMP_SCHEDULE "dynamic"`

Ksh:  
`export OMP_SCHEDULE="dynamic"`

Dos:  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a><a name="41-omp_schedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE`platí pouze `for` pro `parallel for` a direktivy, které mají typ `runtime`plánu . Typ plánu a velikost bloku pro všechny tyto smyčky lze nastavit v době běhu. Nastavte tuto proměnnou prostředí na libovolný rozpoznaný typ plánu a na volitelný *chunk_size*.

Pro `for` `parallel for` a direktivy, `runtime`které `OMP_SCHEDULE` mají jiný typ plánu než , jsou ignorovány. Výchozí hodnota pro tuto proměnnou prostředí je definována implementací. Pokud je nastavena volitelná *chunk_size,* musí být hodnota kladná. Pokud *chunk_size* není nastavena, předpokládá se hodnota 1, `static`s výjimkou případů, kdy je plán . Pro `static` plán je výchozí velikost bloku dat nastavena na prostor iterace smyčky dělený počtem vláken aplikovaných na smyčku.

Příklad:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Křížové odkazy

- [pro](2-directives.md#241-for-construct) směrnici
- [paralelní pro](2-directives.md#251-parallel-for-construct) směrnici

## <a name="42-omp_num_threads"></a><a name="42-omp_num_threads"></a>4.2OMP_NUM_THREADS

Proměnná `OMP_NUM_THREADS` prostředí nastaví výchozí počet podprocesů, které mají být používány během provádění. `OMP_NUM_THREADS`je ignorována, pokud je toto `omp_set_num_threads` číslo explicitně změněno voláním rutiny knihovny. Je také ignorována, pokud je `num_threads` explicitní klauzule o `parallel` směrnici.

Hodnota proměnné `OMP_NUM_THREADS` prostředí musí být kladné celé číslo. Jeho účinek závisí na tom, zda je povoleno dynamické nastavení počtu vláken. Komplexní soubor pravidel týkajících se interakce `OMP_NUM_THREADS` mezi proměnnou prostředí a dynamickým nastavením vláken naleznete [v části 2.3](2-directives.md#23-parallel-construct).

Počet podprocesů, které chcete použít, je definován implementací, pokud:

- proměnná `OMP_NUM_THREADS` prostředí není zadána,
- zadaná hodnota není kladné celé číslo, nebo
- hodnota je větší než maximální počet podprocesů, které systém může podporovat.

Příklad:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Křížové odkazy

- [num_threads](2-directives.md#23-parallel-construct) doložka
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) funkce
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) funkce

## <a name="43-omp_dynamic"></a><a name="43-omp_dynamic"></a>4.3 OMP_DYNAMIC

Proměnná `OMP_DYNAMIC` prostředí umožňuje nebo zakazuje dynamické nastavení počtu podprocesů, které jsou k dispozici pro provádění paralelních oblastí. `OMP_DYNAMIC`je ignorována, pokud je dynamická úprava explicitně povolena nebo zakázána voláním rutiny knihovny. `omp_set_dynamic` Jeho hodnota `TRUE` musí `FALSE`být nebo .

Pokud `OMP_DYNAMIC` je `TRUE`nastavena na , počet podprocesů, které se používají pro provádění paralelních oblastí mohou být upraveny prostředím runtime tak, aby co nejlépe využívaly systémové prostředky.  Pokud `OMP_DYNAMIC` je `FALSE`nastavena na , dynamické nastavení je zakázáno. Výchozí podmínka je definována implementací.

Příklad:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Křížové odkazy

- [Paralelní regiony](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) funkce

## <a name="44-omp_nested"></a><a name="44-omp_nested"></a>4.4OMP_NESTED

Proměnná `OMP_NESTED` prostředí povolí nebo zakáže vnořený paralelismus, pokud není `omp_set_nested` povoleno nebo zakázáno vnořené paralelismu voláním rutiny knihovny. Pokud `OMP_NESTED` je `TRUE`nastavena na , vnořené paralelismus je povolena. Pokud `OMP_NESTED` je `FALSE`nastavena na , vnořený paralelismus je zakázán. Výchozí hodnota je `FALSE`.

Příklad:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Křížového odkazu

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) funkce
