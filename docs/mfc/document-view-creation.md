---
title: Vytvoření zobrazení dokumentu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 894bb5a0b3a4c86d764fc6f4a0e4b9ae18422669
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931850"
---
# <a name="documentview-creation"></a>Vytváření dokumentů/zobrazení
Rozhraní framework poskytuje implementace **nový** a **otevřete** příkazy (mimo jiné) **souboru** nabídky. Vytvoření nového dokumentu a jeho přidružené zobrazení a oken s rámečkem je spolupráci úsilí mezi objekt aplikace, šablony dokumentu, nově vytvořený dokumentu a nově vytvořený rámce okna. Následující tabulka shrnuje, které objekty vytvořit co.  
  
### <a name="object-creators"></a>Tvůrci objektů  
  
|tvůrce|Vytvoří|  
|-------------|-------------|  
|Objekt aplikace|Šablony dokumentů|  
|Šablony dokumentů|Dokument|  
|Šablony dokumentů|Oken s rámečkem|  
|Oken s rámečkem|Zobrazit|  
  
## <a name="see-also"></a>Viz také  
 [Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Vytváření šablon dokumentů](../mfc/document-template-creation.md)   
 [Vztahy mezi objekty MFC](../mfc/relationships-among-mfc-objects.md)   
 [Vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md)

