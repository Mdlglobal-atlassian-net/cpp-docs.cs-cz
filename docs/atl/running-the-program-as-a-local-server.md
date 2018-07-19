---
title: Spuštění programu jako místního serveru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae2e44ba51a878d293ad5b497a1638cc9d7dc76
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848480"
---
# <a name="running-the-program-as-a-local-server"></a>Spuštění programu jako místního serveru
Pokud spuštění programu jako služba je nevhodné, můžete dočasně změnit registr tak, aby program je spuštěn jako normální místní server. Jednoduše přejmenovat `LocalService` hodnoty v rámci vaší AppID, který `_LocalService` a ujistěte `LocalServer32` klíč v rámci vaší CLSID je správně nastavený. (Všimněte si, že použití DCOMCNFG k určení, že vaše aplikace by měl běžet v jiném počítači přejmenuje vaše `LocalServer32` klíč `_LocalServer32`.) Spuštění programu jako místního serveru má několik dalších sekund při spuštění, protože volání `StartServiceCtrlDispatcher` v `CAtlServiceModuleT::Start` trvá několik sekund, než selže.  
  
## <a name="see-also"></a>Viz také  
 [Tipy pro ladění](../atl/debugging-tips.md)

