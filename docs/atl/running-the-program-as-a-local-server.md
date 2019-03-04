---
title: Spuštění programu jako místního serveru
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
ms.openlocfilehash: a412814fc5f3900a248f779501e2720b72287e57
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296823"
---
# <a name="running-the-program-as-a-local-server"></a>Spuštění programu jako místního serveru

Pokud spuštění programu jako služba je nevhodné, můžete dočasně změnit registr tak, aby program je spuštěn jako normální místní server. Jednoduše přejmenovat `LocalService` hodnoty v rámci vaší AppID, který `_LocalService` a ujistěte `LocalServer32` klíč v rámci vaší CLSID je správně nastavený. (Všimněte si, že použití DCOMCNFG k určení, že vaše aplikace by měl běžet v jiném počítači přejmenuje vaše `LocalServer32` klíč `_LocalServer32`.) Spuštění programu jako místního serveru má několik dalších sekund při spuštění, protože volání `StartServiceCtrlDispatcher` v `CAtlServiceModuleT::Start` trvá několik sekund, než selže.

## <a name="see-also"></a>Viz také:

[Tipy pro ladění](../atl/debugging-tips.md)
