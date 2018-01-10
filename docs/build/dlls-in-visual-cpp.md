---
title: Knihovny DLL v jazyce Visual C++ | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed3679d29b8d181e2cbd9896d0322fea634bfbf0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dlls-in-visual-c"></a>Knihovny DLL v jazyce Visual C++  
  
V systému Windows je dynamická knihovna (DLL) druh spustitelný soubor, který funguje jako sdílené knihovny funkce a prostředků. Dynamické propojování je funkci operačního systému, která umožňuje spustitelný soubor k volání funkce nebo použití prostředkům uloženým v samostatném souboru. Tyto funkce a prostředky můžete zkompilovat a nasazuje samostatně z spustitelné soubory, které je používat. Knihovny DLL není samostatný spustitelný soubor; Spustí se v kontextu aplikace, která se volá. Operační systém můžete načíst knihovnu DLL do aplikace paměťový prostor při načtení aplikace (*implicitní propojení*), nebo na vyžádání v době běhu (*explicitní propojení*). Knihovny DLL také usnadňují sdílení funkce a prostředky v spustitelné soubory. Více aplikací můžete přístup k obsahu z jedné kopie knihovny DLL v paměti ve stejnou dobu.  
  
## <a name="differences-between-dynamic-linking-and-static-linking"></a>Rozdíly mezi dynamického propojení a statické propojení  
  
Statické propojení zkopíruje všechny kód objektu v statické knihovny do spustitelné soubory, které ho používat, pokud tyto šablony jsou sestaveny. Dynamické propojování obsahuje pouze informace potřebné pro Windows v době běhu k vyhledání a načtení knihovny DLL obsahující datové položky nebo funkce. Při vytváření knihovny DLL, můžete také vytvořit knihovnu importu, který obsahuje tyto informace. Když vytvoříte spustitelné soubory, které volá knihovnu DLL, linkeru používá exportovaný symboly v knihovně import k ukládání tyto informace pro zavaděč systému Windows. Při zavaděč načtení knihovny DLL, knihovny DLL je mapována do paměťového prostoru svojí aplikace. Pokud je k dispozici, speciální funkce v knihovně DLL `DllMain`, je volána k provedení všechny inicializace vyžaduje knihovnu DLL.  
  
<a name="differences-between-applications-and-dlls"></a>  
  
## <a name="differences-between-applications-and-dlls"></a>Rozdíly mezi aplikacemi a knihovnami DLL  
  
I když knihovny DLL a aplikace jsou obě spustitelné moduly, se liší v několika způsoby. Pro koncového uživatele nejobvyklejší rozdílem je, že knihovny DLL nejsou aplikace, které mohou být spuštěny přímo. V systému hlediska existují dva základní rozdíly mezi aplikacemi a knihovnami DLL:  
  
-   Aplikace může mít více instancí běhu v systému současně, zatímco knihovny DLL může mít pouze jednu instanci.  
  
-   Aplikace mohou být načteny jako proces, který může vlastnit například zásobník, vláken provádění, globální paměť, obslužné rutiny souborů a fronta zpráv, ale nemůže knihovny DLL.  
  
<a name="advantages-of-using-dlls"></a>  
  
## <a name="advantages-of-using-dlls"></a>Výhody použití knihoven DLL  
  
Dynamické propojování místo statické propojení kódu a prostředků nabízí několik výhod. Při použití knihovny DLL, můžete ušetřit místo paměti a snižují prohození. Když se více aplikací můžete použít jenom jedna kopie knihovny DLL, můžete ušetřit místo na disku a stáhnout šířky pásma. Knihovny DLL mohou být nasazeny a aktualizovat samostatně, které lze zadáte podporu a aktualizací softwaru pro následnou trhu bez nutnosti znovu sestavte a odeslání vašeho kódu. Knihovny DLL jsou pohodlný způsob, jak zadat místního zdroje, které může podporovat vícejazyčné programy a usnadňují vytváření mezinárodní verze aplikací. Explicitní propojení můžete povolit aplikace zjistit a načtení knihovny DLL za běhu, jako je například rozšíření, které poskytují nové funkce.  
  
