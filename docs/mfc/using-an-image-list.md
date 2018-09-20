---
title: Použití seznamu obrázků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4dc30d418ae57205e4566dad7f490a773321768e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391667"
---
# <a name="using-an-image-list"></a>Použití seznamu obrázků

Typické použití seznamu obrázků má následující formát, níže:

- Vytvoření [atributu CImageList](../mfc/reference/cimagelist-class.md) objektu a volání jednoho z přetížení jeho [vytvořit](../mfc/reference/cimagelist-class.md#create) funkci pro vytvoření seznamu obrázků a připojte ji k `CImageList` objektu.

- Pokud jste nepřidali Image při vytváření seznamu obrázků, přidání obrázků do seznamu obrázků voláním [přidat](../mfc/reference/cimagelist-class.md#add) nebo [čtení](../mfc/reference/cimagelist-class.md#read) členskou funkci.

- Přidružení seznamu obrázků s ovládacím prvkem voláním příslušné členské funkce ovládacího prvku nebo vykreslení obrázků ze seznamu obrázků sami pomocí seznamu obrázků [nakreslit](../mfc/reference/cimagelist-class.md#draw) členskou funkci.

- Možná umožní uživateli přetáhnout image, pomocí seznamu obrázků integrovanou podporu pro přetažení myší.

> [!NOTE]
>  Pokud byl vytvořen seznam obrázků **nové** operátoru, budete muset zničit `CImageList` objektu, jakmile budete hotovi s ním.

## <a name="see-also"></a>Viz také

[Používání atributu CImageList](../mfc/using-cimagelist.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

