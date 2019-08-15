---
title: Oznámení zaslaná z ovládacích prvků animace
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 68ede3bc55669a29eef192d38b29b8c1ab433e4b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508016"
---
# <a name="notifications-sent-by-animation-controls"></a>Oznámení zaslaná z ovládacích prvků animace

Ovládací prvek animace ([atributu CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) odesílá dva různé typy oznamovacích zpráv. Oznámení se odesílají ve formě zpráv [WM_COMMAND](/windows/win32/menurc/wm-command) .

Zpráva [ACN_START](/windows/win32/Controls/acn-start) se pošle, když ovládací prvek animace začal přehrávat klip. Zpráva [ACN_STOP](/windows/win32/Controls/acn-stop) se pošle, když se ovládací prvek animace dokončí nebo zastaví přehrávání klipu.

## <a name="see-also"></a>Viz také:

[Používání atributu CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
