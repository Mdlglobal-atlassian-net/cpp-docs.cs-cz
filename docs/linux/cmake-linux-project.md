---
title: Konfigurace projektu Linux CMake v sadě Visual Studio
description: Konfigurace projektu Linux CMake v sadě Visual Studio
ms.date: 11/01/2018
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 22de2f7a7b5374f781a032f5152610d7a97feb16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389886"
---
# <a name="configure-a-linux-cmake-project"></a>Konfigurace projektu Linux CMake

Když otevřete složku, která obsahuje projekt CMake Visual Studio používá metadata, která CMake vytvoří konfigurace technologie IntelliSense a sestavení automaticky. Místní konfigurace a nastavení ladění jsou uloženy v souborech JSON, které lze volitelně sdílet s ostatními uživateli, kteří používají Visual Studio. 

Visual Studio neprovede žádné změny souboru CMakeLists.txt nebo původní mezipaměť CMake, tak, aby uživatelé, kteří pracují na stejném projektu můžete dál používat jakékoli nástroje jsou už používá.  

## <a name="before-you-begin"></a>Před zahájením

Nejprve zkontrolujte, zda máte **vývoj pro Linux v C++** nainstalovaná, úloha včetně součásti CMake. Zobrazit [, nainstalujte úlohu C++ Linux v sadě Visual Studio](download-install-and-setup-the-linux-development-workload.md). 

Podpora CMake v sadě Visual Studio vyžaduje režim podporu serveru, která byla zavedena v CMake 3.8. Hodnotu typu variant CMake poskytovaný společností Microsoft, stáhněte si nejnovější předem připravených binární soubory na [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases).

Toto téma předpokládá, že jste si přečetli [nástroje CMake pro Visual Studio](../build/cmake-projects-in-visual-studio.md). 

