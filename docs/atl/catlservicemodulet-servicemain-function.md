---
title: Catlservicemodulet::servicemain – funkce
ms.date: 11/04/2016
f1_keywords:
- ServiceMain
- CServiceModule::ServiceMain
- CServiceModule.ServiceMain
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: 3aad67d58ccd4d1d35572542d899c17e0f42902b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471211"
---
# <a name="catlservicemoduletservicemain-function"></a>Catlservicemodulet::servicemain – funkce

Volá správce řízení služeb (SCM) `ServiceMain` při otevření aplikace ovládacím panelu služby, vyberte službu a klikněte na **Start**.

Po SCM volá `ServiceMain`, služba musí poskytnout SCM funkci obslužné rutiny. Tato funkce umožňuje SCM získání stavu služby a předat konkrétní pokyny (jako je například pozastavení nebo ukončení). SCM získá tuto funkci, když se předá službě `_Handler` funkce rozhraní Win32 API [RegisterServiceCtrlHandler](/windows/desktop/api/winsvc/nf-winsvc-registerservicectrlhandlera). (`_Handler` je statickou členskou funkci, která volá nestatická členská funkce [obslužná rutina](../atl/reference/catlservicemodulet-class.md#handler).)

Při spuštění služby by měl také informovat SCM jeho aktuální stav. Dělá to pomocí předání do funkce rozhraní Win32 API SERVICE_START_PENDING [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).

`ServiceMain` pak zavolá `CAtlExeModuleT::InitializeCom`, která volá funkce rozhraní Win32 API [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex). Ve výchozím nastavení `InitializeCom` předá COINIT_MULTITHREADED příznak funkce. Tento příznak určuje, že program má být server volných vláken.

Nyní `CAtlServiceModuleT::Run` je volána k provedení hlavní služby. `Run` pokračuje v provádění, dokud se tato služba zastavená.

## <a name="see-also"></a>Viz také

[Služby](../atl/atl-services.md)<br/>
[Catlservicemodulet::servicemain –](../atl/reference/catlservicemodulet-class.md#servicemain)

