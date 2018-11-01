---
title: Analýza argumentů příkazového řádku jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line, parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: ffce8037-2811-45c4-8db4-1ed787859c80
ms.openlocfilehash: 8161d724dbd21297bb3beef2cf9406ddd2484ff1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522431"
---
# <a name="parsing-c-command-line-arguments"></a>Analýza argumentů příkazového řádku jazyka C

**Specifické pro Microsoft**

Spouštěcí kód Microsoft C používá při interpretaci argumentů z příkazového řádku operačního systému následující pravidla:

- Argumenty jsou odděleny prázdným znakem, který je mezera nebo tabulátor.

- Řetězec, který je uzavřen do dvojitých uvozovek, je interpretován jako jeden argument bez ohledu na prázdné znaky uvnitř. Řetězec v uvozovkách, může být vložen do argumentu. Všimněte si, že blikající kurzor (**^**) nebyl rozpoznán jako řídicí znak ani oddělovač.

- Dvojitých uvozovek předcházený zpětným lomítkem  **\\"**, je interpretován jako znak dvojitých uvozovek (**"**).

- Zpětná lomítka jsou interpretovány literálně, pokud jsou bezprostředně předcházet dvojité uvozovky.

- -Li sudý počet zpětných lomítek následován znakem dvojitých uvozovek a pak jedno zpětné lomítko (**\\**) se umístí do `argv` pole pro každý pár zpětných lomítek (**\\ \\**) a dvojité uvozovky (**"**) je interpretován jako oddělovač řetězců.

- -Li lichý počet zpětných lomítek následován znakem dvojitých uvozovek a pak jedno zpětné lomítko (**\\**) se umístí do `argv` pole pro každý pár zpětných lomítek (**\\ \\**) a dvojité uvozovky, je interpretován jako sekvence escape ve zbývajících zpětné lomítko způsobí znak dvojitých uvozovek (**"**) se mají umístit na `argv`.

Tento seznam ukazuje výše uvedená pravidla zobrazením interpretovaného výsledku předaného do `argv` pro několik příkladů argumentů příkazového řádku. Výstup uvedený v druhém, třetím a čtvrtém sloupci je z aplikace ARGS.C, která následuje seznam.

|Vstup příkazového řádku|argv [1]|argv [2]|argv [3]|
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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)