---
title: Knihovny DLL v jazyce Visual C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28be2caa3477eabc8b717b387c99d65585a9ef19
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718052"
---
# <a name="dlls-in-visual-c"></a>Knihovny DLL v jazyce Visual C++

Dynamická knihovna (DLL) ve Windows, je druh spustitelný soubor, který funguje jako sdílená knihovna funkcí a prostředků. Dynamické propojení je operační systém schopností, který umožňuje spustitelného souboru k volání funkce nebo prostředkům uloženým v samostatném souboru. Může být sestaven a nasazují samostatně z spustitelné soubory, které používají tyto funkce a prostředky. Knihovny DLL není samostatně spustitelná; spuštění v rámci aplikace, která je volá. Operační systém můžete načíst knihovnu DLL do aplikace paměťového prostoru při načtení aplikace (*implicitní propojení*), nebo na vyžádání za běhu (*explicitní propojení*). Knihovny DLL také usnadňují sdílení funkce a prostředky v spustitelné soubory. Více aplikací můžete přístup k obsahu jedné kopie knihovny DLL v paměti ve stejnou dobu.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Rozdíly mezi dynamické propojení a statické propojení

Statické propojení zkopíruje celého objektového kódu ve statické knihovně do spustitelných souborů, který se použije při sestavení. Dynamické propojení obsahuje pouze informace potřebné pro Windows v době běhu k vyhledání a načtení knihovny DLL obsahující datové položky nebo funkce. Při vytváření knihovny DLL, můžete také vytvořit knihovnu importu, který obsahuje tyto informace. Při vytváření spustitelného souboru, který volá knihovnu DLL linkeru používá exportovaný symbolů v knihovně importu k ukládání příslušných informací pro Windows zavaděče. Když se načte knihovna DLL, knihovnu DLL je namapována na místo v paměti aplikace. Pokud jsou k dispozici, speciální funkce v knihovně DLL `DllMain`, volá se, že můžete udělat všechny inicializace, pak vyžaduje knihovna DLL.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Rozdíly mezi aplikacemi a knihovnami DLL

I když knihovny DLL a aplikace jsou obě spustitelných modulů, se liší v několika způsoby. Koncovému uživateli Nejobvyklejšími rozdílem je, knihovny DLL nejsou aplikací, které mohou být provedeny přímo. V systému pohledu existují dva základní rozdíly mezi aplikacemi a knihovnami DLL:

- Aplikace může mít více instancí současně, spuštěná v systému, že knihovna DLL může mít pouze jednu instanci.

- Aplikace mohou být zavedena jako proces, který může vlastnit například zásobníku, vlákna provádění, globální paměť, popisovače souborů a fronty zpráv, ale nikoli knihovnu DLL.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Výhody použití knihoven DLL

Dynamického propojení namísto statického kódu a prostředky nabízí několik výhod. Při použití knihovny DLL, můžete ušetřit místo v paměti a snižují možnost záměny. Při jedné kopie knihovny DLL mohlo používat více aplikací, můžete ušetřit místo na disku a stáhnout šířky pásma. Knihovny DLL se dají nasadit a aktualizovat samostatně, který umožní poskytujete podporu a aktualizací softwaru pro následné trhu bez nutnosti znovu sestavit a dodávat váš kód. Knihovny DLL jsou pohodlný způsob, jak zadat prostředků specifických pro národní prostředí, které podporují vícejazyčné programy a usnadňují vytváření mezinárodních verzí vašich aplikací. Explicitní propojení umožňuje vaší aplikaci zjišťovat a načíst knihovny DLL v době běhu, jako je například rozšíření, které poskytují nové možnosti.

Dynamické propojení má následující výhody:

- Dynamické propojování šetří paměť a snižuje prohození. Velký počet procesů můžete použít knihovnu DLL současně, sdílení jedné kopie jen pro čtení částí knihovny DLL v paměti. Naproti tomu každou aplikaci, která je vytvořená pomocí staticky propojené knihovny obsahuje úplnou kopii kód knihovny, který Windows musí načíst do paměti.

- Dynamické propojování šetří místo na disku a šířku pásma. Mnoho aplikací můžete sdílet jedinou kopii knihovny DLL na disku. Naproti tomu každou aplikaci vytvořenou pomocí knihovny statických odkazů obsahuje kód knihovny propojené s jeho spustitelné bitové kopie, které používá více místa na disku a má větší šířku pásma pro přenos.

- Údržbu, opravy zabezpečení a inovace může být jednodušší. Když se aplikace používají běžné funkce v knihovně DLL, pak jako argumenty funkce a návratové hodnoty nezmění, můžete implementovat opravy chyb a nasazení aktualizací do knihovny DLL. Při aktualizaci knihovny DLL aplikace, které je používají není nutné znovu zkompilovat, nebo se znovu připojit, a jejich použití nová knihovna DLL ihned poté, co je nasazená. Opravy, které provedete v staticky propojených objektový kód naproti tomu vyžadují, abyste znovu připojit a znovu nasadit každou aplikaci, která ji používá.

- Knihovny DLL můžete použít k zajištění podpory následné na trhu. Například lze upravit ovladač zobrazení knihovny DLL pro podporu zobrazení, která nebyla k dispozici v aplikaci byl dodán. Můžete pomocí explicitní propojení můžete načíst rozšíření aplikací jako knihovny DLL a přidat nové funkce do vaší aplikace bez znovu sestavit nebo jejího opětovného nasazení.

