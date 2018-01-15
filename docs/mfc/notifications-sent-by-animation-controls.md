---
title: "Oznámení zaslaná z ovládacích prvků animace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c57a33bf4b13397d4f296ef4e5aa8e137c2d3594
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="notifications-sent-by-animation-controls"></a>Oznámení zaslaná z ovládacích prvků animace
Ovládacího prvku animace ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) odešle dva různé typy zpráv s oznámením. Oznámení se odesílají v podobě [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zprávy.  
  
 [ACN_START](http://msdn.microsoft.com/library/windows/desktop/bb761891) ovládacího prvku animace bylo zahájeno přehrávání klip je odeslání zprávy. [ACN_STOP](http://msdn.microsoft.com/library/windows/desktop/bb761893) je odeslána zpráva při dokončení nebo zastavit přehrávání zastavíte ovládacího prvku animace.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

