---
title: Přidání ovládacích prvků do seznamu vlastností | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0783571ed77d3d8dfaca69edf06330e62d8e98d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398494"
---
# <a name="adding-controls-to-a-property-sheet"></a>Přidání ovládacích prvků do seznamu vlastností

Ve výchozím nastavení seznam vlastností přiděluje oblasti okna stránky vlastností, pořadové číslo prvku a tlačítka OK, zrušit a použít. (Nemodálního seznamu vlastností se nemusí OK, zrušit a použijte tlačítka). Další ovládací prvky můžete přidat do seznamu vlastností. Můžete například přidat okno náhledu napravo od oblasti stránky vlastností se uživateli zobrazí, co aktuální nastavení může vypadat třeba pokud použité pro externí objekt.

Můžete přidat ovládací prvky do dialogového okna vlastnosti listu v `OnCreate` obslužné rutiny. Narážely další ovládací prvky, obvykle vyžaduje rozšíření dialogové okno seznam vlastností. Po volání metody základní třídy **CPropertySheet::OnCreate**, volání [getwindowrect –](../mfc/reference/cwnd-class.md#getwindowrect) šířku a výšku okna List vlastností. aktuálně přidělené získáte rozbalte obdélníku dimenze a volání [MoveWindow](../mfc/reference/cwnd-class.md#movewindow) ke změně velikosti okna List vlastností.

## <a name="see-also"></a>Viz také

[Seznamy vlastností](../mfc/property-sheets-mfc.md)<br/>
[CPropertyPage – třída](../mfc/reference/cpropertypage-class.md)<br/>
[CPropertySheet – třída](../mfc/reference/cpropertysheet-class.md)
