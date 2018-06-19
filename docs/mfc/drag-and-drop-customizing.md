---
title: 'Přetažení: přizpůsobení | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [MFC], implementing in non-OLE applications
- drag and drop [MFC], customizing behavior
- drag and  [MFC], COleDataSource object
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], customizing behavior
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 59ec5a5a493106750fa7bb8c7ec31b8dbb011070
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344240"
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
