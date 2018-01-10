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
ms.workload: cplusplus
ms.openlocfilehash: 3e398bfed0174e4ec2a262ea03076ed17881f900
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="running-the-program-as-a-local-server"></a>Spuštění programu jako místní Server
Pokud spuštění programu jako služba nepohodlná, můžete dočasně změnit registr tak, aby spuštění programu jako normální místní server. Jednoduše přejmenovat `LocalService` hodnotu v rámci vaší AppID, který `_LocalService` a ujistěte se, `LocalServer32` klíč v rámci vaší CLSID nastavena správně. (Všimněte si, že vaše aplikace by měla spustit v jiném počítači pomocí DCOMCNFG přejmenuje vaše `LocalServer32` klíče na `_LocalServer32`.) S vaším programem jako místní server využívá několik dalších sekund při spuštění, protože volání **StartServiceCtrlDispatcher** v `CAtlServiceModuleT::Start` trvá několik sekund, než se nezdaří.  
  
## <a name="see-also"></a>Viz také  
 [Tipy pro ladění](../atl/debugging-tips.md)

