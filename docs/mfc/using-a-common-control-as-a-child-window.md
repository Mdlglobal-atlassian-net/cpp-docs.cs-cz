---
title: "Použití běžného ovládacího prvku jako podřízeného okna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 116b844f9ecc270d31fe3731c38a63e64b2541fe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-a-common-control-as-a-child-window"></a>Použití běžného ovládacího prvku jako podřízeného okna
Některé běžné ovládací prvky Windows lze použít jako podřízeného okna ostatní okna. Následující postup popisuje, jak vytvořit dynamicky běžného ovládacího prvku a pak s ním pracovat.  
  
### <a name="to-use-a-common-control-as-a-child-window"></a>Použití běžného ovládacího prvku jako podřízeného okna  
  
1.  Definování ovládacího prvku v související třídy nebo obslužná rutina.  
  
2.  Použití přepsání ovládacího prvku [CWnd::Create](../mfc/reference/cwnd-class.md#create) metodu pro vytvoření ovládacího prvku Windows.  
  
3.  Po vytvoření ovládacího prvku (jako včasné jako `OnCreate` obslužná rutina Pokud podtřídy ovládacího prvku), můžete upravit pomocí jeho členské funkce ovládacího prvku. V popisech jednotlivých ovládacích prvků v [ovládací prvky](../mfc/controls-mfc.md) podrobnosti o metody.  
  
4.  Pokud jste hotovi s ovládacím prvkem, použijte [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) odstranění ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)
