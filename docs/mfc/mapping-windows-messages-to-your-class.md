---
title: Mapování zpráv systému Windows na třídu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 398888a858165197c6e35be791169a9311f3014b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346266"
---
# <a name="mapping-windows-messages-to-your-class"></a>Mapování zpráv systému Windows na třídu
Pokud potřebujete vašem dialogovém okně pro zpracování zpráv systému Windows, přepište funkce příslušnou obslužnou rutinu. Uděláte to tak, použijte okno Vlastnosti k [mapy zpráv](../mfc/reference/mapping-messages-to-functions.md) pro třídu dialog. Tím se zapíše položku mapy zpráv pro každou zprávu a přidá členské funkce obslužné rutiny zpráv pro třídu. Psaní kódu v obslužné rutiny zpráv používáte editor Visual C++ zdrojového kódu.  
  
 Můžete také přepsat členské funkce [CDialog](../mfc/reference/cdialog-class.md) a jeho základních tříd, zejména [CWnd](../mfc/reference/cwnd-class.md).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)  
  
-   [Běžně přepisované členské funkce](../mfc/commonly-overridden-member-functions.md)  
  
-   [Běžně přidávané členské funkce](../mfc/commonly-added-member-functions.md)  
  
## <a name="see-also"></a>Viz také  
 [Dialogová okna](../mfc/dialog-boxes.md)   
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

