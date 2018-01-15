---
title: "Pomocí knihovny MFC zdrojových souborů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 930c205ffd690c190f68766f7a51c83b68ef8d2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-mfc-source-files"></a>Použití zdrojových souborů MFC
Knihovna Microsoft Foundation Class (MFC) poskytuje úplný zdrojový kód. Soubory hlaviček (.h) jsou v adresáři \atlmfc\include; implementace soubory (sada), jsou v adresáři \atlmfc\src\mfc.  
  
 Této rodině článků popisuje konvence, které MFC používá pro různé součásti každá třída, co znamená tyto komentáře a co byste měli očekávat najít v každé části komentáře k. Průvodci Visual C++ použít podobné konvence pro třídy, které pro vás vytvořil, a je pravděpodobně užitečné tyto konvence pro vlastní kód.  
  
 Je možné, že znáte **veřejné**, `protected`, a `private` klíčová slova jazyka C++. Při prohlížení soubory hlaviček MFC, zjistíte, že každá třída může mít několik každý z těchto. Například může být veřejné členské proměnné a funkce v rámci více než jednoho **veřejné** – klíčové slovo. To je proto MFC odděluje členské proměnné a funkce na základě jejich používání není typ přístupu povolena. MFC používá `private` pouze; považuje za i položky podrobnosti implementace jsou obecně chráněné a tolikrát, kolikrát se veřejné. I když se nedoporučuje. přístup k podrobnosti implementace, MFC ponechá rozhodnutí pro vás.  
  
 Ve zdrojových souborech MFC a soubory, které vytvoří Průvodce aplikací MFC zjistíte komentáře takovéto v deklaracích třídy (obvykle v tomto pořadí):  
  
 `// Constructors`  
  
 `// Attributes`  
  
 `// Operations`  
  
 `// Overridables`  
  
 `// Implementation`  
  
 Obsahuje následující témata v této rodině článků:  
  
-   [Příklad komentářů](../mfc/an-example-of-the-comments.md)  
  
-   [/ / Komentář implementace](../mfc/decrement-implementation-comment.md)  
  
-   [/ / Komentář ke konstruktorům](../mfc/decrement-constructors-comment.md)  
  
-   [/ / Komentář atributy](../mfc/decrement-attributes-comment.md)  
  
-   [/ / Komentář operací](../mfc/decrement-operations-comment.md)  
  
-   [/ / Komentář k Přepisovatelným](../mfc/decrement-overridables-comment.md)  
  
## <a name="see-also"></a>Viz také  
 [Obecná témata MFC](../mfc/general-mfc-topics.md)

