---
title: "Přetažení (OLE) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5efc5a12acbad786039b687e5a9e3bb00e62e090
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="drag-and-drop-ole"></a>Přetažení (OLE)
Funkce přetažení myší OLE je primárně zástupce pro kopírování a vkládání dat. Použijete-li do schránky Kopírovat nebo vložit data, jsou vyžaduje několik kroků. Vyberte data, klikněte na **Vyjmout** nebo **kopie** z **upravit** nabídky, přejděte do cílového souboru, okno nebo aplikace, umístěte kurzor do požadovaného umístění a klikněte na **Vložení** z **upravit** nabídky.  
  
 OLE – přetažení se liší od mechanismus přetažení myší Správce souborů, který lze zpracovat pouze názvy souborů a je navrženo konkrétně k předat názvy souborů aplikace. OLE – přetažení je mnohem víc Obecné. Umožňuje přetažení všechna data, která může být také umístěny do schránky.  
  
 Pokud používáte OLE – přetažení, odeberete z procesu dva kroky. Vyberte data z okna zdroje ("rozevírací zdroj"), přetáhněte jej do požadované cílové umístění ("cíle přetažení") a umístěte jej uvolněním tlačítka myši. Operaci se eliminuje potřeba nabídky a je rychlejší než pořadí, kopírování a vkládání. Jediným požadavkem je, že rozevírací zdroje i cíle přetažení musí být otevřené a aspoň částečně viditelný na obrazovce.  
  
 Pomocí OLE – přetažení, data můžete přenést z jednoho umístění do druhého v rámci dokumentu, mezi různé dokumenty nebo mezi aplikacemi. Může být implementováno v kontejneru nebo serverová aplikace a všechny aplikace může být zdroje přetažení, cíle přetažení nebo obojí. Pokud má aplikace rozevírací zdroje a cíle přetažení podporu implementována, je povoleno přetažení mezi podřízená okna, nebo v rámci jednoho okna. Tato funkce může usnadnit aplikace mnohem používání.  
  
 Pokud chcete využívat možnosti přetahování myší OLE, přečtěte si téma [přetažení: přizpůsobení](../mfc/drag-and-drop-customizing.md). Techniky popsané v tomto tématu můžete použít k aplikacím jiných než OLE vyřadit zdroje. Článek [přetažení: implementace cíle přetažení](../mfc/drag-and-drop-implementing-a-drop-target.md) popisuje, jak implementovat podporu cíle přetažení OLE a aplikacích jiných než OLE. Může také být vhodné vzorky MFC OLE [OCLIENT](../visual-cpp-samples.md) a [HIERSVR](../visual-cpp-samples.md).  
  
 Pokud nebyly přečíst [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md) rodiny článků, můžete nyní. Tyto články vysvětlují základní informace o přenosu dat a jak implementovat ve svých aplikacích.  
  
 Další informace o přetažení najdete v tématu:  
  
-   [Přetažení: implementace zdroje přemístění](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [Přetažení: implementace cíle přetažení](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [Přetažení: přizpůsobení](../mfc/drag-and-drop-customizing.md)  
  
## <a name="see-also"></a>Viz také  
 [OLE](../mfc/ole-in-mfc.md)   
 [Datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md)

