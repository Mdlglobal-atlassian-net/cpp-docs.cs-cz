---
title: Zdroje a prostředky
ms.date: 08/28/2019
ms.topic: article
ms.assetid: dade2f6b-c51f-4c33-9023-41956ae4b5f6
f1_keywords:
- VC.Project.VCResourceCompilerTool.PreprocessorDefinitions
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- VC.Project.VCResourceCompilerTool.Culture
- VC.Project.VCResourceCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCResourceCompilerTool.IgnoreStandardIncludePath
- VC.Project.VCResourceCompilerTool.ShowProgress
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.ResourceOutputFileName
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: c4a3048bfa07e9635662534b510fa57caa091f00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336080"
---
# <a name="resources-property-page"></a>Stránka vlastností Zdroje

U nativních desktopových programů systému Windows vytvoří sestavení [kompilátor prostředků (rc.exe) a](/windows/win32/menurc/resource-compiler) přidá do binárního souboru obrázky, řetězcové tabulky a soubory *RES.* Vlastnosti vystavené na této stránce vlastností jsou předány kompilátoru prostředků, nikoli kompilátoru Jazyka C++ nebo propojovacímu programu. Další informace o zde uvedených vlastnostech a o tom, jak jsou mapovány na možnosti příkazového řádku RC, naleznete [v tématu Použití RC (Příkazový řádek RC).](/windows/win32/menurc/using-rc-the-rc-command-line-) Informace o tom, jak získat přístup ke stránkám vlastností **Resources,** naleznete [v tématu Nastavení kompilátoru jazyka C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md). Chcete-li programově získat <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>přístup k těmto vlastnostem, naleznete v tématu .

Vlastnosti prostředků .NET v aplikacích C++/CLI jsou vystaveny na [stránce vlastností spravovaných prostředků](managed-resources-property-page.md).

## <a name="preprocessor-definitions"></a>Definice preprocesoru

Určuje jednu nebo více definic pro kompilátor prostředků. (/d[makro])

## <a name="undefine-preprocessor-definitions"></a>Nedefinovat definice preprocesoru

Zrušit definici symbolu. (/u)

## <a name="culture"></a>Culture

Seznam jazykové verze (například angličtina usa nebo italština) použité v prostředcích. (/l [num])

## <a name="additional-include-directories"></a>Další zahrnutí adresářů

Určuje jeden nebo více adresářů, které chcete přidat do cesty zahrnutí; použijte oddělovač středníku, pokud je více než jeden. (/I[cesta])

## <a name="ignore-standard-include-paths"></a>Ignorovat standardní cesty zahrnutí

Zabrání kompilátoru prostředků v hledání souborů zahrnutí v adresářích určených v proměnných prostředí INCLUDE. (/X)

## <a name="show-progress"></a>Zobrazit průběh

Odeslat zprávy o průběhu do výstupního okna. (/v)

## <a name="suppress-startup-banner"></a>Potlačit spouštěcí banner

Potlačit zobrazení spouštěcího banneru a informační zprávy (/nologo)

## <a name="resource-file-name"></a>Název souboru prostředků

Určuje název souboru prostředků (/fo[file])

## <a name="null-terminate-strings"></a>Nulové řetězce ukončení

Připojit null pro všechny řetězce v tabulkách řetězců. (/n)

## <a name="see-also"></a>Viz také

[Odkaz na stránku vlastnosti projektu jazyka C++](property-pages-visual-cpp.md)
