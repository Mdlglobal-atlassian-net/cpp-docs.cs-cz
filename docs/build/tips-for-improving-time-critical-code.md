---
title: Tipy pro zlepšení časově kritického kódu
ms.date: 11/04/2016
helpviewer_keywords:
- _lsearch function
- qsort function
- background tasks
- standard sort routines
- clock cycle losses
- code, time-critical
- memory [C++], monitoring usage
- execution, speed improvements
- local heap performance
- optimization [C++], time-critical code
- performance [C++], time-critical code
- threading [C++], performance
- cache [C++], hits and misses
- linear search performance
- page faults
- best practices, time-critical code
- searching [C++], improving performance
- sorting data, improving performance
- threading [C++], best practices
- threading [C++], background tasks
- lists, sorting
- bsearch function
- MFC [C++], performance
- sort routines
- programs [C++], performance
- _lfind function
- heap allocation, time-critical code performance
ms.assetid: 3e95a8cc-6239-48d1-9d6d-feb701eccb54
ms.openlocfilehash: 039b86eec024daf8e3473bba5d89f190507f3cfd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335460"
---
# <a name="tips-for-improving-time-critical-code"></a>Tipy pro zlepšení časově kritického kódu

Psaní rychlého kódu vyžaduje porozumění všem aspektům vaší aplikace a způsobu, jakým komunikuje se systémem. Toto téma navrhuje alternativy k některým z jasnějších technik kódování, které vám pomůžou zajistit uspokojivý chod částí kódu v kritickém čase.

Pro shrnutí, vylepšení časově kritického kódu, je třeba provést následující:

- Zjistěte, které části programu musí být rychlé.

- Zjistěte velikost a rychlost kódu.

- Poznejte náklady na nové funkce.

- Zjistěte minimální práci potřebnou k provedení úlohy.

Chcete-li shromáždit informace o výkonu kódu, můžete použít nástroj sledování výkonu (Perfmon. exe).

## <a name="sections-in-this-article"></a>Části tohoto článku

