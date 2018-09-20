---
title: Zajištění aktivace bez blikání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd9f780472b8256f6d8332ecbde08138d85c8ebd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378319"
---
# <a name="providing-flicker-free-activation"></a>Zajištění aktivace bez blikání

Pokud váš ovládací prvek vykresluje stejně jako v aktivní a neaktivní stavy (a nepoužívá aktivace bez oken), můžete eliminovat výkresu operace a související vizuální blikání, ke kterému obvykle dojít při přechodu mezi neaktivní a aktivní stavy. Chcete-li to provést, patří **noFlickerActivate** příznak v sadě příznaky vrácený [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Příklad:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]

Kód, který patří tento příznak není automaticky vygenerován, pokud jste vybrali **aktivace bez blikání** možnost [nastavení](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránce při vytváření ovládacího prvku pomocí průvodce ovládací prvek ActiveX knihovny MFC.

Pokud používáte aktivace bez oken, tyto optimalizace nemá žádný vliv.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md)

