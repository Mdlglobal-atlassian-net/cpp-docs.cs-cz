---
title: Funkce CAtlServiceModuleT::Start | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CServiceModule.Start
- CServiceModule::Start
dev_langs: C++
helpviewer_keywords: Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c3eb7009e8092184effad5e1874297c8c04b213e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT::Start – funkce
Při spuštění služby **_tWinMain** volání **CAtlServiceModuleT::WinMain**, který volá `CAtlServiceModuleT::Start`.  
  
 `CAtlServiceModuleT::Start`Nastaví pole **SERVICE_TABLE_ENTRY** struktury, které mapují každé služby jeho spuštění funkce. Toto pole je pak předá funkci Win32 API [StartServiceCtrlDispatcher](http://msdn.microsoft.com/library/windows/desktop/ms686324). Teoreticky může zpracovat jeden EXE více služeb a pole může mít více **SERVICE_TABLE_ENTRY** struktury. V současné době však služby generované ATL podporuje pouze jedna služba za EXE. Proto pole má jeden záznam, který obsahuje název služby a **_ServiceMain** jako funkce spuštění. **_ServiceMain** je funkce statický člen `CAtlServiceModuleT` nestatické členské funkce, který volá `ServiceMain`.  
  
> [!NOTE]
>  Selhání **StartServiceCtrlDispatcher** k ovládacímu prvku service manager (SCM) pravděpodobně znamená, že program není spuštěn jako služba. V takovém případě, že program volá `CAtlServiceModuleT::Run` přímo tak, aby se může program spustit jako místní server. Další informace o spuštění programu jako místní server najdete v tématu [ladění tipy](../atl/debugging-tips.md).  
  
## <a name="see-also"></a>Viz také  
 [Služby](../atl/atl-services.md)   
 [CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)

