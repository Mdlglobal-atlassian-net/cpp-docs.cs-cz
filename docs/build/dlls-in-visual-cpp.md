---
title: Vytváření C/C++ knihoven DLL v aplikaci Visual Studio
ms.date: 07/18/2019
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 9f5b34fda8a429f8e55631e1e0125ed6f79d5bae
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341072"
---
# <a name="create-cc-dlls-in-visual-studio"></a>Vytváření C/C++ knihoven DLL v aplikaci Visual Studio

V systému Windows je dynamická knihovna (DLL) typem spustitelného souboru, který funguje jako sdílená knihovna funkcí a prostředků. Dynamické propojování je schopnost operačního systému, která umožňuje spustitelnému souboru volat funkce nebo používat prostředky uložené v samostatném souboru. Tyto funkce a prostředky mohou být kompilovány a nasazeny odděleně od spustitelných souborů, které je používají. Knihovna DLL není samostatný spustitelný soubor; spouští se v kontextu aplikace, která je volá. Operační systém může knihovnu DLL načíst do paměťového prostoru aplikace, když je aplikace načtena (*implicitní propojení*) nebo na vyžádání za běhu (*explicitní propojení*). Knihovny DLL také usnadňují sdílení funkcí a prostředků napříč spustitelnými soubory. K obsahu jedné kopie knihovny DLL v paměti má současně přístup více aplikací.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Rozdíly mezi dynamickým propojením a statickým propojením

Statické propojování kopíruje veškerý kód objektu ve statické knihovně do spustitelných souborů, které jej používají při sestavení. Dynamické propojování zahrnuje pouze informace potřebné v systému Windows za běhu k vyhledání a načtení knihovny DLL, která obsahuje datovou položku nebo funkci. Při vytváření knihovny DLL můžete také vytvořit knihovnu importu, která obsahuje tyto informace. Při vytváření spustitelného souboru, který volá knihovnu DLL, Linker používá exportované symboly v knihovně Imports pro uložení těchto informací pro zavaděč systému Windows. Když zavaděč načte knihovnu DLL, knihovna DLL je namapována do prostoru paměti aplikace. Je-li k dispozici, je volána speciální `DllMain`funkce v knihovně DLL, která provede jakoukoli inicializaci, kterou knihovna DLL vyžaduje.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Rozdíly mezi aplikacemi a knihovnami DLL

I když jsou knihovny DLL a aplikace oba spustitelnými moduly, liší se různými způsoby. Pro koncového uživatele je nejčastějším rozdílem, že knihovny DLL nejsou aplikace, které je možné přímo spustit. Z pohledu systému existují dva základní rozdíly mezi aplikacemi a knihovnami DLL:

- Aplikace může mít více instancí samotného běhu v systému současně, zatímco knihovna DLL může mít pouze jednu instanci.

- Aplikaci lze načíst jako proces, který může vlastnit vlastní věci, jako je například zásobník, vlákna spuštění, globální paměť, popisovače souborů a fronta zpráv, ale knihovna DLL nemůže.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Výhody použití knihoven DLL

Dynamické propojení s kódem a prostředky nabízí oproti statickému propojování několik výhod:

- Dynamické propojování šetří paměť a snižuje záměna. Mnoho procesů může současně použít knihovnu DLL a sdílet jednu kopii částí knihovny DLL jen pro čtení v paměti. Naproti tomu každá aplikace sestavená pomocí staticky propojené knihovny má úplnou kopii kódu knihovny, kterou musí systém Windows načíst do paměti.

- Dynamické propojení šetří místo na disku a šířku pásma. Mnoho aplikací může sdílet jednu kopii knihovny DLL na disku. Naproti tomu každá aplikace sestavená pomocí knihovny statických odkazů má kód knihovny propojený na jeho spustitelnou image, která využívá více místa na disku a trvá přenosu větší šířky pásma.

- Údržba, opravy a upgrady zabezpečení můžou být jednodušší. Pokud vaše aplikace používají v knihovně DLL společné funkce, pak pokud se argumenty funkce a návratové hodnoty nezmění, můžete implementovat opravy chyb a nasadit aktualizace do knihovny DLL. Když jsou knihovny DLL aktualizovány, aplikace, které je používají, není nutné znovu kompilovat ani znovu propojit a využívají novou knihovnu DLL hned po jejím nasazení. Naproti tomu opravy, které provedete staticky propojeným objektovým kódem, vyžadují opětovné propojení a opětovné nasazení všech aplikací, které ji používají.

- Pomocí knihoven DLL můžete poskytovat podporu po uvedení na trh. Například knihovna DLL ovladače zobrazení může být upravena tak, aby podporovala zobrazení, které nebylo po odeslání aplikace k dispozici.

- Můžete použít explicitní propojení pro zjišťování a načítání knihoven DLL za běhu, například rozšíření aplikace, která do aplikace přidávají nové funkce bez opětovného sestavení nebo opětovného nasazení.

- Dynamické propojení usnadňuje podporu aplikací napsaných v různých programovacích jazycích. Programy napsané v různých programovacích jazycích mohou volat stejnou funkci knihovny DLL, pokud programy dodržují konvenci volání funkce. Programy a funkce DLL musí být kompatibilní následujícími způsoby: pořadí, v nichž funkce očekává uložení argumentů na zásobník, rozhodnutí, zda je za vyčištění zásobníku odpovědná funkce nebo aplikace, a informace, zda jsou kterékoli argumenty předávány v registrech.

