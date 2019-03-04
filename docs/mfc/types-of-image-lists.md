---
title: Typy seznamů obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
ms.openlocfilehash: 939aad78b7cf8cca9c940bae11892d23dbb659cb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304753"
---
# <a name="types-of-image-lists"></a>Typy seznamů obrázků

Existují dva typy seznamů obrázků ([atributu CImageList](../mfc/reference/cimagelist-class.md)): nonmasked a maskované. Seznam"nonmasked image" se skládá z barvy rastrového obrázku, který obsahuje jeden nebo více bitových kopií. "Maskované image seznam" se skládá z dvou rastrové obrázky stejnou velikost. Barvy rastrového obrázku, který obsahuje Image je první a druhý je monochromatický rastrový obrázek, který obsahuje řadu masky – jeden pro každý obrázek v první rastrového obrázku.

Jeden z přetížení `Create` členské funkce má příznak označující, zda je seznam obrázků zakryté hvězdičkami. (Další přetížení vytvořit seznamy obrázků maskované.)

Při vykreslení nonmasked image je jednoduše zkopírovat do kontextu cílového zařízení; To znamená je vykreslen přes existující barvu pozadí kontextu zařízení. Při vykreslení maskované image bitů bitové kopie spolu se bity maska, kde se zobrazuje barva pozadí kontextu cílového zařízení prostřednictvím obvykle vytváří průhledné oblasti v rastrového obrázku. Při vykreslování maskované image, můžete zadat několik vykreslování stylů. Například můžete určit, že se image tónovaná označuje vybraný objekt.

## <a name="see-also"></a>Viz také:

[Používání atributu CImageList](../mfc/using-cimagelist.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