Dynamické propojování má následující výhody:  
  
-   Dynamické propojování, že šetří paměť a snižuje prohození. Velký počet procesů pomocí knihovny DLL současně, sdílení jedné kopie jen pro čtení části knihovny DLL v paměti. Naproti tomu každou aplikaci, která je vytvořená pomocí staticky propojené knihovny obsahuje úplnou kopii knihovny kód, který systém Windows musí načíst do paměti.  
  
-   Dynamické propojování šetří místo na disku a šířku pásma. Mnoho aplikací můžete sdílet jenom jedna kopie knihovny DLL na disku. Každá aplikace vytvořené pomocí staticky propojené knihovny naopak má knihovnu propojenou se jeho spustitelné bitové kopie, který používá více místa na disku a trvá větší šířku pásma pro přenos.  
  
-   Údržba, opravy zabezpečení a upgradu může být snazší. Pokud vaše aplikace používat běžné funkce v knihovně DLL, pak tak dlouho, dokud argumenty funkce a návratové hodnoty se nemění, můžete implementovat oprav chyb a nasazení aktualizací na knihovnu DLL. Když jsou aktualizovány knihovny DLL, aplikace, které je používají nemusíte překompilovat, nebo znovu připojit a budou využívat nové knihovny DLL ihned po jeho nasazení. Opravy, které provedete v kódu staticky propojený objekt naopak vyžadují, abyste znovu připojit a znovu nasaďte každou aplikaci, která jej používá.  
  
-   Knihovny DLL můžete použít k podpoře následnou trhu. Například ovladač zobrazení knihovny DLL můžete upravit tak, aby podporují zobrazení, které nebyly při prodeji aplikace k dispozici. Můžete použít explicitní propojení se načíst rozšíření aplikací jako knihovny DLL a přidání nových funkcí do aplikace bez znovu sestavit nebo jejího opakovaného nasazení.  
  
-   Dynamické propojování usnadňuje podporu aplikace napsané v různých programovacích jazyků. Programy, které jsou napsané v různých programovacích jazyků můžete volat stejnou funkci knihovny DLL, tak dlouho, dokud dodržují konvence volání funkce. Programy a funkce DLL musí být kompatibilní následujícími způsoby: pořadí, v nichž funkce očekává uložení argumentů na zásobník, rozhodnutí, zda je za vyčištění zásobníku odpovědná funkce nebo aplikace, a informace, zda jsou kterékoli argumenty předávány v registrech.  
  
-   Dynamické propojování poskytuje mechanismus pro rozšíření třídy knihovny MFC. Můžete odvozovat z existujících tříd MFC a umístit je rozšíření MFC DLL pro použití aplikací MFC.  
  
-   Dynamické propojování usnadňuje vytváření mezinárodní verze vaší aplikace. Umístíte do knihovny DLL prostředků specifických pro národní prostředí, je mnohem snazší vytvářet mezinárodní verze aplikace. Místo přesouvání mnoho lokalizované verze aplikace, můžete umístit řetězce a bitových kopií pro každý jazyk v samostatných prostředků knihovny DLL a načtěte odpovídající prostředky pro toto národní prostředí za běhu aplikace.   
  
 Potenciální nevýhodou použití knihoven DLL je, že aplikace není úplný a samostatný; To závisí na existenci samostatný modul knihovny DLL, musí nasazení nebo ověřte sami jako součást instalace.  
  
  
## <a name="more-information-on-how-to-create-and-use-dlls"></a>Další informace o tom, jak vytvořit a používat knihovny DLL  
  
