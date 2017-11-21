---
title: "Porovnání modelu Concurrency Runtime s jinými modely souběžného zpracování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Concurrency Runtime, compared to other models
ms.assetid: d8b9a1f4-f15f-43c3-a5b4-c0991edf9c86
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a20df7ed057c11f8d8879e1373cc7466982d871b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="comparing-the-concurrency-runtime-to-other-concurrency-models"></a>Porovnání modelu Concurrency Runtime s jinými modely souběžného zpracování
Tento dokument popisuje rozdíly mezi funkcí a programovacích modelů Concurrency Runtime a další technologie. Podle porozumět tomu, jak výhody Concurrency Runtime porovnávají výhody jinými programovací modely, můžete vybrat technologie, která nejlépe splňuje požadavky aplikací.  
  
 Pokud aktuálně používáte jiný programovací model, například Windows fondu vláken nebo OpenMP, nejsou v situacích, kde může být vhodné pro migraci do Concurrency Runtime. Například v tématu [migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md) popisuje, kdy může být vhodné pro migraci z OpenMP do Concurrency Runtime. Ale pokud budete spokojeni s výkonem aplikací a aktuální podporu ladění, není migrace nutná.  
  
 Funkce a výhody produktivitu Concurrency Runtime můžete použít tak, aby doplňovala existující aplikace, který používá jiný model souběžnosti. Concurrency Runtime nemůže zaručit, Vyrovnávání zatížení při víc plánovače úloh pokouší o stejné výpočetní prostředky. Ale při zatížení se nepřekrývají, tento efekt je minimální.  
  
##  <a name="top"></a>Oddíly  
  
