---
title: Podpora otevírání složek pro systémy sestavení C++ v sadě Visual Studio
ms.date: 03/21/2019
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 380a96bcb1a119b2b6d4104d60936217d1350fbb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59237130"
---
# <a name="open-folder-projects-for-c"></a>Otevřete složku projekty jazyka C++

V sadě Visual Studio 2017 nebo novější umožňuje funkce "Otevřít složku" Otevřít složku zdrojových souborů a okamžitě začněte programovat s podporou technologie IntelliSense, procházení, refaktoring, ladění, a tak dále. Jsou načteny žádné soubory .sln nebo .vcxproj; v případě potřeby můžete zadat vlastní úkoly a sestavujte a uvádějte parametry v souborech .json jednoduché. Obecné informace o otevřít složku najdete v tématu [vývoj kódu v sadě Visual Studio bez projektů nebo řešení](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

CMake je integrovaná v integrovaném vývojovém prostředí sady Visual Studio jako nástroje CMake pro Visual Studio, součást sady funkcí klasické pracovní plochy jazyka C++. Další informace najdete v tématu [projekty CMake v sadě Visual Studio](cmake-projects-in-visual-studio.md). Pro jiné systém sestavení můžete použít funkce Otevřít složku. Otevřít složku efektivně odděluje editor kódu, ladicí program a analyzátorů od systém sestavení a sady nástrojů kompilátoru. Můžete použít editor kódu jazyka C++ s jeho bohaté funkce IntelliSense, analyzátorů kódu a ladicí program sady Visual Studio s prakticky jakýmkoliv systémem sestavení, včetně CMake, Ninja, QMake (pro projekty Qt), gyp, SCons, Gradle, Buck, zkontrolujte a dalších. Funguje i s jeden soubor nebo dojde ke ztrátě kolekce souborů bez systému sestavení.

Použití funkce Otevřít složku v hlavní nabídce vyberte **soubor | Otevřít | Složka** nebo stiskněte klávesu **Ctrl + Shift + Alt + O**. Průzkumník řešení okamžitě zobrazí všechny soubory ve složce. Můžete kliknout na jakýkoli soubor můžete začít s jeho úpravami. Na pozadí spustí aplikace Visual Studio indexování soubory, které chcete povolit technologii IntelliSense, navigace a funkcí refaktoringu. Úpravy, vytváření, přesunout a odstranit soubory, Visual Studio automaticky sleduje změny a průběžně aktualizuje jeho index IntelliSense. 

## <a name="qmake-projects-that-target-the-qt-framework"></a>QMake projekty, které cílí rozhraní framework Qt

Nástroje CMake pro Visual Studio můžete použít k cílení Qt k sestavení projektů Qt, nebo můžete použít [rozšíření sady Visual Studio Qt](https://download.qt.io/development_releases/vsaddin/) pro Visual Studio 2015 nebo Visual Studio 2017.

## <a name="gyp-cons-scons-buck-etc"></a>gyp nevýhody SCons, Buck, atd.

Můžete použít libovolný systém sestavení v sadě Visual Studio a přesto využívat výhod integrovaného vývojového prostředí jazyka C++ a ladicí program. Při otevření kořenové složce vašeho projektu, editor kódu jazyka C++ používá heuristiky indexování zdrojové soubory pro IntelliSense a procházení. Úpravou souboru CppProperties.json může poskytnout nápovědu, konstrukce kódu. Podobným způsobem můžete nakonfigurovat a volat programu sestavení pomocí úpravy souboru launch.vs.json.

## <a name="configuring-open-folder-projects"></a>Konfigurace projektů otevřít složku

Projekt otevřít složku můžete přizpůsobit prostřednictvím tři soubory JSON:

| | |
|-|-|
|CppProperties.json|Zadejte vlastní konfigurační informace pro procházení. Vytvořte tento soubor v případě potřeby v kořenové složce projektu. (Nelze použít v projektech CMake.)|
|tasks.vs.json|Zadejte vlastní sestavení příkazy a přepínače kompilátoru. Přístup přes **Průzkumníka řešení** položka kontextové nabídky **nakonfigurovat úlohy**.|
|launch.vs.json|Zadejte argumenty příkazového řádku pro ladicí program. Přístup přes **Průzkumníka řešení** položka kontextové nabídky **nastavení ladění a spouštění**.|

### <a name="configure-intellisense-and-browsing-hints-with-cpppropertiesjson"></a>Konfigurace technologie IntelliSense a procházení pomocné parametry s CppProperties.json

Technologie IntelliSense a procházení chování částečně závisí na konfiguraci aktivních sestavení, která definuje #include cesty, přepínače kompilátoru a další parametry. Visual Studio poskytuje ve výchozím nastavení, konfigurace Debug a Release. Projekty CMake pomocí souboru CMakeSettings.json a soubor CMakeLists.txt souborů pro tento účel. Pro jiné typy projektů, otevřete složku budete muset vytvořit vlastní konfiguraci, aby IntelliSense a procházení funkce plně pochopit kód. Pokud chcete definovat novou konfiguraci, vytvořte soubor s názvem CppProperties.json v kořenové složce. Tady je příklad:

```json
{
  "configurations": [
    {
      "name": "Windows x64",
      "includePath": [ "include" ],
      "defines": [ "_DEBUG" ],
      "compilerSwitches": "/std:c++17",
      "intelliSenseMode": "windows-msvc-x64",
      "forcedInclude": [ "pch.h" ],
      "undefines": []
    }
  ]
}
```
Další informace najdete v tématu [referenční dokumentace schématu CppProperties](cppproperties-schema-reference.md).

### <a name="define-build-tasks-with-tasksvsjson"></a>Definovat úkoly sestavení pomocí tasks.vs.json

Můžete automatizovat skripty sestavení ani žádné jiné externí operace se soubory, které máte v aktuálním pracovním prostoru spuštěním jako úlohy přímo v integrovaném vývojovém prostředí. Vytvoření nového úkolu můžete nakonfigurovat tak, že kliknete pravým tlačítkem na soubor nebo složku a vyberete **nakonfigurovat úlohy**.

![Konfigurace funkce Otevřít složku úloh](media/open-folder-config-tasks.png)

To vytvoří (nebo se otevře) **tasks.vs.json** souboru ve složce .vs, který sada Visual Studio vytvoří v kořenové složce projektu. Můžete definovat všechny libovolné úlohy v tomto souboru a poté vyvolat z **Průzkumníka řešení** kontextové nabídky. Následující příklad ukazuje tasks.vs.json soubor, který definuje jeden úkol. `taskName` Definuje název, který se zobrazí v místní nabídce. `appliesTo` Definuje soubory, které lze příkaz provést na. `command` Vlastnost odkazuje na proměnnou prostředí COMSPEC, který určuje cestu pro konzolu (cmd.exe ve Windows). Můžete také odkazovat na proměnné prostředí, které jsou deklarovány v CppProperties.json a CMakeSettings.json. `args` Určuje vlastnosti příkazového řádku, který má být volána. `${file}` Makra obnoví na vybraný soubor na **Průzkumníka řešení**. V následujícím příkladu se zobrazí název souboru aktuálně vybraného .cpp.

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

Další informace najdete v tématu [referenční dokumentace schématu Tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Konfigurace ladění parametrů pomocí launch.vs.json

Přizpůsobení vašeho programu argumenty příkazového řádku, klikněte pravým tlačítkem na spustitelný soubor **Průzkumníka řešení** a vyberte **nastavení ladění a spouštění**. Tím otevřete existující **souboru launch.vs.json** souboru, nebo pokud žádný neexistuje, vytvoří nový soubor naplněna informacemi o programu, který jste vybrali.

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
