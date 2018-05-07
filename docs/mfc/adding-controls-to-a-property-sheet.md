---
title: Přidání ovládacích prvků do seznamu vlastností | Microsoft Docs
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
ms.openlocfilehash: 8437fcdaa04ce7dd2b0a214e4bd3a63ca421d014
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="adding-controls-to-a-property-sheet"></a>Přidání ovládacích prvků do seznamu vlastností
Ve výchozím nastavení seznam vlastností přiděluje oblast okna pro stránky vlastností, pořadové číslo a tlačítka OK, zrušit a použít. (Nemodálního seznamu vlastností nemá OK, zrušte a použít tlačítka.) Další ovládací prvky můžete přidat do seznamu vlastností. Například lze přidat okno náhledu napravo od oblasti vlastnost stránky se uživateli zobrazí, co bude aktuální nastavení vypadat Pokud použijí pro externího objektu.  
  
 Ovládací prvky můžete přidat do dialogového okna List vlastností v `OnCreate` obslužné rutiny. Další kontroly požadavků obvykle vyžaduje rozšíření velikost dialogového okna List vlastností. Po volání metody základní třídy **CPropertySheet::OnCreate**, volání [getwindowrect –](../mfc/reference/cwnd-class.md#getwindowrect) získat šířka a výška v okně List aktuálně přidělené vlastnosti, rozbalte obdélníku dimenzí a volání [MoveWindow](../mfc/reference/cwnd-class.md#movewindow) a změňte velikost okna List vlastností.  
  
## <a name="see-also"></a>Viz také  
 [Seznam vlastností](../mfc/property-sheets-mfc.md)   
 [CPropertyPage – třída](../mfc/reference/cpropertypage-class.md)   
 [CPropertySheet – třída](../mfc/reference/cpropertysheet-class.md)
