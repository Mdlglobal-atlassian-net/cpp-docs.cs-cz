---
title: Zajištění podpory přetažení u položek záhlaví
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: 21ff14982baac93fac1cf3ee441353c079f4f760
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602966"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Zajištění podpory přetažení u položek záhlaví

K poskytování podpory a přetažení u položek záhlaví, zadejte hds_dragdrop – styl. Podpora a přetažení u položek záhlaví umožňuje uživateli změnit pořadí položek záhlaví ovládacího prvku záhlaví. Výchozí chování poskytuje poloprůhledných přetáhnout obrázek položky záhlaví jsou kvůli usnadnění použití vypsány a vizuální indikátor na nové pozici, pokud hlavička položka byla vynechána.

Jako s běžnými funkcemi přetažení myší, můžete rozšířit výchozí chování a přetahování zpracováním HDN_BEGINDRAG a HDN_ENDDRAG oznámení. Můžete také upravit vzhled obrázku přetáhněte tak, že přepíšete [CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) členskou funkci.

> [!NOTE]
>  Pokud poskytujete podporu drag drop pro ovládací prvek vložený záhlaví v ovládacím prvku seznamu, naleznete v části Extended Style [změna stylů ovládacího prvku seznam](../mfc/changing-list-control-styles.md) tématu.

## <a name="see-also"></a>Viz také

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)

