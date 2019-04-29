---
title: Přehled Concurrency Runtime
ms.date: 11/19/2018
helpviewer_keywords:
- Concurrency Runtime, requirements
- Concurrency Runtime, architecture
- Concurrency Runtime, overview
- Concurrency Runtime, lambda expressions
ms.assetid: 56237d96-10b0-494a-9cb4-f5c5090436c5
ms.openlocfilehash: 810d77abd37ff2c6f29e980b84645d16526744d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412690"
---
# <a name="overview-of-the-concurrency-runtime"></a>Přehled Concurrency Runtime

Tento dokument poskytuje přehled o modulu Runtime souběžnosti. Popisuje výhody modulu Runtime souběžnosti, kdy ji použít, a způsob, jakým jeho komponenty komunikovat mezi sebou a s operačním systémem a aplikace.

##  <a name="top"></a> Oddíly

Tento dokument obsahuje následující části:

- [Historie provádění Concurrency Runtime](#dlls)

- [Proč je rozhraní Concurrency Runtime důležité](#runtime)

- [Architektura](#architecture)

- [Výrazy Lambda v jazyce C++](#lambda)

- [Požadavky](#requirements)

## <a name="dlls"></a> Historie provádění Concurrency Runtime

V sadě Visual Studio 2010 prostřednictvím 2013 Concurrency Runtime byl zahrnut msvcr100.dll prostřednictvím msvcr120.dll.  Když UCRT refaktoring došlo k chybě v sadě Visual Studio 2015, že knihovna DLL se teď vyčleněný do tří částí:

- ucrtbase.dll – rozhraní API jazyka C, dodáno ve Windows 10 a udržovat nižší úrovně prostřednictvím Windows Update-

- Podpora kompilátoru knihovny vcruntime140.dll – funkce a modulu runtime EH dodáno prostřednictvím sady Visual Studio

- concrt140.dll – Concurrency Runtime dodáno prostřednictvím sady Visual Studio. Vyžaduje se pro paralelní kontejnery a algoritmy, jako `concurrency::parallel_for`. Navíc STL potřebuje tuto knihovnu DLL na Windows XP k power primitiv synchronizace, protože Windows XP nemá podmínku proměnné.

V sadě Visual Studio 2015 a novější Plánovač úloh Concurrency Runtime není nadále Plánovač úloh třídy a souvisejících typů v ppltasks.h. Tyto typy teď použít Windows fondu vláken pro lepší výkon a vzájemná funkční spolupráce s primitiv synchronizace Windows.

##  <a name="runtime"></a> Proč je rozhraní Concurrency Runtime důležité

Rozhraní concurrency runtime poskytuje jednotné a předvídatelnost aplikace a součásti aplikace, na kterých běží současně. Jsou dva příklady výhody modulu Runtime souběžnosti *plánování spolupráce úkolů* a *spolupráce blokování*.

Modulu Runtime souběžnosti používá plánovače úloh spolupráce, který implementuje algoritmus přebírající práci pro efektivní distribuci práce mezi výpočetními prostředky. Zvažte například aplikaci, která má dvě vlákna, která se spravují pomocí stejných modulů runtime. Pokud jedno vlákno skončí její naplánované úlohy, ho přenést práce z jiného podprocesu. Tento mechanismus vyrovnává celkové zatížení aplikace.

Modul Concurrency Runtime poskytuje také synchronizací primitiv, které používají k synchronizaci přístupu k prostředkům spolupráce blokování. Představte si třeba úlohu, která musí mít exkluzivní přístup ke sdíleným prostředkům. Zákonné zodpovědnosti organizací blokováním kooperativně, můžete použít modul runtime zbývající quantum provést jinou úlohu, protože první úloha čeká na prostředek. Tento mechanismus podporuje maximální využití výpočetních prostředků.

[[Horní](#top)]

##  <a name="architecture"></a> Architektura

Modulu Runtime souběžnosti je rozdělena do čtyř komponent: Knihovna paralelních vzorů (PPL), asynchronní knihovnou agentů, Plánovač úloh a Resource Manageru. Tyto součásti jsou umístěny mezi operačního systému a aplikací. Následující obrázek znázorňuje, jak pracují komponenty modulu Runtime souběžnosti mezi operačního systému a aplikací:

**Architektura modulu Runtime souběžnosti**

![Architektura modulu Runtime souběžnosti](../../parallel/concrt/media/concurrencyrun.png "architektura modulu Runtime souběžnosti")

> [!IMPORTANT]
> Součástí plánovače úloh a Resource Manageru nejsou k dispozici z aplikace pro univerzální platformu Windows (UPW) nebo při použití třídy úkolu nebo jiné typy v ppltasks.h.

Modulu Runtime souběžnosti je vysoce *sestavitelné*, to znamená, můžete kombinovat existující funkce lepší. Modulu Runtime souběžnosti lze kombinovat mnoho funkcí, jako je například paralelní algoritmy, ze součástí nižší úrovně.

Modul Concurrency Runtime poskytuje také synchronizací primitiv, které používají k synchronizaci přístupu k prostředkům spolupráce blokování. Další informace o těchto primitivních hodnot synchronizace najdete v tématu [synchronizačních datových struktur](../../parallel/concrt/synchronization-data-structures.md).

Stručný přehled, co jednotlivé komponenty obsahuje a kdy ji použít v následujících částech.

### <a name="parallel-patterns-library"></a>Knihovna PPL (Parallel Patterns Library)

Knihovna paralelních vzorů (PPL) poskytuje kontejnery pro obecné účely a algoritmy pro provádění dosáhnout jemně odstupňovaného paralelismu. Umožňuje PPL *imperativní datový paralelismus* poskytnutím paralelní algoritmy, které distribuovat výpočty na kolekcích nebo sad dat napříč výpočetních prostředků. Umožňuje také *paralelismus úloh* tím, že poskytuje objekty úloh, které se distribuuje více nezávislých operací mezi výpočetních prostředků.

Používejte knihovny Ppl, pokud máte místní výpočtu, který může přinést paralelního provádění. Například můžete použít [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus transformace existující `for` smyčky tak, aby fungoval paralelně.

Další informace o paralelních vzorcích knihovny najdete v tématu [knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

### <a name="asynchronous-agents-library"></a>Knihovna asynchronních agentů

Asynchronní knihovnou agentů (nebo jen *knihovna agentů*) poskytuje programovací model založený na objektu actor i message passing rozhraní pro hrubých toku dat a paralelní zpracování úloh. Asynchronní agenti umožňují vytvářet produktivní použití latencí tím, že provádí práci jako ostatní součásti čekat na data.

Používejte knihovnu agentů v případě, že máte více entit, které komunikují asynchronně. Můžete například vytvořit agenta, který čte data ze souboru nebo síťového připojení a pak používá předávání rozhraní zpráv k odesílání dat do jiného agenta.

Další informace o knihovna agentů najdete v tématu [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md).

### <a name="task-scheduler"></a>Plánovač úloh

Plánovač úloh plánuje a koordinuje úkoly v době běhu. Plánovač úloh je spolupráce a používá algoritmus přebírající práci pro dosažení maximální využití prostředků zpracování.

Concurrency Runtime poskytuje výchozí plánovače, takže není nutné spravovat infrastrukturu podrobnosti. Podle potřeb kvality vaší aplikace, můžete však také poskytnout vlastní plánování zásad nebo přidružit konkrétní plánovači s konkrétními úlohami.

Další informace o Plánovači úloh naleznete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

### <a name="resource-manager"></a>Správce prostředků

Role správce prostředků je spravovat výpočetní prostředky, jako jsou procesory a paměť. Správce prostředků reaguje na úlohy, když se změní za běhu kde může být nejúčinnější přiřazením prostředky.

Správce prostředků slouží jako o abstrakci přes výpočetní prostředky a primárně komunikuje pomocí plánovače úloh. Přestože Resource Manageru můžete optimalizovat výkon aplikací a knihoven, můžete obvykle použít funkci, která je poskytována knihovny Ppl, knihovna agentů a Plánovač úloh. Tyto knihovny jako úlohy změnit dynamicky obnovit rovnováhu prostředků pomocí Resource Manageru.

[[Horní](#top)]

##  <a name="lambda"></a> Výrazy Lambda v jazyce C++

Mnoho typů a algoritmy, které jsou definovány pomocí modulu Runtime souběžnosti, jsou implementovány jako šablony jazyka C++. Některé z těchto typů a algoritmy trvat jako parametr rutiny, která provádí práci. Tento parametr může být funkce lambda, objekt funkce nebo ukazatele na funkci. Tyto entity se také označují jako *pracovní funkce* nebo *fungovat rutiny*.

Výrazy lambda jsou o důležitou novou funkci jazyka Visual C++, protože poskytují stručné způsob, jak definovat pracovní funkce pro paralelní zpracování. Objekty funkce a ukazatelů na funkce umožňují používat Concurrency Runtime s existujícím kódem. Doporučujeme však použít výrazy lambda, pokud píšete nový kód z důvodu bezpečnosti a produktivity výhody, které poskytují.

Následující příklad porovnává syntaxe funkce lambda, objektů funkce a ukazatelů na funkce ve více voláních [: concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus. Každé volání `parallel_for_each` používá jiný postup k výpočtu druhou mocninu každý prvek v [std::array](../../standard-library/array-class-stl.md) objektu.

[!code-cpp[concrt-comparing-work-functions#1](../../parallel/concrt/codesnippet/cpp/overview-of-the-concurrency-runtime_1.cpp)]

**Output**

```Output
1
256
6561
65536
390625
```

Další informace o funkcích lambda v jazyce C++, naleznete v tématu [výrazy Lambda](../../cpp/lambda-expressions-in-cpp.md).

[[Horní](#top)]

##  <a name="requirements"></a> Požadavky

V následující tabulce jsou uvedeny soubory hlaviček, které jsou spojené s každou komponentu modulu Runtime souběžnosti:

|Součást|Soubory hlaviček|
|---------------|------------------|
|Knihovna PPL (Parallel Patterns Library)|ppl.h<br /><br /> concurrent_queue.h<br /><br /> concurrent_vector.h|
|Knihovna asynchronních agentů|agents.h|
|Plánovač úloh|concrt.h|
|Správce prostředků|concrtrm.h|

Modulu Runtime souběžnosti je deklarován v [souběžnosti](../../parallel/concrt/reference/concurrency-namespace.md) oboru názvů. (Můžete také použít [souběžnosti](../../parallel/concrt/reference/concurrency-namespace.md), což je alias pro tento obor názvů.) `concurrency::details` Obor názvů podporuje rozhraní Concurrency Runtime a není určena pro použití přímo v kódu.

Modulu Runtime souběžnosti je dodáván jako součást z knihovny C Runtime (CRT). Další informace o tom, jak vytvořit aplikaci, která používá CRT naleznete v tématu [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).

[[Horní](#top)]
