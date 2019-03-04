---
title: Mapy zpráv (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message maps, ATL
- ATL, message handlers
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
ms.openlocfilehash: 1b8b3fcb2f10f975ebdf68a285c7d5e364b9e1b4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292572"
---
# <a name="message-maps-atl"></a>Mapy zpráv (ATL)

Mapy zpráv obslužnou rutinu přidruží konkrétní zprávy, příkaz nebo oznámení. S použitím ATL [makra map zpráv](../atl/reference/message-map-macros-atl.md), můžete zadat mapy zpráv pro okna. Procedury oken v `CWindowImpl`, `CDialogImpl`, a `CContainedWindowT` směrování zpráv okna do jeho mapování zprávy.

[Funkce obslužné rutiny zpráv](../atl/message-handler-functions.md) přijměte další argument typu `BOOL&`. Tento argument určuje, zda byla zpráva zpracována a je ve výchozím nastavení má hodnotu TRUE. Funkce obslužné rutiny můžete tento argument nastavit na hodnotu FALSE označuje, že nebyla zpracována zprávu. V takovém případě knihovny ATL bude hledat funkci obslužné rutiny dále v mapování zprávy. Tento argument nastavíte na hodnotu FALSE, můžete nejprve provést určité akce v reakci na zprávu a pak povolit výchozí zpracování nebo jinou funkci obslužné rutiny na dokončení zpracování zprávy.

## <a name="chained-message-maps"></a>Zřetězené zprávy Maps

ATL také umožňuje řetězu mapy zpráv, která přesměruje zpracování do mapy zpráv definovaný v jiné třídy zpráv. Například můžete implementovat běžné zpracování zpráv v samostatné třídě poskytovat jednotné chování pro všechna okna řetězení dané třídy. Můžete zřetězit na základní třídu nebo na datový člen třídy.

ATL také podporuje dynamické řetězení, které vám umožní do řetězce do mapy zpráv jiného objektu v době běhu. K implementaci dynamického řetězení, musí být odvozen z vaší třídy [cdynamicchain –](../atl/reference/cdynamicchain-class.md). Potom deklarovat [CHAIN_MSG_MAP_DYNAMIC](reference/message-map-macros-atl.md#chain_msg_map_dynamic) – makro v mapě zpráv. CHAIN_MSG_MAP_DYNAMIC vyžaduje jedinečné číslo identifikující objektu a mapy zpráv, ke kterému jsou řetězení. Je nutné definovat tuto jedinečnou hodnotu přímo pomocí volání `CDynamicChain::SetChainEntry`.

Můžete zřetězit na jakoukoli třídu, která deklaruje mapy zpráv, pokud třída je odvozena z [cmessagemap –](../atl/reference/cmessagemap-class.md). `CMessageMap` Umožňuje zobrazit jeho mapy zpráv na jiné objekty. Všimněte si, že `CWindowImpl` již je odvozena z `CMessageMap`.

## <a name="alternate-message-maps"></a>Alternativní zprávy Maps

Nakonec ATL podporuje alternativní zprávy maps, deklarované s [ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map) – makro. Každý mapování alternativních zprávy je identifikován jedinečný číslo, které můžete předat ALT_MSG_MAP. Pomocí alternativní zprávy maps, můžete zpracovávat zprávy více oken v jednu mapu. Všimněte si, že ve výchozím nastavení, `CWindowImpl` nepoužívá mapy alternativní zpráv. Na přidání této podpory, přepsat `WindowProc` metoda ve vaší `CWindowImpl`-odvozené třídy a volání `ProcessWindowMessage` s identifikátorem mapy zpráv.

## <a name="see-also"></a>Viz také:

[Implementace okna](../atl/implementing-a-window.md)
