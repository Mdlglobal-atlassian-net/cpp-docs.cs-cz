---
title: Jak se Nepříkazové zprávy svým obslužným | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3999c74bf7a612acb998e7a044c12948d7679d9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343879"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Jak se nepříkazové zprávy dostanou k svým obslužným rutinám
Na rozdíl od příkazů standardní zprávy Windows získat není směrován přes strukturu cíle, ale jsou obvykle zpracovávány okno, ke kterému Windows odešle zprávu. Okno může být okno rámce, podřízená okna MDI, standardního ovládacího prvku, dialogové okno, zobrazení nebo jiný druh podřízeného okna.  
  
 Za běhu, jednotlivých období systému Windows je připojen k objektu okna (přímo nebo nepřímo odvozené z `CWnd`) má své vlastní přidružené zprávy mapy a obslužné rutiny funkce. Rozhraní používá zpráva mapy – jako u příkazu – k mapování příchozích zpráv na obslužné rutiny.  
  
## <a name="see-also"></a>Viz také  
 [Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

