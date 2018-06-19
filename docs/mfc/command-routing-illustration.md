---
title: Příkaz znázornění směrování | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a12a5cd19177761dfbf484c64f528d8def194ca5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341133"
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
 [Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

