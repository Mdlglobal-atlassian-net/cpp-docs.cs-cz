---
title: "Běžné makra pro příkazy a vlastnosti sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs: C++
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
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f96e403516d6f85804fa798d7a0c28575482ff43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="common-macros-for-build-commands-and-properties"></a>Běžné makra pro příkazy a vlastnosti sestavení
V závislosti na možnosti instalace sady Visual Studio můžete zpřístupnit stovky makra pro vás. Tyto odpovídat vlastnosti nástroje MSBuild, které jsou nastavené ve výchozím nastavení, nebo soubory props nebo .targets nebo nastavení projektu. Tyto makra lze použít kdekoli v projektu na **stránky vlastností** dialogové, kde jsou přijímány řetězce. Tyto makra se nerozlišují malá a velká písmena.  
  
 Pokud chcete zobrazit aktuálně k dispozici makra ve sloupci vpravo od názvu vlastnosti, klikněte na šipku rozevíracího seznamu. Pokud **upravit** je k dispozici, klikněte na něj a potom v dialogovém okně upravit, klikněte na **makra**. Další informace najdete v tématu **Specifying User-Defined hodnoty** části [stránky vlastností](../ide/property-pages-visual-cpp.md).  
  
 Makra, které jsou označeny "Zastaralé" se již nepoužívají nebo byly nahrazeny ekvivalentní [makro metadata položky](/visualstudio/msbuild/itemmetadata-element-msbuild) (**%(***název***)**) . Makra, které jsou označeny "zastaralé; migrovat"je taky zastaralá. A kromě toho, pokud je projekt, který obsahuje makro migrovali ze sady Visual Studio 2008, Visual Studio převede makro na ekvivalentní aktuální makro.  
  
 Následující tabulka popisuje podmnožinu běžně používané k dispozici makra. Tento seznam není vyčerpávající. Podrobnosti na způsob vytváření a použít jako makra v VCXPROJ soubory props, .targets a definice vlastnosti nástroje MSBuild najdete v tématu [vlastnosti nástroje MSBuild](/visualstudio/msbuild/msbuild-properties).  
  
