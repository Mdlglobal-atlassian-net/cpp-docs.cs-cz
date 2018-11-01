---
title: _CrtSetBreakAlloc
ms.date: 11/04/2016
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
helpviewer_keywords:
- CrtSetBreakAlloc function
- _CrtSetBreakAlloc function
ms.assetid: 33bfc6af-a9ea-405b-a29f-1c2d4d9880a1
ms.openlocfilehash: bbc4b0de553533dde95f37675b3c9234569e3505
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487825"
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

**_CrtSetBreakAlloc** umožňuje aplikaci provést detekci úniků paměti pomocí zastavení na určitém bodě přidělení paměti a trasování zpět k původu žádosti. Tato funkce používá sekvenční číslo pořadí přidělení objektu přiřazené bloku paměti při přidělení na haldě. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_CrtSetBreakAlloc** odstraněna během předběžného zpracování.

Číslo pořadí přidělení objektu je uložen v *lRequest* pole **_CrtMemBlockHeader** struktury definované v souboru Crtdbg.h. Když se informace o bloku paměti hlášeny jednou z funkcí s výpisem ladění, je toto číslo uzavřeno ve složených závorkách, jako například {36}.

Další informace o tom, **_CrtSetBreakAlloc** jde použít s dalšími funkcemi správy paměti naleznete v tématu [sledování požadavků na přidělení haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtSetBreakAlloc**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

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

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
