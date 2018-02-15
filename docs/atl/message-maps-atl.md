---
title: "Zpráva mapy (ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- message maps, ATL
- ATL, message handlers
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 12eeb74266e9c303817430958025d6536147356c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="message-maps-atl"></a>Mapy zpráv (ATL)
Mapy zpráv přidruží obslužnou rutinu konkrétní zprávu, příkaz nebo oznámení. Pomocí knihovny ATL pro [makra map zpráv](../atl/reference/message-map-macros-atl.md), můžete zadat mapy zpráv pro okno. Procedury oken v `CWindowImpl`, `CDialogImpl`, a `CContainedWindowT` přímé časového období zprávy a pokuste se jeho mapy zpráv.  
  
 [Funkce obslužných rutin zpráv](../atl/message-handler-functions.md) přijměte další argument typu `BOOL&`. Tento argument určuje, jestli se zpracovala zprávu, a je nastaven na hodnotu `TRUE` ve výchozím nastavení. Funkce obslužných rutin můžete pak argument na `FALSE` indikující, zda nebyl ke zpracování zprávy. V takovém případě ATL bude hledat funkce obslužné rutiny další v mapy zpráv. Nastavením tento argument na `FALSE`, můžete nejprve provést některé akce v odpovědi na zprávu a potom povolit výchozí zpracování nebo jinou funkci obslužné rutiny na dokončení zpracování zprávy.  
  
## <a name="chained-message-maps"></a>Mapy zpráv zřetězené  
 ATL také umožňuje mapy zpráv řetězec, který přesměruje zpracování do mapy zpráv definované v jiné třídy zpráv. Například můžete implementovat běžné zpracování zpráv v samostatné třídy zajistit uniform chování pro všechny systémy windows řetězení pro tuto třídu. Můžete zřetězené základní třídu nebo datový člen vaší třídy.  
  
 ATL také podporuje dynamické řetězení, což umožňuje řetězce pro mapy zpráv jiného objektu v době běhu. Pokud chcete implementovat dynamické řetězení, musí být odvozeny třídě z [CDynamicChain](../atl/reference/cdynamicchain-class.md). Potom deklarovat [CHAIN_MSG_MAP_DYNAMIC](reference/message-map-macros-atl.md#chain_msg_map_dynamic) makro mapy zpráv. `CHAIN_MSG_MAP_DYNAMIC` vyžaduje jedinečné číslo identifikující objekt a mapy zpráv, ke kterému jsou řetězení. Je nutné definovat Tato jedinečná hodnota prostřednictvím volání `CDynamicChain::SetChainEntry`.  
  
 Všechny třídy, který deklaruje mapy zpráv, můžete zřetězení zadaný třída odvozená z [CMessageMap](../atl/reference/cmessagemap-class.md). `CMessageMap` Umožňuje objekt vystavit jeho mapy zpráv na jiné objekty. Všimněte si, že `CWindowImpl` již je odvozena z `CMessageMap`.  
  
## <a name="alternate-message-maps"></a>Mapy zpráv alternativní  
 Nakonec ATL podporuje mapy alternativní zpráv, deklarovat s [ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map) makro. Každý mapa alternativní zpráv je určený podle jedinečné číslo, které můžete předat `ALT_MSG_MAP`. Pomocí alternativní zprávy mapy, dokáže zpracovat zprávy více oken v jedna mapa. Všimněte si, že se ve výchozím nastavení, `CWindowImpl` nepoužívá mapy alternativní zpráv. Chcete-li přidat tuto podporu, přepište `WindowProc` metoda v vaše `CWindowImpl`-odvozené třídy a volání `ProcessWindowMessage` s identifikátorem mapy zpráv.  
  
## <a name="see-also"></a>Viz také  
 [Implementace okna](../atl/implementing-a-window.md)