- [Neúspěšné přístupy do mezipaměti a chyby stránek](#_core_cache_hits_and_page_faults)

- [Řazení a hledání](#_core_sorting_and_searching)

- [MFC a knihovny tříd](#_core_mfc_and_class_libraries)

- [Sdílené knihovny](#vcovrsharedlibraries)

- [Haldy](#_core_heaps)

- [Vlákna](#_core_threads)

- [Malá pracovní sada](#_core_small_working_set)

## <a name="cache-misses-and-page-faults"></a><a name="_core_cache_hits_and_page_faults"></a>Neúspěšné přístupy do mezipaměti a chyby stránek

Neúspěšné přístupy do mezipaměti v interní i externí mezipaměti i chyby stránek (v případě pokynů k sekundárnímu úložišti pro instrukce a data programu) zpomalují výkon programu.

Dosažení mezipaměti CPU může mít za cenu program 10-20 hodinových cyklů. Dosažení externích mezipamětí může mít náklady na 20-40 hodinových cyklů. Selhání stránky může nákladové cykly 1 000 000 hodin (za předpokladu, že procesor zpracovává pokyny 500 000 000/s a čas 2 milisekund pro chybu stránky). Proto je v nejlepším zájmu při provádění programu napsat kód, který sníží počet chyb zmeškaných přístupů do mezipaměti a chyby stránek.

Jedním z důvodů pomalých programů je to, že nastanou větší počet chyb stránek nebo nezpůsobí ukládání mezipaměti častěji, než je nutné. Aby k tomu nedocházelo, je důležité používat datové struktury se správnou místní referencí, což znamená udržení souvisejících věcí dohromady. Někdy se může stát, že datová struktura, která vypadá dobře, je Horrible z důvodu špatného lokálního odkazu a někdy je opak true. Tady jsou dva příklady:

- Dynamicky přidělené propojené seznamy můžou snížit výkon programu, protože když hledáte položku nebo předáte seznam na konec, může každý vynechaný odkaz přijít o mezipaměť nebo způsobit chybu stránky. Implementace seznamu založená na jednoduchých polích může být mnohem rychlejší kvůli lepšímu ukládání do mezipaměti a menšímu počtu chyb stránek, a to i v případě, že by bylo těžké růst pole, stále může být rychlejší.

- Tabulky hash využívající dynamicky přidělené propojené seznamy můžou snížit výkon. Tabulky hash, které používají dynamicky přidělené propojené seznamy pro ukládání obsahu, mohou být prováděny podstatně horší. Ve skutečnosti může být při konečné analýze jednoduché lineární hledání prostřednictvím pole rychlejší (v závislosti na okolnostech). Tabulky hash založené na poli (tzv. "uzavřené hashing") jsou často převedená implementace, která má často výkon.

## <a name="sorting-and-searching"></a><a name="_core_sorting_and_searching"></a>Řazení a hledání

Řazení je ze své podstaty časově náročná v porovnání s mnoha typickými operacemi. Nejlepším způsobem, jak se vyhnout zbytečnému zpomalení, je vyhnout se řazení v kritických časech. Možná budete mít tyto možnosti:

- Odložit řazení do doby nekritického výkonu.

- Seřaďte data k dřívějšímu nekritickému času, který nebudete mít na výkon.

- Seřadit pouze část dat, která skutečně potřebují řazení.

V některých případech můžete seznam sestavit v setříděném pořadí. Buďte opatrní. vzhledem k tomu, že pokud potřebujete vkládat data do seřazeného pořadí, možná budete potřebovat složitější datovou strukturu s slabými místními odkazy, což vede k neúspěšným chybám a chybám stránky. Neexistuje žádný přístup, který funguje ve všech případech. Vyzkoušejte několik přístupů a změřte rozdíly.

Tady jsou některé obecné tipy pro řazení:

- K minimalizaci chyb použijte řazení na skladě.

- Veškerá práce, kterou můžete provést předem, abyste snížili složitost řazení, je smyslem. Pokud se při jednorázovém průchodu vaše data zjednodušují porovnání a snižuje se řazení z (n protokolu n) na O (n), bude to skoro určitě.

- Zamyslete se nad ohledem na použití algoritmu řazení a dat, na kterých očekáváte, aby běžela.

Pro vyhledávání je k dispozici méně alternativních možností než řazení. Pokud je hledání kritické pro čas, binární hledání nebo vyhledávání v tabulce hash je téměř vždy nejlepší, ale stejně jako při řazení, je nutné mít na paměti místní význam. Lineární hledání v malém poli může být rychlejší než binární hledání prostřednictvím datové struktury s velkým počtem ukazatelů, které způsobují chyby stránky nebo Neúspěšné přístupy do mezipaměti.

## <a name="mfc-and-class-libraries"></a><a name="_core_mfc_and_class_libraries"></a>MFC a knihovny tříd

Microsoft Foundation Classes (MFC) může značně zjednodušit psaní kódu. Při psaní kódu kritického pro čas byste měli být vědomi režie vyplývající z některých tříd. Prohlédněte si kód knihovny MFC, který váš kód kritický pro čas používá k zobrazení, jestli splňuje vaše požadavky na výkon. Následující seznam identifikuje třídy a funkce knihovny MFC, o kterých byste měli vědět:

- `CString`Knihovna MFC volá knihovnu run-time jazyka C k dynamickému přidělování paměti pro [CString](../atl-mfc-shared/reference/cstringt-class.md) . Obecně řečeno, `CString` je stejně efektivní jako jakýkoliv jiný dynamicky přidělovaných řetězec. Stejně jako u jakéhokoli dynamicky přiděleného řetězce má režijní náklady na dynamické přidělování a vydanou verzi. Jednoduché `char` pole v zásobníku může často sloužit ke stejnému účelu a je rychlejší. Nepoužívejte `CString` k uložení konstantního řetězce. Místo toho použijte `const char *`. Jakákoli operace, kterou u `CString` objektu provedete, má nějakou režii. Použití [řetězcových funkcí](../c-runtime-library/string-manipulation-crt.md) knihovny run-time může být rychlejší.

- `CArray`[CArray –](../mfc/reference/carray-class.md) poskytuje flexibilitu, že se nejedná o běžné pole, ale program to nemusí potřebovat. Pokud znáte konkrétní omezení pro pole, můžete místo toho použít globální pevné pole. Použijete- `CArray`li, `CArray::SetSize` použijte k určení jeho velikosti a určení počtu prvků, podle kterých se rozrůstá, když je nutné přerozdělení. V opačném případě přidávání prvků může způsobit, že vaše pole bude často znovu přiděleno a zkopírováno, což je neefektivní a může fragmentovat paměť. Všimněte si také, že pokud vložíte položku do pole, `CArray` přesune následné položky v paměti a může být nutné ji zvětšit. Tyto akce můžou způsobit Neúspěšné přístupy do mezipaměti a chyby stránek. Pokud se podíváte na kód, který knihovna MFC používá, můžete si všimnout, že pro zlepšení výkonu můžete napsat něco konkrétnějšího pro váš scénář. Vzhledem `CArray` k tomu, že je šablona, například můžete poskytnout `CArray` specializace pro konkrétní typy.

- `CList`[CList –](../mfc/reference/clist-class.md) je dvakrát propojený seznam, takže vkládání elementů je rychlé na pozici Head, Tail a na známé pozici (`POSITION`) v seznamu. Vyhledávání elementu podle hodnoty nebo indexu vyžaduje sekvenční hledání, což může být pomalé v případě, že je seznam dlouhý. Pokud váš kód nevyžaduje dvakrát propojený seznam, budete možná chtít znovu zvážit použití `CList`. Když použijete jednotlivě propojený seznam, ušetří se tím režie aktualizace dalšího ukazatele pro všechny operace a také paměti pro tento ukazatel. Další paměť není Skvělé, ale je to další příležitost pro Neúspěšné přístupy do mezipaměti nebo chyby stránek.

- `IsKindOf`Tato funkce může vygenerovat mnoho volání a získat přístup k velkému množství paměti v různých oblastech dat, což vede k špatnému národnímu vztahu. Je užitečné pro sestavení ladění (například ve volání kontrolního výrazu), ale pokusit se ho vyhnout v sestavení pro vydání.

- `PreTranslateMessage`Použijte `PreTranslateMessage` v případě, že konkrétní stromová struktura systému Windows potřebuje jiné klávesové zkratky nebo když je nutné do tohoto čerpadla zpráv vložit zpracování zpráv. `PreTranslateMessage`změní odesílací zprávy knihovny MFC. Pokud přepíšete `PreTranslateMessage`, udělejte to pouze na úrovni, kterou potřebujete. Například není nutné potlačit `CMainFrame::PreTranslateMessage` , pokud vás zajímá pouze zprávy, které se budou napojovat do podřízených objektů konkrétního zobrazení. Místo `PreTranslateMessage` toho přepište pro třídu zobrazení.

   Nepoužívejte normální cestu pro odeslání pomocí `PreTranslateMessage` rutiny k zpracování jakékoli zprávy odeslané do jakéhokoli okna. Pro tento účel použijte [procedury okna](../mfc/registering-window-classes.md) a mapy zpráv knihovny MFC.

- `OnIdle`Nečinné události mohou nastat v časech, které neočekáváte, například `WM_KEYDOWN` mezi `WM_KEYUP` událostmi a. Časovače můžou být efektivnějším způsobem, jak váš kód aktivovat. Nevynuťte `OnIdle` opakované volání vygenerováním falešných zpráv nebo vrácením `TRUE` z přepsání `OnIdle`, které nikdy nedovolí vašemu vláknu přejít do režimu spánku. Znovu, časovač nebo samostatné vlákno může být vhodnější.

## <a name="shared-libraries"></a><a name="vcovrsharedlibraries"></a>Sdílené knihovny

Opětovné použití kódu je žádoucí. Pokud však použijete kód někoho jiného, měli byste se ujistit, že přesně víte, co v nich dělá v případě, kdy je pro vás důležitý výkon. Nejlepším způsobem, jak to pochopit, je prokrokování zdrojového kódu nebo měření pomocí nástrojů, jako je PView nebo sledování výkonu.

## <a name="heaps"></a><a name="_core_heaps"></a>Haldy

Použijte více hald s uvážením. Další haldy vytvořené pomocí `HeapCreate` a `HeapAlloc` umožňují spravovat a následně disponovat související sadou přidělení. Nepotvrzujte příliš mnoho paměti. Pokud používáte více hald, věnujte zvláštní pozornost množství paměti, která je původně potvrzena.

Místo více hald lze použít funkce pomocníka k rozhraní mezi kódem a výchozí haldou. Pomocné funkce usnadňují vlastní strategie přidělování, které mohou zlepšit výkon aplikace. Například pokud často provádíte menší přidělení, je vhodné lokalizovat tato přidělení do jedné části výchozí haldy. Můžete přidělit velký blok paměti a potom použít pomocnou funkci k rozdělení z tohoto bloku. Pokud to uděláte, nebudete mít k dispozici další haldy s nepoužitou pamětí, protože přidělení vychází z výchozí haldy.

V některých případech však může použití výchozí haldy snížit národní prostředí. Pro měření efektů přesunutí objektů z haldy do haldy použijte program Prohlížeč procesů, Spy + + nebo sledování výkonu.

Změřte své haldy, abyste se mohli přihlédnout ke každému přidělení haldy. Použijte [rutiny ladění](/visualstudio/debugger/crt-debug-heap-details) běhového prostředí C k vytvoření kontrolního bodu a výpisu paměti haldy. Výstup můžete načíst do tabulkového programu, jako je Microsoft Excel, a použít k zobrazení výsledků kontingenční tabulky. Všimněte si celkového počtu, velikosti a distribuce přidělení. Porovnejte je s velikostí pracovních sad. Podívejte se také na clustering objektů s příbuznou velikostí.

K monitorování využití paměti můžete také použít čítače výkonu.

## <a name="threads"></a><a name="_core_threads"></a>Vláken

Pro úlohy na pozadí může být efektivní nečinné zpracování událostí rychlejší než použití vláken. V programu s jedním vláknem je snazší pochopit informace o lokálních odkazech.

Dobrým pravidlem je použití vlákna pouze v případě, že je oznámení operačního systému, které jste zablokovali, v kořenu práce na pozadí. Vlákna představují nejlepší řešení v takovém případě, protože je nepraktické zablokovat hlavní vlákno v události.

Vlákna také představují problémy s komunikací. Je nutné spravovat komunikační propojení mezi vlákny, seznamem zpráv nebo přidělením a použitím sdílené paměti. Správa komunikačního propojení obvykle vyžaduje synchronizaci, aby nedocházelo k problémům s konflikty časování a zablokování. Tato složitost může snadno zapínat chyby a problémy s výkonem.

Další informace naleznete v tématu [zpracování smyčky nečinnosti](../mfc/idle-loop-processing.md) a [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="small-working-set"></a><a name="_core_small_working_set"></a>Malá pracovní sada

Menší pracovní sady znamenají lepší lokální informace, méně chyb stránek a další přístupy do mezipaměti. Pracovní sada procesu je nejbližší metrika, kterou operační systém přímo poskytuje k měření národní části Reference.

- K nastavení horních a dolních omezení pracovní sady použijte [SetProcessWorkingSetSize](/windows/win32/api/winbase/nf-winbase-getprocessworkingsetsize).

- K získání horních a dolních omezení pracovní sady použijte [GetProcessWorkingSetSize](/windows/win32/api/winbase/nf-winbase-setprocessworkingsetsize).

- Chcete-li zobrazit velikost pracovní sady, použijte příkaz Spy + +.

## <a name="see-also"></a>Viz také

[Optimalizace kódu](optimizing-your-code.md)
