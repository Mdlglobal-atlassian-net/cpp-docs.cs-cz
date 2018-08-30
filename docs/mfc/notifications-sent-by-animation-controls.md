---
title: Oznámení zaslaná z ovládacích prvků animace | Dokumentace Microsoftu
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
ms.openlocfilehash: d7aff43577a4b1aa55fc0725ba4753228e334000
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199658"
---
# <a name="notifications-sent-by-animation-controls"></a>Oznámení zaslaná z ovládacích prvků animace
Ovládacího prvku animace ([atributu CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) odešle dva různé typy zpráv s oznámením. Oznámení se odesílají v podobě [wm_command –](/windows/desktop/menurc/wm-command) zprávy.  
  
 [ACN_START](/windows/desktop/Controls/acn-start) zpráva se odešle, když ovládací prvek animace začala přehrávat klip. [ACN_STOP](/windows/desktop/Controls/acn-stop) zpráva se odešle, když ovládací prvek animace přestal přehrávání klipu nebo bylo dokončeno.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

