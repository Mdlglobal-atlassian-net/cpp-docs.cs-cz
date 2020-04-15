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

Psaní rychlého kódu vyžaduje pochopení všech aspektů vaší aplikace a způsobu interakce se systémem. Toto téma navrhuje alternativy k některé z více zřejmé kódování techniky, které vám pomohou zajistit, že časově kritické části kódu provádět uspokojivě.

Chcete-li shrnout, zlepšení časově kritický kód vyžaduje, abyste:

- Vědět, které části vašeho programu musí být rychlý.

- Znát velikost a rychlost vašeho kódu.

- Znát náklady na nové funkce.

- Znát minimální práci potřebnou k dokončení práce.

Chcete-li získat informace o výkonu kódu, můžete použít sledování výkonu (perfmon.exe).

## <a name="sections-in-this-article"></a>Oddíly v tomto článku

- [Počet neúspěšných přístupů do mezipaměti a chyb stránky](#_core_cache_hits_and_page_faults)

- [Řazení a vyhledávání](#_core_sorting_and_searching)

- [Knihovny knihovny Knihovny mfc a třídy](#_core_mfc_and_class_libraries)

- [Sdílené knihovny](#vcovrsharedlibraries)

- [Hromady](#_core_heaps)

- [Vlákna](#_core_threads)

- [Malá pracovní sada](#_core_small_working_set)

## <a name="cache-misses-and-page-faults"></a><a name="_core_cache_hits_and_page_faults"></a>Počet neúspěšných přístupů do mezipaměti a chyb stránky

Zmeškané přístupy do mezipaměti v interní i externí mezipaměti, stejně jako chyby stránky (jít do sekundárního úložiště pro instrukce programu a data) zpomalují výkon programu.

Přístupdo mezipaměti cpu může stát váš program 10-20 hodin cykly. Externí přístup do mezipaměti může stát 20-40 hodin cykly. Chyba stránky může stát jeden milion cyklů hodin (za předpokladu, že procesor, který zpracovává 500 milionů instrukcí za sekundu a čas 2 milisekundy pro chybu stránky). Proto je v nejlepším zájmu spuštění programu psát kód, který sníží počet zmeškaných přístupů do mezipaměti a chyb stránky.

Jedním z důvodů pomalých programů je to, že častěji, než je nutné, berou více chyb stránky nebo zmeškají mezipaměť. Chcete-li tomu zabránit, je důležité používat datové struktury s dobrou referenční lokalitou, což znamená, že udržujete související věci pohromadě. Někdy se datová struktura, která vypadá skvěle, ukáže jako hrozná kvůli špatné referenční lokalitě a někdy je to pravda. Tady jsou dva příklady:

- Dynamicky přidělené propojené seznamy mohou snížit výkon programu, protože při hledání položky nebo při procházení seznamu až do konce může každý přeskočený odkaz zmeškat mezipaměť nebo způsobit chybu stránky. Seznam implementace založená na jednoduchých polích může být ve skutečnosti mnohem rychlejší z důvodu lepší ukládání do mezipaměti a méně chyb stránky dokonce - s ohledem na skutečnost, že pole by bylo těžší růst, to ještě může být rychlejší.

- Tabulky hash, které používají dynamicky přidělené propojené seznamy, mohou snížit výkon. Podle rozšíření může dojít k mnohem horším výsledkům tabulek hash, které k ukládání obsahu používají dynamicky přidělené propojené seznamy. Ve skutečnosti v konečné analýze může být jednoduché lineární vyhledávání prostřednictvím pole ve skutečnosti rychlejší (v závislosti na okolnostech). Tabulky hash založené na poli (tzv. uzavřené hašování) jsou často přehlíženou implementací, která má často vynikající výkon.

## <a name="sorting-and-searching"></a><a name="_core_sorting_and_searching"></a>Řazení a vyhledávání

Řazení je ze své podstaty časově náročné ve srovnání s mnoha typickými operacemi. Nejlepším způsobem, jak se vyhnout zbytečnému zpomalení, je vyhnout se třídění v kritických časech. Můžete být schopni:

- Odložit řazení do času nekritického pro výkon.

- Seřaďte data v dřívějším čase, který není kritický pro výkon.

- Seřaďte pouze tu část dat, která skutečně potřebuje řazení.

Někdy můžete vytvořit seznam v seřazené pořadí. Buďte opatrní, protože pokud potřebujete vložit data v seřazené maješky, můžete vyžadovat složitější strukturu dat se špatnou lokalitou odkazu, což vede k chybě mezipaměti a chybám stránek. Neexistuje žádný přístup, který funguje ve všech případech. Vyzkoušejte několik přístupů a změřte rozdíly.

Zde je několik obecných tipů pro řazení:

- Použijte třídu akcií k minimalizaci chyb.

- Jakákoli práce, kterou můžete udělat předem, abyste snížili složitost tohoto druhu, stojí za to. Pokud jednorázový průchod přes vaše data zjednodušuje porovnání a snižuje řazení z O(n log n) na O(n), budete téměř jistě vyjít dopředu.

- Přemýšlejte o lokalitě odkazu algoritmu řazení a na data, která očekáváte, že bude spuštěna.

Existuje méně alternativ pro vyhledávání než pro řazení. Pokud je hledání kritické pro čas, je hledání binárního vyhledávání nebo vyhledávání tabulky hash téměř vždy nejlepší, ale stejně jako při řazení je třeba mít na paměti lokalitu. Lineární vyhledávání přes malé pole může být rychlejší než binární vyhledávání prostřednictvím datové struktury s velkým množstvím ukazatelů, které způsobují chyby stránky nebo netrefení do mezipaměti.

## <a name="mfc-and-class-libraries"></a><a name="_core_mfc_and_class_libraries"></a>Knihovny knihovny Knihovny mfc a třídy

Třídy Microsoft Foundation (MFC) může výrazně zjednodušit psaní kódu. Při psaní kódu kritické ho času, měli byste si být vědomi režie vlastní v některých tříd. Zkontrolujte kód knihovny MFC, který používá váš kód kritický pro čas, abyste zjistili, zda splňuje vaše požadavky na výkon. Následující seznam identifikuje třídy a funkce knihovny MFC, o kterých byste měli vědět:

- `CString`Knihovna MFC volá knihovnu c run-time k dynamickému přidělení paměti pro [řetězec CString.](../atl-mfc-shared/reference/cstringt-class.md) Obecně řečeno, `CString` je stejně efektivní jako jakýkoli jiný dynamicky přidělený řetězec. Stejně jako u všech dynamicky přidělených řetězců má režii dynamické alokace a uvolnění. Jednoduché `char` pole v zásobníku může často sloužit stejnému účelu a je rychlejší. Nepoužívejte k `CString` uložení konstantní řetězec. Místo toho použijte `const char *`. Každá operace, kterou `CString` provedete s objektem, má určitou režii. Použití [funkcí řetězce](../c-runtime-library/string-manipulation-crt.md) knihovny za běhu může být rychlejší.

- `CArray`[CArray](../mfc/reference/carray-class.md) poskytuje flexibilitu, že běžné pole není, ale váš program nemusí potřebovat. Pokud znáte konkrétní omezení pro pole, můžete místo toho použít globální pevné pole. Pokud používáte `CArray` `CArray::SetSize` , použijte k určení jeho velikost a určit počet prvků, o které se zvětšuje, když je nutné přerozdělení. V opačném případě může přidání prvků způsobit, že pole bude často přerozděleno a zkopírováno, což je neefektivní a může fragmentovat paměť. Také uvědomte, že pokud vložíte `CArray` položku do pole, přesune následné položky v paměti a může být nutné rozšířit pole. Tyto akce mohou způsobit nedoletové chybě mezipaměti a chyby stránky. Pokud se podíváte na kód, který používá knihovna MFC, můžete vidět, že můžete napsat něco konkrétnějšího pro váš scénář ke zlepšení výkonu. Vzhledem k tomu, `CArray` že je `CArray` šablona, například můžete poskytnout specializace pro určité typy.

- `CList`[CList](../mfc/reference/clist-class.md) je dvakrát propojený seznam, takže vkládání prvků je rychlé v čele, ocasu`POSITION`a na známé pozici ( ) v seznamu. Vyhledání prvku podle hodnoty nebo indexu vyžaduje sekvenční vyhledávání, které však může být pomalé, pokud je seznam dlouhý. Pokud váš kód nevyžaduje dvojnásob propojený seznam, můžete znovu zvážit `CList`použití . Pomocí singly propojeného seznamu uloží režii aktualizace další ukazatel pro všechny operace, jakož i paměti pro tento ukazatel. Další paměť není skvělá, ale je to další příležitost pro nepřístupy do mezipaměti nebo chyby stránky.

- `IsKindOf`Tato funkce může generovat mnoho volání a přístup k velké množství paměti v různých datových oblastech, což vede k chybné lokalitě odkazu. Je užitečné pro sestavení ladění (v ASSERT volání, například), ale zkuste se vyhnout jeho použití v sestavení verze.

- `PreTranslateMessage`Použijte, `PreTranslateMessage` když určitý strom oken potřebuje různé akcelerátory klávesnice nebo když je nutné vložit zpracování zpráv do čerpadla zprávy. `PreTranslateMessage`změní zprávy odeslání knihovny MFC. Pokud přepíšete `PreTranslateMessage`, uvažte pouze na potřebné úrovni. Například není nutné přepsat, `CMainFrame::PreTranslateMessage` pokud máte zájem pouze o zprávy, které se zobrazují dětem určitého zobrazení. Místo `PreTranslateMessage` toho přepište pro třídu zobrazení.

   Neobcházet normální cestu odeslání `PreTranslateMessage` pomocí zpracování jakékoli zprávy odeslané do libovolného okna. K tomuto účelu použijte [procedury okna](../mfc/registering-window-classes.md) a mapy zpráv knihovny MFC.

- `OnIdle`Nečinnosti události může dojít v době, `WM_KEYDOWN` kterou `WM_KEYUP` neočekáváte, například mezi a události. Časovače může být efektivnější způsob, jak spustit kód. Nenuťte `OnIdle` opakovaně volat generováním falešných zpráv nebo `TRUE` vždy vrácením `OnIdle`z přepsání aplikace , které by nikdy neumožnilo, aby vaše vlákno usnulo. Opět platí, že časovač nebo samostatné vlákno může být vhodnější.

## <a name="shared-libraries"></a><a name="vcovrsharedlibraries"></a>Sdílené knihovny

Opětovné použití kódu je žádoucí. Pokud však budete používat kód někoho jiného, měli byste se ujistit, že přesně víte, co dělá v těch případech, kdy je pro vás výkon kritický. Nejlepší způsob, jak to pochopit, je krokování zdrojového kódu nebo měření pomocí nástrojů, jako je PView nebo Sledování výkonu.

## <a name="heaps"></a><a name="_core_heaps"></a>Hromady

Používejte více hald y s diskrétností. Další hromady vytvořené `HeapCreate` `HeapAlloc` s a umožňují spravovat a potom vyřadit související sadu přidělení. Nezavazuj příliš mnoho paměti. Pokud používáte více hromady, věnujte zvláštní pozornost množství paměti, která je původně potvrzena.

Namísto více hald, můžete použít pomocné funkce rozhraní mezi kódem a výchozí haldy. Pomocné funkce usnadňují vlastní strategie přidělování, které mohou zlepšit výkon vaší aplikace. Například pokud často provádíte malá přidělení, můžete chtít lokalizovat tato přidělení do jedné části výchozí haldy. Můžete přidělit velký blok paměti a potom použít pomocnou funkci pro dílčí přidělení z tohoto bloku. Pokud tak učiníte, nebudete mít další haldy s nevyužitou pamětí, protože přidělení přichází z výchozí haldy.

V některých případech však pomocí výchozí haldy může snížit lokalitu odkazu. Pomocí prohlížeče procesů, Spy++ nebo Sledování výkonu můžete měřit účinky přesouvání objektů z haldy na haldu.

Změřte haldy, abyste mohli účet pro každý příděl na haldě. Použijte c run-time [ladění haldy rutiny](/visualstudio/debugger/crt-debug-heap-details) kontrolníbod a výpis haldy. Můžete si přečíst výstup do tabulkového procesoru, jako je microsoft excel, a zobrazit výsledky pomocí kontingenčních tabulek. Poznamenejte si celkový počet, velikost a rozdělení přidělení. Porovnejte je s velikostí pracovních sad. Podívejte se také na clustering související velikosti objektů.

Čítače výkonu můžete také použít ke sledování využití paměti.

## <a name="threads"></a><a name="_core_threads"></a>Vlákna

Pro úlohy na pozadí efektivní nečinné zpracování událostí může být rychlejší než pomocí podprocesů. Je snazší pochopit lokalitu odkazu v jednovláknovém programu.

Dobrým pravidlem je použít vlákno pouze v případě, že oznámení operačního systému, které zablokujete, je v kořenovém adresáři práce na pozadí. Vlákna jsou nejlepším řešením v takovém případě, protože je nepraktické blokovat hlavní vlákno na události.

Vlákna také představují problémy s komunikací. Je nutné spravovat komunikační spojení mezi podprocesy, se seznamem zpráv nebo přidělením a použitím sdílené paměti. Správa komunikačního spojení obvykle vyžaduje synchronizaci, aby se zabránilo sporům a problémům s zablokováním. Tato složitost může snadno proměnit chyby a problémy s výkonem.

Další informace naleznete [v tématu Nečinné zpracování smyčky](../mfc/idle-loop-processing.md) a [multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="small-working-set"></a><a name="_core_small_working_set"></a>Malá pracovní sada

Menší pracovní sady znamenají lepší referenční lokalitu, méně chyb stránek a více přístupů do mezipaměti. Pracovní sada procesu je nejbližší metrika, kterou operační systém přímo poskytuje pro měření referenční lokality.

- Chcete-li nastavit horní a dolní hranice pracovní sady, použijte [SetProcessWorkingSetSize](/windows/win32/api/winbase/nf-winbase-getprocessworkingsetsize).

- Chcete-li získat horní a dolní hranice pracovní sady, použijte [GetProcessWorkingSetSize](/windows/win32/api/winbase/nf-winbase-setprocessworkingsetsize).

- Chcete-li zobrazit velikost pracovní sady, použijte Spy++.

## <a name="see-also"></a>Viz také

[Optimalizace kódu](optimizing-your-code.md)
