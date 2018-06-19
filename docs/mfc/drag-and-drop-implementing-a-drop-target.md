---
title: 'Přetažení: implementace cíle přetažení | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE drag and drop [MFC], implementing drop targets
- OLE drag and drop [MFC], drop target
- drag and drop [MFC], drop target
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 414437f044869fef7ae48883a88688ad50c9ac5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344266"
---
# <a name="drag-and-drop-implementing-a-drop-target"></a>Přetažení: Implementace cíle přetažení
Tento článek popisuje jak provádět cíle přetažení vaší aplikace. Implementace cíle přetažení trvá mírně další práci než implementace zdroje přetažení, ale je stále poměrně jednoduché. Tyto postupy se rovněž vztahují na aplikacích jiných než OLE.  
  
#### <a name="to-implement-a-drop-target"></a>Implementace cíle přetažení  
  
1.  Přidání členské proměnné do jednotlivých zobrazení v aplikaci, která mají být cíle přetažení. Tato proměnná člena musí být typu `COleDropTarget` nebo z něj odvozenou třídu.  
  
2.  Ze třídy zobrazení funkce, která zpracovává `WM_CREATE` zprávy (obvykle `OnCreate`), volání nové členské proměnné `Register` – členská funkce. `Revoke` bude volána automaticky za vás při zobrazení zničena.  
  
3.  Přepište následující funkce. Pokud chcete stejné chování v celé vaší aplikaci, přepište tyto funkce ve třídě zobrazení. Pokud chcete změnit chování v izolované případech nebo chcete povolit vyřazení na jinou hodnotu než`CView` přepsat tyto funkce v systému windows, vaše `COleDropTarget`-odvozené třídy.  
  
    |přepsání|Chcete-li povolit|  
    |--------------|--------------|  
    |`OnDragEnter`|Vyřaďte operací v okně. Voláno, pokud nejprve do okna pole kurzor.|  
    |`OnDragLeave`|Zvláštní chování při operaci přetažení opustí vybrané okno.|  
    |`OnDragOver`|Vyřaďte operací v okně. Voláno, když ukazatel je přetažen napříč okna.|  
    |`OnDrop`|Zpracování dat probíhá vyřazování na vybrané okno.|  
    |`OnScrollBy`|Zvláštní chování při posouvání je nutné v okně cíl.|  
  
 Najdete v článku MAINVIEW. CPP souboru, který je součástí ukázkové MFC OLE [OCLIENT](../visual-cpp-samples.md) příklad, jak tyto funkce fungují společně.  
  
 Další informace naleznete v tématu:  
  
-   [Implementace zdroje přemístění](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [Vytváření a zničení OLE datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Manipulace s OLE datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="see-also"></a>Viz také  
 [Přetažení (OLE)](../mfc/drag-and-drop-ole.md)   
 [COleDropTarget – třída](../mfc/reference/coledroptarget-class.md)
