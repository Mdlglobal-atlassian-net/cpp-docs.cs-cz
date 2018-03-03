---
title: "Zpracování výjimek v jazyce Visual C++ | Microsoft Docs"
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
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 33ec97d5f29398e9e20be9609573eecf33894948
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exception-handling-in-visual-c"></a>Zpracování výjimek v jazyce Visual C++
Výjimka je chybový stav, nacházející se případně i mimo řízení programu, který brání programu pokračovat dle jeho pravidelné cesty spuštění. Určité operace, včetně vytvoření objektu, vstupu a výstupu souboru a volání funkcí z jiných modulů, představují možné zdroje výjimek i v případě, že program pracuje správně. Robustní kód je na výjimky připraven a zpracovává je.  
  
 Ke zjištění chyby logiky v rámci jednoho programu nebo modulu, použijte kontrolní výrazy a ne výjimky (viz [pomocí kontrolních výrazů](/visualstudio/debugger/c-cpp-assertions)).  
  
 Jazyk Visual C++ podporuje tři druhy zpracování výjimek:  
  
-   [Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)  
  
     Ve většině aplikací jazyka C++ by mělo být použito zpracování výjimek jazyka C++, které je typově bezpečné a zajišťuje, že jsou v průběhu odvíjení zásobníku vyvolány destruktory objektu.  
  
-   [Strukturované zpracování výjimek](../cpp/structured-exception-handling-c-cpp.md)  
  
     Systém Windows nabízí svůj vlastní mechanismus zpracování výjimek zvaný SEH. Jeho použití není vhodné pro programování v jazyce C++ ani při použití knihovny MFC. Použijte SEH jenom v aplikacích MFC C.  
  
-   [MFC – výjimky](../mfc/exception-handling-in-mfc.md)  
  
     Od verze 3.0 používá MFC výjimky jazyka C++, ale stále podporuje jeho starší makra pro zpracování výjimek, jejichž forma se podobá výjimkám jazyka C++. Přestože nejsou tato makra vhodná pro nové programování, jsou z důvodu zpětné kompatibility stále podporována. V aplikacích používajících makra lze volně používat i výjimky jazyka C++. Během předběžného zpracování provádějí makra vyhodnocování na základě klíčových slov zpracování výjimek definovaných v implementaci Visual C++ jazyka C++ stejně jako u Visual C++ verze 2.0. Stávající makra zpracování výjimek lze při použití výjimek jazyka C++ ponechat.  
  
 Použít [/EH](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru k určení typu zpracování výjimek pro použití v projektu; Zpracovávání výjimek v jazyce C++ je výchozí. Nemíchat chyba zpracování mechanismy; Například nepoužívejte výjimky jazyka C++ s strukturované zpracování výjimek. Zpracovávání výjimek v jazyce C++ pomocí bude váš kód víc přenosného a umožňuje zpracování výjimek libovolného typu. Další informace o nevýhod strukturované zpracování výjimek najdete v tématu [strukturované zpracování výjimek](../cpp/structured-exception-handling-c-cpp.md). Žádost o mísení maker MFC a výjimky jazyka C++, najdete v části [výjimky: použití makrech MFC a výjimky jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).  
  
 Informace o zpracování výjimek v aplikacích CLR najdete v tématu [zpracování výjimek](../windows/exception-handling-cpp-component-extensions.md).  
  
 Informace o zpracování na x64 výjimek procesorů, najdete v části [zpracování výjimek (x64)](../build/exception-handling-x64.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)