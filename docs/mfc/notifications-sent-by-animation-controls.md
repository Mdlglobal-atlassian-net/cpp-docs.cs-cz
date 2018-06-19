---
title: Oznámení zaslaná z ovládacích prvků animace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1696389ce3dc40c5d02ec660ebaeb6bf3e6c3ec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345237"
---
# <a name="notifications-sent-by-animation-controls"></a>Oznámení zaslaná z ovládacích prvků animace
Ovládacího prvku animace ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) odešle dva různé typy zpráv s oznámením. Oznámení se odesílají v podobě [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zprávy.  
  
 [ACN_START](http://msdn.microsoft.com/library/windows/desktop/bb761891) ovládacího prvku animace bylo zahájeno přehrávání klip je odeslání zprávy. [ACN_STOP](http://msdn.microsoft.com/library/windows/desktop/bb761893) je odeslána zpráva při dokončení nebo zastavit přehrávání zastavíte ovládacího prvku animace.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

