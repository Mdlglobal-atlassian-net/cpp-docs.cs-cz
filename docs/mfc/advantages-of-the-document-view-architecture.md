---
title: "Výhody architektury dokument zobrazení | Microsoft Docs"
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
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aad0ed0df5eb25ccc0dd896a5a032cd190b6c3b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="advantages-of-the-documentview-architecture"></a>Výhody architektury dokument/zobrazení
Klíče výhodou používání architektuře dokument/zobrazení MFC je architektura zvlášť a podporuje více zobrazení do jednoho dokumentu. (Pokud nepotřebujete více zobrazení a malé nároky na dokument/zobrazení je příliš ve vaší aplikaci, se můžete vyhnout architekturu. [Alternativy k architektuře dokument/zobrazení](../mfc/alternatives-to-the-document-view-architecture.md).)  
  
 Předpokládejme, že vaše aplikace umožňuje uživatelům prohlížet číselná data v podobě tabulky nebo ve formě grafu. Uživatel chtít zobrazit současně oba nezpracovaná data, ve formuláři tabulku a graf, který je výsledkem data. Tyto samostatné zobrazení se zobrazí v oknech s rámečkem samostatné nebo v podoknech rozdělovače v rámci jednoho okna. Nyní předpokládejme, že uživatel můžete upravovat data v tabulce a zjistit, změny okamžitě projeví v grafu.  
  
 V prostředí MFC by být zobrazení tabulky a zobrazení grafu založené na různé třídy odvozené od CView. Obě zobrazení bude přidružený objekt jednotlivý dokument. Dokument ukládá data (nebo ho možná získává z databáze). Obě zobrazení k dokumentu přístup a zobrazit data, která se načíst z něj.  
  
 Když uživatel aktualizuje jedno zobrazení, které zobrazit volání objektu `CDocument::UpdateAllViews`. Tato funkce upozorní všechna zobrazení dokumentu a jednotlivých zobrazení se aktualizuje sám pomocí nejnovější data z dokumentu. Jediné volání `UpdateAllViews` synchronizuje různá zobrazení.  
  
 Tento scénář může být obtížné kódu bez oddělit data ze zobrazení, zvlášť pokud zobrazení uložená data sami. S dokument/zobrazení je snadné. Rozhraní framework provede většinu práce spolupráce.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Alternativy k dokument/zobrazení](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [CDocument](../mfc/reference/cdocument-class.md)  
  
-   [CView](../mfc/reference/cview-class.md)  
  
-   [CDocument::UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)  
  
-   [CView::GetDocument](../mfc/reference/cview-class.md#getdocument)  
  
## <a name="see-also"></a>Viz také  
 [Document/View – architektura](../mfc/document-view-architecture.md)

