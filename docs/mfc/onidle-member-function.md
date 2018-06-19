---
title: ONIDLE – členská funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnIdle
dev_langs:
- C++
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bbe912db448e424f18b6d72f6e148312c5940687
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350364"
---
# <a name="onidle-member-function"></a>OnIdle – členská funkce
Při zpracování zprávy žádné Windows volá framework [CWinApp](../mfc/reference/cwinapp-class.md) – členská funkce [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (popsaný v referenční příručka knihovny MFC).  
  
 Přepsání `OnIdle` k provedení úlohy na pozadí. Výchozí verze aktualizace stavu objektů uživatelského rozhraní, jako jsou tlačítka panelu nástrojů a provádí čištění dočasné objekty vytvořené pomocí rozhraní v průběhu operace. Následující obrázek znázorňuje, jakým způsobem volá smyčce zpráv `OnIdle` Pokud nejsou žádné zprávy ve frontě.  
  
 ![Zpráva smyčky proces](../mfc/media/vc387c1.gif "vc387c1")  
Zpráva smyčky  
  
 Další informace o co můžete dělat v nečinné smyčky najdete v tématu [zpracování nečinné smyčky](../mfc/idle-loop-processing.md).  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
