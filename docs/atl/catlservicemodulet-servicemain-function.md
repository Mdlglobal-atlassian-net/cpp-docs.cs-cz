---
title: Catlservicemodulet::servicemain – funkce | Dokumentace Microsoftu
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
ms.openlocfilehash: 9dff3fa3f3ed20406955570f2ad72531f4e44f11
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848118"
---
# <a name="catlservicemoduletservicemain-function"></a>Catlservicemodulet::servicemain – funkce
Volá správce řízení služeb (SCM) `ServiceMain` při otevření aplikace ovládacím panelu služby, vyberte službu a klikněte na **Start**.  
  
 Po SCM volá `ServiceMain`, služba musí poskytnout SCM funkci obslužné rutiny. Tato funkce umožňuje SCM získání stavu služby a předat konkrétní pokyny (jako je například pozastavení nebo ukončení). SCM získá tuto funkci, když se předá službě `_Handler` funkce rozhraní Win32 API [RegisterServiceCtrlHandler](http://msdn.microsoft.com/library/windows/desktop/ms685054). (`_Handler` je statickou členskou funkci, která volá nestatická členská funkce [obslužná rutina](../atl/reference/catlservicemodulet-class.md#handler).)  
  
 Při spuštění služby by měl také informovat SCM jeho aktuální stav. Dělá to pomocí předání do funkce rozhraní Win32 API SERVICE_START_PENDING [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241).  
  
 `ServiceMain` pak zavolá `CAtlExeModuleT::InitializeCom`, která volá funkce rozhraní Win32 API [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279). Ve výchozím nastavení `InitializeCom` předá COINIT_MULTITHREADED příznak funkce. Tento příznak určuje, že program má být server volných vláken.  
  
 Nyní `CAtlServiceModuleT::Run` je volána k provedení hlavní služby. `Run` pokračuje v provádění, dokud se tato služba zastavená.  
  
## <a name="see-also"></a>Viz také  
 [Služby](../atl/atl-services.md)   
 [Catlservicemodulet::servicemain –](../atl/reference/catlservicemodulet-class.md#servicemain)

