---
title: Nainstalujte úlohu C++ Linux v sadě Visual Studio
description: Popisuje, jak stáhnout, nainstalovat a nastavit Linux úlohy pro C++ v sadě Visual Studio.
ms.date: 06/07/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: af4e3ec0ac21951163e92786555559cd02e8148f
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821579"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Stažení, instalace a nastavení úloh Linux


::: moniker range=">=vs-2017"

Integrované vývojové prostředí sady Visual Studio ve Windows můžete použít k vytváření, úpravy a ladění projektů C++, které jsou spouštěny na fyzickém počítači Linux, virtuální počítač, nebo [subsystém Windows pro Linux](/windows/wsl/about). 

Můžete pracovat na svém stávajícím základu kódu, který používá CMake nebo jakémkoli jiném systému sestavení bez nutnosti převádět na projekt sady Visual Studio. Je-li vašeho základu kódu napříč platformami, je cílem Windows a Linuxem z Visual Studia. Například můžete upravit, ladění a profilování kódu ve Windows pomocí sady Visual Studio a pak rychle změnit cílení projektů pro Linux provedete dalšímu testování. Soubory hlaviček Linux se automaticky zkopírují do svého místního počítače, kde sady Visual Studio je využívá k poskytování plnou podporou technologie IntelliSense (dokončování příkazů, přejít k definici a tak dále) podpory. 
 
Pro některý z těchto scénářů **vývoj pro Linux v C++** zatížení je povinný. 

::: moniker-end

::: moniker range="vs-2019"

V aplikaci Visual Studio 2019 můžete zadat samostatné cíle pro sestavování a ladění. Při cílení na WSL, je už nebude potřeba přidat připojení ke vzdálené nebo konfigurace SSH.

Podpora pro [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) je integrovaná do sady Visual Studio pro Linuxové projekty.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Instalační program sady Visual Studio

1. Zadejte do vyhledávacího pole Windows "Instalační program sady Visual Studio": ![Windows vyhledávacího pole](media/visual-studio-installer-search.png)
2. Vyhledejte instalační služby v rámci **aplikace** výsledky a dvojím kliknutím ho. Když se instalační program otevře, zvolte **změnit**a potom klikněte na **úlohy** kartu. Přejděte dolů k položce **další sady nástrojů** a vyberte **vývoj pro Linux v C++** pracovního vytížení.

   ![Visual C++ pro úlohu vývoj pro Linux](media/linuxworkload.png)

1. Pokud cílíte na platformy vložený nebo IoT, přejděte na **podrobné informace o instalaci** podokno na pravé straně v části **vývoj pro Linux v C++** , rozbalte **volitelné součásti**a vyberte komponenty, které potřebujete. Podpora CMake pro Linux je standardně vybraná.

1. Klikněte na tlačítko **změnit** pokračujte v instalaci.

## <a name="options-for-creating-a-linux-environment"></a>Možnosti pro vytvoření prostředí s Linuxem

Pokud ještě nemáte počítač s Linuxem, můžete vytvořit virtuální počítač s Linuxem v Azure. Další informace najdete v tématu [rychlý start: Vytvoření virtuálního počítače s Linuxem na webu Azure Portal](/azure/virtual-machines/linux/quick-create-portal).

Ve Windows 10 můžete nainstalovat a cílit na vaše oblíbené distribuce Linuxu v subsystému Windows pro Linux (WSL). Další informace najdete v tématu [subsystém Windows pro Linux Instalační příručka pro Windows 10](/windows/wsl/install-win10). WSL je vhodné konzoly prostředí, ale nedoporučuje se používat pro grafických aplikací. 

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Nastavení pro Linux: Ubuntu ve WSL

Na WSL je nutné žádné vzdálené připojení. **ZIP** a **rsync** jsou požadovány pro automatickou synchronizaci hlavičky Linuxu pomocí sady Visual Studio pro podporu technologie Intellisense. Pokud požadované aplikace již nejsou k dispozici, můžete je nainstalovat následujícím způsobem:

```bash
sudo g++ gdb make rsync zip
```
::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu na vzdálených Linuxových systémů

Cílový systém Linux musí mít **openssh-server**, **g ++** , **gdb**, a **gdbserver** nainstalované a ssh démon musí být spuštěn. **ZIP** se vyžaduje pro automatickou synchronizaci vzdálených hlaviček pomocí místního počítače pro podporu technologie Intellisense. Pokud tyto aplikace již nejsou k dispozici, můžete je nainstalovat následujícím způsobem:

1. V příkazovém řádku shell na počítači s Linuxem spusťte:

   ```bash
   sudo apt-get install openssh-server g++ gdb gdbserver zip
   ```

   Můžete být vyzváni k kořenové heslo z důvodu příkazu sudo.  Pokud ano, zadejte ho a pokračovat. Jakmile budete hotovi, se nainstalují požadované služby a nástroje.

1. Zkontrolujte, ssh služba běží na počítači s Linuxem pomocí:

   ```bash
   sudo service ssh start
   ```
   To spustí službu a běží na pozadí je připraven přijmout připojení na portu.

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>Fedora na WSL

Používá fedora **dnf** balíček Instalační služby. Chcete-li stáhnout **g ++** , **gdb**, **rsync** a **zip**, spusťte:

   ```bash
   sudo dnf install gcc-g++ gdb rsync zip
   ```

**ZIP** a **rsync** jsou požadovány pro automatickou synchronizaci hlavičky Linuxu pomocí sady Visual Studio pro podporu technologie Intellisense.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora na vzdálených Linuxových systémů

Cílový počítač s Fedora používá **dnf** balíček Instalační služby. Chcete-li stáhnout **openssh-server**, **g ++** , **gdb**, **gdbserver** a **zip**a restartujte ssh proces démon, postupujte podle těchto pokynů:

1. V příkazovém řádku shell na počítači s Linuxem spusťte:

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip
   ```
   Můžete být vyzváni k kořenové heslo z důvodu příkazu sudo.  Pokud ano, zadejte ho a pokračovat. Jakmile budete hotovi, se nainstalují požadované služby a nástroje.

1. Zkontrolujte, ssh služba běží na počítači s Linuxem pomocí:

   ```bash
   sudo systemctl start sshd
   ```

   To spustí službu a běží na pozadí je připraven přijmout připojení na portu.

::: moniker-end

::: moniker range="vs-2015"

Podpora pro Linux C++ vývoj je k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

## <a name="next-steps"></a>Další kroky

Nyní jste připraveni k vytvoření nebo otevření projektu Linux a nakonfigurovat jej pro spuštění v cílovém systému. Další informace naleznete v tématu:

- [Vytvoření nového projektu Linux](create-a-new-linux-project.md)
- [Konfigurace projektu Linux CMake](cmake-linux-project.md)
