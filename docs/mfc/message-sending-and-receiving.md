---
title: Odesílání a příjem zpráv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b7ded8dd0c818b95d6f45a722bd7b8516d48ff1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347175"
---
# <a name="message-sending-and-receiving"></a>Odesílání a příjem zpráv
Vezměte v úvahu odesílání část procesu a odpovědí rozhraní.  
  
 Většina výsledek zprávy z interakce uživatele s programu. Příkazy jsou generovány kliknutí myší v nabídce položky nebo tlačítka panelu nástrojů nebo stisknutí kláves akcelerátoru. Uživatel generuje také zpráv systému Windows, například přesun nebo změnou velikosti okna. Další zprávy Windows se odesílají při výskytu události, jako je například spuštění programu nebo ukončení, jak windows získat nebo ztratit fokus a tak dále. Oznámení ovládacího prvku zprávy generované kliknutí myši nebo jiné uživatelské interakce s ovládacím prvkem, jako je tlačítko nebo pole se seznamem ovládacího prvku v dialogovém okně.  
  
 **Spustit** funkce člena třídy `CWinApp` načítá zprávy a odešle je do příslušné okna. Většina příkazů zpráv se odesílají do hlavního rámce okna aplikace. `WindowProc` Předdefinovaná v nástroji získá knihovny tříd zprávy a směruje je jinak, v závislosti na kategorii přijatá zpráva.  
  
 Teď se podíváme přijímající součást procesu.  
  
 Počáteční příjemce zprávy musí být objektem okna. Zprávy Windows jsou obvykle zpracovávány přímo okno objektu. Příkaz zprávy, většinou pocházející z okna aplikace hlavního rámce, získat směrovány do řetězu příkaz cíl popsané v [směrování příkazů](../mfc/command-routing.md).  
  
 Každý objekt schopná přijmout zprávy nebo příkazy, má svou vlastní zprávu namapovat této páry zpráva nebo příkaz s názvem jeho obslužné rutiny.  
  
 Když příkaz cílový objekt obdrží zprávu nebo příkazu, vyhledá jeho mapy zpráv pro shodu. Pokud najde obslužnou rutinu pro zprávu, volá obslužnou rutinu. Další informace o tom, jak budou prohledávány mapy zpráv najdete v tématu [jak rámci hledání mapy zpráv](../mfc/how-the-framework-searches-message-maps.md). Znovu najdete na obrázku [příkazy v rámci](../mfc/user-interface-objects-and-command-ids.md).  
  
## <a name="see-also"></a>Viz také  
 [Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

