---
title: "Zničení ovládacího prvku seznam | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 069d9eddc44aa4c0f258f97fce1e39266ced95b6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="destroying-the-list-control"></a>Zničení ovládacího prvku seznam
Pokud vložit vaše [CListCtrl](../mfc/reference/clistctrl-class.md) objekt jako datový člen třídy zobrazení nebo dialogové okno, byla při jeho vlastníka zničena. Pokud používáte [CListView](../mfc/reference/clistview-class.md), rozhraní zničí ovládacího prvku, když ho zničí zobrazení.  
  
 Pokud je uspořádat pro některý ze seznamu data k uložení do aplikací, nikoli ovládací prvek seznamu, musíte uspořádat pro zrušení jeho přidělení. Další informace najdete v tématu [položky zpětného volání a maska zpětného volání](http://msdn.microsoft.com/library/windows/desktop/bb774736) ve Windows SDK.  
  
 Kromě toho jste zodpovědní za rušení přidělení všechny seznamy obrázků jste vytvořili a přidružený objekt ovládacího prvku seznam.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)
