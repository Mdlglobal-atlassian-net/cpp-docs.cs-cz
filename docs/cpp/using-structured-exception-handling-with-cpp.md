---
title: "Používání strukturovaného zpracování výjimek s C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, mixed with SEH
- structured exception handling [C++], with C++ exception handling
ms.assetid: ec34b528-8c26-4429-b24a-6a68553aaa91
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db5d067a391512d56a2d01ce3052ac3fab061f28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-structured-exception-handling-with-c"></a>Používání strukturovaného zpracování výjimek s jazykem C++
Strukturované zpracování výjimek popsaných v těchto článcích funguje s C a C++ zdrojové soubory. Však není speciálně pro jazyk C++ a nedoporučuje se používat. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Navíc je flexibilnější, zpracování mechanismus výjimek C++, v tom, že ho můžete zpracování výjimek libovolného typu.  
  
 Microsoft C++ teď podporuje model, založené na standardní C++ ANSI zpracování výjimek C++. Tento mechanismus automaticky zpracovává likvidace objektů místní během unwind zásobníku. Pokud píšete odolné proti chybám C++ – kód, a chcete implementovat výjimek, důrazně doporučujeme použít C++ zpracování výjimek, místo strukturované zpracování výjimek. (Všimněte si, že i když C++ compiler podporuje strukturovaného zpracování konstrukce, jak je popsáno v těchto článcích výjimek, standardní kompilátor jazyka C nepodporuje zpracování syntaxe výjimek C++.) Podrobné informace o zpracovávání výjimek v jazyce C++ najdete v tématu [zpracování výjimek C++](../cpp/cpp-exception-handling.md) a *poznámkou C++ referenční příručce* Margaret Ellis a Bjarnem Stroustrupem.  
  
## <a name="see-also"></a>Viz také  
 [Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)