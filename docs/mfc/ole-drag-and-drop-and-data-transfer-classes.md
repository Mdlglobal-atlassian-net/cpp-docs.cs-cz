---
title: OLE přetahování myší a třídy přenosu dat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d55d6d171f490631afe17a605f50607fb55f070b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347039"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Přetahování v rozhraní OLE a třídy přenosu dat
Tyto třídy se používají v přenosech souborů OLE. Umožňují data na přenos mezi aplikací pomocí schránky nebo prostřednictvím přetažení a drop.  
  
 [COleDropSource](../mfc/reference/coledropsource-class.md)  
 Určuje operaci přetažení myší od začátku do konce. Tato třída určuje při spuštění operace přetažení a při ukončení. Zobrazí také zpětná vazba kurzoru během operace přetažení myší.  
  
 [Coledatasource –](../mfc/reference/coledatasource-class.md)  
 Když aplikaci poskytuje data pro přenos dat použít. `COleDataSource` může zobrazit jako objekt objektově orientované schránky.  
  
 [COleDropTarget](../mfc/reference/coledroptarget-class.md)  
 Představuje cíl operace přetažení myší. A `COleDropTarget` objekt odpovídá okně na obrazovce. Určují, jestli se má přijmout žádná data do ho vyřadit a implementuje operace skutečného odstranění.  
  
 [COleDataObject](../mfc/reference/coledataobject-class.md)  
 Použít jako na straně příjemce k `COleDataSource`. `COleDataObject` objekty poskytnout přístup k datům, uložení `COleDataSource` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

