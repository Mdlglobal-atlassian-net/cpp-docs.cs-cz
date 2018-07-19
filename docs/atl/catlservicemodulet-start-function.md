---
title: Catlservicemodulet::Start – funkce | Dokumentace Microsoftu
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
ms.openlocfilehash: 5ef614f4cbc3f097e6f790a49c0b599817f9b59c
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849182"
---
# <a name="catlservicemoduletstart-function"></a>Catlservicemodulet::Start – funkce
Když je služba spuštěna, `_tWinMain` volání `CAtlServiceModuleT::WinMain`, která pak volá `CAtlServiceModuleT::Start`.  
  
 `CAtlServiceModuleT::Start` Nastaví pole `SERVICE_TABLE_ENTRY` struktury, které mapují každé služby na její spuštění funkce. Toto pole je pak předán do funkce rozhraní Win32 API [StartServiceCtrlDispatcher](http://msdn.microsoft.com/library/windows/desktop/ms686324). Teoreticky vzato jedné EXE dokáže zpracovat víc služeb a pole může mít více `SERVICE_TABLE_ENTRY` struktury. V současné době ale služby generované ATL podporuje jenom jednu službu za EXE. Proto pole má jednu položku, která obsahuje název služby a `_ServiceMain` jako spouštěcí funkci. `_ServiceMain` je statická členská funkce `CAtlServiceModuleT` nestatická členská funkce, který volá `ServiceMain`.  
  
> [!NOTE]
>  Selhání `StartServiceCtrlDispatcher` pro připojení k řízení služeb manager (SCM) pravděpodobně znamená, že není program spuštěn jako služba. V tomto případě, že program volá `CAtlServiceModuleT::Run` přímo tak, aby se program může spustit jako místního serveru. Další informace o spuštění programu jako místního serveru najdete v tématu [tipy k ladění](../atl/debugging-tips.md).  
  
## <a name="see-also"></a>Viz také  
 [Služby](../atl/atl-services.md)   
 [Catlservicemodulet::Start –](../atl/reference/catlservicemodulet-class.md#start)

