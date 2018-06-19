---
title: Vytvoření nového projektu C++ Linux v sadě Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2017
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 4d4d11ec459215d81996d1daea420513c21b10b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339226"
---
# <a name="create-a-new-linux-project"></a>Vytvoření nového projektu Linux
Pokud kódování pro Linux, máte možnost automatického vytvoření projektu sady Visual Studio nebo CMake projektu. Toto téma popisuje postup vytvoření projektu sady Visual Studio. Informace o CMake projekty najdete v tématu [konfigurace projektu CMake Linux ](cmake-linux-project.md).

Pokud chcete vytvořit nový projekt Linux v sadě Visual Studio, postupujte takto:

1. Vyberte **soubor > Nový projekt** v sadě Visual Studio, nebo klikněte na tlačítko **Ctrl + Shift + N**.
1. Vyberte **Visual C++ > křížové platformy > Linux** uzel a pak vyberte typ projektu, který chcete vytvořit, zadejte název nebo umístění a klikněte na tlačítko OK.

   ![Nový projekt Linux](media/newproject.png)

   | Typ projektu | Popis
   | ------------ | ---
   | **BLINK (malin)**           | Cílem pro malin platformy zařízení ukázkový kód napsaný blikání DIODU projektu
   | **Konzolové aplikace (Linux)** | Projekt cílem pro jakýkoli počítač Linux ukázkový kód zapsána na výstup textu do konzoly nástroje
   | **Prázdný projekt (Linux)**       | Určeno pro každý počítač Linux s žádné ukázkový kód napsaný projektu
   | **Projektem souboru pravidel (Linux)**    | Projekt cílené pro jakýkoli počítač Linux, které budou vytvořeny pomocí standardní systém sestavení souboru pravidel

