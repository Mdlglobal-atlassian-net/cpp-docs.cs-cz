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
ms.openlocfilehash: 25b6ebff4108b47e70b34aa6d83293bede78ee97
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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

