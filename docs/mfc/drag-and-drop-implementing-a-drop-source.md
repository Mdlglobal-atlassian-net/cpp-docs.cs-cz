---
title: "Přetažení: implementace zdroje přetažení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE drag and drop [MFC], initiating drag operations
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], drop source
- OLE drag and drop [MFC], calling DoDragDrop
- drag and drop [MFC], initiating drag operations
- drag and drop [MFC], drop source
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4ebb5968497d274c714f3d24c0c090ff71de81a1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="drag-and-drop-implementing-a-drop-source"></a>Přetažení: Implementace zdroje přemístění
Tento článek vysvětluje, jak získat aplikace k poskytování dat na operaci přetažení myší.  
  
 Základní implementace zdroje přetažení je poměrně jednoduché. Prvním krokem je určit, jaké události se zahájit operaci přetažení. Doporučené pokyny pro uživatelské rozhraní definovat začátku operaci přetažení výběru dat a `WM_LBUTTONDOWN` událostí, ke kterým dochází v bodě uvnitř vybraná data. Ukázky MFC OLE [OCLIENT](../visual-cpp-samples.md) a [HIERSVR](../visual-cpp-samples.md) postupujte podle následujících pokynů.  
  
 Pokud vaše aplikace je kontejner a je vybraná data propojený nebo vložený objekt typu `COleClientItem`, volání jeho `DoDragDrop` – členská funkce. Jinak, vytvořit `COleDataSource` objektu, inicializujte ho s výběrem a volání objekt zdroje dat `DoDragDrop` – členská funkce. Pokud vaše aplikace je server, použijte `COleServerItem::DoDragDrop`. Informace o přizpůsobení standardní chování přetahování myší, najdete v článku [přetažení: přizpůsobení](../mfc/drag-and-drop-customizing.md).  
  
 Pokud `DoDragDrop` vrátí `DROPEFFECT_MOVE`, okamžitě odstranit zdroj dat z zdrojový dokument. Žádnou návratovou hodnotu z `DoDragDrop` nemá žádný vliv na zdroje přetažení.  
  
 Další informace naleznete v tématu:  
  
-   [Implementace cíle přetažení](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [Přizpůsobení – přetažení](../mfc/drag-and-drop-customizing.md)  
  
-   [Vytváření a zničení OLE datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Manipulace s OLE datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="see-also"></a>Viz také  
 [Přetažení (OLE)](../mfc/drag-and-drop-ole.md)   
 [COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop)   
 [COleClientItem::DoDragDrop](../mfc/reference/coleclientitem-class.md#dodragdrop)   
 [CView::OnDragLeave](../mfc/reference/cview-class.md#ondragleave)

