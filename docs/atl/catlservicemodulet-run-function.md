---
title: Catlservicemodulet::Run – funkce
ms.date: 11/04/2016
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
ms.openlocfilehash: 3abb6908a64864463c45d8fc4dc24bfc813db586
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458658"
---
# <a name="catlservicemoduletrun-function"></a>Catlservicemodulet::Run – funkce

`Run` obsahuje volání do `PreMessageLoop`, `RunMessageLoop`, a `PostMessageLoop`. Po volání, `PreMessageLoop` nejprve ukládá ID služby vlákna. Služba bude používat toto ID zavřete samotné odesláním WM_QUIT zprávu pomocí funkce rozhraní Win32 API [PostThreadMessage](https://msdn.microsoft.com/library/windows/desktop/ms644946).

`PreMessageLoop` pak zavolá `InitializeSecurity`. Ve výchozím nastavení `InitializeSecurity` volání [CoInitializeSecurity](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializesecurity) popisovači zabezpečení nastaven na hodnotu NULL, což znamená, že každý uživatel má přístup k objektu.

Pokud nechcete, aby službě a zadejte vlastní zabezpečení, mají přednost před `PreMessageLoop` a Nevolejte `InitializeSecurity`, a modelu COM poté určí nastavení zabezpečení z registru. Je pohodlný způsob, jak nakonfigurovat nastavení registru [DCOMCNFG](../atl/dcomcnfg.md) nástroj prodiskutována později v této části.

Po zabezpečení není zadána, objekt je registrován s modelem COM tak, aby noví klienti můžou připojit k programu. A konečně program informuje správce řízení služeb (SCM), že je spuštěný a program přejde do smyčky zpráv. Program zůstane spuštěný, dokud se odešle zprávy o ukončení při vypnutí služby.

## <a name="see-also"></a>Viz také

[Služby](../atl/atl-services.md)<br/>
[CSecurityDesc – třída](../atl/reference/csecuritydesc-class.md)<br/>
[CSid – třída](../atl/reference/csid-class.md)<br/>
[CDacl – třída](../atl/reference/cdacl-class.md)<br/>
[Catlservicemodulet::Run –](../atl/reference/catlservicemodulet-class.md#run)

