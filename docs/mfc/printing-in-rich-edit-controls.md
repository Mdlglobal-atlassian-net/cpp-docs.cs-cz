---
title: Tisk v ovládacích prvcích pro úpravy s formátováním | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 882ed020b37ec60c072c8983c61bbe564bb74b04
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217685"
---
# <a name="printing-in-rich-edit-controls"></a>Tisk v ovládacích prvcích pro úpravy s formátováním
Poznáte, ovládacích prvků pro úpravy s formátováním ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) k vykreslení jeho výstupu pro zadané zařízení, třeba tiskárny. Můžete také zadat, že výstupní zařízení, pro kterou bohaté ovládacích prvků pro úpravy formátuje text.  
  
 Pokud chcete naformátovat část obsahu ovládacího prvku pro konkrétní zařízení, můžete použít [FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange) členskou funkci. [FORMATRANGE](/windows/desktop/api/richedit/ns-richedit-_formatrange) struktury použité s touto funkcí určuje rozsah textu pro formátování a kontext zařízení (DC) pro cílové zařízení.  
  
 Po naformátování textu pro výstup zařízení, můžete výstup odeslat do zařízení s použitím [DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband) členskou funkci. Opakovaně pomocí `FormatRange` a `DisplayBand`, aplikace, která vytiskne obsah ovládacího prvku můžete implementovat řazení do pásem. (Řazení do pásem je rozdělení výstupu do menších částí pro účely tisku.)  
  
 Můžete použít [SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice) členskou funkci k určení cílového zařízení, pro kterou bohaté ovládacích prvků pro úpravy formátuje text. Tato funkce je užitečná pro WYSIWYG (zobrazené získáte) formátování, ve které aplikace umístí textu s použitím výchozí tiskárna metriky písma místo na obrazovce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

