---
title: Přehled nástroje MSBuild (Visual C++) | Microsoft Docs
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
ms.openlocfilehash: ae6e6d826f4bc1e8c9ab6cc28686e4ad1e6e3b02
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="msbuild-visual-c-overview"></a>Přehled nástroje MSBuild (Visual C++)  
  
MSBuild je standardní sestavení systému pro projekty Visual C++. Při sestavování projektu v sadě Visual Studio integrované vývojové prostředí (IDE), použije nástroj msbuild.exe, soubor projektu na základě XML a soubory volitelné nastavení. Přestože je možné použít msbuild.exe a soubor projektu na příkazovém řádku, rozhraní IDE poskytuje uživatelské rozhraní, takže můžete snadno konfigurovat nastavení a sestavení projektu. Tento přehled popisuje, jak Visual C++ používá MSBuild systému.  
  
## <a name="prerequisites"></a>Požadavky  
  
Přečtěte si následující dokumenty o nástroji MSBuild.  
  
- [MSBuild](/visualstudio/msbuild/msbuild)  
 Přehled koncepty nástroje MSBuild.  
  
- [Referenční dokumentace nástroje MSBuild](/visualstudio/msbuild/msbuild-reference)  
 Referenční informace o systému nástroje MSBuild.  
  
- [Referenční dokumentace schématu souboru projektu](/visualstudio/msbuild/msbuild-project-file-schema-reference)  
 Obsahuje seznam prvků schématu XML MSBuild, spolu s jejich atributů a nadřazené a podřízené elementy. Zejména Poznámka: [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup –](/visualstudio/msbuild/propertygroup-element-msbuild), [cíl](/visualstudio/msbuild/target-element-msbuild), a [úloh](/visualstudio/msbuild/task-element-msbuild) elementy.  
  
- [Referenční dokumentace k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference)  
 Popisuje možnosti, které můžete použít s msbuild.exe a argumenty příkazového řádku.  
  
- [Referenční dokumentace úlohy](/visualstudio/msbuild/msbuild-task-reference)  
 Popisuje úlohy nástroje MSBuild. Zejména Poznámka: tyto úlohy, které jsou specifické pro aplikaci Visual C++: [BscMake – úloha](/visualstudio/msbuild/bscmake-task), [CL – úloha](/visualstudio/msbuild/cl-task), [cppclean – úloha](/visualstudio/msbuild/cppclean-task), [LIB – úloha](/visualstudio/msbuild/lib-task), [Propojit úloh](/visualstudio/msbuild/link-task), [MIDL – úloha](/visualstudio/msbuild/midl-task), [MT – úloha](/visualstudio/msbuild/mt-task), [RC – úloha](/visualstudio/msbuild/rc-task), [SetEnv – úloha](/visualstudio/msbuild/setenv-task), [ Vcmessage – úloha](/visualstudio/msbuild/vcmessage-task), [XDCMake – úloha](/visualstudio/msbuild/xdcmake-task), [XSD – úloha](/visualstudio/msbuild/xsd-task).  
  
## <a name="msbuild-on-the-command-line"></a>Na příkazovém řádku MSBuild  
  
Následující příkaz z [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) ukazuje, že provede nástroj msbuild.exe na implicitního nebo explicitního *project_file* argument (soubor VCXPROJ pro projekty Visual C++) a nula nebo více příkazového řádku *možnosti* argumenty.  
  
> **MSBuild.exe** [ *project_file* ] [ *možnosti* ]  
  
Použití **/target** (nebo **/t**) a **/property** (nebo **/p**) možnosti příkazového řádku k přepsání specifické vlastnosti a cíle, které jsou v souboru projektu zadána.  
  
Základní funkci souboru projektu slouží k zadání *cíl*, což je konkrétní operace u projektu a vstupy a výstupy, která jsou potřebná k provedení této operace. Soubor projektu můžete určit jeden nebo více cílů, které mohou zahrnovat cíl výchozí.  
  
Každý cíl se skládá z pořadí jednoho nebo více *úlohy*. Každý úkol je reprezentována třídu rozhraní .NET Framework, která obsahuje jeden spustitelný soubor příkaz. Například [CL – úloha](/visualstudio/msbuild/cl-task) obsahuje [cl.exe](../build/reference/compiling-a-c-cpp-program.md) příkaz.  
  
