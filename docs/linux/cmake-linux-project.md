---
title: "Konfigurace Linux CMake projektu v sadě Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 10/25/2107
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 67665f3271caf71d16788b2e102d0e756d9f702f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="configure-a-linux-cmake-project"></a>Konfigurace projektu Linux CMake
  
**Visual Studio 2017 verzi 15.4** při instalaci Linux C++ zatížení je standardně vybraná CMake podporu pro Linux. Teď můžete pracovat na váš stávající kód základní používající CMake bez nutnosti ho převést na projekt sady Visual Studio. Pokud je vaše základu kódu platformy, můžete určit cílovou Windows a Linux z Visual Studia. 

Toto téma předpokládá, že máte základní znalost CMake podpory v sadě Visual Studio. Další informace najdete v tématu [CMake nástrojů pro Visual C++](../ide/cmake-tools-for-visual-cpp.md). Další informace o CMake samotné najdete v tématu [sestavení, Test a balíček si Software s CMake](https://cmake.org/).

> [!NOTE] 
> Podpora CMake v sadě Visual Studio vyžaduje podpora režimu serveru, která byla zavedena v CMake 3.8. Pokud váš správce balíčků poskytuje starší verze CMake, můžete je obejít podle budovy CMake 3.8 ze zdroje.



## <a name="open-a-folder"></a>Otevřít složku
Chcete-li začít, zvolte **souboru | Otevřete | Složka** z hlavní nabídky jinak typ `devenv.exe <foldername>` na příkazovém řádku. Otevření složky měli soubor CMakeLists.txt v něm společně s vašeho zdrojového kódu.
Následující příklad ukazuje jednoduchý CMakeLists.txt souboru nebo souboru:

```cpp
// Hello.cpp

#include <iostream>;
 
int main(int argc, char* argv[])
{
    std::cout << "Hello" << std::endl;
}
```

CMakeLists.txt: 
```cmd
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Zvolte cílovou Linux
Jakmile otevřete složku, Visual Studio analyzuje soubor CMakeLists.txt a určuje cílem Windows x86-Debug. Pokud chcete zacílit Linux, změňte nastavení projektu na Linux-Debug nebo Linux verze.

Ve výchozím nastavení, Visual Studio vybere první vzdáleného systému, v seznamu (v části **nástroje | Možnosti | Křížové platformy | Správce připojení**). Pokud se nenajdou žádné vzdálené připojení, zobrazí se výzva k jeho vytvoření.

Po zadání cíle Linuxu, váš zdroj se zkopíruje na počítači pro Linux. CMake je spusťte na počítači Linux pro generování mezipaměti CMake pro váš projekt.  

![Generovat CMake mezipaměti v systému Linux](media/cmake-linux-1.png "generování mezipaměti CMake v systému Linux")  

## <a name="debug-the-project"></a>Ladění projektu  
Chcete-li ladit kód ve vzdáleném systému, nastavit zarážky, vyberte cíl CMake jako položku při spuštění v nabídce panelu nástrojů vedle nastavení projektu a klikněte na tlačítko spustit (nebo stiskněte klávesu F5).

## <a name="configure-cmake-settings-for-linux"></a>Konfigurace nastavení CMake pro Linux
Chcete-li změnit výchozí nastavení CMake, zvolte **CMake | Změna nastavení CMake | CMakeLists.txt** z hlavní nabídky, nebo klikněte pravým tlačítkem na CMakeSettings.txt v **Průzkumníku řešení** a zvolte **změnit nastavení CMake**. Visual Studio vytvoří nový soubor ve složce s názvem `CMakeSettings.json` je naplněna výchozí konfigurace, které jsou uvedeny v položku nabídky nastavení projektu. Následující příklad ukazuje, že výchozí konfiguraci pro Linux-Debug založené na předchozí příklad kódu:

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "remoteMachineName": "${defaultRemoteMachineName}",
      "configurationType": "Debug",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```
`name` Hodnota může být vám líbí. `remoteMachineName` Hodnota určuje cíl, který vzdáleného systému, v případě, že máte více než jednou. IntelliSense je povolený pro toto pole, aby vám pomohou vybrat správné systému. Pole `remoteCMakeListsRoot` Určuje, kde vaše zdroje projektu budou zkopírovány do vzdáleného systému. Pole `remoteBuildRoot` je, kde se budou generovat výstup sestavení do vzdáleného systému. Že výstup je také zkopírován místně do umístění, které `buildRoot`.

## <a name="building-a-supported-cmake-release-from-source"></a>Vytváření podporované verze CMake ze zdroje.
Minimální verze CMake požadované na vašem systému Linux, počítač je 3.8, a musí taky podporovat režim serveru. Chcete ověřit spusťte tento příkaz:

```cmd
cmake --version
```

Chcete-li ověřit, zda že je povolen režim tohoto serveru, spusťte:

```cmd
cmake -E capabilities
```

Ve výstupu vyhledejte "serverMode": true. Všimněte si, že i když zkompilujete CMake ze zdroje jak je popsáno níže by měla zkontrolujte možnosti po dokončení. Váš systém Linux může mít omezení, které brání povolený režim serveru.

Chcete-li získat spustit sestavení ze zdroje v prostředí pro vaše Linux systému zajistěte, aby váš správce balíčků je aktuální a zda máte git a cmake k dispozici. Nejprve naklonujte CMake zdrojů:

```cmd
sudo apt-get update
sudo apt-get install -y git cmake
git clone https://github.com/Kitware/CMake.git
cd CMake
```

Dále zkontrolujte, zda že jsou na podporovanou verzi CMake pro sadu Visual Studio. Aktivně sledujeme CMake vývoj, ale nemůžeme zaručit, že podporujeme nejnovější. Chcete-li vytvořit CMake 3.9.0 (například), nejprve spusťte:

```cmd
git checkout tags/v3.9.0
```

Potom spusťte následující příkazy:

```cmd
mkdir out
cd out
cmake ../
make
sudo make install
```

Výše uvedených příkazů sestavení a nainstalovat aktuální verzi CMake k /usr/local/bin. Spusťte tento příkaz k ověření verze je > = 3.8 a tento server je povolen režim:

```cmd
/usr/local/bin/cmake –version
cmake -E capabilities
```

## <a name="see-also"></a>Viz také
[Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)  
[CMake nástrojů pro Visual C++](../ide/cmake-tools-for-visual-cpp.md)