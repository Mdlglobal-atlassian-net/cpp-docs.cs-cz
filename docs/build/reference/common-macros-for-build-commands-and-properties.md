---
title: Běžná makra pro příkazy MSBuild a vlastnosti
ms.date: 03/20/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
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
- $(PlatformShortName) macro
- SolutionPath macro $(SolutionPath)
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
ms.openlocfilehash: abb42db6a44f1c48d120eff1f117e06c970b6b44
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221783"
---
# <a name="common-macros-for-msbuild-commands-and-properties"></a>Běžná makra pro příkazy MSBuild a vlastnosti

V závislosti na možnostech instalace sady Visual Studio můžete zpřístupnit stovky makra je v projektu sady Visual Studio (založené na MSBuild). Tyto příkazy odpovídají vlastnosti nástroje MSBuild, které jsou nastaveny ve výchozím nastavení, nebo v souborech .props nebo .targets nebo v nastavení projektu. Tato makra lze použít kdekoli v projektu **stránky vlastností** dialogovému oknu, kde se přijímají řetězce. Tato makra se nerozlišují malá a velká písmena.

## <a name="view-the-current-properties-and-macros"></a>Zobrazit aktuální vlastnosti a makra

Zobrazit všechny aktuálně dostupná makra v **stránky vlastností** dialogového okna, v části **adresáře VC ++**, klikněte na šipku rozevíracího seznamu na konci řádku vlastnost. Klikněte na **upravit** a poté v dialogovém okně upravit, vyberte **makra** tlačítko. Aktuální sadu vlastností a makra, které jsou viditelné pro Visual Studio je uveden spolu s aktuální hodnotou pro všechny. Další informace najdete v tématu **Specifying User-Defined hodnoty** část [odkaz na stránku vlastností projektu C++](property-pages-visual-cpp.md).

![Tlačítko makra VC ++](../media/vcppdir_libdir_macros.png "nabídky makra")

## <a name="list-of-common-macros"></a>Seznam běžných makra

Tato tabulka popisuje běžně používané podmnožinou dostupná makra; Existuje mnoho více nejsou uvedené tady. Přejděte **makra** dialogovém okně můžete zobrazit všechny vlastnosti a jejich aktuálními hodnotami ve vašem projektu. Podrobnosti o definice vlastností MSBuild jsou vytvořeny a použít jako maker v .props .targets a souborů VCXPROJ najdete v tématu [vlastnosti nástroje MSBuild](/visualstudio/msbuild/msbuild-properties).

