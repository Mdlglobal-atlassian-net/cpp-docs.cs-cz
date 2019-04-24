---
title: CAtlServiceModuleT::ServiceMain Function
ms.date: 11/04/2016
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: 81cd8fcbdf275063b243e215301eff504a2b5cc6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223206"
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
