---
title: Zajištění podpory přetažení u položek záhlaví
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: 8dfaabf3da62c216d3da662f59c57b63e695d9ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371167"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Zajištění podpory přetažení u položek záhlaví

Chcete-li poskytnout podporu přetažením položek záhlaví, zadejte styl HDS_DRAGDROP. Podpora přetažením položek záhlaví umožňuje uživateli určit pořadí položek záhlaví ovládacího prvku záhlaví. Výchozí chování poskytuje poloprůhledný obrázek přetažení položky záhlaví a vizuální indikátor nové pozice, pokud je položka záhlaví vynechána.

Stejně jako u běžných funkcí přetažení můžete rozšířit výchozí chování přetažení zpracováním HDN_BEGINDRAG a HDN_ENDDRAG oznámení. Vzhled přetahovaná obrazu můžete také přizpůsobit přepsáním členské funkce [CHeaderCtrl::CreateDragImage.](../mfc/reference/cheaderctrl-class.md#createdragimage)

> [!NOTE]
> Pokud poskytujete podporu přetažením pro vložený ovládací prvek záhlaví v ovládacím prvku seznamu, přečtěte si část Rozšířený styl v tématu [Změna stylů ovládacího prvku seznamu.](../mfc/changing-list-control-styles.md)

## <a name="see-also"></a>Viz také

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)
