---
title: Třídy související s ovládacími prvky pro úpravy s formátováním | Dokumentace Microsoftu
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
ms.openlocfilehash: 9ee7b6400dcd5c91d054b31153c21008d5302bd0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401261"
---
# <a name="classes-related-to-rich-edit-controls"></a>Třídy související s ovládacími prvky pro úpravy s formátováním

[Cricheditview –](../mfc/reference/cricheditview-class.md), [cricheditdoc –](../mfc/reference/cricheditdoc-class.md), a [cricheditcntritem –](../mfc/reference/cricheditcntritem-class.md) třídy poskytují funkce pro ovládací prvek RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) v rámci kontextu architektury dokumentu/zobrazení MFC. `CRichEditView` udržuje textu a formátování vlastnosti textu. `CRichEditDoc` udržuje seznam klientské položky OLE, které jsou v zobrazení. `CRichEditCntrItem` poskytuje kontejner straně přístup k klientskou položku OLE. Chcete-li změnit obsah `CRichEditView`, použijte [CRichEditView::GetRichEditCtrl](../mfc/reference/cricheditview-class.md#getricheditctrl) pro přístup k podkladovým pro úpravy s formátováním ovládacího prvku.

## <a name="see-also"></a>Viz také

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

