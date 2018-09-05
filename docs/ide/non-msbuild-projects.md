---
title: Otevřete složku projekty v jazyce Visual C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/01/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4444e70ec158d7afa35c3955bbef9af4bfa12f2
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758875"
---
# <a name="open-folder-projects-in-visual-c"></a>Otevřete složku projekty v jazyce Visual C++

V sadě Visual Studio 2017 nebo novější umožňuje funkce "Otevřít složku" Otevřít složku zdrojových souborů a okamžitě začněte programovat s podporou technologie IntelliSense, procházení, refaktoring, ladění, a tak dále. Jsou načteny žádné soubory .sln nebo .vcxproj; v případě potřeby můžete zadat vlastní úkoly a sestavujte a uvádějte parametry v souborech .json jednoduché. Používá technologii otevřít složku, Visual C++ nyní podporují pouze dojde ke ztrátě kolekce souborů, ale také téměř jakékoli sestavení systému, včetně CMake, Ninja, QMake (pro projekty Qt), gyp, SCons, Gradle, Buck, zkontrolujte a další. 

Použití funkce Otevřít složku v hlavní nabídce vyberte *soubor | Otevřít | Složka* nebo stiskněte klávesu *Ctrl + Shift + Alt + O*. Průzkumník řešení okamžitě zobrazí všechny soubory ve složce. Můžete kliknout na jakýkoli soubor můžete začít s jeho úpravami. Na pozadí spustí aplikace Visual Studio indexování soubory, které chcete povolit technologii IntelliSense, navigace a funkcí refaktoringu. Úpravy, vytváření, přesunout a odstranit soubory, Visual Studio automaticky sleduje změny a průběžně aktualizuje jeho index IntelliSense. 
  
## <a name="cmake-projects"></a>Projekty CMake
CMake je integrovaná v integrovaném vývojovém prostředí sady Visual Studio jako nástroje CMake pro Visual C++, součást sady funkcí klasické pracovní plochy jazyka C++. Další informace najdete v tématu [nástroje CMake pro Visual C++](cmake-tools-for-visual-cpp.md).
 
