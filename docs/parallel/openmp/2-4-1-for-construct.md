---
title: 2.4.1 for – konstrukce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 27d2cbce-786b-4819-91d3-d55b2cc57a5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb9a554d9141223be7a5f6bc741c86b8f03511e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428538"
---
# <a name="241-for-construct"></a>2.4.1 for – konstrukce

**Pro** – direktiva určuje iterativní konstruktoru work-sharing, která určuje, že iterací smyčky související se spustí paralelně. Iterace **pro** smyčky jsou distribuovány napříč vlákny, které již existují v týmu provádí paralelní konstrukce, ke kterému se váže. Syntaxe **pro** konstruktor je následujícím způsobem:

```
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

V klauzuli je jedním z následujících akcí:

**privátní (** *seznamu proměnné* **)**

**firstprivate (** *seznamu proměnné* **)**

**lastprivate (** *seznamu proměnné* **)**

**snížení (** *operátor* **:** *seznamu proměnné* **)**

**Řazení**

**plán (** *druh* [**,** *chunk_size*] **)**

**nowait**

**Pro** směrnice umístí omezení na strukturu odpovídající **pro** smyčky. Konkrétně odpovídající **pro** smyčky musí mít kanonický tvar:

**pro (** *init-expr* **;** *var logické op b*; *incr expr* **)**

*Init – výraz*<br/>
Jeden z následujících postupů:

*var* = *lb*

*celočíselný typ var* = *lb*

*incr – výraz*<br/>
Jeden z následujících postupů:

++ *var*

*var* ++

-- *var*

*var* --

*var* += *incr*

*var* -= *incr*

*var* = *var* + *incr*

*var* = *incr* + *var*

*var* = *var* - *incr*

*var*<br/>
Proměnná celé číslo se znaménkem. Pokud tato proměnná by jinak sdílet, je implicitně k privátní po dobu trvání **pro**.   Tato proměnná nesmí upravovat v těle **pro** příkazu. Pokud není zadána proměnná **lastprivate**, jeho hodnota po neurčitou smyčky.

*logický op*<br/>
Jeden z následujících postupů:

<

\<=

>

\>=

*LB*, *b*, a *incr*<br>
Smyčka výrazy invariantní celé číslo. Neexistuje žádná synchronizace během vyhodnocování těchto výrazů. Proto všechny vyhodnocené vedlejší účinky výsledkům neurčitý.

Všimněte si, že kanonický tvar umožňuje počet iterací smyčky vypočítání při vstupu do smyčky. Tento výpočet se provádí s hodnotami typu *var*, po zvýšení úrovně celého čísla. V případě hodnoty *b* - *lb* + *incr* nemůže být vyjádřena v tom, že typ výsledku je neurčité. Další, pokud *logické op* je < nebo \<= pak *incr expr* musíte zajistit, aby *var* zvýšit při každé iteraci smyčky.   Pokud *logické op* je > nebo > = pak *incr expr* musíte zajistit, aby *var* se při každé iteraci smyčky.

**Plán** klauzule určuje, jak iterací **pro** smyčky jsou rozděleny mezi vlákny týmu. Správnost programu nesmí být závislá na které vlákno provede konkrétní iteraci. Hodnota *chunk_size*, je-li zadána, musí být výraz smyčky invariantní celé číslo s kladnou hodnotu. Neexistuje žádná synchronizace během vyhodnocení tohoto výrazu. Proto všechny vyhodnocené vedlejší účinky výsledkům neurčitý. Plán *druh* může být jedna z následujících akcí:

Tabulka 2-1 **plán** klauzule *druh* hodnoty

|||
|-|-|
|static|Když **plán (statické,** *chunk_size* **)** je zadaný počet iterací jsou rozdělené do bloků velikosti určené *chunk_size*. Bloky dat se staticky přiřadí vlákna v týmu v vždy střídat dokola v pořadí podle počtu vláken. Pokud ne *chunk_size* určena, iteraci místo je rozděleno do bloků dat, které jsou přibližně stejnou velikost, s jeden blok přiřazená každé vlákno.|
|dynamické odkazy|Když **plán (dynamická,** *chunk_size* **)** je zadaný počet iterací jsou rozdělené do řady bloků, každý obsahující *chunk_size* iterací. Každý blok je přiřazená vlákna, který čeká na přiřazení. Vlákno provede blok iterací a pak počká na další zadání žádné bloky dat i nadále možné přiřadit. Všimněte si, že poslední blok dat, který má být přiřazena může mít menší počet iterací. Pokud ne *chunk_size* není zadán, výchozí hodnotu 1.|
|s asistencí|Když **plán (s asistencí,** *chunk_size* **)** je zadaný počet iterací jsou přiřazená vlákna v blocích s snížení velikosti. Po dokončení své přiřazené bloku iterací vlákno ho se dynamicky přiřadí jiného bloku, dokud nezůstanou none. Pro *chunk_size* 1, velikost každého bloku je přibližně počet nepřiřazených iterací vydělí počtem vláken. Tyto velikosti snížit přibližně exponenciálně na hodnotu 1. Pro *chunk_size* s hodnotou *k* větší než 1, velikosti snížit přibližně exponenciálně na *k*, s tím rozdílem, že poslední blok dat může být kratší než  *k* iterací. Pokud ne *chunk_size* není zadán, výchozí hodnotu 1.|
|modul runtime|Když **schedule(runtime)** není zadána, rozhodnutí týkající se plánování je odložena až do modulu runtime. Plán *druh* a velikost bloky dat může být vybrána v době běhu nastavením proměnné prostředí **OMP_SCHEDULE**. Pokud tato proměnná prostředí není nastavená, výsledný plán je definován implementací. Když **schedule(runtime)** není zadána, *chunk_size* nesmí být zadaný.|

Chybí explicitně definovanou **plán** klauzule, výchozí **plán** je definováno implementací.

Aplikace kompatibilní s OpenMP neměli byste tedy spoléhat na konkrétní plán pro správné spuštění. Program, neměli byste tedy spoléhat na plánu *druh* odpovídající přesně popisu výše uvedené, protože je možné mít odchylky v implementacích stejného plánu *druh* napříč Různé kompilátory. Popis je možné vybrat plán, který je vhodný pro konkrétní situaci.

**Seřazené** klauzule musí být použit, pokud **seřazené** direktivy svázat **pro** vytvořit.

Na konci je implicitní bariéry **pro** vytvořit, není-li **nowait** není zadána klauzule.

Omezení **pro** směrnice jsou následující:

- **Pro** smyčky musí být strukturovaný blok, a kromě toho nesmí být jeho spuštění ukončen **přerušení** příkazu.

- Hodnoty smyčky řídit výrazy **pro** smyčky přidružené **pro** direktiva musí být stejný pro všechny vlákna v týmu.

- **Pro** proměnná iterace smyčky musí být typu celé číslo se znaménkem.

- Pouze jeden **plán** klauzule se může objevit v **pro** směrnice.

- Pouze jeden **seřazené** klauzule se může objevit v **pro** směrnice.

- Pouze jeden **nowait** klauzule se může objevit v **pro** směrnice.

- Je neurčená if nebo jak často se žádné vedlejší efekty v rámci *chunk_size*, *lb*, *b*, nebo *incr* výrazy dojít.

- Hodnota *chunk_size* výraz musí být stejný pro všechny vlákna v týmu.

## <a name="cross-references"></a>Křížové odkazy:

- **privátní**, **firstprivate**, **lastprivate**, a **snížení** klauzule, naleznete v tématu [části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.

- **OMP_SCHEDULE** proměnné, viz prostředí [části 4.1](../../parallel/openmp/4-1-omp-schedule.md) na stránce 48.

- **seřazené** vytvořit, přečtěte si téma [části 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) na stránce 22.

- [Příloha D](../../parallel/openmp/d-using-the-schedule-clause.md), stránce 93, poskytuje další informace o použití klauzule schedule.