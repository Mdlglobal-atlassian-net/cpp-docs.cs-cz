---
title: "Vzdálená automatizace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC COM, Remote Automation
- Automation objects [MFC]
- DCOM [MFC], Remote Automation
- Automation objects [MFC], creating
- Remote Automation [MFC]
- MFC, COM support
- Automation controller [MFC]
- COM, Remote Automation [MFC]
ms.assetid: 363f87fb-08fa-4458-b089-b46365a6d4f2
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 123c8a2d9bcf45d28817e0e9256a86748eae97ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="remote-automation"></a>Vzdálená automatizace
> [!NOTE]
>  Vzdálená automatizace je technologie zastaralé a by nemělo být použito pro nové aplikace. Visual C++ nepodporuje systém Windows 95. Případy, ve kterých by potřebujete podporovat vzdálené automatizace jsou popsané v [kde nepodporuje vzdálené automatizace přizpůsobit v](where-does-remote-automation-fit-in-q.md).  
  
 Vzdálená automatizace je typ [automatizace](../mfc/automation.md) umožňuje příjemce rozhraní provést poskytovatele rozhraní, který se nachází na jiném počítači, například v síti.  
  
 Tento článek vysvětluje, jak vytvořit objekty automatizace, které můžete vyvolat a provést vzdáleně a postup vytvoření automatizace řadiče, které můžete použít tyto objekty vzdálené automatizace. Také prozkoumá možnosti konfigurace a odkazuje na hlavní rozdíly mezi vzdálené automatizace a modelu DCOM (distributed verze COM a OLE, který umožňuje rozhraní, které se nevztahují na automatizace pro vyvolání a provést vzdáleně).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Historie modelu DCOM (Distributed Component Object Model)](../mfc/history-of-dcom.md)  
  
 [Kde se uplatní Vzdálená automatizace?](where-does-remote-automation-fit-in-q.md)  
  
 [Co přínosy vzdálené automatizace](what-does-remote-automation-provide-q.md)  
  
 [Zabezpečení vzdálené automatizace](../mfc/security-in-remote-automation.md)  
  
 [Modely dělení na vlákna](../mfc/remote-automation-threading-models.md)  
  
 [Instalace](../mfc/remote-automation-installation.md)  
  
 [Správce automatizace](../mfc/automation-manager-mfc.md)  
  
-   [Správce připojení pro vzdálenou automatizaci](../mfc/remote-automation-connection-manager.md)  
  
-   [Uživatelské komponenty pro vzdálenou automatizaci](../mfc/remote-automation-user-components.md)  
  
 [Vytváření programů využívajících vzdálenou automatizaci](../mfc/creating-programs-that-use-remote-automation.md)  
  
 [Spuštění vzdálené automatizace s použitím příkazů AUTOCLIK a AUTODRIV](../mfc/running-remote-automation-using-autoclik-and-autodriv.md)  
  
## <a name="see-also"></a>Viz také  
 [MFC COM](../mfc/mfc-com.md)   
 [Automatizace](../mfc/automation.md)
