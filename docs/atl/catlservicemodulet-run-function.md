---
title: Catlservicemodulet::Run – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
dev_langs:
- C++
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e509ad88a744f6ebaaca41ecd0d6455d68c2585c
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850651"
---
# <a name="catlservicemoduletrun-function"></a>Catlservicemodulet::Run – funkce
`Run` obsahuje volání do `PreMessageLoop`, `RunMessageLoop`, a `PostMessageLoop`. Po volání, `PreMessageLoop` nejprve ukládá ID služby vlákna. Služba bude používat toto ID zavřete samotné odesláním WM_QUIT zprávu pomocí funkce rozhraní Win32 API [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946).  
  
 `PreMessageLoop` pak zavolá `InitializeSecurity`. Ve výchozím nastavení `InitializeSecurity` volání [CoInitializeSecurity](http://msdn.microsoft.com/library/windows/desktop/ms693736) popisovači zabezpečení nastaven na hodnotu NULL, což znamená, že každý uživatel má přístup k objektu.  
  
 Pokud nechcete, aby službě a zadejte vlastní zabezpečení, mají přednost před `PreMessageLoop` a Nevolejte `InitializeSecurity`, a modelu COM poté určí nastavení zabezpečení z registru. Je pohodlný způsob, jak nakonfigurovat nastavení registru [DCOMCNFG](../atl/dcomcnfg.md) nástroj prodiskutována později v této části.  
  
 Po zabezpečení není zadána, objekt je registrován s modelem COM tak, aby noví klienti můžou připojit k programu. A konečně program informuje správce řízení služeb (SCM), že je spuštěný a program přejde do smyčky zpráv. Program zůstane spuštěný, dokud se odešle zprávy o ukončení při vypnutí služby.  
  
## <a name="see-also"></a>Viz také  
 [Služby](../atl/atl-services.md)   
 [Csecuritydesc – třída](../atl/reference/csecuritydesc-class.md)   
 [CSID – třída](../atl/reference/csid-class.md)   
 [Cdacl – třída](../atl/reference/cdacl-class.md)   
 [Catlservicemodulet::Run –](../atl/reference/catlservicemodulet-class.md#run)

