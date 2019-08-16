---
title: Změna stylů ovládacího prvku seznam
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: b3cc65ce6ef0e84eaa2f6738cb18b6b862a6473a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509048"
---
# <a name="changing-list-control-styles"></a>Změna stylů ovládacího prvku seznam

Styl okna ovládacího prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)) můžete kdykoli po jeho vytvoření změnit. Změnou stylu okna změníte typ zobrazení, které ovládací prvek používá. Například pro emulaci Průzkumníka můžete dodat položky nabídky nebo tlačítka panelu nástrojů pro přepínání ovládacího prvku mezi různými zobrazeními: zobrazení ikon, zobrazení seznamu a tak dále.

Například když uživatel vybere položku nabídky, můžete provést volání [GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) pro načtení aktuálního stylu ovládacího prvku a pak zavolat [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) pro resetování stylu. Další informace najdete v tématu [použití ovládacích prvků zobrazení seznamu](/windows/win32/Controls/using-list-view-controls) v Windows SDK.

K dispozici jsou styly v seznamu [vytvořit](../mfc/reference/clistctrl-class.md#create). Styly **jen**, **LVS_SMALLICON**, **LVS_LIST**a **LVS_REPORT** určují čtyři zobrazení ovládacího prvku seznam.

## <a name="extended-styles"></a>Rozšířené styly

Kromě standardních stylů pro ovládací prvek seznamu je k dispozici další sada označovaná jako rozšířené styly. Tyto styly, které jsou popsány v [rozšířených stylech zobrazení seznamu](/windows/win32/Controls/extended-list-view-styles) v Windows SDK, poskytují celou řadu užitečných funkcí, které přizpůsobují chování ovládacího prvku seznam. Chcete-li implementovat chování určitého stylu (například výběr myši), zavolejte na [CListCtrl:: SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle)a předejte potřebný styl. Následující příklad ukazuje volání funkce:

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
>  Aby výběr najeďte na práci, musíte mít také zapnutou možnost **LVS_EX_ONECLICKACTIVATE** nebo **LVS_EX_TWOCLICKACTIVATE** .

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
