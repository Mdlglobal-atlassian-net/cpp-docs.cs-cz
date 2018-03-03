---
title: "Objednávání položek v ovládacím prvku záhlaví | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 48adbc53ad0e4974edd86d3f8a96d74214093dda
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ordering-items-in-the-header-control"></a>Objednávání položek v ovládacím prvku záhlaví
Jakmile jste [přidání položek do ovládacího prvku záhlaví](../mfc/adding-items-to-the-header-control.md), můžete upravit nebo získat informace o jejich pořadí s následující funkce:  
  
-   [CHeaderCtrl::GetOrderArray](../mfc/reference/cheaderctrl-class.md#getorderarray) a [CHeaderCtrl::SetOrderArray](../mfc/reference/cheaderctrl-class.md#setorderarray)  
  
     Získá a nastaví zleva doprava pořadí položek záhlaví.  
  
-   [CHeaderCtrl::OrderToIndex](../mfc/reference/cheaderctrl-class.md#ordertoindex).  
  
     Načte hodnotu indexu pro konkrétní hlavičky položku.  
  
 Kromě předchozích členské funkce `HDS_DRAGDROP` styl umožňuje uživateli přetažení položek záhlaví v ovládacím prvku záhlaví. Další informace najdete v tématu [zajištění podpory přetažení a přetažení u položek záhlaví](../mfc/providing-drag-and-drop-support-for-header-items.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)

