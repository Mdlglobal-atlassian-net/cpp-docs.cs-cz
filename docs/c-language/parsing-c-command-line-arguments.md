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
ms.openlocfilehash: ace6d1b8295d0901ef22f3c354b32ad17e296e87
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299088"
---
# <a name="parsing-c-command-line-arguments"></a>Analýza argumentů příkazového řádku jazyka C

**Specifické pro společnost Microsoft**

Spouštěcí kód Microsoft C používá při interpretaci argumentů z příkazového řádku operačního systému následující pravidla:

- Argumenty jsou odděleny prázdným znakem, což je mezera nebo karta.

- Řetězec, který je uzavřen do dvojitých uvozovek, je interpretován jako jeden argument bez ohledu na prázdné znaky uvnitř. V argumentu může být vložen řetězec v uvozovkách. Všimněte si, že blikající kurzor ( **^** ) není rozpoznán jako řídicí znak nebo oddělovač.

- Dvojitá uvozovka před znakem zpětného lomítka, **\\"** , je interpretována jako literální dvojité uvozovky ( **"** ).

- Zpětná lomítka jsou interpretována doslova, pokud bezprostředně nepředchází uvozovky.

- Je-li sudý počet zpětných lomítek následován znakem dvojitých uvozovek, pak je jedno zpětné lomítko ( **\\** ) umístěno v `argv` poli pro každou dvojici zpětných lomítek ( **\\\\** ) a dvojité uvozovky ( **"** ) jsou interpretovány jako oddělovač řetězců.

- Je-li lichý počet zpětných lomítek následovaný dvojitou uvozovkou, pak je jedno zpětné lomítko ( **\\** ) umístěno v `argv` poli pro každý pár zpětných lomítek ( **\\\\** ) a Dvojitá uvozovka je interpretována jako řídicí sekvence zbývajícím zpětným lomítkem, což způsobí, že se literální dvojité uvozovky ( **"** ) umístí do `argv`.

Tento seznam ukazuje výše uvedená pravidla zobrazením interpretovaného výsledku předaného do `argv` pro několik příkladů argumentů příkazového řádku. Výstup uvedený v druhém, třetím a čtvrtém sloupci je z aplikace ARGS.C, která následuje seznam.

|Vstup z příkazového řádku|argv[1]|argv[2]|argv[3]|
|-------------------------|---------------|---------------|---------------|
|`"a b c" d e`|`a b c`|`d`|`e`|
|`"ab\"c" "\\" d`|`ab"c`|`\`|`d`|
|`a\\\b d"e f"g h`|`a\\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

## <a name="example"></a>Příklad

### <a name="code"></a>Kód

```c
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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)
