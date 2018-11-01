---
title: Používání atributu CImageList
ms.date: 11/04/2016
f1_keywords:
- CImageList
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
ms.openlocfilehash: 92d639468e7465415b3553558090ca2d6811de9c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502671"
---
# <a name="using-cimagelist"></a>Používání atributu CImageList

Seznam obrázků, reprezentovaný třídou [atributu CImageList](../mfc/reference/cimagelist-class.md), je kolekce obrazů stejné velikosti, z nichž každý lze odkazovat pomocí jeho indexu. Seznamy obrázků se používají k zajištění efektivní správy velkých sad ikony nebo rastrové obrázky. Seznamy obrázků představují samy o sobě ovládací prvky, protože se nejedná o systému windows. Nicméně se používají v několika různých typů ovládacích prvků, včetně ovládacích prvcích seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)), stromové struktury ovládacích prvků ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) a kartě ovládacích prvků ([ctabctrl –](../mfc/reference/ctabctrl-class.md)).

Všechny Image v seznamu obrázků jsou obsaženy v jedné široké rastrového obrázku ve formátu obrazovkovém zařízení. Seznam obrázků může také zahrnovat monochromatický rastrový obrázek, který obsahuje masky umožňuje transparentně vykreslení obrázků (styl ikon). `CImageList` Poskytuje členské funkce, které vám umožní vykreslení obrázků, vytvořit a zničit seznamy obrázků, přidat a odebíráním imagí, nahraďte Image, sloučit Image a přetáhněte obrázky.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Typy seznamů obrázků](../mfc/types-of-image-lists.md)

- [Použití seznamu obrázků](../mfc/using-an-image-list.md)

- [Manipulace se seznamy obrázků](../mfc/manipulating-image-lists.md)

- [Vykreslování obrázků ze seznamu obrázků](../mfc/drawing-images-from-an-image-list.md)

- [Překryvy obrázků v seznamech obrázků](../mfc/image-overlays-in-image-lists.md)

- [Přetahování obrázků ze seznamu obrázků](../mfc/dragging-images-from-an-image-list.md)

- [Informace o obrázku v seznamech obrázků](../mfc/image-information-in-image-lists.md)

## <a name="see-also"></a>Viz také

[Ovládací prvky](../mfc/controls-mfc.md)

