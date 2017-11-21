---
title: "Tipy pro zlepšení časově kritického kódu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5efcf042932163f1e932a55622f7dddd167b8961
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tips-for-improving-time-critical-code"></a>Tipy pro zlepšení časově kritického kódu
Zápis rychlý kód vyžaduje pochopení všechny aspekty aplikace, a jak komunikuje se službou systému. Toto téma navrhuje alternativy k některé z zřejmější kódovacích postupů vám pomohou zajistit uspokojivému provádění části časově kritického kódu.  
  
 To Shrneme, zlepšení časově kritického kódu vyžaduje, aby vám:  
  
-   Vědět, jaké části vašeho programu musí být rychlé.  
  
-   Vědět, velikosti a rychlosti vašeho kódu.  
  
-   Znáte náklady na nových funkcí.  
  
-   Znáte minimální práce potřebné k provedení úlohy.  
  
 Shromažďovat informace o výkonu kódu, můžete použít sledování výkonu (perfmon.exe).  
  
## <a name="sections-in-this-article"></a>Části v tomto článku  
  
-   [Neúspěšné přístupy do mezipaměti a chyb stránek](#_core_cache_hits_and_page_faults)  
  
-   [Řazení a vyhledávání](#_core_sorting_and_searching)  
  
-   [Knihovny MFC a knihovny tříd](#_core_mfc_and_class_libraries)  
  
-   [Sdílené knihovny](#vcovrsharedlibraries)  
  
-   [Hald](#_core_heaps)  
  
-   [Vláken](#_core_threads)  
  
-   [Malého pracovní sady](#_core_small_working_set)  
  
##  <a name="_core_cache_hits_and_page_faults"></a>Neúspěšné přístupy do mezipaměti a chyb stránek  
 Vynechalo přístupů k mezipaměti, v obou interních a externích mezipaměti, a také chyb stránek (přejdete do sekundárního úložiště program pokyny a data) způsobit snížení výkonu programu.  
  
 Vstupů do mezipaměti využití procesoru může náklady vašeho programu 10-20 taktovací cykly. Vstupů do mezipaměti externí může náklady 20-40 hodinových cyklů. Chyby stránky může náklady jeden milión hodinových cyklů (za předpokladu, že procesor, který zpracovává 500 milionů pokyny za sekundu a vždycky 2 milisekund pro chyby stránky). Proto je nejlepší zájmu o spuštění programu napsat kód, který se sníží počet přístupů k mezipaměti zmeškaných a chyb stránek.  
  
 Jedním z důvodů pomalého programy je, že provést další chyb stránek nebo častěji, než je nutné neproběhly mezipaměti. Abyste tomu předešli, je důležité použít datové struktury s funkčním polohu odkaz, který znamená související věcí společně. Někdy datová struktura, která vypadá skvělé jím být horrible z důvodu nízký polohu odkazu a někdy platí opačně. Zde jsou dva příklady:  
  
-   Dynamicky přidělené propojené seznamy může snížit výkon program, protože při vyhledávání pro položku nebo při procházení seznam na konec každé přeskočené připojení může neproběhly mezipaměti nebo způsobit chyby stránky. Na seznamu implementace založené na jednoduchých pole může být ve skutečnosti mnohem rychlejší kvůli lepší ukládání do mezipaměti a méně chyby stránek i – povolení k tomu, že pole bude těžší růst, stále může být rychlejší.  
  
-   Hash – tabulky používající přidělí dynamicky propojené seznamy může snížit výkon. Rozšíření, může provádět zatřiďovací tabulky, které slouží k ukládání jejich obsah dynamicky přidělené propojené seznamy podstatně zhoršení. Ve skutečnosti v konečné fázi jednoduché lineární hledání prostřednictvím pole může být ve skutečnosti rychlejší (v závislosti na v případech). Na základě pole zatřiďovacích tabulkách (takzvané "uzavřené algoritmu hash") je často přehlížen implementace, která často má vyšší výkon.  
  
##  <a name="_core_sorting_and_searching"></a>Řazení a vyhledávání  
 Řazení je ze své podstaty časově náročné ve srovnání s mnoha typických operací. Nejlepší způsob, jak se vyhnout se zbytečné zpomalení se vyhnete řazení v kritické časech. Bude pravděpodobně možné na:  
  
-   Odložení, dokud není výkon kritických časových řazení.  
  
-   Řazení dat během starší, není důležité pro výkon.  
  
-   Seřadit pouze část dat, které skutečně řazení.  
  
 V některých případech můžete vytvořit seznam seřazená. Buďte opatrní, protože pokud je třeba vložit data seřazená, možná budete potřebovat složitější datová struktura s nízký polohu odkaz, což Neúspěšné přístupy do mezipaměti a chyb stránek. Neexistuje žádný způsob, která funguje ve všech případech. Zkuste několik přístupů a měřit rozdíly.  
  
 Zde jsou některé obecné tipy pro řazení:  
  
-   Chcete-li minimalizovat chyby pomocí uložených řazení.  
  
-   Veškerou práci, které může provádět předem ke snížení složitosti řazení je smysl. Pokud jednorázové průchodu přes data zjednodušuje jejich porovnání a snižuje řazení do O(n) z O (n protokolu n), můžete se skoro určitě přijdete dopředu.  
  
-   Vezměte v úvahu polohu odkazu algoritmus řazení a očekáváte, že jeho spuštění data.  
  
 Existují méně alternativami pro hledání než pro řazení. Pokud je kritický pro čas hledání, binární vyhledávání tabulky vyhledávání nebo hodnoty hash je téměř vždy nejvhodnější, ale stejně jako u řazení, je nutné mějte polohu. Lineární hledání prostřednictvím malé pole může být rychlejší než binární vyhledávání prostřednictvím datová struktura s velkým množstvím ukazatele, který způsobuje, že chyb stránek nebo Neúspěšné přístupy do mezipaměti.  
  
##  <a name="_core_mfc_and_class_libraries"></a>Knihovny MFC a knihovny tříd  
 Microsoft Foundation třídy (MFC) může výrazně zjednodušit psaní kódu. Při psaní kódu kritického pro čas, byste měli vědět vyplývajících z některé třídy režijní náklady. Zkontrolujte MFC kód, který váš kód kritický pro čas používá a zjistěte, zda splňuje vaše požadavky na výkon. Následující seznam uvádí MFC – třídy a funkce, které byste měli vědět:  
  
-   `CString`Běhové knihovny jazyka C přidělit paměť pro volání MFC [CString](../../atl-mfc-shared/reference/cstringt-class.md) dynamicky. Obecně řečeno `CString` je jako efektivní jako jakýkoli jiný řetězec přidělí dynamicky. Stejně jako u jakékoli dynamicky přidělené řetězec má režii dynamické přidělování a verzi. Často jednoduchou `char` pole v zásobníku může sloužit ke stejnému účelu a je rychlejší. Nepoužívejte `CString` k uložení konstantní řetězec. Místo nich se používá `const char *`. Všechny operace můžete provádět s nástrojem `CString` objekt má některé režijní náklady. Pomocí běhové knihovny [funkce pro řetězce](../../c-runtime-library/string-manipulation-crt.md) může být rychlejší.  
  
-   `CArray`A [carray –](../../mfc/reference/carray-class.md) poskytuje flexibilitu, že není regulární pole, ale nemusí potřebovat vašeho programu, který. Pokud znáte konkrétní limity pro pole, můžete použít globální pevné pole místo. Pokud používáte `CArray`, použijte `CArray::SetSize` k zahájení jeho velikost a počet prvků, které zvětšování při nové přidělení je nutné zadat. Přidávání elementů, jinak může způsobit vaše pole často opětovnému přidělení a zkopírovali, což je neefektivní a může fragmentovat paměti. Vzít v úvahu taky, pokud položku vložit do pole, `CArray` přesune následné položky v paměti a možná muset růst pole. Tato akce může způsobit Neúspěšné přístupy do mezipaměti a chyb stránek. Pokud se podíváte prostřednictvím kód, který používá MFC, může se zobrazit, když je něco konkrétnější napsat vašemu scénáři ke zlepšení výkonu. Vzhledem k tomu `CArray` je šablona, například můžete zadat `CArray` specializací pro konkrétní typy.  
  
-   `CList`[CList](../../mfc/reference/clist-class.md) je seznam dvakrát propojený element vložení je rychlé v head, značka a na známé pozici (`POSITION`) v seznamu. Vyhledávání element hodnotu nebo index vyžaduje sekvenční hledání, ale může být pomalé, pokud je seznam dlouho. Pokud váš kód nevyžaduje dvakrát propojený seznam můžete chtít nebyla pomocí `CList`. Pomocí jednotlivě propojený seznam uloží nároky na aktualizace pro všechny operace další ukazatel i paměť pro tento ukazatel. Další paměť není skvělé, ale je jiné příležitosti pro Neúspěšné přístupy do mezipaměti nebo chyb stránek.  
  
-   `IsKindOf`Tato funkce může generovat mnoha volání a přístup k velké množství paměti v různých datových oblastech, což chybný polohu odkazu. Je vhodné pro sestavení ladicí verze (v ASSERT volání, např.), ale vhodné používat v sestavení pro vydání.  
  
-   `PreTranslateMessage`Použití `PreTranslateMessage` při konkrétní stromu systému windows musí různé klávesové zkratky nebo při zpracování zpráv je nutné vložit do message pump. `PreTranslateMessage`mění MFC odesílání zpráv. Pokud přepíšete `PreTranslateMessage`, takže jenom na úrovni potřebné. Není například nutné přepsat `CMainFrame::PreTranslateMessage` Pokud vás zajímá jenom v zprávy přenášené do podřízených objektů v konkrétním zobrazení. Přepsání `PreTranslateMessage` pro zobrazení třídy místo.  
  
     Není obejít cesta normální odesílání pomocí `PreTranslateMessage` zpracovat všechny zprávy odeslané do libovolného okna. Použití [procedury oken](../../mfc/registering-window-classes.md) a mapy zpráv knihovny MFC k tomuto účelu.  
  
-   `OnIdle`Nečinnosti události může dojít v některých případech neočekáváte, například jako mezi `WM_KEYDOWN` a `WM_KEYUP` události. Časovače může být efektivnější způsob, jak aktivovat vašeho kódu. Nevynucovat `OnIdle` k volání opakovaně vygenerováním false zprávy nebo vždy vrácením `TRUE` z přepsání `OnIdle`, které by nikdy umožňují vaší vlákno do režimu spánku. Znovu časovač nebo samostatný podproces může být vhodnější.  
  
##  <a name="vcovrsharedlibraries"></a>Sdílené knihovny  
 Opětovné použití kódu je žádoucí. Ale pokud se chystáte použít kód jiného uživatele, měli byste si ověřit, že víte, přesně jak funguje v případech, kdy výkonu pro vás důležité. Nejlepší způsob, jak pochopit, to je procházení zdrojový kód nebo měření pomocí nástroje, například PView nebo sledování výkonu.  
  
##  <a name="_core_heaps"></a>Hald  
 Použití více haldách s vlastního rozhodnutí. Další haldách vytvořené pomocí `HeapCreate` a `HeapAlloc` umožňují spravovat a pak uvolnění související sady přidělení. Nemáte potvrdit příliš mnoho paměti. Pokud používáte více haldách, věnujte zvláštní pozornost množství paměti, která je původně potvrdit.  
  
 Místo více haldách můžete v pomocných funkcí rozhraní mezi kódu a výchozí haldy. Podpůrné funkce usnadnění vlastní přidělení strategií, které může zvýšit výkon vaší aplikace. Například pokud provádíte často malé přidělení, můžete tyto přidělení k jedné části výchozí haldy pro lokalizaci. Můžete přidělit blok velké paměti a pak pomocí pomocné funkce suballocate z tohoto bloku. Pokud to uděláte, nebudete mít další haldách s nevyužitou paměť, protože je přidělení vycházejících z výchozí haldy.  
  
 V některých případech ale použití haldy výchozí může snížit polohu odkazu. K měření důsledky přesouvání objektů z haldy haldy použijte prohlížeč procesu, nástroje Spy ++ nebo sledování výkonu.  
  
 Měření vaší haldách, můžete účet pro každý přidělování v haldě. Použít běhu C [rutiny haldy ladění](/visualstudio/debugger/crt-debug-heap-details) kontrolního bodu a výpisů vaší haldy. Můžete číst výstup do tabulkového procesoru, jako je Microsoft Excel a zobrazíte výsledky pomocí kontingenčních tabulek. Poznámka: Celkový počet, velikost a distribuci přidělení. Porovnejte je s velikost pracovní sady. Podívejte se taky na clustering velikost související objekty.  
  
 Můžete taky čítače výkonu pro monitorování využití paměti.  
  
##  <a name="_core_threads"></a>Vláken  
 Pro úlohy na pozadí může být rychlejší než při použití vláken efektivní nečinnosti zpracování událostí. Je jednodušší zjistit polohu odkazu v programu jednovláknové.  
  
 Dobré pravidlo je použití vlákna pouze v případě, že se oznámení operačního systému, který zablokujete na v kořenovém adresáři práce na pozadí. Vlákna jsou nejlepší řešení v takovém případě, protože je nepraktické blokování hlavního vlákna na událost.  
  
 Vláken také být komunikační problémy. Je třeba spravovat datový spoj mezi vlákny, seznam zpráv nebo přidělování a použitím sdílené paměti. Správa odkaz komunikace obvykle vyžaduje synchronizaci a vyhnout časování zablokování problémy. Tato složitost můžete snadno upravit na chyby a problémy s výkonem.  
  
 Další informace najdete v tématu [zpracování nečinné smyčky](../../mfc/idle-loop-processing.md) a [Multithreading](../../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
##  <a name="_core_small_working_set"></a>Malého pracovní sady  
 Menší pracovní sady znamenají lepší polohu odkazu, menšího počtu chyb stránek a více přístupů k mezipaměti. Pracovní sada procesu je nejblíže metriku, které operační systém přímo poskytuje pro měření polohu odkazu.  
  
-   Pokud chcete nastavit horní a dolní meze pracovní sady, použijte [SetProcessWorkingSetSize](http://msdn.microsoft.com/library/windows/desktop/ms683226.aspx).  
  
-   Horní a dolní meze pracovní sady, použijte [GetProcessWorkingSetSize](http://msdn.microsoft.com/library/windows/desktop/ms686234.aspx).  
  
-   Pokud chcete zobrazit velikost pracovní sady, použijte nástroje Spy ++.  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace kódu](../../build/reference/optimizing-your-code.md)