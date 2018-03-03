---
title: "Stream operace v ovládacích prvcích pro úpravy s formátováním | Microsoft Docs"
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
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c1a73790124adbc1ff8a89290bf4e1d7a4fa6824
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="stream-operations-in-rich-edit-controls"></a>Operace s datovými proudy v ovládacích prvcích pro úpravy s formátováním
Datové proudy můžete použít k přenosu dat do nebo z ovládacího prvku RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Datový proud je definované [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) strukturu, která určuje vyrovnávací paměť a funkce zpětné volání definované aplikací.  
  
 Načíst data do s formátováním ovládacích prvků pro úpravy (tedy Streamovat data v), použijte [StreamIn](../mfc/reference/cricheditctrl-class.md#streamin) – členská funkce. Ovládací prvek opakovaně volá funkci zpětné volání definované aplikací, která přenáší pokaždé, když část dat do vyrovnávací paměti.  
  
 Uložit obsah s formátováním ovládacích prvků pro úpravy (tedy Streamovat data out), můžete použít [StreamOut](../mfc/reference/cricheditctrl-class.md#streamout) – členská funkce. Ovládací prvek opakovaně zapíše do vyrovnávací paměti a pak zavolá funkci zpětné volání definované aplikací. Funkce zpětného volání pro každé volání, která uloží obsah vyrovnávací paměti.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

