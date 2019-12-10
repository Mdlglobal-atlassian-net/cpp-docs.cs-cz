---
title: Společná makra pro příkazy a vlastnosti MSBuild
ms.date: 08/02/2019
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
ms.openlocfilehash: e2c7fe6f2ea63f2cbd259e4114843fcfc28fcd84
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988325"
---
# <a name="common-macros-for-msbuild-commands-and-properties"></a>Společná makra pro příkazy a vlastnosti MSBuild

V závislosti na možnostech instalace může Visual Studio zpřístupnit stovky maker v projektu sady Visual Studio (na základě MSBuild). Odpovídají vlastnostem nástroje MSBuild, které jsou nastaveny ve výchozím nastavení, nebo v souborech. props nebo. Targets nebo v nastavení projektu. Tato makra můžete použít kdekoli v dialogovém okně **stránky vlastností** projektu, kde jsou přijímány řetězce. Tato makra nerozlišují velká a malá písmena.

## <a name="view-the-current-properties-and-macros"></a>Zobrazit aktuální vlastnosti a makra

Chcete-li zobrazit všechna aktuálně dostupná makra, v dialogovém okně **stránky vlastností** v části **adresáře VC + +** vyberte šipku rozevíracího seznamu na konci řádku vlastnosti. Klikněte na **Upravit** a potom v dialogovém okně Upravit zvolte tlačítko **makra** . Aktuální sada vlastností a maker zobrazených v sadě Visual Studio je uvedena spolu s aktuální hodnotou pro každý z nich. Další informace naleznete v části **zadání uživatelem definovaných hodnot** v [ C++ odkazu na stránku vlastností projektu](property-pages-visual-cpp.md).

![Tlačítko makra VC + +](../media/vcppdir_libdir_macros.png "Nabídka makra")

## <a name="list-of-common-macros"></a>Seznam běžných maker

Tato tabulka popisuje běžně použitou podmnožinu dostupných maker. Zde je uvedeno mnoho dalších. Přejděte do dialogového okna **makra** a zobrazte všechny vlastnosti a jejich aktuální hodnoty v projektu. Podrobnosti o tom, jak se vytvářejí definice vlastností MSBuild a používají se jako makra v souborech. props,. targets a. vcxproj, najdete v tématu [vlastnosti MSBuild](/visualstudio/msbuild/msbuild-properties).

