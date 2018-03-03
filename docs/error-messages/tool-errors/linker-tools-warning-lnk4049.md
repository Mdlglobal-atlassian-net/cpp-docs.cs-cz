---
title: "Upozornění linkerů Lnk4049 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4049
dev_langs:
- C++
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f44634bd99e485e444ffe9cee7747f31374becf4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4049"></a>Upozornění linkerů LNK4049
místně definované symbol importovat symbol  
  
 Symbol byl exportovaný z i importovat do programu.  
  
 Toto upozornění je generován linkeru po deklarování symbol pomocí `__declspec(dllexport)` třídy úložiště atributů v souboru jeden objekt a pomocí něj odkazovat `__declspec(dllimport)` atribut v jiném.  
  
 Upozornění LNK4049 je obecnější verze [LNK4217 upozornění Linkerů nástroje](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md). Linkeru generuje LNK4049 upozornění, když nelze určit, z které funkce bylo odkazováno importované symbolu.  
  
 Běžné případy, kdy se vygeneruje LNK4049 místo LNK4217 jsou:  
  
-   Provádění přírůstkové propojování pomocí [/PŘÍRŮSTKOVÉ](../../build/reference/incremental-link-incrementally.md) možnost.  
  
-   Provedení optimalizace celého programu pomocí [/ltgc](../../build/reference/ltcg-link-time-code-generation.md) možnost.  
  
 Chcete-li vyřešit LNK4049, zkuste jednu z následujících:  
  
-   Odeberte `__declspec(dllimport)` název deklarace z dopředného deklarace symbolu, která spustí LNK4049. Symboly v rámci bitové kopie binární můžete vyhledat pomocí **DUMPBIN** nástroj. **DUMPBIN nebo symboly** přepínače zobrazí tabulky symbolů COFF bitové kopie. Další informace o **DUMPBIN** nástroj, najdete v části [DUMPBIN – odkaz](../../build/reference/dumpbin-reference.md).  
  
-   Dočasně zakážete přírůstkové propojování a optimalizace celého programu. Nutnosti rekompilace aplikace vygeneruje LNK4217 upozornění, která bude obsahovat název funkce, ze kterého bylo odkazováno importované symbolu. Odeberte `__declspec(dllimport)` deklarace z importovaných symbol a Povolit přírůstkové propojování nebo optimalizace celého programu podle potřeby.  
  
 Poslední generovaný kód se bude chovat správně, kód generovaný pro volání importované funkce sice méně efektivní než přímé volání funkce. Toto upozornění se nezobrazí, když zkompilujete pomocí možnosti [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Další informace o import a export dat deklarace, najdete v části [dllexport, dllimport](../../cpp/dllexport-dllimport.md).  
  
## <a name="example"></a>Příklad  
 Propojování následující dva moduly vygeneruje LNK4049. První modul generuje soubor objektu obsahující jedné exportované funkce.  
  
```  
// LNK4049a.cpp  
// compile with: /c  
  
__declspec(dllexport) int func()   
{  
   return 3;  
}  
```  
  
## <a name="example"></a>Příklad  
 Druhý modul generuje soubor objektu obsahující deklaraci dopředného exportovali v první modulu, společně s volání této funkce uvnitř funkce `main` funkce. Tento modul s modulem první propojení vygeneruje LNK4049. Odebrání `__declspec(dllimport)` deklarace vyřešit upozornění.  
  
```  
// LNK4049b.cpp  
// compile with: /link /WX /LTCG LNK4049a.obj  
// LNK4049 expected  
  
__declspec(dllimport) int func();  
// try the following line instead  
// int func();  
  
int main()  
{  
   return func();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Upozornění LNK4217 nástroje linkeru](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)   
 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)