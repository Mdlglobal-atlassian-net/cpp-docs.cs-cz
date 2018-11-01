---
title: Manipulace se seznamy obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
ms.openlocfilehash: 7ec641f1e7090e27edd367203b430b932ede52a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643765"
---
# <a name="manipulating-image-lists"></a>Manipulace se seznamy obrázků

[Nahradit](../mfc/reference/cimagelist-class.md#replace) členskou funkci nahrazuje obrázek v seznamu obrázků ([atributu CImageList](../mfc/reference/cimagelist-class.md)) s novou bitovou kopii. Tato funkce je také užitečné, pokud je třeba dynamicky zvýšit počet obrázků do seznamu objektu image. [SetImageCount](../mfc/reference/cimagelist-class.md#setimagecount) funkce dynamicky mění počet obrázků uložených v seznamu obrázků. Pokud zvýšíte velikost seznamu obrázků, zavolejte `Replace` přidat Image do nové image sloty. Je-li snížit velikost seznamu obrázků jsou uvolněny obrázků nad rámec novou velikost.

[Odebrat](../mfc/reference/cimagelist-class.md#remove) členská funkce odebere bitovou kopii ze seznamu obrázků. [Kopírování](../mfc/reference/cimagelist-class.md#copy) můžete členské funkce Kopírovat nebo odkládacího souboru bitové kopie v rámci seznamu obrázků. Tato funkce umožňuje určit, zda zdrojového obrázku mají být zkopírovány do cílového indexu nebo bitové kopie zdrojových a cílových měl vyměnit.

K vytvoření nového seznamu obrázků sloučení dvou seznamů obrázků, použijte odpovídající přetížení [vytvořit](../mfc/reference/cimagelist-class.md#create) členskou funkci. Toto přetížení `Create` sloučení první obrázek existující bitová kopie obsahuje, ukládání výsledná obrázku v seznamu objektů nové image. Kreslení druhý obrázek transparentně přes první vytvoří novou image. Maska pro nové image je výsledek provedení operace logického operátoru OR s bity masky pro dva existující Image.

Tato akce se opakuje dokud všechny bitové kopie byly sloučeny a přidali na nový objekt seznamu obrázků.

Informace o bitové kopii můžete napsat do archivu voláním [zápisu](../mfc/reference/cimagelist-class.md#write) členská funkce a přečtěte si ji zpět voláním [čtení](../mfc/reference/cimagelist-class.md#read) členskou funkci.

[GetSafeHandle](../mfc/reference/cimagelist-class.md#getsafehandle), [připojit](../mfc/reference/cimagelist-class.md#attach), a [odpojit](../mfc/reference/cimagelist-class.md#detach) členských funkcí umožňuje manipulaci s popisovačem seznam obrázků, které jsou připojené k `CImageList` objektu, zatímco [DeleteImageList](../mfc/reference/cimagelist-class.md#deleteimagelist) členská funkce odstraní seznam obrázků, aniž by zlikvidoval `CImageList` objektu.

## <a name="see-also"></a>Viz také

[Používání atributu CImageList](../mfc/using-cimagelist.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

