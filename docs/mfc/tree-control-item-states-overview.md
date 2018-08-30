---
title: Přehled stavů položek ovládacího prvku strom | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be5c0d3e477103edaf31bafed01265a509e48ad1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198338"
---
# <a name="tree-control-item-states-overview"></a>Přehled stavů položek ovládacího prvku strom
Každá položka v ovládacím prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) má aktuální stav. Například může být vybrána položka, zakázané, rozšíření a tak dále. Ve většině případů do ovládacího prvku stromu automaticky nastaví stav položky tak, aby odrážely akcí uživatelů, jako je například výběr položky. Však můžete také nastavit stav položky pomocí [SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate) členské funkce a jejich načtení položky pomocí aktuální stav [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate) členskou funkci. Úplný seznam stavů položek, naleznete v tématu [konstanty ovládacího prvku Tree-View](/windows/desktop/Controls/tree-view-control-item-states) v sadě Windows SDK.  
  
 Je určená aktuální stav položky *nInformace* parametru. Ovládací prvek stromu se může změnit stav položky tak, aby odrážely akci uživatele, jako je například výběrem položky nebo nastavení fokusu na položku. Kromě toho aplikace může změnit stav položky pro zakázání nebo skrytí položky nebo překrytí obrázek nebo obrázku stavu.  
  
 Když zadáte nebo změnit stav položky *nStateMask* parametr určuje, které stav bits k nastavení a *nInformace* parametr obsahuje nové hodnoty pro tyto služby bits. Například následující příklad změní aktuální stav nadřazené položky (určená *hParentItem*) v `CTreeCtrl` objektu (`m_treeCtrl`) k `TVIS_EXPANDPARTIAL`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]  
  
 Nastavit obrázek položky překrytí je další příklad změnu stavu. K tomu *nStateMask* musí zahrnovat `TVIS_OVERLAYMASK` hodnotu, a *nInformace* musí obsahovat založen na jedničce index obrázku překrytí posunuta doleva 8 bitů s použitím [ INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) – makro. Index může být 0 pro žádné překrytí image. Překrytí image musí být přidán do seznamu ovládacího prvku stromu překrytí imagí podle předchozího volání [CImageList::SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) funkce. Funkce určuje založen na jedničce index image, přidat; Toto je index použitý s INDEXTOOVERLAYMASK makra. Stromový ovládací prvek může mít až čtyři překrytí imagí.  
  
 Nastavit stav obrázku položky *nStateMask* musí zahrnovat `TVIS_STATEIMAGEMASK` hodnotu, a *nInformace* musí obsahovat založen na jedničce index obrázku stavu posunuta doleva 12 bitů s použitím [ INDEXTOSTATEIMAGEMASK](/windows/desktop/api/commctrl/nf-commctrl-indextostateimagemask) – makro. Index může být 0 pro žádné obrázku stavu. Další informace o imagích překrytí a stavu najdete v tématu [seznamy obrázků ovládací prvek stromu](../mfc/tree-control-image-lists.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

