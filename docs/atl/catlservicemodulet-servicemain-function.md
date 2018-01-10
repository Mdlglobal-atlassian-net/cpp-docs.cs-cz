---
title: Funkce CAtlServiceModuleT::ServiceMain | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ServiceMain
- CServiceModule::ServiceMain
- CServiceModule.ServiceMain
dev_langs: C++
helpviewer_keywords: ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 633e9bc4689ced93e1c22151b32654f7ae9d7ece
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT::ServiceMain – funkce
Volá správce řízení služeb (SCM) `ServiceMain` při otevření aplikace služby ovládacích panelů, vyberte službu a klikněte na **spustit**.  
  
 Po SCM volá `ServiceMain`, služba musí dát SCM funkce obslužné rutiny. Tato funkce umožňuje SCM získání stavu služby a předat konkrétní pokyny (například pozastavení nebo ukončení). SCM získá tuto funkci, když služba předá **_Handler** funkce rozhraní API Win32 [RegisterServiceCtrlHandler](http://msdn.microsoft.com/library/windows/desktop/ms685054). (**_Handler** je funkce statický člen, který volá nestatické členské funkce [obslužná rutina](../atl/reference/catlservicemodulet-class.md#handler).)  
  
 Při spuštění služby by měl také informovat o tom, SCM jeho aktuálního stavu. Dělá to pomocí předání **SERVICE_START_PENDING** funkce rozhraní API Win32 [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241).  
  
 `ServiceMain`pak zavolá `CAtlExeModuleT::InitializeCom`, která volá funkce rozhraní Win32 API [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279). Ve výchozím nastavení `InitializeCom` předá **COINIT_MULTITHREADED** příznak funkce. Tento příznak označuje, že tento program je jako podprocesy serveru.  
  
 Nyní `CAtlServiceModuleT::Run` je volána pro práci hlavní služby. **Spustit** bude pokračovat v provádění, dokud služba je zastavena.  
  
## <a name="see-also"></a>Viz také  
 [Služby](../atl/atl-services.md)   
 [CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)

