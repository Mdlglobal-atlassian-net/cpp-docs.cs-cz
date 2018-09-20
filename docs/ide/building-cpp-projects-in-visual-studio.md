---
title: Sestavení projektů C++ v sadě Visual Studio | Dokumentace Microsoftu
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
ms.openlocfilehash: 0da2464684a06b62c6e22ea04bb68a01dc36f42b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382346"
---
# <a name="building-c-projects-in-visual-studio"></a>Sestavení projektů C++ v sadě Visual Studio

V sadě Visual Studio integrované vývojové prostředí (IDE) existuje několik způsobů k sestavení celé řešení nebo pouze jeden projekt v ní. Můžete také upravit nastavení sestavení a určit vlastní kroky sestavení k zefektivnit vašeho vývojového procesu.

K vytvoření řešení, která je otevřený v sadě Visual Studio a vybrat v **Průzkumníka řešení**, můžete:

- V panelu nabídky zvolte **sestavení**, **sestavit řešení**.

- Nebo v **Průzkumníka řešení**, otevřete místní nabídku řešení a klikněte na tlačítko **sestavit řešení**.

- Nebo stisknutím klávesy F7. (To je výchozí klávesovou zkratku pro vývojového nastavení jazyka C/C++.)

- Nebo v [příkazové okno](/visualstudio/ide/reference/command-window) (na řádku nabídek zvolte **zobrazení**, **ostatní Windows**, **příkazové okno**), zadejte `Build.BuildSolution`.

- Nebo v [Snadné spuštění](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) zadejte `build build solution`.

Sestavení projektu, který je vybraný v **Průzkumníka řešení**, můžete:

- V panelu nabídky zvolte **sestavení**, **sestavení \<název projektu >**.

- Nebo v **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **sestavení**.

- Nebo v příkazovém okně (na řádku nabídek zvolte **zobrazení**, **ostatní Windows**, **příkazové okno**), zadejte `Build.BuildOnlyProject`.

- V dialogovém okně Snadné spuštění zadat `build project only build only <project name>`.

Při vytváření aplikace v jazyce Visual C++ v sadě Visual Studio, můžete upravit mnoho nastavení sestavení v dialogovém okně stránky vlastností projektu. Informace o tom, jak nastavit vlastnosti projektu naleznete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

Příklad, jak používat rozhraní IDE k vytvoření, sestavení a ladění projektu jazyka C++, naleznete v tématu [názorný postup: prozkoumání Visual Studio IDE v jazyce C++](/visualstudio/ide/getting-started-with-cpp-in-visual-studio). Pro příklad, jak použít rozhraní IDE k sestavení a C + +/ CLR projekt, naleznete v tématu [návod: kompilace programu v jazyce C++ pro CLR v sadě Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md). Příklad, jak použít rozhraní IDE k vytvoření aplikace pro Windows Runtime, naleznete v tématu [vytvoření první aplikace pro Windows Runtime pomocí jazyka C++](https://msdn.microsoft.com/library/windows/apps/hh974580.aspx).

Další informace o tom, jak vytvářet, upravovat nastavení sestavení a zadat vlastní kroky sestavení, naleznete v následujících článcích.

## <a name="in-this-section"></a>V tomto oddílu

[Seznámení s kroky vlastního sestavení a s událostmi sestavení](../ide/understanding-custom-build-steps-and-build-events.md)<br>
Popisuje, jak přizpůsobit proces sestavení v integrovaném vývojovém prostředí.

[Běžná makra pro příkazy a vlastnosti sestavení](../ide/common-macros-for-build-commands-and-properties.md)<br>
Seznam maker, které můžete použít, kde se přijímají řetězce.

[Sestavení externích projektů](../ide/building-external-projects.md)<br>
Tento článek popisuje vytváření projektů, které používají zařízení mimo integrované vývojové prostředí.

[Soubory projektu](../ide/project-files.md)<br>
Představuje strukturu XML souboru .vcxproj.

## <a name="related-sections"></a>Související oddíly

[VC ++ adresáře, projekty, dialogové okno Možnosti](vcpp-directories-property-page.md)<br>
(Pouze projekty MSBuild) Popisuje, jak změnit cesty hledání pro spustitelné soubory, zahrňte soubory, soubory knihovny a soubory zdrojového kódu během sestavení.

[Kompilace a sestavení](/visualstudio/ide/compiling-and-building-in-visual-studio)<br>
Obsahuje informace o sestavování v sadě Visual Studio.

[Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)<br>
Obsahuje odkazy na témata popisující vytváření vaší aplikace z příkazového řádku nebo z integrovaného vývojového prostředí sady Visual Studio.

[Referenční zdroje k sestavení programu v jazyce C/C++](../build/reference/c-cpp-building-reference.md)<br>
Obsahuje odkazy na přehled o vytváření programů v jazyce C++, kompilátoru a linkeru možnosti a nástroje pro další sestavení.

[Upgrade projektů z dřívějších verzí Visual C++](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br>
Obsahuje odkazy na témata týkající se problémů na upgrade na novější verze sady nástrojů kompilátoru projektu v jazyce C++.

[Visual C++ Průvodce přenosem a upgradováním](../porting/visual-cpp-porting-and-upgrading-guide.md) podrobné informace o tom, jak upgradovat aplikací v jazyce C++, které byly vytvořeny v dřívějších verzích sady Visual Studio a postupu při migraci aplikací, které byly vytvořeny pomocí jiných nástrojů než Visual Studio.

## <a name="see-also"></a>Viz také

[Univerzální aplikace pro Windows (C++)](../windows/universal-windows-apps-cpp.md)