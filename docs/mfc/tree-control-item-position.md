---
title: Umístění položky v ovládacím prvku stromu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7b7576786f456320a355920a7a9ef9e4935ab03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382148"
---
# <a name="tree-control-item-position"></a>Umístění položky v ovládacím prvku strom
Počáteční pozice položky je nastavena při přidání položky do ovládacího prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) pomocí `InsertItem` – členská funkce. Volání funkce člen Určuje popisovač nadřazené položky a popisovač položky, po jejímž uplynutí má vložit novou položku. Druhý popisovač musí identifikovat podřízenou položku daného nadřazeného prvku nebo jedné z těchto hodnot: `TVI_FIRST`, `TVI_LAST`, nebo `TVI_SORT`.  
  
 Když `TVI_FIRST` nebo `TVI_LAST` je zadán ovládací prvek stromu umístí novou položku na začátku nebo na konci daného nadřazené položky seznamu podřízené položky. Když `TVI_SORT` je zadán ovládací prvek stromu vloží novou položku do seznamu podřízené položky v abecedním pořadí na základě textu popisků položky.  
  
 Nadřazené položky seznamu podřízené položky můžete vložit do abecedním pořadí voláním [SortChildren](../mfc/reference/ctreectrl-class.md#sortchildren) – členská funkce. Tato funkce obsahuje parametr, který určuje, zda všechny úrovně podřízené položky sestupném z daného nadřazené položky jsou také seřazené podle abecedy.  
  
 [SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb) – členská funkce umožňuje řazení podřízené položky na základě kritérií, které definujete. Při volání této funkce zadejte funkci zpětné volání definované aplikací, která ovládací prvek stromu můžete volat vždy, když je relativní pořadí dva podřízené položky se rozhodla. Funkce zpětného volání přijímá dva 32-bit aplikace definované hodnoty pro položky porovnávané a třetí hodnota 32-bit, zadaný při volání metody `SortChildrenCB`.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

