---
title: Použití seznamů obrázků v ovládacím prvku panel nástrojů
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
ms.openlocfilehash: 81468528c15300a7e9ace6b20fd9fb34818f1928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366500"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>Použití seznamů obrázků v ovládacím prvku panel nástrojů

Ve výchozím nastavení jsou obrazy používané tlačítky v ovládacím prvku panelu nástrojů uloženy jako jedna bitmapa. Obrázky tlačítek však můžete také uložit do sady seznamů obrázků. Objekt ovládacího prvku panelu nástrojů může používat až tři samostatné seznamy obrázků:

- Povolený seznam obrázků Obsahuje obrázky pro tlačítka panelu nástrojů, která jsou aktuálně povolena.

- Seznam zakázaných obrázků Obsahuje obrázky pro tlačítka panelu nástrojů, která jsou aktuálně zakázána.

- Zvýrazněný seznam obrázků Obsahuje obrázky pro aktuálně zvýrazněná tlačítka panelu nástrojů. Tento seznam obrázků se používá pouze v případě, že panel nástrojů používá styl TBSTYLE_FLAT.

Tyto seznamy obrázků jsou používány ovládacím prvkem `CToolBarCtrl` panelu nástrojů, když je přidružíte k objektu. Toto přidružení je provedeno voláním [CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist)a [SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist).

Ve výchozím nastavení knihovna MFC používá třídu `CToolBar` k implementaci panelů nástrojů aplikace knihovny MFC. Členská `GetToolBarCtrl` funkce však lze načíst `CToolBarCtrl` vložený objekt. Potom můžete volat `CToolBarCtrl` do členských funkcí pomocí vrácený objekt.

Následující příklad ukazuje tuto techniku přiřazením`m_ToolBarImages`seznamu povolených ( ) a zakázaných (`m_ToolBarDisabledImages`) obrázků k objektu `CToolBarCtrl` (`m_ToolBarCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
> Seznamy obrázků používané objektem panelu nástrojů musí být trvalé objekty. Z tohoto důvodu jsou běžně datové členy třídy knihovny MFC; v tomto příkladu třídy okna hlavního rámce.

Jakmile jsou seznamy obrázků `CToolBarCtrl` přidruženy k objektu, rozhraní automaticky zobrazí obrázek správného tlačítka.

## <a name="see-also"></a>Viz také

[Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
