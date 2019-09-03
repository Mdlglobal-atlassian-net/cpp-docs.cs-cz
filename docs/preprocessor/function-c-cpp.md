---
title: function – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- function_CPP
- vc-pragma.function
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
ms.openlocfilehash: f99f3c878789a6c47fdb0d48e0a8690d65fa8062
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220135"
---
# <a name="function-pragma"></a>function – direktiva pragma

Instruuje kompilátor, aby vygeneroval volání funkcí zadaných v seznamu argumentů direktivy pragma místo jejich vkládání.

## <a name="syntax"></a>Syntaxe

> **#pragma – funkce (** *Function1* [ **,** *function2* ...] **)**

## <a name="remarks"></a>Poznámky

Vnitřní funkce jsou obvykle generovány jako vložený kód, nikoli jako volání funkce. Použijete-li [vnitřní direktivu pragma](intrinsic.md) nebo možnost kompilátoru [/Oi](../build/reference/oi-generate-intrinsic-functions.md) k oznámení kompilátoru, aby vygeneroval vnitřní funkce, můžete použít direktivu pragma **funkce** k explicitnímu vynucení volání funkce. Po výskytu direktivy pragma **funkce** se projeví v první definici funkce obsahující zadanou vnitřní funkci. Efekt pokračuje do konce zdrojového souboru nebo do výskytu `intrinsic` direktivy pragma, která určuje stejnou vnitřní funkci. Direktivu pragma **funkce** lze použít pouze mimo funkci na globální úrovni.

Seznam funkcí, které mají vnitřní formuláře, najdete v tématu [vnitřní direktiva pragma](intrinsic.md).

## <a name="example"></a>Příklad

```cpp
// pragma_directive_function.cpp
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// use intrinsic forms of memset and strlen
#pragma intrinsic(memset, strlen)

// Find first word break in string, and set remaining
// chars in string to specified char value.
char *set_str_after_word(char *string, char ch) {
   int i;
   int len = strlen(string);  /* NOTE: uses intrinsic for strlen */

   for(i = 0; i < len; i++) {
      if (isspace(*(string + i)))
         break;
   }

   for(; i < len; i++)
      *(string + i) = ch;

   return string;
}

// do not use strlen intrinsic
#pragma function(strlen)

// Set all chars in string to specified char value.
char *set_str(char *string, char ch) {
   // Uses intrinsic for memset, but calls strlen library function
   return (char *) memset(string, ch, strlen(string));
}

int main() {
   char *str = (char *) malloc(20 * sizeof(char));

   strcpy_s(str, sizeof("Now is the time"), "Now is the time");
   printf("str is '%s'\n", set_str_after_word(str, '*'));
   printf("str is '%s'\n", set_str(str, '!'));
}
```

```Output
str is 'Now************'
str is '!!!!!!!!!!!!!!!'
```

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
