---
title: Zajištění aktivace bez blikání
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
ms.openlocfilehash: fad24d6201260e87ff32436752a9fbf035e822ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297044"
---
# <a name="providing-flicker-free-activation"></a>Zajištění aktivace bez blikání

Pokud váš ovládací prvek vykresluje stejně jako v aktivní a neaktivní stavy (a nepoužívá aktivace bez oken), můžete eliminovat výkresu operace a související vizuální blikání, ke kterému obvykle dojít při přechodu mezi neaktivní a aktivní stavy. Chcete-li to provést, patří **noFlickerActivate** příznak v sadě příznaky vrácený [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Příklad:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]

Kód, který patří tento příznak není automaticky vygenerován, pokud jste vybrali **aktivace bez blikání** možnost [nastavení](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránce při vytváření ovládacího prvku pomocí průvodce ovládací prvek ActiveX knihovny MFC.

Pokud používáte aktivace bez oken, tyto optimalizace nemá žádný vliv.

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md)
