---
title: Klávesové zkratky specifické pro vlákno | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdd6cf2f2bb76c30f4cc00d75eb55d7d2c01fa7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="thread-specific-hot-keys"></a>Klávesové zkratky specifické pro vlákno
Aplikace nastaví klávesové zkratky specifické pro vlákno ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) pomocí Windows **RegisterHotKey** funkce. Když uživatel stiskne klávesové zkratky specifické pro vlákno, odešle Windows [WM_HOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646279) zpráva na začátek fronty zpráv konkrétní vlákno. **WM_HOTKEY** zpráva obsahuje virtuální klíče kódu, stav shift a uživatelské ID konkrétní klávesové zkratky, která byla stisknuta. Seznam kódů standardní virtuální klíčů najdete v tématu winuser. Další informace o této metodě naleznete v tématu [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
 Všimněte si, že příznaky stavu shift použitá ve volání do **RegisterHotKey** nejsou stejná jako ta, vrácený [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) – členská funkce; budete muset před voláním převedetytopříznaky**RegisterHotKey**.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

