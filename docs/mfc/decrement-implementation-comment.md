---
title: --Implementační komentář | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Implementation comment in MFC source files
- comments, MFC
- MFC source files, Implementation comment
- comments, Implementation comments
ms.assetid: 4d799c07-8e71-4a6b-90ab-8282d6ff48ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89f87c33abfec7b9d055b589726639fcd741e59d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930271"
---
# <a name="-implementation-comment"></a>// implementační komentář
`// Implementation` Část je nejdůležitější část všechny deklarace třídy MFC.  
  
 Tato část je umístěno všechny podrobnosti implementace. Členské proměnné a členské funkce můžete zobrazit v této části. Všechno pod tento řádek může změnit v budoucí verzi knihovny MFC. Pokud se nelze vyhnout ho, neměli byste tedy spoléhat na níže uvedené podrobnosti `// Implementation` řádku. Kromě toho nejsou popsané členy deklarovaný pod čarou implementace, i když některé implementace je popsána v – technické poznámky. Přepsání virtuální funkce základní třídy se nacházejí v této části, bez ohledu na to, které části funkce základní třídy je definována v, protože podrobností implementace fakt, že funkce přepsání implementaci základní třídy. Obvykle jsou chráněné tito členové, ale ne vždy.  
  
 Všimněte si z `CStdioFile` seznam v části [příklad komentářů](../mfc/an-example-of-the-comments.md) , členy deklaraci níže `// Implementation` komentář může být deklarována jako **veřejné**, **chráněné**, nebo **privátní**. Byste měli používat jenom tyto členy opatrně, protože se můžou změnit v budoucnu. Deklarování skupinu členů jako **veřejné** může být nutné pro implementaci třídy knihovny fungovala správně. Však neznamená to může bezpečně použít tak deklarované členy.  
  
> [!NOTE]
>  Možná komentáře zbývající typů nad nebo pod `// Implementation` komentář. V obou případech popisují typy členů deklarovaný uvedenou pod nimi. Když se vyskytují níže `// Implementation` komentář, musí předpokládat, že členy může změnit v budoucích verzích MFC.  
  
## <a name="see-also"></a>Viz také  
 [Použití zdrojových souborů MFC](../mfc/using-the-mfc-source-files.md)   
 [Příklad komentářů](../mfc/an-example-of-the-comments.md)   
 [/ Komentář ke konstruktorům](../mfc/decrement-constructors-comment.md)   
 [Komentář k atributům](../mfc/decrement-attributes-comment.md)   
 [Komentář k operacím](../mfc/decrement-operations-comment.md)   
 [Komentář k Přepisovatelným](../mfc/decrement-overridables-comment.md)

