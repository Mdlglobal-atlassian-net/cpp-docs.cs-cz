---
title: 'CAtlServiceModuleT:: ServiceMain – funkce'
ms.date: 11/04/2016
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: b79767d4c1696174f90a325ea152ccc7939ed9fe
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491711"
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT:: ServiceMain – funkce

Volání `ServiceMain` správce řízení služeb (SCM) po otevření aplikace ovládacích panelů služby vyberte službu a klikněte na tlačítko **Spustit**.

Po volání `ServiceMain`SCM musí služba poskytnout funkci SCM a obslužné rutiny. Tato funkce umožňuje SCM získat stav služby a předat konkrétní pokyny (například pozastavení nebo zastavení). SCM získá tuto funkci, když služba projde `_Handler` funkci Win32 API, [RegisterServiceCtrlHandler](/windows/win32/api/winsvc/nf-winsvc-registerservicectrlhandlerw). (`_Handler` je statická členská funkce, která volá [obslužnou rutinu](../atl/reference/catlservicemodulet-class.md#handler)nestatické členské funkce.)

Při spuštění by služba měla také informovat správce aktuálního stavu. Provede to předáním SERVICE_START_PENDING do funkce Win32 API, [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus).

`ServiceMain`potom volání `CAtlExeModuleT::InitializeCom`, která volá funkci Win32 API [funkce CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex). Ve výchozím nastavení `InitializeCom` předá funkci příznak COINIT_MULTITHREADED. Tento příznak indikuje, že program musí být serverem s volnými vlákny.

Nyní se `CAtlServiceModuleT::Run` volá, aby se prováděla hlavní práce služby. `Run`pokračuje v provádění až do zastavení služby.

## <a name="see-also"></a>Viz také:

[Služby](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)
