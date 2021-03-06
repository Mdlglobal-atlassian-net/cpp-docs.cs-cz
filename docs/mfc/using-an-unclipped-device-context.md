---
title: Použití neoříznutého kontextu zařízení
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
ms.openlocfilehash: 0f129c0bfa5bd76df4ba34b117e7ed8aa08c2ecb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411809"
---
# <a name="using-an-unclipped-device-context"></a>Použití neoříznutého kontextu zařízení

Pokud jste si naprosto jisti, že ovládací prvek není vykreslovat mimo jeho klientský obdélník, byste mohli realizovat zvýšení rychlosti malou, avšak zjistitelná zakázáním volání `IntersectClipRect` , který provádí `COleControl`. Chcete-li to provést, odeberte *clipPaintDC* příznak ze sady příznaků vrácený [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Příklad:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]

Pokud zvolíte možnost automaticky vytvořit kód můžete odebrat tento příznak **Neoříznutého kontextu zařízení** možnost [nastavení řízení](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránek, při vytváření ovládacího prvku pomocí průvodce ovládací prvek ActiveX knihovny MFC.

Pokud používáte aktivace bez oken, tyto optimalizace nemá žádný vliv.

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md)
