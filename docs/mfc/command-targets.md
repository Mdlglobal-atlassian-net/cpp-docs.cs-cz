---
title: "Příkaz cíle | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 16a2599b97d88cf4e36b15a70203fc0ca91ca2a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="command-targets"></a>Cíle příkazů
Obrázek [příkazy v rámci](../mfc/user-interface-objects-and-command-ids.md) ukazuje připojení mezi objekt uživatelského rozhraní, například položku nabídky a obslužné rutiny, která volá framework k provedení příkazu výsledné při kliknutí na objekt.  
  
 Systém Windows odešle zprávy, které nejsou příkaz zprávy přímo do časového období, jejichž obslužné rutiny pro zprávy je potom volána. Ale rozhraní směruje příkazy na počet objektů candidate – názvem "cíle příkazů" – jeden z nich obvykle vyvolá obslužnou rutinu pro příkaz. Funkce obslužných rutin fungovat stejným způsobem jako pro příkazy a standardní zprávy Windows, ale mechanismy, které se nazývají se liší, jak je popsáno v [jakým způsobem volá Framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md).  
  
## <a name="see-also"></a>Viz také  
 [Zprávy a příkazy v rozhraní Framework](../mfc/messages-and-commands-in-the-framework.md)

