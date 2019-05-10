---
title: Migrace z OpenMP do Concurrency Runtime
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
ms.openlocfilehash: ba2b413d40da601029f5c4e1d861576212c10494
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448420"
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>Migrace z OpenMP do Concurrency Runtime

Modul Concurrency Runtime umožňuje širokou škálu programovacích modelů. Tyto modely mohou překrývat nebo doplňují modely další knihovny. Dokumenty v této části porovnání [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) do Concurrency Runtime a poskytnout příklady o tom, jak migrovat existující kód OpenMP na využití modulu Concurrency Runtime.

OpenMP – programovací model je definován otevřený standard a nemá jasně definované vazby pro programovací jazyky až po Fortran a jazyka C/C++. Verze OpenMP 2.0 a 2.5, které podporuje Microsoft C++ kompilátor, jsou vhodné pro paralelní algoritmy, které jsou iterativní; To znamená provádějí paralelní iterace nad určitým polem data. OpenMP 3.0 podporuje – iterativní úlohy navíc iterativní úlohám.

OpenMP – je nejúčinnější, když stupeň paralelismu předem určit a odpovídá prostředcích k dispozici v systému. OpenMP – model je zvlášť vhodné shoda pro vysokovýkonné výpočetní prostředí, ve kterých se velmi rozsáhlých výpočetních problémech distribuují napříč prostředky zpracování z jednoho počítače. V tomto scénáři je hardwarové prostředí obecně pevně a vývojář můžete přiměřeně očekávají, že má výhradní přístup ke všem prostředkům výpočetní při provádění algoritmu.

Ale méně omezené výpočetních prostředí nemusí být správné odpovídající OpenMP. Rekurzivní problémy (např. algoritmus quicksort nebo hledání tak stromy dat.) jsou například obtížné implementovat pomocí OpenMP 2.0 a 2.5. Modulu Runtime souběžnosti doplňuje funkce OpenMP tím, že poskytuje [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md) a [knihovny Ppl](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). Asynchronní knihovnou agentů podporuje paralelismu hrubých úloh; PPL podporuje více podrobných paralelní úlohy. Modul Concurrency Runtime poskytuje infrastrukturu, která je potřeba provádět operace paralelně, abyste se mohli zaměřit na logiku aplikace. Ale protože Concurrency Runtime umožňuje širokou škálu programovacích modelů, jeho plánování režie může být větší než jiné knihovny concurrency například OpenMP. Doporučujeme proto, že provedete test výkonu postupně po převést svůj existující kód OpenMP na využití modulu Concurrency Runtime.

## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Když migrace z OpenMP do Concurrency Runtime

Může být výhodné k migraci existujícího kódu OpenMP na využití modulu Runtime souběžnosti v následujících případech.

