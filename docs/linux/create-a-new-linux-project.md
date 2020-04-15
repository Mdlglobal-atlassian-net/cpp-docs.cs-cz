---
title: Vytvoření nového projektu C++ Linux v sadě Visual Studio
ms.date: 10/24/2019
description: Vytvořte nový projekt Linux založený na MSBuild v sadě Visual Studio.
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 1e79dd50756b71aabae7ccec75e57178898e7720
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364352"
---
# <a name="create-a-new-linux-project"></a>Vytvoření nového projektu Linux

::: moniker range="vs-2015"

Linuxové projekty jsou dostupné ve Visual Studiu 2017 a novějším.

::: moniker-end

::: moniker range="vs-2017"

Nejprve se ujistěte, že máte **nainstalovanou úlohu vývoje Linuxu** pro Visual Studio. Další informace naleznete v [tématu Stažení, instalace a nastavení úlohy Linuxu](download-install-and-setup-the-linux-development-workload.md).

Pro kompilaci napříč platformami doporučujeme použít CMake. Podpora CMake je v Sadě Visual Studio 2019 úplnější. Pokud CMake není možnost a máte existující řešení Windows Visual Studio, které chcete rozšířit na kompilaci pro Linux, můžete přidat projekt Visual Studio Linux do řešení systému Windows, spolu s projektem **sdílené položky.** Vložte kód, který je sdílen mezi oběma platformami v projektu sdílené položky a přidejte odkaz na tento projekt z projektů Windows a Linux.

## <a name="to-create-a-new-linux-project"></a>Vytvoření nového projektu Linuxu

Pokud chcete vytvořit nový linuxový projekt ve Visual Studiu 2017, postupujte takto:

1. Vyberte **Soubor > Nový projekt** v sadě Visual Studio nebo stiskněte **kombinaci kláves Ctrl + Shift + N**.
1. Vyberte **Visual C++ > Cross Platform >** uzle Linux a pak vyberte typ projektu, který chcete vytvořit. Zadejte **název** a **umístění**a zvolte **OK**.

   ![Nový linuxový projekt](media/newproject.png)

   | Typ projektu | Popis |
   | ------------ | --- |
   | **Blink (Malina)**           | Projekt zaměřený na zařízení Raspberry Pi se ukázkovým kódem, který bliká LED diodou |
   | **Konzolová aplikace (Linux)** | Projekt zaměřený na libovolný počítač s Linuxem s ukázkovým kódem, který vyvádí text do konzoly |
   | **Prázdný projekt (Linux)**       | Projekt zaměřený na jakýkoli počítač s Linuxem bez ukázkového kódu |
   | **Projekt Makefile (Linux)**    | Projekt zaměřený na jakýkoli počítač s Linuxem, postavený pomocí standardního systému sestavení Makefile |

## <a name="next-steps"></a>Další kroky

[Konfigurace projektu Linux](configure-a-linux-project.md)

::: moniker-end

::: moniker range="vs-2019"

Nejprve se ujistěte, že máte **nainstalovanou úlohu vývoje Linuxu** pro Visual Studio. Další informace naleznete v [tématu Stažení, instalace a nastavení úlohy Linuxu](download-install-and-setup-the-linux-development-workload.md).

Při vytváření nového projektu Jazyka C++ pro Linux v sadě Visual Studio můžete vytvořit projekt sady Visual Studio nebo projekt CMake. Tento článek popisuje, jak vytvořit projekt sady Visual Studio. Obecně platí pro nové projekty, které mohou zahrnovat open source kód nebo které máte v úmyslu zkompilovat pro vývoj napříč platformami, doporučujeme použít CMake s Visual Studio. S projektem CMake můžete vytvářet a ladit stejný projekt na Windows i Linux. Další informace naleznete v [tématu Vytvoření a konfigurace projektu Linux CMake Project](cmake-linux-project.md).

Pokud máte existující řešení Windows Visual Studio, které chcete rozšířit na kompilaci pro Linux a CMake není možnost, pak můžete přidat projekt Visual Studio Linux do řešení systému Windows, spolu s projektem **sdílené položky.** Vložte kód, který je sdílen mezi oběma platformami v projektu sdílené položky a přidejte odkaz na tento projekt z projektů Windows a Linux.

## <a name="to-create-a-new-linux-project"></a>Vytvoření nového projektu Linuxu

Pokud chcete vytvořit nový linuxový projekt ve Visual Studiu 2019, postupujte takto:

1. Vyberte **Soubor > Nový projekt** v sadě Visual Studio nebo stiskněte **kombinaci kláves Ctrl + Shift + N**.
1. Nastavte **jazyk** na **C++** a vyhledejte "Linux". Vyberte typ projektu, který chcete vytvořit, a pak zvolte **Další**. Zadejte **název** a **umístění**a zvolte **Vytvořit**.

   ![Nový linuxový projekt](media/newproject-vs2019.png)

   | Typ projektu | Popis |
   | ------------ | --- |
   | **Blink (Malina)**           | Projekt zaměřený na zařízení Raspberry Pi se ukázkovým kódem, který bliká LED diodou |
   | **Konzolová aplikace (Linux)** | Projekt zaměřený na libovolný počítač s Linuxem s ukázkovým kódem, který vyvádí text do konzoly |
   | **Prázdný projekt (Linux)**       | Projekt zaměřený na jakýkoli počítač s Linuxem bez ukázkového kódu |
   | **Projekt Makefile (Linux)**    | Projekt zaměřený na jakýkoli počítač s Linuxem, postavený pomocí standardního systému sestavení Makefile |

## <a name="next-steps"></a>Další kroky

[Konfigurace projektu Linux](configure-a-linux-project.md)

::: moniker-end
