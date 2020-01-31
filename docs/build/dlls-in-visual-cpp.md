---
title: Vytváření C/C++ knihoven DLL v aplikaci Visual Studio
description: Přehled důvodů a způsobu vytváření a používání knihoven DLL s nástrojem C++ v aplikaci Visual Studio.
ms.date: 01/27/2020
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 7083924f137fa9283da40404c7d15183e59c0b1c
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821418"
---
# <a name="create-cc-dlls-in-visual-studio"></a>Vytváření C/C++ knihoven DLL v aplikaci Visual Studio

V systému Windows je dynamická knihovna (DLL) typem spustitelného souboru, který funguje jako sdílená knihovna funkcí a prostředků. Dynamické propojování je schopnost operačního systému. Umožňuje spustitelnému souboru volat funkce nebo používat prostředky uložené v samostatném souboru. Tyto funkce a prostředky mohou být kompilovány a nasazeny odděleně od spustitelných souborů, které je používají.

Knihovna DLL není samostatný spustitelný soubor. Knihovny DLL jsou spouštěny v kontextu aplikací, které je volají. Operační systém načte knihovnu DLL do paměťového prostoru aplikace. Provádí se buď při načtení aplikace (*implicitní propojení*), nebo na vyžádání za běhu (*explicitní propojování*). Knihovny DLL také usnadňují sdílení funkcí a prostředků napříč spustitelnými soubory. K obsahu jedné kopie knihovny DLL v paměti má současně přístup více aplikací.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Rozdíly mezi dynamickým propojením a statickým propojením

Statické propojování kopíruje veškerý kód objektu ve statické knihovně do spustitelných souborů, které jej používají při sestavení. Dynamické propojování zahrnuje pouze informace potřebné v systému Windows za běhu k vyhledání a načtení knihovny DLL, která obsahuje datovou položku nebo funkci. Při vytváření knihovny DLL můžete také vytvořit knihovnu importu, která obsahuje tyto informace. Při vytváření spustitelného souboru, který volá knihovnu DLL, Linker používá exportované symboly v knihovně Imports pro uložení těchto informací pro zavaděč systému Windows. Když zavaděč načte knihovnu DLL, knihovna DLL je namapována do prostoru paměti aplikace. Je-li k dispozici, je volána speciální funkce v knihovně DLL `DllMain`, aby bylo možné provést jakoukoli inicializaci, kterou knihovna DLL vyžaduje.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Rozdíly mezi aplikacemi a knihovnami DLL

I když jsou knihovny DLL a aplikace oba spustitelnými moduly, liší se různými způsoby. Nejvýraznějším rozdílem je, že nemůžete spustit knihovnu DLL. Z pohledu systému existují dva základní rozdíly mezi aplikacemi a knihovnami DLL:

- Aplikace může mít v systému současně spuštěno více instancí. Knihovna DLL může mít pouze jednu instanci.

- Aplikaci lze načíst jako proces. Může se jednat o vlastní věci, jako je například zásobník, vlákna spouštění, globální paměť, popisovače souborů a fronta zpráv. Knihovna DLL nemůže vlastnit tyto věci.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Výhody použití knihoven DLL

Dynamické propojení s kódem a prostředky nabízí oproti statickému propojování několik výhod:

- Dynamické propojování šetří paměť a snižuje záměna. Mnoho procesů může současně použít knihovnu DLL a sdílet jednu kopii částí knihovny DLL jen pro čtení v paměti. Naproti tomu každá aplikace sestavená pomocí staticky propojené knihovny má úplnou kopii kódu knihovny, kterou musí systém Windows načíst do paměti.

- Dynamické propojení šetří místo na disku a šířku pásma. Mnoho aplikací může sdílet jednu kopii knihovny DLL na disku. Naproti tomu každá aplikace sestavená pomocí knihovny statických odkazů má kód knihovny propojený na jeho spustitelnou image. Který využívá více místa na disku a při přenosu trvá větší šířku pásma.

- Údržba, opravy zabezpečení a upgrady můžou být jednodušší. Pokud vaše aplikace používají v knihovně DLL společné funkce, můžete implementovat opravy chyb a nasadit aktualizace do knihovny DLL. Když jsou knihovny DLL aktualizovány, aplikace, které je používají, není nutné znovu zkompilovat ani znovu připojit. Můžou využít novou knihovnu DLL hned po jejím nasazení. Naopak když provádíte opravy v staticky propojeném kódu objektu, musíte znovu propojit a znovu nasadit každou aplikaci, která ho používá.

- Pomocí knihoven DLL můžete poskytovat podporu po uvedení na trh. Například soubor DLL ovladače zobrazení lze upravit tak, aby podporoval zobrazení, které nebylo po odeslání aplikace k dispozici.

- Můžete použít explicitní propojení pro zjišťování a načítání knihoven DLL za běhu. Například rozšíření aplikace, která do aplikace přidávají nové funkce bez opětovného sestavení nebo opětovného nasazení.

- Dynamické propojení usnadňuje podporu aplikací napsaných v různých programovacích jazycích. Programy napsané v různých programovacích jazycích mohou volat stejnou funkci knihovny DLL, pokud programy dodržují konvenci volání funkce. Programy a funkce knihovny DLL musí být kompatibilní následujícími způsoby: pořadí, ve kterém funkce očekává, že se argumenty předají do zásobníku. Určuje, zda je funkce nebo aplikace zodpovědná za vyčištění zásobníku. A zda jsou všechny argumenty předány v registrech.

