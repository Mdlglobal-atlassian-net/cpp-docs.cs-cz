---
title: "Uživatelské komponenty pro vzdálenou automatizaci | Microsoft Docs"
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
- DLLs [MFC], Automation
- Remote Automation [MFC], user components
ms.assetid: 601591cc-a442-440a-988e-baf3284b0d46
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2f82fe529586579109434da447e26b15dcb9503a
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="remote-automation-user-components"></a>Uživatelské komponenty pro vzdálenou automatizaci
Musíte zajistit, že každý klientský počítač obsahuje váš klientský program a všechny knihovny DLL vyžaduje podporu. Musíte také zkontrolujte, zda jsou aplikace serveru a jakékoli podpory knihovny DLL vyžaduje na počítači serveru. Nakonec musíte zajistit, že váš server program je zaregistrována na každý klientský počítač před RAC Manager lze spustit a nakonfigurovat připojení. Pokud program je Samoobslužná registrace (jak bude většina), třeba jenom spuštění programu serveru v klientském počítači a zaregistrujte ho. Pokud neexistuje možná budete muset provést registraci soubor, který zadáte, nebo ručně upravit registr.  
  
## <a name="see-also"></a>Viz také  
 [Správce automatizace (MFC)](../mfc/automation-manager-mfc.md)   
 [Správce připojení pro vzdálenou automatizaci](../mfc/remote-automation-connection-manager.md)   
 [Instalace vzdálené automatizace](../mfc/remote-automation-installation.md)

