---
title: "Windows Sockets: Odvozování z tříd soketů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- derived classes [MFC], from socket classes
- Windows Sockets [MFC], deriving from socket classes
- sockets [MFC], deriving from socket classes
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 63f8b8f735b62c1cbfedd50320bf65cec5905632
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows Sockets: Odvozování z tříd soketů
Tento článek popisuje některé funkce, které můžete získat odvozením vlastní třídy jednu z tříd soketů.  
  
 Vaše vlastní třídy soketů může být odvozen z rozhraní [CAsyncSocket](../mfc/reference/casyncsocket-class.md) nebo [CSocket](../mfc/reference/csocket-class.md) přidat vlastní funkce. Konkrétně tyto třídy zadat počet virtuální členské funkce, které můžete přepsat. Tyto funkce patří [události OnReceive](../mfc/reference/casyncsocket-class.md#onreceive), [OnSend](../mfc/reference/casyncsocket-class.md#onsend), [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept), [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect), a [při zavření](../mfc/reference/casyncsocket-class.md#onclose). Funkce můžete přepsat v třídě odvozené soketu využívat výhod oznámení, která poskytují při výskytu události v síti. Tyto funkce zpětného volání oznámení jako upozornění na důležité soketu událostmi, například příjmu dat, můžete začít čtení volá framework. Další informace o funkcích oznámení najdete v tématu [Windows Sockets: oznámení soketů](../mfc/windows-sockets-socket-notifications.md).  
  
 Kromě toho třídy `CSocket` poskytuje [OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending) – členská funkce (rozšířené přepisovatelné). MFC volání této funkce, přičemž soketu je čerpání zpráv systému Windows. Můžete přepsat `OnMessagePending` vyhledat konkrétní zprávy ze systému Windows a reagovat na ně.  
  
 Výchozí verze `OnMessagePending` zadaný v třídě `CSocket` prozkoumá fronty zpráv pro `WM_PAINT` zprávy při čekání na dokončení blokování volání. Odešle malovat zprávy zlepšení kvality zobrazení. Kromě zajištění dostatečného to něco užitečné, to ukazuje jeden ze způsobů, které mohou potlačit funkce sami. Další příklad, zvažte použití `OnMessagePending` pro následující úlohu. Předpokládejme, že zobrazit dialogové okno nemodální při čekání na transakci sítě k dokončení. Dialogové okno obsahuje tlačítko Storno, které uživatele můžete použít ke zrušení blokování transakce, které trvá příliš dlouho. Vaše `OnMessagePending` přepsání může čerpadla zprávy týkající se tohoto dialogového okna bez režimu.  
  
 Ve vaší `OnMessagePending` přepsat, vraťte se buď **TRUE** nebo return volání základní třídy verzi `OnMessagePending`. Základní třída verze volejte v případě, že provede práci, kterou chcete přesto provést.  
  
 Další informace naleznete v tématu:  
  
-   [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Blokování](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets: Pořadí bajtů](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets: Převádění řetězců](../mfc/windows-sockets-converting-strings.md)  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)

