---
title: "va_arg –, va_copy –, va_end –, va_start – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- va_arg
- va_end
- va_copy
- va_start
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- va_arg
- va_start
- va_list
- va_alist
- va_dcl
- va_copy
- va_end
dev_langs: C++
helpviewer_keywords:
- variable argument lists, accessing
- va_start macro
- va_arg macro
- va_end macro
- arguments [C++], argument lists
- va_list macro
- va_dcl macro
- va_alist macro
- va_copy macro
ms.assetid: a700dbbd-bfe5-4077-87b6-3a07af74a907
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4dc911bfd08781240eaaa73492b61278348bd790
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="vaarg-vacopy-vaend-vastart"></a>va_arg, va_copy, va_end, va_start
Seznamy argumentů s proměnnou přístupů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
type va_arg(  
   va_list arg_ptr,  
   type   
);
void va_copy(  
   va_list dest,  
   va_list src  
); // (ISO C99 and later)  
void va_end(  
   va_list arg_ptr   
);  
void va_start(  
   va_list arg_ptr,  
   prev_param   
); // (ANSI C89 and later)  
void va_start(  
   arg_ptr   
);  // (deprecated Pre-ANSI C89 standardization version)  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Typ argumentu mají být načteny.  
  
 `arg_ptr`  
 Ukazatel na seznam argumentů.  
  
 `dest`  
 Ukazatel na seznam argumentů inicializované ze`src`  
  
 `src`  
 Ukazatel na inicializovaného seznam argumentů, zkopírujte do `dest`.  
  
 `prev_param`  
 Parametr, který se nachází před první nepovinný argument.  
  
## <a name="return-value"></a>Návratová hodnota  
 `va_arg`Vrátí aktuální argument. `va_copy`, `va_start` a `va_end` nevrátí hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 `va_arg`, `va_copy`, `va_end`, A `va_start` makra poskytnout přenosný způsob, jak přístupu argumenty pro funkci v případě, že funkce přijímá proměnný počet argumentů. Existují dvě verze makra: makra definované v STDARG. H odpovídat standardní; ISO C99 makra definované v vararg. H jsou zastaralé, ale se zachovává kvůli zpětné kompatibilitě s kódem, který byla zapsána před standardní kompilátorem C89 ANSI.  
  
 Tyto makra předpokládá, že funkce přijímá pevný počet povinnými argumenty, za nímž následuje proměnný počet volitelné argumenty. Vyžaduje argumenty jsou deklarovány jako obyčejnou parametrů pro funkci a je přístupný prostřednictvím názvy parametrů. Nepovinné argumenty jsou přístupné prostřednictvím makra v STDARG. H (nebo vararg. H pro kód, který byla zapsána před standardu ANSI kompilátorem C89), který nastaví ukazatel na první nepovinný argument v seznamu argumentů načte argumenty ze seznamu a obnoví ukazatele po dokončení zpracování argument.  
  
 Standardní makra C definované v STDARG. H, používají se následujícím způsobem:  
  
-   `va_start`Nastaví `arg_ptr` na první nepovinný argument v seznamu argumentů, který je předán do funkce. Argument `arg_ptr` musí mít `va_list` typu. Argument `prev_param` je název povinný parametr, který okamžitě předchází první nepovinný argument v seznamu argumentů. Pokud `prev_param` je deklarovaný s třídy úložiště registrace jeho chování není definován. `va_start`než se musí použít `va_arg` se používá pro první.  
  
-   `va_arg`načte hodnotu `type` z umístění, které je dán `arg_ptr`a zvýší `arg_ptr` tak, aby odkazoval na další argument v seznamu pomocí velikost `type` k určení, kdy začne další argument. `va_arg`lze použít libovolný počet časy ve funkci k načtení argumentů ze seznamu.  
  
-   `va_copy`Vytvoří kopii seznam argumentů v jejím aktuálním stavu. `src` Parametr musí být již inicializován s `va_start`; je pravděpodobně byly aktualizovány s `va_arg` volá, ale nesmí resetován s `va_end`. Další argument, který načte `va_arg` z `dest` je stejný jako další argument, které se načítají ze `src`.  
  
