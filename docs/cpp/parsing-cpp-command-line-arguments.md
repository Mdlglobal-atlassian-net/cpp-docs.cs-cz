---
title: "Analýza argumentů příkazového řádku jazyka C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line [C++], parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: e634e733-ac2f-4298-abe2-7e9288c94951
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fe9203a94d698aa21ddd861df75c63a76253ce9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="parsing-c-command-line-arguments"></a>Analýza argumentů příkazového řádku jazyka C++
**Konkrétní Microsoft**  
  
 Kód spuštění Microsoft C/C++ používá následující pravidla při interpretaci argumenty zadána na příkazovém řádku operačního systému:  
  
-   Argumenty jsou odděleny prázdný znak, který je mezeru nebo na kartě.  
  
-   Znak pomocí kurzoru (^) není rozpoznán jako řídicí znak nebo oddělovač. Znak je zpracován úplně analyzátorem příkazového řádku v operačním systému před předáním `argv` pole v programu.  
  
-   Řetězec v uvozovkách ("*řetězec*") interpretována jako jeden argument, bez ohledu na to, obsažené v prázdné znaky. Řetězec v uvozovkách, lze jej vkládat v argumentu.  
  
-   Uvozovky uvedené zpětným lomítkem (\\") je interpretován jako znak dvojitých uvozovek (").  
  
-   Zpětná lomítka se interpretují oznámena, pokud se okamžitě předcházet uvozovky.  
  
-   Pokud sudý počet zpětná lomítka následuje uvozovky, jeden zpětné lomítko je umístěn v `argv` pole pro každý pár zpětná lomítka a dvojité uvozovky se interpretuje jako oddělovač řetězec.  
  
-   Pokud lichý počet zpětná lomítka následuje uvozovky, jeden zpětné lomítko je umístěn v `argv` pole pro každý pár zpětná lomítka a dvojité uvozovky se "escape" ve zbývajících zpětné lomítko, způsobuje literálu uvozovky (" ) umístit do `argv`.  
  
## <a name="example"></a>Příklad  
 Následující program ukazuje, jak příkazového řádku argumenty se předávají:  
  
```  
// command_line_arguments.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
int main( int argc,      // Number of strings in array argv  
          char *argv[],   // Array of command-line argument strings  
          char *envp[] )  // Array of environment variable strings  
{  
    int count;  
  
    // Display each command-line argument.  
    cout << "\nCommand-line arguments:\n";  
    for( count = 0; count < argc; count++ )  
         cout << "  argv[" << count << "]   "  
                << argv[count] << "\n";  
}  
```  
  
 Následující tabulka uvádí příklad vstup a očekávaný výstup, ukázka pravidla v předchozím seznamu.  
  
### <a name="results-of-parsing-command-lines"></a>Výsledky analýzy příkazy na příkazových řádcích  
  
|Vstup příkazového řádku|argv – [1]|argv – [2]|argv – [3]|  
|-------------------------|---------------|---------------|---------------|  
|`"abc" d e`|`abc`|`d`|`e`|  
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|  
|`a\\\"b c d`|`a\"b`|`c`|`d`|  
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [hlavní: spuštění programu](../cpp/main-program-startup.md)