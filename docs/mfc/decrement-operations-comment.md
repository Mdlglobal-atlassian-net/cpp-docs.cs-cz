---
title: --Komentář k operacím | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee6bf4a330a5fdf1ac294157e69dab39b5f2bdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342268"
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

