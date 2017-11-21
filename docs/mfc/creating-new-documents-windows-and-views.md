---
title: "Vytváření nových dokumentů, oken a zobrazení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MDI [MFC], creating windows
- window objects [MFC], creating
- objects [MFC], creating document objects
- MFC default objects
- frame windows [MFC], creating
- windows [MFC], MDI
- MFC, documents
- view objects [MFC], creating
- windows [MFC], creating
- overriding, default view behavior
- views [MFC], initializing
- customizing MFC default objects
- MFC, frame windows
- MFC, views
- MDI [MFC], frame windows
- child windows [MFC], creating MDI
- view objects [MFC]
- document objects [MFC], creating
- MFC default objects [MFC], customizing
- views [MFC], overriding default behavior
- initializing views [MFC]
ms.assetid: 88aa1f5f-2078-4603-b16b-a2b4c7b4a2a3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d5bf77d2d14e8dda2f1eb02ac35d0ccaf81a8617
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-new-documents-windows-and-views"></a>Vytváření nových dokumentů, oken a zobrazení
Následující obrázky poskytují přehled o procesu vytvoření pro dokumenty, zobrazení a oken s rámečkem. Další články, které soustředit na zúčastněných objekty poskytnout další podrobnosti.  
  
 Po dokončení tohoto procesu spolupracující objekty existují a uložení ukazatele na sebe navzájem. Následující obrázky zobrazit pořadí, ve kterém jsou vytvořeny objekty. Můžete provést sekvenci obrázek z obrázku.  
  
 ![Pořadí pro vytvoření dokumentu](../mfc/media/vc387l1.gif "vc387l1")  
Pořadí při vytváření dokumentu  
  
 ![Posloupnost vytvoření okna s rámečkem](../mfc/media/vc387l2.png "vc387l2")  
Pořadí při vytváření oken s rámečkem  
  
 ![Pořadí pro vytvoření zobrazení](../mfc/media/vc387l3.gif "vc387l3")  
Pořadí při vytváření zobrazení  
  
 Informace o tom, jak rozhraní inicializuje nový dokument, zobrazení a oken s rámečkem objekty, najdete v tématu třídy [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), a [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) v referenční příručka knihovny MFC. Také najdete v části [Technická poznámka 22](../mfc/tn022-standard-commands-implementation.md), která vysvětluje další procesy vytváření a inicializace pod jeho diskuzi o rozhraní framework pro standardní příkazy `New` a **otevřete** položky na **Souboru** nabídky.  
  
##  <a name="_core_initializing_your_own_additions_to_these_classes"></a>Inicializace vlastní doplňky tyto třídy  
 Předchozí údaje také navrhnout body, ve kterém můžete přepsat členské funkce třeba inicializovat objekty vaší aplikace. Přepsání `OnInitialUpdate` v zobrazení třída je nejlepší místo k inicializaci zobrazení. `OnInitialUpdate` Ihned po je vytvořen okně s rámečkem a zobrazení v okně s rámečkem je připojen k jeho dokumentu dojde k volání. Například, pokud je zobrazení posuňte zobrazení (odvozený od `CScrollView` místo `CView`), měli byste nastavit velikost zobrazení na základě velikosti dokumentu v vaší `OnInitialUpdate` přepsat. (Tento proces je popsán v popisu třídy [CScrollView](../mfc/reference/cscrollview-class.md).) Je možné přepsat **CDocument** členské funkce `OnNewDocument` a `OnOpenDocument` zajistit specifické pro aplikaci inicializace dokumentu. Obvykle je nutné přepsat obě vzhledem k tomu, že dokument můžete vytvořit dvěma způsoby.  
  
 Ve většině případů přepsání by měly volat základní třída verze. Další informace najdete v tématu s názvem členské funkce tříd [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), a [CWinApp](../mfc/reference/cwinapp-class.md) v prostředí MFC Referenční příručka knihovny.  
  
## <a name="see-also"></a>Viz také  
 [Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Vytváření šablon dokumentů](../mfc/document-template-creation.md)   
 [Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)   
 [Vztahy mezi objekty MFC](../mfc/relationships-among-mfc-objects.md)

