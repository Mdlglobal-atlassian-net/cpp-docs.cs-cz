---
title: Použití seznamů obrázků v ovládacím prvku panel nástrojů
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
ms.openlocfilehash: f8b19cd54a6fb2dca940c354ef23e7d06b35f0b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584571"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>Použití seznamů obrázků v ovládacím prvku panel nástrojů

Ve výchozím nastavení jsou uloženy obrázky používané v tlačítek v ovládacím prvku panel nástrojů jako jediné bitmapě. Ale můžete také ukládat obrázky tlačítek seznamů obrázků v sadě. Objekt ovládacího prvku panel nástrojů můžete použít až tři samostatná bitová kopie seznamy:

- Povolené Image obsahuje seznam image pro tlačítka panelu nástrojů, které jsou aktuálně povoleny.

- Zakázat Image obsahuje seznam obrázků pro tlačítka panelu nástrojů, které jsou aktuálně zakázány.

- Zvýrazněný Image obsahuje seznam image pro tlačítka panelu nástrojů, které jsou aktuálně zvýrazněný. Tento seznam obrázků se používá pouze v případě, že používá TBSTYLE_FLAT styl panelu nástrojů.

Když přiřadíte jim používají tyto seznamy obrázků ovládací prvek panelu nástrojů `CToolBarCtrl` objektu. Toto přidružení se provádí tak, že volání [CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist), a [SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist).

Ve výchozím nastavení, knihovna MFC používá `CToolBar` třídu pro implementaci panelů nástrojů aplikace knihovny MFC. Ale `GetToolBarCtrl` členskou funkci je možné načíst vložený `CToolBarCtrl` objektu. Potom může provést volání `CToolBarCtrl` členské funkce pomocí vráceného objektu.

Následující příklad ukazuje tuto techniku přiřazením povolenu (`m_ToolBarImages`) a je zakázaný (`m_ToolBarDisabledImages`) seznamu obrázků `CToolBarCtrl` objektu (`m_ToolBarCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
>  Seznamy obrázků použité objektem nástrojů musí být trvalé objekty. Z tohoto důvodu jsou běžně datové členy třídy knihovny MFC; v tomto příkladu třída okna hlavního rámce.

Jakmile jsou přidružené seznamy obrázků `CToolBarCtrl` objektu, automaticky zobrazí obrázek tlačítka správné rozhraní.

## <a name="see-also"></a>Viz také

[Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

