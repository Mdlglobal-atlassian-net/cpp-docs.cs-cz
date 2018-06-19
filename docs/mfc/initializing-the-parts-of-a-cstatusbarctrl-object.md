---
title: Inicializace částí objektu CStatusBarCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89cea1516924530f821003affd96e2848687882b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344334"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Inicializace částí objektu CStatusBarCtrl
Ve výchozím nastavení stavového řádku zobrazí informace o stavu pomocí samostatných podokna. Tyto podokna (také označované jako částí) může obsahovat textový řetězec, ikonu nebo obojí.  
  
 Použití [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) určit, kolik částí a délka, bude mít na stavovém řádku. Po vytvoření části stavového řádku provádět volání do [SetText –](../mfc/reference/cstatusbarctrl-class.md#settext) a [SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon) nastavit text nebo ikonu pro konkrétní součást na stavovém řádku. Jakmile části byla úspěšně nastavena, bude automaticky překreslen ovládacího prvku.  
  
 Tento příklad inicializuje existující `CStatusBarCtrl` objektu (`m_StatusBarCtrl`) s čtyři podokna a poté nastaví ikonu (IDI_ICON1) a text v druhé části.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]  
  
 Další informace o nastavení režimu `CStatusBarCtrl` objekt, který má jednoduchý, viz [nastavení režimu objektu CStatusBarCtrl](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití třídy CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

