---
title: Nastavení klávesové zkratky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3987ddee98ae35e02a181e38cd71f181801aeb61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379642"
---
# <a name="setting-a-hot-key"></a>Nastavení klávesové zkratky
Aplikace můžete použít informace poskytované klávesové zkratky ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) ovládacího prvku v jednom ze dvou způsobů:  
  
-   Nastavit globální klávesové zkratky pro aktivaci okno nonchild odesláním [WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) zpráva do okna chcete aktivovat.  
  
-   Nastavení klávesové zkratky specifické pro vlákno voláním funkce systému Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

