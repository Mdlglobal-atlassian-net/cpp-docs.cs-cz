---
title: Používání atributu CImageList | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CImageList
dev_langs:
- C++
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8dd30b21b1ec635c6d5b5f2f5c6c6d9eb6fc3fa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-cimagelist"></a>Používání atributu CImageList
Seznam obrázků, reprezentována třída [CImageList](../mfc/reference/cimagelist-class.md), je kolekce stejnou velikost bitové kopie, z nichž každý lze odkazovat pomocí jeho index. Seznamy obrázků umožňují efektivně spravovat velké sady ikony nebo bitmapy. Obrázek seznamy není sami ovládací prvky, protože se nejedná o windows; však se používají s několika různých typů ovládacích prvků, včetně ovládacích prvcích seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)), ovládací prvky stromové struktury ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) a kartě ovládacích prvků ([CTabCtrl](../mfc/reference/ctabctrl-class.md)).  
  
 Všechny Image v seznamu obrázků jsou obsažené v jednom široké rastrový obrázek ve formátu obrazovky zařízení. Seznam obrázků může také zahrnovat černobílý rastrového obrázku, který obsahuje masek použitý k vykreslení obrázků transparentně (ikona styl). `CImageList` Poskytuje členské funkce, které vám umožní kreslení bitové kopie, vytvořit destroy seznamů obrázků, přidat, odebrat bitové kopie, nahradit Image, sloučení bitové kopie a přetáhněte bitové kopie.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Typy seznamů obrázků](../mfc/types-of-image-lists.md)  
  
-   [Použití seznamu obrázků](../mfc/using-an-image-list.md)  
  
-   [Manipulace se seznamy obrázků](../mfc/manipulating-image-lists.md)  
  
-   [Vykreslování obrázků ze seznamu obrázků](../mfc/drawing-images-from-an-image-list.md)  
  
-   [Překryvy obrázků v seznamech obrázků](../mfc/image-overlays-in-image-lists.md)  
  
-   [Přetahování obrázků ze seznamu obrázků](../mfc/dragging-images-from-an-image-list.md)  
  
-   [Informace o obrázku v seznamech obrázků](../mfc/image-information-in-image-lists.md)  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky](../mfc/controls-mfc.md)

