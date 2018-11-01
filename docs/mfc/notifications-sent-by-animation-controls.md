---
title: Oznámení zaslaná z ovládacích prvků animace
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 8c437e6950435b49c280c4f1bb9225002545d6f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449293"
---
# <a name="notifications-sent-by-animation-controls"></a>Oznámení zaslaná z ovládacích prvků animace

Ovládacího prvku animace ([atributu CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) odešle dva různé typy zpráv s oznámením. Oznámení se odesílají v podobě [wm_command –](/windows/desktop/menurc/wm-command) zprávy.

[ACN_START](/windows/desktop/Controls/acn-start) zpráva se odešle, když ovládací prvek animace začala přehrávat klip. [ACN_STOP](/windows/desktop/Controls/acn-stop) zpráva se odešle, když ovládací prvek animace přestal přehrávání klipu nebo bylo dokončeno.

## <a name="see-also"></a>Viz také

[Používání atributu CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

