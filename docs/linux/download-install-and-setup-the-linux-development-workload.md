---
title: Nainstalujte úlohu C++ Linux v sadě Visual Studio | Dokumentace Microsoftu
description: Popisuje, jak stáhnout, nainstalovat a nastavit Linux úlohy pro C++ v sadě Visual Studio.
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 403f1bcd8634c3f471f34ff1266501de5bf05d52
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601389"
---
# <a name="download-install-and-setup-the-linux-workload"></a>Stažení, instalace a nastavení úloh Linux

Integrované vývojové prostředí sady Visual Studio ve Windows můžete použít k vytváření, úpravy a ladění projektů C++, které jsou spouštěny na fyzickém počítači Linux, virtuální počítač, nebo [subsystém Windows pro Linux](/windows/wsl/about). Pro žádnou z těchto scénářů, nejdřív nainstalovat **vývoj pro Linux v C++** pracovního vytížení.

## <a name="visual-studio-setup"></a>Instalační program sady Visual Studio

1. Zadejte "Instalační program sady Visual Studio" v nabídce Windows search; Podívejte se v části **aplikace** výsledky a dvojím kliknutím ho. Když se instalační program otevře, zvolte **změnit**a potom klikněte na **úlohy** kartu. Přejděte dolů k položce **další sady nástrojů** a vyberte **vývoj pro Linux v C++** pracovního vytížení.

   ![Visual C++ pro úlohu vývoj pro Linux](media/linuxworkload.png)

1. Pokud používáte CMake nebo cílíte na platformy vložený nebo IoT, přejděte na **podrobné informace o instalaci** podokno na pravé straně v části **vývoj pro Linux v C++**, rozbalte **volitelné součásti** a vyberte komponenty, které potřebujete. 

1. Klikněte na tlačítko **změnit** pokračujte v instalaci.


## <a name="options-for-creating-a-linux-environment"></a>Možnosti pro vytvoření prostředí s Linuxem

Pokud ještě nemáte počítač s Linuxem, můžete vytvořit virtuální počítač s Linuxem v Azure. Další informace najdete v tématu [rychlý start: vytvoření virtuálního počítače s Linuxem na webu Azure Portal](/azure/virtual-machines/linux/quick-create-portal).

Další možností, ve Windows 10, je k aktivaci subsystém Windows pro Linux. Další informace najdete v tématu [Průvodce instalací systému Windows 10](/windows/wsl/install-win10).

## <a name="linux-setup"></a>Nastavení pro Linux

Musí mít cílový počítač s Linuxem **openssh-server**, **g ++**, **gdb**, a **gdbserver** nainstalované a ssh démon musí být spuštěn. **ZIP** se vyžaduje pro automatickou synchronizaci vzdálených hlaviček pomocí místního počítače pro podporu technologie Intellisense. Pokud tyto aplikace již nejsou k dispozici, můžete je nainstalovat následujícím způsobem:

1. V příkazovém řádku shell na počítači s Linuxem spusťte:

   `sudo apt-get install openssh-server g++ gdb gdbserver zip`

   Můžete být vyzváni k kořenové heslo z důvodu příkazu sudo.  Pokud ano, zadejte ho a pokračovat.  Jakmile budete hotovi, se nainstalují tyto služby a nástroje.

1. Zkontrolujte, ssh služba běží na počítači s Linuxem pomocí:

   `sudo service ssh start`

   Se spustit službu a spustit na pozadí je připraven přijmout připojení na portu.