## <a name="qmake-projects-that-target-the-qt-framework"></a>QMake projekty, které cílí rozhraní framework Qt
Můžete použít nástroje CMake pro Visual C++ pro cílení Qt k sestavení projektů Qt, nebo můžete použít [rozšíření sady Visual Studio Qt](https://download.qt.io/development_releases/vsaddin/) pro Visual Studio 2015 nebo Visual Studio 2017.

## <a name="gyp-cons-scons-buck-etc"></a>gyp nevýhody SCons, Buck, atd.
Můžete použít libovolný systém sestavení v jazyce Visual C++ a přesto využívat výhod integrovaného vývojového prostředí Visual C++ a ladicí program. Při otevření kořenové složce vašeho projektu Visual C++ používá heuristiky pro index zdrojové soubory pro IntelliSense a procházení. Úpravou souboru CppProperties.json může poskytnout nápovědu, konstrukce kódu. Podobným způsobem můžete nakonfigurovat váš program sestavení pomocí úpravy souboru launch.vs.json. 

## <a name="configuring-open-folder-projects"></a>Konfigurace projektů otevřít složku
Projekt otevřít složku můžete přizpůsobit prostřednictvím tři soubory JSON:
|||
|-|-|
|CppProperties.json|Zadejte vlastní konfigurační informace pro procházení. Vytvořte tento soubor v případě potřeby v kořenové složce projektu.|
|launch.vs.json|Zadejte argumenty příkazového řádku. Přístup přes **Průzkumníka řešení** položka kontextové nabídky **nastavení ladění a spouštění**.|
|tasks.vs.json|Zadejte vlastní sestavení příkazy a přepínače kompilátoru. Přístup přes **Průzkumníka řešení** položka kontextové nabídky **nakonfigurovat úlohy**.|

### <a name="configure-intellisense-with-cpppropertiesjson"></a>Konfigurace technologie IntelliSense s CppProperties.json
Technologie IntelliSense a procházení chování částečně závisí na konfiguraci aktivních sestavení, která definuje #include cesty, přepínače kompilátoru a další parametry. Visual Studio poskytuje ve výchozím nastavení, konfigurace Debug a Release. U některých projektů budete muset vytvořit vlastní konfiguraci, aby IntelliSense a procházení funkce plně pochopit kód. Pokud chcete definovat novou konfiguraci, vytvořte soubor s názvem CppProperties.json v kořenové složce. Tady je příklad:

```json
{
  "configurations": [
    {
      "name": "Windows x64",
      "includePath": [ "include" ],
      "defines": [ "_DEBUG" ],
      "compilerSwitches": "/std:c++17",
      "intelliSenseMode": "msvc-x64",
      "forcedInclude": [ "pch.h" ],
      "undefines": []
    }
  ]
}
```
Konfigurace může mít některou z následujících vlastností:

|||  
|-|-| 
|`name`|Název konfigurace, který se zobrazí v rozevírací nabídce konfigurace C++|
|`includePath`|Seznam složek, které musí být zadán v cesty zahrnutí (mapuje /I pro většina kompilátorů)|
|`defines`|seznam maker, která by měla být definována (mapuje /D pro většina kompilátorů)|
|`compilerSwitches`|jeden nebo více dalších přepínačů, které mohou mít vliv na chování technologie IntelliSense|
|`forcedInclude`|hlavičky, které mají být automaticky zahrnuty ve všech jednotkách kompilace (/FI mapuje pro MSVC nebo – zahrnout pro clang)|
|`undefines`|seznam maker na nedefinované (mapuje /U pro MSVC)|
|`intelliSenseMode`|modul IntelliSense, který se má použít. Můžete zadat konkrétní varianty architektury pro MSVC a gcc, Clang:
- msvc-x86 (výchozí)
- msvc-x64
- msvc-arm
- windows-clang-x86
- windows-clang-x64
- windows-clang-arm
- Linux-x64
- Linux-x86
- Linux-arm
- gccarm

#### <a name="environment-variables"></a>Proměnné prostředí
CppProperties.json podporuje systém rozšíření proměnné prostředí pro zahrnout cesty a dalších hodnot vlastností. Syntaxe je `${env.FOODIR}` rozbalit proměnné prostředí `%FOODIR%`. Podporují se také následující proměnných definovaných systémem:

|Název proměnné|Popis|  
|-----------|-----------------|
|vsdev|Výchozí prostředí sady Visual Studio|
|msvc_x86|Sestavit x86 x86 pomocí nástroje|
|msvc_arm|Kompilování pro ARM pomocí x86 nástroje|
|msvc_arm64|Použitou ke kompilaci pro ARM64 x86 nástroje|
|msvc_x86_x64|Kompilace z důvodu AMD64 x86 pomocí nástroje|
|msvc_x64_x64|Kompilace z důvodu AMD64 použití 64bitových nástrojů|
|msvc_arm_x64|Kompilace pro použití 64bitových nástrojů ARM|
|msvc_arm64_x64|Kompilace pro ARM64 použití 64bitových nástrojů|

Když je nainstalovaná úloha Linux, jsou k dispozici pro systémy Linux a WSL vzdáleným cílením následujících prostředích:

|Název proměnné|Popis|  
|-----------|-----------------|
|linux_x86|Cíl x86 Linux vzdáleně|
|linux_x64|Cíl x64 Linux vzdáleně|
|linux_arm|Vzdáleně určené pro ARM Linux|

Můžete definovat vlastní proměnné prostředí v CppProperties.json buď globálně nebo podle konfigurace. Následující příklad ukazuje, jak výchozí a vlastní proměnné prostředí může být deklarovaný a používá. Globální **prostředí** vlastnost deklaruje proměnnou s názvem **zahrnout** , který mohou využívat všechny konfigurace:

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\\src\\includes"
    }
  ],
 
  "configurations": [
    {
      "inheritEnvironments": [
        // Inherit the MSVC 32-bit environment and toolchain.
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "msvc-x86"
    },
    {
      "inheritEnvironments": [
        // Inherit the MSVC 64-bit environment and toolchain.
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "msvc-x64"
    }
  ]
}
```
Můžete také definujte **prostředí** uvnitř konfiguraci tak, že platí pouze pro tuto konfiguraci a přepíše všechny globální proměnné se stejným názvem vlastnosti. V následujícím příkladu x64 konfigurace definuje místní **zahrnout** proměnné, která přepíše globální hodnotu:

```json
{
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\\src\\includes"
    }
  ],
 
  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined in the global environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "msvc-x86"
    },
    {
      "environments": [
        {
          // Append 64-bit specific include path to env.INCLUDE.
          "INCLUDE": "${env.INCLUDE};${workspaceRoot}\\src\\includes64"
        }
      ],
 
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined in the local environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "msvc-x64"
    }
  ]
}
```

Všechny vlastní a výchozí proměnné prostředí jsou také k dispozici v tasks.vs.json a souboru launch.vs.json.

#### <a name="macros"></a>Makra
Máte přístup k následující předdefinované makra v CppProperties.json:
|||
|-|-|
|`${workspaceRoot}`| Úplná cesta ke složce pracovního prostoru|
|`${projectRoot}`| Úplná cesta ke složce, ve kterém je umístí CppProperties.json|
|`${vsInstallDir}`| Úplná cesta ke složce, kde je nainstalována spuštěné instance sady VS 2017|

Pokud váš projekt má zahrnout složku a také zahrnuje windows.h a dalších běžných hlaviček ze sady Windows SDK, budete chtít aktualizovat vaši CppProperties.json obsahuje konfigurační soubor s těmito:

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\ucrt",
        "${env.NETFXSDKDir}\\include\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\shared",
        "${env.VCToolsInstallDir}include"
      ]
    }
  ]
}
```

