---
title: Vytváření nových dokumentů, oken a zobrazení
ms.date: 11/19/2018
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
ms.openlocfilehash: aa1c58b02df92d79ca9915032b97fb5c0e2eaffc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371666"
---
# <a name="creating-new-documents-windows-and-views"></a>Vytváření nových dokumentů, oken a zobrazení

Následující obrázky poskytují přehled procesu vytváření dokumentů, zobrazení a oken rámců. Další články, které se zaměřují na zúčastněné objekty poskytují další podrobnosti.

Po dokončení tohoto procesu existují spolupracující objekty a ukládají ukazatele na sebe. Následující obrázky zobrazily pořadí, ve kterém jsou objekty vytvořeny. Můžete sledovat pořadí od obrázku k obrázku.

![Posloupnost pro vytvoření dokumentu](../mfc/media/vc387l1.gif "Posloupnost pro vytvoření dokumentu") <br/>
Pořadí při vytváření dokumentu

![Sekvence vytváření okna rámce](../mfc/media/vc387l2.png "Sekvence vytváření okna rámce") <br/>
Pořadí při vytváření okna rámce

![Posloupnost pro vytvoření zobrazení](../mfc/media/vc387l3.gif "Posloupnost pro vytvoření zobrazení") <br/>
Pořadí při vytváření zobrazení

Informace o tom, jak rozhraní inicializuje nové objekty document, zobrazení a okna rámce, naleznete v tématu třídy [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)a [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) v odkazu knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny. Viz také [technická poznámka 22](../mfc/tn022-standard-commands-implementation.md), která vysvětluje procesy vytváření a inicializace dále v rámci diskuse o standardní příkazy rozhraní pro **nové** a **otevřené** položky v nabídce **Soubor.**

## <a name="initializing-your-own-additions-to-these-classes"></a><a name="_core_initializing_your_own_additions_to_these_classes"></a>Inicializace vlastních přírůstků do těchto tříd

Předchozí obrázky také naznačují body, ve kterých můžete přepsat členské funkce k inicializaci objektů aplikace. Přepsání `OnInitialUpdate` ve třídě zobrazení je nejlepším místem pro inicializaci zobrazení. K `OnInitialUpdate` volání dojde ihned po vytvoření okna rámce a zobrazení v okně rámce je připojeno k jeho dokumentu. Pokud je například zobrazení zobrazení mj. `CScrollView` (odvozené spíše než `CView`z ) , měli `OnInitialUpdate` byste nastavit velikost zobrazení na základě velikosti dokumentu v přepsání. (Tento proces je popsán v popisu třídy [CScrollView](../mfc/reference/cscrollview-class.md).) Můžete přepsat `CDocument` členské funkce `OnNewDocument` `OnOpenDocument` a poskytnout inicializaci dokumentu specifickou pro aplikaci. Obvykle je nutné přepsat oba, protože dokument lze vytvořit dvěma způsoby.

Ve většině případů by mělo přepsání volat verzi základní třídy. Další informace naleznete v pojmenovaných členských funkcích tříd [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md)a [CWinApp](../mfc/reference/cwinapp-class.md) v odkazu knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny.

## <a name="see-also"></a>Viz také

[Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Vytváření šablon dokumentů](../mfc/document-template-creation.md)<br/>
[Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)<br/>
[Vztahy mezi objekty MFC](../mfc/relationships-among-mfc-objects.md)
