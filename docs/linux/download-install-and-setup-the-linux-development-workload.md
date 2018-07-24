---
title: Nainstalujte úlohu C++ Linux v sadě Visual Studio | Dokumentace Microsoftu
description: Popisuje, jak stáhnout, nainstalovat a nastavit Linux úlohy pro C++ v sadě Visual Studio.
ms.custom: ''
ms.date: 07/20/2018
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
ms.openlocfilehash: e33b9ac72ca7691ccbb80a9a30349d3a1e31e194
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207556"
---
# <a name="download-install-and-setup-the-linux-workload"></a>Stažení, instalace a nastavení úloh Linux

Vytváření a ladění projektů C++ v Linuxu pomocí rozhraní IDE sady Visual Studio, je nutné nainstalovat **vývoj pro Linux v C++** pracovního vytížení.

## <a name="visual-studio-setup"></a>Instalační program sady Visual Studio
1. Spusťte instalační program sady Visual Studio a vyberte položku **vývoj pro Linux v C++** pracovního vytížení.

   ![Visual C++ pro vývoj pro Linux rozšíření](media/linuxworkload.png)

2. Klikněte na tlačítko **nainstalovat** pokračujte v instalaci.

## <a name="linux-setup"></a>Nastavení pro Linux
Musí mít cílový počítač s Linuxem **openssh-server**, **g ++**, **gdb**, a **gdbserver** nainstalované a ssh démon musí být spuštěn.  Pokud tyto ještě nejsou k dispozici, můžete je nainstalovat následujícím způsobem:
 
1. V příkazovém řádku shell na počítači s Linuxem spusťte:

   `sudo apt-get install openssh-server g++ gdb gdbserver`

   Můžete být vyzváni k kořenové heslo z důvodu příkazu sudo.  Pokud ano, zadejte ho a pokračovat.  Jakmile budete hotovi, se nainstalují tyto služby a nástroje.

1. Zkontrolujte, ssh služba běží na počítači s Linuxem pomocí:

   `sudo service ssh start`
   
   Se spustit službu a spustit na pozadí je připraven přijmout připojení na portu.
