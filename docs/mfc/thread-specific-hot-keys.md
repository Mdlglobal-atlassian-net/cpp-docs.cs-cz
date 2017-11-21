---
title: "Klávesové zkratky specifické pro vlákno | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 75c3b5356277e227832ecc94a9f6b70cc15f3a71
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="thread-specific-hot-keys"></a>Klávesové zkratky specifické pro vlákno
Aplikace nastaví klávesové zkratky specifické pro vlákno ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) pomocí Windows **RegisterHotKey** funkce. Když uživatel stiskne klávesové zkratky specifické pro vlákno, odešle Windows [WM_HOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646279) zpráva na začátek fronty zpráv konkrétní vlákno. **WM_HOTKEY** zpráva obsahuje virtuální klíče kódu, stav shift a uživatelské ID konkrétní klávesové zkratky, která byla stisknuta. Seznam kódů standardní virtuální klíčů najdete v tématu winuser. Další informace o této metodě naleznete v tématu [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
 Všimněte si, že příznaky stavu shift použitá ve volání do **RegisterHotKey** nejsou stejná jako ta, vrácený [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) – členská funkce; budete muset před voláním převedetytopříznaky**RegisterHotKey**.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

