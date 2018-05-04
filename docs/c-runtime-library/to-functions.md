---
title: k funkcím | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr120.dll
- msvcr90.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- To
dev_langs:
- C++
helpviewer_keywords:
- to functions
- string conversion, to different characters
- string conversion, case
- lowercase, converting strings
- uppercase, converting strings
- case, converting
- characters, converting
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c852f65e603f11bfaf5812a9cb688dbf0eb36904
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="to-functions"></a>to – funkce
Každý z **k** funkce a jeho přidružené makro, pokud existuje, převede jeden znak na další znak.  
  
|||  
|-|-|  
|[__toascii](../c-runtime-library/reference/toascii-toascii.md)|[ToUpper, _toupper –, towupper –](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|  
|[ToLower, _tolower –, towlower –](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||  
  
## <a name="remarks"></a>Poznámky  
 **k** jsou následující funkce a převody makro.  
  
|Rutina|– Makro|Popis|  
|-------------|-----------|-----------------|  
|`__toascii`|`__toascii`|Převede `c` do znaků ASCII|  
|`tolower`|`tolower`|Převede `c` na malá písmena, pokud je to vhodné|  
|`_tolower`|`_tolower`|Převede `c` na malá.|  
|`towlower`|Žádné|Převede `c` na odpovídající široká charakterová malé písmeno|  
|`toupper`|`toupper`|Převede `c` na velká písmena v případě potřeby|  
|`_toupper`|`_toupper`|Převede `c` na velká písmena|  
|`towupper`|Žádné|Převede na odpovídající široká charakterová velké písmeno c|  
  
 Použití funkce verzí **k** rutin, které jsou také definovat jako makra, buď odeberte definice maker s `#undef` direktivy nebo nezahrnují CTYPE. H. Pokud použijete /Za – možnost kompilátoru, kompilátor použije verze funkce `toupper` nebo `tolower`. Prohlášení o `toupper` a `tolower` funkce jsou v STDLIB. H.  
  
 `__toascii` Rutiny nastaví všechny, ale nejnižší 7 bity `c` na hodnotu 0, tak, aby převedená hodnota představuje znak ve znakové sadě ASCII. Pokud `c` již představuje znaku ASCII, `c` se nemění.  
  
 `tolower` a `toupper` rutiny:  
  
-   Jsou závislé na `LC_CTYPE` kategorie aktuální národní prostředí (`tolower` volání `isupper` a `toupper` volání `islower`).  
  
-   Převést `c` Pokud `c` představuje převést písmeno odpovídající velká písmena v aktuální národní prostředí a v opačném případě existuje pro toto národní prostředí. V opačném `c` se nemění.  
  
 `_tolower` a `_toupper` rutiny:  
  
-   Jsou nezávislé na národním prostředí, mnohem rychlejší verzích `tolower` a **toupper.**  
  
-   Lze použít pouze tehdy, když **isascii – (**`c`**)** a buď **isupper – (**`c`**)** nebo **islower – (**`c`**)**, jsou nenulové hodnoty.  
  
-   Mít undefined výsledky, pokud `c` není k písmenu ASCII odpovídající případu pro převod.  
  
 `towlower` a `towupper` funkce vrátí převedený kopie `c` pokud obě z následujících podmínek jsou nenulové hodnoty. V opačném `c` se nemění.  
  
-   `c` je široká znaková odpovídající případu (to znamená, pro kterou `iswupper` nebo **iswlower –,** , je nenulové hodnoty).  
  
-   Neexistuje odpovídající široká znaková případu cíl (to znamená, pro kterou `iswlower` nebo **iswupper –,** , je nenulové hodnoty).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_toupper.c  
/* This program uses toupper and tolower to  
 * analyze all characters between 0x0 and 0x7F. It also  
 * applies _toupper and _tolower to any code in this  
 * range for which these functions make sense.  
 */  
  
#include <ctype.h>  
#include <string.h>  
  
char msg[] = "Some of THESE letters are Capitals.";  
char *p;  
  
int main( void )  
{  
   printf( "%s\n", msg );  
  
   /* Reverse case of message. */  
   for( p = msg; p < msg + strlen( msg ); p++ )  
   {  
      if( islower( *p ) )  
         putchar( _toupper( *p ) );  
      else if( isupper( *p ) )  
         putchar( _tolower( *p ) );  
      else  
         putchar( *p );  
   }  
}  
```  
  
```Output  
Some of THESE letters are Capitals.  
sOME OF these LETTERS ARE cAPITALS.  
```  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../c-runtime-library/locale.md)   
 [is, isw – rutiny](../c-runtime-library/is-isw-routines.md)