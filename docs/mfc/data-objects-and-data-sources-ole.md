---
title: Datové objekty a zdroje dat (OLE) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f933a8eb75c25921c3025f8ca1bc03a2c72fc81b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443940"
---
# <a name="data-objects-and-data-sources-ole"></a>Datové objekty a zdroje dat (OLE)

Když provádíte přenosu dat, buď pomocí do schránky nebo operace přetažení, data mají zdroj a cíl. Jedna aplikace poskytuje data pro kopírování a jiná aplikace přijme ji pro vložení. Každé straně přenosu musí provádět různé operace na stejná data pro přenos proběhla úspěšně. Knihovny Microsoft Foundation Class (MFC) poskytuje dvě třídy, které představují každé straně tento převod:

- Zdroje dat (jak je implementované `COleDataSource` objekty) představují na straně zdroje dat k přenesení. Když data se mají zkopírovat do schránky, nebo když nejsou k dispozici data pro operaci přetažení myší jsou vytvořeny rutinou zdrojová aplikace.

- Datové objekty (jak je implementované `COleDataObject` objekty) představují na cílové straně přenosu dat. Jsou vytvořeny při cílové aplikace má data přetažení do ní, nebo pokud se zobrazí výzva k provedení operace vložení ze schránky.

Následující články popisují, jak používat datové objekty a zdroje dat ve svých aplikacích. Tyto informace platí pro kontejner i serverových aplikací, protože obě může být volána po zkopírování a vložení data.

- [Datové objekty a zdroje dat: Vytváření a likvidace](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Datové objekty a zdroje dat: Manipulace](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="in-this-section"></a>V tomto oddílu

[Přetažení](../mfc/drag-and-drop-ole.md)

[Schránka](../mfc/clipboard.md)

## <a name="see-also"></a>Viz také

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleDataObject – třída](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource – třída](../mfc/reference/coledatasource-class.md)
