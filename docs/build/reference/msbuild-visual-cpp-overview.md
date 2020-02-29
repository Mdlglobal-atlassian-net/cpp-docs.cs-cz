---
title: Interní prvky nástroje MSBuild C++ pro projekty v aplikaci Visual Studio
ms.date: 02/26/2020
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
ms.openlocfilehash: 010fa244ed77ea782fa76be959c58ff1e1b254a9
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78166716"
---
# <a name="msbuild-internals-for-c-projects"></a>Vnitřní fungování nástroje MSBuild pro projekty C++

Když nastavíte vlastnosti projektu v integrovaném vývojovém prostředí a pak projekt uložíte, sada Visual Studio zapíše nastavení projektu do souboru projektu. Soubor projektu obsahuje nastavení, která jsou jedinečná pro váš projekt. Neobsahuje však všechna nastavení potřebná k sestavení projektu. Soubor projektu obsahuje prvky `Import`, které obsahují síť dalších *podpůrných souborů.* Podpůrné soubory obsahují zbývající vlastnosti, cíle a nastavení potřebná k sestavení projektu.

Většina cílů a vlastností v souborech podpory existují výhradně k implementaci systému sestavení. Tento článek popisuje užitečné cíle a vlastnosti, které můžete zadat v příkazovém řádku MSBuild. Chcete-li zjistit více cílů a vlastností, prozkoumejte soubory v adresářích souborů podpory.

## <a name="support-file-directories"></a>Podpůrné adresáře souborů

Ve výchozím nastavení jsou primární soubory podpory sady Visual Studio umístěny v následujících adresářích. Tyto informace jsou specifické pro verzi.

### <a name="visual-studio-2019"></a>Visual Studio 2019

- % VSINSTALLDIR% MSBuild\\Microsoft\\VC\\*verze*\\VCTargets\\

  Obsahuje primární cílové soubory (. targets) a soubory vlastností (. props), které jsou používány cíli. Ve výchozím nastavení se na tento adresář odkazuje na makro $ (VCTargetsPath). Zástupný symbol *verze* odkazuje na verzi sady Visual Studio: V160 for visual Studio 2019, V150 for visual Studio 2017.

- % VSINSTALLDIR% MSBuild\\Microsoft\\VC\\*verze*\\VCTargets\\Platforms\\*Platform*\\

  Obsahuje cíle a soubory vlastností specifické pro platformu, které přepisují cíle a vlastnosti v nadřazeném adresáři. Tento adresář obsahuje také knihovnu DLL definující úlohy, které jsou používány cíli v tomto adresáři. Zástupný symbol *platformy* představuje podadresář ARM, Win32 nebo x64.

- % VSINSTALLDIR% MSBuild\\Microsoft\\VC\\*verze*\\VCTargets\\Platforms\\*platform*\\PlatformToolsets\\*Sada nástrojů*\\

  Obsahuje adresáře, které umožňují sestavení generovat C++ aplikace pomocí zadané sady *nástrojů*. Zástupný symbol *platformy* představuje podadresář ARM, Win32 nebo x64. Zástupný symbol sady *nástrojů* představuje podadresář sady nástrojů.

### <a name="visual-studio-2017"></a>Visual Studio 2017

- % VSINSTALLDIR% Common7\\IDE\\VC\\VCTargets\\

  Obsahuje primární cílové soubory (. targets) a soubory vlastností (. props), které jsou používány cíli. Ve výchozím nastavení se na tento adresář odkazuje na makro $ (VCTargetsPath).

- % VSINSTALLDIR% Common7\\IDE\\VC\\VCTargets\\Platforms\\*platform*\\

  Obsahuje cíle a soubory vlastností specifické pro platformu, které přepisují cíle a vlastnosti v nadřazeném adresáři. Tento adresář obsahuje také knihovnu DLL definující úlohy, které jsou používány cíli v tomto adresáři. Zástupný symbol *platformy* představuje podadresář ARM, Win32 nebo x64.

- % VSINSTALLDIR% Common7\\IDE\\VC\\VCTargets\\Platforms\\*platform*\\PlatformToolsets\\sady *nástrojů*\\

  Obsahuje adresáře, které umožňují sestavení generovat C++ aplikace pomocí zadané sady *nástrojů*. Zástupný symbol *platformy* představuje podadresář ARM, Win32 nebo x64. Zástupný symbol sady *nástrojů* představuje podadresář sady nástrojů.

### <a name="visual-studio-2015-and-earlier"></a>Visual Studio 2015 a starší

