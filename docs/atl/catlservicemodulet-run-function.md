---
title: Funkce CAtlServiceModuleT::Run | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
dev_langs: C++
helpviewer_keywords: ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 383b054314982a0828d51083a904ccb2f7ddb5d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="catlservicemoduletrun-function"></a>CAtlServiceModuleT::Run – funkce
**Spustit** obsahuje volání `PreMessageLoop`, `RunMessageLoop`, a `PostMessageLoop`. Po volání, `PreMessageLoop` nejprve ukládá ID služby vlákna. Služba bude používat toto ID zavřete samotné odesláním **WM_QUIT** zprávu pomocí funkce rozhraní Win32 API [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946).  
  
 `PreMessageLoop`pak zavolá `InitializeSecurity`. Ve výchozím nastavení `InitializeSecurity` volání [u funkce CoInitializeSecurity](http://msdn.microsoft.com/library/windows/desktop/ms693736) s popisovač zabezpečení nastaven na hodnotu NULL, což znamená, že každý uživatel má přístup k objektu.  
  
 Pokud nechcete, aby službu, kterou chcete zadat vlastní zabezpečení, mají přednost před `PreMessageLoop` a nemůžete volat `InitializeSecurity`, a pak COM určí nastavení zabezpečení z registru. Pohodlný způsob, jak nakonfigurovat nastavení registru je [DCOMCNFG](../atl/dcomcnfg.md) nástroje, které jsou uvedeny dále v této části.  
  
 Po zabezpečení je zadaný objekt je zaregistrovat u modelu COM, aby noví klienti připojovat k programu. Nakonec program informuje správce řízení služeb (SCM), zda je spuštěná a program smyčce zpráv. Program zůstane spuštěný, dokud ji odešle zprávu ukončit po vypnutí služby.  
  
## <a name="see-also"></a>Viz také  
 [Služby](../atl/atl-services.md)   
 [CSecurityDesc – třída](../atl/reference/csecuritydesc-class.md)   
 [Identifikační číslo volané stanice – třída](../atl/reference/csid-class.md)   
 [CDacl – třída](../atl/reference/cdacl-class.md)   
 [CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)

