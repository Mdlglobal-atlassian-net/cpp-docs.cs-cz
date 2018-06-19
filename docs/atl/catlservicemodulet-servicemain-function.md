---
title: Funkce CAtlServiceModuleT::ServiceMain | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- ServiceMain
- CServiceModule::ServiceMain
- CServiceModule.ServiceMain
dev_langs:
- C++
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9936090793890b1e33f0d5e29787d65f378afa84
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355571"
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT::ServiceMain – funkce
Volá správce řízení služeb (SCM) `ServiceMain` při otevření aplikace služby ovládacích panelů, vyberte službu a klikněte na **spustit**.  
  
 Po SCM volá `ServiceMain`, služba musí dát SCM funkce obslužné rutiny. Tato funkce umožňuje SCM získání stavu služby a předat konkrétní pokyny (například pozastavení nebo ukončení). SCM získá tuto funkci, když služba předá **_Handler** funkce rozhraní API Win32 [RegisterServiceCtrlHandler](http://msdn.microsoft.com/library/windows/desktop/ms685054). (**_Handler** je funkce statický člen, který volá nestatické členské funkce [obslužná rutina](../atl/reference/catlservicemodulet-class.md#handler).)  
  
 Při spuštění služby by měl také informovat o tom, SCM jeho aktuálního stavu. Dělá to pomocí předání **SERVICE_START_PENDING** funkce rozhraní API Win32 [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241).  
  
 `ServiceMain` pak zavolá `CAtlExeModuleT::InitializeCom`, která volá funkce rozhraní Win32 API [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279). Ve výchozím nastavení `InitializeCom` předá **COINIT_MULTITHREADED** příznak funkce. Tento příznak označuje, že tento program je jako podprocesy serveru.  
  
 Nyní `CAtlServiceModuleT::Run` je volána pro práci hlavní služby. **Spustit** bude pokračovat v provádění, dokud služba je zastavena.  
  
## <a name="see-also"></a>Viz také  
 [Služby](../atl/atl-services.md)   
 [CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)

