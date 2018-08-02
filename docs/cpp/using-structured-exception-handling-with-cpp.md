---
title: Používání strukturovaného zpracování výjimek s C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, mixed with SEH
- structured exception handling [C++], with C++ exception handling
ms.assetid: ec34b528-8c26-4429-b24a-6a68553aaa91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 363dd00cd5f4e177ea32a109cf5f56a1f3c6cb29
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461722"
---
# <a name="using-structured-exception-handling-with-c"></a>Používání strukturovaného zpracování výjimek s jazykem C++
Strukturované zpracování výjimek je popsáno v těchto článcích funguje se zdrojovými soubory C a C++. Však není výslovně navrženo pro C++ a nedoporučuje se používat. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Mechanismus zpracování výjimek jazyka C++ je také více flexibilní, jelikož dokáže zpracovat výjimky libovolného typu.  
  
 Microsoft C++ teď podporuje model založený na standardu ANSI C++ zpracování výjimek jazyka C++. Tento mechanismus automaticky zpracovává zničení místní objekty během odvíjení zásobníku. Pokud píšete odolné proti chybám kódu jazyka C++ a chcete k implementaci zpracování výjimek, důrazně doporučujeme používat místo strukturované zpracování výjimek zpracování výjimek jazyka C++. (Všimněte si, že i když kompilátor C++ podporuje zpracování konstrukce, jak je popsáno v těchto článcích strukturovaných výjimek, standardní kompilátor jazyka C nepodporuje syntaxe zpracování výjimek jazyka C++.) Podrobné informace o zpracování výjimek jazyka C++, naleznete v tématu [zpracování výjimek jazyka C++](../cpp/cpp-exception-handling.md) a *referenčním manuálu C++ s poznámkami* od Margaret Ellis a Bjarne Stroustrup.  
  
## <a name="see-also"></a>Viz také:  
 [Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)