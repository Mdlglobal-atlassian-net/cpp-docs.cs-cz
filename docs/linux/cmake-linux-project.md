---
title: Konfigurace projektu Linux CMake v sadě Visual Studio | Dokumentace Microsoftu
description: Konfigurace projektu Linux CMake v sadě Visual Studio
ms.custom: ''
ms.date: 07/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 82134d48853896ccb70c2620cd70c803fcc74bc8
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821046"
---
# <a name="configure-a-linux-cmake-project"></a>Konfigurace projektu Linux CMake

**Visual Studio 2017 verze 15.4 nebo novější**<br/>
Pokud jste si nainstalovali úlohu Linux C++ pro Visual Studio, je standardně vybraná podpora CMake pro Linux. Teď můžete pracovat na svém stávajícím základu kódu, který používá CMake bez nutnosti převádět na projekt sady Visual Studio. Je-li vašeho základu kódu napříč platformami, je cílem Windows a Linuxem z Visual Studia.

Toto téma předpokládá, že máte základní znalosti podpora CMake v sadě Visual Studio. Další informace najdete v tématu [nástroje CMake pro Visual C++](../ide/cmake-tools-for-visual-cpp.md). Další informace o CMake samotný najdete v tématu [sestavení, testování a balíček svůj Software s CMake](https://cmake.org/).

> [!NOTE]  
> Podpora CMake v sadě Visual Studio vyžaduje režim podporu serveru, která byla zavedena v CMake 3.8. Pro hodnotu typu variant CMake poskytovaný společností Microsoft, který podporuje [zobrazení cílů CMake](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) podokno v sadě Visual Studio, stáhněte si nejnovější předem připravených binární soubory na [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases). Pokud váš správce balíčků poskytuje starší verze než CMake 3.8, můžete alternativně vyřešit ji [vytváření CMake ze zdroje](#build-a-supported-cmake-release-from-source), nebo byste radši chtěli použít standardní CMake, si můžete stáhnout z oficiální [stránku pro stažení CMake](https://cmake.org/download/). 

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

## <a name="build-a-supported-cmake-release-from-source"></a>Podporované verze CMake ze zdroje sestavení

Minimální verzi CMake požadovaná na vaší platformě Linux 3.8 je počítač, musí taky podporovat režim serveru. To chcete ověřit spuštěním tohoto příkazu:

```cmd
cmake --version
```

Pokud chcete ověřit, že je povolený režim tohoto serveru, spusťte:

```cmd
cmake -E capabilities
```

Ve výstupu vyhledejte **"serverMode": true**. Všimněte si, že i při sestavování CMake ze zdroje jak je popsáno níže by měla zkontrolujte možnosti až budete hotovi. Systému Linux mohou mít omezení, zabrání režim serveru povolené.

Abyste mohli začít vytvářet CMake ze zdroje v prostředí systému Linux, ujistěte se, že váš správce balíčků je aktuální a zda máte git a cmake, které jsou k dispozici.

Nejprve naklonujte CMake zdrojů, ze [úložiště Microsoft CMake](https://github.com/Microsoft/CMake) kde budeme udržovat větev pro Visual Studio – podpora CMake:

```cmd
sudo apt-get update
sudo apt-get install -y git cmake
git clone https://github.com/Microsoft/CMake.git
cd CMake
```

V dalším kroku sestavit a nainstalovat aktuální verzi CMake /usr/local/bin, spusťte tyto příkazy:

```cmd
mkdir out
cd out
cmake ../
make
sudo make install
```

V dalším kroku spusťte tento příkaz k ověření verze > = 3.8 a tento server je povolen režim:

```cmd
/usr/local/bin/cmake –version
cmake -E capabilities
```

## <a name="see-also"></a>Viz také

[Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)<br/>
[Nástroje CMake pro Visual C++](../ide/cmake-tools-for-visual-cpp.md)  
