---
title: "Uživatelské komponenty pro vzdálenou automatizaci | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DLLs [MFC], Automation
- Remote Automation [MFC], user components
ms.assetid: 601591cc-a442-440a-988e-baf3284b0d46
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3fa97dff482226c7a9e6554a0479eb76b25c47f1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="remote-automation-user-components"></a>Uživatelské komponenty pro vzdálenou automatizaci
Musíte zajistit, že každý klientský počítač obsahuje váš klientský program a všechny knihovny DLL vyžaduje podporu. Musíte také zkontrolujte, zda jsou aplikace serveru a jakékoli podpory knihovny DLL vyžaduje na počítači serveru. Nakonec musíte zajistit, že váš server program je zaregistrována na každý klientský počítač před RAC Manager lze spustit a nakonfigurovat připojení. Pokud program je Samoobslužná registrace (jak bude většina), třeba jenom spuštění programu serveru v klientském počítači a zaregistrujte ho. Pokud neexistuje možná budete muset provést registraci soubor, který zadáte, nebo ručně upravit registr.  
  
## <a name="see-also"></a>Viz také  
 [Správce automatizace (MFC)](../mfc/automation-manager-mfc.md)   
 [Správce připojení pro vzdálenou automatizaci](../mfc/remote-automation-connection-manager.md)   
 [Instalace vzdálené automatizace](../mfc/remote-automation-installation.md)

