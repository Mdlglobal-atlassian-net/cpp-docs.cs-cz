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
ms.openlocfilehash: e7ff7c2f7564a5da2c7a1db3913526a95660fe1d
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754670"
---
# <a name="running-the-program-as-a-local-server"></a>Spuštění programu jako místního serveru

Pokud spuštění programu jako služba je nevhodné, můžete dočasně změnit registr tak, aby program je spuštěn jako normální místní server. Jednoduše přejmenovat `LocalService` hodnoty v rámci vaší AppID, který `_LocalService` a ujistěte `LocalServer32` klíč v rámci vaší CLSID je správně nastavený. (Všimněte si, že použití DCOMCNFG k určení, že vaše aplikace by měl běžet v jiném počítači přejmenuje vaše `LocalServer32` klíč `_LocalServer32`.) Spuštění programu jako místního serveru má několik dalších sekund při spuštění, protože volání `StartServiceCtrlDispatcher` v `CAtlServiceModuleT::Start` trvá několik sekund, než selže.

## <a name="see-also"></a>Viz také

[Tipy pro ladění](../atl/debugging-tips.md)

