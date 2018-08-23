---
title: – funkce (C/C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- function_CPP
- vc-pragma.function
dev_langs:
- C++
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 76ab5b2911d349c62ff18967e7a660cdc3589ddd
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464796"
---
# <a name="function-cc"></a>funkce (C/C++)
Určuje, že budou vytvořena volání funkcí zadaných v seznamu argumentů direktivy pragma.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma function( function1 [, function2, ...] )  
```  
  
## <a name="remarks"></a>Poznámky  

Pokud používáte `intrinsic` – Direktiva pragma (nebo /Oi) Chcete-li sdělit kompilátoru, aby vytvářel vnitřní funkce (vnitřní funkce jsou vytvořeny jako vložený kód, nikoli jako volání funkce), můžete použít **funkce** – Direktiva pragma k vynucení explicitního volání funkce. Po nalezení direktivy pragma function se její účinek projeví v první definici funkce obsahující zadanou vnitřní funkci. Účinek trvá do konce zdrojového souboru nebo do výskytu `intrinsic` zadávající stejnou vnitřní funkci. **Funkce** – Direktiva pragma lze použít pouze vně funkce – na globální úrovni.  
  
Seznam funkcí, které mají vlastní vnitřní podobu, naleznete v tématu [#pragma intrinsic](../preprocessor/intrinsic.md).  
  
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
  
## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)