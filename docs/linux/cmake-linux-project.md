---
title: Vytvoření a konfigurace projektu Linux CMake v sadě Visual Studio
description: Jak vytvořit, konfigurovat, upravit a zkompilovat projekt pro Linux CMake v sadě Visual Studio
ms.date: 05/03/2020
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: c12e32801c992f6ba3675327b9ae537890202a4c
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765757"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>Vytvoření a konfigurace projektu Linux CMake

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor **verzí** sady Visual Studio pro tento článek na sadu visual Studio 2017 nebo visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="before-you-begin"></a>Před zahájením

Nejdřív se ujistěte, že máte nainstalovanou úlohu **vývoj pro Linux s C++** , včetně komponenty cmake. Viz [instalace úlohy C++ Linux v aplikaci Visual Studio](download-install-and-setup-the-linux-development-workload.md).

V systému Linux se ujistěte, že jsou nainstalovány následující:

- RSZ
- GDB
- rsync
- věřitel
- expertem-Build

::: moniker-end

::: moniker range="vs-2019"

Podpora Linux pro projekty CMake vyžaduje, aby měl cílový počítač novější verzi CMake. Verze, kterou nabízí výchozí správce balíčků pro distribuci, často není k dispozici, aby podporovala všechny funkce vyžadované v rámci sady Visual Studio. Sada Visual Studio 2019 zjišťuje, zda je v systému Linux nainstalována nejnovější verze CMake. Pokud není žádný nalezen, Visual Studio zobrazí informační panel v horní části podokna editoru. Nabízí instalaci CMake z [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

Podpora CMake v sadě Visual Studio vyžaduje podporu režimu serveru, která byla představena v CMaki 3,8. V systému Visual Studio 2019 se doporučuje verze 3,14 nebo novější.

::: moniker-end

::: moniker range="vs-2017"

Podpora CMake v sadě Visual Studio vyžaduje podporu režimu serveru, která byla představena v CMaki 3,8. V případě varianty CMake poskytované Microsoftem si stáhněte nejnovější předem připravené binární soubory na adrese [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

Binární soubory jsou nainstalovány v `~/.vs/cmake`. Po nasazení binárních souborů se projekt automaticky znovu vygeneruje. Pokud je CMake zadaná v `cmakeExecutable` poli *CMakeSettings. JSON* neplatná (neexistuje nebo je to Nepodporovaná verze) a jsou k dispozici předem připravené binární soubory, sada Visual Studio ignoruje `cmakeExecutable` a použije předem připravené binární soubory.

:::moniker-end

::: moniker range="vs-2019"

## <a name="create-a-new-linux-cmake-project"></a>Vytvořit nový projekt pro Linux CMake

Vytvoření nového projektu Linux CMake v sadě Visual Studio 2019:

1. Vyberte **soubor > nový projekt** v aplikaci Visual Studio nebo stiskněte klávesy **CTRL + SHIFT + N**.
1. Nastavte **jazyk** na **C++** a vyhledejte "cmake". Pak klikněte na tlačítko **Další**. Zadejte **název** a **umístění**a klikněte na **vytvořit**.

Sada Visual Studio vytvoří soubor minimálního *CMakeLists. txt* jenom s názvem spustitelného souboru a minimální požadovanou verzí cmake. Tento soubor můžete upravit ručně. Visual Studio nebude nikdy přepsat vaše změny. V tomto souboru můžete zadat argumenty příkazového řádku CMake a proměnné prostředí. V **Průzkumník řešení** klikněte pravým tlačítkem na kořenový soubor *CMakeLists. txt* a vyberte **Nastavení cmake pro projekt**. Chcete-li zadat možnosti pro ladění, klikněte pravým tlačítkem myši na uzel projektu a zvolte možnost **nastavení ladění a spuštění**.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="open-a-cmake-project-folder"></a>Otevření složky projektu CMake

Když otevřete složku, která obsahuje existující projekt CMake, sada Visual Studio používá k automatické konfiguraci IntelliSense a sestavení proměnné v mezipaměti CMake. Místní konfigurace a nastavení ladění se ukládají do souborů JSON. Volitelně můžete tyto soubory sdílet s jinými uživateli, kteří používají Visual Studio.

Visual Studio neupravuje soubory *CMakeLists. txt* . Tato možnost je samostatná, takže ostatní pracující na stejném projektu můžou dál používat stávající nástroje. Visual Studio při ukládání úprav do souboru *CMakeLists. txt* nebo v některých případech do *CMakeSettings. JSON*znovu vygeneruje mezipaměť. Pokud však používáte **existující konfiguraci mezipaměti** , aplikace Visual Studio neupraví mezipaměť.

Obecné informace o podpoře CMake v sadě Visual Studio najdete v tématu [projekty cmake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md). Než budete pokračovat, přečtěte si to jako první.

Začněte tím, že v hlavní nabídce vyberete **soubor** > **otevřít** > **složku** nebo v okně `devenv.exe <foldername>` [příkazového řádku pro vývojáře](../build/building-on-the-command-line.md) kliknete na jiný typ. Složka, kterou otevřete, by měla obsahovat soubor *CMakeLists. txt* společně se zdrojovým kódem.

Následující příklad ukazuje jednoduchý soubor *CMakeLists. txt* a soubor. cpp:

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

*CMakeLists. txt*:

```txt
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Zvolit cíl pro Linux

Jakmile otevřete složku, aplikace Visual Studio analyzuje soubor *CMakeLists. txt* a určí cíl Windows pro **ladění x86**. Chcete-li cílit na vzdálený systém Linux, změňte nastavení projektu na **Linux-Debug** nebo **Linux-Release**. (Další informace najdete v tématu [Konfigurace nastavení cmake pro Linux](#configure_cmake_linux) .)

::: moniker-end

::: moniker range="vs-2019"

Chcete-li cílit na podsystém Windows pro Linux, klikněte na položku **spravovat konfigurace** v rozevíracím seznamu konfigurace na hlavním panelu nástrojů. Pak stiskněte tlačítko **Přidat konfiguraci** a zvolte možnost **WSL-Debug** nebo **WSL-Release** , pokud používáte RSZ. Použijte Clang varianty, pokud používáte sadu nástrojů Clang/LLVM.

**Visual Studio 2019 verze 16,1** Při cílení na WSL není nutné žádné kopírování zdrojů ani hlaviček. Důvodem je, že kompilátor na platformě Linux má přímý přístup ke zdrojovým souborům v systému souborů Windows. (Ve Windows 10 verze 1903 a novějších můžou aplikace Windows podobně přistupovat k hlavičkovým souborům Linux přímo. Visual Studio tuto funkci ještě nevyužívá.)

::: moniker-end

::: moniker range=">=vs-2017"

Visual Studio zvolí první vzdálený systém v seznamu v nabídce **nástroje** > **Možnosti** > pro**více platforem** > **Správce připojení** ve výchozím nastavení pro vzdálené cíle. Pokud se nenaleznou žádná vzdálená připojení, budete vyzváni k jeho vytvoření. Další informace najdete v tématu [připojení ke vzdálenému počítači se systémem Linux](connect-to-your-remote-linux-computer.md).

Pokud zadáte vzdálený cíl pro Linux, váš zdroj se zkopíruje do vzdáleného systému.

Po výběru cíle se CMake spustí automaticky v systému Linux, aby se pro váš projekt vygenerovala mezipaměť CMake.

![Vygenerovat mezipaměť CMake v systému Linux](media/cmake-linux-1.png "Generování mezipaměti CMake v systému Linux")

Aby bylo možné poskytovat podporu technologie IntelliSense pro hlavičky na vzdálených systémech Linux, Visual Studio je automaticky zkopíruje z počítače se systémem Linux do adresáře na místním počítači s Windows. Další informace najdete v tématu [IntelliSense pro vzdálené hlavičky](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-cmake-project"></a><a name="debug_cmake_project"></a>Ladění projektu CMake

Chcete-li ladit kód v zadaném cílovém systému, nastavte zarážku. V nabídce panelu nástrojů vedle nastavení projektu vyberte cíl CMake jako položku po spuštění. Pak zvolte **&#x23f5; spustit** na panelu nástrojů nebo stiskněte klávesu **F5**.

Pokud chcete přizpůsobit argumenty příkazového řádku programu, stiskněte tlačítko **cíle přepínače** v horní části **Průzkumník řešení** a pak zvolte **zobrazení cíle**. Pak klikněte pravým tlačítkem na cíl a vyberte **nastavení ladění a spouštění**. Tento příkaz otevře nebo vytvoří konfigurační soubor *Launch. vs. JSON* , který obsahuje informace o programu. Chcete-li určit umístění zdrojových souborů, přidejte do souboru vlastnost **sourceFileMap** , jak je znázorněno v následujícím příkladu:

```json
"MIMode": "gdb",
"externalConsole": true,
"sourceFileMap": {
"c/Users/USER/source/repos/CMAKEPROJECTNAME": "C:\\Users\\USER\\source\\repos\\CMAKEPROJECTNAME"
},
"remoteMachineName": "${debugInfo.remoteMachineName}",
```

Chcete-li zadat další argumenty, přidejte je `args` do pole JSON. Další informace najdete v tématech [otevřené složky projekty pro C++](../build/open-folder-projects-cpp.md) a [Konfigurace relací ladění cmake](../build/configure-cmake-debugging-sessions.md).

## <a name="configure-cmake-settings-for-linux"></a><a name="configure_cmake_linux"></a>Konfigurace nastavení CMake pro Linux

Soubor *CMakeSettings. JSON* v projektu cmake pro Linux může určovat všechny vlastnosti uvedené v části [přizpůsobení nastavení cmake](../build/customize-cmake-settings.md)a další vlastnosti, které řídí nastavení sestavení na vzdáleném počítači se systémem Linux.

::: moniker-end

::: moniker range="vs-2019"

Chcete-li změnit výchozí nastavení CMake v sadě Visual Studio 2019, otevřete z hlavního panelu nástrojů rozevírací seznam **Konfigurace** a vyberte možnost **spravovat konfigurace**.

![Správa konfigurací CMake](../build/media/vs2019-cmake-manage-configurations.png "Rozevírací seznam konfigurace CMake")

Tento příkaz zobrazí **Editor nastavení cmake**, který můžete použít k úpravě souboru *CMakeSettings. JSON* v kořenové složce projektu. Soubor můžete otevřít také přímo kliknutím na tlačítko **Upravit JSON** v editoru. Další informace najdete v tématu [přizpůsobení nastavení cmake](../build/customize-cmake-settings.md).

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

::: moniker range="vs-2017"

Chcete-li změnit výchozí nastavení cmake v sadě Visual > Studio 2017, v hlavní nabídce vyberte **cmake** > **změnit nastavení cmake****CMakeLists. txt** . Nebo klikněte pravým tlačítkem na *CMakeSettings. txt* v **Průzkumník řešení** a vyberte **změnit nastavení cmake**. Visual Studio potom vytvoří nový soubor *CMakeSettings. JSON* v kořenové složce projektu. Soubor můžete otevřít pomocí editoru **Nastavení cmake** nebo přímo změnit soubor. Další informace najdete v tématu [přizpůsobení nastavení cmake](../build/customize-cmake-settings.md).

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

::: moniker range=">=vs-2017"

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
[Odkaz na předdefinovaný konfigurační odkaz CMake](../build/cmake-predefined-configuration-reference.md)

::: moniker-end
