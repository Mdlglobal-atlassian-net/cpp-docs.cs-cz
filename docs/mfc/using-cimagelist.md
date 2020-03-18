---
title: Používání atributu CImageList
ms.date: 11/04/2016
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
ms.openlocfilehash: 09fd0e95ce2981afbebbfe10d87b26f88a7b5e13
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447234"
---
# <a name="using-cimagelist"></a>Používání atributu CImageList

Seznam obrázků reprezentovaný třídou [atributu CImageList](../mfc/reference/cimagelist-class.md)je kolekcí obrázků stejné velikosti, z nichž každá může být odkazována podle jejího indexu. Seznamy obrázků slouží k efektivní správě velkých sad ikon nebo rastrových obrázků. Seznamy obrázků samy o sebe nekontrolují, protože nejsou v systému Windows; používají se však s několika různými typy ovládacích prvků, včetně ovládacích prvků List ([CListCtrl](../mfc/reference/clistctrl-class.md)), stromové struktury ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) a ovládací prvky karty ([atributu CTabCtrl](../mfc/reference/ctabctrl-class.md)).

Všechny obrázky v seznamu obrázků jsou obsaženy ve formátu rastrového zařízení ve stejné šířce. Seznam obrázků může obsahovat také monochromatický rastrový obrázek, který obsahuje masky používané pro transparentní vykreslování obrázků (styl ikony). `CImageList` poskytuje členské funkce, které umožňují kreslit obrázky, vytvářet a zničit seznamy obrázků, přidávat a odebírat obrázky, nahrazovat obrázky, slučovat obrázky a přetahovat obrázky.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Typy seznamů obrázků](../mfc/types-of-image-lists.md)

- [Použití seznamu obrázků](../mfc/using-an-image-list.md)

- [Manipulace se seznamy obrázků](../mfc/manipulating-image-lists.md)

- [Vykreslování obrázků ze seznamu obrázků](../mfc/drawing-images-from-an-image-list.md)

- [Překryvy obrázků v seznamech obrázků](../mfc/image-overlays-in-image-lists.md)

- [Přetahování obrázků ze seznamu obrázků](../mfc/dragging-images-from-an-image-list.md)

- [Informace o obrázku v seznamech obrázků](../mfc/image-information-in-image-lists.md)

## <a name="see-also"></a>Viz také

[Ovládací prvky](../mfc/controls-mfc.md)
