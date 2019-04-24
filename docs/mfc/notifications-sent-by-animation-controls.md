---
title: Oznámení zaslaná z ovládacích prvků animace
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 2a736e4315091b1b26daceb4fe0ce9672ab33ff6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62238306"
---
# <a name="notifications-sent-by-animation-controls"></a>Oznámení zaslaná z ovládacích prvků animace

Ovládacího prvku animace ([atributu CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) odešle dva různé typy zpráv s oznámením. Oznámení se odesílají v podobě [wm_command –](/windows/desktop/menurc/wm-command) zprávy.

[ACN_START](/windows/desktop/Controls/acn-start) zpráva se odešle, když ovládací prvek animace začala přehrávat klip. [ACN_STOP](/windows/desktop/Controls/acn-stop) zpráva se odešle, když ovládací prvek animace přestal přehrávání klipu nebo bylo dokončeno.

## <a name="see-also"></a>Viz také:

[Používání atributu CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
