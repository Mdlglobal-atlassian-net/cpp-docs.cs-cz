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
ms.openlocfilehash: 3d4ca55a9bff6ec42643db745896a2cea96dcefb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242607"
---
# <a name="creating-new-documents-windows-and-views"></a>Vytváření nových dokumentů, oken a zobrazení

Na následujících obrázcích poskytují přehled o procesu vytváření pro dokumenty, zobrazení a oken s rámečkem. Další články, které se soustředí na zúčastněných objekty poskytnout další podrobnosti.

Po dokončení tohoto procesu spolupracující objekty existují a uložte ukazatele na sebe navzájem. Následující obrázky znázorňují pořadí, ve kterém jsou vytvořeny objekty. Můžete postupovat podle pořadí z obrázku na obrázek.

![Pořadí pro vytvoření dokumentu](../mfc/media/vc387l1.gif "pořadí pro vytvoření dokumentu") <br/>
Pořadí při vytváření dokumentu

![Posloupnost vytvoření okna rámce](../mfc/media/vc387l2.png "posloupnost vytvoření okna rámce") <br/>
Posloupnost vytvoření okna rámce

![Pořadí pro vytvoření zobrazení](../mfc/media/vc387l3.gif "pořadí pro vytvoření zobrazení") <br/>
Pořadí při vytváření zobrazení

Informace o tom, jak rozhraní inicializuje nového dokumentu, zobrazení a oken s rámečkem objektů, naleznete v tématu třídy [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), a [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) v odkazu knihovny MFC. Viz také [Technická poznámka 22](../mfc/tn022-standard-commands-implementation.md), která vysvětluje v rámci jeho diskuze v rámci standardní příkazy pro další procesy vytváření a inicializace **nový** a **otevřete** položky na **souboru** nabídky.

##  <a name="_core_initializing_your_own_additions_to_these_classes"></a> Inicializace vlastní doplňky tyto třídy

Na předchozích obrázcích také navrhnout body, na které můžete přepsat členské funkce, třeba inicializovat objekty vaší aplikace. Přepsání `OnInitialUpdate` v zobrazení tříd je nejlepším místem k zahájení zobrazení. `OnInitialUpdate` Ihned po vytvoření okna rámce a zobrazení v okně rámce je připojena k jeho dokumentu dojde k volání. Například, pokud je zobrazení posuvníky zobrazení (odvozený od `CScrollView` spíše než `CView`), byste měli nastavit velikost zobrazení na základě velikosti dokumentu ve vaší `OnInitialUpdate` přepsat. (Tento proces je popsán v popisu třídy [cscrollview –](../mfc/reference/cscrollview-class.md).) Je možné přepsat `CDocument` členské funkce `OnNewDocument` a `OnOpenDocument` poskytnout specifické pro aplikaci inicializace dokumentu. Obvykle je nutné přepsat obě vzhledem k tomu, že dokument můžete vytvořit dvěma způsoby.

Ve většině případů by měly volat přepsání verze základní třídy. Další informace najdete v tématu s názvem členské funkce tříd [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), a [CWinApp](../mfc/reference/cwinapp-class.md) v MFC Referenční dokumentace ke knihovně.

## <a name="see-also"></a>Viz také:

[Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Vytváření šablon dokumentů](../mfc/document-template-creation.md)<br/>
[Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)<br/>
[Vztahy mezi objekty MFC](../mfc/relationships-among-mfc-objects.md)
