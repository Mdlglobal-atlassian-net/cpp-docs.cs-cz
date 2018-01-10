---
title: "Instalace vzdálené automatizace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Remote Automation [MFC], installation
- installing Remote Automation [MFC]
ms.assetid: 9a02c9f6-dfc6-4489-b240-a1afe25fa0c5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: acd8ee55261dfa03c68aef506dc90188d8d27d37
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="remote-automation-installation"></a>Instalace vzdálené automatizace
Vzdálená automatizace má poměrně málo součásti:  
  
-   Vzdálená automatizace klienta proxy server, AUTPRX32. KNIHOVNY DLL.  
  
-   Vzdálená automatizace serverovou komponentu, Správce automatizace AUTMGR32. SOUBOR EXE.  
  
-   RAC Manager RACMGR32. EXE s jeho odpovídající RACREG32. KNIHOVNY DLL.  
  
 Z nich RAC Manager je napsána v jazyce Visual Basic a musí proto Visual Basic Runtime podporuje. Tyto a další soubory vzdálené automatizace se instalační program nainstaluje při instalaci Visual C++ Enterprise Edition.  
  
 Pokud zkopírujete komponenty pro vzdálenou automatizaci k počítači na Visual C++ verze Enterprise Edition není nainstalovaná, ujistěte se, že REGSRV32. EXE v cestě počítače a zaregistrujte RACREG32. Knihovny DLL pomocí následující příkazový řádek:  
  
 REGSRVR32 RACREG32. KNIHOVNY DLL  
  
> [!NOTE]
>  Verze nástroje RAC Manager před Visual C++ 5.0 potřebné GUAGE32. OCX a TABCTL32. OCX. Ani jeden z nich je vyžadována pro verzi RAC Manager, který se dodává s Visual C++ Enterprise Edition, verze 5.0 nebo novější.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Správce automatizace](../mfc/automation-manager-mfc.md)  
  
 [Správce připojení pro vzdálenou automatizaci](../mfc/remote-automation-connection-manager.md)  
  
 [Uživatelské komponenty pro vzdálenou automatizaci](../mfc/remote-automation-user-components.md)  
  
## <a name="see-also"></a>Viz také  
 [Vzdálená automatizace](../mfc/remote-automation.md)

