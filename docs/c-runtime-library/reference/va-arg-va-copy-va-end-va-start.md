---
title: va_arg va_copy, va_end, va_start | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c33c8dbfe55008c084daf8f6b9f4700f13281012
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195426"
---
# <a name="vaarg-vacopy-vaend-vastart"></a>va_arg, va_copy, va_end, va_start

Seznamy argumentů proměnných přístupy.

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*Typ*<br/>
Typ argumentu, který se má načíst.

*arg_ptr*<br/>
Ukazatel na seznam argumentů.

*cíl*<br/>
Ukazatel na seznam argumentů, které mají být inicializovány z *src*

*src*<br/>
Ukazatel na inicializované seznam argumentů, které mají zkopírovat do *dest*.

*prev_param*<br/>
Parametr, který předchází první nepovinný argument.

## <a name="return-value"></a>Návratová hodnota

**va_arg** vrátí aktuální argument. **va_copy**, **va_start** a **va_end** nesmí vracet hodnoty.

## <a name="remarks"></a>Poznámky

**Va_arg**, **va_copy**, **va_end**, a **va_start** makra poskytují přenosný způsob pro přístup k argumentům funkce při funkce má proměnný počet argumentů. Existují dvě verze makra: makra definovaná v STDARG. H v souladu s normou, ISO C99 Makra definovaná ve funkcích VARARGS. H jsou zastaralé, ale se zachovává kvůli zpětné kompatibilitě s kódem, který byl zapsán před ANSI C89 standard.

Tato makra se předpokládá, že funkce nepřebírá pevný počet povinné argumenty, za nímž následuje proměnný počet volitelné argumenty. Povinné argumenty jsou deklarovány jako běžný parametrů pro funkci a je přístupný prostřednictvím názvy parametrů. Nepovinné argumenty jsou přístupné prostřednictvím makra v STDARG. H (ani parametry vararg. H pro kód, který byl zapsán před standardu ANSI C89), který nastaví ukazatel na první nepovinný argument v seznamu argumentů, načte argumenty v seznamu a resetuje ukazatel po dokončení zpracování argumentů.

Standardní makra jazyka C definovaná v STDARG. H, používají se následujícím způsobem:

- **va_start** nastaví *arg_ptr* první volitelné argumentu v seznam argumentů, který je předán do funkce. Argument *arg_ptr* musí mít **va_list** typu. Argument *prev_param* je název povinný parametr, který bezprostředně předchází první nepovinný argument v seznamu argumentů. Pokud *prev_param* je deklarována pomocí třídy úložiště register makro chování není definováno. **va_start** musí být použita před **va_arg** je použit poprvé.

- **va_arg** načte hodnotu *typ* z umístění, které je dán *arg_ptr*a zvýší hodnotu *arg_ptr* tak, aby odkazoval na další argument v seznamu podle pomocí velikosti *typ* k určení, kde začíná další argument. **va_arg** lze použít libovolný počet pokusů o ve funkci k načtení ze seznamu argumentů.

- **va_copy** vytvoří kopii tohoto seznamu argumentů v jejím aktuálním stavu. *Src* parametr musí být již inicializována s **va_start**; to může mít aktualizované a přinášejí **va_arg** volání, ale nesmí obnovit s **va_end** . Další argument, který načte **va_arg** z *dest* je stejný jako další argument, který je načten z *src*.

- Jakmile se načetly všechny argumenty, **va_end** resetuje ukazatel na **NULL**. **va_end** musí být volána na každý seznam argumentů, který je inicializován s **va_start** nebo **va_copy** dříve, než funkce vrátí.

> [!NOTE]
> Makra ve funkcích VARARGS. H jsou zastaralé a je zachován pouze z důvodu zpětné kompatibility s kódem, který byl zapsán před standardu ANSI C89. Ve všech ostatních případech použijte makra v STDARGS. H.

Když jsou kompilovány pomocí [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md), programy, které používají makra může způsobit neočekávané výsledky kvůli rozdílům mezi nativní a common language runtime (CLR) typ systémy. Vezměte v úvahu tento program:

```C
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

Všimněte si, že **testit** očekává, že její druhý parametr bude buď **int** nebo **char**<strong>\*</strong>. Argumenty předané jsou 0xffffffff ( **bez znaménka** **int**, nikoli **int**) a **NULL** (ve skutečnosti k **int**, nikoli **char**<strong>\*</strong>). Když je program zkompilován pro nativní kód, vytvoří tento výstup:

```Output
-1

(null)
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<stdio.h > a \<stdarg.h >

**Nepoužívané záhlaví:** \<souboru varargs.h >

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_va.c
// Compile with: cl /W3 /Tc crt_va.c
// The program below illustrates passing a variable
// number of arguments using the following macros:
//      va_start            va_arg              va_copy
//      va_end              va_list

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

```Output
Deviation is: 0.816497
Deviation is: 2.236068
Deviation is: 0.000000
```

## <a name="see-also"></a>Viz také:

[Přístup k argumentu](../../c-runtime-library/argument-access.md)<br/>
[vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)<br/>
