---
title: "Komponenty dialogového okna v rozhraní Framework | Microsoft Docs"
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
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 840e66def6a908b26b5021537eddee68c50a9628
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-box-components-in-the-framework"></a>Komponenty dialogového okna v rozhraní .NET Framework
V rozhraní MFC framework dialogové okno má dvě součásti:  
  
-   Prostředek šablony dialogového okna, které určuje ovládací prvky dialogových oken a jejich umístění.  
  
     Prostředek dialogu ukládá šablony dialogového okna, ve kterém Windows vytvoří dialogového okna a zobrazí se. Šablona specifikuje charakteristiky dialogových oken, včetně jeho velikost, umístění, styl a typy a umístění ovládacích prvků dialogových oken. Obvykle použijete šablony dialogového okna uložený jako prostředek, ale můžete také vytvořit vlastní šablonu v paměti.  
  
-   Odvozené třídy dialogového okna, od [CDialog](../mfc/reference/cdialog-class.md), aby programové rozhraní pro správu dialogové okno.  
  
     Dialogové okno je a bude připojen k období systému Windows, když je viditelná. Při vytvoření dialogového okna prostředků šablony dialogového okna se používá jako šablonu při vytváření podřízených ovládacích prvků okno pro dialogové okno.  
  
## <a name="see-also"></a>Viz také  
 [Dialogová okna](../mfc/dialog-boxes.md)   
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

