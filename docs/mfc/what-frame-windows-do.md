---
title: "Co dělat okna s rámečkem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- frame windows [MFC], about frame widows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7cda73727a7481c6c7d8b5002467ceeef378fdae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="what-frame-windows-do"></a>Jak fungují okna s rámečkem
Kromě zobrazení jednoduše rámců, okna s rámečkem zodpovídají za množství úkoly při spolupráci rámečku s jeho zobrazení a aplikace. [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) a [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) dědí [CFrameWnd](../mfc/reference/cframewnd-class.md), takže mají `CFrameWnd` možnosti, jakož i nové funkce, které si přidají. Podřízená okna příklady zobrazení, ovládací prvky, jako jsou tlačítka a seznamy a ovládací pruhy, včetně panely nástrojů, stavové řádky a řádky dialogové okno.  
  
 Okně s rámečkem je zodpovědný za správu rozložení jeho podřízených systému windows. V rozhraní MFC framework oken s rámečkem umisťuje všechny ovládací pruhy, zobrazení a další podřízená okna uvnitř své klientské oblasti.  
  
 Okně s rámečkem také předá příkazy k jeho zobrazení a může odpovědět na zprávy oznámení z ovládacího prvku windows.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Ovládací pruhy (jak je začlenit do rámce okna)](../mfc/control-bars.md)  
  
-   [Správa nabídek, ovládacích pruhů a akcelerátorů (jak je začlenit do rámce okna)](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
-   [Příkaz směrování (z okna rámce k jeho zobrazení a jiné cíle příkazů)](../mfc/command-routing.md)  
  
-   [Architektury dokument/View](../mfc/document-view-architecture.md)  
  
-   [Ovládací pruhy](../mfc/control-bars.md)  
  
-   [Ovládací prvky](../mfc/controls-mfc.md)  
  
## <a name="see-also"></a>Viz také  
 [Okna s rámečkem](../mfc/frame-windows.md)

