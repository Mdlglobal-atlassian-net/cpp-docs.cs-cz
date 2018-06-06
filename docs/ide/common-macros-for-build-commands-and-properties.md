---
title: Běžné makra pro příkazy a vlastnosti sestavení
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs:
- C++
helpviewer_keywords:
- $(FrameworkSDKDir) macro
- ProjectName macro $(ProjectName)
- DevEnvDir macro $(DevEnvDir)
- $(DevEnvDir) macro
- TargetPath macro $(TargetPath)
- VSInstallDir macro $(VSInstallDir)
- $(InputFileName) macro
- $(SolutionFileName) macro
- macros [C++], build macros
- InputFileName macro $(InputFileName)
- $(VCInstallDir) macro
- $(IntDir) macro
- $(ConfigurationName) macro
- SolutionDir macro $(SolutionDir)
- $(TargetPath) macro
- $(Inherit) macro
- $(SolutionPath) macro
- WebDeployRoot macro $(WebDeployRoot)
- WebDeployPath macro $(WebDeployPath)
- StopEvaluating macro $(StopEvaluating)
- $(RootNamespace) macro
- $(WebDeployRoot) macro
- ProjectPath macro $(ProjectPath)
- $(ProjectPath) macro
- $(InputDir) macro
- SolutionName macro $(SolutionName)
- ProjectExt macro $(ProjectExt)
- $(TargetExt) macro
- $(ProjectFileName) macro
- TargetName macro $(TargetName)
- $(References) macro
- References macro $(References)
- TargetExt macro $(TargetExt)
- ProjectDir macro $(ProjectDir)
- $(TargetDir) macro
- SolutionExt macro $(SolutionExt)
- $(SolutionDir) macro
- ProjectFileName macro $(ProjectFileName)
- VCInstallDir macro $(VCInstallDir)
- $(InputExt) macro
- $(TargetFileName) macro
- $(SolutionExt) macro
- PlatformName macro $(PlatformName)
- IntDir macro $(IntDir)
- $(FrameworkVersion) macro
- $(ProjectDir) macro
- build macros [C++]
- InputPath macro $(InputPath)
- $(VSInstallDir) macro
- $(WebDeployPath) macro
- TargetFileName macro $(TargetFileName)
- NoInherit macro $(NoInherit)
- ConfigurationName macro $(ConfigurationName)
- $(ProjectExt) macro
- TargetDir macro $(TargetDir)
- InputName macro $(InputName)
- $(ProjectName) macro
- FrameworkSDKDir macro $(FrameworkSDKDir)
- $(ParentName) macro
- InputExt macro $(InputExt)
- $(SafeRootNamespace) macro
- InputDir macro $(InputDir)
- $(FxCopDir) macro
- $(RemoteMachine) macro
- Inherit macro $(Inherit)
- FrameworkVersion macro $(FrameworkVersion)
- $(StopEvaluating) macro
- $(OutDir) macro
- FrameworkDir macro $(FrameworkDir)
- SolutionFileName macro $(SolutionFileName)
- $(NoInherit) macro
- RemoteMachine macro $(RemoteMachine)
- properties [C++], build property macros
- $(TargetName) macro
- $(SolutionName) macro
- $(InputPath) macro
- ParentName macro $(ParentName)
- OutDir macro $(OutDir)
- SafeRootNamespace macro $(SafeRootNamespace)
- FxCopDir macro $(FxCopDir)
- $(InputName) macro
- RootNamespace macro $(RootNamespace)
- builds [C++], macros
- $(FrameworkDir) macro
- $(PlatformName) macro
- SolutionPath macro $(SolutionPath)
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 278cb34a49650d88b9e7de9efd8456ff430aca63
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569924"
---
# <a name="common-macros-for-build-commands-and-properties"></a>Běžné makra pro příkazy a vlastnosti sestavení

V závislosti na možnosti instalace sady Visual Studio můžete zpřístupnit stovky makra pro vás. Tyto odpovídat vlastnosti nástroje MSBuild, které jsou nastavené ve výchozím nastavení, nebo soubory props nebo .targets nebo nastavení projektu. Tyto makra lze použít kdekoli v projektu na **stránky vlastností** dialogové, kde jsou přijímány řetězce. Tyto makra se nerozlišují malá a velká písmena.

## <a name="view-the-current-properties-and-macros"></a>Zobrazit aktuální vlastnosti a makra

Zobrazit aktuálně k dispozici makra na libovolné stránce vlastnost **stránky vlastností** dialogové okno, vyberte na šipku rozevíracího seznamu na konci řádku vlastnost. Pokud **upravit** je k dispozici, zvolte jej a potom v dialogovém okně Upravit **makra** tlačítko. Aktuální sadu vlastností a makra viditelné pro Visual Studio je uveden spolu s aktuální hodnota pro každou. Další informace najdete v tématu **Specifying User-Defined hodnoty** části [stránky vlastností](../ide/property-pages-visual-cpp.md).

