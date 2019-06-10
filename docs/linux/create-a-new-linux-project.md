---
title: Vytvoření nového projektu C++ Linux v sadě Visual Studio
ms.date: 06/07/2019
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: e39e60c906901420a4809c22b4f4e71d3b621da1
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821631"
---
# <a name="create-a-new-linux-project"></a>Vytvoření nového projektu Linux

::: moniker range="vs-2015"

Linuxové projekty jsou k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

Nejprve zkontrolujte, zda máte **úlohy pro vývoj pro Linux** pro nainstalovanou sadu Visual Studio. Další informace najdete v tématu [stažení, instalace a nastavení úloh Linux](download-install-and-setup-the-linux-development-workload.md).

Když vytvoříte nový C++ projektu pro Linux v sadě Visual Studio, můžete vytvořit projekt sady Visual Studio nebo projekt CMake. Tento článek popisuje, jak vytvořit projekt sady Visual Studio. Informace o tom, jak vytvořit a pracovat s existující projekty CMake najdete v tématu [konfigurace projektu Linux CMake ](cmake-linux-project.md).

## <a name="to-create-a-new-linux-project"></a>K vytvoření nového projektu Linux

K vytvoření nového projektu Linux v sadě Visual Studio, postupujte podle těchto kroků:

::: moniker range="vs-2019"

1. Vyberte **soubor > Nový projekt** v sadě Visual Studio nebo stisknutím klávesy **Ctrl + Shift + N**.
1. Nastavte **jazyk** k **C++** a vyhledejte položku "Linux". Vyberte typ projektu chcete vytvořit a klikněte na tlačítko **Další**. Zadejte **název** a **umístění**a zvolte **vytvořit**.

   ![Nového projektu Linux](media/newproject-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

1. Vyberte **soubor > Nový projekt** v sadě Visual Studio nebo stisknutím klávesy **Ctrl + Shift + N**.
1. Vyberte **Visual C++ > pro různé platformy > Linuxem** uzlu a pak vyberte typ projektu chcete vytvořit. Zadejte **název** a **umístění**a zvolte **OK**.

   ![Nového projektu Linux](media/newproject.png)

::: moniker-end

   | Typ projektu | Popis |
   | ------------ | --- |
   | **Blikání (Raspberry)**           | Projekt je určená pro Raspberry Pi zařízení, pomocí ukázkového kódu, který bliká kontrolku LED |
   | **Konzolová aplikace (Linux)** | Projekt je určená pro libovolný počítač s Linuxem se se vzorovým kódem, který zobrazí text do konzoly |
   | **Empty Project (Linux)**       | Projekt je určená pro libovolný počítač s Linuxem se bez ukázky kódu |
   | **Projekt makefile (Linux)**    | Projekt je určená pro libovolný počítač s Linuxem se vytvořené pomocí souboru pravidel standardní sestavovacího systému |

## <a name="next-steps"></a>Další kroky

[Konfigurace projektu Linux](configure-a-linux-project.md)
