---
title: 'CAtlServiceModuleT:: Start – funkce'
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: e6de15f40e89bfffba504db04ee7a16b2a68cac9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491667"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT:: Start – funkce

Při spuštění `_tWinMain` služby volání `CAtlServiceModuleT::WinMain`, která zase volá `CAtlServiceModuleT::Start`.

`CAtlServiceModuleT::Start`nastaví pole `SERVICE_TABLE_ENTRY` struktury, které mapují každou službu na její spouštěcí funkci. Toto pole je pak předáno funkci Win32 API, [StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw). Teoreticky může jeden exe zpracovat více služeb a pole může mít několik `SERVICE_TABLE_ENTRY` struktur. V současné době však služba generovaná knihovnou ATL podporuje pouze jednu službu na soubor EXE. Proto má pole jednu položku, která obsahuje název služby a `_ServiceMain` jako funkci spuštění. `_ServiceMain`je statická členská funkce `CAtlServiceModuleT` , která volá nestatickou členskou funkci,. `ServiceMain`

> [!NOTE]
>  `StartServiceCtrlDispatcher` Selhání připojení ke Správci řízení služeb pravděpodobně znamená, že program není spuštěn jako služba. V takovém případě program volá `CAtlServiceModuleT::Run` přímo, takže program může běžet jako místní server. Další informace o spuštění programu jako místního serveru naleznete v tématu [tipy pro ladění](../atl/debugging-tips.md).

## <a name="see-also"></a>Viz také:

[Služby](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
