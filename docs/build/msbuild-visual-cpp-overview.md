---
title: Přehled nástroje MSBuild (Visual C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad6feef707d991d07fa4e086bc8535f32b991825
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716855"
---
# <a name="msbuild-visual-c-overview"></a>Přehled nástroje MSBuild (Visual C++)

Nástroj MSBuild je standardní systém pro projekty Visual C++ sestavení. Při vytváření projektu v sadě Visual Studio integrované vývojové prostředí (IDE), využívá nástroj msbuild.exe, soubor projektu založený na formátu XML a volitelné soubory nastavení. I když můžete použít msbuild.exe a soubor projektu na příkazovém řádku, rozhraní IDE poskytuje uživatelské rozhraní, abyste mohli snadněji konfigurovat nastavení a sestavit projekt. Tento přehled popisuje, jak Visual C++ používá systém MSBuild.

## <a name="prerequisites"></a>Požadavky

Přečtěte si následující dokumenty o MSBuild.

- [Nástroj MSBuild](/visualstudio/msbuild/msbuild) koncepty přehled nástroje MSBuild.

- [Referenční dokumentace nástroje MSBuild](/visualstudio/msbuild/msbuild-reference) referenční informace o systému MSBuild.

- [Referenční dokumentace schématu souboru projektu](/visualstudio/msbuild/msbuild-project-file-schema-reference) uvádí prvky schématu MSBuild XML, spolu s jejich atributy a nadřazené a podřízené prvky. Obzvláště zvažte [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [cílové](/visualstudio/msbuild/target-element-msbuild), a [úloh](/visualstudio/msbuild/task-element-msbuild) elementy.

- [Odkaz na příkazový řádek](/visualstudio/msbuild/msbuild-command-line-reference) popisuje argumenty příkazového řádku a možnosti, které lze použít s msbuild.exe.

- [Úloha odkazu](/visualstudio/msbuild/msbuild-task-reference) úlohy nástroje MSBuild popisuje. Obzvláště zvažte tyto prvky, které jsou specifické pro Visual C++: [BscMake – úloha](/visualstudio/msbuild/bscmake-task), [cl – úloha](/visualstudio/msbuild/cl-task), [cppclean – úloha](/visualstudio/msbuild/cppclean-task), [lib – úloha](/visualstudio/msbuild/lib-task), [Propojení úkolů](/visualstudio/msbuild/link-task), [MIDL – úloha](/visualstudio/msbuild/midl-task), [MT – úloha](/visualstudio/msbuild/mt-task), [RC – úloha](/visualstudio/msbuild/rc-task), [SETENV – úloha](/visualstudio/msbuild/setenv-task), [ Vcmessage – úloha](/visualstudio/msbuild/vcmessage-task), [xdcmake – úloha](/visualstudio/msbuild/xdcmake-task), [XSD – úloha](/visualstudio/msbuild/xsd-task).

## <a name="msbuild-on-the-command-line"></a>MSBuild na příkazovém řádku

Následující příkaz z [MSBuild Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference) znázorňuje, že nástroj msbuild.exe použije implicitní nebo explicitní *project_file* argument (soubor .vcxproj pro projekty Visual C++) a nula nebo více příkazového řádku *možnosti* argumenty.

> **MSBuild.exe** [ *project_file* ] [ *možnosti* ]

Použití **/target** (nebo **/t**) a **/property** (nebo **/p**) možnosti příkazového řádku k přepsání specifické vlastnosti a cíle, které jsou zadaná v souboru projektu.

Základní funkcí souboru projektu je zadání *cílové*, což je určitá operace použitá na váš projekt a vstupy a výstupy, které jsou nutné k provedení této operace. Soubor projektu může určit jeden nebo více cílů, které mohou zahrnovat výchozí cíl.

Každý cíl se skládá ze sekvence jedné nebo více *úlohy*. Každá úloha je reprezentována třídou rozhraní .NET Framework, která obsahuje jeden spustitelný příkaz. Například [cl – úloha](/visualstudio/msbuild/cl-task) obsahuje [cl.exe](../build/reference/compiling-a-c-cpp-program.md) příkaz.

A *parametr úlohy* je vlastnost úlohy třídy a obvykle představuje možnost příkazového řádku pro spustitelný příkaz. Například `FavorSizeOrSpeed` parametr `CL` úlohy odpovídá **/Os** a **/Ot** – možnosti kompilátoru.

Další parametry úlohy podporují infrastrukturu MSBuild. Například `Sources` parametr úlohy Určuje sadu úkolů, které mohou být spotřebovány dalšími úkoly. Další informace o úlohách MSBuild naleznete v tématu [– referenční dokumentace úlohy](/visualstudio/msbuild/msbuild-task-reference).

Většina úkolů vyžaduje vstup a výstup, jako jsou názvy souborů, cesty a řetězce, čísla nebo logické parametry. Společný vstup například je název pro kompilaci zdrojového souboru .cpp. Důležitý vstupní parametr je řetězec, který určuje konfiguraci sestavení a platformy, například "Debug\|Win32". Vstupy a výstupy jsou určeny jeden nebo více uživatelem definované XML `Item` elementů obsažených v `ItemGroup` elementu.

Soubor projektu můžete také určit uživatelem definované *vlastnosti* a `ItemDefinitionGroup` *položky*. Vlastnosti a položky tvoří páry název/hodnota, které lze použít jako proměnné v sestavení. Název součásti páru definuje *– makro*, a součást hodnoty prohlašuje *hodnotu makra*. Makru vlastnosti lze přistupovat pomocí $(*název*) zápisem a makro položky lze přistupovat pomocí %(*název*) notaci.

Dalších prvky XML v souboru projektu mohou testovat makra a podmíněně nastavit hodnotu všech maker nebo řídit spuštění sestavení. Názvy maker a řetězce literálů mohou být spojeny ke generování konstrukce, jako je třeba název a cesta k souboru. Na příkazovém řádku **/property** možnost nastaví nebo přepíše vlastnost projektu. Položky nelze odkazovat na příkazovém řádku.

Systém MSBuild může podmíněně spustit cíl před nebo po jiném cíli. Systém také může vytvořit jiný cíl závislosti na tom, jestli jsou soubory, které cíl využívá novější než soubory, které vydává.

## <a name="msbuild-in-the-ide"></a>MSBuild v IDE

Při nastavení vlastností projektu v integrovaném vývojovém prostředí a uložení projektu Visual C++ zapíše nastavení projektu do souboru projektu. Soubor projektu obsahuje nastavení, které jsou jedinečné pro váš projekt, ale neobsahuje všechna nastavení, které jsou nezbytné k sestavení projektu. Soubor projektu obsahuje `Import` elementy, které obsahují síť dalších *podpůrných souborů.* Soubory podpory obsahují zbývající vlastnosti, cíle a nastavení, které jsou nutné pro sestavení projektu.

Většina cílů a vlastnosti v podpůrném souboru existuje výhradně pro implementaci systému sestavení. Následující část popisuje některé užitečné cíle a vlastnosti, které můžete zadat na příkazovém řádku nástroje MSBuild. Když Pokud chcete zjistit další cíle a vlastnosti, prozkoumejte soubory v adresářích souboru podpory.

### <a name="support-file-directories"></a>Podpora adresářů se soubory

Standardně primární podpůrné soubory Visual C++ jsou umístěny v následujících adresářích. Adresáře v rámci sady Microsoft Visual Studio používají Visual Studio 2017 a novějších verzích, zatímco adresáře v rámci nástroje MSBuild používá Visual Studio 2015 a starší verze.

|Adresář|Popis|
|---------------|-----------------|
|*jednotky*: \Program Files *(x86)* \Microsoft Visual Studio\\*rok*\\*edition*\Common7\IDE\VC\VCTargets\ <br /><br />*jednotky*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp (x86) \v4.0\\*verze*\ |Obsahuje primární cílové soubory (TARGETS) a soubory vlastností (props), které jsou používány těmito cíly. Ve výchozím nastavení makro $(VCTargetsPath) odkazuje na tento adresář.|
|*jednotky*: \Program Files *(x86)* \Microsoft Visual Studio\\*rok*\\*edition*\Common7\IDE\VC\VCTargets\ Platformy\\*platformy*\ <br /><br />*jednotky*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*verze*\Platforms\\*platformy*\ |Obsahuje soubory cíle a vlastnosti specifické pro platformu, které přepíší cíle a vlastnosti svého nadřazeného adresáře. Tento adresář obsahuje taky knihovnu DLL, která definuje úlohy, které jsou používány cíli v tomto adresáři.<br /><br /> *Platformy* zastupuje ARM, Win32 nebo x64 podadresáře.|
|*jednotky*: \Program Files *(x86)* \Microsoft Visual Studio\\*rok*\\*edition*\Common7\IDE\VC\VCTargets\ Platformy\\*platformy*\PlatformToolsets\\*sady nástrojů*\ <br /><br />*jednotky*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*verze*\Platforms\\*platformy*\ PlatformToolsets\\*sady nástrojů*\ <br /><br />*jednotky*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*platformy*\PlatformToolsets\\*sady nástrojů*\ |Obsahuje adresáře, které umožňují sestavení generovat aplikace Visual C++ s použitím zadaného *nástrojů*.<br /><br /> *Rok* a *edition* zástupné symboly používají Visual Studio 2017 a novější verze. *Verze* zástupný symbol je V110 pro sadu Visual Studio 2012, V120 pro Visual Studio 2013 nebo V140 pro Visual Studio 2015. *Platformy* zastupuje ARM, Win32 nebo x64 podadresáře. *Nástrojů* zástupný text představuje podadresář sady nástrojů, například v140 pro vytváření aplikací pro Windows pomocí nástrojů Visual Studio 2015, v120_xp k vývoji pro Windows XP pomocí sady nástrojů Visual Studio 2013 nebo v110_wp80 do vytváření aplikací Windows Phone 8.0 pomocí sady nástrojů Visual Studio 2012.<br /><br />Neobsahuje cestu, která obsahuje adresáře, které umožňují sestavení generovat aplikace Visual C++ 2008 nebo Visual C++ 2010 *verze*a *platformy* představuje zástupný text Itanium, Win32 nebo x64 podadresáře. *Nástrojů* zástupný text představuje podadresář sady nástrojů v90 nebo v100.|

### <a name="support-files"></a>Soubory podpory

Adresáře souboru podpory obsahují soubory s těmito příponami:

|Rozšíření|Popis|
|---------------|-----------------|
|.TARGETS|Obsahuje `Target` elementů XML, které určují úkoly, které jsou spouštěny cílem. Může také obsahovat `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup`a uživatelem definovanými `Item` prvků, které slouží k přiřazení souborů a možnosti příkazového řádku pro parametry úlohy.<br /><br /> Další informace najdete v tématu [Target – Element (MSBuild)](/visualstudio/msbuild/target-element-msbuild).|
|.props|Obsahuje `Property Group` a uživatelem definovanými `Property` elementů XML, které určují soubor a nastavení parametru používané během sestavení.<br /><br /> Může také obsahovat `ItemDefinitionGroup` a uživatelem definovanými `Item` elementů XML, které určují další nastavení. Položky definované ve skupině definice se podobají vlastnosti, ale není přístupný z příkazového řádku. Soubory projektu Visual C++ často používají položky namísto vlastností k vyjádření nastavení.<br /><br /> Další informace najdete v tématu [itemgroup – Element (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), [ItemDefinitionGroup – Element (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild), a [Item – Element (MSBuild)](/visualstudio/msbuild/item-element-msbuild).|
|.xml|Obsahuje elementy XML, které deklarujete a inicializujete prvky uživatelského rozhraní integrovaného vývojového prostředí jako je například seznamy vlastností a stránky vlastností a textové pole a seznamu ovládací prvky.<br /><br /> Soubory XML přímo podporují IDE, nikoli MSBuild. Však hodnoty vlastnosti IDE jsou přiřazeny k vlastnostem sestavení a položkám.<br /><br /> Většina souborů XML jsou v podadresáři národního prostředí. Například soubory pro oblast angličtina-USA jsou v $(VCTargetsPath) \1033\\.|

## <a name="user-targets-and-properties"></a>Uživatelské cíle a vlastnosti

K co nejefektivnějšímu využití MSBuild na příkazovém řádku, pomáhá zjistit, jaké vlastnosti a cíle jsou užitečné a důležité. Většina vlastností a cílů pomáhá implementovat systém sestavení Visual C++ a v důsledku toho nejsou relevantní pro daného uživatele. Tato část popisuje některé vhodné uživatelem orientované vlastnosti a cíle.

### <a name="platformtoolset-property"></a>Vlastnost PlatformToolset

`PlatformToolset` Vlastnost určuje, které sady nástrojů Visual C++ se používají v sestavení. Ve výchozím nastavení se používá aktuální sady nástrojů. Pokud je tato vlastnost nastavena, hodnota vlastnosti je zřetězená s literálovými řetězci k vytvoření cesty k adresáři, který obsahuje vlastnost a cílové soubory, které jsou nutné k vytvoření projektu pro konkrétní platformu. Pro sestavení pomocí této verze sady nástrojů platformy musí být nainstalovaná sada nástrojů platformy.

Například nastavit `PlatformToolset` vlastnost `v140` svou aplikaci pomocí knihoven a nástrojů Visual C++ 2015:

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>Vlastnost PreferredToolArchitecture

`PreferredToolArchitecture` Vlastnost určuje, zda v sestavení použity 32bitové nebo 64bitové kompilátoru a nástrojů. Tato vlastnost nemá vliv výstupní architekturu nebo konfiguraci platformy. Ve výchozím nastavení, nástroj MSBuild používá x86 verzi kompilátoru a nástrojů, je-li tato vlastnost není nastavená.

Například nastavit `PreferredToolArchitecture` vlastnost `x64` použití 64bitového kompilátoru a nástrojů k sestavení aplikace:

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>Vlastnost UseEnv

Ve výchozím nastavení specifické pro platformu pro aktuální projekt potlačit proměnné prostředí PATH, INCLUDE, LIB, LIBPATH, konfigurace a PLATFORMA. Nastavte `UseEnv` vlastnost `true` zaručí, že proměnné prostředí nejsou přepsána.

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Cíle

Existují stovky cílů v podpůrných souborů Visual C++. Nejvíce je však cílů orientovaných na systém, které uživatel může ignorovat. Většině cílů systémů předchází podtržítko (_), nebo mít název, který začíná "Připravitna", "Vypočítat", "Před", "After", "Pre" nebo "Post".

V následující tabulce jsou uvedeny některé užitečné cíle zaměřených na uživatele.

|Cíl|Popis|
|------------|-----------------|
|Nástroje BscMake|Spustí nástroj vyhledejte informace o údržbě nástroje Microsoft bscmake.exe.|
|Sestavení|Vytvoří projekt.<br /><br /> Toto je výchozí cíl pro projekt.|
|ClCompile|Spustí nástroj kompilátoru Visual C++, cl.exe.|
|Vyčistit|Odstraní dočasné a průběžné zprostředkující soubory sestavení.|
|lib|Spustí nástroj Microsoft 32bitový Správce knihovny lib.exe.|
|Odkaz|Spustí nástroj linker Visual C++, link.exe.|
|ManifestResourceCompile|Extrahujte seznam prostředků z manifestu a poté spustí nástroj Microsoft Windows Resource Compiler, rc.exe.|
|MIDL|Spustí nástroj kompilátoru Microsoft Interface Definition Language (MIDL), midl.exe.|
|Opětovné sestavení|Čistí a poté sestaví váš projekt.|
|ResourceCompile|Spustí nástroj Microsoft Windows Resource Compiler, rc.exe.|
|Xdcmake –|Spustí nástroj dokumentace XML, xdcmake.exe.|
|XSD|Spustí nástroj definice schématu XML, xsd.exe. *Viz poznámka níže.*|

> [!NOTE]
> V sadě Visual Studio 2017, projekt C++ podpora **xsd** zastaralé soubory. Můžete dál používat **Microsoft.VisualC.CppCodeProvider** přidáním **CppCodeProvider.dll** ručně do mezipaměti GAC.

## <a name="see-also"></a>Viz také

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