- Dynamické propojování poskytuje mechanismus pro rozšiřování tříd knihovny MFC (Microsoft Foundation Class Library). Třídy můžete odvodit z existujících tříd knihovny MFC a umístit je do knihovny DLL rozšíření MFC pro použití aplikacemi MFC.

- Dynamické propojení usnadňuje vytváření mezinárodní verze vaší aplikace. Knihovny DLL představují pohodlný způsob, jak dodávat prostředky specifické pro národní prostředí, které usnadňují vytváření mezinárodních verzí aplikace. Místo odeslání mnoha lokalizovaných verzí aplikace můžete umístit řetězce a obrázky pro každý jazyk do samostatné knihovny DLL prostředků. Aplikace pak může načíst příslušné prostředky pro toto národní prostředí za běhu.

Potenciálně Nevýhodou použití knihoven DLL je, že aplikace není samostatná. Závisí na existenci samostatného modulu knihovny DLL: ten, který musíte nasadit nebo ověřit jako součást instalace.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Další informace o vytváření a používání knihoven DLL

Následující články poskytují podrobné informace o tom, jak v aplikaci VisualC++ Studio vytvořit C/knihovny DLL.

[Návod: vytvoření a použití dynamické knihovny DLL (C++)](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)\
Popisuje, jak vytvořit a použít knihovnu DLL v sadě Visual Studio.

[Typy knihoven dll](kinds-of-dlls.md)\
Poskytuje informace o různých typech knihoven DLL, které lze vytvořit.

[Nejčastější dotazy k DLL](dll-frequently-asked-questions.md)\
Poskytuje odpovědi na nejčastější dotazy týkající se knihoven DLL.

[Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md)\
Popisuje explicitní a implicitní propojení s knihovnou DLL.

[Inicializace\ DLL](run-time-library-behavior.md#initializing-a-dll)
Popisuje inicializační kód knihovny DLL, který musí být spuštěn při načtení knihovny DLL.

[Knihovny DLL a C++ chování běhové knihovny jazyka Visual](run-time-library-behavior.md) runtime\
Popisuje úvodní sekvenci DLL knihovny run-time.

\ [LoadLibrary a AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)
Popisuje použití `LoadLibrary` a `AfxLoadLibrary` k explicitnímu propojení s knihovnou DLL za běhu.

\ [GetProcAddress](getprocaddress.md)
Popisuje použití `GetProcAddress` k získání adresy exportované funkce v knihovně DLL.

[FreeLibrary a AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)\
Popisuje použití `FreeLibrary` a `AfxFreeLibrary`, když už modul knihovny DLL nepotřebujete.

[Pořadí hledání dynamické knihovny](/windows/win32/Dlls/dynamic-link-library-search-order)\
Popisuje cestu pro hledání, kterou operační systém Windows používá k nalezení knihovny DLL v systému.

[Stavy modulů běžné knihovny MFC DLL dynamicky propojené s knihovnou mfc](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)\
Popisuje stavy modulů běžné knihovny MFC DLL dynamicky propojené s knihovnou MFC.

[Knihovny DLL rozšíření MFC](extension-dlls-overview.md)\
Vysvětluje knihovny DLL, které obvykle implementují opakovaně použitelné třídy odvozené z existujících tříd knihovny MFC.

[Vytvoření knihovny DLL obsahující pouze prostředky](creating-a-resource-only-dll.md)\
Popisuje knihovnu DLL, která obsahuje pouze prostředky jako ikony, bitmapy, řetězce a dialogová okna.

[Lokalizované prostředky v aplikacích MFC: satelitní knihovny dll](localized-resources-in-mfc-applications-satellite-dlls.md)\
Rozšiřuje podporu pro satelitní knihovny DLL, funkci, která pomáhá při vytváření aplikací lokalizovaných do více jazyků.

[Import a export](importing-and-exporting.md)\
Popisuje import veřejných symbolů do aplikace nebo export funkcí z knihovny DLL.

[Aktivní technologie a knihovny dll](active-technology-and-dlls.md)\
Umožňuje implementovat Objektové servery v rámci knihovny DLL.

[Automatizace v knihovně DLL](automation-in-a-dll.md)\
Popisuje, co nabízí možnost automatizace v průvodci knihovny MFC DLL.

Zásady [vytváření názvů pro knihovny MFC dll](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)\
Popisuje, jak se knihovny DLL a knihovny zahrnuté v MFC drží zásady strukturovaného vytváření názvů.

[Volání funkcí knihovny DLL z aplikací Visual Basic](calling-dll-functions-from-visual-basic-applications.md)\
Popisuje způsob, jak volat funkce knihovny DLL z aplikací Visual Basic.

## <a name="related-sections"></a>Související oddíly

[Použití knihovny MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)\
Popisuje běžné knihovny MFC DLL, které umožňují použít knihovnu MFC jako součást knihovny DLL systému Windows.

[DLL verze knihovny MFC](../mfc/tn033-dll-version-of-mfc.md)\
Popisuje, jak můžete použít MFCxx. dll a MFCxxD. dll (kde x je číslo verze knihovny MFC) sdílené dynamické knihovny s aplikacemi MFC a knihovnami DLL rozšíření MFC.
