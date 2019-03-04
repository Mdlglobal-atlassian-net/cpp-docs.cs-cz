---
title: CAtlServiceModuleT::ServiceMain Function
ms.date: 11/04/2016
f1_keywords:
- ServiceMain
- CServiceModule::ServiceMain
- CServiceModule.ServiceMain
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: 32bdea1eb39c91ddb58def72bd16acc2f16ab936
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295419"
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT::ServiceMain Function

Volá správce řízení služeb (SCM) `ServiceMain` při otevření aplikace ovládacím panelu služby, vyberte službu a klikněte na **Start**.

Po SCM volá `ServiceMain`, služba musí poskytnout SCM funkci obslužné rutiny. Tato funkce umožňuje SCM získání stavu služby a předat konkrétní pokyny (jako je například pozastavení nebo ukončení). SCM získá tuto funkci, když se předá službě `_Handler` funkce rozhraní Win32 API [RegisterServiceCtrlHandler](/windows/desktop/api/winsvc/nf-winsvc-registerservicectrlhandlera). (`_Handler` je statickou členskou funkci, která volá nestatická členská funkce [obslužná rutina](../atl/reference/catlservicemodulet-class.md#handler).)

Při spuštění služby by měl také informovat SCM jeho aktuální stav. Dělá to pomocí předání do funkce rozhraní Win32 API SERVICE_START_PENDING [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).

`ServiceMain` pak zavolá `CAtlExeModuleT::InitializeCom`, která volá funkce rozhraní Win32 API [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex). Ve výchozím nastavení `InitializeCom` předá COINIT_MULTITHREADED příznak funkce. Tento příznak určuje, že program má být server volných vláken.

Nyní `CAtlServiceModuleT::Run` je volána k provedení hlavní služby. `Run` pokračuje v provádění, dokud se tato služba zastavená.

## <a name="see-also"></a>Viz také:

[Služby](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)
