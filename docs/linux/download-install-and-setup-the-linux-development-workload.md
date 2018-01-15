---
title: "Stáhnout, nainstalovat a nastavit zatížení systému Linux | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 13201f9fd397eaf191b7621ec0807a9901e961f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="download-install-and-setup-the-linux-workload"></a>Stáhnout, nainstalovat a nastavit zatížení Linux

## <a name="visual-studio-setup"></a>Instalace aplikace Visual Studio
1. Spusťte instalační program sady Visual Studio a vyberte položku **Linux development s jazykem C++** zatížení.

   ![Visual C++ pro Linux Development rozšíření](media/linuxworkload.png)

2. Klikněte na tlačítko **nainstalovat** Chcete-li pokračovat v instalaci.

## <a name="linux-setup"></a>Instalace v systému Linux
Musí mít cílový počítač Linux **openssh server**, **g ++**, **gdb**, a **gdbserver** nainstalován a ssh démon musí být spuštěn.  Pokud tyto ještě neexistují, můžete je nainstalovat následujícím způsobem:
 
1. V řádku prostředí v počítači Linux spusťte:

   `sudo apt-get install openssh-server g++ gdb gdbserver`

   Můžete být vyzváni k zadání hesla kořenové z důvodu příkazu sudo.  Pokud ano, zadat ho a pokračovat.  Po dokončení se nainstalují tyto služby a nástroje.

1. Ujistěte se, ssh je spuštěná v počítači Linux spuštěním:

   `sudo service ssh start`
   
   To se spustit službu a spusťte jej na pozadí, přijímá připojení.
