---
title: Vytvoření a konfigurace projektu Linux CMake v sadě Visual Studio
description: Vytvoření, konfiguraci, upravit a zkompilovat projektu Linux CMake v sadě Visual Studio
ms.date: 06/12/2019
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: d70ffe593cc014bca40a447a9cdb1c1c96a40e3f
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042661"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>Vytvoření a konfigurace projektu Linux CMake

::: moniker range="vs-2015"

Podpora Linuxu je k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

::: moniker range="vs-2019"

Vytvoření nového projektu Linux CMake v aplikaci Visual Studio 2019:

1. Vyberte **soubor > Nový projekt** v sadě Visual Studio nebo stisknutím klávesy **Ctrl + Shift + N**.
1. Nastavte **jazyk** k **C++** a vyhledejte položku "CMake". Klikněte na tlačítko **Další**. Zadejte **název** a **umístění**a zvolte **vytvořit**.

Visual Studio vytvoří minimální soubor CMakeLists.txt pouze název spustitelného souboru a požadavek na minimální verzi CMake. Tento soubor můžete ručně upravit, ale chcete; Visual Studio nikdy přepíše změny. Můžete zadat argumenty příkazového řádku CMake a proměnných prostředí kliknutím pravým tlačítkem na soubor CMakeLists.txt v **Průzkumníka řešení** a zvolíte **nastavení CMake pro projekt**. Postup určení možností pro ladění, klikněte pravým tlačítkem na uzel projektu a zvolte **nastavení ladění a spouštění**.

::: moniker-end

Když otevřete složku, která obsahuje existující projekt CMake Visual Studio používá metadata, která CMake vytvoří konfigurace technologie IntelliSense a sestavení automaticky. Místní konfigurace a nastavení ladění jsou uloženy v souborech JSON, které lze volitelně sdílet s ostatními uživateli, kteří používají Visual Studio. 

Visual Studio neprovede žádné změny souboru CMakeLists.txt tak, aby uživatelé, kteří pracují na stejném projektu můžete dál používat jakékoli nástroje jsou už používá. Visual Studio znovu do mezipaměti, když provedete úpravy CMakeLists.txt nebo v některých případech do souboru CMakeSettings.json. Ale v případě, že používáte **stávající mezipaměti** konfigurace sady Visual Studio a neprovede žádné změny do mezipaměti.

Obecné informace o podpoře CMake v sadě Visual Studio najdete v tématu [projekty CMake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md). Přečtěte si tento před pokračováním v tomto poli.

## <a name="before-you-begin"></a>Před zahájením

Nejprve zkontrolujte, zda máte **vývoj pro Linux v C++** nainstalovaná, úloha včetně součásti CMake. Zobrazit [, nainstalujte úlohu C++ Linux v sadě Visual Studio](download-install-and-setup-the-linux-development-workload.md). 

V systému Linux Ujistěte se, že tyto jsou nainstalovány: 

- gcc
- gdb
- rsync
- zip 

::: moniker range="vs-2019"

Podpora Linuxu pro projekty CMake vyžaduje nejnovější verzi CMake být nainstalovaný na cílovém počítači. Verze, které správce balíčků vaší distribuce výchozí často, není dostatečně nová, podporu všech funkcí, které jsou vyžadovány sady Visual Studio. Visual Studio 2019 zjistí, zda je nainstalována nejnovější verzi CMake v systému Linux. Pokud se žádný nenajde, Visual Studio zobrazuje indikátor informací v horní části podokna editoru, který nabízí možnost instalace pro vás z [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases).

Podpora CMake v sadě Visual Studio vyžaduje režim podporu serveru, která byla zavedena v CMake 3.8. V aplikaci Visual Studio 2019 se doporučuje verze 3.14 nebo novější.

::: moniker-end

::: moniker range="vs-2017"

Podpora CMake v sadě Visual Studio vyžaduje režim podporu serveru, která byla zavedena v CMake 3.8. Hodnotu typu variant CMake poskytovaný společností Microsoft, stáhněte si nejnovější předem připravených binární soubory na [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases).