|Případy|Výhody modulu Runtime souběžnosti|
|-----------|-------------------------------------------|
|Budete potřebovat extensible souběžnému programovacímu.|Mnoho funkcí v modulu Runtime souběžnosti je možné rozšířit. Můžete také kombinovat existující funkce k vytvoření nové značky. Protože OpenMP závisí na direktivy kompilátoru, nelze snadno rozšířit.|
|Vaše aplikace je výhodná spolupráce blokování.|Pokud úkol zablokuje, protože vyžaduje prostředek, který ještě není k dispozici, modulu Runtime souběžnosti můžete provádět další úlohy, zatímco první úloha čeká na prostředek.|
|Vaše aplikace je výhodná dynamické vyrovnávání zatížení.|Modulu Runtime souběžnosti používá plánování algoritmus, který přizpůsobí přidělování výpočetních prostředků jako úlohy změnit. V OpenMP když Plánovač přiděluje výpočetní prostředky v paralelní oblasti přidělením těchto prostředků jsou pevně dané v rámci výpočtu.|
|Budete potřebovat podporu zpracování výjimek.|PPL umožňuje zachytit výjimky uvnitř i vně paralelní oblasti nebo smyčky. V OpenMP musí zpracovat výjimku v rámci paralelní oblasti nebo smyčky.|
|Budete potřebovat mechanismu zrušení.|PPL umožňuje aplikacím zrušit jednotlivé úkoly a paralelní pracovní stromy. OpenMP – vyžaduje, aby aplikace implementovat vlastní mechanismus zrušení.|
|Je potřeba dokončit v jiném kontextu, ze kterého se spouští paralelní kód.|Modul Concurrency Runtime umožňuje spustit úlohu v jednom kontextu a potom počkat nebo zrušit tuto úlohu v jiném kontextu. V OpenMP musíte dokončit všechny paralelně prováděných úloh v kontextu, ze kterého se spouští.|
|Budete potřebovat lepší podporu ladění.|Visual Studio poskytuje **paralelní zásobníky** a **paralelní úlohy** windows tak, aby můžete snadněji ladit aplikace s více vlákny.<br /><br /> Další informace o ladění podpora modulu Runtime souběžnosti, naleznete v tématu [Using the Tasks Window](/visualstudio/debugger/using-the-tasks-window), [použití okna paralelní zásobníky](/visualstudio/debugger/using-the-parallel-stacks-window), a [názorný postup: Ladění paralelní aplikace](/visualstudio/debugger/walkthrough-debugging-a-parallel-application).|

## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Kdy nepoužívat migrace z OpenMP do Concurrency Runtime

Následujících případech popsat, ale nemusí být vhodné k migraci existujícího kódu OpenMP na využití modulu Concurrency Runtime.

|Případy|Vysvětlení|
|-----------|-----------------|
|Už vaše aplikace splňuje vaše požadavky.|Pokud jste spokojeni s výkonem aplikace a aktuální podporu ladění, nemusí být vhodný migrace.|
|Vaše paralelních smyček provádět mnoho zásahů.|Režie Plánovač Concurrency Runtime nemusí překonat výhody spuštění do těla smyčky paralelní, zejména v případě, že do těla smyčky je poměrně malá.|
|Vaše aplikace je napsána v jazyce C.|Protože Concurrency Runtime využívá mnoho z funkcí jazyka C++, nemusí být vhodné při nelze napsat kód, který umožňuje aplikaci jazyka C k plnému využívání.|

## <a name="related-topics"></a>Související témata

[Postupy: Převedení paralelní smyčky for v OpenMP na využití modulu Concurrency Runtime](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)

Zadaný základní smyčku, která se používá OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) a [pro](../../parallel/openmp/reference/for-openmp.md) direktivy, ukazuje, jak převést jej na využití modulu Concurrency Runtime [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus.

[Postupy: Převedení smyčky OpenMP využívající zrušení na využití modulu Concurrency Runtime](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)<br/>
Zadaný OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pro](../../parallel/openmp/reference/for-openmp.md) smyčku, která nevyžaduje všech iterací ke spuštění, ukazuje, jak převeďte ho na použití mechanismu zrušení Concurrency Runtime.

[Postupy: Převedení smyčky OpenMP využívající zpracování výjimek na využití modulu Concurrency Runtime](../../parallel/concrt/convert-an-openmp-loop-that-uses-exception-handling.md)<br/>
Zadaný OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pro](../../parallel/openmp/reference/for-openmp.md) smyčku, která provádí zpracování výjimek, ukazuje, jak ho použít mechanismus zpracování výjimek Concurrency Runtime převést.

[Postupy: Převedení smyčky OpenMP využívající redukční proměnnou na využití modulu Concurrency Runtime](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)<br/>
Zadaný OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pro](../../parallel/openmp/reference/for-openmp.md) smyčku, která se používá [snížení](../../parallel/openmp/reference/reduction.md) klauzule, ukazuje, jak převést jej na využití modulu Concurrency Runtime.

## <a name="see-also"></a>Viz také:

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)<br/>
[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)
