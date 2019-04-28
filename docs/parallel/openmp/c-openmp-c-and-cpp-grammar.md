---
title: C. Gramatika OpenMP – C a C++
ms.date: 01/16/2019
ms.assetid: 97a878ce-1533-47f7-a134-66fcbff48524
ms.openlocfilehash: 85e18161079b49e83cc9fedb3184ee220c889e75
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362943"
---
# <a name="c-openmp-c-and-c-grammar"></a>C. Gramatika OpenMP – C a C++

[C.1 Zápis](#c1-notation)<br/>
[C.2 Pravidla](#c2-rules)

## <a name="c1-notation"></a>C.1 Zápis

Gramatika pravidla jsou založená na názvu bez terminal, za nímž následuje dvojtečka, následovaný nahrazení alternativy na samostatných řádcích.

Syntaktické výraz<sub>optimalizované</sub> znamená, že je výraz nepovinný v nahrazení.

Syntaktické výraz *termín*<sub>optseq</sub> je ekvivalentní *termín seq*<sub>optimalizované</sub> s následující další pravidla:

*termín seq*:  
&nbsp;&nbsp;&nbsp;&nbsp;*Termín*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*termín seq* *termín*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*termín seq* `,` *termín*

## <a name="c2-rules"></a>C.2 Pravidla

Zápis je popsaný v části 6.1 standardu C. Tento dodatek gramatiky ukazuje rozšíření pro základní jazyk gramatiky direktivy OpenMP – C a C++.

**/\* v jazyce C++ (ISO/IEC 14882:1998) \*/**

*statement-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*– Příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*OpenMP – direktiva*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seq – příkaz – příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz seq openmp – direktiva*

**/\* v C90 (ISO/IEC 9899: 1990) \*/**

*seznam příkazů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*– Příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*OpenMP – direktiva*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz seznamu příkazů*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam příkazů openmp – direktiva*

**/\* v C99 (ISO/IEC 9899:1999) \*/**

*block-item*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*– Příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*OpenMP – direktiva*

**/\* standardní příkazy \*/**

*příkaz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-construct*

*konstrukce OpenMP*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*for-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sections-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Single – konstrukce*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-for-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-sections-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*master-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*critical-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*atomic-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ordered-construct*

*OpenMP – direktiva*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Barrier – direktiva*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Flush – direktiva*

*strukturovaný blok*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*– Příkaz*

*parallel-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*strukturované paralelní směrnice – blok*

*parallel-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel` *parallel-clause*<sub>optseq</sub> *new-line*

*parallel-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*unique-parallel-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `if (` *Výraz*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `num_threads (` *Výraz*   `)`

*pro konstruktor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pro direktivu iterace – příkaz*

*pro direktivu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp for` *for-clause*<sub>optseq</sub> *new-line*

*for-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*unique-for-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `ordered`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (` *Typ plánu*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (` *Typ plánu* `,` *výraz*   `)`

*Typ plánu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `static`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `dynamic`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `guided`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `runtime`

*sections-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*části příslušné části – direktiva*

*sections-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp sections` *sections-clause*<sub>optseq</sub> *new-line*

*sections-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*Rozsah oddílu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{oddíl pořadí}*

*části pořadí*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direktivu Section*<sub>optimalizované</sub> *strukturovaný blok*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*strukturované direktivu section části pořadí – blok*

*direktivu Section*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp section` *nový řádek*

*Single – konstrukce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Single – direktiva strukturovaného bloku*

*Single – direktiva*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp single` *jedinou klauzulí*<sub>optseq</sub> *nový řádek*

*single-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*parallel-for-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*paralelní pro direktivu iterace – příkaz*

*paralelní pro direktivu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel for` *parallel-for-clause*<sub>optseq</sub> *new-line*

*parallel-for-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*parallel-sections-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*části rozsahu paralelní – oddíly – direktiva*

*parallel-sections-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel sections` *parallel-sections-clause*<sub>optseq</sub> *new-line*

*parallel-sections-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*master-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hlavní – direktiva strukturovaného bloku*

*master-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp master` *nový řádek*

*critical-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direktivy Critical strukturovaného bloku*

*critical-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp critical` *oblast frázi*<sub>optimalizované</sub> *nový řádek*

*region-phrase*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(identifikátor)*

*barrier-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp barrier` *nový řádek*

*atomic-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výrazu direktivy Atomic*

*atomic-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp atomic` *nový řádek*

*Flush – direktiva*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp flush` *vyprázdnění proměnných*<sub>optimalizované</sub> *nový řádek*

*vyprázdnění proměnných*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(seznamu proměnné)*

*ordered-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*strukturované seřadit direktivy – blok*

*Seřadit direktivy*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp ordered` *nový řádek*

**/\* Standardní deklarace \*/**

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*threadprivate – direktiva*

*Direktiva threadprivate*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp threadprivate (` *seznamu proměnné* `)` *nový řádek*

*data-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `private (` *Proměnná list*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyprivate (`  *Proměnná list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `firstprivate (`  *Proměnná list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `lastprivate (` *Proměnná list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `shared (` *Proměnná list*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( shared )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( none )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `reduction (`  *operátorem Reduction*`:`*seznamu proměnné*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyin (`  *Proměnná list*    `)`

*operátorem Reduction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Jedna z:   `+ \* - & ^ | && ||`

**/\* v jazyce C \*/**

*seznamu proměnné*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznamu proměnné* `,` *identifikátor*

**/\* v jazyce C++ \*/**

*seznamu proměnné*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ID – výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznamu proměnné* `,` *id – výraz*