Binární soubory se nainstalují pro `~/.vs/cmake`. Po nasazení binárních souborů, bude automaticky obnovit váš projekt. Mějte na paměti, že pokud CMake určené `cmakeExecutable` pole `CMakeSettings.json` je neplatný (neexistuje nebo má nepodporovanou verzi) a předem připravených binární soubory jsou k dispozici sady Visual Studio bude ignorovat `cmakeExecutable` a použijte předem sestavené binární soubory.

:::moniker-end

## <a name="open-a-folder"></a>Otevřít složku

Chcete-li začít, zvolte **souboru** > **otevřít** > **složky** z hlavní nabídky jinak typ `devenv.exe <foldername>` na příkazovém řádku. Otevření složky by měl mít soubor CMakeLists.txt, spolu s zdrojového kódu.
Následující příklad ukazuje jednoduchý soubor CMakeLists.txt a soubor .cpp:

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

CMakeLists.txt:

```cmd
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Volba cíle Linuxu

Jakmile otevřete složku sady Visual Studio analyzuje soubor CMakeLists.txt a určuje cílem Windows **x86 ladění**. Cílit na vzdáleném systému Linux, změnit nastavení projektu a **Linux ladění** nebo **Linux verze**. (Viz [CMake nakonfigurovat nastavení pro Linux](#configure_cmake_linux) níže.)

::: moniker range="vs-2019"

Zacílené subsystém Windows pro Linux, klikněte na **spravovat konfigurace** v v rozevíracím seznamu konfigurací na hlavním panelu nástrojů. Stiskněte klávesu **Přidat konfiguraci** tlačítko a zvolte **WSL ladění** nebo **WSL vydání** Pokud pomocí GCC, Clang varianty nebo pokud se používá sada nástrojů Clang/LLVM. 

**Visual Studio 2019 verze 16.1** při cílení na WSL, je nezbytné bez kopírování ze zdroje nebo záhlaví, protože kompilátor v Linuxu má přímý přístup do systému souborů Windows, kde zdrojové soubory nacházejí. (Ve verzi Windows 1903 a novější, Windows aplikace stejně tak mohou přistupovat k soubory hlaviček Linux přímo, ale Visual Studio ještě nevyužívá této funkce).

::: moniker-end

Pro vzdálené cíle, Visual Studio ve výchozím nastavení vybere první vzdálený systém v seznamu v části **nástroje** > **možnosti** > **různé platformy**  >  **Správce připojení**. Pokud se nenajdou žádné vzdálené připojení, zobrazí se výzva k jejímu vytvoření. Další informace najdete v tématu [připojit ke vzdálenému počítači s Linuxem](connect-to-your-remote-linux-computer.md).

Pokud chcete zadat vzdálený cíl Linux, zdroj je zkopírován do vzdáleného systému.

Po výběru cíle CMake se automaticky spouští v systému Linux ke generování mezipaměti CMake pro váš projekt. 

![Vygenerovat mezipaměť CMake v Linuxu](media/cmake-linux-1.png "vygenerovat mezipaměť CMake v Linuxu")

K zajištění podpory IntelliSense pro záhlaví na vzdálených Linuxových systémů, Visual Studio automaticky zkopíruje z počítače Linux do adresáře na místním počítači Windows. Další informace najdete v tématu [technologie IntelliSense pro vzdálených hlaviček](configure-a-linux-project.md#remote_intellisense).

## <a name="debug_cmake_project"></a> Ladit projekt CMake

Ladění kódu v cílovém systému zadané ladění, nastavte zarážku, vyberte cíl CMake jako položku při spuštění v nabídce nástrojů vedle nastavení projektu a zvolte  **&#x23f5; Start** na panelu nástrojů nebo stisknete klávesu F5.

Chcete-li přizpůsobit váš program argumenty příkazového řádku, stiskněte **přepínač cíle** tlačítko v horní části **Průzkumníka řešení** a klikněte na tlačítko **zobrazení cílů**. Klepněte pravým tlačítkem myši na cílový a vyberte **nastavení ladění a spouštění**. Tím se otevře nebo vytvoří launch.vs.json konfigurační soubor, který obsahuje informace o programu. Pokud chcete zadat další argumenty, přidejte je `args` pole JSON. Další informace najdete v tématu [projekty otevřít složku pro jazyk C++](../build/open-folder-projects-cpp.md) a [konfigurace CMake ladicími relacemi](../build/configure-cmake-debugging-sessions.md).

## <a name="configure_cmake_linux"></a> Konfigurace nastavení CMake pro Linux

V projektu CMake Linux souboru CMakeSettings.json můžete určit všechny vlastnosti, které jsou uvedeny v [nastavení přizpůsobení CMake](../build/customize-cmake-settings.md), plus další vlastnosti, které řídí nastavení sestavení na vzdáleném počítači s Linuxem. 

::: moniker range="vs-2019"

Chcete-li změnit výchozí nastavení CMake v aplikaci Visual Studio 2019 z hlavní panel nástrojů, otevřete **konfigurace** rozevírací seznam a zvolte **spravovat konfigurace**. 

![Správa konfigurací CMake](../build/media/vs2019-cmake-manage-configurations.png "konfigurací CMake rozevíracího seznamu")

Tím se zobrazí **Editor nastavení CMake** kterého můžete upravit `CMakeSettings.json` soubor v kořenové složce projektu. Můžete také otevřít soubor přímo po kliknutí **upravit JSON** tlačítko v editoru. Další informace najdete v tématu [přizpůsobit nastavení CMake](../build/customize-cmake-settings.md).

::: moniker-end

::: moniker range="vs-2017"

Chcete-li změnit výchozí nastavení CMake v sadě Visual Studio 2017, zvolte **CMake | Změnit nastavení CMake | Soubor CMakeLists.txt** z hlavní nabídky, nebo klikněte pravým tlačítkem na CMakeSettings.txt v **Průzkumníka řešení** a zvolte **změnit nastavení CMake**. Visual Studio vytvoří nový `CMakeSettings.json` soubor v kořenové složce projektu. Můžete otevřít soubor pomocí **nastavení CMake** editor nebo přímo upravit soubor. Další informace najdete v tématu [nastavení přizpůsobení CMake](../build/customize-cmake-settings.md).

Následující příklad ukazuje výchozí konfiguraci pro Linux ladění v sadě Visual Studio 2017 (a Visual Studio 2019 verze 16.0) na základě předchozího příkladu kódu:

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

 Výchozí konfigurace Linux ladění ve Visual Studio 2019 16.1 a novější verze je, jak je znázorněno zde:

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

Další informace o těchto nastaveních najdete v tématu [CMakeSettings.json odkaz](../build/cmakesettings-reference.md).


## <a name="optional-settings"></a>Volitelná nastavení

Pro větší kontrolu, můžete použít následující volitelné nastavení:

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

Tyto možnosti umožňují spouštět příkazy v systému Linux, před a po sestavení a před generování CMake. Hodnotami může být jakýkoli příkaz, který je platný ve vzdáleném systému. Výstup je přesměrovaná zpět do sady Visual Studio.



## <a name="see-also"></a>Viz také:

[Práce s vlastnostmi projektu](../build/working-with-project-properties.md)<br/>
[Projekty CMake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
[Připojení ke vzdálenému počítači s Linuxem](connect-to-your-remote-linux-computer.md)<br/>
[Přizpůsobení nastavení CMake](../build/customize-cmake-settings.md)<br/>
[Konfigurace ladicích relací CMake](../build/configure-cmake-debugging-sessions.md)<br/>
[Nasazení, spuštění a ladění projektu Linux](deploy-run-and-debug-your-linux-project.md)<br/>
[Referenční dokumentace ke konfiguraci CMake předdefinované](../build/cmake-predefined-configuration-reference.md)<br/>
