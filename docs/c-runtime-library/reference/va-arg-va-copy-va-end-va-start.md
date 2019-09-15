---
title: va_arg, va_copy, va_end, va_start
ms.date: 11/04/2016
api_name:
- va_arg
- va_end
- va_copy
- va_start
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- va_arg
- va_start
- va_list
- va_alist
- va_dcl
- va_copy
- va_end
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
ms.openlocfilehash: 47bd9e3913c6664a52c970dd8a190636683d214e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957363"
---
# <a name="va_arg-va_copy-va_end-va_start"></a>va_arg, va_copy, va_end, va_start

Přistupuje k seznamům proměnných argumentů.

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

*type*<br/>
Typ argumentu, který se má načíst

*arg_ptr*<br/>
Ukazatel na seznam argumentů.

*propojovací*<br/>
Ukazatel na seznam argumentů, které mají být inicializovány ze *Src*

*src*<br/>
Ukazatel na inicializovaný seznam argumentů ke zkopírování na *cíl*.

*prev_param*<br/>
Parametr, který předchází prvnímu volitelnému argumentu.

## <a name="return-value"></a>Návratová hodnota

**va_arg** vrací aktuální argument. **va_copy**, **va_start** a **va_end** nevrací hodnoty.

## <a name="remarks"></a>Poznámky

Makra **va_arg**, **va_copy**, **va_end**a **va_start** poskytují přenosný způsob, jak přistupovat k argumentům funkce v případě, že funkce přebírá proměnný počet argumentů. Existují dvě verze maker: Makra definovaná v STDARG. H vyhovuje standardu ISO C99; Makra definovaná v VARARG H jsou zastaralé, ale jsou zachovány kvůli zpětné kompatibilitě s kódem, který byl napsán před standardem ANSI c89.

Tato makra předpokládají, že funkce přijímá pevný počet požadovaných argumentů následovaný proměnným počtem volitelných argumentů. Požadované argumenty jsou deklarovány jako běžné parametry funkce a jsou dostupné prostřednictvím názvů parametrů. K volitelným argumentům se dostanete prostřednictvím maker v STDARG. H (nebo VARARGS. H pro kód, který byl napsán před standardem ANSI c89), který nastaví ukazatel na první volitelný argument v seznamu argumentů, načte argumenty ze seznamu a po dokončení zpracování argumentu obnoví ukazatel.

Standardní makra jazyka C definovaná v STDARG. H se používají takto:

- **va_start** nastaví *arg_ptr* na první volitelný argument v seznamu argumentů předaných funkci. Argument *arg_ptr* musí mít typ **va_list** . Argument *prev_param* je název požadovaného parametru, který bezprostředně předchází první volitelný argument v seznamu argumentů. Pokud je *prev_param* deklarována s třídou úložiště registru, chování makra není definováno. **va_start** se musí použít před prvním použitím **va_arg** .

- **va_arg** načítá hodnotu *typu* z umístění, které je přiděleno *arg_ptr*a zvyšuje *arg_ptr* , aby odkazoval na další argument v seznamu pomocí velikosti *typu* k určení, kde se spustí další argument. **va_arg** lze použít libovolným počtem výskytů funkce k načtení argumentů ze seznamu.

- **va_copy** vytvoří kopii seznamu argumentů v aktuálním stavu. Parametr *Src* již musí být inicializován pomocí **va_start**; je možné, že byla aktualizována pomocí volání **va_arg** , ale nesmí být resetována pomocí **va_end**. Další argument načtený pomocí **va_arg** z *cíl* je stejný jako další argument načtený z *Src*.

- Po načtení všech argumentů **va_end** obnoví ukazatel na **hodnotu null**. **va_end** se musí volat v každém seznamu argumentů, který je inicializovaný s **va_start** nebo **va_copy** , než se funkce vrátí.

> [!NOTE]
> Makra v VARARG. H jsou zastaralá a jsou zachovaná pouze pro zpětnou kompatibilitu s kódem, který byl napsán před standardem ANSI c89. Ve všech ostatních případech použijte makra v STDARGS. Y.

Pokud jsou kompilovány pomocí [/CLR (modul CLR (Common Language Runtime Compilation))](../../build/reference/clr-common-language-runtime-compilation.md), mohou programy, které používají tato makra, generovat neočekávané výsledky z důvodu rozdílů mezi nativními systémy a systémy typů CLR (Common Language Runtime). Vezměte v úvahu tento program:

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

Všimněte si, že **testIt** očekává, že jeho druhý parametr bude buď **int** , nebo **char**<strong>\*</strong>. Předávané argumenty jsou 0xFFFFFFFF ( **unsigned** **int**, not **int**) a **null** (ve skutečnosti **int**, nikoli **char**<strong>\*</strong>). Když je program zkompilován pro nativní kód, vytvoří tento výstup:

```Output
-1

(null)
```

## <a name="requirements"></a>Požadavky

**Hlavička:** stdio. h > a \<STDARG. h > \<

**Zastaralé záhlaví:** \<VarArgs. h >

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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
