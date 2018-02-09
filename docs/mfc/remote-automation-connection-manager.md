---
title: "Správce připojení pro vzdálenou automatizaci | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Automation clients [MFC], configuring for Remote Automation
- registry [MFC], remote Automation
- Automation servers [MFC], configuring for Remote Automation
- Remote Automation Connection Manager [MFC]
- Remote Automation [MFC], configuring client and server machines
- RAC Manager tool [MFC]
ms.assetid: 562eb7bc-f95c-46ad-ac97-f0dfa98362af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee78c1fb5c66974c946d0571db981d899f405fe3
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="remote-automation-connection-manager"></a>Správce připojení pro vzdálenou automatizaci
Chcete-li nakonfigurovat klienta a serveru, musíte provést změny v registru. Místo díky tomuto ručně, je mnohem snazší pomocí nástroje Správce připojení vzdálené automatizace (RAC). Tento nástroj RACMGR32. EXE, společně s RACREG32. DLL, musí být zkopírován do libovolného adresáře, který zvolíte. Vložíte ho v CESTĚ, mohou být provedeny z hlavního panelu použít příkaz spustit. Alternativně můžete vytvořit zástupce nebo umístit na něj odkaz v nabídce Start.  
  
 RACMGR32 je napsán v jazyce Visual Basic a proto potřebuje některé jazyka Visual Basic podporují knihovny DLL. Tyto soubory jsou umístěny ve stejném adresáři jako RACMGR32. EXE na disku CD-ROM. Verze těchto souborů, které jsou nainstalované při instalaci pro Visual C++ Enterprise Edition jsou ekvivalentní, nebo novější než ty, které dodává s Visual Basic Enterprise Edition 5.0. Instalace Visual C++ zkopíruje nové verze souborů jazyka Visual Basic do systémového adresáře, který je obvykle C:\Windows\System32. Instalační program také zaregistruje tyto soubory s operačním systémem. Můžete je odebrat z instalace jazyka Visual Basic.  
  
## <a name="see-also"></a>Viz také  
 [Správce automatizace (MFC)](../mfc/automation-manager-mfc.md)   
 [Uživatelské komponenty pro vzdálenou automatizaci](../mfc/remote-automation-user-components.md)   
 [Instalace vzdálené automatizace](../mfc/remote-automation-installation.md)

