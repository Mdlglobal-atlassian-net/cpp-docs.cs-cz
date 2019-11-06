---
title: Vytvoření nového C++ projektu pro Linux v aplikaci Visual Studio
ms.date: 10/24/2019
description: Vytvořte nový projekt pro Linux založený na MSBuildu v aplikaci Visual Studio.
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 5d5fa67566d86edb2ed0389fdbe38866b47e2211
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626726"
---
# <a name="create-a-new-linux-project"></a>Vytvoření nového projektu Linux

::: moniker range="vs-2015"

Projekty Linux jsou k dispozici v aplikaci Visual Studio 2017 nebo novější.

::: moniker-end

::: moniker range="vs-2017"

Nejdřív se ujistěte, že máte nainstalovanou **úlohu vývoje pro Linux** pro Visual Studio. Další informace najdete v tématu [stažení, instalace a nastavení úlohy pro Linux](download-install-and-setup-the-linux-development-workload.md).

Pro kompilaci mezi platformami doporučujeme používat CMake. Podpora CMake je více dokončená v sadě Visual Studio 2019. Pokud CMake není možnost a máte stávající řešení Windows Visual Studio, které chcete pro kompilaci pro Linux nasadit, můžete do řešení systému Windows přidat projekt sady Visual Studio Linux společně s projektem **sdílených položek** . Vložte kód, který je sdílen mezi oběma platformami v projektu sdílené položky a přidejte odkaz na tento projekt z projektů pro Windows a Linux.

## <a name="to-create-a-new-linux-project"></a>Vytvoření nového projektu pro Linux

Chcete-li vytvořit nový projekt pro Linux v aplikaci Visual Studio 2017, postupujte podle následujících kroků:

1. Vyberte **soubor > nový projekt** v aplikaci Visual Studio nebo stiskněte klávesy **CTRL + SHIFT + N**.
1. Vyberte uzel **Visual C++ > pro různé platformy > Linux** a potom vyberte typ projektu, který chcete vytvořit. Zadejte **název** a **umístění**a klikněte na **tlačítko OK**.

   ![Nový projekt pro Linux](media/newproject.png)

   | Typ projektu | Popis |
   | ------------ | --- |
   | **Blikání (Malina)**           | Projekt, který je zaměřený na zařízení malin. PI s ukázkovým kódem, který zabliká LED |
   | **Konzolová aplikace (Linux)** | Projekt, který je zaměřený na jakýkoli počítač se systémem Linux, s ukázkovým kódem, který do konzoly vypíše text |
   | **Prázdný projekt (Linux)**       | Projekt, který je zaměřený na jakýkoli počítač se systémem Linux bez ukázkového kódu |
   | **Projekt makefile (Linux)**    | Projekt, který je zaměřený na jakýkoli počítač se systémem Linux, sestavený pomocí standardního systému sestavení makefile |

## <a name="next-steps"></a>Další kroky

[Konfigurace projektu Linux](configure-a-linux-project.md)

::: moniker-end

::: moniker range="vs-2019"

Nejdřív se ujistěte, že máte nainstalovanou **úlohu vývoje pro Linux** pro Visual Studio. Další informace najdete v tématu [stažení, instalace a nastavení úlohy Linux](download-install-and-setup-the-linux-development-workload.md).

Při vytváření nového C++ projektu pro Linux v sadě Visual Studio můžete zvolit vytvoření projektu sady Visual Studio nebo projektu cmake. Tento článek popisuje, jak vytvořit projekt sady Visual Studio. Obecně platí, že pro nové projekty, které mohou zahrnovat open source kód nebo které máte v úmyslu kompilovat pro vývoj pro různé platformy, doporučujeme používat CMake v sadě Visual Studio. Pomocí projektu CMake můžete sestavit a ladit stejný projekt v systému Windows i Linux. Další informace najdete v tématu [Vytvoření a konfigurace projektu Linux cmake](cmake-linux-project.md).

Máte-li existující řešení sady Windows Visual Studio, které byste chtěli zkompilovat pro systém Linux, a CMake není možnost, můžete přidat projekt sady Visual Studio Linux do řešení systému Windows společně s projektem **sdílených položek** . Vložte kód, který je sdílen mezi oběma platformami v projektu sdílené položky a přidejte odkaz na tento projekt z projektů pro Windows a Linux.

## <a name="to-create-a-new-linux-project"></a>Vytvoření nového projektu pro Linux

Chcete-li vytvořit nový projekt pro Linux v aplikaci Visual Studio 2019, postupujte podle následujících kroků:

1. Vyberte **soubor > nový projekt** v aplikaci Visual Studio nebo stiskněte klávesy **CTRL + SHIFT + N**.
1. Nastavte **jazyk** na **C++** a vyhledejte "Linux". Vyberte typ projektu, který chcete vytvořit, a klikněte na tlačítko **Další**. Zadejte **název** a **umístění**a klikněte na **vytvořit**.

   ![Nový projekt pro Linux](media/newproject-vs2019.png)

   | Typ projektu | Popis |
   | ------------ | --- |
   | **Blikání (Malina)**           | Projekt, který je zaměřený na zařízení malin. PI s ukázkovým kódem, který zabliká LED |
   | **Konzolová aplikace (Linux)** | Projekt, který je zaměřený na jakýkoli počítač se systémem Linux, s ukázkovým kódem, který do konzoly vypíše text |
   | **Prázdný projekt (Linux)**       | Projekt, který je zaměřený na jakýkoli počítač se systémem Linux bez ukázkového kódu |
   | **Projekt makefile (Linux)**    | Projekt, který je zaměřený na jakýkoli počítač se systémem Linux, sestavený pomocí standardního systému sestavení makefile |

## <a name="next-steps"></a>Další kroky

[Konfigurace projektu Linux](configure-a-linux-project.md)

::: moniker-end
