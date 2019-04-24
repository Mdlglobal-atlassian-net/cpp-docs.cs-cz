---
title: CAtlServiceModuleT::Handler Function
ms.date: 11/04/2016
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
ms.openlocfilehash: fffdeddce7f3fa27d798ea7abafe85c9a13d9d97
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223180"
---
# <a name="catlservicemodulethandler-function"></a>CAtlServiceModuleT::Handler Function

`CAtlServiceModuleT::Handler` je rutina, která volá správce řízení služeb (SCM) načíst stav služby a přiřaďte jí různé pokyny (jako je zastavení nebo pozastavení). SCM předá operační kód na `Handler` k označení toho, co služba dělat. Výchozí generovaný ATL služba zpracovává pouze instrukce stop. V případě úspěšného SCM instrukce stop, říká službě SCM, program se chystá ukončit. Pak zavolá služba `PostThreadMessage` pro zprávy o ukončení na sebe sama. To ukončí smyčku zpráv a služby se nakonec zavře.

Pro zpracování další pokyny, budete muset změnit `m_status` inicializovat datový člen v `CAtlServiceModuleT` konstruktoru. Tento datový člen říká SCM tlačítek, která umožňuje při výběru služby v ovládacím panelu služby aplikace.

## <a name="see-also"></a>Viz také:

[Služby](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)
