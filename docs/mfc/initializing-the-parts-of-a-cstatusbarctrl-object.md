---
title: "Inicializace částí objektu CStatusBarCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CStatusBarCtrl
dev_langs: C++
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b713a46db13508df5ba80b21e3dfe938261eec65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

