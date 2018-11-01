---
title: Nainstalujte úlohu C++ Linux v sadě Visual Studio
description: Popisuje, jak stáhnout, nainstalovat a nastavit Linux úlohy pro C++ v sadě Visual Studio.
ms.date: 10/12/2018
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 2fa4036ece6dd161c73a5176740870c5593f4669
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441922"
---
# <a name="download-install-and-setup-the-linux-workload"></a>Stažení, instalace a nastavení úloh Linux

Integrované vývojové prostředí sady Visual Studio ve Windows můžete použít k vytváření, úpravy a ladění projektů C++, které jsou spouštěny na fyzickém počítači Linux, virtuální počítač, nebo [subsystém Windows pro Linux](/windows/wsl/about). Pro žádnou z těchto scénářů, nejdřív nainstalovat **vývoj pro Linux v C++** pracovního vytížení.

## <a name="visual-studio-setup"></a>Instalační program sady Visual Studio

1. Zadejte do vyhledávacího pole Windows "Instalační program sady Visual Studio": ![Windows vyhledávacího pole](media/visual-studio-installer-search.png)
2. Vyhledejte instalační služby v rámci **aplikace** výsledky a dvojím kliknutím ho. Když se instalační program otevře, zvolte **změnit**a potom klikněte na **úlohy** kartu. Přejděte dolů k položce **další sady nástrojů** a vyberte **vývoj pro Linux v C++** pracovního vytížení.

   ![Visual C++ pro úlohu vývoj pro Linux](media/linuxworkload.png)

1. Pokud používáte CMake nebo cílíte na platformy vložený nebo IoT, přejděte na **podrobné informace o instalaci** podokno na pravé straně v části **vývoj pro Linux v C++**, rozbalte **volitelné součásti** a vyberte komponenty, které potřebujete.

1. Klikněte na tlačítko **změnit** pokračujte v instalaci.

## <a name="options-for-creating-a-linux-environment"></a>Možnosti pro vytvoření prostředí s Linuxem

Pokud ještě nemáte počítač s Linuxem, můžete vytvořit virtuální počítač s Linuxem v Azure. Další informace najdete v tématu [rychlý start: vytvoření virtuálního počítače s Linuxem na webu Azure Portal](/azure/virtual-machines/linux/quick-create-portal).

Další možností, ve Windows 10, je k aktivaci subsystém Windows pro Linux. Další informace najdete v tématu [Průvodce instalací systému Windows 10](/windows/wsl/install-win10).

## <a name="linux-setup-ubuntu"></a>Nastavení pro Linux: Ubuntu

Musí mít cílový počítač s Linuxem **openssh-server**, **g ++**, **gdb**, a **gdbserver** nainstalované a ssh démon musí být spuštěn. **ZIP** se vyžaduje pro automatickou synchronizaci vzdálených hlaviček pomocí místního počítače pro podporu technologie Intellisense. Pokud tyto aplikace již nejsou k dispozici, můžete je nainstalovat následujícím způsobem:

1. V příkazovém řádku shell na počítači s Linuxem spusťte:

   `sudo apt-get install openssh-server g++ gdb gdbserver zip`

   Můžete být vyzváni k kořenové heslo z důvodu příkazu sudo.  Pokud ano, zadejte ho a pokračovat. Jakmile budete hotovi, se nainstalují požadované služby a nástroje.

1. Zkontrolujte, ssh služba běží na počítači s Linuxem pomocí:

   `sudo service ssh start`

   To spustí službu a běží na pozadí je připraven přijmout připojení na portu.

## <a name="linux-setup-fedora"></a>Nastavení pro Linux: Fedora

Cílový počítač s Fedora používá **dnf** balíček Instalační služby. Chcete-li stáhnout **openssh-server**, **g ++**, **gdb**, **gdbserver** a **zip**a restartujte ssh proces démon, postupujte podle těchto pokynů:

1. V příkazovém řádku shell na počítači s Linuxem spusťte:

   `sudo dnf install openssh-server g++ gdb gdbserver zip`

   Můžete být vyzváni k kořenové heslo z důvodu příkazu sudo.  Pokud ano, zadejte ho a pokračovat. Jakmile budete hotovi, se nainstalují požadované služby a nástroje.

1. Zkontrolujte, ssh služba běží na počítači s Linuxem pomocí:

   `sudo systemctl start sshd`

   To spustí službu a běží na pozadí je připraven přijmout připojení na portu.

