---
title: "Šablony dokumentů a proces vytvoření zobrazení dokumentů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- icons, for multiple document templates
- document templates [MFC], and views
- document/view architecture [MFC], creating document/view
- single document template
- MFC, document templates
- multiple document template
- CDocTemplate class [MFC]
- templates [MFC], document templates
ms.assetid: 311ce4cd-fbdf-4ea1-a51b-5bb043abbcee
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fd47720009449d51abadd1e5f513149a83702ea3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="document-templates-and-the-documentview-creation-process"></a>Šablony dokumentů a proces tvorby v modelu dokument/zobrazení
Ke správě komplexní proces vytváření dokumentů s jejich přidružené zobrazení a oken s rámečkem, rozhraní používá dvě třídy šablony dokumentu: [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) pro aplikace SDI a [CMultiDocTemplate ](../mfc/reference/cmultidoctemplate-class.md) pro aplikace MDI. A `CSingleDocTemplate` můžete vytvořit a uložit jeden dokument jednoho typu najednou. A `CMultiDocTemplate` udržuje seznam mnoho otevřené dokumenty jednoho typu.  
  
 Některé aplikace podporují více typů dokumentů. Například aplikace může podporovat textové dokumenty a grafiky dokumenty. V takové aplikace když uživatel vybere nový příkaz v nabídce Soubor dialogového okna zobrazuje seznam možných nové typy dokument otevřít. Pro každý typ podporovaného dokumentu aplikace používá objektem template odlišné dokumentu. Následující obrázek znázorňuje konfiguraci aplikace MDI, která podporuje dva typy dokumentu a zobrazuje několik otevřené dokumenty.  
  
 ![Aplikace MDI, která má dva typy dokumentu](../mfc/media/vc387h1.gif "vc387h1")  
Aplikace MDI pomocí dvou typů dokumentů.  
  
 Šablony dokumentů jsou vytvářené a udržované pomocí objektu application. Mezi klíčové úlohy prováděné během vaší aplikace `InitInstance` funkce je vytvořit jednu nebo více šablon dokumentů odpovídající typu. Tato funkce je popsána v [vytváření šablon dokumentů](../mfc/document-template-creation.md). Objekt aplikace ukládá ukazatel na každé šablony dokumentu ve svém seznamu šablony a poskytuje rozhraní pro přidání šablony dokumentů.  
  
 Pokud potřebujete podporovat dvě nebo více typů dokumentů, musíte přidat další volání [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) pro každý typ dokumentu.  
  
 Ikona je zaregistrovaný pro každý dokument šablony založené na pozici v seznamu aplikace šablon dokumentů. Pořadí šablony dokumentu je určen podle pořadí, které byly přidány pomocí volání `AddDocTemplate`. MFC předpokládá, že na první prostředek ikona v aplikaci je ikona aplikace, další ikonu prostředků je první ikona dokumentu a tak dále.  
  
 Například šablona dokumentu je třetí tří pro aplikaci. Pokud je aplikace v indexu 3 prostředek s ikonou, že ikona je použita šablony dokumentu. Pokud ne, ikona indexem 0 je použita jako výchozí.  
  
## <a name="see-also"></a>Viz také  
 [Obecná témata MFC](../mfc/general-mfc-topics.md)   
 [Vytváření šablon dokumentů](../mfc/document-template-creation.md)   
 [Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)   
 [Vztahy mezi objekty MFC](../mfc/relationships-among-mfc-objects.md)   
 [Vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md)

