---
title: "Nastavení klávesové zkratky | Microsoft Docs"
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
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9cd52fca8415196fc1393cc49fe7830f6ca2cfd1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="setting-a-hot-key"></a>Nastavení klávesové zkratky
Aplikace můžete použít informace poskytované klávesové zkratky ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) ovládacího prvku v jednom ze dvou způsobů:  
  
-   Nastavit globální klávesové zkratky pro aktivaci okno nonchild odesláním [WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) zpráva do okna chcete aktivovat.  
  
-   Nastavení klávesové zkratky specifické pro vlákno voláním funkce systému Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

