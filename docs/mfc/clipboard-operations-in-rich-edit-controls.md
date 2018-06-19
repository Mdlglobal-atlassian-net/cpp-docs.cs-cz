---
title: Operace se schránkou v bohatých ovládacích prvcích pro úpravy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e831a76a491d1025ae45117d40362a85523742da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341281"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Operace se schránkou v ovládacích prvcích pro úpravy s formátováním
Aplikace můžete vložit obsah schránky do ovládacího prvku RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) pomocí konkrétní formátu schránky nebo nejlépe dostupné volné paměti. Můžete také určit, jestli je schopná vkládání formát schránky ovládacího prvku RichEdit.  
  
 Můžete kopírovat nebo vyjmout obsah aktuální výběr pomocí [kopie](../mfc/reference/cricheditctrl-class.md#copy) nebo [Vyjmout](../mfc/reference/cricheditctrl-class.md#cut) – členská funkce. Podobně můžete vložit obsah schránky do ovládacího prvku RichEdit pomocí [vložit](../mfc/reference/cricheditctrl-class.md#paste) – členská funkce. Ovládací prvek vloží první dostupné formátu, který ho rozpozná, což je pravděpodobně nejvíce popisný formátu.  
  
 Chcete-li vložit konkrétní formát schránky, můžete použít [PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial) – členská funkce. Tato funkce je užitečná pro aplikace s vložením speciální příkaz, který umožňuje uživateli vybrat formát schránky. Můžete použít [CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste) – členská funkce k určení, zda je daný formát rozpoznáno ovládacího prvku.  
  
 Můžete také použít `CanPaste` k určení, zda ovládacího prvku RichEdit rozpozná všechny dostupné formát schránky. Tato funkce je užitečná v `OnInitMenuPopup` obslužné rutiny. Aplikace může povolit nebo šedý jeho příkaz Paste v závislosti na tom, jestli ovládacího prvku můžete vložit všechny dostupné formátu.  
  
 RichEdit ovládací prvky registrace dva schránky formáty: text ve formátu a do formátu textu RichEdit a objektů. Aplikace můžete registrovat pomocí těchto formátů [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) fungovat, určení **CF_RTF** a **CF_RETEXTOBJ** hodnoty.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

