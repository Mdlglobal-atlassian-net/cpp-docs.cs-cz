---
title: "Příkaz znázornění směrování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 03f9547197e2d5dca26fd17c9d4090eb20e795ed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="command-routing-illustration"></a>Znázornění směrování příkazů
Pro ilustraci, zvažte zprávou příkazu z vymazat všechny položky nabídky v nabídce aplikace MDI upravit. Předpokládejme, že se stane, obslužné rutiny pro tento příkaz jako funkce člena třídy dokumentu aplikace. Zde je, jak tento příkaz dosáhne její obslužnou rutinu po výběru položky nabídky:  
  
1.  Hlavní okno rámce nejprve obdrží zprávu příkaz.  
  
2.  Hlavní rámce okna MDI dává aktuálně aktivní podřízeného okna MDI příležitosti pro zpracování příkazu.  
  
3.  Standardní směrování rámce okna MDI podřízené dává jeho zobrazení možnost v příkazu před zaškrtnutím vlastní mapy zpráv.  
  
4.  Zobrazení nejprve hledá vlastní mapy zpráv a hledání žádná obslužná rutina vedle směruje příkaz jeho přidružené dokumentu.  
  
5.  Dokument zkontroluje jeho mapy zpráv a zjistí obslužnou rutinu. Tento dokument – členská funkce je volána a směrování zastaví.  
  
 Pokud dokument neměl obslužnou rutinu, ho by příkaz směrovat vedle jeho šablona dokumentu. Příkaz by pak vrátí k zobrazení a poté okně s rámečkem. Okně s rámečkem by nakonec zkontrolujte jeho mapy zpráv. Pokud se kontroly se nezdařilo i, příkaz zpět do hlavní rámce okna MDI a pak do objektu application směrován – konečným cílem neošetřené příkazy.  
  
## <a name="see-also"></a>Viz také  
 [Jakým způsobem volá Framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

