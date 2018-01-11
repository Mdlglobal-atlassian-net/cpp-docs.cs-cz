---
title: "Zpracování zpráv s oznámením v ovládacím prvku matrice | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22a8b584c309cd6698ddd73449fcbba866111190
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Zpracování zpráv s oznámením v ovládacím prvku matrice
V nadřazené třídě ovládacího prvku matrice, vytvořit `OnChildNotify` funkce obslužná rutina s příkazem přepínač pro libovolný matrice – ovládací prvek (`CReBarCtrl`) chcete zpracování zpráv s oznámením. Oznámení se odesílají do nadřazeného okna, když uživatel nastavuje tažením objekty v ovládacím prvku matrice změny rozložení pruhy matrice, odstraní pásmech z ovládacího prvku matrice a tak dále.  
  
 Objekt ovládacího prvku matrice může odeslat následující zprávy oznámení:  
  
-   **RBN_AUTOSIZE** poslal ovládacím prvkem matrice (vytvořené pomocí **RBS_AUTOSIZE** styl) při matrice automaticky změní velikost sebe sama.  
  
-   **RBN_BEGINDRAG** poslal ovládacím prvkem matrice, když uživatel zahájí přetahování pásmo.  
  
-   **RBN_CHILDSIZE** poslal ovládacím prvkem matrice při změně velikosti vzdálené podřízeného okna.  
  
-   **RBN_DELETEDBAND** odesílá ovládacím prvkem matrice poté, co byla odstraněna pásmo.  
  
-   **RBN_DELETINGBAND** poslal ovládacím prvkem matrice po pásmo má být odstraněn.  
  
-   **RBN_ENDDRAG** poslal ovládacím prvkem matrice, když uživatel přestane přetahování pásmo.  
  
-   **RBN_GETOBJECT** poslal ovládacím prvkem matrice (vytvořené pomocí **RBS_REGISTERDROP** styl) Pokud je objekt přetažen přes vzdálené správy v ovládacím prvku.  
  
-   **RBN_HEIGHTCHANGE** odeslaných službou ovládacím prvkem matrice došlo ke změně jeho výšku.  
  
-   **RBN_LAYOUTCHANGED** poslal ovládacím prvkem matrice, když uživatel změní rozložení ovládacího prvku pásma.  
  
 Další informace o těchto oznámeních naleznete v tématu [matrice – ovládací prvek odkazu](http://msdn.microsoft.com/library/windows/desktop/bb774375) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

