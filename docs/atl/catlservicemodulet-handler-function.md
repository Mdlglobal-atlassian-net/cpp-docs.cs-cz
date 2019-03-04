---
title: CAtlServiceModuleT::Handler Function
ms.date: 11/04/2016
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
ms.openlocfilehash: e344fd36ad6c70a80486eef6a10eacd8a88a2baf
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273371"
---
# <a name="catlservicemodulethandler-function"></a>CAtlServiceModuleT::Handler Function

`CAtlServiceModuleT::Handler` je rutina, která volá správce řízení služeb (SCM) načíst stav služby a přiřaďte jí různé pokyny (jako je zastavení nebo pozastavení). SCM předá operační kód na `Handler` k označení toho, co služba dělat. Výchozí generovaný ATL služba zpracovává pouze instrukce stop. V případě úspěšného SCM instrukce stop, říká službě SCM, program se chystá ukončit. Pak zavolá služba `PostThreadMessage` pro zprávy o ukončení na sebe sama. To ukončí smyčku zpráv a služby se nakonec zavře.

Pro zpracování další pokyny, budete muset změnit `m_status` inicializovat datový člen v `CAtlServiceModuleT` konstruktoru. Tento datový člen říká SCM tlačítek, která umožňuje při výběru služby v ovládacím panelu služby aplikace.

## <a name="see-also"></a>Viz také:

[Služby](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)
