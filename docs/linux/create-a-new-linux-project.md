---
title: Vytvoření nového projektu C++ Linux v sadě Visual Studio
ms.date: 09/12/2018
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: bd5ab1d2bc1077f366082bf8767f8f690173ac8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393188"
---
# <a name="create-a-new-linux-project"></a>Vytvoření nového projektu Linux

Nejprve zkontrolujte, zda máte **úlohy pro vývoj pro Linux** pro nainstalovanou sadu Visual Studio. Další informace najdete v tématu [stažení, instalace a nastavení úloh Linux](download-install-and-setup-the-linux-development-workload.md).

Při vytváření nového projektu C++ v sadě Visual Studio pro Linux, máte možnost vytvořit projekt sady Visual Studio nebo projekt CMake. Toto téma popisuje, jak vytvořit projekt sady Visual Studio. Informace o vytváření a práci s existující projekty CMake najdete v tématu [konfigurace projektu Linux CMake ](cmake-linux-project.md).

K vytvoření nového projektu Linux v sadě Visual Studio, postupujte takto:

1. Vyberte **soubor > Nový projekt** v sadě Visual Studio nebo stisknutím klávesy **Ctrl + Shift + N**.
1. Vyberte **Visual C++ > pro různé platformy > Linuxem** uzlu a pak vyberte typ projektu chcete vytvořit, zadejte název nebo umístění a klikněte na tlačítko OK.

   ![Nového projektu Linux](media/newproject.png)

   | Typ projektu | Popis
   | ------------ | ---
   | **Blikání (Raspberry)**           | Projekt se vzorovým kódem se zapisují do blikání kontrolku LED určené pro zařízení Raspberry Pi
   | **Konzolová aplikace (Linux)** | Projekt určený pro libovolný počítač s Linuxem se vzorovým kódem se zapisují do výstupní text konzoly
   | **Empty Project (Linux)**       | Projekt je určená pro všechny počítače Linux bez ukázky kódu napsané
   | **Projekt makefile (Linux)**    | Projekt cílené pro libovolný počítač s Linuxem, které budou vytvořeny pomocí standardní systém sestavení souboru pravidel
