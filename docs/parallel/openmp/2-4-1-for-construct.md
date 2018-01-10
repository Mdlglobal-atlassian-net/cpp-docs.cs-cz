---
title: "2.4.1 for – konstrukce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 27d2cbce-786b-4819-91d3-d55b2cc57a5e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dd861da77b549a73edf9aeface714b0066d88344
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="241-for-construct"></a>2.4.1 for – konstrukce
**Pro** – direktiva identifikuje iterativní konstrukce sdílení práce, která určuje, že iterace smyčky přidružené spustí paralelně. Iterace z **pro** smyčky distribuováno napříč vlákny, které již existují v provádění paralelní konstrukce, ke kterému se váže týmu. Syntaxe **pro** konstrukce vypadá takto:  
  
```  
#pragma omp for [clause[[,] clause] ... ] new-linefor-loop  
```  
  
 V klauzuli je jedním z následujících akcí:  
  
 **privátní (** *seznamu proměnné* **)**  
  
 **firstprivate (** *seznamu proměnné* **)**  
  
 **lastprivate (** *seznamu proměnné* **)**  
  
 **snížení (** *operátor* **:** *seznamu proměnné***)**  
  
 **řazení**  
  
 **plán (** *druhu*[, *chunk_size*]**)**  
  
 **nowait**  
  
 **Pro** – direktiva umístí omezení na strukturu odpovídající **pro** smyčky. Konkrétně odpovídající **pro** smyčky musí mít kanonický tvar:  
  
 **pro (** *init expr* **;** *var logické op b*; *incr expr***)**  
  
 *Init – výraz*  
 Jeden z následujících postupů:  
  
 *var* = *lb*  
  
 *typ integer var* = *lb*  
  
 *incr – výraz*  
 Jeden z následujících postupů:  
  
 ++*var*  
  
 *var* ++  
  
 -- *var*  
  
 *var* --  
  
 *var* += *incr*  
  
 *var* -= *incr*  
  
 *var* = *var* + *incr*  
  
 *var* = *incr* + *var*  
  
 *var* = *var* - *incr*  
  
 *var*  
 Proměnná se znaménkem. Pokud tato proměnná by jinak sdílet, je implicitně k privátní po dobu trvání **pro**.   Tato proměnná nesmí být upraveno v rámci textu **pro** příkaz. Pokud není zadána proměnná **lastprivate**, jeho hodnota po neurčitou smyčky.  
  
 *logické op*  
 Jeden z následujících postupů:  
  
 <  
  
 \<=  
  
 >  
  
 \>=  
  
 *LB*, *b*, a *incr*  
 Smyčka výrazy invariantní celé číslo. Neexistuje žádná synchronizace během vyhodnocování těchto výrazů. Proto všechny vyhodnotí vedlejší účinky výsledkům neurčitou.  
  
 Všimněte si, že kanonický tvar umožňuje počet iterací smyčky počítaný na položce, aby smyčky. Tento výpočet se provádí s hodnotami v typu *var*, po zvýšení úrovně celého čísla. V případě, hodnota *b* - *lb* + *incr* nelze vyjádřit v, že výsledkem je typ neurčitém. Další, pokud *logické op* je < nebo \<= pak *incr expr* musí způsobit *var* zvýšit na každé iteraci smyčky.   Pokud *logické op* je > nebo > = pak *incr expr* musí způsobit *var* snížení na každé iteraci smyčky.  
  
 **Plán** klauzuli určuje způsob opakování **pro** smyčky jsou rozděleny mezi vláken týmu. Správnost programu nesmí být závislá na vlákno, které provede konkrétní iterací. Hodnota *chunk_size*, pokud zadaný, musí být výraz smyčky invariantní celé číslo s kladnou hodnotu. Neexistuje žádná synchronizace během vyhodnocování výrazu. Proto všechny vyhodnotí vedlejší účinky výsledkům neurčitou. Plán *druh* může být jedna z následujících akcí:  
  
 Tabulka 2-1 **plán** klauzule *druh* hodnoty  
  
