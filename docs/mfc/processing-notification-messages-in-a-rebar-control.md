---
title: Zpracování zpráv s oznámením v ovládacím prvku matrice | Dokumentace Microsoftu
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
ms.openlocfilehash: dce09e84e9a2b5262d05847746f819a122ec36c5
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208972"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Zpracování zpráv s oznámením v ovládacím prvku matrice
V nadřazené třídě ovládacího prvku matrice, vytvořte `OnChildNotify` funkci obslužné rutiny pomocí příkazu switch pro libovolný matrice – ovládací prvek (`CReBarCtrl`) zpracování zpráv s oznámením. Oznámení se posílají nadřazenému oknu, když uživatel přetáhne objekty nad ovládacím prvkem matrice, změny rozložení pruhy matrice, odstraní pásmech z ovládacího prvku matrice a tak dále.  
  
 Objekt ovládacího prvku matrice může odeslat následující upozornění:  
  
-   RBN_AUTOSIZE odesílaných ovládacím prvkem matrice (vytvořenou pomocí stylu RBS_AUTOSIZE) Pokud matrice automaticky změní velikost sebe sama.  
  
-   RBN_BEGINDRAG odesílaných ovládacího prvku rebar, když uživatel zahájí přetahování pásmo.  
  
-   RBN_CHILDSIZE odesílaných ovládacím prvkem matrice při změně velikosti podřízeného okna.  
  
-   RBN_DELETEDBAND odesílaných ovládacím prvkem matrice po odstranění svazku.  
  
-   RBN_DELETINGBAND odesílaných ovládacím prvkem matrice pásmo se neodstraní.  
  
-   RBN_ENDDRAG odesílaných ovládacího prvku rebar, když uživatel přestane přetahovat pásmo.  
  
-   RBN_GETOBJECT odesílaných ovládacím prvkem matrice (vytvořenou pomocí stylu RBS_REGISTERDROP) když je objekt přetažen přes vzdálené správy v rámci ovládacího prvku.  
  
-   RBN_HEIGHTCHANGE odesílaných ovládacího prvku rebar, když došlo ke změně jeho výška.  
  
-   RBN_LAYOUTCHANGED odesílaných ovládacího prvku rebar, když uživatel změní rozložení pásem ovládacího prvku.  
  
 Další informace o těchto oznámeních najdete v tématu [matrice – ovládací prvek odkazu](https://msdn.microsoft.com/library/windows/desktop/bb774375) v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

