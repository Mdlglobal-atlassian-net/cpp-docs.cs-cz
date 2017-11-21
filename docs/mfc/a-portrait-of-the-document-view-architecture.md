---
title: "Portrét architektury dokument zobrazení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- documents [MFC], views
- multiple views [MFC], updating from document
- document/view architecture [MFC]
- views [MFC], and user input
- documents [MFC], accessing data from view
- views [MFC], updating
- input [MFC], view class
- documents [MFC], multiple views
- document/view architecture [MFC], accessing data from view
- document/view architecture [MFC], about document/view architecture
- views [MFC], accessing document data from
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7e79222f908a7b71e81033fb34517834987e6590
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="a-portrait-of-the-documentview-architecture"></a>Portrét architektury dokument/zobrazení
V typické aplikaci MFC jsou spárován dokumentů a zobrazení. Data jsou uložena v dokumentu, ale zobrazení obsahuje privilegovaný přístup k datům. Oddělení dokumentu ze zobrazení odděluje úložiště a údržby dat od jeho zobrazení.  
  
## <a name="gaining-access-to-document-data-from-the-view"></a>Získání přístupu k dokumentu Data ze zobrazení  
 Zobrazení přistupuje k jeho dokumentu dat buď pomocí [GetDocument](../mfc/reference/cview-class.md#getdocument) funkce, která vrací ukazatel k dokumentu nebo tím, že zobrazení třídy jazyka C++ `friend` třídy dokumentu. Zobrazení získat data, když je připraven k vykreslení nebo jinak manipulaci s použije jeho přístup k datům.  
  
 Například ze zobrazení [OnDraw –](../mfc/reference/cview-class.md#ondraw) – členská funkce zobrazení používá **GetDocument** k získání ukazatele dokumentu. Potom použije tento ukazatel pro přístup `CString` – datový člen v dokumentu. Zobrazení předá řetězec, který má `TextOut` funkce. Kód v tomto příkladu najdete v sekci [kreslení v zobrazení](../mfc/drawing-in-a-view.md).  
  
## <a name="user-input-to-the-view"></a>Uživatelský vstup do zobrazení  
 Zobrazení může také interpretovat kliknutí myši v rámci samotné jako výběr nebo úprava dat. Podobně se může vyhodnotit stisknutí kláves jako vstupní data nebo úpravy. Předpokládejme, že uživatel zadá řetězec v zobrazení, která spravuje text. Zobrazení získá ukazatel k dokumentu a používá ukazatele k předání nová data v dokumentu, který ukládá v některé datové struktury.  
  
## <a name="updating-multiple-views-of-the-same-document"></a>Aktualizace více zobrazení do jednoho dokumentu  
 V aplikaci s více zobrazení do jednoho dokumentu – například rozděleném okně v textovém editoru – zobrazení nejprve předá nová data do dokumentu. Potom zavolá dokumentu [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) členská funkce, které sděluje všechna zobrazení dokumentu, který má aktualizovat sami, která znázorňuje nová data. Provádí synchronizaci zobrazení.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Výhody architektury dokument/zobrazení](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [Alternativy k architektuře dokument/zobrazení](../mfc/alternatives-to-the-document-view-architecture.md)  
  
## <a name="see-also"></a>Viz také  
 [Document/View – architektura](../mfc/document-view-architecture.md)

