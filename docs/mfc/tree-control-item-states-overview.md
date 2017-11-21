---
title: "Přehled stavů položek ovládacího prvku strom | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 16a16a1c400c840d0e8abe2e9c078d295d891dc7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tree-control-item-states-overview"></a>Přehled stavů položek ovládacího prvku strom
Každá položka v ovládacím prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) má aktuální stav. Například může být vybrána položka, zakázaná, Rozšířená a tak dále. Ve většině případů ovládací prvek stromu automaticky nastaví stav položky tak, aby odrážela uživatelské akce, jako je výběr položky. Však můžete také nastavit stav položky pomocí [SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate) – členská funkce a načtěte aktuální stav položky pomocí [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate) – členská funkce. Úplný seznam stavů položek, najdete v části [stromové zobrazení ovládacího prvku konstanty](http://msdn.microsoft.com/library/windows/desktop/bb759985) ve Windows SDK.  
  
 Je zadána aktuální stav položky `nState` parametr. Ovládací prvek stromu může změnit stav položky tak, aby odrážela akci uživatele, například výběrem položky nebo nastavení zaměřená na položky. Kromě toho aplikace může změnit stav položky zakázat nebo skryje položku nebo k zadání překrytí obrázek nebo obrázek stavu.  
  
 Když zadáte nebo změna stavu pro položku `nStateMask` parametr určuje, které stavu bits k nastavení a `nState` parametr obsahuje nové hodnoty pro tyto služby bits. Například následující příklad změní aktuální stav nadřazené položky (zadáno v `hParentItem`) v `CTreeCtrl` objektu (`m_treeCtrl`) k **TVIS_EXPANDPARTIAL**:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]  
  
 Další příklad změny stavu bude nastavení položky překrytí image. K tomu `nStateMask` musí obsahovat `TVIS_OVERLAYMASK` hodnotu, a `nState` musí zahrnovat na základě jeden index bitové kopie překrytí zapuštěno zbývajících osm bits pomocí [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) makro. Index může být 0 pro žádné překrytí bitové kopie. Bitovou kopii překrytí musí být přidán do seznamu ovládací prvek stromu bitových kopií překrytí voláním předchozí [CImageList::SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) funkce. Funkce určuje na základě jeden index image přidat; Toto je index použít s **INDEXTOOVERLAYMASK** makro. Ovládací prvek stromu může mít až čtyři obrázky překrytí.  
  
 Nastavit obrázek stavu pro položku, `nStateMask` musí obsahovat `TVIS_STATEIMAGEMASK` hodnotu, a `nState` musí zahrnovat na základě jeden index obrázku stavu zapuštěno zbývajících 12 bits pomocí [INDEXTOSTATEIMAGEMASK](http://msdn.microsoft.com/library/windows/desktop/bb775597) makro. Index může být 0 pro žádné obrázek stavu. Další informace o bitových kopiích překrytí a stavu najdete v tématu [seznamy obrázků ovládací prvek stromu](../mfc/tree-control-image-lists.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

