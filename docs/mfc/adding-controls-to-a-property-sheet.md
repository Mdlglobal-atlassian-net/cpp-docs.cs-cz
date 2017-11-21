---
title: "Přidání ovládacích prvků do seznamu vlastností | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5623f95a77710e0ffbfa8a444de6f569f24105e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="adding-controls-to-a-property-sheet"></a>Přidání ovládacích prvků do seznamu vlastností
Ve výchozím nastavení seznam vlastností přiděluje oblast okna pro stránky vlastností, pořadové číslo a tlačítka OK, zrušit a použít. (Nemodálního seznamu vlastností nemá OK, zrušte a použít tlačítka.) Další ovládací prvky můžete přidat do seznamu vlastností. Například lze přidat okno náhledu napravo od oblasti vlastnost stránky se uživateli zobrazí, co bude aktuální nastavení vypadat Pokud použijí pro externího objektu.  
  
 Ovládací prvky můžete přidat do dialogového okna List vlastností v `OnCreate` obslužné rutiny. Další kontroly požadavků obvykle vyžaduje rozšíření velikost dialogového okna List vlastností. Po volání metody základní třídy **CPropertySheet::OnCreate**, volání [getwindowrect –](../mfc/reference/cwnd-class.md#getwindowrect) získat šířka a výška v okně List aktuálně přidělené vlastnosti, rozbalte obdélníku dimenzí a volání [MoveWindow](../mfc/reference/cwnd-class.md#movewindow) a změňte velikost okna List vlastností.  
  
## <a name="see-also"></a>Viz také  
 [Seznam vlastností](../mfc/property-sheets-mfc.md)   
 [CPropertyPage – třída](../mfc/reference/cpropertypage-class.md)   
 [Cpropertysheet – třída](../mfc/reference/cpropertysheet-class.md)
