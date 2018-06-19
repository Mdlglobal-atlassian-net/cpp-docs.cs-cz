---
title: Třídy související s ovládacími prvky pro úpravy s formátováním | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rich edit controls [MFC], and CRichEditItem
- CRichEditCtrl class [MFC], related classes
- CRichEditDoc class [MFC], Rich Edit controls
- rich edit controls [MFC], classes related to
- classes [MFC], related to rich edit controls
- rich edit controls [MFC], and CRichEditView
- CRichEditCtrlItem class and CRichEditCtrl
- rich edit controls [MFC], and CRichEditDoc
- CRichEditView class [MFC], and CRichEditCtrl
ms.assetid: 4b31c2cc-6ea1-4146-b7c5-b0b5b419f14d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f428242ac84adaf36ea0263f8e193dfeca7d0609
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341395"
---
# <a name="classes-related-to-rich-edit-controls"></a>Třídy související s ovládacími prvky pro úpravy s formátováním
[Cricheditview –](../mfc/reference/cricheditview-class.md), [CRichEditDoc](../mfc/reference/cricheditdoc-class.md), a [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md) třídy poskytují funkce ovládacího prvku RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) v kontextu na MFC document/view – architektura. `CRichEditView` udržuje textu a formátování vlastnosti textu. `CRichEditDoc` udržuje seznam položek OLE klienta, které jsou v zobrazení. `CRichEditCntrItem` poskytuje kontejner straně přístup k položce OLE klienta. Chcete-li upravit obsah `CRichEditView`, použijte [CRichEditView::GetRichEditCtrl](../mfc/reference/cricheditview-class.md#getricheditctrl) pro přístup k základní bohaté ovládacích prvků pro úpravy.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

