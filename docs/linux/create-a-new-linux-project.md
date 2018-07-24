---
title: Vytvoření nového projektu C++ Linux v sadě Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/20/2018
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
ms.openlocfilehash: f64f8eaf09e92df3dd776180db5904af039d6ad7
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207967"
---
# <a name="create-a-new-linux-project"></a>Vytvoření nového projektu Linux
Při psaní kódu jazyka C++ v sadě Visual Studio pro Linux, budete mít možnost vytvořit projekt sady Visual Studio nebo projekt CMake. Toto téma popisuje, jak vytvořit projekt sady Visual Studio. Informace o projekty CMake najdete v tématu [konfigurace projektu Linux CMake ](cmake-linux-project.md).

K vytvoření nového projektu Linux v sadě Visual Studio, postupujte takto:

1. Vyberte **soubor > Nový projekt** v sadě Visual Studio nebo stisknutím klávesy **Ctrl + Shift + N**.
1. Vyberte **Visual C++ > pro různé platformy > Linuxem** uzlu a pak vyberte typ projektu chcete vytvořit, zadejte název nebo umístění a klikněte na tlačítko OK.

   ![Nového projektu Linux](media/newproject.png)

   | Typ projektu | Popis
   | ------------ | ---
   | **Blikání (Raspberry)**           | Projekt se vzorovým kódem se zapisují do blikání kontrolku LED určené pro zařízení Raspberry Pi
   | **Konzolová aplikace (Linux)** | Projekt určený pro libovolný počítač s Linuxem se vzorovým kódem se zapisují do výstupní text konzoly
   | **Prázdný projekt (Linux)**       | Projekt je určená pro všechny počítače Linux bez ukázky kódu napsané
   | **Projekt makefile (Linux)**    | Projekt cílené pro libovolný počítač s Linuxem, které budou vytvořeny pomocí standardní systém sestavení souboru pravidel

