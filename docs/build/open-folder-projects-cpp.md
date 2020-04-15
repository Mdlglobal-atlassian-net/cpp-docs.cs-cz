---
title: Podpora otevřených složek pro systémy sestavení c++ v sadě Visual Studio
ms.date: 12/02/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 9264aa4bf77de406bdde9042ef9ec4251763f721
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320965"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>Podpora otevřených složek pro systémy sestavení c++ v sadě Visual Studio

::: moniker range="vs-2015"

Funkce Otevřít složku je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

::: moniker range=">=vs-2017"

V sadě Visual Studio 2017 a novější chod funkce "Otevřít složku" umožňuje otevřít složku zdrojových souborů a okamžitě začít kódovat s podporou technologie IntelliSense, procházení, refaktoringu, ladění a tak dále. Při úpravách, vytváření, přesouvání nebo odstraňování souborů aplikace Visual Studio automaticky sleduje změny a průběžně aktualizuje svůj index Technologie IntelliSense. Nejsou načteny žádné soubory .sln nebo .vcxproj; V případě potřeby můžete zadat vlastní úkoly, stejně jako parametry sestavení a spuštění prostřednictvím jednoduchých souborů JSON. Tato funkce umožňuje integrovat jakýkoli systém sestavení jiných výrobců do sady Visual Studio. Obecné informace o otevřené složce naleznete [v tématu Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

## <a name="cmake-and-qt"></a>CMake a Qt

CMake je integrován v integrovaném prostředí Visual Studio jako součást úlohy plochy jazyka C++. Pracovní postup pro CMake není totožný s pracovním postupem popsaným v tomto článku. Pokud používáte CMake, najdete [v tématu CMake projekty v sadě Visual Studio](cmake-projects-in-visual-studio.md). Můžete také použít CMake k vytváření projektů Qt nebo můžete použít [rozšíření Qt Visual Studio](https://download.qt.io/development_releases/vsaddin/) pro Visual Studio 2015 nebo Visual Studio 2017.

## <a name="other-build-systems"></a>Ostatní systémy sestavení

Chcete-li použít prostředí IDE sady Visual Studio s nástrojem sestavení nebo nástrojem kompilátoru, který není přímo podporován z hlavní nabídky, vyberte **možnost Soubor | Otevřeno | Složka** nebo stiskněte **kombinaci kláves Ctrl + Shift + Alt + O**. Přejděte do složky, která obsahuje soubory zdrojového kódu. Chcete-li vytvořit projekt, nakonfigurovat technologie IntelliSense a nastavit parametry ladění, přidejte tři soubory JSON:

| | |
|-|-|
|CppProperties.json|Zadejte informace o vlastní konfiguraci pro procházení. V případě potřeby vytvořte tento soubor v kořenové složce projektu. (Nepoužívá se v projektech CMake.)|
|tasks.vs.json|Zadejte vlastní příkazy sestavení. Přístup prostřednictvím položky kontextové nabídky **Průzkumníka řešení** **Konfigurace úloh**.|
|launch.vs.json|Zadejte argumenty příkazového řádku pro ladicí program. Přístup prostřednictvím položky kontextové nabídky **Průzkumníka řešení** **Ladění a Nastavení spuštění**.|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>Konfigurace navigace pomocí kódu CppProperties.json

Pro IntelliSense a procházení chování, jako je **přejít na definici** pracovat správně, Visual Studio potřebuje vědět, který kompilátor používáte, kde jsou systémové hlavičky a kde jsou umístěny všechny další zahrnout soubory, pokud nejsou přímo ve složce, kterou jste otevřeli (složka pracovního prostoru). Chcete-li určit konfiguraci, můžete zvolit **Spravovat konfigurace** z rozevíracího souboru na hlavním panelu nástrojů:

![Rozevírací informace ke správě konfigurací](media/manage-configurations-dropdown.png)

Visual Studio nabízí následující výchozí konfigurace:

![Výchozí konfigurace](media/default-configurations.png)

Pokud například zvolíte **x64-Debug**, Visual Studio vytvoří soubor s názvem *CppProperties.json* v kořenové složce projektu:

```json
{
  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```

Tato konfigurace dědí proměnné prostředí [v příkazovém řádku pro vývojáře](building-on-the-command-line.md)sady Visual Studio x64 . Jedna z těchto `INCLUDE` proměnných je a můžete odkazovat na to zde pomocí `${env.INCLUDE}` makra. Vlastnost `includePath` sděluje Visual Studio, kde hledat všechny zdroje, které potřebuje pro IntelliSense. V tomto případě se říká, že "podívejte se do všech adresářů určených include proměnné prostředí a také všechny adresáře v aktuálním stromu pracovní složky." Vlastnost `name` je název, který se zobrazí v rozbalovací mase a může být cokoli, co se vám líbí. Vlastnost `defines` poskytuje rady pro IntelliSense, když narazí na bloky podmíněné kompilace. Vlastnost `intelliSenseMode` poskytuje některé další rady založené na typu kompilátoru. Pro msvc, gcc a clang je k dispozici několik možností.

> [!NOTE]
> Pokud se zdá, že Visual Studio ignoruje nastavení v *souboru CppProperties.json*, `!/CppProperties.json`zkuste přidat výjimku do souboru *.gitignore* takto: .

## <a name="default-configuration-for-mingw-w64"></a>Výchozí konfigurace pro MinGW-w64

Pokud přidáte konfiguraci MinGW-W64, JSON vypadá takto:

```json
{
  {
      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.BIN_ROOT};${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ]
    }
}
```

Všimněte `environments` si bloku. Definuje vlastnosti, které se chovají jako proměnné prostředí a jsou k dispozici nejen v souboru *CppProperties.json,* ale také v jiných konfiguračních souborech *task.vs.json* a *launch.vs.json*. Konfigurace `Mingw64` dědí `mingw_w64` prostředí a používá `INCLUDE` jeho vlastnost k `includePath`určení hodnoty pro . Podle potřeby můžete do této vlastnosti pole přidat další cesty.

Vlastnost `intelliSenseMode` je nastavena na hodnotu vhodnou pro GCC. Další informace o všech těchto vlastnostech naleznete v tématu [CppProperties odkaz na schéma](cppproperties-schema-reference.md).

Když vše funguje správně, uvidíte IntelliSense ze záhlaví GCC, když najedete na typ:

![GCC IntelliSense](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>Povolení diagnostiky technologie IntelliSense

Pokud nevidíte intelliSense, které očekáváte, můžete řešit problémy s **textem nástroje** > **Options** > **Editor** > **C/C++** > **Upřesnit** a nastavení **Povolit protokolování** na **true**. Chcete-li začít, zkuste nastavit **úroveň protokolování** na 5 a **filtry protokolování** na 8.

![Protokolování diagnostiky](media/diagnostic-logging.png)

Výstup je odváděn do **výstupního okna** a je viditelný, když zvolíte **Zobrazit výstup z: Visual C++ Log*. Výstup obsahuje mimo jiné seznam skutečných cest zahrnutí, které se intelliSense pokouší použít. Pokud cesty neodpovídají cestám v *souboru CppProperties.json*, zkuste složku zavřít a odstranit podsložku *.vs,* která obsahuje data procházení uložené v mezipaměti.

### <a name="define-build-tasks-with-tasksvsjson"></a>Definování úloh sestavení pomocí souboru tasks.vs.json

Můžete automatizovat vytvářet skripty nebo jiné externí operace na soubory, které máte v aktuálním pracovním prostoru spuštěním je jako úlohy přímo v ide. Nový úkol můžete nakonfigurovat tak, že kliknete pravým tlačítkem myši na soubor nebo složku a vyberete **konfigurovat úkoly**.

![Otevřít úlohy konfigurace složky](media/configure-tasks.png)

Tím se vytvoří (nebo otevře) soubor *tasks.vs.json* ve složce .vs, kterou sada Visual Studio vytvoří ve složce kořenového projektu. V tomto souboru můžete definovat libovolnou úlohu a potom ji vyvolat z kontextové nabídky **Průzkumníka řešení.** Chcete-li pokračovat v příkladu GCC, následující úryvek zobrazuje kompletní *soubor tasks.vs.json* s jako jeden úkol, který vyvolá *g ++.exe* k vytvoření projektu. Předpokládejme, že projekt obsahuje jeden soubor s názvem *hello.cpp*.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "build hello",
      "appliesTo": "/",
      "type": "default",
      "command": "g++",
      "args": [
        "-g",
        "-o",
        "hello",
        "hello.cpp"
      ]
    }
  ]
}

