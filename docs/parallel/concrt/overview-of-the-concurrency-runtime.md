---
title: Přehled Concurrency Runtime | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, requirements
- Concurrency Runtime, architecture
- Concurrency Runtime, overview
- Concurrency Runtime, lambda expressions
ms.assetid: 56237d96-10b0-494a-9cb4-f5c5090436c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67f0497f600cf5d528b2c41601b7a02c08771861
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692423"
---
# <a name="overview-of-the-concurrency-runtime"></a>Přehled Concurrency Runtime
Tento dokument obsahuje přehled Concurrency Runtime. Popisuje výhody Concurrency Runtime, kdy ji použít, a způsob jejich součástí interakce mezi sebou a se operační systém a aplikace.  
  
> [!IMPORTANT]
>  V sadě Visual Studio 2015 a novější je Plánovač úloh třídy a souvisejících typů v ppltasks.h už Plánovač úloh Concurrency Runtime. Tyto typy teď použít zachovalo Windows pro lepší výkon a vzájemná funkční spolupráce s Windows synchronizace primitiv. Paralelní algoritmy například parallel_for – nadále používat Plánovač úloh Concurrency Runtime.  
  
##  <a name="top"></a> Oddíly  
 Tento dokument obsahuje následující části:  
  
-   [Proč modul Runtime pro Concurrency je část důležité.](#runtime)  
  
-   [Architektura](#architecture)  
  
-   [Výrazy C++ Lambda](#lambda)  
  
-   [Požadavky](#requirements)  
  
##  <a name="runtime"></a> Proč modul Runtime pro Concurrency je část důležité.  
 Modul runtime pro concurrency poskytuje jednotnost a předvídatelnost aplikací a součástí aplikace, které běžet současně. Jsou dva příklady výhod Concurrency Runtime *plánování úkolů spolupráci* a *spolupráci blokování*.  
  
 Concurrency Runtime používá plánovače úloh spolupráci, který implementuje krádež pracovní algoritmus pro efektivní distribuci pracovní mezi výpočetními prostředky. Představte si třeba aplikace, která má dva vláken, které jsou spravovány nástrojem stejné modulu runtime. Pokud jedno vlákno skončí její naplánované úlohy, je přesměrování zpracování pracovní z jiné vlákno. Tento mechanismus vyrovnává celkové zatížení aplikace.  
  
 Concurrency Runtime také poskytuje primitiv synchronizace, které používají spolupráci blokování synchronizovat přístup k prostředkům. Představte si třeba úlohu, která musí mít výhradní přístup ke sdíleným prostředkům. Spolupráce při blokování, modul runtime pomocí zbývající quantum jinou úlohu provést jako první úloha čeká na prostředek. Tento mechanismus zvýší úroveň maximální využití výpočetních prostředků.  
  
 [[Horní](#top)]  
  
##  <a name="architecture"></a> Architektura  
 Concurrency Runtime je rozdělené do čtyř součástí: paralelní vzory knihovny (PPL), knihovna asynchronních agentů, plánovače úloh a Resource Manager. Tyto součásti nacházet mezi operačního systému a aplikací. Následující obrázek znázorňuje interakci komponenty Concurrency Runtime v rámci operačního systému a aplikací:  
  
 **Architektura Concurrency Runtime**  
  
 ![Architektura Concurrency Runtime](../../parallel/concrt/media/concurrencyrun.png "concurrencyrun")  
  
> [!IMPORTANT]
>  Komponenty plánovače úloh a správce prostředků nejsou k dispozici z aplikace pro univerzální platformu Windows (UWP) nebo při použití třídy úlohy nebo jiné typy v ppltasks.h.  
  
 Concurrency Runtime je vysoce *bez možnosti složení*, tedy můžete kombinovat více stávající funkce. Concurrency Runtime vytvoří mnoha funkcí, jako je například paralelní algoritmy ze součástí nižší úrovně.  
  
 Concurrency Runtime také poskytuje primitiv synchronizace, které používají spolupráci blokování synchronizovat přístup k prostředkům. Další informace o těchto synchronizace primitiv najdete v tématu [synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md).  
  
 Stručný přehled, co jednotlivé komponenty poskytuje a kdy ji použít v následujících částech.  
  
### <a name="parallel-patterns-library"></a>Knihovna PPL (Parallel Patterns Library)  
 Paralelní vzory knihovny (PPL) poskytuje univerzální kontejnery a algoritmy pro provádění podrobného paralelismu. Umožňuje knihovně PPL *imperativní datový paralelismus* tím, že poskytuje paralelní algoritmy, které distribuují výpočtů na kolekce nebo datových sad napříč výpočetních prostředků. Umožňuje také *úkolů paralelismus* tím, že poskytuje objekty úloh, které distribuovat více nezávislých operací do výpočetních prostředků.  
  
 V knihovně paralelní vzory, když máte místní výpočtu, který můžete využít paralelní provádění. Například můžete použít [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus k transformaci existující `for` smyčky tak, aby fungoval paralelně.  
  
 Další informace o knihovně paralelní vzory najdete v tématu [paralelní vzory knihovna PPL ()](../../parallel/concrt/parallel-patterns-library-ppl.md).  
  
### <a name="asynchronous-agents-library"></a>Knihovna asynchronních agentů  
 Knihovna asynchronních agentů (nebo jenom *knihovna agentů*) poskytuje služby na základě objektu actor programovací model a zpráva předávání rozhraní pro hrubý toku dat a paralelní zpracování úlohy. Asynchronní agenti umožňují produktivní využívají latence provedením pracovní jako ostatní součásti čekat na data.  
  
 Knihovna agentů použijte, když máte více entit, které vzájemně komunikovat asynchronně. Můžete například vytvořit agenta, který čte data ze souboru nebo síťového připojení a pak použije předávání rozhraní zpráv k odeslání dat do jiné agenta.  
  
 Další informace o knihovně agentů najdete v tématu [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md).  
  
### <a name="task-scheduler"></a>Plánovač úloh  
 Plánovač úloh plány a koordinuje úlohy v době běhu. Plánovač úloh je spolupráci a používá algoritmus krádež pracovní k dosažení maximální využití prostředků zpracování.  
  
 Concurrency Runtime poskytuje výchozí plánovač, takže není nutné spravovat infrastrukturu podrobnosti. Kvality potřebám vaší aplikace, můžete však také zadat vlastní plánování zásad nebo přidružení konkrétní plánovače s konkrétní úlohy.  
  
 Další informace o Plánovač úloh najdete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
### <a name="resource-manager"></a>Správce prostředků  
 Role správce prostředků je ke správě výpočetních prostředků, jako je například procesory a paměť. Správce prostředků odpoví na úlohy, když se změní za běhu, kde mohou být co nejúčinnější přiřazením prostředky.  
  
 Správce prostředků slouží jako abstrakci přes výpočetních prostředků a primárně komunikuje s Plánovač úloh. I když používáte Resource Manager a systém doladit výkon aplikace a knihovny obvykle používat funkce, které poskytuje knihovna Parallel Patterns Library, knihovna agentů a Plánovač úloh. Tyto knihovny dynamicky znovu vyvážit prostředky mění úloh pomocí Správce prostředků.  
  
 [[Horní](#top)]  
  
##  <a name="lambda"></a> Výrazy C++ Lambda  
 Mnoho typů a algoritmy, které jsou definovány Concurrency Runtime jsou implementované jako šablony jazyka C++. Některé z těchto typů a algoritmy trvat jako parametr rutiny, která provede práci. Tento parametr může být lambda funkce, funkce objektu nebo ukazatel na funkci. Tyto entity jsou také označovány jako *pracovních funkcí* nebo *fungovat rutiny*.  
  
 Lambda – výrazy jsou důležitou součást nového jazyka Visual C++, protože poskytují stručného způsob, jak definovat pracovních funkcí pro paralelní zpracování. Objekty funkcí a ukazatelů na funkce umožňují použití Concurrency Runtime s váš stávající kód. Doporučujeme však při vytvoření nového kódu z důvodu zabezpečení a produktivitu výhody, které obsahují použití výrazů lambda.  
  
 Následující příklad porovnává syntaxe funkce lambda, objektů funkcí a ukazatelů na funkce ve více voláních [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus. Každé volání `parallel_for_each` používá jiný postup vypočítat druhou mocninu každý prvek v [std::array](../../standard-library/array-class-stl.md) objektu.  
  
 [!code-cpp[concrt-comparing-work-functions#1](../../parallel/concrt/codesnippet/cpp/overview-of-the-concurrency-runtime_1.cpp)]  
  
 **Output**  
  
```Output  
1  
256  
6561  
65536  
390625  
```  
  
 Další informace o funkcích lambda v jazyce C++ najdete v tématu [výrazy Lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
 [[Horní](#top)]  
  
##  <a name="requirements"></a> Požadavky  
 Následující tabulka uvádí soubory hlaviček, které jsou přidruženy jednotlivé komponenty Concurrency Runtime:  
  
|Součást|Soubory hlaviček|  
|---------------|------------------|  
|Knihovna PPL (Parallel Patterns Library)|ppl.h<br /><br /> concurrent_queue.h<br /><br /> concurrent_vector.h|  
|Knihovna asynchronních agentů|Agents.h|  
|Plánovač úloh|concrt.h|  
|Správce prostředků|concrtrm.h|  
  
 Concurrency Runtime deklarovaného v souboru [souběžnosti](../../parallel/concrt/reference/concurrency-namespace.md) oboru názvů. (Můžete také použít [souběžnosti](../../parallel/concrt/reference/concurrency-namespace.md), což je alias pro tento obor názvů.) `concurrency::details` Obor názvů podporuje Concurrency Runtime framework a není určena pro použití přímo z vašeho kódu.  
  
 Concurrency Runtime je dodáván jako součást C Runtime Library (CRT). Další informace o tom, jak sestavit aplikaci, která používá CRT najdete v tématu [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).  
  
 [[Horní](#top)]



