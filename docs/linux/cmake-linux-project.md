---
title: Vytvoření a konfigurace projektu Linux CMake v sadě Visual Studio
description: Jak vytvořit, nakonfigurovat, upravit a zkompilovat projekt Linux CMake v sadě Visual Studio
ms.date: 10/04/2019
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 63c1f7953682e4d491660a18bedfa3d0ca4305ae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364392"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>Vytvoření a konfigurace projektu Linux CMake

::: moniker range="vs-2015"

Podpora Linuxu je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

::: moniker range="vs-2019"

Vytvoření nového projektu Linux CMake ve Visual Studiu 2019:

1. Vyberte **Soubor > Nový projekt** v sadě Visual Studio nebo stiskněte **kombinaci kláves Ctrl + Shift + N**.
1. Nastavte **jazyk** na **C++** a vyhledejte "CMake". Pak zvolte **Další**. Zadejte **název** a **umístění**a zvolte **Vytvořit**.

Visual Studio vytvoří minimální soubor CMakeLists.txt pouze s názvem spustitelného souboru a minimální požadovanou verzí CMake. Tento soubor můžete ručně upravit, jak chcete; Visual Studio nikdy přepsat změny. Argumenty příkazového řádku CMake a proměnné prostředí můžete zadat tak, že v **Průzkumníku řešení** kliknete pravým tlačítkem myši na kořenový soubor CMakeLists.txt a zvolíte **nastavení CMake pro projekt**. Chcete-li určit možnosti ladění, klepněte pravým tlačítkem myši na uzel projektu a zvolte **Ladění a nastavení spuštění**.

::: moniker-end

Když otevřete složku, která obsahuje existující projekt CMake, Visual Studio používá proměnné v mezipaměti CMake ke konfiguraci technologie IntelliSense a automaticky se staví. Místní nastavení konfigurace a ladění jsou uloženy v souborech JSON, které lze volitelně sdílet s ostatními uživateli sady Visual Studio.

Visual Studio nezmění soubory CMakeLists.txt, takže ostatní pracující na stejném projektu mohou nadále používat jakékoli nástroje, které již používají. Visual Studio regenerate mezipaměti při ukládání úprav cMakeLists.txt nebo v některých případech CMakeSettings.json. Ale pokud používáte **existující konfigurace mezipaměti,** pak Visual Studio nezmění mezipaměť.

Obecné informace o podpoře CMake v sadě Visual Studio naleznete v tématu [CMake projekty v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md). Přečtěte si, že první před pokračováním zde.

## <a name="before-you-begin"></a>Než začnete

Nejprve se ujistěte, že máte nainstalovaný **vývoj Linuxu s úlohami C++,** včetně komponenty CMake. Viz [Instalace zatížení C++ Linuxu ve Visual Studiu](download-install-and-setup-the-linux-development-workload.md).

V systému Linux zkontrolujte, zda jsou nainstalovány následující:

- Gcc
- Gdb
- Rsync
- Zip
- ninja-stavět

::: moniker range="vs-2019"

Linux podpora pro projekty CMake vyžaduje nejnovější verzi CMake, které mají být nainstalovány na cílovém počítači. Verze nabízená správcem výchozího balíčku distribuce často není dostatečně aktuální, aby podporovala všechny funkce, které visual studio vyžaduje. Visual Studio 2019 zjistí, jestli je v systému Linux nainstalovaná nejnovější verze CMake. Pokud není žádný nalezen, Visual Studio zobrazí informační panel v horní části podokna [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases)editoru, který nabízí k instalaci z aplikace .

Podpora CMake v sadě Visual Studio vyžaduje podporu režimu serveru, která byla zavedena v CMake 3.8. V sadě Visual Studio 2019 verze 3.14 nebo novější se doporučuje.

::: moniker-end

::: moniker range="vs-2017"

Podpora CMake v sadě Visual Studio vyžaduje podporu režimu serveru, která byla zavedena v CMake 3.8. Pro variantu CMake poskytovanou společností Microsoft [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases)stáhněte nejnovější předdefinované binární soubory na adrese .

Binární soubory budou nainstalovány do aplikace `~/.vs/cmake`. Po nasazení binárních souborů se projekt automaticky znovu vygeneruje. Všimněte si, že pokud `cmakeExecutable` CMake zadané pole v `CMakeSettings.json` je neplatná (neexistuje nebo je nepodporovaná verze) `cmakeExecutable` a předem sestavené binární soubory jsou k dispozici Visual Studio bude ignorovat a používat předem sestavené binární soubory.

