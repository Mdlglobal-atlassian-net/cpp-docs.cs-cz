---
title: _CrtIsValidHeapPointer
ms.date: 11/04/2016
api_name:
- _CrtIsValidHeapPointer
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
- CrtlsValidHeapPointer
- _CrtIsValidHeapPointer
helpviewer_keywords:
- _CrtIsValidHeapPointer function
- CrtIsValidHeapPointer function
ms.assetid: caf597ce-1b05-4764-9f37-0197a982bec5
ms.openlocfilehash: 9a8746eb2da90ac5515d92113b977011a4647fe6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942388"
---
# <a name="_crtisvalidheappointer"></a>_CrtIsValidHeapPointer

Ověřuje, že zadaný ukazatel je v haldě přidělené některými knihovnami run-time jazyka C, ale ne nutně v knihovně CRT volajícího. Ve verzích CRT před Visual Studio 2010 Tato verze ověřuje, zda je zadaný ukazatel v místní haldě (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
int _CrtIsValidHeapPointer(
   const void *userData
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Ukazatel na začátek přiděleného bloku paměti.

## <a name="return-value"></a>Návratová hodnota

**_CrtIsValidHeapPointer** vrací hodnotu true, pokud je zadaný ukazatel v haldě sdílené všemi instancemi knihoven CRT. Ve verzích CRT před Visual Studio 2010 vrátí tato hodnota hodnotu TRUE, pokud je zadaný ukazatel v místní haldě. V opačném případě vrátí funkce hodnotu FALSE.

## <a name="remarks"></a>Poznámky

Tuto funkci nedoporučujeme používat. Od knihovny CRT sady Visual Studio 2010, všechny knihovny CRT sdílejí jednu haldu operačního systému, *haldu procesu*. Funkce **_CrtIsValidHeapPointer** hlásí, zda byl ukazatel přidělen v haldě CRT, ale nikoli v případě, že byl přidělen knihovnou CRT volajícího. Zvažte například blok přidělený pomocí verze sady Visual Studio 2010 knihovny CRT. Pokud funkce **_CrtIsValidHeapPointer** exportovaná verzí sady Visual Studio 2012 knihovny CRT testuje ukazatel, vrátí hodnotu true. To již není užitečný test. Ve verzích knihovny CRT před Visual Studio 2010 se funkce používá k zajištění, že konkrétní adresa paměti je v rámci místní haldy. Místní halda odkazuje na haldu vytvořenou a spravovanou určitou instancí knihovny run-time jazyka C. Pokud dynamická knihovna (DLL) obsahuje statický odkaz na běhovou knihovnu, má svou vlastní instanci haldy běhu, a proto vlastní haldu nezávisle na místní haldě aplikace. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtIsValidHeapPointer** se během předběžného zpracování odeberou.

Vzhledem k tomu, že tato funkce vrací hodnotu TRUE nebo FALSE, může být předána jednomu z [_ASSERT](assert-asserte-assert-expr-macros.md) maker pro vytvoření jednoduchého mechanismu pro zpracování chyb ladění. Následující příklad způsobí selhání kontrolního výrazu, pokud zadaná adresa není umístěna v místní haldě:

```C
_ASSERTE( _CrtIsValidHeapPointer( userData ) );
```

Další informace o tom, jak lze **_CrtIsValidHeapPointer** použít s dalšími funkcemi ladění a makry, naleznete v tématu [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting). Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtIsValidHeapPointer**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak otestovat, zda je paměť platná, pokud je použita s běhovými knihovnami jazyka C před sadou Visual Studio 2010. Tento příklad je k dispozici pro uživatele starší verze kódu knihovny CRT.

```C
// crt_isvalid.c
// This program allocates a block of memory using _malloc_dbg
// and then tests the validity of this memory by calling
// _CrtIsMemoryBlock,_CrtIsValidPointer, and _CrtIsValidHeapPointer.

#include <stdio.h>
#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

#define  TRUE   1
#define  FALSE  0

int main( void )
{
    char *my_pointer;

    // Call _malloc_dbg to include the filename and line number
    // of our allocation request in the header information
    my_pointer = (char *)_malloc_dbg( sizeof(char) * 10,
        _NORMAL_BLOCK, __FILE__, __LINE__ );

    // Ensure that the memory got allocated correctly
    _CrtIsMemoryBlock((const void *)my_pointer, sizeof(char) * 10,
        NULL, NULL, NULL );

    // Test for read/write accessibility
    if (_CrtIsValidPointer((const void *)my_pointer,
        sizeof(char) * 10, TRUE))
        printf("my_pointer has read and write accessibility.\n");
    else
        printf("my_pointer only has read access.\n");

    // Make sure my_pointer is within the local heap
    if (_CrtIsValidHeapPointer((const void *)my_pointer))
        printf("my_pointer is within the local heap.\n");
    else
        printf("my_pointer is not located within the local"
               " heap.\n");

    free(my_pointer);
}
```

```Output
my_pointer has read and write accessibility.
my_pointer is within the local heap.
```

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
