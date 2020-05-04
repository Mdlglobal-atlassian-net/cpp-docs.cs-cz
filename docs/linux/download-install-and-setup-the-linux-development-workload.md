---
title: Instalace úlohy C++ Linux v aplikaci Visual Studio
description: Jak stáhnout, nainstalovat a nastavit úlohu pro Linux pro C++ v sadě Visual Studio.
ms.date: 05/03/2020
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: bc75610aaefe2a3bdd919cbc4dd81413202794c6
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765744"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Stažení, instalace a nastavení úlohy Linux

::: moniker range="vs-2015"

Projekty Linux jsou podporovány v aplikaci Visual Studio 2017 a novějších. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor **verzí** sady Visual Studio pro tento článek na sadu visual Studio 2017 nebo visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end

::: moniker range=">=vs-2017"

Integrované vývojové prostředí (IDE) sady Visual Studio ve Windows můžete použít k vytváření, úpravám a ladění projektů C++, které se spouštějí ve vzdáleném systému Linux, virtuálním počítači nebo v [subsystému Windows pro Linux](/windows/wsl/about).

Můžete pracovat na svém stávajícím základu kódu, který používá CMake bez nutnosti ho převést na projekt sady Visual Studio. Pokud je váš základ kódu pro různé platformy, můžete v sadě Visual Studio cílit na Windows i Linux. Můžete například upravovat, sestavovat a ladit kód ve Windows pomocí sady Visual Studio. Pak můžete rychle změnit cílení projektu pro Linux na sestavení a ladění v prostředí Linux. Soubory hlaviček systému Linux jsou automaticky zkopírovány do místního počítače. Visual Studio používá je k poskytování plné podpory IntelliSense (dokončování příkazů, přechodu k definici atd.).

Pro některý z těchto scénářů se vyžaduje **vývoj pro Linux pomocí C++** .

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Instalační program sady Visual Studio

1. Do vyhledávacího pole Windows zadejte "Instalační program pro Visual Studio":

   ![Vyhledávací pole Windows](media/visual-studio-installer-search.png)

1. Vyhledejte instalační program v části výsledky **aplikace** a dvakrát na něj klikněte. Jakmile se instalační program otevře, zvolte **Upravit**a pak klikněte na kartu **úlohy** . Přejděte dolů na jiné sady **nástrojů** a vyberte **vývoj pro Linux s** využitím úlohy C++.

   ![Visual C++ pro vývoj pro Linux úlohy](media/linuxworkload.png)

1. Pokud cílíte na IoT nebo integrované platformy, v pravém podokně otevřete podokno **Podrobnosti o instalaci** . V části **vývoj pro Linux pomocí C++** rozbalte položku **volitelné komponenty**a vyberte požadované součásti. Ve výchozím nastavení je vybrána podpora CMake pro Linux.

1. Pokračujte v instalaci kliknutím na tlačítko **změnit** .

## <a name="options-for-creating-a-linux-environment"></a>Možnosti pro vytvoření prostředí Linux

Pokud ještě nemáte počítač se systémem Linux, můžete v Azure vytvořit virtuální počítač se systémem Linux. Další informace najdete v tématu [rychlý Start: Vytvoření virtuálního počítače se systémem Linux v Azure Portal](/azure/virtual-machines/linux/quick-create-portal).

Ve Windows 10 můžete nainstalovat a cílit na svůj oblíbený distribuce pro Linux v subsystému Windows pro Linux (WSL). Další informace najdete v tématu [Instalační příručka k subsystému Windows pro Linux pro Windows 10](/windows/wsl/install-win10). Pokud nemůžete získat přístup k Windows Storu, můžete [balíčky distribuce pro WSL stáhnout ručně](/windows/wsl/install-manual). WSL je vhodné prostředí konzoly, ale nedoporučuje se pro grafické aplikace.

::: moniker-end

::: moniker range="vs-2019"

Projekty Linux v aplikaci Visual Studio vyžadují, aby byly na vzdáleném systému Linux nebo WSL nainstalovány následující závislosti:

- **Kompilátor** – Visual Studio 2019 má plnou podporu pro RSZ a [Clang](/cpp/build/clang-support-cmake?view=vs-2019).
- **GDB** – Visual Studio automaticky spustí GDB v systému Linux a pomocí front-endu ladicího programu sady Visual Studio poskytuje prostředí pro ladění s plnou přesností na platformě Linux.
- **rsync** a **zip – zahrnutí rsync a zip umožňuje** aplikaci Visual Studio extrahovat hlavičkové soubory ze systému Linux do systému souborů Windows pro použití technologií IntelliSense.
- **značka**
- **OpenSSH-server** (pouze systémy Remote Linux) – Visual Studio se připojuje ke vzdáleným systémům Linux přes zabezpečené připojení SSH.
- **Cmake** (jenom projekty cmake) – můžete nainstalovat [staticky propojené binární soubory cmake Microsoftu pro Linux](https://github.com/microsoft/CMake/releases).
- **expertem-Build** (pouze projekty cmake) – [expertem](https://ninja-build.org/) je výchozí generátor pro konfigurace Linux a WSL v sadě Visual Studio 2019 verze 16,6 nebo novější.

V následujících příkazech se předpokládá, že používáte g + + místo Clang.

::: moniker-end

::: moniker range="vs-2017"

Projekty Linux v aplikaci Visual Studio vyžadují, aby byly na vzdáleném systému Linux nebo WSL nainstalovány následující závislosti:

- **RSZ** – Visual Studio 2017 má plnou podporu pro RSZ.
- **GDB** – Visual Studio automaticky spouští GDB v systému Linux a používá front-end ladicí program sady Visual Studio k poskytování prostředí pro ladění s plnou přesností na platformě Linux.
- **rsync** a **zip – zahrnutí rsync a zip umožňuje** aplikaci Visual Studio extrahovat hlavičkové soubory ze systému Linux do systému souborů Windows pro použití v IntelliSense.
- **značka**
- **OpenSSH-server** – Visual Studio se připojuje ke vzdáleným systémům Linux přes zabezpečené připojení SSH.
- **Cmake** (jenom projekty cmake) – můžete nainstalovat [staticky propojené binární soubory cmake Microsoftu pro Linux](https://github.com/microsoft/CMake/releases).

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Instalace pro Linux: Ubuntu v WSL

Pokud cílíte na WSL, není nutné přidávat vzdálené připojení nebo konfigurovat SSH pro sestavování a ladění. k automatické synchronizaci hlaviček Linux pomocí sady Visual Studio pro podporu technologie IntelliSense jsou vyžadovány soubory **zip** a **rsync** . **expertem-Build** se vyžaduje jenom pro projekty cmake. Pokud požadované aplikace ještě nejsou k dispozici, můžete je nainstalovat pomocí tohoto příkazu:

```bash
sudo apt-get install g++ gdb make ninja-build rsync zip
```

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu na vzdálených systémech Linux

Cílový systém Linux musí mít **OpenSSH-server**, **g + +**, **GDB**a nainstalovaný. **make** **expertem-Build** se vyžaduje jenom pro projekty cmake. Démon procesu **SSH** musí být spuštěn. k automatické synchronizaci vzdálených hlaviček pomocí místního počítače pro podporu technologie IntelliSense se vyžadují soubory **zip** a **rsync** . Pokud tyto aplikace ještě nejsou k dispozici, můžete je nainstalovat následujícím způsobem:

1. Na příkazovém řádku prostředí v počítači se systémem Linux spusťte příkaz:

   ```bash
   sudo apt-get install openssh-server g++ gdb make ninja-build rsync zip
   ```

   Může se zobrazit výzva k zadání kořenového hesla, ve kterém můžete spustit příkaz sudo. Pokud ano, zadejte ho a pokračujte. Po dokončení jsou nainstalovány požadované služby a nástroje.

1. Zajistěte, aby na počítači se systémem Linux běžela služba SSH spuštěním:

   ```bash
   sudo service ssh start
   ```

   Tento příkaz spustí službu a spustí ji na pozadí, která je připravena přijmout připojení.

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>Fedora na WSL

Fedora používá instalační program balíčků **DNF** . Ke stažení **g + +**, **GDB**, **make**, **rsync**, **expertem-Build**a **zip**spusťte:

   ```bash
   sudo dnf install gcc-g++ gdb rsync ninja-build make zip
   ```

k automatické synchronizaci hlaviček Linux pomocí sady Visual Studio pro podporu technologie IntelliSense jsou vyžadovány soubory **zip** a **rsync** . **expertem-Build** se vyžaduje jenom pro projekty cmake.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora na vzdálených systémech Linux

Cílový počítač se systémem Fedora používá instalační program balíčků **DNF** . Pokud chcete stáhnout **OpenSSH-server**, **g + +**, **GDB**, **make**, **expertem-Build**, **rsync**a **zip**a restartovat démona SSH, postupujte podle těchto pokynů. **expertem-Build** se vyžaduje jenom pro projekty cmake.

1. Na příkazovém řádku prostředí v počítači se systémem Linux spusťte příkaz:

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb ninja-build make rsync zip
   ```

   Může se zobrazit výzva k zadání kořenového hesla, ve kterém můžete spustit příkaz sudo. Pokud ano, zadejte ho a pokračujte. Po dokončení jsou nainstalovány požadované služby a nástroje.

1. Zajistěte, aby na počítači se systémem Linux běžela služba SSH spuštěním:

   ```bash
   sudo systemctl start sshd
   ```

   Tento příkaz spustí službu a spustí ji na pozadí, která je připravena přijmout připojení.

## <a name="next-steps"></a>Další kroky

Teď jste připraveni vytvořit nebo otevřít projekt pro Linux a nakonfigurovat ho tak, aby běžel v cílovém systému. Další informace naleznete v tématu:

- [Vytvoření nového projektu Linux](create-a-new-linux-project.md)
- [Konfigurace projektu Linux CMake](cmake-linux-project.md)

::: moniker-end