A *úloh parametr* je vlastnost třídy úlohy a obvykle představuje možnost příkazového řádku spustitelného souboru příkazu. Například `FavorSizeOrSpeed` parametr `CL` úlohy odpovídá **/Os** a **/Ot** – možnosti kompilátoru.  
  
Parametry úlohy další podporu infrastruktury nástroje MSBuild. Například `Sources` úloh parametr určuje sadu úloh, které mohou být spotřebovávána další úlohy. Další informace o úlohy nástroje MSBuild najdete v tématu [– Reference úlohy](/visualstudio/msbuild/msbuild-task-reference).  
  
Většinu úloh vyžadují vstupy a výstupy, jako jsou názvy souborů, cesty a řetězce, parametry číselná nebo logická hodnota. Například běžný vstup je název zdrojového souboru sada zkompilovat. Důležité vstupní parametr je řetězec, který určuje konfiguraci sestavení a platformy, například "ladění\|Win32". Vstupy a výstupy jsou určené jeden nebo více uživatelem definované XML `Item` elementů obsažených v `ItemGroup` elementu.  
  
Soubor projektu můžete také určit vlastní *vlastnosti* a `ItemDefinitionGroup` *položky*. Vlastnosti a položky tvoří dvojice název/hodnota, které lze použít jako proměnné v buildu. Součást názvu pár definuje *makro*, a deklaruje komponentu hodnotu *makro hodnotu*. Makro vlastnost přistupuje pomocí $(*název*) zápis a makru položky přistupuje pomocí %(*název*) zápis.  
  
Jiných elementů XML v souboru projektu můžete otestovat makra a pak podmíněně nastavit hodnotu žádné makro nebo řízení provádění sestavení. Literál řetězce s názvy makro a může být zřetězen ke generování konstruktory, jako jsou název a cesta k souboru. Na příkazovém řádku **/property** možnost nastavuje nebo přepsání vlastnosti projektu. Položky nelze odkazovat na příkazovém řádku.  
  
Systém MSBuild můžete podmíněnému spuštění cíl před nebo po jiný cíl. Systém také můžete vytvořit cíl založené na tom, jestli jsou novější než soubory, které se vydá soubory, které využívá cíl.  
  
## <a name="msbuild-in-the-ide"></a>MSBuild v prostředí IDE  
  
Když nastavíte vlastnosti projektu v prostředí IDE a potom uložte projekt, Visual C++ nastavení projektu zapisuje do souboru projektu. Nastavení, které jsou jedinečné pro váš projekt obsahuje soubor projektu, ale neobsahuje všechna nastavení, které jsou nezbytné k sestavení projektu. Soubor projektu obsahuje `Import` elementy, které zahrnují síť dalších *podpůrných souborů.* Soubory podpory obsahovat zbývající vlastnosti, cílů a nastavení, které jsou nutné k sestavení projektu.  
  
Většina cíle a vlastnosti v podpůrné soubory existují výhradně k implementaci systém sestavení. Následující část popisuje některé užitečné cíle a vlastnosti, které můžete zadat na příkazovém řádku MSBuild. Chcete-li zjistit další cíle a vlastnosti, prozkoumejte soubory v adresáři souboru podpory.  
  
### <a name="support-file-directories"></a>Podpora souborové adresáře  
  
Ve výchozím nastavení jsou primární soubory podpory Visual C++ nachází v následujících adresářích. Adresáře sady Microsoft Visual Studio jsou používány Visual Studio 2017 a novější verze, zatímco adresáře MSBuild používají Visual Studio 2015 a starší verze.  
  