|– Makro|Popis|
|-----------|-----------------|
|**$(Configuration)**|Název aktuální konfigurace projektu, například "Debug".|
|**$(DevEnvDir)**|Instalační adresář sady Visual Studio (definované jako jednotka + cesta); zahrnuje koncové lomítko "\\".|
|**$(FrameworkDir)**|Adresář, do kterého bylo nainstalované rozhraní .NET Framework.|
|**$(FrameworkSDKDir)**|Adresář, do nějž jste nainstalovali rozhraní .NET Framework. Rozhraní .NET Framework může být nainstalovány jako součást sady Visual Studio nebo samostatně.|
|**$(FrameworkVersion)**|Verze rozhraní .NET Framework používá sada Visual Studio. V kombinaci s **$(FrameworkDir)**, úplná cesta k verzi rozhraní .NET Framework používá Visual Studio.|
|**$(FxCopDir)**|Cesta k souboru fxcop.cmd. Soubor fxcop.cmd není nainstalován ve všech edicích sady Visual Studio.|
|**$(IntDir)**|Cesta do adresáře určeného pro zprostředkující soubory. Pokud je relativní cesta, zprostředkující soubory přejděte k této cestě se připojí k adresáři projektu. Tato cesta by měla mít koncové lomítko. To řeší na hodnotu **zprostředkující adresář** vlastnost. Nepoužívejte **$(OutDir)** definovat tuto vlastnost.|
|**$(OutDir)**|Cesta k adresáři výstupního souboru. Pokud je relativní cesta, výstupní soubory přejděte k této cestě se připojí k adresáři projektu. Tato cesta by měla mít koncové lomítko. To řeší na hodnotu **výstupní adresář** vlastnost. Nepoužívejte **$(IntDir)** definovat tuto vlastnost.|
|**$(Platform)**|Název aktuální platformy projektu, například "Win32".|
|**$(PlatformShortName)**|Krátký název aktuální architekturu, například "x86" nebo "x64".|
|**$(ProjectDir)**|Adresář projektu (definované jako jednotka + cesta); zahrnuje koncové lomítko "\\".|
|**$(ProjectExt)**|Přípona souboru projektu. Zahrnuje "." před příponu souboru.|
|**$(ProjectFileName)**|Název souboru projektu (definované jako základní název a příponu souboru).|
|**$(ProjectName)**|Základní název projektu.|
|**$(ProjectPath)**|Absolutní cesta název projektu (definované jako jednotka + cesta + název základní + přípona souboru).|
|**$(RemoteMachine)**|Nastavte na hodnotu **vzdálený počítač** vlastnost na stránce vlastností ladění. Zobrazit [Změna nastavení projektu pro konfiguraci ladění jazyka C/C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) Další informace.|
|**$(RootNameSpace)**|Obor názvů, pokud existuje, obsahující aplikaci.|
|**$(SolutionDir)**|Adresář řešení (definované jako jednotka + cesta); zahrnuje koncové lomítko "\\". Definovat pouze při sestavování řešení v integrovaném vývojovém prostředí.|
|**$(SolutionExt)**|Přípona souboru řešení. Zahrnuje "." před příponu souboru. Definovat pouze při sestavování řešení v integrovaném vývojovém prostředí.|
|**$(SolutionFileName)**|Název souboru řešení (definované jako základní název a příponu souboru). Definovat pouze při sestavování řešení v integrovaném vývojovém prostředí.|
|**$(SolutionName)**|Základní název řešení. Definovat pouze při sestavování řešení v integrovaném vývojovém prostředí.|
|**$(SolutionPath)**|Absolutní cesta název řešení (definované jako jednotka + cesta + název základní + přípona souboru). Definovat pouze při sestavování řešení v integrovaném vývojovém prostředí.|
|**$(TargetDir)**|Adresář primárního výstupního souboru pro sestavení (definuje jako jednotka + cesta); zahrnuje koncové lomítko "\\".|
|**$(TargetExt)**|Přípona primárního výstupního souboru pro sestavení. Zahrnuje "." před příponu souboru.|
|**$(TargetFileName)**|Název souboru primárního výstupního souboru pro sestavení (definované jako základní název a příponu souboru).|
|**$(TargetName)**|Základní název primárního výstupního souboru pro sestavení.|
|**$(TargetPath)**|Absolutní cesta název primárního výstupního souboru pro sestavení (definuje jako jednotka + cesta + název základní + přípona souboru).|
|**$(VCInstallDir)**|Adresář, který obsahuje obsah jazyka C++ instalace sady Visual Studio. Tato vlastnost obsahuje verzi cílové Microsoft C++ sada nástrojů (MSVC), který se může lišit, který hostitel Visual Studio. Například při sestavení s `$(PlatformToolset) = v140`, **$(VCInstallDir)** obsahuje cestu k instalaci sady Visual Studio 2015.|
|**$(VSInstallDir)**|Adresář, do nějž jste nainstalovali aplikaci Visual Studio. Tato vlastnost obsahuje verzi nástroje na cílovou sadu nástrojů Visual Studio, který se může lišit, který hostitel Visual Studio. Například při sestavení s `$(PlatformToolset) = v110`, **$(VSInstallDir)** obsahuje cestu k instalaci sady Visual Studio 2012.|
|**$(WebDeployPath)**|Relativní cesta z kořene nasazení webu na kde výstup projektu patří. Vrátí stejnou hodnotu jako <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>.|
|**$(WebDeployRoot)**|Absolutní cesta k umístění  **\<localhost >**. Například c:\inetpub\wwwroot.|

