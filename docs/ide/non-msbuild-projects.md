---
title: "Otevřete složku projektů v jazyce Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 08/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: da81f8731be97c69a73eddb96e9e56e49c59c91b
ms.sourcegitcommit: 1b480aa74886930b3bd0435d71cfcc3ccda36424
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="open-folder-projects-in-visual-c"></a>Otevřete složku projektů v jazyce Visual C++
Visual Studio 2017 zavádí funkci "Otevřete složku", která umožňuje otevřete složku zdrojových souborů a okamžitě psaní s podporou pro technologii IntelliSense, procházení, refaktoring, ladění a tak dále. Jsou načteny žádné soubory .sln nebo VCXPROJ; v případě potřeby můžete zadat vlastní úlohy a také sestavení a spuštění parametry prostřednictvím jednoduchého .json soubory. Používá technologii otevřít složku, Visual C++ teď podporuje pouze přijít kolekcí souborů, ale také prakticky jakékoli sestavení systému, včetně CMake, expertem, QMake (pro projekty RT), gyp, SCons, Gradle, Buck, zkontrolujte a další. 

Chcete-li použít otevřít složku, vyberte z hlavní nabídky *souboru | Otevřete | Složka* nebo stiskněte klávesu *Ctrl + Shift + Alt + O*. Průzkumník řešení okamžitě zobrazí všechny soubory ve složce. Kliknutím na libovolný soubor můžete začít s jeho úpravami. Na pozadí Visual Studio spustí indexování soubory, které chcete povolit technologii IntelliSense, navigace a refaktoringu funkce. Jak upravit, vytvořit, přesuňte nebo odstraňte soubory, Visual Studio automaticky sleduje změny a průběžně aktualizuje její IntelliSense index. 
  
## <a name="cmake-projects"></a>CMake projekty
CMake je integrovaný do prostředí Visual Studio IDE jako CMake nástrojů pro Visual C++, součást plochy zatížení C++. Další informace najdete v tématu [CMake nástrojů pro Visual C++](cmake-tools-for-visual-cpp.md).
 
