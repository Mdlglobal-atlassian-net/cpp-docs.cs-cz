---
title: 'CAtlServiceModuleT:: run – funkce'
ms.date: 11/04/2016
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
ms.openlocfilehash: 0c35020996852731a8f22c15860d4cceb7a8bdb6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491522"
---
# <a name="catlservicemoduletrun-function"></a>CAtlServiceModuleT:: run – funkce

`Run`obsahuje volání `PreMessageLoop`, `RunMessageLoop`a. `PostMessageLoop` Po zavolání `PreMessageLoop` nejprve uloží ID vlákna služby. Služba bude toto ID používat k tomu, aby se sám zavřeli odesláním zprávy WM_QUIT pomocí funkce Win32 API [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew).

`PreMessageLoop`pak volá `InitializeSecurity`. Ve výchozím nastavení `InitializeSecurity` volá [: CoInitializeSecurity](/windows/win32/api/combaseapi/nf-combaseapi-coinitializesecurity) s popisovačem zabezpečení nastaveným na hodnotu null, což znamená, že každý uživatel má přístup k vašemu objektu.

Pokud nechcete, aby služba určovala vlastní zabezpečení, přepište `PreMessageLoop` a Nevolejte `InitializeSecurity`a model com pak určí nastavení zabezpečení z registru. Pohodlný způsob, jak nakonfigurovat nastavení registru, je pomocí nástroje [Dcomcnfg](../atl/dcomcnfg.md) , který je popsán dále v této části.

Po zadání zabezpečení je objekt zaregistrován v modelu COM, aby se noví klienti mohli připojovat k programu. Nakonec program upozorní správce řízení služeb (SCM), že je spuštěný, a program vloží smyčku zpráv. Program zůstane spuštěný, dokud nebude při vypnutí služby odeslána zpráva o ukončení.

## <a name="see-also"></a>Viz také:

[Služby](../atl/atl-services.md)<br/>
[CSecurityDesc – třída](../atl/reference/csecuritydesc-class.md)<br/>
[CSid – třída](../atl/reference/csid-class.md)<br/>
[CDacl – třída](../atl/reference/cdacl-class.md)<br/>
[CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)