## <a name="list-of-common-macros"></a>Seznam běžných makra

Tato tabulka popisuje podmnožinu běžně používané k dispozici makra. Tento seznam je daleko od vyčerpávající. Podrobnosti na způsob vytváření a použít jako makra v VCXPROJ soubory props, .targets a definice vlastnosti nástroje MSBuild najdete v tématu [vlastnosti nástroje MSBuild](/visualstudio/msbuild/msbuild-properties).

|– Makro|Popis|
|-----------|-----------------|
|**$(Configuration)**|Název aktuální konfigurací projektu, například "Debug".|
|**$(Devenvdir) –**|Instalační adresář sady Visual Studio (definovaný jako jednotka + cesta); zahrnuje koncové zpětné lomítko,\\'.|
|**$(FrameworkDir)**|Adresář, do kterého byla nainstalována rozhraní .NET Framework.|
|**$(Frameworksdkdir) –**|Adresář, do které jste nainstalovali rozhraní .NET Framework. Rozhraní .NET Framework je může nainstalovat jako součást sady Visual Studio, nebo samostatně.|
|**$(FrameworkVersion)**|Verze rozhraní .NET Framework, sada Visual Studio. V kombinaci s **$(FrameworkDir)**, úplná cesta k verzi rozhraní .NET Framework použití Visual Studio.|
|**$(Fxcopdir) –**|Cesta k souboru fxcop.cmd. Soubor fxcop.cmd není nainstalován ve všech edicích Visual C++.|
|**$(IntDir)**|Cesta k adresáři zadaná pro zprostředkující soubory. Pokud to je relativní cesta, zprostředkující soubory přejděte na tuto cestu k adresáři projektu. Tato cesta by měla mít koncové lomítko. To přeloží na hodnotu **zprostředkující Directory** vlastnost. Nepoužívejte **$(outdir) –** k definování této vlastnosti.|
|**$(Outdir) –**|Cesta k adresáři výstupního souboru. Pokud to je relativní cesta, výstupní soubory přejděte na tuto cestu k adresáři projektu. Tato cesta by měla mít koncové lomítko. To se přeloží na hodnotu **výstupního adresáře** vlastnost. Nepoužívejte **$(IntDir)** k definování této vlastnosti.|
|**$(Platform)**|Název aktuální platformy projektu, například "Win32".|
|**$(Projectdir) –**|Do adresáře projektu (definovaný jako jednotka + cesta); zahrnuje koncové zpětné lomítko,\\'.|
|**$(ProjectExt)**|Přípona souboru projektu. Obsahuje,., před příponu souboru.|
|**$(ProjectFileName)**|Název souboru projektu (definován jako základní název + přípona souboru).|
|**$(ProjectName)**|Základní název projektu.|
|**$(ProjectPath)**|Absolutní cesta název projektu (definován jako jednotka + cesta + základní název + přípona souboru).|
|**$(RemoteMachine)**|Nastavte na hodnotu **vzdáleného počítače** vlastnost na stránce vlastností ladění. V tématu [Změna nastavení projektu pro konfiguraci ladění C/C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) Další informace.|
|**$(RootNameSpace)**|Obor názvů, pokud existuje, obsahující aplikaci.|
|**$(Solutiondir) –**|Adresář řešení (definovaný jako jednotka + cesta); zahrnuje koncové zpětné lomítko,\\'. Definována pouze při sestavování řešení v prostředí IDE.|
|**$(Solutionext) –**|Přípona souboru řešení. Obsahuje,., před příponu souboru. Definována pouze při sestavování řešení v prostředí IDE.|
|**$(Solutionfilename) –**|Název souboru řešení (definován jako základní název + přípona souboru). Definována pouze při sestavování řešení v prostředí IDE.|
|**$(SolutionName)**|Základní název řešení. Definována pouze při sestavování řešení v prostředí IDE.|
|**$(Solutionpath) –**|Absolutní cesta název řešení (definován jako jednotka + cesta + základní název + přípona souboru). Definována pouze při sestavování řešení v prostředí IDE.|
|**$(TargetDir)**|Adresář primárního výstupního souboru pro sestavení (definovaný jako jednotka + cesta); zahrnuje koncové zpětné lomítko,\\'.|
|**$(Targetext) –**|Přípona souboru primárního výstupního souboru pro sestavení. Obsahuje,., před příponu souboru.|
|**$(Targetfilename) –**|Název souboru primárního výstupního souboru pro sestavení (definován jako základní název + přípona souboru).|
|**$(TargetName)**|Základní název primárního výstupního souboru pro sestavení.|
|**$(TargetPath)**|Absolutní cesta název primárního výstupního souboru pro sestavení (definován jako jednotka + cesta + základní název + přípona souboru).|
|**$(VCInstallDir)**|Adresář, který obsahuje obsah C++ instalace Visual Studia. Tato vlastnost obsahuje verzi cílové nástrojů Visual C++, který se může lišit, hostitelské sady Visual Studio. Například při sestavení s `$(PlatformToolset) = v140`, **$(VCInstallDir)** obsahuje cestu k instalačním Visual C++ 2015.|
|**$(VSInstallDir)**|Adresář, do které jste nainstalovali Visual Studio. Tato vlastnost obsahuje verzi cílové nástrojů Visual Studio, který se může lišit, hostitelské sady Visual Studio. Například při sestavení s `$(PlatformToolset) = v110`, **$(VSInstallDir)** obsahuje cestu k instalaci sady Visual Studio 2012.|
|**$(Webdeploypath) –**|Relativní cestu z kořene nasazení webu k kde výstup projektu patří. Vrací stejnou hodnotu jako <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>.|
|**$(Webdeployroot) –**|Absolutní cestu k umístění  **\<localhost >**. Například c:\inetpub\wwwroot.|

