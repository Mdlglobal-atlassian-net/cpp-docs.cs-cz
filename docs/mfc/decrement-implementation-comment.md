---
title: "--Implementační komentář | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Implementation comment in MFC source files
- comments, MFC
- MFC source files, Implementation comment
- comments, Implementation comments
ms.assetid: 4d799c07-8e71-4a6b-90ab-8282d6ff48ce
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 437b091b2237c7219a0afeee46d78164751e6d3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="-implementation-comment"></a>// implementační komentář
`// Implementation` Část je nejdůležitější část všechny deklarace třídy MFC.  
  
 Tato část je umístěno všechny podrobnosti implementace. Členské proměnné a členské funkce můžete zobrazit v této části. Všechno pod tento řádek může změnit v budoucí verzi knihovny MFC. Pokud se nelze vyhnout ho, neměli byste tedy spoléhat na níže uvedené podrobnosti `// Implementation` řádku. Kromě toho nejsou popsané členy deklarovaný pod čarou implementace, i když některé implementace je popsána v – technické poznámky. Přepsání virtuální funkce základní třídy se nacházejí v této části, bez ohledu na to, které části funkce základní třídy je definována v, protože podrobností implementace fakt, že funkce přepsání implementaci základní třídy. Obvykle jsou chráněné tito členové, ale ne vždy.  
  
 Všimněte si z `CStdioFile` výpis pod [příklad komentářů](../mfc/an-example-of-the-comments.md) jestli členy deklaruje níže `// Implementation` komentář může být deklarována jako **veřejné**, `protected`, nebo `private`. Byste měli používat jenom tyto členy opatrně, protože se můžou změnit v budoucnu. Deklarování skupinu členů jako **veřejné** může být nutné pro implementaci třídy knihovny fungovala správně. Však neznamená to může bezpečně použít tak deklarované členy.  
  
> [!NOTE]
>  Možná komentáře zbývající typů nad nebo pod `// Implementation` komentář. V obou případech popisují typy členů deklarovaný uvedenou pod nimi. Když se vyskytují níže `// Implementation` komentář, musí předpokládat, že členy může změnit v budoucích verzích MFC.  
  
## <a name="see-also"></a>Viz také  
 [Použití zdrojových souborů MFC](../mfc/using-the-mfc-source-files.md)   
 [Příklad komentářů](../mfc/an-example-of-the-comments.md)   
 [/ Komentář ke konstruktorům](../mfc/decrement-constructors-comment.md)   
 [Komentář k atributům](../mfc/decrement-attributes-comment.md)   
 [Komentář k operacím](../mfc/decrement-operations-comment.md)   
 [Komentář k Přepisovatelným](../mfc/decrement-overridables-comment.md)

