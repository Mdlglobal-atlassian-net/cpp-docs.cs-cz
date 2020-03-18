---
title: Vytvoření a konfigurace projektu Linux CMake v sadě Visual Studio
description: Jak vytvořit, konfigurovat, upravit a zkompilovat projekt pro Linux CMake v sadě Visual Studio
ms.date: 10/04/2019
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 9c6a60162c2dbbab8e348b27d1987d7f1001bee0
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419404"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>Vytvoření a konfigurace projektu Linux CMake

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range="vs-2019"

Vytvoření nového projektu Linux CMake v sadě Visual Studio 2019:

1. Vyberte **soubor > nový projekt** v aplikaci Visual Studio nebo stiskněte klávesy **CTRL + SHIFT + N**.
1. Nastavte **jazyk** na **C++** a vyhledejte "cmake". Pak klikněte na tlačítko **Další**. Zadejte **název** a **umístění**a klikněte na **vytvořit**.

Sada Visual Studio vytvoří soubor minimálního CMakeLists. txt jenom s názvem spustitelného souboru a minimální požadovanou verzí CMake. Tento soubor můžete upravit ručně. Visual Studio nebude nikdy přepsat vaše změny. Argumenty příkazového řádku a proměnné prostředí CMake můžete zadat tak, že kliknete pravým tlačítkem na kořenový soubor CMakeLists. txt v **Průzkumník řešení** a zvolíte **Nastavení cmake pro projekt**. Chcete-li zadat možnosti pro ladění, klikněte pravým tlačítkem myši na uzel projektu a zvolte možnost **nastavení ladění a spuštění**.

::: moniker-end

Když otevřete složku, která obsahuje existující projekt CMake, sada Visual Studio použije proměnné v mezipaměti CMake ke konfiguraci technologie IntelliSense a sestavení automaticky. Místní konfigurace a nastavení ladění jsou uloženy v souborech JSON, které lze volitelně sdílet s ostatními, kteří používají aplikaci Visual Studio.

Visual Studio neupravuje soubory CMakeLists. txt, aby ostatní uživatelé pracující na stejném projektu mohli i nadále používat jakékoli nástroje, které už používají. Visual Studio při ukládání úprav do souboru CMakeLists. txt nebo v některých případech do CMakeSettings. JSON znovu vygeneruje mezipaměť. Pokud však používáte **existující konfiguraci mezipaměti** , aplikace Visual Studio neupraví mezipaměť.

Obecné informace o podpoře CMake v sadě Visual Studio najdete v tématu [projekty cmake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md). Než budete pokračovat, přečtěte si to jako první.

## <a name="before-you-begin"></a>Než začnete

Nejdřív se ujistěte, že máte nainstalovaný **vývoj pro Linux C++ s** nainstalovanou úlohou, včetně komponenty cmake. Viz [instalace úlohy C++ pro Linux v aplikaci Visual Studio](download-install-and-setup-the-linux-development-workload.md). 

V systému Linux se ujistěte, že jsou nainstalovány následující: 

- gcc
- gdb
- rsync
- zip 

::: moniker range="vs-2019"

