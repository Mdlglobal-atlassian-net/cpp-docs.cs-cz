---
title: Vytváření dokumentů a zobrazení
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], creating
- views [MFC], and frame windows
- views [MFC], creating
- tables [MFC]
- MFC, views
- document/view architecture [MFC], creating document/view
- object creators
- MFC, documents
- tables [MFC], objects each MFC object creates
ms.assetid: bda14f41-ed50-439d-af9e-591174e7dd64
ms.openlocfilehash: eccc65df784d000f8dccc244e295da522658b626
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633554"
---
# <a name="documentview-creation"></a>Vytváření dokumentů/zobrazení

Architektura dodává implementace **nový** a **otevřít** příkazy (mimo jiné) na **souboru** nabídky. Vytvořit nový dokument a jeho přidružené zobrazení a okno rámce je kooperativní času mezi objekt aplikace, šablonu dokumentu, nově vytvořený dokument a nově vytvořený rámce okna. Následující tabulka shrnuje, které objekty vytvořit co.

### <a name="object-creators"></a>Tvůrci objektů

|tvůrce|Vytvoří|
|-------------|-------------|
|Objekt aplikace|Šablona dokumentu|
|Šablona dokumentu|Dokument|
|Šablona dokumentu|Okno rámce|
|Okno rámce|Zobrazit|

## <a name="see-also"></a>Viz také

[Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Vytváření šablon dokumentů](../mfc/document-template-creation.md)<br/>
[Vztahy mezi objekty MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md)

