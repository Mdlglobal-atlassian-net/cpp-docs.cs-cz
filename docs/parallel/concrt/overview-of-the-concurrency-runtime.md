---
title: Přehled Concurrency Runtime
ms.date: 11/19/2018
helpviewer_keywords:
- Concurrency Runtime, requirements
- Concurrency Runtime, architecture
- Concurrency Runtime, overview
- Concurrency Runtime, lambda expressions
ms.assetid: 56237d96-10b0-494a-9cb4-f5c5090436c5
ms.openlocfilehash: b50c943bb83c587ab4001556b1143f9d5f868a0b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142924"
---
# <a name="overview-of-the-concurrency-runtime"></a>Přehled Concurrency Runtime

Tento dokument poskytuje přehled Concurrency Runtime. Popisuje výhody Concurrency Runtime, kdy je použít a jak spolu jejich součásti vzájemně spolupracují a s operačním systémem a aplikacemi.

## <a name="top"></a>Řezů

Tento dokument obsahuje následující části:

- [Historie implementace Concurrency Runtime](#dlls)

- [Proč je modul runtime pro souběžnost důležitý](#runtime)

- [Architektura](#architecture)

- [C++Výrazy lambda](#lambda)

- [Požadavky](#requirements)

## <a name="dlls"></a>Historie implementace Concurrency Runtime

V sadě Visual Studio 2010 až 2013 byl Concurrency Runtime začleněn do souboru msvcr100. dll prostřednictvím msvcr120. dll.  V případě refaktoringu UCRT v aplikaci Visual Studio 2015 byla tato knihovna DLL refaktorovaná na tři části:

- ucrtbase. dll – rozhraní API, dodávané ve Windows 10 a se zavedením nižší úrovně prostřednictvím web Windows Update-

- knihovny vcruntime140. dll – funkce podpory kompilátoru a modul runtime EH, dodávané prostřednictvím sady Visual Studio

- concrt140. dll – Concurrency Runtime dodávané prostřednictvím sady Visual Studio. Vyžaduje se u paralelních kontejnerů a algoritmů, jako je `concurrency::parallel_for`. STL také vyžaduje, aby tato knihovna DLL v systému Windows XP měla k dispozici základní možnosti synchronizace, protože systém Windows XP neobsahuje proměnné podmínky.

V aplikaci Visual Studio 2015 a novějších Concurrency Runtime Plánovač úloh již není plánovačem pro třídu úlohy a související typy v ppltasks. h. Tyto typy nyní používají fondu Windows pro lepší výkon a interoperabilitu s prvky synchronizace systému Windows.

## <a name="runtime"></a>Proč je modul runtime pro souběžnost důležitý

Modul runtime pro souběžnost poskytuje jednotnost a předvídatelnost pro aplikace a komponenty aplikace, které běží současně. Dva příklady výhod Concurrency Runtime jsou *kooperativní plánování úloh* a *kooperativní blokování*.

Concurrency Runtime používá spolupráci plánovače úloh, který implementuje algoritmus pro efektivní distribuci práce mezi výpočetními prostředky. Zvažte například aplikaci, která má dvě vlákna, která jsou spravovaná stejným modulem runtime. Pokud jedno vlákno dokončí svou naplánovanou úlohu, může přesměrovat práci z druhého vlákna. Tento mechanismus vyrovnává celkové zatížení aplikace.

Concurrency Runtime také poskytuje prvky synchronizace, které k synchronizaci přístupu k prostředkům používají funkci pro spolupráci. Představte si třeba úlohu, která musí mít výhradní přístup ke sdílenému prostředku. Díky blokování spolupracuje modul runtime za účelem provedení jiné úlohy, když bude první úkol čekat na prostředek. Tento mechanismus podporuje maximální využití výpočetních prostředků.

[[Nahoře](#top)]

## <a name="architecture"></a>Architektura

Concurrency Runtime je rozdělena do čtyř komponent: knihovna paralelních vzorů (PPL), Knihovna asynchronních agentů, Plánovač úloh a Správce prostředků. Tyto součásti jsou umístěné mezi operačním systémem a aplikacemi. Následující obrázek ukazuje, jak Concurrency Runtime komponenty vzájemně spolupracují mezi operačním systémem a aplikacemi:

**Architektura Concurrency Runtime**

![Architektura Concurrency Runtime](../../parallel/concrt/media/concurrencyrun.png "Architektura Concurrency Runtime")

> [!IMPORTANT]
> Komponenty Plánovač úloh a Správce prostředků nejsou k dispozici v aplikaci Univerzální platforma Windows (UWP) ani při použití třídy Task nebo jiných typů v ppltasks. h.

Concurrency Runtime je vysoce *sestavitelná*, to znamená, že můžete kombinovat stávající funkce, abyste mohli víc dělat. Concurrency Runtime vytváří mnoho funkcí, jako jsou například paralelní algoritmy, ze součástí nižší úrovně.

Concurrency Runtime také poskytuje prvky synchronizace, které k synchronizaci přístupu k prostředkům používají funkci pro spolupráci. Další informace o těchto primitivách synchronizace najdete v tématu [Synchronizace datových struktur](../../parallel/concrt/synchronization-data-structures.md).

V následujících částech najdete stručný přehled toho, co jednotlivé komponenty poskytují a kdy je použít.

### <a name="parallel-patterns-library"></a>Knihovna PPL (Parallel Patterns Library)

Knihovna PPL (Parallel Patterns Library) poskytuje obecné kontejnery a algoritmy pro provádění jemně odstupňovaného paralelismu. PPL umožňuje *imperativní datové paralelismuy* tím, že poskytuje paralelní algoritmy, které distribuují výpočty na kolekcích nebo na sady dat napříč výpočetními prostředky. Umožňuje taky *úkol paralelismus* tím, že poskytuje objekty úlohy, které distribuují víc nezávislých operací mezi výpočetními prostředky.

Knihovnu paralelních vzorů použijte v případě, že máte místní výpočet, který může využít paralelního spuštění. Například můžete použít algoritmus [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) k transformaci existující smyčky `for`, aby fungovala paralelně.

Další informace o knihovně paralelních vzorů naleznete v tématu [Knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

### <a name="asynchronous-agents-library"></a>Knihovna asynchronních agentů

Asynchronní agenti knihovny (nebo pouze *agenti knihovny*) poskytují programovací model založený na objektech actor a rozhraní předávání zpráv pro hrubý úlohy toku dat a zpracování. Asynchronní agenti umožňují zvýšit efektivitu tím, že provádí práci, protože jiné komponenty čekají na data.

Použijte knihovnu agenti, pokud máte více entit, které spolu komunikují asynchronně. Můžete například vytvořit agenta, který čte data ze souboru nebo síťového připojení, a pak pomocí rozhraní předávání zpráv odesílat tato data jinému agentovi.

Další informace o knihovně agentů najdete v tématu [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md).

### <a name="task-scheduler"></a>Plánovač úloh

Plánovač úloh plány a koordinuje úlohy za běhu. Plánovač úloh je družstvo a využívá algoritmus pro práci, který se používá k dosažení maximálního využití prostředků zpracování.

Concurrency Runtime poskytuje výchozí Plánovač, takže nemusíte spravovat podrobnosti o infrastruktuře. Pro splnění potřeb kvality aplikace ale můžete také zadat vlastní zásady plánování nebo přidružit konkrétní plánovače k určitým úkolům.

Další informace o Plánovač úloh najdete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

### <a name="resource-manager"></a>Správce prostředků

Role Správce prostředků slouží ke správě výpočetních prostředků, jako jsou procesory a paměť. Správce prostředků reaguje na úlohy při změně v době běhu přiřazením prostředků do místa, kde mohou být nejefektivnější.

Správce prostředků slouží jako abstrakce oproti výpočetním prostředkům a primárně spolupracuje s Plánovač úloh. I když můžete použít Správce prostředků k vyladění výkonu knihoven a aplikací, obvykle používáte funkce, které jsou poskytovány pomocí knihovny paralelních vzorů, knihovny agentů a Plánovač úloh. Tyto knihovny používají Správce prostředků k dynamickému rozložení prostředků při změně zatížení.

[[Nahoře](#top)]

## <a name="lambda"></a>C++ Výrazy lambda

Mnoho typů a algoritmů, které jsou definovány Concurrency Runtime, jsou implementovány jako C++ šablony. Některé z těchto typů a algoritmů přebírají jako parametr rutinu, která provádí práci. Tento parametr může být funkce lambda, objekt funkce nebo ukazatel na funkci. Tyto entity se také označují jako *pracovní funkce* nebo *pracovní postupy*.

Výrazy lambda jsou důležitou novou funkcí C++ vizuálního jazyka, protože poskytují stručný způsob, jak definovat pracovní funkce pro paralelní zpracování. Objekty funkcí a ukazatele na funkce umožňují použít Concurrency Runtime s existujícím kódem. Nicméně doporučujeme používat výrazy lambda při psaní nového kódu v důsledku výhod zabezpečení a produktivity, které poskytují.

Následující příklad porovnává syntaxi funkcí lambda, objektů funkcí a ukazatelů funkcí v několika voláních algoritmu [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) . Každé volání `parallel_for_each` používá jinou metodu pro výpočet čtverce jednotlivých prvků v objektu [std:: Array](../../standard-library/array-class-stl.md) .

[!code-cpp[concrt-comparing-work-functions#1](../../parallel/concrt/codesnippet/cpp/overview-of-the-concurrency-runtime_1.cpp)]

**Výstup**

```Output
1
256
6561
65536
390625
```

Další informace o funkcích lambda v naleznete C++v tématu [lambda Expressions](../../cpp/lambda-expressions-in-cpp.md).

[[Nahoře](#top)]

## <a name="requirements"></a>Požadavků

V následující tabulce jsou uvedeny hlavičkové soubory, které jsou spojeny s jednotlivými součástmi Concurrency Runtime:

|Komponenta|Soubory hlaviček|
|---------------|------------------|
|Knihovna PPL (Parallel Patterns Library)|ppl.h<br /><br /> concurrent_queue.h<br /><br /> concurrent_vector. h|
|Knihovna asynchronních agentů|Agents. h|
|Plánovač úloh|ConcRT. h|
|Správce prostředků|concrtrm.h|

Concurrency Runtime je deklarován v oboru názvů [Concurrency](../../parallel/concrt/reference/concurrency-namespace.md) . (Můžete také použít [Concurrency](../../parallel/concrt/reference/concurrency-namespace.md), což je alias pro tento obor názvů.) Obor názvů `concurrency::details` podporuje Concurrency Runtime Framework a není určen pro použití přímo v kódu.

Concurrency Runtime je k dispozici jako součást běhové knihovny jazyka C (CRT). Další informace o tom, jak vytvořit aplikaci, která používá CRT, najdete v tématu [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).

[[Nahoře](#top)]
