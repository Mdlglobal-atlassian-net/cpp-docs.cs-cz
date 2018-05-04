---
title: _Crtisvalidheappointer – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _CrtIsValidHeapPointer function
- CrtIsValidHeapPointer function
ms.assetid: caf597ce-1b05-4764-9f37-0197a982bec5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bc4be3f464cb48647985a96550a8b9ea13ce5ef
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="crtisvalidheappointer"></a>_CrtIsValidHeapPointer

Ověří, že zadaný ukazatel v haldy přidělené některé běhové knihovny jazyka C, ale nemusí nutně jít knihovny CRT volajícího. Ve verzích CRT před Visual Studio 2010 to ověří, že zadaný ukazatele v lokální haldy (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
int _CrtIsValidHeapPointer(
   const void *userData
);
```

### <a name="parameters"></a>Parametry

*UserData*<br/>
Ukazatel na začátku bloku přidělené paměti.

## <a name="return-value"></a>Návratová hodnota

**_Crtisvalidheappointer –** vrátí hodnotu TRUE, pokud je zadaný ukazatel v haldě sdílí všechny instance knihovny CRT. Ve verzích CRT před Visual Studio 2010 vrátí hodnotu TRUE Pokud je zadaný ukazatel v haldě místní. Funkce, jinak vrátí hodnotu FALSE.

## <a name="remarks"></a>Poznámky

Nedoporučujeme použití této funkce. Od verze Visual Studio 2010 CRT knihovny, všechny knihovny CRT sdílet jeden haldy operačního systému, *haldy procesu*. **_Crtisvalidheappointer –** funkce hlásí, zda má ukazatel byl přidělen CRT haldy, ale ne které byl přidělen pomocí knihovny CRT volajícího. Představte si třeba přidělené pomocí sady Visual Studio 2010 verzi knihovny CRT blok. Pokud **_crtisvalidheappointer –** funkce exportované sadou Visual Studio 2012 verzi knihovny CRT testy ukazatele, vrátí hodnotu TRUE. Toto je už užitečné test. Ve verzích knihovny CRT před Visual Studio 2010 funkce slouží k zajištění, že adresa konkrétní paměti je v rámci lokální haldy. Lokální haldy odkazuje na haldě vytvořen a spravován společností konkrétní instanci běhové knihovny jazyka C. Pokud dynamická knihovna (DLL) obsahuje statický odkaz na běhové knihovny, má svou vlastní instanci haldě běhu a proto vlastní haldy, nezávisle na lokální haldy aplikace. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání **_crtisvalidheappointer –** jsou odebrány při předběžném zpracování.

Protože tato funkce vrátí hodnotu TRUE nebo FALSE, mohla být předána do jednoho z [_ASSERT](assert-asserte-assert-expr-macros.md) makra pro vytváření jednoduchých ladění chyba mechanismu pro zpracování. V následujícím příkladu způsobí chybu assertion Pokud zadaná adresa není umístěn v lokální haldy:

```C
_ASSERTE( _CrtIsValidHeapPointer( userData ) );
```

Další informace o tom, **_crtisvalidheappointer –** lze použít s další funkce ladění a makra najdete v tématu [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting). Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtIsValidHeapPointer**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak otestovat, zda paměti je platná, pokud se používá s běhové knihovny jazyka C před Visual Studio 2010. V tomto příkladu jsou uvedeny pro uživatele starší verze kódu knihovny CRT.

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

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
