---
title: Objednávání položek v ovládacím prvku záhlaví
ms.date: 11/04/2016
f1_keywords:
- DS_DRAGDROP
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
ms.openlocfilehash: bae351d921c25993d6b7029f9052e1938179673b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282017"
---
# <a name="ordering-items-in-the-header-control"></a>Objednávání položek v ovládacím prvku záhlaví

Jakmile [přidání položek do ovládacího prvku záhlaví](../mfc/adding-items-to-the-header-control.md), můžete pracovat s nebo získat informace o jejich pořadí se následující funkce:

- [CHeaderCtrl::GetOrderArray](../mfc/reference/cheaderctrl-class.md#getorderarray) a [CHeaderCtrl::SetOrderArray](../mfc/reference/cheaderctrl-class.md#setorderarray)

   Získá a nastaví pořadí zleva doprava z položek záhlaví.

- [CHeaderCtrl::OrderToIndex](../mfc/reference/cheaderctrl-class.md#ordertoindex).

   Načte hodnotu indexu pro konkrétní hlavičky položku.

Kromě předchozích členské funkce hds_dragdrop – styl umožňuje uživateli přetažení položek záhlaví v ovládacím prvku záhlaví. Další informace najdete v tématu [poskytování podpory a přetažení u položek záhlaví](../mfc/providing-drag-and-drop-support-for-header-items.md).

## <a name="see-also"></a>Viz také:

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)
