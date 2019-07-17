---
title: Instalace úlohy C++ Linux do sady Visual Studio
description: Popisuje, jak stáhnout, nainstalovat a nastavit úlohu pro Linux pro C++ v aplikaci Visual Studio.
ms.date: 06/11/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 5df7b323d202f398059e92abaeeeedbf73439fa4
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299798"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Stažení, instalace a nastavení úlohy Linux

::: moniker range="vs-2015"

Projekty Linux jsou podporovány v aplikaci Visual Studio 2017 a novějších.

::: moniker-end

::: moniker range=">=vs-2017"

Integrované vývojové prostředí (IDE) sady Visual Studio ve Windows můžete použít k vytváření C++ , úpravám a ladění projektů, které se spouštějí na fyzickém počítači Linux, virtuálním počítači nebo v subsystému [Windows pro Linux](/windows/wsl/about). 

Můžete pracovat na svém stávajícím základu kódu, který používá CMake nebo jakýkoli jiný systém sestavení, aniž by bylo nutné ho převést na projekt aplikace Visual Studio. Pokud je váš základ kódu pro různé platformy, můžete v sadě Visual Studio cílit na Windows i Linux. Můžete například upravit, ladit a profilovat kód ve Windows pomocí sady Visual Studio a pak rychle změnit cílení projektu pro Linux na další testování. Soubory hlaviček systému Linux jsou automaticky zkopírovány do místního počítače, kde je aplikace Visual Studio používá k zajištění úplné podpory technologie IntelliSense (dokončování příkazů, přechodu k definici atd.). 
 
Pro některý z těchto scénářů se vyžaduje **vývoj pro C++ Linux s** úlohou. 

::: moniker-end

::: moniker range="vs-2019"

V aplikaci Visual Studio 2019 můžete určit samostatné cíle pro vytváření a ladění. Při cílení na WSL již není nutné přidávat vzdálené připojení nebo konfigurovat SSH.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Instalační program sady Visual Studio

1. Do vyhledávacího pole Windows zadejte "Instalační program pro Visual Studio":

   ![Vyhledávací pole Windows](media/visual-studio-installer-search.png)

2. Vyhledejte instalační program v části výsledky **aplikace** a dvakrát na něj klikněte. Jakmile se instalační program otevře, zvolte **Upravit**a pak klikněte na kartu **úlohy** . Přejděte dolů na **jiné sady nástrojů** a vyberte **vývoj pro Linux pomocí C++**  úlohy.

   ![Visual C++ pro vývoj pro Linux – úlohy vývoje](media/linuxworkload.png)

1. Pokud cílíte na IoT nebo integrované platformy, v **pravém podokně v** části vývoj pro Linux v **C++nástroji**rozbalte možnost **volitelné komponenty** a vyberte požadované součásti. Ve výchozím nastavení je vybrána podpora CMake pro Linux.

1. Pokračujte v instalaci kliknutím na tlačítko **změnit** .

## <a name="options-for-creating-a-linux-environment"></a>Možnosti pro vytvoření prostředí Linux

Pokud ještě nemáte počítač se systémem Linux, můžete v Azure vytvořit virtuální počítač se systémem Linux. Další informace najdete v tématu [rychlý Start: Vytvořte virtuální počítač se systémem Linux v Azure Portal](/azure/virtual-machines/linux/quick-create-portal).

Ve Windows 10 můžete nainstalovat a cílit na svůj oblíbený distribuce pro Linux v subsystému Windows pro Linux (WSL). Další informace najdete v tématu [Instalační příručka k subsystému Windows pro Linux pro Windows 10](/windows/wsl/install-win10). WSL je praktické prostředí konzoly, ale nedoporučuje se pro grafické aplikace. 

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Instalace pro Linux: Ubuntu na WSL

Při cílení na WSL není nutné přidávat vzdálené připojení ani konfigurovat SSH, aby bylo možné sestavovat a ladit. k automatické synchronizaci hlaviček Linux pomocí sady Visual Studio pro podporu technologie IntelliSense jsou vyžadovány soubory **zip** a **rsync** . Pokud požadované aplikace ještě nejsou k dispozici, můžete je nainstalovat následujícím způsobem:

```bash
sudo apt-get install g++ gdb make rsync zip
```
::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu na vzdálených systémech Linux

Cílový systém Linux musí mít nainstalované **OpenSSH-server**, **g + +** , **GDB**a **gdbserver** a musí být spuštěn démon procesu SSH. k automatické synchronizaci vzdálených hlaviček pomocí místního počítače pro podporu technologie IntelliSense se vyžaduje **zip** . Pokud tyto aplikace ještě nejsou k dispozici, můžete je nainstalovat následujícím způsobem:

1. Na příkazovém řádku prostředí v počítači se systémem Linux spusťte příkaz:

   ```bash
   sudo apt-get install openssh-server g++ gdb gdbserver zip
   ```

   V důsledku příkazu sudo se může zobrazit výzva k zadání vašeho kořenového hesla.  Pokud ano, zadejte ho a pokračujte. Po dokončení jsou nainstalovány požadované služby a nástroje.

1. Zajistěte, aby na počítači se systémem Linux běžela služba SSH spuštěním:

   ```bash
   sudo service ssh start
   ```
   Tím se spustí služba a spustí se na pozadí, která je připravena přijmout připojení.

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>Fedora na WSL

Fedora používá instalační program balíčků **DNF** . Ke stažení **g + +** , **GDB**, **rsync** a **zip**spusťte:

   ```bash
   sudo dnf install gcc-g++ gdb rsync zip
   ```

k automatické synchronizaci hlaviček Linux pomocí sady Visual Studio pro podporu technologie IntelliSense jsou vyžadovány soubory **zip** a **rsync** .

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora na vzdálených systémech Linux

Cílový počítač se systémem Fedora používá instalační program balíčků **DNF** . Pokud chcete stáhnout **OpenSSH-server**, **g + +** , **GDB**, **gdbserver** a **zip**a restartovat démona SSH, postupujte podle těchto pokynů:

1. Na příkazovém řádku prostředí v počítači se systémem Linux spusťte příkaz:

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip
   ```
   V důsledku příkazu sudo se může zobrazit výzva k zadání vašeho kořenového hesla.  Pokud ano, zadejte ho a pokračujte. Po dokončení jsou nainstalovány požadované služby a nástroje.

1. Zajistěte, aby na počítači se systémem Linux běžela služba SSH spuštěním:

   ```bash
   sudo systemctl start sshd
   ```

   Tím se spustí služba a spustí se na pozadí, která je připravena přijmout připojení.

::: moniker-end

::: moniker range="vs-2015"

Podpora pro vývoj C++ pro Linux je dostupná v systému Visual Studio 2017 nebo novějším.

::: moniker-end

## <a name="next-steps"></a>Další kroky

Teď jste připraveni vytvořit nebo otevřít projekt pro Linux a nakonfigurovat ho tak, aby běžel v cílovém systému. Další informace naleznete v tématu:

- [Vytvoření nového projektu Linux](create-a-new-linux-project.md)
- [Konfigurace projektu Linux CMake](cmake-linux-project.md)
