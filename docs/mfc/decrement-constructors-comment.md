---
title: "--/ Komentář ke konstruktorům | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1f6425252df34936d4ba3c9013664205b0038d82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

