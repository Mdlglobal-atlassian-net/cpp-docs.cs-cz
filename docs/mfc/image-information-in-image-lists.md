---
title: Obrázek informace v seznamech obrázků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c98bc629cde74cf7a6fc8a416de862f50a1dd5ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422282"
---
# <a name="image-information-in-image-lists"></a>Informace o obrázku v seznamu obrázků

[Cimagelist –](../mfc/reference/cimagelist-class.md) zahrnuje celou řadu funkcí, které načítají informace ze seznamu obrázků. [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo) vyplní členskou funkci `IMAGEINFO` struktura s informacemi o jedné image, včetně popisovačů image a maska rastrové obrázky, počet barevných rovin a počet bitů na pixel a ohraničující obdélník bitové kopie v rámci image rastrového obrázku. Tyto informace můžete přímo pracovat s rastrové obrázky pro bitovou kopii.

[Getimagecount –](../mfc/reference/cimagelist-class.md#getimagecount) členskou funkci zjišťuje počet imagí v seznamu obrázků.

Můžete vytvořit podle image a maska v seznamu obrázků pomocí ikony [ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon) členskou funkci. Vrátí popisovač na ikonu nový.

## <a name="see-also"></a>Viz také

[Používání atributu CImageList](../mfc/using-cimagelist.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

