---
title: Použití seznamu obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: cb95de134939e1b06e2a8b827424c986f8c48ef3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180463"
---
# <a name="using-an-image-list"></a>Použití seznamu obrázků

Typické použití seznamu obrázků má následující formát, níže:

- Vytvoření [atributu CImageList](../mfc/reference/cimagelist-class.md) objektu a volání jednoho z přetížení jeho [vytvořit](../mfc/reference/cimagelist-class.md#create) funkci pro vytvoření seznamu obrázků a připojte ji k `CImageList` objektu.

- Pokud jste nepřidali Image při vytváření seznamu obrázků, přidání obrázků do seznamu obrázků voláním [přidat](../mfc/reference/cimagelist-class.md#add) nebo [čtení](../mfc/reference/cimagelist-class.md#read) členskou funkci.

- Přidružení seznamu obrázků s ovládacím prvkem voláním příslušné členské funkce ovládacího prvku nebo vykreslení obrázků ze seznamu obrázků sami pomocí seznamu obrázků [nakreslit](../mfc/reference/cimagelist-class.md#draw) členskou funkci.

- Možná umožní uživateli přetáhnout image, pomocí seznamu obrázků integrovanou podporu pro přetažení myší.

> [!NOTE]
>  Pokud byl vytvořen seznam obrázků **nové** operátoru, budete muset zničit `CImageList` objektu, jakmile budete hotovi s ním.

## <a name="see-also"></a>Viz také:

[Používání atributu CImageList](../mfc/using-cimagelist.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