## <a name="obsolete-macros"></a>Zastaralé makra

Systém sestavení pro jazyk C++ byl výrazně změněn mezi Visual Studio 2008 a Visual Studio 2010. Mnoho makra použít ve starší typy projektů se změnil na nové. Tyto makra se již nepoužívají nebo byly nahrazeny jednu nebo více vlastností ekvivalentní nebo [makro metadata položky](/visualstudio/msbuild/itemmetadata-element-msbuild) (**%(**_název_**)**) hodnoty. Makra, které jsou označeny "migrované" můžete aktualizovat nástroj pro migraci projektu. Pokud projekt, který obsahuje makro migraci ze sady Visual Studio 2008 nebo nižší do sady Visual Studio 2010, Visual Studio převede makro na ekvivalentní aktuální makro. Novější verze sady Visual Studio se nedá převést projektů ze sady Visual Studio 2008 a dříve na nový typ projektu. Je nutné převést tyto projekty ve dvou krocích; Nejprve je převést na Visual Studio 2010 a výsledek pak převést na vaše novější verze sady Visual Studio. Další informace najdete v tématu [přehled potenciální problémy upgradu](../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

|– Makro|Popis|
|-----------|-----------------|
|**$(Inputdir) –**|(Migrováno.) Adresář souboru vstupního souboru (definovaný jako jednotka + cesta); zahrnuje koncové zpětné lomítko,\\'. Pokud projekt se vstup, pak je ekvivalentní této makro **$(projectdir) –**.|
|**$(Inputext) –**|(Migrováno.) Přípona souboru vstupního souboru. Obsahuje,., před příponu souboru. Pokud projekt se vstup, pak je ekvivalentní této makro **$(ProjectExt)**. U zdrojových souborů, je to **%(Extension)**.|
|**$(InputFileName)**|(Migrováno.) Název souboru vstupního souboru (definován jako základní název + přípona souboru). Pokud projekt se vstup, pak je ekvivalentní této makro **$(ProjectFileName)**. U zdrojových souborů, je to **%(Identity)**.|
|**$(InputName)**|(Migrováno.) Základní název souboru vstupního souboru. Pokud projekt se vstup, pak je ekvivalentní této makro **$(ProjectName)**. U zdrojových souborů, je to **%(Filename)**.|
|**$(InputPath)**|(Migrováno.) Absolutní cesta název souboru vstupního souboru (definován jako jednotka + cesta + základní název + přípona souboru). Pokud projekt se vstup, pak je ekvivalentní této makro **$(ProjectPath)**. U zdrojových souborů, je to **%(FullPath)**.|
|**$(Parentname) –**|Název položky obsahující tuto položku projektu. To bude název nadřazené složky nebo název projektu.|
|**$(SafeInputName)**|Název souboru jako platný název třídy, bez přípony souboru. Tato vlastnost nemá naprosto stejný.|
|**$(SafeParentName)**|Název nadřazeného okamžitou ve formátu platný název. Například formulář je nadřazený tohoto souboru RESX. Tato vlastnost nemá naprosto stejný.|
|**$(Saferootnamespace) –**|Název oboru názvů, ve kterém bude průvodců projektu přidejte kód. Tento název oboru názvů bude obsahovat pouze znaky, které jsou přípustné v platný identifikátor C++. Tato vlastnost nemá naprosto stejný.|

## <a name="see-also"></a>Viz také:

- [Sestavení projektů C++ v sadě Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)
- [Visual C++ Průvodce přenosem a upgradováním](../porting/visual-cpp-porting-and-upgrading-guide.md)
- [Přehled potenciální problémy upgradu](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
