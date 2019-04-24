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
ms.openlocfilehash: e30a358da55b29f9519bc1ab8ee5c93ada308d98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186059"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Přetahování v rozhraní OLE a třídy přenosu dat

Tyto třídy jsou používáno v přenosech dat OLE. Nechají data přenesená mezi aplikacemi s využitím schránky nebo pomocí přetažení a přetažení.

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
Určuje operaci přetažení myší od začátku do konce. Tato třída určuje při operaci přetažení spuštění a ukončení. Zobrazí také kurzor zpětnou vazbu během operace přetažení myší.

[COleDataSource](../mfc/reference/coledatasource-class.md)<br/>
Použít, pokud aplikace poskytuje data pro přenos dat. `COleDataSource` může zobrazit jako objekt schránky objektově orientovaný.

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
Představuje cíl operace přetažení myší. A `COleDropTarget` objekt odpovídá okna na obrazovce. Určuje, jestli se má přijmout žádná data vyřadit problém napravit a implementuje operace skutečné vyřazení.

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
Použít jako straně příjemce `COleDataSource`. `COleDataObject` objekty poskytují přístup k datům uloženým ve `COleDataSource` objektu.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