**Poznámka:** `%WindowsSdkDir%` a `%VCToolsInstallDir%` nejsou nastaveny jako globálních proměnných prostředí proto ujistěte se, že začnete devenv.exe z "Příkazový řádek vývojáře pro VS 2017", který definuje tyto proměnné.

Řešení potíží s IntelliSense chyby způsobené chybějící vkládaným, otevřete **seznam chyb** a filtrovat výstup "Pouze technologie IntelliSense" a kódem chyby E1696 "nelze otevřít zdrojový soubor...". 

Můžete vytvořit libovolný počet konfigurací v CppProperties.json. Každý se zobrazí v rozevírací nabídce konfigurace:

```json
{
  "configurations": [
    {
      "name": "Windows",
      ...
    },
    {
      "name": "with EXTERNAL_CODECS",
      ...
    }
  ]
}
```
### <a name="define-tasks-with-tasksvsjson"></a>Definovat úkoly pomocí tasks.vs.json
Můžete automatizovat skripty sestavení ani žádné jiné externí operace se soubory, které máte v aktuálním pracovním prostoru spuštěním jako úlohy přímo v integrovaném vývojovém prostředí. Vytvoření nového úkolu můžete nakonfigurovat tak, že kliknete pravým tlačítkem na soubor nebo složku a vyberete **nakonfigurovat úlohy**. 

![Konfigurace funkce Otevřít složku úloh](media/open-folder-config-tasks.png)

