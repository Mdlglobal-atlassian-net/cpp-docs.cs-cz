---
title: Zpracování oznámení ovládacího prvku záhlaví | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a0fe657089c33679cf8d18f95268a70335804c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348888"
---
# <a name="processing-header-control-notifications"></a>Zpracování oznámení ovládacího prvku záhlaví
Ve třídě zobrazení nebo dialogové okno Vlastnosti okno použít k vytvoření [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkce obslužná rutina s příkazem přepínač pro všechny prvku záhlaví ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) zpráv s oznámením chcete zpracování (viz [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md)). Oznámení se odesílají do nadřazeného okna, když uživatel klikne na tlačítko nebo poklikáním položky záhlaví, drags a dělicí mezi položkami a tak dále.  
  
 Související s ovládacím prvkem záhlaví zprávy oznámení jsou uvedeny v [odkaz ovládacího prvku záhlaví](http://msdn.microsoft.com/library/windows/desktop/bb775239) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

