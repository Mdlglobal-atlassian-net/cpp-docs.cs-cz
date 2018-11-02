---
title: Přetahování v rozhraní OLE a třídy přenosu dat
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: 7520881314da9568f6130f5fe2ccf0a3e0e88e2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475178"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Přetahování v rozhraní OLE a třídy přenosu dat

Tyto třídy jsou používáno v přenosech dat OLE. Nechají data přenesená mezi aplikacemi s využitím schránky nebo pomocí přetažení a přetažení.

[Coledropsource –](../mfc/reference/coledropsource-class.md)<br/>
Určuje operaci přetažení myší od začátku do konce. Tato třída určuje při operaci přetažení spuštění a ukončení. Zobrazí také kurzor zpětnou vazbu během operace přetažení myší.

[Coledatasource –](../mfc/reference/coledatasource-class.md)<br/>
Použít, pokud aplikace poskytuje data pro přenos dat. `COleDataSource` může zobrazit jako objekt schránky objektově orientovaný.

[Coledroptarget –](../mfc/reference/coledroptarget-class.md)<br/>
Představuje cíl operace přetažení myší. A `COleDropTarget` objekt odpovídá okna na obrazovce. Určuje, jestli se má přijmout žádná data vyřadit problém napravit a implementuje operace skutečné vyřazení.

[Coledataobject –](../mfc/reference/coledataobject-class.md)<br/>
Použít jako straně příjemce `COleDataSource`. `COleDataObject` objekty poskytují přístup k datům uloženým ve `COleDataSource` objektu.

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

