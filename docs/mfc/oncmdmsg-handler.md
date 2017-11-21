---
title: "Oncmdmsg – obslužná rutina | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OnCmdMsg
dev_langs: C++
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 71913ede29f3a8e02c319b3c713d2c33bbcb5b8e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg – obslužná rutina
K dosažení směrování příkazů, každý příkaz cíl volá `OnCmdMsg` – členská funkce další příkaz cíle v pořadí. Příkaz cílem použití `OnCmdMsg` a určit, zda jejich zpracování příkazu směrovat na jiný cíl příkazu, pokud jejich nelze ho zpracovat.  
  
 Každý příkaz cílové třídy mohou přepsat `OnCmdMsg` – členská funkce. Přepsání umožní každý – třída trasy příkazy na konkrétní Další cíl. Okno rámce, například vždy směruje příkazy na jeho aktuální podřízeného okna nebo zobrazení, jak je znázorněno v tabulce [standardních příkazů trasy](../mfc/command-routing.md).  
  
 Výchozí hodnota `CCmdTarget` implementace `OnCmdMsg` používá k hledání funkce obslužné rutiny pro každou zprávu příkaz obdrží mapy zpráv příkaz cílové třídy – stejným způsobem, prohledají se standardní zprávy. Pokud se najde shoda, volá obslužnou rutinu. Vyhledávání map zpráv je vysvětleno v [jak rámci hledání mapy zpráv](../mfc/how-the-framework-searches-message-maps.md).  
  
## <a name="see-also"></a>Viz také  
 [Jakým způsobem volá Framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

