---
title: Porovnání modelu Concurrency Runtime s jinými modely souběžného zpracování
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, compared to other models
ms.assetid: d8b9a1f4-f15f-43c3-a5b4-c0991edf9c86
ms.openlocfilehash: 885cce09707e1c067efdeb0bdc8b7d8a40841c02
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285097"
---
# <a name="comparing-the-concurrency-runtime-to-other-concurrency-models"></a>Porovnání modelu Concurrency Runtime s jinými modely souběžného zpracování

Tento dokument popisuje rozdíly mezi funkcemi a programovacích modelů Concurrency Runtime a dalších technologií. Když porozumíte tomu, jak porovnat výhody modulu Runtime souběžnosti výhod jiných programovacích modelů, můžete vybrat technologie, která nejlépe vyhovuje požadavkům vašich aplikací.

Pokud aktuálně používáte jiný programovací model, jako je například Windows fondu vláken nebo OpenMP, existují situace, kde může být vhodné k migraci do modulu Runtime souběžnosti. Například téma [migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md) popisuje, kdy může být vhodné k migraci z OpenMP do Concurrency Runtime. Nicméně pokud jste spokojeni s výkonem aplikace a aktuální podporu ladění, není migrace nutná.

Funkce a produktivity výhody modulu Runtime souběžnosti můžete doplňují existující aplikaci, která používá jiný model souběžnosti. Modulu Runtime souběžnosti nemůže zaručit, Vyrovnávání zatížení při více plánovačích úkolů soutěžit o stejnou výpočetní prostředky. Ale když úlohy se nepřekrývají, tento efekt je minimální.

##  <a name="top"></a> Oddíly

