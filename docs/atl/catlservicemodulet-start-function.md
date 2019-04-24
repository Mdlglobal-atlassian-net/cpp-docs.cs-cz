---
title: CAtlServiceModuleT::Start Function
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: 204d02a1122ee78b38850bedae5f98b1f338ab1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250742"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT::Start Function

Když je služba spuštěna, `_tWinMain` volání `CAtlServiceModuleT::WinMain`, která pak volá `CAtlServiceModuleT::Start`.

`CAtlServiceModuleT::Start` Nastaví pole `SERVICE_TABLE_ENTRY` struktury, které mapují každé služby na její spuštění funkce. Toto pole je pak předán do funkce rozhraní Win32 API [StartServiceCtrlDispatcher](/windows/desktop/api/winsvc/nf-winsvc-startservicectrldispatchera). Teoreticky vzato jedné EXE dokáže zpracovat víc služeb a pole může mít více `SERVICE_TABLE_ENTRY` struktury. V současné době ale služby generované ATL podporuje jenom jednu službu za EXE. Proto pole má jednu položku, která obsahuje název služby a `_ServiceMain` jako spouštěcí funkci. `_ServiceMain` je statická členská funkce `CAtlServiceModuleT` nestatická členská funkce, který volá `ServiceMain`.

> [!NOTE]
>  Selhání `StartServiceCtrlDispatcher` pro připojení k řízení služeb manager (SCM) pravděpodobně znamená, že není program spuštěn jako služba. V tomto případě, že program volá `CAtlServiceModuleT::Run` přímo tak, aby se program může spustit jako místního serveru. Další informace o spuštění programu jako místního serveru najdete v tématu [tipy k ladění](../atl/debugging-tips.md).

## <a name="see-also"></a>Viz také:

[Služby](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
