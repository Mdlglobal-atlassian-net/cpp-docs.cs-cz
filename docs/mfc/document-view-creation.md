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
ms.openlocfilehash: b5f9b783e8e14744a816fd63b327ed95d9da8e8a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304944"
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

## <a name="see-also"></a>Viz také:

[Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Vytváření šablon dokumentů](../mfc/document-template-creation.md)<br/>
[Vztahy mezi objekty MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md)
