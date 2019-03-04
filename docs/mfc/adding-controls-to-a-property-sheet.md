---
title: Přidání ovládacích prvků do seznamu vlastností
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
ms.openlocfilehash: 07b384b2db36ae59d4de8b99d9c07396ce793979
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296303"
---
# <a name="adding-controls-to-a-property-sheet"></a>Přidání ovládacích prvků do seznamu vlastností

Ve výchozím nastavení seznam vlastností přiděluje oblasti okna stránky vlastností, pořadové číslo prvku a tlačítka OK, zrušit a použít. (Nemodálního seznamu vlastností se nemusí OK, zrušit a použijte tlačítka). Další ovládací prvky můžete přidat do seznamu vlastností. Můžete například přidat okno náhledu napravo od oblasti stránky vlastností se uživateli zobrazí, co aktuální nastavení může vypadat třeba pokud použité pro externí objekt.

Můžete přidat ovládací prvky do dialogového okna vlastnosti listu v `OnCreate` obslužné rutiny. Narážely další ovládací prvky, obvykle vyžaduje rozšíření dialogové okno seznam vlastností. Po volání metody základní třídy **CPropertySheet::OnCreate**, volání [getwindowrect –](../mfc/reference/cwnd-class.md#getwindowrect) šířku a výšku okna List vlastností. aktuálně přidělené získáte rozbalte obdélníku dimenze a volání [MoveWindow](../mfc/reference/cwnd-class.md#movewindow) ke změně velikosti okna List vlastností.

## <a name="see-also"></a>Viz také:

[Seznamy vlastností](../mfc/property-sheets-mfc.md)<br/>
[CPropertyPage – třída](../mfc/reference/cpropertypage-class.md)<br/>
[CPropertySheet – třída](../mfc/reference/cpropertysheet-class.md)
