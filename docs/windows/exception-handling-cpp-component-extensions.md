---
title: "Výjimka zpracování (rozšíření komponent C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- structured exception handling, managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- managed exceptions
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: aa42bfc67a94ed4e25045dc6656651a7b9bd645e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="exception-handling--c-component-extensions"></a>Zpracování výjimek (rozšíření komponent C++)
Aplikace, kompilovat s **/ZW** – možnost kompilátoru nebo **/CLR** – možnost kompilátoru používejte *výjimky* ke zpracování neočekávaným chybám při spuštění programu. Následující témata popisují zpracování výjimek v buď C + +/ CX nebo C + +/ CLI aplikace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Základní koncepce při práci se spravovanými výjimkami](../dotnet/basic-concepts-in-using-managed-exceptions.md)  
 Popisuje vyvolání výjimky a pomocí `try` / `catch` bloky.  
  
 [Rozdíly v chování zpracování výjimek v režimu kompilace/CLR](../dotnet/differences-in-exception-handling-behavior-under-clr.md)  
 Popisuje rozdíly od standardní chování zpracování výjimek jazyka C++.  
  
 [Nakonec](../dotnet/finally.md)  
 Popisuje postup použití finally – klíčové slovo.  
  
 [Postupy: definování a instalace globální obslužné rutiny výjimek](../dotnet/how-to-define-and-install-a-global-exception-handler.md)  
 Ukazuje, jak neošetřených výjimek, se dají zachytit.  
  
 [Postupy: zachycení výjimek v nativním kódu vyvolaných z prostředí MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)  
 Popisuje, jak zachytit výjimky CLR a C++ v nativním kódu.  
  
 [Postupy: definování a instalace globální obslužné rutiny výjimek](../dotnet/how-to-define-and-install-a-global-exception-handler.md)  
 Ukazuje, jak zachytit všechny neošetřené výjimky.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)  
 Popisuje zpracování výjimek v C++.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)