|Adresář|Popis|  
|---------------|-----------------|  
|*jednotka*: \Program Files *(x86)* \Microsoft Visual Studio\\*roku*\\*edition*\Common7\IDE\VC\VCTargets\ <br /><br />*jednotka*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp (x86) \v4.0\\*verze*\ |Obsahuje soubory primární cíl (.targets) a vlastnost soubory (props), které jsou používány cíle. Ve výchozím nastavení makro $(VCTargetsPath) odkazuje tento adresář.|  
|*jednotka*: \Program Files *(x86)* \Microsoft Visual Studio\\*roku*\\*edition*\Common7\IDE\VC\VCTargets\ Platformy\\*platformy*\ <br /><br />*jednotka*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*verze*\Platforms\\*platformy*\ |Obsahuje soubory specifické pro platformu cíle a vlastnosti, které přepsání cíle a vlastnosti v jeho nadřazeném adresáři. Tento adresář také obsahuje knihovnu DLL, kterou definuje úlohy, které jsou používány cíle v tomto adresáři.<br /><br /> *Platformy* zástupný symbol představuje ARM, Win32 nebo x64 podadresáři.|  
|*jednotka*: \Program Files *(x86)* \Microsoft Visual Studio\\*roku*\\*edition*\Common7\IDE\VC\VCTargets\ Platformy\\*platformy*\PlatformToolsets\\*sada nástrojů*\ <br /><br />*jednotka*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*verze*\Platforms\\*platformy*\ PlatformToolsets\\*sada nástrojů*\ <br /><br />*jednotka*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*platformy*\PlatformToolsets\\*sada nástrojů*\ |Obsahuje adresáře, které umožňují sestavení ke generování aplikací Visual C++ pomocí zadaného *nástrojů*.<br /><br /> *Roku* a *edice* zástupné symboly používají Visual Studio 2017 a novější verze. *Verze* zástupný symbol je V110 pro sadu Visual Studio 2012, V120 pro Visual Studio 2013 nebo V140 pro Visual Studio 2015. *Platformy* zástupný symbol představuje ARM, Win32 nebo x64 podadresáři. *Nástrojů* zastupuje podadresáři sada nástrojů, například v140 pro vytváření aplikací pro Windows pomocí sady nástrojů Visual Studio 2015, v120_xp k sestavení pro systém Windows XP pomocí nástrojů Visual Studio 2013 nebo v110_wp80 na zástupný symbol vývoj aplikací pro Windows Phone 8.0 pomocí nástrojů Visual Studio 2012.<br /><br />Neobsahuje cestu, která obsahuje adresáře, které umožňují sestavení ke generování aplikace Visual C++ 2008 nebo Visual C++ 2010 *verze*a *platformy* představuje zástupný symbol Itanium, Win32 nebo x64 podadresáři. *Nástrojů* nástrojů podadresáři v90 nebo v100 zastupuje zástupný symbol.|  
  
### <a name="support-files"></a>Soubory podpory aplikace  
  
Souborové adresáře podporu obsahovat soubory s těmito příponami:  
  