:::moniker-end

## <a name="open-a-folder"></a>Otevření složky

Chcete-li začít, zvolte Otevřít**Open** > **složku souboru** **File** > z hlavní nabídky nebo na příkazovém řádku. `devenv.exe <foldername>` Složka, kterou otevřete, by měla mít v ruce soubor CMakeLists.txt spolu se zdrojovým kódem.
Následující příklad ukazuje jednoduchý soubor CMakeLists.txt a cpp:

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

Soubor CMakeLists.txt:

```cmd
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Vyberte si cíl Linuxu

Jakmile složku otevřete, aplikace Visual Studio analyzuje soubor CMakeLists.txt a určuje cíl systému Windows **x86-Debug**. Chcete-li cílit na vzdálený systém Linux, změňte nastavení projektu na **Linux-Debug** nebo **Linux-Release**. (Viz [Konfigurace nastavení CMake pro Linux](#configure_cmake_linux) níže.)

::: moniker range="vs-2019"

Chcete-li cílit na podsystém Windows pro Linux, klikněte na **spravovat konfigurace** v rozbalovací nabídce konfigurace na hlavním panelu nástrojů. Pak stiskněte tlačítko **Přidat konfiguraci** a zvolte **WSL-Debug** nebo **WSL-Release,** pokud používáte GCC, nebo varianty Clang, pokud používáte sadu nástrojů Clang/LLVM.

**Visual Studio 2019 verze 16.1** Při cílení wsl, žádné kopírování zdrojů nebo záhlaví je nutné, protože kompilátor na Linuxu má přímý přístup k systému souborů Windows, kde jsou umístěny zdrojové soubory. (V systému Windows verze 1903 a novější, aplikace systému Windows také přístup k souborům záhlaví Linux přímo, ale Visual Studio ještě nevyužívá této funkce).

::: moniker-end

Pro vzdálené cíle visual studio ve výchozím nastavení vybere první vzdálený systém v seznamu v části **Nástroje** > **možnosti** > **cross Platform** > **Connection Manager**. Pokud nejsou nalezena žádná vzdálená připojení, budete vyzváni k jeho vytvoření. Další informace naleznete [v tématu Připojení ke vzdálenému počítači s Linuxem](connect-to-your-remote-linux-computer.md).

Pokud zadáte vzdálený cíl Linuxu, zdroj se zkopíruje do vzdáleného systému.

Po výběru cíle cmake spustí automaticky v systému Linux generovat CMake mezipaměti pro váš projekt.

![Generování mezipaměti CMake na Linuxu](media/cmake-linux-1.png "Generovat mezipaměť CMake na Linuxu")

Chcete-li poskytnout podporu IntelliSense pro záhlaví ve vzdálených systémech Linux, Visual Studio je automaticky zkopíruje z počítače s Linuxem do adresáře v místním počítači se systémem Windows. Další informace naleznete [v tématu IntelliSense pro vzdálená záhlaví](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-cmake-project"></a><a name="debug_cmake_project"></a>Ladění projektu CMake

Chcete-li ladit kód v zadaném cílovém systému ladění, nastavte zarážku, vyberte cíl CMake jako položku po spuštění v nabídce panelu nástrojů vedle nastavení projektu a zvolte **&#x23f5; Start** na panelu nástrojů nebo stiskněte klávesu F5.

Chcete-li přizpůsobit argumenty příkazového řádku programu, stiskněte tlačítko **Přepnout cíle** v horní části **Průzkumníka řešení** a pak zvolte **Zobrazení cílů**. Pak klikněte pravým tlačítkem myši na cíl a vyberte **nastavení ladění a spuštění**. Tím se otevře nebo vytvoří konfigurační soubor launch.vs.json, který obsahuje informace o programu. Chcete-li určit umístění zdrojových souborů, přidejte do souboru vlastnost **sourceFileMap,** jak je znázorněno v tomto příkladu:

```json
"MIMode": "gdb",
"externalConsole": true,
"sourceFileMap": {
"c/Users/USER/source/repos/CMAKEPROJECTNAME": "C:\\Users\\USER\\source\\repos\\CMAKEPROJECTNAME"
},
"remoteMachineName": "${debugInfo.remoteMachineName}",
```

Chcete-li zadat další argumenty, přidejte je do `args` pole JSON. Další informace naleznete v [tématech Otevřít projekty složek pro relace ladění jazyka C++](../build/open-folder-projects-cpp.md) a [Konfigurovat ladění CMake](../build/configure-cmake-debugging-sessions.md).

## <a name="configure-cmake-settings-for-linux"></a><a name="configure_cmake_linux"></a>Konfigurace nastavení CMake pro Linux

Soubor CMakeSettings.json v projektu CMake Linux můžete zadat všechny vlastnosti uvedené v [přizpůsobit nastavení CMake](../build/customize-cmake-settings.md), plus další vlastnosti, které řídí nastavení sestavení na vzdáleném počítači SIF.

::: moniker range="vs-2019"

Chcete-li změnit výchozí nastavení CMake v sadě Visual Studio 2019, otevřete na hlavním panelu nástrojů rozevírací panel **Konfigurace** a zvolte **Spravovat konfigurace**.

![CMake spravovat konfigurace](../build/media/vs2019-cmake-manage-configurations.png "Rozevírací položky konfigurace CMake")

Tím se vyvolá **Editor nastavení CMake,** který `CMakeSettings.json` můžete použít k úpravě souboru v kořenové složce projektu. Soubor můžete také otevřít přímo klepnutím na tlačítko **Upravit JSON** v editoru. Další informace naleznete v [tématu Customize CMake Settings](../build/customize-cmake-settings.md).

::: moniker-end

::: moniker range="vs-2017"

Chcete-li změnit výchozí nastavení CMake ve Visual Studiu 2017, zvolte **CMake | Změnit nastavení CMake | Soubor CMakeLists.txt** z hlavní nabídky nebo klepněte pravým tlačítkem myši na soubor CMakeSettings.txt v **Průzkumníku řešení** a zvolte **Změnit nastavení cmake**. Visual Studio pak `CMakeSettings.json` vytvoří nový soubor ve složce kořenového projektu. Soubor můžete otevřít pomocí editoru **CMake Settings** nebo soubor přímo upravit. Další informace naleznete v [tématu Customize CMake settings](../build/customize-cmake-settings.md).

Následující příklad ukazuje výchozí konfiguraci pro Linux-Debug v Sadě Visual Studio 2017 (a Visual Studio 2019 verze 16.0) na základě předchozího příkladu kódu:

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "remoteMachineName": "${defaultRemoteMachineName}",
      "configurationType": "Debug",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteInstallRoot": "/var/tmp/build/${workspaceHash}/install/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "remoteCopySourcesMethod": "rsync",
      "remoteCopySourcesExclusionList": [".vs", ".git"],
      "rsyncCommandArgs" : "-t --delete --delete-excluded",
      "remoteCopyBuildOutput" : "false",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```

