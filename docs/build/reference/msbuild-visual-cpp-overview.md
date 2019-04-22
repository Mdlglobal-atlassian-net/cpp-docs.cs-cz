---
title: Projekty MSBuild interní informace pro jazyk C++ v sadě Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
ms.openlocfilehash: 6c8e891f6bf6ed6b3bb3d1c84dbc13b64ab7b868
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59021901"
---
# <a name="msbuild-internals-for-c-projects"></a>Interní informace o MSBuild pro projekty v jazyce C++

Při nastavení vlastností projektu v integrovaném vývojovém prostředí a uložení projektu sady Visual Studio zapíše nastavení projektu do souboru projektu. Soubor projektu obsahuje nastavení, které jsou jedinečné pro váš projekt, ale neobsahuje všechna nastavení, které jsou nezbytné k sestavení projektu. Soubor projektu obsahuje `Import` elementy, které obsahují síť dalších *podpůrných souborů.* Soubory podpory obsahují zbývající vlastnosti, cíle a nastavení, které jsou nutné pro sestavení projektu.

Většina cílů a vlastnosti v podpůrném souboru existuje výhradně pro implementaci systému sestavení. Následující část popisuje některé užitečné cíle a vlastnosti, které můžete zadat na příkazovém řádku nástroje MSBuild. Když Pokud chcete zjistit další cíle a vlastnosti, prozkoumejte soubory v adresářích souboru podpory.

## <a name="support-file-directories"></a>Podpora adresářů se soubory

Standardně primární podpůrné soubory Visual Studio jsou umístěny v následujících adresářích. Adresáře v rámci sady Microsoft Visual Studio používají Visual Studio 2017 a novějších verzích, zatímco adresáře v rámci nástroje MSBuild používá Visual Studio 2015 a starší verze.

|Adresář|Popis|
|---------------|-----------------|
|*drive*:\Program Files *(x86)* \Microsoft Visual Studio\\*year*\\*edition*\Common7\IDE\VC\VCTargets\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp (x86)\v4.0\\*version*\ |Obsahuje primární cílové soubory (TARGETS) a soubory vlastností (props), které jsou používány těmito cíly. Ve výchozím nastavení makro $(VCTargetsPath) odkazuje na tento adresář.|
|*drive*:\Program Files *(x86)* \Microsoft Visual Studio\\*year*\\*edition*\Common7\IDE\VC\VCTargets\Platforms\\*platform*\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*platform*\ |Obsahuje soubory cíle a vlastnosti specifické pro platformu, které přepíší cíle a vlastnosti svého nadřazeného adresáře. Tento adresář obsahuje taky knihovnu DLL, která definuje úlohy, které jsou používány cíli v tomto adresáři.<br /><br /> *Platformy* zastupuje ARM, Win32 nebo x64 podadresáře.|
|*drive*:\Program Files *(x86)* \Microsoft Visual Studio\\*year*\\*edition*\Common7\IDE\VC\VCTargets\Platforms\\*platform*\PlatformToolsets\\*toolset*\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*platform*\PlatformToolsets\\*toolset*\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*platform*\PlatformToolsets\\*toolset*\ |Obsahuje adresáře, které umožňují sestavení generovat aplikace C++ s použitím zadaného *nástrojů*.<br /><br /> *Rok* a *edition* zástupné symboly používají Visual Studio 2017 a novější verze. *Verze* zástupný symbol je V110 pro sadu Visual Studio 2012, V120 pro Visual Studio 2013 nebo V140 pro Visual Studio 2015. *Platformy* zastupuje ARM, Win32 nebo x64 podadresáře. *Nástrojů* zástupný text představuje podadresář sady nástrojů, například v140 pro vytváření aplikací pro Windows pomocí nástrojů Visual Studio 2015, v120_xp k vývoji pro Windows XP pomocí sady nástrojů Visual Studio 2013 nebo v110_wp80 do vytváření aplikací Windows Phone 8.0 pomocí sady nástrojů Visual Studio 2012.<br /><br />Neobsahuje cestu, která obsahuje adresáře, které umožňují sestavení generovat aplikace Visual Studio 2008 nebo Visual Studio 2010 *verze*a *platformy* zástupného symbolu představuje Itanium, Win32 nebo x64 podadresáře. *Nástrojů* zástupný text představuje podadresář sady nástrojů v90 nebo v100.|

## <a name="support-files"></a>Soubory podpory

Adresáře souboru podpory obsahují soubory s těmito příponami:

