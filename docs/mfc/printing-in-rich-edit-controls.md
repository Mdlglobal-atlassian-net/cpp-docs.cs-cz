---
title: "Tisk v ovládacích prvcích pro úpravy s formátováním | Microsoft Docs"
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
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab8e15e25e2d419bb7c3ac67fc2c6f3453fb03c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="printing-in-rich-edit-controls"></a>Tisk v ovládacích prvcích pro úpravy s formátováním
Se dá zjistit ovládacích prvků pro úpravy s formátováním ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) k vykreslení jeho výstupu pro zadané zařízení, třeba tiskárny. Můžete také zadat, že výstupní zařízení, pro který s formátováním ovládacích prvků pro úpravy formáty jeho textu.  
  
 K formátování části obsahu ovládacího prvku RichEdit pro konkrétní zařízení, můžete použít [FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange) – členská funkce. [FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911) struktura používaná pomocí této funkce určuje rozsah textu k formátování a také kontextu zařízení (DC) pro cílové zařízení.  
  
 Po formátování textu pro výstupní zařízení, můžete odesílat výstup do zařízení pomocí [DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband) – členská funkce. Opakovaně pomocí `FormatRange` a `DisplayBand`, aplikace, která vytiskne obsah ovládacího prvku RichEdit můžete implementovat, řazení do pásem. (Řazení do pásem je výstup rozdělení na menší části pro účely tisku.)  
  
 Můžete použít [SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice) – členská funkce k určení cílového zařízení, pro který s formátováním ovládacích prvků pro úpravy formáty jeho textu. Tato funkce je užitečná pro WYSIWYG (zobrazené je můžete získat) formátování, ve kterém aplikace umisťuje textu s použitím metriky písma tiskárny výchozí místo na obrazovce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

