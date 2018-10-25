---
title: Objednávání položek v ovládacím prvku záhlaví | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DS_DRAGDROP
dev_langs:
- C++
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60139821c1b15673fac0fb8f9ec3925cbfa6dc31
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052094"
---
# <a name="ordering-items-in-the-header-control"></a>Objednávání položek v ovládacím prvku záhlaví

Jakmile [přidání položek do ovládacího prvku záhlaví](../mfc/adding-items-to-the-header-control.md), můžete pracovat s nebo získat informace o jejich pořadí se následující funkce:

- [CHeaderCtrl::GetOrderArray](../mfc/reference/cheaderctrl-class.md#getorderarray) a [CHeaderCtrl::SetOrderArray](../mfc/reference/cheaderctrl-class.md#setorderarray)

   Získá a nastaví pořadí zleva doprava z položek záhlaví.

- [CHeaderCtrl::OrderToIndex](../mfc/reference/cheaderctrl-class.md#ordertoindex).

   Načte hodnotu indexu pro konkrétní hlavičky položku.

Kromě předchozích členské funkce hds_dragdrop – styl umožňuje uživateli přetažení položek záhlaví v ovládacím prvku záhlaví. Další informace najdete v tématu [poskytování podpory a přetažení u položek záhlaví](../mfc/providing-drag-and-drop-support-for-header-items.md).

## <a name="see-also"></a>Viz také

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)

