---
title: _Crtsetbreakalloc – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetBreakAlloc
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
- CrtSetBreakAlloc
- _CrtSetBreakAlloc
dev_langs:
- C++
helpviewer_keywords:
- CrtSetBreakAlloc function
- _CrtSetBreakAlloc function
ms.assetid: 33bfc6af-a9ea-405b-a29f-1c2d4d9880a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32e8fedcd70d0e901c63cd5e794773451f436326
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="crtsetbreakalloc"></a>_CrtSetBreakAlloc

Nastaví zarážku na zadaném čísle pořadí přidělení objektů (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
long _CrtSetBreakAlloc(
   long lBreakAlloc
);
```

### <a name="parameters"></a>Parametry

*lBreakAlloc*<br/>
Číslo pořadí přidělení, pro které chcete nastavit zarážku.

## <a name="return-value"></a>Návratová hodnota

Vrátí předchozí číslo pořadí přidělení objektů, které mělo nastaveno zarážku.

## <a name="remarks"></a>Poznámky

**_Crtsetbreakalloc –** umožňuje aplikaci k provedení zjišťování nevracení paměti ukončování řádků v určitém bodě přidělování paměti a trasování zpět na počátek požadavku. Tato funkce používá sekvenční číslo pořadí přidělení objektu přiřazené bloku paměti při přidělení na haldě. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání **_crtsetbreakalloc –** jsou odebrány při předběžném zpracování.

Objekt přidělení pořadové číslo je uložen v *lRequest* pole z **_crtmemblockheader –** struktuře, které jsou definované v Crtdbg.h. Při hlášení informace o paměti bloku pomocí jedné z funkce výpisu ladění, je toto číslo uzavřené do složených závorek, jako například {36}.

Další informace o tom, **_crtsetbreakalloc –** lze použít s další funkce správy paměti najdete v tématu [sledování požadavků na přidělení haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtSetBreakAlloc**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

```C
// crt_setbrkal.c
// compile with: -D_DEBUG /MTd -Od -Zi -W3 /c /link -verbose:lib -debug

/*
* In this program, a call is made to the _CrtSetBreakAlloc routine
* to verify that the debugger halts program execution when it reaches
* a specified allocation number.
*/

#include <malloc.h>
#include <crtdbg.h>

int main( )
{
        long allocReqNum;
        char *my_pointer;

        /*
         * Allocate "my_pointer" for the first
         * time and ensure that it gets allocated correctly
         */
        my_pointer = malloc(10);
        _CrtIsMemoryBlock(my_pointer, 10, &allocReqNum, NULL, NULL);

        /*
         * Set a breakpoint on the allocation request
         * number for "my_pointer"
         */
        _CrtSetBreakAlloc(allocReqNum+2);

        /*
         * Alternate freeing and reallocating "my_pointer"
         * to verify that the debugger halts program execution
         * when it reaches the allocation request
         */
        free(my_pointer);
        my_pointer = malloc(10);
        free(my_pointer);
        my_pointer = malloc(10);
        free(my_pointer);
}
```

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
