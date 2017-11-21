---
title: "Spuštění programu jako místní Server | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 131bfefb35164b2d1e53f5671016235e5426c096
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="running-the-program-as-a-local-server"></a>Spuštění programu jako místní Server
Pokud spuštění programu jako služba nepohodlná, můžete dočasně změnit registr tak, aby spuštění programu jako normální místní server. Jednoduše přejmenovat `LocalService` hodnotu v rámci vaší AppID, který `_LocalService` a ujistěte se, `LocalServer32` klíč v rámci vaší CLSID nastavena správně. (Všimněte si, že vaše aplikace by měla spustit v jiném počítači pomocí DCOMCNFG přejmenuje vaše `LocalServer32` klíče na `_LocalServer32`.) S vaším programem jako místní server využívá několik dalších sekund při spuštění, protože volání **StartServiceCtrlDispatcher** v `CAtlServiceModuleT::Start` trvá několik sekund, než se nezdaří.  
  
## <a name="see-also"></a>Viz také  
 [Ladění tipy](../atl/debugging-tips.md)

