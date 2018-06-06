---
title: Sestavení projektů C++ v sadě Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ projects, building
- projects [C++], building
- builds [C++], about building in Visual Studio
ms.assetid: 9e8bc1a2-bb17-4951-937a-c757ed88d2d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7008e7fe670471301968482fbd4c6c758f0ff5e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33340499"
---
# <a name="building-c-projects-in-visual-studio"></a>Sestavení projektů C++ v sadě Visual Studio
V sadě Visual Studio integrované vývojové prostředí (IDE) existuje několik způsobů vytvářet celé řešení nebo jedním projektu v ní. Můžete také upravit nastavení sestavení a zadejte vlastní kroky sestavení aby vývojových procesech efektivnější.  
  
 K vytvoření řešení, které je otevřete v sadě Visual Studio a vybrané v **Průzkumníku**, můžete:  
  
-   Na řádku nabídek zvolte **sestavení**, **sestavit řešení**.  
  
-   Nebo v **Průzkumníku řešení**, otevřete místní nabídku pro řešení a zvolte **sestavit řešení**.  
  
-   Nebo stiskněte klávesu F7. (Toto je výchozí klávesové zkratky pro nastavení vývoj C/C++.)  
  
-   Nebo v [příkazové okno](/visualstudio/ide/reference/command-window) (na řádku nabídek zvolte **zobrazení**, **ostatní okna**, **příkazové okno**), zadejte `Build.BuildSolution`.  
  
-   Nebo v [Snadné spuštění](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) zadejte `build build solution`.  
  
 Pro vytvoření projektu, který je vybraný v **Průzkumníku**, můžete:  
  
-   Na řádku nabídek zvolte **sestavení**, **sestavení \<název projektu >**.  
  
-   Nebo v **Průzkumníku řešení**, otevřete místní nabídky projektu a zvolte **sestavení**.  
  
-   Nebo, v příkazovém okně (na řádku nabídek zvolte **zobrazení**, **ostatní okna**, **příkazové okno**), zadejte `Build.BuildOnlyProject`.  
  
-   Nebo v dialogovém okně Snadné spuštění zadejte `build project only build only <project name>`.  
  
 Když vytvoříte aplikaci Visual C++ v sadě Visual Studio, můžete upravit řadu nastavení sestavení v dialogovém okně stránky vlastností projektu. Informace o tom, jak nastavit vlastnosti projektu najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).  
  
 Příklad o tom, jak vytvořit sestavení a ladění projektu jazyka C++ pomocí rozhraní IDE, naleznete v části [návod: prozkoumat Visual Studio IDE s jazykem C++](/visualstudio/ide/getting-started-with-cpp-in-visual-studio). Příklad o tom, jak pomocí rozhraní IDE sestavení C + +/ projektu CLR, najdete v části [návod: kompilace programu C++ pro CLR v sadě Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md). Příklad o tom, jak pomocí rozhraní IDE k vytvoření aplikace pro prostředí Windows Runtime naleznete v části [vytvoření první aplikace Windows Runtime s použitím jazyka C++](http://msdn.microsoft.com/library/windows/apps/hh974580.aspx).  
  
 Číst informace o tom, jak vytvářet, upravovat nastavení sestavení a zadejte vlastní kroky sestavení, najdete v následujících článcích.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Seznámení s kroky vlastního sestavení a s událostmi sestavení](../ide/understanding-custom-build-steps-and-build-events.md)  
 Popisuje postup přizpůsobení procesu sestavení v integrovaném vývojovém prostředí.  
  
 [Běžná makra pro příkazy a vlastnosti sestavení](../ide/common-macros-for-build-commands-and-properties.md)  
 Uvádí makra, které můžete použít, pokud jsou přijaty řetězce.  
  
 [Sestavení externích projektů](../ide/building-external-projects.md)  
 Popisuje sestavení projektů, které používají zařízení mimo integrované vývojové prostředí.  
  
 [Soubory projektu](../ide/project-files.md)  
 Uvede strukturu XML souboru.  
  
## <a name="related-sections"></a>Související oddíly  
 [VC ++ adresáře, projekty, dialogové okno Možnosti](vcpp-directories-property-page.md)  
 (Jenom projektů MSBuild) Popisuje, jak změnit cesta hledání pro spustitelné soubory, zahrnout soubory, soubory knihovny a soubory zdrojového kódu během sestavení.  
  
 [Kompilace a sestavení](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 Poskytuje informace o sestavení v sadě Visual Studio.  
  
 [Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)  
 Obsahuje odkazy na témata popisující sestavení programu z příkazového řádku nebo z integrovaného vývojového prostředí sady Visual Studio.  
  
 [Referenční zdroje k sestavení programu v jazyce C/C++](../build/reference/c-cpp-building-reference.md)  
 Obsahuje odkazy na přehled sestavování programů v jazycích C++, kompilátoru a linkeru možnosti a další sestavovací nástroje.  
  
 [Upgrade projektů z dřívějších verzí Visual C++](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
 Obsahuje odkazy na témata týkající se problémů na upgrade na novější verze sady nástrojů kompilátoru projektu jazyka C++.  
  
[Průvodce přenosem a upgradem Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)  
  Podrobné informace o tom, jak upgradovat aplikací C++, které byly vytvořeny v dřívějších verzích sady Visual Studio a také k migraci aplikace, které byly vytvořeny pomocí nástrojů pro jiné než Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Univerzální aplikace pro Windows (C++)](../windows/universal-windows-apps-cpp.md)