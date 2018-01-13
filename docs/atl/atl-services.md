---
title: "Služby ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CServiceModule
dev_langs: C++
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d13eebbe96ba57c82e3bf1c360b0cb471a6bd975
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="atl-services"></a>ATL Services
K vytvoření objektu ATL COM tak, aby běžel v službě, jednoduše služby (EXE) vyberte ze seznamu možností serveru v Průvodci projektu knihovny ATL. Průvodce potom vytvoří třídy odvozené od `CAtlServiceModuleT` tuto službu implementovat.  
  
 Když je objekt knihovny ATL COM sestavena jako služba, bude registrovat jenom jako místní server, a nebude se zobrazovat v seznamu služeb v Ovládacích panelech. Je to proto, že je snazší ladění služby jako místní server než jako služba. Ji nainstalovat jako službu, spusťte na příkazovém řádku následující:  
  
 `YourEXE``.exe /Service`  
  
 Ho odinstalovat, spusťte následující:  
  
 `YourEXE``.exe /UnregServer`  
  
 První čtyři témata v této části popisují akce, ke kterým došlo během provádění `CAtlServiceModuleT` členské funkce. Tato témata se zobrazí ve stejném pořadí jako funkce se běžně označují jako. Pokud chcete zlepšit pochopení těchto témat, je vhodné použít zdrojový kód je vygenerovat průvodcem ATL projektu jako odkaz. Tato první čtyři témata jsou:  
  

-   [Funkce CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)  
  
-   [Funkce CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)  
  
-   [Funkce CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)  
  
-   [Funkce CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)  
  
 Poslední tři témata popisují koncepty související s vývojem služby:  
  
-   [Položky registru](../atl/registry-entries.md) pro služby ATL  
  
-   [DCOMCNFG](../atl/dcomcnfg.md)  
  
-   [Ladění tipy](../atl/debugging-tips.md) pro služby ATL  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)

