---
title: Modelu COM + 1.0 podporovat v projekty knihovny ATL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.MTS
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3b55cb078dc5db1f0bf727a10f2a77ebfddd260
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="com-10-support-in-atl-projects"></a>Modelu COM + 1.0 podporovat v projekty knihovny ATL
Můžete použít [ATL – Průvodce projektem](../../atl/reference/creating-an-atl-project.md) k vytvoření projektu s základní podpora pro komponenty modelu COM + 1.0.  
  
 COM + 1.0 je určená pro vývoj distribuované aplikace na základě součástí. Také poskytuje infrastrukturu spuštění pro nasazení a správě těchto aplikací.  
  
 Pokud jste vybrali **podpory modelu COM + 1.0** zaškrtávací políčko, Průvodce upraví skriptu buildu v kroku odkaz. Konkrétně modelu COM + 1.0 projektu odkazy na následující knihovny:  
  
-   Comsvcs.lib  
  
-   Mtxguid.lib  
  
 Pokud jste vybrali **podpory modelu COM + 1.0** zaškrtávací políčko, můžete také vybrat **podporu součást registrátora**. Registrátor komponent umožňuje vaší objekt modelu COM + 1.0, který chcete získat seznam součástí, zaregistrovat součásti nebo zrušit registraci součásti (jednotlivě nebo všechny najednou).  
  
## <a name="see-also"></a>Viz také  
 [Základy ATL COM – objekty](../../atl/fundamentals-of-atl-com-objects.md)   
 [Programování s použitím knihovny ATL a běhového kódu jazyka C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)

