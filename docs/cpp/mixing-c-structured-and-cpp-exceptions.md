---
title: "Kombinování C (strukturované) a výjimky jazyka C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2cb390fa0b6cf90a76d0b751b8bdce7d4a3e54b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Kombinace výjimek v jazycích C (strukturované) a C++
Je-li zapotřebí vytvořit lépe přenositelný kód, není v programu jazyka C++ doporučeno používat zpracování strukturovaných výjimek. Ale v některých případech můžete zkompilovat s **/EHa** a kombinovat strukturovaných výjimky a zdrojového kódu C++ a je třeba některá zařízení pro zpracování oba druhy výjimek. Obslužná rutina strukturovaného výjimek obsahuje žádná koncepce objekty nebo typy výjimky, a proto ho nemůže zpracovat výjimky vyvolané C++ – kód; ale C++ **catch** obslužné rutiny můžete zpracování strukturovaných výjimek. Jako takový, zpracování syntaxe výjimek C++ (**zkuste**, `throw`, **catch**) není přijat kompilátor jazyka C, ale strukturovaného zpracování syntaxe výjimek (`__try`, `__except`, `__finally`) podporuje C++ compiler.  
  
 V tématu [_set_se_translator –](../c-runtime-library/reference/set-se-translator.md) informace o zpracování strukturovaných výjimek jako výjimky jazyka C++.  
  
 Jsou-li zkombinovány strukturované výjimky a výjimky jazyka C++, je třeba uvědomit si následující:  
  
1.  Výjimky jazyka C++ a strukturované výjimky nelze kombinovat v rámci stejné funkce.  
  
2.  Obslužné rutiny ukončení (bloky `__finally`) jsou provedeny vždy, i v případě odvíjení po tom, co je vyvolána výjimka.  
  
3.  Zpracovávání výjimek v jazyce C++ může zachytit a zachovat unwind sémantiku ve všech modulech kompilovat s [/EH](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru (Tato možnost umožňuje unwind sémantiku).  
  
4.  Mohou existovat situace, ve kterých nejsou funkce destruktoru volány pro všechny objekty. Například pokud se strukturovaná výjimka objeví při pokusu provést volání funkce prostřednictvím ukazatele neinicializované funkce, přičemž tato funkce přijímá jako parametry objekty, které byly vytvořeny před voláním, nebudou pro tyto objekty během odvíjení zásobníku volány destruktory.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Používání setjmp nebo longjmp v C++ – programy](../cpp/using-setjmp-longjmp.md)  
  
-   [Rozdíly mezi SEH a C++ EH](../cpp/exception-handling-differences.md)  
  
## <a name="see-also"></a>Viz také  
 [Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)