---
title: "Problémy vložené funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4817093bf52ab5398f1d4a788b96bcff16384c1f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="function-inlining-problems"></a>Problémy vložené funkce
Pokud používáte vložené funkce, musíte provést tyto akce:  
  
-   Vložené funkce implementované v záhlaví souboru, které zahrnete mít.  
  
-   Mít vložené zapnuté ON v záhlaví souboru.  
  
```  
// LNK2019_function_inline.cpp  
// compile with: /c   
// post-build command: lib LNK2019_function_inline.obj  
#include <stdio.h>  
struct _load_config_used {  
   void Test();  
   void Test2() { printf("in Test2\n"); }  
};  
  
void _load_config_used::Test() { printf("in Test\n"); }  
```  
  
 A pak  
  
```  
// LNK2019_function_inline_2.cpp  
// compile with: LNK2019_function_inline.lib  
struct _load_config_used {  
   void Test();  
   void Test2();  
};  
  
int main() {  
   _load_config_used x;  
   x.Test();  
   x.Test2();   // LNK2019  
}  
```  
  
 Pokud používáte `#pragma inline_depth` kompilátoru direktivy, ujistěte se, že máte hodnotu 2 nebo vyšší nastavení. Hodnota 0 vypne vložené. Také se ujistěte, že používáte **/Ob1** nebo **/Ob2** – možnosti kompilátoru.  
  
 Kombinování vložené a bez vložené možnosti kompilace na jiné moduly někdy může způsobit problémy. Pokud je vytvořena knihovna C++ s vložené funkce zapnutá ([/Ob1](../../build/reference/ob-inline-function-expansion.md) nebo [/Ob2](../../build/reference/ob-inline-function-expansion.md)), ale odpovídající soubor hlavičky popisující funkce má vložené vypnutý (žádná možnost), zobrazí se chyba LNK2001. Funkce Nezískávat vložená do kódu z soubor hlaviček, ale vzhledem k tomu, že nejsou v soubor knihovny není žádná adresa odkaz na řešení.  
  
 Podobně projekt, který používá funkce vložené ještě definuje funkce v souboru sada, spíše než v hlavičce souboru získají LNK2019. Záhlaví souboru je součástí everywhere považujete za vhodné, ale funkce jsou pouze vložená kdy souboru prochází kompilátoru; proto linkeru uvidí funkce jako chyby definicí při použití v dalších modulů.  
  
```  
// LNK2019_FIP.h  
struct testclass {  
   void PublicStatMemFunc1(void);  
};  
```  
  
 A pak  
  
```  
// LNK2019_FIP.cpp  
// compile with: /c  
#include "LNK2019_FIP.h"  
inline void testclass::PublicStatMemFunc1(void) {}  
```  
  
 A pak  
  
```  
// LNK2019_FIP_2.cpp  
// compile with: LNK2019_FIP.cpp  
// LNK2019 expected  
#include "LNK2019_FIP.h"  
int main() {  
   testclass testclsObject;  
  
   // module cannot see the implementation of PublicStatMemFunc1  
   testclsObject.PublicStatMemFunc1();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Chyba linkerů LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)