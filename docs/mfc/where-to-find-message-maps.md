---
title: "Kde hledat mapy zpráv | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 741c7a62083680c434f7eaa1c415441449525344
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="where-to-find-message-maps"></a>Kde hledat mapy zpráv
Když vytvoříte nové kostru aplikace pomocí Průvodce aplikací, Průvodce aplikací zapíše mapy zpráv pro jednotlivé příkaz cílové třídy, které vytvoří za vás. To zahrnuje odvozené aplikace, dokumentu, zobrazení a třídy oken s rámečkem. Některé z těchto mapy zpráv už máte položky zadaný pomocí Průvodce aplikací pro určité zprávy a příkazy předdefinované a některé jsou jenom zástupné symboly pro obslužné rutiny, které přidáte.  
  
 Mapy zpráv třída se nachází v. Soubor CPP pro třídu. Práce s mapy základní zpráv, které vytvoří průvodce, okno Vlastnosti použít pro přidání položek pro zprávy a příkazy, které bude zpracovávat jednotlivé třídy. Mapy zpráv typické může vypadat třeba takto po přidání některé položky:  
  
 [!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]  
  
 Mapy zpráv se skládá z kolekce makra. Dvě makra [begin_message_map –](reference/message-map-macros-mfc.md#begin_message_map) a [end_message_map –](reference/message-map-macros-mfc.md#end_message_map), závorka mapy zpráv. Ostatní makra, jako například `ON_COMMAND`, vyplňte obsah mapy zpráv.  
  
> [!NOTE]
>  Makra map zpráv nejsou následovaný středníky.  
  
 Když pomocí průvodce Přidat třídu vytvořte novou třídu, poskytuje mapy zpráv pro třídu. Alternativně můžete vytvořit ručně pomocí editoru zdrojového kódu mapy zpráv.  
  
## <a name="see-also"></a>Viz také  
 [Jak Framework prohledává mapy zpráv](../mfc/how-the-framework-searches-message-maps.md)

