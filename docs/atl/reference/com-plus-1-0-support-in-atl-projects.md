---
title: Modelu COM + 1.0 podporovat v projekty knihovny ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.MTS
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3440d3ed2e3244b35588d5c07fd181f1ad2f082
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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

