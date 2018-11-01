---
title: Konfigurace projektu Linux CMake v sadě Visual Studio
description: Konfigurace projektu Linux CMake v sadě Visual Studio
ms.date: 07/20/2018
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 32d69e28c0991adc6117b7f9496eeb1022943ef2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585039"
---
# <a name="configure-a-linux-cmake-project"></a>Konfigurace projektu Linux CMake

**Visual Studio 2017 verze 15.4 nebo novější**<br/>
Pokud jste si nainstalovali úlohu Linux C++ pro Visual Studio, je standardně vybraná podpora CMake pro Linux. Teď můžete pracovat na svém stávajícím základu kódu, který používá CMake bez nutnosti převádět na projekt sady Visual Studio. Je-li vašeho základu kódu napříč platformami, je cílem Windows a Linuxem z Visual Studia.

Toto téma předpokládá, že máte základní znalosti podpora CMake v sadě Visual Studio. Další informace najdete v tématu [nástroje CMake pro Visual C++](../ide/cmake-tools-for-visual-cpp.md). Další informace o CMake samotný najdete v tématu [sestavení, testování a balíček svůj Software s CMake](https://cmake.org/).

> [!NOTE]
> Podpora CMake v sadě Visual Studio vyžaduje režim podporu serveru, která byla zavedena v CMake 3.8. Hodnotu typu variant poskytovaný společností Microsoft CMake stáhnout nejnovější předem připravených binární soubory na [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases).

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

Soubor CMakeLists.txt:

```cmd
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Volba cíle Linuxu

Jakmile otevřete složku sady Visual Studio analyzuje soubor CMakeLists.txt a určuje cílem Windows **x86 ladění**. Cílit na Linuxu, změnit nastavení projektu a **Linux ladění** nebo **Linux verze**.

Visual Studio ve výchozím nastavení, vybere první vzdálený systém v seznamu v části **nástroje** > **možnosti** > **různé platformy**  >  **Správce připojení**. Pokud se nenajdou žádné vzdálené připojení, zobrazí se výzva k jejímu vytvoření.

Po zadání cílové Linux zdroje zkopírována na počítač s Linuxem. CMake se spusťte na počítači s Linuxem ke generování mezipaměti CMake pro váš projekt.

![Vygenerovat mezipaměť CMake v Linuxu](media/cmake-linux-1.png "vygenerovat mezipaměť CMake v Linuxu")

**Visual Studio 2017 verze 15.7 nebo novější:**<br/>
K zajištění podpory IntelliSense pro vzdálených hlaviček, Visual Studio automaticky zkopíruje do adresáře na místním počítači Windows. Další informace najdete v tématu [technologie IntelliSense pro vzdálených hlaviček](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-project"></a>Ladění projektu

Ladění kódu ve vzdáleném systému, nastavte zarážku, vyberte cíl CMake jako položku při spuštění v nabídce nástrojů vedle nastavení projektu a zvolte  **&#x23f5; Start** na panelu nástrojů nebo stisknete klávesu F5.

Přizpůsobení vašeho programu argumenty příkazového řádku, klikněte pravým tlačítkem na spustitelný soubor **Průzkumníka řešení** a vyberte **nastavení ladění a spouštění**. Tím se otevře nebo vytvoří launch.vs.json konfigurační soubor, který obsahuje informace o programu. Pokud chcete zadat další argumenty, přidejte je `args` pole JSON. Další informace najdete v tématu [projekty otevřít složku v jazyce Visual C++](../ide/non-msbuild-projects.md).

## <a name="configure-cmake-settings-for-linux"></a>Konfigurace nastavení CMake pro Linux

Chcete-li změnit výchozí nastavení CMake, zvolte **CMake | Změnit nastavení CMake | Soubor CMakeLists.txt** z hlavní nabídky, nebo klikněte pravým tlačítkem na CMakeSettings.txt v **Průzkumníka řešení** a zvolte **změnit nastavení CMake**. Visual Studio vytvoří nový soubor ve složce s názvem `CMakeSettings.json` , který se naplní výchozími konfiguracemi, které jsou uvedeny v položce nabídky nastavení projektu. Následující příklad ukazuje, že výchozí konfigurace pro ladění Linux podle předchozí příklad kódu:

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

`name` Hodnota může být cokoli, co chcete. `remoteMachineName` Hodnota určuje, které vzdáleného systému do cíle, v případě, že máte více než jedno. Technologie IntelliSense je povolený pro toto pole můžete vybrat správné systému. Pole `remoteCMakeListsRoot` Určuje, které vaše zdroje projektu budou zkopírovány do vzdáleného systému. Pole `remoteBuildRoot` je, kde se vygeneruje výstup sestavení na vzdáleném systému. Zda je také zkopírován výstup místně do umístění určeného proměnnou `buildRoot`. `remoteInstallRoot` a `installRoot` pole se podobají `remoteBuildRoot` a `buildRoot`s výjimkou případů, použijí se při provádění instalace cmake. `remoteCopySources` Položka řídí, jestli vaše místní zdroje se zkopírují do vzdáleného počítače. Může být nastavíte na hodnotu false Pokud máte velké množství souborů a již synchronizujete zdroje sami. `remoteCopyOutputVerbosity` Hodnota určuje úroveň podrobností na krok kopírování v případě, že potřebujete diagnostikovat chyby. `remoteCopySourcesConcurrentCopies` Položka řídí, jak velký počet procesů se vytvoří podřízený proces udělat kopie. `remoteCopySourcesMethod` Hodnota může být jedna z rsync nebo sftp. `remoteCopySourcesExclusionList` Pole umožňuje řídit, co se zkopíruje do vzdáleného počítače. `rsyncCommandArgs` Hodnota umožňuje řídit rsync metodu kopírování. `remoteCopyBuildOutput` Pole určuje, zda je zkopírován výstup vzdáleného buildu do složky místního sestavení.

Existují také některé volitelné nastavení, která vám pomůže k větší kontrolu:

```json
{
      "remotePreBuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostBuildCommand": "",
}
```

Tyto možnosti umožňují spuštění příkazů v okně vzdáleného před a po sestavení a před generování CMake. Může být libovolný platný příkaz na vzdáleného pole. Výstup je přesměrovaná zpět do sady Visual Studio.

## <a name="download-prebuilt-cmake-binaries"></a>Stáhněte si předem připravených binární soubory CMake

Vaší distribuce Linuxu mohou mít starší verzi CMake. Podpora CMake v sadě Visual Studio vyžaduje režim podporu serveru, která byla zavedena v CMake 3.8. Hodnotu typu variant poskytovaný společností Microsoft CMake stáhnout nejnovější předem připravených binární soubory na [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases).

## <a name="see-also"></a>Viz také

[Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)<br/>
[Nástroje CMake pro Visual C++](../ide/cmake-tools-for-visual-cpp.md)