|– Makro|Popis|  
|-----------|-----------------|  
|**$(RemoteMachine)**|Nastavte na hodnotu **vzdáleného počítače** vlastnost na stránce vlastností ladění. V tématu [Změna nastavení projektu pro konfiguraci ladění C/C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) Další informace.|  
|**$(Configuration)**|Název aktuální konfigurací projektu, například "Debug".|  
|**$(Platform)**|Název aktuální platformy projektu, například "Win32".|  
|**$(Parentname) –**|(Nepoužívané). Název položky obsahující tuto položku projektu. To bude název nadřazené složky nebo název projektu.|  
|**$(RootNameSpace)**|Obor názvů, pokud existuje, obsahující aplikaci.|  
|**$(IntDir)**|Cesta k adresáři zadaná pro zprostředkující soubory. Pokud to je relativní cesta, zprostředkující soubory přejděte na tuto cestu k adresáři projektu. Tato cesta by měla mít koncové lomítko. To přeloží na hodnotu **zprostředkující Directory** vlastnost. Nepoužívejte **$(outdir) –** k definování této vlastnosti.|  
|**$(Outdir) –**|Cesta k adresáři výstupního souboru. Pokud to je relativní cesta, výstupní soubory přejděte na tuto cestu k adresáři projektu. Tato cesta by měla mít koncové lomítko. To se přeloží na hodnotu **výstupního adresáře** vlastnost. Nepoužívejte **$(IntDir)** k definování této vlastnosti.|  
|**$(Devenvdir) –**|Instalační adresář sady Visual Studio (definovaný jako jednotka + cesta); zahrnuje koncové zpětné lomítko,\\'.|  
|**$(Inputdir) –**|(Nepoužívané; migrovat.) Adresář souboru vstupního souboru (definovaný jako jednotka + cesta); zahrnuje koncové zpětné lomítko,\\'. Pokud projekt se vstup, pak je ekvivalentní této makro **$(projectdir) –**.|  
|**$(InputPath)**|(Nepoužívané; migrovat.) Absolutní cesta název souboru vstupního souboru (definován jako jednotka + cesta + základní název + přípona souboru). Pokud projekt se vstup, pak je ekvivalentní této makro **$(ProjectPath)**.|  
|**$(InputName)**|(Nepoužívané; migrovat.) Základní název souboru vstupního souboru. Pokud projekt se vstup, pak je ekvivalentní této makro **$(ProjectName)**.|  
|**$(InputFileName)**|(Nepoužívané; migrovat.) Název souboru vstupního souboru (definován jako základní název + přípona souboru). Pokud projekt se vstup, pak je ekvivalentní této makro **$(ProjectFileName)**.|  
|**$(Inputext) –**|(Nepoužívané; migrovat.) Přípona souboru vstupního souboru. Obsahuje,., před příponu souboru. Pokud projekt se vstup, pak je ekvivalentní této makro **$(ProjectExt)**.|  
|**$(Projectdir) –**|Do adresáře projektu (definovaný jako jednotka + cesta); zahrnuje koncové zpětné lomítko,\\'.|  
|**$(ProjectPath)**|Absolutní cesta název projektu (definován jako jednotka + cesta + základní název + přípona souboru).|  
|**$(ProjectName)**|Základní název projektu.|  
|**$(ProjectFileName)**|Název souboru projektu (definován jako základní název + přípona souboru).|  
|**$(ProjectExt)**|Přípona souboru projektu. Obsahuje,., před příponu souboru.|  
|**$(Solutiondir) –**|Adresář řešení (definovaný jako jednotka + cesta); zahrnuje koncové zpětné lomítko,\\'. Definována pouze při sestavování řešení v prostředí IDE.|  
|**$(Solutionpath) –**|Absolutní cesta název řešení (definován jako jednotka + cesta + základní název + přípona souboru). Definována pouze při sestavování řešení v prostředí IDE.|  
|**$(SolutionName)**|Základní název řešení. Definována pouze při sestavování řešení v prostředí IDE.|  
|**$(Solutionfilename) –**|Název souboru řešení (definován jako základní název + přípona souboru). Definována pouze při sestavování řešení v prostředí IDE.|  
|**$(Solutionext) –**|Přípona souboru řešení. Obsahuje,., před příponu souboru. Definována pouze při sestavování řešení v prostředí IDE.|  
|**$(TargetDir)**|Adresář primárního výstupního souboru pro sestavení (definovaný jako jednotka + cesta); zahrnuje koncové zpětné lomítko,\\'.|  
|**$(TargetPath)**|Absolutní cesta název primárního výstupního souboru pro sestavení (definován jako jednotka + cesta + základní název + přípona souboru).|  
|**$(TargetName)**|Základní název primárního výstupního souboru pro sestavení.|  
|**$(Targetfilename) –**|Název souboru primárního výstupního souboru pro sestavení (definován jako základní název + přípona souboru).|  
|**$(Targetext) –**|Přípona souboru primárního výstupního souboru pro sestavení. Obsahuje,., před příponu souboru.|  
|**$(VSInstallDir)**|Adresář, do které jste nainstalovali Visual Studio.<br /><br /> Tato vlastnost obsahuje verzi cílové sady Visual Studio, který se může lišit, hostitelské sady Visual Studio. Například při sestavení s `$(PlatformToolset) = v110`, **$(VSInstallDir)** obsahuje cestu k instalaci sady Visual Studio 2012.|  
|**$(VCInstallDir)**|Adresář, do které jste nainstalovali Visual C++.<br /><br /> Tato vlastnost obsahuje verzi cílové aplikace Visual C++, který se může lišit, hostitelské sady Visual Studio. Například při sestavení s `$(PlatformToolset) = v140`, **$(VCInstallDir)** obsahuje cestu k instalačním Visual C++ 2015.|  
|**$(FrameworkDir)**|Adresář, do kterého byla nainstalována rozhraní .NET Framework.|  
|**$(FrameworkVersion)**|Verze rozhraní .NET Framework, sada Visual Studio. V kombinaci s **$(FrameworkDir)**, úplná cesta k verzi rozhraní .NET Framework použití Visual Studio.|  
|**$(Frameworksdkdir) –**|Adresář, do které jste nainstalovali rozhraní .NET Framework. Rozhraní .NET Framework je může nainstalovat jako součást sady Visual Studio, nebo samostatně.|  
|**$(Webdeploypath) –**|Relativní cestu z kořene nasazení webu k kde výstup projektu patří. Vrací stejnou hodnotu jako <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>.|  
|**$(Webdeployroot) –**|Absolutní cestu k umístění  **\<localhost >**. Například c:\inetpub\wwwroot.|  
|**$(SafeParentName)**|(Nepoužívané). Název nadřazeného okamžitou ve formátu platný název. Například formulář je nadřazený tohoto souboru RESX.|  
|**$(SafeInputName)**|(Nepoužívané). Název souboru jako platný název třídy, bez přípony souboru.|  
|**$(Saferootnamespace) –**|(Nepoužívané). Název oboru názvů, ve kterém bude průvodců projektu přidejte kód. Tento název oboru názvů bude obsahovat pouze znaky, které jsou přípustné v platný identifikátor C++.|  
|**$(Fxcopdir) –**|Cesta k souboru fxcop.cmd. Soubor fxcop.cmd není nainstalován ve všech edicích Visual C++.|  
  
## <a name="see-also"></a>Viz také  
 [Sestavení projektů C++ v sadě Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)