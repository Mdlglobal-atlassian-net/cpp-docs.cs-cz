---
title: Třídy šablony dokumentu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.document
dev_langs:
- C++
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9958484633dd736426fc91321d0964abf0ad7e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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

