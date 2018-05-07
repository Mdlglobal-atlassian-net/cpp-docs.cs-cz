---
title: --/ Komentář ke konstruktorům | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors comment
- declarations, constructors
- MFC source files, Constructors comment
- declaring constructors, code comments
- comments, MFC
- comments, constructors comment
- constructors [MFC], declaring
- instance constructors, code comments
ms.assetid: f400774e-ba85-49ed-85b7-70ef2f7dcb2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71b78e74b4b8d974fceaf5f854c9890cd7cdd1a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-constructors-comment"></a>// Komentář ke konstruktorům
`// Constructors` Části deklarace tříd MFC deklaruje konstruktory (v tom smyslu, C++) a také všechny funkce inicializace vyžadované skutečně použití objektu. Například `CWnd::Create` je v části konstruktory, protože před použitím `CWnd` objektu, se musí "plně zkonstruovat" tak, že první volání konstruktoru C++ a pak volání **vytvořit** funkce. Tito členové jsou obvykle veřejné.  
  
 Například třídy `CStdioFile` má tři konstruktory, z nichž jeden je uveden v seznamu pod [příklad komentářů](../mfc/an-example-of-the-comments.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití zdrojových souborů MFC](../mfc/using-the-mfc-source-files.md)   
 [Implementační komentář](../mfc/decrement-implementation-comment.md)   
 [Komentář k atributům](../mfc/decrement-attributes-comment.md)   
 [Komentář k operacím](../mfc/decrement-operations-comment.md)   
 [Komentář k Přepisovatelným](../mfc/decrement-overridables-comment.md)

