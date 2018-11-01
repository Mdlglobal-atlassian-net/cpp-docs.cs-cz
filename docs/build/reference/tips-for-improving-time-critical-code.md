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
ms.openlocfilehash: 081c8b46d03abf8257cc9bea642db93918f97429
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536939"
---
# <a name="tips-for-improving-time-critical-code"></a>Tipy pro zlepšení časově kritického kódu

Zápis rychlý kód vyžaduje pochopení všechny aspekty vaší aplikace a jak komunikuje se službou systému. Toto téma navrhuje alternativy k některým jasnější technikám kódování vám pomohou zajistit uspokojivě provádět náročné části kódu.

Souhrnně řečeno, zlepšení časově kritického kódu vyžaduje, aby vás:

- Vědět, které části programu musí být rychlé.

- Vědět, velikost a rychlost kódu.

- Vědět, náklady na nové funkce.

- Zjistěte minimální úsilí nutné k provedení úlohy.

Pro shromažďování informací o výkon kódu, můžete použít nástroje Sledování výkonu (perfmon.exe).

## <a name="sections-in-this-article"></a>Části v tomto článku

- [Neúspěšné přístupy do mezipaměti a stránkování](#_core_cache_hits_and_page_faults)

- [Řazení a vyhledávání](#_core_sorting_and_searching)

- [Knihovny MFC a knihovny tříd](#_core_mfc_and_class_libraries)

- [Sdílené knihovny](#vcovrsharedlibraries)

- [Haldy](#_core_heaps)

- [Vlákna](#_core_threads)

- [Malé pracovní sady](#_core_small_working_set)

##  <a name="_core_cache_hits_and_page_faults"></a> Neúspěšné přístupy do mezipaměti a stránkování

Vynechalo přístupů do mezipaměti na obou interních a externích mezipaměti, i stránkování (že přejdete do sekundárního úložiště pokyny programu a data) způsobit snížení výkonu aplikace.

Počet vstupů do mezipaměti využití procesoru může stát program 10-20 hodinových cyklů. Počet vstupů do mezipaměti externího vakcíny stojí 20 – 40 hodinových cyklů. Stránkování vakcíny stojí jednoho milionu hodinových cyklů (za předpokladu, že procesor, který zpracovává 500 milionů pokyny za sekundu a době 2 milisekund pro stránkování). Proto je v nejlepším zájmu provádění programu napsat kód, který se sníží počet přístupů k mezipaměti zmeškaných a stránkování.

Jedním z důvodů pomalého programy je, že trvat další chyby stránky nebo častěji, než je nutné si ujít mezipaměti. Abyste tomu předešli, je důležité použít datových struktur s dobrou místo odkazu, což znamená, že zachování souvisejících věcí najednou. Někdy datová struktura, která vypadá skvělé se ukázalo horrible kvůli špatnému obec odkazu a někdy naopak má hodnotu true. Tady jsou dva příklady:

- Dynamicky přidělené propojené seznamy může snížit výkon aplikace, protože při hledání položky nebo při procházení seznamu na konci každé přeskočené propojení může přijít o mezipaměti nebo způsobit stránkování. Seznam provádění podle jednoduchých polí může být ve skutečnosti mnohem rychlejší z důvodu lepší ukládání do mezipaměti a méně chyb stránek i – umožňuje skutečnost, že pole může být obtížnější růst, stále může být rychlejší.

- Zatřiďovacích tabulek, které používají dynamicky přidělené propojené seznamy může snížit výkon. Při rozšíření i pro, můžou provádět zatřiďovacích tabulek, které používají dynamicky přidělené propojené seznamy pro uložení jejich obsah podstatně horší. Ve skutečnosti v konečné fázi jednoduché lineární hledání prostřednictvím pole může být ve skutečnosti rychlejší (v závislosti na okolnostech). Na základě poli zatřiďovacích tabulek (takzvané "uzavřené hashování") je implementace často přehlédnuta často jehož špičkový výkon.

##  <a name="_core_sorting_and_searching"></a> Řazení a vyhledávání

Řazení je ze své podstaty časově ve srovnání s mnoho typických operací. Nejlepší způsob, jak se vyhnout zbytečným zpomalení je vyhnout řazení v kritické časech. Možná budete moci:

- Odložte, třídění méně důležité pro výkon dobu.

- Řazení dat během starší, méně důležité pro výkon.

- Seřadit pouze část dat, které skutečně potřebuje řazení.

V některých případech můžete vytvořit seznam v seřazeném pořadí. Buďte opatrní, protože pokud potřebujete k vložení dat v seřazeném pořadí, můžete vyžadovat složitější struktury dat s špatnému obec odkazu, což vede k Neúspěšné přístupy do mezipaměti a stránkování. Neexistuje žádný přístup, který funguje ve všech případech. Zkuste několik přístupů a měření rozdílů.

Zde jsou některé obecné tipy pro řazení:

- Chcete-li minimalizovat chyby pomocí uložených řazení.

- Jakékoli práce, které vám pomůžou předem snižuje složitost řazení se vyplatí. Pokud jednorázové heslo nad vašimi daty zjednodušuje porovnání a řazení do O(n) snižuje O (protokolu n n), můžete se téměř jistě přijdete dopředu.

- Představte si místo odkazu algoritmus řazení a očekáváte, že jeho spuštění v datech.

Neexistují nějaké alternativy méně pro vyhledávání než řazení. Pokud je kritický pro čas hledání, binární vyhledávací tabulky vyhledávání nebo hodnoty hash je téměř vždy nejvhodnější, ale stejně jako u řazení, musí mít na paměti umístění. Lineární hledání prostřednictvím malé pole může být rychlejší než binární vyhledávání prostřednictvím datová struktura s velkým množstvím ukazatele, který způsobí, že chyby stránky nebo Neúspěšné přístupy do mezipaměti.

##  <a name="_core_mfc_and_class_libraries"></a> Knihovny MFC a knihovny tříd

Microsoft Foundation Classes (MFC) může výrazně zjednodušit psaní kódu. Při zápisu časově kritického kódu, byste měli vědět systému vyplývajících z některé třídy režijní náklady. Zkontrolujte kód knihovny MFC, která časově kritického kódu používá a zjistěte, jestli splňuje vaše požadavky na výkon. Následující seznam uvádí MFC – třídy a funkce, které byste měli vědět:

- `CString` Volání knihovny run-time jazyka C se přidělit paměť pro knihovny MFC [CString](../../atl-mfc-shared/reference/cstringt-class.md) dynamicky. Obecně řečeno `CString` je tak efektivní jako jakýkoli jiný řetězec přidělí dynamicky. Stejně jako u jakékoli dynamicky přidělené řetězec má režii dynamické přidělování a uvolňování. Často jednoduchý `char` pole v zásobníku může sloužit ke stejnému účelu a je rychlejší. Nepoužívejte `CString` pro uložení konstantní řetězec. Místo nich se používá `const char *`. Všechny operace můžete provádět pomocí `CString` objekt má režijní náklady. Použití knihovny run-time [řetězec funkce](../../c-runtime-library/string-manipulation-crt.md) může být rychlejší.

- `CArray` A [carray –](../../mfc/reference/carray-class.md) poskytuje flexibilitu, že regulární pole nemá, ale váš program, který nemusí. Pokud znáte konkrétní omezení pro pole, můžete použít globální pole dlouhodobého místo. Pokud používáte `CArray`, použijte `CArray::SetSize` vytvoření jeho velikost a počet prvků, které roste při přerozdělení je nutné zadat. V opačném případě přidání prvků může způsobit vaše pole často nevyčerpané a zkopírovat, což je neefektivní a může fragmentovat paměti. Vzít v úvahu taky, pokud vložení položky do pole, `CArray` přesune dalších položek v paměti a může potřebnou k růstu pole. Tato akce může způsobit Neúspěšné přístupy do mezipaměti a stránkování. Pokud si projít kód, který používá knihovnu MFC, může se zobrazit, že vám něco konkrétnější zápisu pro váš scénář pro zvýšení výkonu. Protože `CArray` je šablona, například můžete zadat `CArray` specializace pro konkrétní typy.

- `CList` [CList –](../../mfc/reference/clist-class.md) je dvakrát propojený seznam, tedy vložení elementu rychle v čele, konec a na známé pozici (`POSITION`) v seznamu. Hledání elementu podle hodnoty nebo indexu vyžaduje sekvenčního vyhledávání, ale může být pomalé, pokud je dlouhý seznam. Pokud váš kód nevyžaduje dvakrát propojený seznam můžete chtít zvážit použití `CList`. Pomocí jednotlivě propojený seznam šetří režii aktualizace další ukazatele pro všechny operace a paměť pro tento ukazatel. Další paměť není skvělé, ale je další možnost pro Neúspěšné přístupy do mezipaměti nebo chyby stránek.

- `IsKindOf` Tato funkce může generovat mnoho volání a přístup k velké množství paměti v různých datových oblastí, což vede k chybné lokalitě odkazu. Je užitečné pro sestavení pro ladění (v volání metody ASSERT, například), ale snažte se vyhnout použití v sestavení pro vydání.

- `PreTranslateMessage` Použití `PreTranslateMessage` při strom windows potřebuje různé klávesové zkratky nebo při zpracování zpráv je třeba vložit na pumpu zpráv. `PreTranslateMessage` mění odesílání zpráv knihovny MFC. Pokud přepíšete `PreTranslateMessage`, takže pouze na úrovni potřebné. Není například nutné přepsat `CMainFrame::PreTranslateMessage` Pokud vás zajímá pouze zprávy, že přejdete na podřízené položky v konkrétním zobrazení. Přepsat `PreTranslateMessage` zobrazení tříd – místo toho.

   Cesta normální odeslání není obejít pomocí `PreTranslateMessage` chcete zpracovávat všechny zprávy odeslané do libovolného okna. Použití [procedury okna](../../mfc/registering-window-classes.md) a mapy zpráv knihovny MFC pro tento účel.

- `OnIdle` Nečinnosti může dojít k událostem v některých případech nepočítáte, například mezi `WM_KEYDOWN` a `WM_KEYUP` události. Časovače může být efektivnější způsob, jak aktivovat váš kód. Nesnažte se vynutit `OnIdle` opakovaně volat vygenerováním false zprávy nebo tak, že vždy vrací `TRUE` z přepsání `OnIdle`, které by nikdy umožňují vaše vlákno do režimu spánku. Znovu časovač nebo samostatném vlákně může být vhodnější.

##  <a name="vcovrsharedlibraries"></a> Sdílené knihovny

Opakované využívání kódu je žádoucí. Ale pokud se chystáte použít kód někoho jiného, je by měl Ujistěte se, že víte přesně co to dělá v těchto případech, kde je nejdůležitější pro vás výkon. Nejlepší způsob, jak pochopit je krokování zdrojový kód nebo na základě měření pomocí nástrojů, jako je PView nebo sledování výkonu.

##  <a name="_core_heaps"></a> Haldy

Použití více haldy se podle vlastního uvážení. Další haldy vytvořené pomocí `HeapCreate` a `HeapAlloc` vám umožňují spravovat a pak vyřadit související sadu přidělení. Není potvrzení příliš mnoho paměti. Pokud používáte více haldy, věnujte zvláštní pozornost množství paměti, které je zpočátku potvrzeny.

Místo více haldy můžete v pomocných funkcí rozhraní mezi kódu a výchozí haldy. Pomocné funkce usnadnění vlastní přidělení strategie může zlepšit výkon vaší aplikace. Například pokud je často provést přidělení malých, můžete lokalizovat tyto přidělení na jednu část výchozí haldy. Můžete přidělit velké blok paměti a potom pomocí funkce pomocné rutiny suballocate z tohoto bloku. Pokud to uděláte, nebudete mít další haldy se nevyužitý paměťový protože přidělení pochází z výchozí haldy.

V některých případech však pomocí výchozí haldy můžete snížit místo odkazu. K měření účinky přesouvání objektů na haldě haldy použijte prohlížeč procesu, nástroje Spy ++ nebo sledování výkonu.

Měření vaší haldy, můžete účet pro každou přidělení na haldě. Použití za běhu C [rutiny haldy ladění](/visualstudio/debugger/crt-debug-heap-details) kontrolního bodu a vypsat vaší haldy. Může číst výstup do tabulky programu, jako je Microsoft Excel a zobrazíte výsledky pomocí kontingenční tabulky. Poznámka: Celkový počet, velikost a rozmístění přidělení. Porovnání těchto prvků s velikost pracovní sady. Podívejte se také na Clustering s velikostí související objekty.

Čítače výkonu můžete použít také k monitorování využití paměti.

##  <a name="_core_threads"></a> Vlákna

Pro úlohy na pozadí může být rychlejší než používání vláken efektivní nečinnosti zpracování událostí. Je snazší porozumět místo odkazu v aplikaci s jedním vláknem.

Základním pravidlem je použít vlákno pouze v případě, je oznámení o operační systém, který můžete zablokovat v kořenovém adresáři práce na pozadí. Vlákna jsou nejlepším řešením v takovém případě, protože je nepraktické blokování hlavního vlákna pro událost.

Vlákna jsou k dispozici také komunikační problémy. Spravujte komunikační propojení mezi vlákny, seznam zpráv nebo přidělení a využití sdílené paměti. Správa propojení komunikace obvykle vyžaduje synchronizaci nedošlo ke konfliktům časování a zablokování problémy. Tato složitost můžete snadno změnit na chyby a problémy s výkonem.

Další informace najdete v tématu [zpracování smyčky nečinnosti](../../mfc/idle-loop-processing.md) a [Multithreading](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

##  <a name="_core_small_working_set"></a> Malé pracovní sady

Menší pracovní sady znamená lepší místo odkazu na méně chyb stránky a více přístupů k mezipaměti. Pracovní sada procesu je nejbližší metriku, kterou operační systém poskytuje přímo pro měření místo odkazu.

- Pokud chcete nastavit horní a dolní limity pracovního sadě, použijte [SetProcessWorkingSetSize](/windows/desktop/api/winbase/nf-winbase-getprocessworkingsetsize).

- Horní a dolní limity pracovního sadě, použijte [GetProcessWorkingSetSize](/windows/desktop/api/winbase/nf-winbase-setprocessworkingsetsize).

- Pokud chcete zobrazit velikost pracovní sady, použijte nástroje Spy ++.

## <a name="see-also"></a>Viz také

[Optimalizace kódu](../../build/reference/optimizing-your-code.md)