- [Porovnání Preemptive plánování k plánování spolupráce](#models)

- [Porovnání Concurrency Runtime s Windows API](#winapi)

- [Porovnání modelu Concurrency Runtime s OpenMP](#openmp)

##  <a name="models"></a> Porovnání Preemptive plánování k plánování spolupráce

Preemptive modelu a kooperativní plánování modely jsou dvě běžné způsoby povolení více úkolů ke sdílení výpočetní prostředky, například procesory nebo hardwarových vláken.

### <a name="preemptive-and-cooperative-scheduling"></a>Plánování preemptive a spolupráce

*Preemptive plánování* je kruhové dotazování, na základě priority mechanismus, který poskytuje každý úkol výhradní přístup k výpočetnímu prostředku pro zadané časové období a pak přepne na jiné úlohy. Preemptive plánování je běžné v multitaskingu operační systémy jako Windows. *Plánování spolupráce* virtuálních sítí je mechanismus, která poskytuje každý úkol výhradní přístup k výpočetnímu prostředku, dokud neskončí úloha nebo dokud se úloha provede jeho přístup k prostředku. Modul Concurrency Runtime používá k dosažení maximální využití prostředků zpracování kooperativní plánování spolu s plánovači preemptive operačního systému.

### <a name="differences-between-preemptive-and-cooperative-schedulers"></a>Rozdíly mezi plánovači Preemptive a spolupráce

Preemptive plánovače se snaží poskytnout více vláken rovnocenný přístup k výpočetní prostředky k zajištění, že každé vlákno díky průběh. Na počítačích, které mají mnoho výpočetních prostředků zajištění spravedlivého přístupu bude méně problematické; zajištění efektivního využití prostředků bude však více problematické.

Plánovačem preemptivní režimu jádra vyžaduje kód aplikace, který závisí na operačním systému pro plánování rozhodování. Naopak kooperativní Plánovač uživatelského režimu umožňuje kódu aplikace pro vlastní plánování rozhodování. Protože plánování spolupráce umožňuje mnoho plánování rozhodnutí o aplikací, snižuje většinu zatížení, který je přidružený k synchronizaci režimu jádra. Spolupráce Plánovač obvykle odloží plánovací rozhodnutí do jádra operačního systému, když nemá žádná práce k naplánování. Spolupráce Plánovač se také odloží plánovač operačního systému při blokující operace, které jsou předávány do jádra, ale operace se předávají Plánovač uživatelského režimu.

### <a name="cooperative-scheduling-and-efficiency"></a>Plánování spolupráce a efektivity

Do preemptive plánovače rovná veškerou práci, která má stejnou prioritu. Preemptive scheduler plánuje obvykle vlákna v pořadí, ve kterém jsou vytvořeny. Preemptive Plánovač navíc poskytuje každé vlákno časovém intervalu způsobem kruhové dotazování na základě priority vlákna. I když tento mechanismus nabízí rovnost (každé vlákno provede postup směrem vpřed), obsahuje některé poplatků efektivitu. Například mnoho algoritmů intenzivními nevyžadují rovnost. Místo toho je důležité, že v nejméně celkový čas dokončit související úlohy. Plánování spolupráce umožňuje aplikaci efektivněji plánování práce. Zvažte například aplikaci, která má mnoho vláken. Plánování vláken, které nesdílí prostředky, jak souběžně spustit můžete snížit režijní náklady na synchronizaci a tím zvýšit efektivitu. Další efektivní způsob, jak plánovat úlohy je spuštění kanálů úloh (kde každý úkol zpracovává výstupního předchozím histogramem) na stejném procesoru tak, aby se vstupem každá fáze kanálu je již načteno do mezipaměti.

### <a name="using-preemptive-and-cooperative-scheduling-together"></a>Pomocí plánování společně Preemptive a spolupráce

Plánování spolupráce se nevyřeší všechny problémy s plánováním. Například úkoly, které neposkytují poměrně jiných úloh můžete využívat všech dostupných výpočetních prostředcích a zabránit vidět pokrok jiných úloh. Modulu Runtime souběžnosti využívá výhody efektivita plánování spolupráce zaměřujete záruky rovnost preemptive plánování. Ve výchozím nastavení poskytuje modulu Runtime souběžnosti plánovače spolupráce, který používá algoritmus přebírající práci pro efektivní distribuci práce mezi výpočetní prostředky. Plánovač Concurrency Runtime však také závisí na preemptive Plánovač operační systém poměrně distribuovat prostředky mezi aplikacemi. Můžete také vytvořit vlastní plánovače a zásady plánovače ve svých aplikacích k vytvoření přesnou kontrolu nad provádění vlákna.

[[Horní](#top)]

##  <a name="winapi"></a> Porovnání Concurrency Runtime s Windows API

Microsoft Windows rozhraní, který je obvykle označuje jako rozhraní API Windows (dříve označované jako Win32), poskytuje programovací model, který umožňuje souběžnosti ve svých aplikacích. Modulu Runtime souběžnosti je založena na rozhraní Windows API pro poskytnutí dalších programovacích modelů, které nejsou k dispozici od základního operačního systému.

Modulu Runtime souběžnosti je založena na modelu vlákno rozhraní Windows API a provádí paralelní práci. Také používá rozhraní Windows API Správa paměti a úložiště thread-local se mechanismy. Ve Windows 7 a Windows Server 2008 R2 používá podpora rozhraní Windows API pro uživatele plánovatelná vlákna a počítačů, které mají více než 64 hardwarových vláken. Modulu Runtime souběžnosti rozšiřuje rozhraní Windows API model poskytnutím plánovače úloh spolupráce a algoritmus přebírající práci maximalizovat využití výpočetních prostředků a tím, že umožňuje víc souběžných Plánovač instancí.

### <a name="programming-languages"></a>Programovací jazyky

Rozhraní API Windows programovací jazyk C používá k vystavení programovacího modelu. Modul Concurrency Runtime poskytuje programovací rozhraní C++, který využívá nejnovější funkce v jazyce C++. Například lambda funkce poskytují mechanismus stručné, bezpečnost typů pro definování funkcí paralelní práci. Další informace o nejnovější funkce C++, které používá modulu Runtime souběžnosti, naleznete v tématu [přehled](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="threads-and-thread-pools"></a>Vlákna a fondy vláken

Mechanismus centrálního souběžnost v rozhraní Windows API je vlákno. Obvykle se používá [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) funkce k vytvoření vlákna. I když vlákna je poměrně snadné ho vytvořit a používat, operační systém přiděluje značné množství času a další zdroje informací a spravovat je. Kromě toho i když je zaručeno, že každý podproces přijímat ve stejnou dobu spuštění jako jakékoli jiné vlákno na stejné úrovni priority, přidružené režie potřeba, abyste vytvořili dostatečně velké úlohy. Pro menší nebo další detailnější úkoly můžete zátěž související se souběžností převažují nad výhodou spouštění úloh paralelně.

Fondy vláken jsou jedním ze způsobů, abyste snížili náklady na správu vlákna. Fondy vlastních vláken a implementace fondu vláken, které poskytuje rozhraní API Windows i povolit malé pracovní položky pro efektivní spuštění paralelně. Fondu vláken Windows udržuje pracovních položek do fronty FIFO (FIFO) first-in. Každé pracovní položky se spustí v pořadí, ve kterém byl přidán do fondu.

Modulu Runtime souběžnosti implementuje algoritmus přebírající práci rozšířit FIFO plánovacím mechanismem. Algoritmus přesune do vlákna, které běží mimo pracovní položky úlohy, které ještě nebyly spuštěny. I když algoritmus přebírající práci můžete vyrovnávat zatížení, může také způsobit přeuspořádat pracovní položky. Tento způsob proces může způsobit, že pracovní položky ke spuštění v jiném pořadí, než byla odeslána. To je užitečné s rekurzivní algoritmy, ve kterých je lepší šance, že data se sdílejí mezi úkoly novější než mezi starší. Získání nové položky, které chcete spustit jako první znamená menší počet nezdařených přístupů k mezipaměti a pravděpodobně méně chyb stránky.

Z pohledu operačního systému je krádež pracovní nekalé. Nicméně pokud aplikace implementuje algoritmus nebo spuštění paralelní úlohy, rovnost mezi dílčí úkoly vždy nezáleží. Co důležité je, jak rychle dokončení jedné úlohy. Další algoritmy FIFO je vhodné plánování strategie.

### <a name="behavior-on-various-operating-systems"></a>Chování v různých operačních systémech

Na Windows XP a Windows Vista aplikace, které používají modulu Runtime souběžnosti se chovají podobně, s tím rozdílem, že haldy se výkon v systému Windows Vista.

Ve Windows 7 a Windows Server 2008 R2 operační systém dále podporuje souběžnost a škálovatelnost. Například tyto operační systémy podporovat počítače, které mají více než 64 hardwarových vláken. Abyste mohli využívat tyto nové funkce musí být upravena existující aplikaci, která používá rozhraní Windows API. Ale aplikace, která automaticky používá Concurrency Runtime používá tyto funkce a nevyžaduje změny.

[base.user-mode_scheduling](https://msdn.microsoft.com/library/windows/desktop/dd627187)

[[Horní](#top)]

##  <a name="openmp"></a> Porovnání modelu Concurrency Runtime s OpenMP

Modul Concurrency Runtime umožňuje širokou škálu programovacích modelů. Tyto modely mohou překrývat nebo doplňují modely další knihovny. Tato část porovnává Concurrency Runtime s [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp).

OpenMP – programovací model je definován otevřený standard a nemá jasně definované vazby pro programovací jazyky až po Fortran a jazyka C/C++. Jsou vhodné pro paralelní algoritmy, které jsou iterativní; OpenMP verze 2.0 nebo 2.5 To znamená provádějí paralelní iterace nad určitým polem data. OpenMP – je nejúčinnější, když stupeň paralelismu předem určit a odpovídá prostředcích k dispozici v systému. OpenMP – model je zvlášť vhodné shoda pro vysokovýkonné výpočetní prostředí, ve kterých se velmi rozsáhlých výpočetních problémech distribuují napříč zpracování zdrojů do jednoho počítače. V tomto scénáři se označuje hardwarového prostředí a vývojáři můžou očekávat rozumně exkluzivní přístup k výpočetní prostředky, když se zpracovává algoritmu.

Ale jiné, méně omezené výpočetních prostředí nemusí být dobré nalezena shoda s OpenMP. Rekurzivní problémy (např. algoritmus quicksort nebo hledání tak stromy dat.) jsou například obtížné implementovat pomocí OpenMP. Modulu Runtime souběžnosti doplňuje funkce OpenMP tím, že poskytuje [knihovny Ppl](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) a [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md). Na rozdíl od OpenMP poskytuje modulu Runtime souběžnosti dynamické plánovače, která se přizpůsobí dostupné prostředky a upravuje stupeň paralelismu úloh změnit.

Mnoho funkcí v modulu Runtime souběžnosti je možné rozšířit. Můžete také kombinovat existující funkce k vytvoření nové značky. Protože OpenMP závisí na direktivy kompilátoru, nelze snadno rozšířit.

Další informace o tom, porovná Concurrency Runtime OpenMP a jak migrovat existující kód OpenMP na využití modulu Runtime souběžnosti, naleznete v tématu [migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md).

[[Horní](#top)]

## <a name="see-also"></a>Viz také:

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
[Přehled](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)
