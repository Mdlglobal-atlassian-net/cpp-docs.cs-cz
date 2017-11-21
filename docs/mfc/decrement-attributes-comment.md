---
title: "– Atributy komentář | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- comments, Attributes
- Attributes comment in MFC source files
- MFC source files, Attributes comment
- public attributes comment
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c93d27cb5a9c6ef83f5b4f027d0e54cbe69a6bbd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="-attributes-comment"></a>// Komentář k atributům
`// Attributes` Deklarace tříd MFC obsahuje veřejné atributy (nebo vlastností) objektu. Obvykle jde členské proměnné nebo funkce Get/Set. Funkce "Get" a "Set" může nebo nemusí být virtuální. Funkce "Get" jsou obvykle **const**, protože ve většině případů nejsou žádné vedlejší účinky. Tito členové jsou obvykle veřejné; atributy chráněného a privátní se většinou nacházejí v oddíle implementation.  
  
 V ukázce výpis z třídy `CStdioFile`v části [příklad komentářů](../mfc/an-example-of-the-comments.md), seznam obsahuje jeden členské proměnné `m_pStream`. Třída `CDC` uvádí téměř 20 členy v rámci tohoto komentáře.  
  
> [!NOTE]
>  Velké třídy, jako například `CDC` a `CWnd`, může mít mnoho členů, které jednoduše výpis všech atributů v jedné skupině mnohem pro přehlednost nemohli přidat. V takových případech knihovny tříd používá jiné komentáře jako záhlaví pro další zobrazit členy. Například `CDC` používá `// Device-Context Functions`, `// Drawing Tool Functions`, `// Drawing Attribute Functions`a další. Skupiny, které představují atributy bude postupovat podle obvyklé syntaxe popsané výše. Mít mnoho OLE – třídy implementaci části s názvem `// Interface Maps`.  
  
## <a name="see-also"></a>Viz také  
 [Použití zdrojových souborů MFC](../mfc/using-the-mfc-source-files.md)   
 [Příklad komentářů](../mfc/an-example-of-the-comments.md)   
 [Implementační komentář](../mfc/decrement-implementation-comment.md)   
 [/ Komentář ke konstruktorům](../mfc/decrement-constructors-comment.md)   
 [Komentář k operacím](../mfc/decrement-operations-comment.md)   
 [Komentář k Přepisovatelným](../mfc/decrement-overridables-comment.md)

