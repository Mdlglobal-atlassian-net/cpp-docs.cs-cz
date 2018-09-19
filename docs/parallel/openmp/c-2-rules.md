---
title: C.2 pravidla | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4d52fef7-3eb7-4480-a335-8ed48681092b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c5845a9125bb32254fc0c03b03e9b6076a086d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404771"
---
# <a name="c2-rules"></a>C.2 Pravidla

Zápis je popsaný v části 6.1 standardu C. Tento dodatek gramatiky ukazuje rozšíření pro základní jazyk gramatiky direktivy OpenMP – C a C++.

**/\* v jazyce C++ (ISO/IEC 14882:1998) \*/**

*příkaz seq*:<br/>
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

*blok item*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*– Příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*OpenMP – direktiva*

**/\* standardní příkazy \*/**

*příkaz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*OpenMP – konstruktor*

*konstrukce OpenMP*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Parallel – konstrukce*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pro konstruktor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*oddíly – konstruktor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Single – konstrukce*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*paralelní pro konstrukce*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*paralelní – oddíly – konstruktor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*master – konstrukce*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Critical – konstrukce*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Atomic – konstrukce*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seřadit – konstruktor*

*OpenMP – direktiva*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Barrier – direktiva*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Flush – direktiva*

*strukturovaný blok*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*– Příkaz*

*paralelní konstrukce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*strukturované paralelní směrnice – blok*

*paralelní směrnice*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# – Direktiva pragma omp parallel** *paralelní klauzule*<sub>optseq</sub> *nový řádek*

*paralelní klauzule*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jedinečné paralelní klauzuli*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data – klauzule*

*jedinečné paralelní klauzule*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Pokud (** *výraz* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**num_threads (** *výraz* **)**

*pro konstruktor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pro direktivu iterace – příkaz*

*pro direktivu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omp – Direktiva pragma # pro** *klauzuli for*<sub>optseq</sub> *nový řádek*

*pro klauzuli*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jedinečné pro klauzuli*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data – klauzule*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nowait**

*jedinečné pro klauzuli*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Řazení**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**plán (** *typ plánu* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**plán (** *typ plánu* **,** *výraz* **)**

*Typ plánu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Statická**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Dynamické**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**s asistencí**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Modul runtime**

*oddíly konstrukce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*části příslušné části – direktiva*

*Direktiva oddíly*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**oddíly omp – Direktiva pragma #** *oddíly klauzule*<sub>optseq</sub> *nový řádek*

*oddíly klauzule*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data – klauzule*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nowait**

*Rozsah oddílu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{oddíl pořadí}*

*části pořadí*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direktivu Section*<sub>optimalizované</sub> *strukturovaný blok*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*strukturované direktivu section části pořadí – blok*

*direktivu Section*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omp section. # pragma** *nový řádek*

*Single – konstrukce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Single – direktiva strukturovaného bloku*

*Single – direktiva*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omp – Direktiva pragma # jeden** *jedinou klauzulí*<sub>optseq</sub> *nový řádek*

*jedinou klauzulí*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data – klauzule*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nowait**

*paralelní pro konstrukce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*paralelní pro direktivu iterace – příkaz*

*paralelní pro direktivu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# – Direktiva pragma omp parallel pro** *paralelní pro klauzuli*<sub>optseq</sub> *nový řádek*

*paralelní pro klauzuli*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jedinečné paralelní klauzuli*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jedinečné pro klauzuli*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data – klauzule*

*paralelní. oddíly konstrukce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*části rozsahu paralelní – oddíly – direktiva*

*paralelní. oddíly směrnice*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# – Direktiva pragma omp parallel oddíly** *paralelních oddílů klauzule*<sub>optseq</sub> *nový řádek*

*paralelní oddíly klauzule*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jedinečné paralelní klauzuli*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data – klauzule*

*master – konstrukce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hlavní – direktiva strukturovaného bloku*

*hlavní směrnice*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**hlavní omp – Direktiva pragma #** *nový řádek*

*Critical – konstrukce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direktivy Critical strukturovaného bloku*

*direktivy Critical*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omp – Direktiva pragma # kritické** *oblasti frázi*<sub>optimalizované</sub> *nový řádek*

*oblast frázi*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(identifikátor)*

*Barrier – direktiva*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**bariéra omp – Direktiva pragma #** *nový řádek*

*Atomic – konstrukce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výrazu direktivy Atomic*

*direktivy Atomic*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# – Direktiva pragma omp atomic** *nový řádek*

*Flush – direktiva*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omp – Direktiva pragma # vyprázdnění** *vyprázdnění proměnných*<sub>optimalizované</sub> *nový řádek*

*vyprázdnění proměnných*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(seznamu proměnné)*

*seřazené konstrukce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*strukturované seřadit direktivy – blok*

*Seřadit direktivy*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omp – Direktiva pragma # seřazené** *nový řádek*

**/\* Standardní deklarace \*/**

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*threadprivate – direktiva*

*Direktiva threadprivate*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# threadprivate omp – Direktiva pragma (** *seznamu proměnné***)** *nový řádek* 

*data klauzule*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**privátní (** *seznamu proměnné* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**copyprivate (***seznamu proměnné***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**firstprivate (***seznamu proměnné***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**lastprivate (** *seznamu proměnné***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sdílené (** *seznamu proměnné* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Výchozí (sdílené)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Výchozí (žádné)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**snížení (***operátorem reduction***:***seznamu proměnné***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**copyin (***seznamu proměnné***)** 

*operátorem Reduction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Jeden z:  **+  \* -& ^ &#124; & &&#124;&#124;**

**/\* v jazyce C \*/**

*seznamu proměnné*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznamu proměnné* **,** *identifikátor*

**/\* v jazyce C++ \*/**

*seznamu proměnné*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ID – výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznamu proměnné* **,** *id – výraz*