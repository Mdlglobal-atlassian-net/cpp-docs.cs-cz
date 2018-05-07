---
title: Použití objektu CToolTipCtrl k vytvoření objektu CToolTipCtrl a manipulaci | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CToolTipCtrl
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f2143ea37cfe9448e43aacfa75622beab93d2fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>Použití objektu CToolTipCtrl k vytvoření objektu CToolTipCtrl a manipulaci s ním
Tady je příklad [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) využití:  
  
### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>K vytvoření a manipulaci CToolTipCtrl  
  
1.  Vytvořit `CToolTipCtrl` objektu.  
  
2.  Volání [vytvořit](../mfc/reference/ctooltipctrl-class.md#create) běžné prvkem popis tlačítka Windows a vytvořte jej do `CToolTipCtrl` objektu.  
  
3.  Volání [AddTool](../mfc/reference/ctooltipctrl-class.md#addtool) zaregistrovat nástroj s ovládacím prvkem popis tlačítka, informace uložené v popisu tlačítka se zobrazí, pokud se ukazatel na nástroj.  
  
4.  Volání [SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) informace o popisku tlačítka udržuje pro nástroj.  
  
5.  Volání [SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect) nastavit nové ohraničující obdélník pro nástroj.  
  
6.  Volání [hitTest –](../mfc/reference/ctooltipctrl-class.md#hittest) otestovat bod k určení toho, jestli je v rámci ohraničující obdélník daný nástroj a pokud ano, načíst informace o nástroji.  
  
7.  Volání [GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) načíst počet nástroje registrované s ovládacím prvkem popis tlačítka.  
  
## <a name="see-also"></a>Viz také  
 [Použití objektu CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

