---
title: "Výběr grafického objektu v kontextu zařízení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- graphic objects [MFC], selecting into device context
- SelectObject method [MFC]
- GDI objects [MFC], device contexts
- lifetime, graphic objects [MFC]
- device contexts, selecting graphic objects into
- device contexts, graphic objects [MFC]
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5909625b816deb1303821aaec4034fa24f29be5f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="selecting-a-graphic-object-into-a-device-context"></a>Výběr grafického objektu v kontextu zařízení
Toto téma se týká použití grafických objektů v kontextu zařízení časového období. Po jste [vytvoření objektu](../mfc/one-stage-and-two-stage-construction-of-objects.md), je nutné vybrat do kontextu zařízení místo výchozího objektu v ní uloženy:  
  
 [!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/cpp/selecting-a-graphic-object-into-a-device-context_1.cpp)]  
  
## <a name="lifetime-of-graphic-objects"></a>Doba platnosti grafických objektů  
 Je objekt vrácený [SelectObject –](../mfc/reference/cdc-class.md#selectobject) je "dočasný." To znamená, se odstraní podle [OnIdle](../mfc/reference/cwinapp-class.md#onidle) funkce člena třídy `CWinApp` čas při příštím program získá nečinnosti. Také můžete použít objekt vrácený `SelectObject` v jedné funkce bez vrácení řízení hlavní zpráva smyčky, budete mít žádný problém.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Grafické objekty](../mfc/graphic-objects.md)  
  
-   [Jednofázová a dvoufázová konstrukce grafické objekty](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [Kontexty zařízení](../mfc/device-contexts.md)  
  
-   [Kreslení v zobrazení](../mfc/drawing-in-a-view.md)  
  
## <a name="see-also"></a>Viz také  
 [Grafické objekty](../mfc/graphic-objects.md)

