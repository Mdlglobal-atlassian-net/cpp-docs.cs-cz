---
title: Změna stylů ovládacího prvku seznam
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: 2ba9ae81f7b1693be0df3565256a65e4e3561fd3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266871"
---
# <a name="changing-list-control-styles"></a>Změna stylů ovládacího prvku seznam

Můžete změnit styl okna ovládacího prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)) kdykoli po jeho vytvoření. Změnou stylu okna změníte typ zobrazení, které používá ovládací prvek. Například pro emulaci Explorer, je může zadat položky nabídky nebo tlačítka panelu nástrojů pro přepínání mezi různá zobrazení ovládacího prvku: zobrazení ikon, zobrazení seznamu a tak dále.

Například když uživatel vybere položku nabídky, které může uskutečnit volání [GetWindowLong](/windows/desktop/api/winuser/nf-winuser-getwindowlonga) načíst aktuální styl ovládacího prvku a poté zavolejte [SetWindowLong](/windows/desktop/api/winuser/nf-winuser-setwindowlonga) resetovat styl. Další informace najdete v tématu [ovládací prvky zobrazení pomocí seznamu](/windows/desktop/Controls/using-list-view-controls) v sadě Windows SDK.

K dispozici styly jsou uvedeny v [vytvořit](../mfc/reference/clistctrl-class.md#create). Styly **jen**, **LVS_SMALLICON**, **LVS_LIST**, a **LVS_REPORT** určit čtyři seznamy ovládacího prvku.

## <a name="extended-styles"></a>Rozšířené styly

Kromě standardních stylů pro ovládací prvek seznamu je další sady, jen rozšířené styly. Tyto styly podrobněji [rozšířené styly zobrazení seznamu](/windows/desktop/Controls/extended-list-view-styles) v sadě Windows SDK poskytují celou řadu užitečných funkcí, které přizpůsobit chování ovládacího prvku seznamu. K implementaci chování stylu (například výběr při přechodu myší), ujistěte se, volání [CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), předání potřebných style. Následující příklad ukazuje volání funkce:

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
>  Pro výběr při najetí myší na práci, musíte také mít **LVS_EX_ONECLICKACTIVATE** nebo **LVS_EX_TWOCLICKACTIVATE** zapnuté.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
