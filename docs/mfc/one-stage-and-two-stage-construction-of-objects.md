---
title: Jednofázová a dvoufázová konstrukce objektů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c53f99932887acad4d2eab5c15ed73b66b359fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Jednofázová a dvoufázová konstrukce objektů
Máte možnost volby mezi dvěma metody pro vytváření grafických objektů, jako je například pera a štětce:  
  
-   *Jednofázová konstrukce*: konstrukce a inicializovat objekt v jediném kroku, a to vše pomocí konstruktoru.  
  
-   *Dvoufázová konstrukce*: konstrukce a inicializovat objekt ve dvou samostatných fázích. Konstruktoru vytvoří objekt a inicializační funkce inicializaci.  
  
 Dvoufázová konstrukce je vždy bezpečnější. V jednofázová konstrukce může konstruktoru vyvolat výjimku, pokud zadáte nesprávné argumenty nebo selhání přidělení paměti. Tohoto problému je zabránit dvoufázová konstrukce, i když jste zkontrolujte selhání. V obou případech zničení objekt je stejný postup.  
  
> [!NOTE]
>  Tyto postupy platí pro vytváření všechny objekty, pouze grafické objekty.  
  
## <a name="example-of-both-construction-techniques"></a>Příklad obě tyto metody konstrukce  
 Následující příklad stručný ukazuje obě metody vytváření objekt pera:  
  
 [!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Grafické objekty](../mfc/graphic-objects.md)  
  
-   [Výběr grafického objektu v kontextu zařízení](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [Kontexty zařízení](../mfc/device-contexts.md)  
  
-   [Kreslení v zobrazení](../mfc/drawing-in-a-view.md)  
  
## <a name="see-also"></a>Viz také  
 [Grafické objekty](../mfc/graphic-objects.md)

