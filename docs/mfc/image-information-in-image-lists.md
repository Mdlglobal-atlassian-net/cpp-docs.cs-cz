---
title: Informace o obrázku v seznamu obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
ms.openlocfilehash: 7b83b7e5f7de6f8ccca95d732f71a5d73a97e943
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263062"
---
# <a name="image-information-in-image-lists"></a>Informace o obrázku v seznamu obrázků

[Cimagelist –](../mfc/reference/cimagelist-class.md) zahrnuje celou řadu funkcí, které načítají informace ze seznamu obrázků. [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo) vyplní členskou funkci `IMAGEINFO` struktura s informacemi o jedné image, včetně popisovačů image a maska rastrové obrázky, počet barevných rovin a počet bitů na pixel a ohraničující obdélník bitové kopie v rámci image rastrového obrázku. Tyto informace můžete přímo pracovat s rastrové obrázky pro bitovou kopii.

[Getimagecount –](../mfc/reference/cimagelist-class.md#getimagecount) členskou funkci zjišťuje počet imagí v seznamu obrázků.

Můžete vytvořit podle image a maska v seznamu obrázků pomocí ikony [ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon) členskou funkci. Vrátí popisovač na ikonu nový.

## <a name="see-also"></a>Viz také:

[Používání atributu CImageList](../mfc/using-cimagelist.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