|Linka|Popis|
|---------------|-----------------|
|.TARGETS|Obsahuje `Target` elementů XML, které určují úkoly, které jsou spouštěny cílem. Může také obsahovat `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup`a uživatelem definovanými `Item` prvků, které slouží k přiřazení souborů a možnosti příkazového řádku pro parametry úlohy.<br /><br /> Další informace najdete v tématu [Target – Element (MSBuild)](/visualstudio/msbuild/target-element-msbuild).|
|.props|Obsahuje `Property Group` a uživatelem definovanými `Property` elementů XML, které určují soubor a nastavení parametru používané během sestavení.<br /><br /> Může také obsahovat `ItemDefinitionGroup` a uživatelem definovanými `Item` elementů XML, které určují další nastavení. Položky definované ve skupině definice se podobají vlastnosti, ale není přístupný z příkazového řádku. Soubory projektu Visual Studio často používají položky namísto vlastností k vyjádření nastavení.<br /><br /> Další informace najdete v tématu [itemgroup – Element (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), 
[ItemDefinitionGroup – Element (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild), a [položky – Element (MSBuild)](/visualstudio/msbuild/item-element-msbuild).|
|.xml|Obsahuje elementy XML, které deklarujete a inicializujete prvky uživatelského rozhraní integrovaného vývojového prostředí jako je například seznamy vlastností a stránky vlastností a textové pole a seznamu ovládací prvky.<br /><br /> Soubory XML přímo podporují IDE, nikoli MSBuild. Však hodnoty vlastnosti IDE jsou přiřazeny k vlastnostem sestavení a položkám.<br /><br /> Většina souborů XML jsou v podadresáři národního prostředí. Například soubory pro oblast angličtina-USA jsou v $(VCTargetsPath) \1033\\.|

## <a name="user-targets-and-properties"></a>Uživatelské cíle a vlastnosti

K co nejefektivnějšímu využití MSBuild na příkazovém řádku, pomáhá zjistit, jaké vlastnosti a cíle jsou užitečné a důležité. Většina vlastností a cílů pomáhá implementovat systém sestavení Visual Studio a v důsledku toho nejsou relevantní pro daného uživatele. Tato část popisuje některé vhodné uživatelem orientované vlastnosti a cíle.

### <a name="platformtoolset-property"></a>Vlastnost PlatformToolset

`PlatformToolset` Určuje vlastnost, která sada nástrojů MSVC se používá v sestavení. Ve výchozím nastavení se používá aktuální sady nástrojů. Pokud je tato vlastnost nastavena, hodnota vlastnosti je zřetězená s literálovými řetězci k vytvoření cesty k adresáři, který obsahuje vlastnost a cílové soubory, které jsou nutné k vytvoření projektu pro konkrétní platformu. Pro sestavení pomocí této verze sady nástrojů platformy musí být nainstalovaná sada nástrojů platformy.

Například nastavit `PlatformToolset` vlastnost `v140` svou aplikaci pomocí knihoven a nástrojů Visual Studio 2015:

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>Vlastnost PreferredToolArchitecture

`PreferredToolArchitecture` Vlastnost určuje, zda v sestavení použity 32bitové nebo 64bitové kompilátoru a nástrojů. Tato vlastnost nemá vliv výstupní architekturu nebo konfiguraci platformy. Ve výchozím nastavení, nástroj MSBuild používá x86 verzi kompilátoru a nástrojů, je-li tato vlastnost není nastavená.

Například nastavit `PreferredToolArchitecture` vlastnost `x64` použití 64bitového kompilátoru a nástrojů k sestavení aplikace:

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>Vlastnost UseEnv

Ve výchozím nastavení specifické pro platformu pro aktuální projekt potlačit proměnné prostředí PATH, INCLUDE, LIB, LIBPATH, konfigurace a PLATFORMA. Nastavte `UseEnv` vlastnost **true** zaručí, že proměnné prostředí nejsou přepsána.

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Cíle

Existují stovky cílů v podpůrných souborů sady Visual Studio. Nejvíce je však cílů orientovaných na systém, které uživatel může ignorovat. Většině cílů systémů předchází podtržítko (_), nebo mít název, který začíná "Připravitna", "Vypočítat", "Před", "After", "Pre" nebo "Post".

V následující tabulce jsou uvedeny některé užitečné cíle zaměřených na uživatele.

|Target|Popis|
|------------|-----------------|
|BscMake|Spustí nástroj vyhledejte informace o údržbě nástroje Microsoft bscmake.exe.|
|Sestavení|Vytvoří projekt.<br /><br /> Toto je výchozí cíl pro projekt.|
|ClCompile|Spustí nástroj kompilátoru MSVC cl.exe.|
|Vyčistit|Odstraní dočasné a průběžné zprostředkující soubory sestavení.|
|lib|Spustí nástroj Microsoft 32bitový Správce knihovny lib.exe.|
|Odkaz|Spustí nástroj linker MSVC link.exe.|
|ManifestResourceCompile|Extrahujte seznam prostředků z manifestu a poté spustí nástroj Microsoft Windows Resource Compiler, rc.exe.|
|Midl|Spustí nástroj kompilátoru Microsoft Interface Definition Language (MIDL), midl.exe.|
|Opětovné sestavení|Čistí a poté sestaví váš projekt.|
|ResourceCompile|Spustí nástroj Microsoft Windows Resource Compiler, rc.exe.|
|XdcMake|Spustí nástroj dokumentace XML, xdcmake.exe.|
|Xsd|Spustí nástroj definice schématu XML, xsd.exe. *Viz poznámka níže.*|

> [!NOTE]
> V sadě Visual Studio 2017, projekt C++ podpora **xsd** zastaralé soubory. Můžete dál používat **Microsoft.VisualC.CppCodeProvider** přidáním **CppCodeProvider.dll** ručně do mezipaměti GAC.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace úlohy nástroje MSBuild](/visualstudio/msbuild/msbuild-task-reference)<br/>
[BscMake – úloha](/visualstudio/msbuild/bscmake-task)<br/>
[CL – úloha](/visualstudio/msbuild/cl-task)<br/>
[CPPClean – úloha](/visualstudio/msbuild/cppclean-task)<br/>
[LIB – úloha](/visualstudio/msbuild/lib-task)<br/>
[Odkaz – úloha](/visualstudio/msbuild/link-task)<br/>
[MIDL – úloha](/visualstudio/msbuild/midl-task)<br/>
[MT – úloha](/visualstudio/msbuild/mt-task)<br/>
[RC – úloha](/visualstudio/msbuild/rc-task)<br/>
[SetEnv – úloha](/visualstudio/msbuild/setenv-task)<br/>
[VCMessage – úloha](/visualstudio/msbuild/vcmessage-task)<br/>
[XDCMake – úloha](/visualstudio/msbuild/xdcmake-task)<br/>
