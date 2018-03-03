---
title: "Zápis obslužné rutiny výjimek | Microsoft Docs"
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
- structured exception handling [C++], exception handlers
- exception handling [C++], exception handlers
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52d102f29a015ea077e9ec94a9f1ed63f44f7c1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="writing-an-exception-handler"></a>Zápis obslužné rutiny výjimek
Obslužné rutiny výjimek se obvykle používají jako reakce na konkrétní chyby. Pomocí syntaxe zpracování výjimek lze odfiltrovat všechny výjimky kromě těch, u kterých víte, jak se mají zpracovat. Ostatní výjimky by měly být předány jiné obslužné rutině (případně v knihovně modulu runtime nebo operačního systému) napsané pro vyhledání těchto specifických výjimek.  
  
 Obslužné rutiny výjimek používají příkaz try-except.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Try-except – příkaz](../cpp/try-except-statement.md)  
  
-   [Zápis filtru výjimek](../cpp/writing-an-exception-filter.md)  
  
-   [Vyvolávání výjimek softwaru](../cpp/raising-software-exceptions.md)  
  
-   [Výjimky hardwaru](../cpp/hardware-exceptions.md)  
  
-   [Omezení obslužných rutin výjimek](../cpp/restrictions-on-exception-handlers.md)  
  
## <a name="see-also"></a>Viz také  
 [Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)