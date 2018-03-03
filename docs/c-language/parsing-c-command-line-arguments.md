---
title: "Analýza argumentů příkazového řádku jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line, parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: ffce8037-2811-45c4-8db4-1ed787859c80
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8e3db47ca48e52babc03923dfba7b1dcb8173cc1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="parsing-c-command-line-arguments"></a>Analýza argumentů příkazového řádku jazyka C
**Konkrétní Microsoft**  
  
 Spouštěcí kód Microsoft C používá při interpretaci argumentů z příkazového řádku operačního systému následující pravidla:  
  
-   Argumenty jsou odděleny prázdný znak, který je mezeru nebo na kartě.  
  
-   Řetězec, který je uzavřen do dvojitých uvozovek, je interpretován jako jeden argument bez ohledu na prázdné znaky uvnitř. Řetězec v uvozovkách, lze jej vkládat v argumentu. Všimněte si, že pomocí kurzoru (**^**) nebyl rozpoznán jako řídicí znak nebo oddělovač.  
  
-   Uvozovky znak zpětného lomítka,  **\\"**, interpretována jako literál dvojitých uvozovek (**"**).  
  
-   Zpětná lomítka se interpretují oznámena, pokud se okamžitě předcházet uvozovky.  
  
-   Pokud sudý počet zpětná lomítka následuje uvozovky, pak jeden zpětné lomítko (**\\**) je umístěn v `argv` pole pro každý pár zpětná lomítka ( **\\ \\** ) a dvojité uvozovky (**"**) interpretována jako oddělovač řetězec.  
  
-   Pokud lichý počet zpětná lomítka následuje uvozovky, pak jeden zpětné lomítko (**\\**) je umístěn v `argv` pole pro každý pár zpětná lomítka ( **\\ \\** ) a dvojité uvozovky se interpretuje jako řídicí sekvence ve zbývajících zpětné lomítko, způsobuje literálu uvozovky (**"**) umístit do `argv`.  
  
 Tento seznam ukazuje výše uvedená pravidla zobrazením interpretovaného výsledku předaného do `argv` pro několik příkladů argumentů příkazového řádku. Výstup uvedený v druhém, třetím a čtvrtém sloupci je z aplikace ARGS.C, která následuje seznam.  
  
|Vstup příkazového řádku|argv – [1]|argv – [2]|argv – [3]|  
|-------------------------|---------------|---------------|---------------|  
|`"a b c" d e`|`a b c`|`d`|`e`|  
|`"ab\"c" "\\" d`|`ab"c`|`\`|`d`|  
|`a\\\b d"e f"g h`|`a\\\b`|`de fg`|`h`|  
|`a\\\"b c d`|`a\"b`|`c`|`d`|  
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
  
```  
// Parsing_C_Commandline_args.c  
// ARGS.C illustrates the following variables used for accessing  
// command-line arguments and environment variables:  
// argc  argv  envp  
//  
  
#include <stdio.h>  
  
int main( int argc, // Number of strings in array argv  
 char *argv[],      // Array of command-line argument strings  
 char **envp )      // Array of environment variable strings  
{  
    int count;  
  
    // Display each command-line argument.  
    printf_s( "\nCommand-line arguments:\n" );  
    for( count = 0; count < argc; count++ )  
        printf_s( "  argv[%d]   %s\n", count, argv[count] );  
  
    // Display each environment variable.  
    printf_s( "\nEnvironment variables:\n" );  
    while( *envp != NULL )  
        printf_s( "  %s\n", *(envp++) );  
  
    return;  
}  
```  
  
## <a name="comments"></a>Komentáře  
 Jeden příklad výstupu z této aplikace je:  
  
```  
Command-line arguments:  
  argv[0]   C:\MSC\TEST.EXE  
  
Environment variables:  
  COMSPEC=C:\NT\SYSTEM32\CMD.EXE  
  
  PATH=c:\nt;c:\binb;c:\binr;c:\nt\system32;c:\word;c:\help;c:\msc;c:\;  
  PROMPT=[$p]   
  TEMP=c:\tmp  
  TMP=c:\tmp  
  EDITORS=c:\binr  
  WINDIR=c:\nt        
```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)