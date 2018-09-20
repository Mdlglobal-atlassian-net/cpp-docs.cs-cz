---
title: Zajištění podpory přetažení myší u položek záhlaví | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2eaa5040d34a442868a8fa6cb9f2aae08b0a6f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407696"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Zajištění podpory přetažení u položek záhlaví

K poskytování podpory a přetažení u položek záhlaví, zadejte hds_dragdrop – styl. Podpora a přetažení u položek záhlaví umožňuje uživateli změnit pořadí položek záhlaví ovládacího prvku záhlaví. Výchozí chování poskytuje poloprůhledných přetáhnout obrázek položky záhlaví jsou kvůli usnadnění použití vypsány a vizuální indikátor na nové pozici, pokud hlavička položka byla vynechána.

Jako s běžnými funkcemi přetažení myší, můžete rozšířit výchozí chování a přetahování zpracováním HDN_BEGINDRAG a HDN_ENDDRAG oznámení. Můžete také upravit vzhled obrázku přetáhněte tak, že přepíšete [CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) členskou funkci.

> [!NOTE]
>  Pokud poskytujete podporu drag drop pro ovládací prvek vložený záhlaví v ovládacím prvku seznamu, naleznete v části Extended Style [změna stylů ovládacího prvku seznam](../mfc/changing-list-control-styles.md) tématu.

## <a name="see-also"></a>Viz také

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)

