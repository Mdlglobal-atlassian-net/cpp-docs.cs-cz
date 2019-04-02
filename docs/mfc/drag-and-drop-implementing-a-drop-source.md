---
title: 'Přetažení: Implementace zdroje přemístění'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE drag and drop [MFC], initiating drag operations
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], drop source
- OLE drag and drop [MFC], calling DoDragDrop
- drag and drop [MFC], initiating drag operations
- drag and drop [MFC], drop source
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
ms.openlocfilehash: 2aa593fa953f7a9874036d48124ae7b92d88e0a6
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768637"
---
# <a name="drag-and-drop-implementing-a-drop-source"></a>Přetažení: Implementace zdroje přemístění

Tento článek vysvětluje, jak získat aplikace pro zadání dat pro operaci přetažení myší.

Základní implementace zdroje přemístění je poměrně jednoduché. Prvním krokem je určit, jaké události spustit operaci přetažení. Doporučené pokyny pro uživatelské rozhraní definovat začátku operace přetažení jako výběr data a **WM_LBUTTONDOWN** události, ke kterým dochází v bodě uvnitř vybraná data. Ukázky knihovny MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) a [HIERSVR](../overview/visual-cpp-samples.md) postupujte podle následujících pokynů.

Pokud vaše aplikace je kontejner a je vybraná data propojenou nebo vložený objekt typu `COleClientItem`, zavolejte jeho `DoDragDrop` členskou funkci. V opačném případě sestavit `COleDataSource` , inicializujte ho pomocí výběru a následně zavolat objekt zdroje dat `DoDragDrop` členskou funkci. Pokud vaše aplikace je server, použijte `COleServerItem::DoDragDrop`. Informace o přizpůsobení standardní chování přetažení myší, najdete v článku [přetažení: Přizpůsobení](../mfc/drag-and-drop-customizing.md).

Pokud `DoDragDrop` vrátí **DROPEFFECT_MOVE**, okamžitě odstranit zdroj dat ze zdrojového dokumentu. Žádná návratová hodnota z `DoDragDrop` nemá žádný vliv na zdroj přetažení.

Další informace naleznete v tématu:

- [Implementace cíle přetažení](../mfc/drag-and-drop-implementing-a-drop-target.md)

- [Přizpůsobení přetažení](../mfc/drag-and-drop-customizing.md)

- [Vytváření a ničení OLE datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Manipulace s OLE datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="see-also"></a>Viz také:

[Přetažení (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop)<br/>
[COleClientItem::DoDragDrop](../mfc/reference/coleclientitem-class.md#dodragdrop)<br/>
[CView::OnDragLeave](../mfc/reference/cview-class.md#ondragleave)
