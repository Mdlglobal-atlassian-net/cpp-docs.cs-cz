---
title: CAtlServiceModuleT::Spustit funkci
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: 50054bbb34bcc31a1d11dd8bfab797f98e4e82f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317282"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT::Spustit funkci

Při spuštění služby `_tWinMain` `CAtlServiceModuleT::WinMain`volání , které `CAtlServiceModuleT::Start`zase volání .

`CAtlServiceModuleT::Start`nastaví pole `SERVICE_TABLE_ENTRY` struktur, které mapují každou službu na její funkci při spuštění. Toto pole je pak předáno funkci Rozhraní API Win32 [StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw). Teoreticky jeden EXE by mohl zpracovat více `SERVICE_TABLE_ENTRY` služeb a pole může mít více struktur. V současné době však služba generované atl podporuje pouze jednu službu na EXE. Proto pole má jednu položku, která `_ServiceMain` obsahuje název služby a jako funkce při spuštění. `_ServiceMain`je statická členská `CAtlServiceModuleT` funkce, která volá `ServiceMain`nestatickou členovou funkci .

> [!NOTE]
> Selhání `StartServiceCtrlDispatcher` připojení k správci řízení služeb (SCM) pravděpodobně znamená, že program není spuštěn jako služba. V tomto případě program `CAtlServiceModuleT::Run` volá přímo tak, aby program mohl běžet jako místní server. Další informace o spuštění programu jako místního serveru naleznete v [tématu Tipy pro ladění](../atl/debugging-tips.md).

## <a name="see-also"></a>Viz také

[Služby](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