- Dynamické propojování poskytuje mechanismus pro rozšiřování tříd knihovny MFC. Třídy můžete odvodit z existujících tříd knihovny MFC a umístit je do knihovny DLL rozšíření MFC pro použití aplikacemi MFC.

- Dynamické propojení usnadňuje vytváření mezinárodní verze vaší aplikace. Knihovny DLL představují pohodlný způsob, jak dodávat prostředky specifické pro národní prostředí, které usnadňují vytváření mezinárodních verzí aplikace. Namísto přesouvání mnoha lokalizovaných verzí aplikace můžete umístit řetězce a obrázky pro každý jazyk v samostatné knihovně DLL prostředku a potom může aplikace načíst příslušné prostředky pro toto národní prostředí za běhu.

Potenciálně Nevýhodou použití knihoven DLL je, že aplikace není samostatná. závisí na existenci samostatného modulu knihovny DLL, který je nutné nasadit nebo ověřit jako součást instalace.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Další informace o vytváření a používání knihoven DLL

Následující témata obsahují podrobné informace o tom, jak vytvořit C/C++ knihovny DLL v aplikaci Visual Studio.

[Návod: Vytvoření a použití dynamické knihovny DLL (C++)](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
Popisuje, jak vytvořit a použít knihovnu DLL v sadě Visual Studio.

[Typy knihoven DLL](kinds-of-dlls.md)<br/>
Poskytuje informace o různých typech knihoven DLL, které lze vytvořit.

[Nejčastější dotazy k DLL](dll-frequently-asked-questions.md)<br/>
Poskytuje odpovědi na nejčastější dotazy týkající se knihoven DLL.

[Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md)<br/>
Popisuje explicitní a implicitní propojení s knihovnou DLL.

[Inicializovat knihovnu DLL](run-time-library-behavior.md#initializing-a-dll)<br/>
Popisuje inicializační kód knihovny DLL, který musí být spuštěn při načtení knihovny DLL.

[Knihovny DLL a chování běhové knihovny v jazyce Visual C++](run-time-library-behavior.md)<br/>
Popisuje, jakým způsobem provádí knihovna runtime spouštěcí sekvenci knihovny DLL.

[LoadLibrary a AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)<br/>
Popisuje použití  funkce LoadLibrary `AfxLoadLibrary` a k explicitnímu propojení s knihovnou DLL za běhu.

[GetProcAddress](getprocaddress.md)<br/>
Popisuje použití funkce **GetProcAddress** pro získání adresy exportované funkce v knihovně DLL.

[FreeLibrary a AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)<br/>
Popisuje použití **FreeLibrary** a `AfxFreeLibrary` v případě, že už modul knihovny DLL nepotřebujete.

[Pořadí hledání dynamických propojených knihoven](/windows/desktop/Dlls/dynamic-link-library-search-order)<br/>
Popisuje cestu pro hledání, kterou operační systém Windows používá k nalezení knihovny DLL v systému.

[Stavy modulů běžné knihovny MFC DLL dynamicky propojené do MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)<br/>
Popisuje stavy modulů běžné knihovny MFC DLL dynamicky propojené s knihovnou MFC.

[MFC – rozšiřující knihovny DLL](extension-dlls-overview.md)<br/>
Popisuje knihovny DLL, které obvykle implementují opakovaně použitelné třídy odvozené z existujících tříd knihovny Microsoft Foundation Class.

[Vytvoření knihovny DLL obsahující jen prostředky](creating-a-resource-only-dll.md)<br/>
Popisuje knihovnu DLL, která obsahuje pouze prostředky jako ikony, bitmapy, řetězce a dialogová okna.

[Lokalizované prostředky v aplikacích MFC: Satelitní knihovny DLL](localized-resources-in-mfc-applications-satellite-dlls.md)<br/>
Rozšiřuje podporu pro satelitní knihovny DLL, funkci, která pomáhá při vytváření aplikací lokalizovaných do více jazyků.

[Import a export](importing-and-exporting.md)<br/>
Popisuje import veřejných symbolů do aplikace nebo export funkcí z knihovny DLL.

[Aktivní technologie a knihovny DLL](active-technology-and-dlls.md)<br/>
Umožňuje implementovat Objektové servery v rámci knihovny DLL.

[Automatizace v knihovně DLL](automation-in-a-dll.md)<br/>
Popisuje, co nabízí možnost automatizace v průvodci knihovny MFC DLL.

[Zásady vytváření názvů pro knihovny MFC DLL](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)<br/>
Popisuje, jak se knihovny DLL a knihovny zahrnuté v MFC drží zásady strukturovaného vytváření názvů.

[Volání funkcí knihovny DLL z aplikací Visual Basic](calling-dll-functions-from-visual-basic-applications.md)<br/>
Popisuje způsob, jak volat funkce knihovny DLL z aplikací Visual Basic.

## <a name="related-sections"></a>Související oddíly

[Použití knihovny MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)<br/>
Popisuje běžné knihovny MFC DLL, které umožňují použít knihovnu MFC jako součást knihovny DLL systému Windows.

[DLL verze knihovny MFC](../mfc/tn033-dll-version-of-mfc.md)<br/>
Popisuje, jak můžete použít MFCxx. dll a MFCxxD. dll (kde x je číslo verze knihovny MFC) sdílené dynamické knihovny s aplikacemi MFC a knihovnami DLL rozšíření MFC.