::: moniker-end

::: moniker range="vs-2019"

Výchozí konfigurace Linux-Debug ve Visual Studiu 2019 verze 16.1 a novější je, jak je znázorněno zde:

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "configurationType": "Debug",
      "cmakeExecutable": "/usr/bin/cmake",
      "remoteCopySourcesExclusionList": [ ".vs", ".git", "out" ],
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_x64" ],
      "remoteMachineName": "${defaultRemoteMachineName}",
      "remoteCMakeListsRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/src",
      "remoteBuildRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/build/${name}",
      "remoteInstallRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/install/${name}",
      "remoteCopySources": true,
      "rsyncCommandArgs": "-t --delete --delete-excluded",
      "remoteCopyBuildOutput": false,
      "remoteCopySourcesMethod": "rsync",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    }
  ]
}
```

::: moniker-end

Další informace o těchto nastaveních naleznete v [tématu CMakeSettings.json reference](../build/cmakesettings-reference.md).

## <a name="optional-settings"></a>Volitelná nastavení

Pro větší kontrolu můžete použít následující volitelná nastavení:

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

Tyto možnosti umožňují spouštět příkazy v systému Linux před a po sestavení a před generováním CMake. Hodnoty mohou být libovolný příkaz, který je platný ve vzdáleném systému. Výstup je odváděn zpět do sady Visual Studio.

## <a name="see-also"></a>Viz také

[Práce s vlastnostmi projektu](../build/working-with-project-properties.md)<br/>
[CMake projekty v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
[Připojení ke vzdálenému počítači s Linuxem](connect-to-your-remote-linux-computer.md)<br/>
[Přizpůsobení nastavení CMake](../build/customize-cmake-settings.md)<br/>
[Konfigurace ladicích relací CMake](../build/configure-cmake-debugging-sessions.md)<br/>
[Nasazení, spuštění a ladění projektu Linux](deploy-run-and-debug-your-linux-project.md)<br/>
[CMake předdefinovaný odkaz na konfiguraci](../build/cmake-predefined-configuration-reference.md)<br/>
