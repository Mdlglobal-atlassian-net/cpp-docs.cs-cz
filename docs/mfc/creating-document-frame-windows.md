---
title: "Vytváření oken s rámečkem dokumentu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 25780092d11580225bef325c53e99c82263267b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-document-frame-windows"></a>Vytváření oken s rámečkem v dokumentu
[Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md) ukazuje, jak [CDocTemplate](../mfc/reference/cdoctemplate-class.md) objekt orchestruje vytváření oken s rámečkem, dokumentů a zobrazení a jejich připojením všechny společně. Tři [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) argumenty, které mají `CDocTemplate` konstruktor zadejte oken s rámečkem, dokumentů a zobrazení třídy, které šablona dokumentu vytvoří dynamicky v reakci na příkazy uživatele jako nový příkaz v souboru nabídky nebo v nabídce okna MDI příkaz nové okno. Šablona dokumentu ukládá tyto informace pro pozdější použití při vytváření okna rámce pro zobrazení a dokumentu.  
  
 Pro [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) mechanismus fungovala správně, vaše odvozené třídy oken s rámečkem je třeba deklarovat s [DECLARE_DYNCREATE –](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) makro. Důvodem je, že rozhraní je potřeba vytvořit dokument pomocí mechanismu dynamické vytváření třídy oken s rámečkem `CObject`.  
  
 Když uživatel vybere příkaz, který vytvoří dokument, volá framework při šablona dokumentu vytvořit objekt dokumentu, jeho zobrazení a rámec okna, který se zobrazí zobrazení. Při vytváření okně s rámečkem v dokumentu, vytvoří šablona dokumentu příslušná třída objektu – třída odvozená z [CFrameWnd](../mfc/reference/cframewnd-class.md) pro aplikace SDI nebo z [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) pro MDI aplikace. Rozhraní framework pak zavolá metodu objektu oken s rámečkem [loadframe –](../mfc/reference/cframewnd-class.md#loadframe) – členská funkce získat informace o vytvoření z prostředků a k vytvoření období systému Windows. Rozhraní připojí k objektu oken s rámečkem popisovač okna. Potom vytvoří zobrazení jako podřízeného okna rámce okna dokumentu.  
  
 Buďte opatrní při rozhodování, [kdy je třeba inicializovat](../mfc/when-to-initialize-cwnd-objects.md) vaše `CWnd`-odvozené objektu.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Odvození třídy z objektu CObject (jeho dynamického vytváření mechanismus)](../mfc/deriving-a-class-from-cobject.md)  
  
-   [Vytváření dokumentů/zobrazení (šablony a vytvoření oken s rámečkem)](../mfc/document-view-creation.md)  
  
-   [Zničení oken s rámečkem](../mfc/destroying-frame-windows.md)  
  
## <a name="see-also"></a>Viz také  
 [Použití oken s rámečkem](../mfc/using-frame-windows.md)