|Rozšíření|Popis|  
|---------------|-----------------|  
|.TARGETS|Obsahuje `Target` elementů XML určující úlohy, které jsou spouštěny cíl. Může také obsahovat `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup`a uživatelem definovanými `Item` elementy, které slouží k přiřazení soubory a možnosti příkazového řádku pro parametry úlohy.<br /><br /> Další informace najdete v tématu [Target – Element (MSBuild)](/visualstudio/msbuild/target-element-msbuild).|  
|props|Obsahuje `Property Group` a uživatelem definovanými `Property` elementů XML, které zadejte soubor a parametr nastavení, které se používají při sestavení.<br /><br /> Může také obsahovat `ItemDefinitionGroup` a uživatelem definovanými `Item` elementů XML, které zadejte další nastavení. Položky definované ve skupině Definice podobají vlastnosti, ale není přístupný z příkazového řádku. Soubory projektu Visual C++ často používá položky místo vlastnosti k reprezentaci nastavení.<br /><br /> Další informace najdete v tématu [ItemGroup – Element (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), [ItemDefinitionGroup – Element (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild), a [Item – Element (MSBuild)](/visualstudio/msbuild/item-element-msbuild).|  
|.xml|Obsahuje elementy XML, které deklarace a inicializace prvky uživatelského rozhraní IDE například seznam vlastností a stránky vlastností a ovládací prvky formátovaného textu a v seznamu.<br /><br /> Soubory XML přímo podporují IDE, nejsou MSBuild. Hodnoty vlastností IDE však přiřazené k vytvoření vlastností a položek.<br /><br /> Většina souborů .xml jsou v podadresáři specifická pro národní prostředí. Například soubory pro oblast USA angličtina jsou v \1033 $(VCTargetsPath)\\.|  
  
## <a name="user-targets-and-properties"></a>Cíle uživatele a vlastnosti  
  
Použití nástroje MSBuild efektivní na příkazovém řádku, je důležité znát, které vlastnosti a cíle jsou užitečné a relevantní. Většinu vlastností a cíle pomohou implementovat systém sestavení Visual C++ a v důsledku toho nejsou pro uživatele relevantní. Tato část popisuje některé vlastnosti smysl orientovaných na uživatele a cíle.  

### <a name="platformtoolset-property"></a>Vlastnost PlatformToolset  
  
`PlatformToolset` Vlastnost určuje, které sada nástrojů Visual C++ se používá v buildu. Ve výchozím nastavení se používá aktuální sady nástrojů. Pokud je tato vlastnost nastavena, hodnota vlastnosti je zřetězen s literálu řetězce, které vytvoří cestu adresáře, který obsahuje vlastnost a cíle soubory, které jsou potřebné pro vytvoření projektu pro konkrétní platformu. Sada nástrojů platformy musí být nainstalována na sestavení pomocí této verze sady nástrojů platformy.  
  
Například nastavit `PlatformToolset` vlastnost `v140` sestavení aplikace pomocí nástrojů Visual C++ 2015 a knihovny:  
  
`msbuild myProject.vcxproj /p:PlatformToolset=v140`  
  
### <a name="preferredtoolarchitecture-property"></a>Vlastnost PreferredToolArchitecture  
  
`PreferredToolArchitecture` Vlastnost určuje, zda 32bitovou nebo 64bitovou kompilátoru a nástroje se používají v buildu. Tato vlastnost nemá vliv výstup Architektura platformy nebo konfigurace. Ve výchozím nastavení používá MSBuild x86 verzi kompilátoru a nástroje, pokud není tato vlastnost nastavena.  
  
Například nastavit `PreferredToolArchitecture` vlastnost `x64` pomocí nástrojů pro 64bitový kompilátor a sestavit aplikaci:  
  
`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### <a name="useenv-property"></a>Useenv – vlastnost  
  
Ve výchozím nastavení specifických pro platformy pro aktuální projekt přepsat proměnné prostředí CESTU, zahrnout, LIB, LIBPATH, konfigurace a platformy. Nastavte `UseEnv` vlastnost `true` zaručit, aby proměnné prostředí nepřepíše.  
  
`msbuild myProject.vcxproj /p:UseEnv=true`  
  
### <a name="targets"></a>Cíle  
  
Existují stovky cílů v podpůrných souborů Visual C++. Většina však jsou zaměřené na konkrétní systém cíle, které uživatel můžete ignorovat. Většina systému cíle předchází podtržítko (_), nebo mít název, který začíná "PrepareFor", "Výpočetní", "Před", "Po", "Bez" nebo "Post".  
  
Následující tabulka uvádí několik užitečné cíle orientovaných na uživatele.  
  
|cíl|Popis|  
|------------|-----------------|  
|BscMake|Spustí nástroj Microsoft procházet údržby nástroje pro konfiguraci bscmake.exe.|  
|Sestavení|Vytvoří projekt.<br /><br /> Toto je výchozí cíl pro projekt.|  
|ClCompile|Spustí nástroj kompilátoru Visual C++ cl.exe.|  
|Vyčištění|Odstranění dočasné a zprostředkující sestavení souborů.|  
|Lib|Spustí nástroj Microsoft 32bitový Správce knihovny lib.exe.|  
|Odkaz|Spustí nástroj linkeru jazyka Visual C++ link.exe.|  
|ManifestResourceCompile|Extrahuje z manifestu seznamu prostředků a potom provede nástroj Microsoft kompilátor prostředků Windows rc.exe.|  
|MIDL|Spustí nástroj Microsoft rozhraní Definition Language (MIDL) kompilátoru midl.exe.|  
|Opětovné sestavení|Vyčistí a pak sestavení projektu.|  
|ResourceCompile|Spustí nástroj Microsoft kompilátor prostředků Windows rc.exe.|  
|XdcMake|Spustí nástroj dokumentace XML xdcmake.exe.|  
|XSD|Spustí nástroj XML Schema Definition xsd.exe.|  
  
## <a name="see-also"></a>Viz také  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
