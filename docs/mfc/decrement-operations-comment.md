---
title: "--Komentář k operacím | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 53d2470e0be0ca314da8486d74d8fc618e134c35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="-operations-comment"></a>// Komentář k operacím
`// Operations` Část deklarace tříd MFC obsahuje členské funkce, které lze volat na objekt, chcete-li provádět následující akce nebo provádět akce (provádění operací). Tyto funkce jsou obvykle jinou hodnotu než**const** protože mají obvykle vedlejší účinky. Mohou být virtuální nebo nevirtuální podle potřeb třídy. Tito členové jsou obvykle veřejné.  
  
 V ukázce výpis z třídy `CStdioFile`v [příklad komentářů](../mfc/an-example-of-the-comments.md), seznam obsahuje dva členské funkce v rámci tohoto komentáře: `ReadString` a `WriteString`.  
  
 Stejně jako u atributů, může být další rozdělena operace.  
  
## <a name="see-also"></a>Viz také  
 [Použití zdrojových souborů MFC](../mfc/using-the-mfc-source-files.md)   
 [Příklad komentářů](../mfc/an-example-of-the-comments.md)   
 [Implementační komentář](../mfc/decrement-implementation-comment.md)   
 [/ Komentář ke konstruktorům](../mfc/decrement-constructors-comment.md)   
 [Komentář k atributům](../mfc/decrement-attributes-comment.md)   
 [Komentář k Přepisovatelným](../mfc/decrement-overridables-comment.md)

