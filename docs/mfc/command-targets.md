---
title: Příkaz cíle | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cbcfa1042a8430c704bad93e4bc0ce5655b5921
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="command-targets"></a>Cíle příkazů
Obrázek [příkazy v rámci](../mfc/user-interface-objects-and-command-ids.md) ukazuje připojení mezi objekt uživatelského rozhraní, například položku nabídky a obslužné rutiny, která volá framework k provedení příkazu výsledné při kliknutí na objekt.  
  
 Systém Windows odešle zprávy, které nejsou příkaz zprávy přímo do časového období, jejichž obslužné rutiny pro zprávy je potom volána. Ale rozhraní směruje příkazy na počet objektů candidate – názvem "cíle příkazů" – jeden z nich obvykle vyvolá obslužnou rutinu pro příkaz. Funkce obslužných rutin fungovat stejným způsobem jako pro příkazy a standardní zprávy Windows, ale mechanismy, které se nazývají se liší, jak je popsáno v [jakým způsobem volá Framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md).  
  
## <a name="see-also"></a>Viz také  
 [Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)

