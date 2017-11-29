---
title: "Popisky položek ovládacího prvku strom | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: de81e2694d25375c56a2aa8300146b4d1f5f7b87
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tree-control-item-labels"></a>Popisky položek ovládacího prvku strom
Text popisku pro položku obvykle zadat, pokud položku přidáte do ovládacího prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)). `InsertItem` – Členská funkce můžete předat [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) struktura, která definuje vlastnosti položky, včetně řetězec obsahující text popisku. `InsertItem`má několik přetížení, která může být volána s různé kombinace parametrů.  
  
 Ovládací prvek stromu přidělí paměť pro ukládání každou položku; text popisky položek zabírá podstatnou část tuto paměť. Pokud vaše aplikace udržuje kopii řetězce v ovládacím prvku stromu, můžete snížit požadavky na paměť ovládacího prvku tak, že zadáte **LPSTR_TEXTCALLBACK** hodnotu **pszText** členem `TV_ITEM` nebo `lpszItem` parametr neprochází skutečné řetězce do ovládacího prvku strom. Pomocí **LPSTR_TEXTCALLBACK** způsobí, že k získání textu popisku položky z aplikace, vždy, když je položka překreslit ovládacího prvku strom. K získání textu, odešle ovládací prvek stromu [TVN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518) zprávy oznámení, která zahrnuje adresu [NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418) struktury. Musí odpovědět, a to nastavením odpovídající členů struktury zahrnuty.  
  
 Ovládací prvek stromu používá paměti přidělené z haldy procesu, který vytváří ovládací prvek stromu. Maximální počet položek v ovládacím prvku stromu podle množství paměti k dispozici v haldě. Každá položka má 64 bajtů.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)
