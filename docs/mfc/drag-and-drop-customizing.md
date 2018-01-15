---
title: "Přetažení: přizpůsobení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- drag and drop [MFC], implementing in non-OLE applications
- drag and drop [MFC], customizing behavior
- drag and  [MFC], COleDataSource object
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], customizing behavior
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 387344160cf2009b19ad8de820eabc6063ae1f7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="drag-and-drop-customizing"></a>Přetažení: Přizpůsobení
Výchozí implementace funkce přetažení myší je dostatečné pro většinu aplikací. Některé aplikace však může vyžadovat, aby toto standardní chování změnit. Tento článek vysvětluje kroky potřebné k změnit toto výchozí nastavení. Kromě toho můžete použít tento postup k vytvoření aplikace, které nepodporují složené dokumenty jako rozevírací zdroje.  
  
 Pokud jsou přizpůsobení standardní chování OLE přetahování myší, nebo máte aplikací jiných než OLE, musíte vytvořit `COleDataSource` objektu tak, aby obsahovala data. Když uživatel spustí operace přetahování myší, by měly volat kódu `DoDragDrop` funkce z tohoto objektu místo z jiné třídy, které podporují operací přetažení myší.  
  
 Volitelně můžete vytvořit `COleDropSource` objekt řízení rozevíracího a některé jeho funkce v závislosti na typu chcete změnit chování přepsat. Tento objekt zdroj vynechání jsou předána do `COleDataSource::DoDragDrop` Chcete-li změnit výchozí chování těchto funkcí. Tyto různé možnosti Povolit značnou flexibilitu v tom, jak podporu operací přetažení myší v aplikaci. Další informace o zdrojích dat, najdete v článku [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md).  
  
 Chcete-li přizpůsobit operací přetažení myší následující funkce se dá přepsat:  
  
|přepsání|Chcete-li přizpůsobit|  
|--------------|------------------|  
|`OnBeginDrag`|Jak přetahování je zahájeno po zavolání metody `DoDragDrop`.|  
|`GiveFeedback`|Vizuální zpětnou vazbu, například vzhled kurzor pro různé rozevírací výsledky.|  
|`QueryContinueDrag`|Ukončení operací přetažení myší. Tato funkce umožňuje zkontrolovat klíče stavy modifikátor během operace přetažení.|  
  
## <a name="see-also"></a>Viz také  
 [Přetažení (OLE)](../mfc/drag-and-drop-ole.md)   
 [COleDropSource – třída](../mfc/reference/coledropsource-class.md)   
 [COleDataSource – třída](../mfc/reference/coledatasource-class.md)