- Dynamické propojení usnadňuje podporu aplikace napsané v různých programovacích jazycích. Programy napsané v různých programovacích jazycích mohou volat stejné funkce knihovny DLL, tak dlouho, dokud dodržují konvence volání funkce. Programy a funkce DLL musí být kompatibilní následujícími způsoby: pořadí, v nichž funkce očekává uložení argumentů na zásobník, rozhodnutí, zda je za vyčištění zásobníku odpovědná funkce nebo aplikace, a informace, zda jsou kterékoli argumenty předávány v registrech.

- Dynamické propojování poskytuje mechanismus pro rozšíření tříd knihovny MFC. Můžete odvozovat z existujících tříd knihovny MFC a umístit je do MFC – rozšiřující knihovny DLL pro použití v aplikacích MFC.

- Dynamické propojení usnadňuje vytváření mezinárodních verzí vaší aplikace. Tak, že prostředky specifické pro národní prostředí v knihovně DLL, je snazší vytvářet mezinárodní verze aplikace. Namísto přesouvání mnoho lokalizovaných verzí aplikace, řetězce a bitových kopií pro každý jazyk můžete umístit do samostatného prostředku knihovny DLL a načtěte odpovídající prostředky pro toto národní prostředí za běhu aplikace.

Potenciální nevýhodou použití knihoven DLL je, že aplikace není samostatný; To závisí na existenci samostatný modul knihovny DLL, který musíte nasadit nebo sami ověření jako součást instalace sady.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Další informace o tom, jak vytvořit a používat knihovny DLL

Následující témata obsahují podrobné informace o tom, na program knihovny DLL v jazyce Visual C++.

[Návod: Vytvoření a použití knihovny pro dynamické propojení (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md) popisuje, jak vytvořit a použít knihovnu DLL pomocí sady Visual Studio.

[Druhy knihoven DLL](../build/kinds-of-dlls.md) poskytuje informace o různých typech knihoven DLL, které se dají.

[DLL – nejčastější dotazy](../build/dll-frequently-asked-questions.md) poskytuje odpovědi na nejčastější dotazy týkající se knihoven DLL.

[Propojení spustitelného souboru s knihovnou DLL](../build/linking-an-executable-to-a-dll.md) popisuje explicitní a implicitní propojení s knihovnou DLL.

[Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll) inicializační kód popisuje knihovny DLL, která musí být spuštěn při načtení knihovny DLL.

[Knihovny DLL a chování běhové knihovny jazyka Visual C++](../build/run-time-library-behavior.md) popisuje, jak provádí spouštěcí sekvenci knihovny DLL knihovny run-time.

[LoadLibrary a AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md) popisuje použití **LoadLibrary** a `AfxLoadLibrary` pro explicitní propojení ke knihovně DLL za běhu.

[GetProcAddress](../build/getprocaddress.md) popisuje použití **GetProcAddress** pro získání adresy exportované funkce v knihovně DLL.

[FreeLibrary a AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md) popisuje použití **FreeLibrary** a `AfxFreeLibrary` při modul knihovny DLL je už je nepotřebujete.

[Pořadí hledání knihoven DLL](/windows/desktop/Dlls/dynamic-link-library-search-order) popisuje vyhledávací cestu, operační systém Windows používá k nalezení knihovny DLL v systému.

[Stavy modulů regulární knihovny MFC DLL dynamicky propojené ke knihovně MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md) popisuje stavy modulů běžné knihovny MFC DLL dynamicky propojené ke knihovně MFC.

[MFC – rozšiřující knihovny DLL](../build/extension-dlls-overview.md) vysvětluje DLL, které obvykle implementují opakovaně použitelné třídy odvozené z existujících tříd knihovny Microsoft Foundation Class.

[Vytváření knihovny DLL Resource-Only](../build/creating-a-resource-only-dll.md) popisuje pouze prostředky knihovny DLL, která obsahuje prostředky, jako jsou ikony, bitmapy, řetězce a dialogová okna.

[Lokalizované prostředky v aplikacích MFC: satelitní knihovny DLL](../build/localized-resources-in-mfc-applications-satellite-dlls.md) poskytuje rozšířenou podporu pro satelitní knihovny DLL, funkci, která pomáhá při vytváření aplikací lokalizovaných do více jazyků.

[Import a export](../build/importing-and-exporting.md) popisuje import veřejných symbolů do aplikace nebo export funkcí z knihovny DLL

[Aktivní technologie a knihovny DLL](../build/active-technology-and-dlls.md) umožňuje objektových serverů uvnitř knihovny DLL implementovat.

[Automatizace v knihovně DLL](../build/automation-in-a-dll.md) popisuje, co poskytuje možnost automatizace v průvodci knihovny MFC DLL.

[Zásady vytváření názvů pro knihovny MFC DLL](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions) popisuje, jak se knihovny DLL a knihovny zahrnuté v MFC podle zásady strukturovaného vytváření názvů.

[Volání funkcí knihovny DLL z aplikací Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md) popisuje, jak volat funkce knihovny DLL z aplikací Visual Basic.

## <a name="related-sections"></a>Související oddíly

[Použití prostředí MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md) popisuje běžných knihovnách MFC DLL, které umožňují použít knihovnu MFC jako součást Windows dynamickou knihovnu.

[DLL verze knihovny MFC](../mfc/tn033-dll-version-of-mfc.md) popisuje, jak můžete použít knihovny MFCxx.dll a MFCxxD.dll (kde x je číslo verze knihovny MFC) sdílené knihovny DLL s aplikací knihovny MFC a MFC – rozšiřující knihovny DLL.