To vytvoří (nebo se otevře) `tasks.vs.json` souboru ve složce .vs, který sada Visual Studio vytvoří v kořenové složce projektu. Můžete definovat všechny libovolné úlohy v tomto souboru a poté vyvolat z **Průzkumníka řešení** kontextové nabídky. Následující příklad ukazuje tasks.vs.json soubor, který definuje jeden úkol. `taskName` Definuje název, který se zobrazí v místní nabídce. `appliesTo` Definuje soubory, které lze příkaz provést na. `command` Vlastnost odkazuje na proměnnou prostředí COMSPEC, který určuje cestu pro konzolu (cmd.exe ve Windows). Můžete také odkazovat na proměnné prostředí, které jsou deklarovány v CppProperties.json a CMakeSettings.json. `args` Určuje vlastnosti příkazového řádku, který má být volána. `${file}` Makra obnoví na vybraný soubor na **Průzkumníka řešení**. V následujícím příkladu se zobrazí název souboru aktuálně vybraného .cpp.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```
Po uložení tasks.vs.json, klikněte pravým tlačítkem na libovolný soubor .cpp ve složce, vyberte **Echo filename** z místní nabídky a najdete ve výstupním okně zobrazí název souboru.



#### <a name="appliesto"></a>AppliesTo –
Můžete vytvářet úkoly pro kterýkoli soubor nebo složku tak, že zadáte jeho název `appliesTo` pole, například `"appliesTo" : "hello.cpp"`. Následující masky souboru můžete použít jako hodnoty:
|||
|-|-|
|`"*"`| Úloha je k dispozici pro všechny soubory a složky v pracovním prostoru|
|`"*/"`| Úloha je dostupná pro všechny složky v pracovním prostoru|
|`"*.cpp"`| Úloha je k dispozici pro všechny soubory s příponou .cpp v pracovním prostoru|
|`"/*.cpp"`| Úloha je k dispozici pro všechny soubory s příponou .cpp v kořenu pracovního prostoru|
|`"src/*/"`| Úloha je k dispozici pro všechny podsložky složky "src"|
|`"makefile"`| Úloha je dostupná pro všechny soubory souboru pravidel v pracovním prostoru|
|`"/makefile"`| Úloha je dostupná jenom do souboru pravidel v kořenu pracovního prostoru|

#### <a name="output"></a>výstup
Použití `output` vlastnosti k určení spustitelného souboru, který se spustí po stisknutí klávesy **F5**. Příklad:

```json
      "output": "${workspaceRoot}\\bin\\hellomake.exe" 
```

#### <a name="macros-for-tasksvsjson"></a>Makra pro tasks.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Určuje všechny proměnné prostředí (např. ${env. PATH}, ${env.COMSPEC} a tak dále), která je nastavena pro příkazový řádek pro vývojáře. Další informace najdete v tématu [Developer Command Prompt pro sadu Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Úplná cesta ke složce pracovního prostoru (například "C:\sources\hello")|
|`${file}`| Úplná cesta k souboru nebo složky vybrané ke spuštění této úlohy před (například "C:\sources\hello\src\hello.cpp")|
|`${relativeFile}`| relativní cesta k souboru nebo složky (například "src\hello.cpp")|
|`${fileBasename}`| Název souboru bez cesty a přípony (například "hello")|
|`${fileDirname}`| Úplná cesta k souboru, s výjimkou názvu souboru (například "C:\sources\hello\src")|
|`${fileExtname}`| rozšíření vybraný soubor (například "")|

#### <a name="custom-macros"></a>Vlastní makra
K definování vlastní – makro v tasks.vs.json, přidejte dvojici názvu a hodnoty před bloky úloh. Následující příklad definuje makro s názvem `outDir` což spotřebovává v `args` vlastnost:

```json
{
"version": "0.2.1",
  "outDir": "${workspaceRoot}\\bin",
  "tasks": [
    {
      "taskName": "List outputs",
      "*",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": [
        "dir ${outDir}"
      ]
    }
  ]
```

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Konfigurace ladění parametrů pomocí launch.vs.json
Přizpůsobení vašeho programu argumenty příkazového řádku, klikněte pravým tlačítkem na spustitelný soubor **Průzkumníka řešení** a vyberte **nastavení ladění a spouštění**. Tím otevřete existující `launch.vs.json` souboru, nebo pokud žádný neexistuje, vytvoří nový soubor naplněna informacemi o programu, který jste vybrali. 

Pokud chcete zadat další argumenty, jednoduše je přidejte do `args` pole JSON, jak je znázorněno v následujícím příkladu:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CPP\\7zip\\Bundles\\Alone\\O\\7za.exe",
      "name": "7za.exe list content of helloworld.zip",
      "args": [ "l", "d:\\sources\\helloworld.zip" ]
    }
  ]
}
```

Při ukládání tohoto souboru, nová konfigurace se zobrazí v rozevíracím seznamu cíl ladění a vyberte spuštění ladicího programu. Můžete vytvořit mnoho konfiguraci ladění, jak můžete pro libovolný počet spustitelné soubory. Pokud stisknete **F5** teď ladicí program spustí a přístupů všechny zarážky, možná jste už nastavili. Všechny známé ladicí program systému windows a jejich funkci jsou teď k dispozici.

## <a name="see-also"></a>Viz také
[Integrované vývojové prostředí a nástroje pro vývoj v jazyce Visual C++](ide-and-tools-for-visual-cpp-development.md)

