---
title: Připojení ke vzdálenému počítači s Linuxem v sadě Visual Studio | Dokumentace Microsoftu
description: Jak se připojit ke vzdálenému počítači Linux z uvnitř projektu Visual Studio C++.
ms.custom: ''
ms.date: 07/20/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 387550fa7d3e745038d0be8ee66574d4496132a0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061285"
---
# <a name="connect-to-your-remote-linux-computer"></a>Připojení ke vzdálenému počítači s Linuxem

Při sestavování projektu C++ Linux v sadě Visual Studio, na základě nastavení sady Visual Studio na Linuxu se zkopíruje do vzdálenému počítači s Linuxem a potom zkompiluje kód. Nastavení tohoto vzdáleného připojení:

1. Prvním sestavení projektu nebo ručně vytvořit nový záznam výběrem **nástroje > Možnosti** a pak otevřete **různé platformy > Správce připojení** uzel a klikněte na tlačítko **přidat** tlačítko.

   ![Správce připojení](media/settings_connectionmanager.png)

   V obou scénářích **připojit ke vzdálenému systému** zobrazí se okno.

   ![Připojit ke vzdálenému systému](media/connect.png)

1. Zadejte následující informace:

   | Položka | Popis
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