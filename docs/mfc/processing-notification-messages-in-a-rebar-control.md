---
title: Zpracování zpráv s oznámením v ovládacím prvku matrice | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a1d42d129ab7b7d2e98ae1126b8f32f68b1f356
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931824"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Zpracování zpráv s oznámením v ovládacím prvku matrice
V nadřazené třídě ovládacího prvku matrice, vytvořit `OnChildNotify` funkce obslužná rutina s příkazem přepínač pro libovolný matrice – ovládací prvek (`CReBarCtrl`) chcete zpracování zpráv s oznámením. Oznámení se odesílají do nadřazeného okna, když uživatel nastavuje tažením objekty v ovládacím prvku matrice změny rozložení pruhy matrice, odstraní pásmech z ovládacího prvku matrice a tak dále.  
  
 Objekt ovládacího prvku matrice může odeslat následující zprávy oznámení:  
  
-   RBN_AUTOSIZE poslal ovládacím prvkem matrice (vytvořeny s styl RBS_AUTOSIZE) Pokud matrice automaticky mění velikost.  
  
-   RBN_BEGINDRAG odesílá ovládacím prvkem matrice, když uživatel zahájí přetahování pásmo.  
  
-   RBN_CHILDSIZE odesílá ovládacím prvkem matrice při změně velikosti vzdálené podřízeného okna.  
  
-   RBN_DELETEDBAND odesílá ovládacím prvkem matrice po odstranění pásmo.  
  
-   RBN_DELETINGBAND odesílá ovládacím prvkem matrice po pásmo má být odstraněn.  
  
-   RBN_ENDDRAG odesílá ovládacím prvkem matrice, když uživatel přestane přetahování pásmo.  
  
-   RBN_GETOBJECT poslal ovládacím prvkem matrice (vytvořeny s styl RBS_REGISTERDROP) Pokud je objekt přetažen přes vzdálené správy v ovládacím prvku.  
  
-   RBN_HEIGHTCHANGE odesílá ovládacím prvkem matrice, pokud došlo ke změně jeho výšku.  
  
-   RBN_LAYOUTCHANGED odesílá ovládacím prvkem matrice, když uživatel změní rozložení ovládacího prvku pásma.  
  
 Další informace o těchto oznámeních naleznete v tématu [matrice – ovládací prvek odkazu](http://msdn.microsoft.com/library/windows/desktop/bb774375) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

