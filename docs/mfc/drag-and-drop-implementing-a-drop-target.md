---
title: 'Přetažení: Implementace cíle přetažení'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE drag and drop [MFC], implementing drop targets
- OLE drag and drop [MFC], drop target
- drag and drop [MFC], drop target
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
ms.openlocfilehash: 55c8bbe9484a71ee95d43609b29a055b4177914b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599872"
---
# <a name="drag-and-drop-implementing-a-drop-target"></a>Přetažení: Implementace cíle přetažení

Tento článek popisuje, jak se vaše aplikace cíl přetažení. Implementace cíle přetažení trvá o něco více práce než implementace zdroje přemístění, ale je poměrně snadné. Tyto postupy platí také pro aplikacích jiných než OLE.

#### <a name="to-implement-a-drop-target"></a>Implementace cíle přetažení

1. Přidání členské proměnné do jednotlivých zobrazení v aplikaci, která mají být cíl přetažení. Tato členská proměnná musí být typu `COleDropTarget` nebo z něj odvozenou třídu.

1. Z funkce Zobrazit třídu, která zpracovává **WM_CREATE** zprávy (obvykle `OnCreate`), volání nové členské proměnné `Register` členskou funkci. `Revoke` zavolá se automaticky za vás při zničení zobrazení.

1. Přepište následující funkce. Pokud má stejné chování v rámci aplikace přepište tyto funkce ve třídě zobrazení. Pokud chcete změnit chování v ojedinělých případech nebo chcete povolit vyřazení na jinou hodnotu než`CView` přepsat tyto funkce v systému windows, vaše `COleDropTarget`-odvozené třídy.

    |přepsání|Chcete-li povolit|
    |--------------|--------------|
    |`OnDragEnter`|Operace vyskytuje v okně vyřaďte. Volá se, když ukazatel poprvé vstoupí do okna.|
    |`OnDragLeave`|Zvláštní chování při operaci přetažení opustí určené okno.|
    |`OnDragOver`|Operace vyskytuje v okně vyřaďte. Volá se, když se ocitne kurzoru v okně.|
    |`OnDrop`|Zpracování dat probíhá vyřazování do určené okno.|
    |`OnScrollBy`|Zvláštní chování při posouvání je nezbytné v okně cíl.|

Podívejte se MAINVIEW. CPP souboru, který je součástí ukázky MFC OLE [OCLIENT](../visual-cpp-samples.md) pro příklad, jak tyto funkce fungují společně.

Další informace naleznete v tématu:

- [Implementace zdroje přemístění](../mfc/drag-and-drop-implementing-a-drop-source.md)

- [Vytváření a ničení OLE datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Manipulace s OLE datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="see-also"></a>Viz také

[Přetažení (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDropTarget – třída](../mfc/reference/coledroptarget-class.md)