|– Makro|Popis|
|-----------|-----------------|
|**$ (Konfigurace)**|Název aktuální konfigurace projektu, například "ladit".|
|**$ (DevEnvDir)**|Instalační adresář aplikace Visual Studio (definovaný jako jednotka + cesta); obsahuje koncové zpětné lomítko '\\'.|
|**$(FrameworkDir)**|Adresář, do kterého byl nainstalován .NET Framework.|
|**$(FrameworkSDKDir)**|Adresář, do kterého jste nainstalovali .NET Framework. .NET Framework mohl být nainstalován jako součást sady Visual Studio nebo samostatně.|
|**$ (FrameworkVersion)**|Verze .NET Framework používaná v aplikaci Visual Studio. V kombinaci s **$ (FrameworkDir)** je úplná cesta k verzi .NET Framework, kterou používá Visual Studio.|
|**$(FxCopDir)**|Cesta k souboru FxCop. cmd. Soubor FxCop. cmd není nainstalován se všemi edicemi sady Visual Studio.|
|**$(IntDir)**|Cesta k adresáři určenému pro mezilehlé soubory. Pokud se jedná o relativní cestu, mezilehlé soubory přejdou do této cesty připojené k adresáři projektu. Tato cesta by měla obsahovat koncové lomítko. Přeloží se na hodnotu vlastnosti **zprostředkujícího adresáře** . Pro definování této vlastnosti Nepoužívejte **$ (OutDir)** .|
|**$(OutDir)**|Cesta k adresáři výstupního souboru Pokud se jedná o relativní cestu, výstupní soubory přejdou do této cesty připojené k adresáři projektu. Tato cesta by měla obsahovat koncové lomítko. Přeloží se na hodnotu vlastnosti **výstupní adresář** . Pro definování této vlastnosti Nepoužívejte **$ (IntDir)** .|
|**$(Platform)**|Název aktuální projektové platformy, například "Win32".|
|**$(PlatformShortName)**|Krátký název aktuální architektury, například "x86" nebo "x64".|
|**$(ProjectDir)**|Adresář projektu (definovaný jako jednotka + cesta); obsahuje koncové zpětné lomítko '\\'.|
|**$(ProjectExt)**|Přípona souboru projektu. Obsahuje znak "." před příponou souboru.|
|**$(ProjectFileName)**|Název souboru projektu (definovaný jako základní název + Přípona souboru).|
|**$(ProjectName)**|Základní název projektu|
|**$(ProjectPath)**|Absolutní cesta k názvu projektu (definovaná jako jednotka + cesta + základní název + Přípona souboru).|
|**$ (PublishDir)**|Umístění výstupu pro cíl publikování; obsahuje koncové zpětné lomítko '\\'. Výchozí hodnota je **aplikace $ (OutDir). publish\\** složka.|
|**$ (RemoteMachine)**|Nastavte na hodnotu vlastnosti **vzdálený počítač** na stránce vlastností ladění. Další informace najdete v tématu [Změna nastavení projektuC++ pro konfiguraci C/Debug](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) .|
|**$ (RootNameSpace)**|Obor názvů, pokud existuje, obsahující aplikaci.|
|**$ (SolutionDir)**|Adresář řešení (definovaný jako jednotka + cesta); obsahuje koncové zpětné lomítko '\\'. Definováno pouze při sestavování řešení v integrovaném vývojovém prostředí.|
|**$ (SolutionExt)**|Přípona souboru řešení. Obsahuje znak "." před příponou souboru. Definováno pouze při sestavování řešení v integrovaném vývojovém prostředí.|
|**$(SolutionFileName)**|Název souboru řešení (definovaného jako základní název + Přípona souboru). Definováno pouze při sestavování řešení v integrovaném vývojovém prostředí.|
|**$ (Řešení)**|Základní název řešení Definováno pouze při sestavování řešení v integrovaném vývojovém prostředí.|
|**$ (SolutionPath)**|Absolutní cesta k názvu řešení (definovaného jako jednotka + cesta + základní název + Přípona souboru). Definováno pouze při sestavování řešení v integrovaném vývojovém prostředí.|
|**$(TargetDir)**|Adresář primárního výstupního souboru pro sestavení (definovaný jako jednotka + cesta); obsahuje koncové zpětné lomítko '\\'.|
|**$(TargetExt)**|Přípona souboru primárního výstupního souboru pro sestavení. Obsahuje znak "." před příponou souboru.|
|**$(TargetFileName)**|Název souboru primárního výstupního souboru pro sestavení (definované jako základní název + Přípona souboru).|
|**$(TargetName)**|Základní název primárního výstupního souboru pro sestavení.|
|**$(TargetPath)**|Absolutní cesta k primárnímu výstupnímu souboru pro sestavení (definované jako jednotka + cesta + základní název + Přípona souboru).|
|**$ (VCInstallDir)**|Adresář, který obsahuje C++ obsah vaší instalace sady Visual Studio. Tato vlastnost obsahuje verzi cílené sady nástrojů Microsoft C++ (MSVC), která se může lišit od hostitele sady Visual Studio. Například při sestavování pomocí `$(PlatformToolset) = v140`obsahuje **$ (VCInstallDir)** cestu k instalaci sady Visual Studio 2015.|
|**$ (VSInstallDir)**|Adresář, do kterého jste nainstalovali aplikaci Visual Studio. Tato vlastnost obsahuje verzi cílené sady nástrojů sady Visual Studio, která se může lišit od hostitele sady Visual Studio. Například při sestavování pomocí `$(PlatformToolset) = v110`obsahuje **$ (VSINSTALLDIR)** cestu k instalaci sady Visual Studio 2012.|
|**$(WebDeployPath)**|Relativní cesta z kořenu nasazení webu, do které patří výstup projektu.|
|**$ (WebDeployRoot)**|Absolutní cesta k umístění **\<localhost >** . Například c:\Inetpub\Wwwroot.|

