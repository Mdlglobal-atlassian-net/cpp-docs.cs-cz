---
title: _calloc_dbg – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _calloc_dbg
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
- _calloc_dbg
- calloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2759c19fb88b820fc346b5cf35e97522b7e74cb6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396768"
---
# <a name="callocdbg"></a>_calloc_dbg

Přidělí počet bloky paměti v haldě s další místo pro hlavičku ladění a přepsání vyrovnávací paměti (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void *_calloc_dbg(
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Číslo*<br/>
Požadovaný počet bloky paměti.

*Velikost*<br/>
Požadovaná velikost každého bloku paměti (v bajtech).

*blockType*<br/>
Požadovaný typ bloku paměti: **_client_block –** nebo **_normal_block –**.

Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu[typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*lineNumber*<br/>
Číslo řádku na zdrojový soubor, kde byla vyžádána operace přidělení nebo **NULL**.

*Filename* a *linenumber* parametry jsou k dispozici pouze při **_calloc_dbg –** explicitně volané nebo [_crtdbg_map_alloc –](../../c-runtime-library/crtdbg-map-alloc.md)preprocesoru konstanta byla definována.

## <a name="return-value"></a>Návratová hodnota

Při úspěšném dokončení této funkce vrací ukazatel na části uživatele posledního bloku přidělenou paměť, volá nové funkce obslužné rutiny nebo vrátí **NULL**. Úplný popis návratový chování najdete v části poznámky. Další informace o používání nové funkce obslužné rutiny najdete v tématu [calloc –](calloc.md) funkce.

## <a name="remarks"></a>Poznámky

**_calloc_dbg –** je ladicí verze [calloc –](calloc.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání **_calloc_dbg –** byla snížena volání **calloc –**. Obě **calloc –** a **_calloc_dbg –** přidělit *číslo* paměti bloků v haldě základní ale **_calloc_dbg –** nabízí několik ladění funkce:

- Na obou stranách části uživatele bloku chcete otestovat nevracení vyrovnávací paměti.

- Parametr typ bloku ke sledování přidělení konkrétní typy.

- *Název souboru*/*linenumber* informací k určení původu požadavků na přidělení.

**_calloc_dbg –** přiděluje každého bloku paměti s něco víc místa, než požadovaný *velikost*. Další prostor se používá správce haldy ladění propojení bloky paměti ladění a k poskytování aplikace s informace o ladění záhlaví a přepsat vyrovnávací paměti. Při přidělení bloku části uživatele bloku je vyplněnou hodnotou 0xCD a každý z vyrovnávací paměti přepsat jsou vyplněny 0xFD.

**_calloc_dbg –** nastaví **errno** k **enomem –** Pokud selže přidělení paměti; **Einval –** je vrácena, pokud objem paměti vyžadované (včetně režie, již bylo zmíněno dříve) přesahuje **_heap_maxreq –**. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_calloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_callocd.c
// This program uses _calloc_dbg to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>
#include <crtdbg.h>

int main( void )
{
    long *bufferN, *bufferC;

    // Call _calloc_dbg to include the filename and line number
    // of our allocation request in the header and also so we can
    // allocate CLIENT type blocks specifically
    bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );
    bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );
    if( bufferN != NULL && bufferC != NULL )
        printf( "Allocated memory successfully\n" );
    else
        printf( "Problem allocating memory\n" );

    / _free_dbg must be called to free CLIENT type blocks
    free( bufferN );
    _free_dbg( bufferC, _CLIENT_BLOCK );
}
```

```Output
Allocated memory successfully
```

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[calloc](calloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
