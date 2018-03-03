---
title: "Životní cyklus dialogového okna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 743aed312008d1908701933ec642dd52b0ac3ec8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="life-cycle-of-a-dialog-box"></a>Životní cyklus dialogového okna
Během životního cyklu dialogového okna uživatel vyvolá dialogové okno, obvykle uvnitř obslužná rutina, která vytvoří a inicializuje objektu dialogového okna, uživatel pracuje se dialogové okno a zavření dialogového okna.  
  
 Vaší obslužné rutiny pro modálních dialogových oken, shromažďuje všechna data po zavření dialogového okna zadané uživatelem. Vzhledem k tomu, že objektu dialogového okna existuje po jeho dialogového okna zavřel, jednoduše můžete členské proměnné vlastní třídy dialogového okna jak extrahovat data.  
  
 Pro nemodální dialogová okna může často extrahovat data z objektu dialogového okna, dialogové okno je stále viditelné. V určitém okamžiku objektu dialogového okna zničeno; v takovém případě závisí na kódu.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Vytváření a zobrazování dialogových oken](../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [Vytváření modálních dialogových oken](../mfc/creating-modal-dialog-boxes.md)  
  
-   [Vytváření nemodálních dialogových oken](../mfc/creating-modeless-dialog-boxes.md)  
  
-   [Použití šablony dialogového okna v paměti](../mfc/using-a-dialog-template-in-memory.md)  
  
-   [Nastavení barvy pozadí dialogových oken](../mfc/setting-the-dialog-boxs-background-color.md)  
  
-   [Inicializace dialogových oken](../mfc/initializing-the-dialog-box.md)  
  
-   [Zpracování zpráv systému Windows ve vašem dialogovém okně](../mfc/handling-windows-messages-in-your-dialog-box.md)  
  
-   [Načítání dat z objektu dialogového okna](../mfc/retrieving-data-from-the-dialog-object.md)  
  
-   [Zavření dialogového okna](../mfc/closing-the-dialog-box.md)  
  
-   [Zničení dialogových oken](../mfc/destroying-the-dialog-box.md)  
  
-   [Výměna dat dialogových oken (DDX) a ověřování (DDV)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [Vlastnost list dialogových oken](../mfc/property-sheets-and-property-pages-mfc.md)  
  
## <a name="see-also"></a>Viz také  
 [Dialogová okna](../mfc/dialog-boxes.md)