- *jednotka*:\\Program Files *(x86)* \\MSBuild\\Microsoft. Cpp (x86)\\*verze* 4.0\\\\

  Obsahuje primární cílové soubory (. targets) a soubory vlastností (. props), které jsou používány cíli. Ve výchozím nastavení se na tento adresář odkazuje na makro $ (VCTargetsPath).

- *jednotka*:\\Program Files *(x86)* \\MSBuild\\Microsoft. Cpp\\v 4.0\\*verze*\\Platforms\\*Platform*\\

  Obsahuje cíle a soubory vlastností specifické pro platformu, které přepisují cíle a vlastnosti v nadřazeném adresáři. Tento adresář obsahuje také knihovnu DLL definující úlohy, které jsou používány cíli v tomto adresáři. Zástupný symbol *platformy* představuje podadresář ARM, Win32 nebo x64.

- *jednotka*:\\Program Files *(x86)* \\MSBuild\\Microsoft. Cpp\\v 4.0\\*verze*\\platforms\\*Platform*\\PlatformToolsets\\*Sada nástrojů*\\

  Obsahuje adresáře, které umožňují sestavení generovat C++ aplikace pomocí zadané sady *nástrojů*. Zástupný symbol *verze* je v110 pro visual Studio 2012, V120 pro Visual Studio 2013 a V140 pro visual Studio 2015. Zástupný symbol *platformy* představuje podadresář ARM, Win32 nebo x64. Zástupný symbol sady *nástrojů* představuje podadresář sady nástrojů. Například je v140 pro sestavování aplikací pro Windows pomocí sady nástrojů sady Visual Studio 2015. Nebo v120_xp sestavit pro systém Windows XP pomocí sady nástrojů Visual Studio 2013.

- *jednotka*:\\Program Files *(x86)* \\MSBuild\\Microsoft. Cpp\\v 4.0\\Platforms\\*Platform*\\PlatformToolsets\\*Sada nástrojů*\\

  Cesty, které umožňují sestavení generovat buď aplikace sady Visual Studio 2008 nebo Visual Studio 2010, neobsahují *verzi*. V těchto verzích představuje zástupný symbol *platformy* podadresář Itanium, Win32 nebo x64. Zástupný symbol sady *nástrojů* představuje podadresář v90 nebo V100 sady nástrojů.

## <a name="support-files"></a>Soubory podpory

Adresáře souborů podpory obsahují soubory s těmito příponami:

