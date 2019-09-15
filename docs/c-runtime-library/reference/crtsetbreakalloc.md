---
title: _CrtSetBreakAlloc
ms.date: 11/04/2016
api_name:
- _CrtSetBreakAlloc
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
- CrtSetBreakAlloc
- _CrtSetBreakAlloc
helpviewer_keywords:
- CrtSetBreakAlloc function
- _CrtSetBreakAlloc function
ms.assetid: 33bfc6af-a9ea-405b-a29f-1c2d4d9880a1
ms.openlocfilehash: e13c908c1efd1af9196885dee6e3b0f45845946b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942306"
---
# <a name="_crtsetbreakalloc"></a>_CrtSetBreakAlloc

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

**_CrtSetBreakAlloc** umožňuje aplikaci provádět detekci nevracení paměti tím, že se v určitém bodě přidělení paměti a trasování vrátí k původní žádosti. Tato funkce používá sekvenční číslo pořadí přidělení objektu přiřazené bloku paměti při přidělení na haldě. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtSetBreakAlloc** se během předběžného zpracování odeberou.

Číslo pořadí přidělení objektu je uloženo v poli *poli* struktury **_CrtMemBlockHeader** definované v souboru Crtdbg. h. Když jsou informace o bloku paměti hlášeny jednou z funkcí výpisu ladění, toto číslo je uzavřeno ve složených závorkách, například {36}.

Další informace o tom, jak se dá **_CrtSetBreakAlloc** použít s dalšími funkcemi správy paměti, najdete v tématu [sledování požadavků na přidělení haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtSetBreakAlloc**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

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
