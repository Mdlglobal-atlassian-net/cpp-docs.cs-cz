---
title: "Třídy šablony dokumentu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.document
dev_langs: C++
helpviewer_keywords: document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fe4a74470371f162a9ff01036a66a52f18b314c7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="document-template-classes"></a>Třídy šablony dokumentu
Objekty šablony dokumentu koordinaci vytvoření dokumentu, zobrazení a rámečku okno objekty, když nový dokument nebo není vytvořená zobrazení.  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md)  
 Základní třída pro šablony dokumentů. Tato třída se nikdy používat přímo; Místo toho použijte jeden z jiné třídy šablony dokumentu odvozen z této třídy.  
  
 [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)  
 Šablona pro dokumenty v rozhraní více dokumentů (MDI). Aplikace MDI mohou mít více dokumentů, otevřete v čase.  
  
 [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)  
 Šablona pro dokumenty v rozhraní s jedním dokumentem (SDI). Aplikace SDI mít pouze jeden dokument otevřít v čase.  
  
## <a name="related-class"></a>Související – třída  
 [CCreateContext](../mfc/reference/ccreatecontext-structure.md)  
 Struktury předaná šablony dokumentu na vytvoření oken funkce pro koordinaci vytváření objektů dokumentů, zobrazení a oken s rámečkem.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)