| Linka | Popis |
| --------- | ----------- |
| . targets | Obsahuje `Target` elementy XML, které určují úkoly, které jsou spouštěny cílem. Může obsahovat také `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup`a uživatelem definované `Item` prvky, které slouží k přiřazení souborů a možností příkazového řádku k parametrům úlohy.<br /><br /> Další informace naleznete v tématu [cílový element (MSBuild)](/visualstudio/msbuild/target-element-msbuild). |
| . props | Obsahuje `Property Group` a uživatelsky definované `Property` elementy XML, které určují nastavení souboru a parametrů, které se používají během sestavení.<br /><br /> Může obsahovat také `ItemDefinitionGroup` a uživatelsky definované `Item` elementy XML, které určují další nastavení. Položky definované ve skupině definic položek připomínají vlastnosti, ale nejsou dostupné z příkazového řádku. Soubory projektu sady Visual Studio často používají položky namísto vlastností k vyjádření nastavení.<br /><br /> Další informace naleznete v tématu [element ItemCollection (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), [element ItemDefinitionGroup (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild)a [element Item (MSBuild)](/visualstudio/msbuild/item-element-msbuild). |
| .xml | Obsahuje elementy XML, které deklaruje a inicializuje prvky uživatelského rozhraní IDE. Například seznamy vlastností, stránky vlastností, textové ovládací prvky a ovládací prvky ListBox.<br /><br /> Soubory. XML přímo podporují IDE, nikoli MSBuild. Hodnoty vlastností IDE jsou však přiřazeny k vlastnostem a položkám sestavení.<br /><br /> Většina souborů. XML je v podadresáři specifických pro národní prostředí. Například soubory pro oblast English-US jsou v $ (VCTargetsPath)\\1033\\. |

## <a name="user-targets-and-properties"></a>Cíle a vlastnosti uživatele

Pro efektivní použití nástroje MSBuild pomáhá zjistit, které vlastnosti a cíle jsou užitečné a relevantní. Většina vlastností a cílů usnadňuje implementaci systému sestavení sady Visual Studio, a proto není relevantní pro uživatele. Tato část popisuje uživatelsky orientované vlastnosti a cíle, které mají za cíl vědět.

### <a name="platformtoolset-property"></a>Vlastnost PlatformToolset

Vlastnost `PlatformToolset` určuje, která sada nástrojů MSVC se v sestavení používá. Ve výchozím nastavení se používá aktuální sada nástrojů. Je-li tato vlastnost nastavena, její hodnota se zřetězí s literálovým řetězcem pro vytvoření cesty. Je to adresář, který obsahuje vlastnost a cílové soubory potřebné k sestavení projektu pro konkrétní platformu. Sada nástrojů platformy musí být nainstalována pro sestavení pomocí této verze sady nástrojů platformy.

Například nastavte vlastnost `PlatformToolset` na `v140` pro použití nástrojů a knihoven sady Visual Studio 2015 k sestavení aplikace:

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>Vlastnost PreferredToolArchitecture

Vlastnost `PreferredToolArchitecture` určuje, zda je v sestavení použit kompilátor a nástroj 64 32 nebo. Tato vlastnost nemá vliv na výstupní architekturu nebo konfiguraci platformy. Ve výchozím nastavení nástroj MSBuild používá verzi x86 kompilátoru a nástroje, není-li tato vlastnost nastavena.

Například nastavte vlastnost `PreferredToolArchitecture` na `x64` pro použití 64 kompilátoru a nástrojů k sestavení aplikace:

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>Vlastnost UseEnv

Ve výchozím nastavení jsou pro aktuální projekt popsána nastavení specifická pro danou platformu pro proměnné prostředí PATH, INCLUDE, LIB, LIBPATH, CONFIGURATION a PLATFORM. Nastavte vlastnost `UseEnv` na **hodnotu true** , chcete-li zaručit, že proměnné prostředí nebudou přepsány.

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Cíle

V souborech podpory sady Visual Studio jsou stovky cílů. Většina je ale zaměřená na systém, který uživatel může ignorovat. Většina cílů systému je uvozená podtržítkem (`_`) nebo musí mít název začínající na "PřipravitNa", "COMPUTE", "před", "po", "před" nebo "post".

Následující tabulka uvádí několik užitečných uživatelsky orientovaných cílů.

| Cíl | Popis |
| ------ | ----------- |
| BscMake | Spustí nástroj pro údržbu informací o procházení Microsoftem, BSCMAKE. exe. |
| Sestavení | Vytvoří projekt.<br /><br /> Tento cíl je pro projekt výchozí. |
| ClCompile | Spustí nástroj kompilátoru MSVC, CL. exe. |
| Vyčistit | Odstraní dočasné a mezilehlé soubory sestavení. |
| Knihovna | Spustí nástroj Správce bitových knihoven Microsoft 32, LIB. exe. |
| Odkaz | Spustí nástroj linkeru MSVC, Link. exe. |
| ManifestResourceCompile | Extrahuje seznam prostředků z manifestu a potom spustí nástroj Microsoft Windows Resource Compiler, RC. exe. |
| MIDL | Spustí nástroj kompilátoru MIDL (Microsoft Interface Definition Language), MIDL. exe. |
| Sestavit znovu | Vyčistí a poté sestaví projekt. |
| ResourceCompile | Spustí nástroj Microsoft Windows Resource Compiler, RC. exe. |
| XdcMake | Spustí nástroj dokumentace XML, xdcmake. exe. |
| XSD | Spustí nástroj definice schématu XML (XSD. exe). *Viz poznámka níže.* |

> [!NOTE]
> V aplikaci Visual Studio 2017 nebo novější C++ je podpora projektu pro soubory **XSD** zastaralá. Můžete přesto použít soubor **Microsoft. VisualC. CppCodeProvider** přidáním **CppCodeProvider. dll** do globální mezipaměti sestavení (GAC).

## <a name="see-also"></a>Viz také

\ [referenčních informací o úloze nástroje MSBuild](/visualstudio/msbuild/msbuild-task-reference)
\ [úlohy BSCMAKE](/visualstudio/msbuild/bscmake-task)
\ [úlohy CL](/visualstudio/msbuild/cl-task)
\ [úlohy CPPClean –](/visualstudio/msbuild/cppclean-task)
\ [úlohy lib](/visualstudio/msbuild/lib-task)
[Propojit\ úkolu](/visualstudio/msbuild/link-task)
\ [úlohy MIDL](/visualstudio/msbuild/midl-task)
[MT\ úlohy](/visualstudio/msbuild/mt-task)
\ [úkolu RC](/visualstudio/msbuild/rc-task)
\ [úlohy setenv –](/visualstudio/msbuild/setenv-task)
\ [úlohy VCMessage –](/visualstudio/msbuild/vcmessage-task)
[XDCMake – úloha](/visualstudio/msbuild/xdcmake-task)
