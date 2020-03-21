---
title: Zdroje
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
ms.openlocfilehash: 4f3688da4feb11f673e11372e5df086dc8c7e21a
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078282"
---
# <a name="resources-property-page"></a>Stránka vlastností prostředků

Pro nativní desktopové programy systému Windows vyvolá sestavení [kompilátor prostředků (RC. exe)](/windows/win32/menurc/resource-compiler) pro přidání obrázků, tabulek řetězců a souborů *. res* do binárního souboru. Vlastnosti, které jsou vystaveny na této stránce vlastností, jsou předány kompilátoru prostředků, C++ nikoli kompilátoru nebo linkeru. Další informace o zde uvedených vlastnostech a způsobu mapování na možnosti příkazového řádku RC najdete v tématu [použití RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-). Informace o tom, jak získat přístup ke stránkám vlastností **prostředků** , naleznete v tématu [Nastavení vlastností kompilátoru a sestavení v sadě C++ Visual Studio](../working-with-project-properties.md). Chcete-li programově přistupovat k těmto vlastnostem, přečtěte si téma <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>.

Vlastnosti pro prostředky .NET v C++aplikacích/CLI se zveřejňují na [stránce vlastností spravované prostředky](managed-resources-property-page.md).

## <a name="preprocessor-definitions"></a>Definice preprocesoru

Určuje jednu nebo více definic pro kompilátor prostředků. (/d [makro])

## <a name="undefine-preprocessor-definitions"></a>Zrušit Definice preprocesoru

Zruší definici symbolu. přepínač

## <a name="culture"></a>Kultura

Vypíše jazykovou verzi (například AMERICKou angličtinu nebo italštinu) použitou v prostředcích. (/l [číslo])

## <a name="additional-include-directories"></a>Další adresáře k zahrnutí

Určuje jeden nebo více adresářů, které mají být přidány do cesty include; použijte oddělovač středníkem, pokud je více než jeden. (/I [cesta])

## <a name="ignore-standard-include-paths"></a>Ignorovat standardní cesty zahrnutí

Zabrání kompilátoru prostředků v hledání souborů k zahrnutí v adresářích zadaných v proměnných prostředí INCLUDE. /X

## <a name="show-progress"></a>Zobrazit průběh

Odeslat zprávy o průběhu do okna výstup. /v

## <a name="suppress-startup-banner"></a>Potlačit úvodní nápis

Potlačit zobrazení úvodního nápisu a informační zprávy (/nologo)

## <a name="resource-file-name"></a>Název souboru prostředků

Určuje název souboru prostředků (/FO [soubor]).

## <a name="null-terminate-strings"></a>Prázdné řetězce ukončení

Připojí hodnoty null k všem řetězcům v tabulce řetězců. n

## <a name="see-also"></a>Viz také

[C++odkaz na stránku vlastností projektu](property-pages-visual-cpp.md)