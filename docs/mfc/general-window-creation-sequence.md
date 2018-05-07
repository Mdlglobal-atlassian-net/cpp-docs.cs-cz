---
title: Obecná posloupnost vytvoření okna | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75a9c6ecf6516adceda845dadd4f0313ae605f0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="general-window-creation-sequence"></a>Obecná posloupnost vytvoření okna
Při vytváření okna vlastní, jako je například podřízená okna rozhraní používá mnohem stejný postup, který popsané v [Document/View – vytvoření](../mfc/document-view-creation.md).  
  
 Třídy oken poskytované společnosti využívají MFC [dvoufázová konstrukce](../mfc/one-stage-and-two-stage-construction-of-objects.md). To znamená během k vyvolání C++ **nové** operátor konstruktoru přiděluje a inicializuje objekt C++ ale nevytvoří odpovídající období systému Windows. Je následně provést voláním [vytvořit](../mfc/reference/cwnd-class.md#create) členské funkce objektu okno.  
  
 **Vytvořit** – členská funkce umožňuje období systému Windows a ukládá jeho `HWND` ve členovi objektu C++ veřejná data [m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd). **Vytvoření** poskytuje úplnou flexibilitu nad vytvoření parametry. Před voláním **vytvořit**, můžete chtít zaregistrovat třídy oken s globální funkce [afxregisterwndclass –](../mfc/reference/application-information-and-management.md#afxregisterwndclass) Chcete-li nastavit ikonu a třída styl rámečku.  
  
 Okna s rámečkem, můžete použít [loadframe –](../mfc/reference/cframewnd-class.md#loadframe) – členská funkce místo **vytvořit**. `LoadFrame` Díky období systému Windows pomocí méně parametrů. Získá mnoho výchozí hodnoty z prostředků, včetně titulku rámečku, ikona, tabulka akcelerátoru a nabídky.  
  
> [!NOTE]
>  Vaše ikonu, tabulky akcelerátorů a prostředků nabídky musí mít ID společné prostředků, například **IDR_MAINFRAME**, mohly loadframe – načteny.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Objekty oken](../mfc/window-objects.md)  
  
-   [Registrace tříd"oken"](../mfc/registering-window-classes.md)  
  
-   [Zničení objektů oken](../mfc/destroying-window-objects.md)  
  
-   [Vytváření dokumentů, oken s rámečkem](../mfc/creating-document-frame-windows.md)  
  
## <a name="see-also"></a>Viz také  
 [Vytváření oken](../mfc/creating-windows.md)