Následující témata obsahují podrobné informace o tom, do knihovny DLL programu v jazyce Visual C++.  
  
 [Návod: Vytvoření a použití dynamické knihovny DLL (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)  
 Popisuje, jak vytvořit a použít knihovnu DLL v sadě Visual Studio.  
  
 [Typy knihoven DLL](../build/kinds-of-dlls.md)  
 Poskytuje informace o různých typech knihoven DLL, které lze vytvořit.  
  
 [DLL – nejčastější dotazy](../build/dll-frequently-asked-questions.md)  
 Poskytuje odpovědi na nejčastější dotazy týkající se knihoven DLL.  
  
 [Propojení spustitelného souboru s knihovnou DLL](../build/linking-an-executable-to-a-dll.md)  
 Popisuje explicitní a implicitní propojení s knihovnou DLL.  
  
 [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
 Popisuje kód inicializace knihovny DLL, které musí být spuštěn při načtení knihovny DLL.  
  
 [Knihovny DLL a chování běhové knihovny v jazyce Visual C++](../build/run-time-library-behavior.md)  
 Popisuje, jakým způsobem provádí knihovna runtime spouštěcí sekvenci knihovny DLL.  
  
 [LoadLibrary a AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
 Popisuje použití **LoadLibrary** a `AfxLoadLibrary` explicitně propojit s knihovnou DLL za běhu.  
  
 [GetProcAddress](../build/getprocaddress.md)  
 Popisuje použití **GetProcAddress** získat adresu exportované funkce v knihovně DLL.  
  
 [FreeLibrary a AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
 Popisuje použití **FreeLibrary** a `AfxFreeLibrary` Pokud již nepotřebujete modul knihovny DLL.  
  
 [Cesta hledání používaná Windows k nalezení knihovny DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
 Popisuje cesta hledání, který operační systém Windows používá k nalezení knihovny DLL v systému.  
  
 [Stavy modulů běžné knihovny MFC DLL dynamicky propojené do MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
 Stavy modulů, které MFC DLL dynamicky propojené s MFC běžný popisuje.  
  
 [MFC – rozšiřující knihovny DLL](../build/extension-dlls-overview.md)  
 Popisuje knihovny DLL, které obvykle implementují opakovaně použitelné třídy odvozené z existujících tříd knihovny Microsoft Foundation Class.  
  
 [Vytvoření knihovny DLL obsahující jen prostředky](../build/creating-a-resource-only-dll.md)  
 Popisuje knihovnu DLL, která obsahuje pouze prostředky jako ikony, bitmapy, řetězce a dialogová okna.  
  
 [Lokalizované prostředky v aplikacích MFC: Satelitní knihovny DLL](../build/localized-resources-in-mfc-applications-satellite-dlls.md)  
 Rozšiřuje podporu pro satelitní knihovny DLL, funkci, která pomáhá při vytváření aplikací lokalizovaných do více jazyků.  
  
 [Import a export](../build/importing-and-exporting.md)  
 Popisuje import veřejných symbolů do aplikace nebo export funkcí z knihovny DLL.  
  
 [Aktivní technologie a knihovny DLL](../build/active-technology-and-dlls.md)  
 Umožňuje serverům objektu k implementaci uvnitř knihovny DLL.  
  
 [Automatizace v knihovně DLL](../build/automation-in-a-dll.md)  
 Popisuje, co nabízí možnost automatizace v průvodci knihovny MFC DLL.  
  
 [Zásady vytváření názvů pro knihovny MFC DLL](../build/naming-conventions-for-mfc-dlls.md)  
 Popisuje, jak se knihovny DLL a knihovny zahrnuté v MFC drží zásady strukturovaného vytváření názvů.  
  
 [Volání funkcí knihovny DLL z aplikací jazyka Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md)  
 Popisuje způsob, jak volat funkce knihovny DLL z aplikací Visual Basic.  
  
## <a name="related-sections"></a>Související oddíly  
  
 [Použití prostředí MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
 Popisuje regulární MFC DLL, které vám umožňují používat knihovny MFC jako součást knihovny DLL systému Windows.  
  
 [DLL verze knihovny MFC](../mfc/tn033-dll-version-of-mfc.md)  
 Popisuje, jak můžete použít MFCxx.dll a MFCxxD.dll (kde x je číslo verze knihovny MFC) sdílené knihovny DLL s aplikací MFC a MFC – rozšiřující knihovny DLL.  
