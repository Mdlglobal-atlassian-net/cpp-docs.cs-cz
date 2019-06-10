---
title: Připojení ke vzdálenému počítači s Linuxem v sadě Visual Studio
description: Jak se připojit ke vzdálenému počítači Linux z uvnitř projektu Visual Studio C++.
ms.date: 06/07/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 6348681ecc8e6f7863b2119810db24879526a1c6
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821609"
---
# <a name="connect-to-your-remote-linux-computer"></a>Připojení ke vzdálenému počítači s Linuxem

::: moniker range="vs-2015"

Podpora Linuxu je k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

::: moniker range="vs-2019"

Pokud cílíte subsystém Windows pro Linux (WSL) sady Visual Studio spolupracuje s vaší distribuce Linuxu přímo prostřednictvím systému souborů. žádné vzdálené připojení je nezbytné.

::: moniker-end

Při sestavování C++ projektu Linux pro vzdálený systém Linux (virtuální nebo fyzický počítač), Linux, se zkopíruje do vzdálenému počítači s Linuxem a potom zkompiluje kód podle nastavení sady Visual Studio. Nastavení tohoto vzdáleného připojení:

1. Prvním sestavení projektu nebo ručně vytvořit nový záznam výběrem **nástroje > Možnosti** a pak otevřete **různé platformy > Správce připojení** uzel a klikněte na tlačítko **přidat** tlačítko.

   ![Správce připojení](media/settings_connectionmanager.png)

   V obou scénářích **připojit ke vzdálenému systému** zobrazí se okno.

   ![Připojit ke vzdálenému systému](media/connect.png)

1. Zadejte následující informace:

   | Entry | Popis
   | ----- | ---
   | **Název hostitele**           | Název nebo IP adresa cílového zařízení
   | **Port**                | Port, na kterém běží služba SSH na obvykle 22
   | **Uživatelské jméno**           | Ověření jako
   | **Typ ověřování** | Heslo nebo privátní klíč jsou podporované
   | **Heslo**            | Heslo pro zadané uživatelské jméno
   | **Souboru s privátním klíčem**    | Soubor privátního klíče vytvořené pro ssh připojení
   | **Přístupové heslo**          | Heslo s privátním klíčem výše vybraného

1. Klikněte na tlačítko **připojit** tlačítko pokusu o připojení ke vzdálenému počítači.  Pokud se nepovede, vstupní pole, které je potřeba změnit bude označeno červeně.

   ![Chyba Správce připojení](media/settings_connectionmanagererror.png)