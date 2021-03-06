---
title: Podpora otevření složky pro systémy sestavení C++ v aplikaci Visual Studio
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
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>Podpora otevření složky pro systémy sestavení C++ v aplikaci Visual Studio

::: moniker range="vs-2015"

Funkce otevřít složku je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

V aplikaci Visual Studio 2017 a novější funkce "otevřená složka" umožňuje otevřít složku zdrojových souborů a okamžitě spustit kódování s podporou technologie IntelliSense, procházení, refaktoringu, ladění atd. Při úpravách, vytváření, přesouvání nebo odstraňování souborů aplikace Visual Studio automaticky sleduje změny a průběžně aktualizuje její index IntelliSense. Nejsou načteny žádné soubory. sln nebo. vcxproj. v případě potřeby můžete zadat vlastní úlohy a parametry sestavení a spuštění prostřednictvím jednoduchých souborů. JSON. Tato funkce umožňuje integrovat libovolný systém sestavení třetí strany do sady Visual Studio. Obecné informace o otevřené složce naleznete v tématu [vývoj kódu v aplikaci Visual Studio bez projektů nebo řešení](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

## <a name="cmake-and-qt"></a>CMake a QT

CMake je integrovaná do integrovaného vývojového prostředí (IDE) sady Visual Studio jako součást úlohy C++ pro stolní počítače. Pracovní postup pro CMake není totožný s pracovním postupem popsaným v tomto článku. Pokud používáte CMake, přečtěte si téma [projekty cmake v sadě Visual Studio](cmake-projects-in-visual-studio.md). CMake můžete použít také k sestavení projektů QT nebo můžete použít [rozšíření QT sady Visual Studio](https://download.qt.io/development_releases/vsaddin/) pro sadu visual Studio 2015 nebo visual Studio 2017.

## <a name="other-build-systems"></a>Další systémy sestavení

Použití integrovaného vývojového prostředí sady Visual Studio se systémem sestavení nebo sadou nástrojů kompilátoru, která není přímo podporována v hlavní nabídce vyberte **soubor | Otevřít | Nebo stiskněte** **kombinaci kláves CTRL + SHIFT + ALT + O**. Přejděte do složky, která obsahuje soubory zdrojového kódu. Chcete-li sestavit projekt, nakonfigurujte technologii IntelliSense a nastavte parametry ladění, přidejte tři soubory JSON:

| | |
|-|-|
|CppProperties. JSON|Zadejte vlastní informace o konfiguraci pro procházení. V případě potřeby vytvořte tento soubor do kořenové složky projektu. (Nepoužívá se v projektech CMake.)|
|Tasks. vs. JSON|Zadejte vlastní příkazy sestavení. K dispozici prostřednictvím položky místní nabídky **Průzkumník řešení** **nakonfigurovat úlohy**.|
|Launch. vs. JSON|Zadejte argumenty příkazového řádku pro ladicí program. K dispozici prostřednictvím položky kontextové nabídky **Průzkumník řešení** **ladění a spouštění**.|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>Konfigurace navigace v kódu pomocí CppProperties. JSON

Pro technologii IntelliSense a chování při procházení, jako je například **Přejít k definici** , aby fungovala správně, musí Visual Studio znát, který kompilátor používáte, kde jsou systémové hlavičky a kde jsou umístěny další vložené soubory, pokud nejsou přímo ve složce, kterou jste otevřeli (složka pracovního prostoru). Chcete-li zadat konfiguraci, můžete zvolit možnost **spravovat konfigurace** z rozevíracího seznamu na hlavním panelu nástrojů:

![Rozevírací seznam pro správu konfigurací](media/manage-configurations-dropdown.png)

Visual Studio nabízí následující výchozí konfigurace:

![Výchozí konfigurace](media/default-configurations.png)

Pokud například zvolíte **x64-Debug**, Visual Studio vytvoří soubor s názvem *CppProperties. JSON* ve složce kořenového projektu:

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

Tato konfigurace dědí proměnné prostředí Developer Command Prompt sady Visual Studio [x64](building-on-the-command-line.md). Jedna z těchto proměnných je `INCLUDE` a můžete na ni odkazovat pomocí `${env.INCLUDE}` makra. `includePath` Vlastnost oznamuje aplikaci Visual Studio, kde hledat všechny zdroje, které IT potřebují pro technologii IntelliSense. V tomto případě říká "hledání ve všech adresářích určených proměnnou prostředí INCLUDE" a také všechny adresáře ve stromu aktuální pracovní složky. " `name` Vlastnost je název, který se zobrazí v rozevíracím seznamu, a může to být cokoli, co chcete. `defines` Vlastnost poskytuje nápovědu pro technologii IntelliSense při výskytu podmíněných kompilačních bloků. `intelliSenseMode` Vlastnost poskytuje další tipy na základě typu kompilátoru. K dispozici je několik možností pro MSVC, RSZ a Clang.

> [!NOTE]
> Pokud se zdá, že Visual Studio bude ignorovat nastavení v souboru *CppProperties. JSON*, zkuste přidat výjimku do souboru *. gitignore* takto: `!/CppProperties.json`.

## <a name="default-configuration-for-mingw-w64"></a>Výchozí konfigurace pro MinGW-W64

Pokud přidáte konfiguraci MinGW-W64, vyhledá JSON tento kód:

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

Poznamenejte `environments` si blok. Definuje vlastnosti, které se chovají jako proměnné prostředí a jsou k dispozici nejen v souboru *CppProperties. JSON* , ale také v ostatních konfiguračních souborech *Task. vs. JSON* a *Launch. vs. JSON*. `Mingw64` Konfigurace `mingw_w64` dědí prostředí a používá jeho `INCLUDE` vlastnost k určení hodnoty pro `includePath`. Podle potřeby můžete přidat další cesty k této vlastnosti pole.

`intelliSenseMode` Vlastnost je nastavena na hodnotu VHODNOU pro RSZ. Další informace o všech těchto vlastnostech naleznete v tématu [CppProperties Schema Reference](cppproperties-schema-reference.md).

Pokud vše funguje správně, uvidíte IntelliSense z hlaviček RSZ při najetí myší na typ:

![Funkce RSZ IntelliSense](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>Povolit diagnostiku IntelliSense

Pokud se vám technologie IntelliSense, kterou**Text Editor** > **C/C++** > jste očekávali, nezobrazuje, můžete řešit problémy tak, že v **nabídce nástroje** > zvolíte**možnost** > **Upřesnit** a nastavení **Povolit protokolování** na **hodnotu true**. Pokud chcete začít, zkuste nastavit **úroveň protokolování** na 5 a **filtry protokolování** na 8.

![Protokolování diagnostiky](media/diagnostic-logging.png)

Výstup se přesměruje do **okno výstup** a zobrazí se, když vyberete **Zobrazit výstup z: Visual C++ protokol*. Výstup obsahuje mimo jiné seznam skutečných cest, které IntelliSense pokouší použít. Pokud cesty se neshodují s těmi v *CppProperties. JSON*, zkuste zavřít složku a odstranit podsložku *. vs* , která obsahuje data procházení v mezipaměti.

### <a name="define-build-tasks-with-tasksvsjson"></a>Definování úloh sestavení pomocí Tasks. vs. JSON

Můžete automatizovat skripty sestavení nebo jiné externí operace se soubory, které máte v aktuálním pracovním prostoru, a to tak, že je spustíte jako úkoly přímo v integrovaném vývojovém prostředí. Novou úlohu můžete nakonfigurovat tak, že kliknete pravým tlačítkem na soubor nebo složku a vyberete **Konfigurovat úlohy**.

![Otevřít složku konfigurovat úlohy](media/configure-tasks.png)

Tím se vytvoří (nebo otevře) soubor *Tasks. vs. JSON* ve složce. vs, kterou sada Visual Studio vytvoří v kořenové složce projektu. V tomto souboru můžete definovat libovolný úkol a potom ho vyvolat z kontextové nabídky **Průzkumník řešení** . Pokud chcete pokračovat v příkladu RSZ, následující fragment kódu ukazuje kompletní *úlohy. soubor. JSON* s jako jeden úkol, který vyvolá soubor *g + +. exe* pro sestavení projektu. Předpokládat, že projekt obsahuje jeden soubor s názvem *Hello. cpp*.

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

Soubor JSON se umístí do podsložky *. vs* . Chcete-li zobrazit složku, klikněte na tlačítko **Zobrazit všechny soubory** v horní části **Průzkumník řešení**. Tuto úlohu můžete spustit tak, že kliknete pravým tlačítkem na kořenový uzel v **Průzkumník řešení** a zvolíte **sestavení Hello**. Až se úloha dokončí, měl by se zobrazit nový soubor *Hello. exe* v **Průzkumník řešení**.

Můžete definovat mnoho druhů úkolů. Následující příklad ukazuje *soubor Tasks. vs. JSON* , který definuje jeden úkol. `taskLabel`definuje název, který se zobrazí v místní nabídce. `appliesTo`definuje soubory, na kterých lze příkaz provést. `command` Vlastnost odkazuje na PROMĚNNOU prostředí ComSpec, která identifikuje cestu pro konzolu (*cmd. exe* ve Windows). Můžete také odkazovat na proměnné prostředí, které jsou deklarovány v CppProperties. JSON nebo CMakeSettings. JSON. `args` Vlastnost určuje příkazový řádek, který má být vyvolán. `${file}` Makro načte vybraný soubor v **Průzkumník řešení**. Následující příklad zobrazí název souboru aktuálně vybraného souboru. cpp.

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

Po uložení *Tasks. vs. JSON*můžete kliknout pravým tlačítkem na libovolný soubor *. cpp* ve složce, zvolit z kontextové nabídky příkaz **echo filename** a zobrazit název souboru zobrazeného v okně výstup.

Další informace najdete v tématu [Referenční dokumentace schématu Tasks. vs. JSON](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Konfigurace parametrů ladění pomocí Launch. vs. JSON

Pokud chcete přizpůsobit argumenty příkazového řádku programu a pokyny pro ladění, klikněte pravým tlačítkem na spustitelný soubor v **Průzkumník řešení** a vyberte **nastavení ladění a spouštění**. Tím se otevře existující soubor *Launch. vs. JSON* , nebo pokud žádný neexistuje, vytvoří se nový soubor se sadou minimálních nastavení spuštění. Nejdřív máte možnost určit, jaký typ relace ladění chcete nakonfigurovat. Pro ladění projektu MinGw-W64 jsme zvolili **spuštění C/C++ pro MINGW/Cygwin (GDB)**. Tím se vytvoří konfigurace spuštění pro použití *GDB. exe* s některými pedagogy, které se týkají výchozích hodnot. Jedna z těchto výchozích hodnot je `MINGW_PREFIX`. Můžete nahradit literálovou cestu (jak je vidět níže), nebo můžete definovat `MINGW_PREFIX` vlastnost v *CppProperties. JSON*:

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

Chcete-li spustit ladění, zvolte spustitelný soubor v rozevíracím seznamu ladění a pak klikněte na zelenou šipku:

![Spustit ladicí program](media/launch-debugger-gdb.png)

Měl by se zobrazit dialogové okno **inicializace ladicího programu** a pak externí okno konzoly, ve kterém je spuštěný program.

Další informace najdete v referenčních informacích ke [schématu Launch. vs. JSON](launch-vs-schema-reference-cpp.md).

## <a name="launching-other-executables"></a>Spouštění dalších spustitelných souborů

Můžete definovat nastavení spuštění libovolného spustitelného souboru v počítači. Následující příklad spustí *7za* a určí další argumenty jejich přidáním do pole `args` JSON:

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

Při uložení tohoto souboru se nová konfigurace zobrazí v rozevíracím seznamu cíl ladění a můžete ji vybrat ke spuštění ladicího programu. Pro libovolný počet spustitelných souborů můžete vytvořit tolik konfigurací ladění, kolik chcete. Pokud stisknete klávesu **F5** nyní, ladicí program se spustí a zahájí všechny zarážky, které jste už možná nastavili. K dispozici jsou teď všechna známá okna ladicího programu a jejich funkce.

::: moniker-end