> [!NOTE]
> Podpora CMake v sadě Visual Studio vyžaduje režim podporu serveru, která byla zavedena v CMake 3.8. Hodnotu typu variant poskytovaný společností Microsoft CMake stáhnout nejnovější předem připravených binární soubory na [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases). V aplikaci Visual Studio 2019 předem připravených binární soubory dají automaticky nasazovat (viz [stažení předem připravených binární soubory CMake](#download-prebuilt-cmake-binaries)).

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
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Volba cíle Linuxu

Jakmile otevřete složku sady Visual Studio analyzuje soubor CMakeLists.txt a určuje cílem Windows **x86 ladění**. Cílit na Linuxu, změnit nastavení projektu a **Linux ladění** nebo **Linux verze**.

Visual Studio ve výchozím nastavení, vybere první vzdálený systém v seznamu v části **nástroje** > **možnosti** > **různé platformy**  >  **Správce připojení**. Pokud se nenajdou žádné vzdálené připojení, zobrazí se výzva k jejímu vytvoření. Další informace najdete v tématu [připojit ke vzdálenému počítači s Linuxem](connect-to-your-remote-linux-computer.md).

Po zadání cílové Linux zdroje zkopírována na počítač s Linuxem. CMake se spusťte na počítači s Linuxem ke generování mezipaměti CMake pro váš projekt.

![Vygenerovat mezipaměť CMake v Linuxu](media/cmake-linux-1.png "vygenerovat mezipaměť CMake v Linuxu")

**Visual Studio 2017 verze 15.7 nebo novější:**<br/>
K zajištění podpory IntelliSense pro vzdálených hlaviček, Visual Studio automaticky zkopíruje z počítače Linux do adresáře na místním počítači Windows. Další informace najdete v tématu [technologie IntelliSense pro vzdálených hlaviček](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-project"></a>Ladění projektu

Ladění kódu ve vzdáleném systému, nastavte zarážku, vyberte cíl CMake jako položku při spuštění v nabídce nástrojů vedle nastavení projektu a zvolte  **&#x23f5; Start** na panelu nástrojů nebo stisknete klávesu F5.

Přizpůsobení vašeho programu argumenty příkazového řádku, klikněte pravým tlačítkem na spustitelný soubor **Průzkumníka řešení** a vyberte **nastavení ladění a spouštění**. Tím se otevře nebo vytvoří launch.vs.json konfigurační soubor, který obsahuje informace o programu. Pokud chcete zadat další argumenty, přidejte je `args` pole JSON. Další informace najdete v tématu [projekty otevřít složku pro jazyk C++](../build/open-folder-projects-cpp.md) a [konfigurace CMake ladicími relacemi](../build/configure-cmake-debugging-sessions.md).

## <a name="configure-cmake-settings-for-linux"></a>Konfigurace nastavení CMake pro Linux

V projektu CMake Linux souboru CMakeSettings.json můžete určit všechny vlastnosti, které jsou uvedeny v [nastavení přizpůsobení CMake](../build/customize-cmake-settings.md), plus další vlastnosti, které řídí nastavení sestavení na vzdáleném počítači s Linuxem. Chcete-li změnit výchozí nastavení CMake, zvolte **CMake | Změnit nastavení CMake | Soubor CMakeLists.txt** z hlavní nabídky, nebo klikněte pravým tlačítkem na CMakeSettings.txt v **Průzkumníka řešení** a zvolte **změnit nastavení CMake**. Visual Studio vytvoří nový `CMakeSettings.json` soubor v kořenové složce projektu. Můžete otevřít soubor pomocí **nastavení CMake** editor nebo přímo upravit soubor. 

Následující příklad ukazuje, že výchozí konfigurace pro ladění Linux podle předchozí příklad kódu:

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
V následující tabulce najdete souhrn nastavení:

|Nastavení|Popis|
|-----------|-----------------|
|`name`|Tato hodnota může být cokoli, co chcete.|
|`remoteMachineName`|Určuje které vzdáleného systému do cíle, v případě, že máte více než jedno. Technologie IntelliSense je povolený pro toto pole můžete vybrat správné systému.|
|`remoteCMakeListsRoot`|Určuje, které vaše zdroje projektu budou zkopírovány do vzdáleného systému.|
|`remoteBuildRoot`|Určuje, kde se vygeneruje výstup sestavení na vzdáleném systému. Zda je také zkopírován výstup místně do umístění určeného proměnnou `buildRoot`.|
|`remoteInstallRoot` a `installRoot`| Podobně jako `remoteBuildRoot` a `buildRoot`s výjimkou případů, použijí se při provádění instalace CMake.|
|`remoteCopySources`|Určuje, zda vaše místní zdroje jsou zkopírovány do vzdáleného počítače. Může být nastavíte na hodnotu false Pokud máte mnoho souborů a již synchronizujete zdroje sami.|
|`remoteCopyOutputVerbosity`| Určuje úroveň podrobností na krok kopírování v případě, že potřebujete diagnostikovat chyby.|
|`remoteCopySourcesConcurrentCopies`| Určuje, jak velký počet procesů se vytvoří podřízený proces udělat kopie.|
|`remoteCopySourcesMethod`| Může být buď `rsync` nebo `sftp`.|
|`remoteCopySourcesExclusionList`| Určuje soubory, které nechcete, které se mají zkopírovat do vzdáleného počítače.|
|`rsyncCommandArgs`|Určuje metodu rsync kopírování.|
|`remoteCopyBuildOutput`| Určuje, zda je zkopírován výstup vzdáleného buildu do složky místního sestavení.|

Pro větší kontrolu, můžete použít tyto volitelné nastavení:

```json
{
      "remotePreBuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostBuildCommand": "",
}
```

Tyto možnosti umožňují spouštět příkazy ve vzdáleném systému, před a po sestavení a před generování CMake. Hodnotami může být jakýkoli příkaz, který je platný ve vzdáleném systému. Výstup je přesměrovaná zpět do sady Visual Studio.

## <a name="download-prebuilt-cmake-binaries"></a>Stáhněte si předem připravených binární soubory CMake

Vaší distribuce Linuxu mohou mít starší verzi CMake. Podpora CMake v sadě Visual Studio vyžaduje režim podporu serveru, která byla zavedena v CMake 3.8. Hodnotu typu variant CMake poskytovaný společností Microsoft, stáhněte si nejnovější předem připravených binární soubory na [ https://github.com/Microsoft/CMake/releases ](https://github.com/Microsoft/CMake/releases).

**Visual Studio 2019**<br/>
Pokud ve vzdáleném počítači nebyl nalezen platný CMake informačního panelu se zobrazí a poskytnout možnost výběru automaticky nasadit předem sestavené binární soubory CMake. Binární soubory se nainstalují pro `~/.vs/cmake`. Po nasazení binárních souborů, bude automaticky obnovit váš projekt. Mějte na paměti, že pokud CMake určené `cmakeExecutable` pole `CMakeSettings.json` je neplatný (neexistuje nebo má nepodporovanou verzi) a předem připravených binární soubory jsou k dispozici sady Visual Studio bude ignorovat `cmakeExecutable` a použijte předem sestavené binární soubory.

## <a name="see-also"></a>Viz také:

[Práce s vlastnostmi projektu](../build/working-with-project-properties.md)<br/>
[Projekty CMake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
[Připojení ke vzdálenému počítači s Linuxem](connect-to-your-remote-linux-computer.md)<br/>
[Přizpůsobení nastavení CMake](../build/customize-cmake-settings.md)<br/>
[Konfigurace ladicích relací CMake](../build/configure-cmake-debugging-sessions.md)<br/>
[Nasazení, spuštění a ladění projektu Linux](deploy-run-and-debug-your-linux-project.md)<br/>
[Referenční dokumentace ke konfiguraci CMake předdefinované](../build/cmake-predefined-configuration-reference.md)<br/>
