---
title: _CrtIsValidHeapPointer
ms.date: 11/04/2016
apiname:
- _CrtIsValidHeapPointer
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
- CrtlsValidHeapPointer
- _CrtIsValidHeapPointer
helpviewer_keywords:
- _CrtIsValidHeapPointer function
- CrtIsValidHeapPointer function
ms.assetid: caf597ce-1b05-4764-9f37-0197a982bec5
ms.openlocfilehash: cdfb02c622cddc4c86a99f614e469abc527d8845
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662004"
---
# <a name="crtisvalidheappointer"></a>_CrtIsValidHeapPointer

Ověří, zda zadaný ukazatel do haldy přidělené ve některé knihovny run-time jazyka C, ale ne nutně knihovnou CRT volajícího. Ve verzích CRT před Visual Studio 2010 ověří, že zadaný ukazatel je v lokální haldy (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
int _CrtIsValidHeapPointer(
   const void *userData
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Ukazatel na začátku bloku přidělené paměti.

## <a name="return-value"></a>Návratová hodnota

**_Crtisvalidheappointer –** vrátí TRUE, pokud je zadaný ukazatel v haldě sdílena všemi instancemi knihovny CRT. Ve verzích CRT před Visual Studio 2010 to vrátí hodnotu TRUE Pokud je zadaný ukazatel v lokální haldy. V opačném případě vrátí funkce hodnotu FALSE.

## <a name="remarks"></a>Poznámky

Nedoporučujeme tuto funkci použít. Od verze Visual Studio 2010 CRT knihovny, všechny knihovny CRT sdílet jeden haldy operačního systému, *haldy procesu*. **_Crtisvalidheappointer –** funkce oznámí, zda ukazatel přidělení haldy CRT, ale ne, který byl přidělen knihovnou CRT volajícího. Představte si třeba blok přidělaná pomocí sady Visual Studio 2010 verzi knihovny CRT. Pokud **_crtisvalidheappointer –** funkce exportované sadou Visual Studio 2012 verzi knihovny CRT testuje ukazatel, vrátí hodnotu TRUE. Už je to užitečné test. Ve verzích před Visual Studio 2010 knihovny CRT funkce používá tak, aby byl adresu konkrétní paměti v rámci lokální haldy. Lokální haldy odkazuje na haldě vytvoří a spravuje konkrétní instanci knihovny run-time C. Pokud se dynamická knihovna (DLL) obsahuje statický odkaz na knihovny run-time, má svoji vlastní instanci haldy za běhu a proto své vlastní haldy, nezávisle na lokální haldy vaší aplikace. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_crtisvalidheappointer –** odstraněna během předběžného zpracování.

Protože tato funkce vrací hodnotu TRUE nebo FALSE, může být předán do jednoho z [_ASSERT](assert-asserte-assert-expr-macros.md) makra vytvořit jednoduchý mechanismus zpracování ladění chyb. Následující příklad způsobí selhání kontrolního výrazu, pokud zadaná adresa není umístěn v rámci lokální haldy:

```C
_ASSERTE( _CrtIsValidHeapPointer( userData ) );
```

Další informace o tom, **_crtisvalidheappointer –** jde použít s další funkce ladění a makra, najdete v článku [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting). Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtIsValidHeapPointer**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak otestovat, zda paměť je platná, pokud se použije s parametrem knihovny runtime jazyka C před Visual Studio 2010. V tomto příkladu se poskytuje pro uživatelé staršího kódu knihovny CRT.

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
