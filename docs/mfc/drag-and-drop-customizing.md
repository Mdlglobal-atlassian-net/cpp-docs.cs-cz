---
title: 'Přetažení: Přizpůsobení'
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], implementing in non-OLE applications
- drag and drop [MFC], customizing behavior
- drag and  [MFC], COleDataSource object
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], customizing behavior
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
ms.openlocfilehash: d97bebce3ec7935dba7a9eca02a21be749efbec7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494288"
---
# <a name="drag-and-drop-customizing"></a>Přetažení: Přizpůsobení

Výchozí implementace funkcí přetahování myší stačí pro většinu aplikací. Některé aplikace však může vyžadovat, aby byla změněna tento standardní chování. Tento článek vysvětluje postup, chcete-li změnit toto výchozí nastavení. Kromě toho můžete použít tuto techniku k vytvoření aplikace, které nepodporují složené dokumenty jako zdroj přetažení.

Pokud se přizpůsobení standardní chování a přetahování OLE nebo už využíváte-OLE – aplikace, musíte vytvořit `COleDataSource` objekt obsahující data. Když uživatel spustí operaci přetažení myší, by měl váš kód volat `DoDragDrop` funkce z tohoto objektu namísto z jiné třídy, které podporují operace přetažení myší.

Volitelně můžete vytvořit `COleDropSource` objektu na ovládací prvek rozevírací nabídku a některé jeho funkce v závislosti na typ chcete změnit chování přepsat. Tento objekt zdroje přemístění je pak předán `COleDataSource::DoDragDrop` Chcete-li změnit výchozí chování těchto funkcí. Těmito možnostmi umožní značnou flexibilitu při jak podporovat operace přetažení myší ve vaší aplikaci. Další informace o zdrojích dat najdete v článku [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md).

Následující funkce pro přizpůsobení operací přetažení myší, můžete přepsat:

|přepsání|Chcete-li přizpůsobit|
|--------------|------------------|
|`OnBeginDrag`|Jak přetažení je zahájeno po zavolání `DoDragDrop`.|
|`GiveFeedback`|Vizuální zpětnou vazbu, jako je například vzhled kurzoru pro jiné odkládací výsledky.|
|`QueryContinueDrag`|Ukončení operace přetažení myší. Tato funkce umožňuje zkontrolovat stavy klíče modifikátor během operace přetažení.|

## <a name="see-also"></a>Viz také

[Přetažení (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDropSource – třída](../mfc/reference/coledropsource-class.md)<br/>
[COleDataSource – třída](../mfc/reference/coledatasource-class.md)