|||  
|-|-|  
|static|Když **plán (statické,** *chunk_size***)** není zadaný, iterací dělí do bloků velikosti určeného *chunk_size*. Bloky dat jsou staticky přiřazeny vláken v týmu v kruhového dotazování v pořadí podle počtu vláken. Pokud ne *chunk_size* není zadaný, iterace volné místo je rozděleno do bloků, které jsou přibližně stejnou velikost, se jeden blok přiřazené každé vlákno.|  
|dynamické odkazy|Když **plán (dynamicky** *chunk_size***)** není zadaný, iterace dělí do bloků, každý obsahující řady *chunk_size* iterací. Každého bloku je přiřazený k vlákno, které se čeká na přiřazení. Vlákno provede u bloku iterací a potom počká, než jeho další přiřazení, dokud nezůstanou žádné bloky dat pro přiřazení. Všimněte si, že poslední bloku přiřazení může mít menší počet iterací. Pokud ne *chunk_size* je zadána výchozí hodnota 1.|  
|na základě|Když **plán (na základě,** *chunk_size***)** není zadaný, iterace jsou přiřazeny k vláken v bloky dat s snížení velikosti. Po dokončení své přiřazené bloku iterací vlákno je dynamicky přiřazen jiný bloku, dokud žádné zůstanou. Pro *chunk_size* 1, velikost každého bloku je přibližně počet nepřiřazených iterací dělený počet vláken. Tyto velikosti snížit přibližně exponenciálnímu na 1. Pro *chunk_size* s hodnotou *tisíc* větší než 1, velikosti snížit přibližně exponenciálnímu na *tisíc*kromě toho, že poslední bloku dat může mít méně než  *k* iterací. Pokud ne *chunk_size* je zadána výchozí hodnota 1.|  
|modul runtime|Když **schedule(runtime)** není zadaný, rozhodnutí týkající se plánování je odložena až do modulu runtime. Plán *druhu* a velikost bloky dat je možné vybrat v době běhu nastavením proměnné prostředí **OMP_SCHEDULE**. Pokud není nastavena tato proměnná prostředí, výsledný plán je definované implementací. Když **schedule(runtime)** není zadaný, *chunk_size* nesmí být zadaný.|  
  
 Chybí explicitně definovaných **plán** klauzule, bude výchozí **plán** je definované implementací.  
  
 Kompatibilní se standardem OpenMP program neměli spoléhat na konkrétní plán pro správné spuštění. Program neměli spoléhat na plán *druhu* odpovídající přesněji popisu výše uvedené, protože je možné, že rozdíly v implementacích stejný plán *druh* napříč Různé kompilátory. Popisy lze zvolit podle plánu, který je vhodný pro konkrétní situaci.  
  
 **Seřazené** klauzule musí být při **seřazené** direktivy vytvořit vazbu **pro** vytvořit.  
  
 Na konci je implicitní bariéry **pro** vytvořit, pokud **nowait** je zadána klauzule.  
  
 Omezení **pro** – direktiva jsou následující:  
  
-   **Pro** smyčky musí být strukturovaný blok, a kromě toho nesmí být jeho spuštění ukončen **zalomení** příkaz.  
  
-   Hodnoty smyčky řízení výrazy **pro** smyčky přidružené **pro** – direktiva musí být stejné pro všechny vlákna v týmu.  
  
-   **Pro** proměnné iterace smyčky musí mít typ se znaménkem.  
  
-   Jediným **plán** klauzule lze zobrazit na **pro** – direktiva.  
  
-   Jediným **seřazené** klauzule lze zobrazit na **pro** – direktiva.  
  
-   Jediným **nowait** klauzule lze zobrazit na **pro** – direktiva.  
  
-   Pokud neurčené nebo jak často ovlivňuje všechny straně v rámci *chunk_size*, *lb*, *b*, nebo *incr* výrazy dojít.  
  
-   Hodnota *chunk_size* výraz musí být stejné pro všechny vlákna v týmu.  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   **privátní**, **firstprivate**, **lastprivate**, a **snížení** klauzule, najdete v části [části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.  
  
-   **OMP_SCHEDULE** proměnné, naleznete v prostředí [části 4.1](../../parallel/openmp/4-1-omp-schedule.md) na stránce 48.  
  
-   **seřazené** vytvořit najdete v tématu [část 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) na stránce 22.  
  
-   [Dodatek D](../../parallel/openmp/d-using-the-schedule-clause.md), stránka 93, poskytuje další informace o použití klauzule plán.