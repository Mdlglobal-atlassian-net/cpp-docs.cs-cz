---
title: "Připojení k vzdáleného počítače Linux | Microsoft Docs"
ms.custom: 
ms.date: 11/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 4ff19875064302e891236c931f28ebef630904e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="connect-to-your-remote-linux-computer"></a>Připojení k vzdáleného počítače Linux

Při vytváření, Linux kód se zkopíruje do vzdáleného počítače Linux a pak zkompilovány v daném systému podle nastavení vybraná v sadě Visual Studio.  K nastavení tohoto vzdáleného připojení:

1. Sestavení projektu poprvé nebo ručně vytvořte novou položku výběrem **nástroje > Možnosti** a pak otevřete **křížové platformy > Správce připojení** uzel a klikněte na tlačítko **přidat** tlačítko.

   ![Správce připojení](media/settings_connectionmanager.png)

   V obou těchto případech **připojit ke vzdálenému systému** okno se zobrazí.
   
   ![Připojení do vzdáleného systému](media/connect.png)

1. Zadejte následující informace:

   | Položka | Popis
   | ----- | ---
   | **Název hostitele**           | Název nebo IP adresa cílového zařízení
   | **Port**                | Port, který běží služba SSH na obvykle 22
   | **Uživatelské jméno**           | Ověření jako uživatele
   | **Typ ověřování** | Heslo nebo privátní klíč jsou podporované
   | **Heslo**            | Heslo pro zadané uživatelské jméno
   | **Soubor privátního klíče**    | Privátní klíč pro vytvořit ssh připojení
   | **Přístupové heslo**          | Přístupové heslo používané s privátním klíčem vybraném výše

1. Klikněte **Connect** tlačítko pokusu o připojení ke vzdálenému počítači.  Pokud se nepovede připojit, vstupní pole, které je třeba změnit bude označeno červeně.

   ![Chyba Správce připojení](media/settings_connectionmanagererror.png)