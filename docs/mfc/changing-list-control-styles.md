---
title: Změna stylů ovládacího prvku seznam
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: 5f45e0549c3fc0f5747f8dd12a6310fafd7dd7bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370806"
---
# <a name="changing-list-control-styles"></a>Změna stylů ovládacího prvku seznam

Styl okna ovládacího prvku seznamu ([CListCtrl](../mfc/reference/clistctrl-class.md)) můžete kdykoli po jeho vytvoření změnit. Změnou stylu okna změníte druh zobrazení, které ovládací prvek používá. Chcete-li například emulovat Explorer, můžete zadat položky nabídky nebo tlačítka panelu nástrojů pro přepínání ovládacího prvku mezi různými zobrazeními: zobrazení ikon, zobrazení seznamu a tak dále.

Například když uživatel vybere položku nabídky, můžete provést volání [GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) načíst aktuální styl ovládacího prvku a potom volat [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) obnovit styl. Další informace naleznete [v tématu Použití ovládacích prvků zobrazení seznamu](/windows/win32/Controls/using-list-view-controls) v sadě Windows SDK.

Dostupné styly jsou uvedeny v seznamu [Vytvořit](../mfc/reference/clistctrl-class.md#create). Styly **LVS_ICON**, **LVS_SMALLICON**, **LVS_LIST**a **LVS_REPORT** označují čtyři zobrazení ovládacích prvků seznamu.

## <a name="extended-styles"></a>Rozšířené styly

Kromě standardních stylů pro ovládací prvek seznamu existuje další sada, označovaná jako rozšířené styly. Tyto styly popsané v [rozšířené seznam y zobrazení stylů](/windows/win32/Controls/extended-list-view-styles) v sadě Windows SDK poskytují celou řadu užitečných funkcí, které přizpůsobují chování ovládacího prvku seznamu. Chcete-li implementovat chování určitého stylu (například výběr při přechodu), zavolejte [clistctrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), předání potřebného stylu. Následující příklad ukazuje volání funkce:

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
> Aby výběr na jevu fungoval, musíte mít zapnutou také **LVS_EX_ONECLICKACTIVATE** nebo **LVS_EX_TWOCLICKACTIVATE.**

## <a name="see-also"></a>Viz také

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