-   Poté, co byly získány všechny argumenty, `va_end` resetuje má ukazatel na **NULL**. `va_end`musí být volána pro každý seznam argumentů, který je inicializován s `va_start` nebo `va_copy` před funkce vrátí hodnotu.  
  
> [!NOTE]
>  Makra v vararg. H jsou zastaralé a jsou uchovány pouze pro zpětné kompatibility s kódem, který byla zapsána před standardní kompilátorem C89 ANSI. Ve všech ostatních případech použitím makra v STDARGS. H.  
  
 Když se kompilují pomocí [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md), programy, které používají tyto makra může způsobit neočekávané výsledky z důvodu rozdíly mezi nativní a common language runtime (CLR) typu systémy. Vezměte v úvahu tento program:  
  
```  
#include <stdio.h>  
#include <stdarg.h>  
  
void testit (int i, ...)  
{  
    va_list argptr;  
    va_start(argptr, i);  
  
    if (i == 0)  
    {  
        int n = va_arg(argptr, int);  
        printf("%d\n", n);  
    }  
    else  
    {  
        char *s = va_arg(argptr, char*);  
        printf("%s\n", s);  
    }  

    va_end(argptr);  
}  
  
int main()  
{  
    testit(0, 0xFFFFFFFF); // 1st problem: 0xffffffff is not an int  
    testit(1, NULL);       // 2nd problem: NULL is not a char*  
}  
```  
  
 Všimněte si, že `testit` očekává, že její druhý parametr bude buď `int` nebo `char*`. Argumenty předávány jsou 0xffffffff ( `unsigned int`, nikoli `int`) a `NULL` (ve skutečnosti k `int`, nikoli `char*`). Během kompilace programu pro nativní kód, dostanete tento výstup:  
  
```Output  
-1  
  
(null)  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<stdio.h > a \<stdarg.h >  
  
 **Nepoužívané záhlaví:** \<varargs.h >  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_va.c  
/* Compile with: cl /W3 /Tc crt_va.c  
 * The program below illustrates passing a variable  
 * number of arguments using the following macros:  
 *      va_start            va_arg              va_copy  
 *      va_end              va_list  
 */  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <math.h>  
  
double deviation(int first, ...);  
  
int main( void )  
{  
    /* Call with 3 integers (-1 is used as terminator). */  
    printf("Deviation is: %f\n", deviation(2, 3, 4, -1 ));  
  
    /* Call with 4 integers. */  
    printf("Deviation is: %f\n", deviation(5, 7, 9, 11, -1));  
  
    /* Call with just -1 terminator. */  
    printf("Deviation is: %f\n", deviation(-1));  
}  
  
/* Returns the standard deviation of a variable list of integers. */  
double deviation(int first, ...)  
{  
    int count = 0, i = first;  
    double mean = 0.0, sum = 0.0;  
    va_list marker;  
    va_list copy;  
  
    va_start(marker, first);     /* Initialize variable arguments. */  
    va_copy(copy, marker);       /* Copy list for the second pass */  
    while (i != -1)  
    {  
        sum += i;  
        count++;  
        i = va_arg(marker, int);  
    }  
    va_end(marker);              /* Reset variable argument list. */  
    mean = sum ? (sum / count) : 0.0;  
  
    i = first;                  /* reset to calculate deviation */  
    sum = 0.0;  
    while (i != -1)  
    {  
        sum += (i - mean)*(i - mean);  
        i = va_arg(copy, int);  
    }  
    va_end(copy);               /* Reset copy of argument list. */  
    return count ? sqrt(sum / count) : 0.0;  
}  
  
```  
  
## <a name="output"></a>Výstup  
  
```Output  
Deviation is: 0.816497  
Deviation is: 2.236068  
Deviation is: 0.000000  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Přístup k argumentu](../../c-runtime-library/argument-access.md)   
 [vfprintf –, _vfprintf_l –, vfwprintf –, _vfwprintf_l –](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)