Podpora Linux pro projekty CMake vyžaduje, aby na cílovém počítači byla nainstalována novější verze CMake. Verze, kterou nabízí výchozí správce balíčků pro distribuci, často není k dispozici, aby podporovala všechny funkce, které jsou požadovány v aplikaci Visual Studio. Sada Visual Studio 2019 zjišťuje, zda je v systému Linux nainstalována nejnovější verze CMake. Pokud není žádný nalezen, Visual Studio zobrazí informační panel v horní části podokna editoru, které nabízí instalaci pro vás z [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

Podpora CMake v sadě Visual Studio vyžaduje podporu režimu serveru, která byla představena v CMaki 3,8. V systému Visual Studio 2019 se doporučuje verze 3,14 nebo novější.

::: moniker-end

::: moniker range="vs-2017"

Podpora CMake v sadě Visual Studio vyžaduje podporu režimu serveru, která byla představena v CMaki 3,8. V případě varianty CMake poskytované Microsoftem si stáhněte nejnovější předem připravené binární soubory na [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

Binární soubory se nainstalují do `~/.vs/cmake`. Po nasazení binárních souborů se projekt automaticky znovu vygeneruje. Všimněte si, že pokud je CMake zadaná v poli `cmakeExecutable` v `CMakeSettings.json` neplatná (neexistuje nebo se jedná o nepodporovanou verzi) a jsou k dispozici předem připravené binární soubory, sada Visual Studio bude ignorovat `cmakeExecutable` a bude používat předem připravené binární soubory.

:::moniker-end

## <a name="open-a-folder"></a>Otevření složky

Chcete-li začít, vyberte **soubor** > **otevřete** > **složce** z hlavní nabídky nebo zadejte `devenv.exe <foldername>` na příkazovém řádku. Složka, kterou otevřete, by měla obsahovat soubor CMakeLists. txt společně se zdrojovým kódem.
Následující příklad ukazuje jednoduchý soubor CMakeLists. txt a soubor. cpp:

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

CMakeLists. txt:

```cmd
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Zvolit cíl pro Linux

Jakmile otevřete složku, aplikace Visual Studio analyzuje soubor CMakeLists. txt a určí cíl Windows pro **ladění x86**. Chcete-li cílit na vzdálený systém Linux, změňte nastavení projektu na **Linux-Debug** nebo **Linux-Release**. (Další informace najdete v tématu [Konfigurace nastavení cmake pro Linux](#configure_cmake_linux) .)

::: moniker range="vs-2019"

Chcete-li cílit na podsystém Windows pro Linux, klikněte na možnost **spravovat konfigurace** v rozevírací nabídce konfigurace v hlavním panelu nástrojů. Pak stiskněte tlačítko **Přidat konfiguraci** a zvolte možnost **WSL-Debug** nebo **WSL-Release** při použití nástroje RSZ nebo Clang varianty, pokud používáte sadu nástrojů Clang/LLVM. 

**Visual Studio 2019 verze 16,1** Při cílení na WSL není nutné žádné kopírování zdrojů nebo hlaviček, protože kompilátor systému Linux má přímý přístup k systému souborů systému Windows, ve kterém jsou umístěny vaše zdrojové soubory. (V systému Windows verze 1903 a novějších mají aplikace systému Windows podobně přístup k hlavičkovým souborům Linux přímo, ale Visual Studio tuto funkci ještě nevyužívá).

::: moniker-end

Pro vzdálené cíle zvolí Visual Studio ve výchozím nastavení první vzdálený systém v seznamu **nástroje** > **Možnosti** >  > **Správce připojení**pro **různé platformy** . Pokud se nenaleznou žádná vzdálená připojení, zobrazí se výzva k jejímu vytvoření. Další informace najdete v tématu [připojení ke vzdálenému počítači se systémem Linux](connect-to-your-remote-linux-computer.md).

Pokud zadáte vzdálený cíl pro Linux, váš zdroj se zkopíruje do vzdáleného systému.

Po výběru cíle se CMake spustí automaticky v systému Linux, aby se pro váš projekt vygenerovala mezipaměť CMake. 

![Vygenerovat mezipaměť CMake v systému Linux](media/cmake-linux-1.png "Generování mezipaměti CMake v systému Linux")

Aby bylo možné poskytovat podporu technologie IntelliSense pro hlavičky na vzdálených systémech Linux, Visual Studio je automaticky zkopíruje z počítače se systémem Linux do adresáře na místním počítači s Windows. Další informace najdete v tématu [IntelliSense pro vzdálené hlavičky](configure-a-linux-project.md#remote_intellisense).

## <a name="debug_cmake_project"></a>Ladění projektu CMake

Chcete-li ladit kód v zadaném cílovém systému pro ladění, nastavte zarážku, vyberte cíl cmake jako položku po spuštění v nabídce panelu nástrojů vedle nastavení projektu a zvolte možnost  **&#x23f5; spustit** na panelu nástrojů nebo stiskněte klávesu F5.

Pokud chcete přizpůsobit argumenty příkazového řádku programu, stiskněte tlačítko **cíle přepínače** v horní části **Průzkumník řešení** a pak zvolte **zobrazení cíle**. Pak klikněte pravým tlačítkem na cíl a vyberte **nastavení ladění a spouštění**. Tím se otevře nebo vytvoří konfigurační soubor Launch. vs. JSON, který obsahuje informace o programu. Chcete-li určit umístění zdrojových souborů, přidejte do souboru vlastnost **sourceFileMap** , jak je znázorněno v následujícím příkladu:

```json
"MIMode": "gdb",
"externalConsole": true,
"sourceFileMap": {
"c/Users/USER/source/repos/CMAKEPROJECTNAME": "C:\\Users\\USER\\source\\repos\\CMAKEPROJECTNAME"
},
"remoteMachineName": "${debugInfo.remoteMachineName}",
```

Chcete-li zadat další argumenty, přidejte je do pole `args` JSON. Další informace najdete v tématech [otevření složky projekty pro C++ ](../build/open-folder-projects-cpp.md) a [Konfigurace relací ladění cmake](../build/configure-cmake-debugging-sessions.md).

## <a name="configure_cmake_linux"></a>Konfigurace nastavení CMake pro Linux

Soubor CMakeSettings. JSON v projektu CMake pro Linux může určovat všechny vlastnosti uvedené v části [přizpůsobení nastavení cmake](../build/customize-cmake-settings.md)a další vlastnosti, které řídí nastavení sestavení na vzdáleném počítači se systémem Linux. 

::: moniker range="vs-2019"

Chcete-li změnit výchozí nastavení CMake v sadě Visual Studio 2019, otevřete z hlavního panelu nástrojů rozevírací seznam **Konfigurace** a klikněte na možnost **spravovat konfigurace**. 

![Správa konfigurací CMake](../build/media/vs2019-cmake-manage-configurations.png "Rozevírací seznam konfigurace CMake")

Tím se zobrazí **Editor nastavení cmake** , který můžete použít k úpravě souboru `CMakeSettings.json` v kořenové složce projektu. Soubor můžete otevřít také přímo kliknutím na tlačítko **Upravit JSON** v editoru. Další informace najdete v tématu [přizpůsobení nastavení cmake](../build/customize-cmake-settings.md).

::: moniker-end

::: moniker range="vs-2017"

Chcete-li změnit výchozí nastavení CMake v sadě Visual Studio 2017, vyberte **cmake | Změnit nastavení CMake | CMakeLists. txt** z hlavní nabídky nebo klikněte pravým tlačítkem na CMakeSettings. txt v **Průzkumník řešení** a vyberte **změnit nastavení cmake**. Visual Studio potom vytvoří nový soubor `CMakeSettings.json` v kořenové složce projektu. Soubor můžete otevřít pomocí editoru **Nastavení cmake** nebo přímo změnit soubor. Další informace najdete v tématu [přizpůsobení nastavení cmake](../build/customize-cmake-settings.md).

Následující příklad ukazuje výchozí konfiguraci pro Linux-Debug v aplikaci Visual Studio 2017 (a Visual Studio 2019 verze 16,0) na základě předchozího příkladu kódu:

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

Výchozí konfigurace Linux-Debug v aplikaci Visual Studio 2019 verze 16,1 a novější je znázorněna zde:

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

Další informace o těchto nastaveních naleznete v tématu [CMakeSettings. JSON reference](../build/cmakesettings-reference.md).


## <a name="optional-settings"></a>Volitelná nastavení

Pro větší kontrolu můžete použít následující volitelná nastavení:

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

Tyto možnosti umožňují spustit příkazy v systému Linux před a po sestavení a před generováním CMake. Hodnoty můžou být libovolný příkaz, který je platný na vzdáleném systému. Výstup je zapsán do kanálu zpět do sady Visual Studio.



## <a name="see-also"></a>Viz také

[Práce s vlastnostmi projektu](../build/working-with-project-properties.md)<br/>
[Projekty CMake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
[Připojení ke vzdálenému počítači s Linuxem](connect-to-your-remote-linux-computer.md)<br/>
[Přizpůsobení nastavení CMake](../build/customize-cmake-settings.md)<br/>
[Konfigurace ladicích relací CMake](../build/configure-cmake-debugging-sessions.md)<br/>
[Nasazení, spuštění a ladění projektu Linux](deploy-run-and-debug-your-linux-project.md)<br/>
[Odkaz na předdefinovaný konfigurační odkaz CMake](../build/cmake-predefined-configuration-reference.md)<br/>
