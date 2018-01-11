---
title: "Jak se Nepříkazové zprávy svým obslužným | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 33d0d65c9916cfc571ecfd623138938c0c883ba5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Jak se nepříkazové zprávy dostanou k svým obslužným rutinám
Na rozdíl od příkazů standardní zprávy Windows získat není směrován přes strukturu cíle, ale jsou obvykle zpracovávány okno, ke kterému Windows odešle zprávu. Okno může být okno rámce, podřízená okna MDI, standardního ovládacího prvku, dialogové okno, zobrazení nebo jiný druh podřízeného okna.  
  
 Za běhu, jednotlivých období systému Windows je připojen k objektu okna (přímo nebo nepřímo odvozené z `CWnd`) má své vlastní přidružené zprávy mapy a obslužné rutiny funkce. Rozhraní používá zpráva mapy – jako u příkazu – k mapování příchozích zpráv na obslužné rutiny.  
  
## <a name="see-also"></a>Viz také  
 [Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

