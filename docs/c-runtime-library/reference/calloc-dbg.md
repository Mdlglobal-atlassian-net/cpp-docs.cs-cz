---
title: _calloc_dbg
ms.date: 11/04/2016
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
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
ms.openlocfilehash: c525aa2f19b39ba3cb8304c59c96196707ad859c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454389"
---
# <a name="callocdbg"></a>_calloc_dbg

Přidělí počet bloků paměti haldy pro další místa pro ladění záhlaví a přepsat vyrovnávací paměti (pouze ladicí verze).

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
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

Informace o typech bloku přidělení a způsob jejich použití naleznete v tématu[typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*Číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadovaná operace rozdělení nebo **NULL**.

*Filename* a *linenumber* parametry jsou k dispozici pouze při **_calloc_dbg –** explicitně volána nebo [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)byla definována konstanta preprocesoru.

## <a name="return-value"></a>Návratová hodnota

Při úspěšném dokončení, tato funkce vrací ukazatel na uživatelské část poslední blok paměti přidělené, volá funkci novou obslužnou rutinu nebo vrátí **NULL**. Úplný popis návratový chování naleznete v části poznámky. Další informace o tom, jak použít nové funkce obslužné rutiny najdete v tématu [calloc](calloc.md) funkce.

## <a name="remarks"></a>Poznámky

**_calloc_dbg –** je ladicí verzi [calloc](calloc.md) funkce. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, každé volání **_calloc_dbg –** je omezená na volání **calloc**. Obě **calloc** a **_calloc_dbg –** přidělit *číslo* bloky paměti v haldě základní, ale **_calloc_dbg –** nabízí několik ladění funkce:

- Vyrovnávací paměť po obou stranách část uživatele bloku pro testování nevracení.

- Parametr typu blok pro sledování přidělení konkrétních typů.

- *Název souboru*/*linenumber* informací pro určení původu požadavků na přidělení.

**_calloc_dbg –** přiděluje každý blok paměti se trochu více místa požadovaného *velikost*. Další místo používá správce hald ladění k propojení paměť bloků ladicího a k poskytování aplikací s informace hlavičky ladění a přepsat vyrovnávací paměti. Při přidělení bloku část uživatele bloku je vyplněny hodnotou 0xCD a každý z vyrovnávací paměti přepsání jsou vyplněny 0xFD.

**_calloc_dbg –** nastaví **errno** k **ENOMEM** Pokud selže přidělování paměti. **EINVAL** je vrácena, pokud přesahuje velikost potřebné paměti (včetně režie již bylo zmíněno dříve) **_heap_maxreq –**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce haldy standardní oproti jeho ladicí verze v sestavení pro ladění aplikace najdete v tématu [ladění verze z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_calloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[calloc](calloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
