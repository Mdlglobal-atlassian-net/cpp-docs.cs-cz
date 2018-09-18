---
title: Analýza argumentů příkazového řádku jazyka C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line [C++], parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: e634e733-ac2f-4298-abe2-7e9288c94951
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a48e731e714f59a249e5fa689e046e94faf360e6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040216"
---
# <a name="parsing-c-command-line-arguments"></a>Analýza argumentů příkazového řádku jazyka C++

**Specifické pro Microsoft**

Spouštěcí kód Microsoft C/C++ používá při interpretaci argumentů příkazového řádku operačního systému následující pravidla:

- Argumenty jsou odděleny prázdným znakem, který je mezera nebo tabulátor.

- Znak stříšky (^) nebyl rozpoznán jako řídicí znak ani oddělovač. Znak, který je zcela zpracovat analyzátor příkazového řádku v operačním systému před předáním `argv` pole v programu.

- Řetězec v dvojitých uvozovkách ("*řetězec*") je interpretován jako jeden argument, bez ohledu na prázdné znaky uvnitř. Řetězec v uvozovkách, může být vložen do argumentu.

- Znak dvojitých uvozovek předcházený zpětným lomítkem (\\") je interpretován jako znak dvojitých uvozovek (").

- Zpětná lomítka jsou interpretovány literálně, pokud jsou bezprostředně předcházet dvojité uvozovky.

- Je-li sudý počet zpětných lomítek následován znakem dvojitých uvozovek, jedno zpětné lomítko je umístěn v `argv` pole pro každý pár zpětných lomítek a dvojitých uvozovek, je interpretován jako oddělovač řetězců.

- Je-li lichý počet zpětných lomítek následován znakem dvojitých uvozovek, jedno zpětné lomítko je umístěn v `argv` pole pro každý pár zpětných lomítek a dvojitá uvozovka není "uvozeno uvozovacím znakem" ve zbývajících zpětné lomítko způsobí znak dvojitých uvozovek (" ) se mají umístit na `argv`.

## <a name="example"></a>Příklad

Následující program ukazuje, jak příkazového řádku argumenty jsou předány:

```cpp
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

Následující tabulka uvádí příklad vstupu a očekávaný výstup, ukázka pravidla v předchozím seznamu.

### <a name="results-of-parsing-command-lines"></a>Výsledky analýzy příkazové řádky

|Vstup příkazového řádku|argv [1]|argv [2]|argv [3]|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[main: spuštění programu](../cpp/main-program-startup.md)