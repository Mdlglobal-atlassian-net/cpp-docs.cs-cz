---
title: "ONIDLE – členská funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OnIdle
dev_langs: C++
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4dfbc0a1f20cb6cc01143ed6f07a63e84b53be6b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="onidle-member-function"></a>OnIdle – členská funkce
Při zpracování zprávy žádné Windows volá framework [CWinApp](../mfc/reference/cwinapp-class.md) – členská funkce [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (popsaný v referenční příručka knihovny MFC).  
  
 Přepsání `OnIdle` k provedení úlohy na pozadí. Výchozí verze aktualizace stavu objektů uživatelského rozhraní, jako jsou tlačítka panelu nástrojů a provádí čištění dočasné objekty vytvořené pomocí rozhraní v průběhu operace. Následující obrázek znázorňuje, jakým způsobem volá smyčce zpráv `OnIdle` Pokud nejsou žádné zprávy ve frontě.  
  
 ![Zpráva smyčky proces](../mfc/media/vc387c1.gif "vc387c1")  
Zpráva smyčky  
  
 Další informace o co můžete dělat v nečinné smyčky najdete v tématu [zpracování nečinné smyčky](../mfc/idle-loop-processing.md).  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
