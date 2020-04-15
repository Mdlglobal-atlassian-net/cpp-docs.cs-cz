---
title: Použití seznamu obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: 0d9566739a15e5d216eb052a7265313850515648
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366577"
---
# <a name="using-an-image-list"></a>Použití seznamu obrázků

Typické použití seznamu obrázků se řídí následujícím vzorem:

- Vytvořte objekt [CImageList](../mfc/reference/cimagelist-class.md) a volání jednoho z přetížení jeho [Create](../mfc/reference/cimagelist-class.md#create) funkce vytvořit `CImageList` seznam obrázků a připojit jej k objektu.

- Pokud jste při vytváření seznamu obrázků nepřidali obrázky, přidejte obrázky do seznamu obrázků voláním členské funkce [Přidat](../mfc/reference/cimagelist-class.md#add) nebo [Číst.](../mfc/reference/cimagelist-class.md#read)

- Přidružte seznam obrázků k ovládacímu prvku voláním příslušné členské funkce tohoto ovládacího prvku nebo nakreslete obrázky ze seznamu obrázků sami pomocí členské funkce [Draw](../mfc/reference/cimagelist-class.md#draw) seznamu obrázků.

- Možná, že umožní uživateli přetáhnout obrázek, pomocí seznamu obrázků je vestavěná podpora pro přetažení.

> [!NOTE]
> Pokud byl seznam obrázků vytvořen pomocí **nového** `CImageList` operátoru, musíte objekt po dokončení zničit.

## <a name="see-also"></a>Viz také

[Používání atributu CImageList](../mfc/using-cimagelist.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
