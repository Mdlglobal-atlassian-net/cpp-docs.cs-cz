---
title: "Zpracování a mapování zpráv | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 64a99bad7d6bc7fa937100cc5bf864e968572402
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="message-handling-and-mapping"></a>Zpracování a mapování zpráv
Rodina Tento článek popisuje zpracování zprávy a příkazy pomocí rozhraní MFC framework a jak se připojit je k jejich funkcím obslužných rutin.  
  
 Tradiční aplikace pro Windows jsou zpracovávány zpráv systému Windows v velké Switch v postupu okno. Místo toho používá MFC [zprávy mapy](../mfc/message-categories.md) mapovat přímé zprávy členské funkce distinct třídy. Mapy zpráv jsou efektivnější než virtuální funkce pro tento účel, které umožňují zprávy zpracovávat objekt nejvhodnější C++ – aplikace, dokumentu, zobrazení a tak dále. Můžete namapovat do jedné zprávy nebo rozsah zpráv, identifikátory příkazů nebo řízení ID.  
  
 **Wm_command –** zprávy – obvykle generují nabídky, tlačítek panelu nástrojů nebo akcelerátorů – také používat mechanismus map zpráv. MFC definuje standard [směrování](../mfc/command-routing.md) příkaz zpráv mezi aplikace, s rámečkem oken, zobrazení a aktivní dokumenty v programu. Můžete přepsat toto směrování, pokud je potřeba.  
  
 Mapy zpráv také zadat způsob aktualizace objektů uživatelského rozhraní (například nabídky a tlačítka panelu nástrojů), povolení nebo zakázání je podle aktuálního kontextu.  
  
 Obecné informace o zprávy a fronty zpráv v systému Windows najdete v tématu [zprávy a fronty zpráv](http://msdn.microsoft.com/library/windows/desktop/ms632590) ve Windows SDK.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Zprávy a příkazy v rozhraní Framework](../mfc/messages-and-commands-in-the-framework.md)  
  
-   [Jakým způsobem volá rámec obslužné rutiny zpráv](../mfc/how-the-framework-calls-a-handler.md)  
  
-   [Jak Framework prohledává mapy zpráv](../mfc/how-the-framework-searches-message-maps.md)  
  
-   [Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)  
  
-   [Mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md)  
  
-   [Postup zobrazení informací o příkazu ve stavovém řádku](../mfc/how-to-display-command-information-in-the-status-bar.md)  
  
-   [Dynamická aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)  
  
-   [Postupy: vytvoření mapy zpráv pro třídu šablony](../mfc/how-to-create-a-message-map-for-a-template-class.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../mfc/mfc-concepts.md)   
 [Obecná témata MFC](../mfc/general-mfc-topics.md)   
 [Třída CWnd](../mfc/reference/cwnd-class.md)   
 [CCmdTarget – třída](../mfc/reference/ccmdtarget-class.md)