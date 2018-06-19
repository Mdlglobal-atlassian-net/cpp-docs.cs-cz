---
title: Funkce CAtlServiceModuleT::Start | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule.Start
- CServiceModule::Start
dev_langs:
- C++
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da8d7358c634416941a551c93c6a2772549a3fd2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357274"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT::Start – funkce
Při spuštění služby **_tWinMain** volání **CAtlServiceModuleT::WinMain**, který volá `CAtlServiceModuleT::Start`.  
  
 `CAtlServiceModuleT::Start` Nastaví pole **SERVICE_TABLE_ENTRY** struktury, které mapují každé služby jeho spuštění funkce. Toto pole je pak předá funkci Win32 API [StartServiceCtrlDispatcher](http://msdn.microsoft.com/library/windows/desktop/ms686324). Teoreticky může zpracovat jeden EXE více služeb a pole může mít více **SERVICE_TABLE_ENTRY** struktury. V současné době však služby generované ATL podporuje pouze jedna služba za EXE. Proto pole má jeden záznam, který obsahuje název služby a **_ServiceMain** jako funkce spuštění. **_ServiceMain** je funkce statický člen `CAtlServiceModuleT` nestatické členské funkce, který volá `ServiceMain`.  
  
> [!NOTE]
>  Selhání **StartServiceCtrlDispatcher** k ovládacímu prvku service manager (SCM) pravděpodobně znamená, že program není spuštěn jako služba. V takovém případě, že program volá `CAtlServiceModuleT::Run` přímo tak, aby se může program spustit jako místní server. Další informace o spuštění programu jako místní server najdete v tématu [ladění tipy](../atl/debugging-tips.md).  
  
## <a name="see-also"></a>Viz také  
 [Služby](../atl/atl-services.md)   
 [CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)

