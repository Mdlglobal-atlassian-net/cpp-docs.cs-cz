---
title: Catlservicemodulet::Handler – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
dev_langs:
- C++
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbc7c74e0fd6fdd34ba9a0c386c028469113c88e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767078"
---
# <a name="catlservicemodulethandler-function"></a>Catlservicemodulet::Handler – funkce

`CAtlServiceModuleT::Handler` je rutina, která volá správce řízení služeb (SCM) načíst stav služby a přiřaďte jí různé pokyny (jako je zastavení nebo pozastavení). SCM předá operační kód na `Handler` k označení toho, co služba dělat. Výchozí generovaný ATL služba zpracovává pouze instrukce stop. V případě úspěšného SCM instrukce stop, říká službě SCM, program se chystá ukončit. Pak zavolá služba `PostThreadMessage` pro zprávy o ukončení na sebe sama. To ukončí smyčku zpráv a služby se nakonec zavře.

Pro zpracování další pokyny, budete muset změnit `m_status` inicializovat datový člen v `CAtlServiceModuleT` konstruktoru. Tento datový člen říká SCM tlačítek, která umožňuje při výběru služby v ovládacím panelu služby aplikace.

## <a name="see-also"></a>Viz také

[Služby](../atl/atl-services.md)   
[Catlservicemodulet::Handler –](../atl/reference/catlservicemodulet-class.md#handler)

