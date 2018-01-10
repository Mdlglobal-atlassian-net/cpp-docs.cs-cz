---
title: "Použití objektů CObject | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CObject
dev_langs: C++
helpviewer_keywords:
- examples [MFC], CObject
- root base class for MFC
- derived classes [MFC], from CObject
- MFC, base class
- CObject class [MFC]
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 17bffb412975cfc6a97eae8b30aff2514a2e1d93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-cobject"></a>Použití objektů CObject
[CObject](../mfc/reference/cobject-class.md) je kořenová základní třída pro většinu z Microsoft Foundation Class Library (MFC). `CObject` Třída obsahuje mnoho užitečných funkcí, které chcete zahrnout do vlastní objekty programu, včetně podpory serializace, run-time třída informace a výstup diagnostiky objektu. Pokud odvozujete třídě z `CObject`, třídě může zneužít tyto `CObject` funkce.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat  
  
-   [Odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md)  
  
-   [Přidat podporu pro run-time třída informace, dynamických a serializace Moje odvozené třídy](../mfc/specifying-levels-of-functionality.md)  
  
-   [Přístup k informacím run-time třída](../mfc/accessing-run-time-class-information.md)  
  
-   [Vytváření objektů dynamicky](../mfc/dynamic-object-creation.md)  
  
-   [Dump data objektu k diagnostickým účelům](http://msdn.microsoft.com/en-us/727855b1-5a83-44bd-9fe3-f1d535584b59)  
  
-   Ověření objektu vnitřní stav (viz [assert_valid – MFC a CObject::AssertValid](http://msdn.microsoft.com/en-us/7654fb75-9e9a-499a-8165-0a96faf2d5e6))  
  
-   [Mají třídu serializovat sama sebe do trvalého úložiště](../mfc/serialization-in-mfc.md)  
  
-   Podívejte se do seznamu [CObject nejčastější dotazy](../mfc/cobject-class-frequently-asked-questions.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../mfc/mfc-concepts.md)   
 [Obecná témata MFC](../mfc/general-mfc-topics.md)   
 [Struktura CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)   
 [Soubory](../mfc/files-in-mfc.md)   
 [Serializace](../mfc/serialization-in-mfc.md)

