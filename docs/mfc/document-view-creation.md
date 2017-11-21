---
title: "Vytvoření zobrazení dokumentu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e98f6e4b1b9ecd5848c2701043aa9b0b7dcea7d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="documentview-creation"></a>Vytváření dokumentů/zobrazení
Rozhraní framework poskytuje implementace `New` a **otevřete** příkazy (mimo jiné) **souboru** nabídky. Vytvoření nového dokumentu a jeho přidružené zobrazení a oken s rámečkem je spolupráci úsilí mezi objekt aplikace, šablony dokumentu, nově vytvořený dokumentu a nově vytvořený rámce okna. Následující tabulka shrnuje, které objekty vytvořit co.  
  
### <a name="object-creators"></a>Tvůrci objektů  
  
|tvůrce|Vytvoří|  
|-------------|-------------|  
|objekt aplikace|Šablony dokumentů|  
|Šablony dokumentů|Dokument|  
|Šablony dokumentů|Oken s rámečkem|  
|Oken s rámečkem|Zobrazit|  
  
## <a name="see-also"></a>Viz také  
 [Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Vytváření šablon dokumentů](../mfc/document-template-creation.md)   
 [Vztahy mezi objekty MFC](../mfc/relationships-among-mfc-objects.md)   
 [Vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md)

