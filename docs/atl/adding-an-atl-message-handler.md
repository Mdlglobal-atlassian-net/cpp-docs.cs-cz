---
title: "Přidání popisovače zpráv knihovny ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a30c8d2c26893ddf101d7084a91215c7ed55bf48
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="adding-an-atl-message-handler"></a>Přidání popisovače zpráv knihovny ATL
Přidání obslužné rutiny zpráv (členské funkce, která zpracovává zprávy systému Windows) do ovládacího prvku, nejprve vyberte ovládací prvek v zobrazení tříd. Otevřete **vlastnosti** vyberte **zprávy** ikonu a klikněte na rozevírací seznam řízení v poli opačným požadované zprávy. Tím se přidá deklaraci pro obslužné rutiny zpráv v záhlaví souboru ovládacího prvku a kostru implementaci obslužné rutiny v souboru sada ovládacího prvku. Rovněž přidat mapu zprávu a přidat záznam pro obslužnou rutinu.  
  
 Přidání obslužné rutiny zpráv v ATL je podobný jako při přidávání do třídy knihovny MFC obslužné rutiny zpráv. V tématu [Přidání popisovače zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md) Další informace.  
  
 Tyto podmínky platí pouze pro přidání popisovače zpráv knihovny ATL:  
  
-   Obslužné rutiny zpráv podle stejné zásady vytváření názvů jako MFC.  
  
-   Nové položky mapy zpráv se přidají do mapy hlavní zpráv. Průvodce nebyl rozpoznán mapy alternativní zpráv a řetězení.  
  
## <a name="see-also"></a>Viz také  
 [Implementace okno](../atl/implementing-a-window.md)