## <a name="obsolete-macros"></a>Zastaralá makra

Sestavovací systém pro C++ byl významně změněn mezi visual Studio 2008 a visual Studio 2010. Mnoho maker použitých v dřívějších typech projektů bylo změněno na nové. Tato makra se již nepoužívají nebo byly nahrazeny jednou nebo více ekvivalentními vlastnostmi nebo hodnotami makra ( **%(** _Name_ **)** [položek](/visualstudio/msbuild/itemmetadata-element-msbuild) . Makra, která jsou označená jako migrované, se dají aktualizovat nástrojem Project Migration Tool. Pokud je projekt obsahující makro migrován ze sady Visual Studio 2008 nebo starší do sady Visual Studio 2010, aplikace Visual Studio převede makro na ekvivalentní aktuální makro. Novější verze sady Visual Studio nemůžou převést projekty ze sady Visual Studio 2008 a starší na nový typ projektu. Tyto projekty je nutné převést ve dvou krocích. Nejprve je převeďte do sady Visual Studio 2010 a pak výsledek převeďte na novější verzi sady Visual Studio. Další informace najdete v tématu [Přehled potenciálních problémů s upgradem](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

|– Makro|Popis|
|-----------|-----------------|
|**$ (InputDir)**|(Migrováno) Adresář vstupního souboru (definovaný jako jednotka + cesta); obsahuje koncové zpětné lomítko '\\'. Pokud je projekt vstupem, pak je toto makro ekvivalentní **$ (ProjectDir)** .|
|**$ (InputExt)**|(Migrováno) Přípona souboru vstupního souboru. Obsahuje znak "." před příponou souboru. Pokud je projekt vstupem, pak je toto makro ekvivalentní **$ (ProjectExt)** . U zdrojových souborů se jedná o **% (rozšíření)** .|
|**$ (InputFileName)**|(Migrováno) Název souboru vstupního souboru (definovaného jako základní název + Přípona souboru). Pokud je projekt vstupem, pak je toto makro ekvivalentní **$ (ProjectFileName)** . U zdrojových souborů se jedná o **% (identitu)** .|
|**$ (Vstup)**|(Migrováno) Základní název vstupního souboru. Pokud je projekt vstupem, pak je toto makro ekvivalentní **$ (ProjectName)** . U zdrojových souborů se jedná o **% (název souboru)** .|
|**$ (InputPath)**|(Migrováno) Absolutní cesta ke vstupnímu souboru (definovaná jako jednotka + cesta + základní název + Přípona souboru). Pokud je projekt vstupem, pak je toto makro ekvivalentní **$ (ProjectPath)** . Pro zdrojové soubory je to **% (FullPath)** .|
|**$(ParentName)**|Název položky obsahující tuto položku projektu Toto bude název nadřazené složky nebo název projektu.|
|**$ (SafeInputName)**|Název souboru jako platný název třídy, mínus Přípona souboru. Tato vlastnost nemá přesný ekvivalent.|
|**$(SafeParentName)**|Název bezprostředního nadřazeného objektu ve formátu platného názvu. Například formulář je nadřazený souboru. resx. Tato vlastnost nemá přesný ekvivalent.|
|**$(SafeRootNamespace)**|Název oboru názvů, do kterého budou Průvodci projektu přidány kód. Tento název oboru názvů bude obsahovat pouze znaky, které by mohly být povoleny C++ v platném identifikátoru. Tato vlastnost nemá přesný ekvivalent.|

## <a name="see-also"></a>Viz také:

[Projekty sady Visual Studio C++ –](../creating-and-managing-visual-cpp-projects.md)\
[Průvodce C++ portací a upgradem vizuálů](../../porting/visual-cpp-porting-and-upgrading-guide.md)\
[Přehled potenciálních problémů s upgradem](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
