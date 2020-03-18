---
title: Přetahování v rozhraní OLE a třídy přenosu dat
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: 7e01b6d5a7d14e0af4ca760e6e601e91359c8ab1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447624"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Přetahování v rozhraní OLE a třídy přenosu dat

Tyto třídy jsou používány v datových přenosech OLE. Umožňují přenos dat mezi aplikacemi pomocí schránky nebo přetahování myší.

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
Řídí operaci přetažení od začátku do konce. Tato třída určuje, kdy se operace přetažení spustí a kdy skončí. Zobrazuje také zpětnou vazbu kurzoru během operace přetažení.

[COleDataSource –](../mfc/reference/coledatasource-class.md)<br/>
Používá se, když aplikace poskytuje data pro přenos dat. `COleDataSource` lze zobrazit jako objektově orientovaný objekt schránky.

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
Představuje cíl operace přetažení. Objekt `COleDropTarget` odpovídá oknu na obrazovce. Určuje, zda se mají přijmout všechna data, která jsou na něj vyřazena, a implementuje samotnou operaci drop.

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
Slouží jako `COleDataSource`přijímače na straně přijímače. objekty `COleDataObject` poskytují přístup k datům uloženým objektem `COleDataSource`.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