## <a name="obsolete-macros"></a>Zastaralé makra

Systém sestavení pro C++ se významně změnil mezi Visual Studio 2008 a sadu Visual Studio 2010. Mnoho makra použitá v starších typech projektů se změnily nové značky. Tato makra se již nepoužívají nebo byly nahrazeny jednu nebo více rovnocenné vlastností nebo [makro položky metadat](/visualstudio/msbuild/itemmetadata-element-msbuild) (**%(**_název_**)**) hodnoty. Makra, které jsou označeny "migrované" můžete aktualizovat projekt nástroj pro migraci. Pokud projekt, který obsahuje makro migraci ze sady Visual Studio 2008 nebo dřívějších k sadě Visual Studio 2010, Visual Studio převede makra ekvivalentní aktuální – makro. Novější verze sady Visual Studio nelze převést projekty ze sady Visual Studio 2008 a dříve na nový typ projektu. Je nutné převést tyto projekty ve dvou krocích; Nejprve je převést na sadu Visual Studio 2010 a poté převést výsledek do novější verze sady Visual Studio. Další informace najdete v tématu [přehled potenciálních problémů s upgradem](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

|– Makro|Popis|
|-----------|-----------------|
|**$(InputDir)**|(Migroval). Adresář výstupního souboru (definované jako jednotka + cesta); zahrnuje koncové lomítko "\\". Pokud je vstup projekt, pak toto makro je ekvivalentní **$(ProjectDir)**.|
|**$(InputExt)**|(Migroval). Přípona souboru vstupního souboru. Zahrnuje "." před příponu souboru. Pokud je vstup projekt, pak toto makro je ekvivalentní **$(ProjectExt)**. Pro zdrojové soubory. to je **%(Extension)**.|
|**$(InputFileName)**|(Migroval). Název souboru vstupní soubor (definované jako základní název a příponu souboru). Pokud je vstup projekt, pak toto makro je ekvivalentní **$(ProjectFileName)**. Pro zdrojové soubory. to je **%(Identity)**.|
|**$(InputName)**|(Migroval). Základní název výstupního souboru. Pokud je vstup projekt, pak toto makro je ekvivalentní **$(ProjectName)**. Pro zdrojové soubory. to je **%(Filename)**.|
|**$(InputPath)**|(Migroval). Absolutní cesta název výstupního souboru (definované jako jednotka + cesta + název základní + přípona souboru). Pokud je vstup projekt, pak toto makro je ekvivalentní **$(ProjectPath)**. Pro zdrojové soubory. to je **%(FullPath)**.|
|**$(ParentName)**|Název položky obsahující tuto položku projektu. To bude název nadřazené složky, nebo název projektu.|
|**$(SafeInputName)**|Název souboru jako platný název třídy, bez přípony souboru. Tato vlastnost nemá naprosto stejný.|
|**$(SafeParentName)**|Název nejbližšího nadřazeného ve formátu platný název. Například formulář je nadřazený soubor .resx. Tato vlastnost nemá naprosto stejný.|
|**$(SafeRootNamespace)**|Název oboru názvů, ve kterém se průvodci projektu přidat kód. Tento název oboru názvů bude obsahovat pouze znaky, které by byl povolen v platný identifikátor C++. Tato vlastnost nemá naprosto stejný.|

## <a name="see-also"></a>Viz také:

- [Projekty sady Visual Studio – C++](../creating-and-managing-visual-cpp-projects.md)
- [Visual C++ Průvodce přenosem a upgradem](../../porting/visual-cpp-porting-and-upgrading-guide.md)
- [Přehled potenciálních problémů s upgradem](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