-   [Porovnání preemptivní plánování pro spolupráci plánování](#models)  
  
-   [Porovnání modelu Concurrency Runtime s rozhraním API systému Windows](#winapi)  
  
-   [Porovnání modelu Concurrency Runtime s OpenMP](#openmp)  
  
##  <a name="models"></a>Porovnání preemptivní plánování pro spolupráci plánování  
 Preemptivní modelu a spolupráce plánování modely dvěma způsoby běžné povolit více úkolů sdílet výpočetní prostředky, například procesory nebo hardwaru vláken.  
  
### <a name="preemptive-and-cooperative-scheduling"></a>Preemptivní a spolupráci plánování  
 *Preemptivní plánování* kruhového dotazování, na základě priority mechanismus, který dává každý úkol výhradní přístup k výpočetnímu prostředku v daném časovém období a dojde k přepnutí do jiná úloha. Preemptivní plánování je běžné v multitasking operační systémy, třeba Windows*. Plánování spolupráci* mechanismus, který poskytuje každý úkol výhradní přístup k výpočetních prostředků, dokud na dokončení úlohy nebo úlohu poskytuje přístup k prostředku. Concurrency Runtime používá k dosažení maximální využití prostředků zpracování spolupráci plánování spolu s plánovači preemptivní operačního systému.  
  
### <a name="differences-between-preemptive-and-cooperative-schedulers"></a>Rozdíly mezi preemptivní a spolupráci plánovače  
 Preemptivní plánovače se snaží poskytnout více vláken rovna přístup k výpočetních prostředků, která zajistí, že každé vlákno umožňuje průběh. Na počítačích, které mají mnoho výpočetních prostředků zajištění správného přístup stane méně problematické; zajistíte efektivní využití prostředků stane však více problematické.  
  
 Scheduler preemptivní režimu jádra vyžaduje kód aplikace, který závisí na operačním systému k rozhodnutí pro plánování. Naopak umožňuje spolupráci plánovače uživatelského režimu kódu aplikace, aby vlastní plánovací rozhodnutí. Vzhledem k tomu spolupráci plánování umožňuje mnoho plánování rozhodnutí, která má být provedeno aplikací, snižuje mnohem režie, která souvisí se režimu jádra synchronizací. Spolupráci scheduler odkládat obvykle údaje plánovací rozhodnutí s jádrem operačního systému, když nemá žádné další kroky při plánování. Spolupráci scheduler odkládat údaje také Plánovač operačního systému při blokování operace, které informace se předávají do jádra, ale není operace oznamovat Plánovač uživatelského režimu.  
  
### <a name="cooperative-scheduling-and-efficiency"></a>Plánování spolupráci a efektivity  
 Preemptivní plánovačem je rovna všechnu práci, který má stejnou úrovní priority. Preemptivní scheduler plánuje obvykle vláken v pořadí, ve kterém jsou vytvořeny. Preemptivní scheduler navíc poskytuje každé vlákno časovém intervalu způsobem kruhového dotazování na základě priority přístup z více vláken. I když tento mechanismus nabízí rovnosti (každých vlákno umožňuje postup směrem vpřed), obsahuje některé náklady efektivitu. Například mnoho algoritmy náročné na výpočetní nevyžadují rovnosti. Místo toho je důležité, aby související úkoly dokončí v nejméně celkovou dobu. Plánování spolupráci umožňuje aplikaci efektivněji plánování práce. Představte si třeba aplikace, která má velký počet vláken. Plánování vláken, které nesdílí prostředky spuštěny současně, můžete snížit režijní náklady na synchronizaci a tím zvýšit efektivitu. Jiné efektivní způsob, jak naplánovat úlohy je spuštění kanálů úloh (kde každý úkol funguje na výstup předchozí) na stejném procesoru tak, aby vstupní u každé fáze kanálu je již načten do mezipaměti.  
  
### <a name="using-preemptive-and-cooperative-scheduling-together"></a>Pomocí preemptivní a spolupráci plánování společně  
 Plánování spolupráci všechny plánování problémy nevyřeší. Úlohy, které zisk poměrně na jiné úlohy, například můžete využívat všechny dostupné výpočetní prostředky a zabránit dalších úloh v průběhu provádění. Concurrency Runtime používá efektivitu výhod spolupráci plánování aby doplňovala záruky rovnosti preemptivní plánování. Ve výchozím nastavení poskytuje Concurrency Runtime spolupráci plánovače, který používá algoritmus krádež pracovní pro efektivní distribuci pracovní mezi výpočetní prostředky. Plánovač Concurrency Runtime však také závisí na preemptivní Plánovač operačního systému poměrně distribuovat prostředky mezi aplikacemi. Můžete také vytvořit vlastní plánovače a zásady plánovače ve svých aplikacích k vytvoření jemně odstupňovanou kontrolu nad provádění vlákna.  
  
 [[Horní](#top)]  
  
##  <a name="winapi"></a>Porovnání modelu Concurrency Runtime s rozhraním API systému Windows  
 Microsoft Windows rozhraní, která je obvykle označována jako rozhraní API systému Windows (a dříve označované jako Win32), poskytuje programovací model, který umožňuje souběžnosti v aplikacích. Concurrency Runtime založený na rozhraní API systému Windows k poskytování dalších programovací modely, které nejsou k dispozici prostřednictvím příslušný operační systém.  
  
 Concurrency Runtime založený na rozhraní API systému Windows modelu vláken pro paralelní práci. Také používá rozhraní API systému Windows Správa paměti a úložiště thread-local mechanismy. V systému Windows 7 a Windows Server 2008 R2 využívá podporu rozhraní API systému Windows pro které lze uživatele plánovat vláken a počítačů, které mají víc než 64 vláken hardwaru. Concurrency Runtime rozšiřuje možnosti rozhraní API systému Windows poskytnutím plánovače úloh spolupráci a algoritmus krádež pracovní maximalizovat využití výpočetních prostředků a povolením více souběžných scheduler instancí.  
   
### <a name="programming-languages"></a>Programovací jazyky  
 Rozhraní API systému Windows používá programovací jazyk C ke zveřejnění programovací model. Concurrency Runtime poskytuje programovací rozhraní C++, který využívá nejnovější funkce v jazyce C++. Například lambda funkce poskytují mechanismus stručného, bezpečnost typů pro definování paralelní pracovních funkcí. Další informace o nejnovější funkce C++, které používá Concurrency Runtime najdete v tématu [přehled](../../parallel/concrt/asynchronous-message-blocks.md).  
  
### <a name="threads-and-thread-pools"></a>Vláken a fondy vláken  
 Mechanismus centrální souběžnost v rozhraní API systému Windows je vlákno. Obvykle se používá [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) funkce vytvořit vláken. I když jsou poměrně snadné vytváření a používání vláken, operační systém přiděluje významné množství času a další prostředky spravovat. Kromě toho Přestože se každý podproces záruku, že pro příjem ve stejnou dobu provádění jako jiné vlákno se stejnou úrovní priority, přidruženého režie potřeba, abyste vytvořili dostatečně velké úlohy. Pro menší nebo podrobnějšího úlohy může zatížení, který je přidružen souběžnosti převáží nad Výhodou spuštění úlohy paralelně.  
  
 Fondy vláken jsou jeden způsob, jak snížit náklady na správu přístup z více vláken. Fondy vlastní vláken a implementace fondu vláken, která poskytuje rozhraní API systému Windows, jak povolit malé pracovních položek pro efektivní spuštění paralelně. Fond vláken Windows udržuje pracovních položek ve frontě použity first-in. Každé pracovní položky je spuštěn v pořadí, ve kterém byl přidán do fondu.  
  
 Concurrency Runtime implementuje algoritmus krádež pracovní rozšířit FIFO plánování mechanismus. Algoritmus přesune úlohy, které ještě nebyly spustili vláken, které dostatek pracovních položek. I když algoritmus krádež pracovní můžou vyrovnávat zatížení, může také způsobit přeuspořádat pracovní položky. Tento způsob proces může způsobit pracovní položky pro spuštění v jiném pořadí, než byla odeslána. To je užitečné s rekurzivní algoritmů, kde je lepší šance, že data je sdílen novější úlohy než mezi starší. Získávání nové položky, které chcete spustit jako první znamená méně Neúspěšné přístupy do mezipaměti a které by mohly mít méně chyb stránek.  
  
 Z pohledu operačního systému je krádež pracovní nekalé. Ale pokud aplikace implementuje algoritmus nebo úloha pro spuštění paralelně, rovné zacházení s dílčí úkoly vždy nezáleží. Co vás je, jak rychle celkové úkol dokončí. Jiné algoritmy FIFO je vhodné plánování strategie.  
  
### <a name="behavior-on-various-operating-systems"></a>Chování v různých operačních systémech  
 V systému Windows XP a Windows Vista aplikace, které používají Concurrency Runtime chovají podobně, s tím rozdílem, že haldy výkon je vyšší, v systému Windows Vista.  
  
 Ve Windows 7 a Windows Server 2008 R2 podporuje operační systém další souběžnosti a škálovatelnost. Například tyto operační systémy podporují počítačů, které mají víc než 64 vláken hardwaru. Existující aplikace, která používá rozhraní API systému Windows musíte změnit a využít těchto nových funkcí. Aplikace, která používá Concurrency Runtime automaticky však používá tyto funkce a nevyžaduje změny.  
  
 [Base.User mode_scheduling](http://msdn.microsoft.com/library/windows/desktop/dd627187)  
  
 [[Horní](#top)]  
  
##  <a name="openmp"></a>Porovnání modelu Concurrency Runtime s OpenMP  
 Concurrency Runtime umožňuje celou řadu programovacích modelů. Tyto modely můžou překrývat nebo doplňují modely další knihovny. Tato část porovná Concurrency Runtime s [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp).  
  
 Programovací model OpenMP je určené o otevřený standard a je dobře definovaný vazby na Fortran a C/C++ programovací jazyky. Jsou vhodné pro paralelní algoritmy, které jsou iterativní; OpenMP verze 2.0 a 2.5 To znamená že provádět paralelní iterace přes pole dat. OpenMP je nejúčinnější, když stupně paralelního zpracování je předem určit a odpovídá dostupných prostředků systému. OpenMP model se zejména dobrý shodu vysoce výkonné výpočty, kde jsou velmi velké výpočetní problémy distribuovány na zpracování prostředků do jednoho počítače. V tomto scénáři je známý hardwarového prostředí a vývojář přiměřeně očekávat výhradní přístup k výpočetních prostředků, když se spustí algoritmus.  
  
 Ale jiné, méně omezené výpočetních prostředí nemusí být funkční odpovídající OpenMP. Například jsou obtížné implementovat pomocí OpenMP rekurzivní problémy (například algoritmus quicksort nebo vyhledávání stromu dat). Concurrency Runtime doplňuje tím, že poskytuje možnosti OpenMP [Parallel Library vzory](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) a [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md). Na rozdíl od OpenMP poskytuje Concurrency Runtime dynamické plánovače, který přizpůsobí dostupné prostředky a upraví stupně paralelního zpracování mění úlohy.  
  
 Mnoho funkcí v Concurrency Runtime lze rozšířit. Můžete také kombinovat stávajících funkcí, chcete-li vytvořit nové. Protože OpenMP závisí na direktivy kompilátoru, nelze snadno rozšířit.  
  
 Další informace o tom, porovná Concurrency Runtime OpenMP a jak migrovat existující kód OpenMP na využití modulu Concurrency Runtime, najdete v části [migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md).  
  
 [[Horní](#top)]  
  
## <a name="see-also"></a>Viz také  
 [Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)     
 [Přehled](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Knihovna Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)   
 [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)
