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
ms.openlocfilehash: 5e6a5dd4a00bd4d98c36222434d7cd83242905c9
ms.sourcegitcommit: db6b2ad3195e71abfb60b62f3f015f08b0a719d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410756"
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