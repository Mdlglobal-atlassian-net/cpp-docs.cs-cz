---
title: Použití seznamů obrázků v ovládacím prvku panel nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3604de0b3b24b638e549c6823ea6c95036543c1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401768"
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

