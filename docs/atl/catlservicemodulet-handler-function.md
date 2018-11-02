---
title: Catlservicemodulet::Handler – funkce
ms.date: 11/04/2016
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
ms.openlocfilehash: 74c52e07f5be4ac16c8f9a20115a623c53f46090
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553683"
---
# <a name="catlservicemodulethandler-function"></a>Catlservicemodulet::Handler – funkce

`CAtlServiceModuleT::Handler` je rutina, která volá správce řízení služeb (SCM) načíst stav služby a přiřaďte jí různé pokyny (jako je zastavení nebo pozastavení). SCM předá operační kód na `Handler` k označení toho, co služba dělat. Výchozí generovaný ATL služba zpracovává pouze instrukce stop. V případě úspěšného SCM instrukce stop, říká službě SCM, program se chystá ukončit. Pak zavolá služba `PostThreadMessage` pro zprávy o ukončení na sebe sama. To ukončí smyčku zpráv a služby se nakonec zavře.

Pro zpracování další pokyny, budete muset změnit `m_status` inicializovat datový člen v `CAtlServiceModuleT` konstruktoru. Tento datový člen říká SCM tlačítek, která umožňuje při výběru služby v ovládacím panelu služby aplikace.

## <a name="see-also"></a>Viz také

[Služby](../atl/atl-services.md)<br/>
[Catlservicemodulet::Handler –](../atl/reference/catlservicemodulet-class.md#handler)

