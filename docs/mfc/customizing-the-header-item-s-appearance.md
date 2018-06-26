---
title: Přizpůsobení položky záhlaví&#39;s vzhled | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e09f8bc0b61e22435ee348968f117940b57132e3
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930872"
---
# <a name="customizing-the-header-item39s-appearance"></a>Přizpůsobení položky záhlaví&#39;s vzhledu
Nastavením *dwStyle* parametr při prvním vytvoření ovládacího prvku záhlaví ([CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create)), můžete definovat vzhled a chování záhlaví položky nebo hlavičky ovládací prvek.  
  
 Tady je vzorkování styly, které můžete nastavit a jejich účel:  
  
-   Chcete-li položku záhlaví vypadat pushbutton, použijte **HDS_BUTTONS** stylu.  
  
     Tento styl použijte, pokud chcete provádět akce v reakci na kliknutí myší na položky záhlaví, jako je například řazení dat podle konkrétního sloupce, jak se provádí v aplikaci Microsoft Outlook.  
  
-   Položky hlavičky "aktivní sledování" vzhled při předá myší nad nimi, použijte **HDS_HOTTRACK** stylu.  
  
     Aktivní sledování zobrazí 3D outline jako ukazatel prochází přes položku v opačném případě ploché panelu.  
  
-   K označení, že by být skrytý ovládacím prvku záhlaví, použijte **HDS_HIDDEN** stylu.  
  
     **HDS_HIDDEN** styl označuje, že ovládacím prvku záhlaví je určena pro použití jako kontejner dat a není ovládacího prvku visual. Tento styl není automaticky skrýt ovládacího prvku, ale místo toho má vliv na chování `CHeaderCtrl::Layout`. Hodnota vrácená v *cy* členem `WINDOWPOS` struktura bude nula indikující, že ovládacího prvku by neměly být viditelné pro uživatele.  
  
 Další informace o těchto vlastnostech najdete v tématu [položky](http://msdn.microsoft.com/library/windows/desktop/bb775238) ve Windows SDK. Informace o přidávání položek do ovládacího prvku záhlaví najdete v tématu [přidávání položek do ovládacího prvku záhlaví](../mfc/adding-items-to-the-header-control.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