```

Soubor JSON je umístěn do podss *.vs.* Chcete-li tuto složku zobrazit, klikněte na tlačítko **Zobrazit všechny soubory** v horní části **Průzkumníka řešení**. Tuto úlohu můžete spustit kliknutím pravým tlačítkem myši na kořenový uzel v **Průzkumníku řešení** a výběrem **možnosti sestavení hello**. Po dokončení úkolu byste měli vidět nový soubor, *hello.exe* v **Průzkumníku řešení**.

Můžete definovat mnoho druhů úkolů. Následující příklad ukazuje *soubor tasks.vs.json,* který definuje jeden úkol. `taskLabel`definuje název, který se zobrazí v místní nabídce. `appliesTo`definuje, ve kterých souborech lze příkaz provádět. Vlastnost `command` odkazuje na proměnnou prostředí COMSPEC, která identifikuje cestu pro konzolu *(cmd.exe* v systému Windows). Můžete také odkazovat na proměnné prostředí, které jsou deklarovány v CppProperties.json nebo CMakeSettings.json. Vlastnost `args` určuje příkazový řádek, který má být vyvolán. Makro `${file}` načte vybraný soubor v **Průzkumníku řešení**. V následujícím příkladu se zobrazí název souboru aktuálně vybraného souboru CPP.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```

