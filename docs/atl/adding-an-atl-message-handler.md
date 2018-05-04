---
title: Přidání popisovače zpráv knihovny ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e79598b79ccbad13ad98c7fc1284808fe1b05cfc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="adding-an-atl-message-handler"></a>Přidání popisovače zpráv knihovny ATL
Přidání obslužné rutiny zpráv (členské funkce, která zpracovává zprávy systému Windows) do ovládacího prvku, nejprve vyberte ovládací prvek v zobrazení tříd. Otevřete **vlastnosti** vyberte **zprávy** ikonu a klikněte na rozevírací seznam řízení v poli opačným požadované zprávy. Tím se přidá deklaraci pro obslužné rutiny zpráv v záhlaví souboru ovládacího prvku a kostru implementaci obslužné rutiny v souboru sada ovládacího prvku. Rovněž přidat mapu zprávu a přidat záznam pro obslužnou rutinu.  
  
 Přidání obslužné rutiny zpráv v ATL je podobný jako při přidávání do třídy knihovny MFC obslužné rutiny zpráv. V tématu [Přidání popisovače zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md) Další informace.  
  
 Tyto podmínky platí pouze pro přidání popisovače zpráv knihovny ATL:  
  
-   Obslužné rutiny zpráv podle stejné zásady vytváření názvů jako MFC.  
  
-   Nové položky mapy zpráv se přidají do mapy hlavní zpráv. Průvodce nebyl rozpoznán mapy alternativní zpráv a řetězení.  
  
## <a name="see-also"></a>Viz také  
 [Implementace okna](../atl/implementing-a-window.md)

