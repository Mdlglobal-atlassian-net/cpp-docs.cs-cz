---
title: "Přizpůsobení položky záhlaví & č. 39; vzhled s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 494372aa3e6dcc418a6ffdacbb7b06635a010310
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="customizing-the-header-item39s-appearance"></a>Přizpůsobení položky záhlaví & č. 39; s vzhledu
Nastavením *dwStyle* parametr při prvním vytvoření ovládacího prvku záhlaví ([CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create)), můžete definovat vzhled a chování záhlaví položky nebo hlavičky ovládací prvek.  
  
 Tady je vzorkování styly, které můžete nastavit a jejich účel:  
  
-   Chcete-li položku záhlaví vypadat pushbutton, použijte `HDS_BUTTONS` stylu.  
  
     Tento styl použijte, pokud chcete provádět akce v reakci na kliknutí myší na položky záhlaví, jako je například řazení dat podle konkrétního sloupce, jak se provádí v aplikaci Microsoft Outlook.  
  
-   Položky hlavičky "aktivní sledování" vzhled při předá myší nad nimi, použijte `HDS_HOTTRACK` stylu.  
  
     Aktivní sledování zobrazí 3D outline jako ukazatel prochází přes položku v opačném případě ploché panelu.  
  
-   K označení, že by být skrytý ovládacím prvku záhlaví, použijte `HDS_HIDDEN` stylu.  
  
     `HDS_HIDDEN` Styl označuje, že ovládacím prvku záhlaví je určena pro použití jako kontejner dat a není ovládacího prvku visual. Tento styl není automaticky skrýt ovládacího prvku, ale místo toho má vliv na chování `CHeaderCtrl::Layout`. Hodnota vrácená v **cy** členem `WINDOWPOS` struktura bude nula indikující, že ovládacího prvku by neměly být viditelné pro uživatele.  
  
 Další informace o těchto vlastnostech najdete v tématu [položky](http://msdn.microsoft.com/library/windows/desktop/bb775238) ve Windows SDK. Informace o přidávání položek do ovládacího prvku záhlaví najdete v tématu [přidávání položek do ovládacího prvku záhlaví](../mfc/adding-items-to-the-header-control.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