Po uložení *souboru tasks.vs.json*můžete klepnout pravým tlačítkem myši na libovolný soubor *CPP* ve složce, z kontextové nabídky zvolit **název souboru Echo** a zobrazit název souboru zobrazený v okně Výstup.

Další informace naleznete v [tématu Tasks.vs.json odkaz na schéma](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Konfigurace parametrů ladění pomocí souboru launch.vs.json

Chcete-li přizpůsobit argumenty příkazového řádku programu a pokyny k ladění, klepněte pravým tlačítkem myši na spustitelný soubor v **Průzkumníku řešení** a vyberte **nastavení ladění a spuštění**. Tím se otevře existující soubor *launch.vs.json,* nebo pokud žádný neexistuje, vytvoří se nový soubor se sadou minimálních nastavení spuštění. Nejprve budete mít na výběr, jaký druh relace ladění, kterou chcete konfigurovat. Pro ladění projektu MinGw-w64 volíme **C/C++ Launch pro MinGW/Cygwin (gdb)**. Tím se vytvoří konfigurace spuštění pro použití *gdb.exe* s některými vzdělanými odhady o výchozích hodnotách. Jednou z těchto `MINGW_PREFIX`výchozích hodnot je . Můžete nahradit literál cestu (jak je znázorněno `MINGW_PREFIX` níže) nebo můžete definovat vlastnost v *CppProperties.json*:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "cppdbg",
      "name": "hello.exe",
      "project": "hello.exe",
      "cwd": "${workspaceRoot}",
      "program": "${debugInfo.target}",
      "MIMode": "gdb",
      "miDebuggerPath": "c:\\msys64\\usr\\bin\\gdb.exe",
      "externalConsole": true
    }
  ]
}

```

Chcete-li začít ladit, zvolte spustitelný soubor v rozevíracím seznamu ladění a klikněte na zelenou šipku:

![Spuštění ladicího programu](media/launch-debugger-gdb.png)

Měli byste vidět **inicializace ladicího programu** dialogové okno a potom externí okno konzoly, která je spuštěna program.

Další informace naleznete v [tématu launch.vs.json odkaz na schéma](launch-vs-schema-reference-cpp.md).

## <a name="launching-other-executables"></a>Spuštění dalších spustitelných souborů

Můžete definovat nastavení spuštění pro libovolný spustitelný soubor v počítači. Následující příklad spustí *7za* a určuje další argumenty jejich `args` přidáním do pole JSON:

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

Když uložíte tento soubor, nová konfigurace se zobrazí v rozevíracím souboru Ladění cíle a můžete ji vybrat a spustit ladicí program. Můžete vytvořit libovolný počet konfigurací ladění pro libovolný počet spustitelných souborů. Pokud stisknete **klávesu F5** nyní, ladicí program se spustí a narazí na všechny zarážky, které jste již nastavili. Všechna známá okna ladicího programu a jejich funkce jsou nyní k dispozici.

::: moniker-end
