---
title: "Zpracovávání výjimek v jazyce C++ | Microsoft Docs"
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
- C++ exception handling
- Visual C++, exception handling
ms.assetid: 65f80b44-9d0f-4d17-b910-07205a5c5c40
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6cbe3489b0d45111a527102c85e6d8c207715ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="c-exception-handling"></a>Zpracovávání výjimek v jazyce C++
Jazyk C++ obsahuje integrovanou podporu pro vyvolávání a zachycování výjimek. Při programování v jazyce C++ byste téměř vždy měli používat integrovanou podporu výjimek jazyka C++ popsanou v tomto oddíle.  
  
 Pokud chcete povolit C++ zpracování výjimek v kódu, použijte [/EHsc](../build/reference/eh-exception-handling-model.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Tato diskuse o zpracování výjimek jazyka C++ obsahuje:  
  
-   [Try, catch a throw – příkazy](../cpp/try-throw-and-catch-statements-cpp.md)  
  
-   [Jak se vyhodnocují Catch – bloky](../cpp/how-catch-blocks-are-evaluated-cpp.md)  
  
-   [Výjimky a uvolnění zásobníku](../cpp/exceptions-and-stack-unwinding-in-cpp.md)  
  
-   [Specifikace výjimek](../cpp/exception-specifications-throw-cpp.md)  
  
-   [noexcept](../cpp/noexcept-cpp.md)  
  
-   [Nezpracované výjimky jazyka C++](../cpp/unhandled-cpp-exceptions.md)  
  
-   [Kombinace výjimek v jazycích C (strukturované) a C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)  
  
## <a name="support-for-earlier-mfc-exceptions"></a>Podpora starších výjimek knihovny MFC  
 Od verze 4.0 MFC začal pomocí zpracování mechanismus výjimek C++. I když jste v novém kódu vedeni k používání zpracování výjimek jazyka C++, knihovna MFC verze 4.0 a novější zachovává makra z předchozích verzí knihovny MFC z důvodu kompatibility se starším kódem. Tato makra a nový mechanismus lze také kombinovat. Informace na kombinování makra a zpracovávání výjimek v jazyce C++ a převádění staré kódu pro použití nového mechanismu, najdete v článcích [výjimky: použití makrech MFC a výjimky jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) a [výjimky: převádění z rozhraní MFC Makra výjimek](../mfc/exceptions-converting-from-mfc-exception-macros.md). Starší výjimky maker knihovny MFC, pokud je stále používáte, se vyhodnotí jako klíčová slova výjimek jazyka C++. V tématu [výjimky: změny maker pro výjimky ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)