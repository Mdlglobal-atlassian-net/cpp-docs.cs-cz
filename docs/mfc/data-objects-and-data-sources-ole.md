---
title: "Datové objekty a zdroje dat (OLE) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb39b5089b7cd4849e5afd3eaac239c0c2ab3adf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="data-objects-and-data-sources-ole"></a>Datové objekty a zdroje dat (OLE)
Při provádění přenosu dat, buď pomocí schránky nebo přetažení a drop, data má zdroj a cíl. Jednu aplikaci poskytuje data pro kopírování a přijímá ho jiná aplikace pro vložení. Každé straně přenos je potřeba provádět různé operace na stejná data pro přenos proběhla úspěšně. Knihovna Microsoft Foundation Class (MFC) obsahuje dvě třídy, které představují každé straně tento přenos:  
  
-   Zdroje dat (jak je implementované `COleDataSource` objekty) představují na straně zdroje dat k přenesení. Zdroj aplikací jsou vytvořeny, když data budou zkopírovány do schránky nebo je-li data pro operaci přetažení myší.  
  
-   Datové objekty (jak je implementované `COleDataObject` objekty) představují přenos dat na cílový straně. Jsou vytvořeny při cílové aplikace má data vyřadit do ní, nebo když se zobrazí výzva k provedení operace vložte ze schránky.  
  
 Na následující články popisují, jak se datové objekty a zdroje dat ve svých aplikacích. Tyto informace platí pro kontejner a server aplikace, protože obě může být volána po k kopírovat a vkládat data.  
  
-   [Datové objekty a zdroje dat: vytváření a likvidace](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Datové objekty a zdroje dat: manipulace](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přetažení](../mfc/drag-and-drop-ole.md)  
  
 [Schránky](../mfc/clipboard.md)  
  
## <a name="see-also"></a>Viz také  
 [OLE](../mfc/ole-in-mfc.md)   
 [COleDataObject – třída](../mfc/reference/coledataobject-class.md)   
 [Coledatasource – třída](../mfc/reference/coledatasource-class.md)