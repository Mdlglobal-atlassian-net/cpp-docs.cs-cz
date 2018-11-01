---
title: Přetažení (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
ms.openlocfilehash: 956c746d6eef84edd7be3ab9b6c6d15107269b1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450346"
---
# <a name="drag-and-drop-ole"></a>Přetažení (OLE)

Funkce a přetahování OLE je primárně klávesovou zkratku pro kopírování a vkládání dat. Při použití schránky pro kopírování nebo vkládání dat, se vyžadují několik kroků. Vyberte data, klikněte na tlačítko **Vyjmout** nebo **kopírování** z **upravit** nabídce, přejít k cílovému souboru, okno nebo aplikace, umístěte kurzor do požadovaného umístění a klikněte na **Vložit** z **upravit** nabídky.

OLE – přetažení se liší od mechanismus přetažení myší Správce souborů, který může zpracovat pouze názvy souborů a je určený konkrétně pro předávání názvů souborů do aplikace. OLE – přetažení je mnohem více obecné. Umožňuje přetáhnout myší všechna data, která můžete také umístit do schránky.

Při použití OLE – přetažení, odeberete z procesu dva kroky. Vyberte data z okna zdroje ("rozevírací zdroj"), přetáhněte ho do požadovaného cíle ("cíl") a umístěte ho uvolněním tlačítka myši. Tato operace se eliminuje potřeba nabídky a je rychlejší než řada, kopírování a vkládání. Jediným požadavkem je, že rozevírací zdroj i cíl přetažení musí být otevřený a aspoň částečně viditelný na obrazovce.

Použití OLE – přetažení, může být přenesená data z jednoho umístění do jiného v rámci dokumentu, mezi různými dokumenty nebo mezi aplikacemi. Se dá implementovat v kontejneru nebo serverové aplikace, a jakékoli aplikace může být zdroje přemístění nebo cíl přetažení. Pokud aplikace podporuje rozevírací zdroj a cíl přetažení implementované, je povoleno přetažení mezi podřízená okna nebo v rámci jednoho okna. Tato funkce může vaše aplikace značně zjednodušují použít.

Pokud chcete používat funkce a přetahování OLE, přečtěte si téma [přetažení: přizpůsobení](../mfc/drag-and-drop-customizing.md). Technik popsaných v tomto článku můžete použít tak, aby aplikace OLE – přetažení zdroje. Tento článek [přetažení: implementace cíle přetažení](../mfc/drag-and-drop-implementing-a-drop-target.md) popisuje způsob implementace cíle přetažení podporu technologie OLE a aplikacích jiných než OLE. To se hodí i prozkoumat ukázky MFC OLE [OCLIENT](../visual-cpp-samples.md) a [HIERSVR](../visual-cpp-samples.md).

Pokud jste čtení [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md) řady článků, můžete chtít provést nyní. Tyto články vysvětlují základní informace o přenosu dat a jak implementovat ve svých aplikacích.

Další informace o přetahování naleznete v tématu:

- [Přetažení: Implementace zdroje přemístění](../mfc/drag-and-drop-implementing-a-drop-source.md)

- [Přetažení: Implementace cíle přetažení](../mfc/drag-and-drop-implementing-a-drop-target.md)

- [Přetažení: Přizpůsobení](../mfc/drag-and-drop-customizing.md)

## <a name="see-also"></a>Viz také

[OLE](../mfc/ole-in-mfc.md)<br/>
[Datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md)