## <a name="qmake-projects-that-target-the-qt-framework"></a>QMake projekty, které používají rozhraní RT
CMake nástroje můžete použít pro Visual C++ cíl RT k sestavení projektů RT nebo můžete použít rozšíření RT Visual Studio. Poznámka: Od srpna 2017 [rozšíření sady Visual Studio RT podpora pro Visual Studio 2017](https://download.qt.io/development_releases/vsaddin/) je k dispozici jako beta verze.

## <a name="gyp-cons-scons-buck-etc"></a>gyp Cons, SCons, Buck atd
Můžete použít libovolný sestavení systém v jazyce Visual C++ a stále přesto využívat výhod Visual C++ IDE a ladicí program. Při otevření kořenové složce projektu Visual C++ pomocí heuristické metody index zdrojové soubory pro funkce IntelliSense a procházení. Úpravou souboru CppProperties.json můžete poskytnout nápovědu, jak struktury vašeho kódu. Podobným způsobem můžete nakonfigurovat úpravou souboru launch.vs.json vašeho programu sestavení. 

## <a name="configuring-open-folder-projects"></a>Konfigurace projektů otevřít složku
Projekt otevřít složku můžete přizpůsobit prostřednictvím tři soubory JSON:
|||
|-|-|
|CppProperties.json|Zadejte informace o vlastní konfigurace pro procházení. Tento soubor vytvořte, v případě potřeby v kořenové složce projektu.|
|Launch.vs.JSON|Zadejte argumenty příkazového řádku. Přístupu prostřednictvím **Průzkumníku řešení** položky kontextové nabídky **ladění a spusťte nastavení**.|
|Tasks.vs.JSON|Zadejte vlastní sestavovací příkazy a přepínače kompilátoru. Přístupu prostřednictvím **Průzkumníku řešení** položky kontextové nabídky **nakonfigurovat úlohy**.|

### <a name="configure-intellisense-with-cpppropertiesjson"></a>Nakonfigurovat CppProperties.json IntelliSense
IntelliSense a procházení chování částečně závisí na konfiguraci active sestavení, který definuje #include cesty, přepínače kompilátoru a další parametry. Ve výchozím nastavení Visual Studio poskytuje konfigurace Debug a Release. U některých projektů musíte vytvořit vlastní konfiguraci, aby plně pochopit kódu technologie IntelliSense a procházení funkce. Pokud chcete definovat novou konfiguraci, vytvořte soubor s názvem CppProperties.json v kořenové složce. Tady je příklad:

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
Konfigurace může mít některý z následujících vlastností:

|||  
|-|-| 
|`name`|Název konfigurace, který se zobrazí v rozevírací nabídce konfigurace C++|
|`includePath`|Seznam složek, které musí být zadán v zahrnout cesty (maps na /I pro většinu kompilátory)|
|`defines`|seznam makra, které by měly být definován (mapy do /D pro většinu kompilátory)|
|`compilerSwitches`|minimálně jeden další přepínače, které mohou mít vliv na chování IntelliSense|
|`forcedInclude`|záhlaví má být automaticky zahrnut v každou jednotku kompilace (mapuje /FI pro MSVC nebo – zahrnout pro clang)|
|`undefines`|seznam makra být definován (mapuje /U pro MSVC)|
|`intelliSenseMode`|modul IntelliSense, který se má použít. Můžete zadat konkrétní variant architektura pro MSVC, RSZ nebo Clang:
- msvc-x86 (výchozí)
- msvc x64
- msvc arm
- Windows-clang-x86
- Windows-clang-x64
- Windows-clang – arm
- Linux x64
- Linux x86
- Linux arm
- gccarm

CppProperties.json podporuje rozšíření proměnné prostředí pro zahrnují cesty a dalších hodnot vlastností. Syntaxe je `${env.FOODIR}` rozbalte proměnné prostředí `%FOODIR%`.

Máte také přístup k následující předdefinované makra uvnitř tohoto souboru:
|||
|-|-|
|`${workspaceRoot}`| Úplná cesta ke složce pracovního prostoru|
|`${projectRoot}`| Úplná cesta ke složce, kde je umístěn CppProperties.json|
|`${vsInstallDir}`| Úplná cesta ke složce, kde je nainstalován spuštěnou instanci VS 2017|

Pokud projekt má zahrnout složku a také zahrnuje odkazující na Windows a dalších běžných hlaviček ze sady Windows SDK, můžete chtít aktualizovat vaši CppProperties.json konfiguračního souboru pomocí těchto zahrnuje:

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

**Poznámka:** `%WindowsSdkDir%` a `%VCToolsInstallDir%` nejsou nastaveny jako globální proměnné, zajistěte, aby spuštění devenv.exe z "Vývojáře příkazového řádku pro VS 2017" definující tyto proměnné.

K řešení potíží s IntelliSense chyby způsobené chybí zahrnout cesty, otevřete **seznam chyb** a její výstup do "Pouze IntelliSense" filtrovat a kód chyby E1696 "nelze otevřít zdrojový soubor...". 

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
### <a name="define-tasks-with-tasksvsjson"></a>Definování úloh s tasks.vs.json
Je možné automatizovat skripty sestavení nebo jiné externí operace se soubory, které máte v aktuálním pracovním prostoru spuštěním jako úlohy přímo v prostředí IDE. Novou úlohu můžete nakonfigurovat tak, že kliknete pravým tlačítkem na soubor nebo složku a výběr **nakonfigurovat úlohy**. 

![Otevřít složku konfigurovat úlohy](media/open-folder-config-tasks.png)

To vytvoří (nebo otevře) `tasks.vs.json` soubor ve složce neodstraňujte, která sada Visual Studio vytvoří v kořenové složce projektu. Můžete definovat všechny libovolné úlohy v tomto souboru a potom vyvolat z **Průzkumníku řešení** kontextové nabídky. Následující příklad ukazuje soubor tasks.vs.json, který definuje jednu úlohu. `taskName`Definuje název, který se zobrazí v místní nabídce. `appliesTo`Definuje soubory, které lze provést příkaz na. `command` Vlastnost odkazuje na proměnné prostředí COMSPEC, které identifikuje cestu pro konzolu (cmd.exe v systému Windows). `args` Vlastnost určuje příkazový řádek, který má být volána. `${file}` Makro načte vybraného souboru v **Průzkumníku řešení**. V následujícím příkladu se zobrazí název souboru aktuálně vybraného souboru.

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
Po uložení tasks.vs.json, klikněte pravým tlačítkem na libovolný soubor sada ve složce, vyberte **Echo filename** z kontextové nabídky a zjistit, na které se zobrazí název souboru v okně výstupu.

#### <a name="appliesto"></a>AppliesTo –
Můžete vytvořit úlohy pro libovolný soubor nebo složku a to zadáním názvu v `appliesTo` pole, například `"appliesTo" : "hello.cpp"`. Následující masek souboru můžete použít jako hodnoty:
|||
|-|-|
|`"*"`| Úloha je k dispozici pro všechny soubory a složky v pracovním prostoru|
|`"*/"`| Úloha je k dispozici pro všechny složky v pracovním prostoru|
|`"*.cpp"`| Úloha je k dispozici pro všechny soubory s příponou sada v pracovním prostoru|
|`"/*.cpp"`| Úloha je k dispozici pro všechny soubory s příponou sada v kořenu pracovního prostoru|
|`"src/*/"`| Úloha je k dispozici pro všechny podsložky složky "src"|
|`"makefile"`| Úloha je k dispozici pro všechny soubory souboru pravidel v pracovním prostoru|
|`"/makefile"`| Úloha je k dispozici pouze v souboru pravidel v kořenu pracovního prostoru|

#### <a name="output"></a>výstup
Použití `output` vlastnosti k určení spustitelného souboru, který se spustí po stisknutí klávesy **F5**. Příklad:

```json
      "output": "${workspaceRoot}\\bin\\hellomake.exe" 
```

#### <a name="macros-for-tasksvsjson"></a>Makra pro tasks.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Určuje všechny proměnné prostředí (například ${env. CESTA}, ${env.COMSPEC} a tak dále), je nastaven pro příkazový řádek vývojáře. Další informace najdete v tématu [příkazový řádek vývojáře pro sadu Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Úplná cesta ke složce prostoru (například "C:\sources\hello")|
|`${file}`| Úplná cesta k souboru nebo složky, které chcete spustit tuto úlohu (například "C:\sources\hello\src\hello.cpp")|
|`${relativeFile}`| relativní cesta k souboru nebo složky (například "src\hello.cpp")|
|`${fileBasename}`| Název souboru bez cesty nebo rozšíření (například "hello")|
|`${fileDirname}`| Úplná cesta k souboru, s výjimkou název souboru (například "C:\sources\hello\src")|
|`${fileExtname}`| rozšíření vybraný soubor (například "")|

#### <a name="custom-macros"></a>Vlastní makra
K definování vlastní makro v tasks.vs.json, přidáte dvojici název: hodnota před bloky úloh. V následujícím příkladu definuje makro s názvem `outDir` které se využívá v `args` vlastnost:

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

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Konfigurace ladění parametrů s launch.vs.json
Chcete-li přizpůsobit vašeho programu argumenty příkazového řádku, klikněte pravým tlačítkem na spustitelný soubor **Průzkumníku řešení** a vyberte **ladění a spusťte nastavení**. Tím se otevře existující `launch.vs.json` souboru, nebo pokud žádný neexistuje, vytvoří nový soubor naplněna informacemi o programu, který jste vybrali. 

Pokud chcete zadat další argumenty, stačí přidat je do `args` pole JSON, jak je znázorněno v následujícím příkladu:

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

Při ukládání tohoto souboru, nová konfigurace se zobrazí v rozevírací nabídce ladění cíl a můžete vybrat tak, aby ladicí program. Můžete vytvářet konfigurace mnoho ladění, jak se vám líbí, pro libovolný počet spustitelné soubory. Pokud vyberete **F5** nyní bude ladicí program spustit a stiskněte tlačítko žádné zarážek mohou být již nastavena. Všechny známé ladicího programu a jejich funkce jsou nyní k dispozici.

## <a name="see-also"></a>Viz také
[IDE a nástrojů pro vývoj Visual C++](ide-and-tools-for-visual-cpp-development.md)

