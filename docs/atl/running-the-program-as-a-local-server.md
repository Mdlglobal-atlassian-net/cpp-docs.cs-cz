---
title: Spuštění programu jako místního serveru
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
ms.openlocfilehash: 9a55dba861457eae888f519fb3bbd6c7a66e623c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610857"
---
# <a name="running-the-program-as-a-local-server"></a>Spuštění programu jako místního serveru

Pokud spuštění programu jako služba je nevhodné, můžete dočasně změnit registr tak, aby program je spuštěn jako normální místní server. Jednoduše přejmenovat `LocalService` hodnoty v rámci vaší AppID, který `_LocalService` a ujistěte `LocalServer32` klíč v rámci vaší CLSID je správně nastavený. (Všimněte si, že použití DCOMCNFG k určení, že vaše aplikace by měl běžet v jiném počítači přejmenuje vaše `LocalServer32` klíč `_LocalServer32`.) Spuštění programu jako místního serveru má několik dalších sekund při spuštění, protože volání `StartServiceCtrlDispatcher` v `CAtlServiceModuleT::Start` trvá několik sekund, než selže.

## <a name="see-also"></a>Viz také

[Tipy pro ladění](../atl/debugging-tips.md)

